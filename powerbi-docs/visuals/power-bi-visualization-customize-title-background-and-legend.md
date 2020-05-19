---
title: Erste Schritte beim Formatieren von Power BI-Visualisierungen
description: Anpassen von Visualisierungstitel, Hintergrund und Legende
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5a55fca07e4a0e5f9c027bcd17c3fba66a09958e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277132"
---
# <a name="customize-visualization-titles-backgrounds-and-legends"></a>Anpassen von Visualisierungstiteln, Hintergründen und Legenden

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    


In diesem Tutorial lernen Sie einige verschiedene Möglichkeiten zum Anpassen von Visualisierungen kennen. Es gibt so viele Optionen zum Anpassen von Visualisierungen. Der beste Weg, um mehr über sie alle zu erfahren, ist die Erkundung des Bereichs **Format** (wählen Sie das Farbrollensymbol aus). Um Ihnen den Einstieg zu erleichtern, wird in diesem Artikel das Anpassen des Titels, der Legende und des Hintergrunds einer Visualisierung und das Hinzufügen eines Designs erläutert.

Sie können nicht alle Visualisierungen anpassen. Details hierzu finden Sie in der [kompletten Liste](#visualization-types-that-you-can-customize) der Visualisierungen.


## <a name="prerequisites"></a>Voraussetzungen

- Der Power BI-Dienst oder Power BI Desktop

- Bericht zum Analysebeispiel für den Einzelhandel

> [!NOTE]
> Eine Freigabe Ihres Berichts für einen Power BI-Kollegen erfordert, dass Sie und Ihr Kollege jeweils eine eigene Power BI Pro-Lizenz haben oder dass der Bericht in der Premium-Kapazität gespeichert wird. Weitere Informationen finden Sie unter [Freigeben von Berichten](../collaborate-share/service-share-reports.md).

## <a name="customize-visualization-titles-in-reports"></a>Anpassen der Visualisierungstitel in Berichten

Melden Sie sich bei Power BI Desktop an, und öffnen Sie das [Analysebeispiel für den Einzelhandel](../create-reports/sample-datasets.md).

> [!NOTE]
> Wenn Sie eine Visualisierung an ein Dashboard anheften, wird sie zu einer Dashboardkachel. Sie können auch die Kacheln selbst mit [neuen Titeln und Untertiteln, Hyperlinks und Größenänderungen](../create-reports/service-dashboard-edit-tile.md) anpassen.

1. Gehen Sie zur Seite **Neue Filialen** des Berichts zum **Analysebeispiel für den Einzelhandel**.

1. Wählen Sie das gruppierte Säulendiagramm **Anzahl eröffneter Filialen nach Eröffnungsmonat und Kette** aus.

1. Wählen Sie im Bereich **Visualisierungen** das Farbrollensymbol aus, um die Formatoptionen anzuzeigen.

1. Wählen Sie **Titel** aus, um diesen Abschnitt zu erweitern.

   ![Screenshot des Bereichs „Format“ mit hervorgehobenem Farbrollensymbol und auf die Dropdownliste „Titel“ weisendem Pfeil.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Setzen Sie den Schieberegler**Titel** auf **Ein**.

1. Um den Titel zu ändern, geben Sie *Ladenanzahl nach Öffnungsmonat* in das Feld **Titeltext** ein.

    ![Screenshot des Bereichs „Format“ mit dem eingegebenen Titeltext.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Ändern Sie **Schriftfarbe** in Weiß und **Hintergrundfarbe** in Blau.    

    a. Wählen in der Dropdownliste aus **Designfarben**, **Zuletzt verwendete Farben** oder **Benutzerdefinierte Farbe** eine Farbe aus.
    
    ![Screenshot der Optionen „Schriftfarbe“ und „Hintergrundfarbe“.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. Wählen Sie die Dropdownliste aus, um das Farbfenster zu schließen.


1. Vergrößern Sie die Textgröße auf **16 pt**.

1. Die letzte Anpassung, die Sie am Diagrammtitel vornehmen, ist die Ausrichtung in der Mitte der Visualisierung.

    ![Screenshot der Ausrichtungssteuerelemente, wobei die Option „Mitte“ ausgewählt ist.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    An diesem Punkt des Tutorials sollte der Titel Ihres gruppierten Säulendiagramms wie folgt aussehen:

    ![Screenshot des neu konfigurierten gruppierten Säulendiagramms.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Speichern Sie die Änderungen, die Sie vorgenommen haben, und fahren Sie mit dem nächsten Abschnitt fort.

Wenn Sie einmal alle Änderungen zurücksetzen müssen, wählen Sie **Auf Standardwert zurücksetzen** am unteren Rand des Anpassungsbereichs des **Titels** aus.

![Screenshot der Option „Auf Standardwert zurücksetzen“.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Anpassen der Hintergründe von Visualisierungen

Erweitern Sie im gleichen gruppierten Säulendiagramm die Optionen für den **Hintergrund**.

1. Setzen Sie den **Hintergrund**-Schieberegler auf **Ein**.

1. Wählen Sie die Dropdownliste und dann eine graue Farbe aus.

1. Ändern Sie **Transparenz** in **74%** .

An diesem Punkt des Tutorials sollte der Hintergrund Ihres gruppierten Säulendiagramms wie folgt aussehen:

![Screenshot des gruppierten Säulendiagramms mit aktualisierter Hintergrundfarbe.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Speichern Sie die Änderungen, die Sie vorgenommen haben, und fahren Sie mit dem nächsten Abschnitt fort.

Wenn Sie einmal alle Änderungen zurücksetzen müssen, wählen Sie **Auf Standardwert zurücksetzen** am unteren Rand des Anpassungsbereichs des **Hintergrunds** aus.

## <a name="customize-visualization-legends"></a>Anpassen der Legenden von Visualisierungen

1. Öffnen Sie die Berichtsseite **Übersicht**, und wählen Sie das Diagramm **Gesamtabweichung Verkäufe nach FiscalMonth und Regionalmanager** aus.

1. Wählen Sie in der Registerkarte **Visualisierung** das Farbrollensymbol aus, um den Bereich „Format“ zu öffnen.

1. Erweitern Sie die Optionen von **Legende**:

    ![Screenshot der Karte „Legende“.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Setzen Sie den **Legende**-Schieberegler auf **Ein**.

1. Verschieben Sie die Legende auf die linke Seite der Visualisierung.

1. Fügen Sie einen Legendentitel hinzu, indem Sie **Titel** auf **Ein** umschalten.

1. Geben Sie *Manager* in das Feld **Legendenname** ein.

1. Ändern Sie **Farbe** in Schwarz.

Speichern Sie die Änderungen, die Sie vorgenommen haben, und fahren Sie mit dem nächsten Abschnitt fort.

Wenn Sie einmal alle Änderungen zurücksetzen müssen, wählen Sie **Auf Standardwert zurücksetzen** am unteren Rand des Anpassungsbereichs der **Legende** aus.

## <a name="customize-colors-using-a-theme"></a>Anpassen von Farben mithilfe eines Designs

Mit Berichtsdesigns können Sie Entwurfsänderungen auf den gesamten Bericht anwenden, z. B. die Verwendung von Unternehmensfarben, das Ändern von Symbolsätzen oder das Anwenden der neuen Standardformatierung für Visuals. Wenn Sie ein Berichtsdesign anwenden, verwenden alle Visuals im Bericht Farben und Formatierung des ausgewählten Designs.

Wenn Sie ein Design auf den Bericht anwenden möchten, wählen Sie **Design wechseln** in der Menüleiste aus. Wählen Sie ein Design aus.  Im folgenden Bericht wird das Design **Solar** verwendet.

 
![Bericht mit Design „Solar“ in Gelb-, Orange- und Rottönen](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Visualisierungstypen, die Sie anpassen können

Hier ist eine Liste der Visualisierungen und jeweils verfügbaren Anpassungsoptionen:

| Visualisierung | Titel | Hintergrund | Legende |
|:--- |:--- |:--- |:--- |
| Fläche | Ja | Ja |Ja |
| Balken | Ja | Ja |Ja |
| Karte | Ja | Ja |n/v |
| Mehrzeilige Karte | Ja | Ja | n/v |
| Spalte | Ja | Ja | Ja |
| Kombinationsdiagramm | Ja | Ja | Ja |
| Ringdiagramm | Ja | Ja | Ja |
| Flächenkartogramm | Ja | Ja | Ja |
| Trichterdiagramm | Ja | Ja | n/v |
| Maßstab | Ja | Ja | n/v |
| Wichtigste Einflussfaktoren | Ja | Ja | n/v |
| KPI | Ja | Ja | n/v |
| Linie | Ja | Ja | Ja |
| Zuordnung | Ja | Ja | Ja |
| Matrix | Ja | Ja | n/v |
| Kreis | Ja | Ja | Ja |
| Q&A | Ja | Ja | n/v |
| Punktdiagramm | Ja | Ja | Ja |
| Formen | Ja | Ja | Ja |
| Slicer | Ja | Ja | n/v |
| Tabelle | Ja | Ja | n/v |
| Textfeld | Nein | Ja | n/v |
| Treemap | Ja | Ja | Ja |
| Wasserfall | Ja | Ja | Ja |

## <a name="next-steps"></a>Nächste Schritte

- [Anpassen der Eigenschaften der X- und Y-Achse](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Erste Schritte mit Farbeinstellungen und Achseneigenschaften](service-getting-started-with-color-formatting-and-axis-properties.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)


