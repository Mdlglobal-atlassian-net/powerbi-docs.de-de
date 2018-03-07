---
title: Informationen zu Filtern und Hervorhebungen in Power BI-Berichten
description: Informationen zu Filtern und Hervorhebungen in Power BI-Berichten
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/08/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: dc39f23c192c8bbe1126551c20205bafd8be3a07
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="about-filters-and-highlighting-in-power-bi-reports"></a>Informationen zu Filtern und Hervorhebungen in Power BI-Berichten
***Filter*** entfernen alles bis auf die Daten, auf die Sie sich konzentrieren möchten.  ***Hervorheben*** ist kein Filtern, da hierbei keine Daten entfernt, sondern eine Teilmenge der sichtbaren Daten hervorgehoben wird. Die nicht hervorgehobenen Daten bleiben sichtbar, sind jedoch abgeblendet.

Zum Zuweisen von Filtern und Hervorhebungen zu Berichten haben Sie in Power BI verschiedene Möglichkeiten. Diese eingehend zu beschreiben, würde den Rahmen dieses Artikels sprengen. Wir haben also folgende Aufteilung vorgenommen:

* Einführung in Filter und Hervorhebungen (dieser Artikel)
* Über das [Erstellen und Verwenden von Filtern und Hervorhebungen in der Bearbeitungsansicht von Berichten, deren Besitzer Sie sind](power-bi-report-add-filter.md). Wenn Sie über die erforderlichen Berechtigungen zum Bearbeiten des Berichts verfügen, können Sie darin Filter und Hervorhebungen erstellen, Änderungen vornehmen und diese auch wieder löschen.
* Über das [Verwenden von Filtern und Hervorhebungen in einem Bericht, der für Sie freigegeben wurde oder den Sie in der Leseansicht aufgerufen haben](service-reading-view-and-editing-view.md). Hier bestehen Einschränkungen, Power BI bietet Ihnen jedoch in jedem Fall eine Vielzahl von Optionen für Filter und Hervorhebungen.  
* [Eine ausführliche Tour, in der Sie die Benutzeroberfläche für die Steuerung der Filter und Hervorhebungen kennenlernen](power-bi-how-to-report-filter.md), einschließlich der verschiedensten Filtertypen (z.B. Datum und Uhrzeit, Nummern- und Textfilter) und einer Erklärung des Unterschieds zwischen Standard- und erweiterten Optionen.
* Sobald Sie das Standardverfahren für die Verwendung von Filtern und Hervorhebungen kennen, fahren wir mit der Art und Weise fort, [wie verschiedene Visualisierungen auf einer Seite einander durch Filter und Hervorhebungen beeinflussen (und wie Sie deren Verhalten ändern können)](service-reports-visual-interactions.md).

