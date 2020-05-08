---
title: Verwenden von berechneten Spalten in Power BI Desktop
description: Berechnete Spalten in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 425bf50ad6eb4da9b50f7d9cdc760ef71cb7bff2
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753283"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Erstellen von berechneten Spalten in Power BI Desktop
Mit berechneten Spalten können Sie einer bereits in Ihrem Modell vorhandenen Tabelle neue Daten hinzufügen. Aber statt Werte abzufragen und sie aus einer Datenquelle in Ihre neue Spalte zu laden, erstellen Sie eine DAX-Formel, die die Werte der Spalte definiert. In Power BI Desktop werden berechnete Spalten mithilfe der Funktion „Neue Spalte“ in der **Berichtsansicht** erstellt.

Im Gegensatz zu benutzerdefinierten Spalten, die als Teil einer Abfrage im Abfrage-Editor mithilfe von **Benutzerdefinierte Spalte hinzufügen** erstellt werden, basieren berechnete Spalten, die in der **Berichtsansicht** oder in der **Datenansicht** erstellt werden, auf bereits in das Modell geladenen Daten. Sie können sich beispielsweise dazu entschließen, Werte aus zwei verschiedenen Spalten in zwei verschiedenen, aber aufeinander bezogenen Tabellen zu verketten, eine Addition auszuführen oder Teilzeichenfolgen zu extrahieren.

Die von Ihnen erstellten berechneten Spalten werden ebenso in der Liste **Felder** angezeigt wie jedes andere Feld, sie weisen jedoch ein besonderes Symbol auf, das die Werte als Ergebnis einer Formel ausweist. Sie können Ihre Spalten nach Belieben benennen und sie Berichtsvisualisierungen hinzufügen, genau wie andere Felder.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Die berechneten Spalten berechnen die Ergebnisse mithilfe von DAX, einer Formelsprache, die für die Arbeit mit relationalen Daten, wie sie in Power BI Desktop verwendet werden, konzipiert ist. DAX beinhaltet eine Bibliothek mit über 200 Funktionen, Operatoren und Konstrukten. Diese bietet immense Flexibilität beim Erstellen von Formeln zum Berechnen von Ergebnissen für nahezu jede benötigte Datenanalyse. Weitere Informationen zu DAX finden Sie unter [DAX-Grundlagen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

DAX-Formeln sind ähnlich wie Excel-Formeln. Tatsächlich verwendet DAX viele der gleichen Formeln wie Excel. DAX-Funktionen sind jedoch für die Überarbeitung von interaktiv segmentierten oder in einem Bericht gefilterten Daten, wie in Power BI-Desktop, konzipiert. In Excel können Sie für jede Zeile in einer Tabelle eine andere Formel verwenden. Wenn Sie in Power BI eine DAX-Formel für eine neue Spalte erstellen, wird für jede Zeile in der Tabelle ein Ergebnis berechnet. Spaltenwerte werden bei Bedarf neu berechnet, etwa wenn die zugrundeliegenden Daten aktualisiert werden und sich Werte geändert haben.

## <a name="lets-look-at-an-example"></a>Betrachten wir dazu ein Beispiel.
Tyge ist Versandleiter bei Contoso und möchte einen Bericht erstellen, aus dem die Anzahl der Lieferungen in verschiedene Städte hervorgeht. Jeff verfügt über eine Tabelle **Geography** (Geographie) mit separaten Feldern für City (Stadt) und State (Bundesstaat). Allerdings möchte Jeff in seinem Bericht die Werte City (Stadt) und State (Bundesstaat) als einen einzigen Wert in derselben Zeile anzeigen. Zurzeit ist in der Tabelle **Geography** (Geographie) von Jeff das gewünschte Feld nicht vorhanden.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Mit einer berechneten Spalte kann Jeff aber die Städte aus der Spalte **City** (Stadt) mit den Bundesländern aus der Spalte **State** (Bundesstaat) zusammenführen.

Jeff klickt mit der rechten Maustaste auf die Tabelle **Geography** (Geografie) und klickt dann auf **Neue Spalte**. Anschließend gibt Tyge die folgende DAX-Formel in die Bearbeitungsleiste ein:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Mithilfe dieser Formel wird einfach eine neue Spalte mit dem Namen **CityState** (Stadt, Staat) erstellt. Für jede Zeile in der Tabelle **Geography** (Geographie) verwendet die Formel Werte aus der Spalte **City** (Stadt), fügt ein Komma und ein Leerzeichen hinzu und verkettet dann Werte aus der Spalte **State** (Staat).

Jeff hat nun das gewünschte Feld.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Jeff kann das Feld jetzt zusammen mit der Anzahl der Lieferungen zum Berichtszeichenbereich hinzufügen. Mit wenig Aufwand hat Jeff nun ein Feld **CityState** (Stadt, Staat), das zu nahezu jedem Visualisierungstyp hinzugefügt werden kann. Wenn Jeff eine neue Karte erstellt, weiß Power BI Desktop bereits, wie die Werte City (Stadt) und State (Bundesstaat) in der neuen Spalte zu lesen sind.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>Nächste Schritte
Dies ist nur eine kurze Einführung in berechnete Spalten. Weitere Informationen finden Sie in den folgenden Artikeln:

* Weitere Informationen zum Herunterladen einer Beispieldatei und zur ausführlichen Lerneinheit zum Erstellen weiterer Spalten finden Sie unter [Tutorial: Erstellen von berechneten Spalten in Power BI Desktop](desktop-tutorial-create-calculated-columns.md).

* Weitere Informationen zu DAX finden Sie unter [DAX-Grundlagen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

* Weitere Informationen über Spalten, die im Rahmen von Abfragen erstellt werden, finden Sie im Abschnitt **Erstellen von benutzerdefinierten Spalten** in [Allgemeine Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md).  

