---
title: Bewährte Methoden für Bereitstellungspipelines
description: Bewährte Methoden für Bereitstellungspipelines in Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: e76d820e804a19db148e0db4c2702e002ee2c017
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275913"
---
# <a name="deployment-pipelines-best-practices-preview"></a>Bewährte Methoden für Bereitstellungspipelines (Vorschau)

Dieser Artikel bietet eine Anleitung für BI-Ersteller, die ihre Inhalte während des gesamten Lebenszyklus verwalten. Hierbei liegt der Schwerpunkt auf der Nutzung von Bereitstellungspipelines als Tool für die Lebenszyklusverwaltung von BI-Inhalten.

Dieser Artikel ist in vier Abschnitte unterteilt:

* **Inhaltsvorbereitung**: Bereiten Sie Ihre Inhalte auf die Lebenszyklusverwaltung vor.

* **Bereitstellung**: Lernen Sie die besten Möglichkeiten zur Erstellung von Inhalten in der Entwicklungsphase für Bereitstellungspipelines kennen.

* **Test**: Erfahren Sie, wie Sie die Testphase für Bereitstellungspipelines zum Testen Ihrer Umgebung verwenden können.

* **Produktion**: Nutzen Sie die Produktionsphase für Bereitstellungspipelines, wenn Sie Ihre Inhalte zur Nutzung zur Verfügung stellen.

## <a name="content-preparation"></a>Inhaltsvorbereitung

Bereiten Sie Ihre Inhalte für die fortlaufende Verwaltung während des gesamten Lebenszyklus vor. Lesen Sie zunächst alle Informationen im vorliegenden Abschnitt, bevor Sie eine der folgenden Aktionen durchführen:

* Freigeben von Inhalten für die Produktion

* Beginn der Verwendung einer Bereitstellungspipeline für einen bestimmten Arbeitsbereich

* Veröffentlichen Ihrer Arbeit

### <a name="treat-each-workspace-as-a-complete-package-of-analytics"></a>Behandeln Sie jeden Arbeitsbereich als ein vollständiges Analysepaket

Im Idealfall sollte ein Arbeitsbereich einen Aspekt (z. B. Abteilung, Geschäftseinheit, Projekt, Sparte) in Ihrer Organisation vollständig abbilden. Dies erleichtert die Verwaltung von Berechtigungen für verschiedene Benutzer und ermöglicht es, die Inhaltsfreigabe für den gesamten Arbeitsbereich nach einem geplanten Zeitplan zu steuern.  

Wenn Sie [zentralisierte Datasets](../connect-data/service-datasets-across-workspaces.md) verwenden, die organisationsweit genutzt werden, wird das Erstellen von zwei Arten von Arbeitsbereichen empfohlen:

* **Arbeitsbereiche für Modellierung und Daten**: Diese Arbeitsbereiche enthalten alle zentralisierten Datasets.

* **Arbeitsbereiche für die Berichterstellung**: Diese Arbeitsbereiche enthalten alle abhängigen Berichte und Dashboards.

### <a name="plan-your-permission-model"></a>Planen Ihres Berechtigungsmodells

