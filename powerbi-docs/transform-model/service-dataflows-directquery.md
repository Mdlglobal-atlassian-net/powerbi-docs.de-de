---
title: Verwenden von DirectQuery mit Dataflows in Power BI (Vorschau)
description: Hier erfahren Sie mehr über die Verwendung von DirectQuery mit Dataflows in Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 9de8c9611b24eaa627b3ddf044f13d36d7b9a3d4
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694571"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Verwenden von DirectQuery mit Dataflows in Power BI (Vorschau)

Sie können DirectQuery verwenden, um eine direkte Verbindung mit Dataflows und daher auch mit Ihrem Dataflow herzustellen, ohne die Daten importieren zu müssen. 

Die Verwendung von DirectQuery mit Dataflows ermöglicht die folgenden Verbesserungen an den Power BI- und Dataflowprozessen:

* **Vermeiden separater Aktualisierungszeitpläne:** DirectQuery stellt eine direkte Verbindung mit einem Dataflow her, weshalb kein Dataset erstellt werden muss. Die Verwendung von DirectQuery mit Ihren Dataflows hat zur Folge, dass Sie keine separaten Aktualisierungszeitpläne für den Dataflow und das Dataset benötigen, um sicherzustellen, dass die Daten synchronisiert werden.

* **Filtern von Daten:** DirectQuery ist nützlich für das Arbeiten an einer gefilterten Ansicht von Daten in einem Dataflow. Wenn Sie Daten filtern und infolgedessen nur einen kleineren Teil der Daten in Ihrem Dataflow verwenden möchten, können Sie DirectQuery (und die Compute-Engine) verwenden, um Dataflowdaten zu filtern und mit der benötigten gefilterten Teilmenge zu arbeiten.


## <a name="using-directquery-for-dataflows"></a>Verwenden von DirectQuery für Dataflows

Die Verwendung von DirectQuery mit Dataflows ist eine Previewfunktion, die ab der Power BI Desktop-Version von Mai 2020 verfügbar ist. 

Für die Verwendung von DirectQuery mit Dataflows gibt es einige Voraussetzungen:

* Der Dataflow muss sich in einem Arbeitsbereich befinden, der für Power BI Premium aktiviert ist.
* Die **Compute-Engine** muss aktiviert sein. Weitere Informationen zur Compute-Engine finden Sie unter [Erweiterte Compute-Engine](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Aktivieren von DirectQuery für Dataflows

Die erweiterte Compute-Engine muss sich im optimierten Zustand befinden, um sicherzustellen, dass Ihr Dataflow für den DirectQuery-Zugriff verfügbar ist. Legen Sie die neue Option **Enhanced compute engine settings** (Erweiterte Compute-Engine-Einstellungen) auf **Optimiert** fest, um DirectQuery für Dataflows zu aktivieren. In der folgenden Abbildung wird die Einstellung ordnungsgemäß aktiviert.

![Aktivieren der erweiterten Compute-Engine für Dataflows](media/service-dataflows-directquery/dataflows-directquery-01.png)

Nachdem Sie diese Einstellung angewendet haben, aktualisieren Sie den Dataflow, damit die Optimierung wirksam wird. 


## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

Es gibt einige bekannte Einschränkungen im Zusammenhang mit DirectQuery und Dataflows, die in der folgenden Liste erläutert werden.

* DirectQuery für Dataflows funktioniert nicht, wenn das **erweiterte Metadatenvorschaufeature** aktiviert ist. Diese Ausnahme sollte in einem künftigen, monatlichen Power BI Desktop-Release entfernt werden.
* Während der Vorschauphase dieses Features können bei einigen Kunden möglicherweise Timeouts oder Leistungsprobleme auftreten, wenn sie DirectQuery mit Dataflows verwenden. Diese Probleme werden während des Zeitraums der Vorschauphase aktiv behandelt.


## <a name="next-steps"></a>Nächste Schritte

Die folgenden Artikel enthalten nützliche Informationen und Szenarien zur Verwendung von Dataflows:

* [Self-Service-Datenaufbereitung mit Dataflows](service-dataflows-overview.md)
* [Using computed entities on Power BI Premium (Verwenden berechneter Entitäten in Power BI Premium)](service-dataflows-computed-entities-premium.md)
* [Using dataflows with on-premises data sources (Verwenden von Datenflüssen mit lokalen Datenquellen)](service-dataflows-on-premises-gateways.md)
* [Developer resources for Power BI dataflows (Entwicklerressourcen für Power BI-Datenflüsse)](service-dataflows-developer-resources.md)
* [Dataflows und Integration in Azure Data Lake (Vorschauversion)](service-dataflows-azure-data-lake-integration.md)

Weitere Informationen zum Common Data Model finden Sie im folgenden Übersichtsartikel:
* [Common Data Model – Übersicht](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Auf GitHub](https://github.com/Microsoft/CDM) erfahren Sie mehr über das Common Data Model-Schema und Entitäten.

Ähnliche Artikel über Power BI Desktop:

* [Herstellen einer Verbindung mit Datasets im Power BI-Dienst über Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Abfrageübersicht in Power BI Desktop](desktop-query-overview.md)

Ähnliche Artikel über den Power BI-Dienst:
* [Konfigurieren geplanter Aktualisierungen](../connect-data/refresh-scheduled-refresh.md)
