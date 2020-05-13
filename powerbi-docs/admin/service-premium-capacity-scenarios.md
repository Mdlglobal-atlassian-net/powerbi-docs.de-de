---
title: Szenarios mit Microsoft Power BI Premium-Kapazitäten
description: Beschreibt häufige Szenarios mit Microsoft Power BI Premium-Kapazitäten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9b3e06172d29f218f9234cf1f3d7e1f623495001
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83135187"
---
# <a name="premium-capacity-scenarios"></a>Szenarios mit Premium-Kapazitäten

In diesem Artikel werden Szenarios aus der Praxis beschrieben, in denen Power BI Premium-Kapazitäten implementiert wurden. Häufige Probleme und Herausforderungen werden ebenso erläutert wie die Identifizierung von Problemen und deren Lösung:

- [Aktuellhalten von Datasets](#keeping-datasets-up-to-date)
- [Identifizieren von langsam reagierenden Datasets](#identifying-slow-responding-datasets)
- [Identifizieren von Ursachen für sporadisch langsam reagierende Datasets](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Bestimmen, ob genügend Arbeitsspeicher vorhanden ist](#determining-whether-there-is-enough-memory)
- [Bestimmen, ob genügend CPU-Kapazität vorhanden ist](#determining-whether-there-is-enough-cpu)

Die Schritte sowie Diagramm- und Tabellenbeispiele stammen aus der **Power BI Premium-Kapazitäts-Metrik-App**, auf die ein Power BI-Administrator Zugriff hat.

## <a name="keeping-datasets-up-to-date"></a>Aktuellhalten von Datasets

In diesem Szenario wurde eine Untersuchung eingeleitet, als sich die Benutzer beschwerten, dass die Berichtsdaten manchmal alt oder „überholt“ erschienen.

In der App interagiert der Administrator mit dem Visual **Aktualisierungen** und sortiert Datasets nach der Statistik **Max. Wartezeit** in absteigender Reihenfolge. Dieses Visual hilft ihnen, Datasets mit den längsten Wartezeiten, gruppiert nach Arbeitsbereichsnamen, anzuzeigen.

![Das Dataset wird nach absteigender maximaler Wartezeit sortiert und, nach Arbeitsbereich gruppiert, aktualisiert.](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Im Visual **Durchschnittliche stündliche Aktualisierungswartezeiten** sehen sie, dass die Aktualisierungswartezeiten jeden Tag immer um etwa 16 Uhr einen Spitzenwert erreichen.

![Spitzenwerte von Aktualisierungszeiten regelmäßig um 16 Uhr](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Es gibt mehrere mögliche Erklärungen für diese Ergebnisse:

- Möglicherweise gibt es zu viele gleichzeitige Aktualisierungsversuche, die die durch den Kapazitätsknoten definierten Grenzen überschreiten. In diesem Fall werden sechs gleichzeitige Aktualisierungen auf einem P1 mit Standardspeicherzuweisung durchgeführt.

- Zu aktualisierende Datasets können für den verfügbaren Speicher zu groß sein (für eine vollständige Aktualisierung wird mindestens der doppelte Speicher benötigt).
- Ineffiziente Power Query-Logik kann zu einem Anstieg der Speichernutzung während der Aktualisierung des Datasets führen. Bei einer Kapazitätsauslastung kann diese Spitze gelegentlich die physische Grenze erreichen, wodurch die Aktualisierung fehlschlägt und andere Vorgänge der Berichtsansicht zur Kapazität beeinträchtigt werden können.
- Häufig abgefragte Datasets, die im Speicher bleiben müssen, können aufgrund des begrenzten verfügbaren Speichers die Aktualisierung anderer Datasets beeinträchtigen.

Um die Untersuchung zu erleichtern, kann der Power BI-Administrator nach Folgendem suchen:

- Wenig verfügbarer Speicher zum Zeitpunkt der Datenaktualisierungen, wenn der verfügbare Speicher weniger als doppelt so groß ist wie das zu aktualisierende Dataset.
- Für Datasets, die nicht aktualisiert wurden und sich vor dem Aktualisieren nicht im Speicher befanden, wurde jedoch ein interaktiver Datenverkehr während Aktualisierungszeiten mit hohen Auslastungen angezeigt. Informationen darüber, welche Datasets zu einem bestimmten Zeitpunkt in den Speicher geladen werden, kann ein Power BI-Administrator im Datasetbereich auf der Registerkarte **Datasets** in der App einsehen. Der Administrator kann dann den Filter auf eine bestimmte Zeit verschieben, indem er auf einen der Balken in **Anzahl von stündlich geladenen Datasets** klickt. Ein lokaler Spitzenwert, der in der unteren Abbildung dargestellt ist, zeigt eine Stunde, in der mehrere Datasets in den Speicher geladen wurden, wodurch es zu einer Verzögerung des Beginns der geplanten Aktualisierungen kommen konnte.
- Zum Startzeitpunkt der Datenaktualisierungen finden vermehrt Entfernungen von Datasets statt. Entfernungen können darauf hindeuten, dass eine hohe Speicherauslastung auftrat, die dadurch verursacht wurde, dass zu viele verschiedene interaktive Berichte vor dem Zeitpunkt der Aktualisierung bereitgestellt wurden. Das Visual **Entfernte Datasets und Arbeitsspeicherverbrauch pro Stunde** kann deutlich auf Spitzenwerte bei Entfernungen hinweisen.

Die folgende Abbildung zeigt einen lokalen Spitzenwert in geladenen Datasets, der eine interaktive Abfrage bei verzögerten Starts der Aktualisierungen vorschlägt. Die Auswahl eines Zeitraums im Visual **Anzahl von stündlich geladenen Datasets** bewirkt eine Kreuzfilterung des Visuals **Datasetgrößen**.

![Ein lokaler Spitzenwert in geladenen Datasets schlägt eine interaktive Abfrage bei verzögerten Starts der Aktualisierungen vor.](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

Der Power BI-Administrator kann das Problem ggf. beheben, indem er Maßnahmen ergreift, um sicherzustellen, dass genügend Speicherplatz für die Datenaktualisierung zur Verfügung steht:

- Kontaktaufnahme mit den Datasetbesitzern und Aufforderung, die Datenaktualisierungspläne zu staffeln und zu löschen.
- Reduzierung der Abfragelast für Datasets durch Entfernen unnötiger Dashboards oder Dashboardkacheln, insbesondere solcher, die die Sicherheit auf Zeilenebene durchsetzen.
- Beschleunigung der Datenaktualisierungen durch Optimierung der Power Query-Logik. Verbesserung der Modellierung von berechneten Spalten oder Tabellen. Reduzierung der Datasetgrößen oder Konfiguration größerer Datasets zur Durchführung einer inkrementellen Datenaktualisierung.

## <a name="identifying-slow-responding-datasets"></a>Identifizieren von langsam reagierenden Datasets.

In diesem Szenario wurde eine Untersuchung eingeleitet, als sich Benutzer darüber beschwerten, dass das Öffnen bestimmter Berichte zu lange dauerte und manchmal auch zum Stillstand kommen würde.

In der App kann der Power BI-Administrator das Visual **Abfragedauer** verwenden, um die Datasets mit der schlechtesten Leistung zu bestimmen, indem er Datasets nach **Durchschnittliche Dauer** absteigend sortiert. Dieses Visual zeigt auch die Anzahl der Abfragen von Datasets an, sodass Sie sehen können, wie oft diese abgefragt werden.

![Leistungsschwächste Datasets](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

Der Administrator kann sich auf das Visual **Verteilung der Abfragedauer** beziehen, das eine Gesamtverteilung der getakteten Abfrageleistung (<= 30 ms, 0-100 ms) für den gefilterten Zeitraum anzeigt. Im Allgemeinen werden Abfragen, die eine Sekunde oder weniger dauern, von den meisten Benutzern als schnell beantwortet angesehen; Abfragen, die länger dauern, führen tendenziell dazu, dass die Leistung schlechter beurteilt wird.

Mit dem Visual **Stündliche Verteilungen der Abfragedauer** kann der Power BI-Administrator einstündige Zeiträume identifizieren, in denen die Kapazitätsleistung als schlecht empfunden werden konnte. Je größer die Balkensegmente, die die Abfragedauer über eine Sekunde darstellen, desto wahrscheinlicher ist es, dass Benutzer eine schlechte Leistung feststellen.

Das Visual ist interaktiv, sodass bei Auswahl eines Segments des Balkens das entsprechende Tabellenvisual **Abfragedauer** auf der Berichtsseite kreuzgefiltert wird, um die entsprechenden Datasets anzuzeigen. Durch diese Kreuzfilterung kann der Power BI-Administrator leicht erkennen, welche Datasets langsam reagieren.

Die folgende Abbildung zeigt ein Visual, das nach **Stündliche Verteilungen der Abfragedauer** gefiltert ist und sich auf die Datasets mit der schlechtesten Leistung in einstündigen Buckets konzentriert. 

![Das gefilterte Visual „Stündliche Verteilungen der Abfragedauer“ zeigt die leistungsschwächsten Datasets](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Sobald das leistungsschwache Dataset in einem festgelegten Zeitraum von einer Stunde identifiziert wurde, kann der Power BI-Administrator untersuchen, ob eine schlechte Leistung durch eine zu hohe Kapazitätsauslastung oder durch ein schlecht entwickeltes Dataset bzw. einen schlecht konzipierten Bericht verursacht wird. Sie können sich auf das Visual **Abfragewartezeiten** beziehen und Datasets nach der absteigenden durchschnittlichen Wartezeit der Abfrage sortieren. Wenn ein großer Prozentsatz der Abfragen wartet, ist eine hohe Nachfrage nach dem Dataset wahrscheinlich die Ursache für zu lange Abfragezeiten. Wenn die durchschnittliche Wartezeit für die Abfrage erheblich ist (> 100 ms), kann es sich lohnen, das Dataset und den Bericht zu überprüfen. So lässt sich feststellen, ob Optimierungen vorgenommen werden können. Beispiele hierfür sind weniger Visuals auf bestimmten Berichtsseiten oder eine DAX-Ausdruckoptimierung.

![Das Visual „Abfragewartezeiten“ trägt dazu bei, leistungsschwache Datasets aufzudecken.](media/service-premium-capacity-scenarios/query-wait-times.png)

Es gibt mehrere mögliche Gründe, warum sich für Datasets bei Abfragen längere Wartezeiten ergeben:

- Ungünstige Modelldesigns, Measureausdrücke oder sogar Berichtsdesigns: dies sind alles Umstände, die zu zeitintensiven Abfragen und hoher CPU-Nutzung beitragen können. Dadurch müssen neue Abfragen warten, bis CPU-Threads verfügbar sind, sodass ein Konvoi-Effekt (Datenverkehrsstau) entsteht, der häufig zu den Hauptgeschäftszeiten auftritt. Die Seite **Abfragewartezeiten** ist die wichtigste Informationsquelle, um festzustellen, ob Datasets eine hohe durchschnittliche Wartezeit bei Abfragen haben.
- Eine hohe Anzahl von gleichzeitigen Zugriffen (Hunderte bis Tausende) auf den gleichen Bericht oder das gleiche Dataset. Selbst gut durchdachte Datasets können bei Überschreitung eines Schwellenwerts für die gleichzeitige Nutzung schlecht abschneiden. Dies wird in der Regel durch ein einzelnes Dataset angezeigt, das einen deutlich höheren Wert für die Anzahl der Abfragen aufweist als andere Datasets (z. B. 300.000 Abfragen für ein Dataset im Vergleich zu < 30.000 Abfragen für alle anderen Datasets). Ab einem bestimmten Zeitpunkt werden die Abfragewartezeiten für dieses Dataset gestaffelt, wie im Visual **Abfragedauer** zu sehen ist.
- Viele unterschiedliche Datasets wurden gleichzeitig abgefragt, was zu einer Überlastung durch den häufigen Wechsel der Datasets im Speicher führte. Infolgedessen stellten Benutzer fest, dass Datasets nur langsam in den Speicher geladen wurden. Zur Bestätigung kann sich der Power BI-Administrator auf das Visual **Entfernte Datasets und Arbeitsspeicherverbrauch pro Stunde** beziehen, das darauf hinweist, dass eine große Anzahl von in den Speicher geladenen Datasets wiederholt entfernt wurde.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identifizieren von Ursachen für sporadisch langsam reagierende Datasets

In diesem Szenario wurde eine Untersuchung eingeleitet, als die Benutzer beschrieben, dass Berichtsvisuals manchmal nur langsam oder gar nicht mehr, zu anderen Zeiten aber zuverlässig reagierten.

In der App wurde der Abschnitt **Abfragedauer** verwendet, um das verursachende Dataset wie folgt zu finden:

- Im Visual **Abfragedauer** filterte der Administrator das Dataset nach Dataset (beginnend mit den obersten abgefragten Datasets) und untersuchte die kreuzgefilterten Balken im Visual **Stündliche Verteilungen der Abfragedauer**.
- Wenn ein einzelner Ein-Stunden-Balken signifikante Änderungen im Verhältnis zwischen allen Abfragedauergruppen und anderen Ein-Stunden-Balken für dieses Dataset zeigte (z. B. eine drastische Veränderung der Verhältnisse zwischen den Farben), bedeutet dies, dass dieses Dataset eine sporadische Änderung der Leistung zeigte.
- Die Ein-Stunden-Balken, die einen unregelmäßigen Anteil der nicht zufriedenstellenden Abfragen anzeigen, veranschaulichten eine Zeitspanne, in der dieses Dataset von einem „Noisy Neighbor“-Effekt betroffen war, der durch die Aktivitäten anderer Datasets verursacht wurde.

Die folgende Abbildung zeigt eine Stunde am 30. Januar, in der ein signifikanter Leistungseinbruch eines Datasets auftrat, dargestellt durch die Größe des „(3,10s]“-Ausführungsdauerbuckets. Wenn Sie auf diesen Ein-Stunden-Balken klicken, werden alle in diesem Zeitraum in den Speicher geladenen Datasets aufgedeckt, worunter auch Datasets sein können, die den „Noisy Neighbor“-Effekt verursachen.

![Balken mit der schlechtesten Leistung von einem großen Anteil](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Sobald eine problematische Zeitspanne identifiziert wurde (z. B. während des 30. Januar in der obigen Abbildung), kann der Power BI-Administrator alle Datasetfilter entfernen. Dann kann er nur nach dieser Zeitspanne filtern, um festzustellen, welche Datasets während dieser Zeit aktiv abgefragt wurden. Das verursachende Dataset für den „Noisy Neighbor“-Effekt ist in der Regel das oberste abgefragte Dataset oder das mit der längsten durchschnittlichen Abfragedauer.

Eine mögliche Lösung für dieses Problem wäre die Verteilung der verursachenden Datasets auf verschiedene Arbeitsbereiche verschiedener Premium-Kapazitäten oder auf gemeinsame Speicherkapazitäten, wenn die Größe des Datasets, der Nutzungsbedarf und die Datenaktualisierungsmuster unterstützt werden.

Das Gegenteil könnte auch der Fall sein. Der Power BI-Administrator könnte Zeiten identifizieren, in denen sich die Leistung einer Datasetabfrage drastisch verbessert, und dann nach dem verschwundenen Element suchen. Wenn an dieser Stelle bestimmte Informationen fehlen, kann dies helfen, das verursachende Problem zu erkennen.

## <a name="determining-whether-there-is-enough-memory"></a>Bestimmen, ob genügend Arbeitsspeicher vorhanden ist

Um zu bestimmen, ob genügend Speicherkapazität vorhanden ist, um die Workloads abzuschließen, kann der Power BI-Administrator auf das Visual **Prozentsätze des verbrauchten Arbeitsspeichers** auf der Registerkarte **Datasets** der App zugreifen. **Alle**: Der gesamte Speicher zeigt den von den geladenen Datasets insgesamt genutzten Speicher, unabhängig davon, ob sie aktiv abgefragt oder verarbeitet werden. **Aktiv**: Der aktive Speicher zeigt den von den aktiv verarbeiteten Datasets genutzten Speicher.

Bei einer guten Speicherkapazität sieht das Visual wie folgt aus und zeigt eine Lücke zwischen „Alle“ und „Aktiv“, also dem gesamten und dem aktiven Speicher an.

![Bei einer guten Speicherkapazität gibt es eine Lücke zwischen dem gesamten und dem aktiven Speicher](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Bei einer unzureichenden Speicherkapazität zeigt das gleiche Visual deutlich den aktiven Speicher und den gesamten Speicher konvergierend an, sodass es dann unmöglich ist, zusätzliche Datasets in den Speicher zu laden. In diesem Fall kann der Power BI-Administrator auf **Neustart der Kapazität** klicken (unter **Erweiterte Optionen** im Bereich für Kapazitätseinstellungen des Administratorportals). Ein Neustart der Kapazität führt dazu, dass alle Datasets aus dem Speicher geleert werden und bei Bedarf (durch Abfragen oder Datenaktualisierung) wieder in den Speicher geladen werden können.

![**Aktiver** Speicher konvergierend mit **gesamtem** Speicher](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Bestimmen, ob genügend CPU-Kapazität vorhanden ist

Im Allgemeinen sollte die durchschnittliche CPU-Auslastung einer Kapazität unter 80 % liegen. Wenn dieser Wert überschritten wird, nähert sich die Kapazität der CPU-Sättigung.

Die Auswirkungen der CPU-Sättigung äußern sich in Vorgängen mit längerer Ausführungszeit, da versucht wird, mit der Kapazität viele Vorgänge zu verarbeiten, indem zwischen CPU-Kontexten gewechselt wird. In einer Premium-Kapazität mit einer hohen Anzahl gleichzeitiger Abfragen wird dies durch lange Abfragewartezeiten angegeben. Eine Folge langer Abfragewartezeiten sind längere Reaktionszeiten als üblich. Der Power BI-Administrator kann leicht erkennen, wann die CPU gesättigt ist, indem er das Visual **Stündliche Wartezeitverteilungen für Abfragen** überprüft. Regelmäßig auftretende Spitzen bei den Indikatoren der Abfragewartezeit weisen auf eine potenzielle CPU-Sättigung hin.

![Regelmäßig auftretende Spitzen bei den Indikatoren der Abfragewartezeit weisen auf eine potenzielle CPU-Sättigung hin](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

In manchen Fällen kann ein einfaches Muster in Hintergrundvorgängen erkannt werden, wenn diese zur CPU-Sättigung beitragen. Ein Power BI-Administrator kann nach einem vorübergehenden Anstieg der Aktualisierungszeiten für ein bestimmtes Dataset suchen, der auf die jeweilige CPU-Sättigung hinweisen kann (wahrscheinlich aufgrund anderer laufender Aktualisierungen von Datasets und/oder interaktiver Abfragen). In diesem Fall kann der Blick auf die Ansicht **System** in der App nicht unbedingt Aufschluss darüber geben, ob die CPU bei 100 % liegt. Die Ansicht **System** zeigt stündliche Durchschnittswerte an, aber die CPU kann für mehrere Minuten rechenintensiver Vorgänge gesättigt werden, was sich als Spitzen in den Wartezeiten wiederspiegelt.

Es gibt weitere Details, die den Effekt der CPU-Sättigung verdeutlichen. Obwohl die Anzahl der wartenden Abfragen wichtig ist, werden immer gewisse Abfragewartezeiten auftreten, ohne dass es zu erkennbaren Leistungseinbrüchen kommt. Einige Datasets (mit längerer durchschnittlicher Abfragezeit, die auf Komplexität oder Größe hinweist) sind für die Effekte der CPU-Sättigung anfälliger als andere. Um diese Datasets leicht zu identifizieren, kann der Power BI-Administrator nach Änderungen in der Farbzusammensetzung der Balken im Visual **Stündliche Wartezeitverteilungen für Abfragen** suchen. Nachdem er einen Ausreißer erkannt hat, kann er nach den Datasets mit Abfragewartezeiten in diesem Zeitraum suchen und sich auch die durchschnittliche Abfragewartezeit im Vergleich zur durchschnittlichen Abfragedauer ansehen. Wenn diese beiden Metriken gleich groß sind und die Abfrageworkload für das Dataset nicht trivial ist, wird die Abfrageleistung für das Dataset wahrscheinlich durch eine unzureichende CPU-Kapazität beeinträchtigt.

Dieser Effekt tritt besonders deutlich zutage, wenn ein Dataset in kurzen Bursts von hochfrequenten Abfragen durch mehrere Benutzer (z. B. in einer Schulungssitzung) genutzt wird. Das Ergebnis ist eine CPU-Sättigung bei jedem Burst. In diesem Fall können erhebliche Abfragewartezeiten für dieses Dataset auftreten, die sich in Bezug auf die Kapazität auch auf andere Datasets auswirken („Noisy Neighbor“-Effekt).

In manchen Fällen können Power BI-Administratoren auch Datasetbesitzer auffordern, eine weniger schwankende Abfrageworkload zu erzeugen, indem sie anstelle eines Berichts ein Dashboard erstellen (das regelmäßig mit jeder Aktualisierung des Datasets für zwischengespeicherte Kacheln abfragt). Dies kann dazu beitragen, Auslastungsspitzen beim Laden des Dashboards zu vermeiden. Möglicherweise ist diese Lösung für bestimmte Geschäftsanforderungen mitunter nicht umsetzbar, aber sie kann dennoch eine effektive Methode sein, um eine CPU-Sättigung zu vermeiden, ohne Änderungen am Dataset vorzunehmen.

## <a name="acknowledgements"></a>Danksagungen

Dieser Artikel wurde von Peter Myers, Data Platform MVP und unabhängiger BI-Experte bei [Bitwise Solutions](https://www.bitwisesolutions.com.au/), verfasst.

## <a name="next-steps"></a>Weitere Schritte

> [!div class="nextstepaction"]
> [Überwachen von Premium-Kapazitäten über die App](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Überwachen von Kapazitäten im Verwaltungsportal](service-admin-premium-monitor-portal.md)   

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

||||||