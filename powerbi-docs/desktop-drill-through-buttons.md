---
title: Erstellen einer Drillthroughschaltfläche in Power BI
description: Sie können in Power BI-Berichten Drillthroughschaltflächen hinzufügen, sodass das Verhalten Ihrer Berichte Apps ähnelt und sie von Benutzern noch einfacher verwendet werden können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d3cb3c8093446d4417a59c5f64ab6b85a765e3c8
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79206445"
---
# <a name="create-a-drill-through-button-in-power-bi-preview"></a>Erstellen einer Drillthroughschaltfläche in Power BI (Vorschauversion)

Wenn Sie in Power BI eine Schaltfläche erstellen möchten, können Sie auf die Aktion **Drillthrough (Vorschau)** klicken. Dieser Aktionstyp erstellt eine Schaltfläche, die einen Drillthrough zu einer bestimmten Seite ausführt, um Details zu erhalten, die in einem bestimmten Kontext gefiltert werden.

Eine Drillthroughschaltfläche kann nützlich sein, wenn Sie die Auffindbarkeit wichtiger Drillthroughszenarios in Ihren Berichten verbessern möchten.

In diesem Beispiel ist die Schaltfläche **Details anzeigen** aktiviert, nachdem der Benutzer in die Leiste für Word im Diagramm geklickt hat.

