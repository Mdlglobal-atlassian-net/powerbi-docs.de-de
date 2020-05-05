---
title: Einbetten eines Berichts-Webparts in SharePoint Online
description: 'Jetzt in Power BI: Mit dem neuen Berichts-Webpart für SharePoint Online können Sie interaktive Power BI-Berichte einfach in SharePoint Online-Seiten einbetten.'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 04/27/2020
ms.openlocfilehash: 5b726137fae0087701833b2d713cf7b5a329f899
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82585194"
---
# <a name="embed-a-report-web-part-in-sharepoint-online"></a>Einbetten eines Berichts-Webparts in SharePoint Online

Jetzt in Power BI: Mit dem neuen Berichts-Webpart für SharePoint Online können Sie interaktive Power BI-Berichte einfach in SharePoint Online-Seiten einbetten.

Mit der neuen Option **In SharePoint Online einbetten** ist die umfassende Sicherheit eingebetteter Berichte gewährleistet. Erstellen Sie einfach sichere interne Portale.

## <a name="requirements"></a>Anforderungen

Damit **In SharePoint Online einbetten**-Berichte funktionieren, müssen folgende Voraussetzungen erfüllt sein:

* Eine Power BI Pro-Lizenz oder eine [Power BI Premium-Kapazität (EM oder P SKU)](service-premium-what-is.md) mit einer Power BI-Lizenz.
* Das Power BI-Webpart für SharePoint Online erfordert [Moderne Seiten](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).
* Damit Benutzer eingebettete Berichte verwenden können, müssen sie sich beim Power BI-Dienst anmelden, um ihre Power BI-Lizenz zu aktivieren.

## <a name="embed-your-report"></a>Einbetten des Berichts
Um Ihren Bericht in SharePoint Online einzubetten, müssen Sie die Berichts-URL abrufen und sie mit dem Power BI-Webpart von SharePoint Online verwenden.

### <a name="get-a-report-url"></a>Abrufen einer Berichts-URL

1. Zeigen Sie den Bericht in Power BI an.

2. Klicken Sie im Dropdownmenü **Weitere Optionen** auf **Einbetten** > **SharePoint Online**.

    ![Option „SharePoint Online“ im Menü „Weitere Optionen“](media/service-embed-report-spo/power-bi-more-options-sharepoint-online.png)

