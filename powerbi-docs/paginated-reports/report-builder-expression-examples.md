---
title: Beispiele für Ausdrücke im Power BI-Berichts-Generator
description: Ausdrücke werden in paginierten Berichten im Power BI Report Builder häufig verwendet, um den Inhalt und die Darstellung der Berichte zu steuern.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921146"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Beispiele für Ausdrücke im Power BI-Berichts-Generator
Ausdrücke werden in paginierten Berichten im Power BI Report Builder häufig verwendet, um den Inhalt und die Darstellung der Berichte zu steuern. Ausdrücke werden in Microsoft Visual Basic geschrieben und können integrierte Funktionen, benutzerdefinierten Code, Berichts- und Gruppenvariablen sowie benutzerdefinierte Variablen verwenden. Ausdrücke beginnen mit einem Gleichheitszeichen (=).   

Dieses Thema enthält Beispiele für Ausdrücke, die für allgemeine Aufgaben in einem Bericht verwendet werden können.  
  
-   [Visual Basic-Funktionen](#VisualBasicFunctions) Beispiele für Datum, Zeichenfolge, Konvertierung und bedingte Visual Basic-Funktionen.  
  
-   [Berichtsfunktionen](#ReportFunctions) Beispiele für Aggregate und andere integrierte Berichtsfunktionen.  
  
-   [Darstellung von Berichtsdaten](#AppearanceofReportData) Beispiele zum Ändern der Darstellung eines Berichts.  
  
-   [Eigenschaften](#Properties) Beispiele zum Festlegen von Berichtselementeigenschaften, um das Format oder die Sichtbarkeit zu steuern.  
  
-   [Parameter](#Parameters) Beispiele zum Verwenden von Parametern in einem Ausdruck.  
  
-   [Benutzerdefinierter Code](#CustomCode) Beispiele für eingebetteten benutzerdefinierten Code.  
  
Weitere Informationen über einfache und komplexe Ausdrücke, über die Anwendungsbereiche der Ausdrücke, und die Arten von Verweisen, die Sie in einen Ausdruck aufnehmen können, finden Sie in den Themen unter [Ausdrücken in Power BI-Berichts-Generator](report-builder-expressions.md). 
  
## <a name="functions"></a>Funktionen  
 Viele Ausdrücke in einem Bericht enthalten Funktionen. Sie können Daten formatieren, Logik anwenden und mit diesen Funktionen auf Berichtsmetadaten zugreifen. Sie können Ausdrücke schreiben, die Funktionen aus der Microsoft Visual Basic-Laufzeitbibliothek sowie aus den Namespaces `xref:System.Convert` und `xref:System.Math` verwenden. Sie können Verweise auf Funktionen in benutzerdefiniertem Code hinzufügen. Sie können auch Klassen aus Microsoft .NET Framework verwenden, wie z.B. `xref:System.Text.RegularExpressions`.  
  
##  <a name="VisualBasicFunctions"></a> Visual Basic-Funktionen  
 Mit Visual Basic-Funktionen können Sie die Daten bearbeiten, die in Textfeldern angezeigt werden, oder die für Parameter, Eigenschaften oder andere Bereichen des Berichts verwendet werden. Dieser Abschnitt enthält Beispiele zur Veranschaulichung einiger dieser Funktionen. Weitere Informationen finden Sie unter [Member der Visual Basic-Laufzeitbibliothek](https://go.microsoft.com/fwlink/?LinkId=198941) auf MSDN.  
  
 Das .NET Framework bietet viele benutzerdefinierte Formatoptionen, z.B. für bestimmte Datumsformate. Weitere Informationen finden Sie unter [Formatierung von Typen](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Mathematische Funktionen  
  
-   Mit der Funktion **Round** können Sie Zahlen auf die nächste ganze Zahl runden. Der folgende Ausdruck rundet 1,3 auf 1 ab:  
  
    ```  
    = Round(1.3)  
    ```  
  
     Sie können auch einen Ausdruck schreiben, um einen Wert auf ein von Ihnen angegebenes Vielfaches zu runden (vergleichbar mit der Funktion **MRund** in Excel). Multiplizieren Sie den Wert mit einem Faktor, der eine ganze Zahl erstellt, runden Sie die Zahl, und teilen Sie sie dann durch den gleichen Faktor. Um beispielsweise 1,3 auf das nächste Vielfache von 0,2 (1,4) zu runden, verwenden Sie den folgenden Ausdruck:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="DateFunctions"></a> Datumsfunktionen  
  
-   Die Funktion **Today** stellt das aktuelle Datum bereit. Dieser Ausdruck kann in einem Textfeld verwendet werden, um das Datum im Bericht anzuzeigen, oder in einem Parameter, um Daten nach dem aktuellen Datum zu filtern.  
  
    ```  
    =Today()  
    ```  
  
-   Verwenden Sie die Funktion **DateInterval** um einen bestimmten Teil eines Datums abzurufen. Hier sind einige gültige **DateInterval**-Parameter:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Dieser Ausdruck zeigt beispielsweise die Wochenzahl im aktuellen Jahr für das heutige Datum an:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   Mit der Funktion **DateAdd** wird ein Datumsbereich basierend auf einem einzigen Parameter bereitgestellt. Der folgende Ausdruck liefert ein Datum, das sechs Monate nach dem Datum eines Parameters mit der Bezeichnung *StartDate* liegt.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   Die Funktion **Year** zeigt das Jahr für ein bestimmtes Datum an. Hiermit können Sie Datumsangaben zusammenfassen oder die Jahreszahl für eine Datumsgruppe anzeigen. Dieser Ausdruck gibt das Jahr für eine bestimmte Gruppe von Bestelldaten an. Die Funktion **Month** und andere Funktionen können ebenfalls zum Bearbeiten von Daten verwendet werden. Weitere Informationen finden Sie in der Visual Basic-Dokumentation.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Sie können Funktionen in einem Ausdruck auch miteinander kombinieren, um das Format anzupassen. Der folgende Ausdruck ändert das Format eines Datums in der Form „Monat-Tag-Jahr“ in „Monat-Woche-Wochenzahl“. Zum Beispiel vom „12/23/2009“ in „Dezember Woche 3“:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Wenn Sie diesen Ausdruck als berechnetes Feld in einem Dataset verwenden, können Sie in einem Diagramm Werte pro Woche innerhalb eines jeden Monats aggregieren.  
  
-   Der folgende Ausdruck formatiert den Wert „SellStartDate“ als „MMM-YY“. Das Feld „SellStartDate“ hat den Datentyp „datetime“.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   Der folgende Ausdruck formatiert den Wert „SellStartDate“ als „dd/MM/yyyy“. Das Feld „SellStartDate“ hat den Datentyp „datetime“.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   Die Funktion **CDate** konvertiert den Wert in ein Datum. Die Funktion **Now** gibt einen Datumswert zurück, der das aktuelle Datum und die aktuelle Uhrzeit laut Ihrem System enthält. **DateDiff** gibt einen Long-Wert zurück, der die Anzahl der Zeitintervalle zwischen zwei Datumswerten angibt.  
  
     Das folgende Beispiel zeigt das Startdatum des aktuellen Jahres an.  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   Im folgende Beispiel wird das Startdatum des vorherigen Monats basierend auf dem aktuellen Monat angezeigt.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   Der folgende Ausdruck generiert die Jahre des Intervalls zwischen „SellStartDate“ und „LastReceiptDate“. Diese Felder sind in zwei unterschiedlichen Datasets enthalten, „DataSet1“ und „DataSet2“.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   Die Funktion **DatePart** gibt einen ganzzahligen Wert zurück, der die angegebene Komponente eines gegebenen Datumswertes enthält. Der folgende Ausdruck gibt das Jahr für den ersten Wert für „SellStartDate“ im „DataSet1“ zurück. Der Datasetbereich ist angegeben, da mehrere Datasets im Bericht enthalten sind.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   Die Funktion **DateSerial** gibt einen Datumswert zurück, der ein bestimmtes Jahr, einen bestimmten Monat und Tag darstellt, wobei die Zeitinformation auf Mitternacht gesetzt ist. Im folgende Beispiel wird das Enddatum des vorherigen Monats basierend auf dem aktuellen Monat angezeigt.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Die folgenden Ausdrücke zeigen verschiedene Daten basierend auf einem vom Benutzer ausgewählten Datumsparameterwert an.  
  
|Beispielbeschreibung|Beispiel|  
|-------------------------|-------------|  
|Yesterday|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Vor zwei Tagen|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Vor einem Monat|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Vor zwei Monaten|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Vor einem Jahr|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Vor zwei Jahren|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="StringFunctions"></a> Zeichenfolgenfunktion  
  
-   Kombinieren Sie mehr als ein Feld, indem Sie Verkettungsoperatoren und Visual Basic-Konstanten verwenden. Der folgende Ausdruck gibt zwei Felder in jeweils einer separaten Zeile im gleichen Textfeld zurück:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Mit der Funktion **Format** können Sie Daten und Zahlen in einer Zeichenfolge formatieren. Der folgende Ausdruck zeigt die Werte der Parameter *StartDate* und *EndDate* im langen Datumsformat an:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Wenn das Textfeld nur ein Datum oder eine Zahl enthält, sollten Sie die Eigenschaft „Format“ des Textfelds verwenden, um die Formatierung anstelle der Funktion **Format** innerhalb des Textfelds anzuwenden.  
  
-   Mit den Funktionen **Right**, **Len** und **InStr** kann eine Teilzeichenfolge zurückgegeben werden, z.B. wird *DOMAIN*\\*username* auf „username“ verkürzt. Der folgende Ausdruck gibt den Teil der Zeichenfolge rechts neben einem umgekehrten Schrägstrich (\\) aus einem Parameter namens *User* zurück:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     Der folgende Ausdruck ergibt den gleichen Wert wie der vorherige, wobei Elemente der `xref:System.String`-Klasse von .NET Framework anstelle von Visual Basic-Funktionen verwendet werden:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Sie können die ausgewählten Werte aus einem mehrwertigen Parameter anzeigen. Das folgende Beispiel verwendet die Funktion **Join**, um die ausgewählten Werte des Parameters *MySelection* zu einer einzelnen Zeichenfolge zu verketten, die als Ausdruck für den Wert eines Textfeldes in einem Berichtselement festgelegt werden kann:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     Das folgende Beispiel ergibt das gleiche Ergebnis wie das obige Beispiel, und zeigt zudem eine Textzeichenfolge vor der Liste der ausgewählten Werte an.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   Die Funktionen **Regex** aus dem .NET Framework `xref:System.Text.RegularExpressions` sind hilfreich, um das Format bestehender Zeichenfolgen zu ändern, z.B. um eine Telefonnummer zu formatieren. Der folgende Ausdruck verwendet die Funktion **Replace**, um das Format einer zehnstelligen Telefonnummer in einem Feld von „*nnn*-*nnn*-*nnnnnn*“ in „(*nnn*) *nn*-*nnnn*“ zu ändern:  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Vergewissern Sie sich, dass der Wert für „Fields!Phone.Value“ keine zusätzlichen Leerzeichen enthält und vom Typ `xref:System.String` ist.  
  
### <a name="lookup"></a>Lookup  
  
-   Durch die Angabe eines Schlüsselfeldes können Sie mit der Funktion **Lookup** einen Wert aus einem Dataset für eine 1:1-Beziehung abrufen, z.B. ein Schlüssel-Wert-Paar. Der folgende Ausdruck zeigt den Produktnamen aus einem Dataset („Product“) an, wenn der Produktbezeichner übereinstimmt:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Durch die Angabe eines Schlüsselfeldes können Sie mit der Funktion **LookupSet** einen Wert aus einem Dataset für eine 1:n-Beziehung abrufen. Beispielsweise kann eine Person mehrere Telefonnummern haben. Im folgenden Beispiel nehmen wir an, dass das Dataset „PhoneList“ in jeder Zeile einen Personenbezeichner und eine Telefonnummer enthält. **LookupSet** gibt ein Array von Werten zurück. Der folgende Ausdruck kombiniert die Rückgabewerte zu einer einzigen Zeichenfolge und zeigt die Liste der Telefonnummern für die durch „ContactID“ angegebene Person an:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="ConversionFunctions"></a> Konvertierungsfunktionen  
 Mit den Visual Basic-Funktionen können Sie ein Feld des einen Datentyps in einen anderen Datentyp konvertieren. Mit Hilfe von Konvertierungsfunktionen kann der Standarddatentyp für ein Feld in den für Berechnungen erforderlichen Datentyp konvertiert oder Text kombiniert werden.  
  
-   Der folgende Ausdruck konvertiert die Konstante „500“ in den Typ „Decimal“, um sie mit einem Datentyp „Transact-SQL money“ im Feld „Value“ für einen Filterausdruck zu vergleichen.  
  
    ```  
    =CDec(500)  
    ```  
  
-   Der folgende Ausdruck zeigt die Anzahl der für den mehrwertigen Parameter *MySelection* ausgewählten Werte an.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="DecisionFunctions"></a> Entscheidungsfunktionen  
  
-   Die Funktion **Iif** gibt einen von zwei Werten zurück, je nachdem, ob der Ausdruck wahr ist oder nicht. Der folgende Ausdruck verwendet die Funktion **Iif**, um einen booleschen Wert von **True** zurückzugeben, wenn der Wert von `LineTotal` 100 überschreitet. Andernfalls wird **False** zurückgegeben:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Verwenden Sie mehrere **IIF**-Funktionen (auch bekannt als „verschachtelte IIFs“), um einen von drei Werten abhängig vom Wert von `PctComplete` zurückzugeben. Der folgende Ausdruck kann in die Füllfarbe eines Textfeldes eingefügt werden, um die Hintergrundfarbe abhängig vom Wert im Textfeld zu ändern.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Werte, die größer oder gleich 10 sind, werden mit einem grünen Hintergrund angezeigt. Werte zwischen 1 und 9 erhalten einen blauen Hintergrund, und Werte kleiner als 1 werden mit rotem Hintergrund dargestellt.  
  
-   Eine andere Art, die gleiche Funktionalität zu erhalten, verwendet die Funktion **Switch**. Die Funktion **Switch** kann verwendet werden, wenn Sie drei oder mehr Bedingungen testen müssen. Die Funktion **Switch** gibt den Wert zurück, der dem ersten Ausdruck in einer Reihe zugeordnet ist, der als „True“ ausgewertet wird:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Werte, die größer oder gleich 10 sind, werden mit einem grünen Hintergrund angezeigt. Werte zwischen 1 und 9 erhalten einen blauen Hintergrund, Werte, die gleich 1 sind, einen gelben Hintergrund, und Werte, die 0 oder kleiner sind, werden mit einem roten Hintergrund dargestellt.  
  
-   Mit dem Ausdruck wird der Wert des Feldes `ImportantDate` geprüft und „Red“ zurückgegeben, wenn er älter als eine Woche ist. Andernfalls wird „Blue“ zurückgegeben. Dieser Ausdruck kann verwendet werden, um die Eigenschaft „Color“ eines Textfeldes in einem Berichtselement zu steuern:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Mit dem Ausdruck wird der Wert des Felds `PhoneNumber` geprüft und „No Value“ zurückgegeben, wenn er **NULL** (**Nothing** in Visual Basic) ist. Andernfalls wird der Wert der Telefonnummer zurückgegeben. Dieser Ausdruck kann verwendet werden, um den Wert eines Textfeldes in einem Berichtselement zu steuern.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Mit dem Ausdruck wird der Wert des Felds `Department` geprüft und entweder ein Unterberichtsname oder **NULL** (**Nothing** in Visual Basic) zurückgegeben. Dieser Ausdruck kann für bedingte Drillthrough-Unterberichte verwendet werden.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Der Ausdruck prüft, ob ein Feldwert Null ist. Dieser Ausdruck kann verwendet werden, um die Eigenschaft **Hidden** eines Bildberichtselements zu steuern. Im folgenden Beispiel wird das durch das Feld [LargePhoto] angegebene Bild nur angezeigt, wenn der Wert des Feldes nicht Null ist.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   Die Funktion **MonthName** gibt einen Zeichenfolgenwert zurück, der den Namen des angegebenen Monats enthält. Das folgende Beispiel zeigt NA im Monatsfeld an, wenn das Feld den Wert 0 enthält.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="ReportFunctions"></a> Berichtsfunktionen  
 In einem Ausdruck können Sie einen Verweis auf zusätzliche Berichtsfunktionen hinzufügen, die Daten in einem Bericht bearbeiten. Dieser Abschnitt enthält Beispiele für zwei dieser Funktionen. 
  
###  <a name="Sum"></a> Sum  
  
-   Die Funktion **Sum** kann die Werte in einer Gruppe oder einem Datenbereich addieren. Diese Funktion kann in der Kopf- oder Fußzeile einer Gruppe nützlich sein. Der folgende Ausdruck zeigt die Summe der Daten in der Gruppe oder im Datenbereich „Order“ an:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   Sie können die Funktion **Sum** auch für bedingte Aggregatberechnungen verwenden. Wenn ein Dataset beispielsweise ein Feld mit dem Namen „State“ mit den möglichen Werten „Not Started“, „Started“, „Finished“ enthält, berechnet der folgende Ausdruck, wenn er in eine Gruppenkopfzeile platziert wird, die aggregierte Summe nur für den Wert „Finished“:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="RowNumber"></a> RowNumber  
  
-   Die Funktion **RowNumber** zeigt bei Verwendung in einem Textfeld innerhalb eines Datenbereichs die Zeilennummer für jede Instanz des Textfelds an, in dem der Ausdruck erscheint. Diese Funktion kann für die Nummerierung von Zeilen in einer Tabelle verwendet werden. Sie kann auch für komplexere Aufgaben sinnvoll sein, wie z.B. das Bereitstellen von Seitenumbrüchen basierend auf der Anzahl der Zeilen. Weitere Informationen finden Sie unter [Seitenumbrüche](#PageBreaks) in diesem Thema.  
  
     Der Bereich, den Sie für **RowNumber** angeben, steuert, wann die Neunummerierung beginnt. Das Schlüsselwort **Nothing** zeigt an, dass die Funktion mit dem Zählen in der ersten Zeile im äußersten Datenbereich beginnt. Um die Zählung innerhalb verschachtelter Datenbereiche zu starten, verwenden Sie den Namen des Datenbereichs. Um die Zählung innerhalb einer Gruppe zu starten, verwenden Sie den Namen der Gruppe.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="AppearanceofReportData"></a> Darstellung von Berichtsdaten  
 Mit Ausdrücken können Sie bearbeiten, wie Daten in einem Bericht angezeigt werden. Beispielsweise können Sie die Werte von zwei Feldern in einem einzigen Textfeld anzeigen, Informationen über den Bericht anzeigen oder bestimmen, wie Seitenumbrüche in den Bericht eingefügt werden.  
  
###  <a name="PageHeadersandFooters"></a> Kopf- und Fußzeilen für Seiten  
 Wenn Sie einen Bericht erstellen, können Sie den Namen des Berichts und die Seitennummer in der Fußzeile des Berichts anzeigen. Dafür können Sie die folgenden Ausdrücke verwenden:  
  
-   Der folgende Ausdruck gibt den Namen des Berichts und die Uhrzeit seiner Ausführung an. Er kann in ein Textfeld in der Fußzeile des Berichts oder im Textkörper des Berichts eingefügt werden. Die Uhrzeit wird mit der Formatierungszeichenfolge von .NET Framework für das kurze Datum formatiert:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   Der folgende Ausdruck, der in einem Textfeld in der Fußzeile eines Berichts platziert wird, gibt die Seitenzahl und die Gesamtseitenzahl im Bericht an:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 Die folgenden Beispiele beschreiben, wie Sie den ersten und letzten Wert einer Seite in der Kopfzeile der Seite anzeigen können, ähnlich wie bei einer Verzeichnisliste. Das Beispiel geht von einem Datenbereich aus, der ein Textfeld mit dem Namen `LastName` enthält.  
  
-   Der folgende Ausdruck, der in einem Textfeld auf der linken Seite des Kopfzeile der Seiten eingefügt wird, gibt den ersten Wert des `LastName`-Textfelds auf der Seite an:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   Der folgende Ausdruck, der in einem Textfeld auf der rechten Seite des Kopfzeile der Seiten eingefügt wird, gibt den letzten Wert des `LastName`-Textfelds auf der Seite an:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 Das folgende Beispiel beschreibt, wie man eine Seitensumme anzeigt. Im Beispiel wird angenommen, dass der Datenbereich ein Textfeld mit dem Namen `Cost` enthält.  
  
-   Der folgende Ausdruck, der in der Kopf- oder Fußzeile der Seite eingefügt wird, gibt die Summe der Werte im Textfeld `Cost` für die Seite an:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Sie können nur auf ein Berichtselement pro Ausdruck in einer Kopf- oder Fußzeile einer Seite verweisen. Sie können in Kopf- und Fußzeilenausdrücken einer Seite auch auf den Namen des Textfeldes verweisen, aber nicht auf den eigentlichen Datenausdruck innerhalb des Textfeldes.  
  
###  <a name="PageBreaks"></a> Seitenumbrüche  
 In einigen Berichten möchten Sie möglicherweise einen Seitenumbruch am Ende einer bestimmten Anzahl von Zeilen anstelle von oder zusätzlich zu Gruppen oder Berichtselementen einfügen. Erstellen Sie dazu eine Gruppe, die die gewünschten Gruppen oder Datensätze enthält, fügen Sie der Gruppe einen Seitenumbruch hinzu, und fügen Sie dann einen Gruppenausdruck zur Gruppe anhand einer bestimmten Anzahl von Zeilen hinzu.  
  
-   Wenn der folgende Ausdruck im Gruppenausdruck eingefügt wird, weist er jedem Satz von 25 Zeilen eine Nummer zu. Wenn für die Gruppe ein Seitenumbruch definiert ist, wird durch diesen Ausdruck alle 25 Zeilen ein Seitenumbruch erzeugt.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Damit der Benutzer einen Wert für die Anzahl der Zeilen pro Seite festlegen kann, erstellen Sie einen Parameter mit dem Namen `RowsPerPage`, und nutzen Sie diesen als Basis für den Gruppenausdruck, wie im folgenden Ausdruck gezeigt:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="Properties"></a> Eigenschaften  
 Ausdrücke werden nicht nur zum Anzeigen von Daten in Textfeldern verwendet. Sie können auch verwendet werden, um die Anwendung von Eigenschaften auf Berichtselemente zu ändern. Sie können Stilinformationen für ein Berichtselement oder seine Sichtbarkeit ändern.  
  
###  <a name="Formatting"></a> Formatierung  
  
-   Der folgende Ausdruck ändert bei Verwendung in der Eigenschaft „Color“ eines Textfelds die Farbe des Textes in Abhängigkeit vom Wert des Feldes `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Sie können auch die Visual Basic-Objektvariable `Me` verwenden. Diese Variable ist eine weitere Möglichkeit, auf den Wert eines Textfelds zu verweisen.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   Der folgende Ausdruck wechselt bei Verwendung in der Eigenschaft „BackgroundColor“ eines Berichtselements in einem Datenbereich die Hintergrundfarbe jeder Zeile zwischen blassgrün und weiß:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Wenn Sie einen Ausdruck für einen bestimmten Bereich verwenden, müssen Sie möglicherweise das Dataset für die Aggregatfunktion angeben:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Verfügbare Farben stammen aus der .NET Framework-Enumeration „KnownColor“.  
  
### <a name="chart-colors"></a>Diagrammfarben  
 Um Farben für ein Formdiagramm festzulegen, können Sie mit benutzerdefiniertem Code die Reihenfolge steuern, in der Farben den Datenpunktwerten zugeordnet werden. Auf diese Weise können Sie konsistente Farben für mehrere Diagramme mit gleichen Kategoriegruppen verwenden. 
  
###  <a name="Visibility"></a> Sichtbarkeit  
 Sie können Elemente in einem Bericht über die Sichtbarkeitseigenschaften des Berichtselements ein- und ausblenden. In einem Datenbereich wie einer Tabelle können Sie Detailzeilen zunächst basierend auf dem Wert in einem Ausdruck ausblenden.  
  
-   Wenn der folgende Ausdruck für die ursprüngliche Sichtbarkeit von Detailzeilen in einer Gruppe verwendet wird, werden die Detailzeilen für alle Umsätze angezeigt, die im `PctQuota`-Feld den Wert 90 % übersteigen:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   Wenn der folgende Ausdruck in der Eigenschaft „Hidden“ einer Tabelle angegeben wird, wird die Tabelle nur angezeigt, wenn sie mehr als 12 Zeilen hat:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   Wenn der folgende Ausdruck in der Eigenschaft **Hidden** einer Spalte angegeben wird, wird die Spalte nur angezeigt, wenn das Feld im Berichtsdataset enthalten ist, nachdem die Daten aus der Datenquelle abgerufen wurden:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="Hyperlinks"></a> URLs  
 Sie können URLs mithilfe von Berichtsdaten anpassen und außerdem bedingt steuern, ob URLs als Aktion für ein Textfeld hinzugefügt werden.  
  
-   Wenn der folgende Ausdruck als Aktion auf einem Textfeld verwendet wird, wird eine benutzerdefinierte URL generiert, die das Datasetfeld `EmployeeID` als URL-Parameter angibt.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   Der folgende Ausdruck steuert bedingt, ob eine URL in ein Textfeld hinzugefügt werden soll. Dieser Ausdruck hängt von einem Parameter namens `IncludeURLs` ab, mit dem ein Benutzer entscheiden kann, ob aktive URLs in einen Bericht aufgenommen werden sollen. Dieser Ausdruck wird als eine Aktion in einem Textfeld festgelegt. Indem Sie den Parameter auf „False“ festlegen und dann den Bericht anzeigen, können Sie den Bericht ohne Hyperlinks in Microsoft Excel exportieren.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="ReportData"></a> Berichtsdaten  
 Mit Ausdrücken können die im Bericht verwendeten Daten bearbeitet werden. Sie können auf Parameter und sonstige Berichtsinformationen verweisen. Es ist sogar möglich, die Abfrage zu ändern, mit der Daten für den Bericht abgerufen werden.  
  
###  <a name="Parameters"></a> Parameter  
 Ausdrücke können in einem Parameter verwendet werden, um den Standardwert für den Parameter zu ändern. Beispielsweise können Sie mithilfe eines Parameters Daten nach einem bestimmten Benutzer basierend auf der Benutzer-ID filtern, mit der der Bericht ausgeführt wird.  
  
-   Wenn der folgende Ausdruck als Standardwert für einen Parameter verwendet wird, wird die Benutzer-ID der Person abgerufen, die den Bericht ausführt:  
  
    ```  
    =User!UserID  
    ```  
  
-   Verwenden Sie die globale Auflistung **Parameters**, um auf einen Parameter in einem Abfrageparameter, auf einen Filterausdruck, ein Textfeld oder einen anderen Bereich des Berichts zu verweisen. Bei diesem Beispiel wird von einem Parameter namens *Department*ausgegangen:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Parameter können in einem Bericht erstellt und trotzdem ausgeblendet werden. Wenn der Bericht auf dem Berichtsserver ausgeführt wird, wird der Parameter nicht auf der Symbolleiste angezeigt, und der Leser des Berichts kann den Standardwert nicht ändern. Sie können einen ausgeblendeten, auf einen Standardwert festgelegten Parameter als benutzerdefinierte Konstante verwenden. Diesen Wert können Sie in einem beliebigen Ausdruck verwenden, einschließlich eines Feldausdrucks. Der folgende Ausdruck gibt das vom Standardparameterwert für den Parameter mit dem Namen *ParameterField* angegebene Feld an:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="CustomCode"></a> Benutzerdefinierter Code  
 Sie können in einem Bericht eingebetteten benutzerdefinierten Code verwenden. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Verwenden von Gruppenvariablen für benutzerdefinierte Aggregation  
 Sie können den Wert für eine Gruppenvariable initialisieren, die zu einem bestimmten Gruppenbereich lokal ist, und anschließend einen Verweis auf diese Variable in den Ausdrücken einbinden. Eine der Methoden, wie Sie eine Gruppenvariable mit benutzerdefiniertem Code verwenden können, besteht darin, ein benutzerdefiniertes Aggregat zu implementieren. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Unterdrücken von NULL oder 0 zur Laufzeit  
 Einige Werte in einem Ausdruck können zur Berichtsverarbeitungszeit mit NULL oder „nicht definiert“ ausgewertet werden. Dies kann zu Laufzeitfehlern und zur Anzeige von **#Error** im Textfeld anstelle des ausgewerteten Ausdrucks führen. Die **IIF**-Funktion ist für dieses Verhalten besonders empfindlich, da im Gegensatz zu einer If-Then-Else-Anweisung jeder Teil der **IIF** -Anweisung (einschließlich Funktionsaufrufe) ausgewertet wird, bevor er an die Routine zur Prüfung auf **true** oder **false** übergeben wird. Die Anweisung `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` generiert **#Error** im gerenderten Bericht, wenn `Fields!Sales.Value` NOTHING ist.  
  
 Wählen Sie eine der folgenden Strategien aus, um diesen Fehler zu vermeiden:  
  
-   Legen Sie den Zähler auf 0 und den Nenner auf 1 fest, wenn der Wert für das Feld B 0 oder nicht definiert ist. Andernfalls legen Sie den Zähler auf den Wert für Feld A und den Nenner auf den Wert für Feld B fest.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Verwenden Sie eine benutzerdefinierte Codefunktion, um den Wert für den Ausdruck zurückzugeben. Im folgenden Beispiel wird der Prozentsatzunterschied zwischen einem aktuellen Wert und einem vorherigen Wert zurückgegeben. Dieser Wert kann zur Berechnung der Differenz zwischen zwei aufeinanderfolgenden Werten verwendet werden und verarbeitet den Grenzfall des ersten Vergleichs (wenn kein vorheriger Wert vorhanden ist) sowie Fälle, in denen entweder der vorherige Wert oder der aktuelle Wert **Null** (**Nothing** in Visual Basic) ist.  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     Der folgende Ausdruck veranschaulicht, wie dieser benutzerdefinierte Code aus einem Textfeld für den Container „ColumnGroupByYear“ (Gruppe bzw. Datenbereich) aufgerufen wird.  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Dadurch wird die Ausführung von Laufzeitausnahmen vermieden. Sie können nun einen Ausdruck wie `=IIF(Me.Value < 0, "red", "black")` in der Eigenschaft **Color** des Textfelds verwenden, um den Text unter Bedingungen anzuzeigen, nämlich abhängig davon, ob die Werte größer oder kleiner als 0 sind.  
  
## <a name="next-steps"></a>Nächste Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
  
