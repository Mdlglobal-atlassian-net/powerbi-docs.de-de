---
ms.openlocfilehash: f4043a5a8deac0596b58519183988f6ae574458e
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2019
ms.locfileid: "70847687"
---
Es gibt zwei primäre Berechnungen, die Sie mithilfe von DAX erstellen können:

* **Berechnete Spalten**
* **Berechnete Measures**

Bevor Sie versuchen, eine davon zu erstellen, sollten Sie ein ausgeprägtes Verständnis der DAX-Syntax für Tabellen und Spalten besitzen. Dies hilft Ihnen bei der Erstellung von **berechneten Spalten** oder **berechneten Measures** weiter.

## <a name="dax-table-and-column-name-syntax"></a>DAX-Syntax für Tabellen- und Spaltennamen
Es ist wichtig, das allgemeine Format von Tabellennamen in DAX zu kennen, egal ob Sie eine neue Spalte oder ein neues Measure erstellen.

    'Table Name'[ColumnName]

Wenn Leerzeichen im Tabellennamen (siehe oben) vorhanden sind, sind einfache Anführungszeichen um den Tabellennamen zwingend erforderlich. Wenn der Tabellenname keine Leerzeichen enthält, können die einfachen Anführungszeichen ausgelassen werden, und die Syntax sieht wie folgt aus:

    TableName[ColumnName]

Die folgende Abbildung zeigt eine DAX-Formel, die in Power BI erstellt wird:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

Sie können den Tabellennamen auch komplett weglassen und nur den Spaltennamen verwenden, dies ist für eindeutige Funktionen jedoch keine empfohlene Vorgehensweise (und so auch nicht für den eindeutigen DAX-Code). Spaltennamen müssen immer rechteckige Klammern enthalten.

Es wird empfohlen, *immer* folgendermaßen vorzugehen:

* Keine Leerzeichen im Tabellennamen
* Schließen Sie den Tabellennamen immer in Formeln mit ein (lassen Sie ihn nicht weg, auch wenn DAX dies zulässt)

## <a name="creating-calculated-columns"></a>Erstellen von berechneten Spalten
**Berechnete Spalten** sind nützlich, wenn Sie aus dem Wert Slices erstellen oder danach filtern möchten, oder wenn Sie eine Berechnung für jede Zeile in der Tabelle benötigen.

Sie können berechnete Spalten in Power BI Desktop erstellen, indem Sie **New Column** (Neue Spalte) auf der Registerkarte **Modeling** (Modellierung) auswählen. Hierzu wird die Datenansicht empfohlen (anstatt die Berichtsansicht oder die **Beziehungsansicht**), da Sie die neu erstelle Spalte und anzeigen können, und die **Bearbeitungsleiste** ist aufgefüllt und bereit für Ihre DAX-Formeln.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Sobald Sie die Schaltfläche **New Column** (Neue Spalte) auswählen, wird die**Bearbeitungsleiste** mit einem Standardspaltennamen (den Sie natürlich so verändern, dass er zu Ihrer Formel passt) und dem **=** -Operator aufgefüllt, und die neue Spalte erscheint im Datenraster, wie im folgenden Bild gezeigt.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Die erforderlichen Elemente für eine berechnete Spalte sind die folgenden:

* ein neuer Spaltenname
* mindestens eine Funktion oder ein Ausdruck

Wenn Sie in der Formel für die berechnete Spalte auf eine Tabelle oder Spalte verweisen, müssen Sie keine Zeile in der Tabelle angeben – Power BI berechnet die Spalte für die aktuelle Zeile für jede Berechnung.

## <a name="creating-calculated-measures"></a>Erstellen von berechneten Measures
Verwenden Sie ein **berechnetes Measure**, wenn Sie Prozentsätze oder Verhältnisse berechnen oder komplexe Aggregationen benötigen. Wählen Sie die Schaltfläche **New Measure** (Neues Measure) der Registerkarte **Modeling** (Modellierung), um ein Measure mithilfe einer DAX-Formel zu erstellen. Hier empfiehlt sich wieder die **Datenansicht** von Power BI Desktop, da sie die **Bearbeitungsleiste** anzeigt und das Schreiben Ihrer DAX-Formel einfach macht.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

Mit **Measures** wird ein neues Measure-Symbol im Bereich **Fields** (Felder) mit dem Namen des Measures angezeigt. Die **Bearbeitungsleiste** wird erneut mit dem Namen Ihrer DAX-Formel (diesmal mit Ihrem Measure) aufgefüllt.

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

Die erforderlichen Elemente für ein berechnetes Measure sind die gleichen wie für eine berechnete Spalte:

* einen neuer Measurename
* mindestens eine Funktion oder ein Ausdruck

> Videoinhalt zur Verfügung gestellt von [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

