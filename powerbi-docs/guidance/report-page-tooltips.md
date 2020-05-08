---
title: Erweitern von Visuals mit QuickInfos für Berichtsseiten
description: Leitfaden zum Arbeiten mit QuickInfos für Berichtsseiten
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 5a6b7bda8bf5e8d80ae8b22a71035f8bc362fb89
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377740"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Erweitern von Visuals mit QuickInfos für Berichtsseiten

Dieser Artikel richtet sich an Berichtsautoren wie Sie, die Power BI-Berichte entwerfen. Er enthält Vorschläge und Empfehlungen für das Erstellen von [QuickInfos für Berichtsseiten](../desktop-tooltips.md).

## <a name="suggestions"></a>Vorschläge

QuickInfos für Berichtsseiten können die Möglichkeiten für die Benutzer von Berichten verbessern. Mithilfe von QuickInfos für Seiten gewinnen die Benutzer eines Berichts schnell und effizient Erkenntnisse aus Visuals. Sie können verschiedenen Berichtsobjekten zugeordnet werden:

- **Visuals:** Sie können alle Visuals einzeln konfigurieren und festlegen, ob die QuickInfo für die Seite angezeigt wird oder nicht. Es besteht also für jedes Visual die Möglichkeit, die QuickInfo standardmäßig (im Visualbereich „Felder“ konfiguriert) oder gar nicht anzeigen zu lassen bzw. eine QuickInfo für eine bestimmte Seite zu verwenden.
- **Visualheader:** Sie können bestimmte Visuals so konfigurieren, dass eine QuickInfo für eine Seite angezeigt wird. Die Benutzer des Berichts können die QuickInfo der Seite anzeigen, wenn sie mit dem Mauszeiger auf das Symbol des Visualheaders zeigen. Stellen Sie sicher, dass Sie die Benutzer über dieses Symbol informieren.

> [!NOTE]
> In einem Berichtsvisual kann nur eine QuickInfo für eine Seite angezeigt werden, wenn die Filter für die QuickInfo der Seite mit dem Design des Visuals kompatibel sind. Beispielsweise ist ein Visual, das nach _product_ gruppiert, mit einer Seite für QuickInfos kompatibel, die nach _product_ filtert.
>
> QuickInfos für eine Seite unterstützen keine Interaktivität. Wenn Sie möchten, dass die Benutzer des Berichts interagieren, erstellen Sie stattdessen eine [Drillthroughseite](../desktop-drillthrough.md).
>
> Power BI-Visuals unterstützen keine QuickInfos für Seiten.

Im Folgenden finden Sie einige empfohlene Entwurfsszenarios:

