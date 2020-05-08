---
title: Verwenden des Analysebereichs in Power BI Desktop
description: Erstellen dynamischer Bezugslinien für Visualisierungen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4ad843078e452502a94aa7d60b3304528fd25496
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76038760"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Verwenden des Analysebereichs in Power BI Desktop

Mit dem Bereich **Analyse** in Power BI Desktop können Sie dynamische *Bezugslinien* zu Visuals hinzufügen und wichtige Trends und Erkenntnisse identifizieren. Der Bereich und das Symbol **Analyse** befinden sich in Power BI Desktop unter **Visualisierungen**.

![Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> Der Bereich **Analyse** wird nur angezeigt, wenn Sie im Power BI Desktop-Zeichenbereich ein Visual auswählen.

## <a name="search-within-the-analytics-pane"></a>Suche im Bereich „Analyse“

Ab dem Power BI Desktop-Release vom Februar 2018 (Version 2.55.5010.201 oder höher) können Sie innerhalb des Bereichs **Analyse** Suchen durchführen. Der Bereich für die Analyse ist ein Unterabschnitt des Bereichs **Visualisierungen**. Das Suchfeld wird angezeigt, wenn Sie das Symbol **Analyse** auswählen.

![Suchfeld, Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Verwenden des Bereichs „Analyse“

Mithilfe des Bereichs **Analyse** können Sie die folgenden Arten von dynamischen Bezugslinien erstellen:

* Bezugslinie für X-Achse
* Bezugslinie für Y-Achse
* Linie für Mindestwert
* Linie für Maximalwert
* Durchschnittslinie
* Linie für Medianwert
* Linie für Perzentil
* Symmetrieschattierung

> [!NOTE]
> Nicht alle Linien sind für alle Visualtypen verfügbar.

In den folgenden Abschnitten erfahren Sie, wie Sie den Bereich **Analyse** und die dynamischen Bezugslinien in Ihren Visualisierungen verwenden können.

Um die für eine Visualisierung verfügbaren dynamischen Bezugslinien anzuzeigen, führen Sie die folgenden Schritte aus:

1. Wählen Sie eine Visualisierung aus, oder erstellen Sie eine Visualisierung. Wählen Sie dann das Symbol **Analyse** im Bereich **Visualisierungen** aus.

    ![Anzeigen der Analyse für ein Visual, Bereich „Visualisierungen“, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Wählen Sie die zu erstellende Linie aus, um die zugehörigen Optionen zu erweitern. In diesem Fall entscheiden wir uns für die **Linie für Durchschnitt**.

    ![Linie für den Durchschnitt, Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Um eine neue Linie zu erstellen, wählen Sie **+&nbsp;Hinzufügen** aus. Anschließend können Sie die Linie benennen. Doppelklicken Sie auf das Textfeld, und geben Sie Ihren Namen ein.

    Jetzt stehen zahlreiche Optionen für Ihre Linie zur Verfügung. Sie können die **Farbe**, den Prozentsatz der **Transparenz**, **Linienart** und die **Position** (im Vergleich zu den Datenelementen des Visuals) angeben. Sie können außerdem entscheiden, ob Sie eine **Datenbeschriftung** einschließen möchten. Um das Visualmeasure anzugeben, auf dem Ihre Linie basieren soll, wählen Sie die Dropdownliste **Measure** aus, die automatisch mit Datenelementen aus dem Visual aufgefüllt wird. In diesem Fall entscheiden wir uns für **Culture** (Kultur) als Measure, geben als Bezeichnung *Durchschnitt für „Culture“* ein und passen einige weitere Optionen an.

    ![Durchschnittslinie für „Culture“ (Kultur), Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Wenn eine Datenbeschriftung angezeigt werden soll, ändern Sie die Einstellung **Datenbeschriftung** von **Aus** in **Ein**. Dadurch wird eine Reihe an weiteren Optionen für die Datenbeschriftung angezeigt.

    ![Datenbeschriftungseinstellungen, Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Beachten Sie die Zahl, die neben dem Element **Durchschnittslinie** im Bereich **Analyse** angezeigt wird. Dieser Wert steht für die Anzahl der in Ihrem Visual verwendeten dynamischen Linien und verrät auch, von welchem Typ diese sind. Wenn wir eine **Linie für Maximalwert** für **Affordability** (Erschwinglichkeit) hinzufügen, wird im Bereich **Analyse** angezeigt, dass nun auch eine dynamische Bezugslinie vom Typ **Linie für Maximalwert** für das Visual verwendet wird.

    ![Gesamtwerte für „Linie für Maximalwert“ und „Linie für Durchschnitt“, Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Wenn das ausgewählte Visual keine dynamischen Bezugslinien verwenden kann (in diesem Fall ein Visual vom Typ **Karte**), sehen Sie die folgende Meldung, wenn Sie den Bereich **Analyse** aufrufen.

![Nicht verfügbare Analyse für ein Visual vom Typ „Karte“, Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

Sie können viele interessante Erkenntnisse gewinnen, wenn Sie mithilfe des Bereichs **Analyse** dynamische Bezugslinien erstellen.

Wir arbeiten an der Umsetzung weiterer Features und Funktionen, u. a. beispielsweise daran, dynamische Bezugslinien für mehr Visuals verfügbar zu machen. Überprüfen Sie diese Seite deshalb regelmäßig auf Neuigkeiten.

## <a name="apply-forecasting"></a>Anwenden von Vorhersagen

Wenn in Ihrer Datenquelle Zeitdaten vorhanden sind, können Sie diese für das Feature *Vorhersage* verwenden. Wählen Sie einfach ein Visual aus, und erweitern Sie dann den Abschnitt **Vorhersage** des Bereichs **Analyse**. Sie können viele Eingaben zum Ändern der Vorhersage festlegen, z. B. die **Länge der Prognose**, das **Konfidenzintervall** und weitere Eingaben. Die folgende Abbildung zeigt ein einfaches Visual vom Typ „Liniendiagramm“ mit angewendeter Vorhersage. Seien Sie kreativ (und experimentieren Sie mit der Vorhersagefunktion), um zu sehen, wie sie auf Ihre Modelle angewendet werden kann.

![Feature „Vorhersage“, Bereich „Analyse“, Visualisierungen, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> Das Vorhersagefeature ist nur für Visuals vom Typ „Liniendiagramm“ verfügbar.

## <a name="limitations"></a>Einschränkungen

Die Möglichkeit zum Verwenden von dynamischen Bezugslinien ist abhängig vom verwendeten visuellen Element. In den folgenden Listen werden diese Einschränkungen näher erläutert.

Sie können *Bezugslinie für X-Achse*, *Bezugslinie für Y-Achse* und *Symmetrieschattierung* für das folgende Visual verwenden:

* Punktdiagramm

Die Verwendung von *Bezugslinie*, *Linie für Mindestwert*, *Linie für Maximalwert*, *Linie für Durchschnitt*, *Linie für Medianwert* und *Linie für Perzentil* ist für diese Visuals verfügbar:

* Flächendiagramm
* Gruppiertes Balkendiagramm
* Gruppiertes Säulendiagramm
* Liniendiagramm
* Punktdiagramm

Für die folgenden visuellen Elemente kann nur eine *Bezugslinie* aus dem Bereich **Analyse** verwendet werden:

* Gestapeltes Flächendiagramm
* Gestapeltes Balkendiagramm
* Gestapeltes Säulendiagramm
* Wasserfalldiagramm
* Gestapeltes Balkendiagramm (100 %)
* Gestapeltes Säulendiagramm (100 %)

Die folgenden Visuals können eine *Trendlinie* verwenden, wenn Zeitdaten vorhanden sind:

* Flächendiagramm
* Gruppiertes Säulendiagramm
* Liniendiagramm
* Linien- und gruppiertes Säulendiagramm

Schließlich können Sie derzeit keine dynamischen Linien auf viele Visuals anwenden, einschließlich (aber nicht beschränkt auf):

* Trichterdiagramm
* Linien- und gruppiertes Säulendiagramm
* Linien- und gestapeltes Säulendiagramm
* Bänderdiagramm
* Nicht kartesische Visuals, z. B. Ringdiagramm, Messgerät, Matrix, Kreisdiagramm und Tabelle

*Linie für Perzentil* ist nur verfügbar, wenn importierte Daten in Power BI Desktop verwendet werden oder wenn eine Liveverbindung mit einem Modell auf einem Server mit **Analysis Service 2016** oder höher, **Azure Analysis Services** oder einem Dataset im Power BI-Dienst vorhanden ist.

## <a name="next-steps"></a>Weitere Schritte

Mit Power BI Desktop können Sie vielfältige Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in folgenden Ressourcen:

* [Neuigkeiten in Power BI Desktop](desktop-latest-update.md)
* [Power BI Desktop erwerben](desktop-get-the-desktop.md)
* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datentypen in Power BI Desktop](desktop-data-types.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Durchführen allgemeiner Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)
