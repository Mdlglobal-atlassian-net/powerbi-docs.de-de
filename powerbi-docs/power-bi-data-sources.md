---
title: Power BI-Datenquellen
description: In diesem Artikel werden die von Power BI unterstützten Datenquellen aufgeführt, einschließlich Informationen über DirectQuery und das lokale Datengateway.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: kfollis
ms.openlocfilehash: 1853e710958b5bed0dad011594d9e04ccc99842d
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79041675"
---
# <a name="power-bi-data-sources"></a>Power BI-Datenquellen

In der folgenden Tabelle werden die von Power BI für Datasets unterstützten Datenquellen aufgeführt, einschließlich Informationen zu DirectQuery und dem lokalen Datengateway. Informationen zu Dataflows finden Sie unter [Herstellen einer Verbindung mit Datenquellen über Power BI-Dataflows](service-dataflows-data-sources.md).

> [!NOTE]
> Es gibt zahlreiche Datenconnectors für Power BI Desktop, die für die Authentifizierung Internet Explorer 10 (oder höher) benötigen. 


| Datenquellen- | Verbindung vom Desktop aus | Verbindung und Aktualisierung vom Dienst aus | DirectQuery-/Liveverbindung | Gateway (unterstützt) | Gateway (erforderlich) |
|---|---|---|---|---|---|---|---|
| Access-Datenbank | Ja | Ja | Nein | Ja <sup>1</sup> | Ja |
| ActiveDirectory | Ja | Ja | Nein | Ja | Ja |
| Adobe Analytics | Ja | Ja | Nein | Nein | Nein |
| Amazon Redshift | Ja | Ja | Ja | Ja | Nein |
| appFigures | Ja | Ja | Nein | Nein | Nein |
| AtScale-Cubes | Ja | Ja | Ja | Ja | Nein |
| Azure Analysis Services | Ja | Ja | Ja | Ja <sup>2</sup> | Nein |
| Azure Blob Storage | Ja | Ja | Nein | Ja | Nein |
| Azure Cosmos DB | Ja | Ja | Nein | Nein | Nein |
| Azure Cost Management | Ja | Ja | Nein | Nein | Nein |
| Azure Data Explorer (Kusto) | Ja | Ja | Ja | Nein | Nein |
| Azure Data Lake Storage Gen1 | Ja | Ja | Nein | Nein | Nein |
| Azure Data Lake Storage Gen2 | Ja | Ja | Nein | Ja | Nein |
| Azure DevOps | Ja | Ja | Nein | Nein | Nein |
| Azure DevOps Server | Ja | Ja | Nein | Ja | Ja |
| Azure HDInsight (HDFS) | Ja | Ja | Nein | Nein | Nein |
| Azure HDInsight Spark | Ja | Ja | Ja | Nein | Nein |
| Azure SQL-Datenbank | Ja | Ja | Ja | Ja <sup>2</sup> | Nein |
| Azure SQL Data Warehouse | Ja | Ja | Ja | Ja <sup>2</sup> | Nein |
| Azure-Tabellenspeicher | Ja | Ja | Nein | Ja | Nein |
| BI-Connector | Ja | Ja | Ja | Ja | Ja |
| BI360 – Budgeting & Financial Reporting | Ja | Ja | Nein | Nein | Nein |
| Common Data Service | Ja | Ja | Nein | Nein | Nein |
| Data.World – Dataset abrufen | Ja | Ja | Nein | Nein | Nein |
| Denodo | Ja | Ja | Ja | Ja | Ja |
| Dremio | Ja | Ja | Ja | Ja | Ja |
| Dynamics 365 (online) | Ja | Ja | Nein | Nein | Nein |
| Dynamics 365 Business Central | Ja | Ja | Nein | Nein | Nein |
| Dynamics 365 Business Central (lokal) | Ja | Ja | Nein | Nein | Nein |
| Dynamics 365 Customer Insights | Ja | Ja | Nein | Nein | Nein |
| Dynamics NAV | Ja | Ja | Nein | Nein | Nein |
| Emigo Data Source | Ja | Ja | Nein | Nein | Nein |
| Entersoft Business Suite | Ja | Ja | Nein | Nein | Nein |
| Essbase | Ja | Ja | Ja | Ja | Ja |
| Exasol | Ja | Ja | Ja | Ja | Ja |
| Excel | Ja <sup>3</sup> | Ja <sup>3</sup> | Nein | Ja <sup>3</sup> | Nein <sup>4</sup> |
| Facebook | Ja | Ja | Nein | Nein | Nein |
| Datei | Ja | Ja | Nein | Ja | Ja |
| Ordner | Ja | Ja | Nein | Ja | Ja |
| GitHub | Ja | Ja | Nein | Nein | Nein |
| Google Analytics | Ja | Ja | Nein | Nein | Nein |
| Google BigQuery | Ja | Ja | Nein | Nein | Nein |
| Hadoop-Datei (HDFS) | Ja | Nein | Nein | Nein | Nein |
| HDInsight Interactive Query | Ja | Ja | Ja | Nein | Nein |
| IBM DB2 | Ja | Ja | Ja | Ja | Nein |
| IBM Informix-Datenbank | Ja | Ja | Nein | Ja | Nein |
| IBM Netezza | Ja | Ja | Ja | Ja | Ja |
| Impala | Ja | Ja | Ja | Ja | Ja |
| Indexima | Ja | Ja | Ja | Ja | Ja |
| Industrial App Store | Ja | Ja | Nein | Nein | Nein |
| Information Grid | Ja | Ja | Nein | Nein | Nein |
| Intersystems IRIS | Ja | Ja | Ja | Ja | Ja |
| Intune Data Warehouse | Ja | Ja | Nein | Nein | Nein |
| Jethro ODBC | Ja | Ja | Ja | Ja | Ja |
| JSON | Ja | Ja | Nein | Ja** | Nein <sup>4</sup> |
| Kyligence Enterprise | Ja | Ja | Ja | Ja | Ja |
| MailChimp | Ja | Ja | Nein | Nein | Nein |
| Marketo | Ja | Ja | Nein | Nein | Nein |
| MarkLogic ODBC | Ja | Ja | Ja | Ja | Ja |
| Microsoft Azure Consumption Insights | Ja | Ja | Nein | Nein | Nein |
| Microsoft Exchange | Ja | Ja | Nein | Ja | Nein |
| Microsoft Exchange Online | Ja | Ja | Nein | Nein | Nein |
| Microsoft Graph-Sicherheit | Ja | Ja | Nein | Ja | Nein |
| Mixpanel | Ja | Ja | Nein | Nein | Nein |
| MySQL | Ja | Ja | Nein | Ja | Ja |
| OData | Ja | Ja | Nein | Ja | Nein |
| ODBC | Ja | Ja | Nein | Ja | Ja |
| OLE DB | Ja | Ja | Nein | Ja | Ja |
| Oracle | Ja | Ja | Ja | Ja | Ja |
| Paxata | Ja | Ja | Nein | Ja | Nein |
| PDF | Ja | Ja | Nein | Ja | Nein <sup>4</sup> |
| Planview Enterprise One – CTM | Ja | Ja | Nein | Nein | Nein |
| Planview Enterprise One – PRM | Ja | Ja | Nein | Nein | Nein |
| Planview Projectplace | Ja | Ja | Nein | Nein | Nein |
| PostgreSQL | Ja | Ja | Ja | Ja | Nein |
| Power BI-Dataflows | Ja | Ja | Nein | Nein | Nein |
| Power BI-Datasets | Ja | Ja | Ja | Nein | Nein |
| Power Platform-Dataflows | Ja | Ja | Nein | Nein | Nein |
| Python-Skript | Ja | Ja <sup>5</sup> | Nein | Ja <sup>5</sup> | Ja |
| QubolePresto | Ja | Ja | Ja | Ja | Ja |
| Quick Base | Ja | Ja | Nein | Ja | Ja |
| QuickBooks Online | Ja | Ja | Nein | Nein | Nein |
| R-Skript | Ja | Ja <sup>5</sup> | Nein | Ja <sup>5</sup> | Nein |
| Roamler | Ja | Ja | Nein | Ja | Nein |
| Salesforce-Objekte | Ja | Ja | Nein | Nein | Nein |
| Salesforce-Berichte | Ja | Ja | Nein | Nein | Nein |
| SAP Business Warehouse-Nachrichtenserver | Ja | Ja | Ja | Ja | Ja |
| SAP Business Warehouse-Server | Ja | Ja | Ja | Ja | Ja |
| SAP HANA | Ja | Ja | Ja | Ja | Ja |
| SharePoint-Ordner | Ja | Ja | Nein | Ja | Nein <sup>4</sup> |
| SharePoint-Liste | Ja | Ja | Nein | Ja | Nein <sup>4</sup> |
| SharePoint-Online-Liste | Ja | Ja | Nein | Ja <sup>2</sup> | Nein |
| Smartsheet | Ja | Ja | Nein | Nein | Nein |
| Snowflake | Ja | Ja | Ja | Ja | Nein |
| Spark | Ja | Ja | Ja | Ja | Nein |
| SparkPost | Ja | Ja | Nein | Nein | Nein |
| SQL Server | Ja | Ja | Ja | Ja | Ja |
| SQL Server Analysis Services | Ja | Ja | Ja | Ja | Ja |
| Stripe | Ja | Ja | Nein | Nein | Nein |
| SurveyMonkey | Ja | Ja | Nein | Ja | Nein |
| SweetIQ | Ja | Ja | Nein | Nein | Nein |
| Sybase | Ja | Ja | Nein | Ja | Ja |
| TeamDesk | Ja | Ja | Nein | Ja | Nein |
| Tenforce | Ja | Ja | Nein | Nein | Nein |
| Teradata | Ja | Ja | Ja | Ja | Ja |
| Text/CSV | Ja | Ja | Nein | Ja | Nein <sup>4</sup> |
| Twilio | Ja | Ja | Nein | Nein | Nein |
| tyGraph | Ja | Ja | Nein | Nein | Nein |
| Vertica | Ja | Ja | Ja | Ja | Ja |
| Web | Ja | Ja | Nein | Ja | Ja <sup>6</sup> |
| Webtrends | Ja | Ja | Nein | Nein | Nein |
| Workforce Dimensions | Ja | Ja | Nein | Ja | Nein |
| XML | Ja | Ja | Nein | Ja | Nein <sup>4</sup> |
| Zendesk | Ja | Ja | Nein | Nein | Nein |
| | | | | | | | |

