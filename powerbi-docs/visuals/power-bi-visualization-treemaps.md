---
title: Treemaps in Power BI
description: Treemaps in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 189cc784577df277b0b0517253699ae06842b30c
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866884"
---
# <a name="treemaps-in-power-bi"></a>Treemaps in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Treemaps zeigen hierarchische Daten als verschachtelten Rechtecke an. Jede Hierarchieebene wird durch ein farbiges Rechteck (Verzweigung) dargestellt, das kleinere Rechtecke (Blätter) enthält. Power BI macht die Größe der Fläche in jedem Rechteck vom gemessenen Wert abhängig. Die Rechtecke werden von oben links (das Größte) nach unten rechts (das Kleinste) angeordnet.

![Screenshot eines Treemap-Diagramms von „Produktzahl“ nach „Kategorie“ und „Hersteller“.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Wenn Sie beispielsweise Ihre Verkäufe analysieren, haben Sie möglicherweise Verzweigungen auf höchster Ebene für die Kleidungskategorien: **In der Stadt**, **Auf dem Land**, **Jugend** und **Mix**. Power BI würde für die Bekleidungshersteller innerhalb dieser Kategorie Ihre Kategorierechtecke in Blätter aufteilen. Die Größe und Schattierungen dieser Blätter werden wiederum den Verkaufszahlen angepasst.

In der Verzweigung **In der Stadt** wurden viele Kleidungsstücke von **VanArsdel** verkauft. Von **Natura** und **Fama** wurde weniger verkauft. Nur wenig wurde von **Leo** verkauft. Demnach sieht die Verzweigung **In der Stadt** Ihres Treemap-Diagramms wie folgt aus:

* Das größte Rechteck für **VanArsdel** befindet sich oben links in der Ecke.

* Die Rechtecke für **Natura** und **Fama** sind etwas kleiner.

* Es gibt viele Rechtecke für alle anderen verkauften Kleidungsstücke.

* Es gibt ein kleines Rechteck für **Leo**.

Sie könnten die Anzahl der in anderen Kleidungskategorien verkauften Artikeln durch Vergleich von Größe und Schattierung der einzelnen Blattknoten vergleichen. Je größer und dunkler schattiert das Rechteck ist, desto höher ist der Wert.


## <a name="when-to-use-a-treemap"></a>Verwenden von Treemaps

Treemaps sind gut geeignet:

* Zum Anzeigen großer Mengen hierarchischer Daten.

* Bei einer Anzahl von Werten, die für ein Balkendiagramm zu groß wäre.

* Zum Darstellen des Verhältnisses zwischen den einzelnen Teilen und der Gesamtmenge.

* Zum Anzeigen der Verteilung der einzelnen Werte innerhalb jeder Kategorieebene in der Hierarchie.

* Zum Anzeigen von Attributen über Größe und Farbcodierung.

* Zum Erkennen von Mustern, Ausreißern, der wichtigsten Einflussfaktoren und Ausnahmen.

## <a name="prerequisite"></a>Voraussetzung

Dieses Tutorial verwendet die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Wählen Sie im oberen linken Bereich der Menüleiste **Datei** > **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.

> [!NOTE]
> Eine Freigabe Ihres Berichts für einen Power BI-Kollegen erfordert, dass Sie und Ihr Kollege jeweils eine eigene Power BI Pro-Lizenz haben oder dass der Bericht in der Premium-Kapazität gespeichert wird.    



Nach dem Abrufen des Datasets für das **Analysebeispiel für den Einzelhandel** können Sie beginnen.

## <a name="create-a-basic-treemap"></a>Erstellen eines einfachen Treemap-Diagramms

Sie erstellen einen Bericht und fügen ein einfaches Treemap-Diagramm hinzu.


1. Wählen Sie im Bereich **Felder** das Measure **Verkäufe** > **Verkäufe im letzten Jahr** aus.

   ![Screenshot mit Auswahl von „Verkäufe > Verkäufe im letzten Jahr“ und der resultierenden Visualisierung.](media/power-bi-visualization-treemaps/treemapfirstvalue-new.png)

1. Wählen Sie das Treemap-Diagrammsymbol ![Screenshot des Treemap-Diagrammsymbols](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) aus, um das Diagramm in ein Treemap-Diagramm umzuwandeln.

   ![Screenshot des Treemap-Diagramms ohne Konfiguration.](media/power-bi-visualization-treemaps/treemapconvertto-new.png)

1. Wählen Sie **Element** > **Kategorie** aus, wodurch dem Bereich **Gruppe** noch **Kategorie** hinzugefügt wird.

    Power BI erstellt ein Treemap-Diagramm, in dem die Größe der Rechtecke auf dem Gesamtumsatz basiert und die Farbe die Kategorie widerspiegelt. Im Wesentlichen haben Sie eine Hierarchie erstellt, die die relative Größe des Gesamtumsatzes nach Kategorie visuell darstellt. In der Kategorie **Herren** wurden die höchsten Umsätze verzeichnet, in der Kategorie **Strumpfwaren** hingegen die niedrigsten.

    ![Screenshot des konfigurierten Treemap-Diagramms.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Wählen Sie **Laden** > **Kette** aus, wodurch dem Bereich **Details** noch **Kette** hinzugefügt wird, um das Treemap-Diagramm zu vervollständigen. Sie können den Vorjahresumsatzes jetzt nach Kategorie und Kette vergleichen.

   ![Screenshot des Treemap-Diagramms, wobei „Laden > Kette“ den „Details“ hinzugefügt ist.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Farbsättigung und Details können nicht gleichzeitig verwendet werden.

1. Zeigen Sie auf einen **Kettenbereich** , um die QuickInfo für diesen Teil der **Kategorie**anzuzeigen.

    Wenn Sie in dem Rechteck **090-Home** z.B. mit dem Mauszeiger über **Fashions Direct** fahren, wird die QuickInfo zum Fashions Direct-Teil der Kategorie „Home“ angezeigt.

   ![Screenshot der Home-QuickInfo, die angezeigt wird.](media/power-bi-visualization-treemaps/treemaphoverdetail-new.png)


## <a name="highlighting-and-cross-filtering"></a>Hervorheben und Kreuzfiltern

Das Markieren von **Kategorien** oder **Details** in einem Treemap-Diagramm ermöglicht die Kreuzhervorhebung und Kreuzfilterung anderer Visualisierungen auf der Berichtsseite. Fügen Sie dieser Berichtsseite entweder einige Visuals hinzu, oder kopieren Sie das Treemap-Diagramm auf eine der anderen Seiten in diesem Bericht. Im folgenden Bild wurde das Treemap-Diagramm auf die Seite **Übersicht** kopiert. 

1. Wählen Sie im Treemap-Diagramm entweder eine **Kategorie** oder eine **Kette** innerhalb einer **Kategorie** aus. Dadurch erfolgt eine Kreuzhervorhebung der anderen Visualisierungen auf der Seite. Wenn Sie beispielsweise **050-Schuhe** auswählen, wird für Schuhe ein Umsatz von **16.352.432 $** für das letzte Jahr angezeigt, wobei **2.174.185 $** auf **Fashions Direct** entfielen.

   ![Screenshot des „Übersicht über Ladenverkäufe“-Berichts mit Kreuzhervorhebung.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. Wählen Sie im Kreisdiagramm **Verkäufe im letzten Jahr nach Kette** das Segment **Fashions Direct** aus, um eine Kreuzfilterung des Treemap-Diagramms durchzuführen.
   ![GIF-Demonstration der Kreuzfilterungsfunktion.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Informationen zum Steuern der Kreuzhervorhebung und Kreuzfilterung von Diagrammen finden Sie unter [Ändern der Interaktion von Visualisierungen in einem Power BI-Bericht](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Nächste Schritte

* [Wasserfalldiagramme in Power BI](power-bi-visualization-waterfall-charts.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
