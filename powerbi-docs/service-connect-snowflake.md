---
title: Herstellen einer Verbindung mit Snowflake in Power BI
description: Snowflake mit SSO für Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 4d98274aa0b9aa09db99add2dda91a3ba8fed40b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576875"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Herstellen einer Verbindung mit Snowflake im Power BI-Dienst

## <a name="introduction"></a>Einführung

Das Herstellen einer Verbindung mit Snowflake im Power BI-Dienst unterscheidet sich in einem Punkt von anderen Connectors: Für AAD sind zusätzliche Funktionen verfügbar (mit einer Option für SSO). Verschiedene Teile der Integration erfordern unterschiedliche Administratorrollen für Snowflake, Power BI und Azure. Sie können die AAD-Authentifizierung auch ohne einmaliges Anmelden (SSO) aktivieren. Die Standardauthentifizierung funktioniert ähnlich wie andere Connectors im Dienst.

Wenn Sie daran interessiert sind, die AAD-Integration zu konfigurieren und optional SSO zu aktivieren, gibt es folgende Möglichkeiten:
* Lesen Sie sich den Artikel [Erste Schritte: Snowflake mit SSO für Power BI](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) in der Snowflake-Dokumentation durch, wenn Sie Snowflake-Administrator sind.
* (SSO) Lesen Sie den Abschnitt „Konfiguration des Power BI-Diensts: Verwaltungsportal“, wenn Sie Power BI-Administrator sind.
* (SSO) Lesen Sie den Abschnitt „Konfiguration des Power BI-Diensts: Aktivieren eines Datasets“, wenn Sie Power BI-Datenbankersteller sind.

## <a name="power-bi-service-configuration"></a>Konfiguration des Power BI-Diensts

### <a name="admin-portal"></a>Verwaltungsportal

Wenn Sie SSO aktivieren möchten, muss der Mandantenadministrator zum Verwaltungsportal wechseln und das Senden von Power BI-AAD-Anmeldeinformationen an Snowflake genehmigen.

![Mandantenadministratoreinstellung für Snowflake-SSO](media/service-connect-snowflake/snowflakessotenant.png)

Navigieren Sie zum „Verwaltungsportal“, klicken Sie auf der Seitenleiste auf „Mandanteneinstellungen“, und scrollen Sie nach unten zu „Integrationseinstellungen“, um die Option „Snowflake-SSO“ anzuzeigen.

Wie bereits erwähnt müssen Sie diese manuell aktivieren, damit Ihr AAD-Token an die Snowflake-Server gesendet werden kann. Klicken Sie zum Aktivieren der Option zunächst auf den Umschalter „Disabled“ (Deaktiviert) und dann auf „Apply“ (Anwenden), und warten Sie, bis die Einstellungen geändert werden. Es kann bis zu einer Stunde dauern, bis der Dienst die Konfiguration weitergibt.

Nachdem dieser Vorgang abgeschlossen ist, können Sie Berichte mit SSO verwenden.

### <a name="configuring-a-dataset-with-aad"></a>Konfigurieren eines Datasets mit AAD

Nachdem ein auf dem Snowflake-Connector basierender Bericht im Web veröffentlicht wurde, muss der Ersteller des Datasets im Power BI-Webdienst zum entsprechenden Arbeitsbereich navigieren und zunächst auf „Datasets“ und dann auf „Einstellungen“ klicken (über das „...“-Menü neben dem relevanten Dataset für weitere Aktionen).

Aufgrund der Funktionsweise von Power BI funktioniert SSO nur, wenn keine Datenquellen über das lokale Datengateway ausgeführt werden.

* Wenn Sie nur eine Snowflake-Quelle in Ihrem Datenmodell verwenden, können Sie SSO verwenden, wenn Sie das lokale Datengateway nicht verwenden möchten.
* Wenn Sie eine Snowflake-Quelle zusammen mit einer anderen Quelle verwenden, können Sie SSO verwenden, wenn keine der Quellen das lokale Datengateway verwenden.
* Wenn Sie eine Snowflake-Quelle über das lokale Datengateway verwenden, werden AAD-Anmeldeinformationen aktuell nicht unterstützt. Dies kann relevant sein, wenn Sie versuchen, von einer einzelnen IP-Adresse aus auf ein virtuelles Netzwerk zuzugreifen, auf dem das Gateway installiert ist, und nicht vom gesamten Power BI-IP-Adressbereich.
* Wenn Sie neben einer anderen Quelle, die ein Gateway erfordert, eine Snowflake-Quelle verwenden, müssen Sie auch Snowflake über das lokale Datengateway verwenden und können SSO nicht nutzen.

Weitere Informationen zur Verwendung des lokalen Datengateways finden Sie im Artikel [Was ist ein lokales Daten Gateway?](https://docs.microsoft.com/power-bi/service-gateway-onprem).

Wenn Sie das Gateway nicht verwenden, können Sie fortfahren. Wenn Sie Snowflake-Anmeldeinformationen auf dem lokalen Datengateway konfiguriert haben, diese Datenquelle aber nur in Ihrem Modell verwenden, können Sie auf der Seite „Dataseteinstellungen“ auf den Umschalter klicken, um das Gateway für dieses Datenmodell zu deaktivieren.

![Dataseteinstellung zum Deaktivieren des Gateways](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

Der Ersteller des Datasets muss auf „Datenquellen-Anmeldeinformationen“ klicken und sich anmelden. Das Dataset kann mit Basisanmeldeinformationen oder OAuth2-Anmeldeinformationen (AAD) in Snowflake signiert werden. Wenn Sie AAD verwenden, kann das Dataset für die Verwendung von SSO aktiviert werden. Wenn sich dieser erste Benutzer für das Dataset bei Snowflake anmelden möchte, muss er die Option auswählen, durch die andere Benutzer OAuth2-Anmeldeinformationen zum Abrufen von Daten verwenden. Dadurch wird AAD-SSO aktiviert. Unabhängig davon, ob sich der erste Benutzer mit der Standardauthentifizierung oder OAuth2 (AAD) anmeldet, werden die AAD-Anmeldeinformationen für SSO gesendet. 

![Dataseteinstellung für Snowflake-SSO](media/service-connect-snowflake/snowflakessocredui.png)

Nachdem dies geschehen ist, sollten alle zusätzlichen Benutzer automatisch ihre AAD-Authentifizierung verwenden, um eine Verbindung mit Daten aus diesem Snowflake-Dataset herzustellen.

Wenn Sie SSO nicht aktivieren, verwenden Benutzer, die den Bericht aktualisieren, wie bei den meisten anderen Power BI-Berichten die Anmeldeinformationen des angemeldeten Benutzers.

### <a name="troubleshooting"></a>Problembehandlung

Wenn bei der Integration Probleme auftreten, finden Sie weitere Informationen im [Handbuch zur Problembehandlung in Snowflake](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting).

