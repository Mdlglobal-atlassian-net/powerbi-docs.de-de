---
title: "Verwenden der Funktion „Datenschnitt für numerischen Bereich“ in Power BI Desktop"
description: Mit dem Datenschnitt in Power BI Desktop numerische Bereiche eingrenzen
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f6e0433e8862e2acb6f0e7a72a1293e37f2185eb
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>Verwenden der Funktion „Datenschnitt für numerischen Bereich“ in Power BI Desktop
Mit dem Feature **Datenschnitt für numerischen Bereich** können Sie numerischen Spalten eine Reihe an Filtern zuweisen. Sie können numerische Daten filtern, die **zwischen** Zahlen liegen oder deren Wert **kleiner als oder gleich** oder **größer als oder gleich** eine Zahl ist. Diese Filtermethode ist unkompliziert, aber leistungsstark.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>Verwenden der Funktion „Datenschnitt für numerischen Bereich“
Der Datenschnitt für numerische Bereiche funktioniert wie jeder andere Datenschnitt. Erstellen Sie einfach eine **Datenschnitt**-Visualisierung für einen Bericht, und legen Sie dann für **Feld** einen Wert fest. In der folgenden Abbildung ist *UnitPrice* ausgewählt.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

Klicken Sie rechts oben im **Datenschnitt für numerischen Bereich** auf das Zirkumflexzeichen. Ein Menü wird angezeigt.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

Der numerische Bereich kann mithilfe von drei Bedingungen eingegrenzt werden:

* Zwischen
* Kleiner als oder gleich
* Größer als oder gleich

Wenn Sie **zwischen** auswählen, wird ein Schieberegler angezeigt, mit dem Sie die Ober- und Untergrenze des Filters einstellen können. Statt den Schieberegler zu verwenden, können Sie die Werte auch über die Eingabefelder festlegen. Das ist besonders nützlich, wenn Sie den Datenschnitt bei bestimmten ganzen Zahlen ansetzen möchten, die sich mit dem Schieberegler nicht genau einstellen lassen.

In der folgenden Abbildung wird die Berichtsseite nach Werten zwischen 500 und 1500 in der Spalte *UnitPrice* gefiltert.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

Wenn Sie **Kleiner als oder gleich** auswählen, verschwindet der linke Ziehpunkt des Schiebereglers (für den niedrigeren Wert), und nur der Ziehpunkt für den höheren Wert kann eingestellt werden. In der folgenden Abbildung wurde der Schieberegler auf 497,17 festgelegt.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

Wenn Sie **Größer als oder gleich** auswählen, verschwindet der rechte Ziehpunkt (für den höheren Wert), und der niedrigere Wert kann angepasst werden. Das sehen Sie in der nächsten Abbildung. Jetzt werden nur Elemente mit einem *UnitPrice* größer als oder gleich 750,56 in den Visualisierungen auf der Berichtsseite angezeigt.

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer-preview"></a>Ausrichten an ganzen Zahlen mit dem Slicer für numerische Bereiche (Vorschau)

Seit dem Release von **Power BI Desktop** vom Februar 2018 wird der Slicer für numerische Bereiche an ganzen Zahlen ausgerichtet. Dadurch kann der Slicer ordnungsgemäß an ganzen Zahlen ausgerichtet werden. Das Ausrichten an ganzen Zahlen gilt nicht für Dezimalfilter.


## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen
Die folgenden Überlegungen und Einschränkungen betreffen derzeit das Feature **Datenschnitt für numerischen Bereich**.

* Die Funktion **Datenschnitt für numerischen Bereich** filtert derzeit jede zugrunde liegende Zeile in den Daten, keine aggregierten Werte. Beispiel: Wenn Sie das Feld *SalesAmount* verwenden, wird der Filter auf jede Transaktion angewandt, die auf *SalesAmount* basiert, nicht auf die *SalesAmount*-Summe für jeden Datenpunkt der Visualisierung.
* Das Feature funktioniert derzeit nicht bei Measures.
* Momentan ist das Feature **Datenschnitt für numerischen Bereich** nur in **Power BI Desktop** verfügbar. Wenn Sie einen Bericht mit **Datenschnitt für numerische Bereiche** im **Power BI-Dienst** veröffentlichen, wird der Filter übernommen, aber als Listendatenschnitt angezeigt.
