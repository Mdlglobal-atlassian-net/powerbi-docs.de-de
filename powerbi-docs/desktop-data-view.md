---
title: Datensicht in Power BI Desktop
description: Datensicht in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 1fee95bbfb790a1c61d82131579c8fb43980ca05
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866723"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Arbeiten mit der Datenansicht in Power BI Desktop

Die *Datenansicht* hilft Ihnen, Daten in einem *Power BI Desktop-Modell* zu überprüfen, zu untersuchen und zu verstehen. Sie unterscheidet sich von der Anzeige von Tabellen, Spalten und Daten im *Power Query-Editor*. In der Datenansicht sehen Sie die Daten, *nachdem* sie in das Modell geladen wurden.

> [!NOTE]
> Da in der Datenansicht Daten angezeigt werden, nachdem sie in das Modell geladen wurden, ist das Datenansicht-Symbol nicht sichtbar, wenn alle Datenquellen auf DirectQuery basieren. 

Wenn Sie Ihre Daten modellieren, möchten Sie möglicherweise sehen, was tatsächlich in einer Tabelle oder Spalte vorhanden ist, ohne ein Visual im Berichtszeichenbereich zu erstellen. Möglicherweise möchten Sie auch bis auf Zeilenebene Einblick erhalten. Dies Funktion ist besonders nützlich, wenn Sie Measures und berechnete Spalten erstellen oder einen Datentyp/eine Datenkategorie identifizieren müssen.

Sehen Sie sich nun einige der Elemente in der Datenansicht näher an.

![Datensicht in Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Symbol für Datenansicht** Mit einem Klick auf dieses Symbol gelangen Sie zur Datenansicht.

2. **Datenraster** In diesem Bereich wird die ausgewählte Tabelle mit allen ihren Spalten und Zeilen angezeigt. Spalten, die aus der Ansicht *Bericht* ausgeblendet wurden, sind ausgegraut. Sie können mit der rechten Maustaste auf eine Spalte klicken, um Optionen anzuzeigen.

3. **Menüband für die Modellierung** Hier können Sie Beziehungen verwalten, Berechnungen erstellen und den Datentyp, das Format und die Datenkategorie einer Spalte ändern.

4. **Bearbeitungsleiste** Hier können Sie DAX-Formeln (Data Analysis Expression) für Measures und berechnete Spalten eingeben.

5. **Suchen** Hier können Sie nach einer Tabelle oder Spalte im Modell suchen.

6. **Liste „Felder“** Hier können Sie eine Tabelle oder Spalte auswählen, die im Datenraster angezeigt werden soll.

## <a name="filtering-in-data-view"></a>Filtern in der Datensicht

Sie können Daten in der Datenansicht auch filtern und sortieren. In jeder Spalte wird ein Symbol angezeigt, das die Sortierreihenfolge angibt (bei aktivierter Sortierung).

![Sortieren und Filtern in der Datensicht in Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Sie können einzelne Werte filtern oder erweiterte Filter auf Grundlage der Daten in der Spalte verwenden.

> [!NOTE]
> Wenn ein Power BI-Modell in einer anderen Kultur als der aktuellen Benutzeroberfläche erstellt wird, wird das Suchfeld in der Benutzeroberfläche der Datenansicht nur für Textfelder angezeigt. Dies gilt beispielsweise für ein Modell, das in der Sprache Englisch (USA) erstellt wurde und das Sie sich auf Spanisch anzeigen lassen.


## <a name="next-steps"></a>Nächste Schritte

Mit Power BI Desktop können Sie vielfältige Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in den folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datentypen in Power BI Desktop](desktop-data-types.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Allgemeine Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)
