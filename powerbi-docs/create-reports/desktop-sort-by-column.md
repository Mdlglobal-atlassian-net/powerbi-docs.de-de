---
title: Sortieren nach Spalten in Power BI Desktop
description: In Power BI können Sie das Erscheinungsbild eines Visuals ändern, indem Sie es nach verschiedenen Datenfeldern sortieren.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: db5bc2566e4711873629522d08a2d0c818071b81
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83334037"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Sortieren nach Spalten in Power BI Desktop
In Power BI Desktop und im Power BI-Dienst können Sie das Erscheinungsbild eines Visuals ändern, indem Sie es nach verschiedenen Datenfeldern sortieren. Indem Sie die Sortierung eines Visuals ändern, können Sie die Informationen hervorheben, die Sie vermitteln möchten, und sicherstellen, dass das Visual den gewünschten Trend (oder den gewünschten zentralen Aspekt) widerspiegelt.

Ob Sie numerische Daten (z. B. Umsatzzahlen) oder Text (z. B. Ländernamen) verwenden – die Visualisierungen lassen sich wunschgemäß sortieren und optisch aufbereiten. Power BI bietet große Flexibilität beim Sortieren sowie Schnellmenüs. Klicken Sie auf das Menü **Weitere Optionen** (…), klicken Sie auf **Sortieren nach**, und wählen Sie dann das Feld aus, nach dem Sie sortieren möchten, um ein Visual zu sortieren.

