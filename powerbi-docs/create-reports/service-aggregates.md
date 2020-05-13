---
title: Verwenden von Aggregaten (Summe, Durchschnitt usw.) im Power BI-Dienst
description: Erfahren Sie, wie Sie die Aggregation in einem Diagramm (Summe, Durchschnitt, Maximum usw.) im Power BI-Dienst ändern können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 469f217426f4c66c6d1d0d72192efbda8391689c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83315292"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Verwenden von Aggregaten (Summe, Durchschnitt usw.) im Power BI-Dienst

## <a name="what-is-an-aggregate"></a>Was ist ein Aggregat?

Unter Umständen möchten Sie Werte in Ihren Daten mathematisch miteinander kombinieren. Dabei kann es sich um die mathematische Operation zum Ermitteln von Summe, Durchschnitt, Maximum, Anzahl usw. handeln. Das Kombinieren von Werten in Daten wird als *aggregieren* bezeichnet. Das Ergebnis dieser mathematischen Operation ist ein *Aggregat*.

Wenn im Power BI-Dienst und Power BI Desktop Visualisierungen erstellt werden, können dabei Daten aggregiert werden. Häufig handelt es sich bei dem Aggregat bereits um die benötigten Werte, in anderen Fällen möchten Sie die Werte aber vielleicht auch auf andere Weise aggregieren,  z.B. mit einer Summe anstelle eines Durchschnittswerts. Es gibt verschiedene Möglichkeiten zum Verwalten und Ändern des Aggregats, das in einer Visualisierung in Power BI verwendet wird.

Zunächst betrachten Sie die *Datentypen*, da der Typ der Daten bestimmt, wie und ob sie in Power BI aggregiert werden können.

## <a name="types-of-data"></a>Datentypen

Die meisten Datasets enthalten mehr als einen Datentyp. Grundsätzlich sind die Daten entweder numerisch oder nicht numerisch. Power BI kann numerische Daten als Summe, Durchschnitt, Anzahl, Minimum, Varianz und vieles mehr aggregieren. Der Dienst kann sogar Textdaten aggregieren, diese werden häufig als *Kategoriedaten* bezeichnet. Wenn Sie versuchen, ein Kategoriefeld zu aggregieren, indem Sie es in einem rein numerischen Bereich wie **Werte** oder **QuickInfos** platzieren, zählt Power BI die Vorkommnisse jeder Kategorie oder die Anzahl verschiedener Vorkommnisse jeder Kategorie. Für bestimmte Arten von Daten, wie Datumsangaben, gibt es eigene Aggregationsoptionen: früheste, letzte, erste und letzte.

Betrachten Sie folgendes Beispiel:

- **Units Sold** und **Manufacturing Price** sind Spalten mit numerischen Daten.

- **Segment**, **Country**, **Product**, **Month** und **Month Name** enthalten Kategoriedaten.

   ![Screenshot: Beispieldataset](media/service-aggregates/power-bi-aggregate-chart.png)

Beim Erstellen einer Visualisierung in Power BI aggregiert der Dienst numerische Felder über ein Kategoriefeld (standardmäßig als *Summe*).  Beispiele sind: „Units Sold ***by Product***“, „Units Sold ***by Month***“ und „Manufacturing Price ***by Segment***“ (Verkaufte Einheiten nach Produkt, verkaufte Einheiten nach Monat, Produktionskosten nach Segment). Power BI bezeichnet einige numerische Felder als **Measures**. Measures sind im Power BI-Berichts-Editor leicht zu erkennen: Die Liste **Felder** führt Measures mit dem Symbol „∑“ auf. Weitere Informationen finden Sie in der [Einführung in den Berichts-Editor in Power BI](service-the-report-editor-take-a-tour.md).

