---
title: Leitfaden für zusammengesetzte Modelle in Power BI Desktop
description: Leitfaden zum Entwickeln zusammengesetzter Modelle
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 528fc40427a1cb242d9154028d1a7c6617c8a14e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279683"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Leitfaden für zusammengesetzte Modelle in Power BI Desktop

Dieser Artikel richtet sich an Datenmodellierer, die zusammengesetzte Modelle für Power BI entwickeln. Er beschreibt Anwendungsfälle zusammengesetzter Modelle und bietet Ratschläge für Entwürfe. Hauptziel dieses Leitfadens ist es, Ihnen dabei zu helfen, festzulegen, ob ein zusammengesetztes Modell für Ihre Lösung geeignet ist. Wenn dies der Fall ist, hilft Ihnen dieser Artikel auch beim Entwerfen eines optimalen Modells.

> [!NOTE]
> Dieser Artikel enthält keine grundlegenden Informationen zu zusammengesetzten Modellen. Wenn Sie nicht vollständig mit zusammengesetzten Modellen vertraut sind, sollten Sie zunächst den Artikel [Verwenden zusammengesetzter Modelle in Power BI Desktop](../transform-model/desktop-composite-models.md) lesen.
>
> Da zusammengesetzte Modelle aus mindestens einer DirectQuery-Quelle bestehen, ist es auch wichtig, dass Sie mit [Modellbeziehungen](../transform-model/desktop-relationships-understand.md), [DirectQuery-Modellen](../connect-data/desktop-directquery-about.md) und dem [Designleitfaden für DirectQuery-Modelle](directquery-model-guidance.md) vertraut sind.

## <a name="composite-model-use-cases"></a>Anwendungsfälle für zusammengesetzte Modelle

Wenn möglich, sollten Sie ein Modell im Importmodus entwickeln. Er bietet größtmögliche Flexibilität für Entwürfe und die beste Leistung.

Allerdings können Herausforderungen, die im Zusammenhang mit großen Datenmengen oder der Berichterstellung über Quasi-Echtzeitdaten stehen, nicht durch Importmodelle gelöst werden. In diesen Fällen würde sich ein DirectQuery-Modell anbieten, vorausgesetzt, Ihre Daten sind in einer einzelnen Datenquelle gespeichert, [die vom DirectQuery-Modus unterstützt wird](../connect-data/power-bi-data-sources.md).

Ein zusammengesetztes Modell wäre auch für folgende Situationen gut geeignet:

- Sie haben bereits ein DirectQuery-Modell, möchten aber noch bessere Leistung. Ein zusammengesetztes Modell ist leistungsfähiger, weil für jede Tabelle der passende Speicher konfiguriert werden kann. Sie können auch [Aggregationen](../transform-model/desktop-aggregations.md) hinzufügen. Beide Optimierungen werden weiter unten in diesem Artikel erläutert.
- Sie möchten ein DirectQuery-Modell mit zusätzlichen Daten kombinieren, die in das Modell importiert werden müssen. Importierte Daten können aus einer anderen Datenquelle oder aus berechneten Tabellen geladen werden.
- Sie möchten zwei oder mehr DirectQuery-Datenquellen in einem einzelnen Modell kombinieren.

