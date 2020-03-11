---
title: Anzeigen von mobilen SSRS-Berichten und -KPIs in der mobilen Windows 10-App – Power BI
description: Die mobile Power BI-App für Windows 10 bietet touchfähigen, mobilen Livezugriff auf Ihre wichtigen lokalen Geschäftsdaten.
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: mshenhav
ms.openlocfilehash: 4666e7c0e4901a99867ea72ab404df4cbffe110b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879351"
---
# <a name="view-reporting-services-ssrs-mobile-reports-and-kpis-in-the-windows-10-power-bi-mobile-app"></a>Anzeigen von mobilen SSRS (Reporting Services)-Berichten und -KPIs in der mobilen Power BI-App für Windows 10
Die mobile Power BI-App für Windows 10 bietet touchfähigen, mobilen Livezugriff auf Ihre wichtigen lokalen Geschäftsdaten in SQL Server 2016 Reporting Services. 

![Mobile Reporting Services-Berichte](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>Das Wichtigste zuerst
[Erstellen Sie mobile Reporting Services-Berichte](https://msdn.microsoft.com/library/mt652547.aspx) mit dem SQL Server 2016 Enterprise Edition Mobile Report Publisher, und veröffentlichen Sie sie im [Reporting Services-Webportal](https://msdn.microsoft.com/library/mt637133.aspx). Erstellen Sie KPIs direkt im Webportal. Organisieren Sie sie in Ordnern, und markieren Sie Ihre Favoriten, damit Sie sie leicht finden können. 

Zeigen Sie dann in der mobilen Power BI-App für Windows 10 die mobilen Berichte und KPIs in Ordnern organisiert oder als Favoriten zusammengestellt an. 

> [!NOTE]
> Auf Ihrem Gerät muss Windows 10 ausgeführt werden. Die App funktioniert am besten auf Geräten mit mindestens 1 GB RAM und 8 GB internem Speicher.
> 
> 

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Erkunden von Beispielen ohne einen SQL Server 2016 Reporting Services-Server
Auch wenn Sie keinen Zugriff auf ein Reporting Services-Webportal haben, können Sie trotzdem die Funktionen von mobilen Reporting Services-Berichten untersuchen.

1. Öffnen Sie auf Ihrem Windows 10-Gerät die Power BI-App.
2. Tippen Sie auf die globale Navigationsschaltfläche ![Globale Navigationsschaltfläche](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) in der linken oberen Ecke.
3. Tippen Sie auf das Symbol **Einstellungen**![Symbol „Einstellungen“](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), klicken Sie mit der rechten Maustaste auf **Mit Server verbinden** (oder halten Sie diese Option gedrückt), und tippen Sie dann auf **Beispiele anzeigen**.
   
   ![SSRS-Beispiele anzeigen](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Öffnen Sie dann den Ordner „Retail Reports“ oder „Sales Reports“, um die zugehörigen KPIs und mobilen Berichte auszuwählen.
   
   ![Beispiel-KPIs und mobile Berichte](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Durchsuchen Sie die Beispiele, um mit KPIs und mobilen Berichten zu interagieren.

## <a name="connect-to-a-reporting-services-report-server"></a>Verbinden mit einem Reporting Services-Berichtsserver
1. Tippen Sie unten im Navigationsbereich auf **Einstellungen** ![Symbol „Einstellungen“](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Tippen Sie auf **Mit Server verbinden**.
3. Geben Sie die Adresse des Servers sowie Ihren Benutzernamen und das Kennwort ein. Verwenden Sie dieses Format für die Adresse des Servers:
   
     `https://<servername>/reports` ODER `https://<servername>/reports`
   
   > [!NOTE]
   > Geben Sie am Anfang der Verbindungszeichenfolge **http** oder **https** ein.
   > 
   > 
   
    Tippen Sie optional auf **Erweiterte Optionen**, um einen Namen für den Server einzugeben.
4. Tippen Sie auf das Häkchen, um die Verbindung herzustellen. 
   
   Der Server wird jetzt im Navigationsbereich angezeigt.
   
   ![Server im Navigationsbereich](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Durch Tippen auf die globale Navigationsschaltfläche ![Globale Navigationsschaltfläche](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) können Sie jederzeit zwischen mobilen Reporting Services-Berichten und Ihren Dashboards im Power BI-Dienst wechseln. 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Anzeigen von Reporting Services-KPIs und mobilen Berichten in der Power BI-App
Die KPIs und mobilen Berichte von Reporting Services werden in den gleichen Ordnern wie im Reporting Services-Webportal angezeigt.

![Berichtsordner](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Tippen Sie auf einen KPI, um diesen im Fokusmodus anzuzeigen.
  
    ![KPI im Fokusmodus](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Tippen Sie auf einem mobilen Bericht, um diesen in der Power BI-App zu öffnen und mit der Interaktion zu beginnen.
  
    ![Reporting Services-Mobilgerätebericht](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Anzeigen Ihrer bevorzugten KPIs und Berichte
Sie können KPIs und mobile Berichte als Favoriten auf Ihrem Reporting Services-Webportal markieren und dann bequem neben den als Favoriten gespeicherten Dashboards und Berichten in einem Ordner auf Ihrem Windows 10-Gerät anzeigen.

* Tippen Sie auf **Favoriten**.
  
   ![Symbol „Favoriten“](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Ihre Favoriten vom Webportal werden alle auf dieser Seite angezeigt.
  
   ![Seite „Favoriten“](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-favorites.png)

Weitere Informationen zu [Favoriten in den mobilen Power BI-Apps](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Entfernen einer Verbindung mit einem Berichtsserver
In der mobilen Power BI-App ist jeweils nur eine Verbindung mit einem Berichtsserver möglich. Wenn Sie eine Verbindung mit einem anderen Server herstellen möchten, müssen Sie erst die Verbindung mit dem aktuellen Server trennen.

1. Tippen Sie unten im Navigationsbereich auf **Einstellungen** ![Symbol „Einstellungen“](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Tippen Sie auf den Servernamen, dessen Verbindung Sie trennen möchten, und halten Sie ihn gedrückt.
3. Tippen Sie auf **Server entfernen**.
   
    ![Server entfernen](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Erstellen von mobilen Reporting Services-Berichten und KPIs
Reporting Services KPIs und mobile Berichte werden nicht in der mobilen Power BI-App erstellt. Sie werden im Publisher für mobile Berichte von SQL Server und im SQL Server 2016 Reporting Services-Webportal erstellt.

* [Erstellen Sie eigene mobile Reporting Services-Berichte](https://msdn.microsoft.com/library/mt652547.aspx), und veröffentlichen Sie sie in einem Reporting Services-Webportal.
* Erstellen Sie [KPIs in einem Reporting Services-Webportal](https://msdn.microsoft.com/library/mt683632.aspx).

## <a name="next-steps"></a>Nächste Schritte
* [Erste Schritte mit der mobilen Power BI-App für Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [Was ist Power BI?](../../fundamentals/power-bi-overview.md)  
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

