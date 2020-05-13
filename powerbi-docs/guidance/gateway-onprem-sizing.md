---
title: Festlegen der Größe des lokalen Datengateways
description: Dies ist ein Leitfaden für das Ändern der Größe des lokalen Datengateways.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: de84dd7e9021abf1198f2dc4f910afb8bd078ac6
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279524"
---
# <a name="on-premises-data-gateway-sizing"></a>Festlegen der Größe des lokalen Datengateways

Dieser Artikel richtet sich an Power BI-Administratoren, die das [lokale Datengateway](../connect-data/service-gateway-onprem.md) installieren und verwalten müssen.

Das Gateway ist immer dann erforderlich, wenn Power BI Zugriff auf Daten benötigt, die nicht direkt über das Internet zugänglich sind. Es kann entweder auf einem lokalen Server oder in einem VM-gehosteten IaaS-Dienst (Infrastructure-as-a-Service) installiert werden.

## <a name="gateway-workloads"></a>Gatewayworkloads

Das lokale Datengateway unterstützt zwei Workloads. Es ist wichtig, dass Sie diese verstehen, bevor Sie sich mit der Gatewaygröße und den Empfehlungen beschäftigen.

### <a name="cached-data-workload"></a>Workload des Typs „Zwischengespeicherte Daten“

Die Workload des Typs _Zwischengespeicherte Daten_ ruft Quelldaten ab und transformieren sie, damit sie in Power BI-Datasets geladen werden können. Dies erfolgt in drei Schritten:

1. **Verbindung:** Das Gateway stellt eine Verbindung mit den Quelldaten her.
1. **Datenabruf und Transformation:** Die Daten werden abgerufen und bei Bedarf transformiert. Wenn möglich überträgt die Power Query-Mashup-Engine Transformationsschritte mithilfe von Push zur Datenquelle. Dieser Vorgang wird als _[Query Folding](power-query-folding.md)_ bezeichnet. Wenn dies nicht möglich ist, müssen die Transformationen vom Gateway durchgeführt werden. In diesem Fall verbraucht das Gateway mehr CPU- und Arbeitsspeicherressourcen.
1. **Übertragung:** Die Daten werden an den Power BI-Dienst übertragen. Dabei ist besonders für große Datenvolumen eine zuverlässige und schnelle Internetverbindung entscheidend.

