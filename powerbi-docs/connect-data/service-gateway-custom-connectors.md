---
title: Verwenden von benutzerdefinierten Datenconnectors mit dem lokalen Datengateway
description: Sie können benutzerdefinierte Datenconnectors mit dem lokalen Datengateway verwenden.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: bdf01eadc656467e50d17f04150c278da4603ef1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83299813"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Verwenden von benutzerdefinierten Datenconnectors mit dem lokalen Datengateway

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Mithilfe der Datenconnectors für Power BI können Sie eine Verbindung zu Daten einer App, eines Diensts oder einer Datenquelle herstellen und auf diese zugreifen. Sie können benutzerdefinierte Datenconnectors entwickeln und diese in Power BI Desktop verwenden.

Weitere Informationen zum Entwickeln benutzerdefinierter Datenconnectors für Power BI finden auf der GitHub-Seite zum [Datenconnector SDK](https://aka.ms/dataconnectors). Diese Seite enthält Informationen zu den ersten Schritten sowie Beispiele für Power BI und Power Query.

Wenn Sie Berichte in Power BI Desktop erstellen, die benutzerdefinierte Datenconnectors nutzen, können Sie das lokale Datengateway dazu verwenden, diese Berichte über den Power BI-Dienst zu aktualisieren.

## <a name="enable-and-use-this-capability"></a>Aktivieren und Verwenden dieser Funktion

Wenn Sie die Version vom Juli 2018 oder eine neuere Version des lokalen Datengateways installieren, wird Ihnen die Registerkarte **Connectors** in der App des lokalen Datengateways angezeigt. Wählen Sie im Feld **Benutzerdefinierte Datenconnectors aus folgendem Ordner laden** einen Ordner aus, auf den der Benutzer zugreifen kann, der den Gatewaydienst ausführt. Der Standardbenutzer ist *NT SERVICE\PBIEgwService*. Das Gateway lädt automatisch die Dateien des benutzerdefinierten Connectors, die sich in diesem Ordner befinden. Sie werden in der Datenconnectorliste angezeigt.

![Benutzerdefinierte Datenkonnektoren](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Wenn Sie das lokale Datengateway (persönlicher Modus) verwenden, können Sie an dieser Stelle Ihren Power BI-Bericht im Power BI-Dienst hochladen und das Gateway zum Aktualisieren verwenden.

Für das lokale Datengateway müssen Sie eine Datenquelle für Ihren benutzerdefinierten Connector erstellen. Auf der Seite „Gatewayeinstellungen“ im Power BI-Dienst sollte eine Option angezeigt werden, wenn Sie dem Gatewaycluster erlauben, benutzerdefinierte Connectors mit diesem Cluster zu verwenden. Vergewissern Sie sich, dass für alle Gateways im Cluster das Update vom Juli 2018 oder höher installiert ist, damit diese Option verfügbar ist. Wählen Sie diese Option aus, um das Verwenden von benutzerdefinierten Connectors mit diesem Cluster zu aktivieren.

![Seite „Gatewayclustereinstellungen“](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Wenn diese Option aktiviert ist, werden Ihre benutzerdefinierten Connectors als verfügbare Datenquellen angezeigt, die Sie in diesem Gatewaycluster erstellen können. Nach dem Erstellen einer Datenquelle mit Ihrem neuen benutzerdefinierten Connector können Sie die Power BI-Berichte aktualisieren, indem Sie diesen benutzerdefinierten Connector im Power BI-Dienst verwenden.

![Seite „Datenquelleneinstellungen“](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

* Stellen Sie sicher, dass der erstellte Ordner für den Gatewaydienst im Hintergrund zugänglich ist. In der Regel ist der Zugriff auf Ordner unter Windows-Ordnern oder Systemordnern Ihres Benutzers nicht möglich. Die App für das lokale Datengateway zeigt eine Nachricht an, wenn nicht auf den Ordner zugegriffen werden kann. Diese Anweisung gilt nicht für lokale Datengateways (persönlicher Modus).
* Damit benutzerdefinierte Connectors mit dem lokalen Datengateway verwendet werden können, muss in deren Code ein „TestConnection“-Abschnitt implementiert werden. Dieser Abschnitt ist nicht erforderlich, wenn Sie benutzerdefinierte Connectors mit Power BI Desktop verwenden. Daher können Sie einen benutzerdefinierten Connector nutzen, der zwar mit Power BI Desktop, aber nicht mit dem Gateway verwendet werden kann. Weitere Informationen zur Implementierung eines TestConnection-Abschnitts finden Sie in [dieser Dokumentation](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support).
* OAuth für benutzerdefinierte Connectors über Gateways wird derzeit nur für Gatewayadministratoren unterstützt, für andere Datenquellenbenutzer jedoch nicht.

## <a name="next-steps"></a>Weitere Schritte

* [Verwalten Ihrer Datenquelle – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Verwalten Ihrer Datenquelle –SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Verwalten Ihrer Datenquelle – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Verwalten der Datenquelle – Oracle](service-gateway-onprem-manage-oracle.md)  
* [Verwalten der Datenquelle: Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Konfigurieren von Proxyeinstellungen für das lokale Datengateway](/data-integration/gateway/service-gateway-proxy)
* [Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) von Power BI bei lokalen Datenquellen](service-gateway-sso-kerberos.md)  

Weitere Fragen? Stellen Sie Ihre Frage in der [Power BI-Community](https://community.powerbi.com/).
