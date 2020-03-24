---
title: Leitfaden für die Optimierung von Power BI
description: Leitfaden für die Optimierung von Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d718c9c7f627d735c083a46c1483815e3744faca
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378867"
---
# <a name="optimization-guide-for-power-bi"></a>Leitfaden für die Optimierung von Power BI

Dieser Artikel enthält Anweisungen, mit denen Entwickler und Administratoren optimierte Power BI-Lösungen erstellen und verwalten können. Sie können Ihre Lösung auf verschiedenen Architekturebenen optimieren. Dazu zählen:

- Die Datenquelle(n)
- Das Datenmodell
- Visualisierungen, einschließlich Dashboards, Power BI-Berichte und paginierte Power BI-Berichte
- Die Umgebung, einschließlich Kapazitäten, Datengateways und Netzwerk

## <a name="optimizing-the-data-model"></a>Optimieren des Datenmodells

Das Datenmodell unterstützt das gesamte Visualisierungserlebnis. Datenmodelle werden entweder extern oder intern gehostet und in Power BI als _Datasets_ bezeichnet. Sie sollten mit den verfügbaren Optionen vertraut sein und den geeigneten Typ von Dataset für Ihre Lösung auswählen. Sie können zwischen drei Datasetmodi wählen: „Import“, „DirectQuery“ und „Zusammengesetzt“. Weitere Informationen finden Sie unter [Datasets im Power BI-Dienst](../service-datasets-understand.md) und [Datasetmodi im Power BI-Dienst](../service-dataset-modes-understand.md).

Spezifische Anweisungen zu Datasetmodi finden Sie hier:

