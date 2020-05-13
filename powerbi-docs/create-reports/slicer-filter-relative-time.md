---
title: Verwenden eines Slicers oder Filters für relative Zeitbereiche in Power BI
description: Hier erfahren Sie, wie Sie mit einem Slicer oder Filter relative Zeitbereiche in Power BI einschränken.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 31563e5bb5b91468b8913c3204e9d27607716c77
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279202"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Verwenden eines Slicers und Filters für relative Zeitbereiche in Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Bei sich schnell ändernden Szenarios kann es nützlich sein, hinsichtlich eines kleineren Zeitfensters filtern zu können. Durch Verwenden des Slicers oder Filters für relative Zeitbereiche können Sie zeitbasierte Filter auf beliebige Datums- oder Zeitspalten in Ihrem Datenmodell anwenden. So können Sie beispielsweise den Slicer für relative Zeitbereiche so einstellen, dass nur die Videoaufrufe der letzten Minute oder Stunde angezeigt werden. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Beispiel für relative Zeit":::

Sie müssen das Feature nicht zusammen mit der Funktion für [automatische Seitenaktualisierung](../create-reports/desktop-automatic-page-refresh.md) verwenden. Viele relative Zeitszenarien lassen sich jedoch gut mit der Funktion für automatische Seitenaktualisierung kombinieren.  

