---
title: Datenquellen in Power BI Desktop
description: Datenquellen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/16/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5247b2c990c8c0cfd29da0e8a30cdc8691000106
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866815"
---
# <a name="data-sources-in-power-bi-desktop"></a>Datenquellen in Power BI Desktop

Mit Power BI Desktop können Sie Verbindungen mit Daten aus vielen verschiedenen Quellen herstellen. Eine vollständige Liste der verfügbaren Datenquellen finden Sie unter [Power BI-Datenquellen](power-bi-data-sources.md).

Sie können mithilfe des Menübands **Start** eine Datenverbindung herstellen. Um die Datentypen **Am häufigsten verwendet** anzuzeigen, wählen Sie die Schaltfläche **Daten abrufen** oder den nach unten weisenden Pfeil aus.

![Menü mit den am häufigsten verwendeten Datentypen, „Daten abrufen“ in Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Um zum Dialogfeld **Daten abrufen** zu wechseln, zeigen Sie das Menü **Am häufigsten verwendet** an und klicken auf **Mehr**. Sie können das Dialogfeld **Daten abrufen** auch durch direktes Auswählen des Symbols **Daten abrufen** öffnen (und das Menü **Am häufigsten verwendet** umgehen).

![Schaltfläche „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> Das Power BI-Team erweitert laufend die Datenquellen, die für Power BI Desktop und den Power BI-Dienst verfügbar sind. Daher finden Sie häufig Vorabversionen von noch nicht in der Endversion vorliegenden Datenquellen, die als **Beta** oder **Vorschau** gekennzeichnet sind. Für alle als **Beta** oder **Vorschau** markierten Datenquellen werden nur eingeschränkter Support und weniger Funktionen bereitgestellt, deshalb sollten sie nicht in Produktionsumgebungen verwendet werden. Zudem sind alle Datenquellen, die als **Beta** oder **Vorschau** für Power BI Desktop gekennzeichnet sind, möglicherweise nicht für die Verwendung im Power BI-Dienst oder in anderen Microsoft-Diensten verfügbar, bis die Datenquelle allgemein verfügbar wird (GA).

> [!NOTE]
> Es gibt zahlreiche Datenconnectors für Power BI Desktop, die für die Authentifizierung Internet Explorer 10 (oder höher) benötigen. 


## <a name="data-sources"></a>Datenquellen

Im Dialogfeld **Daten abrufen** werden Datentypen in die folgenden Kategorien unterteilt:

* Alles
* Datei
* Datenbank
* Power Platform
* Azure
* Onlinedienste
* Sonstige

Die Kategorie **Alles** umfasst alle Datenverbindungstypen aus allen Kategorien.

### <a name="file-data-sources"></a>Datenquellen vom Typ „Datei“

Die Kategorie **Datei** bietet die folgenden Datenverbindungen:

* Excel
* Text/CSV
* XML
* JSON
* Ordner
* PDF
* SharePoint-Ordner

Die folgende Abbildung zeigt das Fenster **Daten abrufen** für **Datei**.

![Datenquelle „Datei“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Datenquellen vom Typ „Datenbank“

Die Kategorie **Datenbank** bietet die folgenden Datenverbindungen:

* SQL Server-Datenbank
* Access-Datenbank
* SQL Server Analysis Services-Datenbank
* Oracle-Datenbank
* IBM DB2-Datenbank
* IBM Informix-Datenbank (Beta)
* IBM Netezza
* MySQL-Datenbank
* PostgreSQL-Datenbank
* Sybase-Datenbank
* Teradata-Datenbank
* SAP HANA-Datenbank
* SAP Business Warehouse-Anwendungsserver
* SAP Business Warehouse-Nachrichtenserver
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* AtScale-Cubes
* BI-Connector 
* Data Virtuality LDW (Beta)
* Denodo
* Dremio
* Exasol
* Indexima (Beta)
* InterSystems IRIS (Beta)
* Jethro (Beta)
* Kyligence
* MarkLogic

> [!NOTE]
> Sie müssen einige Datenbankconnectors aktivieren, indem Sie **Datei > Optionen und Einstellungen > Optionen** und dann **Vorschaufeatures** auswählen und den Connector aktivieren. Wenn einige der oben genannten Connectors nicht angezeigt werden und Sie diese verwenden möchten, überprüfen Sie die Einstellungen von **Vorschaufeatures**. Außerdem stehen für alle als *Beta* oder *Vorschau* markierten Datenquellen nur eingeschränkter Support und weniger Funktionen zur Verfügung, und sie sollten nicht in Produktionsumgebungen verwendet werden.

Die folgende Abbildung zeigt das Fenster **Daten abrufen** für **Datenbank**.

![Datenquelle „Datenbank“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Datenquellen vom Typ „Power Platform“

Die Kategorie **Power Platform** bietet die folgenden Datenverbindungen:

* Power BI-Datasets
* Power BI-Dataflows
* Common Data Service
* Power Platform-Dataflows

Die folgende Abbildung zeigt das Fenster **Daten abrufen** für **Power Platform**.

![Datenquelle „Power Platform“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Azure-Datenquellen

Die Kategorie **Azure** bietet die folgenden Datenverbindungen:

* Azure SQL-Datenbank
* Azure SQL Data Warehouse
* Azure Analysis Services-Datenbank
* Azure Database for PostgreSQL
* Azure Blob Storage
* Azure-Tabellenspeicher
* Azure Cosmos DB
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Data Explorer (Kusto)
* Azure Cost Management


Die folgende Abbildung zeigt das Fenster **Daten abrufen** für **Azure**.

![Datenquelle „Azure“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Datenquellen vom Typ „Onlinedienste“

Die Kategorie **Online Services** bietet die folgenden Datenverbindungen:

* SharePoint-Online-Liste
* Microsoft Exchange Online
* Dynamics 365 (online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (lokal)
* Microsoft Azure Consumption Insights (Beta)
* Azure DevOps (nur für Boards)
* Azure DevOps Server (nur für Boards)
* Salesforce-Objekte
* Salesforce-Berichte
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* Data.World – Dataset abrufen (Beta)
* GitHub (Beta)
* LinkedIn Sales Navigator (Beta)
* Merketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One – PRM (Beta)
* Planview Projectplace (Beta)
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* SweetIQ (Beta)
* Planview Enterprise One – CTM (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)
* Asana (Beta)
* Dynamics 365 Customer Insights (Beta)
* Emigo Data Source
* Entersoft Business Suite (Beta)
* FactSet Analytics (Beta)
* Industrial App Store
* Intune Data Warehouse (Beta)
* Microsoft Graph-Sicherheit (Beta)
* Product Insights (Beta)
* Quick Base
* TeamDesk (Beta)
* Workplace Analytics (Beta)
* Projectplace für Power BI (Beta)
* Webtrends Analytics (Beta)
* Zoho Creator (Beta)

Die folgende Abbildung zeigt das Fenster **Daten abrufen** für **Onlinedienste** an.

![Datenquelle „Onlinedienste“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Andere Datenquellen

Die Kategorie **Sonstige** bietet die folgenden Datenverbindungen:

* Web
* SharePoint-Liste
* OData-Feed
* Active Directory
* Microsoft Exchange
* Hadoop-Datei (HDFS)
* Spark
* Hive LLAP (Beta)
* R-Skript
* Python-Skript
* ODBC
* OLE DB
* BI360 – Budgeting & Financial Reporting (Beta)
* Cognite Data Fusion (Beta)
* FHIR
* Information Grid (Beta)
* Jamf Pro (Beta)
* MicroStrategy für Power BI
* Paxata
* QubolePresto (Beta)
* Roamler (Beta)
* Siteimprove
* SurveyMonkey (Beta)
* TIBCO(R) Data Virtualization (Beta)
* Vena (Beta)
* Workforce Dimensions (Beta)
* Zucchetti HR Infinity (Beta)
* Tenforce (Smart)List
* Shortcuts Business Insights (Beta)
* Vessel Insight (Beta)
* Leere Abfrage

Die folgende Abbildung zeigt das Fenster **Daten abrufen** für **Sonstige**.

![Datenquelle „Sonstige“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> Zurzeit ist es nicht möglich, eine Verbindung mit benutzerdefinierten Datenquellen herzustellen, die mit Azure Active Directory gesichert wurden.

## <a name="connecting-to-a-data-source"></a>Herstellen einer Verbindung mit einer Datenquelle

Wenn Sie die Verbindung mit einer Datenquelle herstellen möchten, wählen Sie die Datenquelle im Fenster **Daten abrufen** und dann **Verbinden**aus. In der folgenden Abbildung ist **Web** aus der Datenverbindungskategorie **Sonstige** ausgewählt.

![Verbindung mit „Web“, Dialogfeld „Daten abrufen“, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

Es wird ein für den Typ der Datenverbindung spezifisches Verbindungsfenster angezeigt. Wenn Anmeldeinformationen erforderlich sind, werden Sie aufgefordert, diese bereitzustellen. Die folgende Abbildung zeigt eine URL, die eingegeben wird, um die Verbindung mit einer Webdatenquelle herzustellen.

![Eingabe-URL, Dialogfeld „Aus dem Web“, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Geben Sie die URL oder Ressourcenverbindungsinformationen ein, und klicken Sie auf **OK**. Power BI Desktop stellt die Verbindung mit der Datenquelle her und zeigt die verfügbaren Datenquellen im **Navigator** an.

![Dialogfeld „Navigator“, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Klicken Sie zum Laden der Daten unten im Bereich des **Navigators** auf die Schaltfläche **Laden**. Klicken Sie auf die Schaltfläche **Daten transformieren**, um die Abfrage vor dem Laden der Daten im Power Query-Editor zu transformieren oder zu bearbeiten.

Das ist alles, was zum Herstellen der Verbindung mit Datenquellen im Power BI-Designer erforderlich ist. Sie können eine Verbindung mit Daten aus der wachsenden Liste von Datenquellen herstellen, die wir kontinuierlich erweitern.

## <a name="using-pbids-files-to-get-data"></a>Verwenden von PBIDS-Dateien zum Abrufen von Daten

PBIDS-Dateien sind Power BI Desktop-Dateien, die eine bestimmte Struktur und die Erweiterung „.PBIDS“ aufweisen, um anzugeben, dass es sich um eine Power BI-Datenquellendatei handelt.

Sie können eine PBIDS-Datei erstellen, um die Funktion **Daten abrufen** für Berichtersteller in Ihrer Organisation zu optimieren. Um einem neuen Berichtsautor die Verwendung von PBIDS-Dateien zu erleichtern, empfehlen wir, dass ein Administrator diese Dateien für häufig verwendete Verbindungen erstellt.

Wenn ein Autor eine PBIDS-Datei öffnet, wird Power BI Desktop geöffnet und fordert den Benutzer zur Eingabe von Anmeldeinformationen auf, um sich zu authentifizieren und eine Verbindung mit der in der Datei angegebenen Datenquelle herzustellen. Das Dialogfeld **Navigation** wird angezeigt, und der Benutzer muss die Tabellen aus dieser Datenquelle auswählen, die in das Modell geladen werden sollen. Benutzer müssen möglicherweise auch die Datenbanken auswählen, falls diese nicht in der PBIDS-Datei angegeben werden.

Von diesem Zeitpunkt an kann der Benutzer mit dem Erstellen von Visualisierungen beginnen oder **Zuletzt verwendete Quellen** auswählen, um einen neuen Tabellensatz in das Modell zu laden.

Aktuell unterstützen PBIDS-Dateien nur eine einzelne Datenquelle in einer Datei. Wenn Sie mehr als eine Datenquelle angeben, tritt ein Fehler auf.

Um eine PBIDS-Datei zu erstellen, muss ein Administrator die erforderlichen Eingaben für eine einzelne Verbindung angeben. Der Administrator kann außerdem als Verbindungsmodus entweder „DirectQuery“ oder „Import“ festlegen. Wenn die Angabe zum **Modus** in der Datei fehlt/NULL ist, wird der Benutzer, der die Datei in Power BI Desktop öffnet, aufgefordert, **DirectQuery** oder **Import** auszuwählen.

### <a name="pbids-file-examples"></a>Beispiele für PBIDS-Dateien

Dieser Abschnitt enthält einige Beispiele aus häufig verwendeten Datenquellen. Der PBIDS-Dateityp unterstützt bis auf zwei Ausnahmen nur Datenverbindungen, die auch in Power BI Desktop unterstützt werden: Live Connect und leere Abfrage

Die PBIDS-Datei enthält *keine* Authentifizierungsinformationen und keine Tabellen- und Schemainformationen.  

Die folgenden Codeausschnitten zeigen einige gängige Beispiele für PBIDS-Dateien, die aber nicht vollständig oder umfassend sind. Für andere Datenquellen finden Sie weitere Informationen im Thema [DSR-Format (Data Source Reference ) für Protokoll- und Adressinformationen](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification).

Diese Beispiele dienen nur als Übersicht, sie sind nicht umfassend und enthalten nicht alle unterstützten Connectors im DSR-Format. Administratoren oder Organisationen können eigene Datenquellen anhand dieser Beispiele als Orientierungshilfe erstellen, aus denen sie ihre eigenen Datenquelldateien erstellen und unterstützen können.

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>Ordner

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>SharePoint-Liste

Die URL muss auf die SharePoint-Website selbst, nicht auf eine Liste innerhalb der Website verweisen. Benutzer erhalten einen Navigator, mit dem Sie mindestens eine Liste von dieser Website auswählen können, die jeweils zu einer Tabelle im Modell wird.

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>Textdatei

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>Dataflow

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Nächste Schritte

Mit Power BI Desktop können Sie vielfältige Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in den folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datentypen in Power BI Desktop](desktop-data-types.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Allgemeine Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)
