---
title: Herstellen einer Verbindung mit dem Präsenzbericht zur Krisenkommunikation
description: Erfahren Sie, wie Sie die Vorlagen-App zum COVID-19-Präsenzbericht zur Krisenkommunikation erhalten und installieren und wie Sie eine Verbindung mit Daten herstellen.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: f637bb10ed7ec27dcb3da07fc04cae39328ffebe
ms.sourcegitcommit: 34cca70ba84f37b48407d5d8a45c3f51fb95eb3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752255"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>Herstellen einer Verbindung mit dem Präsenzbericht zur Krisenkommunikation

Bei dieser Power BI-App handelt es sich um das Berichts-/Dashboardartefakt in der Microsoft Power Platform-Lösung für die Krisenkommunikation. Es verfolgt den Workerstandort für Benutzer der App zur Krisenkommunikation. Die Lösung kombiniert Funktionen von Power Apps, Power Automate, Teams, SharePoint und Power BI. Sie kann im Web, mobil oder in Teams verwendet werden.

![App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

Das Dashboard zeigt Krisenmanagern aggregierte Daten aus dem gesamten Gesundheitssystem an, mit deren Hilfe sie schnelle und richtige Entscheidungen treffen können.

In diesem Artikel erfahren Sie, wie Sie die App installieren und eine Verbindung mit den Datenquellen herstellen. Weitere Informationen zur App zur Krisenkommunikation finden Sie unter [Einrichten und Kennenlernen der Beispielvorlage für die Krisenkommunikation in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app).

Nachdem Sie die Vorlagen-App installiert und eine Verbindung mit den Datenquellen hergestellt haben, können Sie den Bericht gemäß Ihren Anforderungen anpassen. Anschließend können Sie sie als App an Kollegen in Ihrer Organisation verteilen.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie diese Vorlagen-App installieren, müssen Sie zunächst das [Beispiel für die Krisenkommunikation](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app) installieren und einrichten. Durch die Installation dieser Lösung werden die zum Befüllen der App mit Daten erforderlichen Datenquellenverweise erstellt.

Beachten Sie beim Installieren des Beispiels für die Krisenkommunikation den [„CI_Employee Status“-Ordnerpfad der SharePoint-Liste und die Listen-ID](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi).

## <a name="install-the-app"></a>Installieren der App

1. Klicken Sie auf den folgenden Link, um die App zu erhalten: [Vorlagen-App zum Präsenzbericht zur Krisenkommunikation](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Klicken Sie auf der AppSource-Seite für die App auf [**JETZT HOLEN**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms).

    [![App zum Präsenzbericht zur Krisenkommunikation in AppSource](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. Lesen Sie die Informationen unter **Noch etwas**, und klicken Sie auf **Weiter**.

    ![„Noch etwas“ zur App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. Wählen Sie **Installieren** aus. 

    ![Installieren der App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    Nachdem die App installiert wurde, wird sie auf der Seite „Apps“ angezeigt.

   ![App zum Präsenzbericht zur Krisenkommunikation auf der Seite „Apps“](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Verbinden mit Datenquellen

1. Klicken Sie auf das Symbol auf der Seite „Apps“, um die App zu öffnen.

1. Klicken Sie auf dem Begrüßungsbildschirm auf **Explore app** (App erkunden).

   ![Begrüßungsbildschirm mit Vorlagen-App](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   Die App wird geöffnet, und es werden Beispieldaten angezeigt.

1. Klicken Sie auf dem Banner oben auf der Seite auf **Ihre Daten verbinden**.

   ![„Ihre Daten verbinden“ in der App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. Gehen Sie im Dialogfeld wie folgt vor:
   1. Geben Sie im Feld „SharePoint_Folder“ den [„CI_Employee Status“-Pfad der SharePoint-Liste](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi) ein.
   1. Geben Sie im Feld „List_ID“ die Listen-ID ein, die Sie aus den Listeneinstellungen erhalten haben. Klicken Sie anschließend auf **Weiter**.

   ![URL-Dialogfeld der App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. Legen Sie im nächsten Dialogfeld, das angezeigt wird, die Authentifizierungsmethode auf **OAuth2** fest. Sie müssen nichts an den Datenschutzeinstellungen ändern.

   Wählen Sie **Anmelden**.

   ![Dialogfeld zur Authentifizierung für die App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Melden Sie sich auf dem Microsoft-Anmeldebildschirm bei Power BI an.

   ![Anmeldeseite von Microsoft](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   Nachdem Sie sich angemeldet haben, stellt der Bericht eine Verbindung mit den Datenquellen her und wird mit aktuellen Daten befüllt. Währenddessen verändert sich der Aktivitätsmonitor.

   ![„Aktualisierung wird durchgeführt“ in der App zum Präsenzbericht zur Krisenkommunikation](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planen der Berichtsaktualisierung

Wenn die Daten vollständig aktualisiert wurden, [richten Sie einen Aktualisierungszeitplan ein](../refresh-scheduled-refresh.md), um die Berichtsdaten aktuell zu halten.

1. Klicken Sie im oberen Header auf **Power BI**.

   ![Power BI-Breadcrumb](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. Suchen Sie im linken Navigationsbereich unter **Arbeitsbereiche** nach dem Arbeitsbereich „Supportdashboard für Notfalleinsätze im Krankenhaus“, und befolgen Sie die im Artikel [Konfigurieren von geplanten Aktualisierungen](../refresh-scheduled-refresh.md) beschriebenen Anweisungen.

## <a name="customize-and-share"></a>Anpassen und freigeben

Weitere Informationen finden Sie unter [Anpassen und Freigeben der App](../service-template-apps-install-distribute.md#customize-and-share-the-app). Lesen Sie sich unbedingt die [Haftungsausschlüsse zum Bericht](../create-reports/sample-covid-19-us.md#disclaimers) durch, bevor Sie die App veröffentlichen oder verteilen.

## <a name="next-steps"></a>Nächste Schritte
* [Einrichten und Kennenlernen der Beispielvorlage für die Krisenkommunikation in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
* [Was sind Power BI-Vorlagen-Apps?](../service-template-apps-overview.md)
* [Installieren und Verteilen von Vorlagen-Apps in Ihrer Organisation](../service-template-apps-install-distribute.md)
