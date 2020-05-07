---
title: Verwenden von Menübanddiagrammen in Power BI
description: Erstellen und Verwenden von Menübanddiagrammen im Power BI Desktop
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1cee814b5013ece3a847aeb3660f1257c69be125
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73871144"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Verwenden von Menübanddiagrammen in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Mit den Menübanddiagrammen können Sie Daten visualisieren und schnell feststellen, welche Kategorie von Daten den höchsten Rang (größten Wert) hat. Menübanddiagramme eignen sich gut zum Anzeigen von Rangänderungen, wobei der höchste Rang (Wert) immer für jeden Zeitraum oben angezeigt wird. 

![Menübanddiagramm](media/desktop-ribbon-charts/ribbon-charts-01.png)

## <a name="prerequisites"></a>Voraussetzungen

In diesem Tutorial wird die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) verwendet.

1. Wählen Sie im oberen linken Bereich der Menüleiste **Datei** > **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.

## <a name="create-a-ribbon-chart"></a>Erstellen eines Menübanddiagramms

1. Wählen Sie zum Erstellen eines leeren Diagramms die Option **Menübanddiagramm** im Bereich **Visualisierungen** aus.

    ![Visualisierungsvorlagen](media/desktop-ribbon-charts/power-bi-template.png)

    Menübanddiagramme verknüpfen eine Kategorie von Daten über das visualisierte Zeitkontinuum mithilfe von Bändern, sodass Sie den Rang einer bestimmten Kategorie während der gesamten Spanne der X-Achse (in der Regel die Zeitachse) erkennen können.

2. Wählen Sie Felder für **Achse**, **Legende** und **Wert** aus.  In diesem Beispiel wurde Folgendes ausgewählt: **Store** > **OpenDate**, **Item** > **Kategorie**, und **Vertrieb** > **This Year Sales** > **Wert**.  

    ![Ausgewählte Felder](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Da das Dataset nur die Daten eines Jahres enthält, wurde das Feld **Jahr** und **Quartal**von der **Achse** entfernt.

3. Auf dem Menübanddiagramm wird die Rangfolge für jeden Monat angezeigt. Diese hat sich im Laufe der Zeit geändert. Beispielsweise wechselt die Kategorie „Home“ von Februar auf März vom zweiten auf den fünften Rang.

    ![Menübanddiagramm](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Formatieren eines Menübanddiagramms
Wenn Sie ein Menübanddiagramm erstellen, stehen Ihnen im Abschnitt **Format** des Bereichs **Visualisierungen** Formatierungsoptionen zur Verfügung. Die Formatierungsoptionen für Menübanddiagramme ähneln denen für ein gestapeltes Säulendiagramm, mit zusätzlichen speziellen Formatierungsoptionen für die Bänder.

![Menüband-Vorlage auf dem Bereich „Visualisierung“](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Mit den Formatierungsoptionen für Menübanddiagramme können Sie Anpassungen vornehmen.

* Mit **Abstand** können Sie den Abstand zwischen Bändern anpassen. Die Zahl ist der Prozentwert der maximalen Höhe der Spalte.
* Mit **Serienfarbe abgleichen** können Sie die Farbe der Bänder an die Reihenfarbe anpassen. Wenn die Option auf **Aus** festgelegt ist, sind die Bänder grau.
* **Transparenz** gibt die Transparenz der Bänder an. Der Standardwert ist 30.
* Mit **Rand** können Sie am oberen und unteren Rand der Bänder einen dunklen Rahmen platzieren. „Rand“ ist standardmäßig deaktiviert.

Da die die y-Achse in dem Menübanddiagramm nicht beschriftet ist, sollten Sie Datenbeschriftungen hinzufügen. Klicken Sie dafür im Formatierungsbereich auf **Datenbeschriftungen**. 

![Formatierungsoptionen für Datenbeschriftungen](media/desktop-ribbon-charts/power-bi-labels.png)

Legen Sie Formatierungsoptionen für Ihre Datenbeschriftungen fest. In diesem Beispiel wurde für die Textfarbe „weiß“, und für die Anzeigeeinheiten „Tausend“ festgelegt.

![Menüband-Vorlage auf dem Bereich „Visualisierung“](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Nächste Schritte

[Punktdiagramme und Blasendiagramme in Power BI](power-bi-visualization-scatter.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