> [!NOTE]
> Wenn Sie einen Filter oder Slicer für relative Zeitbereiche auf Seiten- oder Berichtsebene anwenden, werden alle visuellen Elemente (Visuals) auf dieser Seite oder in diesem Bericht für den exakt identischen Zeitbereich gefiltert, wozu eine gemeinsame *Anker*-Zeit verwendet wird. Da visuelle Elemente möglicherweise geringfügig abweichende Ausführungszeiten haben, wird durch diese gemeinsame Ankerzeit sichergestellt, dass die visuellen Elemente auf der gesamten Seite oder im gesamten Bericht synchronisiert werden. Weitere Informationen zu [Ankerzeit](#understanding-anchor-time) finden Sie in diesem Artikel.

## <a name="turn-on-relative-time-preview"></a>Aktivieren der Vorschau für relative Zeit

Der Filter für relative Zeitbereiche ist als Vorschauversion verfügbar, weshalb Sie den Featureschalter aktivieren müssen. Öffnen Sie **Datei** > **Optionen und Einstellungen** > **Optionen**. Aktivieren Sie unter **Globale Einstellungen** > **Vorschaufunktionen** die Option **Relativer Zeitfilter**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="Vorschauoption für relative Zeit festlegen":::

## <a name="create-a-relative-time-slicer-or-filter"></a>Erstellen eines Slicers oder Filters für relative Zeitbereiche

Nachdem Sie das Feature aktiviert haben, können Sie das Datums- oder Uhrzeitfeld in den Feldbereich eines Slicers (Datenschnitt) oder in die Ablagezone im Bereich „Filter“ ziehen und dort ablegen. 

### <a name="create-a-slicer"></a>Erstellen von Slicern

1. Ziehen Sie ein Datums- oder Uhrzeitfeld in den Zeichenbereich.

2. Wählen Sie den Visualisierungstyp **Slicer** aus.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Einen Uhrzeitslicer erstellen":::

### <a name="create-a-filter"></a>Erstellen eines Filters
 
- Ziehen Sie ein Datums- oder Uhrzeitfeld für **dieses Visual**, **diese Seite**oder **alle Seiten** in den Bereich „Filter“.

### <a name="set-relative-time"></a>Festlegen der relativen Zeit 

Ändern Sie den Filtertyp nun in **Relative Zeit**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="In relative Zeit ändern":::
 
So sieht das Ergebnis in einem Slicer aus:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Relative Zeit in einem Slicer":::

So sieht das Ergebnis auf einer Filterkarte aus: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Relative Zeit in einem Filter":::
 
Mit diesem neuen Filtertyp haben Sie die Möglichkeit, auf Basis von **Letzter**, **Nächster** oder **Dieser Zeitraum** zu filtern: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="„Letzter“, „Nächster“ oder „Dieser Zeitraum“ auswählen":::
 
Sie geben das Zeitfenster mit einer ganzen Zahl und einer Zeiteinheit an: **Minuten** oder **Stunden**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Minuten oder Stunden auswählen":::

Wenn Sie Speicherplatz auf der Canvas (Zeichenbereich) sparen müssen, können Sie den relativen Zeitfilter auch als Filterkarte im Bereich „Filter“ erstellen.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Stattdessen relative Zeit in einem Filter festlegen":::
 
## <a name="understanding-anchor-time"></a>Grundlegendes zu Ankerzeit

Wenn ein Filter auf Seiten- oder Berichtsebene angewendet wird, werden alle visuellen Elemente auf dieser Seite oder in diesem Bericht für den identischen Zeitbereich synchronisiert. Diese Abfragen werden alle relativ bezogen auf eine Zeit ausgeführt, die als *Ankerzeit* bezeichnet wird. Die Ankerzeit wird unter folgenden Bedingungen automatisch aktualisiert:

- Erstmaliges Laden einer Seite
- Manuelle Aktualisierung
- Automatische Seitenaktualisierung oder Seitenaktualisierung nach Änderungserkennung
- Eine Änderung des Modells

### <a name="anchor-time-exceptions"></a>Ankerzeitausnahmen

- Ein relatives Filtern nach Zeit mit diesem Q&A-Visual erfolgt solange nicht relativ zu dieser Ankerzeit, bis Sie das Q&A-Visual in ein Standardvisual konvertiert haben. Die anderen visuellen KI-Elemente, etwa Haupteinflussfaktoren und der Analysebaum, werden jedoch mit der Ankerzeit synchronisiert. 
- Außerdem sind Filter oder Slicer für relative Datumsbereiche nicht relativ zur Ankerzeit, es sei denn, es sind relative Zeitfilter vorhanden. Befinden sich ein relativer Datums- und ein relativer Zeitfilter auf derselben Seite, wird für den relativen Datumsfilter die Ankerzeit berücksichtigt.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Die folgenden Einschränkungen und Überlegungen betreffen derzeit den Slicer und den Filter für relative Zeitbereiche.

- **Überlegungen zu Zeitzonen**: Datenmodelle in Power BI enthalten keine Zeitzoneninformationen. In Modellen können Zeitangaben gespeichert werden, es gibt jedoch keinerlei Hinweise auf die entsprechende Zeitzone. Die Datenschnitte und Filter basieren immer auf der Zeit in UTC. Wenn Sie einen Filter in einem Bericht einrichten und an einen Kollegen in einer anderen Zeitzone senden, sehen sie beide dieselben Daten. Wenn Sie oder Ihr Kollege sich nicht in der UTC-Zeitzone befinden, müssen sie beide den entsprechenden Zeitversatz berücksichtigen. Verwenden Sie den Abfrage-Editor, um Daten, die in einer lokalen Zeitzone erfasst wurden, in UTC zu konvertieren.
- Dieser neue Filtertyp wird in Power BI Desktop, im Power BI-Dienst, in Power BI Embedded und in den mobilen Power BI-Apps unterstützt. Es gibt jedoch einige bekannte Unterstützungseinschränkungen:

    - Der Filtertyp wird über die Einbettungs-API nicht unterstützt.
    - Er wird für „Im Web veröffentlichen“ nicht unterstützt.

- **Zwischenspeicherung von Abfragen**: Es wird der Clientcache verwendet. Angenommen, Sie geben „letzte 1 Minute“, dann „letzte 5 Minuten“ und dann wieder „letzte 1 Minute“ an. An diesem Punkt sehen Sie dieselben Ergebnisse wie bei der ersten Ausführung, es sei denn, Sie aktualisieren die Seite, oder die Seite wird automatisch aktualisiert.

## <a name="next-steps"></a>Nächste Schritte

- [Verwenden eines Slicers und Filters für relative Datumsbereiche in Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Datenschnitte in Power BI](../visuals/power-bi-visualization-slicers.md)
