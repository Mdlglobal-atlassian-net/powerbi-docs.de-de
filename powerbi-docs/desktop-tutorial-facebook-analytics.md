---
title: 'Tutorial: Analysieren von Facebook-Daten mit Power BI Desktop'
description: Informationen zum Importieren von Daten aus Facebook und zu deren Verwendung in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 1f5cedba1c32f152cd6e4a9f9f51d0355ac05ce5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77497300"
---
# <a name="tutorial-analyze-facebook-data-by-using-power-bi-desktop"></a>Tutorial: Analysieren von Facebook-Daten mit Power BI Desktop

In diesem Tutorial erfahren Sie, wie Sie Daten aus Facebook importieren und in Power BI Desktop verwenden. Sie verbinden und importieren Daten von der Power BI-Facebook-Seite, wenden Transformationen auf die importierten Daten an und verwenden die Daten in Berichtsvisualisierungen.

> [!WARNING]
> Aufgrund von Berechtigungseinschränkungen der Facebook-App funktionieren die in diesem Artikel beschriebenen Connectorfunktionen zurzeit nicht ordnungsgemäß. Wir arbeiten mit Facebook zusammen, um diese Funktionalität so bald wie möglich wiederherzustellen.


## <a name="connect-to-a-facebook-page"></a>Herstellen der Verbindung mit einer Facebook-Seite

