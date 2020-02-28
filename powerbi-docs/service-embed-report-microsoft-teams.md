---
title: Einbetten von Berichten mit der Registerkarte „Power BI“ für Microsoft Teams
description: Mit der Registerkarte „Power BI“ für Microsoft Teams können Sie interaktive Berichte problemlos in Kanäle und Chats einbetten.
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 01/31/2020
ms.openlocfilehash: fb4846a777dda4787e1ed0be7de869367a616ea5
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530485"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>Einbetten von Berichten mit der Registerkarte „Power BI“ für Microsoft Teams

Mit der aktualisierten Registerkarte „Power BI“ für Microsoft Teams können Sie interaktive Berichte problemlos in Kanäle und Chats in Microsoft Teams einbetten.

Verwenden Sie die Registerkarte „Power BI“ für Microsoft Teams, um Ihre Kollegen bei der Suche nach den Daten zu unterstützen, die Ihr Team verwendet, und um sich in Ihren Teamkanälen über die Daten auszutauschen.

## <a name="requirements"></a>Anforderungen

Folgendes ist erforderlich, damit die **Registerkarte „Power BI“ für Microsoft Teams** funktioniert:

- Eine Power BI Pro-Lizenz oder der Bericht ist in einer [Power BI Premium-Kapazität (EM oder P SKU)](service-premium-what-is.md) mit einer Power BI-Lizenz enthalten.
- Die Registerkarte „Power BI“ für Microsoft Teams
- Der Benutzer muss sich beim Power BI-Dienst anmelden, um seine Power BI-Lizenz zur Nutzung des Berichts zu aktivieren.
- Der Benutzer muss über die Berechtigung zum Anzeigen des Berichts verfügen.

## <a name="embed-your-report"></a>Einbetten des Berichts
Fügen Sie den Bericht wie unten beschrieben hinzu, um ihn in einen Microsoft Teams-Kanal oder -Chat einzubetten.

1. Öffnen Sie den gewünschten Kanal oder Chat in Microsoft Teams, und klicken Sie auf das Symbol **+** .

    ![Hinzufügen einer Registerkarte zu einem Kanal oder Chat](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. Klicken Sie auf die Registerkarte „Power BI“.

    ![Liste mit Registerkarten in Microsoft Teams, Power BI ausgewählt](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. Verwenden Sie die verfügbaren Optionen, um einen Bericht aus einem Arbeitsbereich, dem Bereich „Für mich freigegeben“ oder einer Power BI-App auszuwählen.

    ![Registerkarte „Power BI“ für Einstellungen für Microsoft Teams](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. Der Registerkartenname wird automatisch an den Berichtsnamen angepasst. Sie haben aber die Möglichkeit, diesen zu ändern. 

5. Klicken Sie auf **Speichern**.

## <a name="supported-reports"></a>Unterstützte Berichte

Sie können über die Registerkarte die folgenden Berichte einbetten:

- Interaktive und paginierte Berichte
- Berichte unter „Mein Arbeitsbereich“, neue Benutzeroberfläche für Arbeitsbereiche und klassische Arbeitsbereiche
- Berichte in Power BI-Apps


## <a name="grant-access-to-reports"></a>Gewähren des Zugriffs auf Berichte

Wenn Sie einen Bericht in Microsoft Teams einbetten, erhalten die Benutzer nicht automatisch die Berechtigung, den Bericht aufzurufen. Sie müssen den [Benutzern die Berechtigung erteilen, den Bericht in Power BI aufzurufen](service-share-dashboards.md). Sie können eine Office 365-Gruppe für Ihr Team verwenden, um diesen Prozess zu vereinfachen. 

> [!IMPORTANT]
> Überprüfen Sie im Power BI-Dienst, wer den Bericht sehen kann, und stellen Sie sicher, dass nicht aufgeführte, berechtigte Benutzer Zugriff erhalten.

Eine Möglichkeit, um sicherzustellen, dass jeder in Ihrem Team Zugriff auf die von Ihnen einbetteten Berichte hat, besteht darin, sie in einem einzelnen Arbeitsbereich in Power BI zu platzieren und der Office 365-Gruppe Ihres Teams Zugriff auf den Arbeitsbereich zu gewähren.

## <a name="known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen

- Power BI unterstützt nicht die gleichen lokalisierten Sprachen wie Microsoft Teams. Daher wird im eingebetteten Bericht möglicherweise nicht die ordnungsgemäße Lokalisierung angezeigt.
- Power BI Dashboards können nicht in die Registerkarte „Power BI“ für Microsoft Teams eingebettet werden.
- Benutzern ohne Power BI-Lizenz oder ohne Zugriffsberechtigung für den Bericht wird die Meldung „Inhalt ist nicht verfügbar“ angezeigt.
- Bei Verwendung von Internet Explorer 10 können Probleme auftreten. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL-Filter](service-url-filters.md) werden auf der Registerkarte „Power BI“ für Microsoft Teams nicht unterstützt.
- In nationalen Clouds ist die neue Registerkarte „Power BI“ nicht verfügbar. Möglicherweise ist aber eine ältere Version verfügbar, die die neue Benutzeroberfläche für Arbeitsbereiche oder Berichte in Power BI-Apps nicht unterstützt. 
- Wenn die Registerkarte gespeichert wird, kann der Registerkartenname nicht mehr über die Registerkarteneinstellungen geändert werden. Verwenden Sie die Option „Umbenennen“, wenn Sie den Namen ändern möchten.

## <a name="next-steps"></a>Nächste Schritte
- [Freigeben eines Dashboards für Kollegen und andere](service-share-dashboards.md)  
- [Erstellen und Verteilen einer App in Power BI](service-create-distribute-apps.md)  
- [Was ist Power BI Premium?](service-premium-what-is.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
