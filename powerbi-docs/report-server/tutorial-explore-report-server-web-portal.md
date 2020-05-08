---
title: 'Tutorial: Erkunden von Power BI-Berichtsserver auf einem virtuellen Computer'
description: In diesem Tutorial erstellen Sie einen virtuellen Computer, auf dem Power BI-Berichtsserver bereits installiert ist, und erkunden das Webportal.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: tutorial
ms.date: 05/06/2019
ms.author: maggies
ms.openlocfilehash: 312b86f9e0c0dda0c9c943520c74286e0458acef
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79207020"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>Tutorial: Erkunden des Power BI-Berichtsserver-Webportals auf einem virtuellen Computer
In diesem Tutorial erstellen Sie einen virtuellen Azure-Computer mit bereits installiertem Power BI-Berichtsserver, sodass Sie das Anzeigen, Bearbeiten und Verwalten von Power BI-Beispielberichten und paginierten Berichten sowie KPIs üben können.

![Webportal von Berichtsserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

Folgende Aufgaben führen Sie in diesem Tutorial aus:

> [!div class="checklist"]
> * Erstellen eines virtuellen Computers und Herstellen einer Verbindung mit diesem Computer
> * Starten und Erkunden des Power BI-Berichtsserver-Webportals
> * Markieren eines Favoriten
> * Anzeigen und Bearbeiten eines Power BI-Berichts
> * Anzeigen, Verwalten und Bearbeiten eines paginierten Berichts
> * Anzeigen einer Excel-Arbeitsmappe in Excel Online

Für dieses Tutorial benötigen Sie ein Azure-Abonnement. Wenn Sie noch keins besitzen, erstellen Sie ein [kostenloses Konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F), bevor Sie beginnen.

## <a name="create-a-power-bi-report-server-vm"></a>Erstellen eines virtuellen Computers mit Power BI-Berichtsserver

Das Power BI-Team hat einen virtuellen Computer erstellt, auf dem Power BI-Berichtsserver bereits installiert ist.

1. Wählen Sie im Azure Marketplace den Power BI-Berichtsserver aus. Über diesen Link können Sie ihn direkt öffnen: [Power BI-Berichtsserver](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview).  

2. Wählen Sie **Jetzt anfordern** aus.
3. Um den Nutzungsbedingungen und der Datenschutzrichtlinie des Anbieters zuzustimmen, klicken Sie auf **Fortfahren**.

4. Wählen Sie **Erstellen** aus.

    ![Erstellen eines virtuellen Computers mit Power BI-Berichtsserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create.png)

5. Geben Sie in **Schritt 1 – Grundlagen** **reportservervm** als **VM-Name** ein.

    Der Name des Power BI-Berichtsservers darf keine Bindestriche enthalten.

5. Erstellen Sie einen Benutzername und ein Kennwort.

6. Wählen Sie unter **Ressourcengruppe** die Option **Neu erstellen** aus, und geben Sie den Namen **reportserverresourcegroup** > **OK** ein.

    Wenn Sie mehrmals das Tutorial durchlaufen, müssen Sie der Ressourcengruppe nach dem ersten Mal einen anderen Namen geben. Sie können denselben Ressourcengruppennamen nicht zweimal in einem Abonnement verwenden. 

    ![Benennen des virtuellen Computers und der Ressourcengruppe](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

7. Behalten Sie die anderen Standardwerte bei, und klicken Sie auf **OK**.

8. Behalten Sie in **Schritt 2 – Einstellungen** die Standardwerte bei, und klicken Sie auf **OK**.
 
    Die Werte von **SQL-Speicherkonto** und **Diagnosespeicherkonto** müssen ebenfalls eindeutig sein. Wenn Sie das Tutorial mehrmals durchlaufen, müssen Sie ihnen jeweils andere Namen geben.

9. Überprüfen Sie in **Schritt 3 – Übersicht** Ihre Auswahl > **OK**.

10. Lesen Sie in **Schritt 4 – Kaufen** die Nutzungsbedingungen und die Datenschutzrichtlinie, und klicken Sie auf **Erstellen**.

    Der Prozess **Bereitstellung für Power BI-Berichtsserver wird übermittelt** kann einige Minuten dauern.

## <a name="connect-to-your-virtual-machine"></a>Herstellen einer Verbindung mit dem virtuellen Computer

1. Wählen Sie im Navigationsbereich von Azure die Option **Virtuelle Computer** aus. 

2. Geben Sie im Feld **Nach Name filtern** den Begriff „Report“ ein. 

3. Wählen Sie den virtuellen Computer namens **REPORTSERVERVM** aus.

    ![Anzeigen des virtuellen Computers](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. Klicken Sie im virtuellen Computer REPORTSERVERVM auf die Option **Verbinden**.

    ![Herstellen einer Verbindung mit dem virtuellen Computer](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. Behalten Sie im Bereich **Verbindung mit virtuellem Computer herstellen** die Standardwerte bei, und wählen Sie **RDP-Datei herunterladen** aus.

1. Klicken Sie im Dialogfeld **Remotedesktopverbindung** auf **Verbinden**.

6. Geben Sie den Namen und das Kennwort ein, den bzw. das Sie für den virtuellen Computer erstellt haben, und klicken Sie auf **OK**.

7. Das nächste Dialogfeld informiert darüber, dass die **Identität des Remotecomputers nicht identifiziert werden** kann. Klicken Sie auf **OK**.

   Voilà! Ihr neuer virtueller Computer wird geöffnet.

## <a name="power-bi-report-server-on-the-vm"></a>Power BI-Berichtsserver auf dem virtuellen Computer

Wenn der virtuelle Computer geöffnet wird, werden auf dem Desktop folgende Elemente angezeigt.

![Virtueller Computer mit Power BI-Berichtsserver nach dem Start](media/tutorial-explore-report-server-web-portal/power-bi-report-server-vm-5-numbers.png)

|Zahl  |Beschreibung  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Power BI-Beispielberichte (PBIX) |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Links zur Dokumentation zu Power BI-Berichtsserver |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Startet die für Power BI-Berichtsserver optimierte Power BI Desktop-Anwendung (Januar 2019) |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) | Öffnet das Webportal von Power BI-Berichtsserver im Browser |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Startet SQL Server Data Tools zum Erstellen paginierter Berichte (RDL) |

Doppelklicken Sie auf das Symbol **Berichtsserver-Webportal**. Der Browser öffnet die Seite `https://localhost/reports/browse`. Im Webportal sehen Sie verschiedene Dateien nach Typ gruppiert. 

![Webportal von Power BI-Berichtsserver](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|Zahl  |Beschreibung  |
|---------|---------|
|![Nummer 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Im Webportal erstellte KPIs |
|![Nummer 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Power BI-Berichte (PBIX)  |
|![Nummer 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Im Publisher für mobile Berichte von SQL Server erstellte mobile Berichte  |
|![Nummer 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  Im Berichts-Generator oder in SQL Server Data Tools erstellte paginierte Berichte  |
|![Nummer 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Excel-Arbeitsmappen   | 
|![Nummer 6](media/tutorial-explore-report-server-web-portal/number-6.png) | Datenquellen für paginierte Berichte | 


## <a name="tag-your-favorites"></a>Markieren von Favoriten
Sie können die Berichte und KPIs markieren, die Sie als Favoriten wünschen. Sie sind leichter zu finden, da sie alle, sowohl im Webportal als auch in den mobilen Power BI-Apps, im zentralen Ordner „Favoriten“ gesammelt werden. 

1. Klicken Sie rechts oben in der KPI **Profit Margin** auf die Auslassungspunkte ( **...** ), und klicken Sie dann auf **Zu Favoriten hinzufügen**.
   
    ![Zu Favoriten hinzufügen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. Wählen Sie **Favoriten** im Menüband des Webportals aus, um dieses mit den anderen Favoriten auf der Seite „Favoriten“ im Webportal anzuzeigen.
   
    ![Favoriten anzeigen](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. Klicken Sie auf **Durchsuchen**, um wieder zum Webportal zu wechseln.
   
## <a name="view-items-in-list-view"></a>Anzeigen von Elementen in der Listenansicht
Standardmäßig werden die Inhalte des Webportals in der Neben-/Untereinanderansicht angezeigt.

Sie können zur Listenansicht wechseln, in der das gleichzeitige Verschieben oder Löschen mehrerer Elemente einfach ist. 

1. Wählen Sie **Kacheln** > **Liste** aus.
   
    ![Ansicht wechseln](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. Wechseln Sie zurück zur Kachelansicht, indem Sie auf **Liste** > **Kacheln** klicken.

## <a name="power-bi-reports"></a>Power BI-Berichte

Im Webportal können Sie Power BI-Berichte anzeigen und damit interagieren und Power BI Desktop starten.

### <a name="view-power-bi-reports"></a>Anzeigen von Power BI-Berichten

1. Wählen Sie im Webportal unter **Power BI-Berichte** den **Sample Customer Overview Report** aus. Der Bericht wird im Browser geöffnet.

1. Wählen Sie in der Strukturzuordnung den Block „United States“ aus, um zu sehen, wie die verknüpften Werte in den anderen Visuals markiert werden.

    ![Markierter Power BI-Bericht](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>In Power BI Desktop bearbeiten

1. Wählen Sie **In Power BI Desktop bearbeiten** aus.

1. Klicken Sie auf **Zulassen**, um der Website zu erlauben, ein Programm auf Ihrem Computer zu öffnen. 

     Der Bericht wird in Power BI Desktop geöffnet. Beachten Sie den Namen in der oberen Leiste: Power BI Desktop (Januar 2019). Das ist die für Power BI-Berichtsserver optimierte Version.

    Verwenden Sie die Version von Power BI Desktop, die auf der VM installiert ist. Sie können Berichte nicht domänenübergreifend hochladen.

3. Erweitern Sie im Bereich „Felder“ die Tabelle „Customers“, und ziehen Sie das Feld „Occupation“ in den Filterbereich auf Berichtsebene.

    ![Ziehen eines Felds in den Bereich „Filter“](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. Speichern Sie den Bericht.

1. Wechseln Sie wieder zum Bericht im Browser, und klicken Sie auf das Browsersymbol **Aktualisieren**.

    ![Browsersymbol zum Aktualisieren](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. Erweitern Sie den Bereich **Filter** auf der rechten Seite, um den hinzugefügten Filter **Occupation** anzuzeigen. Wählen Sie **Professional** aus.

    ![Gefilterter Power BI-Bericht](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. Klicken Sie auf **Durchsuchen**, um wieder zum Webportal zu wechseln.

## <a name="paginated-rdl-reports"></a>Paginierte Berichte (RDL)

Im Webportal können Sie paginierte Berichte anzeigen und verwalten sowie den Berichts-Generator starten.

### <a name="manage-a-paginated-report"></a>Verwalten eines paginierten Berichts

1. Klicken Sie im Webportal unter **Paginierte Berichte** auf **Weitere Optionen** (...) neben **Sales Order** > **Verwalten**.

1. Wählen Sie **Parameter** aus, ändern Sie den Standardwert für **SalesOrderNumber** zu **SO50689**, und klicken Sie auf  > **Anwenden**.

   ![Festlegen von Berichtsparametern](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. Klicken Sie auf **Durchsuchen**, um wieder zum Webportal zu wechseln.

### <a name="view-a-paginated-report"></a>Anzeigen eines paginierten Berichts

1. Wählen Sie im Webportal die Option **Sales Order** aus.
 
3.  Der Auftrag wird mit dem **Order**-Parameter geöffnet, den Sie festgelegt haben: **SO50689**. 

    ![Parameter für paginierten Bericht](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    Sie können diesen sowie weitere Parameter hier ändern, ohne dabei die Standardwerte zu verändern.

1. Wählen Sie **Order** **SO48339** > **Bericht anzeigen** aus.

4. Sie sehen, dass dies Seite 1 von 2 ist. Klicken Sie auf den Pfeil nach rechts, um die zweite Seite anzuzeigen. Die Tabelle wird auf dieser Seite fortgesetzt.

    ![Seite 2 von 2 des paginierten Berichts](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. Klicken Sie auf **Durchsuchen**, um wieder zum Webportal zu wechseln.

### <a name="edit-a-paginated-report"></a>Bearbeiten eines paginierten Berichts

Sie können paginierte Berichte im Berichts-Generator bearbeiten, den Sie direkt aus dem Browser starten können.

1. Klicken Sie im Webportal auf **Weitere Optionen** (...) neben **Sales Order** > **Im Berichts-Generator bearbeiten**.

1. Klicken Sie auf **Zulassen**, um der Website zu erlauben, ein Programm auf Ihrem Computer zu öffnen.

1. Der Sales Order-Bericht wird in der Designansicht im Berichts-Generator geöffnet.

    ![Designansicht, paginierter Bericht](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. Klicken Sie auf **Ausführen**, um eine Vorschau des Berichts anzuzeigen.

    ![Anzeigen der Vorschau eines paginierten Berichts](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. Schließen Sie den Berichts-Generator, und wechseln Sie wieder in den Browser.

## <a name="view-excel-workbooks"></a>Anzeigen von Excel-Arbeitsmappen

Sie können Excel-Arbeitsmappen in Excel Online in Power BI-Berichtsserver anzeigen und mit ihnen interagieren. 

1. Wählen Sie die Excel-Arbeitsmappe **Office Liquidation Sale.xlsx** aus. Möglicherweise werden Sie zum Eingeben von Anmeldeinformationen aufgefordert. Klicken Sie auf **Abbrechen**. 
    Die Mappe wird im Webportal geöffnet.
1. Klicken Sie im Slicer auf **Appliance**.

    ![Excel Online im Webportal](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. Klicken Sie auf **Durchsuchen**, um wieder zum Webportal zu wechseln.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Nachdem Sie dieses Tutorial beendet haben, löschen Sie die Ressourcengruppe, den virtuellen Computer und alle zugehörigen Ressourcen. 

- Wählen Sie zu diesem Zweck die Ressourcengruppe für den virtuellen Computer aus, und klicken Sie auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie einen virtuellen Computer mit Power BI-Berichtsserver erstellt. Sie haben einige der Funktionen des Webportals ausprobiert und einen Power BI-Bericht sowie einen paginierten Bericht in den jeweiligen Editoren geöffnet. Auf dieser VM sind SSAS-Datenquellen (SQL Server Analysis Services) installiert. Sie können also versuchen, Ihre eigenen Power BI-Berichte und paginierten Berichte mit den gleichen Datenquellen zu installieren. 

Um mehr über die Erstellung von Berichten für Power BI-Berichtsserver zu erfahren, fahren Sie mit den nächsten Schritten fort.

> [!div class="nextstepaction"]
> [Erstellen eines Power BI-Berichts für Power BI-Berichtsserver](./quickstart-create-powerbi-report.md)



