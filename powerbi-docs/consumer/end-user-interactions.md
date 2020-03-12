---
title: Interaktionen zwischen Visuals in einem Bericht
description: Dokumentation für Power BI-Endbenutzer, die erklärt, wie visuelle Elemente auf einer Berichtsseite interagieren.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: fb7bf439cdf2f7ebd6058aba6b147f800b9cf258
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79113053"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Gegenseitige Kreuzfilterung von Visuals in einem Power BI-Bericht

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Eines der herausragenden Features von Power BI ist die Art, auf die alle visuellen Elemente auf einer Berichtsseite miteinander verbunden sind. Wenn Sie in einem der visuellen Elemente einen Datenpunkt auswählen, ändern sich alle anderen visuellen Elemente auf der Seite, die diese Daten enthalten, auf Grundlage dieser Auswahl. 

![Video von interagierenden visuellen Elementen](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>Interaktion von Visuals

Standardmäßig führt die Auswahl eines Datenpunkts in einem Visual auf einer Berichtseite zur Kreuzfilterung oder -hervorhebung der anderen Visuals auf der Seite. Wie visuelle Elemente auf einer Seite genau miteinander interagieren, wird vom *Designer* des Berichts festgelegt. *Designer* können Interaktionen von Visuals aktivieren und deaktivieren sowie das Standardverhalten der Kreuzfilterung, -hervorhebung und von [Drillvorgängen](end-user-drill.md) ändern. 

Wenn Sie Hierarchien und Drillvorgänge noch nicht kennengelernt haben, finden Sie weitere Informationen unter [Drilldowns in Power BI](end-user-drill.md). 

### <a name="cross-filtering-and-cross-highlighting"></a>Kreuzfiltern und übergreifendes Hervorheben

Die Kreuzfilterung und die Kreuzhervorhebung können sich als nützlich erweisen, wenn Sie identifizieren möchten, wie Werte in Ihren Daten zusammenhängen. Die Begriffe *Kreuzfilterung* und *Kreuzhervorhebung* werden verwendet, um das hier beschriebene Verhalten davon zu unterscheiden, was geschieht, wenn Sie den Bereich **Filter** zum Filtern und Hervorheben von Visualisierungen verwenden.  

Sehen Sie sich die Berichtsseiten unten an. So können diese Benennungen definiert werden. Das Ringdiagramm „Total category volume by segment“ hat zwei Werte: „Moderation“ und „Convenience“. 

![Berichtseite](media/end-user-interactions/power-bi-interactions-before.png)

1. Sehen Sie sich nun an, was geschieht, wenn Sie **Moderation** auswählen.

    ![Berichtsseite, nachdem im Ringdiagramm das Segment „Moderation“ ausgewählt wurde](media/end-user-interactions/power-bi-interactions-after.png)

2. Durch die **Kreuzfilterung** werden nicht geltende Daten entfernt. Wenn Sie beispielsweise **Moderation** im Ringdiagramm auswählen, wird das Liniendiagramm kreuzgefiltert. Das Liniendiagramm zeigt jetzt nur noch Datenpunkte an, die für das Segment „Moderation“ gelten. 

3. Durch die **übergreifende Hervorhebung** werden alle ursprünglichen Datenpunkte beibehalten, aber der Teil, der nicht für Ihre Auswahl gilt, wird abgeblendet. Wenn Sie beispielsweise **Moderation** im Ringdiagramm auswählen, wird das Säulendiagramm übergreifend hervorgehoben. Das Säulendiagramm blendet alle Daten ab, die für das Segment „Convenience“ gelten, und hebt alle Daten hervor, die für das Segment „Moderation“ gelten. 


## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
- Wenn Ihr Bericht ein Visual enthält, das [Drillvorgänge](end-user-drill.md) standardmäßig unterstützt, haben Drillvorgänge an einem Visual keine Auswirkungen auf die anderen Visuals der Berichtseite. Allerdings kann der *Designer* des Berichts dieses Verhalten ändern. Überprüfen Sie daher die Visuals, für die ein Drillvorgang ausgeführt werden kann, um zu sehen, ob der *Designer* des Berichts **Drillfilter anderer Visuals** aktiviert hat.
    
- Filter auf Visualebene werden beibehalten, wenn andere Visuals auf der Berichtsseite kreuzgefiltert oder übergreifend hervorgehoben werden. Wenn Sie oder der Berichtersteller Filter auf Visualebene für VisualA angewendet haben, und Sie verwenden VisualA zur Interaktion mit VisualB, werden Filter auf Visualebene, die für VisualA gelten, auch auf VisualB angewendet.

    ![Berichtsseite, nachdem im Ringdiagramm das Segment „Moderation“ ausgewählt wurde](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>Nächste Schritte
[Verwenden von Berichtsfiltern](../power-bi-how-to-report-filter.md)    


[Weitere Informationen zum Filtern und Hervorheben](end-user-report-filter.md) 
