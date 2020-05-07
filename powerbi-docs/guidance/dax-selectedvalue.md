---
title: 'DAX: Verwenden von SELECTEDVALUE anstelle von VAUES'
description: Leitfaden für die Verwendung der SELECTEDVALUE-Fehlerfunktionen
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700476"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: Verwenden von SELECTEDVALUE anstelle von VAUES

Als Datenmodellierer müssen Sie ggf. in manchen Fällen einen DAX-Ausdruck schreiben, der testet, ob eine Spalte nach einem bestimmten Wert gefiltert wird.

In früheren DAX-Versionen wurde diese Anforderung durch die Verwendung eines Musters mit drei DAX-Funktionen sicher erfüllt. Die Funktionen sind [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) und [VALUES](/dax/values-function-dax). Die folgende Measuredefinition stellt ein Beispiel dar. Sie berechnet den Umsatzsteuerbetrag, jedoch nur für Verkäufe an australische Kunden.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

In diesem Beispiel gibt die HASONEVALUE-Funktion nur dann TRUE zurück, wenn ein einzelner Wert die Spalte **Country-Region** (Land/Region) filtert. Wenn der Wert TRUE ist, wird die VALUES-Funktion mit dem literalen Text „Australia“ verglichen. Wenn die VALUES-Funktion TRUE zurückgibt, wird das Measure **Sales** mit 0,10 multipliziert (entspricht 10 %). Wenn die HASONEVALUE-Funktion FALSE zurückgibt, weil mehr als ein Wert die Spalte filtert, gibt die erste IF-Funktion BLANK zurück.

Die Verwendung von HASONEVALUE ist eine defensive Methode. Sie ist erforderlich, da möglicherweise mehrere Werte die Spalte **Country-Region** (Land/Region) filtern. In diesem Fall gibt die VALUES-Funktion eine Tabelle mit mehreren Zeilen zurück. Der Vergleich einer Tabelle mit mehreren Zeilen mit einem skalaren Wert führt zu einem Fehler.

## <a name="recommendation"></a>Empfehlung

Es wird empfohlen, die Funktion [SELECTEDVALUE](/dax/selectedvalue-function) zu verwenden. Mit dieser Funktion wird das gleiche Ergebnis wie das in diesem Artikel beschriebene Muster erzielt, jedoch effizienter und eleganter.

Mit der SELECTEDVALUE-Funktion wird die Measuredefinition im Beispiel nun umgeschrieben.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> Es ist möglich, einen _alternativen Ergebniswert_ an die SELECTEDVALUE-Funktion zu übergeben. Der alternative Ergebniswert wird zurückgegeben, wenn entweder keine oder mehrere Filter auf die Spalte angewendet werden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
