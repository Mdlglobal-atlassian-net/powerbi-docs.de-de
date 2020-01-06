---
title: 'Übersicht: Single Sign-On für Gateways in Power BI'
description: Konfigurieren Ihres Gateways zur Aktivierung des SSO von Power BI bei lokalen Datenquellen
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: bfa4534b625a965226dfced17403a7e2da7a7f84
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "74699197"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Übersicht: Single Sign-On für Gateways in Power BI

Sie können nahtlose Verbindungen mit einmaligem Anmelden erreichen und für Power BI-Berichte und -Dashboards das Aktualisieren von lokalen Daten in Echtzeit ermöglichen, indem Sie Ihr lokales Datengateway konfigurieren. Sie haben die Option, Ihr Gateway entweder mit eingeschränkter [Kerberos](service-gateway-sso-kerberos.md)-Delegierung oder der Security Assertion Markup Language ([SAML](service-gateway-sso-saml.md)) zu konfigurieren. Das lokale Datengateway unterstützt das einmalige Anmelden über [DirectQuery](desktop-directquery-about.md). Damit werden Verbindungen mit lokalen Datenquellen hergestellt.

Power BI unterstützt die folgenden Datenquellen:

* SQL Server (Kerberos)
* SAP HANA (Kerberos und SAML)
* SAP BW-Anwendungsserver (Kerberos)
* SAP BW-Nachrichtenserver (Kerberos), Öffentliche Vorschau
* Oracle (Kerberos), Öffentliche Vorschau
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

Das einmalige Anmelden (SSO) für [M-Erweiterungen](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md) wird derzeit nicht unterstützt.

Wenn ein Benutzer mit einem DirectQuery-Bericht im Power BI-Dienst interagiert, kann jeder Kreuzfilter-, Segmentierungs-, Sortier- und Berichtsbearbeitungsvorgang Abfragen bewirken, die live für die zugrunde liegende Datenquelle ausgeführt werden. Wenn Sie SSO für die Datenquelle konfigurieren, werden Abfragen unter der Identität des Benutzers ausgeführt, der mit Power BI interagiert (d. h. über die Webumgebung oder mobile Power BI-Apps). Daher sieht jeder Benutzer genau die Daten, für die er über Berechtigungen in der zugrunde liegenden Datenquelle verfügt. Wenn Single Sign-On konfiguriert ist, gibt es keine gemeinsame Zwischenspeicherung von Daten für verschiedene Benutzer.

## <a name="query-steps-when-running-sso"></a>Abfrageschritte beim Ausführen von SSO

Eine mit SSO ausgeführte Abfrage umfasst drei Schritte, wie in der folgenden Abbildung veranschaulicht.

![SSO-Abfrageschritte](media/service-gateway-sso-overview/sso-query-steps.png)

Es folgen weitere Details zu jedem Schritt:

1. Der Power BI-Dienst enthält für jede Abfrage den *Benutzerprinzipalnamen* (UPN, d. h. der voll qualifizierte Benutzernamen des Benutzers, der zurzeit beim Power BI-Dienst angemeldet ist), wenn eine Abfrageanforderung an das konfigurierte Gateway gesendet wird.

2. Das Gateway muss den Azure Active Directory-UPN einer lokalen Active Directory-Identität zuordnen.

   a. Wenn Azure AD DirSync (auch als *Azure AD Connect* bezeichnet) konfiguriert ist, erfolgt die Zuordnung automatisch im Gateway.

   b.  Andernfalls kann das Gateway den Azure AD-UPN suchen und einem lokalen AD-Benutzer zuordnen. Dies erfolgt durch eine Suche in der lokalen Active Directory-Domäne.

3. Der Prozess des Gatewaydiensts nimmt die Identität des zugeordneten lokalen Benutzers an, öffnet die Verbindung mit der zugrunde liegenden Datenbank und sendet die Abfrage. Das Gateway muss nicht auf denselben Computern wie die Datenbank installiert sein.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie sich nun grundlegend mit der Aktivierung von SSO über das Gateway auskennen, können Sie sich ausführlichere Informationen zu Kerberos und SAML ansehen:

* [Einmaliges Anmelden (SSO): Kerberos](service-gateway-sso-kerberos.md)
* [Einmaliges Anmelden (SSO): SAML](service-gateway-sso-saml.md)
