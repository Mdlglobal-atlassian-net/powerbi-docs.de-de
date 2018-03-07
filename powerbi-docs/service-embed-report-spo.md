---
title: Einbetten mit dem Berichts-Webpart in SharePoint Online
description: "Jetzt in Power BI: Mit dem neuen Berichts-Webpart für SharePoint Online können Sie interaktive Power BI-Berichte einfach in SharePoint Online-Seiten einbetten."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/19/2017
ms.author: maghan
LocalizationGroup: Share your work
ms.openlocfilehash: a6c134cd39b835ad0007b5ad8d6b6804b4d243d0
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Einbetten mit dem Berichts-Webpart in SharePoint Online

Jetzt in Power BI: Mit dem neuen Berichts-Webpart für SharePoint Online können Sie interaktive Power BI-Berichte einfach in SharePoint Online-Seiten einbetten.

Mit der neuen Option **In SharePoint Online einbetten** ist die umfassende Sicherheit eingebetteter Berichte gewährleistet. Erstellen Sie einfach sichere interne Portale.

## <a name="requirements"></a>Anforderungen

Wenn Sie Berichte mit der Option **In SharePoint Online einbetten** verwenden möchten, sind einige Anforderungen zu erfüllen.

* Das Power BI-Webpart für SharePoint Online erfordert [Moderne Seiten](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Einbetten des Berichts

Um den Bericht in SharePoint Online einzubetten, müssen Sie zuerst die URL des Berichts abrufen. Diese URL wird dann im neuen Power BI-Webpart in SharePoint Online verwendet.

### <a name="get-a-url-to-your-report"></a>Abrufen der Berichts-URL

1. Rufen Sie den Bericht im Power BI-Dienst auf.

2. Wählen Sie den Menüeintrag **Datei** aus.

3. Wählen Sie **In SharePoint Online einbetten** aus.
   
    ![](media/service-embed-report-spo/powerbi-file-menu.png)

4. Kopieren Sie die URL aus dem Dialogfeld.

    ![](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

   > [!NOTE]
   > Sie können auch die URL verwenden, die beim Betrachten eines Berichts in der Adressleiste des Webbrowsers angezeigt wird. Diese URL enthält die derzeit angezeigte Berichtsseite. Sie müssen den Berichtsabschnitt aus der URL entfernen, wenn Sie eine andere Seite verwenden möchten.

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Hinzufügen des Power BI-Berichts zu einer SharePoint Online-Seite

1. Öffnen Sie die gewünschte Seite in SharePoint Online, und wählen Sie **Bearbeiten** aus.

    ![](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Sie können auch eine neue moderne Websiteseite erstellen, indem Sie in SharePoint Online **+ Neu** auswählen.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Wählen Sie **+** und dann das Webpart **Power BI**  aus.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Wählen Sie **Bericht hinzufügen** aus.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)

4. Fügen Sie die Berichts-URL im Eigenschaftsbereich ein. Dies ist die vorhin kopierte URL. Der Bericht wird automatisch geladen.

    ![](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Wählen Sie **Veröffentlichen** aus, damit Ihre SharePoint Online-Benutzer die Änderung sehen können.

    ![](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="granting-access-to-reports"></a>Zugriff gewähren auf Berichte

Nachdem Sie einen Bericht in SharePoint Online eingebettet haben, müssen Sie den Benutzern die Berechtigung geben, den Bericht anzuzeigen. Die Berechtigungen zum Anzeigen des Berichts werden im Power BI-Dienst festgelegt.

> [!IMPORTANT]
> Überprüfen Sie im Power BI-Dienst, wer den Bericht sehen kann, und stellen Sie sicher, dass nicht aufgeführte, berechtigte Benutzer Zugriff erhalten.

Es gibt zwei Möglichkeiten, den Zugriff auf den Bericht im Power BI-Dienst zu regeln. Wenn Sie die SharePoint Online-Teamwebsite auf Grundlage einer Office 365-Gruppe erstellen, geben Sie im Power BI-Dienst an, dass die Benutzer Mitglieder des App-Arbeitsbereichs sind. Dadurch wird sichergestellt, dass die Benutzer die Inhalte der Gruppe sehen können. Weitere Informationen finden Sie unter [Erstellen und Verteilen einer App in Power BI](service-create-distribute-apps.md).

Alternativ können Sie Benutzern den Zugriff auf den Bericht auf folgende Weise gewähren.

1. Heften Sie eine Kachel aus dem Bericht an ein Dashboard an.

2. Geben Sie das Dashboard für die Benutzer frei, die Zugriff auf den Bericht benötigen. Weitere Informationen erhalten Sie unter [Freigeben eines Dashboards für Kollegen und andere](service-share-dashboards.md).

## <a name="web-part-settings"></a>Webpart-Einstellungen

Das Power BI-Webpart für SharePoint Online verfügt über die folgenden Einstellungen.

![](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Eigenschaft | Beschreibung |
| --- | --- |
| Seitenname |Die Standardseite, die vom Webpart angezeigt wird. Wählen Sie einen Wert aus der Dropdownliste aus. Wenn keine Seiten angezeigt werden, verfügt der Bericht entweder nur über eine Seite, oder die eingefügte URL enthält den Seitennamen. Entfernen Sie den Berichtsabschnitt aus der URL, um eine bestimmte Seite auswählen zu können. |
| Anzeige |Option zum Festlegen, wie der Bericht in die SharePoint Online-Seite eingepasst wird. |
| Navigationsbereich anzeigen |Anzeigen oder Ausblenden des Navigationsbereichs der Seite. |
| Filterbereich anzeigen |Anzeigen oder Ausblenden des Filterbereichs. |

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

Wenn Ihre Power BI-Umgebung die Anmeldung per Multi-Factor Authentication erfordert, können Sie aufgefordert werden, Ihre Identität mithilfe eines Sicherheitsgeräts zu bestätigen. Dies ist der Fall, wenn Sie sich nicht bereits per Multi-Factor Authentication bei SharePoint Online angemeldet haben, Ihre Power BI-Umgebung aber ein per Sicherheitsgerät verifiziertes Konto erfordert.

> [!NOTE]
> Multi-Factor Authentication wird derzeit noch nicht von Azure Active Directory 2.0 unterstützt. Benutzer erhalten dann die Meldung *Fehler*. Der Benutzer kann sich mithilfe eines Sicherheitsgeräts erneut bei SharePoint Online anmelden, um Zugriff auf den Bericht zu erhalten.

## <a name="reports-that-do-not-load"></a>Nicht geladene Berichte

Möglicherweise wird der Bericht im Power BI-Webpart nicht geladen, und die folgende Meldung wird angezeigt.

*Dieser Inhalt ist nicht verfügbar.*

![](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Dies kann vor allem zwei Gründe haben.

1. Sie haben keinen Zugriff auf diesen Bericht.
2. Der Bericht wurde gelöscht.

Wenden Sie sich an den Besitzer der SharePoint Online-Seite, um diese Probleme zu beheben.

## <a name="known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen

* **Fehler: „Es ist ein Fehler aufgetreten, melden Sie sich ab und wieder an und öffnen Sie diese Seite dann erneut. Korrelations-ID: nicht definiert, HTTP-Antwortstatus: 400, Serverfehlercode 10001, Meldung: Fehlendes Aktualisierungstoken“**
  
  Wenn Sie diesen Fehler erhalten, führen Sie einen der folgenden Schritte aus.
  
  1. Melden Sie sich aus SharePoint ab und anschließend wieder an. Achten Sie darauf, alle Browserfenster zu schließen, bevor Sie sich erneut anmelden.

  2. Wenn für Ihr Benutzerkonto die Multi-Factor Authentication (MFA) erforderlich ist, stellen Sie sicher, dass Sie sich in SharePoint mit Ihrem MFA-Gerät anmelden (Smartphone-App, Smartcard usw.).

* Power BI unterstützt nicht die gleichen lokalisierte Sprachen wie SharePoint Online. Daher wird im eingebetteten Bericht möglicherweise nicht die ordnungsgemäße Lokalisierung angezeigt.

* Bei Verwendung von Internet Explorer 10 können Probleme auftreten. Informieren Sie sich über die [Browserunterstützung für Power BI](service-browser-support.md) und für [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

## <a name="next-steps"></a>Nächste Schritte

[Erstellen moderner Websiteseiten durch Endbenutzer zulassen oder verhindern](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
[Erstellen und Verteilen einer App in Power BI](service-create-distribute-apps.md)  
[Freigeben eines Dashboards für Kollegen und andere](service-share-dashboards.md)  
[Power BI Premium – Beschreibung](service-premium.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/) 
