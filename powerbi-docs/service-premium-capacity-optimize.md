---
title: Optimieren von Microsoft Power BI Premium-Kapazitäten
description: Beschreibt Optimierungsstrategien für Power BI Premium-Kapazitäten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 4d03419105244b7fddafea3b26b69e4f4f5f874c
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79207687"
---
# <a name="optimizing-premium-capacities"></a>Optimieren von Premium-Kapazitäten

Wenn Leistungsprobleme bei Premium-Kapazitäten auftreten, ist der erste Ansatz häufig, Ihre Lösungen zu optimieren oder anzupassen, um wieder akzeptable Reaktionszeiten zu erzielen. Der Grund dafür ist, dass ein Erwerb zusätzlicher Premium-Kapazität zunächst vermieden werden soll, solange dies nicht gerechtfertigt ist.

Wenn zusätzliche Premium-Kapazität benötigt wird, gibt es zwei Möglichkeiten, die in diesem Artikel beschrieben werden:

- Zentrales Hochskalieren vorhandener Premium-Kapazität
- Hinzufügen neuer Premium-Kapazität

Am Ende dieses Artikels werden noch Testansätze und die Dimensionierung der Premium-Kapazität beschrieben.

## <a name="best-practices"></a>Bewährte Methoden

Für Ihr Vorhaben, die bestmögliche Nutzung und Leistung zu erzielen, werden einige bewährte Methoden empfohlen. Dazu gehören:

- Verwenden von Arbeitsbereichen anstelle persönlicher Arbeitsbereiche
- Trennen von unternehmenskritischer und Self-Service-BI (SSBI) in verschiedene Kapazitäten

  ![Trennen von unternehmenskritischer und Self-Service-BI in verschiedene Kapazitäten](media/service-premium-capacity-optimize/separate-capacities.png)

- Wenn Inhalte nur für Power BI Pro-Benutzer freigegeben werden, ist es möglicherweise nicht erforderlich, den Inhalt in einer dedizierten Kapazität zu speichern.
- Verwenden Sie dedizierte Kapazitäten, wenn Sie eine bestimmte Aktualisierungszeit erreichen möchten oder wenn bestimmte Features erforderlich sind, z.B. bei großen Datasets oder paginierten Berichten.

### <a name="addressing-common-questions"></a>Häufig gestellte Fragen

Die Optimierung von Power BI Premium-Bereitstellungen ist ein komplexes Thema, das Kenntnisse über Workloadanforderungen, verfügbare Ressourcen und deren effektive Nutzung umfasst.

In diesem Artikel werden sieben häufig gestellte Supportfragen behandelt, wobei mögliche Probleme und Erklärungen genannt sowie Informationen zu deren Erkennung und Lösung gegeben werden.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Warum ist die Kapazität langsam, und was kann ich tun?

Es gibt viele Ursachen, die zu einer langsamen Premium-Kapazität beitragen können. Diese Frage erfordert weitere Informationen, um zu verstehen, was mit langsam gemeint ist. Werden Berichte langsam geladen? Oder werden Sie gar nicht geladen? Werden visuelle Elemente in Berichten langsam geladen oder aktualisiert, wenn Benutzer mit dem Bericht interagieren? Dauern Aktualisierungen länger als erwartet oder als es zuvor der Fall war?

Nachdem Sie die Ursache verstanden haben, können Sie mit der Untersuchung beginnen. Die Antworten auf die folgenden sechs Fragen helfen Ihnen bei spezifischeren Problemen.

### <a name="what-content-is-using-up-my-capacity"></a>Welche Inhalte verbrauchen meine Kapazität?

Mithilfe der App **Power BI Premium-Kapazitätsmetriken** können Sie nach Kapazität filtern und Leistungsmetriken für Arbeitsbereichsinhalte überprüfen. Sie können für alle in einer Premium-Kapazität gespeicherten Inhalte die Leistungsmetriken und die Ressourcennutzung nach Stunden in den letzten sieben Tagen überprüfen. Die Überwachung ist häufig der erste Schritt, wenn es darum geht, ein allgemeines Problem in Bezug auf die Premium-Kapazitätsleistung zu beheben.

Zu überwachende Schlüsselmetriken sind:

- Durchschnittliche CPU-Auslastung und Anzahl hohe Auslastung
- Durchschnittliche Speicherauslastung und Anzahl hohe Auslastung sowie Speicherauslastung für bestimmte Datasets, Dataflows und paginierte Berichte
- Aktive, im Arbeitsspeicher geladene Datasets
- Durchschnittliche und maximale Abfragedauer
- Durchschnittliche Abfragewartezeiten
- Durchschnittliche Aktualisierungszeiten für Datasets und Dataflows

