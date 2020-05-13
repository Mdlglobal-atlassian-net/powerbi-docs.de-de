---
title: Verwalten von Microsoft Power BI Premium-Kapazitäten
description: Beschreibt Verwaltungsaufgaben für Power BI Premium-Kapazitäten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 2e32a61891cee2fb5e2a80167d5283962dc164bb
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83134816"
---
# <a name="managing-premium-capacities"></a>Verwalten von Premium-Kapazitäten

Das Verwalten von Power BI Premium umfasst das Erstellen, Verwalten und Überwachen von Premium-Kapazitäten. Dieser Artikel bietet einen Überblick über Kapazitäten. Schrittanleitungen finden Sie unter [Verwalten von Premium-Kapazitäten](service-admin-premium-manage.md).

## <a name="creating-and-managing-capacities"></a>Erstellen und Verwalten von Kapazitäten

Auf der Seite **Kapazitätseinstellungen** des Power BI-Verwaltungsportals werden die Anzahl der erworbenen V-Kerne und verfügbare Premium-Kapazitäten angezeigt. Auf der Seite können globale Office 365-Administratoren und Power BI-Dienstadministratoren Premium-Kapazitäten aus verfügbaren V-Kernen erstellen oder vorhandene Premium-Kapazitäten ändern.

Beim Erstellen einer Premium-Kapazität müssen Administratoren Folgendes definieren:

- Kapazitätsname (innerhalb des Mandanten eindeutig).
- Kapazitätsadministrator(en).
- Kapazitätsumfang.
- Region für Data Residency.

Mindestens ein Kapazitätsadministrator muss zugewiesen werden. Als Kapazitätsadministratoren zugewiesene Benutzer können folgende Aktionen ausführen:

- Zuweisen von Arbeitsbereichen zur Kapazität.
- Verwalten von Benutzerberechtigungen, um zusätzliche Kapazitätsadministratoren oder Benutzer mit Zuweisungsberechtigungen hinzuzufügen (damit sie der Kapazität Arbeitsbereiche zuweisen können).
- Verwalten von Workloads, um die maximale Speicherauslastung von Workloads für paginierte Berichte und Dataflows zu konfigurieren.
- Neustarten der Kapazität, um alle Vorgänge aufgrund einer Systemüberlastung zurückzusetzen.

Kapazitätsadministratoren können nicht auf Arbeitsbereichsinhalte zugreifen, solange sie nicht explizit in Arbeitsbereichsberechtigungen zugewiesen werden. Sie haben auch keinen Zugriff auf alle Power BI-Administrationsbereiche (solange sie nicht explizit zugewiesen werden) wie Nutzungsmetriken, Überwachungsprotokolle oder Mandanteneinstellungen. Wichtig: Kapazitätsadministratoren sind auch nicht berechtigt, neue Kapazitäten zu erstellen oder vorhandene Kapazitäten zu skalieren. Administratoren werden pro Kapazität zugewiesen, um sicherzustellen, dass sie nur Kapazitäten anzeigen und verwalten können, denen sie zugewiesen sind.

Der Kapazitätsumfang wird aus einer Liste verfügbarer SKU-Optionen ausgewählt, die durch die Anzahl der verfügbaren V-Kerne im Pool eingeschränkt wird. Es ist möglich, mehrere Kapazitäten aus dem Pool zu erstellen, für die eine oder mehrere erworbene SKUs als Quelle dienen könnten. Beispielsweise könnte eine P3-SKU (32 V-Kerne) zum Erstellen von drei Kapazitäten verwendet werden: eine P2 (16 V-Kerne) und zwei P1 (2 x 8 V-Kerne). Verbesserte Leistung und Skalierbarkeit können Sie erzielen, indem Sie kleinere Kapazitäten erstellen, wie im Artikel [Optimieren von Premium-Kapazitäten](service-premium-capacity-optimize.md) beschrieben. Die folgende Abbildung zeigt ein Beispielsetup für die fiktive Organisation Contoso aus fünf Premium-Kapazitäten (3 x P1 und 2 x P3), die jeweils Arbeitsbereiche enthalten, und mehreren Arbeitsbereichen in gemeinsam genutzter Kapazität.

