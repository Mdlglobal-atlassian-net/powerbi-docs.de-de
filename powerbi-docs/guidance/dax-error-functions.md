---
title: 'DAX: Angemessene Verwendung von Fehlerfunktionen'
description: Leitfaden für die Verwendung der DAX-Fehlerfunktionen
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 4730e835c511153232f79c193de5bbd56d63b963
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74410902"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Angemessene Verwendung von Fehlerfunktionen

Wenn Sie als Datenmodellierer einen DAX-Ausdruck schreiben, der zur Auswertungszeit zu einem Fehler führen könnte, stehen Ihnen zwei hilfreiche DAX-Funktionen zur Verfügung.

- Die Funktion [ISERROR](/dax/iserror-function-dax), die einen einzelnen Ausdruck akzeptiert und TRUE zurückgibt, wenn dieser Ausdruck zu einem Fehler führt.
- Die Funktion [IFERROR](/dax/iferror-function-dax), die zwei Ausdrücke verwendet. Wenn der erste Ausdruck zu einem Fehler führt, wird der Wert für den zweiten Ausdruck zurückgegeben. Es handelt sich hierbei um eine optimierte Implementierung der Schachtelung der ISERROR-Funktion innerhalb einer [IF](/dax/if-function-dax)-Funktion.

Auch wenn diese Funktionen hilfreich sein und zum Schreiben leicht verständlicher Ausdrücke beitragen können, so können sie doch auch die Leistung von Berechnungen erheblich beeinträchtigen. Dies liegt daran, dass diese Funktionen die Anzahl der erforderlichen Scans der Speicher-Engine erhöhen.

Die meisten Auswertungsfehler sind auf unerwartete Leerzeichen oder Nullwerte oder eine ungültige Datentypkonvertierung zurückzuführen.

## <a name="recommendations"></a>Empfehlungen

Es empfiehlt sich, die Funktionen ISERROR und IFERROR zu vermeiden. Setzen Sie stattdessen bei der Entwicklung des Modells und beim Schreiben von Ausdrücken auf Abwehrstrategien. Mögliche Strategien:

- **Sicherstellen, dass Qualitätsdaten in das Modell geladen werden:** Verwenden Sie Power Query-Transformationen, um ungültige oder fehlende Werte zu entfernen oder zu ersetzen und richtige Datentypen festzulegen. Eine Power Query-Transformation kann auch dazu dienen, Zeilen zu filtern, wenn Fehler wie eine ungültige Datenkonvertierung auftreten.

    Die Datenqualität kann auch gesteuert werden, indem die Eigenschaft **Lässt NULL-Werte zu** des Modells auf „Aus“ festgelegt wird, was zum Fehlschlagen der Datenaktualisierung führt, sollten Leerzeichen gefunden werden. Bei Auftreten dieses Fehlers verbleiben die durch eine erfolgreiche Aktualisierung geladenen Daten in den Tabellen.
- **Verwenden der IF-Funktion:** Mit dem logischen Testausdruck der IF-Funktion kann bestimmt werden, ob möglicherweise ein Fehlerergebnis auftritt. Beachten Sie, dass diese Funktion wie die Funktionen ISERROR und IFERROR zu zusätzlichen Scans durch die Speicher-Engine führen kann, aber wahrscheinlich eine bessere Leistung bringt, da kein Fehler ausgelöst werden muss.
- **Verwenden fehlertoleranter Funktionen:** Einige DAX-Funktionen testen und kompensieren Fehlerbedingungen. Mit diesen Funktionen können Sie ein alternatives Ergebnis eingeben, das stattdessen zurückgegeben wird. Die Funktion [DIVIDE](/dax/divide-function-dax) ist ein solches Beispiel. Weitere Anleitungen zu dieser Funktion finden Sie in im Artikel [DAX: Vergleich zwischen der DIVIDE-Funktion und dem Divisionsoperator (/)](dax-divide-function-operator.md).

## <a name="example"></a>Beispiel

Der folgende Measureausdruck testet, ob ein Fehler ausgelöst wird. Er gibt in diesem Fall BLANK zurück (was passiert, wenn Sie an die IF-Funktion keinen Wert übergeben, wenn der Ausdruck FALSE ist).

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

Diese nächste Version des Measureausdrucks wurde durch die Verwendung der IFERROR-Funktion anstelle der Funktionen IF und ISERROR verbessert.

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

Diese endgültige Version des Measureausdrucks führt jedoch zu dem gleichen Ergebnis, ist aber effizienter und eleganter.

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
