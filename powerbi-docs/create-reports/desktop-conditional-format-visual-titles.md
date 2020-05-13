---
title: Ausdrucksbasierte Titel in Power BI Desktop
description: Erstellen Sie dynamische Titel in Power BI Desktop, die sich basierend auf programmgesteuerten Ausdrücken ändern, wozu bedingte programmgesteuerte Formatierung verwendet wird.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f3c1f047e3be7520005458294381877d1198ee21
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83298387"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Ausdrucksbasierte Titel in Power BI Desktop

Sie können dynamische angepasste Titel für Ihre visuellen Power BI-Elemente erstellen. Durch Erstellen von DAX-Ausdrücken (Data Analysis Expressions), die auf Feldern, Variablen oder anderen programmgesteuerten Elementen basieren, können die Titel ihrer visuellen Elemente nach Bedarf automatisch angepasst werden. Diese Änderungen basieren auf Filtern, ausgewählten Elementen oder anderen Benutzerinteraktionen und Konfigurationen.

![Screenshot der Power BI Desktop-Option für bedingte Formatierung](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Das Erstellen eines dynamischen Titels (manchmal als *ausdrucksbasierter Titel* bezeichnet) ist einfach. 

## <a name="create-a-field-for-your-title"></a>Erstellen eines Felds für Ihren Titel

Der erste Schritt beim Erstellen eines ausdrucksbasierten Titels besteht darin, ein Feld in Ihrem Modell zu erstellen, das für den Titel verwendet werden soll. 

Es gibt viele verschiedene Arten von kreativen Möglichkeiten, wie Ihr visueller Titel das zum Ausdruck bringt, was Sie mitteilen oder ausdrücken möchten. Sehen Sie sich einige Beispiele an.

Sie können einen Ausdruck erstellen, der sich entsprechend dem Filterkontext ändert, den das visuelle Element für den Markennamen des Produkts empfängt. Die folgende Abbildung zeigt die DAX-Formel für ein solches Feld.

![Screenshot der DAX-Formel](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Ein weiteres Beispiel ist das Verwenden eines dynamischen Titels, der sich entsprechend der Sprache oder Kultur des Benutzers ändert. Sie können sprachspezifische Titel in einem DAX-Measure erstellen, indem Sie die `USERCULTURE()`-Funktion verwenden. Diese Funktion gibt den Kulturcode für den Benutzer anhand dessen Betriebssystem oder Browsereinstellungen zurück. Sie können die folgende DAX-SWITCH-Anweisung verwenden, um den richtigen übersetzten Wert auszuwählen. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Alternativ können Sie die Zeichenfolge aus einer Nachschlagetabelle abrufen, die alle Übersetzungen enthält. Sie platzieren diese Tabelle in Ihrem Modell. 

Dies sind nur einige Beispiele dazu, wie Sie dynamische ausdrucksbasierte Titel für Ihre visuellen Elemente in Power BI Desktop erstellen können. Die Ausdrucksmöglichkeiten für Ihre Titel sind nur durch Ihre Phantasie und Ihr Modell eingeschränkt.


## <a name="select-your-field-for-your-title"></a>Auswählen eines Felds für Ihren Titel

Nachdem Sie den DAX-Ausdruck für das Feld erstellt haben, das Sie in Ihrem Modell erstellt haben, müssen Sie es auf den Titel Ihres visuellen Elements anwenden.

Um das Feld auszuwählen und anzuwenden, wechseln Sie zum Bereich **Visualisierungen**. Wählen Sie im Abschnitt **Format** die Option **Titel** aus, um die Titeloptionen für das visuelle Element anzuzeigen. 

Wenn Sie mit der rechten Maustaste auf **Titeltext** klicken, wird ein Kontextmenü angezeigt, in dem Sie **<em>fx</em>Bedingte Formatierung** auswählen können. Wenn Sie dieses Menüelement auswählen, wird das Dialogfeld **Titeltext** angezeigt. 

![Screenshot des Dialogfelds „Titeltext“](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

In diesem Fenster können Sie das Feld auswählen, das Sie für Ihren Titel verwenden möchten.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Es gibt einige Einschränkungen bei der aktuellen Implementierung von ausdrucksbasierten Titeln für visuelle Elemente:

* Ausdrucksbasierte Formatierung wird derzeit nicht für visuelle Python-, R- oder „Wichtigste Einflussfaktoren“-Elemente unterstützt.
* Das Feld, das Sie für den Titel erstellen, muss einen Zeichenfolgendatentyp (String-Datentyp) haben. Measures, die Zahlen oder Datum/Uhrzeit-Werte (oder einen beliebigen anderen Datentyp) zurückgeben, werden zurzeit nicht unterstützt.
* Ausdrucksbasierte Titel werden nicht übertragen, wenn Sie ein visuelles Element an ein Dashboard anheften.

## <a name="next-steps"></a>Weitere Schritte

In diesem Artikel ist beschrieben, wie Sie DAX-Ausdrücke erstellen, mit denen die Titel ihrer visuellen Elemente in dynamische Felder umgewandelt werden, die sich ändern können, wenn Benutzer mit ihren Berichten interagieren. Möglicherweise sind auch die folgenden Artikel für Sie nützlich.

* [Bedingte Formatierung in Tabellen](desktop-conditional-table-formatting.md)
* [Use cross-report drillthrough in Power BI Desktop](desktop-cross-report-drill-through.md) (Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop)
* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)
