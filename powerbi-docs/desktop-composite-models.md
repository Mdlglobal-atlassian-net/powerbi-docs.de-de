---
title: Verwenden zusammengesetzter Modelle in Power BI Desktop
description: Erstellen von Datenmodellen mit mehreren Datenverbindungen und m:n-Beziehungen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 45f7ecee11cd57a73ed0e998dad26935b560c8ad
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2020
ms.locfileid: "76161213"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>Verwenden zusammengesetzter Modelle in Power BI Desktop

Wenn Sie bislang DirectQuery in einem Bericht in Power BI Desktop verwendet haben, waren keine anderen Datenverbindungen für diesen Bericht zulässig – ganz gleich, ob es sich um DirectQuery- oder Importdatenverbindungen handelte. Bei zusammengesetzten Modellen ist diese Einschränkung hinfällig. Ein Bericht kann problemlos mehrere DirectQuery- oder Importdatenverbindungen in einer beliebigen Kombination derselbigen umfassen.

Die Funktion „Zusammengesetzte Modelle“ in Power BI Desktop besteht aus drei in Beziehung stehenden Features:

* **Zusammengesetzte Modelle**: Hierbei kann ein Bericht mehrere Datenverbindungen beinhalten, einschließlich DirectQuery- oder Importverbindungen in beliebiger Kombination. In diesem Artikel werden die zusammengesetzten Modelle ausführlich erläutert.

* **m:n-Beziehungen**: Mithilfe zusammengesetzter Modelle können Sie *m:n-Beziehungen* zwischen Tabellen einrichten. Bei diesem Ansatz entfallen die Anforderungen für eindeutige Werte in Tabellen. Zudem sind vorherige Problemumgehungen hinfällig, wie z.B. die Einführung neuer Tabellen zum Einrichten von Beziehungen. Weitere Informationen finden Sie unter [Anwenden von m:n-Beziehungen in Power BI Desktop](desktop-many-to-many-relationships.md).

* **Speichermodus**: Sie können nun angeben, welche Visuals Back-End-Datenquellen abfragen. Visuals, für die keine Abfrage nötig ist, werden importiert, auch wenn diese auf DirectQuery basieren. Mit diesem Feature kann die Leistung verbessert und die Auslastung des Back-Ends verringert werden. Zuvor initiierten sogar einfache Visuals wie Slicer Abfragen von Back-End-Quellen. Weitere Informationen erhalten Sie unter [Verwalten des Speichermodus in Power BI Desktop](desktop-storage-mode.md).

## <a name="use-composite-models"></a>Verwenden von zusammengesetzten Modelle

Mithilfe zusammengesetzter Modelle können Sie eine Verbindung mit verschiedenen Arten von Datenquellen herstellen, wenn Sie Power BI Desktop oder den Power BI-Dienst verwenden. Sie haben mehrere Möglichkeiten, diese Datenverbindungen einzurichten:

* Durch das Importieren von Daten in Power BI, was den einfachsten Weg darstellt, Daten abzurufen
* Durch die direkte Verbindung mit Daten im ursprünglichen Quellrepository über DirectQuery. Weitere Informationen zu DirectQuery finden Sie unter [Verwenden von DirectQuery mit Power BI](desktop-directquery-about.md).

Bei Verwendung von DirectQuery mit zusammengesetzten Modellen ist es möglich, ein Power BI-Modell – beispielsweise eine einzelne Power BI Desktop-Datei im *PBIX*-Format – für folgende Zwecke zu erstellen:

* Kombinieren von Daten aus mindestens einer DirectQuery-Quelle
* Kombinieren von Daten aus DirectQuery-Quellen und Importdaten

Wenn Sie z.B. zusammengesetzte Modelle verwenden, können Sie ein Modell erstellen, das die folgenden Datentypen kombiniert:

* Verkaufsdaten eines Data Warehouse von einem Unternehmen
* Verkaufszieldaten von einer SQL Server-Abteilungsdatenbank
* Daten, die aus einem Arbeitsblatt importiert wurden

Ein Modell, bei dem Daten aus mehr als einer DirectQuery-Quelle kombiniert werden oder bei dem DirectQuery mit importierten Daten kombiniert wird, wird als zusammengesetztes Modell bezeichnet.

