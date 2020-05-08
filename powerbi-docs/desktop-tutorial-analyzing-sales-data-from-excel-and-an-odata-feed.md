---
title: 'Tutorial: Kombinieren von Daten aus Excel und einem OData-Feed in Power BI Desktop'
description: 'Tutorial: Kombinieren von Daten aus Excel und einem OData-Feed'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0e3f742e0ad9d3b9bf81c9dd95e9193413a70d6a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76540019"
---
# <a name="tutorial-analyze-sales-data-from-excel-and-an-odata-feed"></a>Tutorial: Analysieren von Umsatzdaten aus Excel und einem OData-Feed

Es ist üblich, dass sich Daten an mehreren Datenquellen befinden. Es kann z. B. sein, dass Sie über zwei Datenbanken verfügen, eine für Produktinformationen und eine für Vertriebsinformationen. Mit *Power BI Desktop* können Sie Daten aus verschiedenen Quellen kombinieren, um aufschlussreiche, überzeugende Datenanalysen und Visualisierungen zu erstellen.

In diesem Tutorial kombinieren Sie Daten aus zwei Datenquellen:

* Daten aus einer Excel-Arbeitsmappe mit Produktinformationen
* Daten aus einem OData-Feed mit Bestelldaten

Sie importieren beide Datasets und führen Transformationen und Aggregationen durch. Dann verwenden Sie die Daten aus beiden Datenquellen, um einen Verkaufsanalysebericht mit interaktiven Visualisierungen zu erstellen. Später können Sie diese Verfahren auch auf SQL Server-Abfragen, CSV-Dateien und andere Datenquellen in Power BI Desktop anwenden.

>[!NOTE]
>In Power BI Desktop gibt es oft mehrere Möglichkeiten zum Ausführen einer Aufgabe. Sie können z. B. mit der rechten Maustaste auf **Weitere Optionen** in einer Spalte oder Zelle klicken, um weitere Auswahlmöglichkeiten im Menüband anzuzeigen. In den folgenden Schritten werden mehrere alternative Methoden beschrieben.

## <a name="import-excel-product-data"></a>Importieren von Produktdaten aus Excel

Importieren Sie zunächst die Produktdaten aus der Excel-Arbeitsmappe *Products.xlsx* in Power BI Desktop.

