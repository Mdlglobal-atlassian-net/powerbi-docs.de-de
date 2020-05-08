---
title: Überwachen der Berichtsleistung in Power BI
description: Anleitungen zum Überwachen der Berichtsleistung in Power BI.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 2962d5f8504b7214cb685457c59b11f1d9d7b85e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81525535"
---
# <a name="monitor-report-performance-in-power-bi"></a>Überwachen der Berichtsleistung in Power BI

Überwachen Sie die Berichtsleistung in Power BI Desktop mithilfe der [Power BI Premium Metrics-App](../service-premium-metrics-app.md), ermitteln Sie Engpässe, und erfahren Sie, wie Sie die Berichtsleistung verbessern können.

Die Überwachung der Leistung ist in den folgenden Situationen relevant:

- Das Importdatenmodell wird langsam aktualisiert.
- Ihre DirectQuery-Berichte oder Liveverbindungsberichte werden langsam generiert.
- Ihre Modellberechnungen werden langsam durchgeführt.

Ein Schwerpunkt der kontinuierlichen Optimierung sollten langsame Abfragen oder visuelle Berichtselemente sein.

## <a name="use-query-diagnostics"></a>Verwenden der Abfragediagnose

Verwenden Sie die [Abfragediagnose](/power-query/QueryDiagnostics) in Power BI Desktop, um das Verhalten von Power Query bei der Vorschauanzeige oder beim Ausführen von Abfragen zu ermitteln. Erfassen Sie zudem mithilfe der _Schrittdiagnose_ detaillierte Informationen zur Auswertung der einzelnen Abfrageschritte. Die Ergebnisse werden in Power Query verfügbar gemacht, und Sie können Transformationen anwenden, um die Abfrageausführung besser zu verstehen.

> [!NOTE]
> Die Abfragediagnose ist zurzeit als Previewfunktion verfügbar und muss unter _Optionen und Einstellungen_ aktiviert werden. Nach der Aktivierung stehen die zugehörigen Befehle im Fenster des Power Query-Editors auf der Registerkarte **Tools** des Menübands zur Verfügung.

![Die Registerkarte „Tools“ des Menübands im Power Query-Editor. Im Menüband werden die Befehle „Schrittdiagnose“, „Diagnose starten“ und „Diagnose beenden“ angezeigt.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>Verwenden der Leistungsanalyse

Mit der [Leistungsanalyse](../desktop-performance-analyzer.md) in Power BI Desktop können Sie die Leistung für jedes Ihrer Berichtselemente – beispielsweise visuelle Elemente und DAX-Formeln – ermitteln. Sie eignet sich insbesondere, um zu ermitteln, ob die Leistung durch eine Abfrage oder beim Rendern eines visuellen Elements beeinträchtigt wird.

## <a name="use-sql-server-profiler"></a>Verwenden von SQL Server Profiler

Langsame Abfragen können auch mithilfe von [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) ermittelt werden.

> [!NOTE]
> SQL Server Profiler ist als Teil von [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) verfügbar.

Verwenden Sie SQL Server Profiler, wenn Sie eine der folgenden Lösungen als Datenquelle nutzen:

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop unterstützt die Verbindung mit einem Diagnoseport. Über den Diagnoseport können andere Tools eine Verbindung herstellen, um zu Diagnosezwecken eine Ablaufverfolgung durchzuführen. Das Durchführen von Änderungen am Power Desktop-Datenmodell wird nicht unterstützt. Änderungen am Datenmodell können zu Datenbeschädigung und Datenverlust führen.

Befolgen Sie diese Anweisungen, um eine SQL Server Profiler-Ablaufverfolgung zu erstellen:

1. Öffnen Sie Ihren Power BI Desktop-Bericht (um den Port im nächsten Schritt problemlos ermitteln zu können). Schließen Sie alle anderen offenen Berichte.
1. Zum Ermitteln des von Power BI Desktop verwendeten Ports geben Sie in PowerShell (mit Administratorrechten) oder an der Eingabeaufforderung den folgenden Befehl ein:
    ```powershell
    netstat -b -n
    ```
    Die Ausgabe zeigt eine Liste mit Anwendungen und ihre geöffneten Ports. Suchen Sie den von **msmdsrv.exe** verwendeten Port, und notieren Sie die Nummer, da sie sie später benötigen. Es handelt sich um Ihre Instanz von Power BI Desktop.
1. So verbinden Sie SQL Server Profiler mit Ihrem Power BI Desktop-Bericht:
    1. Öffnen Sie SQL Server Profiler.
    1. Wählen Sie in SQL Server Profiler im Menü _Datei_ die Option _Neue Ablaufverfolgung_ aus.
    1. Wählen Sie für **Servertyp** die Option _Analysis Services_ aus.
    1. Geben Sie für **Servername** den Namen _localhost:[der zuvor notierte Port]_ ein.
    1. Klicken Sie auf _Ausführen_. Die SQL Server Profiler-Ablaufverfolgung ist nun aktiv und erstellt Profile für Ihre Power BI Desktop-Abfragen.
1. Wenn Power BI Desktop-Abfragen ausgeführt werden, werden ihre Dauer und CPU-Zeiten angezeigt. Abhängig vom Datenquellentyp werden weitere Ereignisse angezeigt, die Auskunft über die Ausführung der Abfrage geben. Anhand dieser Informationen können Sie ermitteln, welche Abfragen zu Engpässen führen.

Ein Vorteil bei Verwendung von SQL Server Profiler ist, dass Sie eine Ablaufverfolgung für eine (relationale) SQL Server-Datenbank speichern können. Die Ablaufverfolgung kann als Eingabe für den [Datenbankoptimierungsratgeber](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor) verwendet werden. Auf diese Weise können Sie Empfehlungen zur Optimierung Ihrer Datenquelle erhalten.

## <a name="monitor-premium-metrics"></a>Überwachen von Premium-Metriken

Um die Integrität und Kapazität Ihres Power BI Premium-Abonnements zu überwachen, können Sie die **Power BI Premium Metrics-App** verwenden. Weitere Informationen finden Sie unter [Power BI Premium Metrics-App](../service-premium-metrics-app.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Abfragediagnose](/power-query/QueryDiagnostics)
- [Leistungsanalyse](../desktop-performance-analyzer.md)
- [Problembehandlung für die Berichtsleistung in Power BI](report-performance-troubleshoot.md)
- [Power BI Premium Metrics-App](../service-premium-metrics-app.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
