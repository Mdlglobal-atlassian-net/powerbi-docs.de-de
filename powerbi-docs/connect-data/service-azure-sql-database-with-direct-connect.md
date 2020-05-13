---
title: Azure SQL-Datenbank mit DirectQuery
description: Azure SQL-Datenbank mit DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.date: 04/28/2020
LocalizationGroup: Data from databases
ms.openlocfilehash: aa1ae57d928633ce61ab66a8e0e905118c3a7877
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302159"
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL-Datenbank mit DirectQuery

Erfahren Sie, wie Sie eine direkte Verbindung mit der Azure SQL-Datenbank herstellen und Berichte erstellen, in denen Livedaten verwendet werden. Sie können Ihre Daten in der Datenquelle und nicht in Power BI speichern.

Durch DirectQuery werden Abfragen zurück zur Azure SQL-Datenbank gesendet, während Sie die Daten in der Berichtsansicht untersuchen. Diese Variante wird für Benutzer empfohlen, die mit den Datenbanken und den Entitäten vertraut sind, mit denen die Verbindung hergestellt wird.

**Hinweise:**

* Geben Sie beim Herstellen der Verbindung den vollqualifizierten Servernamen an (weitere Informationen folgen später im Abschnitt).
* Stellen Sie sicher, dass die Firewallregeln für die Datenbank so konfiguriert sind, dass sie den „[Zugriff auf Azure-Dienste erlauben](https://docs.microsoft.com/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services)“.
* Durch jede Aktion, z. B. beim Auswählen einer Spalte oder dem Hinzufügen eines Filters, wird eine Abfrage zurück an die Datenbank gesendet.
* Die Kacheln werden stündlich aktualisiert (die Aktualisierung muss nicht geplant werden). Beim Herstellen einer Verbindung können Sie unter „Erweiterte Einstellungen“ festlegen, wie oft aktualisiert werden soll.
* Q&A steht für DirectQuery-Datasets nicht zur Verfügung.
* Schemaänderungen werden nicht automatisch übernommen.

Diese Einschränkungen und Hinweise können sich ändern, da wir die Benutzeroberfläche fortlaufend optimieren. Die Schritte zum Herstellen der Verbindung werden nachfolgend beschrieben.

> [!Important]
> Die Konnektivität mit Azure SQL-Datenbank wurde verbessert.  Verwenden Sie Power BI Desktop für optimale Ergebnisse beim Herstellen einer Verbindung mit Ihrer Azure SQL-Datenbank-Datenquelle.  Sobald Sie Ihr Modell und Ihren Bericht erstellt haben, können Sie diese im Power BI-Dienst veröffentlichen.  Der direkte Connector für Azure SQL-Datenbank im Power BI-Dienst ist mittlerweile veraltet.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop und DirectQuery

Verwenden Sie Power BI Desktop zum Herstellen einer Verbindung mit der Azure SQL-Datenbank über DirectQuery. Dieser Ansatz bietet zusätzliche Flexibilität und Funktionalität. Mit Power BI Desktop erstellte Berichte können dann im Power BI-Dienst veröffentlicht werden. [Hier](desktop-use-directquery.md) erhalten Sie weitere Informationen zum Herstellen einer Verbindung mit der Azure SQL-Datenbank über DirectQuery in Power BI Desktop.

## <a name="find-parameter-values"></a>Suchen von Parameterwerten

Sie finden Ihren vollqualifizierten Servernamen und den Datenbanknamen im Azure-Portal.

![Neues Azure Portal-Update](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Azure Portal-Update](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](../includes/direct-query-sso.md)]

## <a name="next-steps"></a>Weitere Schritte

* [Verwenden von DirectQuery in Power BI Desktop](desktop-use-directquery.md)  
* [Was ist Power BI?](../fundamentals/power-bi-overview.md)  
* [Abrufen von Daten für Power BI](service-get-data.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
