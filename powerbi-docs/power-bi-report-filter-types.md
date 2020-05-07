---
title: Filtertypen in Power BI-Berichten
description: Hinzufügen eines Seiten-, Visualisierungs- oder Berichtsfilters zu einem Bericht in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c96b4ebae574a3b6a6fa54c5f5dc99b5bc948a90
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874419"
---
# <a name="types-of-filters-in-power-bi-reports"></a>Filtertypen in Power BI-Berichten

Nicht alle Filter verhalten sich gleich, weil sie nicht auf die gleiche Weise erstellt werden. Wie Sie sie erstellen, beeinflusst ihr Verhalten im neuen Filterbereich im Bearbeitungsmodus. In diesem Artikel werden die verschiedenen Arten von Filtern beschrieben: Die verschiedenen Möglichkeiten, wie Sie sie erstellen, und die unterschiedlichen Zwecke, für die sie bestimmt sind. Erfahren Sie, wie Sie [Berichten Filter hinzufügen](power-bi-report-add-filter.md). 

![Filterbereich](media/power-bi-report-filter-types/power-bi-filter-pane.png)

Wir beginnen mit den zwei am häufigsten verwendeten Filtertypen: manuelle und automatische.

## <a name="manual-filters"></a>Manuelle Filter 

Manuelle Filter sind die Filter, die Berichtersteller an beliebiger Stelle im neuen Filterbereich ziehen und ablegen. Benutzer mit Bearbeitungsberechtigung für den Bericht können diese Filter im neuen Bereich bearbeiten, löschen, deaktivieren, ausblenden, sperren, umbenennen oder sortieren.

## <a name="automatic-filters"></a>Automatische Filter 

Automatische Filter sind die Filter, die automatisch auf der visuellen Ebene des Filterbereichs hinzugefügt werden, wenn Sie eine Visualisierung erstellen. Diese Filter basieren auf den Feldern, aus denen die Visualisierung besteht. Benutzer mit Bearbeitungsberechtigung für den Bericht können diese Filter im neuen Bereich bearbeiten, deaktivieren, ausblenden, sperren, umbenennen oder sortieren. Sie können automatische Filter nicht löschen, da das visuelle Element auf diese Felder verweist.

## <a name="more-advanced-filters"></a>Erweiterte Filter

Diese nächsten Filtertypen sind weniger verbreitet, aber Sie müssen sie trotzdem verstehen, wenn sie in Ihrem Bericht angezeigt werden. Außerdem könnten sie ja auch genau die richtigen Filter für Ihren Bericht sein.

## <a name="include-and-exclude-filters"></a>Einschluss-/Ausschlussfilter

Einschluss- und Ausschlussfilter werden dem Filterbereich automatisch hinzugefügt, wenn Sie die Einschluss- oder Ausschlussfunktion für ein Visual verwenden. Benutzer mit Bearbeitungsberechtigung für den Bericht können diese Filter im neuen Bereich löschen, sperren, ausblenden, oder sortieren. Sie können einen Einschluss- oder Ausschlussfilter nicht bearbeiten, deaktivieren oder umbenennen, da er der Einschluss- und Ausschlussfunktionalität visueller Elemente zugeordnet ist.

![Ausschlussfilter](media/power-bi-report-filter-types/power-bi-filters-exclude.png)

## <a name="drill-down-filters"></a>Drilldownfilter

Drilldownfilter werden dem Filterbereich automatisch hinzugefügt, wenn Sie die Drilldownfunktion für ein Visual in Ihrem Bericht verwenden. Benutzer mit Bearbeitungsberechtigung für den Bericht können diesen Filter im neuen Bereich bearbeiten oder deaktivieren. Sie können diesen Filter nicht löschen, ausblenden, sperren, umbenennen oder sortieren, da er mit der Drilldownfunktionalität von Visuals verbunden ist. Um den Drilldownfilter zu entfernen, klicken Sie auf die Drillupschaltfläche des visuellen Elements.

![Drilldownfilter](media/power-bi-report-filter-types/power-bi-filters-drill-down.png)

## <a name="cross-drill-filters"></a>Crossdrillfilter

