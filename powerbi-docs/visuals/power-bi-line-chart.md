---
title: Liniendiagramme in Power BI
description: Liniendiagramme in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 9f7cd6c277a02ce4e44db40930184cce955e5948
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274188"
---
# <a name="line-charts-in-power-bi"></a>Liniendiagramme in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Ein Liniendiagramm ist eine Reihe von Datenpunkten, die durch Punkte dargestellt und durch gerade Linien verbunden sind. Ein Liniendiagramm kann aus einer oder mehreren Linien bestehen. Liniendiagramme haben eine X- und eine Y-Achse. 

![einfaches Liniendiagramm](media/power-bi-line-charts/power-bi-line.png)



## <a name="create-a-line-chart"></a>Erstellen eines Liniendiagramms
Mit dieser Anleitung erstellen Sie anhand der Beispiel-App für Vertrieb und Marketing ein Liniendiagramm, das den Absatz des laufenden Jahres nach Kategorie anzeigt. Rufen Sie hierfür die Beispiel-App aus appsource.com ab.

> [!NOTE]
> Eine Freigabe Ihres Berichts für einen Power BI-Kollegen erfordert, dass Sie und Ihr Kollege jeweils eine eigene Power BI Pro-Lizenz haben oder dass der Bericht in der Premium-Kapazität gespeichert wird.

1. Beginnen Sie auf einer leeren Berichtsseite. Wenn Sie den Power BI-Dienst verwenden, achten Sie darauf, den Bericht in der [Bearbeitungsansicht](../create-reports/service-interact-with-a-report-in-editing-view.md) zu öffnen.

2. Wählen Sie im Bereich „Felder“ **SalesFact** \> **Gesamtanzahl der Einheiten** und dann **Datum** > **Monat** aus.  Power BI erstellt ein Säulendiagramm im Zeichenbereich des Berichts.

    ![Auswählen im Bereich „Felder“](media/power-bi-line-charts/power-bi-step1.png)

