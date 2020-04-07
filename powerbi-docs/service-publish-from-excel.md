---
title: Veröffentlichen in Power BI aus Microsoft Excel
description: Erfahren Sie, wie Sie eine Excel-Arbeitsmappe auf Ihrer Power BI-Website veröffentlichen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/26/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e503d2c68b4b726ab44c3bec0fad7001da33e184
ms.sourcegitcommit: 8267a7383d6506dae42f87e4f4a2362b875b2911
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80329610"
---
# <a name="publish-to-power-bi-from-microsoft-excel"></a>Veröffentlichen in Power BI aus Microsoft Excel
Ab Microsoft Excel 2016 können Sie Ihre Excel-Arbeitsmappen direkt in Ihrem [Power BI](https://powerbi.microsoft.com)-Arbeitsbereich veröffentlichen. Dort können Sie hoch interaktive Berichte und Dashboards auf Grundlage der Daten in Ihrer Arbeitsmappe erstellen. Sie können Ihre Einblicke dann für andere Personen in Ihrer Organisation freigeben.

![Veröffentlichen einer Arbeitsmappe in Power BI](media/service-publish-from-excel/pbi_uploadexport2.png)

Beim Veröffentlichen einer Arbeitsmappe in Power BI müssen Sie folgende Punkte beachten:

* Sie müssen für die Anmeldung bei Office, OneDrive for Business (wenn die Arbeitsmappen hier gespeichert sind) und Power BI dasselbe Konto verwenden.
* Es können weder leere Arbeitsmappen noch Arbeitsmappen ohne von Power BI unterstützten Inhalt veröffentlicht werden.
* Sie können weder verschlüsselte oder kennwortgeschützte Arbeitsmappen noch Arbeitsmappen veröffentlichen, die Information Protection Management aufweisen.
* Um etwas in Power BI zu veröffentlichen, muss die moderne Authentifizierung aktiviert sein (Standardeinstellung). Wenn sie deaktiviert ist, steht die Option „Veröffentlichen“ nicht im Menü „Datei“ zur Verfügung.

## <a name="publish-your-excel-workbook"></a>Veröffentlichen der Excel-Arbeitsmappe
Klicken Sie zum Veröffentlichen Ihrer Excel-Arbeitsmappe in Excel auf **Datei** > **Veröffentlichen** und anschließend entweder auf **Hochladen** oder **Exportieren**.

Beim **Hochladen** der Arbeitsmappe in Power BI können Sie damit auf die gleiche Weise interagieren wie in Excel Online. Sie können auch eine Auswahl aus der Arbeitsmappe an Power BI-Dashboards anheften sowie die Arbeitsmappe oder ausgewählte Elemente über Power BI freigeben.

Beim **Exportieren** können Sie Tabellendaten und das zugehörige Datenmodell in ein Power BI-Dataset exportieren, mit dem Sie anschließend Power BI-Berichte und -Dashboards erstellen können.

### <a name="local-file-publishing"></a>Veröffentlichen lokaler Dateien
Excel unterstützt die Veröffentlichung von lokalen Excel-Dateien. Die Dateien müssen hierfür nicht in OneDrive for Business oder SharePoint Online gespeichert werden.

> [!IMPORTANT]
> Lokale Dateien können nur unter Excel 2016 (oder höher) mit einem Office 365-Abonnement veröffentlicht werden. Mit einer eigenständigen Excel 2016-Installation können Sie nur in Power BI veröffentlichen, wenn Sie die Arbeitsmappe in OneDrive for Business oder SharePoint Online speichern.
> 

Nachdem Sie auf **Veröffentlichen** geklickt haben, können Sie den für die Veröffentlichung gewünschten Arbeitsbereich auswählen. Dabei kann es sich um Ihren persönlichen Arbeitsbereich oder einen Gruppenarbeitsbereich handeln, auf den Sie Zugriff haben (wie in der folgenden Abbildung dargestellt).

![In Power BI veröffentlichen](media/service-publish-from-excel/pbi_choose_workspace.png)

Sie haben zwei Optionen, die Arbeitsmappe in Power BI zu veröffentlichen.

![In Power BI veröffentlichen](media/service-publish-from-excel/pbi_uploadexport3.png)

Nach der Veröffentlichung wird der veröffentlichte Inhalt der Arbeitsmappe getrennt von der lokalen Datei in Power BI importiert. Wenn Sie die Datei in Power BI aktualisieren möchten, müssen Sie die aktualisierte Version noch mal veröffentlichen. Alternativ dazu können Sie die Daten auch aktualisieren, indem Sie für die Arbeitsmappe oder das Dataset in Power BI eine geplante Aktualisierung konfigurieren.

### <a name="publishing-from-a-standalone-excel-installation"></a>Veröffentlichen aus einer eigenständigen Excel-Installation
Wenn Sie aus einer eigenständigen Excel-Installation veröffentlichen möchten, müssen Sie die Arbeitsmappe in OneDrive for Business speichern. Klicken Sie auf **In der Cloud speichern**, und wählen Sie einen Speicherort in OneDrive for Business aus.

![Speichern in OneDrive for Business](media/service-publish-from-excel/pbi_savetoonedrive2.png)

Nachdem Sie die Arbeitsmappe in OneDrive for Business gespeichert haben, stehen Ihnen unter **Veröffentlichen** zwei Optionen für die Veröffentlichung Ihrer Arbeitsmappe in Power BI zur Verfügung: **Hochladen** oder **Exportieren**.

![Optionen für Power BI](media/service-publish-from-excel/pbi_uploadexport2.png)

#### <a name="upload-your-workbook-to-power-bi"></a>Hochladen Ihrer Arbeitsmappe zu Power BI
Bei der Option **Hochladen** wird die Arbeitsmappe in Power BI genauso angezeigt wie in Excel Online. Allerdings stehen Ihnen im Gegensatz zu Excel Online einige Funktionen zur Verfügung, mit denen Sie Elemente aus Arbeitsblättern an Dashboards anheften können.

Sie können Ihre Arbeitsmappe in Power BI nicht bearbeiten. Wenn Sie Änderungen an den Daten vornehmen möchten, klicken Sie auf **Bearbeiten**, um die Arbeitsmappe in Excel Online zu bearbeiten oder in Excel auf Ihrem Computer zu öffnen. Alle vorgenommenen Änderungen werden in der Arbeitsmappe in OneDrive for Business gespeichert.

Beim **Hochladen** wird kein Dataset in Power BI erstellt. Ihre Arbeitsmappe wird im Navigationsbereich Ihres Arbeitsbereichs unter „Berichte“ angezeigt. Nach Power BI hochgeladene Arbeitsmappen weisen ein besonderes Excel-Symbol auf, das anzeigt, dass sie aus Excel hochgeladen wurden.

Die Option **Hochladen** eignet sich in Fällen, wenn Ihre Daten ausschließlich in Arbeitsblättern gespeichert sind oder wenn Sie Pivottabellen und Diagramme in Power BI anzeigen möchten.

Die Verwendung der Option „Hochladen“ in Excel für die Veröffentlichung in Power BI ähnelt der Vorgehensweise **Daten abrufen > Datei > OneDrive for Business > Excel mit Power BI verbinden und in Power BI verwalten und anzeigen** von Power BI in Ihrem Browser.

#### <a name="export-workbook-data-to-power-bi"></a>Arbeitsmappendaten nach Power BI exportieren
Bei der Option **Exportieren** werden alle unterstützten Daten in Tabellen und/oder Datenmodellen in ein neues Dataset in Power BI exportiert. Alle Power View-Blätter in der Arbeitsmappe werden in Power BI als Berichte neu erstellt.

Sie können Ihre Arbeitsmappe weiterhin bearbeiten. Die gespeicherten Änderungen werden für gewöhnlich innerhalb einer Stunde mit dem Dataset in Power BI synchronisiert. Für eine schnellere Aktualisierung der Änderungen können Sie in Excel noch mal die Option **Veröffentlichen** auswählen, um die Änderungen direkt zu exportieren. Auch alle Visualisierungen in Berichten und Dashboards werden aktualisiert.

Wählen Sie die Option **Veröffentlichen**, wenn Sie die Funktionen „Daten abrufen und transformieren“ oder „Power Pivot“ zum Laden von Daten in ein Datenmodell verwendet haben oder wenn Ihre Arbeitsmappe über Power View-Blätter mit Visualisierungen verfügt, die in Power BI angezeigt werden sollen.

Die Verwendung der Option **Exportieren** ähnelt der Vorgehensweise **Daten abrufen > Datei > OneDrive for Business > Excel-Daten in Power BI exportieren** von Power BI in Ihrem Browser.

## <a name="publishing"></a>Veröffentlichen
Bei beiden Optionen meldet sich Excel mit Ihrem aktuellen Konto bei Power BI an, und die Arbeitsmappe wird anschließend in Ihrem Power BI-Arbeitsbereich veröffentlicht. Auf der Statusleiste in Excel wird der Fortschritt des Veröffentlichungsprozesses angezeigt.

![Statusleiste für die Veröffentlichung in Power BI](media/service-publish-from-excel/pbi_publishingstatus.png)

Nach Abschluss des Vorgangs können Sie direkt von Excel zu Power BI wechseln.

![Wechseln zu Power BI](media/service-publish-from-excel/pbi_gotopbi.png)

## <a name="next-steps"></a>Nächste Schritte
[Excel-Daten in Power BI](service-excel-workbook-files.md)  
Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

