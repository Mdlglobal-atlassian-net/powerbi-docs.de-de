---
title: Tipps und Tricks für Fragen mit Q&A
description: Tipps und Tricks für Fragen mit Q&A in Power BI
author: mihart
ms.reviewer: Mohammad
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: d97ff72c385edd4c59c6eb72ce1eb873656923c9
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376820"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Tipps zum Stellen von Fragen mit Power BI Q&A

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Wörter und Begriffe, die von Q&A erkannt werden
Die Liste mit Schlüsselwörtern auf dieser Seite ist nicht vollständig.  Die beste Möglichkeit, um festzustellen, ob Power BI ein Schlüsselwort erkennt, besteht darin, es durch Eingeben im Fragefeld auszuprobieren.  Wenn das Wort oder der Begriff ausgegraut ist, erkennt Power BI Wort oder Begriff nicht.

In der nachstehenden Liste wird Präsens verwendet, jedoch werden in den meisten Fällen alle Zeitformen erkannt. Beispielsweise umfasst „is“ auch **are**, **was**, **were**, **will be**, **have**, **has**, **had**, **will have**, **has got**, **do**, **does**, **did**.  Außerdem ist in „sort“ auch **sorted** und **sorting** enthalten.  Darüber hinaus erkennt Power BI Singular- und Pluralversionen eines Worts und schließt diese mit ein. 

> [!NOTE]
> Q&A steht auch in der [Microsoft Power BI-App für iOS auf iPads, iPhones und iPod Touch-Geräten](mobile/mobile-apps-ios-qna.md) zur Verfügung.
>  


|Kategorie  |Schlüsselwörter  |Column3  |
|---------|---------|---------|
|**Aggregate**     | total, sum, amount, number, quantity, count, average, most, least, fewest, largest, smallest, highest, biggest, maximum, max, greatest, lowest, littlest, minimum, min          |
|     |         |         
**Artikel**     |  a, an, the              |
|     |         |         
|**Leerzeichen und Boolesch**     |   blank, empty, null, prefixed with „non“ or „non-“, empty string, empty text, true, t, false, f          |
|     |         |         |
|**Vergleiche**     |   vs, versus, compared to, compared with            |
|     |         |         |
|**Konjunktionen**     |  and, or, each of, with, versus, &, and, but, nor, along with, in addition to       |         
|          |         |
|**Kontraktionen**     |  Q&A erkennt fast alle Kontraktionen, probieren Sie es aus.  Hier sind einige Beispiele: didn't, haven't, he'd, he's, isn't, it's, she'll, they'd, weren't, who's, won't, wouldn't.          |
|        |         |
|**Datumsangaben**     |       Power BI erkennt die meisten Datumsbegriffe (day, week, month, year, quarter, decade, …) und Daten in vielen verschiedenen Formaten (siehe unten). Power BI erkennt außerdem die folgenden Schlüsselwörter: MonthName, Days 1-31, decade. Beispiele: January 3rd of 1995, January 3rd 1995, jan 03 1995, 3 Jan 1995, the 3rd of January, January 1995, 1995 January, 1995-01, 01/1995, Monatsnamen         |
|        |         |
|**Relative Datumsangaben**     |   today, right now, current time, yesterday, tomorrow, the current, next, the coming, last, previous, ago, before now, sooner than, after, later than, from, at, on, from now, after now, in the future, past, last, previous, within, in, over, N days ago, N days from now, next, once, twice.|
|    |  Beispiel: count of orders in the past 6 days.  |            |
|        |         |
|**Gleichheit (Bereich)**     |   in, equal to, =, after, is more than, in, between, before  |
|  |Beispiele: Order year is before 2012? Price equals between 10 and 20? Is the age of John greater than 40? Total sales in 200-300?              |
|        |         |
|**Gleichheit (Wert)**     |   is, equal, equal to, in, of, for, within, is in, is on |
|   | Beispiele: Welche Produkte sind grün? Order date equals 2012. Is the age of John 40? Total sales that aren't equal to 200? Order date of 1/1/2016. 10 in price? Green for color? 10 in price?              |
|        |         |
|**Namen**     |       Wenn eine Spalte im Dataset den Begriff „Name“ (z.B. EmployeeName) enthält, erkennt Q&A, dass die Werte in dieser Spalte Namen sind. Sie können Fragen stellen wie „welche Mitarbeiter heißen Robert“.          |
|        |         |
**Pronomen**  | he, him, himself, his, she, herself, her, hers, it, itself, its, they, their, them, themselves, theirs, this, these, that, those
|**Abfragebefehle**     |    sorted, sort by, direction, group, group by, by, show, list, display, give me, name, just, only, arrange, rank, compare, to, with, against, alphabetically, ascending, descending, order             |
|        |         |
|**Bereich**     |      greater, more, larger, above, over, >, less, smaller, fewer, below, under, <, at least, no less than, >=, at most, no more than, <=, in, between, in the range of, from, later, earlier, sooner, after, on, at, later than, after, since, starting with, starting from, ending with           |
|        |         |
**Uhrzeiten**  |am, pm, o'clock, noon, midnight, hour, minute, second, hh:mm:ss  |
|  |  Beispiele: 10 pm, 10:35 pm, 10:35:15 pm, 10 o'clock, noon, midnight, hour, minute, second.  |
|  |  |
|**Top N**     |     (Reihenfolge, Rangfolge): top, bottom, highest, lowest, first, last, next, earliest, newest, oldest, latest, most recent, next            |
|        |         |
|**Visualisierungstypen**     |  alle nativen Power BI-Visualisierungstypen.  Wenn die Option im Bereich „Visualisierungen“ vorhanden ist, können Sie sie in Ihre Frage einschließen.  Die Ausnahme dieser Regel stellen hierbei [Power BI-Visuals](../developer/visuals/power-bi-custom-visuals.md) dar, die Sie manuell dem Bereich „Visualisierungen“ hinzugefügt haben.  |
|  |  Beispiel: show districts by month and sales total as bar chart               |
|        |         |
|**W-Fragewörter (Beziehung, qualifiziert)**  | when, where, which, who, whom, how many, how much, how many times, how often, how frequently, amount, number, quantity, how long, what                |

