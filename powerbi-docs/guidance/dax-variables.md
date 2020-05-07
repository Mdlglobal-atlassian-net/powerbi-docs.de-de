---
title: 'DAX: Verwenden von Variablen zur Verbesserung von Formeln'
description: Leitfaden zum Verwenden von Variablen in DAX-Ausdrücken
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: f352cbbd7c42aa54ae876e73c0ed821eccda59c8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700706"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX: Verwenden von Variablen zur Verbesserung von Formeln

Das Schreiben und Debuggen von DAX-Berechnungen kann für Datenmodellierer eine große Herausforderung darstellen. Komplexe Berechnungsanforderungen beinhalten häufig das Schreiben zusammengesetzter oder komplexer Ausdrücke. Zusammengesetzte Ausdrücke können die Verwendung vieler geschachtelter Funktionen und möglicherweise die Wiederverwendung von Ausdruckslogik einschließen.

Die Verwendung von Variablen in DAX-Formeln erleichtert das Anfertigen komplexer und effizienter Berechnungen. Variablen unterstützen Sie bei Folgendem:

- [Verbessern der Leistung](#improve-performance)
- [Verbessern der Lesbarkeit](#improve-readability)
- [Vereinfachen des Debuggens](#simplify-debugging)
- [Reduzieren der Komplexität](#reduce-complexity)

In diesem Artikel werden anhand der Verwendung eines Beispielmeasures für das YoY-Umsatzwachstum (Year-over-Year) die drei wichtigsten Vorteile veranschaulicht. (Die Formel für das Umsatzwachstum im Vergleich zum Vorjahr lautet folgendermaßen: „period sales _fewer sales“ für den gleichen Zeitraum im vergangenen Jahr _dividiert durch_ den Umsatz für den gleichen Zeitraum im vergangenen Jahr)

Beginnen wir mit der folgenden Measuredefinition.

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

Das Measure erzeugt das richtige Ergebnis, aber sehen wir uns jetzt an, wie es weiter verbessert werden kann.

## <a name="improve-performance"></a>Verbessern der Leistung

Beachten Sie, dass in der Formel der Ausdruck für die Berechnung für den gleichen Zeitraum im vergangenen Jahr wiederholt wird. Diese Formel ist ineffizient, da Power BI den gleichen Ausdruck zweimal auswerten muss. Die Measuredefinition kann mithilfe einer Variable effizienter gemacht werden.

Die folgende Measuredefinition weisen eine Verbesserung auf. Es wird ein Ausdruck verwendet, um einer Variable namens **SalesPriorYear** das Ergebnis für „same period last year“ (Vorjahreszeitraum) zuzuweisen. Die Variable wird dann zweimal im Ausdruck „RETURN“ (ZURÜCKGEBEN) verwendet.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

Das Measure erzeugt weiterhin das korrekte Ergebnis in etwa der Hälfte der Abfragezeit.

## <a name="improve-readability"></a>Verbessern der Lesbarkeit

Beachten Sie, dass der Ausdruck „RETURN“ (ZURÜCKGEBEN) durch die Auswahl des Variablennamens in der vorherigen Measuredefinition leichter zu verstehen ist. Der Ausdruck ist kurz und selbsterklärend.

## <a name="simplify-debugging"></a>Vereinfachen des Debuggens

Variablen können auch beim Debuggen einer Formel helfen. Schreiben Sie zum Testen eines einer Variable zugeordneten Ausdrucks vorübergehend den Ausdruck „RETURN“ (ZURÜCKGEBEN) um, um die Variable auszugeben.

Die folgende Measuredefinition gibt nur die Variable **SalesPriorYear** zurück. Beachten Sie, wie der beabsichtigte Ausdruck „RETURN“ (ZURÜCKGEBEN) auskommentiert wird. Diese Technik ermöglicht es Ihnen, den Ausdruck nach Abschluss des Debuggens problemlos wiederherzustellen.

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>Reduzieren der Komplexität

In früheren Versionen von DAX wurden Variablen noch nicht unterstützt. Komplexe Ausdrücke, die neue Filter eingeführt haben, mussten die DAX-Funktionen [EARLIER](/dax/earlier-function-dax) oder [EARLIEST](/dax/earliest-function-dax) verwenden, um auf äußere Filterkontexte zu verweisen. Leider waren diese Funktionen laut Datenmodellierern schwer zu verstehen und zu verwenden.

Variablen werden immer außerhalb der Filter ausgewertet, die der Ausdruck „RETURN“ (ZURÜCKGEBEN) anwendet. Wenn Sie eine Variable innerhalb eines geänderten Filterkontexts verwenden, wird daher das gleiche Ergebnis wie bei der „EARLIEST“-Funktion erzielt. Daher kann die Verwendung der Funktionen „EARLIER“ oder „EARLIEST“ vermieden werden. Dies bedeutet, dass Sie jetzt Formeln schreiben können, die weniger komplex sind und leichter zu verstehen sind.

Beachten Sie die folgende Definition einer berechneten Spalte, die der Tabelle **Subcategory** hinzugefügt wurde. Sie wertet, basierend auf den Werten in der Spalte **Subcategory Sales** (Umsatz Unterkategorie), einen Rang für jede Produktunterkategorie aus.

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

Die Funktion „EARLIER“ wird verwendet, um auf den Wert in der Spalte **Subcategory Sales** (Umsatz Unterkategorie) im _aktuellen Zeilenkontext_ zu verweisen.

Die Definition von berechneten Spalten kann mithilfe einer Variablen anstelle der „EARLIER“-Funktion verbessert werden. Die Variable **CurrentSubcategorySales** speichert den Wert der Spalte **Subcategory Sales** (Umsatz Unterkategorie) _im aktuellen Zeilenkontext_, und der Ausdruck „RETURN“ (ZURÜCKGEBEN) verwendet ihn in einem geänderten Filterkontext.

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- Artikel zur DAX-Funktion [VAR](/dax/var-dax)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
