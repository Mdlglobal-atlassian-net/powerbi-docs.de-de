---
title: Datenquellen für Power BI-Berichte in Power BI-Berichtsserver
description: Power BI-Berichte können Verbindungen mit einer Reihe von Datenquellen herstellen. Je nach Verwendung der Daten sind verschiedene Datenquellen verfügbar.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: maggies
ms.openlocfilehash: 166f72a717c99457e1d6b8e9a1f30535a9b4686f
ms.sourcegitcommit: e7fda395b47e404c61e961a60816b7a1b0182759
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80979843"
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Datenquellen für Power BI-Berichte in Power BI-Berichtsserver
Power BI-Berichte können Verbindungen mit einer Reihe von Datenquellen herstellen. Je nach Verwendung der Daten sind verschiedene Datenquellen verfügbar. Daten können importiert werden, oder Daten können direkt mit DirectQuery oder über eine Liveverbindung mit SQL Server Analysis Services abgefragt werden.

Diese Datenquellen sind spezifisch für Power BI-Berichte, die in Power BI-Berichtsserver verwendet werden. Weitere Informationen zu Datenquellen, die für paginierte Berichte (RDL) unterstützt werden, finden Sie unter [Von Reporting Services unterstützte Datenquellen](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Alle Datenquellen in einem Power BI Desktop-Bericht müssen das Konfigurieren geplanter Aktualisierungen unterstützen.
>  

## <a name="list-of-supported-data-sources"></a>Liste der unterstützten Datenquellen

Andere Datenquellen können funktionieren, selbst wenn sie nicht in der Liste der unterstützten Datenquellen aufgeführt werden.

| **Datenquelle** | **Zwischengespeicherte Daten** | **Geplante Aktualisierung** | **Live/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server-Datenbank |Ja |Ja |Ja |
| SQL Server Analysis Services |Ja |Ja |Ja |
| Azure SQL-Datenbank |Ja |Ja |Ja |
| Azure SQL Data Warehouse |Ja |Ja |Ja |
| Excel |Ja |Ja |Nein |
| Access-Datenbank |Ja |Ja |Nein |
| Active Directory |Ja |Ja |Nein |
| Amazon Redshift |Ja |Nein |Nein |
| Azure Blob Storage |Ja |Ja |Nein |
| Azure Data Lake Store |Ja |Nein |Nein |
| Azure HDInsight (HDFS) |Ja |Nein |Nein |
| Azure HDInsight (Spark) |Ja |Nein |Nein |
| Azure-Tabellenspeicher |Ja |Ja |Nein |
| Dynamics 365 (online) |Ja |Nein |Nein |
| Facebook |Ja |Nein |Nein |
| Ordner |Ja |Ja |Nein |
| Google Analytics |Ja |Nein |Nein |
| Hadoop-Datei (HDFS) |Ja |Nein |Nein |
| IBM DB2-Datenbank |Ja |Ja |Nein |
| Impala |Ja |Nein |Nein |
| JSON |Ja |Ja |Nein |
| Microsoft Exchange |Ja |Nein |Nein |
| Microsoft Exchange Online |Ja |Nein |Nein |
| MySQL-Datenbank |Ja |Ja |Nein |
| OData-Feed |Ja |Ja |Nein |
| ODBC |Ja |Ja |Nein |
| OLE DB |Ja |Ja |Nein |
| Oracle-Datenbank |Ja |Ja |Ja |
| PostgreSQL-Datenbank |Ja |Ja |Nein |
| Power BI-Dienst |Nein |Nein |Nein |
| R-Skript |Ja |Nein |Nein |
| Salesforce-Objekte |Ja |Nein |Nein |
| Salesforce-Berichte |Ja |Nein |Nein |
| SAP Business Warehouse-Server |Ja |Ja |Ja |
| SAP HANA-Datenbank |Ja |Ja |Ja |
| SharePoint-Ordner (lokal) |Ja |Ja |Nein |
| SharePoint-Liste (lokal) |Ja |Ja |Nein |
| SharePoint-Online-Liste |Ja |Nein |Nein |
| Snowflake |Ja |Nein |Nein |
| Sybase-Datenbank |Ja |Ja |Nein |
| Teradata |Ja |Ja |Ja |
| Text/CSV |Ja |Ja |Nein |
| Web |Ja |Ja |Nein |
| XML |Ja |Ja |Nein |
| appFigures (Beta) |Ja |Nein |Nein |
| Azure Analysis Services-Datenbank |Ja |Nein |Ja |
| Azure Cosmos DB (Beta) |Ja |Nein |Nein |
| Azure HDInsight Spark (Beta) |Ja |Nein |Nein |
| Common Data Service (Beta) |Ja |Nein |Nein |
| comScore Digital Analytix (Beta) |Ja |Nein |Nein |
| Dynamics 365 for Customer Insights (Beta) |Ja |Nein |Nein |
| Dynamics 365 for Financials (Beta) |Ja |Nein |Nein |
| GitHub (Beta) |Ja |Nein |Nein |
| BigQuery von Google (Beta) |Ja |Nein |Nein |
| IBM Informix-Datenbank (Beta) |Ja |Nein |Nein |
| IBM Netezza (Beta) |Ja |Nein |Nein |
| Kusto (Beta) |Ja |Nein |Nein |
| MailChimp (Beta) |Ja |Nein |Nein |
| Microsoft Azure Consumption Insights (Beta) |Ja |Nein |Nein |
| Mixpanel (Beta) |Ja |Nein |Nein |
| Planview Enterprise (Beta) |Ja |Nein |Nein |
| Projectplace (Beta) |Ja |Nein |Nein |
| QuickBooks Online (Beta) |Ja |Nein |Nein |
| Smartsheet |Ja |Nein |Nein |
| Spark (Beta) |Ja |Nein |Nein |
| SparkPost (Beta) |Ja |Nein |Nein |
| SQL Sentry (Beta) |Ja |Nein |Nein |
| Stripe (Beta) |Ja |Nein |Nein |
| SweetIQ (Beta) |Ja |Nein |Nein |
| Troux (Beta) |Ja |Nein |Nein |
| Twilio (Beta) |Ja |Nein |Nein |
| tyGraph (Beta) |Ja |Nein |Nein |
| Vertica (Beta) |Ja |Nein |Nein |
| Visual Studio Team Services (Beta) |Ja |Nein |Nein |
| Webtrends (Beta) |Ja |Nein |Nein |
| Zendesk (Beta) |Ja |Nein |Nein |

> [!IMPORTANT]
> Die in der Datenquelle konfigurierte Sicherheit auf Zeilenebene sollte für bestimmte DirectQuery-Verbindungen (SQL Server, Azure SQL-Datenbank, Oracle und Teradata) und Liveverbindungen funktionieren, vorausgesetzt, Kerberos ist in der Umgebung ordnungsgemäß konfiguriert.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Liste der unterstützten Authentifizierungsmethoden für die Aktualisierung des Modells

Microsoft Power BI-Berichtsserver unterstützt keine auf OAuth basierende Authentifizierung für die Aktualisierung des Modells. Einige Datenquellen wie Excel oder Access-Datenbanken nutzen bei der Verbindungserstellung zu Daten einen Zwischenschritt wie eine Datei oder das Web.

| **Datenquelle** | **Anonyme Authentifizierung** | **Schlüsselauthentifizierung** | **Benutzername und Kennwort** | **Windows-Authentifizierung** |
| --- | --- | --- | --- | --- |
| SQL Server-Datenbank |Nein |Nein |Ja |Ja |
| SQL Server Analysis Services |Nein |Nein |Ja |Ja |
| Web |Ja |Nein |Ja |Ja |
| Azure SQL-Datenbank |Nein |Nein |Ja |Nein |
| Azure SQL Data Warehouse |Nein |Nein |Ja |Nein |
| Active Directory |Nein |Nein |Ja |Ja |
| Amazon Redshift |Nein |Nein |Nein |Nein |
| Azure Blob Storage |Ja |Ja |Nein |Nein |
| Azure Data Lake Store |Nein |Nein |Nein |Nein |
| Azure HDInsight (HDFS) |Nein |Nein |Nein |Nein |
| Azure HDInsight (Spark) |Nein |Nein |Nein |Nein |
| Azure-Tabellenspeicher |Nein |Ja |Nein |Nein |
| Dynamics 365 (online) |Nein |Nein |Nein |Nein |
| Facebook |Nein |Nein |Nein |Nein |
| Ordner |Nein |Nein |Nein |Ja |
| Google Analytics |Nein |Nein |Nein |Nein |
| Hadoop-Datei (HDFS) |Nein |Nein |Nein |Nein |
| IBM DB2-Datenbank |Nein |Nein |Ja |Ja |
| Impala |Nein |Nein |Nein |Nein |
| Microsoft Exchange |Nein |Nein |Nein |Nein |
| Microsoft Exchange Online |Nein |Nein |Nein |Nein |
| MySQL-Datenbank |Nein |Nein |Ja |Ja |
| OData-Feed |Ja |Ja |Ja |Ja |
| ODBC |Ja |Nein |Ja |Ja |
| OLE DB |Ja |Nein |Ja |Ja |
| Oracle-Datenbank |Nein |Nein |Ja |Ja |
| PostgreSQL-Datenbank |Nein |Nein |Ja |Nein |
| Power BI-Dienst |Nein |Nein |Nein |Nein |
| R-Skript |Nein |Nein |Nein |Nein |
| Salesforce-Objekte |Nein |Nein |Nein |Nein |
| Salesforce-Berichte |Nein |Nein |Nein |Nein |
| SAP Business Warehouse-Server |Nein |Nein |Ja |Nein |
| SAP HANA-Datenbank |Nein |Nein |Ja |Ja |
| SharePoint-Ordner (lokal) |Ja |Nein |Nein |Ja |
| SharePoint-Liste (lokal) |Ja |Nein |Nein |Ja |
| SharePoint-Online-Liste |Nein |Nein |Nein |Nein |
| Snowflake |Nein |Nein |Nein |Nein |
| Sybase-Datenbank |Nein |Nein |Ja |Ja |
| Teradata |Nein |Nein |Ja |Ja** |
| appFigures (Beta) |Nein |Nein |Nein |Nein |
| Azure Analysis Services-Datenbank (Beta) |Nein |Nein |Nein |Nein |
| Azure Cosmos DB (Beta) |Nein |Nein |Nein |Nein |
| Azure HDInsight Spark (Beta) |Nein |Nein |Nein |Nein |
| Common Data Service (Beta) |Nein |Nein |Nein |Nein |
| comScore Digital Analytix (Beta) |Nein |Nein |Nein |Nein |
| Dynamics 365 for Customer Insights (Beta) |Nein |Nein |Nein |Nein |
| Dynamics 365 for Financials (Beta) |Nein |Nein |Nein |Nein |
| GitHub (Beta) |Nein |Nein |Nein |Nein |
| BigQuery von Google (Beta) |Nein |Nein |Nein |Nein |
| IBM Informix-Datenbank (Beta) |Nein |Nein |Nein |Nein |
| IBM Netezza (Beta) |Nein |Nein |Nein |Nein |
| Kusto (Beta) |Nein |Nein |Nein |Nein |
| MailChimp (Beta) |Nein |Nein |Nein |Nein |
| Microsoft Azure Consumption Insights (Beta) |Nein |Nein |Nein |Nein |
| Mixpanel (Beta) |Nein |Nein |Nein |Nein |
| Planview Enterprise (Beta) |Nein |Nein |Nein |Nein |
| Projectplace (Beta) |Nein |Nein |Nein |Nein |
| QuickBooks Online (Beta) |Nein |Nein |Nein |Nein |
| Smartsheet |Nein |Nein |Nein |Nein |
| Spark (Beta) |Nein |Nein |Nein |Nein |
| SparkPost (Beta) |Nein |Nein |Nein |Nein |
| SQL Sentry (Beta) |Nein |Nein |Nein |Nein |
| Stripe (Beta) |Nein |Nein |Nein |Nein |
| SweetIQ (Beta) |Nein |Nein |Nein |Nein |
| Troux (Beta) |Nein |Nein |Nein |Nein |
| Twilio (Beta) |Nein |Nein |Nein |Nein |
| tyGraph (Beta) |Nein |Nein |Nein |Nein |
| Vertica (Beta) |Nein |Nein |Nein |Nein |
| Visual Studio Team Services (Beta) |Nein |Nein |Nein |Nein |
| Webtrends (Beta) |Nein |Nein |Nein |Nein |
| Zendesk (Beta) |Nein |Nein |Nein |Nein |

** Die Verwendung der LDAP-Authentifizierung mit Teradata (in Power BI Desktop über den Eingabeaufforderungsbefehl „setx PBI_EnableTeradataLdap true“ aktiviert) wird für die Modellaktualisierung nicht unterstützt.

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Liste der unterstützten Authentifizierungsmethoden für DirectQuery

Microsoft Power BI-Berichtsserver unterstützt keine auf OAuth basierende Authentifizierung für DirectQuery.

| **Datenquelle** | **Anonyme Authentifizierung** | **Schlüsselauthentifizierung** | **Benutzername und Kennwort** | **Windows-Authentifizierung** | **Integrierte Windows-Authentifizierung** |
| --- | --- | --- | --- | --- | --- |
| SQL Server-Datenbank |Nein |Nein |Ja |Ja |Ja |
| SQL Server Analysis Services |Nein |Nein |Ja |Ja |Ja |
| Azure SQL-Datenbank |Nein |Nein |Ja |Nein |Nein |
| Azure SQL Data Warehouse |Nein |Nein |Ja |Nein |Nein |
| Oracle-Datenbank |Nein |Nein |Ja |Ja |Ja |
| SAP Business Warehouse-Server |Nein |Nein |Ja |Nein |Nein |
| SAP HANA-Datenbank |Nein |Nein |Ja |Ja |Ja** |
| Teradata |Nein |Nein |Ja |Ja |Ja |

** SAP HANA unterstützt DirectQuery mit integrierter Windows-Authentifizierung nur bei Verwendung als relationale Datenbank in der veröffentlichten Power BI Desktop-Datei (.pbix).

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Verbindung mit Ihrer Datenquelle hergestellt haben, [erstellen Sie einen Power BI-Bericht](quickstart-create-powerbi-report.md) anhand der Daten aus der betreffenden Datenquelle.

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
