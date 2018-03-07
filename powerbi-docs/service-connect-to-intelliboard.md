---
title: Herstellen einer Verbindung mit IntelliBoard mithilfe von Power BI
description: "IntelliBoard für Power BI"
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d73a02e754615263a155d3a7e31e47af4b740fd8
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Herstellen einer Verbindung mit IntelliBoard mithilfe von Power BI
IntelliBoard bietet vereinfachten Zugriff auf Ihre Moodle-Lernmanagementsystem-Daten über Reporting Services. Das IntelliBoard-Inhaltspaket für Power BI bietet zusätzliche Analysen, einschließlich Metriken auf Ihre Kurse, registrierter Benutzer, der Gesamtleistung und Ihrer LMS-Aktivität.

Stellen Sie eine Verbindung mit dem [IntelliBoard-Inhaltspaket](https://app.powerbi.com/getdata/services/intelliboard) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Wählen Sie **IntelliBoard** und anschließend **Abrufen** aus.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Wählen Sie **OAuth 2** und anschließend **Anmelden** aus. Geben Sie Ihre IntelliBoard-Anmeldeinformationen an, wenn Sie dazu aufgefordert werden.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Sobald Sie verbunden sind, werden ein Dashboard, ein Bericht und ein Dataset automatisch geladen. Anschließend werden die Kacheln mit Daten aus Ihrem IntelliBoard-Konto aktualisiert.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](power-bi-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](service-dashboard-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Ihr Dataset ist auf eine tägliche Aktualisierung festgelegt. Sie können jedoch das Aktualisierungsintervall ändern oder es über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Das Inhaltspaket umfasst Daten aus den folgenden Tabellen:  

    - Activity  
    - Agents  
    - Auth (Authentifizierung)  
    - Länder  
    - CoursesProgress (Kursfortschritt)  
    - Enrollments (Registrierungen)
    - Lang (Sprache)  
    - Platform (Plattform)  
    - Totals (Gesamtergebnisse)  
    - UsersProgress (Benutzerfortschritt)    

## <a name="system-requirements"></a>Systemanforderungen
Ein IntelliBoard-Konto mit Berechtigungen für die obigen Tabellen wird benötigt, um dieses Inhaltspaket zu instanziieren.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Power BI – Grundkonzepte](service-basic-concepts.md)
