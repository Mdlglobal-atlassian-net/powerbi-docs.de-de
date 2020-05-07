---
title: 'DAX: Spalten- und Measureverweise'
description: Anleitung für das Verweisen auf Spalten in Measures in Ihren DAX-Ausdrücken.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75498735"
---
# <a name="dax-column-and-measure-references"></a>DAX: Spalten- und Measureverweise

Als Entwickler eines Datenmodells verweisen Ihre DAX-Ausdrücke auf Spalten und Measures des Modells. Spalten und Measures werden immer Modelltabellen zugeordnet. Diese Zuordnungen unterscheiden sich jedoch. Deshalb finden Sie in diesem Artikel verschiedene Empfehlungen, wie Sie Verweise in Ihren Ausdrücken verwenden.

## <a name="columns"></a>Spalten

Eine Spalte ist ein Objekt auf Tabellenebene. Spaltennamen müssen innerhalb einer Tabelle eindeutig sein. Derselbe Spaltenname kann also mehrfach in Ihrem Modell vorkommen, vorausgesetzt, er wird in verschiedenen Tabellen verwendet. Dazu kommt eine weitere Regel: Der Name einer Spalte darf nicht identisch mit den Namen eines Measures oder einer Hierarchie in derselben Tabelle sein.

Grundsätzlich erzwingt DAX nicht die Verwendung eines _vollqualifizierten_ Verweises auf eine Spalte. Vollqualifiziert bedeutet für einen Namen, dass der Tabellenname dem Spaltennamen vorangeht.

Unten finden Sie ein Beispiel für eine Definition einer berechneten Spalte, für die nur Verweise auf Spaltennamen verwendet werden. Die Spalten **Sales** und **Cost** gehören beide zu einer Tabelle namens **Orders**.

```dax
Profit = [Sales] - [Cost]
```

Dieselbe Definition kann so umgeschrieben werden, dass vollqualifizierte Spaltenverweise verwendet werden.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Manchmal müssen Sie jedoch vollqualifizierte Spaltenverweise verwenden, wenn Power BI Ambiguitäten entdeckt. Sie werden darüber bei der Eingabe einer Formel durch eine rote, wellenförmige Unterstreichung informiert. Auch für einige DAX-Funktionen müssen vollqualifizierte Spalten verwendet werden, z. B. für die DAX-Funktion [LOOKUPVALUE](/dax/lookupvalue-function-dax).

Es wird empfohlen, immer vollqualifizierte Spaltenverweise zu verwenden. Die Gründe dafür finden Sie im Bereich [Empfehlungen](#recommendations).

## <a name="measures"></a>Measures

Ein Measure ist ein Objekt auf Modellebene. Deshalb müssen Measurenamen eindeutig innerhalb eines Modells sein. Im Bereich **Felder** sehen Berichtersteller jedoch, dass jedem Measure eine einzelne Modelltabelle zugeordnet ist. Diese Zuordnung wurde aus kosmetischen Gründen vorgenommen, und Sie können sie konfigurieren, indem Sie für das Measure die Eigenschaft **Hometabelle** festlegen. Weitere Informationen finden Sie unter [Organisieren Ihrer Measures](../desktop-measures.md#organizing-your-measures).

Sie können in Ihren Ausdrücken ein vollqualifiziertes Measure verwenden. Über DAX IntelliSense werden Ihnen sogar Vorschläge gemacht. Das ist jedoch nicht zwingend erforderlich und keine empfohlene Praxis. Wenn Sie die Hometabelle in ein Measure ändern, funktionieren alle Ausdrücke nicht mehr, die einen vollqualifizierten Measureverweis verwenden. In diesem Fall müssen Sie alle defekten Formeln bearbeiten, um den Measureverweis zu entfernen (oder zu aktualisieren).

Deshalb empfehlen wir Ihnen, keine vollqualifizierten Measureverweise zu verwenden. Die Gründe dafür finden Sie im Bereich [Empfehlungen](#recommendations).

## <a name="recommendations"></a>Empfehlungen

Unsere Empfehlungen sind unkompliziert und einfach zu merken:

- Verwenden Sie immer vollqualifizierte Spaltenverweise
- Verwenden Sie nie vollqualifizierte Measureverweise

Dies ist der Grund:

- **Formeleingabe:** Ausdrücke werden akzeptiert, da keine ambigen Verweise aufgelöst werden müssen. Außerdem erfüllen Sie die Anforderungen derjenigen DAX-Funktionen, für die vollqualifizierte Spaltenverweise erforderlich sind.
- **Stabilität:** Ausdrücke funktionieren auch dann noch, wenn Sie die Measureeigenschaft einer Hometabelle ändern.
- **Lesbarkeit:** Ausdrücke sind schnell und einfach zu verstehen. Sie sehen sofort, ob es sich um eine Spalte oder ein Measure handelt, je nachdem, ob ein vollqualifizierter Name verwendet wird oder nicht.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
