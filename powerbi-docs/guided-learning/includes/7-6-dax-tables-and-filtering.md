---
ms.openlocfilehash: 5bc0d3bbfb2c2b67b56e6406646f6131a360b97d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799867"
---
Ein wesentlicher Unterschied zwischen **DAX** und der Excel-Formelsprache ist der, dass Sie mit DAX *komplette Tabellen* in Ausdrücken berechnen können, ohne dass Sie auf einen einzigen Wert beschränkt sind. Ein signifikanter Effekt ist, dass DAX Ihnen erlaubt, Tabellen in deren Ausdrücken zu filtern und anschließend mit dem gefilterten Wertesatz zu arbeiten.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

Mit DAX können Sie völlig neue berechnete Tabellen erstellen und diese dann wie jede andere Tabelle behandeln – einschließlich der Erstellung von Beziehungen zwischen ihnen und anderen Tabellen in Ihrem Datenmodell.

## <a name="dax-table-functions"></a>DAX-Tabellenfunktionen
DAX verfügt über einen umfangreichen Satz von **Tabellenfunktionen**, einschließlich der folgenden:

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Diese Funktionen geben anstatt eines Werts eine vollständige Tabelle zurück. Normalerweise verwenden Sie die Ergebnisse einer **Tabellenfunktion** in weiteren Analysen als Teil eines größeren Ausdrucks und nicht die zurückgegebene Tabelle als endgültigen Wert. Es ist wichtig, zu beachten, dass wenn Sie eine Tabellenfunktion verwenden, die Ergebnisse die Beziehungen zwischen den Spalten erben.

Sie können Tabellenfunktionen in Ihrem Ausdruck kombinieren, solange eine Funktion jeweils eine Tabelle verwendet und eine Tabelle zurückgegeben wird. Betrachten Sie beispielsweise den folgenden DAX-Ausdruck:

    FILTER (ALL (Table), Condition)

Dieser Ausdruck wendet einen Filter auf die gesamte *Tabelle* an, und alle aktuellen Filterinhalte werden ignoriert.

Die DISTINCT-Funktion gibt die unterschiedlichen Werte einer Spalte zurück, die auch im aktuellen Kontext sichtbar sind. Um den oben genannten DAX-Ausdruck zu verwenden, werden mit **ALL** alle Filter in diesem Ausdruck ignoriert. Ersetzt man **ALL** durch **DISTINCT** würde dieser wieder berücksichtigt.

## <a name="counting-values-with-dax"></a>Zählen von Werten mit DAX
Eine häufig gestellte Frage beim Erstellen von Berichten in Power BI ist die folgende:

* „Wie viele Werte sind für diese Spalte vorhanden?“

Diese Frage kann schnell beantwortet werden, wenn Ihnen eine Tabelle angezeigt wird, DAX bietet jedoch einen anderen Ansatz, insbesondere dann, wenn eine Beziehung zwischen Tabellen besteht.

Power BI und DAX schließen z.B. Werte ein, die nicht ordnungsgemäß untereinander indiziert werden. Wenn die eingehende Beziehung getrennt wird, fügt DAX eine neue Zeile zur verknüpften Tabelle hinzu, deren Felder leer sind, und verknüpft diese neue Zeile mit der nicht indizierten Zeile, um die referenzielle Integrität zu gewährleisten. Wenn die Funktion leere Zeilen einschließt, was z.B oft der Fall ist, wenn **ALL** verwendet wird, werden diese leeren Zeilen in die Anzahl der Werte eingeschlossen, die für diese Spalte zurückgegeben werden.

Sie können auch ganze berechnete Tabellen mit DAX-Funktionen erstellen. Berechnete mit DAX erstellte Tabellen erfordern jeweils eine **NAME**- und eine **TABLE**-Funktion. Berechnete Tabellen können wie jede andere Tabelle verwendet werden, u.a. zum Erstellen von Beziehungen.

> Videoinhalt zur Verfügung gestellt von [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

