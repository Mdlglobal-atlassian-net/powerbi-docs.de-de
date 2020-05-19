---
title: Tipps und Tricks zur Farbformatierung in Berichten
description: Tipps und Tricks zur Farbformatierung in Power BI-Berichten
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/29/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c2800ab9d57732448db9e4fe647a0601a20a816c
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276603"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Tipps und Tricks zur Farbformatierung in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Power BI bietet viele unterschiedliche Methoden zum Anpassen der Dashboards und Berichte. In diesem Artikel erhalten Sie Tipps, wie Sie Ihre Power BI-Visualisierungen ansprechender, interessanter und personalisierter gestalten können.

Nachfolgend finden Sie einige Tipps. Haben Sie weitere tolle Tipps? Sehr gut! Wenn Sie sie uns zukommen lassen, nehmen wir sie möglicherweise in diese Liste auf.

* Anwenden eines Designs auf den gesamten Bericht
* Farbe eines einzelnen Datenpunkts ändern
* Bedingte Formatierung
* Farben eines Diagramms nach einem numerischen Wert vergeben
* Farbe der Datenpunkte nach einem numerischen Wert vergeben
* Farben in der Farbskala anpassen
* Abweichende Farbskalen verwenden
* Hinzufügen von Farben zu Tabellenzeilen
* Änderungen in Power BI rückgängig machen

Sie benötigen Berechtigungen zum Bearbeiten des Berichts, um Änderungen vorzunehmen. Öffnen Sie in Power BI Desktop die Ansicht **Bericht**. Im Power BI-Dienst müssen Sie dazu den Bericht öffnen und wie in der folgenden Abbildung dargestellt in der Menüleiste auf **Bearbeiten** klicken.

![Position des Menüs „Bearbeiten“](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-report.png)

Wenn die Bereiche **Filter** und **Visualisierungen** auf der rechten Seite des Berichtszeichenbereichs angezeigt werden, können Sie den Bericht anpassen. Wenn die Bereiche nicht angezeigt werden, klicken Sie auf den Pfeil in der oberen rechten Ecke, um sie zu öffnen.

![Berichtszeichenbereich in der Bearbeitungsansicht](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

## <a name="apply-a-theme"></a>Anwenden eines Designs
Mit Berichtsdesigns können Sie Entwurfsänderungen auf den gesamten Bericht anwenden, z. B. die Verwendung von Unternehmensfarben, das Ändern von Symbolsätzen oder das Anwenden der neuen Standardformatierung für Visuals. Wenn Sie ein Berichtsdesign anwenden, verwenden alle Visuals im Bericht die Farben und Formatierung des ausgewählten Designs. Weitere Informationen finden Sie unter [Verwenden von Berichtdesigns](../create-reports/desktop-report-themes.md).

![Symbol „Design wechseln“ in der Menüleiste](media/service-tips-and-tricks-for-color-formatting/power-bi-theme.png)

Hier wurde das Design **Innovate** auf den Bericht für Vertrieb und Marketing angewendet.

![Angewendetes Innovate-Design](media/service-tips-and-tricks-for-color-formatting/power-bi-theme-innovate.png)

## <a name="change-the-color-of-a-single-data-point"></a>Farbe eines einzelnen Datenpunkts ändern
Unter Umständen möchten Sie einen bestimmten Datenpunkt markieren. Das können z. B. die Verkaufszahlen für ein neu eingeführtes Produkt oder bessere Qualitätsergebnisse nach der Einführung eines neuen Programms sein. Mit Power BI können Sie einen bestimmten Datenpunkt hervorheben, indem Sie seine Farbe ändern.

In der folgenden Visualisierung werden verkaufte Einheiten nach Produktsegment angeordnet. 

![Ändern der Datenfarben in Grau](media/service-tips-and-tricks-for-color-formatting/power-bi-data.png)

Stellen Sie sich vor, dass Sie das Segment **Convenience** farblich hervorheben möchten, um zu zeigen, wie gut dieses brandneue Segment abschneidet. Gehen Sie wie folgt vor:

Erweitern Sie die Karte **Datenfarben**, und aktivieren Sie den Schieberegler für **Alles anzeigen**. Die Farben für jedes Datenelement in der Visualisierung werden angezeigt. Jetzt können Sie jeden beliebigen Datenpunkt bearbeiten.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show.png)

