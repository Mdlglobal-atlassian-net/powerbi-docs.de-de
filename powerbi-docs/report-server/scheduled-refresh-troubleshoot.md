---
title: Problembehandlung für die geplante Aktualisierung in Power BI-Berichtsserver
description: In diesem Artikel werden die verfügbaren Ressourcen für die Behandlung von Problemen mit der geplanten Aktualisierung in Power BI-Berichtsserver erläutert.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: troubleshooting
ms.date: 11/01/2017
ms.author: maggies
ms.openlocfilehash: dd7d6a140dd9828a188f22144e31ea89e342c370
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698691"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Problembehandlung für die geplante Aktualisierung in Power BI-Berichtsserver
In diesem Artikel werden die verfügbaren Ressourcen für die Behandlung von Problemen mit der geplanten Aktualisierung in Power BI-Berichtsserver erläutert.

Da weitere Probleme festgestellt werden können, wird dieser Artikel laufend mit hilfreichen Informationen aktualisiert.

## <a name="common-issues"></a>Häufige Probleme
Im Folgenden werden die am häufigsten auftretenden Probleme beim Planen der Aktualisierung für einen Bericht erläutert. 

### <a name="driver-related-problems"></a>Treiberbezogene Probleme
Beim Herstellen einer Verbindung mit Datenquellen können Treiber von Drittanbietern erforderlich sein, die installiert werden müssen, damit eine Verbindung erfolgreich hergestellt werden kann. Sie müssen diese nicht nur auf dem Computer installieren, auf dem Sie mit Power BI Desktop arbeiten, Sie müssen auch sicherstellen, dass der Treiber auf dem Berichtsserver installiert ist.

Der Treiber kann zudem in einer 32-Bit-Version und einer 64-Bit-Version vorliegen. Sie müssen den 64-Bit-Treiber installieren, da Power BI-Berichtsserver auf 64 Bit ausgelegt ist.

Wenden Sie sich an den jeweiligen Hersteller, um Einzelheiten zum Installieren und Konfigurieren der Treiber von Drittanbietern zu erfragen.

### <a name="memory-pressure"></a>Arbeitsspeicherauslastung
Arbeitsspeicherauslastung kann auftreten, wenn beim Verarbeiten und Rendern von Berichten mehr Arbeitsspeicher belegt wird. Bei der geplanten Aktualisierung von Berichten kann eine erhebliche Menge von Arbeitsspeicher auf dem Computer verbraucht werden. Dies gilt insbesondere für größere Berichte. Eine Arbeitsspeicherauslastung kann zu Berichtsfehlern sowie zum Absturz des Berichtsservers führen.

Wenn häufig eine Arbeitsspeicherauslastung auftritt, empfiehlt es sich möglicherweise, eine horizontale Hochskalierung des Berichtsservers zu erwägen, um die Last der Ressourcen zu verteilen. Sie können auch festlegen, dass ein bestimmter Berichtsserver für die Datenaktualisierung verwendet wird. Hierfür verwenden Sie die Einstellung `IsDataModelRefreshService` in der Datei „rsreportserver.config“. Mit dieser Einstellung können Sie einen oder mehrere Server als Frontend-Server für die Verarbeitung von Berichten bei Bedarf festlegen, während Sie eine andere Gruppe von Servern ausschließlich für die geplante Aktualisierung vorsehen.

