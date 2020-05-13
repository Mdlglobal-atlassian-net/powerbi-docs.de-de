---
title: Herstellen einer Verbindung mit Daten mithilfe generischer Schnittstellen in Power BI Desktop
description: Erfahren Sie, wie Sie mithilfe generischer Schnittstellen in Power BI Desktop eine Verbindung mit unterschiedlichen Datenquellen herstellen.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c5e1c290df42af24db3edbc2534270bfd165a0b0
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347583"
---
# <a name="connect-to-data-by-using-power-bi-desktop-generic-interfaces"></a>Herstellen einer Verbindung mit Daten mithilfe der generischen Power BI Desktop-Schnittstellen 

Sie können mithilfe integrierter Datenconnectors, die von **Access-Datenbanken** bis zu **Zendesk**-Ressourcen reichen und im Fenster **Daten abrufen** aufgeführt sind, eine Verbindung mit zahlreichen unterschiedlichen Datenquellen in **Power BI Desktop** herstellen. Sie können auch eine Verbindung mit verschiedenen *anderen* Datenquellen herstellen. So verfügen Sie noch über weitaus mehr Verbindungsoptionen, indem Sie generische Schnittstellen (z.B. **ODBC** oder **REST-APIs**) verwenden, die in **Power BI Desktop** integriert sind.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_1.png)

## <a name="power-bi-desktop-data-interfaces"></a>Power BI Desktop-Datenschnittstellen
**Power BI Desktop** enthält eine ständig wachsende Sammlung von Datenconnectors, die dem Herstellen der Verbindung mit einer bestimmten Datenquelle dienen. Beispielsweise stellt der Datenconnector **SharePoint-Liste** während der Verbindungssequenz bestimmte Felder und unterstützende Informationen bereit, die für **SharePoint-Listen** vorgesehen sind. Dies ist der Fall, wenn Sie **Daten abrufen > Sonstige** auswählen, um sonstige Datenquellen im Fenster anzuzeigen (siehe Abbildung oben).

Zudem können Sie in **Power BI Desktop** eine Verbindung mit Datenquellen herstellen, die nicht in den Listen in **Daten abrufen** aufgeführt sind, indem Sie eine der folgenden generischen Datenschnittstellen verwenden:

* **ODBC**
* **OLE DB**
* **OData**
* **REST-APIs**
* **R-Skript**

Durch die Bereitstellung der entsprechenden Parameter in den Verbindungsfenstern, die durch diese generischen Schnittstellen angezeigt werden, wird die Auswahl der Datenquellen, die Sie in **Power BI Desktop** aufrufen und verwenden können, wesentlich erweitert.

In den folgenden Abschnitten finden Sie Listen der Datenquellen, auf die über diese generischen Schnittstellen zugegriffen werden kann.

Finden Sie eine Datenquelle nicht, die Sie in **Power BI Desktop** verwenden möchten? Senden Sie Ihre Vorschläge an die [Liste der Vorschläge und Anforderungen](https://ideas.powerbi.com/) des Power BI-Teams.

## <a name="data-sources-accessible-through-odbc"></a>Datenquellen mit Zugriff über ODBC
Mit dem **ODBC**-Connector in **Power BI Desktop** können Sie Daten über den ODBC-Treiber von Drittanbietern importieren, indem Sie einfach einen **Datenquellennamen (DSN)** oder eine *Verbindungszeichenfolge* angeben. Optional können Sie auch eine SQL-Anweisung angeben, die für den ODBC-Treiber ausgeführt werden soll.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_2.png)

In der folgenden Liste sind einige Beispiele für Datenquellen aufgeführt, mit denen **Power BI Desktop** eine Verbindung über die generische **ODBC**-Schnittstelle herstellen kann.

