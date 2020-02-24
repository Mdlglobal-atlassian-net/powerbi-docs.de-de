---
title: Tipps zum Erstellen überzeugender Berichte
description: Tipps und Tricks zum Erstellen von Berichten in Power BI und Power BI Desktop
author: davidiseminger
ms.reviewer: willthom
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: davidi
LocalizationGroup: Reports
ms.openlocfilehash: d7f2c83cf1d0f29f2c0d0c6e621a253acdd3ce41
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860886"
---
# <a name="tips-and-tricks-for-creating-reports-in-power-bi-desktop-and-power-bi-service"></a>Tipps und Tricks zum Erstellen von Berichten in Power BI Desktop und im Power BI-Dienst
Um Ihre Daten optimal zu nutzen, benötigen Sie manchmal etwas zusätzliche Hilfe. Wir haben einige Tipps und Tricks zusammengestellt, die Sie nutzen können, wenn Sie Berichte in Microsoft Power BI Desktop, im Power BI-Dienst *und* in Microsoft Excel 2016 oder Excel 2013 Pro Plus-Editionen erstellen, wobei das Power Pivot-Add-In und Power Query installiert und aktiviert sein müssen.

## <a name="power-bi-desktop"></a>Power BI Desktop

### <a name="learning-to-use-the-query-editor"></a>Arbeiten mit dem Abfrage-Editor
Der Abfrage-Editor in Power BI Desktop hat eine vergleichbare Funktionalität wie das Power Query-Add-In in Excel 2013. Es gibt zwar einige hilfreiche Artikel in Power BI Support, es empfiehlt sich aber, für den Einstieg die Power Query-Dokumentation auf „support.office.com“ zu lesen.

