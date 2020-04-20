---
title: Verwenden eines Slicers für numerische Bereiche in Power BI
description: Hier erfahren Sie, wie Sie mit einem Slicer in Power BI numerische Bereiche eingrenzen.
author: davidiseminger
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: bd5f937154edf9f8b6a86fb7f53690943a7f3a53
ms.sourcegitcommit: 915cb7d8088deb0d9d86f3b15dfb4f6f5b1b869c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2020
ms.locfileid: "81006639"
---
# <a name="use-the-numeric-range-slicer-in-power-bi"></a>Verwenden eines Slicers für numerische Bereiche in Power BI

[!INCLUDE [applies-to](includes/applies-to.md)] [!INCLUDE [yes-desktop](includes/yes-desktop.md)] [!INCLUDE [yes-service](includes/yes-service.md)]

Mit dem Feature „Datenschnitt für numerischen Bereich“ können Sie numerischen Spalten eine Reihe an Filtern zuweisen. Sie haben drei Optionen zum Filtern von numerischen Daten: Daten, die zwischen Zahlen liegen oder deren Wert kleiner als oder gleich oder größer als oder gleich eine Zahl ist. Diese einfache Technik eignet sich ausgezeichnet, um Ihre Daten zu filtern.

![Visual mit dem Datenschnitt für numerischen Bereich](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="video"></a>Video

In diesem Video wird die Erstellung eines Slicers für numerische Bereiche veranschaulicht.

> [!NOTE]
> In diesem Video wird eine ältere Version von Power BI Desktop verwendet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 


## <a name="add-a-numeric-range-slicer"></a>Hinzufügen eines Slicers für numerische Bereiche

Der Datenschnitt für numerische Bereiche funktioniert wie jeder andere Datenschnitt. Erstellen Sie einfach ein **Datenschnittvisual** für einen Bericht, und legen Sie dann für **Feld** einen numerischen Wert fest. In der folgenden Abbildung ist das Feld **LineTotal** ausgewählt.

![Erstellen der Funktion „Datenschnitt für numerischen Bereich“](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Wählen Sie rechts oben in der Funktion „Datenschnitt für numerischen Bereich“ die Verknüpfung mit dem Pfeil nach unten aus. Dann wird ein Menü angezeigt.

![Menü „Datenschnitt für numerischen Bereich“](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Für den numerischen Bereich können Sie eine der folgenden drei Optionen auswählen:

* **Zwischen**
* **Kleiner als oder gleich**
* **Größer als oder gleich**

Wenn Sie im Menü **Zwischen** auswählen, wird ein Schieberegler angezeigt. Mit dem Schieberegler können Sie numerische Werte auswählen, die zwischen den Zahlen liegen. Manchmal ist es aufgrund der Granularität beim Bewegen der Datenschnittleiste schwierig, genau diese Zahl zu treffen. Sie können auch den Schieberegler verwenden und ein beliebiges Feld auswählen, um die gewünschten Werte einzugeben. Diese Option ist praktisch, wenn Sie den Datenschnitt für bestimmte Zahlen ausführen möchten.

In der folgenden Abbildung wird die Berichtsseite nach Werten zwischen 2500,00 und 6000,00 in der Spalte **LineTotal** gefiltert.

![Datenschnitt für numerischen Bereich mit Zwischenwerten](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Wenn Sie **Kleiner als oder gleich** auswählen, verschwindet der linke Ziehpunkt des Schiebereglers (für den niedrigeren Wert), und nur der Ziehpunkt für den höheren Wert kann eingestellt werden. In der folgenden Abbildung wurde der Schieberegler auf den Maximalwert von 5928,19 festgelegt.

![Datenschnitt für numerischen Bereich mit „Kleiner als“](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Wenn Sie schließlich **Größer als oder gleich** auswählen, wird der rechte Schieberegler (höherer Wert) ausgeblendet. Anschließend können Sie den niedrigeren Wert anpassen, wie in der folgenden Abbildung dargestellt. Jetzt werden nur Elemente mit einem **LineTotal** größer als oder gleich 4902,99 in den Visuals auf der Berichtsseite angezeigt.

![Datenschnitt für numerischen Bereich mit „Größer als“](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Ausrichten an ganzen Zahlen mit dem Datenschnitt für numerische Bereiche

Ein Datenschnitt für den numerischen Bereich richtet sich an ganzen Zahlen aus, wenn der Datentyp des zugrunde liegenden Felds *Ganze Zahl* ist. Durch dieses Feature kann der Datenschnitt ordnungsgemäß an ganzen Zahlen ausgerichtet werden. In Feldern vom Typ *Dezimalzahl* können Sie Bruchzahlen eingeben oder diese darin auswählen. Die im Textfeld angewendete Formatierung entspricht der im Feld festgelegten Formatierung, auch wenn Sie genauere Zahlen eingeben oder auswählen können.

## <a name="display-formatting-with-the-date-range-slicer"></a>Anzeigen der Formatierung mit dem Datenschnitt für den Datumsbereich

Wenn Sie einen Datenschnitt verwenden, um einen Datumsbereich anzuzeigen oder einzustellen, werden die Daten im Format *Kurzes Datum* angezeigt. Das Datumsformat wird durch den Browser oder das Gebietsschema des Betriebssystems des Benutzers festgelegt. Somit ist es das Anzeigeformat, unabhängig davon, welche Einstellungen der Datentyp für die zugrunde liegenden Daten oder das Modell vorgenommen hat.

Sie könnten z.B. ein langes Datumsformat für den zugrunde liegenden Datentyp verwenden. In diesem Fall würde ein Datumsformat wie *dddddd, MMMM d, yyyyy* ein Datum in anderen Grafiken oder Umständen wie *Mittwoch, 14. März 2001* formatieren. Im Datenschnitt für Datumsbereiche wird dieses Datum im Datenschnitt als *03/14/2001* angezeigt.

Durch das Anzeigen des kurzen Datumsformats im Datenschnitt wird sichergestellt, dass die Länge der Zeichenfolge innerhalb des Datenschnitts konsistent und kompakt bleibt.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Die folgenden Überlegungen und Einschränkungen betreffen das Feature „Datenschnitt für numerischen Bereich“:

* Die Funktion „Datenschnitt für numerischen Bereich“ filtert jede zugrunde liegende Zeile in den Daten, keine aggregierten Werte. Nehmen wir beispielsweise an, Sie verwenden das Feld *Betrag der Verkäufe*. Der Datenschnitt filtert dann jede Transaktion basierend auf dem Betrag der Verkäufe, nicht nach der Summe des Verkaufsbetrags für jeden Datenpunkt eines Visuals.
* Das Feature funktioniert derzeit nicht bei Measures.
* Sie können eine beliebige Zahl in einen numerischen Datenschnitt eingeben, auch wenn sie außerhalb des Wertebereichs der zugrunde liegenden Spalte liegt. Mit dieser Option können Sie Filter einrichten, wenn Sie wissen, dass sich die Daten in Zukunft ändern können.
