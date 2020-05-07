---
title: Verwenden von Gitternetzlinien und „Am Raster ausrichten“ in Power BI Desktop-Berichten
description: Verwenden von Gitternetzlinien, der Option „Am Raster ausrichten“, der Z-Reihenfolge, Ausrichtung und Verteilung in Power BI Desktop-Berichten
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b7be8601a535843fc012cf7ea0f2ae723ea6ba79
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73878211"
---
# <a name="use-gridlines-and-snap-to-grid-in-power-bi-desktop-reports"></a>Verwenden von Gitternetzlinien und „Am Raster ausrichten“ in Power BI Desktop-Berichten
Der Berichtszeichenbereich in **Power BI Desktop** enthält Gitternetzlinien, mit denen Sie Visuals genau auf eine Berichtsseite ausrichten können, sowie die Funktion „Am Raster ausrichten“ verwenden können, sodass Berichte aufgeräumt, organisiert und konsistent aussehen.

In **Power BI Desktop** können Sie außerdem die Z-Reihenfolge (in den Vordergrund/Hintergrund setzen) von Objekten in einem Bericht anpassen und Objekte im Zeichenbereich ausrichten oder mit gleichem Abstand verteilen.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_0.png)

## <a name="enabling-gridlines-and-snap-to-grid"></a>Aktivieren von Gitternetzlinien und die Funktion „Am Raster ausrichten“
Um Gitternetzlinien und die Option „Am Raster ausrichten“ zu aktivieren, wählen Sie das Menüband **Ansicht** aus, und aktiveren Sie dann die Kontrollkästchen für **Gitternetzlinien anzeigen** und **Objekte am Raster ausrichten**. Sie können eines oder beide Optionen aktivieren, da die Funktionen nicht abhängig voneinander sind.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_1.png)

> [!NOTE]
> Wenn **Gitternetzlinien anzeigen** und **Objekte am Raster ausrichten** deaktiviert sind, stellen Sie eine Verbindung mit einer beliebigen Datenquelle her, um diese Funktionen zu aktivieren.

## <a name="using-gridlines"></a>Verwenden von Gitternetzlinien
Bei Gitternetzlinien handelt es sich um sichtbare Hinweise, mit den Sie Ihre Visuals ausrichten können. Wenn Sie die Ausrichtung mehrerer Visuals überprüfen möchten, können Sie Gitternetzlinien verwenden, um die Ausrichtung anhand der Rahmen zu beurteilen.

Sie können STRG+Klick verwenden, um mehrere Visuals gleichzeitig auszuwählen. Dann werden deren Rahmen angezeigt, sodass Sie die Ausrichtung der Visuals überprüfen können.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_2.png)

### <a name="using-gridlines-inside-visuals"></a>Verwenden von Gitternetzlinien in Visuals
In Power BI enthalten Visuals auch Gitternetzlinien, die sichtbare Unterstützung zum Vergleichen von Datenpunkten und Werten bieten. Ab der im September 2017 veröffentlichten Version von **Power BI Desktop** können Sie die Gitternetzlinien in Visuals mit der Karte **X-Achse** oder **Y-Achse** (je nach Typ des Visuals) im Abschnitt **Format** des Bereichs **Visualisierungen** verwalten. Sie können die folgenden Elemente von Gitternetzlinien in einem Visual verwalten:

* Aktivieren oder Deaktivieren von Gitternetzlinien
* Ändern der Farbe von Gitternetzlinien
* Anpassen der Strichstärke (Breite) von Gitternetzlinien
* Auswählen der Linienart der Gitternetzlinien im Visual, z.B. „Durchgezogen“, „Gestrichelt“ oder „Gepunktet“

In Berichten, in denen dunkle Hintergründe für Visuals verwendet werden, kann das Ändern bestimmter Elemente von Gitternetzlinien besonders hilfreich sein. In der folgenden Abbildung wird der Abschnitt **Gitternetzlinien** auf der Karte **Y-Achse** dargestellt.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_9.png)

## <a name="using-snap-to-grid"></a>Verwenden von „Am Raster ausrichten“
Wenn Sie die Funktion **Objekte am Raster ausrichten** aktivieren, werden alle Visualisierungen auf der Zeichenfläche in **Power BI Desktop** automatisch an der nächsten Gitternetzachse ausgerichtet, wenn diese bewegt (oder in der Größe angepasst) werden. So können Sie leicht sicherstellen, dass mehrere Visualisierungen an derselben Stelle der Seite horizontal oder vertikal ausgerichtet sind.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_3.png)

Und das ist schon alles, was Sie über **Gitternetzlinien** und die Funktion **Am Raster ausrichten** wissen müssen, damit Sie Visuals in Berichten sauber ausrichten können.

## <a name="using-z-order-align-and-distribute"></a>Verwenden der Z-Reihenfolge, Ausrichten und Verteilen
Sie können in Berichten die Reihenfolge von Visuals auf der Vordergrund-Hintergrund-Achse ändern (die *Z-Reihenfolge* von Elementen). Mithilfe dieses Features können sich Visuals in beliebiger Weise überlappen. Passen Sie anschließend die Vordergrund-Hintergrund-Reihenfolge für jedes Visual an. Legen Sie die Reihenfolge Ihrer Visuals mithilfe der Schaltflächen **Nach vorne** und **Nach hinten** fest, die im Abschnitt **Anordnen** des Menübands **Formatieren** zu finden ist. Das Menüband **Formatieren** wird angezeigt, sobald Sie mindestens ein Visual auf der Seite anklicken.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_4.png)

Mithilfe des Menübands **Formatieren** können Sie Ihre Visuals auf verschiedene Weise ausrichten, um sicherzustellen, dass diese bestmöglich auf der Seite angezeigt werden.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_5.png)

Die Schaltfläche **Ausrichten** richtet die Visualisierung an der Kante (oder in der Mitte) des Berichtszeichenbereichs wie in der folgenden Abbildung dargestellt aus.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_6.png)

Wenn mindestens zwei Visuals ausgewählt sind, werden sie zusammen ausgerichtet, wobei die Begrenzung einer der Visualisierungen zur Ausrichtung dient. Wenn Sie z.B. zwei Visuals auswählen und auf die Schaltfläche **Links ausrichten** klicken, werden die Visuals an der am weitesten links liegenden Begrenzung aller ausgewählten Visuals ausgerichtet.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_7.png)

Sie können Visualisierungen im Berichtszeichenbereich auch gleich verteilen (horizontal und vertikal). Verwenden Sie einfach Schaltfläche **Verteilen** im Menüband **Format**.

![](media/desktop-gridlines-snap-to-grid/snap-to-grid_8.png)

Mit den Tools für Gitternetzlinien, Ausrichtung und Verteilung können Sie Ihre Berichte nach Belieben gestalten.

