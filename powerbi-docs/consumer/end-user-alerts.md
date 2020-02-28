---
title: 'Tutorial: Festlegen von Datenwarnungen auf Dashboards des Power BI-Diensts'
description: In diesem Tutorial erfahren Sie, wie Sie Warnungen festlegen, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen im Microsoft Power BI-Dienst festgelegten Grenzen überschreiten.
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 5f4dc1d1f3e707a59ef81e63be42714c499d050f
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496514"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutorial: Festlegen von Warnungen für Power BI-Dashboards

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Legen Sie Warnungen fest, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen festgelegten Grenzen überschreiten. Warnungen können für Messgeräte, KPIs und Karten festgelegt werden. Da diese Funktion noch weiterentwickelt wird, sehen Sie sich den Abschnitt weiter unten zu [Tipps und Problembehandlung](#tips-and-troubleshooting) an.

![Kachel, Karte, KPI](media/end-user-alerts/card-gauge-kpi.png)

Die Warnungen werden nur Ihnen angezeigt, auch wenn Sie das Dashboard freigeben. Datenwarnungen werden mit allen Plattformen synchronisiert. Sie können Datenwarnungen daher [in den mobilen Power BI-Apps](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) und im Power BI-Dienst festlegen und anzeigen. 

> [!WARNING]
> Diese Warnungen enthalten Informationen zu Ihren Daten. Wenn Sie Power BI-Daten auf einem mobilen Gerät anzeigen und das Gerät gestohlen wird, sollten Sie mithilfe des Power BI-Diensts alle Warnungen deaktivieren.
> 

In diesem Tutorial werden folgende Themen behandelt:
> [!div class="checklist"]
> * Wer kann Warnungen einrichten?
> * Welche Visuals unterstützen Warnungen?
> * Wer kann meine Warnungen sehen?
> * Funktionieren Warnungen in Power BI Desktop und mobil?
> * So erstellen Sie eine Warnung
> * Wo werde ich meine Warnungen erhalten?

Wenn Sie noch nicht bei Power BI registriert sind, müssen Sie sich zuerst für eine [kostenlose Testversion registrieren](https://app.powerbi.com/signupredirect?pbi_source=web).

In diesem Beispiel wird eine Dashboardkartenkachel aus der Beispiel-App „Sales & Marketing“ verwendet. Diese App ist unter [Microsoft AppSource](https://appsource.microsoft.com) verfügbar. Hilfe zur Installation der App erhalten Sie unter [Installieren und Verwenden von Apps mit Dashboards und Berichten in Power BI](end-user-app-view.md).

1. Wählen Sie von einem Messgerät, KPI oder einer Kartenkachel eines Dashboards die Auslassungspunkte aus.
   
   ![Kartenkachel](media/end-user-alerts/power-bi-cards.png)
2. Wählen Sie das Glockensymbol ![Warnungssymbol](media/end-user-alerts/power-bi-bell-icon.png) oder **Warnungen verwalten** aus, um eine oder mehrere Warnungen für **Filialen insgesamt** hinzuzufügen.

   ![Kartenkachel mit ausgewählten Auslassungspunkten](media/end-user-alerts/power-bi-ellipses.png)

   
1. Wählen Sie **+ Warnungsregel hinzufügen** im Bereich **Warnungen verwalten** aus.  Stellen Sie sicher, dass der Schieberegler auf **Ein** festgelegt ist, und geben Sie der Warnung einen Titel. Durch Titel lassen sich Warnungen schnell einordnen.
   
   ![Fenster „Warnungen verwalten“](media/end-user-alerts/power-bi-manage-alert.png)
4. Scrollen Sie nach unten, und geben Sie die Warnungsdetails ein.  In diesem Beispiel erstellen wir eine Warnung, die uns einmal täglich benachrichtigt, wenn unser Marktanteil auf 35 oder höher ansteigt. Warnungen werden in der Mitteilungszentrale angezeigt. Und außerdem lassen wir uns von Power BI eine E-Mail senden.
   
   ![Fenster „Warnungen verwalten“, Festlegen des Schwellenwerts](media/end-user-alerts/power-bi-manage-alert-details.png)
5. Klicken Sie auf **Speichern und schließen**.
 
   > [!NOTE]
   > Warnungen erfolgen nur für Daten, die aktualisiert werden. Wenn Daten aktualisiert werden, überprüft Power BI, ob eine Warnung für diese Daten festgelegt ist. Wenn die Daten einen Warnungsschwellenwert erreicht haben, wird eine Warnung ausgelöst. 
   > 

## <a name="receiving-alerts"></a>Empfangen von Warnungen
Wenn die nachverfolgten Daten einen der von Ihnen festgelegten Schwellenwerte erreichen, erfolgen mehrere Aktionen. Power BI überprüft zunächst, ob seit dem Senden der letzten Warnung mehr als eine Stunde oder mehr als 24 Stunden (je nach der von Ihnen ausgewählten Option) verstrichen sind. Solange die Daten den Schwellenwert überschreiten, erhalten Sie eine Warnung.

Anschließend sendet Power BI eine Warnung an Ihre Mitteilungszentrale und optional an Ihre E-Mail-Adresse. Jede Warnung enthält einen direkten Link zu den entsprechenden Daten. Klicken Sie auf den Link, um die relevante Kachel zu sehen.  

1. Wenn Sie festgelegt haben, dass bei einer Warnung eine E-Mail an Sie gesendet wird, enthält Ihr Posteingang etwa Folgendes. Dies ist eine Warnung, die wir auf einem anderen Dashboard festlegen. Dieses Dashboard verfolgt abgeschlossene Aufgaben des Teams für Benutzerfreundlichkeit.
   
   ![Warnungs-E-Mail](media/end-user-alerts/power-bi-alert-email.png)
2. Power BI fügt der **Mitteilungszentrale** eine Nachricht und der entsprechenden Kachel das Symbol für eine neue Warnung hinzu.
   
   ![Benachrichtigungssymbol in Power BI](media/end-user-alerts/power-bi-task-alert.png)
3. Öffnen Sie die Mitteilungszentrale, um die Warnungsdetails anzuzeigen.
   
    ![Warnung lesen](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>Verwalten von Warnungen

Es gibt viele Möglichkeiten zum Verwalten von Warnungen: in der Dashboardkachel, im Menü für Power BI-Einstellungen, auf einer einzelnen Kachel in der [mobilen Power BI-App auf dem iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) oder in der [mobilen Power BI-App für Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>In der Kachel

1. Wenn Sie eine Warnung für eine Kachel ändern oder entfernen müssen, öffnen Sie das Fenster **Warnungen verwalten** erneut, indem Sie auf das Glockensymbol ![Warnungssymbol](media/end-user-alerts/power-bi-bell-icon.png) klicken. Alle Warnungen, die Sie für diese Kachel festgelegt haben, werden angezeigt.
   
    ![Fenster „Warnungen verwalten“](media/end-user-alerts/power-bi-manage-alerts.png).
2. Um eine Warnung zu ändern, wählen Sie den Pfeil links neben dem Namen der Warnung.
   
    ![Pfeil neben dem Namen der Warnung](media/end-user-alerts/power-bi-modify-alert.png).
3. Um eine Warnung zu löschen, wählen Sie den Papierkorb rechts neben dem Namen der Warnung.
   
      ![Papierkorbsymbol](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Im Menü für Power BI-Einstellungen

1. Wählen Sie das Zahnradsymbol auf der Power BI-Menüleiste.
   
    ![Zahnradsymbol](media/end-user-alerts/powerbi-gear-icon.png).
2. Wählen Sie unter **Einstellungen** die Option **Warnungen** aus.
   
    ![Registerkarte „Warnungen“ im Fenster „Einstellungen“](media/end-user-alerts/power-bi-alert-settings.png)
3. Hier können Sie Warnungen aktivieren und deaktivieren, das Fenster **Warnungen verwalten** öffnen, um Änderungen vorzunehmen, oder die Warnung löschen.

## <a name="tips-and-troubleshooting"></a>Tipps und Problembehandlung 

* Warnungen können nur für Messgeräte, KPIs und Karten festgelegt werden.
* Wenn Sie für ein Messgerät, eine KPI oder eine Karte keine Warnung festlegen können, bitten Sie Ihren Systemadministrator um Hilfe. Manchmal sind Warnungen für Ihr Dashboard oder bestimmte Dashboardkacheln deaktiviert oder nicht verfügbar.
* Warnungen erfolgen nur für Daten, die aktualisiert werden. Sie können nicht für statische Daten ausgelöst werden. Die meisten der von Microsoft bereitgestellten Beispiele sind statisch. 
* *Benutzer* erstellen nicht ihre eigenen Dashboards. Dashboards werden von *Designern* erstellt und anschließend mit den Benutzern geteilt. Zum Empfangen und Aufrufen von geteilten Inhalten ist eine Power BI Pro- oder Power BI Premium-Lizenz erforderlich. Weitere Informationen finden Sie unter [So ermitteln Sie Ihren Lizenztyp](end-user-license.md). 


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen
Anleitungen zum Löschen von Warnungen sind weiter oben beschrieben. Kurz gesagt, wählen Sie das Zahnradsymbol auf der Power BI-Menüleiste. Klicken Sie unter **Einstellungen** auf **Warnungen** und löschen Sie die Warnung.

> [!div class="nextstepaction"]
> [Festlegen von Datenwarnungen auf Ihrem mobilen Gerät](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


