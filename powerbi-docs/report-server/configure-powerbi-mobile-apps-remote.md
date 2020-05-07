---
title: Remotekonfiguration des Zugriffs von mobilen Apps auf Berichtsserver
description: Erfahren Sie, wie Sie Ihre mobilen Apps remote für Ihren Berichtsserver konfigurieren.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: b84d7a23cf947b18302c761ff5f78143bf3356aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73925877"
---
# <a name="configure-power-bi-mobile-app-access-to-report-server-remotely"></a>Remotekonfiguration des Zugriffs der mobilen Power BI-App auf Berichtsserver

Gilt für:

| ![iPhone](./media/configure-powerbi-mobile-apps-remote/ios-logo-40-px.png) | ![Android-Smartphone](./media/configure-powerbi-mobile-apps-remote/android-logo-40-px.png) |
|:--- |:--- |
| iOS |Android- |

In diesem Artikel erfahren Sie, wie Sie das MDM-Tool Ihrer Organisation verwenden, um den Zugriff für mobile Power BI-App auf Berichtsserver zu konfigurieren. IT-Administratoren erstellen für die Konfiguration eine Richtlinie für die App-Konfiguration mit den erforderlichen Informationen, die per Push an die App weitergeleitet werden sollen. 

 Wenn die Berichtsserververbindung bereits konfiguriert ist, können Benutzer der mobilen App für Power BI einfacher eine Verbindung mit dem Berichtsserver ihrer Organisation herstellen. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Erstellen der Richtlinie für die App-Konfiguration im MDM-Tool 

Sie als Administrator müssen in Microsoft Intune die folgenden Schritte ausführen, um die Richtlinie für die App-Konfiguration zu erstellen. Die Schritte und Erfahrungen beim Erstellen der Richtlinie für die App-Konfiguration unterscheiden sich womöglich in anderen MDM-Tools. 

1. Verbinden Sie Ihr MDM-Tool. 
2. Erstellen Sie einen Namen und eine neue Richtlinie für die App-Konfiguration. 
3. Wählen Sie aus, an welchen Benutzer diese Richtlinie für die App-Konfiguration verteilt wird. 
4. Erstellen Sie Schlüssel-Wert-Paare. 

In der folgenden Tabelle sind die Paare aufgeführt.

|Schlüssel  |type  |Beschreibung  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Zeichenfolge | Berichtsserver-URL <br> Muss mit http/https beginnen |
| com.microsoft.powerbi.mobile.ServerUsername | Zeichenfolge | [Optional] <br> Der Benutzername, der zum Verbinden des Servers verwendet wird. <br> Wenn keiner vorhanden ist, fordert die App den Benutzer auf, den Benutzernamen für die Verbindung einzugeben.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Zeichenfolge | [Optional] <br> Der Standardwert ist „Berichtsserver“. <br> Ein Anzeigename, der in der App zur Darstellung des Servers verwendet wird | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolesch | Der Standardwert ist TRUE <br>Wenn der Wert TRUE festgelegt ist, werden sämtliche Berichtsserverdefinitionen überschrieben, die möglicherweise bereits auf dem mobilen Gerät gespeichert sind. Alle Server, die bereits konfiguriert wurden, werden gelöscht. <br> Wenn die Außerkraftsetzung auf TRUE festgelegt ist, wird dadurch auch verhindert, dass der Benutzer diese Konfiguration entfernt. <br> Bei FALSE werden die mithilfe von Push übertragenen Werte hinzugefügt, und vorhandene Einstellungen werden beibehalten. <br> Wenn dieselbe Server-URL bereits in der mobilen App konfiguriert ist, werden keine Änderungen an der Konfiguration durch die App vorgenommen. Die App fordert den Benutzer nicht dazu auf, für denselben Server erneut eine Authentifizierung durchzuführen. |

Unten sehen Sie ein Beispiel der Festlegung der Konfigurationsrichtlinie über Intune.

![Intune-Konfigurationseinstellungen](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-report-server"></a>Endbenutzer, die eine Verbindung mit einem Berichtsserver herstellen

 Angenommen, Sie veröffentlichen die Richtlinie für die App-Konfiguration für eine Verteilerliste. Wenn dann Benutzer und Geräte, die in dieser Liste aufgeführt sind, die mobile App starten, geschieht Folgendes. 

1. Den Benutzern wird eine Meldung angezeigt, die besagt, dass ihre mobile App mit einem Berichtsserver konfiguriert ist. Der Benutzer tippt dann auf **Anmelden**.

    ![Anmelden bei dem Berichtsserver](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Auf der Seite **Mit Server verbinden** sind die Berichtsserverdetails bereits ausgefüllt. Die Benutzer müssen auf **Verbinden** tippen.

    ![Ausgefüllte Berichtsserverdetails](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Zur Authentifizierung müssen Benutzer ein Kennwort eingeben und anschließend auf **Anmelden** tippen. 

    ![Ausgefüllte Berichtsserverdetails](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Sie können nun KPIs und Power BI-Berichte, die auf dem Berichtsserver gespeichert sind, anzeigen und mit diesen interagieren.

## <a name="next-steps"></a>Weitere Schritte

- [Aktivieren des Remotezugriffs auf Power BI Mobile mit dem Azure AD-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi)
- [Administratorübersicht](admin-handbook-overview.md)  
- [Installieren von Power BI-Berichtsserver](install-report-server.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

