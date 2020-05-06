---
title: Erstellen eines Power BI-Berichts für den Power BI-Berichtsserver
description: Erfahren Sie, wie Sie in wenigen einfachen Schritten einen Power BI-Bericht für Power BI-Berichtsserver erstellen.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/03/2020
ms.author: maggies
ms.openlocfilehash: 69ebfa9b1d2ef500b388a1bbb57926dc53ff2607
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76975008"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>Erstellen eines Power BI-Berichts für den Power BI-Berichtsserver
Sie können Power BI-Berichte lokal im Webportal von Power BI-Berichtsserver ebenso wie in der Cloud im Power BI-Dienst https://powerbi.com) speichern und verwalten. Sie erstellen und bearbeiten Berichte in Power BI Desktop und veröffentlichen sie im Webportal. Anschließend können Leser in Ihrer Organisation die Berichte in einem Browser oder einer mobilen Power BI-App auf einem Mobilgerät anzeigen.

![Power BI-Bericht im Webportal](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Hier finden Sie vier einfache Schritte, um Ihnen den Einstieg zu erleichtern.

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Schritt 1: Installieren von für Power BI-Berichtsserver optimiertem Power BI Desktop

Wenn Sie bereits Power BI-Berichte in Power BI Desktop erstellt haben, ist das Erstellen von Power BI-Berichten für Power BI-Berichtsserver auch nicht mehr schwer. Wir empfehlen die Installation der Version von Power BI Desktop, die für Power BI-Berichtsserver optimiert ist, damit Sie sicher sein können, dass Server und App stets synchron sind. Es können beide Versionen von Power BI Desktop auf demselben Computer installiert sein.

1. Wählen Sie im Report Server Web-Portal die **herunterladen** Pfeil > **Power BI Desktop**.

    ![Power BI Desktop aus dem Webportal herunterladen](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    Oder besuchen Sie die Startseite des [Power BI-Berichtsservers](https://powerbi.microsoft.com/report-server/), und wählen Sie **Erweiterte Downloadoptionen** aus.

2. Wählen Sie im Download Center **Download** aus.

3. Wählen Sie abhängig von Ihrem Computer eine der folgenden Versionen aus:

    - **PBIDesktopRS.msi** (32-Bit-Version) oder

    - **PBIDesktopRS_x64.msi** (64-Bit-Version).

4. Nachdem Sie das Installationsprogramm heruntergeladen haben, führen Sie den Setup-Assistenten für Power BI Desktop (September 2019) aus.

2. Aktivieren Sie am Ende des Installationsvorgangs **Power BI Desktop jetzt starten**.
   
    Die App wird automatisch gestartet, sodass Sie gleich loslegen können. Anhand des Texts **Power BI Desktop (September 2019)** auf der Titelleiste erkennen Sie, dass Sie über die richtige Version verfügen.

    ![Power BI Desktop September 2019](media/quickstart-create-powerbi-report/power-bi-report-server-desktop-sept-2019.png)

3. Wenn Sie mit Power BI Desktop nicht vertraut sind, wird empfohlen, sich die Videos auf dem Begrüßungsbildschirm anzusehen.
   
    ![Startbildschirm von Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Schritt 2: Auswählen einer Datenquelle
Sie können Verbindungen mit einer Vielzahl von Datenquellen herstellen. Erfahren Sie mehr über das [Verbinden mit Datenquellen](connect-data-sources.md).

1. Klicken Sie auf dem Begrüßungsbildschirm auf **Daten abrufen**.
   
    Oder klicken Sie auf der Registerkarte **Start** auf **Daten abrufen**.
2. Wählen Sie Ihre Datenquelle (in diesem Beispiel **Analysis Services**) aus.
   
    ![Datenquelle auswählen](media/quickstart-create-powerbi-report/power-bi-report-server-get-data-ssas.png)
3. Füllen Sie **Server** und optional **Datenbank** aus. Stellen Sie sicher, dass **Live verbinden** ausgewählt ist, und klicken Sie auf **OK**.
   
    ![Servername](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Wählen Sie den Berichtsserver aus, auf dem Sie die Berichte speichern.
   
    ![Auswahl des Berichtsservers](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Schritt 3: Entwerfen des Berichts
Hier ist Kreativität gefragt, denn Sie erstellen nun die Visuals zum Veranschaulichen Ihrer Daten.

Sie können z.B. ein Trichterdiagramm von Kunden und Gruppenwerten nach Jahreseinkommen erstellen.

![Bericht entwerfen](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. Wählen Sie in **Visualisierungen** die Option **Trichterdiagramm** aus.
2. Ziehen Sie das zu zählende Feld in den Bereich **Werte**. Wenn es sich nicht um ein numerisches Feld handelt, wird es von Power BI Desktop automatisch als *Anzahl* des Werts angezeigt.
3. Ziehen Sie das Feld, anhand dessen gruppiert wird, in den Bereich **Gruppe**.

Erfahren Sie mehr über das [Entwerfen eines Power BI-Berichts](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Schritt 4: Speichern des Berichts auf dem Berichtsserver
Wenn Ihr Bericht fertig ist, speichern Sie ihn auf dem Power BI-Berichtsserver, den Sie in Schritt 2 ausgewählt haben.

1. Klicken Sie im Menü **Datei** auf **Speichern unter** > **Power BI-Berichtsserver**.
   
    ![Auf dem Berichtsserver speichern](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Jetzt können Sie ihn im Webportal anzeigen.
   
    ![Den Bericht im Webportal anzeigen](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)
    
> [!NOTE]
> Falls Sie den Bericht zu einem späteren Zeitpunkt noch einmal bearbeiten möchten, entsprechen die in Power BI Desktop angezeigten Berichtsdaten immer den zwischengespeicherten Daten, die Sie bei der Erstellung des Berichts verwendet haben.  Wenn Sie möchten, dass beim Bearbeiten des Berichts aktuelle Daten angezeigt werden, müssen Sie die Daten in der Power BI Desktop-Anwendung aktualisieren.

## <a name="next-steps"></a>Nächste Schritte
### <a name="power-bi-desktop"></a>Power BI Desktop
Power BI Desktop bietet zahlreiche nützliche Ressourcen zum Erstellen von Berichten. Dieser Link ist ein guter Ausgangspunkt.

* [Erste Schritte mit Power BI Desktop](../desktop-getting-started.md)
* Lernen mit Anleitungen: [Power BI Desktop im Überblick](/learn/modules/get-data-power-bi/2-getting-started-power-bi-desktop)

### <a name="power-bi-report-server"></a>Power BI-Berichtsserver
* [Installieren von für Power BI-Berichtsserver optimiertem Power BI Desktop](install-powerbi-desktop.md)  
* [Was ist der Power BI-Berichtsserver?](get-started.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