| Generischer Power BI Desktop-Connector | Externe Datenquelle | Link für weitere Informationen |
| --- | --- | --- |
| ODBC |Cassandra |[Cassandra-ODBC-Treiber](https://www.simba.com/drivers/cassandra-odbc-jdbc/) |
| ODBC |Couchbase DB |[Couchbase und Power BI](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |
| ODBC |DynamoDB |[DynamoDB-ODBC-Treiber](https://www.simba.com/drivers/dynamodb-odbc-jdbc/) |
| ODBC |BigQuery von Google |[BigQuery-ODBC-Treiber](https://www.simba.com/drivers/bigquery-odbc-jdbc/) |
| ODBC |HBase |[HBase-ODBC-Treiber](https://www.simba.com/drivers/hbase-odbc-jdbc/) |
| ODBC |Hive |[Hive-ODBC-Treiber](https://www.simba.com/drivers/hive-odbc-jdbc/) |
| ODBC |IBM Netezza |[Informationen zu IBM Netezza](https://www.ibm.com/support/knowledgecenter/SSULQD_7.2.1/com.ibm.nz.datacon.doc/c_datacon_plg_overview.html) |
| ODBC |Presto |[Presto-ODBC-Treiber](https://www.simba.com/drivers/presto-odbc-jdbc/) |
| ODBC |Project Online |[Project Online-Artikel](desktop-project-online-connect-to-data.md) |
| ODBC |Progress OpenEdge |[Blogeintrag zum Progress OpenEdge-ODBC-Treiber](https://www.progress.com/blogs/connect-microsoft-power-bi-to-openedge-via-odbc-driver) |

## <a name="data-sources-accessible-through-ole-db"></a>Datenquellen mit Zugriff über OLE DB
Mit dem **OLE DB**-Connector in **Power BI Desktop** können Sie Daten über den OLE DB-Treiber von Drittanbietern importieren, indem Sie einfach eine *Verbindungszeichenfolge* angeben. Optional können Sie auch eine SQL-Anweisung angeben, die für den OLE DB-Treiber ausgeführt werden soll.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_3.png)

In der folgenden Liste sind einige Beispiele für Datenquellen aufgeführt, mit denen **Power BI Desktop** eine Verbindung über die generische **OLE DB**-Schnittstelle herstellen kann.

| Generischer Power BI Desktop-Connector | Externe Datenquelle | Link für weitere Informationen |
| --- | --- | --- |
| OLE DB |SAS OLE DB |[SAS-Anbieter für OLE DB](https://support.sas.com/downloads/package.htm?pid=648) |
| OLE DB |Sybase OLE DB |[Sybase-Anbieter für OLE DB](http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.infocenter.dc35888.1550/doc/html/jon1256941734395.html) |

## <a name="data-sources-accessible-through-odata"></a>Datenquellen mit Zugriff über OData
Mit dem **OData**-Connector in **Power BI Desktop** können Sie Daten über eine beliebige**OData**-URL importieren, indem Sie einfach die **OData**-URL eingeben oder einfügen. Sie können mehrere URL-Teile hinzufügen, indem Sie diese Links in die Textfelder im Fenster **OData-Feed** eingeben oder einfügen.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_4.png)

In der folgenden Liste sind einige Beispiele für Datenquellen aufgeführt, mit denen **Power BI Desktop** eine Verbindung über die generische **OData**-Schnittstelle herstellen kann.

| Generischer Power BI Desktop-Connector | Externe Datenquelle | Link für weitere Informationen |
| --- | --- | --- |
| OData |In Kürze verfügbar |OData-Datenquellen werden hier in Kürze aufgeführt. |

## <a name="data-sources-accessible-through-rest-apis"></a>Datenquellen mit Zugriff über REST-APIs
Sie können mit **REST-APIs** eine Verbindung mit Datenquellen herstellen und auf diese Weise Daten aus allen Arten von Datenquellen verwenden, die **REST** unterstützen.

![](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_5.png)

In der folgenden Liste sind einige Beispiele für Datenquellen aufgeführt, mit denen **Power BI Desktop** eine Verbindung über die generische **REST-API**-Schnittstelle herstellen kann.

| Generischer Power BI Desktop-Connector | Externe Datenquelle | Link für weitere Informationen |
| --- | --- | --- |
| REST-APIs |Couchbase DB |[Informationen zur Couchbase-REST-API](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |

## <a name="data-sources-accessible-through-r-script"></a>Datenquellen mit Zugriff über R-Skript
Sie können mit **R-Skripts** auf Datenquellen zugreifen und diese Daten in **Power BI Desktop** verwenden.

![](media/desktop-connect-using-generic-interfaces/r-scripts-2.png)

In der folgenden Liste sind einige Beispiele für Datenquellen aufgeführt, mit denen **Power BI Desktop** eine Verbindung über die generische **R-Skript**-Schnittstelle herstellen kann.

| Generischer Power BI Desktop-Connector | Externe Datenquelle | Link für weitere Informationen |
| --- | --- | --- |
| R-Skript |SAS-Dateien |[Anleitung zu R-Skript vom CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| R-Skript |SPSS-Dateien |[Anleitung zu R-Skript vom CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| R-Skript |R-Statistikdateien |[Anleitung zu R-Skript vom CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |

## <a name="next-steps"></a>Weitere Schritte
Sie können mithilfe von **Power BI Desktop** eine Verbindung mit allen Arten von Datenquellen herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Datenquellen in Power BI-Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