1. [Laden Sie die Excel-Arbeitsmappe „Products.xlsx“ herunter](https://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx), und speichern Sie sie als *Products.xlsx*.

1. Klicken Sie im Power BI Desktop-Menüband auf der Registerkarte **Start** auf den Pfeil neben **Daten abrufen**, und wählen Sie dann im Menü **Am häufigsten verwendet** den Eintrag **Excel** aus.

   ![Daten abrufen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)

   >[!NOTE]
   >Sie können auch das Element **Daten abrufen** selbst auswählen oder im Power BI-Dialogfeld **Erste Schritte** die Option **Daten abrufen** wählen und dann im Dialogfeld **Daten abrufen** auf **Excel** oder **Datei** > **Excel** klicken und **Verbinden** auswählen.

1. Navigieren Sie im Dialogfeld **Öffnen** zur Datei **Products.xlsx**, und wählen Sie sie aus. Klicken Sie dann auf **Öffnen**.

1. Wählen Sie im **Navigator** die Tabelle **Produkte** aus, und klicken Sie dann auf **Daten transformieren**.

   ![Navigatorbereich für Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

Eine Vorschau der Tabelle wird im Power Query-Editor geöffnet, in dem Sie Transformationen zum Bereinigen der Daten anwenden können.

![Power Query-Editor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)

>[!NOTE]
>Sie können den Power Query-Editor auch öffnen, indem Sie in Power BI Desktop im Menüband **Start** auf **Abfragen bearbeiten** > **Abfragen bearbeiten** klicken, indem Sie mit der rechten Maustaste klicken oder indem Sie neben einer Abfrage in der **Berichtsansicht** auf **Weitere Optionen** klicken und **Abfrage bearbeiten** auswählen.

## <a name="clean-up-the-products-columns"></a>Bereinigen der Produktspalten

Ihr kombinierter Bericht verwendet nur die Spalten **ProductID**, **ProductName**, **QuantityPerUnit** und **UnitsInStock** aus der Excel-Arbeitsmappe. Die übrigen Spalten können Sie daher entfernen.

1. Wählen Sie im Power Query-Editor die Spalten **ProductID**, **ProductName**, **QuantityPerUnit** und **UnitsInStock** aus. Sie können mit STRG mehrere Spalten auswählen oder mit UMSCHALT aneinander angrenzende Spalten auswählen.

1. Klicken Sie mit der rechten Maustaste auf einen der ausgewählten Header. Wählen Sie **Andere Spalten entfernen** aus dem Dropdownmenü aus.
   Sie können auch im Menüband auf der Registerkarte **Start** in der Gruppe **Spalten verwalten** auf **Spalten entfernen** > **Andere Spalten entfernen** klicken.

   ![Andere Spalten entfernen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-odata-feeds-order-data"></a>Importieren der Bestelldaten aus dem OData-Feed

Importieren Sie als Nächstes die Auftragsdaten aus dem OData-Feed des Northwind-Beispielvertriebssystems.

1. Klicken Sie im Power Query-Editor auf **Neue Quelle**, und wählen Sie dann **OData-Feed** aus dem Menü **Am häufigsten verwendet** aus.

   ![Abrufen von OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)

1. Fügen Sie im Dialogfeld **OData-Feed** die URL für den Northwind-OData-Feed `https://services.odata.org/V3/Northwind/Northwind.svc/` ein. Wählen Sie **OK** aus.

   ![Dialogfeld „OData-Feed“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)

1. Wählen Sie im **Navigator** die Tabelle **Orders** und anschließend **Daten transformieren** aus, um die Daten in den Power Query-Editor zu laden.

   ![Navigator für OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)

   >[!NOTE]
   >Um eine Vorschau anzuzeigen, können Sie im **Navigator** einen beliebigen Tabellennamen auswählen, ohne das Kontrollkästchen zu aktivieren.

## <a name="expand-the-order-data"></a>Erweitern der Auftragsdaten

Beim Herstellen einer Verbindung mit Datenquellen, die mehrere Tabellen enthalten (z.B. relationale Datenbanken oder der Northwind-OData-Feed), können Sie Verweise zwischen Tabellen verwenden, um Ihre Abfragen zu erstellen. Die Tabelle **Orders** enthält Verweise auf mehrere verknüpfte Tabellen. Sie können die Spalten **ProductID**, **UnitPrice** und **Quantity** aus der verknüpften Tabelle **Order_Details** über die Option „Erweitern“ der betreffenden Tabelle (**Orders**) hinzufügen.

1. Scrollen Sie in der Tabelle **Orders** nach rechts, bis Sie die Spalte **Order_Details** sehen. Sie enthält anstelle von Daten Verweise auf eine andere Tabelle.

   ![Spalte „Order_Details“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/order-details-column.png)

1. Klicken Sie in der Spaltenüberschrift **Order_Details** auf das Symbol **Erweitern** (![Symbol Erweitern](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)).

1. Führen Sie im Dropdownmenü folgende Aktionen aus:

   1. Wählen Sie **(Alle Spalten auswählen)** aus, um alle Spalten zu deaktivieren.

   1. Wählen Sie **ProductID**, **UnitPrice** und **Quantity** aus, und klicken Sie dann auf **OK**.

      ![Dropdownmenü „Aufklappen“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand-drop-down-menu.png)

Wenn Sie die Tabelle **Order_Details** erweitert haben, ersetzen drei neue geschachtelte Tabellenspalten die Spalte **Order_Details**. Die Tabelle enthält neue Zeilen für die hinzugefügten Daten jeder Bestellung.

![Erweiterte Spalten](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expanded-columns.png)

## <a name="create-a-custom-calculated-column"></a>Erstellen einer benutzerdefinierten berechneten Spalte

Im Power Query-Editor können Sie Berechnungen und benutzerdefinierte Felder erstellen, um Ihre Daten anzureichern. Sie erstellen eine benutzerdefinierte Spalte zum Berechnen des Gesamtpreises für die einzelnen Zeilenelemente in einem Auftrag, indem der Einzelpreis mit der Artikelanzahl multipliziert wird.

1. Wählen Sie im Power Query-Editor im Menüband auf der Registerkarte **Spalte hinzufügen** die Option **Benutzerdefinierte Spalte**.

   ![Hinzufügen einer benutzerdefinierten Spalte](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/adding-a-custom-column.png)

1. Geben Sie im Dialogfeld **Benutzerdefinierte Spalte** im Feld **Neuer Spaltenname** den Text **LineTotal** ein.

1. Geben Sie im Feld **Benutzerdefinierte Spaltenformel** nach **=** Folgendes ein: **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . Sie können die Feldnamen auch aus dem Scrollfeld **Verfügbare Spalten** auswählen und auf **<< Einfügen** klicken, statt sie einzugeben.

1. Wählen Sie **OK** aus.

   ![Dialogfeld „Benutzerdefinierte Spalte“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/custom-column-dialog-box.png)

   Das neue Feld **LineTotal** wird als letzte Spalte in der Tabelle **Orders** angezeigt.

## <a name="set-the-new-fields-data-type"></a>Festlegen des Datentyps für das neue Feld

Wenn der Power Query-Editor eine Verbindung mit Daten herstellt, gibt er eine Schätzung des Datentyps jedes Feld zum Anzeigen ab. Ein Headersymbol gibt den zugewiesenen Datentyp jedes Felds an. Auf der Registerkarte **Start** in der Gruppe **Transformieren** können Sie auch unter **Datentyp** weitere Informationen erhalten.

Die neue Spalte **LineTotal** hat den Datentyp **Any**, enthält aber Währungswerte. Klicken Sie zum Zuweisen eines Datentyps mit der rechten Maustaste auf die Spaltenüberschrift **LineTotal**, wählen Sie in der Dropdownliste **Typ ändern** aus, und klicken Sie dann auf **Feste Dezimalzahl**.

![Ändern des Datentyps in eine feste Dezimalzahl](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/change-data-type-to-fixed-decimal.png)

>[!NOTE]
>Sie können auch die Spalte **LineTotal** auswählen, dann im Menüband auf der Registerkarte **Start** im Bereich **Transformieren** auf den Pfeil neben **Datentyp** klicken und anschließend **Feste Dezimalzahl** auswählen.

## <a name="clean-up-the-orders-columns"></a>Bereinigen der Auftragsspalten

Sie können einige der Spalten löschen, umbenennen und neu anordnen, um die Bearbeitung des Modells in Berichten zu vereinfachen.

In Ihrem Bericht werden die folgenden Spalten verwendet:

* **OrderDate**
* **ShipCity**
* **ShipCountry**
* **Order_Details.ProductID**
* **Order_Details.UnitPrice**
* **Order_Details.Quantity**
* **LineTotal**

Wählen Sie diese Spalten aus, und verwenden Sie **Andere Spalten entfernen** wie bei den Excel-Daten. Alternativ können Sie die nicht aufgeführten Spalten verwenden, auf eine davon mit der rechten Maustaste klicken und **Spalten entfernen** auswählen.

Sie können die Spalten mit dem Präfix **Order_Details** umbenennen, damit diese besser gelesen werden können:

1. Doppelklicken oder tippen Sie auf die einzelnen Spaltenüberschriften, oder klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift und in der Dropdownliste dann auf **Umbenennen**.

1. Löschen Sie das Präfix **Order_Details.** aus den einzelnen Namen.

Um schließlich den Zugriff auf die Spalte **LineTotal** zu vereinfachen, ziehen Sie sie nach links, und legen Sie sie rechts neben der Spalte **ShipCountry** ab.

![Bereinigte Tabelle](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/cleaned-up-table.png)

## <a name="review-the-query-steps"></a>Überprüfen der Abfrageschritte

Die Aktionen, die Sie im Power Query-Editor zum Formen und Transformieren von Daten durchführen, werden erfasst. Jeder Schritt wird rechts in den **Abfrageeinstellungen** unter **Angewendete Schritte** angezeigt. Sie können sich die **angewendeten Schritte** noch mal ansehen und diese bearbeiten, löschen oder neu anordnen (falls erforderlich). Wenn Sie vorhergehende Schritte ändern, kann es jedoch sein, dass sich dies negativ auf folgende Schritte auswirkt.

Wählen Sie die einzelnen Abfragen in der Liste **Abfragen** auf der linken Seite des Power Query-Editors aus, und überprüfen Sie die Schritte unter **Angewendete Schritte** in den **Abfrageeinstellungen**. Nach dem Anwenden der vorherigen Datentransformationen sollte der Abschnitt **Angewendete Schritte** für Ihre beiden Abfragen wie folgt aussehen:

![Produktabfrage: angewendete Schritte](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/products-query-applied-steps.png) &nbsp;&nbsp; ![Auftragsabfrage: angewendete Schritte](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orders-query-applied-steps.png)

>[!TIP]
>Den angewendeten Schritten liegen Formeln zugrunde, die in der *Power Query-Sprache*, auch bekannt als [M-Sprache](https://docs.microsoft.com/powerquery-m/power-query-m-reference), geschrieben sind. Zum Anzeigen und Bearbeiten der Formeln wählen Sie in der Registerkarte **Start** des Menübands in der Gruppe **Abfrage** die Option **Erweiterter Editor** aus.

## <a name="import-the-transformed-queries"></a>Importieren der transformierten Abfragen

Wenn Sie mit den transformierten Daten zufrieden sind und diese in Ihre Power BI Desktop-**Berichtsansicht** importieren möchten, klicken Sie auf der Registerkarte **Start** auf dem Menüband in der Gruppe **Schließen** auf **Schließen und übernehmen** > **Schließen und übernehmen**.

![Schließen und übernehmen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Sobald die Daten geladen wurden, werden die Abfragen in der Liste **Felder** in der **Berichtsansicht** von Power BI Desktop angezeigt.

![Abfragen in der Liste „Felder“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/queries-in-fields-list.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Verwalten der Beziehung zwischen den Datasets

Sie müssen in Power BI Desktop keine Abfragen kombinieren, um für diese einen Bericht zu erstellen. Allerdings können Sie die Beziehungen zwischen Datasets, die auf gemeinsamen Feldern beruhen, zum Erweitern und Anreichern Ihre Berichte nutzen. Power BI Desktop kann Beziehungen automatisch erkennen, oder Sie können diese im Power BI Desktop-Dialogfeld **Beziehungen verwalten** erstellen. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Beziehungen in Power BI Desktop](desktop-create-and-manage-relationships.md).

Das Feld `ProductID` erstellt eine Beziehung zwischen den Datasets `Orders` und `Products`, die wir in diesem Tutorial verwenden.

1. Klicken Sie in der **Berichtsansicht** von Power BI Desktop auf der Registerkarte **Start** auf dem Menüband im Bereich **Beziehungen** auf **Beziehungen verwalten**.

   ![Menüband „Beziehungen verwalten“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)

1. Beachten Sie im Dialogfeld **Beziehungen verwalten**, dass Power BI Desktop bereits eine aktive Beziehung zwischen den Tabellen **Products** und **Orders** erkannt und aufgeführt hat. Klicke Sie zum Anzeigen der Beziehung auf **Bearbeiten**.

   ![Dialogfeld „Beziehungen verwalten“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)

   Das Dialogfeld **Beziehung bearbeiten** wird geöffnet und zeigt Details über die Beziehung an.  

   ![Dialogfeld „Beziehung bearbeiten“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)

1. Power BI Desktop hat die Beziehung automatisch richtig erkannt, daher können Sie auf **Abbrechen** und dann auf **Schließen** klicken.

Klicken Sie in Power BI Desktop auf der linken Seite auf **Modell**, um Abfragebeziehungen anzuzeigen und zu verwalten. Doppelklicken Sie auf den Pfeil auf der Verbindungslinie zwischen den beiden Abfragen, um das Dialogfeld **Beziehung bearbeiten** zu öffnen und die Beziehung anzuzeigen oder zu ändern.

![Beziehungsansicht](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Klicken Sie auf das **Berichtssymbol**, um von der **Modellansicht** wieder zur **Berichtsansicht** zu wechseln.

![Symbol für Berichtsansicht](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Erstellen von Visualisierungen mithilfe Ihrer Daten

Sie können in der Ansicht „Überprüfen“ in Power BI Desktop verschiedene Visualisierungen erstellen, um Erkenntnisse aus den Daten zu gewinnen. Berichte können über mehrere Seiten verfügen, und jede Seite kann mehrere Visuals enthalten. Sie und andere Benutzer können mit den Visualisierungen interagieren, um die Daten einfacher zu analysieren und zu verstehen. Weitere Informationen finden Sie unter [Interagieren mit einem Bericht in der Bearbeitungsansicht des Power BI-Diensts](service-interact-with-a-report-in-editing-view.md).

Sie können beide Datasets und die Beziehung zwischen ihnen verwenden, um Ihre Vertriebsdaten zu visualisieren und zu analysieren.

Erstellen Sie zunächst ein gestapeltes Säulendiagramm, das Felder aus beiden Abfragen verwendet, um die Menge der einzelnen bestellten Produkte anzuzeigen.

1. Wählen Sie auf der rechten Seite im Bereich **Felder** unter **Orders** das Feld **Quantity** aus, oder ziehen Sie es auf einen leeren Bereich der Canvas. Dadurch wird ein gestapeltes Säulendiagramm erstellt, das die Gesamtmenge aller bestellten Produkte anzeigt.

1. Klicken Sie im Bereich **Felder** unter **Products** auf **ProductName**, oder ziehen Sie das Element auf das Diagramm, um die Menge der einzelnen bestellten Produkte anzuzeigen.

1. Klicken Sie oben rechts in der Visualisierung auf die Auslassungspunkte **Weitere Optionen** ( **...** ), und klicken Sie dann auf **Sort By Quantity** (Nach Menge sortieren), um die Produkte von den meistbestellten bis zu den am wenigsten bestellten zu sortieren.

1. Verwenden Sie die Handles an den Ecken des Diagramms, um es zu vergrößern, sodass weitere Produktnamen angezeigt werden.

   ![Balkendiagramm mit der Menge nach ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/quantity-by-productname-bar-chart.png)

Als Nächstes erstellen Sie ein Diagramm mit den Geldbeträgen der Aufträge (**LineTotal**) im Zeitverlauf (**OrderDate**).

1. Während in der Canvas nichts ausgewählt ist, klicken Sie im Bereich **Felder** unter **Orders** auf **LineTotal**, oder ziehen Sie das Element in einen leeren Bereich der Canvas. Das gestapelte Säulendiagramm zeigt den Gesamtbetrag aller Aufträge an.

1. Klicken Sie auf das gestapelte Diagramm und unter **Orders** auf **OrderDate**, oder ziehen Sie das Element auf das Diagramm. Das Diagramm zeigt jetzt Zeilengesamtwerte für jedes Auftragsdatum an.

1. Sie können die Größe der Visualisierung durch Ziehen der Ecken anpassen, um weitere Daten anzuzeigen.

   ![Liniendiagramm „LineTotals nach OrderDate“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-orderdate-line-chart.png)

   >[!TIP]
   >Wenn im Diagramm nur **Jahre** angezeigt werden (nur drei Datenpunkte), klicken Sie im Bereich **Visualisierungen** im Feld **Achse** auf den Pfeil neben **OrderDate**, und wählen Sie **OrderDate** anstelle von **Datumshierarchie** aus.

Erstellen Sie abschließend eine Kartenvisualisierung, die die Auftragsmengen aus den einzelnen Ländern zeigt.

1. Während in der Canvas nichts ausgewählt ist, klicken Sie im Bereich **Felder** unter **Orders** auf **ShipCountry**, oder ziehen Sie das Element in einen leeren Bereich der Canvas. Power BI Desktop erkennt, dass es sich bei den Daten um Ländernamen handelt. Dann erstellt es automatisch eine Kartenvisualisierung mit einem Datenpunkt für jedes Land mit den entsprechenden Bestellungen.

1. Wenn Sie möchten, dass die Größe jedes Datenpunkts die Bestellmenge in jedem Land widerspiegelt, können Sie das Feld **LineTotal** auf die Karte ziehen. Sie können es auch im Bereich **Visualisierungen** unter **Größe** zu **Datenfelder hierher ziehen** ziehen. Die Größen der Kreise auf der Karte geben jetzt die Geldbeträge der Aufträge aus den einzelnen Länder wieder.

   ![Kartenvisualisierung „LineTotals nach ShipCountry“](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/linetotals-by-shipcountry-map-visualization.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagieren mit Berichtsvisuals zur weiteren Analyse

Sie können in Power BI Desktop mit Visuals interagieren, die sich gegenseitig hervorheben und filtern, um weitere Trends zu bestimmen. Weitere Informationen finden Sie unter [Filtern und Hervorhebungen in Power BI-Berichten](power-bi-reports-filters-and-highlighting.md).

Aufgrund der Beziehung zwischen Ihren Abfragen wirken sich Interaktionen mit einer Visualisierung auf alle anderen Visualisierungen auf der Seite aus.

Wählen Sie auf der Kartenvisualisierung den Kreis aus, der mitten in **Kanada** liegt. Die beiden anderen Visualisierungen werden so gefiltert, dass sie die Zeilengesamtwerte und Auftragsmengen ausschließlich für Kanada anzeigen.

![Für Kanada gefilterte Vertriebsdaten](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/sales-data-filtered-for-canada.png)

Wählen Sie ein Produkt im Diagramm **Quantity by ProductName** aus, damit die Karte und der Datumsfilter die Daten dieses Produkts anzeigen. Wählen Sie ein Datum im Diagramm **LineTotal by OrderDate** aus, damit die Karte und der Produktfilter die Daten dieses Datums anzeigen.

>[!TIP]
>Um eine Auswahl aufzuheben, wählen Sie sie erneut aus, oder wählen Sie eine der anderen Visualisierungen.

## <a name="complete-the-sales-analysis-report"></a>Abschließen des Umsatzanalyseberichts

Im fertig gestellten Bericht werden Daten aus der Excel-Datei *Products.xlsx* und dem Northwind-OData-Feed zu visuellen Elementen verbunden, die die Analyse von Auftragsinformationen für verschiedene Länder, Zeitrahmen und Produkte ermöglichen. Wenn Ihr Bericht fertig ist, können Sie ihn [in den Power BI-Dienst hochladen](desktop-upload-desktop-files.md), um ihn für andere Power BI-Benutzer freizugeben.

## <a name="next-steps"></a>Nächste Schritte

* [Weitere Tutorials zu Power BI Desktop lesen](/power-bi/guided-learning/)
* [Videos zu Power BI Desktop ansehen](/power-bi/desktop-videos)
* [Power BI-Forum besuchen](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Power BI-Blog lesen](https://go.microsoft.com/fwlink/?LinkID=519327)
