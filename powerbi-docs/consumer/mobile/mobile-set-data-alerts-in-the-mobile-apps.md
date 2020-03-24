---
title: Festlegen von Datenwarnungen in den mobilen Power BI-Apps
description: Sie können in den mobilen Power BI-Apps Warnungen festlegen, um Benachrichtigungen erhalten, wenn die Daten in einem Dashboard die von Ihnen festgelegten Grenzen überschreiten.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/11/2019
ms.author: painbar
ms.openlocfilehash: ff33bc2005918ba08c6098afd91a020e0cb6ba79
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79435810"
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Festlegen von Datenwarnungen in den mobilen Power BI-Apps
Gilt für:

| ![iPhone](./media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](./media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Android-Smartphone](./media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Android-Tablet](./media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Android-Tablet](./media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-Telefone |Android-Tablets |Windows 10-Geräte |

Sie können Warnungen für Dashboards in den mobilen Power BI-Apps und im Power BI-Dienst festlegen. Mit Warnungen werden Sie benachrichtigt, wenn die Daten in einer Kachel die von Ihnen festgelegten Grenzen überschreiten. Warnungen können für Kacheln mit einer einzelnen Zahl (beispielsweise Karten und Messgeräte) verwendet werden, aber nicht für Streamingdaten. Sie können Datenwarnungen auf dem mobilen Gerät festlegen und im Power BI-Dienst anzeigen und umgekehrt. Nur Sie können die festgelegten Datenwarnungen sehen, auch wenn Sie ein Dashboard oder eine Momentaufnahme einer Kachel freigeben.

Sie können Warnungen für Kacheln festlegen, wenn Sie über eine Power BI Pro-Lizenz verfügen oder wenn das freigegebene Dashboard zu einer Premium-Kapazität gehört. 

> [!WARNING]
> Datengesteuerte Warnungsbenachrichtigungen liefern Informationen über Ihre Daten. Wenn das Gerät gestohlen wird, sollten Sie im Power BI-Dienst alle Regeln für datengesteuerte Warnungen deaktivieren. 
> 
> Erfahren Sie mehr über das [Verwalten von Datenwarnungen im Power BI-Dienst](../../service-set-data-alerts.md).
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>Datenwarnungen auf einem iPhone oder iPad
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>Festlegen einer Warnung auf einem iPhone oder iPad
1. Tippen Sie in einem Dashboard auf eine Zahlen- oder Maßstabkachel, um sie im Fokusmodus zu öffnen.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Tippen Sie auf das Glockensymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png), um eine Warnung hinzuzufügen.  
3. Tippen Sie auf **Warnungsregel hinzufügen**.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. Wählen Sie aus, ob Sie Warnungen bei Über- oder Unterschreiten eines Werts empfangen möchten, und legen Sie dann den Wert fest.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. Legen Sie fest, ob Warnungen stündlich oder täglich empfangen werden sollen und ob zusammen mit der Warnung auch eine E-Mail an Sie gesendet werden soll.
   
   > [!NOTE]
   > Sie empfangen Warnungen nicht jede Stunde oder jeden Tag, wenn die Daten während dieser Zeit nicht aktualisiert wurden.
   > 
   > 
6. Sie können auch den Warnungstitel ändern.
7. Tippen Sie auf **Speichern**.
8. Eine einzelne Kachel kann Warnungen für Werte über und unter einem Schwellenwert enthalten. Tippen Sie in **Benachrichtigungen verwalten** auf **Warnungsregel hinzufügen**.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>Verwalten von Warnungen auf dem iPhone oder iPad
Sie können einzelne Warnungen auf dem Mobilgerät verwalten oder [alle Warnungen im Power BI-Dienst verwalten](../../service-set-data-alerts.md).

1. Tippen Sie in einem Dashboard auf eine Zahlen- oder Maßstabkachel, die eine Warnung aufweist.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual_has_alert.png)

2. Tippen Sie auf das Glockensymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png).  
3. Tippen Sie auf den Namen der Warnung, um sie zu bearbeiten, tippen Sie auf den Schieberegler, um E-Mail-Benachrichtigungen zu deaktivieren, oder tippen Sie auf den Papierkorb, um die Warnung zu löschen.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Datenwarnungen auf einem Android-Gerät
### <a name="set-an-alert-on-an-android-device"></a>Festlegen einer Warnung auf einem Android-Gerät
1. Tippen Sie in einem Power BI-Dashboard auf eine Zahlen- oder Maßstabkachel, um sie zu öffnen.  
2. Tippen Sie auf das Glockensymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png), um eine Warnung hinzuzufügen.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. Tippen Sie auf das Plussymbol (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. Wählen Sie aus, ob Sie Warnungen bei Über- oder Unterschreiten eines Werts empfangen möchten, und geben Sie den Wert ein.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. Tippen Sie auf **Fertig**.
6. Legen Sie fest, ob Warnungen stündlich oder täglich empfangen werden sollen und ob zusammen mit der Warnung auch eine E-Mail an Sie gesendet werden soll.
   
   > [!NOTE]
   > Sie empfangen Warnungen nicht jede Stunde oder jeden Tag, wenn die Daten während dieser Zeit nicht aktualisiert wurden.
   > 
   > 
7. Sie können auch den Warnungstitel ändern.
8. Tippen Sie auf **Speichern**.

### <a name="manage-alerts-on-an-android-device"></a>Verwalten von Warnungen auf einem Android-Gerät
Sie können einzelne Warnungen in der mobilen Power BI-App verwalten oder [alle Warnungen im Power BI-Dienst verwalten](../../service-set-data-alerts.md).

1. Tippen Sie in einem Dashboard auf eine Karten- oder Maßstabkachel, die eine Warnung aufweist.  
2. Tippen Sie auf das Glockensymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png).  
3. Tippen Sie auf die Warnung, um einen Wert zu ändern oder die Warnung zu deaktivieren.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. Tippen Sie auf das Pluszeichen (+), um derselben Kachel eine weitere Warnung hinzuzufügen.
5. Um die Warnung ganz zu entfernen, tippen Sie auf das Papierkorbsymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Datenwarnungen auf einem Windows-Gerät