In der Power BI Premium-Kapazitätsmetriken-App zeigt der aktive Arbeitsspeicher die Gesamtmenge an Speicher, die einem Bericht zugewiesen ist, der nicht entfernt werden kann, da er innerhalb der letzten drei Minuten verwendet wurde. Ein hoher Anstieg der Aktualisierungswartezeit kann mit einem großen und/oder aktiven Dataset in Zusammenhang stehen.

Das Diagramm **Top 5 nach durchschnittlicher Dauer** zeigt die fünf wichtigsten Datasets, paginierten Berichte und Dataflows, die Kapazitätsressourcen verbrauchen. Der Inhalt der Top 5-Listen stellt Kandidaten für die Untersuchung und mögliche Optimierung dar.

### <a name="why-are-reports-slow"></a>Warum sind Berichte langsam?

In den folgenden Tabellen sind mögliche Probleme und Möglichkeiten aufgeführt, diese zu erkennen und zu behandeln.

#### <a name="insufficient-capacity-resources"></a>Unzureichende Kapazitätsressourcen

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Hoher aktiver Gesamtspeicher (das Modell kann nicht entfernt werden, da es innerhalb der letzten drei Minuten verwendet wurde)<br><br> Mehrere hohe Spitzen in Abfragewartezeiten<br><br> Mehrere hohe Spitzen in Aktualisierungswartezeiten | Überwachen Sie die Arbeitsspeichermetriken \[[1](#endnote-1)\] und die Anzahl von Entfernungen \[[2](#endnote-2)\]. | Verringern Sie die Modellgröße, oder wechseln Sie in den DirectQuery-Modus. Weitere Informationen finden Sie im Abschnitt [Optimieren von Modellen](#optimizing-models) in diesem Artikel.<br><br> Skalieren Sie die Kapazität zentral hoch.<br><br> Weisen Sie den Inhalt einer anderen Kapazität zu. |

#### <a name="inefficient-report-designs"></a>Ineffiziente Berichtsentwürfe

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Berichtsseiten enthalten zu viele visuelle Elemente (interaktives Filtern kann mindestens eine Abfrage pro visuellem Element auslösen)<br><br> Visuelle Elemente rufen mehr Daten als notwendig ab | Überprüfen Sie die Berichtsentwürfe.<br><br> Befragen Sie Berichtsbenutzer, um zu verstehen, wie diese mit den Berichten interagieren.<br><br> Überwachen Sie die Metriken für Datasetabfragen \[[3](#endnote-3)\]. | Gestalten Sie Berichte mit weniger visuellen Elementen pro Seite. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Dataset ist langsam, insbesondere wenn Berichte zuvor eine gute Leistung aufwiesen

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Zunehmend große Mengen an Importdaten<br><br> Komplexe oder ineffiziente Berechnungslogik, einschließlich RLS-Rollen<br><br> Modell nicht vollständig optimiert<br><br> (DQ/LC) Gatewaylatenz<br><br> Langsame Antwortzeiten der DQ-Quellabfrage | Überprüfen Sie die Modellentwürfe.<br><br> Überwachen Sie die Gateway-Leistungsindikatoren. | Weitere Informationen finden Sie im Abschnitt [Optimieren von Modellen](#optimizing-models) in diesem Artikel. |

#### <a name="high-concurrent-report-usage"></a>Hohe gleichzeitige Berichtsnutzung

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Hohe Abfragewartezeiten<br><br> CPU-Sättigung<br><br> DQ/LC-Verbindungslimits überschritten | Überwachen Sie die Metriken für CPU-Auslastung \[[4](#endnote-4)\], Abfragewartezeiten und DQ/LC-Auslastung \[[5](#endnote-5)\] und die Abfragedauer. Schwankungen können auf Parallelitätsprobleme hindeuten. | Skalieren Sie die Kapazität zentral hoch, oder weisen Sie den Inhalt einer anderen Kapazität zu.<br><br> Gestalten Sie Berichte mit weniger visuellen Elementen pro Seite. |

**Hinweise:**    
<a name="endnote-1"></a>\[1\] Durchschnittliche Arbeitsspeicherauslastung (GB) und höchster Arbeitsspeicherverbrauch (GB)   
<a name="endnote-2"></a>\[2\] Entfernte Datasets   
<a name="endnote-3"></a>\[3\] Datasetabfragen, durchschnittliche Abfragedauer für Datasets (ms), Anzahl der Wartevorgänge für Datasets und durchschnittliche Wartezeit für Datasets (ms)   
<a name="endnote-4"></a>\[4\] Anzahl hohe CPU-Auslastung und CPU-Zeit der höchsten Auslastung (letzte sieben Tage)   
<a name="endnote-5"></a>\[5\] Anzahl hohe DQ/LC-Auslastung und DQ/LC-Zeit der höchsten Auslastung (letzte sieben Tage)   

### <a name="why-are-reports-not-loading"></a>Warum werden Berichte nicht geladen?

Wenn Berichte nicht geladen werden können, ist das ein sicheres Zeichen dafür, dass die Kapazität über unzureichenden Arbeitsspeicher verfügt und überbeansprucht ist. Dies kann vorkommen, wenn alle geladenen Modelle aktiv abgefragt werden und daher nicht entfernt werden können und Aktualisierungsvorgänge angehalten oder verzögert wurden. Der Power BI-Dienst versucht 30 Sekunden lang, das Dataset zu laden, und der Benutzer wird ordnungsgemäß über den Fehler informiert mit dem Vorschlag, es in Kürze erneut zu versuchen.

Derzeit gibt es keine Metrik, die auf Fehler beim Laden von Berichten überwacht werden kann. Sie können das Potenzial für dieses Problem erkennen, indem Sie den Systemspeicher überwachen, insbesondere die höchste Auslastung und die Zeit der höchsten Auslastung. Viele entfernte Datasets und eine lange durchschnittliche Wartezeit für Datasetaktualisierungen können darauf hindeuten, dass dieses Problem auftritt.

Wenn dies nur sehr selten vorkommt, wird es möglicherweise nicht als vorrangiges Problem betrachtet. Berichtsbenutzer werden darüber informiert, dass der Dienst ausgelastet ist und sie es nach kurzer Zeit noch einmal versuchen sollen. Wenn dies zu häufig vorkommt, kann das Problem durch zentrales Hochskalieren der Premium-Kapazität oder Zuweisen des Inhalts zu einer anderen Kapazität behoben werden.

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Abfragefehler** überwachen, um festzustellen, wann dies geschieht. Sie können auch die Kapazität neu starten und bei Überlastung des Systems alle Vorgänge zurücksetzen.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Warum werden Aktualisierungen nicht nach Zeitplan gestartet?

Startzeiten für geplante Aktualisierungen sind nicht garantiert. Für den Power BI-Dienst haben interaktive Vorgänge immer höhere Priorität als Hintergrundvorgänge. Die Aktualisierung ist ein Hintergrundvorgang, der stattfinden kann, wenn zwei Bedingungen erfüllt sind:

- Es ist genügend Arbeitsspeicher vorhanden.
- Die Anzahl der unterstützten gleichzeitigen Aktualisierungen für die Premium-Kapazität wird nicht überschritten.

Wenn die Bedingungen nicht erfüllt sind, wird die Aktualisierung in die Warteschlange gestellt, bis die Bedingungen günstig sind.

Beachten Sie bei einer vollständigen Aktualisierung, dass mindestens das Doppelte der aktuellen Arbeitsspeichergröße des Datasets erforderlich ist. Ist nicht genügend Arbeitsspeicher verfügbar, kann die Aktualisierung erst beginnen, wenn durch das Entfernen des Modells Arbeitsspeicher freigegeben wird. Dies bedeutet Verzögerungen, bis ein oder mehrere Datasets inaktiv werden und entfernt werden können.

Die unterstützte maximale Anzahl gleichzeitiger Aktualisierungen ist auf das 1,5-fache der Back-End-V-Kerne (aufgerundet) festgelegt.

Eine geplante Aktualisierung schlägt fehl, wenn sie nicht vor dem Beginn der nächsten geplanten Aktualisierung begonnen werden kann. Bei einer bedarfsgesteuerten Aktualisierung, die manuell über die Benutzeroberfläche ausgelöst wird, werden bis zu drei Ausführungsversuche unternommen, bevor sie fehlschlägt.

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Durchschnittliche Aktualisierungswartezeit (Minuten)** überwachen, um die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start des Vorgangs zu ermitteln.

In der Regel hat es keine administrative Priorität, pünktliche Aktualisierungen der Daten zu erwirken, doch stellen Sie sicher, dass genügend Arbeitsspeicher verfügbar ist. Dies kann das Isolieren von Datasets in Kapazitäten mit bekanntermaßen ausreichenden Ressourcen umfassen. Es ist auch möglich, dass sich Administratoren mit Datasetbesitzern abstimmen, um die geplanten Datenaktualisierungszeiten zu verschieben oder zu verkürzen und so Konflikte zu minimieren. Beachten Sie, dass es einem Administrator nicht möglich ist, die Aktualisierungswarteschlange anzuzeigen oder Zeitpläne für Datasets abzurufen.

### <a name="why-are-refreshes-slow"></a>Warum sind Aktualisierungen langsam?

Aktualisierungen können langsam sein – oder als langsam empfunden werden (wie bei der vorherigen häufig gestellten Frage angesprochen).

Wenn die Aktualisierung tatsächlich langsam ist, kann dies mehrere Ursachen haben:

- Unzureichende CPU (eine Aktualisierung kann sehr CPU-intensiv sein)
- Nicht genügend Arbeitsspeicher, was zum Anhalten der Aktualisierung führt (wodurch die Aktualisierung neu gestartet werden muss, wenn die Bedingungen günstig dafür sind)
- Nicht kapazitätsbedingte Ursachen, einschließlich Reaktionsfähigkeit des Datenquellsystems, Netzwerklatenz, ungültige Berechtigungen oder Gatewaydurchsatz
- Datenvolumen – ein guter Grund für das Konfigurieren einer inkrementellen Aktualisierung wie unten erläutert

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Durchschnittliche Aktualisierungsdauer (Minuten)** überwachen, um einen Benchmark für den Vergleich im zeitlichen Verlauf zu ermitteln, und die Metrik **Durchschnittliche Aktualisierungswartezeit (Minuten)** überwachen, um die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start des Vorgangs zu ermitteln.

Die inkrementelle Aktualisierung kann die Dauer der Datenaktualisierung erheblich verkürzen, insbesondere bei großen Modelltabellen. Die inkrementelle Aktualisierung bietet vier Vorteile:

- **Aktualisierungen sind schneller**: Es muss nur eine Teilmenge einer Tabelle geladen werden, wodurch sich die CPU- und Arbeitsspeicherauslastung reduziert, und bei der Aktualisierung mehrerer Partitionen kann die Parallelität höher sein.
- **Aktualisierungen erfolgen nur bei Bedarf**: Richtlinien für die inkrementelle Aktualisierung können so konfiguriert werden, dass Daten nur dann geladen werden, wenn sie geändert wurden.
- **Aktualisierungen sind zuverlässiger**: Kürzere aktive Verbindungen mit flüchtigen Datenquellsystemen sind weniger anfällig für ein Trennen der Verbindung.
- **Modelle bleiben klein**: Richtlinien für die inkrementelle Aktualisierung können so konfiguriert werden, dass der Verlauf über ein verschiebbares Zeitfenster hinaus automatisch entfernt wird.

Weitere Informationen finden Sie unter [Inkrementelle Aktualisierung in Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Warum werden Datenaktualisierungen nicht abgeschlossen?

Wenn die Datenaktualisierung beginnt, aber nicht abgeschlossen wird, kann dies mehrere Ursachen haben:

- Nicht genügend Arbeitsspeicher, auch wenn nur ein Modell in der Premium-Kapazität vorhanden ist, d.h. das Modell ist sehr groß
- Nicht kapazitätsbedingte Ursachen, einschließlich Verbindungstrennung vom Datenquellsystem, ungültige Berechtigungen oder Gatewayfehler

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Aktualisierungsfehler aufgrund von Arbeitsspeichermangel** überwachen.

## <a name="optimizing-models"></a>Optimieren von Modellen

Ein optimaler Modellentwurf ist entscheidend für die Bereitstellung einer effizienten und skalierbaren Lösung. Eine umfassende Erläuterung geht jedoch über den Rahmen dieses Artikels hinaus. Stattdessen werden in diesem Abschnitt wichtige Bereiche genannt, die beim Optimieren von Modellen zu berücksichtigen sind.

### <a name="optimizing-power-bi-hosted-models"></a>Optimieren von Power BI-gehosteten Modellen

Eine Optimierung von Modellen, die in einer Premium-Kapazität gehostet werden, kann auf Datenquellen- und Modellebene erzielt werden.

Sehen Sie sich die Optimierungsmöglichkeiten für ein Importmodell an:

![Optimierungsmöglichkeiten für ein Importmodell](media/service-premium-capacity-optimize/import-model-optimizations.png)

Auf Datenquellenebene:

- Relationale Datenquellen können optimiert werden, um eine schnellstmögliche Aktualisierung sicherzustellen. Dazu werden Daten vorab integriert, geeignete Indizes angewendet, Tabellenpartitionen definiert, die sich an Zeiträumen für die inkrementelle Aktualisierung orientieren, und Berechnungen materialisiert (anstelle von berechneten Modelltabellen und -spalten) oder eine Berechnungslogik zu Sichten hinzugefügt.
- Nicht relationale Datenquellen können vorab in relationale Speicher integriert werden.
- Stellen Sie sicher, dass Gateways über ausreichende Ressourcen verfügen, vorzugsweise auf dedizierten Computern, mit ausreichender Netzwerkbandbreite und in unmittelbarer Nähe der Datenquellen.

Auf Modellebene:

- Mit Power Query-Abfrageentwürfen können komplexe Transformationen minimiert oder entfernt werden, insbesondere solche, bei denen verschiedene Datenquellen zusammengeführt werden (Data Warehouses können dies während ihrer ETL-Phase (Extract-Transform-Load) erreichen). Außerdem kann sichergestellt werden, dass geeignete Datenschutzebenen für die Datenquellen festgelegt sind, sodass Power BI keine vollständigen Ergebnisse laden muss, um ein abfragenübergreifendes kombiniertes Ergebnis zu erstellen.
- Die Modellstruktur bestimmt die zu ladenden Daten und wirkt sich direkt auf die Modellgröße aus. Es kann so entworfen werden, dass ein Laden nicht benötigter Daten vermieden wird, indem Spalten entfernt, Zeilen (insbesondere Verlaufsdaten) entfernt oder zusammengefasste Daten geladen werden (auf Kosten des Ladens von Detaildaten). Eine drastische Verringerung der Größe kann erreicht werden, indem Sie Spalten mit hoher Kardinalität (insbesondere Textspalten) entfernen, die nicht sehr effizient gespeichert oder komprimiert werden.
- Die Abfrageleistung des Modells kann durch Konfigurieren von Beziehungen mit nur einer Richtung verbessert werden, es sei denn, es gibt einen zwingenden Grund für eine bidirektionale Filterung. Ziehen Sie auch eine Verwendung der [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function)-Funktion anstelle der bidirektionalen Filterung in Betracht.
- Aggregationstabellen können durch das Laden vorab zusammengefasster Daten schnelle Abfrageantworten erzielen, was jedoch zu einem größeren Modell und längeren Aktualisierungszeiten führt. Generell sollten Aggregationstabellen sehr großen Modellen oder Entwürfen mit zusammengesetzten Modellen vorbehalten sein.
- Berechnete Tabellen und Spalten erhöhen die Modellgröße und führen zu längeren Aktualisierungszeiten. Im Allgemeinen können eine geringere Speichergröße und eine schnellere Aktualisierungszeit erreicht werden, wenn die Daten in der Datenquelle materialisiert oder berechnet werden. Wenn das nicht möglich ist, kann die Verwendung benutzerdefinierter Power Query-Spalten eine verbesserte Speicherkomprimierung bieten.
- Vielleicht besteht die Möglichkeit, DAX-Ausdrücke für Measures und RLS-Regeln zu optimieren, und eventuell die Logik neu zu schreiben, um kostspielige Formeln zu vermeiden.
- Die inkrementelle Aktualisierung kann die Aktualisierungszeit drastisch verkürzen sowie die Arbeitsspeicher- und CPU-Auslastung verringern. Die inkrementelle Aktualisierung kann auch so konfiguriert werden, dass Verlaufsdaten entfernt und somit Modellgrößen gering gehalten werden.
- Ein Modell kann als zwei Modelle umgestaltet werden, wenn unterschiedliche und widersprüchliche Abfragemuster vorhanden sind. Beispielsweise stellen einige Berichte allgemeine Aggregate im gesamten Verlauf dar und können eine Latenz von 24 Stunden tolerieren. Andere Berichte betreffen die aktuellen Daten und benötigen einen präzisen Zugriff auf einzelne Transaktionen. Anstatt ein einzelnes Modell für alle Berichte zu entwerfen, erstellen Sie zwei Modelle, die für die jeweilige Anforderung optimiert sind.

Sehen Sie sich die Optimierungsmöglichkeiten für ein DirectQuery-Modell an. Da das Modell Abfrageanforderungen an die zugrunde liegende Datenquelle ausgibt, ist die Optimierung der Datenquelle für die Bereitstellung reaktionsfähiger Modellabfragen von ausschlaggebender Bedeutung.

 ![Optimierungsmöglichkeiten für ein DirectQuery-Modell](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Auf Datenquellenebene:

- Die Datenquelle kann optimiert werden, um eine schnellstmögliche Abfrage zu gewährleisten. Dazu werden Daten vorab integriert (was auf Modellebene nicht möglich ist), geeignete Indizes angewendet, Tabellenpartitionen definiert, zusammengefasste Daten materialisiert (mit indizierten Sichten) und die Berechnungsmenge minimiert. Das beste Ergebnis wird erzielt, wenn Pass-Through-Abfragen nur innere Joins zwischen indizierten Tabellen oder Sichten filtern und ausführen müssen.
- Stellen Sie sicher, dass Gateways über ausreichende Ressourcen verfügen, vorzugsweise auf dedizierten Computern, mit ausreichender Netzwerkbandbreite und in unmittelbarer Nähe der Datenquelle.

Auf Modellebene:

- Power Query-Abfrageentwürfe sollten vorzugsweise keine Transformationen anwenden. Versuchen Sie andernfalls, Transformationen auf ein absolutes Minimum zu beschränken.
- Die Abfrageleistung des Modells kann durch Konfigurieren von Beziehungen mit nur einer Richtung verbessert werden, es sei denn, es gibt einen zwingenden Grund für eine bidirektionale Filterung. Außerdem sollten Modellbeziehungen unter der Annahme konfiguriert werden, dass referenzielle Integrität erzwungen wird (wenn das der Fall ist), was dazu führt, dass Datenquellenabfragen effizientere innere Joins (anstelle von äußeren Joins) verwenden.
- Vermeiden Sie es, benutzerdefinierte Power Query-Spalten oder vom Modell berechnete Spalten zu erstellen, sondern materialisieren Sie diese nach Möglichkeit in der Datenquelle.
- Vielleicht besteht die Möglichkeit, DAX-Ausdrücke für Measures und RLS-Regeln zu optimieren, und eventuell die Logik neu zu schreiben, um kostspielige Formeln zu vermeiden.

Sehen Sie sich die Optimierungsmöglichkeiten für ein zusammengesetztes Modell an. Ein zusammengesetztes Modell ermöglicht eine Mischung aus Import- und DirectQuery-Tabellen.

![Optimierungsmöglichkeiten für ein zusammengesetztes Modell](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Im Allgemeinen trifft die Optimierung für Import- und DirectQuery-Modelle auf Tabellen des zusammengesetzten Modells zu, die diese Speichermodi verwenden.
- In der Regel sollten Sie einen ausgeglichenen Entwurf anstreben, indem Sie Tabellen des Dimensionstyps (die Geschäftsentitäten darstellen) als Speichermodus „Dual“ und Tabellen des Faktentyps (häufig große Tabellen, die operative Fakten darstellen) als Speichermodus „DirectQuery“ konfigurieren. Der Speichermodus „Dual“ bedeutet, dass sowohl der Speichermodus „Import“ als auch „DirectQuery“ verwendet werden. Dadurch kann der Power BI-Dienst den effizientesten Speichermodus ermitteln, der beim Generieren einer systemeigenen Abfrage für Pass-Through verwendet werden soll.
- Stellen Sie sicher, dass Gateways über ausreichende Ressourcen verfügen, vorzugsweise auf dedizierten Computern, mit ausreichender Netzwerkbandbreite und in unmittelbarer Nähe der Datenquellen.
- Aggregationstabellen, die als Speichermodus „Import“ konfiguriert sind, können drastische Verbesserungen der Abfrageleistung bewirken, wenn sie zur Zusammenfassung von Tabellen des Faktentyps im Speichermodus „DirectQuery“ verwendet werden. In diesem Fall führen Aggregationstabellen zu einem größeren Modell und längeren Aktualisierungszeiten, doch ist dies häufig ein akzeptabler Kompromiss für schnellere Abfragen.

### <a name="optimizing-externally-hosted-models"></a>Optimieren von extern gehosteten Modellen

Viele Optimierungsmöglichkeiten, die im Abschnitt [Optimieren von Power BI-gehosteten Modellen](#optimizing-power-bi-hosted-models) erläutert werden, gelten auch für Modelle, die mit Azure Analysis Services und SQL Server Analysis Services entwickelt wurden. Eindeutige Ausnahmen sind bestimmte Features, die derzeit nicht unterstützt werden, einschließlich zusammengesetzter Modelle und Aggregationstabellen.

Eine zusätzliche Überlegung bei extern gehosteten Datasets betrifft das Datenbankhosting in Bezug auf den Power BI-Dienst. Bei Azure Analysis Services bedeutet dies, dass die Azure-Ressource in derselben Region wie der Power BI-Mandant (ursprüngliche Region) erstellt wird. Bei SQL Server Analysis Services für IaaS bedeutet dies, dass der virtuelle Computer in derselben Region gehostet wird, und für die lokale Umgebung bedeutet es die Sicherstellung einer effizienten Gatewayeinrichtung.

Außerdem kann es von Interesse sein, dass Azure Analysis Services-Datenbanken und tabellarische SQL Server Analysis Services-Datenbanken es erforderlich machen, dass ihre Modelle vollständig in den Arbeitsspeicher geladen werden und dort die ganze Zeit verbleiben, um Abfragen zu unterstützen. Wie beim Power BI-Dienst muss ausreichend Arbeitsspeicher für die Aktualisierung vorhanden sein, wenn das Modell während der Aktualisierung online bleiben muss. Im Gegensatz zum Power BI-Dienst gibt es kein Konzept, dass Modelle je nach Nutzung automatisch in den Arbeitsspeicher eingebunden und daraus entfernt werden. Power BI Premium bietet daher einen effizienteren Ansatz zur Maximierung von Modellabfragen bei geringerer Arbeitsspeicherauslastung.

## <a name="capacity-planning"></a>Kapazitätsplanung

Die Größe einer Premium-Kapazität bestimmt die verfügbaren Arbeitsspeicher- und Prozessorressourcen sowie die für die Kapazität zutreffenden Grenzwerte. Die Anzahl der Premium-Kapazitäten ist ebenfalls zu berücksichtigen, da das Erstellen mehrerer Premium-Kapazitäten dazu beitragen kann, Workloads voneinander zu isolieren. Der Speicher beträgt 100 TB pro Kapazitätsknoten, und dies ist wahrscheinlich für alle Workloads mehr als ausreichend.

Die Festlegung der Größe und Anzahl von Premium-Kapazitäten kann eine Herausforderung darstellen, insbesondere bei den anfänglichen Kapazitäten, die von Ihnen erstellt werden. Der erste Schritt bei der Dimensionierung der Kapazität besteht darin, die durchschnittliche Workload zu verstehen, die die erwartete tägliche Nutzung darstellt. Es ist wichtig zu erkennen, dass nicht alle Workloads gleich sind. Beispielsweise kann an einem Ende des Spektrums problemlos eine Anzahl von 100 gleichzeitigen Benutzern erreicht werden, die auf eine einzelne Berichtsseite zugreifen, die wiederum ein einzelnes visuelles Element enthält. Doch kann am anderen Ende des Spektrums eine Anzahl von 100 gleichzeitigen Benutzern, die auf 100 verschiedene Berichte mit jeweils 100 visuellen Elementen auf der Berichtsseite zugreifen, ganz andere Anforderungen an die Kapazitätsressourcen stellen.

Kapazitätsadministratoren müssen daher viele Faktoren berücksichtigen, die für Ihre Umgebung, die Inhalte und die erwartete Nutzung spezifisch sind. Das übergeordnete Ziel ist es, die Kapazitätsauslastung zu maximieren und gleichzeitig konsistente Abfragezeiten, akzeptable Wartezeiten und Entfernungsraten bereitzustellen. Dabei sind unter anderem die folgenden Faktoren zu berücksichtigen:

- **Modellgröße und Datenmerkmale**: Importmodelle müssen vollständig in den Arbeitsspeicher geladen werden, um Abfragen oder Aktualisierungen zu ermöglichen. Für LC/DQ-Datasets kann eine beträchtliche Prozessorzeit und möglicherweise erheblicher Arbeitsspeicher erforderlich sein, um komplexe Measures oder RLS-Regeln auszuwerten. Arbeitsspeicher- und Prozessorgröße sowie der LC/DQ-Abfragedurchsatz werden durch die Kapazitätsgröße eingeschränkt.
- **Gleichzeitige aktive Modelle**: Die gleichzeitige Abfrage verschiedener Importmodelle bietet optimale Reaktionsfähigkeit und Leistung, wenn diese im Arbeitsspeicher verbleiben. Es muss genügend Arbeitsspeicher zum Hosten aller stark abgefragten Modelle vorhanden sein sowie zusätzlicher Arbeitsspeicher, um deren Aktualisierung zu ermöglichen.
- **Aktualisierung des Importmodells**: Der Aktualisierungstyp (vollständig oder inkrementell), die Dauer und Komplexität von Power Query-Abfragen und die Logik berechneter Tabellen/Spalten können sich auf den Arbeitsspeicher und insbesondere die Prozessorauslastung auswirken. Gleichzeitige Aktualisierungen werden durch die Kapazitätsgröße eingeschränkt (1,5 x Back-End-V-Kerne, aufgerundet).
- **Gleichzeitige Abfragen**: Viele gleichzeitige Abfragen können zu nicht reagierenden Berichten führen, wenn Prozessor- oder LC/DQ-Verbindungen die Kapazitätsgrenze überschreiten. Dies gilt insbesondere für Berichtsseiten, die viele visuelle Elemente enthalten.
- **Dataflows und paginierte Berichte**: Die Kapazität kann so konfiguriert werden, dass Dataflows und paginierte Berichte unterstützt werden, wobei jeder einen konfigurierbaren maximalen Prozentsatz des Kapazitätsspeichers erfordert. Der Arbeitsspeicher wird Dataflows dynamisch zugeordnet, ist paginierten Berichten jedoch statisch zugeordnet.

Zusätzlich zu diesen Faktoren können Kapazitätsadministratoren das Erstellen mehrerer Kapazitäten in Betracht ziehen. Mehrere Kapazitäten ermöglichen das Isolieren von Workloads und können so konfiguriert werden, dass Workloads mit Priorität garantierte Ressourcen zur Verfügung stehen. Es können beispielsweise zwei Kapazitäten erstellt werden, um unternehmenskritische Workloads von SSBI-Workloads (Self-Service-BI) zu trennen. Die unternehmenskritische Kapazität kann verwendet werden, um große Unternehmensmodelle zu isolieren und ihnen garantierte Ressourcen bereitzustellen, wobei der Erstellungszugriff nur der IT-Abteilung erteilt wird. Die SSBI-Kapazität kann verwendet werden, um eine wachsende Anzahl kleinerer Modelle zu hosten, wobei der Zugriff den Business Analysts gewährt wird. Bei der SSBI-Kapazität kann es gelegentlich zu tolerierbaren Wartezeiten bei der Abfrage oder Aktualisierung kommen.

Im Laufe der Zeit können Kapazitätsadministratoren Arbeitsbereiche kapazitätsübergreifend ausgleichen, indem sie Inhalte zwischen Arbeitsbereichen oder Arbeitsbereiche zwischen Kapazitäten verschieben und Kapazitäten zentral hoch- oder herunterskalieren. Im Allgemeinen wird zum Hosten größerer Modelle eine zentrale Hochskalierung und für höhere Parallelität eine horizontale Hochskalierung vorgenommen.

Durch den Erwerb einer Lizenz werden dem Mandanten V-Kerne bereitgestellt. Bei Erwerb eines **P3**-Abonnements können eine oder bis zu vier Premium-Kapazitäten erstellt werden, d.h. 1 x P3 oder 2 x P2 oder 4 x P1. Außerdem kann vor der Erweiterung einer P2-Kapazität auf eine P3-Kapazität die Aufteilung der V-Kerne in zwei P1-Kapazitäten in Betracht gezogen werden.

## <a name="testing-approaches"></a>Testansätze

Nachdem eine Kapazitätsgröße festgelegt wurde, können Tests durchgeführt werden, indem eine kontrollierte Umgebung erstellt wird. Eine praktische und wirtschaftliche Möglichkeit besteht darin, eine Azure-Kapazität (A-SKUs) zu erstellen, wobei darauf zu achten ist, dass eine P1-Kapazität dieselbe Größe wie eine A4-Kapazität und die P2- und P3-Kapazität die gleiche Größe wie die A5- bzw. A6-Kapazität hat. Azure-Kapazitäten können schnell erstellt und auf Stundenbasis abgerechnet werden. So können sie nach Abschluss der Tests einfach gelöscht werden, um anfallende Kosten zu vermeiden.

Der Testinhalt kann zu den Arbeitsbereichen hinzugefügt werden, die in der Azure-Kapazität erstellt wurden, und dann kann ein einzelner Benutzer Berichte ausführen, um eine realistische und repräsentative Workload von Abfragen zu generieren. Wenn Importmodelle vorhanden sind, sollte auch eine Aktualisierung für jedes Modell durchgeführt werden. Überwachungstools können dann zum Überprüfen aller Metriken verwendet werden, um die Ressourcennutzung zu verstehen.

Es ist wichtig, dass die Tests wiederholbar sind. Tests sollten mehrmals ausgeführt werden und jedes Mal ungefähr dasselbe Ergebnis liefern. Der Durchschnitt dieser Ergebnisse kann verwendet werden, um eine Workload unter echten Produktionsbedingungen zu extrapolieren und abzuschätzen.

Wenn Sie bereits über eine Kapazität und die Berichte verfügen, für die Sie einen Auslastungstest durchführen möchten, verwenden Sie das [PowerShell-Tool zum Generieren einer Auslastung](https://aka.ms/PowerBILoadTestingTool), um schnell einen Auslastungstest zu erzeugen. Mit dem Tool können Sie abschätzen, wie viele Instanzen jedes Berichts ihre Kapazität innerhalb einer Stunde ausführen kann. Sie können das Tool verwenden, um die Fähigkeit der Kapazität zum Rendern einzelner Berichte oder zum parallelen Rendern mehrerer verschiedener Berichte abzuschätzen. Weitere Informationen erhalten Sie im Video [Microsoft Power BI: Premium-Kapazität](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Zum Generieren eines komplexeren Tests sollten Sie die Entwicklung einer Auslastungstestanwendung in Betracht ziehen, die eine realistische Workload simuliert. Weitere Informationen erhalten Sie im Webinar zum Thema [Testen von Power BI-Anwendungen mit dem Visual Studio-Auslastungstest](https://powerbi.microsoft.com/blog/week-4-11-webinars-load-testing-power-bi-applications-with-visual-studio-load-test-and-getting-started-with-cds-for-apps-based-model-driven-apps/).

## <a name="acknowledgements"></a>Danksagungen

Dieser Artikel wurde von Peter Myers, Data Platform MVP und unabhängiger BI-Experte bei [Bitwise Solutions](https://www.bitwisesolutions.com.au/), verfasst.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Szenarios mit Premium-Kapazitäten](service-premium-capacity-scenarios.md)   
  
Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)