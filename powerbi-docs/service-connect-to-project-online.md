---
title: Herstellen einer Verbindung mit Project Online mithilfe von Power BI
description: Project Online für Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 07/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 32d731c354d848809d336392ef51f667b14427d8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74565679"
---
# <a name="connect-to-project-web-app-with-power-bi"></a>Herstellen einer Verbindung mit Project Web App mithilfe von Power BI
Microsoft Project Web App ist eine flexible Onlinelösung für das Projektportfoliomanagement (PPM) und die tägliche Arbeit. Project Web App ermöglicht es Organisationen, die ersten Schritte zu unternehmen, Investitionen in Projektportfolios zu priorisieren und den beabsichtigten Geschäftserfolg zu realisieren. Mit der Vorlagen-App für Power BI von Project Web App können Sie Erkenntnisse von Project Web App nutzen, um das Verwalten von Projekten, Portfolios und Ressourcen zu vereinfachen.

Stellen Sie eine Verbindung mit der [Vorlagen-App von Project Web App](https://appsource.microsoft.com/product/power-bi/pbi_msprojectonline.pbi-microsoftprojectwebapp) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung

1. Wählen Sie im Navigationsbereich **Apps** und dann in der oberen rechten Ecke **Apps abrufen** aus.

    ![Apps abrufen](media/service-connect-to-project-online/GetApps.png)

2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![AppSource](media/service-connect-to-project-online/AppSource.png)
3. Wählen Sie in AppSource die Registerkarte **Apps** aus, und suchen Sie nach bzw. klicken Sie auf **Microsoft Project Web App**.
   
4. Klicken Sie bei der nun angezeigten Meldung **Diese Power BI-App installieren?** auf **Installieren**. 

   ![Installieren von Project Web](media/service-connect-to-project-online/ProjectTile.png)
5. Klicken Sie im Bereich **Apps** auf die Kachel **Microsoft Project Web App**. 
   
   ![Microsoft Project Web App](media/service-connect-to-project-online/getstarted.png)
6. Wählen Sie unter **Erste Schritte mit Ihrer neuen App** die Option **Daten verbinden** aus.
   
   ![Herstellen einer Datenverbindung](media/service-connect-to-project-online/mproject.png)
7. Geben Sie im Textfeld **Project Web App-URL** die URL für die Project Web App (PWA) ein, mit der Sie eine Verbindung herstellen möchten.  Beachten Sie, dass dies bei Verwendung einer benutzerdefinierten Domäne vom Beispiel abweichen kann. Geben Sie im Textfeld **PWA Site Language** (PWA-Websitesprache) die Zahl ein, die der Sprache Ihrer PWA-Website entspricht. Geben Sie die einzelne Zahl „1“ für Englisch, „2“ für Französisch, „3“ für Deutsch, „4“ für Portugiesisch (Brasilien), „5“ für Portugiesisch (Portugal) oder „6“ für Spanisch ein. 
   
   ![Herstellen einer Verbindung mit Microsoft Project Online](media/service-connect-to-project-online/params.png)
8. Wählen Sie für die Authentifizierungsmethode **oAuth2** \> **Anmelden** aus. Wenn Sie dazu aufgefordert werden, geben Sie Ihre Project Web App-Anmeldeinformationen ein, und führen Sie den Authentifizierungsvorgang aus.

    > [!NOTE]
    > Sie müssen über Portfolio Viewer-, Portfolio Manager- oder Administrator-Berechtigungen für die Project Web-App verfügen, mit der Sie eine Verbindung herstellen.

9. Eine Benachrichtigung wird angezeigt, dass Ihre Daten geladen werden. Je nach Größe Ihres Kontos kann dies einige Zeit dauern. Nachdem Power BI die Daten importiert hat, werden die Inhalte Ihres neuen Arbeitsbereichs angezeigt. Möglicherweise müssen Sie das Dataset aktualisieren, um die neuesten Updates zu erhalten. 

    Nachdem die Daten von Power BI importiert wurden, werden im Navigationsbereich der Bericht mit 13 Seiten und das Dataset angezeigt. 

10. Sobald Ihre Berichte bereit sind, können Sie Ihre Project Web App-Daten erkunden. Die Vorlagen-App enthält 13 umfangreiche und detaillierte Berichte für die Portfolioübersicht (sechs Berichtsseiten), die Ressourcenübersicht (fünf Berichtsseiten) und den Projektstatus (zwei Berichtsseiten). 

    ![Portfoliodashboard](media/service-connect-to-project-online/report1.png)
   
    ![Verfügbarkeit](media/service-connect-to-project-online/report3.png)
   
    ![Projektstatus](media/service-connect-to-project-online/report2.png)

**Was nun?**

* Für Ihr Dataset wird eine tägliche Aktualisierung geplant, Sie können jedoch den Aktualisierungszeitplan ändern oder bei Bedarf über **Jetzt aktualisieren** eine Aktualisierung anfordern.

**Erweitern der Vorlagen-App**

Laden Sie die [GitHub-PBIT-Datei](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) herunter, um das Inhaltspaket weiter anzupassen und zu aktualisieren.

## <a name="next-steps"></a>Weitere Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