![Schaltfläche „Details anzeigen“](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Wenn Sie auf **Details anzeigen** klicken, wird ein Drillthrough zur Seite für die Warenkorbanalyse durchgeführt. Wie Sie im Visual auf der linken Seite sehen, wird die Drillthroughseite jetzt nach Word gefiltert.

![Gefiltertes Visual](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Einrichten einer Drillthroughschaltfläche

Sie müssen zum Einrichten einer Drillthroughschaltfläche zunächst [eine gültige Drillthroughseite im Bericht einrichten](desktop-drillthrough.md). Anschließend müssen Sie eine Schaltfläche mit **Drillthrough** als Aktionstyp erstellen und die Drillthroughseite als **Destination** (Ziel) auswählen.

Da die Drillthroughschaltfläche zwei Zustände aufweist (Drillthrough aktiviert bzw. deaktiviert), werden Sie feststellen, dass es zwei QuickInfo-Optionen gibt.

![Einrichten der Drillthroughschaltfläche](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Wenn Sie die QuickInfo-Felder leer lassen, generiert Power BI automatisch QuickInfos. Diese QuickInfos basieren auf den Feldern „Destination“ (Ziel) und „Drillthrough“.

Im Folgenden finden Sie ein Beispiel für die automatisch generierte QuickInfo, wenn die Schaltfläche deaktiviert ist:

„To drill through to Market Basket Analysis (the destination page), select a single data point from Product (the drill-through field).“ (Wählen Sie einen einzelnen Datenpunkt des Produkts (Drillthroughfeld) aus, um einen Drillthrough zur Seite für die Warenkorbanalyse (Zielseite) durchzuführen.)

![Deaktivierte, automatisch generierte QuickInfo](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Und hier finden Sie ein Beispiel für die automatisch generierte QuickInfo, wenn die Schaltfläche aktiviert ist:

„Click to drill through to Market Basket Analysis (the destination page).“ (Klicken Sie hier, um einen Drillthrough zur Seite für die Warenkorbanalyse durchzuführen (Zielseite).)

![Aktivierte, automatisch generierte QuickInfo](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Wenn Sie jedoch benutzerdefinierte QuickInfos bereitstellen möchten, können Sie immer eine statische Zeichenfolge eingeben. Die bedingte Formatierung für QuickInfos wird noch nicht unterstützt.

Sie können die bedingte Formatierung verwenden, um den Schaltflächentext basierend auf dem ausgewählten Wert eines Felds zu ändern. Dazu müssen Sie ein Measure erstellen, das die gewünschte Zeichenfolge basierend auf der DAX-Funktion „SELECTEDVALUE“ ausgibt.

Hier ist ein Beispielmeasure, das „See product details“ (Produktdetails anzeigen) ausgibt, wenn ein einzelner Produktwert NICHT ausgewählt ist. Andernfalls wird „See details for [the selected Product]“ (Details für [das ausgewählte Produkt] anzeigen) ausgegeben:

```
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0), "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Nachdem Sie dieses Measure erstellt haben, klicken Sie auf die Option **Bedingte Formatierung** für den Schaltflächentext:

![Auswählen der bedingten Formatierung](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Anschließend wählen Sie das Measure aus, das Sie für den Schaltflächentext erstellt haben:

![Wert „Basierend auf Feld“](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Wenn ein einzelnes Produkt ausgewählt wird, lautet der Schaltflächentext folgendermaßen:

„See details for Word“ (Details für Word anzeigen)

![Wenn ein einzelner Wert ausgewählt wird](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Wenn entweder keine Produkte oder mehr als ein Produkt ausgewählt sind, wird die Schaltfläche deaktiviert und der Schaltflächentext lautet folgendermaßen:

„See product details“ (Produktdetails anzeigen)

![Wenn mehrere Werte ausgewählt sind](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="pass-filter-context"></a>Übergeben von Filterkontext

Die Schaltfläche funktioniert wie der normale Drillthrough, sodass Sie auch Filter für zusätzliche Felder übergeben können, indem Sie für die Visuals eine Kreuzfilterung durchführen, die das Drillthroughfeld enthalten. Bei Verwendung von **STRG** + **Klicken** und der Kreuzfilterung können Sie beispielsweise mehrere Filter im Speicher an die Drillthroughseite übergeben, da Ihre Auswahl eine Kreuzfilterung für das Visual ausführt, das das Produkt (Drillthroughfeld) enthält:

![Übergeben des Filterkontexts](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Wenn Sie auf die Drillthroughschaltfläche klicken, werden die Filter sowohl für den Store als auch das Produkt angezeigt, die an die Zielseite weitergeleitet werden:

![Filter für diese Seite](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Mehrdeutiger Filterkontext

Da die Drillthroughschaltfläche nicht an ein einzelnes Visual gebunden ist, wird die Schaltfläche deaktiviert, wenn die Auswahl mehrdeutig ist.

In diesem Beispiel ist die Schaltfläche deaktiviert, da zwei Visuals jeweils eine einzelne Auswahl für das Produkt enthalten. Es ist nicht eindeutig, mit welchem Datenpunkt des jeweiligen Elements die Drillthroughaktion verknüpft werden soll:

![Mehrdeutiger Filterkontext](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="limitations"></a>Einschränkungen

- Mit dieser Schaltfläche können nicht mehrere Ziele mithilfe einer einzelnen Schaltfläche verwendet werden.
- Diese Schaltfläche unterstützt nur Drillthroughvorgänge innerhalb desselben Berichts. Das bedeutet, dass keine berichtsübergreifenden Drillthroughs unterstützt werden.
- Die deaktivierte Statusformatierung für die Schaltfläche ist an die Farbklassen im Berichtsdesign gebunden. Hier finden Sie weitere Informationen zu [Farbklassen](desktop-report-themes.md#setting-structural-colors).
- Die Drillthroughaktion funktioniert für alle integrierten und *einige* von AppSource importierten Visuals. Es kann jedoch nicht garantiert werden, dass die Arbeit mit *allen* aus AppSource importierten Visuals möglich ist.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Features, die Schaltflächen ähneln oder mit diesen interagieren, finden Sie in den folgenden Artikeln:

* [Erstellen von Schaltflächen](desktop-buttons.md)
* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)
* [Verwenden von Lesezeichen zum Teilen von Erkenntnissen und zum Erstellen von Präsentationen in Power BI](desktop-bookmarks.md)

