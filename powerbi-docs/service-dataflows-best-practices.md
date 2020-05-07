---
title: Bewährte Methoden für Power BI-Dataflows
description: Bewährte Methoden für Power BI-Dataflows
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4bbc8b71455d01405854304dd4b889f664ce8575
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877290"
---
# <a name="dataflows-best-practice"></a>Bewährte Methoden für Dataflows

Dieser Artikel beschreibt bewährte Methoden für das Entwerfen von Dataflows in Power BI. Mithilfe dieser Anleitung können Sie erfahren, wie Sie Dataflows erstellen, und diese Methoden auf Ihre eigenen Dataflows anwenden.

> [!NOTE]
> Die Empfehlungen in diesem Artikel sind Richtlinien. Für jede bewährte Methode in diesem Artikel kann es berechtigte Gründe geben, von dieser Anleitung abzuweichen. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Aufteilen der Erfassung und Transformation für die Verwendung der erweiterten Compute-Engine

Beim Erstellen von Dataflows neigen Sie vielleicht dazu, einen einzelnen Dataflow mit allen Entitäten, Transformationen, Joins und Verbesserungen an einem Ort zu erstellen. Bei kleineren Datasets kann ein einzelner Dataflow effektiv sein. Bei größeren Datenvolumen kann es jedoch vorkommen, dass bei der Ausführung von Joins oder bestimmten Transformationen manchmal Drosselungs- oder Arbeitsspeicherlimits auftreten. Um diese Probleme zu beheben, wurde eine erweiterte Engine für Power BI Premium-Benutzer veröffentlicht, die für viel größere Datenvolumen skaliert ist. Die erweiterte Compute-Engine funktioniert nur mit verknüpften oder berechneten Entitäten, sodass die erweiterte Engine für das Erstellen eines separaten Dataflows für die Erfassung und eines verknüpften Dataflows zum Ausführen aller komplexen Zusammenführungen und Transformationen vorteilhaft sein kann.

Das Aufteilen von Dataflows ist auch nützlich für die Diagnose und das Debuggen von Aktualisierungsproblemen, insbesondere beim Arbeiten mit Quellen mit Drosselungslimits.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Ausführen von Aktionen, die die erweiterte Compute-Engine verwenden können

Stellen Sie sicher, dass Sie die erweiterte Compute-Engine nutzen, indem Sie sicherstellen, dass Sie Joins und Filtertransformationen zuerst in einer berechneten Entität ausführen, bevor Sie andere Transformationstypen ausführen.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Aufteilen von Dataflows beim Herstellen einer Verbindung mit SharePoint

Wenn Sie mit SharePoint arbeiten und eine Verbindung mit mehreren Dateien herstellen, bemerken Sie möglicherweise sporadische Fehler. SharePoint drosselt Anforderungen, um beständige Zuverlässigkeit und Reaktionsfähigkeit sicherzustellen. Wenn Sie von SharePoint aus Verbindungen mit Excel-Dateien herstellen, sind Sie daher möglicherweise geneigt, alle Dateien in einem einzelnen Dataflow herunterzuladen. Wenn Sie viele Dateien (mehr als 20) herunterladen, erstellen Sie mindestens zwei Dataflows, um die Aktualisierungslast aufzuteilen und die SharePoint-Drosselung zu überwinden.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Vermeiden eines Aktualisierungszeitplans für verknüpfte Entitäten innerhalb desselben Arbeitsbereichs

Wenn Sie regelmäßig von Ihren Dataflows ausgesperrt werden, die verknüpfte Entitäten enthalten, kann dies daran liegen, dass entsprechende abhängige Dataflows innerhalb desselben Arbeitsbereichs während der Dataflowaktualisierung gesperrt werden. Diese Sperrung sorgt für Transaktionsgenauigkeit und stellt sicher, dass beide Dataflows erfolgreich aktualisiert werden, kann Sie jedoch an der Bearbeitung hindern. 

