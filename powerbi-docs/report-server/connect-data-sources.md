---
title: Datenquellen für paginierte Berichte auf dem Power BI-Berichtsserver
description: Informationen zu Datenquellen auf dem Power BI-Berichtsserver, mit denen paginierte Berichte (RDL) eine Verbindung herstellen können.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260713"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Datenquellen für paginierte Berichte auf dem Power BI-Berichtsserver
Paginierte Reporting Services-Berichte auf dem Power BI-Berichtsserver unterstützen die gleichen Datenquellen, die in SQL Server Reporting Services unterstützt werden. Eine Liste finden Sie unter [Von Reporting Services unterstützte Datenquellen](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Herstellen einer Verbindung mit Oracle-Datenquellen mithilfe von UseInstalledUICulture

Um eine Verbindung mit Oracle-Datenquellen herzustellen, verwendet der Power BI-Berichtsserver den Oracle-Datenanbieter für .NET (ODP.NET), der NLS-agnostisch ist.

Standardmäßig verwendet der Berichtsserver die Benutzeroberflächenkultur des ersten Clients, um ODP.NET zu laden.  Dies führt dazu, dass alle nachfolgenden Verbindungen vom Berichtsserver mit Oracle in dieser anfänglichen Benutzeroberflächenkultur erfolgen, bis der Dienst neu gestartet wird.  Diese Vorgehensweise kann aufgrund von Konflikten bei der Formatierung in der Benutzeroberflächenkultur zu Problemen beim Rendern von Berichten führen.

Um die Funktionalität des Power BI-Berichtsservers in dieser Hinsicht zu verbessern, haben wir eine Konfigurationseinstellung namens UseInstalledUICulture eingeführt. Wenn UseInstalledUICulture auf „true“ festgelegt ist, lädt der Berichtsserver ODP.NET immer in der Benutzeroberflächenkultur des Servers, nicht in der Kultur des ersten Clients.
Diese Einstellung ist ab der Februarversion des Diensts im Power BI-Berichtsserver verfügbar.

Zum Aktivieren des Features ändern Sie den Eintrag für die ORACLE-Erweiterung in der rsReportServer.config-Datei wie folgt.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Nächste Schritte
Da Sie nun eine Verbindung mit der Datenquelle hergestellt haben, können Sie [einen paginierten Bericht erstellen](quickstart-create-paginated-report.md).  


Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
