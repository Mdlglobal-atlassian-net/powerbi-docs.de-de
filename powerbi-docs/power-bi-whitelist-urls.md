---
title: Power BI-URLs zur Aufnahme in die Whitelist
description: In diesem Artikel werden URL-Endpunkte und Ports aufgeführt, die für die Konnektivität mit Power BI in eine Liste sicherer Adressen aufgenommen werden müssen.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.custom: seodec18
ms.openlocfilehash: 6844d09c04759f0cdb780b3c1805698f1b1b519f
ms.sourcegitcommit: 743167a911991d19019fef16a6c582212f6a9229
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78401923"
---
# <a name="power-bi-urls-for-whitelisting"></a>Power BI-URLs zur Aufnahme in die Whitelist

**Der Power BI-Onlinedienst**, auch als SaaS-App von Power BI bezeichnet, erfordert eine Verbindung mit dem Internet. Die unten aufgeführten Endpunkte sollten für Kunden, die den Power BI-Onlinedienst verwenden, erreichbar sein.

Um den Online-Dienst in Power BI zu verwenden, müssen Sie Verbindungen zu den in den Tabellen unten als **erforderlich** und auf den verknüpften Websites als **erforderlich** markierten Endpunkten herstellen können. Wenn sich der Link zu einer externen Website auf einen bestimmten Abschnitt bezieht, müssen Sie in diesem Abschnitt nur die Endpunkte überprüfen.

Endpunkte, die als **optional** markiert sind, können **auf die Whitelist gesetzt werden**, wenn die Nutzung bestimmter Funktionen erforderlich ist.

Der Power BI-Onlinedienst setzt nur voraus, dass für die aufgeführten Endpunkte der TCP-Port 443 geöffnet wird.

Platzhalter (*) stellen alle Ebenen unterhalb der Stammdomäne dar, und N/V wird verwendet, wenn keine Informationen verfügbar sind. Die Spalte **Ziel(e)** ist eine Liste mit FQDN/Domänen und Links zu externen Websites, die weitere Informationen zu den Endpunkten enthalten.

>[!Important]
>Die Informationen in den Tabellen unten gelten nicht für die  **Government Cloud**, **die Cloud Deutschland** oder **die Cloud China**.

## <a name="authentication"></a>Authentifizierung

Power BI ist auf die verschiedenen Endpunkte in den Office 365-Abschnitten zur Authentifizierung und Identität angewiesen. Zum Verwenden von Power BI müssen Sie eine Verbindung zu den Endpunkten herstellen können, die auf der unten verknüpften Website aufgeführt sind.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Erforderlich:** Authentifizierung und Identität | In der Office 365-Dokumentation finden Sie [allgemeine und Office Online-URLs](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online).  | N/V |

## <a name="general-site-usage"></a>Allgemeine Verwendung der Website