Weitere Informationen finden Sie im [Power Query-Ressourcencenter](https://support.office.com/article/Microsoft-Power-Query-for-Excel-Help-2b433a85-ddfb-420b-9cda-fe0e60b82a94).

Sie können sich auch die [Formelreferenz](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f) ansehen.

### <a name="data-types-in-query-editor"></a>Datentypen im Abfrage-Editor
Wenn Sie den Abfrage-Editor in Power BI Desktop dazu verwenden, Daten zu laden, erfolgt eine Datentyperkennung nach bester Vermutung.  Bei Verwendung von Formeln kann es vorkommen, dass Datentypeinstellungen für Spalten nicht beibehalten werden. Sie sollten die Datentypen der Spalten auf Richtigkeit prüfen, nachdem Sie einen der folgenden Vorgänge ausgeführt haben:  Erstmaliges Laden von Daten auf die Registerkarte für Abfragen, Festlegen der ersten Zeile als Überschrift, Hinzufügen einer Spalte, Gruppieren nach, Zusammenführen, Anfügen. Dies gilt auch, bevor Sie bestätigen, dass die Daten erstmalig geladen werden sollen.

Ein zu beachtender wichtiger Punkt: Kursivformatierung im Datenraster bedeutet nicht, dass der Datentyp richtig festgelegt ist, sondern bedeutet nur, dass die Daten nicht als Text angesehen werden.

### <a name="reference-queries-in-the-query-editor"></a>Verweisabfragen im Abfrage-Editor
Wenn Sie im Navigator des Abfrage-Editors in Power BI Desktop mit der rechten Maustaste auf eine der Abfragen klicken, ist eine Option für „Reference“ (Verweis) verfügbar.  Dies ist aus folgendem Grund hilfreich:

* Wenn Sie Dateien als Datenquelle für eine Abfrage verwenden, wird der absolute Pfad zur Datei in der Abfrage gespeichert. Wenn Sie eine Power BI Desktop-Datei oder eine Excel-Arbeitsmappe freigeben oder verschieben, sparen Sie Zeit, wenn Sie die Pfade aktualisieren, indem Sie diese nur einmal statt jeweils einzeln aktualisieren.

Standardmäßig werden alle Abfragen entweder auf ein Excel-Arbeitsblatt oder in das Datenmodell (oder beides) geladen. Einige Abfragen sind zwischengeschaltete Schritte sind und nicht für Endbenutzer vorgesehen.  Dies ist häufig der Fall, wenn so, wie oben angegeben, auf Abfragen verwiesen wird.  Sie können das Ladeverhalten einer Abfrage steuern, indem Sie im Navigator mit der rechten Maustaste auf die Abfrage klicken und dann die Option „Laden aktivieren" umschalten.  Wenn kein Häkchen neben „Laden aktivieren“ angezeigt wird, ist die Abfrage weiterhin auf der Abfrageregisterkarte verfügbar, und Sie können sie mit anderen Abfragen verwenden.  Dies ist insbesondere in Verbindung mit Zusammenführungs-, Anfügungs- und Verweistransformationen nützlich.  Weil die Ergebnisse der Abfrage aber nicht in das Datenmodell geladen werden, führt die Abfrage nicht dazu, dass die Feldliste Ihres jeweiligen Berichts oder Ihr Datenmodell überladen wird.

### <a name="scatter-charts-need-a-point-identifier"></a>Punktdiagramme erfordern einen Punktbezeichner
Nehmen Sie als ein Beispiel eine einfache Tabelle, die Temperaturen sowie die Uhrzeiten enthält, zu denen die Messungen erfolgt sind. Wenn Sie diese Daten direkt in einem Punktdiagramm darstellen, aggregiert Power BI alle Werte zu einem einzigen Punkt. Damit einzelne Datenpunkte angezeigt werden, müssen Sie ein Feld zum „Details“-Bucket der Feldquelle hinzufügen.   Eine einfache Möglichkeit hierfür in Power BI Desktop ist, auf der Abfrageregisterkarte die Option „Indexspalte hinzufügen“ im Menüband „Spalte hinzufügen“ zu verwenden.

### <a name="reference-lines-in-your-report"></a>Bezugslinien in Ihrem Bericht
Sie können in Power BI Desktop eine berechnete Spalte verwenden, um eine Bezugslinie zu definieren.  Ermitteln Sie die Tabelle und die Spalte, für die Sie eine Bezugslinie erstellen möchten.  Wählen Sie „Neue Spalte“ im Menüband aus, und geben Sie in der Bearbeitungsleiste die folgende Formel ein:

    Target Value = 100

Diese berechnete Spalte gibt den Wert 100 zurück, unabhängig davon, wo sie verwendet wird.  Die neue Spalte wird in der Feldliste angezeigt.  Fügen Sie berechnete Spalte „Target Value“ zu einem Liniendiagramm hinzu, um darzustellen, wie sich die Datenreihen zu dieser bestimmten Bezugslinie verhalten.  

### <a name="sort-by-another-column"></a>Sortieren nach einer anderen Spalte
Wenn Sie einen Kategoriewert (eine Zeichenfolge) für Diagrammachsen in Power BI oder in einem Datenschnitt oder Filter verwenden, ist die Standardreihenfolge alphabetisch. Wenn Sie diese Reihenfolge außer Kraft setzen müssen, z. B. für Angaben wie Tage der Woche oder des Monats, können Sie Power BI Desktop anweisen, nach einer anderen Spalte zu sortieren. Weitere Informationen hierzu finden Sie unter [Sortieren nach Spalten in Power BI Desktop](desktop-sort-by-column.md).

### <a name="building-maps-more-easily-with-hints-to-bing"></a>Einfacheres Erstellen von Karten mit Hinweisen auf Bing
Power BI arbeitet mit Bing zusammen, um Standardkartenkoordinaten bereitzustellen (ein Prozess, der als Geocodierung bezeichnet wird), sodass Sie einfacher Karten erstellen können.  Bing verwendet einige Algorithmen und Hinweise, um zu versuchen, die richtige Ortsangabe zu ermitteln, dies ist aber eine bestmögliche Schätzung. Durch Beachten der folgenden Tipps können Sie die Wahrscheinlichkeit einer richtigen Geocodierung erhöhen:

Wenn Sie eine Karte erstellen, sollen häufig auch Länder (Staaten), Bundesländer (Bundesstaaten) und Städte darin dargestellt werden.  Wenn Sie Spalten in Power BI Desktop nach der geografischen Bezeichnung benennen, erkennt Bing leichter, was Sie anzeigen möchten. Wenn Sie beispielsweise ein Feld für Namen von US-Bundesstaaten wie „Kalifornien“ und „Washington“ haben, könnte Bing für das Wort „Washington“ den Standort Washington DC anstelle von Washington Bundesstaat zurückgeben.  Ein Benennen der Spalte „Bundesland“ verbessert das Geocoding.  Das gleiche gilt für Spalten namens „Land/Region“ und „Stadt“.   

Einige Bezeichnungen sind mehrdeutig, wenn sie im Kontext mehrerer Länder/Regionen berücksichtigt werden.  In einigen Fällen wird das, was in einem Land bzw. in einer Region als „Staat“ bezeichnet wird, als ein „Bundesland“ oder ein „Landkreis“ oder eine andere Bezeichnung behandelt.  Sie können die Genauigkeit der Geocodierung erhöhen, indem Sie Spalten erstellen, in denen mehrere Felder zusammengefügt sind, und dann diese Spalten dazu verwenden, Datenortsangaben zu zeichnen.  Ein Beispiel: Statt nur „Wiltshire“ zu übergeben, können Sie „Wiltshire, England“ übergeben, um ein genauere Geocodierungsergebnis zu erhalten.

Sie können in Power BI oder Power BI Desktop immer bestimmte Breiten- und Längengrade für Ortsangaben bereitstellen.  In diesem Fall müssen Sie auch ein „Ortsangabe“-Feld übergeben, denn andernfalls werden die Daten standardmäßig aggregiert, sodass die Ortsangabe aus Breiten- und Längengrad möglicherweise nicht dem entspricht, was Sie erwartet haben.

### <a name="categorizing-geographic-fields-to-hint-bings-geocoding"></a>Kategorisieren von geografischen Feldern als Hinweise für Bings Geocodierung
Sie können die korrekte Geocodierung der Felder auch sicherstellen, indem Sie die Datenkategorie der Datenfelder festlegen.   Wählen Sie in Power BI Desktop die gewünschte Tabelle aus, wechseln Sie zum Menüband „Erweitert“, und legen Sie dann die „Datenkategorie“ auf „Adresse“, „Ort“, „Kontinent“, „Land/Region“, „Landkreis“, „Postleitzahl“ oder „Bundesland oder Kanton“ fest.  Mithilfe dieser Datenkategorien können Daten von Bing richtig codiert werden. Weitere Informationen finden Sie unter [Datenkategorisierung in Power BI Desktop](desktop-data-categorization.md).

### <a name="better-geocoding-with-more-specific-locations"></a>Besseres Geocoding mit spezielleren Ortsangaben
Manchmal genügt es aber nicht, die Datenkategorien für die Zuordnung festzulegen.  Mit dem Abfrage-Editor in Power BI Desktop können Sie eine speziellere Ortsangabe erstellen, etwa eine Straße mit Hausnummer.  Verwenden Sie die Funktion „Spalte hinzufügen“, um eine benutzerdefinierte Spalte zu erstellen.  Erstellen Sie die gewünschte Ortsangabe dann wie folgt:

    = [Field1] & " " & [Field2]

Verwenden Sie dieses resultierende Feld anschließend in den Kartenvisualisierungen. Dies ist sehr nützlich für das Erstellen von Adressen (Straße und Hausnummer) aus Versandadressfeldern, die in Datasets üblich sind.  Zu beachten ist, dass die Verkettung nur mit Textfeldern funktioniert.  Gegebenenfalls konvertieren Sie die Hausnummer in einen Text-Datentyp, bevor Sie sie dazu verwenden, eine Adresse zu erstellen.

### <a name="histograms-in-the-query-stage"></a>Histogramme in der Abfragephase
Es gibt in Power BI Desktop verschiedene Möglichkeiten zum Erstellen von Histogrammen. Hier wird mit der einfachsten begonnen:

Einfachstes Histogramm - Bestimmen Sie, welche Abfrage das Feld hat, für das Sie ein Histogramm erstellen möchten.  Verwenden Sie die Option „Verweis“ für die Abfrage, um eine neue Abfrage zu erstellen, und geben Sie dieser den Namen „FieldName-Histogramm“. Verwenden Sie die Option „Gruppieren nach“ im Menüband „Transformieren“, und wählen Sie das Aggregat „Zeilen zählen“ aus.  Achten Sie darauf, dass die resultierende Aggregatspalte eine Zahl als Datentyp hat. Visualisieren Sie diese Daten dann auf der Berichtsseite.  Dies ist schnell und einfach zu erstellen, funktioniert aber nicht brauchbar, wenn Sie viele Datenpunkte haben, und ermöglicht kein Brushing über visuelle Objekte hinweg.

Definieren von Buckets, um ein Histogramm zu erstellen - Bestimmen Sie, welche Abfrage das Feld hat, für das Sie ein Histogramm erstellen möchten.  Verwenden Sie die Option „Verweis“ für die Abfrage, um eine neue Abfrage zu erstellen, und geben Sie dieser den Namen „FieldName“.  Nun definieren Sie die Buckets mit einer Regel.  Verwenden Sie die Option „Benutzerdefinierte Spalte hinzufügen“ im Menüband „Spalte hinzufügen“, und erstellen Sie eine benutzerdefinierte Regel.  Eine einfache Regel zur Erstellung von Buckets könnte folgendermaßen aussehen:

    if([FieldName] \< 2) then "\<2 min" else
    if([FieldName] \< 5) then "\<5 min" else
    if([FieldName] \< 10) then "\<10 min" else
    if([FieldName] \< 30) then "\<30 min" else
    "longer")

