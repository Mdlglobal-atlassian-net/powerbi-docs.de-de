---
title: Dataflows in Power BI
description: Erfahren Sie mehr über die Funktionsweise von Dataflows in Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/01/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 9a0b9eb90e3c39cf1f07842f5ea1da88b7cd06ad
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83322399"
---
# <a name="self-service-data-prep-in-power-bi"></a>Self-Service-Datenaufbereitung in Power BI

Mit dem stets wachsenden Datenvolumen wächst auch die Herausforderung, diese Daten in gut geformte, handlungsrelevante Informationen umzuwandeln. Wir wollen Daten, die für Analysen geeignet sind, um Visuals, Berichte und Dashboards aufzufüllen, damit wir aus den Datenmengen schnell handlungsrelevante Informationen gewinnen. Mit der  **Self-Service-Datenaufbereitung** für Big Data in Power BI wandeln Sie Daten mit wenigen Klicks in Power BI-Informationen um.

![Verwenden von Dataflows in Power BI](media/service-dataflows-overview/powerbi-dataflows_01.png)

Power BI führt **Dataflows** ein, um Organisationen dabei zu unterstützen, Daten aus unterschiedlichen Quellen zu vereinheitlichen und zum Modellieren aufbereiten. Analysten können mit vertrauten Self-Service-Tools ganz einfach Dataflows erstellen. Dataflows werden zum Erfassen, Transformieren, Integrieren und Anreichern von Big Data verwendet, indem unter anderem Datenquellenverbindungen, ETL-Logik und Aktualisierungspläne definiert werden. Darüber hinaus gestaltet die neue modellgesteuerte Berechnungs-Engine, die zum Funktionsumfang eines Dataflows gehört, die Datenaufbereitung verwaltbar, deterministischer und unkomplizierter für Datenanalysten und Berichtsersteller. Ähnlich wie Tabellenkalkulationen Neuberechnungen für alle betroffenen Formeln verarbeiten, verwalten Dataflows Änderungen für Entitäten oder Datenelemente in Ihrem Namen, automatisieren Updates und erleichtern einst schwierige und zeitaufwändige Logikprüfungen für eine einfache Datenaktualisierung. Mit Dataflows können Aufgaben, die früher von Data Scientists überwacht werden mussten – und mehrere Stunden oder Tage dauerten – nun mit wenigen Klicks von Analysten und Berichtserstellern erledigt werden. 