- [Unterschiedliche Perspektive](#different-perspective)
- [Hinzufügen von Details](#add-detail)
- [Hinzufügen von Hilfe](#add-help)

### <a name="different-perspective"></a>Unterschiedliche Perspektive

Eine QuickInfo für eine Seite kann die gleichen Daten visualisieren wie das Quellvisual. Dies erfolgt mithilfe derselben Visual- und Pivotgruppen oder mithilfe verschiedener Visualtypen. QuickInfos für Seiten können auch andere Filter anwenden als die Filter, die auf das Quellvisual angewendet werden.

Im folgenden Beispiel wird gezeigt, was geschieht, wenn der Benutzer des Berichts mit dem Mauszeiger auf den Wert **EnabledUsers** zeigt. Der Filterkontext für den Wert ist „Yammer“ im November 2018.

![Ein Matrixvisual zeigt in den Zeilen ein Raster mit nach Jahr und Monat gruppierten Werten an. Der Benutzer des Berichts hat mit dem Mauszeiger auf einen einzelnen Wert gezeigt. Eine QuickInfo für die Seite wird angezeigt.](media/report-page-tooltips/suggestion-different-perspective.png)

Eine QuickInfo für die Seite wird angezeigt. Sie stellt ein anderes Datenvisual dar (Liniendiagramm und gruppiertes Säulendiagramm) und wendet einen kontrastierenden Zeitfilter an. Beachten Sie, dass der Filterkontext für den Datenpunkt „November 2018“ ist. Die QuickInfo für die Seite zeigt aber einen _Trend über ein ganzes Jahr hinweg_ an.

### <a name="add-detail"></a>Hinzufügen von Details

Eine QuickInfo für eine Seite kann zusätzliche Details anzeigen und Kontext hinzufügen.

Im folgenden Beispiel wird gezeigt, was geschieht, wenn der Benutzer des Berichts mit dem Mauszeiger auf den Wert **Average of Violation Points** (Durchschnitt der Verstoßpunkte) für die Postleitzahl „98022“ zeigt.

![Ein Tabellenvisual zeigt ein Raster mit Werten an, und die Tabelle enthält drei Spalten. Eine QuickInfo für die Seite wird angezeigt.](media/report-page-tooltips/suggestion-add-details.png)

Eine QuickInfo für die Seite wird angezeigt. Sie zeigt bestimmte Attribute und Statistiken für die Postleitzahl „98022“ an.

### <a name="add-help"></a>Hinzufügen von Hilfe

Visualheader können so konfiguriert werden, dass für diese QuickInfos für Seiten angezeigt werden. Sie können einer QuickInfo für eine Seite Hilfedokumentation hinzufügen, indem Sie umfangreich formatierte Textfelder verwenden. Sie können auch Bilder und Formen hinzufügen.

Interessanterweise können für die QuickInfo für die Seite eines Visualheaders auch Schaltflächen, Bilder, Textfelder und Formen angezeigt werden.

Im folgenden Beispiel wird gezeigt, was geschieht, wenn der Benutzer des Berichts mit dem Mauszeiger auf das [Symbol für den Visualheader](../desktop-visual-elements-for-reports.md) zeigt.

![Der Benutzer eines Berichts hat mit dem Mauszeiger auf das Symbol des Visualheaders gezeigt (Fragezeichen). Es wurde eine umfangreich formatierte QuickInfo angezeigt.](media/report-page-tooltips/suggestion-add-help.png)

Eine QuickInfo für die Seite wird angezeigt. Sie stellt umfangreich formatierten Text in vier Textfeldern und eine Linie dar. Die QuickInfo-Seite bietet Unterstützung, indem sie die Akronyme im Visual beschreibt.

## <a name="recommendations"></a>Empfehlungen

Zur Entwurfszeit des Berichts werden wir die folgenden Vorgehensweisen empfohlen:

- **Seitengröße:** Konfigurieren Sie eine kleine QuickInfo für die Seite. Sie können die integrierte **QuickInfo**-Option (320 Pixel Breite und 240 Pixel Höhe) verwenden. Sie können aber auch benutzerdefinierte Dimensionen festlegen. Achten Sie darauf, dass Sie keine zu große Seitengröße verwenden, da diese sonst die Visuals auf der Quellseite verbergen kann.
- **Seitenansicht:** Legen Sie im Berichts-Designer die Seitenansicht auf **Tatsächliche Größe** fest (die Standardeinstellung für die Seitenansicht lautet **An Seite anpassen**). Auf diese Weise sehen Sie beim Entwerfen die tatsächliche Größe der QuickInfo für die Seite.
- **Stil:** Verwenden Sie beim Entwerfen der QuickInfo für die Seite ggf. dasselbe Design und denselben Stil wie im Bericht. Dadurch haben Benutzer das Gefühl, als würden sie mit dem Bericht arbeiten. Sie können auch einen komplementären Stil für die QuickInfos entwerfen und diesen Stil auf alle QuickInfos für Seiten anwenden.
- **QuickInfo-Filter:** Weisen Sie QuickInfos für Seiten Filter zu, damit Sie beim Entwerfen ein realistisches Ergebnis anzeigen können. Achten Sie darauf, dass Sie diese Filter vor dem Veröffentlichen des Berichts entfernen.
- **Sichtbarkeit der Seite:** Blenden Sie QuickInfo-Seiten immer aus, damit Benutzer nicht direkt zu diesen navigieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Erstellen von QuickInfos basierend auf Berichtsseiten in Power BI Desktop](../desktop-tooltips.md)
- [Anpassen von QuickInfos in Power BI Desktop](../desktop-custom-tooltips.md)
- [Use visual elements to enhance Power BI reports (Erweitern von Power BI-Berichten durch Visualelemente)](../desktop-visual-elements-for-reports.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