## <a name="qa-helps-you-phrase-the-question"></a>Q&A hilft Ihnen beim Formulieren der Frage
Q&A versucht stets, die gestellte Frage zu verstehen und zu beantworten. Dabei versucht Q&A, sie auf verschiedene Weise zu verstehen. Für alle diese Formulierungen können Sie die Aktion vollständig, teilweise oder gar nicht akzeptieren. Beim Eingeben Ihrer Frage in Q&A geschieht Folgendes:

* Die Wörter und Fragen werden automatisch vervollständigt. Es kommen verschiedene Strategien zur Anwendung, einschließlich der automatischen Vervollständigung wiedererkennbarer Wörter, gespeicherter Fragen und Nutzung zuvor bereits verwendeter Fragen, die gültige Antworten zurückgegeben haben. Wenn mehrere Optionen für die automatische Vervollständigung verfügbar sind, werden sie in einer Dropdownliste angezeigt.
* Die Rechtschreibung wird korrigiert.
* Eine Vorschau der Antwort wird in Form einer Visualisierung angezeigt. Diese Visualisierung wird immer wieder aktualisiert, wenn Sie weitere Eingaben vornehmen und die Frage bearbeiten (es wird nicht darauf gewartet, dass Sie die EINGABETASTE drücken).
* Es werden Ersatzbegriffe aus den zugrunde liegenden Datasets vorgeschlagen, wenn Sie den Cursor wieder in das Fragefeld setzen.
* Die Frage wird anhand der Daten in den zugrunde liegenden Datasets umformuliert. Q&A ersetzt die von Ihnen verwendeten Wörter durch Synonyme aus den zugrunde liegenden Datasets. Wenn Sie die Umformulierung lesen, wissen Sie, ob Q&A Ihre Frage verstanden hat. 
* Fügt einem nicht verstandenen Wort einen doppelten Unterstrich hinzu.
* Fügt einem verstandenen Wort einen einfachen Unterstrich hinzu.
* Ermöglicht es Ihnen, den Besitzer des Berichts oder Dashboards zu kontaktieren, wenn Ihr Begriff nicht gefunden wird oder wenn Ihre Frage keine Ergebnisse ergibt.

## <a name="dont-stop-now"></a>Das ist noch nicht alles
Halten Sie die Konversation am Laufen, nachdem Q&A Ihre Ergebnisse anzeigt! Nutzen Sie die interaktiven Features der Visualisierung und von Q&A, um weitere Einblicke zu gewinnen.

## <a name="next-steps"></a>Nächste Schritte
Zurück zu [Q&A in Power BI](end-user-q-and-a.md)  

[Power BI – Grundkonzepte](end-user-basic-concepts.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

