---
title: Power BI Premium-Metrik-App
description: Erfahren Sie, wie Sie die Power BI Premium-Metrik-App zur Verwaltung und Problembehandlung Ihrer Premium-Kapazität verwenden.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/17/2020
LocalizationGroup: Premium
ms.openlocfilehash: 80f870f1657e629786cec299484f3b3c97609e79
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637944"
---
# <a name="power-bi-premium-metrics-app"></a>Power BI Premium-Metrik-App

Sie können die **Power BI Premium-Metrik-App** verwenden, um die Integrität und Kapazität Ihres Power BI Premium-Abonnements zu verwalten. Mit dem Feature **Capacity Health Center** können Administratoren die Indikatoren, die zur Überwachung der Integrität der Premium-Kapazität dienen, anzeigen und mit ihnen interagieren. Die Metrik-App besteht aus der Startseite, die als **Capacity Health Center** bezeichnet wird, sowie Details zu drei wichtigen Metriken:

* Aktiver Arbeitsspeicher
* Abfragewartevorgänge
* Aktualisierungswartevorgänge

![Die Power BI Premium-Metrik-App](media/service-premium-metrics-app/premium-metrics-app-00.png)

In den folgenden Abschnitte werden die Startseite sowie die drei Metrikberichtsseiten detailliert beschrieben. 





## <a name="premium-capacity-health-center"></a>Premium – Capacity Health Center

Wenn Sie die **Power BI Premium-Metrik-App** öffnen, wird das **Capacity Health Center** angezeigt, das eine Übersicht über die Integrität Ihrer Power BI Premium-Kapazität bietet.

![Das Capacity Health Center in der Premium-Metrik-App](media/service-premium-metrics-app/premium-metrics-app-01.png)

Auf der Startseite können Sie die Power BI Premium-Kapazität auswählen, die Sie anzeigen möchten, falls Ihre Organisation über mehrere Premium-Abonnements verfügt. Um eine Premium-Kapazität anzuzeigen, wählen Sie im oberen Bereich der Seite das Dropdownmenü **Kapazität auswählen, um zugehörige Metriken anzuzeigen** aus.

Die drei KPIs zeigen die aktuelle Integrität der ausgewählten Premium-Kapazität an, basierend auf den Einstellungen der einzelnen KPIs. 

Um Details zu jedem KPI anzuzeigen, klicken Sie im unteren Bereich des entsprechenden KPI-Visuals auf die Schaltfläche **Erkunden**. Daraufhin wird die zugehörige Detailseite angezeigt. In den folgenden Abschnitten werden die einzelnen KPIs und die entsprechenden Details beschrieben.

## <a name="the-active-memory-metric"></a>Die Metrik für aktiven Arbeitsspeicher

Die Metrik **Aktiver Arbeitsspeicher** gehört zur Kategorie *Kapazitätsplanung* und ist ein guter Integritätsindikator, mit dem Sie den Ressourcenverbrauch Ihrer Kapazität bewerten und die Kapazität bei Bedarf anpassen können, um den Kapazitätsumfang zu planen. 

![Die KPI für aktiven Arbeitsspeicher](media/service-premium-metrics-app/premium-metrics-app-02.png)

Im **aktiven Arbeitsspeicher** werden Datasets verarbeitet, die derzeit verwendet und daher nicht entfernt werden, wenn weiterer Arbeitsspeicher benötigt wird. Die Metrik für aktiven Arbeitsspeicher gibt an, ob Ihre Kapazität zusätzliche Lasten verarbeiten kann oder ob die aktuelle Last Ihre Kapazität bereits ausschöpft oder sogar überschreitet. Derzeit genutzter Arbeitsspeicher steht nicht zur Unterstützung weiterer Aktualisierungsvorgänge und Abfragen zur Verfügung. 

Die KPI **Aktiver Arbeitsspeicher** misst, wie häufig der aktive Arbeitsspeicher der Kapazität den Schwellenwert von 70 % um den Faktor 50 überschritten hat (der Marker ist auf 30 % in den letzten sieben Tagen festgelegt). Dies deutet darauf hin, dass die Kapazität sich einem Punkt nähert, an dem Benutzer möglicherweise Leistungsprobleme bei Abfragen bemerken.

