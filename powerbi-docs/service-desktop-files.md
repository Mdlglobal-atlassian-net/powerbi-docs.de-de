---
title: Abrufen von Daten aus Power BI Desktop-Dateien
description: Erfahren Sie, wie Sie Daten und Berichte aus Power BI Desktop in Power BI abrufen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ea5e4a4af3f4049ccb9d69fbe95a13dc08a8cf05
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877108"
---
# <a name="get-data-from-power-bi-desktop-files"></a>Abrufen von Daten aus Power BI Desktop-Dateien
![](media/service-desktop-files/pbid_file_icon.png)

Business Intelligence gewinnen und Berichte erstellen – mit **Power BI Desktop** ist es ganz einfach. Ob für die Verbindung zu den verschiedensten Datenquellen, das Abfragen und Transformieren von Daten, die Datenmodellierung oder das Erstellen leistungsstarker und dynamischer Berichte: In **Power BI Desktop** lassen sich Business Intelligence-Aufgaben mit intuitiver Bedienung schnell bewältigen. Wenn Sie mit **Power BI Desktop** noch nicht vertraut sind, lesen Sie den Artikel [Erste Schritte mit Power BI Desktop](desktop-getting-started.md).

Sobald Sie Daten in **Power BI Desktop** eingebracht und einige Berichte erstellt haben, ist es Zeit, Ihre gespeicherte Datei an den **Power BI-Dienst** zu übertragen.

## <a name="where-your-file-is-saved-makes-a-difference"></a>Der Speicherort Ihrer Datei ist entscheidend
**Lokal** – Wenn Sie Ihre Datei auf einem lokalen Laufwerk Ihres Computers oder an einem anderen Speicherort in Ihrer Organisation speichern, können Sie Ihre Datei *importieren* oder sie über Power BI Desktop *veröffentlichen*, um die Daten nach Power BI zu übertragen. In Wahrheit verbleibt Ihre Datei aber auf Ihrem lokalen Laufwerk. Die Datei wird also eigentlich gar nicht nach Power BI verschoben. Tatsächlich wird ein neues Dataset in Power BI erstellt, und die Daten und das Datenmodell aus der Power BI Desktop-Datei werden in das Dataset geladen. Wenn Ihre Datei Berichte enthält, werden diese auf Ihrer Power BI-Website unter „Berichte“ angezeigt.

**OneDrive – Geschäftlich** – Wenn Sie One Drive for Business verwenden, können Sie sich mit demselben Konto auch bei Power BI anmelden. So synchronisieren Sie Ihre Arbeit in Power BI Desktop oder einer CSV-Datei mit den Datasets, Berichten und Dashboards in Power BI auf mit Abstand effektivste Art und Weise. Da sich sowohl Power BI als auch OneDrive in der Cloud befinden, *verbindet* sich Power BI etwa einmal in der Stunde mit Ihrer Datei in OneDrive. Wenn Änderungen gefunden werden, werden Ihre Dataset, Berichte und Dashboards in Power BI automatisch aktualisiert.

**OneDrive – Persönlich** – Wenn Sie Ihre Dateien in Ihrem eigenen OneDrive-Konto speichern, erhalten Sie dennoch viele der Vorteile, die Ihnen OneDrive for Business bieten würde. Der Hauptunterschied besteht darin, dass Sie sich beim ersten Verknüpfen mit Ihrer Datei, mit Ihrem Microsoft-Konto bei OneDrive anmelden müssen (mit „Daten abrufen“ > „Dateien“ > „OneDrive – Persönlich“). Normalerweise sind Ihr Microsoft- und Ihr Power BI-Konto nicht identisch. Stellen Sie bei der OneDrive-Anmeldung mithilfe Ihres Microsoft Kontos sicher, dass Sie die Option „Angemeldet bleiben“ aktiviert haben. Auf diese Weise ist Power BI in der Lage, sich etwa einmal die Stunde mit Ihrer Datei zu verbinden und sicherzustellen, dass Ihr Dataset in Power BI synchronisiert ist.

**SharePoint-Teamwebsites** – Ihre Power BI Desktop-Dateien in SharePoint-Teamwebsites zu speichern funktioniert ähnlich wie das Speichern in OneDrive for Business. Der größte Unterschied besteht im Herstellen der Verknüpfung zur Datei aus Power BI. Sie können eine URL angeben oder eine Verknüpfung mit einem Stammordner erstellen.

## <a name="import-or-connect-to-a-power-bi-desktop-file-from-power-bi"></a>Herstellen einer Verknüpfung zu bzw. Importieren einer Power BI Desktop-Datei mithilfe von Power Bi
>[!IMPORTANT]
>Die maximale Dateigröße für Importe in Power BI beträgt 1 GB.

1. Klicken Sie im Navigatorbereich von Power BI auf ** Daten abrufen**.
   
   ![](media/service-desktop-files/pbid_get_data_button.png)
2. Klicken Sie in **Dateien** auf **Abrufen**.
   
   ![](media/service-desktop-files/pbid_files_get.png)
3. Suchen Sie Ihre Datei. Power BI Desktop-Dateien haben die Erweiterung PBIX.
   
   ![](media/service-desktop-files/pbid_find_your_file.png)

## <a name="publish-a-file-from-power-bi-desktop-to-your-power-bi-site"></a>Veröffentlichen einer Power BI Desktop-Datei auf Ihrer Power BI-Website
Die Funktion „Veröffentlichen“ in Power BI Desktop ist faktisch identisch mit der Funktion „Daten abrufen“ in Power BI. Diese dient dazu, Ihre Datei von einem lokalen Laufwerk zu importieren oder sie zu verknüpfen, wenn sie in OneDrive gespeichert ist.  Hier finden Sie eine kurz gehaltene Anleitung. Für weiterführende Erläuterungen lesen Sie bitte [Veröffentlichen aus Power BI Desktop](desktop-upload-desktop-files.md).

1. Klicken Sie in Power BI Desktop auf **Datei** > **Veröffentlichen** > **In Power BI veröffentlichen** aus, oder klicken Sie im Menüband auf **Veröffentlichen**.
   
   ![](media/service-desktop-files/pbid_publish.png)
2. Melden Sie sich bei Power BI an. Dies ist nur bei der ersten Anmeldung nötig.
   
   Wenn der Vorgang abgeschlossen ist, erhalten Sie einen Link zum Öffnen des Berichts auf Ihrer Power BI-Website.
   
   ![](media/service-desktop-files/pbid_publishing.png)

## <a name="next-steps"></a>Nächste Schritte
**Werten Sie Ihre Daten aus** – Sobald Sie Ihre Daten und Berichte aus Ihrer Datei in Power BI geladen haben, können Sie sie auswerten. Wenn die Datei bereits Berichte enthält, werden diese im Navigatorbereich unter **Berichte** angezeigt. Wenn die Datei ausschließlich Daten enthält, können Sie neue Berichte erstellen. Klicken Sie einfach mit der rechten Maustaste auf das neue Dataset und anschließend auf **Durchsuchen**.

**Aktualisieren von Daten aus externen Quellen** – Wenn Ihre Power BI Desktop-Datei mit externen Datenquellen verknüpft ist, können Sie eine geplante Aktualisierung einrichten, damit das Dataset immer auf dem neuesten Stand ist. In den meisten Fällen ist das Einrichten einer geplanten Aktualisierung recht einfach. Eine detaillierte Beschreibung übersteigt aber den Rahmen dieses Artikels. Weitere Informationen finden Sie unter [Aktualisieren von Daten in Power BI](refresh-data.md).