In diesem Tutorial werden Daten von der [Facebook-Seite für Microsoft Power BI](https://www.facebook.com/microsoftbi) verwendet. Um sich mit dieser Seite zu verbinden und Daten zu importieren, benötigen Sie keine besonderen Anmeldeinformationen, sondern lediglich ein persönliches Facebook-Konto.

1. Öffnen Sie Power BI Desktop, und klicken Sie im Dialogfeld **Erste Schritte** oder auf der Registerkarte des Menübands **Home** auf **Daten abrufen**. Klicken Sie anschließend auf **Mehr**.
   
2. Klicken Sie im Dialogfeld **Daten abrufen** in der Gruppe **Onlinedienste** auf die Option **Facebook**, und klicken Sie anschließend auf **Verbinden**.
   
   ![Daten abrufen](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Es wird ein Dialogfeld angezeigt, das Sie vor den Risiken bei der Verwendung eines Drittanbieterdiensts warnt.
   
   ![Warnung vor Drittanbieterdienst](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. Wählen Sie **Weiter** aus. 
   
4. Geben Sie im Dialogfeld **Facebook** den Seitennamen **microsoftbi** als **Benutzernamen** ein. Wählen Sie aus dem Dropdownmenü unter **Verbindung** die Option **Beiträge** aus, und klicken Sie anschließend auf **OK**.
   
   ![Verbinden](media/desktop-tutorial-facebook-analytics/2.png)
   
5. Wenn Sie zur Eingabe von Anmeldeinformationen aufgefordert werden, melden Sie sich mit Ihrem Facebook-Konto an, um Power BI Zugriff auf Ihr Konto zu gewähren.
   
   ![Anmeldeinformationen](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   Nach dem Herstellen der Verbindung mit der Facebook-Seite für Power BI wird Ihnen eine Vorschau der Beitragsdaten auf der Seite angezeigt. 
   
   ![Datenvorschau](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>Strukturieren und Transformieren der importierten Daten

Angenommen, Sie möchten sehen, welche Beiträge im Laufe der Zeit die meisten Kommentare aufweisen. In der Vorschau der Beiträge stellen Sie jedoch fest, dass die Daten von **created_time** schwer zu lesen und zu verstehen sind, und es zu wenige Daten zu Kommentaren gibt. Sie müssen die Daten zunächst strukturieren und bereinigen, damit Sie diese optimal nutzen können. Mit dem Power Query-Editor von Power BI Desktop können Sie dafür die Daten vor oder nach dem Import in Power BI Desktop bearbeiten. 

### <a name="split-the-datetime-column"></a>Unterteilen der Spalte für Datum/Uhrzeit

Unterteilen Sie zunächst die Werte für Datum und Uhrzeit in der Spalte **created_time** für eine bessere Lesbarkeit. 

1. Wählen Sie in der Facebook-Datenvorschau **Bearbeiten** aus. 
   
   ![Datenvorschau – Bearbeiten](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   Der Power Query-Editor von Power BI Desktop wird in einem neuen Fenster geöffnet und zeigt die Datenvorschau von der Facebook-Seite für Power BI an. 
   
   ![Power Query-Editor](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. Wählen Sie die Spalte **created_time** aus. Es handelt sich um den Datentyp **Text**, der durch ein **ABC**-Symbol in der Spaltenüberschrift gekennzeichnet ist. Klicken Sie erst mit der rechten Maustaste auf die Überschrift und anschließend mit der linken auf **Spalte teilen** > **Nach Trennzeichen**. Alternativ können Sie auf der Registerkarte **Home** des Menübands unter der Gruppe **Transformieren** auf **Spalte teilen** > **Nach Trennzeichen** klicken.  
   
   ![Spalte nach Trennzeichen teilen](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. Wählen Sie im Dialogfeld **Spalte nach Trennzeichen teilen** in der Dropdownliste die Option **Benutzerdefiniert** aus, geben Sie das Zeichen **T** in das Eingabefeld ein (welches den Anfang des Uhrzeitteils in den **created_time**-Werten angibt). Klicken Sie anschließend auf **OK**. 
   
   ![Dialogfeld „Spalte nach Trennzeichen teilen“](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   Die Spalte wird in zwei Spalten unterteilt, die die Zeichenfolgen vor und nach dem Trennzeichen *T* enthalten. Die neuen Spalten erhalten die Namen **created_time.1** und **created_time.2**. Power BI hat die Datentypen **Datum** für die erste Spalte und **Uhrzeit** für die zweite Spalte automatisch erkannt und geändert. Die Datums- und Zeitwerte wurden so formatiert, dass sie besser lesbar sind.
   
4. Benennen Sie die beiden Spalten um. Wählen Sie erst die Spalte **created_time.1** aus, und klicken Sie dann in der Gruppe **Beliebige Spalte** auf der Registerkarte **Transformieren** des Menübands auf **Umbenennen**. Alternativ können Sie auch auf die Spaltenüberschrift doppelklicken und den neuen Spaltennamen **created_date** eingeben. Wiederholen Sie diesen Schritt für die Spalte **created_time.2**, und benennen Sie diese in **created_time** um.
   
   ![Neue Datums- und Uhrzeitspalten](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>Erweitern der geschachtelten Spalte

Wenn die Datums- und Zeitdaten Ihren Anforderungen entsprechen, können Sie die Kommentardaten abrufen, indem Sie eine geschachtelte Spalte erweitern. 

1. Klicken Sie im oberen Bereich der Spalte **object_link** auf das Symbol ![Erweiterungssymbol](media/desktop-tutorial-facebook-analytics/14.png), um das Dialogfeld **Expand/Aggregate** (Erweitern/Aggregieren) zu öffnen. Wählen Sie **Verbindungen**, und wählen Sie dann **OK**. 
   
   ![Erweitern von „object_link“](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   Die Spaltenüberschriften werden in **object_link.connections** geändert.
2. Klicken Sie im oberen Bereich der Spalte **object_link.connections** auf das Symbol ![Erweiterungssymbol](media/desktop-tutorial-facebook-analytics/14.png), und klicken Sie anschließend auf **Kommentare** und **OK**. Die Spaltenüberschriften werden in **object_link.connections.comments** geändert.
   
3. Klicken Sie im oberen Bereich der Spalte **object_link.connections.comments** auf das Symbol ![Erweiterungssymbol](media/desktop-tutorial-facebook-analytics/14.png), und klicken Sie diesmal im Dialogfeld auf **Aggregieren** anstatt auf **Erweitern**. Wählen Sie **# Anzahl von ID**, und wählen Sie dann **OK**. 
   
   ![Aggregieren von Kommentaren](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   In der Spalte wird nun die Anzahl von Kommentaren für jede Nachricht angezeigt. 
   
4. Benennen Sie die Spalte **Anzahl von object_link.connections.comments.id** in **Anzahl von Kommentaren** um.
   
5. Klicken Sie neben der Spaltenüberschrift **Number of comments** (Anzahl von Kommentaren) auf den Pfeil nach unten und auf **Absteigend sortieren**, um die Beiträge absteigend nach Kommentaren zu sortieren. 
   
   ![Kommentare pro Nachricht](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>Überprüfen der Abfrageschritte

Während Sie Daten im Power Query-Editor strukturieren und transformieren, wird jeder Schritt auf der rechten Seite des **Power Query-Editor**-Fensters im Bereich **Abfrageeinstellungen** im Abschnitt **Angewendete Schritte** aufgezeichnet. Sie können sich dann später die **angewendeten Schritte** noch mal ansehen, um herauszufinden, welche Änderungen Sie vorgenommen haben, und die Schritte bearbeiten, löschen oder bei Bedarf neu anordnen. Gehen Sie vorsichtig vor, wenn Sie diese Schritte ändern, da die Änderung einzelner Schritte Auswirkungen auf nachfolgende Schritte haben kann. 

Wenn Sie die bisher erläuterten Datentransformationen angewendet haben, sollte der Abschnitt **Angewendete Schritte** wie folgt aussehen:
   
   ![Angewendete Schritte](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >Den **angewendeten Schritten** liegen Formeln zugrunde, die in der [Power Query-Formelsprache M](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language) geschrieben sind. Zum Anzeigen und Bearbeiten der Formeln wählen Sie in der Registerkarte **Start** des Menübands in der Gruppe **Abfrage** die Option **Erweiterter Editor** aus. 

### <a name="import-the-transformed-data"></a>Importieren der transformierten Daten

Wenn Sie mit den Daten zufrieden sind, klicken Sie auf der Registerkarte **Home** des Menübands auf **Close & Apply** (Schließen und übernehmen)  > **Close & Apply** (Schließen und übernehmen), um sie in Power BI Desktop zu importieren. 
   
   ![Schließen und übernehmen](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   Dann wird ein Dialogfeld angezeigt, in dem Sie den Status des Ladevorgangs der Daten in das Datenmodell von Power BI Desktop verfolgen können. 
   
   ![Die Daten werden geladen.](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   Sobald die Daten geladen sind, werden sie in der **Berichtsansicht** im Bereich **Felder** als neue Abfrage angezeigt.
   
   ![Neue Abfrage](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>Verwenden der Daten in Berichtvisualisierungen 

Nachdem Sie die Daten von der Facebook-Seite importiert haben, können Sie mithilfe von Visualisierungen schnell und einfach Einblicke in Ihre Daten erhalten. Die Erstellung einer Visualisierung ist denkbar einfach: Wählen Sie ein Feld aus, oder ziehen Sie es aus dem Bereich **Felder** in die Berichtscanvas.

### <a name="create-a-bar-chart"></a>Erstellen eines Balkendiagramms

1. Klicken Sie in der **Berichtsansicht** von Power BI Desktop im Bereich **Felder** auf die Option **Nachricht**, oder ziehen Sie sie in die Berichtscanvas. Eine Tabelle mit allen Beitragsnachrichten wird im Zeichenbereich angezeigt. 
   
   ![Neue Abfrage](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. Wenn Sie diese Tabelle ausgewählt haben, klicken Sie im Bereich **Felder** auf **Number of comments** (Anzahl von Kommentaren), oder ziehen Sie sie in die Tabelle. 
   
3. Klicken Sie im Bereich **Visualisierungen** auf das Symbol **Gestapeltes Balkendiagramm**. Die Tabelle wird in ein Balkendiagramm geändert, das die Anzahl von Kommentaren pro Beitrag zeigt. 
   
   ![Balkendiagramm](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. Klicken Sie neben der Visualisierung auf die Auslassungspunkte (...), um **Weitere Optionen** abzurufen, und klicken Sie dann auf **Sortieren nach** > **Number of comments** (Anzahl von Kommentaren), um die Tabelle nach absteigender Anzahl von Kommentaren zu sortieren. 

   Beachten Sie, dass die meisten Kommentare mit **(Leeren)** Nachrichten verbunden waren (diese Beiträge können Geschichten, Links, Videos oder andere Inhalte ohne Text gewesen sein). 
   
5. Sie können leere Zeilen herausfiltern, indem Sie erst im Bereich **Filter** auf **message is (All)** (Nachricht ist (Alle)) und dann auf **Alle auswählen** klicken. Klicken Sie dann auf **(Leer)** , um die Auswahl aufzuheben. 

   Der Eintrag im Bereich **Filter** wird in **message is not (Blank)** (Nachricht ist nicht (Leer)) geändert, und die Zeile **(Leer)** wird nicht mehr in der Diagrammvisualisierung angezeigt.
   
   ![Zeile „Leere herausfiltern“](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>Formatieren der Tabelle

Die Visualisierung wird interessanter, allerdings können Sie nicht viel vom Beitragstext im Diagramm sehen. So zeigen Sie mehr vom Beitragstext an

1. Vergrößern Sie das Diagramm über die Handles der Diagrammvisualisierung soweit wie möglich. 
   
2. Wählen Sie das Diagramm aus, und klicken Sie im Bereich **Visualisierung** auf das **Formatierungssymbol** (Farbroller).
   
3. Klicken Sie neben der **Y-Achse** auf den Pfeil nach unten, und ziehen Sie den Schieberegler für die **Maximale Größe** ganz nach rechts (**50 %** ). 
4. Verringern Sie zudem die **Textgröße** auf **10 Punkt**, damit mehr Text hineinpasst.
   
   ![Formatierungsänderungen](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   Im Diagramm sind nun die meisten Beitragsinhalte zu sehen. 
   
   ![Anzeigen weiterer Beiträge](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
Auf der X-Achse (number of comments (Anzahl von Kommentaren)) des Diagramms werden keine genauen Werte angezeigt, und sie sieht am unteren Ende des Diagramms ein bisschen verloren aus. Verwenden Sie stattdessen Datenbezeichnungen: 

1. Wählen Sie das **Formatsymbol** aus, und legen Sie den Schieberegler für die **X-Achse** auf **Aus** fest. 
   
2. Legen Sie den Schieberegler für die **Datenbeschriftungen** auf **Ein** fest. 

   Jetzt wird im Diagramm die genaue Anzahl von Kommentaren für jeden Beitrag angezeigt.
   
   ![Anwenden von Datenbeschriftungen](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>Bearbeiten des Datentyps

Das Diagramm sollte nun schon viel besser aussehen, die Datenbeschriftungen haben jedoch noch alle eine Nachkommastelle ( **,0**). Dies ist störend und irreführend, da die **Anzahl von Beiträgen** eine ganze Zahl sein muss. Daher müssen Sie den Datentyp für die Spalte **Number of posts** (Anzahl von Beiträgen) in **Ganze Zahl** ändern:

1. Klicken Sie im Bereich **Felder** mit der rechten Maustaste auf **Query1** (Abfrage1), oder zeigen Sie auf den Bereich, und klicken Sie auf die Auslassungszeichen (...), um **Weitere Optionen** anzuzeigen. 

2. Klicken Sie im Kontextmenü auf **Abfrage bearbeiten**. Alternativ können Sie auch auf der Registerkarte **Home** des Menübands für die Gruppe **Externe Daten** auf **Abfragen bearbeiten** > **Abfragen bearbeiten** klicken. 
   
3. Klicken Sie im Fenster **Power Query-Editor** auf die Spalte **Number of comments** (Anzahl von Kommentaren), und ändern Sie den Datentyp, indem Sie einen der folgenden Schritte ausführen: 
   - Klicken Sie auf das Symbol **1.2** neben der Spaltenüberschrift **Number of comments** (Anzahl von Kommentaren), und wählen Sie anschließend aus der Dropdownliste die Option **Ganze Zahl** aus.
   - Klicken Sie hierzu mit der rechten Maustaste auf die Spaltenüberschrift und anschließend mit der linken auf **Typ ändern**  > **Ganze Zahl**.
   - Klicken Sie auf **Datentyp auswählen > Dezimalzahl** auf der Registerkarte **Home** in der Gruppe **Transformieren** oder auf die Option **Ganze Zahl** auf der Registerkarte **Transformieren** in der Gruppe **Beliebige Spalte**.
   
   Das Symbol in der Spaltenüberschrift wird in **123** geändert und weist so auf den Datentyp **Ganze Zahl** hin.
   
   ![Ändern des Datentyps](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. Sie können die Änderungen übernehmen, indem Sie auf **Datei** > **Close & Apply** (Schließen und Anwenden) oder auf **Datei** > **Anwenden** klicken, damit das Fenster **Power Query-Editor** nicht geschlossen wird. 

   Sobald die Änderungen geladen sind, werden die Datenbeschriftungen im Diagramm als ganze Zahlen angezeigt.
   
   ![Diagramm mit ganzen Zahlen](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>Erstellen eines Datenschnitts

Angenommen, Sie möchten die Anzahl von Kommentaren zu Beiträgen im Zeitverlauf visualisieren. Sie können eine Datenschnittvisualisierung erstellen, um die Diagrammdaten für verschiedene Zeitabschnitte zu filtern. 

1. Klicken Sie erst auf eine leere Stelle in der Canvas, und dann im Bereich **Visualisierungen** auf das **Datenschnittsymbol**. 

   Es wird eine leere Datenschnittvisualisierung angezeigt.
   
   ![Auswählen des Datenschnittsymbols](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. Wählen Sie aus dem Bereich **Felder** das Feld **created_date** aus, oder ziehen Sie es in den neuen Datenschnitt. 

   Der Datenschnitt wird basierend auf dem Datentyp **Datum** des Felds in einen Datumsschieberegler geändert.
   
   ![Datenschnitt mit Datumsschieberegler](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. Verschieben Sie die Schieberegler-Ziehpunkte, um einen anderen Datumsbereich zu wählen, und sehen Sie, wie die Diagrammdaten entsprechend gefiltert werden. Sie können auch die Datumsfelder im Datenschnitt verwenden, um bestimmte Daten einzugeben, oder Sie wählen die Daten im Popupkalender aus.
    
   ![Datenschnitt](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>Formatieren der Visualisierungen

Geben Sie dem Diagramm einen aussagekräftigeren und attraktiveren Titel: 

1. Wählen Sie das Diagramm aus, und klicken Sie auf das **Formatierungssymbol** im Bereich **Visualisierungen**. Klicken Sie anschließend neben dem **Titel** auf den Pfeil, um das entsprechende Dropdownmenü aufzuklappen.

2. Ändern Sie **Titeltext** in **Kommentare pro Beitrag**. 

3. Klicken Sie auf den Dropdownpfeil neben der Option **Schriftfarbe**, und wählen Sie eine grüne Farbe aus, passend zu den grünen Balken der Visualisierung.

4. Erhöhen Sie die **Textgröße** auf **10 Punkt**, und ändern Sie die **Schriftfamilie** in **Segoe (Fett)** .

5. Experimentieren Sie mit anderen Formatierungsoptionen und Einstellungen, um das Aussehen Ihrer Visualisierungen zu ändern. 

   ![Visualisierungen](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>Erstellen weiterer Visualisierungen

Wie Sie sehen können, ist das Anpassen von Visualisierungen in Berichten wirklich einfach, um so Ihre Daten in der gewünschten Weise zu präsentieren. Verwenden Sie zum Beispiel die importierten Facebook-Daten, um dieses Liniendiagramm mit der Anzahl von Kommentaren im Zeitverlauf zu erstellen.

![Liniendiagramm](media/desktop-tutorial-facebook-analytics/moreviz.png)

Power BI Desktop bietet ein nahtloses End-to-End-Erlebnis, das vom Abrufen der Daten aus einer Vielzahl von Datenquellen über die Strukturierung der Daten für Analysezwecke bis zur Visualisierung dieser Daten auf umfassende und interaktive Weise reicht. Sobald Ihr Bericht fertig ist, können Sie ihn [im Power BI-Dienst hochladen](desktop-upload-desktop-files.md) und auf dessen Grundlage Dashboards erstellen, die Sie für andere Power BI-Benutzer freigeben können.

## <a name="next-steps"></a>Nächste Schritte
* [Weitere Tutorials zu Power BI Desktop lesen](https://go.microsoft.com/fwlink/?LinkID=521937)
* [Videos zu Power BI Desktop ansehen](https://go.microsoft.com/fwlink/?LinkID=519322)
* [Power BI-Forum besuchen](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Power BI-Blog lesen](https://go.microsoft.com/fwlink/?LinkID=519327)