Das in diesem Abschnitt gezeigte Visual (in Form eines Messgeräts) zeigt, dass in den sieben Tagen seit der letzten Aktualisierung des Berichts die Kapazität den Schwellenwert von 70 % viermal überschritten hat, aufgeteilt in Zeitspannen von je einer Stunde. Der Maximalwert des Visuals – 168 – repräsentiert die letzten sieben Tage in Stunden.

Um Details zur KPI für aktiven Arbeitsspeicher zu erhalten, klicken Sie auf die Schaltfläche **Erkunden**. Damit wird eine Berichtsseite geöffnet, die Visualisierungen der Metrikdetails sowie in der rechten Spalte einen Leitfaden zur Problembehandlung anzeigt. 

Auf der Berichtsseite werden zwei Szenarien erläutert, die Sie durch Auswahl von **Szenario 1** bzw. **Szenario 2** anzeigen können. 

![Detailseite zum aktiven Arbeitsspeicher](media/service-premium-metrics-app/premium-metrics-app-03.png)

Die Leitfäden zur Problembehandlung, die jedem Szenario zugeordnet sind, bieten detaillierte Erläuterungen zur Bedeutung der Metriken, sodass Sie den Status der Kapazität besser verstehen und erfahren, wie Sie vorgehen können, um Probleme zu minimieren. 

Diese beiden Szenarien werden in den folgenden Abschnitten beschrieben.

### <a name="scenario-one---current-load-is-too-high"></a>Szenario 1: zu hohe aktuelle Last 

Um zu ermitteln, ob genügend Arbeitsspeicher vorhanden ist, damit die Kapazität ihre Workloads abschließen kann, sehen Sie sich das erste Visual auf der Seite an: **A: Prozentsätze des verbrauchten Arbeitsspeichers**. Dieses Visual zeigt den Arbeitsspeicher an, der von Datasets genutzt wird, die derzeit aktiv verarbeitet werden und daher nicht entfernt werden können.

Der Alarmschwellenwert – die gestrichelte rote Linie – kennzeichnet Vorkommen eines Arbeitsspeicherverbrauchs von 90 %.

Der Warnschwellenwert – die gestrichelte gelbe Linie – kennzeichnet Vorkommen eines Arbeitsspeicherverbrauchs von 70 %. 

Die gestrichelte schwarze Linie zeigt die Trendlinie des Arbeitsspeicherverbrauchs an, basierend auf dem aktuellen Arbeitsspeicherverbrauch der Kapazität auf der Zeitskala des Diagramms.

Wenn der aktive Arbeitsspeicher den Alarmschwellenwert (gestrichelte rote Linie) und die Trendlinie (gestrichelte schwarze Linie) häufig überschreitet, deutet dies auf eine Auslastung der Arbeitsspeicherkapazität hin. Diese kann dazu führen, dass in diesem Zeitraum keine weitere Datasets in den Arbeitsspeicher geladen werden können. 

In solchen Fällen sollten Sie die anderen Diagramme auf der Seite sorgfältig untersuchen, um herauszufinden, wann und warum so häufig so viel Arbeitsspeicher verbraucht wird. So können Sie auch ermitteln, welche Lastenausgleichs- oder Optimierungsaktionen Sie durchführen können oder ob die Kapazität zentral hochskaliert werden muss. 

Das zweite Visual auf der Seite, **B: Stündlich geladene aktive Datasets**, zeigt in Zeitspannen von je einer Stunde an, wie häufig die maximale Anzahl von Datasets in den Arbeitsspeicher geladen wurde. 

Das dritte Visual, **C: Warum befinden sich Datasets im Arbeitsspeicher**, ist eine Tabelle, in der die Datasets nach Arbeitsbereichsname, Datasetname und unkomprimierter Größe der Datasets im Arbeitsspeicher aufgelistet werden. Hier wird der Grund erläutert, aus dem die einzelnen Datasets in den Arbeitsspeicher geladen wurden (z. B. aufgrund einer Aktualisierung oder einer Abfrage oder beidem).

#### <a name="diagnosing-scenario-one"></a>Diagnose für Szenario 1

