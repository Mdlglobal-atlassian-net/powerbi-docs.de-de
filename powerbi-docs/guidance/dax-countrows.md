---
title: 'DAX: Verwenden von COUNTROWS anstelle von COUNT'
description: Leitfaden für die Verwendung der COUNTROWS-Fehlerfunktionen
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/23/2019
ms.author: v-pemyer
ms.openlocfilehash: fd3b50e9016298db8b692d6a2f3549b770f143e8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700660"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: Verwenden von COUNTROWS anstelle von COUNT

Als Datenmodellierer müssen Sie ggf. in manchen Fällen einen DAX-Ausdruck zum Zählen von Tabellenzeilen schreiben. Die Tabelle kann eine Modelltabelle oder ein Ausdruck sein, der eine Tabelle zurückgibt.

Ihre Anforderung kann auf zwei Arten erfüllt werden. Sie können die Funktion [COUNT](/dax/count-function-dax) verwenden, um Spaltenwerte zu zählen, oder Sie können die Funktion [COUNTROWS](/dax/countrows-function-dax) verwenden, um Tabellenzeilen zu zählen. Beide Funktionen erzielen dasselbe Ergebnis, vorausgesetzt, dass die gezählte Spalte keine BLANKs enthält.

Die folgende Measuredefinition stellt ein Beispiel dar. Sie berechnet die Anzahl der **OrderDate**-Spaltenwerte.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

Wenn die Granularität der **Sales**-Tabelle eine Zeile pro Verkaufsauftrag beträgt und die **OrderDate**-Spalte keine BLANKS enthält, gibt das Measure ein korrektes Ergebnis zurück.

Die folgende Measuredefinition ist jedoch eine bessere Lösung.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Es gibt drei Gründe, warum die zweite Measuredefinition besser ist:

- Sie ist effizienter und funktioniert deshalb besser.
- BLANKS, die in einer Spalte der Tabelle enthalten sind, werden nicht berücksichtigt.
- Die Absicht der Formel ist eindeutiger bzw. sogar selbstbeschreibend.

## <a name="recommendation"></a>Empfehlung

Wenn Sie Tabellenzeilen zählen möchten, empfiehlt es sich, immer die COUNTROWS-Funktion zu verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