Weitere Informationen zum Überwachen einer Analysis Services-Instanz finden Sie unter [Überwachen einer Analysis Services-Instanz](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Weitere Informationen zu Arbeitsspeichereinstellungen in Analysis Services finden Sie unter [Speichereigenschaften](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Kerberos-Konfiguration
Zum Herstellen einer Verbindung mit einer Datenquelle mit Windows-Anmeldeinformationen muss möglicherweise die eingeschränkte Kerberos-Delegierung konfiguriert werden, damit die Verbindung erfolgreich hergestellt werden kann. Weitere Informationen zum Konfigurieren der eingeschränkten Kerberos-Delegierung finden Sie unter [Konfigurieren von Kerberos für die Verwendung von Power BI-Berichten](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Bekannte Probleme
Informationen zu bekannten Problemen werden hier aufgelistet, sobald sie verfügbar werden.

## <a name="configuration-settings"></a>Konfigurationseinstellungen
Anhand der folgenden Einstellungen kann die geplante Aktualisierung konfiguriert werden. In SSMS (SQL Server Management Studio) festgelegte Einstellungen gelten für alle Berichtsserver in einer Bereitstellung für horizontales Skalieren. In „rsreportserver.config“ konfigurierte Einstellungen gelten für die Server, auf dem sie festgelegt sind.

**Einstellungen in SSMS:**

| Einstellung | Beschreibung |
| --- | --- |
| MaxFileSizeMb |Maximale Dateigröße für hochgeladene Berichte. Die Standardeinstellung ist 1.000 MB (1 GB). Der Maximalwert ist 2.000 MB (2 GB). |
| ModelCleanupCycleMinutes |Legt fest, wie oft das Modell für die Entfernung aus dem Speicher überprüft wird. Die Standardeinstellung ist 15 Minuten. |
| ModelExpirationMinutes |Legt anhand des Zeitpunkts der letzten Verwendung den Zeitraum bis zum Ablauf und zur Entfernung des Modells fest. Die Standardeinstellung ist 60 Minuten. |
| ScheduleRefreshTimeoutMinutes |Legt fest, wie lange die Datenaktualisierung für einen Modus dauern kann. Die Standardeinstellung ist 120 Minuten. Eine Obergrenze ist nicht festgelegt. |

**Einstellungen in „rsreportserver.config“:**

```xml
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Tools zur Problembehandlung
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Relevante Protokolle für die geplante Aktualisierung von Power BI-Berichten
Die Protokolldateien mit Informationen zur geplanten Aktualisierung sind die RSPowerBI_-Protokolle. Sie sind im Ordner „LogFiles“ des Berichtsserver-Installationsverzeichnisses enthalten. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Fehlerbedingung**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Erfolgreiche Aktualisierung***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Falsche Anmeldeinformationen**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Aktivieren der ausführlichen Protokollierung
Das Aktivieren der ausführlichen Protokollierung erfolgt in Power BI-Berichtsserver auf dieselbe Weise wie für SQL Server Reporting Services.

1. Öffnen Sie `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Ändern Sie unter `<system.diagnostics>` den Wert für **DefaultTraceSwitch** in **4**.
3. Ändern Sie unter `<RStrace>` den Wert für **Components** in **all:4**. 

### <a name="executionlog"></a>Ausführungsprotokoll
Beim Rendern eines Power BI-Berichts oder beim Ausführen eines Plans für die geplante Aktualisierung werden dem Ausführungsprotokoll in der Datenbank neue Einträge hinzugefügt. Diese Einträge sind in der Ansicht **ExecutionLog3** in der Berichtsserver-Katalogdatenbank verfügbar.

Ausführungsprotokolleinträge für Power BI-Berichte unterscheiden sich von Einträgen für andere Berichtstypen.

* TimeRendering-Spalten weisen stets den Wert 0 auf. Das Rendern von Power BI-Berichten erfolgt im Browser, nicht auf dem Server.
* Es gibt zwei Anforderungstypen und nachfolgende Aktionen für Elemente:
  * **Interactive**: Beim Anzeigen eines Berichts.
    * **ASModelStream**: Beim Streamen des Datenmodells in Analysis Services aus dem Katalog.
    * **ConceptualSchema**: Wenn der Benutzer auf die Anzeige des Berichts klickt.
    * **QueryData**: Beim Anfordern von Daten vom Client.
  * **RefreshCache**: Bei erfolgter Ausführung eines Plans für die geplante Aktualisierung.
    * **ASModelStream**: Beim Streamen des Datenmodells in Analysis Services aus dem Katalog.
    * **DataRefresh**: Beim Aktualisieren von Daten aus einer oder mehreren Datenquellen.
    * **SaveToCatalog**: Beim Speichern des Datenmodells im Katalog.

## <a name="analysis-services"></a>Analysis Services
Möglicherweise möchten Sie gelegentlich Analysis Services ändern, um Probleme zu untersuchen oder um Speicherlimits anzupassen.

> [!IMPORTANT]
> Diese Einstellungen werden bei jedem Upgrade des Berichtsservers zurückgesetzt. Bewahren Sie eine Kopie der vorgenommenen Änderungen auf, und wenden Sie sie ggf. erneut an.
> 
> 

### <a name="install-location"></a>Installationsverzeichnis
Es gilt der folgende Standardspeicherort für Power BI-Berichtsserver und Analysis Services.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Konfigurieren von Analysis Services-Einstellungen („msmdsrv.ini“)
Im Verzeichnis `<install directory>\PBIRS\ASEngine` befindet sich die Datei *msmdsrv.ini*, mit der Sie verschiedene Einstellungen von Analysis Services steuern können. Wenn Sie diese Datei öffnen, stellen Sie sofort fest, dass sie nicht alle Einstellungen enthält, die in der Datei „msmdsrv.ini“ zu erwarten wären. 

Dies ist darauf zurückzuführen, dass der tatsächliche von Power BI-Berichtsserver ausgeführte Analysis Services-Prozess in `<install directory>\PBIRS\ASEngine\workspaces` gestartet wird. In diesem Ordner sehen Sie die gewohnte komplette Datei *msmdsrv.ini*. Die Datei darf auf keinen Fall im Ordner „workspaces“ geändert werden, da sie beim Starten des Analysis Services-Prozesses jedes Mal neu geschrieben wird. Wenn Sie eine Einstellung anpassen möchten, nehmen Sie die erforderliche Änderung in der Datei „msmdsrv.ini“ im Verzeichnis `<install directory>\PBIRS\ASEngine` vor.

Die folgenden Einstellungen werden bei jedem Start des Analysis Services-Prozesses geändert. Alle an diesen Einstellungen vorgenommenen Änderungen werden ignoriert.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Profilerstellung für den lokalen Analysis Services-Prozess
Eine SQL Profiler-Ablaufverfolgung kann zu Diagnosezwecken für den lokalen Analysis Services-Prozess ausgeführt werden. Führen Sie zum Herstellen der Verbindung mit der lokalen Analysis Services-Instanz Folgendes aus.

Die SQL Server Profiler-Ablaufverfolgung ist im [SSMS (SQL Server Management Studio)-Download](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) enthalten.

1. Starten Sie **SQL Server Profiler** als Administrator.
2. Wählen Sie die Schaltfläche **Neue Ablaufverfolgung** aus.
3. Wählen Sie im Dialogfeld **Mit Server verbinden** die Option **Analysis Services** aus, und geben Sie als Servernamen **localhost:5132** ein.
4. Wählen Sie im Dialogfeld **Ablaufverfolgungseigenschaften** die zu erfassenden Ereignisse aus, und wählen Sie **Ausführen** aus.

## <a name="lock-pages-in-memory-windows-privilege"></a>Windows-Berechtigung „Sperren von Seiten im Speicher“
Wenn Sie feststellen, dass ein Power BI-Bericht nicht gerendert werden kann, stellt das Zuweisen der Berechtigung **Sperren von Seiten im Speicher** zum Dienstkonto, unter dem Power BI-Berichtsserver ausgeführt wird, eine mögliche Lösung dar. Weitere Informationen zum Konfigurieren von **Sperren von Seiten im Speicher** finden Sie unter [Windows-Berechtigungen, die dem Analysis Services-Dienstkonto zugewiesen sind](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

