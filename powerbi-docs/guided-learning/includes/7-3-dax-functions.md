---
ms.openlocfilehash: c3b1b7288d0d277fc866ea47887335d10279c6cc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799866"
---
Mit DAX erhalten Sie viele verfügbare Funktionen zum Strukturieren, Formatieren oder Analysieren Ihrer Daten. Diese Funktionen können in eine Handvoll Kategorien unterteilt werden:

* **Aggregationsfunktionen**
* **Zählfunktionen**
* **Logische** Funktionen
* **Informationsfunktionen**
* **Textfunktionen**
* **Datumsfunktionen**

Ähnlich wie Excel erscheint eine Liste von verfügbaren Funktionen, wenn Sie beginnen, Ihre Formel in die **Bearbeitungsleiste** von Power BI Desktop einzugeben. Diese Liste hilft Ihnen dabei, zu bestimmen, welche verfügbare Funktion Sie auswählen möchten. Mithilfe der **NACH-OBEN**- und der **NACH-UNTEN**-Pfeiltaste auf Ihrer Tastatur können Sie jede beliebige, verfügbare Funktion markieren. Dabei wird eine kurze Beschreibung angezeigt.

Power BI zeigt die Funktionen an, die mit den bereits eingegebenen Buchstaben übereinstimmen. Wenn Sie also *S* eingeben, werden nur Funktionen in der Liste angezeigt, die mit *S* beginnen. Wenn Sie *Su* eingeben, werden nur Funktionen, die die Buchstabenfolge *Su* *enthalten*, in der Liste angezeigt (sie müssen nicht mit *Su* beginnen, es muss nur die Buchstabenfolge enthalten sein).

![](media/7-3-dax-functions/dax-functions_1.png)

Es ist einfach, mit DAX auf diese Weise zu experimentieren und jede der verschiedenen DAX-Funktionen zu suchen, die in Power BI verfügbar sind. Sie müssen nur anfangen zu tippen, und Power BI hilft Ihnen weiter.

Jetzt da wir wissen, wie man mit der DAX-Formel beginnt, sehen wir uns wiederum jede dieser Funktionskategorien an.

## <a name="aggregation-functions"></a>Aggregationsfunktionen
DAX verfügt über eine Anzahl von **Aggregationsfunktionen**, darunter die folgenden häufig verwendeten Funktionen:

* SUMME
* MITTELWERT
* MIN
* MAX
* SUMX (und andere *X*-Funktionen)

Diese Funktionen können nur für numerische Spalten verwendet werden und können im Allgemeinen jeweils nur eine Spalte aggregieren.

Allerdings können spezielle Aggregationsfunktionen, die auf **X** enden, z.B. **SUMX**, mehrere Spalten gleichzeitig bearbeiten. Diese Funktionen durchlaufen die Tabelle und werten den Ausdruck für jede Zeile aus.

## <a name="counting-functions"></a>Zählfunktionen
Diese in DAX häufig verwendeten **Zählfunktionen** erhalten z.B.:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Mit diesen Funktionen werden verschiedene Elemente gezählt, z.B. unterschiedliche Werte, nicht leere Werte oder Tabellenzeilen.

## <a name="logical-functions"></a>Logische Funktionen
Die Sammlung der **logischen** Funktionen in DAX enthalten:

* AND
* OR
* NOT
* IF
* IFERROR

Diese speziellen Funktionen können auch mit *Operatoren* ausgedrückt werden. Sie können in Ihrer DAX-Formel beispielsweise **AND** als **&&** eingeben bzw. dadurch ersetzen.

Sie können Operatoren verwenden (z.B. **&&** ), wenn Sie mehr als zwei Bedingungen in der Formel benötigen. Andernfalls ist es jedoch von Vorteil, den Namen der Funktion (z.B. **AND**) für die Lesbarkeit Ihres DAX-Codes zu verwenden.

## <a name="information-functions"></a>Informationsfunktionen
**Informationsfunktionen** in DAX enthalten:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Diese Funktionen können zwar in manchen Situationen nützlich sein, es ist jedoch von Vorteil, den Datentyp Ihrer Spalten vorher schon zu kennen, anstatt sich bei der Bestimmung des Datentyps auf diese Funktionen zu verlassen.

DAX verwendet die **MAX**- und **MIN**-Funktionen um Werte jeweils zu *aggregieren* und zu *vergleichen*.

## <a name="text-functions"></a>Textfunktionen
Die **Textfunktionen** in DAX enthalten:

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Diese **Textfunktionen** funktionieren ähnlich wie die Excelfunktionen, die den gleichen Namen besitzen. Wenn Sie sich also damit auskennen, wie Excel mit Textfunktionen umgeht, dann sind Sie schon einen Schritt voraus. Wenn dies nicht der Fall, können Sie immer mit diesen Funktionen in Power BI experimentieren und erfahren, wie sie sich verhalten.

## <a name="date-functions"></a>Datumsfunktionen
DAX enthält die folgenden **Datumsfunktionen**:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Diese Funktionen sind hilfreich zum Berechnen und Extrahieren von Informationen aus *Datumswerten*. Sie gelten nicht für Zeitintelligenz, bei der eine Datumstabelle verwendet wird.

> Videoinhalt zur Verfügung gestellt von [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

