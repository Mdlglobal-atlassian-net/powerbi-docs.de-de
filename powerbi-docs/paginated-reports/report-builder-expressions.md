---
title: Ausdrücke im Power BI-Berichts-Generator
description: Ausdrücke werden in paginierten Berichten im Power BI Report Builder häufig verwendet, um Daten abzurufen, zu berechnen, anzuzeigen, zu gruppieren, zu sortieren, zu filtern, zu parametrisieren oder zu formatieren.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 96c62fec55f87a31970b624a79314656ced0c159
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921123"
---
# <a name="expressions-in-power-bi-report-builder"></a>Ausdrücke im Power BI-Berichts-Generator
  Ausdrücke werden in paginierten Berichten im Power BI Report Builder häufig verwendet, um Daten abzurufen, zu berechnen, anzuzeigen, zu gruppieren, zu sortieren, zu filtern, zu parametrisieren oder zu formatieren. 
  
  Viele Eigenschaften von Berichtselementen können auf einen Ausdruck festgelegt werden. Mit Ausdrücken können Sie den Inhalt, das Design und die Interaktivität Ihres Berichts bestimmen. Ausdrücke werden in Microsoft Visual Basic geschrieben, in der Berichtsdefinition gespeichert und vom Berichtsprozessor ausgewertet, wenn Sie den Bericht ausführen.  
  
 Im Gegensatz zu Anwendungen wie Microsoft Excel, in denen Sie direkt mit Daten auf Arbeitsblättern arbeiten, arbeiten Sie in Berichten mit Ausdrücken, die als Platzhalter für Daten fungieren. Wenn Sie die tatsächlichen Daten der ausgewerteten Ausdrücke sehen möchten, müssen Sie eine Vorschau des Berichts anzeigen. Wenn Sie den Bericht ausführen, wertet der Berichtsprozessor jeden Ausdruck aus, während er die Berichtsdaten und die Berichtslayoutelemente (z. B. Tabellen und Diagramme) miteinander kombiniert.  
  
 Beim Entwerfen eines Berichts werden viele Ausdrücke für Berichtselemente für Sie festgelegt. Wenn Sie beispielsweise ein Feld aus dem Datenbereich in eine Zelle in der Tabelle auf der Berichtsentwurfsoberfläche ziehen, wird der Wert im Textfeld für das Feld auf einen einfachen Ausdruck festgelegt. Auf der folgenden Abbildung werden im Berichtsdatenbereich die Datasetfelder „ID“, „Name“, „SalesTerritory“, „Code“ und „Sales“ angezeigt. Der Tabelle wurden drei Felder hinzugefügt: [Name], [Code] und [Sales]. [Name] steht auf der Entwurfsoberfläche für den zugrunde liegenden Ausdruck `=Fields!Name.Value`.  
  