![Die Abbildung zeigt das lokale Datengateway, das mit lokalen Quellen verbunden ist: relationale Datenbanken, Excel-Arbeitsmappen und CSV-Dateien. Das Gateway ruft Daten ab und transformiert sie.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Workloads des Typs „Liveverbindung und DirectQuery“

Die Workload des Typs _Liveverbindung und DirectQuery_ funktioniert größtenteils im Pass-Through-Modus. Der Power BI-Dienst sendet Abfragen, und das Gateway antwortet mit Abfrageergebnissen. Abfrageergebnisse sind allgemein eher klein.

- Weitere Informationen zur Liveverbindung finden Sie unter [Datasets im Power BI-Dienst (extern gehostete Modelle)](../connect-data/service-datasets-understand.md#external-hosted-models).
- Weitere Informationen zu DirectQuery finden Sie im Artikel [Datasetmodi im Power BI-Dienst (DirectQuery-Modus)](../connect-data/service-dataset-modes-understand.md#directquery-mode).

Diese Workload benötigt CPU-Ressourcen für das Routing von Abfragen und Abfrageergebnissen. Normalerweise ist die CPU-Auslastung sehr viel geringer als für Workloads des Typs „Zwischengespeicherte Daten“. Dies gilt vor allem dann, wenn Daten für die Zwischenspeicherung transformiert werden müssen.

Eine zuverlässige, schnelle und gleichmäßige Verbindung ist wichtig, damit Benutzer von Berichten optimal damit arbeiten können.

![Die Abbildung zeigt das lokale Datengateway, das mit lokalen Quellen verbunden ist: Tabellarische und relationale Analysis Services-Datenbanken Das Gateway funktioniert hauptsächlich im Pass-Through-Modus.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Überlegungen zur Größe

Das Festlegen der korrekten Größe für Ihren Gatewaycomputer kann von den folgenden Faktoren abhängen:

- Bei Workloads des Typs „Zwischengespeicherte Daten“:
  - Anzahl der gleichzeitigen Datasetaktualisierungen
  - Typen von Datenquellen (relationale Datenbank, Analysedatenbank, Datenfeeds oder Dateien)
  - Datenvolumen, das aus Datenquellen abgerufen werden soll
  - alle Transformationen, die von der Power Query-Mashup-Engine ausgeführt werden müssen
  - Datenvolumen, das an den Power BI-Dienst übertragen werden soll
- Bei Workloads des Typs „Liveverbindung und DirectQuery“:
  - Anzahl von Benutzern, die den Bericht gleichzeitig verwenden
  - Anzahl der Visuals auf den Berichtsseiten (jedes Visual sendet mindestens eine Abfrage)
  - Häufigkeit, mit der der Abfragecache des Power BI-Dashboards aktualisiert wird
  - Anzahl von Echtzeitberichten, die das Feature [Automatische Seitenaktualisierung](../create-reports/desktop-automatic-page-refresh.md) verwenden
  - ob Datasets die [Sicherheit auf Zeilenebene](../create-reports/desktop-rls.md) erzwingen

Im Allgemeinen erfordern Workloads des Typs „Liveverbindung und DirectQuery“ ausreichend CPU, während Workloads des Typs „Zwischengespeicherte Daten“ mehr CPU und Arbeitsspeicher benötigen. Beide Workloads benötigen sowohl zum Power BI-Dienst als auch zu den Datenquellen gute Konnektivität.

> [!NOTE]
> Die Kapazitäten von Power BI verursachen Limits für den Parallelismus der Modellaktualisierung, die Liveverbindung und den DirectQuery-Durchsatz. Es ist zwecklos, für Ihre Gateways eine Größe festzulegen, die die vom Power BI-Dienst unterstützte Größe übersteigt. Limits variieren je nach Premium-SKU (und gleichgroßen A-SKUs). Weitere Informationen finden Sie unter [Was ist Power BI Premium? (Kapazitätsknoten)](../admin/service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Empfehlungen

Die Empfehlungen für Gatewaygrößen hängen von vielen Faktoren ab. In diesem Abschnitt erhalten Sie allgemeine Empfehlungen, die Ihnen bei der Entscheidung helfen können.

### <a name="initial-sizing"></a>Anfängliche Größeneinstellung

Es kann sehr schwierig sein, die richtige Größe korrekt einzuschätzen. Es wird empfohlen, mit einem Computer mit mindestens 8 CPU-Kernen, 8 GB RAM und mehreren Gigabit an Netzwerkadaptern zu beginnen. Anschließend können Sie eine typische Gatewayworkload messen, indem Sie die Systemzähler für die CPU und den Arbeitsspeicher protokollieren. Weitere Informationen finden Sie unter [Überwachen und Optimieren der Leistung des lokalen Datengateways](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Konnektivität

Schaffen Sie von vornherein die besten Voraussetzungen für die bestmögliche Konnektivität zwischen dem Power BI-Dienst und Ihrem Gateway sowie zwischen dem Gateway und den Datenquellen.

- Bemühen Sie sich um Zuverlässigkeit, Schnelligkeit und eine niedrige, gleichmäßige Latenz.
- Eliminieren (oder reduzieren) Sie Computerhops zwischen dem Gateway und Ihren Datenquellen.
- Entfernen Sie alle Netzwerkeinschränkungen, die von Ihrer Firewallproxyschicht verursacht werden. Weitere Informationen zu Power BI-Endpunkten finden Sie unter [Power BI-URLs zur Aufnahme in die Whitelist](../admin/power-bi-whitelist-urls.md).
- Konfigurieren Sie [Azure ExpressRoute](/azure/expressroute/expressroute-introduction), um private, verwaltete Verbindungen zu Power BI herzustellen.
- Stellen Sie für Datenquellen auf Azure-VMs sicher, dass sich die VMs [in derselben Region wie der Power BI-Dienst befinden](../admin/service-admin-where-is-my-tenant-located.md).
- Stellen Sie sicher, dass für Liveverbindungsworkloads zu SQL Server Analysis Services (SSAS), die die dynamische Sicherheit auf Zeilenebene verwenden, eine gute Verbindung zwischen dem Gatewaycomputer und dem lokalen Active Directory-Dienst besteht.

### <a name="clustering"></a>Clustering

Bei großen Bereitstellungen können Sie ein Gateway von Clusterinstallationen erstellen. Mit Clustern lassen sich Single Points of Failure vermeiden. Außerdem können Sie einen gatewayübergreifenden Lastenausgleich für den Datenverkehr vornehmen. Sie können:

- Installieren von mindestens einem Gateway in einem Cluster
- Auslagern von Workloads in eigenständige Gateways oder Cluster von Gatewayservern

Weitere Informationen finden Sie unter [Verwalten von Clustern mit hoher Verfügbarkeit und Lastenausgleich für das lokale Datengateway](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Datasetentwurf und -einstellungen

Der Entwurf und die Einstellungen eines Datasets können Auswirkungen auf Gatewayworkloads haben. Sie können die folgende Maßnahmen ergreifen, um die Gatewayworkload zu reduzieren.

Bei importierten Datasets:

- Verringern Sie die Häufigkeit der Datenaktualisierung.
- Konfigurieren Sie eine [inkrementelle Aktualisierung](../admin/service-premium-incremental-refresh.md), um die zu übertragende Datenmenge zu minimieren.
- Stellen Sie sicher, dass nach Möglichkeit [Query Folding](power-query-folding.md) angewendet wird.
- Vor allem bei großen Datenmengen oder einem Bedarf an geringer Latenz sollten Sie den Entwurf in ein DirectQuery-Modell oder ein [zusammengesetztes](../connect-data/service-dataset-modes-understand.md#composite-mode) Modell konvertieren.

Bei DirectQuery-Datasets:

- Optimieren Sie die Datenquellen, Modelle und Berichtsentwürfe. Weitere Informationen finden Sie unter [Leitfaden für das DirectQuery-Model in Power BI Desktop](directquery-model-guidance.md).
- Erstellen Sie [Aggregationen](../transform-model/desktop-aggregations.md), um allgemeine Ergebnisse zwischenzuspeichern und so die Anzahl von DirectQuery-Anforderungen zu reduzieren.
- Schränken Sie die Intervalle für die [automatische Seitenaktualisierung](../create-reports/desktop-automatic-page-refresh.md) in Berichtsentwürfen und den Kapazitätseinstellungen ein.
- Schränken Sie die Aktualisierungshäufigkeit des Dashboardcaches vor allem dann ein, wenn die dynamische Sicherheit auf Zeilenebene erzwungen wird.
- Konvertieren Sie den Entwurf vor allem bei kleineren Datenmengen oder permanenten Daten in ein importiertes oder ein [zusammengesetztes](../connect-data/service-dataset-modes-understand.md#composite-mode) Modell.

Bei Liveverbindungsdatasets:

- Schränken Sie die Aktualisierungshäufigkeit des Dashboardcaches vor allem dann ein, wenn die dynamische Sicherheit auf Zeilenebene erzwungen wird.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Leitfaden zum Bereitstellen eines Datengateways für Power BI](../connect-data/service-gateway-deployment-guidance.md)
- [Configure proxy settings for the on-premises data gateway (Konfigurieren von Proxyeinstellungen für das lokale Datengateway)](/data-integration/gateway/service-gateway-proxy)
- [Überwachen und Optimieren der Leistung des lokalen Datengateways](/data-integration/gateway/service-gateway-performance)
- [Lokales Datengateway – Power BI](../connect-data/service-gateway-onprem-tshoot.md)
- [Problembehandlung für das lokale Datengateway](/data-integration/gateway/service-gateway-tshoot)
- [Query Folding-Anleitung für Power BI Desktop](power-query-folding.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com)