Sie können wie gewohnt Beziehungen zwischen Tabellen herstellen, auch wenn diese Tabellen aus verschiedenen Quellen stammen. Alle quellenübergreifenden Beziehungen werden mit einer Kardinalität von m:n erstellt, unabhängig von ihrer tatsächlichen Kardinalität. Sie können sie in 1:n, n:1 oder m:n ändern. Unabhängig von der festgelegten Kardinalität weisen quellenübergreifende Beziehungen ein abweichendes Verhalten auf. Sie können keine DAX-Funktionen (Data Analysis Expressions) verwenden, um Werte der `one`-Seite von der `many`-Seite aus abzurufen. Ferner stellen Sie möglicherweise eine beeinträchtigte Leistung im Vergleich mit m:n-Beziehungen innerhalb der gleichen Quelle fest.

> [!NOTE]
> Im Kontext von zusammengesetzten Modellen stellen alle importierten Tabellen im Grunde eine einzelne Quelle dar, unabhängig von den tatsächlichen zugrunde liegenden Datenquellen.

## <a name="example-of-a-composite-model"></a>Beispiel für ein zusammengesetztes Modell

Nehmen Sie für das Beispiel eines zusammengesetzten Modells an, dass Sie über einen Bericht verfügen, der über DirectQuery mit einem Data Warehouse eines Unternehmens in SQL Server verbunden ist. In diesem Fall enthält das Data Warehouse die Daten **Sales by Country** (Verkäufe nach Land/Region), **Quarter** (Quartal) und **Bike (Product)** (Fahrrad (Produkt)), so wie in folgender Abbildung dargestellt:

![Beziehungsansicht bei zusammengesetzten Modellen](media/desktop-composite-models/composite-models_04.png)

Nun könnten Sie mithilfe von Feldern aus dieser Quelle einfache Visuals erstellen. Die folgende Abbildung zeigt den Gesamtumsatz nach *ProductName* für ein ausgewähltes Quartal.

![Visual basierend auf Daten](media/desktop-composite-models/composite-models_05.png)

Aber was geschieht, wenn Sie Daten in einer Office Excel-Arbeitsmappe über den Produktmanager (Product Manager) verfügen, der jedem Produkt zusammen mit der Marketingprioriät zugewiesen ist? Wenn Sie den **Sales Amount** (Verkaufssumme) nach **Product Manager** anzeigen möchten, können Sie diese lokalen Daten möglicherweise nicht dem Data Warehouse des Unternehmens hinzuzufügen. Bestenfalls dauert es ansonsten Monate.

Es ist vielleicht möglich, diese Umsatzdaten über das Data Warehouse zu importieren anstatt über DirectQuery. Die Verkaufsdaten könnten dann mit den Daten kombiniert werden, die Sie vom Arbeitsblatt importiert haben. Dieser Ansatz ist jedoch nicht sinnvoll angesichts der Beweggründe, aus denen DirectQuery überhaupt verwendet wird. Diese Gründe sind unter anderem folgende:

* Sicherheitsregeln, die in der zugrunde liegenden Quelle erzwungen werden
* Die Notwendigkeit, die neuesten Daten anzuzeigen
* Das schiere Volumen der Daten

An dieser Stelle kommen zusammengesetzte Modelle ins Spiel. Zusammengesetzte Modelle ermöglichen es Ihnen, über DirectQuery eine Verbindung herzustellen und dann **Daten abrufen** für zusätzliche Quellen zu verwenden. In diesem Beispiel richten wir zunächst die DirectQuery-Verbindung für das Data Warehouse des Unternehmens. Wir verwenden **Daten abrufen**, wählen **Excel** aus, und navigieren dann zu dem Arbeitsblatt, das unsere lokalen Daten enthält. Schließlich importieren wir das Arbeitsblatt, das die *Produktnamen* (Product Name), den zugewiesenen **Vertriebsleiter** (Sales Manager) und die **Priorität** (Priority) enthält.  

![Navigator-Fenster](media/desktop-composite-models/composite-models_06.png)

In der Liste **Fields** (Felder) sehen Sie zwei Tabellen: die ursprüngliche **Bike**-Tabelle von SQL Server und die neue **ProductManagers**-Tabelle. Die neue Tabelle enthält die Daten, die von Excel importiert wurden.

![Felderansicht der Tabellen](media/desktop-composite-models/composite-models_07.png)

Auch in Power BI Desktop finden Sie unter **Beziehungsansicht** nun eine weitere Tabelle mit dem Namen **ProductManagers**.

![Beziehungsansicht der Tabellen](media/desktop-composite-models/composite-models_08.png)

Nun müssen wir diese Tabellen mit den anderen Tabellen im Modell verknüpfen. Wir erstellen wie immer eine Beziehung zwischen der **Bike**-Tabelle von SQL Server und der importierten **ProductManagers**-Tabelle. Das heißt, die Beziehung wird zwischen **Bike[ProductName]** und **ProductManagers[ProductName]** aufgebaut. Wie zuvor erwähnt, weisen alle quellenübergreifenden Beziehungen die Standardkardinalität m:n auf.

