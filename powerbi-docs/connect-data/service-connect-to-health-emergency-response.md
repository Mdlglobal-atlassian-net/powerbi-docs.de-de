---
title: Herstellen einer Verbindung mit dem Supportdashboard für Notfalleinsätze im Krankenhaus
description: In diesem Artikel erfahren Sie, wie Sie das Supportdashboard für Entscheidungen in Bezug auf COVID-19 für die Vorlagen-App für medizinische Notfälle abrufen und installieren, und wie Sie eine Verbindung mit Daten herstellen.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 65f1246185584b5887d97bb9188b43e016e78e8f
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279248"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>Herstellen einer Verbindung mit dem Supportdashboard für Notfalleinsätze im Krankenhaus
Die Vorlagen-App für das Supportdashboard für Notfalleinsätze im Krankenhaus ist die Berichterstattungskomponente der [Microsoft Power Platform-Lösung für Notfalleinsätze](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/). Das Dashboard zeigt Krisenmanagern aggregierte Daten aus dem gesamten Gesundheitssystem an, mit deren Hilfe sie schnelle und richtige Entscheidungen treffen können.

![App-Bericht für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

In diesem Artikel erfahren Sie, wie Sie die App installieren und eine Verbindung mit den Datenquellen herstellen. Weitere Informationen zur Verwendung des Berichts, der Ihnen mit dieser App angezeigt wird, finden Sie in der [Dokumentation für das Supportdashboard für Notfalleinsätze im Krankenhaus](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard).

Nachdem Sie die Vorlagen-App installiert und eine Verbindung mit den Datenquellen hergestellt haben, können Sie den Bericht gemäß Ihren Anforderungen anpassen. Anschließend können Sie sie als App an Kollegen in Ihrer Organisation verteilen.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie diese Vorlagen-App installieren können, müssen Sie erst die [Power Platform-Lösung für Notfalleinsätze im Krankenhaus](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure) installieren und einrichten. Durch die Installation dieser Lösung werden die zum Befüllen der App mit Daten erforderlichen Datenquellenverweise erstellt.

Achten Sie beim Installieren der Power Platform-Lösung für Notfalleinsätze im Krankenhaus auf die [URL Ihrer Common Data Service-Umgebungsinstanz](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Diese benötigen Sie zum Herstellen einer Verbindung zwischen der Vorlagen-App und den Daten.

## <a name="install-the-app"></a>Installieren der App

1. Klicken Sie auf den folgenden Link, um die App zu erhalten: [Vorlagen-App für das Supportdashboard für Notfalleinsätze im Krankenhaus](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare)

1. Klicken Sie auf der AppSource-Seite für die App auf [**JETZT HOLEN**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare).

    [![App für das Supportdashboard für Notfalleinsätze im Krankenhaus in AppSource](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.powerapps_healthcare)

1. Lesen Sie die Informationen unter **Noch etwas**, und klicken Sie auf **Weiter**.

    ![„Noch etwas“ in der App für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. Wählen Sie **Installieren** aus. 

    ![Installieren der App für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    Nachdem die App installiert wurde, wird sie auf der Seite „Apps“ angezeigt.

   ![App für das Supportdashboard für Notfalleinsätze im Krankenhaus auf der Seite „Apps“](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Verbinden mit Datenquellen

1. Klicken Sie auf das Symbol auf der Seite „Apps“, um die App zu öffnen.

1. Klicken Sie auf dem Begrüßungsbildschirm auf **Erkunden**.

   ![Begrüßungsbildschirm der Vorlagen-App](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   Die App wird geöffnet, und es werden Beispieldaten angezeigt.

1. Klicken Sie auf dem Banner oben auf der Seite auf **Ihre Daten verbinden**.

   ![Link „Ihre Daten verbinden“ in der App für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. Gehen Sie im Dialogfeld wie folgt vor:
   1. Geben Sie in das Feld „Organisationsname“ den Namen Ihrer Organisation ein, z. B. „Contoso Health Systems“. Dieses Feld ist optional. Der Name wird oben links im Dashboard angezeigt.
   1. Geben Sie in das Feld „CDS_base_solution“ die [URL Ihrer Common Data Service-Umgebungsinstanz](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard) ein, z. B.: https://[myenv].crm.dynamics.com. Klicken Sie anschließend auf **Weiter**.

   ![URL-Dialogfeld der App für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. Legen Sie im nächsten Dialogfeld, das angezeigt wird, die Authentifizierungsmethode auf **OAuth2** fest. Sie müssen nichts an den Datenschutzeinstellungen ändern.

   Wählen Sie **Anmelden**.

   ![Authentifizierungsdialogfeld der App für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. Melden Sie sich auf dem Microsoft-Anmeldebildschirm bei Power BI an.

   ![Anmeldeseite von Microsoft](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   Nachdem Sie sich angemeldet haben, stellt der Bericht eine Verbindung mit den Datenquellen her und wird mit aktuellen Daten befüllt. Währenddessen verändert sich der Aktivitätsmonitor.

   ![Aktualisierung der App für das Supportdashboard für Notfalleinsätze im Krankenhaus](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planen der Berichtsaktualisierung

Wenn die Daten vollständig aktualisiert wurden, [richten Sie einen Aktualisierungszeitplan ein](../connect-data/refresh-scheduled-refresh.md), um die Berichtsdaten aktuell zu halten.

1. Klicken Sie im oberen Header auf **Power BI**.

   ![Power BI-Breadcrumb](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. Suchen Sie im linken Navigationsbereich unter **Arbeitsbereiche** nach dem Arbeitsbereich „Supportdashboard für Notfalleinsätze im Krankenhaus“, und befolgen Sie die im Artikel [Konfigurieren von geplanten Aktualisierungen](../connect-data/refresh-scheduled-refresh.md) beschriebenen Anweisungen.

## <a name="customize-and-share"></a>Anpassen und freigeben

Weitere Informationen finden Sie unter [Anpassen und Freigeben der App](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app). Lesen Sie sich unbedingt die [Haftungsausschlüsse zum Bericht](../create-reports/sample-covid-19-us.md#disclaimers) durch, bevor Sie die App veröffentlichen oder verteilen.

## <a name="next-steps"></a>Nächste Schritte
* [Grundlegendes zum Bericht für Notfalleinsätze im Krankenhaus](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [Einrichten und Kennenlernen der Beispielvorlage für die Krisenkommunikation in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
* [Was sind Power BI-Vorlagen-Apps?](../connect-data/service-template-apps-overview.md)
* [Installieren und Verteilen von Vorlagen-Apps in Ihrer Organisation](../connect-data/service-template-apps-install-distribute.md)