![Screenshot: Power BI mit hervorgehobener Felderliste](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Warum funktionieren Aggregate nicht wie ich mir das vorstelle?

Die Arbeit mit Aggregaten im Power BI-Dienst kann verwirrend sein. Möglicherweise verfügen Sie über ein numerisches Feld und Power BI lässt nicht zu, dass Sie die Aggregation ändern. Oder haben Sie ein Feld (beispielsweise ein Jahr), das nicht aggregiert werden soll, sondern für das Sie lediglich die Anzahl von Vorkommen ermitteln möchten?

In der Regel liegt das zugrunde liegende Problem bei der Felddefinition im Dataset. Möglicherweise hat der Besitzer des Datasets das Feld als Text definiert, was erklären würde, wieso Power BI weder die Summe noch den Durchschnitt ermitteln kann. [Die Kategorisierung eines Felds kann allerdings nur vom Besitzer des Datasets geändert werden.](../transform-model/desktop-measures.md) Wenn Sie also über Besitzerberechtigungen für das Dataset verfügen (in Power BI Desktop oder in dem Programm, in dem das Dataset erstellt wurde, z. B. Excel), können Sie das Problem beheben. Andernfalls müssen Sie den Besitzer des Datasets um Hilfe bitten.  

Am Ende dieses Artikels finden Sie einen gesonderten Abschnitt namens [**Zu beachtende Aspekte und Problembehandlung**](#considerations-and-troubleshooting). Dort finden Sie Tipps und Anleitungen. Wenn Sie dort keine passende Antwort finden, stellen Sie Ihre Frage im [Forum der Power BI-Community](https://community.powerbi.com). Sie erhalten eine umgehende Antwort direkt vom Power BI-Team.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Ändern, wie ein numerisches Feld aggregiert wird

Angenommen, Sie haben ein Diagramm, in dem die verkauften Einheiten für verschiedene Produkte addiert werden. Sie benötigen aber den Mittelwert.

1. Erstellen Sie ein **Säulendiagramm (gruppiert)** , das ein Measure und eine Kategorie verwendet. In diesem Beispiel verwenden wir „Units Sold by Product“.  Power BI erstellt standardmäßig ein Diagramm mit der Summe der verkauften Einheiten (ziehen Sie das Measure in das Feld **Wert**) für jedes Produkt (ziehen Sie die Kategorie in das Feld **Achse**).

   ![Screenshot: Diagramm, Bereich „Visualisierungen“ und Liste „Felder“ mit Summe hervorgehoben](media/service-aggregates/power-bi-aggregate-sum.png)

1. Klicken Sie im Bereich **Visualisierungen** mit der rechten Maustaste auf das Measure, und wählen Sie dann den gewünschten Aggregattyp aus. Wählen Sie in diesem Fall **Durchschnitt** aus. Wenn die benötigte Aggregation nicht angezeigt wird, finden Sie weitere Informationen unten im Abschnitt [**Zu beachtende Aspekte und Problembehandlung**](#considerations-and-troubleshooting).

   ![Screenshot: Aggregationsliste mit ausgewählter und hervorgehobener Option „Durchschnitt“](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Die in der Dropdownliste verfügbaren Optionen variieren je nach ausgewähltem Feld und je nachdem, wie der Besitzer des Datasets das Feld kategorisiert hat.

1. Die Visualisierung wird nun mit einem Durchschnittswert aggregiert.

   ![Screenshot: Diagramm mit dem Durchschnitt der verkauften Einheiten nach Produkt](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Möglichkeiten zum Aggregieren von Daten

Hier sind einige der Optionen aufgeführt, die möglicherweise zum Aggregieren eines Felds zur Verfügung stehen:

- **Nicht zusammenfassen**. Wenn diese Option ausgewählt wird, behandelt Power BI alle Werte im Feld separat und fasst sie nicht zusammen. Verwenden Sie diese Option, wenn Sie über eine numerische ID-Spalte verfügen, die der Dienst nicht zusammenfassen sollte.

- **Summe**. Mit dieser Option werden alle Werte in diesem Feld addiert.

- **Mittelwert**. Ermittelt den arithmetischen Mittelwert der Werte.

- **Minimum**. Zeigt den kleinsten Wert.

- **Maximum**. Zeigt den größten Wert.

- **Anzahl (ohne Leerstellen)** . Zählt die Anzahl der Werte in diesem Feld auf, die nicht leer sind.

- **Anzahl (diskret)** . Mit dieser Option wird die Anzahl der verschiedenen Werte in diesem Feld gezählt.

- **Standardabweichung**.

- **Varianz.**

- **Median**.  Zeigt den Medianwert (mittlerer Wert) an. Dieser Wert hat die gleiche Anzahl von Werten über und unter sich.  Wenn 2 Mediane vorhanden sind, erstellt Power BI einen Durchschnittswert.

Die Daten:

| Land | Amount |
|:--- |:--- |
| USA |100 |
| VEREINIGTES KÖNIGREICH |150 |
| Kanada |100 |
| Deutschland |125 |
| Frankreich | |
| Japan |125 |
| Australien |150 |

führen zu folgenden Ergebnissen:

- **Nicht zusammenfassen:** Jeder Wert wird separat dargestellt.

- **Summe:** 750

- **Durschnitt:** 125

- **Maximum:**  150

- **Minimum:** 100

- **Anzahl (ohne Leerstellen):** 6

- **Anzahl (diskret):** 4

- **Standardabweichung:** 20,4124145...

- **Varianz:** 416,666...

- **Median:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Erstellen eines Aggregats mit einem Kategoriefeld (Text)

Sie können auch nicht numerische Felder aggregieren. Wenn beispielsweise ein Feld mit Produktnamen vorhanden ist, können Sie es als Wert hinzufügen und dafür **Anzahl**, **Diskrete Anzahl**, **Erste** oder **Letzter** festlegen.

1. Ziehen Sie das Feld **Product** (Produkt) in das Feld **Werte**. Das Feld **Werte** wird normalerweise für numerische Felder verwendet. Power BI erkennt, dass es sich bei diesem Feld um ein Textfeld handelt, legt das Aggregat auf **Nicht zusammenfassen** fest und zeigt eine einspaltige Tabelle an.

   ![Screenshot: Feld „Produkt“ im Feld „Werte“](media/service-aggregates/power-bi-aggregate-value.png)

1. Wenn Sie die Aggregation von der Standardeinstellung **Nicht zusammenfassen** in **Anzahl (eindeutig)** ändern, zählt Power BI die Anzahl der verschiedenen Produkte. In diesem Fall sind es vier.
  
   ![Screenshot: eindeutige Anzahl der Produkte](media/service-aggregates/power-bi-aggregate-count.png)

1. Und wenn Sie die Aggregation in **Anzahl**ändern, zählt Power BI die Gesamtanzahl. In diesem Fall liegen sieben Einträge für **Product** (Produkt) vor.

   ![Screenshot: Anzahl der Produkte](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Indem Sie das gleiche Feld (in diesem Fall **Product**) in das Feld **Werte** ziehen und die Standardaggregation **Nicht zusammenfassen** übernehmen, gliedert Power BI die Anzahl nach Produkt.

   ![Screenshot: Produkt und Anzahl der Produkte](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

F:  Warum ist die Option **Nicht zusammenfassen** nicht verfügbar?

A:  Das ausgewählte Feld ist wahrscheinlich ein berechnetes oder erweitertes Measure, das in Excel oder [Power BI Desktop](../transform-model/desktop-measures.md) erstellt wurde. Jedes berechnete Measure verfügt über eine eigene hartcodierte Formel. Sie können die von Power BI verwendete Aggregation nicht ändern. Wenn es sich z.B. um eine Summe handelt, muss es eine Summe bleiben. In der Liste **Felder** werden *berechnete Measures* mit einem Taschenrechnersymbol angezeigt.

F:  Mein Feld **ist** numerisch. Warum stehen mir nur die Optionen **Anzahl** und **Diskrete Anzahl** zur Verfügung?

A1:  Die naheliegende Erklärung besteht darin, dass der Besitzer des Datasets das Feld *nicht* als Zahl klassifiziert hat. Wenn ein Dataset beispielsweise das Feld **Jahr** enthält, kann der Besitzer des Datasets diesen Wert als Text kategorisieren. Es ist wahrscheinlicher, dass Power BI das Feld **Jahr** zählt (z. B. die Anzahl der im Jahr 1974 geborenen Menschen). Es ist weniger wahrscheinlich, dass Power BI die Summe oder den Durchschnitt berechnet. Als Besitzer können Sie das Dataset in Power BI Desktop öffnen und den Datentyp auf der Registerkarte **Modellierung** ändern.

A2: Wenn das Feld mit einem Taschenrechnersymbol gekennzeichnet ist, handelt es sich um ein *berechnetes Measure*. Jedes berechnete Measure verfügt über eine eigene hartcodierte Formel, die nur der Besitzer der Datasets ändern kann. Bei der von Power BI verwendeten Berechnung kann es sich um eine einfache Aggregation handeln, z. B. ein Durchschnitt oder eine Summe. Es sind aber auch kompliziertere Aggregationen wie „prozentualer Anteil an einer übergeordneten Kategorie“ oder „laufende Summe seit Jahresbeginn“ möglich. Power BI berechnet keine Summe und keinen Durchschnitt für die Ergebnisse. Stattdessen wird die Berechnung für jeden Datenpunkt noch mal durchgeführt (mithilfe der hartcodierten Formel).

A3:  Eine weitere Möglichkeit: Sie haben das Feld in einem *Bucket* platziert, in dem nur Kategoriewerte zulässig sind.  In diesem Fall stehen nur die Optionen „Count“ und „Distinct Count“ zur Verfügung.

A4:  Die vierte Möglichkeit besteht darin, dass Sie das Feld für eine Achse verwenden. Auf der Achse eines Balkendiagramms zeigt Power BI beispielsweise jeweils einen Balken pro eindeutigem Wert an. Die Feldwerte werden also überhaupt nicht aggregiert.

>[!NOTE]
>Eine Ausnahme sind Punktdiagramme, bei denen aggregierte Werte für die X- und Y-Achse *erforderlich* sind.

F:  Warum kann ich keine Textfelder für SSAS-Datenquellen (SSAS = SQL Server Analysis Services) aggregieren?

A:  Liveverbindungen mit mehrdimensionalen SSAS-Modellen lassen keine clientseitigen Aggregationen zu. Zu diesen zählen „first“, „last“, „avg“, „min“, „max“ und „sum“.

F:  Ich habe ein Punktdiagramm und möchte *nicht*, dass mein Feld aggregiert wird.  Wie kann ich das erreichen?

A:  Fügen Sie das Feld dem Bucket **Details** (und nicht den Buckets für die X- oder Y-Achse) hinzu.

F:  Wenn ich ein numerisches Feld einer Visualisierung hinzufüge, wird bei den meisten standardmäßig eine Summe gebildet, bei einigen wird hingegen standardmäßig ein Mittelwert gebildet, die Anzahl ermittelt oder eine andere Aggregation verwendet.  Warum ist die standardmäßige Aggregation nicht immer gleich?

A:  Besitzer von Datasets können die Standardzusammenfassung individuell für die einzelnen Felder festlegen. Als Besitzer eines Datasets können Sie die Standardzusammenfassung auf der Power BI Desktop-Registerkarte **Modellierung** ändern.

F:  Ich bin Besitzer eines Datasets und möchte sicherstellen, dass ein Feld nicht aggregiert wird.

A:  Legen Sie in Power BI Desktop auf der Registerkarte **Modellierung** die Option **Datentyp** auf **Text** fest.

F:  In der Dropdownliste steht die Option **Nicht zusammenfassen** nicht zur Verfügung.

A:  Entfernen Sie das Feld, und fügen Sie es anschließend wieder hinzu.

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)