![Das Fenster „Beziehung erstellen“](media/desktop-composite-models/composite-models_09.png)

Da wir nun diese Beziehung erstellt haben, wird die sie erwartungsgemäß in Power BI Desktop in der **Beziehungsansicht** angezeigt.

![Ansicht „Neue Beziehung“](media/desktop-composite-models/composite-models_10.png)

Nun können wir Visuals erstellen, indem wir ein beliebiges Feld der Liste **Fields**- (Felder) verwenden. Mit diesem Ansatz werden problemlos Daten aus mehreren Quellen vermischt. Beispielsweise wird der gesamte *SalesAmount* für jeden *Product Manager* in folgender Darstellung abgebildet:

![Bereich „Felder“](media/desktop-composite-models/composite-models_11.png)

Im folgenden Beispiel wird ein häufiges Szenario einer *Dimensionstabelle* dargestellt (z. B. **Product** oder **Customer**), die mit einigen zusätzlichen Daten aus anderen Quellen erweitert wird. Es ist ebenso möglich, dass Tabellen DirectQuery verwenden, um eine Verbindung zu verschiedenen Quellen herzustellen. Stellen Sie sich für unser Beispiel zudem vor, dass **SalesTargets** nach **Country** und **Period** in einer separaten Abteilungsdatenbank gespeichert werden würden. Mit **Daten abrufen** können Sie wie gewohnt eine Verbindung mit diesen Daten herstellen, wie in der folgenden Abbildung dargestellt wird:

![Das Navigator-Fenster](media/desktop-composite-models/composite-models_12.png)

Wie im Beispiel vorher können dann Beziehungen zwischen der neuen Tabelle und anderen Tabellen im Modell sowie Visuals erstellt werden, die die jeweiligen Tabellendaten kombinieren. Werfen wir erneut einen Blick auf die **Beziehungsansicht**, in der wir die neuen Beziehungen erstellt haben.

![Beziehungsansicht mit vielen Tabellen](media/desktop-composite-models/composite-models_13.png)

Die nächste Abbildung basiert auf den neuen Daten und Beziehungen, die wir erstellt haben. Das Visual links unten zeigt den gesamten *Umsatz* (Sales Amount) versus das *Ziel* (Target) sowie die Berechnung der Varianz für den Unterschied an. Die Daten von **Sales Amount** und **Target** stammen aus zwei unterschiedlichen SQL Server-Datenbanken.