Crossdrillfilter werden dem neuen Bereich automatisch hinzugefügt, wenn ein Drilldownfilter über das Feature Kreuzfilterung oder Kreuzhervorhebung einem anderen visuellen Element auf der Berichtsseite übergeben wird. Benutzer mit Bearbeitungsberechtigung für den Bericht können diesen Filter nicht löschen, deaktivieren, ausblenden, sperren, umbenennen oder sortieren, da er mit der Drilldownfunktionalität von Visuals verbunden ist. Sie können diesen Filter auch nicht bearbeiten, weil er vom Drilldown in einem anderen Visual stammt. Um den Drilldownfilter zu entfernen, klicken Sie auf die Drillupschaltfläche des visuellen Elements, das den Filter übergibt.

## <a name="drillthrough-filters"></a>Drillthroughfilter

Drillthroughfilter werden über das Drillthroughfeature von einer Seite zur anderen übergeben. Sie werden im Drillthroughbereich angezeigt. Es gibt zwei Typen von Drillthroughfiltern. Der erste Typ ruft den Drillthrough auf. In Berichts-Editoren kann dieser Filtertyp bearbeitet, gelöscht, deaktiviert, ausgeblendet oder gesperrt werden. Der zweite Typ ist der Drillthroughfilter, der dem Ziel auf Basis der Seitenebenenfilter der Quellseite übergeben wird. In Berichts-Editoren kann dieser transiente Drillthroughfiltertyp bearbeitet, gelöscht oder deaktiviert werden. Dieser Filter kann nicht für Endbenutzer gesperrt oder ausgeblendet werden.

## <a name="url-filters"></a>URL-Filter

URL-Filter werden dem neuen Bereich durch Hinzufügen eines URL-Abfrageparameters hinzugefügt. Benutzer mit Bearbeitungsberechtigung für den Bericht können diesen Filter im neuen Bereich bearbeiten, löschen oder deaktivieren. Sie können diesen Filter nicht ausblenden, sperren, umbenennen oder sortieren, da er mit dem URL-Parameter verbunden ist. Um den Filter zu entfernen, entfernen Sie den Parameter aus der URL. Hier ist eine Beispiel-URL mit einem Parameter:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=Stores~2FStatus%20eq%20'Off'

![URL-Filter](media/power-bi-report-filter-types/power-bi-filter-url.png)

Erfahren Sie mehr über [URL-Filter](service-url-filters.md).

## <a name="pass-through-filters"></a>Pass-Through-Filter

Pass-Through-Filter sind Filter auf Visualebene, die über Q&A erstellt werden. Ersteller können diese Filter im neuen Bereich löschen, ausblenden oder sortieren. Sie können diese Filter allerdings nicht umbenennen, bearbeiten, deaktivieren oder sperren.

![Pass-Through-Filter mit Q&A](media/power-bi-report-filter-types/power-bi-filters-qna.png)

## <a name="comparing-filter-types"></a>Vergleichen von Filtertypen

Diese Tabelle zeigt zum Vergleich, wie Ersteller die verschiedenen Arten von Filtern verwenden können.

| Filtertyp | Edit (Bearbeiten) | Clear | Löschen | Ausblenden | Sperre | Sortieren | Umbenennen |
|----|----|----|----|----|----|----|----|
| Manuelle Filter | J | J | J | J | J | J | J |
| Automatische Filter | J | J | N | J | J | J | J |
| Einschluss-/Ausschlussfilter | N | N | J | J | J | J | N |
| Drilldownfilter | J | J | N | N | N | N | N |
| Crossdrillfilter | N | N | N | N | N | N | N |
| Drillthroughfilter (rufen Drillthrough auf) | J | J | J | J | J | N | N |
| Drillthroughfilter (transient) | J | J | J | N | N | N | N |
| URL-Filter – transient | J | J | J | N | N | N | N |
| Pass-Through-Filter | N | N | J | J | N | J | N |



## <a name="next-steps"></a>Weitere Schritte

[Hinzufügen von Filtern zu Berichten](power-bi-report-add-filter.md)

[Überblick über den Berichtsbereich „Filter“](consumer/end-user-report-filter.md)

[Filter und Hervorhebungen in Berichten](power-bi-reports-filters-and-highlighting.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

