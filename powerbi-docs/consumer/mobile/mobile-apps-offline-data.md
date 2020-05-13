---
title: Offlinemodus zum Anzeigen von Daten in mobilen Power BI-Apps
description: 'Erfahren Sie Näheres über die Vorteile über das Anzeigen von Power BI in einer mobilen App anstatt in einem mobilen Browser: Sie können Ihre Daten auch dann anzeigen, wenn keine Netzverbindung besteht.'
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/09/2019
ms.author: painbar
ms.openlocfilehash: cfb5e4f1f75437db6235ece0d8661bab3f008649
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148417"
---
# <a name="view-your-data-offline-in-the-power-bi-mobile-apps"></a>Offlinemodus zum Anzeigen von Daten in mobilen Power BI-Apps
Gilt für:

| ![iPhone](./media/mobile-apps-offline-data/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-offline-data/ipad-logo-50-px.png) | ![Android-Smartphone](./media/mobile-apps-offline-data/android-phone-logo-50-px.png) | ![Android-Tablet](./media/mobile-apps-offline-data/android-tablet-logo-50-px.png) | ![Windows 10](./media/mobile-apps-offline-data/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-Telefone |Android-Tablets |Windows 10-Geräte |

>[!NOTE]
>Die Unterstützung für die mobile Power BI-App für **Smartphones mit Windows 10 Mobile** wird am 16. März 2021 eingestellt. [Weitere Informationen](https://go.microsoft.com/fwlink/?linkid=2121400)

Power BI in einer mobilen App hat gegenüber der Verwendung in einem mobilen Browser einen entscheidenden Vorteil: Sie können Ihre Daten auch dann anzeigen, wenn keine Netzverbindung besteht. Dies wird als Offlinemodus bezeichnet. 

![Meldung zu fehlender Netzverbindung](./media/mobile-apps-offline-data/power-bi-iphone-no-network.png)

Power BI aktualisiert die Daten häufig, sodass Sie jederzeit aktuelle Antworten auf geschäftliche Fragen erhalten – selbst wenn Sie unterwegs sind oder sich in anderen Mobilfunknetzen aufhalten („Roaming“).

## <a name="data-access-while-youre-offline"></a>Datenzugriff im Offlinebetrieb
Während Sie offline sind, können Sie auf die Dashboards, auf die Sie vorher über die mobile App zugegriffen haben, zugreifen und mit diesen interagieren.

Zusätzlich haben Sie schreibgeschützten Zugriff auf alle Power BI-Berichte, auf die Sie zuvor über die mobile App zugegriffen haben. Sie können die vollständigen Berichte anzeigen, aber Sie können keine Filter, Kreuzfilter oder Slicer verwenden.

## <a name="background-data-refresh"></a>Datenaktualisierung im Hintergrund
Durch die Aktualisierung im Hintergrund werden Ihre Dashboardfavoriten sowie die Dashboards und Berichte, die Sie in den letzten zwei Wochen angezeigt haben, mit den Daten im Power BI-Dienst (nicht der Datenquelle) aktualisiert. Wenn eine WLAN-Verbindung besteht, wird die Aktualisierung im Hintergrund alle 2 Stunden ausgeführt. Wenn die Verbindung hingegen über ein 3G-Netz erfolgt, werden die Inhalte in Power BI alle 24 Stunden aktualisiert.

Sie können beispielsweise die Datenaktualisierung im Hintergrund deaktivieren, um eine hohe Netzwerkauslastung zu vermeiden. Überprüfen Sie hierzu die Einstellungen auf Ihrem Gerät.

> [!NOTE]
> Wenn Sie die mobile Power BI-App auf einem iOS-Gerät verwenden und Ihr Unternehmen Microsoft Intune MAM konfiguriert hat, ist die Datenaktualisierung im Hintergrund deaktiviert. Power BI aktualisiert die Daten über den Power BI-Dienst im Web, wenn Sie das nächste Mal die App aufrufen.
> 
> Erfahren Sie mehr über das [Konfigurieren der mobilen Power BI-Apps mit Microsoft Intune](../../admin/service-admin-mobile-intune.md). 
> 
> 

## <a name="offline-indicators"></a>Anzeige des Offlinemodus
Power BI zeigt klar an, wenn Sie in den Offline- oder Onlinemodus wechseln. Außerdem wird angezeigt, welche Dashboards, Berichte und Kacheln nicht offline verfügbar sind.

## <a name="limitations"></a>Einschränkungen
Wenn Sie Power BI auf Ihrem Mobilgerät im Offlinemodus nutzen, gelten diese Einschränkungen:

* Power BI kann bis zu 250 MB Daten offline zwischenspeichern.
* Für einige Kacheltypen ist eine aktive Serververbindung nötig, sie stehen daher nicht offline zur Verfügung; z. B. Kacheln von Bing-Karten und einige benutzerdefinierte Kacheln.
* Vollständige Excel-Arbeitsmappen sind in Power BI nicht offline verfügbar.
* Sie können mobile Reporting Services-Berichte und KPIs offline anzeigen, wenn Sie sie angezeigt haben, während sie verbunden waren. Sie aktualisieren sich nicht im Hintergrund. Sie aktualisieren sich jedes Mal, wenn Sie sie öffnen.
* In den mobilen Power BI-Apps können Sie keine Power BI Desktop-Dateien (PBIX-Dateien) anzeigen, die im Power BI-Berichtsserver gespeichert sind. 
* Paginierte Berichte (RDL) sind nicht verfügbar, wenn das Netzwerk offline ist.

## <a name="next-steps"></a>Weitere Schritte
Ihr Feedback hilft uns zu entscheiden, welche Features wir künftig implementieren. Geben Sie deshalb Ihr Votum ab, welche Features Sie sich in den Power BI Mobile-Apps wünschen. 

* [Power BI-Apps für mobile Geräte](mobile-apps-for-mobile-devices.md)
* Folgen Sie @MSPowerBI auf Twitter
* Werden Sie Teil der [Power BI-Community](https://community.powerbi.com/), um sich mit den Mitgliedern auszutauschen
* [Was ist Power BI?](../../fundamentals/power-bi-overview.md)