Legen Sie **Convenience** auf Orange fest. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Sobald die Auswahl getroffen wurde, wird der Datenpunkt **Convenience** in einem ansprechenden Orange hervorgehoben.

Auch wenn Sie Visualisierungstypen ändern und später zurückkehren, speichert Power BI Ihre Auswahl und markiert **Convenience** in Orange.

Sie können die Farbe eines Datenpunkts für einzelne, mehrere oder alle Datenelemente in der Visualisierung ändern. Vielleicht möchten Sie Ihr Visual an Ihre Unternehmensfarben Gelb, Grün und Blau anpassen. 

![Balkendiagramm mit Balken in Grün, Gelb und Blau](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Farben bieten Ihnen viele Gestaltungsmöglichkeiten. Der nächste Abschnitt dreht sich um die bedingte Formatierung.

## <a name="conditional-formatting-for-visualizations"></a>Bedingte Formatierung für Visualisierungen
Visualisierungen lassen sich mit dynamischen Farbeinstellungen nach dem numerischen Wert eines Felds ansprechend gestalten. Dadurch können Sie einen anderen als für die Größe eines Balkens verwendeten Wert anzeigen und die beiden Werte in einer einzelnen Grafik anzeigen. Sie können damit auch Datenpunkte markieren, die über (oder unter) einem bestimmten Wert liegen, z. B. Bereiche mit geringer Rentabilität.

Die folgenden Abschnitte zeigen die verschiedene Methoden, Farben auf Grundlage eines numerischen Werts anzupassen.

### <a name="base-the-color-of-data-points-on-a-value"></a>Farbe von Datenpunkten nach einem numerischen Wert vergeben
Um die Farbe anhand eines Werts zu ändern, wählen Sie eine Visualisierung aus, um diese zu aktivieren. Öffnen Sie den Bereich „Formatierung“, indem Sie auf das Farbrollersymbol klicken und die Karte **Datenfarben** öffnen. Zeigen Sie auf die Karte, klicken Sie auf die drei vertikalen Punkte, und wählen Sie **Bedingte Formatierung** aus.  

![Auswählen der Option „Bedingte Formatierung“ durch Klicken auf die drei vertikalen Punkte](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting.gif)

Verwenden Sie im Bereich **Standardfarbe** die Dropdownlisten, um die Felder zu identifizieren, die für die bedingte Formatierung verwendet werden. In diesem Beispiel wird das Feld **Sales fact** > **Total Units** ausgewählt und hellblau für **Niedrigster Wert** bzw. dunkelblau für **Höchster Wert** verwendet. 

![Einstellungen für die bedingte Formatierung von Datenfarben](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![Säulendiagramm, für das die Standardfarben verwendet werden](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

Sie können die Farbe des Visuals mithilfe eines Felds formatieren, das nicht Teil des Visuals ist. In der folgenden Abbildung wird **%Market Share SPLY YTD** (% Marktanteil im gleichen Vorjahreszeitraum seit Jahresbeginn) verwendet. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Sie sehen, dass zwar mehr Einheiten aus den Bereichen **Productivity** (Produktivität) und **Extreme** verkauft wurden (die Säulen sind höher), **Moderation** aber dennoch einen höheren Wert für **%Market Share SPLY YTD** (% Marktanteil im gleichen Vorjahreszeitraum seit Jahresbeginn) aufweist (die Säule zeigt eine stärkere Farbsättigung).

### <a name="customize-the-colors-used-in-the-color-scale"></a>Farben in der Farbskala individuell anpassen
Sie können auch ändern, wie die Werte diesen Farben zugeordnet werden. In der folgenden Abbildung werden für **Minimal** und **Maximal** die Farben Orange und Grün festgelegt.

Achten Sie im ersten Bild darauf, wie die Balken im Diagramm den Farbverlauf in der Farbverlaufsleiste widerspiegeln. Der höchste Wert ist Grün, ist der niedrigste ist Orange, und jeder Balken dazwischen wird mit einer Farbe zwischen Grün und Orange gekennzeichnet.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Lassen Sie uns überprüfen, was passiert, wenn wir in den Feldern **Minimum** und **Maximum** numerische Werte angeben. Wählen Sie sowohl für **Minimum** als auch **Maximum** den Wert **Benutzerdefiniert** aus den Dropdownfeldern aus, und legen Sie **Minimum** auf 3.500 und **Maximum** auf 6.000 fest.

![Bedingtes Formatieren nach Zahlen](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting-numbers.png)

Werden diese Werte festgelegt, wird der Farbverlauf nicht mehr auf die Werte im Diagramm angewendet, die unter dem **Minimum** oder über dem **Maximum** liegen. Alle Balken mit Werten oberhalb des **Maximums** werden grün, alle Balken mit Werten unterhalb des **Minimums** rot markiert.

![Ergebnis der bedingten Formatierung nach Zahlen](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

### <a name="use-diverging-color-scales"></a>Abweichende Farbskalen verwenden
Manchmal verfügen Ihre Daten über natürlich abweichende Skalen. Beispielsweise liegt bei einem Temperaturbereich die natürliche Mitte am Gefrierpunkt, und eine Rentabilitätsbewertung hat einen natürlichen Mittelpunkt (Null).

Aktivieren Sie das Kontrollkästchen **Abweichend**, um abweichende Farbskalen zu verwenden. Wenn **Abweichend** aktiviert ist, wird wie im Folgenden dargestellt eine zusätzliche Farbauswahl namens **Mitte** angezeigt.

![Dialogfeld für Standardfarbe mit ausgewählter Farbskala](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging-colors.png)

Wenn der Schieberegler **Abweichend** aktiviert ist, können Sie die Farben für **Minimal**, **Maximal** und **Mitte** separat auswählen. In der folgenden Abbildung wird die **Mitte** für **% Market Share SPLY YTD** (% Marktanteil im gleichen Vorjahreszeitraum seit Jahresbeginn) auf „0,2“ festgelegt, sodass Balken mit Werten über 0,2 in einem Grünton und Balken mit Werten unter 0,2 in einem Rotton angezeigt werden.

![Säulendiagramm mit roten und grünen Balken](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="add-color-to-table-rows"></a>Hinzufügen von Farben zu Tabellenzeilen
Tabellen und Matrizen bieten zahlreiche Farbformatierungsoptionen. 

![Standardtabelle](media/service-tips-and-tricks-for-color-formatting/power-bi-table.png)

Das Farbschema von Tabellen und Matrizen lässt sich am schnellsten ändern, indem Sie auf der Registerkarte „Formatierung“ auf **Stil** klicken.  In der folgenden Abbildung wurde die Option **Kopfzeile in Fettformatierung, auffällige Zeilen** ausgewählt.

![Standardtabelle](media/service-tips-and-tricks-for-color-formatting/power-bi-table-style.png)

Experimentieren Sie mit anderen Farbformatierungsoptionen. In der folgenden Abbildung wurde sowohl die Hintergrundfarbe der **Spaltenüberschriften** als auch die **Hintergrundfarbe** und die **Alternative Hintergrundfarbe** der **Werte** (Zeilen) geändert.

![Standardtabelle](media/service-tips-and-tricks-for-color-formatting/power-bi-table-rows.png)

## <a name="how-to-undo-in-power-bi"></a>Änderungen in Power BI rückgängig machen
Wie viele andere Microsoft-Dienste und Software bietet Power BI eine einfache Möglichkeit, den letzten Befehl rückgängig zu machen. Nehmen wir an, Sie ändern die Farbe eines Datenpunkts oder eine Reihe von Datenpunkten, und die Farbe gefällt Ihnen nicht, wenn sie in der Visualisierung angezeigt wird. Sie wissen nicht genau, wie die Farbe zuvor festgelegt war, aber Sie möchten wieder diese Farbe angezeigt bekommen.

Sie können Ihre letzte Aktion bzw. die letzten paar Aktionen ganz einfach **rückgängig machen**: STRG + Z.

Klicken Sie auf **Auf Standardwert zurücksetzen**, um alle Änderungen zu verwerfen, die Sie auf der Karte „Formatierung“ vorgenommen haben.

![Formatierungskarte mit der Option „Auf Standardwert zurücksetzen“ am unteren Rand](media/service-tips-and-tricks-for-color-formatting/power-bi-revert.png)

## <a name="feedback"></a>Feedback
Haben Sie einen Tipp, von dem Sie berichten möchten? Bitte lassen Sie ihn uns zukommen –möglicherweise nehmen wir ihn in diese Liste auf.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Farbeinstellungen und Achseneigenschaften](service-getting-started-with-color-formatting-and-axis-properties.md)

[Freigeben von Berichten](../collaborate-share/service-share-reports.md).

