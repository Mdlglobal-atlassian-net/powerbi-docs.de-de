---
title: Beispiele von Power BI-Visuals
description: In diesem Artikel werden Beispiele von Power BI-Visuals vorgestellt, darunter Slicer, mehr als 20 Arten von Diagrammen, WebGL- und R-Visuals sowie Skripts.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132385"
---
# <a name="samples-of-power-bi-visuals"></a>Beispiele für Power BI-Visuals

Sie können diese Power BI-Visuals von GitHub herunterladen, einsetzen und bearbeiten. Diese Beispiele veranschaulichen den Umgang mit typischen Situationen bei der Entwicklung mit Power BI.

## <a name="slicers"></a>Slicer

Ein Slicer grenzt den Teil der Daten ein, die in anderen Visualisierungen in einem Bericht gezeigt werden. Slicer sind eine von mehreren Möglichkeiten in Power BI zum Filtern von Daten.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Chiclet-Slicer](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Zeigt Bild- oder Textschaltflächen an, die in der Canvas als Filter für andere Visuals fungieren | [Timeline-Slicer](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Grafische Auswahl des Datumsbereichs zum Filtern nach Datum | [Slicerbeispiel](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Veranschaulicht die Verwendung der API für erweiterte Filterung

## <a name="charts"></a>Diagramme

Lassen Sie sich von unserem Katalog inspirieren, der Balkendiagramme, Kreisdiagramme, eine Wortwolke u. a. enthält.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Aster-Plot](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Eine Variante eines standardmäßigen Ringdiagramms, bei der ein zweiter Wert dazu dient, einen Pfeilwinkel zu steuern. | [Bullet Chart ](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Ein Balkendiagramm mit zusätzlichen visuellen Elementen, um Kontext zum Nachverfolgen von Zielen bereitzustellen | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Eine grafische Methode zum Anzeigen der Beziehungen zwischen Daten in einer Matrix
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Dot plot](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Stellt Sie die Verteilung von Häufigkeiten auf übersichtliche Weise dar | [Dual KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Visualisiert zwei Measures effizient über einen Zeitraum hinweg und bildet Trends auf einer gemeinsamen Zeitachse ab | [Enhanced Scatter](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Bietet Verbesserungen des vorhandenen Punktdiagramms
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Force Graph](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Erzwingt ein Layoutdiagramm mit gekrümmten Pfad, das sich zum Anzeigen von Verbindungen zwischen Entitäten eignet | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Ein Balkendiagramm, das die Zeitachse oder den Zeitplan eines Projekts mit Ressourcen veranschaulicht | [Tabellenheatmap](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Hiermit vergleichen Sie Daten mithilfe von Farben in einer Tabelle problemlos und intuitiv miteinander.
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Histogram-Diagramm](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualisiert die Verteilung von Daten über einen Zeitraum hinweg oder in einem bestimmten Zeitrahmen | [LineDot-Diagramm](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Animiertes Liniendiagramm mit sich bewegenden Punkten, um eine Zielgruppe für die Daten zu interessieren | [Mekko-Diagramm](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Eine Mischung aus einem zu 100% gestapelten Säulendiagramm und einem zu 100% gestapelten Balkendiagramm, die in einer Ansicht kombiniert werden.
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Multi-KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Eine leistungsstarke Visualisierung mehrerer KPIs mit einem Schlüssel-KPI zusammen mit mehreren Sparklines für unterstützende Daten | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Ein leistungsstarker KPI-Indikator mit mehrzeiligem Diagramm und Beschriftungen für aktuelles Datum, Wert und Abweichungen | [Power-KPI-Matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Ermöglicht das Überwachen von Balanced Scorecards und einer unbegrenzten Anzahl von Metriken und KPIs in einer kompakten, leicht lesbaren Liste
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Pulsdiagramm](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Liniendiagramm mit Anmerkungen zu den wichtigsten Ereignissen, das sich ideal zur Untermauerung von Aussagen mit Daten eignet| [Netzdiagramm](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Zeigt mehrere auf einer Kategorieachse gezeichnete Messwerte zum Vergleichen von Attributen | [Sankey-Diagramm](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Flussdiagramm, bei dem die Breite der Datenreihe proportional zum Umfang des Datenflusses ist
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Stream Graph](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Gestapeltes Flächendiagramm mit geglätteter Interpolation zur Darstellung von Werten in einem bestimmten Zeitraum | [Sunburst-Diagramm](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Ringdiagramm mit mehreren Ebenen zur Visualisierung hierarchischer Daten| [Tornado-Diagramm](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Dient zum Vergleichen der relativen Wichtigkeit von Variablen zwischen zwei Gruppen
 | <img src="media/samples/word-cloud.png" width="200">
 | [Word Cloud](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Dient zum Erstellen eines interessanten Visuals mit häufig in Ihren Daten verwendetem Text

## <a name="webgl"></a>WebGL

WebGL ermöglicht die Verwendung einer auf OpenGL ES 2.0 basierenden API für das 2D- und 3D-Rendering von Webinhalten in einer HTML-Canvas.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Globe Map](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Abbilden von Standorten auf einer interaktiven 3D-Karte

## <a name="r-visuals"></a>R-Visuals

Diese Beispiele veranschaulichen, wie die analytischen und visuellen Möglichkeiten von R-Visuals und R-Skripts genutzt werden können.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Zuordnungsregeln](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Ermitteln Sie Beziehung zwischen scheinbar nicht in Beziehung stehenden Daten mithilfe von if-then-Anweisungen. | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Dient zum Finden von Ähnlichkeitsgruppen in Ihren Daten mithilfe des k-Means-Algorithmus | [Clustering mit Ausreißern](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Dient zum Finden von Ähnlichkeitsgruppen und Ausreißern in Ihren Daten
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Korrelationsplot](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Dient zum Markieren der am häufigsten korrelierten Variablen in einer Datentabelle | [Entscheidungsstrukturdiagramm](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Schematisches baumförmiges Diagramm zur Bestimmung der statistischen Wahrscheinlichkeit mittels rekursiver Partitionierung | [Forecasting TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Zeitreihenvorhersage für Reihen mit mehreren Saisonabhängigkeiten unter Verwendung des TBATS-Modells
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Vorhersagen mit ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Vorhersagen künftiger Werte auf Grundlage historischer Daten mithilfe von ARIMA (Autoregressive Integrated Moving Average) | [Trichterdiagramm](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Dient zum Finden von Ausreißern in Ihren Daten mithilfe eines Trichterdiagramms | [Erkennung von Ausreißern](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Dient zum Finden von Ausreißern in Ihren Daten mithilfe der geeignetsten Methode und Zeichnung
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Spline-Diagramm](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Dient zum Verstehen und Visualisieren überflüssiger Daten | [Diagramm für die Zeitreihenaufgliederung](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Dient zum Verstehen von Zeitreihenkomponenten mithilfe von STL (Seasonal and Trend decomposition using Loess) | [Diagramm für die Zeitreihenprognose](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Verwenden exponentieller Glättungsmodelle zum Vorhersagen zukünftiger Werte auf Grundlage der zuvor beobachteten Werte

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Erstellen von Power BI-Visuals finden Sie unter [Tutorial: Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md).