<sup>1</sup> Mit dem [ACE-OLEDB-Anbieter](https://www.microsoft.com/download/details.aspx?id=54920) unterstützt, der auf demselben Computer wie das Gateway installiert ist.

<sup>2</sup> Mit derselben M-Funktion wie die lokale Version unterstützt, was zu eingeschränkten Authentifizierungsoptionen führt (das Gateway unterstützt OAuth nicht).

<sup>3</sup> Für Dateien im Format Excel 1997–2003 (.xls) wird der [ACE OLEDB-Anbieter](https://www.microsoft.com/download/details.aspx?id=54920) benötigt.

<sup>4</sup> Für die lokale Version der Technologie erforderlich.

<sup>5</sup> Nur mit dem [persönlichen Gateway](service-gateway-personal-mode.md) unterstützt.

<sup>6</sup> Für HTML-, XLS- und Access-Datenbanken erforderlich

## <a name="single-sign-on-sso-for-directquery-sources"></a>Einmaliges Anmelden (SSO) für DirectQuery-Quellen

Wenn die Option „SSO“ aktiviert ist und Benutzer auf Berichte zugreifen, die auf der Datenquelle beruhen, werden deren authentifizierte Azure AD-Anmeldeinformationen von Power BI in den Abfragen an die zugrunde liegende Datenquelle gesendet. Dadurch wird sichergestellt, dass die auf Datenquellenebene konfigurierten Sicherheitseinstellungen in Power BI berücksichtigt werden.
Die SSO-Option gilt für alle Datasets, die diese Datenquelle verwenden. Sie hat keine Auswirkungen auf das Authentifizierungsverfahren, das bei Importszenarien verwendet wird. Die folgenden Datenquellen unterstützen SSO für Verbindungen mithilfe von DirectQuery:

- Azure SQL-Datenbank
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW-Nachrichtenserver
- Snowflake
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) wird nicht unterstützt. Benutzer, die SSO mit DirectQuery verwenden möchten, müssen von MFA ausgenommen werden.

## <a name="next-steps"></a>Nächste Schritte

[Verbinden mit Daten in Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Verwendung von DirectQuery in Power BI](desktop-directquery-about.md)  
[SQL Server Analysis Services-Livedaten in Power BI](sql-server-analysis-services-tabular-data.md)  
[What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](service-gateway-onprem.md)  