3. Kopieren Sie die Berichts-URL aus dem Dialogfeld.

    ![Einbetten eines Links](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Hinzufügen des Power BI-Berichts zu einer SharePoint Online-Seite

1. Öffnen Sie die Zielseite in SharePoint Online, und wählen Sie **Bearbeiten** aus.

    ![Seite „Bearbeitungen“ in SP](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Alternativ können Sie in Sharepoint Online **+ Neu** auswählen, um eine neue moderne Websiteseite zu erstellen.

    ![Neue Seite in SP](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Wählen Sie die **+** -Dropdownliste und dann das **Power BI**-Webpart aus.

    ![Neuer Webpart in SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Wählen Sie **Bericht hinzufügen** aus.

    ![Neuer Bericht in SP](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Fügen Sie die zuvor kopierte Berichts-URL in den Bereich **Power BI-Berichtslink** ein. Der Bericht wird automatisch geladen.

    ![Neue Webparteigenschaften in SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Wählen Sie **Veröffentlichen** aus, damit Ihre SharePoint Online-Benutzer die Änderung sehen können.

    ![SP-Bericht geladen](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Gewähren des Zugriffs auf Berichte

Nachdem Sie einen Bericht in SharePoint Online eingebettet haben, haben die Benutzer nicht automatisch die Berechtigung, den Bericht anzuzeigen: Sie müssen die Ansichtsberechtigungen in Power BI festlegen.

> [!IMPORTANT]
> Überprüfen Sie im Power BI-Dienst, wer den Bericht sehen kann, und stellen Sie sicher, dass nicht aufgeführte, berechtigte Benutzer Zugriff erhalten.

Es gibt zwei Möglichkeiten, den Berichtszugriff in Power BI zu erteilen. Erstens können Sie beim Erstellen der SharePoint Online-Teamwebsite auf Grundlage einer Office 365-Gruppe den Benutzer als Mitglied des **Arbeitsbereichs im Power BI-Dienst** und der **SharePoint-Seite** aufführen. Weitere Informationen finden Sie unter [Verwalten eines Arbeitsbereichs](service-manage-app-workspace-in-power-bi-and-office-365.md).

Zweitens können Sie einen Bericht in eine App einbetten und diese direkt für Benutzer freigeben:  

1. Der Autor, der ein Pro-Benutzer sein muss, erstellt einen Bericht in einem Arbeitsbereich. Zur Freigabe für *Power BI Free-Benutzer* muss der Arbeitsbereich als *Premium-Arbeitsbereich* festgelegt sein.

2. Der Ersteller veröffentlicht die App und installiert sie dann. Der Autor muss die App installieren, damit er Zugriff auf die Berichts-URL hat, die zum Einbetten in SharePoint Online verwendet wird.

3. Nun müssen auch alle Endbenutzer die App installieren. Sie können außerdem die Funktion **App automatisch installieren** verwenden, die Sie im [Power BI-Verwaltungsportal](service-admin-portal.md) aktivieren können, damit die App für die Endbenutzer vorinstalliert wird.

   ![App automatisch installieren](media/service-embed-report-spo/install-app-automatically.png)

4. Der Ersteller öffnet die App und ruft den Bericht auf.

5. Der Autor kopiert die einzubettende Berichts-URL aus dem von der App installierten Bericht. Verwenden Sie nicht die ursprüngliche Berichts-URL aus dem Arbeitsbereich.

6. Erstellen Sie in SharePoint Online eine neue Teamwebsite.

7. Fügen Sie die zuvor kopierte Berichts-URL zum Power BI-Webpart hinzu.

8. Fügen Sie alle Endbenutzer und/oder Gruppen hinzu, die die Daten auf der SharePoint Online-Seite und in der von Ihnen erstellten Power BI-App verwenden werden.

    > [!NOTE]
    > **Benutzer bzw. Gruppen benötigen Zugriff sowohl auf die SharePoint Online-Seite als auch auf den Bericht in der Power BI-App, um den Bericht auf der SharePoint-Seite anzuzeigen.**

Jetzt kann der Endbenutzer die Teamseite in SharePoint Online aufrufen und die Berichte auf der Seite anzeigen.

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

Wenn Ihre Power BI-Umgebung die Anmeldung mit mehrstufiger Authentifizierung (MFA) erfordert, können Sie aufgefordert werden, Ihre Identität mithilfe eines Sicherheitsgeräts zu bestätigen. Dies geschieht, wenn Sie sich nicht mithilfe von mehrstufiger Authentifizierung bei SharePoint Online angemeldet haben, Ihre Power BI-Umgebung aber ein Sicherheitsgerät zum Überprüfen eines Kontos erfordert.

> [!NOTE]
> Power BI unterstützt noch keine mehrstufige Authentifizierung bei Azure Active Directory 2.0: den Benutzern wird eine Fehlermeldung angezeigt. Der Benutzer kann sich mithilfe eines Sicherheitsgeräts erneut bei SharePoint Online anmelden, um Zugriff auf den Bericht zu erhalten.

## <a name="web-part-settings"></a>Webpart-Einstellungen

Unten finden Sie die Einstellungen, die Sie für das Power BI-Webpart für SharePoint Online anpassen können.

![Webparteigenschaften in SP](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Eigenschaft | Beschreibung |
| --- | --- |
| Seitenname |Legt die Standardseite des Webparts fest. Wählen Sie einen Wert aus der Dropdownliste aus. Wenn keine Seiten angezeigt werden, verfügt der Bericht entweder nur über eine Seite, oder die eingefügte URL enthält den Seitennamen. Entfernen Sie den Berichtsabschnitt aus der URL, um eine bestimmte Seite auswählen zu können. |
| Anzeige |Passt die Einpassung des Berichts in die SharePoint Online-Seite an. |
| Navigationsbereich anzeigen |Zeigt den Navigationsbereich der Seite an oder blendet ihn aus. |
| Filterbereich anzeigen |Anzeigen oder Ausblenden des Filterbereichs. |

## <a name="reports-that-do-not-load"></a>Nicht geladene Berichte

Falls Ihr Bericht im Power BI-Webpart nicht geladen wird, wird möglicherweise die folgende Meldung angezeigt:

![Nachricht „Dieser Inhalt ist nicht verfügbar“](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Dies kann vor allem zwei Gründe haben.

1. Sie besitzen keinen Zugriff auf den Bericht.
2. Der Bericht wurde gelöscht.

Wenden Sie sich an den Besitzer der SharePoint Online-Seite, um dieses Problem zu beheben.

## <a name="licensing"></a>Lizenzierung

Benutzer, die einen Bericht in SharePoint anzeigen, benötigen entweder eine **Power BI Pro-Lizenz**, oder der Inhalt muss sich in einem Arbeitsbereich integriert sein, der sich in einer **[Power BI Premium-Kapazität (EM oder P SKU)](service-admin-premium-purchase.md)** befindet.

## <a name="known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen

* Fehler: „Es ist ein Fehler aufgetreten, melden Sie sich ab und wieder an und öffnen Sie diese Seite dann erneut. Korrelations-ID: nicht definiert, HTTP-Antwortstatus: 400, Serverfehlercode 10001, Meldung: Fehlendes Aktualisierungstoken“
  
  Wenn Sie diesen Fehler erhalten, versuchen Sie einen der folgenden Schritte zur Fehlerbehebung.
  
  1. Melden Sie sich bei SharePoint ab und anschließend wieder an. Achten Sie darauf, alle Browserfenster zu schließen, bevor Sie sich erneut anmelden.

  2. Wenn MFA für Ihr Benutzerkonto erforderlich ist, melden Sie sich mit Ihrem MFA-Gerät (Smartphone-App, Smartcard usw.) bei SharePoint an.
  
  3. Azure B2B-Gastbenutzerkonten werden nicht unterstützt. Den Benutzern wird das Power BI-Logo angezeigt, das anzeigt, dass der Teil geladen wird, jedoch wird der Bericht nicht angezeigt.

* Power BI unterstützt nicht die gleichen lokalisierte Sprachen wie SharePoint Online. Daher wird im eingebetteten Bericht möglicherweise nicht die ordnungsgemäße Lokalisierung angezeigt.

* Bei Verwendung von Internet Explorer 10 können Probleme auftreten. <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->

* Das Power BI-Webpart ist für [nationale Clouds](https://powerbi.microsoft.com/clouds/) nicht verfügbar.

* Der klassische Server von SharePoint Server wird mit diesem Webpart nicht unterstützt.

* [URL-Filter](service-url-filters.md) werden mit dem SPO-Webpart nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

* [Erstellen moderner Websiteseiten durch Endbenutzer zulassen oder verhindern](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Erstellen und Verteilen einer App in Power BI](service-create-distribute-apps.md)  
* [Freigeben eines Dashboards für Kollegen und andere](service-share-dashboards.md)  
* [Was ist Power BI Premium?](service-premium-what-is.md)
* [Einbetten eines Berichts in ein sicheres Portal oder eine sichere Website](service-embed-secure.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
