---
title: Überwachen von Power BI Premium-Kapazitäten mithilfe des Verwaltungsportals
description: Verwenden des Power BI-Verwaltungsportals zum Überwachen von Premium-Kapazitäten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 941e67984405392a76a7302d297479bbeccb7842
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83137131"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Überwachen von Kapazitäten im Verwaltungsportal

Im Verwaltungsportal sehen Sie im Bereich **Kapazitätseinstellungen** auf der Registerkarte **Integrität** eine Zusammenfassung der Metriken für Ihre Kapazität und aktivierten Workloads.  

![Registerkarte „Kapazitätsintegrität“ im Portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Für umfassendere Metriken können Sie die App [Power BI Premium-Kapazitätsmetriken](service-admin-premium-monitor-capacity.md) verwenden. Sie bietet Drilldown- und Filterfunktionen sowie äußerst detaillierte Metriken für nahezu alle Aspekte, die sich auf die Kapazitätsleistung auswirken. Weitere Informationen finden Sie unter [Überwachen von Premium-Kapazitäten über die App](service-admin-premium-monitor-capacity.md).

> [!IMPORTANT]
> Wenn Ihre Power BI Premium-Kapazität einen hohen Ressourcenverbrauch aufweist, der zu Leistungs- oder Zuverlässigkeitsproblemen führt, erhalten Sie eine E-Mail-Benachrichtigung, damit Sie das Problem identifizieren und lösen können. Dies kann eine optimierte Methode zum Behandeln von Problemen mit überlasteten Kapazitäten darstellen. Weitere Informationen finden Sie unter [Benachrichtigungen zu Kapazität und Zuverlässigkeit](service-interruption-notifications.md#capacity-and-reliability-notifications).


## <a name="system-metrics"></a>Systemmetriken

Ganz oben auf der Registerkarte **Integrität** bieten die Angaben zu CPU-Auslastung und Speicherauslastung einen schnellen Überblick über die wichtigsten Metriken für die Kapazität. Diese Metriken sind kumulativ und enthalten alle aktivierten Workloads für die Kapazität.

| **Metrik** | **Beschreibung** |
| --- | --- |
| CPU-AUSLASTUNG | Durchschnittliche CPU-Auslastung als Prozentsatz der gesamten verfügbaren CPU-Kapazität. |
| SPEICHERAUSLASTUNG | Durchschnittliche Speicherauslastung in Gigabytes (GB).|

## <a name="workload-metrics"></a>Workloadmetriken

Für jede für die Kapazität aktivierte Workload werden die CPU-Auslastung und die Speicherauslastung angezeigt.

| **Metrik** | **Beschreibung** |
| --- | --- |
| CPU-AUSLASTUNG | Durchschnittliche CPU-Auslastung als Prozentsatz der gesamten verfügbaren CPU-Kapazität. |
| SPEICHERAUSLASTUNG | Durchschnittliche Speicherauslastung in Gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Detaillierte Workloadmetriken

Jede Workload verfügt über weitere Metriken. Je nach Workload werden unterschiedliche Typen von Metriken angezeigt. Klicken Sie auf den Pfeil nach unten, um detaillierte Metriken für eine Workload anzuzeigen.

![Pfeil nach unten für detaillierte Workloadmetriken](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Dataflows

##### <a name="dataflow-operations"></a>Dataflowvorgänge

| **Metrik** | **Beschreibung** |
| --- | --- |
| Gesamtanzahl | Die Gesamtanzahl aller Aktualisierungen für jeden Dataflow. |
| Anzahl erfolgreicher Vorgänge | Gesamtzahl aller erfolgreichen Aktualisierungen für jeden Dataflow.|
| Durchschnittliche Dauer (Min.) | die durchschnittliche Dauer in Minuten für die Aktualisierung des Datenflusses |
| Maximale Dauer (Min.) | Die Dauer der Dataflowaktualisierung mit der längsten Ausführungsdauer in Minuten. |
| Durchschnittliche Wartezeit (Min.) | Die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start einer Dataflowaktualisierung in Minuten. |
| Maximale Wartezeit (Min.) | Die maximale Wartezeit für den Dataflow in Minuten.  |

#### <a name="datasets"></a>Datasets

##### <a name="refresh"></a>Aktualisieren

| **Metrik** | **Beschreibung** |
| --- | --- |
| Gesamtanzahl | Die Gesamtanzahl aller Aktualisierungen für jedes Dataset. |
| Anzahl erfolgreicher Vorgänge | Gesamtzahl aller erfolgreichen Aktualisierungen für jedes Dataset. |
| Anzahl Fehler | Gesamtzahl aller fehlerhaften Aktualisierungen für jedes Dataset. |
| Erfolgsrate  | Anzahl der erfolgreichen Aktualisierungen geteilt durch die Gesamtzahl der Aktualisierungen. Misst die Zuverlässigkeit. |
| Durchschnittliche Dauer (Min.) | Die durchschnittliche Dauer der Aktualisierung des Datasets in Minuten.  |
| Maximale Dauer (Min.) | Die Dauer der Datasetaktualisierung mit der längsten Ausführungsdauer in Minuten. |
| Durchschnittliche Wartezeit (Min.) | Die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start einer Datasetaktualisierung in Minuten. |
| Maximale Wartezeit (Min.) | Die maximale Wartezeit für das Dataset in Minuten. |

##### <a name="query"></a>Abfrage

| **Metrik** | **Beschreibung** |
| --- | --- |
| Gesamtanzahl | Die Gesamtzahl der Abfragen, die für das Dataset ausgeführt werden. |
| Durchschnittliche Dauer (ms) |die durchschnittliche Abfragedauer für das Dataset in Millisekunden|
| Maximale Dauer (ms) |Die Dauer der Abfrage mit der längsten Ausführungsdauer im Dataset in Millisekunden. |
| Durchschnittliche Wartezeit (ms) |Die durchschnittliche Abfragewartezeit für das Dataset in Millisekunden. |
| Maximale Wartezeit (ms) |Die Dauer der Abfrage mit der längsten Wartezeit für das Dataset in Millisekunden. |

##### <a name="eviction"></a>Entfernung

| **Metrik** | **Beschreibung** |
| --- | --- |
| Modellanzahl | Gesamtzahl der entfernten Datasets für diese Kapazität. Wenn eine Kapazität Arbeitsspeicherauslastung unterliegt, entfernt der Knoten mindestens ein Dataset aus dem Arbeitsspeicher. Datasets, die inaktiv sind (ohne derzeit ausgeführten Abfrage- oder Aktualisierungsvorgang), werden zuerst entfernt. Anschließend orientiert sich die Entfernungsreihenfolge an den „am seltensten verwendeten“ Datasets. |

#### <a name="paginated-reports"></a>Paginated Reports

##### <a name="report-execution"></a>Berichtsausführung

| **Metrik** | **Beschreibung** |
| --- | --- |
| Ausführungsanzahl  | Anzahl der Ausführungen und Aufrufe des Berichts durch Benutzer.|

##### <a name="report-usage"></a>Berichtsnutzung

| **Metrik** | **Beschreibung** |
| --- | --- |
| Anzahl erfolgreicher Vorgänge | Anzahl der Aufrufe des Berichts durch einen Benutzer. |
| Anzahl Fehler |Anzahl der Aufrufe des Berichts durch einen Benutzer.|
| Zeilenanzahl |Die Anzahl von Datenzeilen im Bericht. |
| Dauer des Datenabrufs (ms) |die durchschnittlich benötigte Zeit in Millisekunden zum Abrufen von Daten für den Bericht. Eine lange Dauer kann auf langsame Abfragen oder andere Probleme mit der Datenquelle hinweisen.  |
| Verarbeitungsdauer (ms) |Die durchschnittlich benötigte Zeit zum Verarbeiten von Daten für einen Bericht in Millisekunden. |
| Renderingdauer (ms) |Die durchschnittlich benötigte Zeit zum Rendern eines Berichts im Browser in Millisekunden. |

> [!NOTE]
> Ausführliche Metriken für den **KI**-Workload sind noch nicht verfügbar.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Überwachung von Power BI Premium-Kapazitäten kennengelernt haben, können Sie sich über das Optimieren von Kapazitäten informieren.

> [!div class="nextstepaction"]
> [Optimieren von Power BI Premium-Kapazitäten](service-premium-capacity-optimize.md)
