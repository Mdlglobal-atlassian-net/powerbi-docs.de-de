---
title: Installieren von für Power BI-Berichtsserver optimiertem Power BI Desktop
description: Erfahren Sie mehr zum Installieren von für Power BI-Berichtsserver optimiertem Power BI Desktop
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/13/2020
ms.openlocfilehash: dfb6c313e989514da2aa04facd6c6136a0eadc1a
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404180"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Installieren von für Power BI-Berichtsserver optimiertem Power BI Desktop

Damit Sie Power BI-Berichte für Power BI-Berichtsserver erstellen können, müssen Sie die Version von Power BI Desktop herunterladen und installieren, die für Power BI-Berichtsserver optimiert wurde. Diese Version unterscheidet sich von der Power BI Desktop-Version, die mit dem Power BI-Dienst verwendet wird. Beispielsweise enthält die Power BI Desktop-Version für den Power BI-Dienst Previewfunktionen, die erst mit Erreichen der allgemeinen Verfügbarkeit der Version für den Power BI-Berichtsserver zur Verfügung stehen. Sie müssen diese Version verwenden, um sicherzustellen, dass der Berichtsserver mit einer bekannten Version der Berichte und des Modells interagieren kann. 

Power BI Desktop und Power BI Desktop (optimiert für den Power BI-Berichtsserver) können glücklicherweise parallel auf dem gleichen Computer installiert werden.

## <a name="download-and-install-power-bi-desktop"></a>Herunterladen und Installieren von Power BI Desktop

Die einfachste Möglichkeit, um sicherzustellen, dass Sie die aktuelle Version des für Power BI-Berichtsserver optimiertem Power BI Desktop verwenden, besteht darin, zunächst das Webportal des Berichtsservers aufzurufen.

