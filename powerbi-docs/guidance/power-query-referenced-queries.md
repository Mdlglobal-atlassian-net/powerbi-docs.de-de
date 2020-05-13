---
title: Verweis auf Power Query-Abfragen
description: Leitfaden für Verweise auf Power Query-Abfragen.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 242f1e44e3314af900d9f4d4e4fb7380b28b4103
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278673"
---
# <a name="referencing-power-query-queries"></a>Verweis auf Power Query-Abfragen

Dieser Artikel ist an Modellierer von Daten gerichtet, die mit Power BI Desktop arbeiten. Der Artikel bietet einen Leitfaden für die Definition von Power Query-Abfragen, die auf andere Abfragen verweisen.

Das bedeutet Folgendes: _Wenn eine Abfrage auf eine zweite Abfrage verweist, werden die Schritte in der zweiten Abfrage praktisch mit den Schritten in der ersten Abfrage kombiniert und vor diesen ausgeführt._

Ein Beispiel mit mehreren Abfragen: **Abfrage 1** fragt Daten aus einem Webdienst ab, die Funktion zum Laden der Daten ist deaktiviert. **Abfrage 2**, **Abfrage 3** und **Abfrage 4** verweisen alle auf **Abfrage 1**, und ihre Ausgaben werden in das Datenmodell geladen.

![Ansicht der Abfrageabhängigkeiten, gezeigt werden die im vorherigen Absatz beschriebenen Abfragen.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Bei der Aktualisierung des Datenmodells wird häufig angenommen, dass Power Query das Ergebnis von **Abfrage 1** abruft und dieses von den Abfragen, auf die verwiesen wurde, wiederverwendet wird. Diese Annahme ist falsch. Tatsächlich führt Power Query **Abfrage 2**, **Abfrage 3** und **Abfrage 4** getrennt aus.

Sie können sich das Procedere so vorstellen, dass die Schritte von **Abfrage 1** in **Abfrage 2** eingebettet sind. Das Gleiche gilt auch für **Abfrage 3** und **Abfrage 4**. Die folgende Abbildung verdeutlicht, wie die Abfragen ausgeführt werden.

![Eine modifizierte Ansicht der Abfrageabhängigkeiten, gezeigt werden Abfrage 2, Abfrage 3 und Abfrage 4. Abfrage 1 ist in jede der drei Abfragen eingebettet.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Abfrage 1** wird drei Mal ausgeführt. Die mehrfache Ausführung kann zu einer verlangsamten Datenaktualisierung führen und sich negativ auf die Datenquelle auswirken.

Die Verwendung der Funktion [Table.Buffer](/powerquery-m/table-buffer) in **Abfrage 1** verhindert nicht den zusätzlichen Datenabruf. Diese Funktion puffert eine Tabelle in den Arbeitsspeicher. Die gepufferte Tabelle kann nur innerhalb derselben Abfrageausführung verwendet werden. Für das Beispiel gilt also: Wenn **Abfrage 1** bei der Ausführung von **Abfrage 2** gepuffert wird, können die gepufferten Daten bei der Ausführung von **Abfrage 3** und **Abfrage 4** nicht verwendet werden. Diese beiden Abfragen puffern die Daten selbst noch zwei weitere Male. (Dies könnte die negative Leistung weiter verschlimmern, weil die Tabelle bei jeder verweisenden Abfrage gepuffert wird.)

> [!NOTE]
> Die Cachingarchitektur von Power Query ist sehr komplex und nicht das Thema dieses Artikels. Power Query kann aus einer Datenquelle abgerufene Daten zwischenspeichern. Wenn jedoch eine Abfrage ausgeführt wird, werden die Daten möglicherweise mehrmals aus der Datenquelle abgerufen.

## <a name="recommendations"></a>Empfehlungen

Im Allgemeinen wird empfohlen, auf Abfragen zu verweisen, um eine Duplizierung der Logik in Ihren Abfragen zu vermeiden. Dieser Entwurf kann jedoch, wie in diesem Artikel beschrieben, zu einer verlangsamten Aktualisierung von Daten führen und Datenquellen überlasten.

Daher empfehlen wir, stattdessen einen [Dataflow](../transform-model/service-dataflows-overview.md) zu erstellen. Die Verwendung eines Dataflows kann die Datenaktualisierung beschleunigen und die negativen Auswirkungen auf Ihre Datenquellen reduzieren.

Sie können den Dataflow so entwerfen, dass die Quelldaten und Transformationen gekapselt werden. Da es sich bei einem Dataflow um einen persistenten Datenspeicher im Power BI-Dienst handelt, erfolgen Datenabrufe schnell. Daher lassen sich die Datenaktualisierungen beschleunigen, auch wenn verweisende Abfragen zu mehreren Anforderungen für den Dataflow führen.

Wenn **Abfrage 1** im Beispiel als Dataflowentität entworfen wird, kann sie von **Abfrage 2**, **Abfrage 3** und **Abfrage 4** als Datenquelle verwendet werden. Bei diesem Entwurf wird die Entität, die als Quelle für **Abfrage 1** dient, nur einmal ausgewertet.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Self-Service-Datenaufbereitung in Power BI](../transform-model/service-dataflows-overview.md)
- [Erstellen und Verwenden von Dataflows in Power BI](../transform-model/service-dataflows-create-use.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