> [!TIP]
> Wie wird in Power BI ermittelt, welche Daten wie zusammenhängen?  Es werden die Beziehungen zwischen den verschiedenen Tabellen und Feldern im zugrunde liegenden [Datenmodell](https://support.office.com/article/Create-a-Data-Model-in-Excel-87e7a54c-87dc-488e-9410-5c75dbcb0f7b?ui=en-US&rs=en-US&ad=US) herangezogen, damit Elemente auf einer Berichtsseite miteinander interagieren.
> 
> 

## <a name="introduction-to-filters-and-highlighting-in-reports-using-the-filters-pane"></a>Einführung in Filter und Hervorhebungen in Berichte im Bereich „Filter“
![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Filter und Hervorhebungen können über den Bereich **Filter** angewendet werden oder indem Sie eine Auswahl direkt im Bericht selbst treffen (Informationen zu diesem als „Ad-hoc“ bezeichneten Verfahren finden Sie am Ende dieser Seite). Im Bereich „Filter“ werden die Tabellen und Felder, die im Bericht verwendet werden, sowie die ggf. angewendeten Filter angezeigt. Jeder Filter gehört zu einer von drei Kategorien: **Filter auf Seitenebene**, **Filter auf Berichtsebene** und **Filter auf visueller Ebene**.  Die Filter auf visueller Ebene werden nur angezeigt, wenn Sie auf dem Berichtszeichenbereich eine Visualisierung ausgewählt haben.

> [!TIP]
> Wenn neben einem Filter die Bezeichnung **Alle** erscheint, wird das Feld insgesamt als Filter verwendet.  Beispiel: **Kette(Alle)** (siehe Screenshot unten) zeigt an, dass diese Berichtsseite Informationen über alle Ketten enthält.  Andererseits können wir der Angabe **Geschäftsjahr ist 2013 oder 2014** entnehmen, dass der Bericht ausschließlich Informationen aus den Geschäftsjahren 2013 und 2014 umfasst.
> 
> 

## <a name="filters-in-reading-view-versus-editing-view"></a>Filter in der Leseansicht und Filter in der Bearbeitungsansicht
Es gibt zwei Modi für die Interaktion mit Berichten: [Leseansicht und Bearbeitungsansicht](service-reading-view-and-editing-view.md).  Es hängt vom Modus ab, in dem Sie sich befinden, welche Filterfunktionen verfügbar sind.

* In der Bearbeitungsansicht können Sie Berichts-, Seiten- und visuelle Filter hinzufügen. Wenn Sie den Bericht speichern, werden die Filter ebenfalls gespeichert. Personen, die den Bericht in der Leseansicht anzeigen, können mit den von Ihnen hinzugefügten Filtern interagieren, aber die Änderungen nicht speichern.
* In der Leseansicht können Sie mit allen Seitenfiltern und visuellen Filtern interagieren, die im Bericht bereits vorhanden sind. Sie können Ihre Filteränderungen allerdings nicht speichern.

### <a name="the-filters-pane-in-reading-view"></a>Der Bereich „Filter“ in der Leseansicht
Wenn Sie auf einen Bericht nur über die Leseansicht zugreifen können, wird der Bereich „Filter“ wie hier angezeigt:

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Diese Berichtsseite verfügt über sechs Filter auf Seitenebene und einen Filter auf Berichtsebene.

Um herauszufinden, ob auch Filter auf visueller Ebene vorhanden sind, wählen Sie eine Visualisierung aus. Im Bild unten wurden sechs Filter auf das Blasendiagramm angewendet.

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

In der Leseansicht können Sie die Daten untersuchen, indem Sie die bestehenden Filter modifizieren. Wie Sie dazu vorgehen müssen, erfahren Sie im Artikel [Interagieren mit einem Bericht in der Leseansicht](service-reading-view-and-editing-view.md).

### <a name="the-filters-pane-in-editing-view"></a>Der Bereich „Filter“ in der Bearbeitungsansicht
Wenn Sie über die Besitzerberechtigungen für einen Bericht verfügen und diesen in der Bearbeitungsansicht öffnen, sehen Sie, dass der Bereich **Filter** nur einer von einer Reihe an verfügbaren Bearbeitungsbereichen ist.

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Wie in der Leseansicht (oben) verfügt diese Berichtsseite über sechs Filter auf Seitenebene und einen Filter auf Berichtsebene. Durch Auswahl des Blasendiagramms erfahren wir, dass sechs Filter auf visueller Ebene angewendet wurden.

Allerdings haben Sie bei der Arbeit mit Filtern und Hervorhebungen in der Bearbeitungsansicht viel mehr Möglichkeiten. Der größte Unterschied besteht darin, dass wir neue Filter hinzufügen können. Weitere ausführliche Informationen dazu finden Sie im Artikel [Hinzufügen eines Filters zu einem Bericht](power-bi-report-add-filter.md).

## <a name="ad-hoc-filterting-and-highlighting"></a>Ad-hoc-Filter und -Hervorhebungen
Wählen Sie zum Filtern und Hervorheben des übrigen Teils der Seite im Berichtszeichenbereich ein Feld aus. Wählen Sie in derselben Visualisierung einen leeren Bereich an, um die eben getroffene Auswahl wieder zu entfernen. Dieser Filter- und Hervorhebungstyp wird nicht mit dem Bericht gespeichert, Sie können so aber den Einfluss von Daten schnell untersuchen. Wie Sie das Verhalten dieser Art von Kreuzfiltern und -hervorhebungen anpassen können, erfahren Sie unter [Visuelle Interaktionen](service-reports-visual-interactions.md).

![](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

## <a name="next-steps"></a>Nächste Schritte
[Interagieren mit Filtern und Hervorhebungen (in der Leseansicht)](service-reading-view-and-editing-view.md)

[Hinzufügen eines Filters zu einem Bericht (in der Bearbeitungsansicht)](power-bi-report-add-filter.md)

[Überblick über Berichtsfilter](power-bi-how-to-report-filter.md)

[Ändern der Kreuzfilterung und -hervorhebung von Berichtsvisualisierungen](service-reports-visual-interactions.md)

Erfahren Sie mehr über [Berichte in Power BI](service-reports.md).

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