1. Wählen Sie im Report Server Web-Portal die **herunterladen** Pfeil > **Power BI Desktop**.

    ![Power BI Desktop aus dem Webportal herunterladen](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Oder besuchen Sie die Startseite des [Power BI-Berichtsservers](https://powerbi.microsoft.com/report-server/), und wählen Sie **Erweiterte Downloadoptionen** aus.

2. Wählen Sie im Download Center eine Sprache und dann **Download** aus.

3. Wählen Sie abhängig von Ihrem Computer eine der folgenden Versionen aus: 

    - **PBIDesktopRS.msi** (32-Bit-Version) oder
    - **PBIDesktopRS_x64.msi** (64-Bit-Version).

1. Nachdem Sie das Installationsprogramm heruntergeladen haben, führen Sie den Setup-Assistenten für Power BI Desktop (September 2019) aus.

2. Wählen Sie am Ende des Installationsvorgangs **Power BI Desktop starten** aus.

    Die App wird automatisch gestartet, sodass Sie gleich loslegen können.

## <a name="verify-youre-using-the-correct-version"></a>Überprüfen, ob Sie die richtige Version verwenden
Sie können ganz einfach überprüfen, ob Sie die richtige Power BI Desktop-Version verwenden: Schauen Sie sich den Startbildschirm oder die Titelleiste in Power BI Desktop an. Anhand des Texts **Power BI Desktop (September 2019)** auf der Titelleiste erkennen Sie, dass Sie über die richtige Version verfügen. Darüber hinaus sind die Farben des Power BI-Logos umgekehrt, d. h. gelb auf schwarz anstatt schwarz auf gelb.

![Power BI Desktop September 2019](media/install-powerbi-desktop/power-bi-report-server-desktop-sept-2019.png)

Die Power BI Desktop-Version für den Power BI-Dienst gibt Monat und Jahr nicht in der Titelleiste an.

## <a name="file-extension-association"></a>Zuordnung der Dateinamenerweiterung
Wenn Sie Power BI Desktop und Power BI Desktop (optimiert für den Power BI-Berichtsserver) auf demselben Computer installieren, weist die neueste Installation von Power BI Desktop die Dateizuordnung zu PBIX-Dateien auf. Wenn Sie also auf eine PBIX-Datei doppelklicken, wird die Power BI Desktop-Version gestartet, die Sie zuletzt installiert haben.

Wenn Sie Power BI Desktop bereits installiert haben und dann Power BI Desktop (optimiert für den Power BI-Berichtsserver) installieren, werden alle PBIX-Dateien standardmäßig in für den Power BI-Berichtsserver optimiertem Power BI Desktop geöffnet. Wenn Sie möchten, dass beim Öffnen von PBIX-Dateien standardmäßig Power BI Desktop gestartet wird, müssen Sie [Power BI Desktop aus dem Microsoft Store](https://aka.ms/pbidesktopstore) erneut installieren.

Sie können immer zuerst die Version von Power BI Desktop öffnen, die Sie verwenden möchten. Öffnen Sie anschließend die Datei in Power BI Desktop.

Zum Bearbeiten eines Power BI-Berichts auf dem Power BI-Berichtsserver oder Erstellen eines neuen Power BI-Berichts über das Webportal wird stets die richtige Version von Power BI Desktop geöffnet.

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Power BI-Berichte funktionieren im Power BI-Berichtsserver, im Power BI-Dienst (`https://app.powerbi.com`) sowie in den mobilen Power BI-Apps fast identisch. Nur einige Funktionen unterscheiden sich.

### <a name="selecting-a-language"></a>Auswählen einer Sprache

Wählen Sie für Power BI Desktop mit Optimierung für Power BI-Berichtsserver die Sprache beim Installieren der App aus. Sie können sie anschließend nicht mehr ändern, aber Sie können eine Version in einer weiteren Sprache installieren.

### <a name="report-visuals-in-a-browser"></a>Visuelle Berichtselemente in einem Browser

Power BI-Berichtsserver-Berichte unterstützen beinahe alle Visualisierungen, einschließlich Power BI-Visuals. Power BI-Berichtsserver-Berichte unterstützen Folgendes nicht:

* Visuelle R-Elemente
* ArcGIS-Karten
* Brotkrümel
* Vorschaufeatures für Power BI Desktop

### <a name="reports-in-the-power-bi-mobile-apps"></a>Berichte in den mobilen Power BI-Apps

Power BI-Berichtsserver-Berichte unterstützen alle Grundfunktionen in den [mobilen Power BI-Apps](../consumer/mobile/mobile-apps-for-mobile-devices.md), einschließlich:

* [Berichtslayout für Smartphones](../desktop-create-phone-report.md): Sie können einen Bericht für die Power BI Mobile-Apps optimieren. Auf dem Mobiltelefon sind optimierte Berichte mit einem speziellen Symbol, ![Berichtslayout für Smartphones](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png), gekennzeichnet, und sie weisen ein besonderes Layout auf.
  
    ![Für Telefone optimierter Bericht](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Die folgenden Funktionen werden von den Power BI-Berichtsserver-Berichten in den mobilen Power BI-Apps nicht unterstützt:

* R-Visuals
* ArcGIS-Karten
* Power BI-Visuals
* Brotkrümel
* Geofilter oder Strichcodes

### <a name="custom-security"></a>Benutzerdefinierte Sicherheit

Die für den Power BI-Berichtsserver optimierte Version von Power BI Desktop unterstützt die benutzerdefinierte Sicherheit nicht. Wenn Ihre Instanz des Power BI-Berichtsservers mit einer benutzerdefinierten Sicherheitserweiterung konfiguriert ist, können Sie keine Power BI-Berichte über Power BI Desktop (für den Power BI-Berichtsserver optimiert) in dieser Instanz speichern. Sie müssen die PBIX-Berichtsdatei aus Power BI Desktop speichern und anschließend auf der Website des Power BI-Berichtsserver-Portals hochladen.

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>Power BI Desktop für frühere Versionen von Power BI-Berichtsserver

Wenn Sie eine frühere Version des Berichtsservers verwenden, benötigen Sie die entsprechende Version von Power BI Desktop. Hier ist der Link zum Herunterladen einer vorhergehenden Version.

- Microsoft Power BI Desktop ([für den Power BI-Berichtsserver optimiert, September 2019](https://go.microsoft.com/fwlink/?linkid=2103723))

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Power BI Desktop installiert haben, können Sie mit dem Erstellen von Power BI-Berichten beginnen.

[Erstellen eines Power BI-Berichts für Power BI-Berichtsserver](quickstart-create-powerbi-report.md)  
[Was ist der Power BI-Berichtsserver?](get-started.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
