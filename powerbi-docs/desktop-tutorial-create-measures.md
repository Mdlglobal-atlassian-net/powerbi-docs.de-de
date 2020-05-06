---
title: 'Tutorial: Erstellen eigener Measures in Power BI Desktop'
description: Measures in Power BI Desktop unterstützen Sie, indem sie Berechnungen mit Ihren Daten durchführen, während Sie mit Ihren Berichten interagieren.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0d2b316b53b4107c86a036cc8a436440dd8bd674
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74311524"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutorial: Erstellen eigener Measures in Power BI Desktop
Sie können mithilfe von Measures einige der leistungsstärksten Datenanalyselösungen in Power BI Desktop erstellen. Measures unterstützen uns, indem sie Berechnungen mit Ihren Daten durchführen, während Sie mit Ihren Berichten interagieren. Dieses Tutorial führt Sie durch die Grundlagen von Measures hin zum Erstellen eigener einfacher Measures in Power BI Desktop.

## <a name="prerequisites"></a>Voraussetzungen

- Dieses Tutorial richtet sich an Power BI-Benutzer, die mit der Verwendung von Power BI Desktop zum Erstellen etwas fortgeschrittener Modelle bereits vertraut sind. Sie sollten bereits mit der Verwendung von „Daten abrufen“ und des Abfrage-Editors zum Importieren von Daten, dem Arbeiten mit mehreren aufeinander bezogenen Tabellen und dem Hinzufügen von Feldern zum Berichtszeichenbereich vertraut sein. Wenn Sie noch nicht mit Power BI Desktop vertraut sind, sollten Sie [Erste Schritte mit Power BI Desktop](desktop-getting-started.md) lesen.
  
- In diesem Tutorial wird die Datei [Contoso Sales Sample for Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip) verwendet, die Onlineumsatzdaten des fiktiven Unternehmens Contoso enthält. Da diese Daten aus einer Datenbank importiert werden, können Sie keine Verbindung mit der Datenquelle herstellen oder die Daten im Abfrage-Editor anzeigen. Laden Sie die Datei herunter, und extrahieren Sie sie auf Ihrem Computer.

## <a name="automatic-measures"></a>Automatische Measures

Wenn Power BI Desktop ein Measure erstellt, erfolgt dies meist für Sie automatisch. Führen Sie die folgenden Schritte aus, um zu verfolgen, wie Power BI Desktop ein Measure erstellt:

1. Wählen Sie in Power BI Desktop **Datei** > **Öffnen** aus. Navigieren Sie zur Datei *Contoso Sales Sample for Power BI Desktop.pbix*, und wählen Sie **Öffnen** aus.

