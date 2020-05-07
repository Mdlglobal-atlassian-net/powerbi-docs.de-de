---
title: 'DAX: Vermeiden der Konvertierung von BLANKs in Werte'
description: Leitfaden zur Konvertierung von BLANKs in Werte
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74700384"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Vermeiden der Konvertierung von BLANKs in Werte

Als Datenmodellierer können Sie beim Schreiben von Measureausdrücken auf Fälle stoßen, in denen kein sinnvoller Wert zurückgegeben werden kann. Dann ist es möglicherweise verlockend, einen Wert wie z.B. 0 (null) zurückzugeben. Es wird empfohlen, sorgfältig zu prüfen, ob dieser Entwurf effizient und praktisch ist.

Beachten Sie die folgende Measuredefinition, die BLANK-Ergebnisse explizit in 0 (null) konvertiert.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Betrachten Sie eine andere Measuredefinition, die auch die BLANK-Ergebnisse in 0 konvertiert.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

Die Funktion [DIVIDE](/dax/divide-function-dax) teilt das Measure **Profit** durch das Measure **Sales**. Wenn das Ergebnis 0 (null) oder BLANK ist, wird das dritte Argument – das alternative Ergebnis (das optional ist) – zurückgegeben. Da in diesem Beispiel 0 als alternatives Ergebnis übergeben wird, ist sichergestellt, dass das Measure immer einen Wert zurückgibt.

Diese Measureentwürfe sind ineffizient und führen zu schlechten Berichtsentwürfen.

Wenn sie einem Berichtsvisual hinzugefügt werden, versucht Power BI, alle Gruppierungen innerhalb des Filterkontexts abzurufen. Durch das Auswerten und Abrufen umfangreicher Abfrageergebnisse wird das Rendern von Berichten häufig verlangsamt. Jedes Beispielmeasure wandelt eine Sparseberechnung in eine Denseberechnung um und zwingt Power BI, mehr Arbeitsspeicher als nötig zu verwenden.

Außerdem wird es durch zu viele Gruppierungen für die Berichtsbenutzer oft zu unübersichtlich.

Sehen Sie sich an, was geschieht, wenn das Measure **Profit Margin** zu einem Tabellenvisual hinzugefügt wird, das nach Kunden gruppiert ist.

![Ein Tabellenvisual mit drei Spalten: „Customer“ (Kunde), „Sales“ (Umsatz) und „Profit Margin“ (Gewinnspanne). Es sind etwa zehn Datenzeilen zu sehen, aber die vertikale Scrollleiste zeigt an, dass es noch viel mehr Zeilen gibt, die angezeigt werden können. In der Spalte „Sales“ werden keine Werte angezeigt. In der Spalte „Profit Margin“ wird nur 0 angezeigt.](media/dax-avoid-converting-blank/table-visual-poor.png)

Das Tabellenvisual zeigt eine überwältigende Anzahl von Zeilen an. (Es gibt tatsächlich 18.484 Kunden im Modell, sodass versucht wird, sie alle in der Tabelle anzuzeigen.) Beachten Sie, dass die betrachteten Kunden keine Umsätze erzielt haben. Da das Measure **Profit Margin** jedoch immer einen Wert liefert, werden sie angezeigt.

> [!NOTE]
> Wenn zu viele Datenpunkte in einem Visual angezeigt werden müssen, kann Power BI Datenreduktionsstrategien anwenden, um umfangreiche Abfrageergebnisse zu entfernen oder zusammenzufassen. Weitere Informationen finden Sie unter [Datenpunktgrenzwerte und Strategien nach Visualtyp](../visuals/power-bi-data-points.md).

Nun sehen Sie, was geschieht, wenn die Definition des Measures **Profit Margin** verbessert wird. Es wird nun nur dann ein Wert zurückgegeben, wenn das Measure **Sales** nicht BLANK (oder 0 (null)) ist.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

Das Tabellenvisual zeigt nun nur noch Kunden an, die innerhalb des aktuellen Filterkontexts Umsätze getätigt haben. Das verbesserte Measure führt zu einer effizienteren und praktischeren Erfahrung für die Berichtsbenutzer.

![Das gleiche Tabellenvisual zeigt nun vier Datenzeilen an. Jede Zeile bezieht sich auf einen Kunden mit einem Sales-Wert, und die Werte in „Profit Margin“ sind ungleich 0 (null).](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Bei Bedarf können Sie das Visual so konfigurieren, dass alle Gruppen (die Werte oder BLANK zurückgeben) im Filterkontext angezeigt werden, indem Sie die Option [Elemente ohne Daten anzeigen](../desktop-show-items-no-data.md) aktivieren.

## <a name="recommendation"></a>Empfehlung

Es wird empfohlen, dass Measures BLANK zurückgeben, wenn kein sinnvoller Wert zurückgegeben werden kann.

Dieser Entwurfsansatz ist effizient und ermöglicht Power BI, Berichte schneller zu rendern. Zudem ist ein Vorteil der Rückgabe von BLANK, dass Berichtsvisuals Gruppierungen standardmäßig löschen, wenn Zusammenfassungen leer (BLANK) sind.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