Wenn Sie einen separaten Zeitplan für den verknüpften Dataflow einrichten, können Dataflows unnötig aktualisiert werden, sodass Sie an der Bearbeitung des Dataflows gehindert werden. Es gibt zwei Empfehlungen, um dieses Problem zu vermeiden: 

* Vermeiden der Festlegung eines Aktualisierungszeitplan für einen verknüpften Dataflow im gleichen Arbeitsbereich wie der Quelldataflow
* Wenn Sie einen Aktualisierungszeitplan separat konfigurieren und das Sperrverhalten vermeiden möchten, separieren Sie den Dataflow in einem separaten Arbeitsbereich.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Erstellen eines separaten Arbeitsbereichs für Erfassung und Transformation

Um vielen Benutzern Zugriff auf zugrunde liegende Dataflowdaten zu bieten, ohne den Zugriff auf die Rohdaten des zugrunde liegenden Quellsystems zuzulassen, erstellen Sie einen separaten Arbeitsbereich, der alle Daten enthält, die Sie freigeben müssen, und weisen Sie Berechtigungen zu. Individuelle Dataflowberechtigungen werden zurzeit nicht unterstützt.

### <a name="ensure-capacity-is-in-the-same-region"></a>Sicherstellen, dass sich die Kapazität in derselben Region befindet

Dataflows unterstützen derzeit keine Multi-Geo-Regionen. Die Premium-Kapazität muss in derselben Region erstellt werden, in der sich auch Ihr Power BI-Mandant befindet.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Trennen lokaler Quellen von Cloudquellen

Zusätzlich zu den zuvor beschriebenen bewährten Methoden können Sie einen separaten Dataflow für jeden Quelltyp erstellen, z. B. lokal, Cloud, SQL Server, Spark, Dynamics usw. Sie sollten Ihren Dataflow unbedingt nach dem Datenquellentyp aufteilen. Eine solche Trennung nach Quelltyp erleichtert eine schnelle Problembehandlung und vermeidet interne Grenzen beim Aktualisieren Ihrer Dataflows.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Separieren von Dataflows in einer separaten Kapazität

Wenn Sie Drosselungslimits feststellen oder regelmäßige Ausfälle bei Ihren Dataflows aufgrund von Arbeitsspeicherlimits bei Ihrer Kapazität auftreten, erwägen Sie, die Dataflows zu trennen oder die Premium-Kapazität für zusätzlichen Arbeitsspeicher zentral hochzuskalieren.

## <a name="next-steps"></a>Weitere Schritte

Dieser Artikel enthält Informationen zu bewährten Methoden für Dataflows. Weitere Informationen zu Dataflows finden Sie in den folgenden Artikeln:

* [Self-Service-Datenaufbereitung in Power BI (Vorschau)](service-dataflows-overview.md)
* [Erstellen und Verwenden von Dataflows in Power BI](service-dataflows-create-use.md)
* [Using computed entities on Power BI Premium (Verwenden berechneter Entitäten in Power BI Premium)](service-dataflows-computed-entities-premium.md)
* [Using dataflows with on-premises data sources (Verwenden von Datenflüssen mit lokalen Datenquellen)](service-dataflows-on-premises-gateways.md)

Informationen zur Entwicklung eines CDM (Common Data Modell) sowie Tutorials finden Sie in den folgenden Artikeln:
* [Was ist das Common Data Model?](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM folders (CDM-Ordner)](https://go.microsoft.com/fwlink/?linkid=2045304)
* [The metadata file (model.json) for the Common Data Model (Die Metadatendatei (model.json) des CDM)](https://go.microsoft.com/fwlink/?linkid=2045521)


Weitere Informationen zu Power Query und zur geplanten Aktualisierung finden Sie in den folgenden Artikeln:
* [Abfrageübersicht in Power BI Desktop](desktop-query-overview.md)
* [Konfigurieren geplanter Aktualisierungen](refresh-scheduled-refresh.md)
