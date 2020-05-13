---
title: Verwenden der erweiterten Compute-Engine mit Dataflows
description: Informationen zur Verwendung der erweiterten Compute-Engine in Power BI Premium mit Dataflows
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e126451bf016bf4e9dcce7b7a4df51db9ed20386
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83320513"
---
# <a name="the-enhanced-compute-engine"></a>Erweiterte Compute-Engine

Die verbesserte Compute-Engine in Power BI ermöglicht Power BI Premium-Abonnenten, ihre Kapazität zum Optimieren der Verwendung von Dataflows zu nutzen. Die Verwendung der erweiterten Compute-Engine bietet folgende Vorteile:

* Reduziert drastisch die Aktualisierungszeit, die für ETL-Schritte mit langer Ausführungszeit über berechnete Entitäten benötigt wird, z. B. die Durchführung von *joins*, *distinct*, *filters* und *group by*.
* Durchführen von DirectQuery-Abfragen über Entitäten (im Februar 2020)

In den folgenden Abschnitten wird beschrieben, wie die erweiterte Compute-Engine aktiviert wird, und es werden häufig gestellte Fragen beantwortet.


## <a name="using-the-enhanced-compute-engine"></a>Verwenden der erweiterten Compute-Engine

Die erweiterte Compute-Engine wird über die Seite **Kapazitätseinstellungen** im Power BI-Dienst im Abschnitt **Dataflows** aktiviert. Standardmäßig ist die erweiterte Compute-Engine **Aus**. Zum Einschalten schalten Sie den Umschalter auf **Ein**, wie in der folgenden Abbildung gezeigt, und speichern Sie Ihre Einstellungen. 

![Aktivieren der erweiterten Compute-Engine](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

Nachdem Sie die erweiterte Compute-Engine aktiviert haben, kehren Sie zu den Dataflows zurück und Sie sollten eine Leistungsverbesserung in jeder berechneten Entität sehen, die komplexe Operationen ausführt, z. B. *joins*- oder *group by*-Operationen für Dataflows, die aus bestehenden verknüpften Entitäten für dieselbe Kapazität erstellt wurden. 

Um die Compute-Engine optimal zu nutzen, sollten Sie die ETL-Phase wie folgt in zwei getrennte Dataflows unterteilen:

* **Dataflow 1** – Dieser Dataflow sollte nur alle erforderlichen Daten von einer Datenquelle aufnehmen und in den Dataflow 2 stellen.
* **Dataflow 2** – Führen Sie alle ETL-Operationen in diesem zweiten Dataflow durch, aber stellen Sie sicher, dass Sie auf Dataflow 1 verweisen, der dieselbe Kapazität aufweisen sollte. Vergewissern Sie sich auch, dass Sie faltbare Operationen (filter, group by, distinct, join) zuerst durchführen, bevor Sie eine andere Operation durchführen, um sicherzustellen, dass die Compute-Engine verwendet wird.

## <a name="common-questions-and-answers"></a>Häufig gestellte Fragen und Antworten

**Frage:** Ich habe die erweiterte Compute-Engine aktiviert, aber meine Aktualisierungen sind langsamer. Warum?

**Antwort:** Wenn Sie die erweiterte Compute-Engine aktivieren, gibt es zwei mögliche Erklärungen, die zu langsameren Aktualisierungszeiten führen könnten:

 - Wenn die erweiterte Compute-Engine aktiviert ist, benötigt sie etwas Speicher, um ordnungsgemäß zu funktionieren. Daher wird der für die Durchführung einer Aktualisierung verfügbare Arbeitsspeicher reduziert und somit die Wahrscheinlichkeit erhöht, dass Aktualisierungen in eine Warteschlange gestellt werden, was wiederum die Anzahl der Dataflows reduziert, die gleichzeitig aktualisiert werden können. Um dem entgegenzuwirken, sollten Sie bei der Aktivierung des erweiterten Compute den für Dataflows zugewiesenen Speicher erhöhen, um sicherzustellen, dass der für gleichzeitige Aktualisierungen des Dataflows verfügbare Speicher gleich bleibt.

 - Ein weiterer Grund, warum Sie möglicherweise auf langsamere Aktualisierungen stoßen, ist die Tatsache, dass die Compute Engine nur oberhalb von bestehenden Entitäten arbeitet. Wenn Ihr Dataflow auf eine Datenquelle verweist, die kein Dataflow ist, werden Sie keine Verbesserung sehen. Es gibt keine Leistungssteigerung, da in einigen Big Data-Szenarien das anfängliche Lesen von einer Datenquelle langsamer wäre, da die Daten an die erweiterte Compute-Engine übergeben werden müssen.  

**Frage:** Ich kann den Umschalter der erweiterten Compute-Engine nicht sehen. Warum?

**Antwort:** Die erweiterte Compute-Engine wird schrittweise in Regionen auf der ganzen Welt eingeführt. Wir gehen davon aus, dass bis Ende 2020 alle Regionen unterstützt werden.

**Frage:** Welche Datentypen werden von der Compute-Engine unterstützt?

**Antwort:** Die erweiterte Compute-Engine und Dataflows unterstützen derzeit die folgenden Datentypen. Wenn Ihr Dataflow nicht einen der folgenden Datentypen verwendet, tritt beim Aktualisieren ein Fehler auf:

* Datum/Uhrzeit
* Dezimalzahl
* Text
* Ganze Zahl
* Datum/Uhrzeit/Zone
* TRUE/FALSE
* Datum
* Zeit

## <a name="next-steps"></a>Nächste Schritte

Dieser Artikel enthält Informationen über die Verwendung der erweiterten Compute-Engine für Dataflows. Die folgenden Artikel können ebenfalls hilfreich sein:

* [Self-Service-Datenaufbereitung mit Dataflows](service-dataflows-overview.md)
* [Erstellen und Verwenden von Dataflows in Power BI](service-dataflows-create-use.md)
* [Using computed entities on Power BI Premium (Verwenden berechneter Entitäten in Power BI Premium)](service-dataflows-computed-entities-premium.md)
* [Developer resources for Power BI dataflows (Entwicklerressourcen für Power BI-Datenflüsse)](service-dataflows-developer-resources.md)

Weitere Informationen zu Power Query und zur geplanten Aktualisierung finden Sie in den folgenden Artikeln:
* [Abfrageübersicht in Power BI Desktop](desktop-query-overview.md)
* [Konfigurieren geplanter Aktualisierungen](../connect-data/refresh-scheduled-refresh.md)

Weitere Informationen zum Common Data Model finden Sie im folgenden Übersichtsartikel:
* [Was ist das Common Data Model?](https://docs.microsoft.com/powerapps/common-data-model/overview)