Für die allgemeine Verwendung von Power BI müssen Sie eine Verbindung zu den in der Tabelle aufgeführten Endpunkten und zu den Endpunkten, die auf den verknüpften Websites aufgeführt sind, herstellen können.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Erforderlich:** Back-End-APIs | *.analysis.windows.net | TCP 443 |
| 2 | **Erforderlich:** Back-End-APIs | *.pbidedicated.windows.net | TCP 443 |
| 3 | **Erforderlich:** Office 365-Integration | In der Office 365-Dokumentation finden Sie [allgemeine und Office Online-URLs](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/V |
| 4 | **Erforderlich:** Portal | app.powerbi.com | TCP 443 |
| 5 | **Erforderlich:** Diensttelemetrie | dc.services.visualstudio.com | TCP 443 |
| 6 | **Optional:** Informationsmeldungen | dynmsg.modpim.com | TCP 443 |
| 7 | **Optional:** NPS-Umfragen | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Verwaltung

Zum Ausführen administrativer Funktionen in Power BI müssen Sie eine Verbindung zu den Endpunkten auf den unten verknüpften Websites herstellen können.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Erforderlich:** Zum Verwalten von Benutzern und Anzeigen von Überwachungsprotokollen | In der Office 365-Dokumentation finden Sie [allgemeine und Office Online-URLs](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/V |
| | | |

## <a name="getting-data"></a>Abrufen von Daten

Zum Abrufen von Daten aus bestimmten Datenquellen wie OneDrive müssen Sie eine Verbindung zu den Endpunkten unten in der Tabelle herstellen können. Es kann sein, dass der Zugriff auf zusätzliche Internetdomänen und URLs für bestimmte Datenquellen erforderlich ist, die in Ihrer Organisation verwendet werden.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Erforderlich:** AppSource (interne oder externe Apps in Power BI) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **Optional:** Melden Sie sich an, und rufen Sie Daten für Inhaltspakete ab | Von verwendeten Inhaltspaketen abhängig | Von verwendeten Inhaltspaketen abhängig |
| 3 | **Optional:** Importieren von Dateien aus OneDrive (privat) | Weitere Informationen finden Sie auf der Website [Required URLs and ports for OneDrive site (Erforderliche URLs und Ports für OneDrive)](https://docs.microsoft.com/onedrive/required-urls-and-ports). | N/V |
| 4 | **Optional:** Power BI in 60 Sekunden, Videotutorial | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **Optional:** PubNub-Streamingdatenquellen | Weitere Informationen finden Sie in der [PubNub-Dokumentation](https://support.pubnub.com/support/solutions/articles/14000043522). | N/V |
| | | |

## <a name="dashboard-and-report-integration"></a>Dashboard- und Berichtsintegration

Zur Unterstützung von Dashboards und Berichten ist Power BI auf bestimmte Endpunkte angewiesen. Sie müssen eine Verbindung zu den Endpunkten in der Tabelle und den unten verknüpften Websites herstellen können.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Erforderlich:** Excel-Integration | In der Office 365-Dokumentation finden Sie [allgemeine und Office Online-URLs](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online). | N/V |
| | | |

## <a name="power-bi-visuals"></a>Power BI-Visuals

Power BI ist auf bestimmte Endpunkte angewiesen, um Power BI-Visuals anzeigen und darauf zugreifen zu können. Sie müssen eine Verbindung zu den Endpunkten in der Tabelle und den unten verknüpften Websites herstellen können.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Erforderlich:** Importieren eines benutzerdefinierten Visuals über die Marketplace-Schnittstelle oder aus einer Datei | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **Optional:** Bing Maps | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **Optional:** PowerApps | Weitere Informationen finden Sie im Abschnitt [Erforderliche Dienste](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) auf der Website mit den PowerApps-Systemanforderungen. | N/V |
| 4 | **Optional:** Visio | In der Office 365-Dokumentation finden Sie [allgemeine und Office Online-URLs](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) sowie [URLs von SharePoint Online und OneDrive for Business](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business). | N/V |
| | | |

## <a name="related-external-sites"></a>Verwandte externe Websites

Power BI verlinkt zu verwandten Websites. Das können z. B. Dokumentationen, Supportwebsites oder Websites für Anforderungen neuer Features sein. Der Zugriff auf diese Websites wirkt sich nicht auf die Funktionalität von Power BI aus, daher ist deren Aufnahme in die Whitelist optional.

| Zeile | Zweck | Ziel(e) | Port(s) |
| --- | --- | --- | --- |
| 1 | **Optional:** Community-Website | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **Optional:** Dokumentationswebsite | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **Optional:** Downloadwebsite (für Power BI Desktop usw.) | download.microsoft.com | TCP 443 |
| 4 | **Optional:** Externe Weiterleitungen | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **Optional:** Ideas-Website für Feedback| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **Optional:** Power BI-Website: Landing Page, Links zu weiteren Informationen, Supportwebsite, Downloadlinks, Partnershowcases usw. | powerbi.microsoft.com | TCP 443 |
| 7 | **Optional:** Power BI Developer Center | dev.powerbi.com | TCP 443 |
| 8 | **Optional:** Support-Website | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