>[!NOTE]
>Die Unterstützung für die mobile Power BI-App für **Smartphones mit Windows 10 Mobile** wird am 16. März 2021 eingestellt. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=2121400)

### <a name="set-data-alerts-on-a-windows-device"></a>Festlegen von Datenwarnungen auf einem Windows-Gerät
1. Tippen Sie in einem Dashboard auf eine Zahlen- oder Maßstabkachel, um sie zu öffnen.  
2. Tippen Sie auf das Glockensymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png), um eine Warnung hinzuzufügen.  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. Tippen Sie auf das Plussymbol (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. Wählen Sie aus, ob Sie Warnungen bei Über- oder Unterschreiten eines Werts empfangen möchten, und geben Sie den Wert ein.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. Legen Sie fest, ob Warnungen stündlich oder täglich empfangen werden sollen und ob zusammen mit der Warnung auch eine E-Mail an Sie gesendet werden soll.
   
   > [!NOTE]
   > Sie empfangen Warnungen nicht jede Stunde oder jeden Tag, wenn die Daten während dieser Zeit nicht aktualisiert wurden.
   > 
   > 
6. Sie können auch den Warnungstitel ändern.
7. Tippen Sie auf das Häkchen.
8. Eine einzelne Kachel kann Warnungen für Werte über und unter einem Schwellenwert enthalten. Tippen Sie in **Warnungen verwalten** auf das Pluszeichen (+).
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Verwalten von Warnungen auf einem Windows-Gerät
Sie können einzelne Warnungen in der mobilen Power BI-App verwalten oder [alle Warnungen im Power BI-Dienst verwalten](../../service-set-data-alerts.md).

1. Tippen Sie in einem Dashboard auf eine Karten- oder Maßstabkachel, die eine Warnung aufweist.  
2. Tippen Sie auf das Glockensymbol ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png).  
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. Tippen Sie auf die Warnung, um einen Wert zu ändern oder die Warnung zu deaktivieren.
   
    ![](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. Um die Warnung vollständig zu löschen, klicken Sie mit der rechten Maustaste darauf, oder halten Sie die Warnung gedrückt, und wählen Sie **Löschen** aus.

## <a name="receiving-alerts"></a>Empfangen von Warnungen
Sie empfangen Warnungen in der Power BI-[Mitteilungszentrale](mobile-apps-notification-center.md) auf dem Mobilgerät oder im Power BI-Dienst zusammen mit Benachrichtigungen zu neuen Dashboards, die für Sie freigegeben wurden.

Häufig wird die tägliche Aktualisierung von Datenquellen festgelegt, manche werden jedoch in kürzeren Abständen aktualisiert. Wenn die Daten im Dashboard aktualisiert werden und die nachverfolgten Daten einen der von Ihnen festgelegten Schwellenwerte erreichen, erfolgen mehrere Aktionen.

1. Power BI überprüft, ob seit dem Senden der letzten Warnung mehr als eine Stunde oder mehr als 24 Stunden (je nach der von Ihnen ausgewählten Option) verstrichen sind.
   
   Solange die Daten den Schwellenwert überschreiten, erhalten Sie stündlich oder alle 24 Stunden eine Warnung.
2. Wenn Sie festgelegt haben, dass bei einer Warnung eine E-Mail an Sie gesendet wird, enthält Ihr Posteingang etwa Folgendes.
   
   ![](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. Power BI fügt eine Benachrichtigung in Ihre [Mitteilungszentrale](mobile-apps-notification-center.md) und einen gelben Punkt zum Glockensymbol ![Glockensymbol](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png) in der Titelleiste (iOS und Android) oder zur globalen Navigationsschaltfläche ![globale Navigationsschaltfläche](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) (Windows 10-Geräte) hinzu.


4. Tippen Sie auf das Glockensymbol ![Glockensymbol](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png) oder die globale Navigationsschaltfläche ![Globale Navigationsschaltfläche](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png), um [ Ihre **Mitteilungszentrale**](mobile-apps-notification-center.md) zu öffnen und die Details der Warnung anzuzeigen.
   
     

> [!NOTE]
> Warnungen erfolgen nur für Daten, die aktualisiert werden. Wenn Daten aktualisiert werden, überprüft Power BI, ob eine Warnung für diese Daten festgelegt ist. Wenn die Daten einen Warnungsschwellenwert erreicht haben, wird eine Warnung ausgelöst.
> 
> 

## <a name="tips-and-troubleshooting"></a>Tipps und Problembehandlung
* Für Bing-Kacheln und für Kartenkacheln mit Datum/Uhrzeit-Measures werden Warnungen derzeit nicht unterstützt.
* Warnungen können nur für numerische Daten ausgelöst werden.
* Warnungen erfolgen nur für Daten, die aktualisiert werden. Sie können nicht für statische Daten ausgelöst werden.
* Warnungen können nicht mit Kacheln verwendet werden, die Streamingdaten enthalten.

## <a name="next-steps"></a>Nächste Schritte
* [Verwalten von Warnungen im Power BI-Dienst](../../service-set-data-alerts.md)
* [Mobile Power BI-Mitteilungszentrale](mobile-apps-notification-center.md)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

