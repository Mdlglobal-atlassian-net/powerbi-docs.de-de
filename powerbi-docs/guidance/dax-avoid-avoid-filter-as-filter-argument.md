---
title: 'DAX: Vermeiden der Verwendung von FILTER als Filterargument'
description: Anleitungen zur Verwendung der Funktion FILTER als Filterargument.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 6abcb77e3eb534e8b5d20c1d5567c117cbb97ffe
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161430"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX: Vermeiden der Verwendung von FILTER als Filterargument

Als Datenmodellierer ist es üblich, DAX-Ausdrücke zu schreiben, die in einem modifizierten Filterkontext ausgewertet werden müssen. Sie können z. B. eine Measuredefinition schreiben, um den Umsatz für „gewinnträchtige Produkte“ zu berechnen. Diese Berechnung wird später in diesem Artikel beschrieben.

> [!NOTE]
> Dieser Artikel ist besonders relevant für Modellberechnungen, die Filter zum Importieren von Tabellen anwenden.

Die DAX-Funktionen [CALCULATE](/dax/calculate-function-dax) und [CALCULATETABLE](/dax/calculatetable-function-dax) sind wichtige und nützliche Funktionen. Mit ihnen können Sie Berechnungen schreiben, die Filter entfernen oder hinzufügen oder Beziehungspfade ändern. Dies erfolgt durch die Übergabe von Filterargumenten, die entweder boolesche Ausdrücke, Tabellenausdrücke oder spezielle Filterfunktionen sind. In diesem Artikel werden nur boolesche und Tabellenausdrücke diskutiert.

Betrachten Sie die folgende Measuredefinition, die den Umsatz des roten Produkts mithilfe eines Tabellenausdrucks berechnet. Sie ersetzt alle Filter, die auf die Tabelle **Product** (Produkt) angewendet werden können.

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

Die Funktion CALCULATE akzeptiert einen Tabellenausdruck, der von der DAX-Funktion [FILTER](/dax/filter-function-dax) zurückgegeben wird, die ihren Filterausdruck für jede Zeile der Tabelle **Produkt** auswertet. Sie erzielt das richtige Ergebnis – das Verkaufsergebnis für rote Produkte. Dies kann jedoch mit einem booleschen Ausdruck wesentlich effizienter erreicht werden.

Im folgenden finden Sie eine verbesserte Measuredefinition, die einen booleschen Ausdruck anstelle des Tabellenausdrucks verwendet. Die DAX-Funktion [KEEPFILTERS](/dax/keepfilters-function-dax) stellt sicher, dass vorhandene, auf die Spalte **Color** (Farbe) angewendete Filter beibehalten und nicht überschrieben werden.

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

Es wird empfohlen, nach Möglichkeit Filterargumente als boolesche Ausdrücke zu übergeben. Das liegt daran, dass die Importmodelltabellen speicherinterne Columnstores sind. Sie sind explizit optimiert, um Spalten auf diese Weise effizient zu filtern.

Es gibt jedoch Einschränkungen, die für boolesche Ausdrücke gelten, wenn sie als Filterargumente verwendet werden. Einschränkungen:

- Sie können Spalten nicht mit anderen Spalten vergleichen.
- Sie können nicht auf ein Measure verweisen.
- Sie können keine geschachtelten CALCULATE-Funktionen verwenden.
- Sie können keine Funktionen verwenden, die eine Tabelle überprüfen oder zurückgeben.

Das bedeutet, dass Sie für komplexere Filteranforderungen Tabellenausdrücke verwenden müssen.

Betrachten Sie nun eine andere Measuredefinition.

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

Als _gewinnträchtiges Produkt_ wird ein Produkt definiert, dessen Listenpreis das Doppelte der Standardkosten übersteigt. In diesem Beispiel muss die Funktion FILTER verwendet werden. Das liegt daran, dass der Filterausdruck zu komplex für einen booleschen Ausdruck ist.

Hier folgt noch ein Beispiel. Die Anforderung ist diesmal, den Umsatz zu berechnen, aber nur für die Monate, die einen Gewinn erzielt haben.

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

In diesem Beispiel muss auch die Funktion FILTER verwendet werden. Der Grund dafür ist, dass das Measure **Profit** (Gewinn) bewertet werden muss, um die Monate zu beseitigen, in denen kein Gewinn erzielt wurde. Es ist nicht möglich, ein Measure in einem booleschen Ausdruck zu verwenden, wenn es als Filterargument verwendet wird.

## <a name="recommendations"></a>Empfehlungen

Um die optimale Leistung zu erreichen, empfehlen wir Ihnen, nach Möglichkeit boolesche Ausdrücke als Filterargumente zu verwenden.

Deshalb sollte die Funktion FILTER nur bei Bedarf verwendet werden. Sie können damit auch komplexe Spaltenvergleiche filtern. Diese Spaltenvergleiche können Folgendes umfassen:

- Measures
- Andere Spalten
- Verwendung der DAX-Funktion [OR](/dax/or-function-dax) oder des logischen Operators OR (||)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- [Filterfunktionen (DAX)](/dax/filter-function-dax)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