Achten Sie darauf, dass die resultierende Aggregatspalte eine Zahl als Datentyp hat. Jetzt können die in „Einfachstes Histogramm“ beschriebene „Gruppieren nach“-Vorgehensweise verwenden, um das Histogramm zu realisieren.  Bei dieser Option werden mehr Datenpunkte verarbeitet, aber auch sie ermöglicht kein Brushing.

Definieren eines Histogramms, das Brushing unterstützt – Brushing liegt vor, wenn visuelle Elemente miteinander verknüpft sind, sodass, nachdem ein Benutzer einen Datenpunkt in einem visuellen Element ausgewählt hat, in anderen visuellen Elementen auf der Berichtsseite Datenpunkte hervorgehoben oder gefiltert werden, die mit dem ausgewählten Datenpunkt verknüpft sind.  Da Daten zur Abfragezeit verarbeitet werden, müssen Sie eine Beziehung zwischen Tabellen erstellen und sicher sein, dass Sie wissen, welches Detailelement mit dem Bucket im Histogramm verknüpft ist und umgekehrt.

Beginnen Sie den Vorgang, indem Sie die Option „Verweis“ für die Abfrage verwenden, die das Feld umfasst, für das Sie ein Histogramm erstellen möchten.  Geben Sie der neuen Abfrage den Namen „Buckets“.  Für dieses Beispiel soll die ursprüngliche Abfrage den Namen „Details“ haben.  Entfernen Sie als Nächstes alle Spalten außer der Spalte, die Sie als Bucket für das Histogramm verwenden möchten.  Verwenden Sie nun die Funktion „Duplikate entfernen“ in der Abfrage (diese Funktion wird im Kontextmenü angezeigt, wenn Sie die Spalte auswählen), damit die verbleibenden Werte die eindeutigen Werte in der Spalte sind.   Wenn Sie Dezimalzahlen haben, können Sie zunächst den Tipp zum Definieren von Buckets verwenden, um ein Histogramm zu erstellen, damit Sie eine verwaltbare Anzahl von Buckets erhalten.  Prüfen Sie jetzt die Daten, die in der Abfragevorschau angezeigt werden.  Wenn Sie leere Werte oder Nullwerte sehen, müssen Sie diese korrigieren, bevor Sie eine Beziehung erstellen.  Weitere Informationen finden Sie unter „Erstellen einer Beziehung, wenn die Daten Null- oder leere Werte haben“.   Dieser Ansatz kann problematisch sein, weil sortiert werden muss.  Informationen zur richtigen Sortierung der Buckets finden Sie unter „Sortierreihenfolge: Kategorien in der gewünschten Reihenfolge anzeigen“.  