![Abbildung mit weiteren Daten](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Festlegen des Speichermodus

Jede Tabelle in einem zusammengesetzten Modell weist einen Speichermodus auf, der angibt, ob die Tabelle auf DirectQuery oder Importen basiert. Der Speichermodus kann im Bereich **Eigenschaft** angezeigt und geändert werden. Um den Speichermodus anzuzeigen, klicken Sie mit der rechten Maustaste in die **Feldliste**, und wählen Sie **Eigenschaften** aus. Die folgende Abbildung zeigt den Speichermodus für die **SalesTargets**-Tabelle.

Der Speichermodus ist auch in der QuickInfo für die einzelnen Tabellen einsehbar.

![QuickInfo, die den Speichermodus anzeigt](media/desktop-composite-models/composite-models_16.png)

Bei Power BI Desktop-Dateien (*PBIX*-Format), die zum Teil Tabellen vom DirectQuery und importierte Tabellen enthalten, wird in der Statusleiste der Speichermodus mit dem Status **Gemischt** angezeigt. Durch Klicken auf diese Bezeichnung in der Statusleiste können Sie problemlos zwischen allen zu importierenden Tabellen wechseln.

Weitere Informationen zum Speichermodus finden Sie unter [Verwalten des Speichermodus in Power BI Desktop](desktop-storage-mode.md).  

> [!NOTE]
> Sie können den *gemischten* Speichermodus in Power BI Desktop und im Power BI-Dienst verwenden.

## <a name="calculated-tables"></a>Berechnete Tabellen

Sie können einem Modell, das DirectQuery verwendet, berechnete Tabelle hinzufügen. Die Data Analysis Expressions-Bibliothek (DAX), die die berechnete Tabelle definiert, kann entweder auf importierte Tabellen oder DirectQuery-Tabellen oder eine Kombination aus diesen beiden verweisen.

Berechnete Tabellen werden immer importiert, und die Daten in diesen Tabellen werden bei Aktualisierung der Tabellen aktualisiert. Wenn eine berechnete Tabelle auf eine DirectQuery-Tabelle verweist, zeigen Visuals, die auf die DirectQuery-Tabelle verweisen, immer die neuesten Werte in der zugrunde liegenden Quelle an. Visuals, die auf die berechnete Tabelle verweisen, zeigen alternativ die Werte für den Zeitpunkt an, als die berechnete Tabelle zuletzt aktualisiert wurde.

## <a name="security-implications"></a>Folgen für die Sicherheit

Zusammengesetzte Modelle haben Folgen für die Sicherheit. Eine an eine Datenquelle gesendete Abfrage kann Datenwerte enthalten, die von einer Quelle abgerufen wurden. Im vorherigen Beispiel hat das Visual, das den **Sales Amount** nach **Product Manager** angezeigt hat, eine SQL-Abfrage an die relationale Datenbank „Sales“ (Verkäufe) gesendet. Diese SQL-Abfrage kann die Namen der Product Manager sowie die zugehörigen Produkte enthalten.

![Skript mit den Folgen für die Sicherheit](media/desktop-composite-models/composite-models_17.png)

Aus diesem Grund werden die in der Tabelle gespeicherten Informationen nun in eine Abfrage eingefügt, die an die relationale Datenbank gesendet wird. Berücksichtigen Sie die genannten Folgen für die Sicherheit, wenn diese Informationen vertraulich sind. Beachten Sie insbesondere die folgenden Punkte:

* Jeder Administrator der Datenbank, der die Ablaufverfolgungen oder Überwachungsprotokolle anzeigen kann, kann diese Informationen einsehen, auch ohne Berechtigungen für die Daten in der ursprünglichen Datenquelle. In diesem Beispiel benötigt der Administrator Berechtigungen für die Excel-Datei.

* Die Verschlüsselungseinstellungen für jede Quelle müssen berücksichtigt werden. Vermeiden Sie es, Informationen aus einer Quelle über eine verschlüsselte Verbindung abzurufen und diese dann versehentlich in eine Abfrage einzuschließen, die über eine nicht verschlüsselte Verbindung an eine andere Quelle gesendet wird.

Um zu bestätigen, dass Sie die Auswirkungen auf die Sicherheit verstanden haben, wird in Power BI Desktop eine Warnmeldung angezeigt, wenn Sie ein zusammengesetztes Modell erstellen.  

Aus ähnlichen Gründen müssen Sicherheitsvorkehrungen getroffen werden, wenn eine Power BI Desktop-Datei geöffnet wird, die nicht von einer vertrauenswürdigen Quelle gesendet wurde. Sollte die Datei zusammengesetzte Modelle enthalten, werden Informationen, die eine Person mithilfe der Anmeldeinformationen des Benutzers, der die Datei öffnet, aus einer Quelle abruft, als Teil einer Abfrage an eine andere Datenquelle gesendet. Die Informationen können vom böswilligen Autor der Power BI Desktop-Datei angezeigt werden. Wenn Sie das erste Mal eine Power BI Desktop-Datei öffnen, die mehrere Quellen enthält, zeigt Power BI Desktop eine Warnung an. Diese Warnung ist mit der Warnung vergleichbar, die beim Öffnen einer Datei mit nativen SQL-Abfragen angezeigt wird.  

## <a name="performance-implications"></a>Folgen für die Leistung  

Bei der Verwendung von DirectQuery sollte stets die Leistung berücksichtigt werden, und zwar in erster Linie, um sicherzustellen, dass die Back-End-Quelle genügend Ressourcen aufweist, um ein zufriedenstellendes Benutzererlebnis bereitzustellen. Das bedeutet, dass sich die Visuals in weniger als fünf Sekunden aktualisieren. Weitere Empfehlungen zur Leistung finden Sie unter [Verwenden von DirectQuery in Power BI](desktop-directquery-about.md).

Das Verwenden von zusammengesetzten Modelle bringt weitere Punkte hinsichtlich der Leistung mit sich. Ein einzelnes Visual kann dazu führen, dass Abfragen an mehrere Quellen gesendet werden, wodurch die Ergebnisse häufig von einer Abfrage zu einer zweiten Quelle weitergeleitet werden. Diese Situation kann in den folgenden Ausführungsmöglichkeiten eintreten:

* **Eine SQL-Abfrage, die eine große Anzahl an Literalwerten enthält:** Zum Beispiel muss ein Visual, das den gesamten **Sales Amount**-Wert für eine Reihe ausgewählter **Product Managers** enthält, zunächst ermitteln, welche **Products** von diesen Product Managers verwaltet wurden. Diese Sequenz muss erfolgen, bevor das Visual eine SQL-Abfrage sendet, die alle Produkt-IDs in einer `WHERE`-Klausel enthält.

* **Eine SQL-Abfrage, die auf einer niedrigeren Granularitätsebene abfragt, wobei die Daten später lokal aggregiert werden:** Da die Anzahl von **Products** zunimmt, die den Filterkriterien unter **Product Manager** entsprechen, kann es ineffizient oder nicht praktikabel sein, alle Produkte in einer `WHERE`-Klausel zusammenzufassen. Stattdessen können Sie die relationale Quelle auf der unteren **Products**-Ebene abfragen und die Ergebnisse dann lokal aggregieren. Wenn die Kardinalität der **Produkte** einen Grenzwert von 1 Million überschreitet, tritt bei der Abfrage ein Fehler auf.

* **Mehrere SQL-Abfragen, eine pro Gruppe nach Wert**: Wenn die Aggregation **DistinctCount** eine Gruppierung nach einer bestimmten Spalte aus einer anderen Quelle verwendet, muss eine SQL-Abfrage pro Gruppe nach Wert gesendet werden, wenn die externe Quelle keine effiziente Übergabe von vielen Literalwerten mit definierter Gruppierung unterstützt.

   Ein Visual, das eine andere **CustomerAccountNumber**-Anzahl (aus der SQL Server-Tabelle) von **ProductManagers** (aus dem Arbeitsblatt) anfordert, muss die Details aus der Tabelle **ProductManagers** in der Abfrage übergeben, die an SQL Server gesendet wird. Diese Aktion ist für andere Quellen – z. B. Redshift – nicht durchführbar. Stattdessen müsste eine SQL-Abfrage pro **Sales Manager** gesendet werden, bis zu einem bestimmten durchführbaren Grenzwert, bei dessen Überschreitung die Abfrage einen Fehler verursachen würde.

Jeder dieser Fälle bringt andere Folgen für die Leistung mit sich, wobei die jeweiligen Details je nach Datenquelle variieren können. Obwohl die Kardinalität der in der Beziehung verwendeten Spalten zur Verknüpfung der zwei Quellen weiterhin gering ausfällt (im vierstelligen Bereich), sollte die Leistung nicht beeinträchtigt werden. Mit zunehmender Kardinalität sollten Sie Ihre Aufmerksamkeit auf den Einfluss auf die resultierende Leistung richten.

Darüber hinaus hat die Verwendung von m:n-Beziehungen zur Folge, dass die Einzelwerte nicht lokal aggregiert werden, sondern dass für die einzelnen Ebenen der Gesamt- bzw. Zwischensumme separate Abfragen an die zugrunde liegende Quelle gesendet werden müssen. Ein einfaches Tabellenvisual mit Gesamtbeträgen würde anstelle von einer SQL-Abfrage zwei senden.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Bei diesem Release der zusammengesetzten Modelle gibt es einige Einschränkungen:

Derzeit wird die [inkrementelle Aktualisierung](service-premium-incremental-refresh.md) nur für zusammengesetzte Modelle unterstützt, die mit SQL-, Oracle- und Teradata-Datenquellen verbunden sind.

Die folgenden mehrdimensionalen Live Connect-Quellen können nicht mit zusammengesetzten Modellen verwendet werden:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-Datasets
* Azure Analysis Services

Wenn Sie mithilfe von DirectQuery eine Verbindung mit diesen mehrdimensionalen Quellen herstellen, können Sie weder eine Verbindung mit einer anderen DirectQuery-Quelle herstellen noch importierte Daten kombinieren.

Die bestehenden Einschränkungen für die Verwendung von DirectQuery gelten nach wie vor für die Verwendung des Features „Zusammengesetzte Modelle“. Viele dieser Einschränkungen gelten jetzt abhängig vom Speichermodus der Tabelle für eine einzelne Tabelle. Beispielsweise kann eine berechnete Spalte in einer importierten Tabelle auf andere Tabellen verweisen, wohingegen eine berechnete Spalte in einer DirectQuery-Tabelle nach wie vor nur auf Spalten in derselben Tabelle verweisen kann. Es gelten weitere Einschränkungen für das Modell als Ganzes, wenn eine der Tabellen im Modell DirectQuery enthält. Die Features QuickInsights und Q&A sind nicht für Modelle verfügbar, wenn eine der Tabellen den Speichermodus „DirectQuery“ aufweist.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu zusammengesetzten Modellen und DirectQuery finden Sie in den folgenden Artikeln:

* [Beziehungen mit einer m:n-Kardinalität in Power BI Desktop](desktop-many-to-many-relationships.md)
* [Speichermodus in Power BI Desktop](desktop-storage-mode.md)
* [Verwenden von DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery in Power BI unterstützte Datenquellen](desktop-directquery-data-sources.md)