![Ein Beispielsetup für die fiktive Organisation Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Eine Premium-Kapazität kann anderen Regionen als der Startregion des Power BI-Mandanten zugewiesen werden; dieses Feature wird als Multi-Geo bezeichnet. Mit Multi-Geo kann die Verwaltung steuern, in welchen Rechenzentren innerhalb der definierten geografischen Regionen sich Ihr Power BI-Inhalt befindet. Der Grund für eine Multi-Geo-Bereitstellung liegt in der Regel eher in der Konformität mit Unternehmens- oder behördlichen Anforderungen als in Leistung und Skalierung. Für das Laden von Berichten und Dashboards sind weiterhin Metadatenanforderungen an die Startregion erforderlich. Weitere Informationen finden Sie unter [Multi-Geo-Unterstützung für Power BI Premium](service-admin-premium-multi-geo.md).

Power BI-Dienstadministratoren und globale Office 365-Administratoren können Premium-Kapazitäten ändern. Sie haben insbesondere folgende Möglichkeiten:

- Ändern des Kapazitätsumfangs zum zentralen Hoch- oder Herunterskalieren von Ressourcen.
- Hinzufügen oder Entfernen von Kapazitätsadministratoren.
- Hinzufügen oder Entfernen von Benutzern, die über Zuweisungsberechtigungen verfügen.
- Hinzufügen oder Entfernen zusätzlicher Workloads.
- Ändern von Regionen.

Zuweisungsberechtigungen sind erforderlich, um einer bestimmten Premium-Kapazität einen Arbeitsbereich zuzuweisen. Die Berechtigungen können für die gesamte Organisation, bestimmte Benutzer oder Gruppen gewährt werden.

Premium-Kapazitäten unterstützen standardmäßig Workloads für die Ausführung von Power BI-Abfragen. Premium-Kapazitäten unterstützen auch zusätzliche Workloads: **KI (Cognitive Services)** , **paginierte Berichte** und **Dataflows**. Jede Workload erfordert das Konfigurieren des maximalen Arbeitsspeichers (als Prozentsatz des gesamten verfügbaren Arbeitsspeichers) für die Verwendung durch die Workload. Es ist wichtig zu verstehen, dass das Erhöhen der maximalen Speicherzuordnungen sich auf die Anzahl der aktiven Modelle, die gehostet werden können, und den Durchsatz von Aktualisierungen auswirken kann. 

Der Arbeitsspeicher wird Dataflows dynamisch zugeordnet, ist paginierten Berichten jedoch statisch zugeordnet. Der Grund für die statische Zuordnung des maximalen Arbeitsspeichers ist, dass paginierte Berichte innerhalb eines gesicherten, eigenständigen Raums der Kapazität ausgeführt werden können. Beim Festlegen des Arbeitsspeichers für paginierte Berichte ist Vorsicht geboten, da der verfügbare Arbeitsspeicher für das Laden von Modellen reduziert wird. Weitere Informationen finden Sie in den [Standardeinstellungen für den Arbeitsspeicher](service-admin-premium-workloads.md#default-memory-settings).

Das Löschen einer Premium-Kapazität ist möglich und führt nicht zum Löschen der Arbeitsbereiche und Inhalte. Stattdessen werden alle zugewiesenen Arbeitsbereiche in gemeinsam genutzte Kapazität verschoben. Wenn die Premium-Kapazität in einer anderen Region erstellt wurde, wird der Arbeitsbereich in die gemeinsam genutzte Kapazität der Startregion verschoben.

### <a name="assigning-workspaces-to-capacities"></a>Zuweisen von Arbeitsbereichen zu Kapazitäten

Arbeitsbereiche können einer Premium-Kapazität im Power BI-Verwaltungsportal oder, für einen Arbeitsbereich, im Bereich **Arbeitsbereich** zugewiesen werden.

Kapazitätsadministratoren und globale Administratoren von Office 365 oder Power BI-Dienstadministratoren können Arbeitsbereiche im Power BI-Verwaltungsportal im Massenvorgang zuweisen. Zuweisungen im Massenvorgang können auf Folgendes angewendet werden:

- **Arbeitsbereiche nach Benutzer**: Alle Arbeitsbereiche, die sich im Besitz dieser Benutzer befinden, einschließlich persönlicher Arbeitsbereiche, werden der Premium-Kapazität zugewiesen. Dies schließt die erneute Zuweisung von Arbeitsbereichen ein, wenn sie bereits einer anderen Premium-Kapazität zugewiesen sind. Außerdem werden den Benutzern auch Berechtigungen zur Zuweisung von Arbeitsbereichen zugewiesen.

- **Bestimmte Arbeitsbereiche**
- **Die Arbeitsbereiche der gesamten Organisation**: Alle Arbeitsbereiche einschließlich persönlicher Arbeitsbereiche werden der Premium-Kapazität zugewiesen. Allen derzeitigen und zukünftigen Benutzern werden Berechtigungen zur Zuweisung von Arbeitsbereichen zugewiesen. Diese Vorgehensweise wird nicht empfohlen. Ein gezielterer Ansatz wird bevorzugt.

Ein Arbeitsbereich kann einer Premium-Kapazität im Bereich **Arbeitsbereich** hinzugefügt werden, sofern der Benutzer ein Arbeitsbereichsadministrator ist und über Zuweisungsberechtigungen verfügt.

![Verwenden des Bereichs „Arbeitsbereich“ zum Zuweisen eines Arbeitsbereichs zu einer Premium-Kapazität](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Arbeitsbereichsadministratoren können einen Arbeitsbereich aus einer Kapazität entfernen (in gemeinsam genutzte Kapazität), ohne dass eine Zuweisungsberechtigung erforderlich ist. Durch das Entfernen von Arbeitsbereichen aus dedizierten Kapazitäten wird der Arbeitsbereich tatsächlich in gemeinsam genutzte Kapazität verlagert. Beachten Sie, dass das Entfernen eines Arbeitsbereichs aus einer Premium-Kapazität negative Konsequenzen haben kann, sodass beispielsweise gemeinsam genutzte Inhalte nicht mehr für Benutzer mit Power BI Free-Lizenz verfügbar sind, oder das Aussetzen geplanter Aktualisierung, wenn die durch gemeinsam genutzte Kapazitäten unterstützten Ressourcen überschritten werden.

Im Power BI-Dienst ist ein Arbeitsbereich, der einer Premium-Kapazität zugewiesen ist, leicht an dem Diamantsymbol zu erkennen, mit dem der Name des Arbeitsbereichs versehen ist.

![Identifizieren eines Arbeitsbereichs, der einer Premium-Kapazität zugewiesen ist](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Überwachen von Kapazitäten

Durch Überwachen von Premium-Kapazitäten erhalten Administratoren Informationen über die Leistung ihrer Kapazitäten. Kapazitäten können mithilfe des Power BI-Verwaltungsportals und der **Power BI Premium-Kapazitäts-Metrik-App** (Power BI) überwacht werden.

### <a name="power-bi-admin-portal"></a>Power BI-Verwaltungsportal

Im Verwaltungsportal enthält die Registerkarte **Integrität** für jede Kapazität Zusammenfassungsmetriken für die Kapazität und jede aktivierte Workload. Metriken zeigen einen Durchschnittswert der letzten sieben Tage an.  

Auf Kapazitätsebene sind Metriken für alle aktivierten Workloads kumulativ. Folgende Metriken werden bereitgestellt:

- **CPU-AUSLASTUNG**: Gibt die durchschnittliche CPU-Auslastung als Prozentsatz der gesamten für die Kapazität verfügbaren CPU-Ressourcen an.  
- **SPEICHERAUSLASTUNG**: Gibt die durchschnittliche Speicherauslastung (in GB) als Teil der Summe des verfügbaren Arbeitsspeichers für die Kapazität an. 

Für jede aktivierte Workload werden CPU-Auslastung und Speicherauslastung sowie eine Reihe von workloadspezifischen Metriken bereitgestellt. Beispielsweise zeigt **Gesamtzahl** für die Dataflowworkload die gesamten Aktualisierungen für jeden Dataflow an und **Durchschnittliche Dauer** die durchschnittliche Dauer der Aktualisierung für den Dataflow.

![Registerkarte „Kapazitätsintegrität“ im Portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Weitere Informationen zu allen verfügbaren Metriken für die einzelnen Workloads finden Sie unter [Überwachen von Kapazitäten im Verwaltungsportal](service-admin-premium-monitor-portal.md).

Die Überwachungsfunktionen im Verwaltungsportal von Power BI sind so konzipiert, dass sie eine kurze Zusammenfassung der wichtigsten Kapazitätsmetriken bereitstellen. Für eine ausführlichere Überwachung sollten Sie die **Power BI Premium-Kapazitäts-Metrik-App** verwenden.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium-Kapazitäts-Metrik-App

Die [Power BI Premium-Kapazitäts-Metrik-App](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) ist eine für Kapazitätsadministratoren verfügbare Power BI-App und wird wie jede andere Power BI-App installiert. Sie enthält ein Dashboard und einen Bericht.

![Power BI Premium-Kapazitäts-Metrik-App](media/service-premium-capacity-manage/capacity-metrics-app.png)

Wenn die App geöffnet wird, wird das Dashboard geladen und präsentiert zahlreiche Kacheln, die eine aggregierte Ansicht aller Kapazitäten bilden, für die der Benutzer ein Kapazitätsadministrator ist. Das Dashboardlayout besteht aus fünf Hauptabschnitten:

- **Übersicht**: App-Version, Anzahl der Kapazitäten und Arbeitsbereiche
- **Systemübersicht**: Metriken für Arbeitsspeicher und CPU
- **Datasetübersicht**: Anzahl der Datasets, DQ/LC, Aktualisierung und Abfragemetriken
- **Dataflowübersicht**: Anzahl der Dataflows und Datasetmetriken
- **Übersicht über paginierte Berichte**: Aktualisierungs- und Anzeigemetriken

Auf den zugrunde liegenden Bericht, von dem aus die Dashboardkacheln angeheftet wurden, können Sie durch Klicken auf eine beliebige Dashboardkachel zugreifen. Er bietet eine ausführlichere Darstellung der einzelnen Dashboardabschnitte und unterstützt das interaktive Filtern. 

Zum Filtern können Slicer nach Datumsbereich, Kapazität, Arbeitsbereich und Workload festgelegt werden (Bericht, Dataset, Dataflow) und Elemente in Berichtsvisuals zum Kreuzfiltern der Berichtsseite ausgewählt werden. Die Kreuzfilterung ist eine leistungsstarke Technik zur Eingrenzung auf bestimmte Zeiträume, Kapazitäten, Arbeitsbereiche, Datasets usw. und kann bei der Analyse der Grundursache sehr hilfreich sein.

Ausführliche Informationen zu Dashboards und Berichtsmetriken in der App finden Sie unter [Überwachen von Premium-Kapazitäten über die App](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretieren von Metriken

Metriken sollten überwacht werden, um ein grundlegendes Verständnis von Ressourcenverwendung und Workloadaktivität zu gewinnen. Wenn bei der Kapazität Leistungsschwächen auftreten, müssen Sie wissen, welche Metriken Sie überwachen und welche Konsequenzen Sie ziehen können.

Im Idealfall sollten Abfragen innerhalb einer Sekunde durchgeführt werden, um Berichtsbenutzern Ergebnisse zu liefern, auf deren Basis sie optimal reagieren können, und einen höheren Abfragedurchsatz zu ermöglichen. Es ist in der Regel von geringerer Bedeutung, wenn die Ausführung von Hintergrundprozessen einschließlich Aktualisierungen länger dauert.

Im Allgemeinen können langsame Berichte ein Hinweis auf eine Kapazitätsüberlastung sein. Wenn Berichte nicht geladen werden können, ist dies ein Hinweis auf eine Kapazitätsüberlastung. In beiden Situationen könnte die Ursache auf zahlreiche Faktoren zurückzuführen sein, darunter:

- **Fehler bei Abfragen** weisen sicherlich auf unzureichenden Arbeitsspeicher hin, und dass ein Modell nicht in den Arbeitsspeicher geladen werden konnte. Der Power BI-Dienst versucht 30 Sekunden lang, ein Modell zu laden, bevor ein Fehler gemeldet wird.

- **Übermäßig lange Wartezeiten bei Abfragen** können aus verschiedenen Gründen auftreten:
  - Der Power BI-Dienst muss zuerst Modelle entfernen und dann das für die Abfrage gewünschte Modell laden (denken Sie daran, dass höhere Datasetentfernungsraten allein kein Anzeichen für eine Kapazitätsüberlastung sind, sofern sie nicht von langen Abfragewartezeiten begleitet werden, die auf eine Speicherüberlastung hinweisen).
  - Ladezeiten von Modellen (insbesondere das Warten auf das Laden eines großen Modells in den Arbeitsspeicher).
  - Abfragen mit langer Ausführungszeit.
  - Zu viele LC\DQ-Verbindungen (Überschreiten der Kapazitätsgrenzen).
  - CPU-Sättigung
  - Komplexe Berichtsentwürfe mit einer übermäßigen Anzahl von visuellen Elementen auf einer Seite (denken Sie daran, dass jede Visualisierung eine Abfrage ist).

- **Lange Abfragezeiten** können darauf hindeuten, dass Modellentwürfe nicht optimiert sind, insbesondere wenn mehrere Datasets in einer Kapazität aktiv sind und nur ein Dataset lange Abfragezeiten erzeugt. Dies deutet darauf hin, dass die Kapazitätsressourcen ausreichen und das fragliche Dataset suboptimal oder einfach langsam ist. Abfragen mit langer Ausführungszeit können problematisch sein, da sie den Zugriff auf Ressourcen blockieren können, die von anderen Prozessen benötigt werden.
- **Lange Aktualisierungswartezeiten** weisen auf unzureichenden Arbeitsspeicher hin, weil viele aktive Modelle Arbeitsspeicher belegen, oder dass eine problematische Aktualisierung andere Aktualisierungen blockiert (Überschreitung der Limits für parallele Aktualisierung).

Eine ausführlichere Erläuterung zur Verwendung der Metriken finden Sie im Artikel [Optimieren von Premium-Kapazitäten](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Danksagungen

Dieser Artikel wurde von Peter Myers, Data Platform MVP und unabhängiger BI-Experte bei [Bitwise Solutions](https://www.bitwisesolutions.com.au/), verfasst.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Optimieren von Premium-Kapazitäten](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Konfigurieren von Workloads in einer Premium-Kapazität](service-admin-premium-workloads.md)   

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