>[!NOTE]
>Sie sollten sich die Sortierreihenfolge überlegt haben, bevor Sie Visuals erstellen.   

Der nächste Schritt in der Vorgehensweise besteht darin, eine Beziehung zwischen den Abfragen „Buckets“ und „Details“ über die Bucketspalte zu definieren.  Klicken Sie in Power BI Desktop auf **Beziehungen verwalten** im Menüband.  Erstellen Sie eine Beziehung, in der sich „Buckets“ in der linken Tabelle und „Details“ in der rechten Tabelle befindet, und wählen Sie das Feld aus, das Sie für das Histogramm verwenden.

Der letzte Schritt ist die Erstellung des Histogramms.  Ziehen Sie das Bucketfeld aus der Tabelle „Buckets“.  Entfernen Sie das Standardfeld aus dem resultierenden Säulendiagramm.  Ziehen Sie nun das Histogrammfeld aus der Tabelle „Details“ in dasselbe visuelle Objekt.  Ändern Sie in der Feldquelle das Standardaggregat in „Anzahl“.  Das Ergebnis ist das Histogramm. Wenn Sie ein weiteres visuelles Objekt erstellen, etwa ein Treemap-Diagramm aus der Tabelle „Details“, wählen Sie einen Datenpunkt in der Treemap aus, um die Histogrammhervorhebung und das Histogramm für den ausgewählten Datenpunkt in Bezug auf den Trend für das gesamte Dataset anzuzeigen.