Eine konsistente hohe Nutzung des aktiven Arbeitsspeichers kann dazu führen, dass aktiv verwendete Datasets zwangsweise entfernt oder keine neuen Datasets geladen werden. Die folgenden Schritte können bei der Problemdiagnose helfen.

1. Sehen Sie sich das Diagramm *A: Prozentsätze des verbrauchten Arbeitsspeichers* an.

    **a.** Wenn Diagramm A zeigt, dass der Alarmschwellenwert (90 %) mehrmals und/oder über mehrere Stunden hinweg überschritten wird, steht für Ihre Kapazität zu häufig zu wenig Arbeitsspeicher zur Verfügung. Im Diagramm unten sehen Sie, dass der Warnschwellenwert (70 %) viermal überschritten wurde.

    ![Diagramm A: Prozentsätze des verbrauchten Arbeitsspeichers](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** Diagramm *B: Stündlich geladene aktive Datasets* zeigt in Zeitspannen von je einer Stunde die maximale Anzahl von eindeutigen Datasets an, die in den Arbeitsspeicher geladen wurden. Bei Auswahl eines Balkens im Visual erfolgt eine Kreuzfilterung der Gründe, aus denen sich die Datasets in diesem Arbeitsspeichervisual befinden.  

    ![Diagramm B: verbrauchter Arbeitsspeicher pro Stunde](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** In der Tabelle **Warum befinden sich Datasets im Arbeitsspeicher** sehen Sie eine Liste der Datasets, die in den Arbeitsspeicher geladen wurden. Sortieren Sie die Tabelle nach *Datasetgröße (MB)* , um die Datasets hervorzuheben, die den meisten Arbeitsspeicher einnehmen. Kapazitätsvorgänge werden entweder als *interaktiv* oder *im Hintergrund* klassifiziert. Zu den interaktiven Vorgängen gehören Renderinganforderungen und die Reaktion auf Benutzerinteraktionen (Filtern, Q&A-Abfragen usw.). Die Gesamtanzahl von Abfragen und Aktualisierungen gibt Aufschluss darüber, ob mehr interaktive Vorgänge (Abfragen) oder mehr Hintergrundvorgänge (Aktualisierungen) im Dataset ausgeführt werden. Es ist wichtig zu verstehen, dass interaktive Vorgänge immer Vorrang vor Hintergrundvorgängen haben, um die bestmögliche Benutzererfahrung sicherzustellen. Wenn nicht ausreichend Ressourcen vorhanden sind, werden Hintergrundvorgänge einer Warteschlange hinzugefügt und dann verarbeitet, wenn wieder Ressourcen freigegeben wurden. Hintergrundvorgänge, wie z. B. Datasetaktualisierungen und KI-Funktionen, können vom Power BI-Dienst mitten im Vorgang angehalten und einer Warteschlange hinzugefügt werden.
    
    ![Tabelle C: Liste von Datasets](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>Abhilfemaßnahmen in Szenario 1

Um die Probleme in Szenario 1 zu beheben, können Sie folgende Schritte ausführen:

1. **Skalieren Sie die Kapazität zentral hoch**: Durch zentrales Hochskalieren auf die nächste SKU steht doppelt so viel Arbeitsspeicher zur Verfügung wie in der aktuellen SKU. So können Sie die aktuelle Speicherauslastung durch die Kapazität verringern.

2. **Verschieben Sie Datasets in eine andere Kapazität**: Wenn Sie über eine andere Kapazität mit mehr Arbeitsspeicher verfügen, können Sie Arbeitsbereiche mit größeren Datasets in diese Kapazität verschieben.


### <a name="scenario-two---future-load-will-exceed-limits"></a>Szenario 2: Überschreitung der Grenzwerte durch zukünftige Lasten

Um zu ermitteln, ob genügend Arbeitsspeicher vorhanden ist, damit die Kapazität ihre Workloads abschließen kann, sehen Sie sich das Visual **A: Prozentsätze des verbrauchten Arbeitsspeichers** oben auf der Seite an. Dieses Visual stellt den Arbeitsspeicher dar, der von Datasets genutzt wird, die derzeit aktiv verarbeitet werden und daher nicht entfernt werden können. Die gestrichelte schwarze Linie hebt Trends hervor. Wenn bei einer Kapazität eine Speicherauslastung auftritt, zeigt dieses Visual, dass die Trendlinie für den Arbeitsspeicher (gestrichelte schwarze Linie) nach oben weist. Dies bedeutet, dass diese Auslastung möglicherweise verhindert, dass weitere Datasets in den Arbeitsspeicher geladen werden können. Die schwarze gestrichelte Trendlinie zeigt den Wachstumstrend basierend auf den Daten aus sieben Tagen. 

![Detailseite zum aktiven Arbeitsspeicher](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>Diagnose für Szenario 2

Um Szenario 2 zu diagnostizieren, ermitteln Sie, ob die Trendlinie einen Aufwärtstrend hin zu einem Warnungs- oder Alarmschwellenwert zeigt. 

1. Sehen Sie sich **Diagramm A** an:

    ![Diagramm mit verbrauchtem Arbeitsspeicher](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** Wenn das Diagramm einen Aufwärtstrend zeigt, weist dies darauf hin, dass der Arbeitsspeicherverbrauch in den letzten sieben Tagen gestiegen ist.

    **b.** Nehmen Sie das aktuelle Wachstum als Grundlage, und prognostizieren Sie, wann die Trendlinie den Warnschwellenwert (die gestrichelte gelbe Linie) überschreiten wird.

    **c.** Überprüfen Sie die Trendlinie mindestens alle zwei Tage, um zu ermitteln, ob sich der Trend fortsetzt.

#### <a name="remedies-for-scenario-two"></a>Abhilfemaßnahmen in Szenario 2

Um die Probleme in Szenario 2 zu beheben, können Sie folgende Schritte ausführen:

1. **Skalieren Sie die Kapazität zentral hoch**: Durch zentrales Hochskalieren auf die nächste SKU steht doppelt so viel Arbeitsspeicher zur Verfügung wie in der aktuellen SKU. So können Sie die aktuelle Speicherauslastung durch die Kapazität verringern.

2. **Verschieben Sie Datasets in eine andere Kapazität**: Wenn Sie über eine andere Kapazität mit mehr Arbeitsspeicher verfügen, können Sie Arbeitsbereiche mit größeren Datasets in diese Kapazität verschieben.


## <a name="the-query-waits-metric"></a>Die Metrik für Abfragewartevorgänge

Die Kategorie **Abfragen** gibt an, ob Berichtsvisuals möglicherweise langsam oder gar nicht reagieren. **Abfragewartevorgänge** geben an, wie viel Zeit zwischen dem Auslösen einer Abfrage und dem Beginn der Ausführung der Abfrage vergeht. Diese KPI misst, ob es bei 25 % oder mehr der Abfragen für die ausgewählte Kapazität 100 Millisekunden oder länger dauert, bis die Ausführung beginnt. Abfragewartevorgänge treten auf, wenn nicht genügend CPU-Kapazität verfügbar ist, um alle ausstehenden Abfragen auszuführen. 

![Das Visual für Abfragewartevorgänge](media/service-premium-metrics-app/premium-metrics-app-09.png)

Dieses Visual (in Form eines Messgeräts) zeigt, dass in den sieben Tagen seit der letzten Aktualisierung 17,32 % der Abfragen mehr als 100 Millisekunden gewartet haben. 

Um Details zur KPI für Abfragewartevorgänge anzuzeigen, klicken Sie auf die Schaltfläche **Erkunden**. Damit wird eine Berichtsseite geöffnet, die eine Visualisierung der relevanten Metriken sowie in der rechten Spalte einen Leitfaden zur Problembehandlung anzeigt. Der Leitfaden zur Problembehandlung enthält zwei Szenarien. Jedes dieser Szenarien stellt detaillierte Erläuterungen zur Metrik sowie zum Status der Kapazität bereit und informiert darüber, mit welchen Maßnahmen sich das Problem minimieren lässt.

In den folgenden Abschnitten wird jedes dieser Szenarien ausführlich beschrieben.

### <a name="scenario-one---long-running-queries-consume-cpu"></a>Szenario 1: CPU-Verbrauch durch Abfragen mit langer Ausführungszeit

In Szenario 1 verbrauchen Abfragen mit langer Ausführungszeit zu viel CPU-Kapazität. 

Sie können untersuchen, ob die geringe Berichtsleistung durch eine überlastete Kapazität oder durch ein Dataset oder einen Bericht verursacht wird, dessen Entwurf Schwachstellen aufweist. Es gibt verschiedene Gründe dafür, dass eine Abfrageausführung einen längeren Zeitraum in Anspruch nimmt. Ein längerer Zeitraum liegt vor, wenn die Ausführung einer Abfrage mehr als 10 Sekunden dauert. Abfragen mit langer Ausführungszeit können durch die Größe und Komplexität des Datasets sowie durch die Komplexität der Abfrage verursacht werden, um nur einige Beispiele zu nennen. 

Auf der Berichtsseite werden die folgenden Visuals angezeigt: 

* Die obere Tabelle mit dem Titel **A: Lange Wartezeiten** führt die Datasets mit Abfragen auf, die sich im Wartezustand befinden. 
* **B: Verteilung langer Wartezeiten nach Stunde** zeigt die Verteilung der langen Wartezeiten. 
* Das Diagramm **C: Anzahl langer Wartezeiten nach Stunde** zeigt die Anzahl von Abfragen mit langer Ausführungszeit, aufgeteilt in Zeitspannen von je einer Stunde.
* Das letzte Visual, Tabelle **D: Abfragen mit langer Ausführungszeit**, listet die Abfragen mit langer Ausführungszeit und die zugehörigen Statistiken auf.

![Detailseite zu Abfragewartevorgängen](media/service-premium-metrics-app/premium-metrics-app-10.png)

Es gibt einige Schritte, die Sie ausführen können, um Probleme mit Abfragewartezeiten zu diagnostizieren und zu beheben. Diese Schritte werden im Folgenden beschrieben.

#### <a name="diagnosing-scenario-one"></a>Diagnose für Szenario 1

Als Erstes können Sie feststellen, ob Abfragen mit langer Ausführungszeit auftreten, wenn Abfragen warten. 

![Tabelle der langen Wartezeiten](media/service-premium-metrics-app/premium-metrics-app-11.png)

Sehen Sie sich **Tabelle B** an, die zeigt, wie viele Abfragen mehr als 100 ms warten. Wählen Sie eine der Spalten aus, die eine hohe Anzahl von Wartevorgängen zeigen.

![Verteilung der langen Wartezeiten](media/service-premium-metrics-app/premium-metrics-app-12.png)

Wenn Sie auf eine Spalte mit langen Wartezeiten klicken, wird **Diagramm C** gefiltert und zeigt die Anzahl von Abfragen mit langer Ausführungszeit an, die in diesem Zeitraum ausgeführt wurden, wie in der folgenden Abbildung veranschaulicht:

![Anzahl langer Wartezeiten nach Stunde](media/service-premium-metrics-app/premium-metrics-app-13.png)

Darüber hinaus wird **Diagramm B** ebenfalls gefiltert und zeigt die Abfragen an, die im ausgewählten Zeitraum lange Ausführungszeiten aufwiesen.

![Zeitintensive Abfragen](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>Abhilfemaßnahmen in Szenario 1

Um Probleme aus Szenario 1 zu beheben, können Sie folgende Schritte ausführen:

1. **Führen Sie PerfAnalyzer aus, um Berichte und Datasets zu optimieren**: Die Leistungsanalyse für Berichte zeigt die Auswirkung jeder Interaktion auf einer Seite – beispielsweise, wie lange die Aktualisierung jedes Visuals dauert und für welche Elemente die Zeit aufgewendet wird.

2. **Skalieren Sie die Kapazität zentral hoch**: Durch zentrales Hochskalieren auf die nächste SKU steht doppelt so viel CPU-Leistung zur Verfügung. So können Sie die CPU-Auslastung durch die Kapazität verringern.

3. **Verschieben Sie Datasets in eine andere Kapazität**: Wenn Sie über eine andere Kapazität mit mehr CPU-Leistung verfügen, können Sie Arbeitsbereiche mit Datasets, die wartende Abfragen enthalten, in diese Kapazität verschieben.

### <a name="scenario-two---too-many-queries"></a>Szenario 2: zu viele Abfragen

In Szenario 2 werden zu viele Abfragen ausgeführt.

Wenn die Anzahl von auszuführenden Abfragen die Kapazitätsgrenzen überschreitet, werden Abfragen in eine Warteschlange eingereiht, bis Ressourcen für die Ausführung zur Verfügung stehen. Wenn eine Warteschlange zu groß wird, warten Abfragen in dieser Warteschlange möglicherweise länger als 100 Millisekunden.

![Szenario 2](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>Diagnose für Szenario 2

Wählen Sie in **Tabelle A** ein Dataset mit einem hohen Prozentsatz an Wartezeit aus.

![Tabelle der langen Wartezeiten](media/service-premium-metrics-app/premium-metrics-app-16.png)

Sobald Sie ein Dataset mit langer Wartezeit ausgewählt haben, wird **Diagramm B** gefiltert und zeigt die Wartezeitverteilungen für Abfragen der letzten sieben Tage in diesem Dataset an. Wählen Sie als Nächstes eine der Spalten aus **Diagramm B** aus.

![Diagramm zur Verteilung langer Wartezeiten nach Stunde](media/service-premium-metrics-app/premium-metrics-app-17.png)

**Diagramm C** wird gefiltert und zeigt die Warteschlangenlänge in dem in Diagramm B ausgewählten Zeitraum an.

![Länge der Abfragewarteschlange pro Stunde](media/service-premium-metrics-app/premium-metrics-app-18.png)

Wenn die Länge der Warteschlange den Schwellenwert 20 überschritten hat, treten wahrscheinlich Verzögerungen bei Abfragen im ausgewählten Dataset auf, weil versucht wird, zu viele Abfragen gleichzeitig auszuführen.

![Tabelle mit ausgeführten Abfragen](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>Abhilfemaßnahmen in Szenario 2

Um die Probleme in Szenario 2 zu beheben, können Sie folgende Schritte ausführen:

1. **Skalieren Sie die Kapazität zentral hoch**: Durch zentrales Hochskalieren auf die nächste SKU steht doppelt so viel Arbeitsspeicher zur Verfügung wie in der aktuellen SKU. So können Sie die aktuelle Speicherauslastung durch die Kapazität verringern.

2. **Verschieben Sie Datasets in eine andere Kapazität**: Wenn Sie über eine andere Kapazität mit mehr Arbeitsspeicher verfügen, können Sie Arbeitsbereiche mit größeren Datasets in diese Kapazität verschieben.


## <a name="the-refresh-waits-metric"></a>Die Metrik für Aktualisierungswartevorgänge

Die Metrik **Aktualisierungswartevorgänge** bietet Erkenntnisse dazu, wann Benutzern möglicherweise veraltete Daten angezeigt werden. **Aktualisierungswartevorgänge** bezeichnen den Zeitraum, den eine bestimmte Datenaktualisierung ab dem Zeitpunkt der bedarfsgesteuerten Auslösung oder dem Zeitpunkt der geplanten Ausführung gewartet hat, bis die Ausführung tatsächlich stattgefunden hat. Diese KPI misst, ob 10 % oder mehr der ausstehenden Aktualisierungsanforderungen 10 Minuten oder länger warten. Wartezeiten treten generell dann auf, wenn nicht ausreichend Arbeitsspeicher oder CPU-Leistung verfügbar ist.

![Das Visual für Aktualisierungswartevorgänge](media/service-premium-metrics-app/premium-metrics-app-20.png)

Dieses Visual (in Form eines Messgeräts) zeigt, dass in den sieben Tagen seit der letzten Berichtsaktualisierung 3,18 % der Aktualisierungen mehr als 10 Minuten gewartet haben. 

Um weitere Details zur KPI für **Aktualisierungswartevorgänge** zu erhalten, klicken Sie auf die Schaltfläche **Erkunden**. Damit wird eine Seite geöffnet, die Metriken sowie in der rechten Spalte einen Leitfaden zur Problembehandlung anzeigt. Der Leitfaden bietet detaillierte Erläuterungen zu den Metriken auf der Seite, sodass Sie den Status der Kapazität verstehen und erfahren, welche Maßnahmen Sie zur Minimierung von Problemen ergreifen können.

![Erkunden der Metrik für Aktualisierungswartevorgänge](media/service-premium-metrics-app/premium-metrics-app-21.png)

Auf der Berichtsseite werden zwei Szenarien erläutert, die Sie durch Auswahl von Szenario 1 bzw. Szenario 2 anzeigen können. In den folgenden Abschnitten wird jedes dieser Szenarien ausführlich beschrieben.

### <a name="scenario-one---not-enough-memory"></a>Szenario 1: nicht genügend Arbeitsspeicher

In Szenario 1 ist nicht genügend Arbeitsspeicher verfügbar, um das Dataset zu laden. Es gibt zwei Situationen, die dazu führen, dass eine Aktualisierung bei unzureichendem Arbeitsspeicher gedrosselt wird:

1. Es ist nicht genügend Arbeitsspeicher vorhanden, um das Dataset zu laden.
2. Die Aktualisierung wurde aufgrund eines Vorgangs mit höherer Priorität abgebrochen. 

Die Priorität beim Laden von Datasets lautet wie folgt:

1. Interaktive Abfrage
2. Bedarfsgesteuerte Aktualisierung
3. Geplante Aktualisierung

Wenn nicht genügend Arbeitsspeicher zum Laden eines Datasets für eine interaktive Abfrage verfügbar ist, werden geplante Aktualisierungen angehalten und die zugehörigen Datasets entladen, bis genügend Arbeitsspeicher zur Verfügung steht. Wenn dadurch nicht genügend Arbeitsspeicher frei wird, werden bedarfsgesteuerte Aktualisierungen angehalten und die zugehörigen Datasets entladen.

#### <a name="diagnosing-scenario-one"></a>Diagnose für Szenario 1

Um Szenario 1 zu diagnostizieren, ermitteln Sie zunächst, ob die Drosselung aufgrund des unzureichenden Arbeitsspeichers stattfindet. Führen Sie dazu die folgenden Schritte aus.

1.    Wählen Sie in **Tabelle A** das Dataset aus, an dem Sie interessiert sind, indem Sie darauf klicken: 

    ![Tabelle A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Wenn in **Tabelle A** ein Dataset ausgewählt wird, wird **Diagramm B** gefiltert und zeigt an, wann die Wartevorgänge aufgetreten sind.

    ![Diagramm B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. Dann wird **Diagramm C** gefiltert und zeigt alle Drosselungsvorgänge an, wie im nächsten Schritt erläutert. 

2. Sehen Sie sich die Ergebnisse im gefilterten **Diagramm C** an. Wenn das Diagramm zeigt, dass zu Zeitpunkten, zu denen das Dataset gewartet hat, eine Drosselung aufgrund unzureichenden Arbeitsspeichers stattgefunden hat, hat das Dataset gewartet, weil nicht genügend Arbeitsspeicher vorhanden war.

    ![Diagramm C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Überprüfen Sie abschließend **Diagramm D**, das zeigt, welche Arten von Aktualisierungen stattgefunden haben: geplante oder bedarfsgesteuerte. Alle gleichzeitig aufgetretenen bedarfsgesteuerte Aktualisierungen können der Grund für die Drosselung sein.

    ![Diagramm D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>Abhilfemaßnahmen in Szenario 1

Um die Probleme in Szenario 1 zu beheben, können Sie folgende Schritte ausführen:

1. **Skalieren Sie die Kapazität zentral hoch**: Durch zentrales Hochskalieren auf die nächste SKU steht doppelt so viel Arbeitsspeicher zur Verfügung wie in der aktuellen SKU. So können Sie die aktuelle Speicher- und CPU-Auslastung durch die Kapazität verringern.

2. **Verschieben Sie Datasets in eine andere Kapazität**: Wenn Wartezeiten durch Speicherauslastung entstehen und Sie über eine andere Kapazität mit mehr Arbeitsspeicher verfügen, können Sie die Arbeitsbereiche mit wartenden Datasets in diese Kapazität verschieben.

3. **Verteilen Sie geplante Aktualisierungen**: Durch Verteilen der Aktualisierungen können Sie vermeiden, dass versucht wird, zu viele Aktualisierungen gleichzeitig auszuführen.



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>Szenario 2: nicht genügend CPU-Leistung für Aktualisierungen

In Szenario 2 ist nicht genügend CPU-Leistung zum Ausführen der Aktualisierungen vorhanden. 

Bei dedizierten Kapazitäten begrenzt Power BI die Anzahl von Aktualisierungen, die gleichzeitig stattfinden können. Die Anzahl entspricht der Anzahl von Back-End-Kernen, multipliziert mit 1,5. Eine dedizierte P1-Kapazität, die über vier Back-End-Kerne verfügt, kann beispielsweise sechs Aktualisierungen gleichzeitig ausführen. Sobald die maximale Anzahl gleichzeitiger Aktualisierungen erreicht ist, warten weitere Aktualisierungen, bis die Ausführung einer Aktualisierung beendet wurde.

![Szenario 2 für die Aktualisierung](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>Diagnose für Szenario 2

Zum Diagnostizieren von Szenario 2 ermitteln Sie zunächst, ob die Drosselung erfolgt, weil der Maximalwert für gleichzeitige Aktualisierungen erreicht wurde. Führen Sie dazu die folgenden Schritte aus.

1.    Wählen Sie in **Tabelle A** das Dataset aus, an dem Sie interessiert sind, indem Sie darauf klicken: 

    ![Tabelle A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. Wenn in **Tabelle A** ein Dataset ausgewählt wird, wird **Diagramm B** gefiltert und zeigt an, wann die Wartevorgänge aufgetreten sind.

    ![Diagramm B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. Dann wird **Diagramm C** gefiltert und zeigt alle Drosselungsvorgänge an, wie im nächsten Schritt erläutert. 

2. Sehen Sie sich die Ergebnisse im gefilterten **Diagramm C** an. Wenn das Diagramm zeigt, dass zu Zeitpunkten, zu denen das Dataset gewartet hat, die *maximale Anzahl gleichzeitiger Aktualisierungen* erreicht war, hat das Dataset gewartet, weil nicht genügend CPU-Leistung vorhanden war.

    ![Diagramm C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. Überprüfen Sie abschließend **Diagramm D**, das zeigt, welche Arten von Aktualisierungen stattgefunden haben: geplante oder bedarfsgesteuerte. Alle gleichzeitig aufgetretenen bedarfsgesteuerte Aktualisierungen können der Grund für die Drosselung sein.

    ![Diagramm D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>Abhilfemaßnahmen in Szenario 2

1. **Skalieren Sie die Kapazität zentral hoch**: Durch zentrales Hochskalieren auf die nächste SKU steht doppelt so viel Arbeitsspeicher und doppelt so viele gleichzeitige Aktualisierungsvorgänge zur Verfügung wie in der aktuellen SKU. So können Sie die aktuelle Speicher- und CPU-Auslastung durch die Kapazität verringern.

2. **Verschieben Sie Datasets in eine andere Kapazität**: Wenn Wartezeiten durch Erreichen der maximalen Anzahl gleichzeitiger Aktualisierungen entstehen und Sie über eine andere Kapazität mit mehr Parallelität verfügen, können Sie die Arbeitsbereiche mit wartenden Datasets in diese Kapazität verschieben.

3. **Verteilen Sie geplante Aktualisierungen**: Durch Verteilen der Aktualisierungen können Sie vermeiden, dass versucht wird, zu viele Aktualisierungen gleichzeitig auszuführen.



## <a name="next-steps"></a>Nächste Schritte

* [Was ist Power BI Premium?](service-premium-what-is.md)
* [Power BI Premium – Anmerkungen zu dieser Version](service-premium-release-notes.md)
* [Microsoft Power BI Premium-Whitepaper](https://aka.ms/pbipremiumwhitepaper)
* [Planning a Power BI Enterprise Deployment whitepaper (Whitepaper zum Planen der Unternehmensbereitstellung von Power BI)](https://aka.ms/pbienterprisedeploy)
* [Aktivierung der erweiterten Pro-Testversion](service-extended-pro-trial.md)
* [Power BI Embedded – FAQ](developer/embedded/embedded-faq.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)