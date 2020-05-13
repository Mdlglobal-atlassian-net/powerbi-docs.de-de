---
title: Große Datasets, Datenpunktgrenzwerte und Datenstrategien
description: Datengrenzwerte für Visuals und Datenverringerungsstrategien
author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: a874875c470cd85720570e57b7c6d7cf50dabca1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274165"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>Anwenden von Datenpunktgrenzwerten und Strategien nach Visualtyp

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

Beim Rendern eines Visuals in Power BI muss die Visualisierung schnell und genau sein. Dafür müssen für jeden Visualtyp grundlegende Algorithmen konfiguriert werden. Visuals in Power BI müssen über ausreichend Flexibilität verfügen, um verschiedene Größen von Datasets zu verarbeiten. Einige Datasets enthalten nur wenige Datenpunkte, während andere mehrere Petabytes aufweisen. In diesem Artikel werden die von Power BI verwendeten Strategien zum Rendern von Visualisierungen beschrieben.

## <a name="data-reduction-strategies"></a>Datenverringerungsstrategien
Jedes Visual nutzt mindestens eine *Datenverringerungsstrategie*, um die potenziell großen Mengen von zu analysierenden Daten zu verarbeiten. Selbst einfache Tabellen wenden eine Strategie an, um zu vermeiden, das gesamte Dataset für den Client zu laden.  Die verwendete Verringerungsstrategie variiert je nach Visualtyp. Jedes Visual wählt eine unterstützte *Datenverringerungsstrategie* beim Generieren der Datenanforderung aus, die an den Server gesendet wird. 

Jedes Visual steuert die Parameter dieser Strategien, um die Gesamtmenge an Daten zu beeinflussen.   

## <a name="strategies"></a>Strategien
Für jede Strategie gibt es Standardwerte, die auf Form und Typ der visualisierten Daten basieren. Diese Standardwerte können jedoch im Formatierungsbereich von Power BI überschrieben werden, um die Ansicht entsprechend anzupassen. 

* **Data Windowing** (Segmentierung): Hiermit können Sie Benutzern ermöglichen, durch die Daten in einem Visual zu scrollen, indem die Fragmente des gesamten Datasets progressiv geladen werden.
* **TopN** (Oberste N): Hiermit werden nur die ersten N Elemente angezeigt.
* **Simple Sample** (Einfaches Beispiel): Hiermit werden das erste und letzte Element sowie N gleichmäßig verteilte Elemente dazwischen angezeigt.
* **BottomN** (Unterste N): Hiermit werden nur die letzten N Elemente angezeigt.  Dies eignet sich zur Überwachung häufig aktualisierter Daten.
* **High-density sampling** (Stichprobenentnahme mit hoher Dichte): Dies ist ein verbesserter Algorithmus für die Stichprobenentnahme, bei dem Ausreißer und bzw. oder die Form von Kurven besser berücksichtigt werden.
    * **Binned line sampling** (Stichprobenentnahme für Zeilen mit Binning): Hiermit werden Beispieldatenpunkte basierend auf Ausreißern in Klassen auf einer Achse entnommen.
    * **Overlapping points sampling** (Stichprobenentnahme für überlappende Datenpunkte): Hiermit werden Datenpunkte anhand überlappender Werte entnommen, um Ausreißer beizubehalten.

## <a name="statistics"></a>Statistik
Bestimmte Modelle können Statistiken zur Anzahl von Werten für bestimmte Spalten bereitstellen. Wenn solche Informationen vorhanden sind, werden sie dazu genutzt, mehrere Hierarchien ausgewogener darzustellen, wenn ein Visual die Anzahl von Werten für eine Strategie nicht explizit überschreibt.