> [!NOTE]
> In zusammengesetzten Modellen ist es nicht möglich, Liveverbindungen und DirectQuery-Analysedatenbanken miteinander zu kombinieren. Zu Liveverbindungen zählen [extern gehostete Modelle](../connect-data/service-datasets-understand.md#external-hosted-models) und Power BI Datasets. Zu DirectQuery-Analysedatenbanken werden auch SAP Business Warehouse und SAP HANA gezählt.

## <a name="optimize-model-design"></a>Optimieren des Modellentwurfs

Sie können ein zusammengesetztes Modell optimieren, indem Sie [Speichermodi](../transform-model/desktop-storage-mode.md) für Tabellen konfigurieren und [Aggregationen](../transform-model/desktop-aggregations.md) hinzufügen.

### <a name="table-storage-mode"></a>Tabellenspeichermodus

In einem zusammengesetzten Modell können Sie den Speichermodus jeder Tabelle konfigurieren, mit Ausnahme berechneter Tabellen:

- **DirectQuery**: Dieser Modus empfiehlt sich für Tabellen, die große Datenmengen enthalten oder in Quasi-Echtzeit Ergebnisse liefern müssen. Daten werden nie in diese Tabellen importiert. In der Regel haben diese Faktentabellen und werden für Zusammenfassungen verwendet.
- **Import**: Dieser Modus empfiehlt sich für Dimensionstabellen, d. h. für Tabellen, mit deren Hilfe gefiltert und gruppiert wird. Tatsächlich ist dieser Modus die einzige Option für Tabellen, die auf Quellen basieren, die nicht vom DirectQuery-Modus unterstützt werden. Berechnete Tabellen haben immer diesen Modus.
- **Dual**: Diesen Modus sollten Sie für Tabellen des Typs „Dimension“ verwenden, wenn die Chance besteht, dass sie zusammen mit DirectQuery-Tabellen des Typs „Fakt“ aus derselben Quelle abgefragt werden.

Beim Abfragen eines zusammengesetzten Modells durch Power BI sind mehrere Szenarios denkbar:

- **Es werden nur Tabellen mit dem Modus „Import“ oder „Dual“ abgefragt:** Alle Daten werden aus dem Modellcache abgerufen. Dadurch wird die schnellstmögliche Leistung erzielt. Dieses Szenario kommt häufig bei Tabellen des Typs „Dimension“ vor, die mit Filtern oder Datenschnittvisuals abgefragt werden.
- **Es werden nur Tabellen mit dem Modus „Dual“ oder DirectQuery-Tabellen abgefragt, die aus derselben Quelle stammen:** Alle Daten werden abgerufen, indem eine oder mehrere native Abfragen an die DirectQuery-Quelle gesendet werden. Dadurch wird die schnellstmögliche Leistung erzielt, insbesondere wenn in den Quelltabellen geeignete Indizes vorhanden sind. Dieses Szenario wird häufig bei Abfragen verwendet, bei denen Tabellen, die den Typ „Dimension“ und den Modus „Dual“ haben, mit DirectQuery-Tabellen des Typs „Fakt“ verknüpft werden. Diese Abfragen haben eine _intra-island_-Beziehung (Beziehungen innerhalb der Dateninsel), d. h., alle 1:1- oder 1:n-Beziehungen werden als [starke Beziehungen](../transform-model/desktop-relationships-understand.md#strong-relationships) bewertet.
- **Alle anderen Abfragen:** Diese Abfragen umfassen inselübergreifende Beziehungen. Der Grund hierfür ist entweder, dass eine Tabelle mit dem Modus „Import“ mit einer DirectQuery-Tabelle verknüpft ist, oder dass eine Tabelle mit dem Modus „Dual“ mit einer DirectQuery-Tabelle aus einer anderen Quelle verknüpft ist und sich deshalb wie eine Tabelle mit dem Modus „Import“ verhält. Alle Beziehungen werden als [schwache Beziehungen](../transform-model/desktop-relationships-understand.md#weak-relationships) bewertet. Das bedeutet auch, dass Gruppierungen, die auf nicht mit DirectQuery erstellte Tabellen angewendet werden, als virtuelle Tabelle an die DirectQuery-Quelle gesendet werden müssen. In diesem Fall kann die native Abfrage ineffizient sein, insbesondere bei großen Gruppierungssätzen. Außerdem besteht die Möglichkeit, dass in der nativen Abfrage sensible Daten angezeigt werden.

Zusammenfassend empfiehlt sich Folgendes:

- Überlegen Sie gut, ob ein zusammengesetztes Modell die richtige Lösung ist. Es erlaubt zwar die Integration verschiedener Datenquellen auf Modellebene, macht aber auch das Entwerfen komplizierter, was Konsequenzen haben kann.
- Legen Sie den Speichermodus auf **DirectQuery** fest, wenn eine Tabelle den Typ „Fakt“ hat und in ihr große Datenmengen gespeichert sind, oder sie in Quasi-Echtzeit Ergebnisse liefern muss.
- Legen Sie den Speichermodus auf **Dual** fest, wenn eine Tabelle den Typ "Dimension" hat und sie zusammen mit **DirectQuery**-Tabellen des Typs „Fakt“ abgefragt wird, die aus derselben Quelle stammen.
- Konfigurieren Sie die Aktualisierungshäufigkeiten so, dass der Modellcache für Tabellen mit dem Modus „Dual“ (und für alle abhängigen, kalkulierten Tabellen) und die Quelldatenbanken synchron sind.
- Bemühen Sie sich um datenquellenübergreifende Datenintegrität (einschließlich Modellcache) – durch schwache Beziehungen werden Reihen eliminiert, wenn verknüpfte Spaltenwerte nicht übereinstimmen.
- Optimieren Sie DirectQuery-Datenquellen mit geeigneten Indizes für effiziente Joins, Filter, Gruppierungen.
- Laden Sie sensible Daten nicht in Tabellen mit dem Modus „Import“ oder „Dual“, wenn das Risiko besteht, dass eine native Abfrage abgefangen wird. Weitere Informationen hierzu finden Sie unter [Verwenden zusammengesetzter Modelle in Power BI Desktop (Abschnitt „Folgen für die Sicherheit“)](../transform-model/desktop-composite-models.md#security-implications).

### <a name="aggregations"></a>Aggregationen

Sie können den DirectQuery-Tabellen in Ihrem zusammengesetzten Modell Aggregationen hinzufügen. Aggregationen werden im Modell zwischengespeichert. Deshalb verhalten sie sich wie Tabellen mit dem Modus „Import“, können aber nicht wie Modelltabellen verwendet werden. Ihr Zweck besteht darin, die Leistung bei Abfragen mit höherer Granularität zu verbessern. Weitere Informationen finden Sie unter [Aggregationen in Power BI Desktop](../transform-model/desktop-aggregations.md).

Eine Aggregationstabelle sollte dieser Grundregel folgen: Die Zeilenanzahl muss mindestens um den Faktor 10 kleiner sein als in der zugrunde liegenden Tabelle. Wenn die zugrunde liegende Tabelle z. B. 1 Milliarde Zeilen hat, sollte die Aggregationstabelle nicht länger als 100 Millionen Zeilen sein. Mit dieser Regel stellen Sie sicher, dass Sie im Gegenzug für die beim Erstellen und Verwalten einer Aggregationstabelle entstehenden Kosten auch eine angemessene Leistungssteigerung erhalten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Verwenden zusammengesetzter Modelle in Power BI Desktop](../transform-model/desktop-composite-models.md)
- [Modellieren von Beziehungen in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [DirectQuery-Modelle in Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [Verwenden von DirectQuery in Power BI Desktop](../connect-data/desktop-use-directquery.md)
- [Problembehandlung für das DirectQuery-Model in Power BI Desktop](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI-Datenquellen](../connect-data/power-bi-data-sources.md)
- [Speichermodus in Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Aggregationen in Power BI Desktop](../transform-model/desktop-aggregations.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com)
