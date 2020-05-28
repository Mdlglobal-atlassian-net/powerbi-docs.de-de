---
title: Überwachen von Power BI Premium-Kapazitäten mit der App „Power BI Premium-Kapazitätsmetriken“
description: Verwenden des Power BI-Verwaltungsportals und der Power BI Premium Capacity Metrics-App
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/18/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8bea8c2fc59deeb6aec4817f27d10371518f523e
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564318"
---
# <a name="monitor-premium-capacities-with-the-app"></a>Überwachen von Premium-Kapazitäten über die App

Die Überwachung Ihrer Kapazitäten ist entscheidend für das Treffen fundierter Entscheidungen zur optimalen Nutzung Ihrer Premium-Kapazitäten. Sie können die Kapazitäten im Verwaltungsportal oder mithilfe der App **Power BI Premium-Kapazitätsmetriken** überwachen. In diesem Artikel wird die Verwendung der Premium-Kapazitätsmetriken-App erläutert. Die App stellt ausführliche Informationen zur Leistung Ihrer Kapazitäten bereit. Einen allgemeineren Überblick durchschnittlicher Nutzungsmetriken der letzten sieben Tage finden Sie im Verwaltungsportal. Weitere Informationen zur Überwachung im Portal finden Sie unter [Monitor Premium capacities in the Admin portal (Überwachung von Premium-Kapazitäten im Verwaltungsportal)](service-admin-premium-monitor-portal.md).