4. Konvertieren Sie es in ein Liniendiagramm, indem Sie die Vorlage für Liniendiagramme im Bereich „Visualisierungen“ auswählen. 

    ![Konvertieren in ein Liniendiagramm](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filtern Sie Ihr Liniendiagramm zur Anzeige der Daten aus den Jahren 2012-2014. Wenn der Bereich „Filter“ reduziert ist, erweitern Sie ihn jetzt. Wählen Sie im Bereich „Felder“ **Datum** \> **Jahr** aus, und ziehen Sie das Feld in den Bereich „Filter“. Legen Sie es unter der Überschrift **Filter für dieses Visual**  ab. 
     
    ![Linie neben dem Bereich „Felder“](media/power-bi-line-charts/power-bi-year-filter.png)

    Ändern Sie **Erweiterte Filter** zu **Basisfilter**, und wählen Sie **2012**, **2013** und **2014** aus.

    ![Filter für Jahr](media/power-bi-line-charts/power-bi-filter-year.png)

6. Optional können Sie [die Textgröße und -farbe des Diagramms anpassen](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Vergrößern des Schriftgrads und Ändern der Schriftart für die Y-Achse](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Hinzufügen weiterer Linien zum Diagramm
Liniendiagramme können viele verschiedene Linien haben. In einigen Fällen können die Werte in den Linien so voneinander abweichen, dass sie nicht gut zusammen angezeigt werden können. Sie lernen, wie Sie unserem aktuellen Diagramm zusätzliche Linien hinzufügen, und erfahren dann, wie Sie das Diagramm formatieren, wenn die durch die Linien dargestellten Werte sehr unterschiedlich sind. 

### <a name="add-additional-lines"></a>Hinzufügen zusätzlicher Linien
Anstatt die Gesamtanzahl der Einheiten für alle Regionen als einzelne Linie im Diagramm darzustellen, unterteilen wir die Gesamtanzahl der Einheiten nach Regionen. Fügen Sie zusätzliche Linien hinzu, indem Sie **Geografischer Raum** > **Region** in den Bereich „Legende“ ziehen.

   ![Eine Linie für jede Region](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Verwenden von zwei Y-Achsen
Was ist, wenn Sie den Gesamtumsatz und die Gesamtanzahl der Einheiten im gleichen Diagramm betrachten möchten? Verkaufszahlen sind sehr viel höher als Einheitenzahlen, sodass das Liniendiagramm nicht verwendet werden kann. Tatsächlich scheint die rote Linie für die Gesamtanzahl der Einheiten bei 0 (null) zu liegen.

   ![stark abweichende Werte](media/power-bi-line-charts/power-bi-diverging.png)

Um stark abweichende Werte im gleichen Diagramm anzuzeigen, verwenden Sie ein Kombinationsdiagramm. Unter [Kombinationsdiagramm in Power BI](power-bi-visualization-combo-chart.md) erfahren Sie alles über Kombinationsdiagramme. In unserem Beispiel unten können wir Verkäufe und Gesamtanzahl der Einheiten zusammen in einem Diagramm darstellen, indem wir eine zweite Y-Achse hinzufügen. 

   ![stark abweichende Werte](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>Hervorheben und Kreuzfiltern
Informationen zur Verwendung des Filterbereichs finden Sie unter [Hinzufügen eines Filters zu einem Bericht in Power BI](../create-reports/power-bi-report-add-filter.md).

Die Auswahl eines Datenpunkts auf einem Liniendiagramm ermöglicht das Kreuzhervorheben und Kreuzfiltern anderer Visualisierungen auf der Berichtsseite und umgekehrt. Öffnen Sie hierfür die Registerkarte **Marktanteil**.  

In einem Liniendiagramm ist ein einzelner Datenpunkt der Schnittpunkt eines X- und Y-Achsenwerts. Wenn Sie einen Datenpunkt auswählen, fügt Power BI Markierungen hinzu, die anzeigen, welcher Punkt (für eine einzelne Linie) oder welche Punkte (bei zwei oder mehr Linien) die Quelle für Kreuzhervorheben und Kreuzfiltern der anderen Visualisierungen auf der Berichtsseite ist bzw. sind. Wenn Ihre Visualisierung sehr dicht ist, wählt Power BI den Punkt aus, der am nächsten an der Stelle liegt, wo Sie auf das visuelle Element klicken.

In diesem Beispiel haben wir einen Datenpunkt ausgewählt, der Folgendes umfasst: Juli 2014, Marktanteil der Einheiten R12 33,16 Prozent und Marktanteil der Einheiten 34,74 Prozent.

![Auswählen eines einzelnen Datenpunkts in einem Liniendiagramm](media/power-bi-line-charts/power-bi-single-select.png)

Beachten Sie, dass das Säulendiagramm kreuzhervorgehoben und das Messgerät kreuzgefiltert ist.

Informationen zum Steuern der Kreuzhervorhebung und Kreuzfilterung von Diagrammen finden Sie unter [Interaktionen mit Visualisierungen in einem Power BI-Bericht](../create-reports/service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
* Ein Liniendiagramm kann keine zwei Y-Achsen haben.  Sie müssen stattdessen ein Kombinationsdiagramm verwenden.
* In den obigen Beispielen wurden die Diagramme so formatiert, dass der Schriftgrad vergrößert, die Schriftfarbe geändert, Achsentitel hinzugefügt, Diagrammtitel und Legende zentriert, der Ausgangspunkt beider Achsen auf 0 (null) gesetzt und vieles mehr durchgeführt wurde. Der Bereich „Formatierung“ (Farbrollensymbol) bietet zahlreiche Optionen, mit denen Sie Ihre Diagramme nach Wunsch gestalten können. Sie lernen diese Möglichkeit am besten kenn, indem Sie den Bereich „Formatierung“ öffnen und erforschen.

## <a name="next-steps"></a>Nächste Schritte

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)