Daten werden als Entitäten im [**Common Data Model**](https://docs.microsoft.com/powerapps/common-data-model/overview) in Azure Data Lake Storage Gen2 gespeichert. Dataflows werden in Arbeitsbereichen mithilfe des Power BI-Diensts erstellt und verwaltet.  
 
**Dataflows** wurden zum Verwenden des **Common Data Model** konzipiert. Dabei handelt es sich um eine standardisierte, modulare und erweiterbare Sammlung von Datenschemas, die von Microsoft veröffentlicht wurde und darauf ausgelegt ist, das Erstellen, Verwenden und Analysieren von Daten zu vereinfachen. Mit diesem Modell können Sie schnell und einfach von Datenquellen zu Power BI-Dashboards wechseln.

Sie können Dataflows verwenden, um Daten aus einer großen und wachsenden Anzahl von unterstützten lokalen und cloudbasierten Datenquellen wie Dynamics 365, Salesforce, Azure SQL-Datenbank, Excel und SharePoint zu übernehmen.

Dann können Sie Daten Standardentitäten im Common Data Model zuordnen, vorhandene Entitäten ändern und erweitern sowie benutzerdefinierte Entitäten erstellen. Fortgeschrittene Benutzer können vollständig angepasste Dataflows erstellen, indem sie eine integrierte Power Query-Self-Service-Erstellungsumgebung mit wenig bis gar keinem Code verwenden, ähnlich der Power Query-Umgebung, mit der bereits Millionen von Power BI Desktop- und Excel-Benutzer arbeiten.  

Wenn Sie einen Dataflow erstellt haben, können Sie mit Power BI Desktop und dem Power BI-Dienst Datasets, Berichte, Dashboards und Apps erstellen, die mithilfe des Common Data Model wichtige Informationen zu Ihren Geschäftsaktivitäten gewinnen. 

Die Planung der Dataflowaktualisierung wird direkt in dem Arbeitsbereich verwaltet, in dem der Dataflow erstellt wurde, genau wie bei Ihren Datasets. 

## <a name="how-dataflows-work"></a>Funktionsweise von Dataflows

Hier sind einige Beispiele für die Funktionsweise von Dataflows:

* Organisationen können ihre Daten Standardentitäten im Common Data Model zuordnen oder eigene benutzerdefinierte Entitäten erstellen. Diese Entitäten können dann als Bausteine verwendet werden, um einsatzbereite Berichte, Dashboards und Apps zu erstellen und direkt an Benutzer in ihrer gesamten Organisation zu verteilen. 

* Mithilfe der umfangreichen Sammlung von Microsoft-Datenconnectors können Organisationen ihre eigenen Datenquellen mit Dataflows verbinden. Power Query wird dazu genutzt, die Daten aus ihrer Quelle zuzuordnen und in Power BI einzubinden. Wenn diese Daten von einem Dataflow importiert (und mit einer angegebenen Häufigkeit aktualisiert) wurden, lassen sich mit diesen Dataflowentitäten in der Power BI Desktop-Anwendung ansprechende Berichte und Dashboards erstellen. 

## <a name="how-to-use-dataflows"></a>Verwenden von Dataflows

Der vorherige Abschnitt beschreibt mehrere Szenarien zum schnellen Erstellen leistungsstarker Analysen in Power BI mit Dataflows. Dieser Abschnitt bietet einen Überblick darüber, wie schnell Sie in einer Organisation mithilfe von Dataflows Einblicke erhalten, und wie BI Pro-Benutzer ihre eigenen Dataflows erstellen und Informationen für ihre eigene Organisation anpassen.

> [!NOTE]
> Sie benötigen ein kostenpflichtiges Power BI-Konto, um Dataflows verwenden zu können, z.B. ein Power BI Pro- oder ein Power BI Premium-Konto. Sie leisten für die Nutzung von Dataflows jedoch keine separaten Zahlungen. 

### <a name="extend-the-common-data-model-for-your-business-needs"></a>Erweitern des Common Data Model für Ihre Geschäftsanforderungen
Business Intelligence-Experten in Organisationen, die das Common Data Model erweitern möchten, können mit Dataflows die Standardentitäten anpassen oder neue erstellen. Dieser Self-Service-Ansatz zum Anpassen des Datenmodells kann zusammen mit Dataflows zum Erstellen von Apps und Power BI-Dashboards verwendet werden, die auf eine Organisation zugeschnitten sind.

### <a name="define-dataflows-programmatically"></a>Programmgesteuertes Definieren von Dataflows
Vielleicht möchten Sie auch Ihre eigenen programmgesteuerten Lösungen entwickeln, um Dataflows zu erstellen. Mit öffentlichen APIs und der Funktion zum Erstellen programmgesteuerter benutzerdefinierter Definitionsdateien für Dataflows (model.json) entwickeln Sie eine benutzerdefinierte Lösung gemäß den individuellen Daten- und Analyseanforderungen Ihrer Organisation. 

Dank öffentlichen APIs können Entwickler einfach und unkompliziert mit Power BI und Dataflows arbeiten.

### <a name="extend-your-capabilities-with-azure"></a>Erweitern Ihrer Funktionen mit Azure
Azure Data Lake Storage Gen2 ist in jedem kostenpflichtigen Power BI-Abonnement enthalten (10 GB pro Benutzer, 100 TB pro P1-Knoten). So können Sie ganz einfach mit der Self-Service-Datenaufbereitung in Azure Data Lake beginnen. 

Power BI lässt sich so konfigurieren, dass Dataflowdaten im Azure Data Lake Storage Gen2-Konto Ihrer Organisation gespeichert werden. Wenn Power BI mit Ihrem Azure-Abonnement verknüpft ist, können Datenentwickler und Data Scientists leistungsstarke Azure-Produkte wie Azure Machine Learning, Azure Databricks und Azure Data Factory nutzen.

Power BI kann auch mit Ordnern mit schematisierten Daten im Common Data Model-Format verknüpft werden, die im Azure Data Lake Storage-Konto Ihrer Organisation gespeichert sind. Diese Ordner können von Diensten wie den Azure-Datendiensten erstellt werden. Wenn Analysten eine Verbindung mit diesen Ordnern herstellen, können sie in Power BI nahtlos mit diesen Daten arbeiten. 

Weitere Informationen zu Azure Data Lake Storage Gen2 und zur Integration von Dataflows, z. B. wie Dataflows erstellt werden, die im Azure Data Lake-Repository Ihrer Organisation gespeichert sind, finden Sie im Artikel [Dataflows and Azure Data Lake integration (Preview) (Dataflows und Azure Data Lake-Integration (Vorschauversion))](service-dataflows-azure-data-lake-integration.md).

## <a name="dataflow-capabilities-on-power-bi-premium"></a>Dataflowfeatures in Power BI Premium

Um Dataflowfeatures und -workloads mit einem Power BI Premium-Abonnement zu verwenden, Müssen Sie die Dataflowworkload für diese Premium-Kapazität aktivieren. Die folgende Tabelle beschreibt Dataflowfeatures und ihre Kapazitäten beim Verwenden eines Power BI Pro-Kontos und vergleicht diese mit Power BI Premium.


|Dataflowfeature | Power BI Pro |   Power BI Premium |
|---------|---------|---------|
|Geplante Aktualisierung| 8 pro Tag|  48|
|Gesamtspeicher| 10 GB/Benutzer  |100 TB/Knoten|
|Dataflowerstellung mit Power Query Online|    +   |+|
|Dataflowverwaltung in Power BI|   +|  +|
|Dataflow-Datenconnector in Power BI Desktop|  +|  +|
|Integration in Azure|    +|  +|
|Berechnete Entitäten (Transformationen im Speicher über M) | |   +|
|Neue Connectors|    +|  +|
|Inkrementelle Dataflowaktualisierung|  |   +|
|Ausführung in Power BI Premium-Kapazität/parallele Ausführung von Transformationen|   |   +|
|Verknüpfte Dataflowentitäten| |        +|
|Standardisiertes Schema/integrierte Common Data Model-Unterstützung|  +|  +|

Weitere Informationen über das Aktivieren von Datenflussworkloads in Premium-Kapazitäten finden Sie im Artikel [Konfigurieren von Workloads in einer Premium-Kapazität](../admin/service-admin-premium-workloads.md). Dataflowworkloads sind in Multi-Geo-Kapazitäten zurzeit nicht verfügbar.

## <a name="summary-of-self-service-data-prep-for-big-data-in-power-bi"></a>Zusammenfassung: Self-Service-Datenaufbereitung für Big Data in Power BI
Wie bereits in diesem Artikel erwähnt, gibt es mehrere Szenarien und Beispiele, wie Sie mit **Dataflows** Ihre Geschäftsdaten besser kontrollieren und daraus schneller Informationen gewinnen können. Mit einem Standarddatenmodell (Schema), das durch das Common Data Model definiert ist, können Dataflows Ihre wertvollen Geschäftsdaten importieren und in kürzester Zeit zum Modellieren und Erstellen von BI-Informationen bereitstellen. All das dauerte bislang Monate, wenn nicht gar länger. 

Durch das Speichern von Geschäftsdaten im standardisierten **Common Data Model**-Format können Ihre BI Pro-Benutzer (oder Entwickler) Apps erstellen, die schnell, einfach und automatisch Visuals und Berichte generieren. Zum Funktionsumfang gehört unter anderem Folgendes:


* Zuordnen von Daten zu Standardentitäten im Common Data Model, um Daten zu vereinheitlichen und mit dem bekannten Schema direkt verwendbare Informationen zu gewinnen
* Erstellen eigener benutzerdefinierter Entitäten, um Daten Ihrer Organisation zu vereinheitlichen 
* Verwenden und Aktualisieren von **externen Daten** im Rahmen eines Dataflows und Importieren dieser Daten zum Gewinnen von Informationen
* Vorstellen von Dataflows für Entwickler


## <a name="next-steps"></a>Weitere Schritte

Dieser Artikel bietet einen Überblick über die Self-Service-Datenaufbereitung für Big Data in Power BI und die vielfältigen Verwendungsoptionen. Die folgenden Artikel gehen näher auf gängige Anwendungsszenarien für Dataflows ein. 

* [Erstellen und Verwenden von Dataflows in Power BI](service-dataflows-create-use.md)
* [Using computed entities on Power BI Premium (Verwenden berechneter Entitäten in Power BI Premium)](service-dataflows-computed-entities-premium.md)
* [Using dataflows with on-premises data sources (Verwenden von Datenflüssen mit lokalen Datenquellen)](service-dataflows-on-premises-gateways.md)
* [Developer resources for Power BI dataflows (Entwicklerressourcen für Power BI-Datenflüsse)](service-dataflows-developer-resources.md)
* [Dataflows und Azure Data Lake-Integration](service-dataflows-azure-data-lake-integration.md)

Weitere Informationen zu Power Query und zur geplanten Aktualisierung finden Sie in den folgenden Artikeln:
* [Abfrageübersicht in Power BI Desktop](desktop-query-overview.md)
* [Konfigurieren geplanter Aktualisierungen](../connect-data/refresh-scheduled-refresh.md)

Weitere Informationen zum Common Data Model finden Sie im Übersichtsartikel:
* [Was ist das Common Data Model?](https://docs.microsoft.com/powerapps/common-data-model/overview)