### <a name="histograms"></a>Histogramme
In Power BI Desktop können Sie ein berechnetes Feld verwenden, um ein Histogramm zu definieren.  Ermitteln Sie die Tabelle und die Spalte, für die Sie ein Histogramm erstellen möchten.  Geben Sie im Berechnungsbereich die folgende Formel ein:

> Frequency:=COUNTROWS(\<Spaltenname\>)
>
>

Speichern Sie Ihre Änderungen, und kehren Sie zu Ihrm Bericht zurück.  Fügen Sie \<Spaltenname\> und den Frequency-Wert (Häufigkeit) einer Tabelle hinzu, und konvertieren Sie die Werte in ein Balkendiagramm.  Achten Sie darauf, dass \<Spaltenname\> die x-Achse und das berechnete Frequency-Feld (Häufigkeit) die y-Achse bildet.

### <a name="tips-and-tricks-for-creating-relationships-in-power-bi-desktop"></a>Tipps und Tricks zum Erstellen einer Beziehung in Power BI Desktop
Wenn Sie Detaildatasets aus mehreren Quellen laden, verhindern Probleme wie Nullwerte, leere Werte oder doppelte Werte häufig, dass Sie Beziehungen erstellen können.

Betrachten wir dazu ein Beispiel:

Sie laden Datasets mit aktiven Kundensupportanfragen und ein anderes Dataset mit Arbeitselementen, die folgende Schemas aufweisen:

> Kundenereignisse: {EreignisID, Kundenname, Problemname, ErfasstDatum, Status} Arbeitsaufgaben: {ArbeitsaufgabeID, EreignisID, ArbeitsaufgabeName, ErfasstDatum, Status, Kundenname}
>
>

Wenn alle Ereignisse und Arbeitsaufgaben überwacht werden sollen, die zu einem bestimmten Kundennamen gehören, genügt es nicht, einfach eine Beziehung zwischen diesen beiden Datasets zu erstellen.  Einige Arbeitsaufgaben sind möglicherweise keinem Kundennamen zugeordnet, sodass das Feld „Kundenname“ leer oder gleich NULL ist.  Es gibt möglicherweise mehrere Datensätze in „Arbeitsaufgaben“ und „Kundenereignisse“ für einen Namen in „Kundenname“.  

#### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-null-or-blank-values"></a>Erstellen von Beziehungen in Power BI Desktop, wenn Daten über NULL- oder leere Werte verfügen
Häufig enthalten Datasets Spalten mit Null- oder leeren Werten.  Dies kann Probleme verursachen, wenn versucht wird, Beziehungen zu verwenden.  Sie haben grundsätzlich zwei Optionen zum Reagieren auf die Probleme.  Sie können die Zeilen entfernen, die Null- oder leere Werte enthalten.  Sie können dazu entweder die Filterfunktion auf der Abfrageregisterkarte oder, wenn Sie Abfragen zusammenführen, die Option „Nur übereinstimmende Zeilen beibehalten“ verwenden. Alternativ können Sie die Null- oder leeren Werte durch Werte ersetzen, die in Beziehungen funktionieren, in der Regel Zeichenfolgen wie „NULL“ und „(leer)“.   Es gibt hier keinen richtigen Ansatz - ein Herausfiltern in der Abfragephase bewirkt ein Entfernen von Zeilen, kann sich aber auf Übersichtsstatistiken und -berechnungen auswirken.  Der zweite Ansatz bewirkt, dass Datenzeilen erhalten bleiben, kann jedoch dazu führen, dass nicht verknüpfte Zeilen im Modell als verknüpft erscheinen, wodurch sich Fehlberechnungen ergeben.  Wenn Sie die zweite Lösung umsetzen, müssen in der Ansicht/im Diagramm geeignete Filter verwenden, damit sichergestellt ist, dass Sie genaue Ergebnisse erzielen.  Am wichtigsten ist, dass Sie ermitteln, welche Zeilen beibehalten/entfernt werden, und dass Sie die Auswirkungen auf die Analyse erkennen.  

#### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-duplicate-values"></a>Erstellen von Beziehungen in Power BI Desktop, wenn Daten über doppelte Werte verfügen
Wenn Sie detaillierte Datasets aus mehreren Quellen laden, verhindern häufig doppelte Datenwerte, dass Sie eine Beziehung erstellen können.  Dies lässt sich umgehen, indem Sie eine Dimensionstabelle mit eindeutigen Werte aus beiden Datasets erstellen.

Betrachten wir dazu ein Beispiel:

Sie laden Datasets mit aktiven Kundensupportanfragen und ein anderes Dataset mit Arbeitselementen, die folgende Schemas aufweisen:

> Kundenereignisse: {EreignisID, Kundenname, Problemname, ErfasstDatum, Status} Arbeitsaufgaben: {ArbeitsaufgabeID, EreignisID, ArbeitsaufgabeName, ErfasstDatum, Status, Kundenname}
>
>

Wenn alle Ereignisse und Arbeitsaufgaben überwacht werden sollen, die zu einem bestimmten Kundennamen gehören, genügt es nicht, einfach eine Beziehung zwischen diesen beiden Datasets zu erstellen.  Einige Arbeitsaufgaben sind möglicherweise keinem Kundennamen zugeordnet, sodass das Feld „Kundenname“ leer oder gleich NULL ist.  Wenn die Tabelle mit den Kundennamen leere Werte oder Nullwerte enthält, können Sie möglicherweise immer noch keine Beziehung erstellen (siehe „Erstellen einer Beziehung, wenn die Daten Null- oder leere Werte haben“).  Es gibt möglicherweise mehrere „Arbeitsaufgaben“ und „Kundenereignisse“ für einen einzelnen Namen in „Kundenname“.  

Um in diesem Fall eine Beziehung zu erstellen, muss ein logisches Dataset aller Kundennamen über die beiden Datasets erstellt werden.  Führen Sie auf der Abfrageregisterkarte die folgenden Schritte aus, um das logische Dataset zu erstellen:

1. Duplizieren Sie beide Abfragen, und geben Sie die ersten den Namen **Temp** und der zweiten den Namen **Kundennamen**.
2. Entfernen Sie in jeder Abfrage alle Spalten *außer* der Spalte „Kundenname“.
3. Verwenden Sie in jeder Abfrage den Befehl  **Duplikate entfernen**.
4. Wählen Sie in der Abfrage **Kundennamen** die Option **Anfügen** im Menüband aus, und wählen Sie die Abfrage **Temp**aus.
5. Wählen Sie in der Abfrage **Kundennamen** den Befehl **Duplikate entfernen**.

Sie haben nun eine Dimensionstabelle, die Sie dazu verwenden können, Beziehungen zu „Kundenereignisse“ und „Arbeitsaufgaben“ zu erstellen, und die alle Werte von beiden enthält.  

### <a name="patterns-to-jump-start-your-use-of-the-query-editor"></a>Muster für den Schnelleinstieg in den Abfrage-Editor
Der Abfrage-Editor ist sehr leistungsfähig hinsichtlich des Bearbeitens von Daten, um diese zu formen und zu bereinigen, sodass sie visualisiert oder modelliert werden können. Es gibt einige Muster, die Sie beachten sollten.

#### <a name="temporary-columns-can-be-deleted-after-computing-a-result"></a>Temporäre Spalten können gelöscht werden, nachdem ein Ergebnis berechnet ist
Häufig müssen Sie in Power BI Desktop eine Berechnung erstellen, in der Daten aus mehreren Spalten in eine einzige neue Spalte transformiert werden.  Dies kann komplex sein.  Eine einfache Möglichkeit, das Problem zu umgehen, besteht darin, den Vorgang in Schritte zu zerlegen.  Beginnen Sie, indem Sie die ursprünglichen Spalten duplizieren. Erstellen Sie danach temporäre Spalten. Erstellen Sie daran anschließend eine Spalte für das Endergebnis.  Nun können Sie die temporären Spalten löschen, damit das resultierende Dataset nicht überladen ist. Dies ist möglich, weil Schritte auf der Abfrageregisterkarte der Reihe nach ausgeführt wird.