![Menü „Mehr Optionen“](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>Sortierbeispiel
Sehen Sie sich im Folgenden ein ausführliches Beispiel an und wie es in Power BI Desktop funktioniert.

In der folgenden Visualisierung sind die Kosten, die Verkaufsmenge sowie der Rabattbetrag für den jeweiligen Herstellernamen aufgeführt. Hier sehen Sie die Visualisierung vor dem weiteren Sortieren:

![Erste Visualisierung](media/desktop-sort-by-column/sortbycolumn_1.png)

Das Visual ist momentan nach der Spalte **SalesQuantity** sortiert. Sie können die Sortierspalte bestimmen, indem Sie die Farbe der aufsteigenden Balken mit der Legende abgleichen. Es gibt aber auch eine einfachere Möglichkeit. Klicken Sie dazu auf das Menü **Weitere Optionen** (…).

![Menü „Mehr Optionen“](media/desktop-sort-by-column/sortbycolumn_2.png)

Die Sortierauswahl lautet folgendermaßen:

* Das aktuelle Sortierfeld ist **SalesQuantity**, was durch den Fettdruck von und die gelbe Leiste vor **SalesQuantity** angegeben wird. 

* Die aktuelle Sortierrichtung ist aufsteigend, was durch den Fettdruck von und die gelbe Leiste vor **Aufsteigend sortieren** angegeben wird.

In den nächsten beiden Abschnitten betrachten Sie das Sortierfeld und die Sortierrichtung.

## <a name="select-which-column-to-use-for-sorting"></a>Auswählen der Sortierspalte
Möglicherweise haben Sie schon die gelbe Leiste neben **SalesQuantity** im Menü **Weitere Optionen** gesehen, die angibt, dass das Visual nach der **SalesQuantity**-Spalte sortiert ist. Wenn Sie nach einer anderen Spalte sortieren möchten, ist dies einfach: Klicken Sie auf die Auslassungspunkte (…), um das Menü **Weitere Optionen** anzuzeigen, klicken Sie auf **Sortieren nach**, und wählen Sie dann eine andere Spalte aus.

In der folgenden Abbildung wurde die Spalte **DiscountAmount** als Sortierspalte ausgewählt. Diese Spalte entspricht einer Linie im Visual und keinem Balken. 

![Sortieren nach DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Beachten Sie, wie sich das visuelle Element geändert hat. Die Werte werden nun vom höchsten **DiscountAmount**-Wert im Visual „Fabrikam Inc.“ nach unten zum Hersteller „Northwind Traders“ sortiert. 

Aber was geschieht, wenn wir statt in absteigender Reihenfolge aufsteigend sortieren möchten? Im nächsten Abschnitt wird gezeigt, wie einfach das ist.

## <a name="select-the-sort-order"></a>Auswählen der Sortierreihenfolge
Wenn Sie sich das **Weitere Optionen**-Menü in der vorherigen Abbildung genauer ansehen, sehen Sie, dass **Absteigend sortieren** fettgedruckt ist und eine gelbe Leiste davor angezeigt wird.

![Nach Größe sortieren (absteigend)](media/desktop-sort-by-column/sortbycolumn_4.png)

Wenn **Absteigend sortieren** ausgewählt wird, wird das Visual nach der ausgewählten Spalte vom größten zum kleinsten Wert sortiert. Sie möchten dies ändern? Das ist problemlos möglich. Wählen Sie einfach **Aufsteigend sortieren** aus, und die Sortierreihenfolge der ausgewählten Spalte ändert sich, sodass vom kleinsten zum größten Wert sortiert wird.

Unten sehen Sie das gleiche Visual, nachdem die Sortierung von **DiscountAmount** geändert wurde. Beachten Sie, dass Northwind Traders nun der erste aufgeführte Hersteller ist und Fabrikam Inc. der letzte – also das genaue Gegenteil wie zuvor.

![Nach Größe sortieren (aufsteigend)](media/desktop-sort-by-column/sortbycolumn_5.png)

Die Darstellung lässt sich nach jeder im Visual enthaltenen Spalte sortieren – beispielsweise könnte **SalesQuantity** als Sortierspalte ausgewählt werden, um die Hersteller mit den meisten Verkäufen an erster Stelle anzuzeigen. Die anderen Spalten werden im Visual weiterhin berücksichtigt, so wie sie für den betreffenden Hersteller gelten. Hier sehen Sie das Visual mit den besprochenen Einstellungen:

![Sortieren nach SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Sortieren mit der Schaltfläche „Nach Spalte sortieren“
Es gibt eine weitere Möglichkeit zum Sortieren von Daten. Sie können auf die Schaltfläche **Nach Spalte sortieren** im Menüband **Modellierung** klicken.

![Sortieren nach Spalte (Schaltfläche)](media/desktop-sort-by-column/sortbycolumn_8.png)

Bei diesem Sortieransatz müssen Sie zuerst die Spalte (Feld) im Bereich **Felder** auswählen, die sortiert werden soll, und dann auf **Modellierung**  >  **Nach Spalte sortieren** klicken, um Ihr Visual zu sortieren. Wenn Sie keine Spalte auswählen, ist die Schaltfläche **Nach Spalte sortieren** inaktiv.

Im Folgenden wird ein gängiges Beispielszenario beschrieben. Sie verfügen über Daten für die einzelnen Monate des Jahres, und diese sollen chronologisch sortiert werden. In den folgenden Schritten wird die Vorgehensweise erläutert:

1. Zunächst stellen Sie Folgendes fest: Wenn das Visual, jedoch keine Spalte im Bereich **Felder** ausgewählt ist, ist die Schaltfläche **Nach Spalte sortieren** inaktiv (abgeblendet dargestellt).
   
   ![Inaktive „Nach Spalte sortieren“-Schaltfläche](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Wenn Sie im Bereich **Felder** die Spalte auswählen, nach der sortiert werden soll, wird die Schaltfläche **Nach Spalte sortieren** aktiviert.
   
   ![Aktive „Nach Spalte sortieren“-Schaltfläche](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Nun können Sie bei ausgewähltem Visual die Spalte **MonthOfYear** anstelle der Standardspalte **MonthName** auswählen, und das Visual wird in der gewünschten Reihenfolge sortiert: nach dem Monat des Jahres.
   
   ![Nach Spalte sortieren (Menü)](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>Weitere Schritte

Folgende Artikel könnten Sie ebenfalls interessieren:

* [Use cross-report drillthrough in Power BI Desktop](desktop-cross-report-drill-through.md) (Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop)
* [Datenschnitte in Power BI](../visuals/power-bi-visualization-slicers.md)
