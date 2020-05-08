---
title: m:n-Beziehungen in Power BI Desktop
description: Verwenden von Beziehungen mit einer m:n-Kardinalität in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761063"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Anwenden von m:n-Beziehungen in Power BI Desktop

Mithilfe der *Beziehungen mit m:n-Kardinalität* in Power BI Desktop können Sie Tabellen verknüpfen, die eine *m:n-Kardinalität* verwenden. Sie können einfacher und intuitiver Datenmodelle erstellen, die zwei oder mehr Datenquellen enthalten können. *Beziehungen mit m:n-Kardinalität* sind Teil der umfangreicheren Funktionen der *Zusammengesetzten Modelle* in Power BI Desktop.

![m:n-Beziehung im Bereich „Beziehung bearbeiten“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

*Beziehungen mit m:n-Kardinalität* in Power BI Desktop bestehen aus einer von drei miteinander in Beziehung stehenden Funktionen:

* **Zusammengesetzte Modelle**: Bei einem *zusammengesetzten Modell* kann ein Bericht zwei oder mehr Datenverbindungen beinhalten, einschließlich DirectQuery- oder Importverbindungen in beliebiger Kombination. Weitere Informationen finden Sie unter [Verwenden zusammengesetzter Modelle in Power BI Desktop](desktop-composite-models.md).

* **Beziehungen mit einer m:n-Kardinalität:** Mithilfe zusammengesetzter Modelle können Sie *Beziehungen mit m:n-Kardinalität* zwischen Tabellen erstellen. Bei diesem Ansatz entfallen die Anforderungen für eindeutige Werte in Tabellen. Zudem sind vorherige Problemumgehungen hinfällig, wie z.B. die Einführung neuer Tabellen zum Einrichten von Beziehungen. Im vorliegenden Artikel wird das Feature ausführlich erläutert.

* **Speichermodus**: Sie können nun angeben, welche Visuals eine Abfrage in Back-End-Datenquellen erfordern. Visuals, für die keine Abfrage nötig ist, werden importiert, auch wenn diese auf DirectQuery basieren. Mit diesem Feature kann die Leistung verbessert und die Auslastung des Back-Ends verringert werden. Zuvor initiierten sogar einfache Visuals wie Slicer Abfragen, die an Back-End-Quellen gesendet wurden. Weitere Informationen erhalten Sie unter [Storage mode in Power BI Desktop (Speichermodus in Power BI Desktop)](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Zweck einer Beziehung mit m:n-Kardinalität

Bevor *Beziehungen mit m:n-Kardinalität* verfügbar waren, wurde die Beziehung zwischen zwei Tabellen in Power BI definiert. Mindestens eine der Tabellenspalten, die an der Beziehung beteiligt war, musste eindeutige Werte enthalten. Häufig hat jedoch keine Spalte eindeutige Werte enthalten.

Angenommen, zwei Tabellen verfügten über eine Spalte mit der Bezeichnung „Land/Region“. Jedoch waren die Werte für „Land/Region“ in keiner Tabelle eindeutig. Solche Tabellen konnten nur über eine Problemumgehung miteinander verknüpft werden. Eine Möglichkeit zur Umgehung des Problems bestand darin, zusätzliche Tabellen mit den erforderlichen eindeutigen Werten einzufügen. Mithilfe der *Beziehungen mit m:n-Kardinalität* können Sie solche Tabellen direkt miteinander verknüpfen, indem Sie eine Beziehung mit *m:n-Kardinalität* verwenden.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Verwenden von Beziehungen mit m:n-Kardinalität

Wenn Sie eine Beziehung zwischen zwei Tabellen in Power BI definieren, müssen Sie die Kardinalität der Beziehung definieren. Die Beziehung zwischen den Tabellen „ProductSales“ und „Product“ kann beispielsweise mithilfe der Spalten „ProductSales[ProductCode]“ und „Product[ProductCode]“ als *n:1* definiert werden. Die Beziehung wird auf diese Weise definiert, weil es für jedes Produkt viele Verkäufe gibt und die Spalte „ProductCode“ in der Tabelle „Product“ eindeutig ist. Wenn Sie die Kardinalität einer Beziehung als *n:1*, *1:n* oder *1:1* definieren, überprüft Power BI, ob die ausgewählte Kardinalität den tatsächlichen Daten auch entspricht.

Die folgende Abbildung zeigt beispielsweise ein einfaches Modell:

![Tabellen „ProductSales und „Product“ in der Beziehungsansicht in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Nehmen Sie nun an, dass die Tabelle **Product** wie im Folgenden dargestellt nur zwei Zeilen anzeigt:

![Visual der Tabelle „Product“ mit zwei Zeilen in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Angenommen, die Tabelle „Sales“ enthielte nur vier Zeilen, darunter die Zeile für ein Produkt C. Aufgrund eines Fehlers in der referenziellen Integrität ist die Zeile für Produkt C in der Tabelle **Product** nicht vorhanden.

![Visual der Tabelle „Sales“ mit vier Zeilen in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Die Spalten **ProductName** und **Price** (aus der Tabelle **Product**) zusammen mit der Gesamtmenge **Qty** für jedes Produkt (aus der Tabelle „ProductSales“) würden nun wie folgt angezeigt:

![Visual mit den Spalten „ProductName“, „Price“ und „Qty“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Sie sehen in der vorherigen Abbildung, dass eine leere **ProductName**-Zeile den Verkäufen für Produkt C zugeordnet ist. Folgende Gründe können für die leere Zeile verantwortlich sein:

* Alle Zeilen in der Tabelle **ProductSales**, für die keine zugehörige Zeile in der Tabelle **Product** vorhanden ist. Es besteht ein Problem mit der referenziellen Integrität, das sich in diesem Beispiel auf Produkt C auswirkt.

* Zeilen in der Tabelle **ProductSales**, bei denen die Fremdschlüsselspalte NULL ist.

Aus diesen Gründen deckt die leere Zeile in beiden Fällen Verkäufe ab, bei denen **ProductName** und **Price** unbekannt sind.

Manchmal werden die Tabellen durch zwei Spalten verknüpft, von denen jedoch keine eindeutig ist. Betrachten Sie beispielsweise die folgenden beiden Tabellen:

* Die Tabelle **Sales** stellt die Umsatzdaten nach **State** dar, wobei jede Zeile den Umsatzbetrag für den Typ des Umsatzes im jeweiligen Bundesstaat enthält. Zu diesen Bundesstaaten zählen z.B. Kalifornien, Washington und Texas (CA, WA, TX).

    ![Tabelle „Sales“ mit dem Umsatz nach Bundesstaaten in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* Die Tabelle **CityData** enthält Daten zu Städten, wie etwa Einwohnerzahl und Bundesstaat (z. B. CA, WA und New York).

    ![Tabelle „Sales“ mit „City“, „State“ und „Population“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Beide Tabellen enthalten also eine Spalte für **State**. Es liegt nun nahe, in einem Bericht die Gesamtumsätze pro Bundesstaat mit der Gesamtbevölkerung der einzelnen Bundesstaaten zu kombinieren. Dabei gibt es jedoch ein Problem: In keiner Tabelle ist die Spalte **State** eindeutig.

## <a name="the-previous-workaround"></a>Die bisherige Problemumgehung

Vor dem Power BI Desktop-Release vom Juli 2018 konnten Benutzer keine direkte Beziehung zwischen diesen Tabellen erstellen. Eine gängige Problemumgehung bestand aus den folgenden Schritten:

* Eine dritte Tabelle wurde erstellt, die ausschließlich die eindeutigen IDs von „State“ enthielt. Für die Tabelle galt eine oder alle der folgenden Optionen:
  * Eine berechnete Tabelle, die mithilfe von DAX (Data Analysis Expressions) definiert wurde
  * Eine Tabelle, die auf einer Abfrage basiert, die im Abfrage-Editor definiert wurde, und in der die eindeutigen IDs enthalten sein können, die aus einer der Tabellen abgerufen wurden.
  * Eine Kombination aus beidem.

* Anschließend wurde mithilfe herkömmlicher *n:1*-Beziehungen eine Beziehung zwischen den beiden ursprünglichen Tabellen und der neuen Tabelle hergestellt.

Dabei konnte die Tabelle für die Problemumgehung sichtbar bleiben. Oder die Tabelle konnte ausgeblendet werden, damit sie nicht in der Liste **Felder** angezeigt wurde. Bei ausgeblendeter Tabelle wurden die *n:1*-Beziehungen üblicherweise so festgelegt, dass in beide Richtungen gefiltert wurde. So konnte das Feld „State“ von jeder Tabelle verwendet werden. Die spätere Kreuzfilterung wurde an die andere Tabelle weitergegeben. Dieser Ansatz wird in der folgenden Abbildung veranschaulicht:

![Ausgeblendete Tabelle „State“ in der Beziehungsansicht in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Ein Visual, das **State** (aus der Tabelle **CityData**) zusammen mit der Gesamtwert von **Population** und **Sales** anzeigt, würde dann wie folgt aussehen:

![Tabellen „State“, „Population“ und „Sales“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Da in dieser Problemumgehung der Wert für „State“ aus der Tabelle **CityData** verwendet wird, werden nur die State-Werte dieser Tabelle aufgeführt (weshalb TX ausgeschlossen wurde). Im Gegensatz zu *n:1*-Beziehungen ist zudem in den Details keine leere Zeile enthalten, die solche nicht übereinstimmenden Zeilen abdeckt. Die Zeile „Total“ enthält hingegen alle **Sales**-Werte (einschließlich der von TX). Analog dazu gäbe es keine leere Zeile für alle **Sales**-Werte, bei denen der Wert für **State** NULL lautet.

Angenommen, Sie fügen dem Visual auch die Spalte „City“ hinzu. Obwohl die Einwohnerzahl für jeden City-Wert bekannt ist, wird in der **Sales**-Spalte für „City“ nur der **Sales**-Wert für die entsprechende **State**-Spalte wiederholt. Zu diesem Szenario kann es kommen, wenn die Spaltengruppierung, wie in der folgenden Abbildung gezeigt, mit keinem aggregierten Measure verknüpft ist:

![„State“, „City Population“ und „Sales“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Angenommen, Sie definieren die neue Tabelle „Sales“ als Kombination aller Werte für „States“ und machen dies in der Liste **Felder** sichtbar. Dasselbe Visual würde **State** (in der neuen Tabelle), die Gesamtbevölkerung für **Population** und den Gesamtumsatz für **Sales** anzeigen:

![Visual mit „State“, „Population“ und „Sales“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Sie sehen, dass TX (inklusive Daten für **Sales**, jedoch ohne Daten für *Population*) und New York (inklusive Daten für **Population**, jedoch ohne Daten für **Sales**) enthalten wären. Diese Umgehung ist nicht ideal und führt zu vielen Problemen. Für Beziehungen mit m:n-Kardinalität werden die daraus resultierenden Probleme wie im folgenden Abschnitt beschrieben behoben.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Verwenden von Beziehungen mit m:n-Kardinalität anstelle einer Problemumgehung

Mit der Power BI Desktop-Version vom Juli 2018 können Sie Tabellen direkt miteinander verknüpfen, ohne auf die oben beschriebene Problemumgehung zurückgreifen zu müssen. Die Kardinalität einer Beziehung kann nun auf *m:n* festgelegt werden. Diese Einstellung gibt an, dass keine der Tabellen eindeutige Werte enthält. Dennoch können Sie für diese Beziehungen weiterhin steuern, welche Tabelle die andere Tabelle filtern soll. Alternativ können Sie mit einer bidirektionalen Filterung auch festlegen, dass sich die Tabellen gegenseitig filtern sollen.

In Power BI Desktop lautet die Standardeinstellung für die Kardinalität *m:n*, wenn festgestellt wird, dass keine der Tabellen eindeutige Werte für die Beziehungsspalten enthält. In solchen Fällen müssen Sie in einer Warnmeldung bestätigen, dass Sie eine Beziehung festlegen möchten und die Änderung nicht die unbeabsichtigte Auswirkung eines Datenproblems ist.

Wenn Sie z. B. eine direkte Beziehung zwischen „CityData“ und „Sales“ erstellen (mit Filterrichtung von „CityData“ zu „Sales“), zeigt Power BI Desktop das Dialogfeld **Beziehung bearbeiten** an:

![Dialogfeld „Beziehung bearbeiten“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Die resultierende **Beziehungsansicht** würde dann die direkte m:n-Beziehung zwischen den beiden Tabellen darstellen. Die Darstellung der Tabellen in der Liste **Felder** und deren späteres Verhalten, wenn die Visuals erstellt wurden, ähneln den Ergebnissen, die durch die Problemumgehung erzielt wurden. In der Problemumgehung wurde die zusätzliche Tabelle mit den eindeutigen Daten für „State“ nicht sichtbar gemacht. Wie oben bereits erwähnt, wird ein Visual mit den Spalten **State**, **Population** und **Sales** folgendermaßen angezeigt:

![Tabellen „State“, „Population“ und „Sales“ in Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Zwischen *Beziehungen mit einer m:n-Kardinalität* und den geläufigeren *n:1*-Beziehungen bestehen folgende wesentliche Unterschiede:

* Die angezeigten Werte enthalten keine leere Zeile, die nicht übereinstimmende Zeilen in der anderen Tabelle abdeckt. Die Werte decken ebenfalls keine Zeilen ab, bei denen die Spalte, die in der anderen Tabelle der Beziehung verwendet wurde, den Wert NULL aufweist.
* Die Funktion `RELATED()` kann nicht verwendet werden, da mehr als eine Zeile verknüpft sein könnte.
* Mit der Funktion `ALL()` werden in einer Tabelle keine Filter entfernt, die auf andere verknüpfte Tabellen angewendet wurden, mit denen eine m:n-Beziehung besteht. Im vorherigen Beispiel würde ein Measure, das wie hier definiert wurde, keine Filter für Spalten in der verknüpften Tabelle „CityData“ entfernen:

    ![Beispiel für ein Skript](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Ein Visual mit Daten für **State**, **Sales** und **Sales total** würde folgendermaßen angezeigt werden:

    ![Tabellenvisual](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Stellen Sie aufgrund dieser Unterschiede sicher, dass die Berechnungen, die `ALL(<Table>)` verwenden (wie z. B. *% von Gesamtsumme*), die gewünschten Ergebnisse zurückgeben.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Bei diesem Release für *Beziehungen mit einer m:n-Kardinalität* und zusammengesetzte Modelle gibt es einige Einschränkungen.

Die folgenden (mehrdimensionalen) Live Connect-Quellen können nicht mit zusammengesetzten Modellen verwendet werden:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-Datasets
* Azure Analysis Services

Wenn Sie mithilfe von DirectQuery eine Verbindung mit diesen mehrdimensionalen Quellen herstellen, können Sie keine Verbindung mit einer anderen DirectQuery-Quelle herstellen oder diese mit importierten Daten kombinieren.

Die bestehenden Einschränkungen für die Verwendung von DirectQuery gelten nach wie vor, wenn Sie *Beziehungen mit einer m:n-Kardinalität* verwenden. Viele Einschränkungen gelten jetzt abhängig vom Speichermodus der Tabelle für eine einzelne Tabelle. Beispielsweise kann eine berechnete Spalte in einer importierten Tabelle auf andere Tabellen verweisen, wohingegen eine berechnete Spalte in einer DirectQuery-Tabelle nach wie vor nur auf Spalten in derselben Tabelle verweisen kann. Es gelten weitere Einschränkungen für das ganze Modell, wenn darin enthaltene Tabellen den Modus „DirectQuery“ aufweisen. Die Funktionen „QuickInsights“ und „Q&A“ sind nicht für Modelle verfügbar, wenn darin enthaltene Tabellen den Speichermodus „DirectQuery“ aufweisen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu zusammengesetzten Modellen und DirectQuery finden Sie in den folgenden Artikeln:
* [Verwenden zusammengesetzter Modelle in Power BI Desktop](desktop-composite-models.md)
* [Speichermodus in Power BI Desktop](desktop-storage-mode.md)
* [Verwenden von DirectQuery in Power BI](desktop-directquery-about.md)
* [Power BI-Datenquellen](power-bi-data-sources.md)