#### <a name="duplicate-or-reference-queries-followed-by-merge-to-original-query"></a>Duplizieren der oder Verweisen auf die Abfragen, dann Zusammenführen mit der ursprünglichen Abfrage
Manchmal sollen Übersichtsstatistiken für ein Dataset berechnet werden.  Die einfache Möglichkeit hierzu ist, die Abfrage auf der Abfrageregisterkarte zu duplizieren oder dort auf diese Abfrage zu verweisen. Danach verwenden Sie **Gruppieren nach** , um die Übersichtsstatistiken zu berechnen.  Übersichtsstatistiken versetzen Sie in die Lage, die ursprünglichen Daten zu normalisieren, sodass sie besser vergleichbar sind als im ursprünglichen Zustand.  Dies ist besonders nützlich für ein Vergleichen von einzelnen Werten mit allen Werten.  Wechseln Sie dazu zur ursprüngliche Abfrage, und wählen Sie die Option für Zusammenführen aus.  Führen Sie dann die Daten aus der Übersichtsstatistikabfrage zusammen, die mit den entsprechenden Bezeichnern übereinstimmen.  Nun können Sie die Daten nach Bedarf für Ihre Analyse zu normalisieren.

### <a name="using-dax-for-the-first-time"></a>Erstmaliges Verwenden von DAX
DAX ist die Formelsprache für Berechnungen in Power BI Desktop.  Sie ist für Business Intelligence (BI) optimiert.  Sie unterscheidet sich ein wenig von dem, mit dem Sie möglicherweise vertraut sind, wenn Sie nur eine SQL-orientierte Abfragesprache verwendet haben. Sowohl online als auch in Buchform gibt es sehr gute Ressourcen zum Erlernen von DAX.

[Erlernen der DAX-Grundlagen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md)

