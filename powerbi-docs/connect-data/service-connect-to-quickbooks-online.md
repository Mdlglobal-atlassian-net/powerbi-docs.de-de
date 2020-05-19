---
title: Herstellen einer Verbindung mit QuickBooks Online mithilfe von Power BI
description: QuickBooks Online für Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 4c21c36694f36e4d6f95b8edc920648313dc8a7a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348503"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Herstellen einer Verbindung mit QuickBooks Online mithilfe von Power BI
Wenn Sie über Power BI eine Verbindung mit Ihren QuickBooks Online-Daten herstellen, erhalten Sie sofort ein Power BI-Dashboard und Power BI-Berichte, die Rückschlüsse auf Cashflows im Unternehmen, Rentabilität, Kunden und weitere Informationen bereitstellen. Sie können die bereitgestellten Dashboards und Berichte unverändert verwenden oder sie anpassen, um die für Sie wichtigsten Informationen hervorzuheben. Die Daten werden automatisch einmal täglich aktualisiert.

Stellen Sie die Verbindung mit der [QuickBooks Online-Vorlagen-App](https://dxt.powerbi.com/getdata/services/quickbooks-online) für Power BI her.

>[!NOTE]
>Damit Sie die QuickBooks Online-Daten in Power BI importieren können, müssen Sie für Ihr QuickBooks Online-Konto über Administratorrechte verfügen und sich mit Ihren Administratoranmeldeinformationen anmelden. Sie können diesen Connector mit QuickBooks Desktop-Software verwenden. 

## <a name="how-to-connect"></a>Herstellen der Verbindung

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Wählen Sie **QuickBooks Online** und dann **Abrufen** aus.
   
   ![Abrufen von QuickBooks](media/service-connect-to-quickbooks-online/qbo.png)

4. Wählen Sie unter **Diese Power BI-App installieren?** die Option **Installieren** aus.

    ![Installieren von QuickBooks](media/service-connect-to-quickbooks-online/power-bi-install-quickbooks.png)

4. Wählen Sie im Bereich **Apps** die Kachel **QuickBooks** aus.

   ![Auswählen der Kachel „QuickBooks“](media/service-connect-to-quickbooks-online/power-bi-quickbooks-tile.png)

6. Klicken Sie im Fenster **Erste Schritte mit Ihrer neuen App** auf **Verbinden**.

    ![Erste Schritte mit Ihrer neuen App](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Wählen Sie als Authentifizierungsmethode die Option **oAuth2** und dann **Anmelden**aus. 
5. Geben Sie bei der entsprechenden Aufforderung Ihre QuickBooks Online-Anmeldeinformationen ein, und führen Sie den QuickBooks Online-Authentifizierungsprozess aus. Wenn Sie in Ihrem Browser bereits bei QuickBooks Online angemeldet sind, werden Sie möglicherweise nicht zur Eingabe von Anmeldeinformationen aufgefordert.
   >[!NOTE]
   >Für Ihr QuickBooks Online-Konto benötigen Sie Administratoranmeldeinformationen.
6. Wählen Sie auf dem nächsten Bildschirm das Unternehmen aus, das Sie mit Power BI verbinden möchten.
   
   ![Fast fertig in QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)

7. Wählen Sie auf dem nächsten Bildschirm **Autorisieren** aus, um den Importvorgang zu starten. Der Vorgang kann je nach Umfang Ihrer Unternehmensdaten einige Minuten dauern. 
   
   ![Autorisieren von QuickBooks](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
8. Nachdem Power BI die Daten importiert hat, sehen Sie die Inhaltsliste für Ihre QuickBooks App: ein neues Dashboard, einen neuen Bericht und ein neues Dataset.
9. Wählen Sie das Dashboard QuickBooks aus, um den Erkundungsprozess zu starten. Power BI hat dieses Dashboard automatisch erstellt, um Ihre importierten Daten anzuzeigen.

    ![Dashboard QuickBooks](media/service-connect-to-quickbooks-online/power-bi-connect-quickbooks-sample.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](../consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](../create-reports/service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](../consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="troubleshooting"></a>Problembehandlung
**„Es ist ein Fehler aufgetreten“**

Wenn Sie diese Meldung nach der Auswahl von **Autorisieren**erhalten:

„Es ist ein Fehler aufgetreten“ Schließen Sie dieses Fenster, und versuchen Sie es erneut.

Die Anwendung wurde für dieses Unternehmen bereits von einem anderen Benutzer abonniert. Wenden Sie sich an [Admin-E-Mail], um Änderungen an diesem Abonnement vorzunehmen.“

![Ups! Es ist ein Fehler aufgetreten.](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... dieser Fehler bedeutet, dass bereits ein anderer Administrator in Ihrem Unternehmen mit Power BI eine Verbindung mit den Unternehmensdaten hergestellt hat. Bitten Sie diesen Administrator, das Dashboard für Sie freizugeben. Derzeit kann jeweils nur ein Administratorbenutzer mit Power BI eine Verbindung zu einem bestimmten QuickBooks Online-Unternehmensdataset herstellen. Nachdem das Dashboard von Power BI erstellt wurde, kann es der Administrator für mehrere Kollegen im selben Power BI-Mandanten freigeben.

**„Diese Anwendung wurde nicht dafür konfiguriert, dass Verbindungen aus Ihrem Land zulässig sind“**

Derzeit unterstützt Power BI nur US-Versionen von QuickBooks Online. 

![Diese Anwendung wurde nicht dafür konfiguriert, dass Verbindungen aus Ihrem Land zulässig sind.](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](../fundamentals/power-bi-overview.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](../fundamentals/service-basic-concepts.md)