Weitere Informationen erhalten Sie unter [What's new in Analysis Services (Neuerungen in Analysis Services)](https://docs.microsoft.com/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017).

## <a name="dynamic-limits"></a>Dynamische Grenzwerte
Neben den oben genannten Strategien verwenden Visuals mit zwei Hierarchien von Gruppierungsspalten („Achse und „Legende“ oder „Kategorie“ und „Reihe“) eine weitere Strategie, *dynamische Grenzwerte*.  Dynamische Grenzwerte sind dafür konzipiert, Datenpunkte besser auszugleichen. 

Dynamische Grenzwerte stellen eine bessere Auswahl an Punkten für Daten mit geringer Dichte bereit als statische Grenzwerte. Ein Visual könnte beispielsweise dafür konfiguriert werden, 100 Kategorien und 10 Reihen mit insgesamt 1.000 Punkten auszuwählen. Tatsächlich enthalten die Daten aber nur 50 Kategorien und 20 Reihen.  Zur Abfragelaufzeit wählen die dynamischen Grenzwerte alle 20 Reihen aus, um die 1.000 angeforderten Datenpunkte aufzufüllen.

Dynamische Grenzwerte werden automatisch angewendet, wenn der Server wie in den folgenden Fällen dazu fähig ist:

* [Bei Nutzung der SuperDax-Funktionen des Servers](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/) in Power BI Desktop mit der lokalen SSAS-Version 2016 oder höher

* Bei Verwendung eines importierten Modells, einer direkten Abfrage oder von Live Connect mit dem Dienst oder mit AS PaaS in Power BI Desktop oder dem Power BI-Dienst. 

* Beim Herstellen einer Verbindung über ein lokales Gateway mit einem lokalen SSAS-Server im Power BI-Dienst können dynamische Grenzwerte nicht verwendet werden. Das lokale Gateway unterstützt diese Strategie, die eine andere Struktur von Resultsets vom lokalen SSAS-Server zurückgibt, nicht vollständig.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Strategien und Datenpunktgrenzwerte nach Visualtyp

### <a name="area-chart"></a>Flächendiagramm
Siehe [Funktionsweise der Stichprobenentnahme für Linienelemente](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Balken-/Säulendiagramme
- Im kategorischen Modus
    - Kategorien: Virtualisierung mit Fenstern von 500 Zeilen zur gleichen Zeit
    - Reihen: Oberste 60
    - Im Skalarmodus (hier könnten dynamische Grenzwerte angewandt werden)
        - Maximale Anzahl von Datenpunkten: 10.000
        - Kategorien: Stichprobe von 500 Werten
        - Reihen: Oberste 20 Werte

### <a name="card-multirow"></a>Karte (mehrzeilig) 
- Werte: Virtualisierung mit Fenstern von 200 Zeilen zur gleichen Zeit

### <a name="combo-chart"></a>Kombinationsdiagramm
 Verwendet die gleichen Strategien wie Säulendiagramme Beachten Sie, dass die Zeile im **Kombinationsdiagramm** nicht den Algorithmus für hohe Dichte verwendet, den **Liniendiagramme** verwenden.

### <a name="power-bi-visuals"></a>Power BI-Visuals
Kann bis zu 30.000 Datenpunkte abrufen. Die Entscheidung, welche Strategien angewandt werden sollen, liegt jedoch beim Autor des visuellen Elements. Der Standardgrenzwert ist 1.000, aber der Ersteller des visuellen Elements kann dies ändern und maximal 30.000 festlegen.

### <a name="doughnut"></a>Ringdiagramm
- Maximale Anzahl von Datenpunkten: 3.500
- Gruppe: Oberste 500
- Details: Oberste 20

### <a name="filled-map-choropleth"></a>Flächenkartogramm (Choroplethenkarte) 
Flächenkartogramme können Statistiken oder dynamische Grenzwerte verwenden. Power BI versucht Datenverringerungsstrategien in folgender Reihenfolge anzuwenden: dynamische Grenzwerte, Statistiken und zuletzt Konfiguration. 
- Maximale Anzahl von Datenpunkten: 10.000
- Kategorien: Oberste 500
- Reihe (Wenn X und Y vorhanden sind): Oberste 20

### <a name="funnel"></a>Trichterdiagramm
- Maximale Anzahl von Datenpunkten: 3.500
- Kategorien: Oberste 3.500

### <a name="kpi"></a>KPI
- Trendachse
- Unterste 3.500

### <a name="line-chart"></a>Liniendiagramm
Siehe [Funktionsweise der Stichprobenentnahme für Linienelemente](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Liniendiagramm mit hoher Dichte
Siehe [Stichprobenentnahme mit hoher Dichte](../create-reports/desktop-high-density-sampling.md)

### <a name="map"></a>Zuordnung 
- Maximale Anzahl von Datenpunkten: 3.500

Je nach Konfiguration kann eine Karte Folgendes enthalten:
- Ort: Oberste 3.500
- Ort, Größe: Oberste 3.500
- Ort, Aggregierte Breitengrade und Längengrade (+/-Größe): Oberste 3.500
- Breitengrade, Längengrade: siehe [Punktdiagramme mit hoher Dichte](../create-reports/desktop-high-density-scatter-charts.md)
- Breitengrad, Längengrad, Größe: Oberste 3.500
- Legende, Breitengrade, Längengrade: siehe [Punktdiagramme mit hoher Dichte](../create-reports/desktop-high-density-scatter-charts.md)
- Legende, Breitengrade, Längengrade, Größe: Oberste 233 Legenden, oberste 15 Breitengrade und Längengrade (hier könnten Statistiken oder dynamische Grenzwerte angewandt werden)
- Ort, Legende, Aggregierte Breitengrade und Längengrade (+/-Größe): Oberste 233 Orte, oberste 15 Legenden (hier könnten Statistiken oder dynamische Grenzwerte angewandt werden)

### <a name="matrix"></a>Matrix
- Zeilen: Virtualisierung mit Fenstern von 500 Zeilen zur gleichen Zeit
- Spalten: Oberste 100 Gruppierungsspalten 
- Werte: Mehrere Werte werden für die Datenverringerung nicht berücksichtigt.

### <a name="powerapps-visual"></a>Visuelles PowerApps-Element
Kann bis zu 30.000 Datenpunkte abrufen. Die Entscheidung, welche Strategien angewandt werden sollen, liegt jedoch beim Autor des visuellen Elements. Der Standardgrenzwert ist 1.000, aber der Ersteller des visuellen Elements kann dies ändern und maximal 30.000 festlegen.

### <a name="radial-gauge"></a>Radiale Messanzeige
Keine Datenverringerungsstrategien

### <a name="slicer"></a>Slicer
- Werte: Virtualisierung mit Fenstern von 200 Zeilen zur gleichen Zeit

### <a name="scatter-chart-high-density"></a>Punktdiagramm (mit hoher Dichte)
Siehe [Punktdiagramme mit hoher Dichte](https://docs.microsoft.com/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Kreis
- Maximale Anzahl von Datenpunkten: 3.500
- Gruppe: Oberste 500
- Details: Oberste 20

### <a name="r--python-visuals"></a>R- und Python-Visuals
Auf 150.000 Zeilen beschränkt. Wenn mehr als 150.000 Zeilen ausgewählt werden, werden nur die oberen 150.000 Zeilen verwendet.

### <a name="ribbon-chart"></a>Bänderdiagramm
- Im kategorischen Modus
    - Kategorien: Virtualisierung (Data Windowing) mit Fenstern von 500 Zeilen zur gleichen Zeit
    - Reihen: Oberste 60
    - Im Skalarmodus (hier könnten dynamische Grenzwerte angewandt werden)
        - Maximale Anzahl von Datenpunkten: 10.000
        - Kategorien: Stichprobe von 500 Werten
        - Reihen: Oberste 20 Werte

### <a name="shape-map-preview"></a>Formenzuordnung (Vorschau)
Die Formenzuordnung kann Statistiken oder dynamische Grenzwerte verwenden. 
- Maximale Anzahl von Datenpunkten: 1.500
- Kategorien: Oberste 500

### <a name="table"></a>Tabelle
- Werte: Virtualisierung (Data Windowing) mit Fenstern von 500 Zeilen zur gleichen Zeit

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Kacheldiagramm (hier könnten Statistiken oder dynamische Grenzwerte verwendet werden)
- Maximale Anzahl von Datenpunkten: 3.500
- Gruppe: Oberste 500
- Details: Oberste 20

### <a name="waterfall-chart"></a>Wasserfalldiagramm
- Wenn nur der Kategoriebucket vorhanden ist
    - Maximale Anzahl von Datenpunkten: 3.500
    - Nur Kategorie: Oberste 3.500
- Wenn sowohl die Kategorie als auch die Aufschlüsselung vorhanden sind.
    - Kategorie: Virtualisierung (Data Windowing) mit Fenstern von 30 Zeilen zur gleichen Zeit
    - Aufschlüsselung: Oberste 200 Werte


## <a name="next-steps"></a>Nächste Schritte
[Visualisierungstypen](power-bi-report-visualizations.md)
