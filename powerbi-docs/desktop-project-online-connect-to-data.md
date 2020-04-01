---
title: 'Project Online: Verbinden mit Daten über Power BI Desktop'
description: 'Project Online: Verbinden mit Daten über Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 281d5b616b58fce4326e6d719502e443c249372a
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80403175"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Herstellen einer Verbindung mit Project Online-Daten über Power BI Desktop
Sie können sich mit Daten in Project Online über Power BI Desktop verbinden.

## <a name="step-1-download-power-bi-desktop"></a>Schritt 1: Laden Sie Power BI Desktop herunter
1. [Laden Sie Power BI Desktop herunter](https://go.microsoft.com/fwlink/?LinkID=521662), und führen Sie das Installationsprogramm aus, um **Power BI Desktop** auf Ihrem Computer zu installieren.

## <a name="step-2-connect-to-project-online-with-odata"></a>Schritt 2: Verbinden mit Project Online mit OData
1. Öffnen Sie **Power BI Desktop**.
2. Klicken Sie auf der *Willkommensseite* auf **Daten abrufen**.
3. Wählen Sie **OData-Feed**, und klicken Sie auf **Verbinden**.
4. Geben Sie die Adresse des OData-Feeds in das URL-Feld ein und klicken Sie dann auf „OK“.
   
   Wenn die Adresse für die Project Web App-Website *https://\<Mandantenname\>.sharepoint.com/sites/pwa* ähnelt, lautet die Adresse, die Sie für den OData-Feed eingeben *https://\<Mandantenname\>.sharepoint.com/sites/pwa\_/api/Projectdata*.
   
   In unserem Beispiel verwenden wir `https://contoso.sharepoint.com/sites/pwa/default.aspx`
5. Power BI Desktop fordert Sie zur Authentifizierung mit Ihrem Office 365-Konto auf. Wählen Sie das Organisationskonto aus und geben Sie dann Ihre Anmeldeinformationen ein.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Das Konto, mit dem Sie sich mit dem OData-Feed verbinden, muss mindestens Portfoliobetrachterzugriff auf die Website der Project-Web-App haben. 

Von hier aus können Sie auswählen, zu welchen Tabellen Sie eine Verbindung herstellen und eine Abfrage erstellen möchten.  Sie möchten einen Überblick über die ersten Schritte?  Im folgenden Blogbeitrag wird gezeigt, wie ein Burndowndiagramm aus Ihren Project Online-Daten erstellt wird.  Im Blogbeitrag wird auf Power Query zum Verbinden mit Project Online verwiesen, wobei dies auch für Power BI Desktop gilt.

[Erstellen von Burndowndiagrammen für Project mithilfe von Power Pivot und Power Query](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