![Entwurfsansicht des Berichts-Generators](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Wenn Sie eine Vorschau des Berichts anzeigen, kombiniert der Berichtsprozessor den Tabellendatenbereich mit den tatsächlichen Daten aus der Datenverbindung und zeigt für jede Zeile im Resultset eine Zeile in der Tabelle an.  
  
 Wenn Sie Ausdrücke manuell eingeben möchten, wählen Sie ein Element auf der Entwurfsoberfläche aus, und verwenden Sie das Kontextmenü und die Dialogfelder, um die Eigenschaften des Elements festzulegen. Wenn die Schaltfläche ***(fx)*** oder der Wert `<Expression>` in einer Dropdownliste angezeigt wird, wissen Sie, dass Sie die Eigenschaft auf einen Ausdruck festlegen können. 
  
##  <a name="Types"></a> Grundlegendes zu einfachen und komplexen Ausdrücken  
 Ausdrücke beginnen mit einem Gleichheitszeichen (=) und werden in Microsoft Visual Basic geschrieben. Ausdrücke können aus einer Kombination aus Konstanten, Operatoren und Verweisen auf integrierte Werte (Felder, Sammlungen oder Funktionen) oder auf externen oder benutzerdefinierten Code bestehen.  
  
 Sie können mit Ausdrücken den Wert vieler Berichtselementeigenschaften festlegen. Die häufigsten Eigenschaften sind Werte für Textfeld- und Platzhaltertext. Wenn ein Textfeld nur einen Ausdruck enthält, ist der Ausdruck normalerweise der Wert der Textfeldeigenschaft. Wenn ein Textfeld mehrere Ausdrücke enthält, ist jeder Ausdruck eine Wert für Platzhaltertext im Textfeld.  
  
 Standardmäßig werden Ausdrücke auf der Berichtsentwurfsoberfläche als *einfache* oder *komplexe Ausdrücke* angezeigt.  
  
-   **Einfach:** Ein einfacher Ausdruck enthält einen Verweis auf ein einzelnes Element in einer integrierten Sammlung, z. B. auf ein Dataset, einen Parameter oder ein integriertes Feld. Auf der Entwurfsoberfläche wird ein einfacher Ausdruck in Klammern angezeigt. `[FieldName]` entspricht z. B. dem zugrunde liegenden Ausdruck `=Fields!FieldName.Value`. Einfache Ausdrücke werden automatisch für Sie erstellt, wenn Sie das Berichtslayout erstellen und Elemente aus dem Berichtsdatenbereich auf die Entwurfsoberfläche ziehen. Weitere Informationen zu den Symbolen, die für unterschiedliche integrierte Sammlungen stehen, finden Sie weiter unten unter [Grundlegendes zu Präfixsymbolen für einfache Ausdrücke](#DisplayText).  
  
-   **Komplex:** Ein komplexer Ausdruck enthält Verweise auf mehrere integrierte Verweise, Operatoren und Funktionsaufrufe. Ein komplexer Ausdruck wird als <\<Expr>> angezeigt, wenn der Ausdruckswert mehr als einen einfachen Verweis enthält. Zeigen Sie mit dem Mauszeiger auf einen Ausdruck, wenn Sie diesen anzeigen möchten, und verwenden Sie die QuickInfo. Öffnen Sie den Ausdruck im Dialogfeld **Ausdruck**, wenn Sie diesen bearbeiten möchten.  
  
 In der folgenden Abbildung sehen Sie typische einfache und komplexe Ausdrücke für Textfelder und Platzhaltertext.  
  
![Standardformat von Ausdrücken im Berichts-Generator](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Wenden Sie Formatierungen auf den Textfeld- oder Platzhaltertext an, um statt Ausdruckstext Beispielwerte anzuzeigen. Auf der folgenden Abbildung sehen Sie die Berichtsentwurfsoberfläche mit Beispielwerten:  
  
![Beispielformat von Ausdrücken im Berichts-Generator](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="DisplayText"></a> Grundlegendes zu Präfixsymbolen in einfachen Ausdrücken  

Einfache Ausdrücke verwenden Symbole, um anzugeben, ob der Verweis auf ein Feld, einen Parameter, eine integrierte Sammlung oder die ReportItems-Sammlung verweist. In der folgenden Tabelle werden Beispiele für Anzeige- und Ausdruckstext aufgeführt:  
  
|Artikel|Beispiel für Anzeigetext|Beispiel für Ausdruckstext|  
|----------|--------------------------|-----------------------------|  
|Datasetfelder|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Berichtsparameter|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Integrierte Felder|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Literalzeichen, die für den Anzeigetext verwendet werden|`\[Sales\]`|`[Sales]`|  
  
##  <a name="References"></a> Schreiben komplexer Ausdrücke  
 Ausdrücke können Verweise auf Funktionen, Operatoren, Konstanten, Felder, Parameter, Elemente aus integrierten Sammlungen und auf eingebetteten benutzerdefinierten Code oder benutzerdefinierte Assemblys enthalten.  
  
 In der folgenden Tabelle werden die Arten von Verweisen aufgelistet, die Sie in Ausdrücken verwenden können:  
  
|Referenzen|Beschreibung|Beispiel|  
|----------------|-----------------|-------------|  
|Konstanten|Beschreibt die Konstanten, auf die Sie für Eigenschaften, die konstante Werte (wie z. B. Schriftfarben) erfordern, interaktiv zugreifen können.|`="Blue"`|  
|Operatoren|Beschreibt die Operatoren, die Sie zum Kombinieren von Verweisen in einem Ausdruck verwenden können. Der Operator **&** wird z. B. zum Verketten von Zeichenfolgen verwendet.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Integrierte Sammlungen|Beschreibt die integrierten Sammlungen, die Sie in einem Ausdruck verwenden können, z. B. `Fields`, `Parameters` und `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Integrierte Berichts- und Aggregatfunktionen|Beschreibt die integrierten Funktionen, auf die Sie von einem Ausdruck aus zugreifen können, z. B. `Sum` oder `Previous`.|`=Previous(Sum(Fields!Sales.Value))`|  
|Verweise auf benutzerdefinierten Code und Assemblys in Ausdrücken im Berichts-Generator |Beschreibt, wie Sie von einer externen Assembly auf die integrierten CLR-Klassen `xref:System.Math` und `xref:System.Convert`, andere CLR-Klassen, Visual Basic-Runtimebibliotheksfunktionen oder Methoden zugreifen können.<br /><br /> Beschreibt, wie Sie auf benutzerdefinierten Code zugreifen können, der in Ihren Bericht eingebettet ist oder den Sie als benutzerdefinierte Assembly auf dem Berichtsclient und dem Berichtsserver kompilieren und installieren.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="Valid"></a> Überprüfen von Ausdrücken  
 Wenn Sie einen Ausdruck für eine bestimmte Berichtselementeigenschaft erstellen, hängen die Verweise, die Sie im Ausdruck verwenden können, von zwei Faktoren ab: von den Werten, die die Berichtselementeigenschaft akzeptiert, und vom Bereich, in dem die Eigenschaft ausgewertet wird. Beispiel:  
  
-   Der Ausdruck [Sum] berechnet standardmäßig die Summe der Daten, die sich zum Zeitpunkt der Auswertung des Ausdrucks im Bereich befinden. Für eine Zelle in einer Tabelle hängt der Bereich von Zugehörigkeiten zu Zeilen- und Spaltengruppen ab. 
  
-   Für den Wert einer Font-Eigenschaft muss der Wert als Name einer Schriftart ausgewertet werden.  
  
-   Die Ausdruckssyntax wird zur Entwurfszeit überprüft. Die Überprüfung des Ausdrucksbereichs erfolgt, wenn Sie den Bericht veröffentlichen. Überprüfungen, die von den tatsächlichen Daten abhängen, können Fehler nur zur Laufzeit erkennen. Einige dieser Ausdrücke führen zu #Error als Fehlermeldung im gerenderten Bericht. 

## <a name="next-steps"></a>Nächste Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
