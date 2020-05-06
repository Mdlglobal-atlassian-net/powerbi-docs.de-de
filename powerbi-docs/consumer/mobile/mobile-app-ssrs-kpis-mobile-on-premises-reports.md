---
title: Anzeigen lokaler Berichte und KPIs in den mobilen Power BI-Apps
description: Die mobile Power BI-Apps bieten touchfähigen, mobilen Livezugriff auf Ihre lokalen Geschäftsdaten in SQL Server Reporting Services und Power BI-Berichtsserver.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/05/2019
ms.author: painbar
ms.openlocfilehash: 6020a6cb72be4e8d7be0485c7787fefc097e679d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75220053"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Anzeigen lokaler Berichte und KPIs eines Berichtsservers in den mobilen Power BI-Apps

Die mobilen Power BI-Apps bieten touchfähigen, mobilen Livezugriff auf Ihre lokalen Geschäftsdaten in Power BI-Berichtsserver und SQL Server 2016 Reporting Services (SSRS).

Gilt für:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android-Smartphone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android-Tablet](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-Telefone |Android-Tablets |


![Report Server-Startseite in den mobilen Apps](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Das Wichtigste zuerst
**Die mobilen Apps dienen zum Anzeigen von Power BI-Inhalten und nicht zu deren Erstellung.**

* Sie und andere Berichtersteller in Ihrer Organisation können [Power BI-Berichte mit Power BI Desktop erstellen und dann im Webportal von Power BI-Berichtsserver veröffentlichen](../../report-server/quickstart-create-powerbi-report.md). 
* Sie können [KPIs direkt im Webportal](https://docs.microsoft.com/sql/reporting-services/working-with-kpis-in-reporting-services) erstellen, sie mithilfe von Ordnern organisieren und als Favoriten markieren, damit Sie sie später einfach wiederfinden. 
* [Erstellen Sie mobile Reporting Services-Berichte](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) mit dem SQL Server 2016 Enterprise Edition Mobile Report Publisher, und veröffentlichen Sie sie im [Reporting Services-Webportal](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode).  

Stellen Sie dann in den mobilen Power BI-Apps eine Verbindung mit bis zu fünf Berichtsservern her, um die Power BI-Berichte und KPIs in Ordnern organisiert oder als Favoriten zusammengestellt anzuzeigen. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Untersuchen von Beispielen in den mobilen Apps ohne Serververbindung
Auch wenn Sie keinen Zugriff auf ein Reporting Services-Webportal haben, können Sie trotzdem die Features von mobilen Reporting Services-Berichten und KPIs untersuchen. 

1. Tippen Sie auf Ihr Profilbild in der oberen linken Ecke, und tippen Sie dann auf **Einstellungen** im sich öffnenden Kontobereich.

2. Tippen Sie auf der sich öffnenden Einstellungsseite auf **Reporting Services-Beispiele**, und durchsuchen Sie diese, um mit den beispielhaften KPIs und mobilen Berichten zu interagieren.
   
   ![Beispiele für Reporting Services](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Herstellen einer Verbindung mit einem lokalen Berichtsserver
In den mobilen Power BI-Apps können Sie lokale Power BI-Berichte, mobile Reporting Services-Berichte und KPIs anzeigen. 

1. Öffnen Sie auf Ihrem Mobilgerät die Power BI-App.
2. Wenn Sie sich noch nicht bei Power BI angemeldet haben, tippen Sie auf **Berichtsserver**.
   
   ![Anmelden bei einem Berichtsserver](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Wenn Sie sich bereits bei der Power BI-App angemeldet haben, tippen Sie auf Ihr Profilbild in der oberen linken Ecke, und tippen Sie dann auf **Einstellungen** im sich öffnenden Kontobereich.
3. Tippen Sie auf der sich öffnenden Einstellungsseite auf **Mit Server verbinden**.
   
    ![Mit Server verbinden](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

    Die mobile App muss irgendwie auf den Server zugreifen können. Hierzu gibt es verschiedene Möglichkeiten:
     * Am einfachsten ist es, wenn sie sich im gleichen Netzwerk befindet oder über VPN verbunden ist.
     * Für eine Verbindung von außerhalb der Organisation kann auch ein Webanwendungsproxy verwendet werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Reporting Services mithilfe von OAuth](mobile-oauth-ssrs.md).
     * Öffnen Sie in der Firewall eine Verbindung (Port).

4. Tragen Sie die Serveradresse ein, und geben Sie dem Server einen Anzeigenamen, wenn Sie möchten. Verwenden Sie dieses Format für die Adresse des Servers:
   
     `https://<servername>/reports`
   
     OR
   
     `https://<servername>/reports`
   
   Geben Sie vor der Verbindungszeichenfolge **http** oder **https** ein.
   
    ![Dialogfeld „Mit Server verbinden“](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. Nachdem Sie die Serveradresse und den optionalen Anzeigenamen eingegeben haben, tippen Sie auf **Verbinden**, und geben Sie dann Ihren Benutzernamen und Ihr Kennwort ein, wenn Sie dazu aufgefordert werden.
6. Jetzt wird Ihnen im Kontobereich der Server angezeigt. In diesem Beispiel heißt dieser „Arbeitsserver“.
   
   ![Berichtsserver im Navigationsbereich](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios-or-android"></a>Herstellen einer Verbindung mit einem lokalen Berichtsserver in iOS oder Android

Wenn Sie Power BI in der mobilen App für iOS oder Android anzeigen, hat Ihr IT-Administrator womöglich eine App-Konfigurationsrichtlinie definiert. Falls dies der Fall ist, wird die Verbindung mit dem Berichtsserver optimiert, und Sie müssen nicht mehr so viele Informationen bereitstellen, wenn Sie eine Verbindung zu einem Berichtsserver herstellen. 

1. Es wird eine Meldung angezeigt, die besagt, dass Ihre mobile App mit einem Berichtsserver konfiguriert ist. Tippen Sie auf **Anmelden**.

    ![Anmelden bei dem Berichtsserver](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  Auf der Seite **Mit Server verbinden** sind die Berichtsserverdetails bereits ausgefüllt. Tippen Sie auf **Verbinden**.

    ![Ausgefüllte Berichtsserverdetails](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Geben Sie zur Authentifizierung ein Kennwort ein, tippen Sie dann auf **Anmelden**. 

    ![Ausgefüllte Berichtsserverdetails](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

Sie können nun KPIs und Power BI-Berichte, die auf dem Berichtsserver gespeichert sind, anzeigen und mit diesen interagieren.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Anzeigen von Power BI-Berichten und KPIs in der Power BI-App
Power BI-Berichte, mobile Reporting Services-Berichte und KPIs werden in den gleichen Ordnern wie im Reporting Services-Webportal angezeigt. 

* Tippen Sie auf einen Power BI-Bericht ![Symbol für Power BI-Bericht](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). Er wird im Querformat geöffnet, und Sie können in der Power BI-App mit ihm interagieren.

    > [!NOTE]
  > Die Ausführung eines Drilldowns und Drillups ist derzeit in Power BI-Berichten auf einem Power BI-Berichtsserver nicht aktiviert.
  
    ![Power BI-Bericht](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* In Power BI Desktop können die Besitzer von Berichten [einen Bericht für die mobilen Power BI-Apps optimieren](../../desktop-create-phone-report.md). Auf dem Mobiltelefon sind optimierte Berichte mit einem speziellen Symbol, ![Symbol für optimierten Power BI-Bericht](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png) gekennzeichnet, und sie weisen ein besonderes Layout auf.
  
    ![Für Mobilgeräte optimierter Power BI-Bericht](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Tippen Sie auf einen KPI, um diesen im Fokusmodus anzuzeigen.
  
    ![KPI im Fokusmodus](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Anzeigen Ihrer bevorzugten KPIs und Berichte
Sie können KPIs und Berichte im Webportal als Favoriten markieren und dann bequem neben den als Favoriten gespeicherten Power BI-Dashboards in einem Ordner auf Ihrem Mobilgerät anzeigen.

* Tippen Sie auf **Favoriten** in der Navigationsleiste.
  
   ![Favoriten im Navigationsbereich](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Ihre bevorzugten KPIs und Berichte aus dem Webportal befinden sich zusammen mit Power BI-Dashboards im Power BI-Dienst alle auf dieser Seite:
  
   ![Power BI-Berichte und -Dashboard auf der Seite „Favoriten“](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Entfernen einer Verbindung mit einem Berichtsserver
1. Öffnen Sie den Kontobereich, und klicken Sie auf **Einstellungen**.
2. Tippen Sie auf den Servernamen, dessen Verbindung Sie trennen möchten.
3. Tippen Sie auf **Server entfernen**.

## <a name="next-steps"></a>Weitere Schritte
* [Was ist Power BI?](../../fundamentals/power-bi-overview.md)  
* Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

