---
title: Ausführliche Informationen zu On-premises Data Gateway
description: Dieser Artikel befasst sich ausführlich mit dem lokalen Gateway. Er beleuchtet die Funktionsweise des Diensts in Kombination mit Azure Active Directory und Ihrem lokalen Active Directory, wenn Sie Analysis Services nutzen.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: c277c21ffd3546307f9c38dfc06364324702986f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699381"
---
# <a name="on-premises-data-gateway-in-depth"></a>Ausführliche Informationen zu On-premises Data Gateway

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Wir haben die Informationen aus diesem Artikel in mehrere Artikel zu Power BI und in die allgemeinen Dokumente verschoben. Folgen Sie den Links unter den einzelnen Überschriften, um die relevanten Inhalte zu finden.

## <a name="how-the-gateway-works"></a>Funktionsweise des Gateways

Siehe [Architektur eines lokalen Datengateways](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Liste der verfügbaren Datenquellentypen

Siehe [Verwalten von Datenquellen](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Authentifizierung gegenüber lokalen Datenquellen

Siehe [Authentifizierung gegenüber lokalen Datenquellen](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Authentifizierung gegenüber einer Analysis Services-Livedatenquelle

Siehe [Authentifizierung gegenüber einer Analysis Services-Livedatenquelle](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Rollenbasierte Sicherheit

Siehe [Rollenbasierte Sicherheit](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Sicherheit auf Zeilenebene

Siehe [Sicherheit auf Zeilenebene](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>Welche Rolle spielt Azure Active Directory?

Siehe [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Woher weiß ich meinen UPN?

Siehe [Wo erfahre ich meinen UPN?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="map-user-names-for-analysis-services-data-sources"></a>Zuordnen von Benutzernamen zu Analysis Services-Datenquellen

Siehe [Zuordnen von Benutzernamen zu Analysis Services-Datenquellen](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synchronisieren eines lokalen Active Directorys mit Azure Active Directory

Siehe [Synchronisieren eines lokalen Active Directorys mit Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Nächste Schritte

Weitere Informationen finden Sie in den Artikeln zu Datenquellen:

[Verwalten von Datenquellen](service-gateway-data-sources.md)
[Verwalten Ihrer Datenquelle – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Verwalten Ihrer Datenquelle –SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Verwalten Ihrer Datenquelle – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Verwalten der Datenquelle – Oracle](service-gateway-onprem-manage-oracle.md)  
[Verwalten der Datenquelle – Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>An welchen Stellen etwas schief gehen kann

Siehe [Fehlerbehebung für das lokale Datengateway](/data-integration/gateway/service-gateway-tshoot) und [Fehlerbehebung für Gateways – Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Das Anmeldekonto

Siehe [Das Anmeldekonto](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Windows-Dienstkonto

Siehe [Ändern des Dienstkontos für das lokale Datengateway](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Ports

Siehe [Ports](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Erzwingen der HTTPS-Kommunikation mit Azure Service Bus

Siehe [Erzwingen der HTTPS-Kommunikation mit Azure Service Bus](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Unterstützung für TLS 1.2

Siehe [TLS 1.2 für Gatewaydatenverkehr](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>So starten Sie das Gateway neu

Siehe [Neustart eines Gateways](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Nächste Schritte

[Was ist das lokale Datengateway?](service-gateway-onprem.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)