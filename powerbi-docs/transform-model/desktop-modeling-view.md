---
title: Verwenden der Modellierungsansicht in Power BI Desktop
description: Verwenden der Modellierungsansicht zur Anzeige komplexer Datasets in einem visuellen Format in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 27d601da2a3ef922c75aee6f52011ac22ca26336
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83280332"
---
# <a name="work-with-modeling-view-in-power-bi-desktop"></a>Arbeiten mit der Modellierungsansicht in Power BI Desktop

Die **Modellierungsansicht** in **Power BI Desktop** erlaubt es Ihnen, komplexe Datasets mit vielen Tabellen anzuzeigen und mit diesen zu arbeiten.


## <a name="using-modeling-view"></a>Verwenden der Modellierungsansicht

Um auf die Modellierungsansicht zuzugreifen, wählen Sie das Symbol „Modellierungsansicht“ aus, das im linken Bereich von **Power BI Desktop** angezeigt wird, siehe nachstehende Abbildung.

![Symbol „Modellierungsansicht“ in Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Erstellen separater Diagramme

Mit der Modellierungsansicht können Sie Diagramme Ihres Modells erstellen, die nur eine Teilmenge der Tabellen in Ihrem Modell umfassen. So erhalten Sie einen klareren Überblick über die Tabellen, mit denen Sie arbeiten möchten, und es kann die Arbeit mit komplexen Datasets erleichtern. Um ein neues Diagramm zu erstellen, das nur einen Teil der Tabellen enthält, klicken Sie auf das **+** -Zeichen neben der Registerkarte **Alle Tabellen** im unteren Bereich des Power BI Desktop-Fensters.

![Erstellen eines neuen Diagramms durch Klicken auf das +-Zeichen im Registerkartenabschnitt](media/desktop-modeling-view/modeling-view_03.png)

Sie können anschließend eine Tabelle aus der Liste **Felder** auf die Diagrammoberfläche ziehen. Klicken Sie mit der rechten Maustaste auf die Tabelle, und wählen Sie anschließend im angezeigten Menü die Option **Verknüpfte Tabellen hinzufügen** aus.

![Rechtsklick auf eine Tabelle und Auswahl von „Verknüpfte Tabellen hinzufügen“](media/desktop-modeling-view/modeling-view_04.png)

Hierdurch werden alle mit der ursprünglichen Tabelle verknüpften Tabellen im neuen Diagramm angezeigt. Die folgende Abbildung zeigt, wie verknüpfte Tabellen angezeigt werden, nachdem die Menüoption **Verknüpfte Tabellen hinzufügen** ausgewählt wurde.

![Anzeige verknüpfter Tabellen](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Festlegen allgemeiner Eigenschaften

Sie können in der Modellierungsansicht einem Arbeitsschritt mehrere Objekte auswählen, indem Sie die **STRG**-Taste gedrückt halten und auf mehrere Tabellen klicken. Wenn Sie mehrere Tabellen auswählen, werden diese in der Modellierungsansicht hervorgehoben dargestellt. Nach der Auswahl mehrerer Tabellen werden Änderungen, die im Bereich **Eigenschaften** durchgeführt werden, auf alle ausgewählten Tabellen angewendet.

Sie können beispielsweise den [Speichermodus](desktop-storage-mode.md) für mehrere Tabellen in Ihrer Diagrammansicht ändern, indem Sie die **STRG**-Taste gedrückt halten, mehrere Tabellen auswählen und dann die Einstellung für den Speichermodus im Bereich **Eigenschaften** ändern.

![Auswahl mehrerer Tabellen durch Halten der STRG-Taste und anschließende Festlegung allgemeiner Eigenschaften für alle ausgewählten Tabellen](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Weitere Schritte

Die folgenden Artikeln enthalten weitere Informationen über Datenmodelle sowie Details zu DirectQuery.

* [Aggregationen in Power BI Desktop (Vorschau)](desktop-aggregations.md)
* [Verwenden zusammengesetzter Modelle in Power BI Desktop](desktop-composite-models.md)
* [Speichermodus in Power BI Desktop (Vorschauversion)](desktop-storage-mode.md)
* [Beziehungen mit einer m:n-Kardinalität in Power BI Desktop](desktop-many-to-many-relationships.md)


Artikel zu DirectQuery:

* [Verwendung von DirectQuery in Power BI](../connect-data/desktop-directquery-about.md)
* [Von DirectQuery in Power BI unterstützte Datenquellen](../connect-data/power-bi-data-sources.md)
