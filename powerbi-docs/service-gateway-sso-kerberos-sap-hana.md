---
title: Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) bei SAP HANA
description: Konfigurieren Ihres SAP HANA-Servers, um einmaliges Anmelden vom Power BI-Dienst zu aktivieren
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9c2eb554a4e3b3ec90d3fe17145e0ec277298e1b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74697495"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) bei SAP HANA

In diesem Artikel wird beschrieben, wie Sie Ihre SAP HANA-Datenquelle dafür konfigurieren, dass SSO vom Power BI-Dienst aktiviert wird.

> [!NOTE]
> Bevor Sie versuchen, einen auf SAP HANA basierenden Bericht zu aktualisieren, der Kerberos SSO verwendet, führen Sie beide Schritte in diesem Artikel und die Schritte in [Kerberos SSO konfigurieren](service-gateway-sso-kerberos.md) aus.

## <a name="enable-sso-for-sap-hana"></a>Aktivieren von SSO für SAP HANA

Gehen Sie folgendermaßen vor, um SSO für SAP HANA zu aktivieren:

1. Vergewissern Sie sich, dass auf dem SAP HANA-Server die erforderliche Mindestversion ausgeführt wird (abhängig von der Plattformebene Ihres SAP HANA-Servers):
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. Installieren Sie auf dem Gatewaycomputer den aktuellen SAP HANA-ODBC-Treiber. Die Mindestversion ist die HANA-ODBC-Version 2.00.020.00 vom August 2017.

3. Stellen Sie sicher, dass der SAP HANA-Server für Kerberos-basiertes SSO konfiguriert wurde. Weitere Informationen zum Einrichten von SSO für SAP HANA mit Kerberos finden Sie im SAP HANA Security Guide im Thema [Single Sign-On Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Einmaliges Anmelden mit Kerberos). Sehen Sie sich außerdem die Links auf dieser Seite an – insbesondere den SAP-Hinweis 1837331 (HOWTO HANA DBSSO Kerberos/Active Directory).

Wir empfehlen außerdem, diese zusätzlichen Schritte durchzuführen, die eine geringfügige Verbesserung der Leistung bewirken können:

1. Suchen Sie im Gatewayinstallationsverzeichnis die folgende Konfigurationsdatei, und öffnen Sie sie: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Suchen Sie die `FullDomainResolutionEnabled`-Eigenschaft, und ändern Sie Ihren Wert in `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Jetzt können Sie [einen Power BI-Bericht ausführen](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum lokalen Datengateway und zu DirectQuery finden Sie in den folgenden Ressourcen:

* [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
