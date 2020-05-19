---
title: 'Tutorial: Festlegen von Datenwarnungen auf Dashboards des Power BI-Diensts'
description: In diesem Tutorial erfahren Sie, wie Sie Warnungen festlegen, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen im Microsoft Power BI-Dienst festgelegten Grenzen überschreiten.
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 04/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 4cad37b9d4a7bf9e74a29312786a02b26fce5463
ms.sourcegitcommit: faa8cfb66e79ea16ba46605f752cc9ca57924d0e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83382759"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutorial: Festlegen von Warnungen für Power BI-Dashboards

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Legen Sie Warnungen fest, um Benachrichtigungen zu erhalten, wenn die Daten in den Dashboards die von Ihnen festgelegten Grenzen überschreiten. Warnungen können nur für Kacheln, die über Berichtsvisuals angeheftet wurden, und nur für Messgeräte, KPIs und Karten festgelegt werden. 

*Anwender* können Warnungen zu Kacheln in Dashboards hinzufügen, die sie in **Mein Arbeitsbereich** erstellt haben. *Anwender* können auch Warnungen zu Kacheln in Dashboards hinzufügen, die für sie in einer [Premium-Kapazität](end-user-license.md) freigegeben wurden. Wenn Sie über eine Power BI Pro-Lizenz verfügen, können Sie auch Warnungen für Kacheln in einem anderen Arbeitsbereich festlegen.
Da diese Funktion noch weiterentwickelt wird, sehen Sie sich den Abschnitt weiter unten zu [Tipps und Problembehandlung](#tips-and-troubleshooting) an.

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

In diesem Beispiel wird eine Dashboardkartenkachel aus der Beispiel-App „Sales & Marketing“ verwendet. Diese App ist unter [Microsoft AppSource](https://appsource.microsoft.com) verfügbar. Hilfe zur Installation der App erhalten Sie unter [Installieren und Verwenden der „Vertrieb und Marketing“-App](end-user-app-marketing.md).

1. Wählen Sie von einem Messgerät, KPI oder einer Kartenkachel eines Dashboards die Auslassungspunkte aus.
   
   ![Kartenkachel](media/end-user-alerts/power-bi-cards.png)
2. Wählen Sie das Glockensymbol ![Warnungssymbol](media/end-user-alerts/power-bi-bell-icon.png) oder **Warnungen verwalten** aus, um eine oder mehrere Warnungen für **Marktanteil der Einheiten in Prozent** hinzuzufügen.

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

Es gibt viele Möglichkeiten zum Verwalten von Warnungen: in der Dashboardkachel, im Menü für Power BI-Einstellungen, auf einer einzelnen Kachel in der [mobilen Power BI-App auf dem iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) oder in der [mobilen Power BI-App für Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

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

* Wenn Sie für ein Messgerät, eine KPI oder eine Karte keine Warnung festlegen können, bitten Sie Ihren Mandantenadministrator um Hilfe. Manchmal sind Warnungen für Ihr Dashboard oder bestimmte Dashboardkacheln deaktiviert oder nicht verfügbar.
* Warnungen erfolgen nur für Daten, die aktualisiert werden. Sie können nicht für statische Daten ausgelöst werden. Die meisten der von Microsoft bereitgestellten Beispiele sind statisch. 
* Zum Empfangen und Aufrufen von geteilten Inhalten ist eine Power BI Pro- oder Power BI Premium-Lizenz erforderlich. Weitere Informationen finden Sie unter [So ermitteln Sie Ihren Lizenztyp](end-user-license.md).
* Warnungen können für visuelle Elemente festgelegt werden, die aus Streamingdatasets erstellt wurden, die aus einem Bericht an ein Dashboard angeheftet wurden. Warnungen können nicht für Streamingkacheln festgelegt werden, die direkt auf dem Dashboard über **Kachel hinzufügen** > **Benutzerdefinierte Streamingdaten** erstellt wurden.


## <a name="clean-up-resources"></a>Bereinigen von Ressourcen
Anleitungen zum Löschen von Warnungen sind weiter oben beschrieben. Kurz gesagt, wählen Sie das Zahnradsymbol auf der Power BI-Menüleiste. Klicken Sie unter **Einstellungen** auf **Warnungen** und löschen Sie die Warnung.

> [!div class="nextstepaction"]
> [Festlegen von Datenwarnungen auf Ihrem mobilen Gerät](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