- [Verfahren für die Datenreduktion bei der Importmodellierung](import-modeling-data-reduction.md)
- [Leitfaden für das DirectQuery-Modell in Power BI Desktop](directquery-model-guidance.md)
- [Leitfaden für zusammengesetzte Modelle in Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Optimieren von Visualisierungen

Bei Power BI-Visualisierungen kann es sich um Dashboards, Power BI-Berichte oder paginierte Power BI-Berichte handeln. Da jede dieser Visualisierungen über eine eigene Architektur verfügt, gelten jeweils individuelle Anweisungen. 

### <a name="dashboards"></a>Dashboards

Power BI verfügt über einen Cache für Ihre Dashboardkacheln (mit Ausnahme von Liveberichtskacheln und Streamingkacheln). Weitere Informationen finden Sie unter [Aktualisieren von Daten in Power BI (Kachelaktualisierung)](../refresh-data.md#tile-refresh). Wenn Ihr Dataset eine dynamische [Sicherheit auf Zeilenebene (Row-Level Security, RLS)](../service-admin-rls.md) erzwingt, sollten Sie mit den Auswirkungen auf die Leistung vertraut sein, da Kacheln pro Benutzer zwischengespeichert werden.

Wenn Sie Liveberichtskacheln im Dashboard anheften, werden sie nicht aus dem Abfragecache bereitgestellt. Stattdessen entspricht das Verhalten dem regulären Berichtsverhalten, sodass Abfragen nach Bedarf an Back-End-Kerne erfolgen.

Wie der Name bereits vermuten lässt, bietet das Abrufen der Daten aus dem Abfragecache eine bessere und konsistentere Leistung als das Verwenden der Datenquelle. Eine Möglichkeit zum Nutzen dieser Funktionalität besteht darin, Dashboards als erste Landing Page für die Benutzer anzuzeigen. Heften Sie häufig verwendete und stark nachgefragte Visuals an die Dashboards an. Auf diese Weise werden Dashboards eine wertvolle „erste Abwehrlinie“ und bieten eine konsistente Leistung bei geringerer Beanspruchung der Kapazität. Die Benutzer können immer noch durch den Bericht klicken, um die Details zu analysieren.

Der Abfragecache wird bei DirectQuery-Datasets und Datasets mit Liveverbindungen in regelmäßigen Abständen durch Abfragen der Datenquelle aktualisiert. Standardmäßig erfolgt die Aktualisierung stündlich. Sie können in den Dataseteinstellungen jedoch auch ein anderes Intervall festlegen. Bei jeder Aktualisierung des Caches werden Abfragen an die zugrunde liegende Datenquelle gesendet, um den Cache zu aktualisieren. Die Anzahl der generierten Abfragen ist abhängig von der Anzahl der an Dashboards angehefteten Visuals, die diese Datenquelle benötigen. Beachten Sie, dass bei Aktivieren der Sicherheit auf Zeilenebene für jeden einzelnen Sicherheitskontext Abfragen generiert werden. Angenommen, Ihre Benutzer werden mithilfe von zwei Rollen kategorisiert, und es gibt zwei unterschiedliche Ansichten der Daten. Bei der Aktualisierung des Abfragecaches generiert Power BI zwei Sätze von Abfragen.

### <a name="power-bi-reports"></a>Power BI-Berichte

Für die Optimierung von Power BI-Berichtsentwürfen sind eine Reihe von Empfehlungen verfügbar.

> [!NOTE]
> Wenn Berichte auf einem DirectQuery-Dataset basieren, finden Sie unter [Leitfaden für das DirectQuery-Model in Power BI Desktop (Optimieren von Berichtsentwürfen)](directquery-model-guidance.md#optimize-report-designs) weitere Optimierungen für Berichtsentwürfe.

#### <a name="apply-the-most-restrictive-filters"></a>Anwenden der restriktivsten Filter

Je mehr Daten in einem Visual angezeigt werden müssen, umso länger dauert das Laden des Visuals. Auch wenn dieses Prinzip offensichtlich erscheint, gerät es leicht in Vergessenheit. Betrachten Sie beispielsweise ein großes Dataset. Auf Grundlage dieses Datasets erstellen Sie einen Bericht mit einer Tabelle. Die Endbenutzer verwenden Slicer auf der Seite, um die gewünschten Zeilen abzurufen – in der Regel sind sie nur an wenigen Dutzend Zeilen interessiert.

Ein häufiger Fehler besteht darin, dass die Standardansicht der Tabelle nicht gefiltert ist und alle Zeilen zeigt, in diesem Fall über 100 Millionen. Die Daten für diese Zeilen werden in den Arbeitsspeicher geladen und bei jeder Aktualisierung dekomprimiert. Diese Art der Verarbeitung geht mit hohen Arbeitsspeicheranforderungen einher. Die Lösung: Verwenden Sie den Filter „Top N“, um die maximale Anzahl von Elementen zu verringern, die in der Tabelle angezeigt werden. Sie können die maximale Anzahl von Elementen auf einen deutlich höheren Wert festlegen als die Menge, die Benutzer benötigen, z. B. 10.000. Das Ergebnis hiervon ist, dass sich die Benutzeroberfläche für Endbenutzer nicht ändert, die Speicherauslastung aber bedeutend sinkt. Außerdem wird die Leistung verbessert.

Ein ähnlicher Ansatz wird für alle visuellen Elemente in Ihrem Bericht empfohlen. Fragen Sie sich, ob wirklich alle Daten in einem Visual benötigt werden. Gibt es Möglichkeiten, die Menge der angezeigten Daten im Visual zu filten, ohne dass sich für den Endbenutzer viel ändert? Bedenken Sie, dass insbesondere Tabellen äußerst ressourcenintensiv sein können.

#### <a name="limit-visuals-on-report-pages"></a>Einschränken von Visuals auf Berichtsseiten

Das oben genannte Prinzip gilt genauso für die Anzahl von visuellen Elementen, die zu einer Berichtsseite hinzugefügt werden. Es wird dringend empfohlen, die Anzahl von visuellen Elementen auf einer Berichtsseite auf die wirklich benötigten Elemente zu beschränken. [Drillthroughseiten](report-drillthrough.md) und [QuickInfos zur Berichtsseite](report-page-tooltips.md) sind eine hervorragende Möglichkeit, um zusätzliche Informationen bereitzustellen, ohne dem Bericht weitere visuelle Elemente hinzuzufügen.

#### <a name="evaluate-custom-visual-performance"></a>Auswerten der Leistung von benutzerdefinierten visuellen Elementen

Achten Sie darauf, jedes benutzerdefinierte Visual zu analysieren, um eine hohe Leistung sicherzustellen. Schlecht optimierte Power BI-Visuals können sich negativ auf die Leistung des gesamten Berichts auswirken.

### <a name="power-bi-paginated-reports"></a>Paginierte Power BI-Berichte

Paginierte Power BI-Berichtsentwürfe können optimiert werden, indem Sie bewährte Methoden für den Datenabruf des Berichts anwenden. Weitere Informationen finden Sie unter [Leitfaden zum Datenabruf von paginierten Berichten](report-paginated-data-retrieval.md).

Stellen Sie außerdem sicher, dass im Rahmen Ihrer Kapazität genügend Arbeitsspeicher für die [Workload paginierter Berichte](../service-admin-premium-workloads.md#paginated-reports) zugeordnet ist.

## <a name="optimizing-the-environment"></a>Optimieren der Umgebung

Sie können die Power BI-Umgebung optimieren, indem Sie Kapazitätseinstellungen konfigurieren, Datengateways anpassen und die Netzwerklatenz verringern.

### <a name="capacity-settings"></a>Kapazitätseinstellungen

Bei Verwendung dedizierter Kapazitäten – verfügbar mit Power BI Premium (P-SKUs) oder Power BI Embedded (A-SKUs, A4-A6) – haben Sie die Möglichkeit, Kapazitätseinstellungen zu verwalten. Weitere Informationen finden Sie unter [Verwalten von Premium-Kapazitäten](../service-premium-capacity-manage.md). Eine Anleitung zur Optimierung Ihrer Kapazität finden Sie unter [Optimieren von Premium-Kapazitäten](../service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Festlegen der Gatewaygröße

Ein Gateway ist immer dann erforderlich, wenn Power BI Zugriff auf Daten benötigt, die nicht direkt über das Internet zugänglich sind. Sie können das [lokale Datengateway](../service-gateway-onprem.md) entweder auf einem lokalen Server oder in einem VM-gehosteten IaaS-Dienst (Infrastructure-as-a-Service) installieren.

Empfehlungen zu Gatewayworkloads und zur Festlegung der Größe finden Sie unter [Festlegen der Größe des lokalen Datengateways](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Netzwerklatenz

Die Netzwerklatenz kann die Leistung eines Berichts beeinträchtigen, wenn es länger dauert, bis Anforderungen den Power BI-Dienst erreichen und Antworten übermittelt werden. Mandanten in Power BI werden einer bestimmten Region zugewiesen.

> [!TIP]
> Im Artikel [Wo befindet sich mein Power BI-Mandant?](../service-admin-where-is-my-tenant-located.md) erfahren Sie, wie Sie ermitteln, in welcher Region sich Ihr Mandant befindet.

Wenn Benutzer von einem Mandanten aus auf den Power BI-Dienst zugreifen, werden ihre Anforderungen immer an diese Region weitergeleitet. Wenn die Anforderungen den Power BI-Dienst erreichen, kann der Dienst zusätzliche Anforderungen senden (z.B. an die zugrunde liegende Datenquelle oder das Gateway), die ebenfalls der Netzwerklatenz unterliegen.

Tools wie [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) bieten einen Überblick über die Netzwerklatenz zwischen dem Client und der Azure-Region. Im Allgemeinen sollten sich, um die Auswirkungen der Netzwerklatenz zu minimieren, Datenquellen, Gateways und der Power BI-Cluster in möglichst großer Nähe zueinander befinden. Idealerweise befinden sie sich innerhalb derselben Region. Wenn die Netzwerklatenz ein Problem darstellt, versuchen Sie, Gateways und Datenquellen näher an Ihrem Power BI-Cluster anzuordnen, indem Sie sie auf in der Cloud gehosteten VMs platzieren.

## <a name="monitoring-performance"></a>Leistungsüberwachung

Sie können die Leistung überwachen, um Engpässe zu ermitteln. Ein Schwerpunkt der kontinuierlichen Optimierung sollten langsame Abfragen oder langsame visuelle Berichtselemente sein. Die Überwachung kann zur Entwurfszeit in Power BI Desktop oder auf Produktionsworkloads in Power BI Premium-Kapazitäten erfolgen. Weitere Informationen finden Sie unter [Überwachen der Berichtsleistung in Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Dokumentation zum Power BI-Leitfaden](index.yml)
- [Überwachen der Berichtsleistung](monitor-report-performance.md)
- Whitepaper: [Planning a Power BI Enterprise Deployment](https://go.microsoft.com/fwlink/?linkid=2057861)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