[DAX-Referenz (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx)

[DAX-Ressourcencenter](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx)

## <a name="power-bi-service-and-power-bi-desktop"></a>Power BI-Dienst *und* Power BI Desktop

### <a name="read-andor-watch-how-to-design-visually-stunning-reports-and-dashboards-in-power-bi"></a>Erfahren Sie mehr unter „Erstellen visuell ansprechender Berichte (und Dashboards) in Power BI“.
Community-Mitglied Miguel Myers ist sowohl Datenanalysten als auch Grafikdesigner.

![](media/power-bi-reports-tips-and-tricks-for-creating/power-bi-reports.png)

* [Blogbeitrag lesen](https://powerbi.microsoft.com/blog/how-to-design-visually-stunning-reports/)
* [Webinar ansehen](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-04Apr-19-Design-Reports-in-PowerBI-Registration.html)

### <a name="consider-your-audience"></a>Zielgruppe berücksichtigen
Wie lauten die wichtigsten Kennzahlen, um Entscheidungen zu treffen? Wozu wird der Bericht verwendet? Welche erlernten oder kulturellen Annahmen wirken sich möglicherweise auf die Gestaltung aus? Welche Informationen benötigt Ihre Zielgruppe, um erfolgreich zu sein?

Wo wird der Bericht angezeigt? Wird es auf einem großen Monitor angezeigt, können Sie mehr Inhalt einfügen. Wird er von Lesern auf Tablets angezeigt, ist er mit weniger Visualisierungen besser lesbar.

### <a name="tell-a-story-and-keep-it-to-one-screen"></a>Alle Informationen auf einen Blick
Jede Berichtsseite sollte einen Gesamtüberblick bieten. Können Sie Scrollleisten auf Ihren Seiten vermeiden? Ist der Bericht zu überladen oder überfrachtet?  Entfernen Sie alles bis auf die wesentlichen Informationen, die leicht gelesen und interpretiert werden können.

### <a name="make-the-most-important-information-biggest"></a>Die wichtigsten Informationen in der größten Schrift anzeigen
Wenn die Texte und Visualisierungen auf Ihrer Berichtsseite alle gleich groß sind, haben die Leser Schwierigkeiten, sich auf das Wesentliche zu konzentrieren. So sind z. B. Kartenvisualisierungen eine gute Möglichkeit, wichtige Informationen anschaulich zu präsentieren:  
![Kartenvisualisierung](media/service-dashboards-design-tips/pbi_card.png)

### <a name="but-be-sure-to-provide-context"></a>Stellen Sie unbedingt Kontext bereit  

Verwenden Sie Features wie z.B. Textfelder und QuickInfos, um den Visualisierungen Kontext hinzufügen.

### <a name="put-the-most-important-information-in-the-upper-corner"></a>Die wichtigsten Informationen in der oberen Ecke platzieren
Die meisten Personen lesen von oben nach unten. Daher sollten die wichtigsten Details oben angezeigt werden und weitere Einzelheiten in der Leserichtung Ihrer Zielgruppe eingefügt werden (von links nach rechts, von rechts nach links)

### <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>Die richtigen Visualisierungen für die Daten verwenden und diese in ein übersichtliches Format bringen
Vermeiden Sie zahlreiche Visualisierungen auf Kosten der Vielfalt.  Visualisierungen sollten ein Bild vermitteln und leicht zu „lesen“ und interpretieren sein.  Für einige Daten und Visualisierungen reicht eine einfache grafische Visualisierung aus. Möglicherweise erfordern andere Daten eine komplexere Visualisierung – verwenden Sie Titel und Beschriftungen sowie andere Anpassungen, um das Lesen zu erleichtern.  

* Seien Sie vorsichtig mit Diagrammen, die die Realität verzerren, wie z.B. 3D-Diagramme und Diagramme, die nicht bei Null beginnen. Bedenken Sie, dass das Interpretieren bestimmter Kreisformen für das menschliche Gehirn schwieriger ist. Kreisdiagramme, Ringdiagramme, Messgerätdiagramme und andere Arten von kreisförmigen Diagrammen mögen nett aussehen, sollten jedoch möglicherweise durch andere visuelle Elemente ersetzt werden.    
* Achten Sie auf Einheitlichkeit bei den Diagrammskalen auf Achsen, der Reihenfolge der Diagrammdimensionen und den Farben der Dimensionswerte in Diagrammen.    
* Stellen Sie sicher, dass quantitative Daten ansprechend verschlüsselt sind. Zeigen Sie in Telefonnummern maximal drei oder vier Ziffern am Stück an. Runden Sie Maßangaben auf eine oder zwei Stellen nach dem Dezimalkomma und unterteilen Sie Tausender oder Millionen, d. h. 3,4 Millionen anstatt 3.400.000.    
* Achten Sie möglichst auf eine Trennung von Genauigkeit und Zeit. Sorgen Sie für verständliche Zeitangaben.  Zeigen Sie ein Diagramm vom letzten Monat nicht neben gefilterten Diagrammen von einem bestimmten Monat an.    
* Wechseln Sie auf einer Skala, wie etwa auf einem Linien- oder Balkendiagramm, nicht zwischen großen und kleinen Maßeinheiten.  Beispiel: Eine Maßeinheit wird in Millionen, die andere in Tausenden angegeben.  Hier wäre es schwierig, die Differenz der Maßeinheit in Millionen und der Maßeinheit in Tausenden zu ermitteln.  Müssen Sie beide angeben, wählen Sie eine Visualisierung, bei der eine zweite Achse möglich ist, wie z.B. ein Kombinationsdiagramm.    
* Überladen Sie Ihre Diagramme nicht mit unnötigen Datenbeschriftungen. Werte in Balkendiagrammen sind in der Regel, ***wenn sie groß genug sind***, auch ohne Anzeige der tatsächlichen Zahl gut verständlich.   
* Achten Sie darauf, wie die [Diagramme sortiert werden](consumer/end-user-change-sort.md).  Wenn Sie den höchsten oder niedrigsten Wert hervorheben möchten, sortieren Sie nach der Maßeinheit.  Sollen Benutzer eine bestimmte Kategorie in vielen anderen Kategorien schnell finden können, sortieren Sie nach der Achse.  
* Kreisdiagramme sind mit weniger als acht Kategorien am übersichtlichsten. Da Sie Werte nicht nebeneinander vergleichen können, sind Werte in einem Kreisdiagramm schwieriger zu vergleichen als in Balken- und Säulendiagrammen. Kreisdiagramme eignen sich besser zum Anzeigen von Teil-Ganzes-Beziehungen als zum Vergleichen der Teile. Und Messgerätdiagramme eignen sich ideal, um den aktuellen Status im Kontext eines Ziels anzuzeigen.    

Weitere Informationen zur Visualisierung finden Sie unter [Visualisierungstypen in Power BI](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

### <a name="learn-more-about-best-practice-dashboard-design"></a>Weitere Informationen zu Best Practices bei der Gestaltung von Dashboards
Zu unseren Lieblingsbüchern (in englischer Sprache) zählen:

* *Storytelling with Data* von Cole Nussbaumer Knafic
* *Data points* von Nathan Yau
* *The truthful Art* von Alberto Cairo
* *Now You See It* von Stephen Few  
* *Envisioning Information* von Edward Tufte  
* *Advanced Presentations Design* von Andrew Abela   

## <a name="next-steps"></a>Nächste Schritte
[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

[Berichte in Power BI](consumer/end-user-reports.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
