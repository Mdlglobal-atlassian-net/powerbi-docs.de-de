---
title: Integration von Power BI in Microsoft Flow
description: Erfahren Sie, wie Sie Flows erstellen, die durch Power BI-Datenwarnungen ausgelöst werden.
author: mgblythe
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: mblythe
LocalizationGroup: Get started
ms.openlocfilehash: a5b5a34e7cd61ac9d197faa0ef4410cd9558f597
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881841"
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow und Power BI

[Microsoft Flow](https://flow.microsoft.com/documentation/getting-started) ist ein SaaS-Dienst zum Automatisieren von Workflows zwischen den immer zahlreicheren Anwendungen und SaaS-Diensten, auf die Geschäftsbenutzer zugreifen. Mit Flow können Sie Aufgaben automatisieren, indem Sie Ihre bevorzugten Apps und Dienste (einschließlich Power BI) synchronisieren, um Benachrichtigungen zu erhalten, Dateien zu synchronisieren, Daten zu sammeln und weitere Aktionen ausführen zu lassen. Die Automatisierung von Workflows vereinfacht Aufgaben, die sich wiederholen.

[Erste Schritte mit Flow](https://flow.microsoft.com/documentation/getting-started)

Sehen Sie sich an, wie Sirui einen Flow erstellt, der eine detaillierte E-Mail an Kollegen versendet, wenn eine Power BI-Warnung ausgelöst wird. Befolgen Sie dann die schrittweisen Anleitungen unter dem Video, um es selbst ausprobieren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Erstellen eines Flows, der durch eine Power BI-Datenwarnung ausgelöst wird

### <a name="prerequisites"></a>Voraussetzungen
In diesem Tutorial erfahren Sie, wie Sie zwei verschiedene Flows erstellen: einen Flow aus einer Vorlage und einen von Grund auf neuen Flow. Um die Schritte des Tutorials auszuführen, [erstellen Sie in Power BI eine Datenwarnung](service-set-data-alerts.md), erstellen ein kostenloses Slack-Konto und [registrieren Sie sich für Microsoft Flow](https://flow.microsoft.com/#home-signup) (kostenlos!).

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Erstellen eines Flows, der Power BI verwendet – aus einer Vorlage
In dieser Aufgabe verwenden wir eine Vorlage, um einen einfachen Flow zu erstellen, der durch eine Power BI-Datenwarnung (Benachrichtigung) ausgelöst wird.

1. Melden Sie sich bei Microsoft Flow („flow.microsoft.com“) an.
2. Wählen Sie **Meine Flows** aus.
   
   ![Menüleiste „Flow“](media/service-flow-integration/power-bi-my-flows.png)
3. Wählen Sie **Aus Vorlage erstellen** aus.
   
    ![Menüleiste „My Flows“ (Meine Flows)](media/service-flow-integration/power-bi-template.png)
4. Verwenden Sie das Suchfeld, um Power BI-Vorlagen zu suchen, und wählen Sie **Eine E-Mail an eine beliebige Zielgruppe senden, sobald durch Power BI-Daten eine Warnung ausgelöst wird > Weiter** aus.
   
    ![Suchergebnisse](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>Erstellen des Flows
Diese Vorlage verfügt über einen Trigger (Power BI-Datenwarnung bei neuen Olympiamedaillen für Irland) und eine Aktion (E-Mail senden). Wenn Sie ein Feld auswählen, werden dynamische Inhalte angezeigt, die Sie einschließen können.  In diesem Beispiel haben wir den Kachelwert und die Kachel-URL in den Nachrichtentext eingefügt.

![Vorlage „Flow“](media/service-flow-integration/power-bi-template1.png)

1. Wählen Sie in der Trigger-Dropdownliste eine Power BI-Datenwarnung aus. Wählen Sie die Option **New medal for Ireland** (Neue Medaille für Irland). Informationen zum Erstellen einer Warnung finden Sie unter [Datenwarnungen in Power BI](service-set-data-alerts.md).
   
   ![Dropdownliste für Warnungen](media/service-flow-integration/power-bi-trigger-flow.png)
2. Geben Sie mindestens eine gültige E-Mail-Adresse ein, und wählen Sie dann **Bearbeiten** (siehe unten) oder **Dynamische Inhalte hinzufügen** aus. 
   
   ![Anzeige „E-Mail senden an“](media/service-flow-integration/power-bi-flow-email.png)

3. Flow erstellt einen Titel und eine Nachricht für Sie, den bzw. die Sie beibehalten oder ändern können. Alle Werte, die Sie beim Erstellen der Warnung in Power BI festgelegt haben, können nun verwendet werden. Platzieren Sie einfach Ihren Cursor, und treffen Sie im grau hervorgehobenen Bereich Ihre Auswahl. 

   ![Anzeige „E-Mail senden an“](media/service-flow-integration/power-bi-flow-email-default.png)

1.  Wenn Sie beispielsweise in Power BI eine Warnung mit dem Titel **Wir haben eine weitere Medaille gewonnen** erstellt haben, können Sie **Warnungstitel** auswählen, um den Text in die Betreffzeile Ihrer E-Mail einzufügen.

    ![E-Mail-Text erstellen](media/service-flow-integration/power-bi-flow-message.png)

    Darüber hinaus haben Sie Möglichkeit, den standardmäßigen E-Mail-Text zu übernehmen oder einen eigenen zu erstellen. Das obige Beispiel enthält einige Änderungen an der Nachricht.

1. Wenn Sie fertig sind, wählen Sie **Flow erstellen** oder **Flow speichern** aus.  Der Flow wird erstellt und ausgewertet.  Wenn Fehler gefunden werden, wird Ihnen dies mitgeteilt.
2. Wenn Fehler gefunden wurden, wählen Sie **Fluss bearbeiten** aus, um sie zu beheben. Wählen Sie andernfalls **Fertig** aus, um den neuen Flow auszuführen.
   
   ![Erfolgsmeldung](media/service-flow-integration/power-bi-flow-running.png)
5. Sobald die Datenwarnung ausgelöst wird, wird eine E-Mail an die von Ihnen angegeben Adressen gesendet.  
   
   ![Warnungs-E-Mail](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>Erstellen eines Flows, der Power BI verwendet – ohne Vorlage (leer)
In dieser Aufgabe erstellen wir einen einfachen Flow von Grund auf neu, der durch eine Power BI-Datenwarnung (Benachrichtigung) ausgelöst wird.

1. Melden Sie sich bei Microsoft Flow an.
2. Wählen Sie **Meine Flows** > **Ohne Vorlage erstellen** aus.
   
   ![Obere Menüleiste „Flow“](media/service-flow-integration/power-bi-my-flows.png)
3. Verwenden Sie das Suchfeld, um einen Power BI-Trigger zu suchen, und wählen Sie **Power BI – wenn eine datenbasierte Warnung ausgelöst wird** aus.

### <a name="build-your-flow"></a>Erstellen des Flows
1. Wählen Sie in der Dropdownliste den Namen der Warnung aus.  Informationen zum Erstellen einer Warnung finden Sie unter [Datenwarnungen in Power BI](service-set-data-alerts.md).
   
    ![Namen der Warnung auswählen](media/service-flow-integration/power-bi-totalstores2.png)
2. Wählen Sie **Neuer Schritt** > **Aktion hinzufügen** aus.
   
   ![Neuen Schritt hinzufügen](media/service-flow-integration/power-bi-new-step.png)
3. Suchen Sie nach **Outlook**, und wählen Sie **Ereignis erstellen** aus.
   
   ![Erstellen des Flows](media/service-flow-integration/power-bi-create-event.png)
4. Füllen Sie die Ereignisfelder aus. Wenn Sie ein Feld auswählen, werden dynamische Inhalte angezeigt, die Sie einschließen können.
   
   ![Fortfahren mit dem Erstellen des Flows](media/service-flow-integration/power-bi-flow-event.png)
5. Wählen Sie zum Abschluss **Flow erstellen** aus.  Der Flow wird gespeichert und ausgewertet. Wenn keine Fehler vorliegen, wählen Sie **Fertig** aus, um diesen Flow auszuführen.  Der neue Flow wird der Seite **Meine Flüsse** hinzugefügt.
   
   ![Flow abschließen](media/service-flow-integration/power-bi-flow-running.png)
6. Wenn der Flow durch die Power BI-Datenwarnung ausgelöst wird, erhalten Sie eine ähnliche Outlook-Ereignisbenachrichtigung wie die folgende.
   
    ![Outlook-Benachrichtigung bei Auslösung des Flows](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>Nächste Schritte
* [Erste Schritte mit Microsoft Flow](https://flow.microsoft.com/documentation/getting-started/)
* [Festlegen von Datenwarnungen im Power BI-Dienst](service-set-data-alerts.md)
* [Festlegen von Datenwarnungen auf dem iPhone](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* [Festlegen von Datenwarnungen in der mobilen Power BI-App für Windows 10](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