Die App erhält regelmäßige Updates mit neuen Features und Funktionalitäten. Stellen Sie sicher, dass Sie die neueste Version verwenden. Wenn eine neue Version verfügbar ist, erhalten Sie eine [Benachrichtigung](../connect-data/service-template-apps-install-distribute.md#update-a-template-app).

> [!IMPORTANT]
> Wenn Ihre Power BI Premium-Kapazität einen hohen Ressourcenverbrauch aufweist, der zu Leistungs- oder Zuverlässigkeitsproblemen führt, erhalten Sie eine E-Mail-Benachrichtigung, damit Sie das Problem identifizieren und lösen können. Dies kann eine optimierte Methode zum Behandeln von Problemen mit überlasteten Kapazitäten darstellen. Weitere Informationen finden Sie unter [Benachrichtigungen zu Kapazität und Zuverlässigkeit](service-interruption-notifications.md#capacity-and-reliability-notifications).

## <a name="install-the-app"></a>Installieren der App

Informationen zum Installieren der App und Verbinden der Daten finden Sie unter [Herstellen einer Verbindung mit Power BI Premium Capacity Metrics](../connect-data/service-connect-to-pbi-premium-capacity-metrics.md). Alternativ können Sie [direkt die App aufrufen](https://go.microsoft.com/fwlink/?linkid=2114036).

## <a name="get-app-refresh-history"></a>Abrufen des Aktualisierungsverlaufs der App

So überprüfen Sie den Zeitpunkt der letzten Aktualisierung Ihrer Premium Capacity Metrics-App:

1. Rufen Sie den Arbeitsbereich auf, der mit der App installiert wurde.

   ![Wechseln Sie zum App-Arbeitsbereich.](media/service-admin-premium-monitor-capacity/settings-refresh-history.png)

1. Klicken Sie in der Datasetzeile auf **Aktualisierung planen**.

   ![Schaltfläche „Aktualisierung planen“](media/service-admin-premium-monitor-capacity/schedule-refresh.png)

   Die letzte Aktualisierung wird angezeigt. Klicken Sie auf **Aktualisierungsverlauf**, um geplante und abrufbare Aktualisierungen anzuzeigen.

   ![Letzte Aktualisierung](media/service-admin-premium-monitor-capacity/settings-last-refresh.png)

## <a name="monitor-capacities-with-the-app"></a>Überwachen von Kapazitäten über die App

Nachdem Sie die App installiert haben, können Sie Metriken zu den Kapazitäten in Ihrer Organisation anzeigen. Die App stellt ein Dashboard mit Metrikübersichten und detaillierten Metrikberichten bereit.

### <a name="dashboard"></a>Dashboard

Um ein Dashboard mit einer Übersicht über die Schlüsselmetriken für Kapazitäten anzuzeigen, für die Sie als Administrator zuständig sind, klicken Sie im Bereich **Dashboards** auf **Power BI Premium-Kapazitätsmetriken**. Ein Dashboard wird angezeigt.

![Metrik-App-Dashboard](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Das Dashboard umfasst die folgenden Metriken:

#### <a name="top"></a>Oben

| Metric | Beschreibung |
| --- | --- |
| Version | Die App-Version. | 
| Funktionen | Die Anzahl der Kapazitäten, für die Sie als Administrator zuständig sind. | 
| Arbeitsbereiche | Die Anzahl der Arbeitsbereiche in Ihren Kapazitäten, die Metriken melden.|
|||

#### <a name="system-summary"></a>Systemübersicht

| Metric | Beschreibung |
| --- | --- |
| Kapazität mit der höchsten CPU-Auslastung | Die Kapazität mit den häufigsten Fällen, in denen die CPU-Auslastung in den letzten sieben Tagen 80 % der Schwellenwerte überschritten hat. |
| Anzahl der Fälle mit der höchsten CPU-Auslastung | Die Anzahl der Fälle, in denen die benannte Kapazität in den letzten sieben Tagen 80 % der Schwellenwerte für die CPU-Auslastung überschritten hat. | 
| Kapazität mit maximaler Arbeitsspeicherauslastung | Die Kapazität mit den häufigsten Fällen, in denen in den letzten sieben Tagen der Maximalwert der Arbeitsspeicherauslastung erreicht wurde, unterteilt in Buckets von je drei Minuten.  |
| Anzahl der Fälle mit maximaler Arbeitsspeicherauslastung| Die Anzahl der Fälle, in denen die benannte Kapazität in den letzten sieben Tagen den Maximalwert der Arbeitsspeicherauslastung erreicht hat, unterteilt in Buckets von je drei Minuten. |
|||

#### <a name="dataset-summary"></a>Dataset Summary

| Metric | Beschreibung |
| --- | --- |
| Datasets | Die Gesamtzahl der Datasets über alle Arbeitsbereiche in Ihren Kapazitäten.|
| Durchschnittsgröße von Datasets (MB) | Die durchschnittliche Größe von Datasets in allen Arbeitsbereichen in Ihren Kapazitäten.|  
| Anzahl von durchschnittlich geladenen Datasets | Die durchschnittliche Anzahl der im Arbeitsspeicher geladenen Datasets. |  
| Datasets – durchschnittlich aktive Datasets (%)| Die durchschnittliche Anzahl der aktiven Datasets in den letzten sieben Tagen. Ein Dataset gilt als aktiv, wenn ein Benutzer in den letzten drei Minuten mit dem Visual interagiert hat. |
| CPU – Maximalwert für Datasets (%)| Der maximale CPU-Verbrauch nach Datasetworkload in den letzten sieben Tagen. |
| CPU – Durchschnittswert für Datasets (%)| Der durchschnittliche CPU-Verbrauch nach Datasetworkload in den letzten sieben Tagen. |
| Arbeitsspeicher – Durchschnittswert für Datasets (GB) | Der durchschnittliche Arbeitsspeicherverbrauch nach Datasetworkload in den letzten sieben Tagen. |
| Arbeitsspeicher – Maximalwert für Datasets (GB) | Der maximale Arbeitsspeicherverbrauch nach Datasetworkload in den letzten sieben Tagen.|
| Entfernte Datasets | Die Gesamtanzahl der aufgrund einer hohen Speicherauslastung entfernten Datasets. |
| Anzahl von DirectQuery-/Liveverbindungen mit hoher Auslastung| Die Anzahl der Fälle, in denen DirectQuery-/Liveverbindungen innerhalb der letzten sieben Tage 80 % der Schwellenwerte überschritten haben, unterteilt in Buckets von je drei Minuten. |
| Anzahl von DirectQuery-/Liveverbindungen mit maximaler Auslastung| Die häufigste Fälle, in denen DirectQuery-/Liveverbindungen 80 % überschritten haben, unterteilt in Buckets von je einer Stunde. |
| DirectQuery-/Liveverbindungen mit maximaler Auslastung | Die maximale Anzahl der Fälle, in denen DirectQuery-/Liveverbindungen innerhalb der letzten sieben Tage 80 % der Schwellenwerte überschritten haben, unterteilt in Buckets von je drei Minuten.|
| Maximale Vorkommnisse von DirectQuery-/Liveverbindungen – lokale Uhrzeit | Die UTC-Zeit, zu der DirectQuery-/Liveverbindungen den Wert von 80% am häufigsten innerhalb einer Stunde überschritten haben. |
| Aktualisierungen gesamt | Die Gesamtanzahl von Aktualisierungen in den letzten sieben Tagen. |
| Zuverlässigkeit der Aktualisierung (%) | Die Anzahl von erfolgreichen Aktualisierungen, geteilt durch die Gesamtanzahl von Aktualisierungen in den letzten sieben Tagen. |
| Durchschnittliche Dauer von Aktualisierungen (Minuten) | Der durchschnittliche Zeitraum für eine vollständige Aktualisierung. |
| Durchschnittliche Wartezeit bei Aktualisierungen (Minuten)| Der durchschnittliche Zeitraum vor dem Starten einer Aktualisierung. |
| Abfragen gesamt |  Die Gesamtanzahl der ausgeführten Abfragen in den letzten sieben Tagen. |
| Gesamtanzahl von Abfragen mit Wartezeit | Die Gesamtanzahl der Abfragen, die vor der Ausführung warten mussten. |
| Durchschnittliche Abfragedauer (ms) | Die durchschnittliche Dauer für die Ausführung von Abfragen. |
| Durchschnittliche Wartezeit für Abfragen (ms) | Die durchschnittliche Zeit, die Abfragen auf Systemressourcen warten, bevor sie ausgeführt werden. |
|||

#### <a name="dataflow-summary"></a>Dataflow Summary

| Metric | Beschreibung |
| --- | --- |
| Dataflows |  Die Gesamtzahl der Dataflows in allen Arbeitsbereichen in Ihren Kapazitäten.|
| Aktualisierungen gesamt | Die Gesamtanzahl von Aktualisierungen in den letzten sieben Tagen.|  
| Durchschnittliche Dauer von Aktualisierungen (Minuten) | Die Dauer für die Ausführung einer Aktualisierung. |
| Durchschnittliche Wartezeiten bei Aktualisierungen (Minuten) | Die Verzögerung zwischen der geplanten Zeit und dem tatsächlichen Start der Aktualisierung.|
| CPU – Maximalwert für Dataflows (%) | Der maximale CPU-Verbrauch nach Dataflowworkload in den letzten sieben Tagen. |
| CPU – Durchschnittswert für Dataflows (%) | Der durchschnittliche CPU-Verbrauch nach Dataflowworkload in den letzten sieben Tagen. |
| Arbeitsspeicher – Maximalwert für Dataflows (GB) | Der maximale Arbeitsspeicherverbrauch nach Dataflowworkload in den letzten sieben Tagen. |
| Arbeitsspeicher – Durchschnittswert für Dataflows (GB) | Der durchschnittliche Arbeitsspeicherverbrauch nach Dataflowworkload in den letzten sieben Tagen. |
|||

#### <a name="paginated-report-summary"></a>Paginated Report Summary

| Metric | Beschreibung |
| --- | --- |
| Paginated Reports |  Die Gesamtanzahl der paginierten Berichte in allen Arbeitsbereichen in Ihren Kapazitäten. |
| Ansichten gesamt | Die Gesamtzahl der Fälle, in denen alle Berichte von Benutzern angezeigt wurden. | 
| Zeilen gesamt | Die Gesamtanzahl der Datenzeilen in allen Berichten.|
| Total Time | Die Gesamtzeit in Millisekunden für alle Phasen (Abrufen, Verarbeiten und Rendern von Daten) für alle Berichte. |
| CPU – Maximalwert für paginierte Berichte (%) | Der maximale CPU-Verbrauch nach Workload für paginierte Berichte in den letzten sieben Tagen. |
| CPU – Durchschnittswert für paginierte Berichte (%) | Der durchschnittliche CPU-Verbrauch nach Workload für paginierte Berichte in den letzten sieben Tagen. |
| Arbeitsspeicher – Maximalwert für paginierte Berichte (GB) | Der maximale Arbeitsspeicherverbrauch nach Workload für paginierte Berichte in den letzten sieben Tagen. |
| Arbeitsspeicher – Durchschnittswert für paginierte Berichte (GB) | Der durchschnittliche Arbeitsspeicherverbrauch nach Workload für paginierte Berichte in den letzten sieben Tagen. |
|||

#### <a name="ai-summary"></a>KI-Zusammenfassung

| Metric | Beschreibung |
| --- | --- |
| AI Function Execution (KI-Funktionsausführung) | Die Gesamtzahl der Ausführungen in den letzten sieben Tagen. |
| AI Function Execution Reliability (%) (Zuverlässigkeit der KI-Funktionsausführung (%)) | Die Anzahl der erfolgreichen Ausführungen, geteilt durch die Gesamtzahl der Ausführungen in den letzten sieben Tagen. |
| CPU Max (%)| Der maximale CPU-Verbrauch nach KI-Workload in den letzten sieben Tagen. |
| Memory Max (GB) (Arbeitsspeicher maximal (GB)) | Maximale Arbeitsspeichernutzung durch die KI-Workload in den letzten sieben Tagen.|
| AI Function Execution Max Wait Time (MS) (Maximale Wartezeit bei KI-Funktionsausführung (ms)) | Maximal verstrichene Zeit vor Beginn der Ausführung. |
| AI Function Execution Average Wait Time (MS) (Mittlere Wartezeit bei KI-Funktionsausführung (ms))| Durchschnittlich verstrichene Zeit vor Beginn der Ausführung. |
| AI Function Execution Max Duration (MS) (Maximale Dauer bei KI-Funktionsausführung (ms)) | Der maximale Zeitraum für die vollständige Ausführung. |
| AI Function Execution Average Duration (MS) (Mittlere Dauer der KI-Funktionsausführung (ms))| Der mittlere Zeitraum für die vollständige Ausführung. |
| | |

### <a name="reports"></a>Berichte

Berichte bieten detaillierte Metriken. Um Berichte für die Kapazitäten anzuzeigen, für die Sie als Administrator zuständig sind, klicken Sie im Bereich **Berichte** auf **Power BI Premium-Kapazitätsmetriken**. Alternativ dazu können Sie auch im Dashboard auf eine Metrikzelle klicken, um zum zugrunde liegenden Bericht zu gelangen. 

Am unteren Rand des Berichts finden Sie fünf *Registerkarten*:

[**Datasets**](#datasets): Hier finden Sie ausführliche Metriken zur Integrität der Power BI-Datasets in Ihren Kapazitäten.
[**Paginierte Berichte**](#paginated-reports): Hier finden Sie ausführliche Metriken zur Integrität der paginierten Berichte in Ihren Kapazitäten.
[**Dataflows**](#dataflows): Hier finden Sie ausführliche Aktualisierungsmetriken für Dataflows in Ihren Kapazitäten.
[**KI**](#ai): Stellt detaillierte Metriken zum Status der in Ihren Kapazitäten verwendeten KI-Funktionen bereit.
[**Ressourcenverbrauch**](#resource-consumption): Hier finden Sie detaillierte Ressourcenmetriken, einschließlich hoher Auslastung von Arbeitsspeicher und CPU.
[**IDs und Info:** ](#ids-and-info) Hier finden Sie die Namen, IDs und Besitzer von Kapazitäten, Arbeitsbereichen und Workloads.

Auf jeder Registerkarte wird eine neue Seite geöffnet, auf der Sie die Metriken nach Kapazität und Datumsbereich filtern können. Wenn keine Filter ausgewählt sind, zeigt der Bericht standardmäßig die Metriken der letzten Woche für alle Kapazitäten an, die Metriken melden. 

### <a name="datasets"></a>Datasets

Die Seite „Datasets“ weist verschiedene *Bereiche* auf: **Aktualisierungen**, **Abfragedauer**, **Abfragewartezeiten** und **Datasets**. Verwenden Sie die Schaltflächen oben auf der Seite, um zu verschiedenen Bereichen zu navigieren.

#### <a name="refreshes-area"></a>Bereich „Refreshes“ (Aktualisierungen)

| Berichtsabschnitt | Metrics |
| --- | --- |
| Refreshes |  Gesamtanzahl: Die Gesamtanzahl aller Aktualisierungen für jedes Dataset.<br>  Zuverlässigkeit: Der Prozentsatz von Aktualisierungen, die für jedes Dataset ausgeführt wurden.<br>  Durchschnittliche Wartezeit: Die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start einer Datasetaktualisierung in Minuten.<br>  Maximale Wartezeit: Die maximale Wartezeit für das Dataset in Minuten.<br>  Durchschnittliche Dauer: Die durchschnittliche Dauer der Aktualisierung des Datasets in Minuten.<br>  Maximale Dauer: Die Dauer der Datasetaktualisierung mit der längsten Ausführungsdauer in Minuten. |
| Top-5-Datasets nach durchschnittlicher Dauer (Minuten) |  Die fünf Datasets mit der längsten durchschnittlichen Aktualisierungsdauer in Minuten. |
| Top-5-Datasets nach durchschnittlicher Wartezeit (Minuten) |  Die fünf Datasets mit der längsten durchschnittlichen Aktualisierungswartezeit in Minuten. |
| Stündliche Aktualisierungen und Arbeitsspeicherverbrauch (GB) |  Erfolgreiche Vorgänge, Fehler und Arbeitsspeicherverbrauch, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| Durchschnittliche stündliche Aktualisierungswartezeiten (Minuten) |  Die durchschnittliche Aktualisierungswartezeit, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. Mehrere Spitzen mit langen Aktualisierungswartezeiten weisen auf eine hohe Auslastung der Kapazität hin. |
|  |  |

#### <a name="query-durations-area"></a>Bereich „Query Durations“ (Abfragedauer)

| Berichtsabschnitt | Metrics |
| --- | --- |
| Abfragedauer |  Die Daten in diesem Bereich sind nach Datasets, Arbeitsbereich und in Buckets von je einer Stunde in den letzten sieben Tagen aufgeteilt.<br>  Gesamt: Die Gesamtzahl der Abfragen, die für das Dataset ausgeführt werden.<br>  Durschnitt: die durchschnittliche Abfragedauer für das Dataset in Millisekunden<br>  Maximal: Die Dauer der Abfrage mit der längsten Ausführungsdauer im Dataset in Millisekunden.|
| Verteilung der Abfragedauer |  Das Histogramm der Abfragedauer ist nach der Dauer (in Millisekunden) in die folgenden Kategorien unterteilt: <= 30 ms, 30–100 ms, 100–300 ms, 300 ms bis 1 s, 1–3 s, 3–10 s, 10–30 s und > 30 s. Lange Ausführungsdauern und lange Wartezeiten sind ein Hinweis auf sich erschöpfende Kapazität. Es kann aber auch bedeuten, dass ein einzelnes Dataset Probleme verursacht und weitere Untersuchungen erforderlich sind. |
| Top 5 Datasets nach durchschnittlicher Dauer |  Die fünf Datasets mit der längsten durchschnittlichen Abfragedauer in Millisekunden. |
| Stündliche Verteilungen der Abfragedauer |  Abfrageanzahl und durchschnittliche Dauer (in Millisekunden) im Vergleich zum Arbeitsspeicherverbrauch in GB, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| DirectQuery-/Liveverbindungen (> 80 % Auslastung) |  Die Häufigkeit, mit der eine DirectQuery-Verbindung oder Liveverbindung eine CPU-Auslastung von 80% überschritten hat, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
|  |  |

#### <a name="query-waits-area"></a>Bereich „Query Waits“ (Abfragewartezeit)

| Berichtsabschnitt | Metrics |
| --- | --- |
| Abfragewartezeiten |  Die Daten in diesem Bereich sind nach Datasets, Arbeitsbereich und in Buckets von je einer Stunde in den letzten sieben Tagen aufgeteilt.<br>  Gesamt: Die Gesamtzahl der Abfragen, die für das Dataset ausgeführt werden.<br>  Anzahl der Wartevorgänge: Die Anzahl von Abfragen im Dataset, die vor der Ausführung auf Systemressourcen gewartet haben.<br>  Durschnitt: Die durchschnittliche Abfragewartezeit für das Dataset in Millisekunden.<br>  Maximal: Die Dauer der Abfrage mit der längsten Wartezeit für das Dataset in Millisekunden.|
| Top 5 Datasets nach durchschnittlicher Wartezeit |  Die fünf Datasets mit der längsten durchschnittlichen Wartezeit bis zum Start der Ausführung einer Abfrage in Millisekunden. |
| Wartezeitverteilungen |  Das Histogramm der Abfragedauer ist nach der Dauer (in Millisekunden) in die folgenden Intervallkategorien unterteilt: <= 50 ms, 50–100 ms, 100–200 ms, 200–400 ms, 400 ms bis 1 s, 1–5 s und > 5 s. |
| Stündliche Wartezeitverteilungen für Abfragen |  Anzahl von Wartevorgängen und durchschnittliche Wartezeit für Abfragen (in Millisekunden) im Vergleich zum Arbeitsspeicherverbrauch in GB, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
|  |  |

#### <a name="datasets-area"></a>Bereich „Datasets“

| **Berichtsabschnitt** | **Metriken** |
| --- | --- |
| Datasetgrößen  |  Maximale Größe: Die maximale Größe des Datasets in MB für den angezeigten Zeitraum. |
| Anzahl von entfernten Datasets |  Gesamt: Gesamtzahl der *entfernten* Datasets für jede Kapazität. Wenn eine Kapazität Arbeitsspeicherauslastung unterliegt, entfernt der Knoten mindestens ein Dataset aus dem Arbeitsspeicher. Datasets, die inaktiv sind (ohne derzeit ausgeführten Abfrage- oder Aktualisierungsvorgang), werden zuerst entfernt. Anschließend orientiert sich die Entfernungsreihenfolge an den „am seltensten verwendeten“ Datasets.|
| Anzahl von stündlich geladenen Datasets |  Die Anzahl der in den Arbeitsspeicher geladenen Datasets im Vergleich zum Arbeitsspeicherverbrauch in GB, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| Entfernte Datasets und Arbeitsspeicherverbrauch pro Stunde |  Entfernte Datasets im Vergleich zum Arbeitsspeicherverbrauch in GB, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| Prozentsätze des verbrauchten Arbeitsspeichers |  Gesamtanzahl der aktiven Datasets im Arbeitsspeicher, angegeben als Prozentsatz des gesamten Arbeitsspeichers. Das Delta zwischen den aktiven und allen definierten Datasets, die entfernt werden können. Angabe in Stunden für die letzten sieben Tage. |
|  |  |

### <a name="paginated-reports"></a>Paginated Reports

| **Berichtsabschnitt** | **Metriken** |
| --- | --- |
| Verwendung gesamt |  Aufrufe gesamt: Die Häufigkeit der Aufrufe des Berichts durch Benutzer.<br>  Zeilenanzahl: Die Anzahl von Datenzeilen im Bericht.<br>  Abrufe (durchschn.): die durchschnittlich benötigte Zeit in Millisekunden zum Abrufen von Daten für den Bericht. Eine lange Dauer kann auf langsame Abfragen oder andere Probleme mit der Datenquelle hinweisen. <br>  Verarbeitung (durchschn.): Die durchschnittlich benötigte Zeit zum Verarbeiten von Daten für einen Bericht in Millisekunden.<br> Rendering (durchschn.): Die durchschnittlich benötigte Zeit zum Rendern eines Berichts im Browser in Millisekunden.<br>  Gesamtzeit: Die für alle Phasen des Berichts benötigte Zeit in Millisekunden. |
| Top 5 Berichte nach durchschnittlicher Datenabrufzeit |  Die fünf Berichte mit der längsten durchschnittlichen Datenabrufzeit in Millisekunden. |
| Top 5 Berichte nach durchschnittlicher Berichtverarbeitungsdauer |  Die fünf Berichte mit der längsten durchschnittlichen Berichtverarbeitungsdauer in Millisekunden. |
| Stündliche Ergebnisse |  Erfolgreiche Vorgänge, Fehler und Arbeitsspeicherverbrauch, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| Stündliche Dauer |  Die Dauer des Datenabrufs im Vergleich zur Verarbeitungs- und Renderingdauer, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
|  |  |

### <a name="dataflows"></a>Dataflows

| **Berichtsabschnitt** | **Metriken** |
| --- | --- |
| Refreshes |  Gesamt: Die Gesamtanzahl aller Aktualisierungen für jeden Dataflow.<br>  Zuverlässigkeit: Der Prozentsatz von Aktualisierungen, die für jeden Datenfluss ausgeführt wurden.<br>  Durchschnittliche Wartezeit: Die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start einer Dataflowaktualisierung in Minuten.<br>  Maximale Wartezeit: Die maximale Wartezeit für den Dataflow in Minuten.<br>  Durchschnittliche Dauer: Die durchschnittliche Dauer für die Aktualisierung des Dataflows in Minuten.<br>  Maximale Dauer: Die Dauer der Dataflowaktualisierung mit der längsten Ausführungsdauer in Minuten. |
| Top-5-Dataflows nach durchschnittlicher Aktualisierungsdauer |  Die fünf Dataflows mit der längsten durchschnittlichen Aktualisierungsdauer in Minuten. |
| Top-5-Dataflows nach durchschnittlicher Wartezeit |  Die fünf Dataflows mit der längsten durchschnittlichen Aktualisierungswartezeit in Minuten. |
| Durchschnittliche stündliche Aktualisierungswartezeiten |  Die durchschnittliche Aktualisierungswartezeit, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. Mehrere Spitzen mit langen Aktualisierungswartezeiten weisen auf eine hohe Auslastung der Kapazität hin. |
| Stündliche Aktualisierungen und Arbeitsspeicherverbrauch |  Erfolgreiche Vorgänge, Fehler und Arbeitsspeicherverbrauch, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
|  |  |

### <a name="ai"></a>KI

| **Berichtsabschnitt** | **Metriken** |
| --- | --- |
| KI-Arbeitsspeicherverbrauch | Arbeitsspeicherverbrauch in GB, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| AI Function Execution Average Wait Time (MS) (Stündliche KI-Funktionsausführung und mittlere Wartezeit (ms)) | KI-Ausführungen und durchschnittliche Wartezeit in Millisekunden, unterteilt in Buckets von je einer Stunde, Angabe in UTC-Zeit. |
| Verwendung gesamt | Gesamtzahl: Anzahl von KI-Funktionen in einem Arbeitsbereich oder Datenfluss. <br> System Reliability (Zuverlässigkeit des Systems): Der Prozentsatz von Ausführungen, die abgeschlossen wurden.<br> Avg. Wartezeit: Die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start einer Ausführung in Millisekunden.<br> Maximale Wartezeit: Die maximale Wartezeit in Millisekunden.<br> Avg. Dauer: Die durchschnittliche Dauer einer Ausführung in Millisekunden.<br> Maximale Dauer: Die Dauer der Abfrage mit der längsten Ausführungsdauer in Millisekunden.<br> Avg Total Size (Mittlere Gesamtgröße): Die durchschnittliche Größe in Byte der eingehenden und ausgehenden Daten für die KI-Funktion. |
| | |

### <a name="resource-consumption"></a>Ressourcenverbrauch

| **Berichtsabschnitt** | **Metriken** |
| --- | --- |
| CPU-Verbrauch |  Maximale CPU-Auslastung pro Stunde nach Arbeitsauslastung als Prozentsatz der gesamten CPU-Kapazität. Angabe in Stunden für die letzten sieben Tage. |
| Arbeitsspeicherverbrauch |  Der maximale Arbeitsspeicherverbrauch in GB pro Stunde nach Arbeitsauslastung (durchgezogene Linien) im Vergleich zu Arbeitsauslastungsgrenzen (gepunktete Linie). Angabe in Stunden für die letzten sieben Tage. |
|  |  |

### <a name="ids-and-info"></a>IDs und Info

Die Registerkarte **IDs und Info** enthält die Bereiche **Kapazitäten**, **Arbeitsbereiche**, **Datasets**, **Paginierte Berichte** und **Dataflows**.

#### <a name="capacities-area"></a>Bereich „Kapazitäten“

| Berichtsabschnitt | Metrics |
| --- | --- |
| SKU- und Workloadinformationen | Die SKU- und Workloadeinstellungen für die Kapazität. |
| Administrators | Die Namen der Administratoren für die Kapazität. |
|||

#### <a name="workspaces-area"></a>Bereich „Arbeitsbereiche“

| Berichtsabschnitt | Metrics |
| --- | --- |
| Arbeitsbereiche | Die Namen und IDs für alle Arbeitsbereiche. |
|||

#### <a name="datasets-area"></a>Bereich „Datasets“

| Berichtsabschnitt | Metrics |
| --- | --- |
| Datasets | Die Arbeitsbereichsnamen und IDs für alle Datasets. |
|||

#### <a name="paginated-reports-area"></a>Bereich „Paginierte Berichte“

| Berichtsabschnitt | Metrics |
| --- | --- |
| Paginated Reports | Die Namen, Arbeitsbereichsnamen und IDs für alle paginierten Berichte. |
|||

#### <a name="dataflows-area"></a>Bereich „Dataflows“

| Berichtsabschnitt | Metrics |
| --- | --- |
| Dataflows | Die Dataflownamen, Arbeitsbereichsnamen und IDs für alle Dataflows. |
|||

## <a name="monitor-power-bi-embedded-capacity"></a>Überwachen einer Power BI Embedded-Kapazität

Sie können die Power BI Premium-Kapazitätsmetriken-App zum Überwachen von Kapazitäten mit *A-SKU* in Power BI Embedded verwenden. Diese Kapazitäten werden im Bericht angezeigt, sofern Sie ein Administrator der Kapazität sind. Die Aktualisierung des Berichts ist jedoch nur erfolgreich, wenn Sie Power BI bestimmte Berechtigungen für Ihre A-SKUs erteilen:

1. Öffnen Sie Ihre Kapazität im Azure-Portal.

1. Klicken Sie auf **Zugriffssteuerung (IAM)** , und fügen Sie die App **Power BI Premium** zur Rolle „Leser“ hinzu. Wenn Sie den Namen der App nicht finden, können Sie sie auch per Client-ID hinzufügen: `cb4dc29f-0bf4-402a-8b30-7511498ed654`.

    ![Berechtigungen für Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Sie können die Nutzung der Power BI Embedded-Kapazität in der App oder im Azure-Portal überwachen, nicht jedoch im Power BI-Verwaltungsportal.


## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Optimieren von Power BI Premium-Kapazitäten](service-premium-capacity-optimize.md)