2. Erweitern Sie im Abschnitt **Felder**die Tabelle **Sales**. Aktivieren Sie dann entweder das Kontrollkästchen neben dem Feld **SalesAmount** (Umsatzbetrag), oder ziehen Sie **SalesAmount** in den Berichtszeichenbereich.

    Eine neue Säulendiagrammvisualisierung wird gezeigt, die die Summe aller Werte in der Spalte **SalesAmount** der Tabelle **Sales** enthält.

    ![Diagramm der Spalte „SalesAmount“](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Alle Felder (Spalten) im Bereich **Felder** mit einem ![Sigmasymbol](media/desktop-tutorial-create-measures/meastut_sigma.png) sind numerisch, sodass dessen Werte aggregiert werden können. Anstatt eine Tabelle mit vielen Werten anzuzeigen (2 Mio. Zeilen in **SalesAmount**), erstellt und berechnet Power BI Desktop automatisch ein Measure zum Aggregieren der Daten, sobald ein numerischer Datentyp erkannt wird. Eine Summe ist die Standardaggregation für einen numerischen Datentyp, aber Sie können auch problemlos verschiedene Aggregationen wie Mittelwert oder Anzahl anwenden. Das Konzept von Aggregation ist für das Verständnis von Measures von grundlegender Wichtigkeit, da jedes Measure irgendeine Form von Aggregation durchführt. 

Um die Diagrammaggregation zu ändern, führen Sie die folgenden Schritte aus:

1. Wählen Sie im Berichtszeichenbereich die Visualisierung **SalesAmount** aus.  

1. Wählen Sie im Bereich **Wert** des Bereichs **Visualisierungen** den nach unten zeigenden Pfeil rechts neben **SalesAmount** aus. 

1. Wählen Sie im eingeblendeten Menü **Durchschnitt** aus. 

    Die Visualisierung zeigt dann im Feld **SalesAmount** einen Mittelwert aller Umsatzwerte.

    ![SalesAmount-Diagramm für Mittelwerte](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Abhängig vom gewünschten Ergebnis können Sie den Aggregationstyp ändern. Allerdings eignen sich nicht alle Aggregationstypen für jeden numerischen Datentyp. So sind beispielsweise für das Feld **SalesAmount** „Summe“ und „Durchschnitt“ nützlich, und auch „Minimum“ und „Maximum“ haben ihre Berechtigung. „Anzahl“ ist für das Feld **SalesAmount** hingegen nicht wirklich sinnvoll, denn seine Werte sind zwar numerisch, stellen aber eigentlich eine Währung dar.

Aus Measures berechnete Werte ändern sich als Reaktion auf Ihre Interaktionen mit Ihrem Bericht. Wenn Sie z. B. das Feld **RegionCountryName** aus der Tabelle **Geography** auf Ihr Diagramm **SalesAmount** ziehen, ändert sich die Anzeige in die durchschnittlichen Umsatzbeträge für jedes Land.

![Umsatzbetrag nach Land/Region](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Wenn sich das Ergebnis eines Measures aufgrund einer Interaktion mit unserem Bericht ändert, nehmen Sie Einfluss auf den *Kontext* Ihres Measures. Bei jeder Interaktion mit Ihren Berichtvisualisierungen ändern Sie den Kontext, in dem ein Measure seine Ergebnisse berechnet und anzeigt.

## <a name="create-and-use-your-own-measures"></a>Erstellen und Verwenden eines eigenen Measures

In den meisten Fällen berechnet Power BI Desktop Werte automatisch und gibt sie entsprechend den von Ihnen gewählten Feld- und Aggregationstypen zurück. In anderen Fällen müssen Sie jedoch ggf. eigene Measures erstellen, um komplexere, spezifischere Berechnungen durchzuführen. Mit Power BI Desktop können Sie Ihre eigenen Measures mit der DAX-Formelsprache (Data Analysis Expressions) erstellen. 

DAX-Formeln verwenden häufig die gleichen Funktionen, Operatoren und die gleiche Syntax wie Excel-Formeln. Allerdings sind die DAX-Funktionen für die Arbeit mit relationalen Daten und zur Durchführung dynamischerer Berechnungen während Ihrer Interaktion mit Berichten ausgelegt. Es gibt mehr als 200 DAX-Funktionen, die alles von einfachen Aggregationen wie Summe und Mittelwert bis hin zu komplexeren Statistik- und Filterfunktionen ausführen. Es gibt zahlreiche Ressourcen, die Sie nutzen können, um mehr über DAX zu erfahren. Nachdem Sie dieses Tutorial abgeschlossen haben, werfen Sie einen Blick auf [DAX-Grundlagen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Wenn Sie ein eigenes Measure erstellen, wird es als *Modellmeasure* bezeichnet und der Liste **Felder** für die von Ihnen ausgewählte Tabelle hinzugefügt. Modellmeasures bieten z. B. folgende Vorteile: Sie können für sie beliebige, aussagekräftige Namen vergeben, Sie können sie als Argumente in anderen DAX-Ausdrücken verwenden, und Sie können sie schnell komplexe Berechnungen durchführen lassen.

### <a name="quick-measures"></a>Quickmeasures

Ab der Power BI Desktop-Version vom Februar 2018 stehen Ihnen viele gängige Berechnungen als *Quickmeasures* zur Verfügung, die die DAX-Formeln basierend auf Ihren Eingaben in ein Fenster schreiben. Diese schnellen, leistungsstarken Berechnungen eignen sich auch hervorragend, um DAX-Formeln zu erlernen oder eigene maßgeschneiderte Measures einzusetzen. 

Erstellen Sie ein Quickmeasure mit einer der folgenden Methoden: 
 - Klicken Sie in einer Tabelle im Bereich **Felder** mit der rechten Maustaste, und wählen Sie **Weitere Optionen** ( **...** ) und dann in der Liste **Neues Quickmeasure** aus.

 - Wählen Sie auf dem Menüband von Power BI Desktop auf der Registerkarte **Start** unter **Berechnungen** die Option **Neues Quickmeasure** aus.

Weitere Informationen zum Erstellen und Verwenden von Quickmeasures finden Sie unter [Verwenden von Quickmeasures](desktop-quick-measures.md).

### <a name="create-a-measure"></a>Erstellen eines Measures

Angenommen, Sie möchten Ihren Nettoumsatz analysieren, indem Sie Rabatte und Retouren von den Gesamtumsätzen abziehen. Für den Kontext in Ihrer Visualisierung benötigen Sie ein Measure, das die Summe aus „DiscountAmount“ (Rabattbetrag) und „ReturnAmount“ (Retourenbetrag) von der Summe von „SalesAmount“ subtrahiert. In der Liste **Felder** gibt kein Feld für Nettoumsatz, aber Sie haben die Bausteine, um Ihr eigenes Measure zur Berechnung des Nettoumsatzes zu erstellen. 

Führen Sie die folgenden Schritte aus, um ein Measure zu erstellen:

1. Klicken Sie in der Liste **Felder** mit der rechten Maustaste auf die Tabelle **Sales**, oder zeigen Sie auf die Tabelle, und wählen Sie die **Weitere Optionen** ( **...** ) aus. 

1. Wählen Sie im eingeblendeten Menü **Neues Measure** aus. 

    Diese Aktion speichert Ihr neues Measure in der Tabelle **Sales**, wo es leicht zu finden ist.
    
    ![Neues Measure aus Liste](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Sie können auch ein neues Measure erstellen, indem Sie auf dem Power BI Desktop-Menüband auf der Registerkarte **Start** in der Gruppe **Berechnungen** die Option **Neues Measure** wählen.
    
    ![Neues Measure über Menüband](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Wenn Sie ein Measure über das Menüband erstellen, kann es in jeder beliebigen Tabelle erstellt werden. Es ist aber einfacher zu finden, wenn Sie es an der vorgesehenen Stelle erstellen. Wählen Sie in diesem Fall zuerst die Tabelle **Sales** aus, um sie zu aktivieren, und dann **Neues Measure** aus. 
    
    Die Bearbeitungsleiste wird oben im Berichtszeichenbereich angezeigt, wo Sie Ihr Measure umbenennen und eine DAX-Formel eingeben können.
    
    ![Bearbeitungsleiste](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
1. Standardmäßig heißt ein neues Measure *Measure*. Wenn Sie es nicht umbenennen, werden weitere neue Measures als *Measure 2*, *Measure 3* usw. benannt. Damit Sie Ihre Measures besser identifizieren können, markieren Sie *Measure* auf der Bearbeitungsleiste, und ändern Sie den Namen in *Net Sales* (Nettoumsatz).
    
1. Beginnen Sie mit dem Eingeben Ihrer Formel. Geben Sie nach dem Gleichzeichen *Sum* (Summe) ein. Während der Eingabe wird eine Dropdownliste mit Vorschlägen angezeigt, die alle DAX-Funktionen enthält, die mit den eingegebenen Buchstaben beginnen. Scrollen ggf. nach unten, um **SUM** in der Liste auszuwählen, und drücken Sie dann die **EINGABETASTE**.
    
    ![Wählen von SUM in Liste](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Eine öffnende Klammer wird zusammen mit einer Dropdownliste mit Vorschlägen für die verfügbaren Spalten angezeigt, die Sie an die SUM-Funktion übergeben können.
    
    ![Auswählen der Spalte](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
1. Ausdrücke treten immer zwischen einer öffnenden und einer schließenden Klammer auf. Der Ausdruck in diesem Beispiel enthält ein einzelnes Argument, das an die SUM-Funktion übergeben werden muss: die Spalte **SalesAmount**. Beginnen Sie mit der Eingabe von *SalesAmount*, bis in der Liste nur noch der Wert **Sales(SalesAmount)** angezeigt wird. 

    Der Spaltenname, dem der Tabellenname vorangestellt ist, wird als vollqualifizierter Name der Spalte bezeichnet. Vollqualifizierte Spaltennamen verbessern die Lesbarkeit Ihrer Formeln.
    
    ![Auswählen von SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
1. Wählen Sie in der Liste **Sales[SalesAmount]** aus, und geben Sie dann eine schließende Klammer ein.
    
    > [!TIP]
    > Syntaxfehler werden meistens durch eine fehlende oder falsch platzierte schließende Klammer verursacht.
    
    
    
1. Subtrahieren Sie die anderen beiden Spalten in der Formel:

    a. Geben Sie nach der schließenden Klammer für den ersten Ausdruck ein Leerzeichen, einen Minusoperator (-) und ein weiteres Leerzeichen ein. 

    b. Geben Sie eine weitere SUM-Funktion ein, und beginnen Sie mit der Eingabe von *DiscountAmount*, bis Sie die Spalte **Sales[DiscountAmount]** als Argument auswählen können. Fügen Sie eine schließende Klammer hinzu. 

    c. Geben Sie ein Leerzeichen, einen Minusoperator, ein Leerzeichen, eine weitere SUM-Funktion mit **Sales[ReturnAmount]** als Argument und dann eine schließende Klammer ein.
    
    ![Vollständige Formel](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
1. Drücken Sie die **EINGABETASTE**, oder klicken Sie auf der Bearbeitungsleiste auf **Commit** (Häkchensymbol), um die Formel abzuschließen und zu validieren. 

    Das validierte Measure **Net Sales** kann jetzt im Bereich **Felder** für die Tabelle **Sales** verwendet werden.
    
    ![Measure „Net Sales“ in der Feldliste der Tabelle „Sales“](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
1. Wenn nicht mehr genügend Platz zur Eingabe einer Formel vorhanden ist oder Sie möchten, dass sie in separaten Zeilen steht, wählen Sie den nach unten zeigenden Pfeil auf der rechten Seite der Bearbeitungsleiste aus, um mehr Platz zu schaffen. 

    Der nach unten zeigende Pfeil zeigt jetzt nach oben, und ein großes Feld wird angezeigt.

    ![Nach oben zeigender Pfeil für Formel](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

1. Trennen Sie Teile der Formel durch Drücken von **ALT** + **EINGABETASTE** auf separate Zeilen auf, oder drücken Sie die **TAB-TASTE**, um Tabstopps hinzuzufügen.

   ![Formel – erweitert](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Verwenden Ihres Measures im Bericht
Fügen Sie das Measure **Net Sales** zum Berichtszeichenbereich hinzu, und berechnen Sie den Nettoumsatz für alle anderen Felder, die Sie dem Bericht hinzufügen. 

Sehen Sie sich den Nettoumsatz nach Ländern an:

1. Wählen Sie das Measure **Net Sales** aus der Tabelle **Sales**, und ziehen Sie es in den Berichtszeichenbereich.
    
1. Wählen Sie jetzt in der Tabelle **Geography** das Feld **RegionCountryName** aus, und ziehen Sie es in das Diagramm **Net Sales**.
    
    ![Nettoumsatz nach Ländern](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
1. Um den Unterschied zwischen Nettoumsatz und Umsatzbetrag nach Land/Region darzustellen, wählen Sie das Feld **SalesAmount** aus und ziehen es in das Diagramm. 

    ![Umsatzbetrag und Nettoumsatz nach Ländern](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

    Das Diagramm verwendet nun zwei Measures: **SalesAmount**, das von Power BI automatisch summiert wurde, und das von Ihnen manuell erstellte Measure **Net Sales**. Jedes Measure wurde im Kontext eines anderen Felds, nämlich **RegionCountryName**, berechnet.
    
### <a name="use-your-measure-with-a-slicer"></a>Verwenden Ihres Measures mit einem Datenschnitt

Fügen Sie einen Datenschnitt hinzu, um Nettoumsätze und Umsatzbeträge nach Kalenderjahren weiter zu filtern:
    
1. Wählen Sie einen leeren Bereich neben dem Diagramm aus. Wählen Sie im Bereich **Visualisierungen** die Visualisierung **Tabelle** aus. 

    Durch diese Aktion wird im Berichtszeichenbereich eine leere Tabellenvisualisierung erstellt.
    
    ![Neue leere Tabellenvisualisierung](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
1. Ziehen Sie das Feld **Jahr** aus der Tabelle **Kalender** in die neue leere Tabellenvisualisierung. 
    
    Da es sich bei **Jahr** um ein numerisches Feld handelt, summiert Power BI Desktop dessen Werte. Diese Summierung funktioniert jedoch nicht gut als Aggregation, worauf wir im nächsten Schritt eingehen.

    ![Jahr – Aggregation](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3. Wählen Sie im Bereich **Visualisierungen** im Feld **Werte** den nach unten zeigenden Pfeil neben **Jahr** und dann **Nicht zusammenfassen** aus. In der Tabelle werden jetzt einzelne Jahre aufgeführt.
    
    ![„Nicht zusammenfassen“ auswählen](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Wählen Sie im Bereich **Visualisierungen** das Symbol **Datenschnitt** aus, um die Tabelle in einen Datenschnitt zu konvertieren. Wenn die Visualisierung anstelle einer Liste einen Schieberegler anzeigt, wählen Sie im Dropdownmenü des Schiebereglers **Liste** aus.

    ![Konvertieren einer Tabelle in einen Datenschnitt](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Wählen Sie einen beliebigen Wert im Datenschnitt **Jahr** aus, um das Diagramm für **Nettoumsätze und Umsatzbeträge nach RegionCountryName** entsprechend zu filtern. Die Measures **Net Sales** und **SalesAmount** berechnen die Ergebnisse neu und zeigen sie im Kontext des ausgewählten Feldes **Jahr** an. 
    
    ![Diagrammdatenschnitt nach Jahr](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Verwenden Ihres Measures in einem anderen Measure

Sie möchten herausfinden, welche Produkte den höchsten Nettoumsatz pro verkaufter Einheit bringen. Sie benötigen ein Measure, das den Nettoumsatz durch die Menge der verkauften Einheiten dividiert. Erstellen Sie ein neues Measure, das das Ergebnis Ihres Measures **Net Sales** durch die Summe von **Sales[SalesQuantity]** dividiert.

1.  Erstellen Sie im Bereich **Felder** in der Tabelle **Sales** ein neues Measure mit dem Namen **Net Sales per Unit** (Nettoumsatz pro Einheit).
    
1. Beginnen Sie in der Bearbeitungsleiste mit der Eingabe von *Net Sales*. Die Vorschlagsliste zeigt, was Sie hinzufügen können. Wählen Sie **[Net Sales]** aus.
    
    ![Formel mit „Net Sales“](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
1. Sie können außerdem auf Measures verweisen, indem Sie einfach eine öffnende eckige Klammer eingeben ( **[** ). In der Vorschlagsliste werden nur für Ihre Formel geeignete Measures gezeigt.
    
    ![Klammer zeigt nur die Measures](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
1. Geben Sie ein Leerzeichen, einen Divisionsoperator (/), ein weiteres Leerzeichen, eine SUM-Funktion und dann *Quantity* ein. Die Vorschlagsliste zeigt alle Spalten an, deren Name *Quantity* enthält. Wählen Sie **Sales[SalesQuantity]** aus. Geben Sie die schließende Klammer ein, und drücken Sie die **EINGABETASTE**. Oder wählen Sie **Commit** (Häkchensymbol) aus, um Ihre Formel zu validieren. 

    Die resultierende Formel sollte folgendermaßen aussehen:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
1. Wählen Sie in der Tabelle **Sales** das Measure **Net Sales per Unit** aus, und ziehen Sie es an eine leere Stelle im Berichtszeichenbereich. 

    Das Diagramm zeigt für alle verkauften Produkte den Nettoumsatz pro Einheit. Dieses Diagramm ist nicht sehr informativ, worauf wir im nächsten Schritt eingehen.
    
    ![Gesamtnettoumsatz pro Einheit](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
1. Für ein anderes Erscheinungsbild ändern Sie den Visualisierungstyp des Diagramms in **Treemap**.
    
    ![Ändern in Treemap](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
1. Wählen Sie das Feld **Produktkategorie** aus, oder ziehen Sie es auf die Treemap oder das Feld **Gruppe** im Bereich **Visualisierungen**. Jetzt haben Sie verwertbare Informationen.
    
    ![Treemap nach Produktkategorie](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Entfernen Sie das Feld **ProductCategory**, und ziehen Sie stattdessen das Feld **ProductName** in das Diagramm. 
    
    ![Treemap nach Produktname](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
   OK, Sie haben jetzt etwas herumgespielt, aber Sie müssen zugeben, dass es Spaß gemacht hat. Experimentieren Sie mit anderen Möglichkeiten, die Visualisierung zu filtern und zu formatieren.

## <a name="what-youve-learned"></a>Was Sie gelernt haben
Measures sind leistungsstarke Hilfsmittel, wenn es darum geht, aus Ihren Daten die gewünschten Erkenntnisse zu gewinnen. Sie haben gelernt, wie Sie mithilfe der Bearbeitungsleiste Measures erstellen, diese sinnvoll benennen und anhand der DAX-Vorschlagslisten die richtigen Formelelemente finden und auswählen. Sie haben außerdem eine Einführung in Kontext erhalten, wodurch sich das Ergebnis von Berechnungen entsprechend anderer Felder oder anderer Ausdrücke in Ihrer Formel ändert.

## <a name="next-steps"></a>Nächste Schritte
- Weitere Informationen zu Quickmeasures von Power BI Desktop, die Ihnen viele gängige Measureberechnungen bieten, finden Sie unter [Verwenden von Quickmeasures zur einfachen Nutzung gängiger und leistungsstarker Berechnungsfunktionen](desktop-quick-measures.md).
  
- Wenn Sie tiefer in DAX-Formeln einsteigen und fortgeschrittenere Measures erstellen möchten, lesen Sie [DAX-Grundlagen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Dieser Artikel konzentriert sich auf grundlegende Konzepte in DAX, wie etwa Syntax, Funktionen und ein tiefer gehendes Verständnis von Kontext.
  
- Denken Sie daran, die [DAX-Referenz (Data Analysis Expressions)](https://docs.microsoft.com/dax/index) zu Ihren Favoriten hinzuzufügen. In dieser Referenz finden Sie detaillierte Informationen zur DAX-Syntax, zu Operatoren und den über 200 DAX-Funktionen.