Eine Bereitstellungspipeline ist ein Power BI-Objekt mit eigenen [Berechtigungen](deployment-pipelines-process.md#permissions). Zusätzlich umfasst die Pipeline Arbeitsbereiche, die ebenfalls über eigene Berechtigungen verfügen.

Um einen sicheren und einfachen Workflow zu implementieren, müssen Sie planen, wer Zugriff auf jeden Teil der Pipeline erhält. Berücksichtigen Sie unter anderem Folgendes:

* Wer sollte Zugriff auf die Pipeline erhalten?

* Welche Vorgänge sollten Benutzer mit Pipelinezugriff in jeder Phase ausführen dürfen?

* Wer überprüft die Inhalte in der Testphase?

* Sollten Reviewer für die Testphase Zugriff auf die Pipeline erhalten?

* Wer betreut die Bereitstellung in die Produktionsphase?

* Welche Arbeitsbereiche werden zugewiesen?

* Welchen Phasen wird Ihr Arbeitsbereich zugewiesen?

* Müssen Änderungen an den Berechtigungen des Arbeitsbereichs vorgenommen werden, den Sie zuweisen?

### <a name="connect-different-stages-to-different-databases"></a>Verbinden verschiedener Phasen mit verschiedenen Datenbanken

Eine Produktionsdatenbank sollte immer stabil und verfügbar sein. Sie sollte nicht mit Abfragen überlastet werden, die von BI-Erstellern für ihre Entwicklungs- oder Testdatasets generiert wurden. Erstellen Sie separate Datenbanken für Entwicklung und Tests. Dies trägt zum Schutz der Produktionsdaten bei und verhindert, dass die Entwicklungsdatenbank mit dem gesamten Produktionsdaten überlastet wird, wodurch Vorgänge möglicherweise verlangsamt werden.

>[!NOTE]
>Wenn Ihre Organisation [freigegebene zentralisierte Datasets](../connect-data/service-datasets-share.md) verwendet, können Sie diese Empfehlung überspringen.

### <a name="use-parameters-in-your-model"></a>Verwenden von Parametern in Ihrem Modell

Da Sie Datenquellen für Datensätze nicht im Power BI-Dienst bearbeiten können, wird anstelle einer statischen Verbindungszeichenfolge die Verwendung von [Parametern](https://docs.microsoft.com/power-query/power-query-query-parameters) zum Speichern von Verbindungsdetails wie beispielsweise Instanznamen und Datenbanknamen empfohlen. Auf diese Weise können Sie die Verbindungen zu einem späteren Zeitpunkt über das Power BI-Webportal oder [unter Verwendung von APIs](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup) verwalten.

In Bereitstellungspipelines können Sie Parameterregeln konfigurieren, um bestimmte Werte für die Entwicklungs-, Test- und Produktionsphase festzulegen.

Wenn Sie keine Parameter für Ihre Verbindungszeichenfolge verwenden, können Sie Datenquellenregeln definieren, um eine Verbindungszeichenfolge für ein bestimmtes Dataset anzugeben. In Bereitstellungspipelines wird dies jedoch nicht für alle Datenquellen unterstützt. Anhand der Informationen unter [Einschränkungen für Datensatzregeln](deployment-pipelines-get-started.md#dataset-rule-limitations) können Sie überprüfen, ob Sie Regeln für Ihre Datenquelle konfigurieren können.

Für Parameter gibt es zusätzliche Verwendungsmöglichkeiten, sie können z. B. zum Durchführen von Änderungen an Abfragen, Filtern und dem in einem Bericht angezeigten Text genutzt werden.

## <a name="development"></a>Entwicklung

Dieser Abschnitt bietet Empfehlungen für die Arbeit mit der Entwicklungsphase für Bereitstellungspipelines.

### <a name="use-power-bi-desktop-to-edit-your-reports-and-datasets"></a>Verwenden von Power BI Desktop zum Bearbeiten Ihrer Berichte und Datasets

Erwägen Sie die Verwendung von Power BI Desktop als Ihre lokale Entwicklungsumgebung. Mit Power BI Desktop können Sie Aktualisierungen Ihrer Berichte und Datasets testen, erkunden und überprüfen. Sobald die Arbeit abgeschlossen ist, können Sie Ihre neue Version in die Entwicklungsphase hochladen. Aus den folgenden Gründen wird empfohlen, PBIX-Dateien in der Desktop-Version (und nicht im Power BI-Dienst) zu bearbeiten:

* Es ist einfacher, mit anderen Entwicklern an derselben PBIX-Datei zusammenzuarbeiten, wenn alle Änderungen mit demselben Tool durchgeführt werden.

 * Durch Onlineänderungen, das Herunterladen der PBIX-Datei und anschließendes erneutes Hochladen werden doppelte Berichte und Datasets erzeugt.

* Sie können die Versionskontrolle verwenden, um Ihre PBIX-Dateien auf dem neuesten Stand zu halten.

### <a name="version-control-for-pbix-files"></a>Versionskontrolle für PBIX-Dateien

Wenn Sie den Versionsverlauf Ihrer Berichte und Datasets verwalten möchten, verwenden Sie die [automatische Synchronisierung von Power BI mit OneDrive](../connect-data/service-connect-to-files-in-app-workspace-onedrive-for-business.md). Auf diese Weise werden Ihre Dateien mit der aktuellen Version auf dem neuesten Stand gehalten. Darüber hinaus können Sie bei Bedarf ältere Versionen abrufen.

>[!NOTE]
>Verwenden Sie die automatische Synchronisierung mit OneDrive (oder einem anderen Repository) nur mit den PBIX-Dateien in der Entwicklungsphase der Bereitstellungspipelines. Führen Sie keine Synchronisierung von PBIX-Dateien in den Test- und Produktionsphasen der Bereitstellungspipelines durch. Dies führt zu Problemen bei der pipelineübergreifenden Bereitstellung von Inhalten.

### <a name="separate-modeling-development-from-report-and-dashboard-development"></a>Trennen der Modellierungsentwicklung von der Entwicklung von Berichten und Dashboards

Für Bereitstellungen auf Unternehmensniveau wird empfohlen, die Entwicklung von Datasets und die Entwicklung von Berichten und Dashboards voneinander zu trennen. Um Änderungen nur an einen Bericht oder ein Dataset weiterzugeben, verwenden Sie die Option zur selektiven Bereitstellung von Bereitstellungspipelines.  

Dieser Ansatz sollte von Power BI Desktop ausgehen, indem eine separate PBIX-Datei für Datasets und Berichte erstellt wird. Beispielsweise können Sie eine PBIX-Datei für ein Dataset erstellen und in die Entwicklungsphase hochladen. Später können Ihre Berichtsautoren eine neue PBIX-Datei nur für den Bericht erstellen und diese über eine Liveverbindung [mit dem veröffentlichten Dataset verbinden](../connect-data/service-datasets-discover-across-workspaces.md). Diese Technik ermöglicht es verschiedenen Erstellern, getrennt an Modellierung und Visualisierungen zu arbeiten und sie unabhängig voneinander für die Produktion bereitzustellen.

Mit [freigegebenen Datasets](../connect-data/service-datasets-share.md) können Sie diese Methode auch arbeitsbereichsübergreifend verwenden.

### <a name="manage-your-models-using-xmla-readwrite-capabilities"></a>Verwalten Ihrer Modelle mithilfe von XMLA-Lese-/Schreibfunktionen

Durch die Trennung der Modellierungsentwicklung von der Berichts- und Dashboardentwicklung können Sie erweiterte Funktionen wie die Quellcodeverwaltung, das Zusammenführen von Diff-Änderungen und automatisierte Prozesse nutzen. Diese Änderungen sollten in der Entwicklungsphase vorgenommen werden, sodass die fertigen Inhalte in der Test- und Produktionsphase eingesetzt werden können. Dadurch können Änderungen einen einheitlichen Prozess mit anderen abhängigen Elementen durchlaufen, bevor sie in der Produktionsphase bereitgestellt werden.

Sie können die Modellierungsentwicklung von der Visualisierung trennen, indem Sie einen [freigegebenes Dataset](../connect-data/service-datasets-share.md) unter Verwendung von XMLA-Lese-/Schreibfunktionen in einem externen Arbeitsbereich verwalten. Das freigegebene Dataset kann eine Verbindung mit mehreren Berichten in verschiedenen Arbeitsbereichen herstellen, die in mehreren Pipelines verwaltet werden.

## <a name="test"></a>Test

Dieser Abschnitt bietet Empfehlungen für die Arbeit mit der Testphase für Bereitstellungspipelines.

### <a name="simulate-your-production-environment"></a>Simulieren Ihrer Produktionsumgebung

Neben einer Überprüfung, ob neue Berichte oder Dashboards ordnungsgemäß angezeigt werden, muss ebenfalls deren Leistung aus Sicht des Endbenutzers überprüft werden. In der Testphase von Bereitstellungspipelines können Sie zu Testzwecken eine reale Produktionsumgebung simulieren.

Stellen Sie sicher, dass in Ihrer Testumgebung diese drei Faktoren berücksichtigt werden:

* Datenmenge

* Nutzungsumfang

* Eine ähnliche Kapazität wie in der Produktion

Beim Testen können Sie dieselbe Kapazität wie in der Produktionsphase verwenden. Dadurch kann jedoch die Produktion während der Auslastungstests instabil werden. Um eine instabile Produktion zu vermeiden, verwenden Sie zu Testzwecken eine andere Kapazität, die einen ähnlichen Ressourcenverbrauch wie die Produktionskapazität aufweist. Um Zusatzkosten zu vermeiden, können Sie eine [Azure-Kapazität im A-Tarif](../developer/embedded/azure-pbie-create-capacity.md) nutzen, für die nur für den Testzeitraum Gebühren anfallen.

![Diagramm zu bewährten Methoden für Bereitstellungspipelines](media/deployment-pipelines-best-practices/deployment-pipelines-best-practices-diagram.png)

### <a name="use-dataset-rules-with-a-real-life-data-source"></a>Verwenden von Datasetregeln mit einer realen Datenquelle

Wenn Sie die Testphase nutzen, um die reale Datenverwendung zu simulieren, wird eine Trennung der Entwicklungs- und Testdatenquellen empfohlen. Die Entwicklungsdatenbank sollte relativ klein sein, und die Testdatenbank sollte der Produktionsdatenbank so ähnlich wie möglich sein. Verwenden Sie [Datenquellenregeln](deployment-pipelines-get-started.md#step-4---create-dataset-rules), um Datenquellen in der Testphase auszutauschen.

Es ist nützlich, die aus Ihrer Datenquelle importierte Datenmenge zu steuern, wenn Sie in der Testphase eine Produktionsdatenquelle verwenden. Fügen Sie hierzu in Power BI Desktop einen Parameter in Ihre Datenquellenabfrage ein. Verwenden Sie Parameterregeln, um die Menge der importierten Daten zu steuern, oder bearbeiten Sie den Parameterwert.
Sie können diesen Ansatz auch nutzen, wenn Sie Ihre Kapazität nicht überlasten möchten.

### <a name="measure-performance"></a>Messen der Leistung

Wenn Sie eine Produktionsphase simulieren, [überprüfen Sie die Berichtslast und die Interaktionen](../guidance/monitor-report-performance.md), und ermitteln Sie, ob die von Ihnen vorgenommenen Änderungen diese beeinflussen.

Sie müssen außerdem die [Auslastung der Kapazität überwachen](../admin/service-admin-premium-monitor-capacity.md), um Lastspitzen auffangen zu können, bevor sie die Produktion erreichen.  

>[!NOTE]
>Es wird empfohlen, die Kapazitätslasten nach der Bereitstellung von Updates in der Produktionsphase erneut zu überwachen.

### <a name="check-related-items"></a>Überprüfen zugehöriger Elemente

Zugehörige Elemente können von Änderungen an Datasets oder Berichten betroffen sein. Vergewissern Sie sich während der Tests, dass Ihre Änderungen nicht die Leistung vorhandener Elemente, die möglicherweise von den aktualisierten Elementen abhängen, beeinträchtigen oder deren Lauffähigkeit einschränken.

Sie können zugehörige Elemente mithilfe des Arbeitsbereichs [Herkunftsansicht](../collaborate-share/service-data-lineage.md) leicht ermitteln.

### <a name="test-your-app"></a>Testen Ihrer App

Wenn Sie Inhalte über eine App an Ihre Endbenutzer verteilen, überprüfen Sie die neue Version der App, bevor sie in der Produktion eingesetzt wird. Da jede Phase der Bereitstellungspipeline über einen eigenen Arbeitsbereich verfügt, können Sie Apps problemlos für die Entwicklungs- und Testphase veröffentlichen und aktualisieren. Auf diese Weise können Sie die App aus Sicht des Endbenutzers testen.

>[!IMPORTANT]
>Der Bereitstellungsprozess umfasst nicht die Aktualisierung der App-Inhalte oder -Einstellungen. Wenn Sie Änderungen an Inhalten oder Einstellungen durchführen möchten, müssen Sie die App in der erforderlichen Pipelinephase manuell aktualisieren.

## <a name="production"></a>Produktion

Dieser Abschnitt bietet Empfehlungen für die Arbeit mit der Produktionsphase für Bereitstellungspipelines.

### <a name="manage-who-can-deploy-to-production"></a>Verwalten der Bereitstellung für die Produktion

Die Bereitstellung in der Produktion sollte mit Umsicht erfolgen, deshalb gehört es zu den Best Practices, nur bestimmte Benutzer mit dieser sensiblen Aufgabe zu betrauen. Dennoch möchten Sie wahrscheinlich, dass alle BI-Ersteller für einen bestimmten Arbeitsbereich Zugriff auf die Pipeline erhalten. Dies lässt sich mit [Arbeitsbereichsberechtigungen](deployment-pipelines-process.md#permissions) für die Produktion erreichen.  

Um Inhalte phasenübergreifend bereitzustellen, müssen Benutzer entweder über Mitglieder- oder Administratorberechtigungen für beide Phasen verfügen. Stellen Sie sicher, dass nur die Personen über Arbeitsbereichsberechtigungen für die Produktion verfügen, denen Sie eine Bereitstellung in der Produktion ermöglichen möchten. Andere Benutzer können die Rollen „Mitwirkender“ oder „Betrachter“ für den Produktionsarbeitsbereich erhalten. Sie können Inhalte aus der Pipeline anzeigen, aber keine Bereitstellung durchführen.

Zusätzlich sollten Sie den Zugriff auf die Pipeline einschränken, indem Sie nur den Benutzern Pipelineberechtigungen erteilen, die am Prozess der Inhaltserstellung beteiligt sind.

### <a name="set-rules-to-ensure-production-stage-availability"></a>Festlegen von Regeln zum Sicherstellen von Verfügbarkeit in der Produktionsphase

[Datasetregeln](deployment-pipelines-get-started.md#step-4---create-dataset-rules) sind eine leistungsstarke Möglichkeit, um sicherzustellen, dass stets eine Verbindung mit den Daten in der Produktion besteht, damit diese jederzeit für die Benutzer verfügbar sind. Nach dem Anwenden von Datasetregeln können Bereitstellungen mit der Gewissheit ausgeführt werden, dass die Endbenutzer die relevanten Informationen unterbrechungsfrei anzeigen können.

Stellen Sie sicher, dass Sie Regeln für Produktionsdatasets für Datenquellen und Parameter festlegen, die im Dataset definiert sind.

### <a name="update-the-production-app"></a>Aktualisieren der Produktions-App

Bei der Bereitstellung in einer Pipeline werden die Inhalte des Arbeitsbereichs aktualisiert, die zugeordnete App wird jedoch nicht automatisch aktualisiert. Wenn Sie eine App zur Verteilung von Inhalten verwenden, vergessen Sie nicht, die App nach der Bereitstellung für die Produktion zu aktualisieren, damit Endbenutzer sofort die neueste Version verwenden können.  

### <a name="quick-fixes-to-content"></a>Schnellkorrekturen an Inhalten

Falls es in der Produktion zu Fehlern kommt, die eine schnelle Behebung erfordern, lassen Sie sich nicht dazu verleiten, eine neue PBIX-Version direkt in die Produktionsphase hochzuladen oder im Power BI-Dienst eine Onlineänderung durchzuführen. Eine rückwärts gerichtete Bereitstellung in den Test- und Entwicklungsphasen ist nicht möglich, wenn in diesen Phasen bereits Inhalte vorhanden sind. Darüber hinaus stellt eine Fehlerkorrektur ohne vorherige Tests keine gute Praxis dar. Die richtige Vorgehensweise zur Problembehandlung besteht darin, die Korrektur in der Entwicklungsphase zu implementieren und per Push in die verbleibenden Phasen der Bereitstellungspipeline zu übertragen. Auf diese Weise kann überprüft werden, ob die Fehlerkorrektur funktioniert, bevor sie in der Produktion bereitgestellt wird. Die Bereitstellung in allen Phasen der Pipeline dauert nur wenige Minuten.

## <a name="next-steps"></a>Nächste Schritte

>[!div class="nextstepaction"]
>[Einführung in Bereitstellungspipelines](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Erste Schritte mit Bereitstellungspipelines](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Grundlegendes zum Prozess für Bereitstellungspipelines](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Behandeln von Problemen mit Bereitstellungspipelines](deployment-pipelines-troubleshooting.md)
