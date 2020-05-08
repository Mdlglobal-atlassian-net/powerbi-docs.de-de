---
title: Verwenden der Leistungsanalyse zum Untersuchen der Leistung von Berichtselementen in Power BI Desktop
description: Erfahren Sie, wie Sie die Leistung von Visualisierungen und Berichtselementen in Bezug auf Ressourcenverbrauch und Reaktionsfähigkeit ermitteln.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e3e9e8ebc7feda46cb4c79ffd1535807d04a178b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709773"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Verwenden der Leistungsanalyse zum Untersuchen der Leistung von Berichtselementen

In **Power BI Desktop** können Sie die Leistung für jedes Ihrer Berichtselemente – beispielsweise Visuals und DAX-Formeln – ermitteln. Mithilfe der **Leistungsanalyse** können Sie Protokolle anzeigen und aufzeichnen, um die Leistung für jedes Ihrer Berichtselemente bei der Benutzerinteraktion zu messen und festzustellen, welche Aspekte die meisten (oder wenigsten) Ressourcen verbrauchen.

![Performance Analyzer](media/desktop-performance-analyzer/performance-analyzer-01.png)

Die Leistungsanalyse untersucht und zeigt die Dauer an, die zum Aktualisieren aller Visuals benötigt wird, die über Benutzerinteraktionen initiiert werden. Die Ergebnisse werden so dargestellt, dass Sie die Ergebnisse anzeigen, näher untersuchen oder exportieren können. Mithilfe der Leistungsanalyse können Sie visuelle Elemente identifizieren, die sich auf die Leistung Ihrer Berichte auswirken, und Sie können den Grund für die Beeinträchtigung ermitteln.

## <a name="displaying-the-performance-analyzer-pane"></a>Anzeige des Bereichs „Leistungsanalyse“

Wählen Sie in **Power BI Desktop** das Menüband **Ansicht** aus. Im Bereich **Anzeigen** des Menübands **Ansicht** können Sie das Kontrollkästchen neben **Leistungsanalyse** aktivieren, um den Bereich „Leistungsanalyse“ anzuzeigen.

![Auswählen der Leistungsanalyse im Menüband „Ansicht“](media/desktop-performance-analyzer/performance-analyzer-02.png)

Nach der Auswahl wird die Leistungsanalyse in einem eigenen Bereich rechts neben der Berichtscanvas angezeigt.

## <a name="using-performance-analyzer"></a>Verwenden der Leistungsanalyse

Die Leistungsanalyse misst die benötigte Verarbeitungszeit (einschließlich der Zeit zum Erstellen oder Aktualisieren eines Visuals) für das Aktualisieren von Berichtselementen, die über eine Benutzerinteraktion ausgelöst wurden und zum Ausführen einer Abfrage führen. Beispielsweise muss bei Anpassung eines Slicers das Slicervisual geändert, eine Abfrage an das Datenmodell gesendet und eine Aktualisierung der Visuals durchgeführt werden, die aufgrund der neuen Einstellungen aktualisiert werden müssen. 

Klicken Sie einfach auf **Aufzeichnung starten**, um mit der Aufzeichnung durch die Leistungsanalyse zu beginnen.

![Aufzeichnung starten](media/desktop-performance-analyzer/performance-analyzer-03.png)

Alle Aktionen, die Sie im Bericht ausführen, werden im Bereich „Leistungsanalyse“ in der Reihenfolge angezeigt und protokolliert, in der das Visual von Power BI geladen wird. So könnten Sie beispielsweise über einen Bericht verfügen, für den die Benutzer eine lange Aktualisierungsdauer gemeldet haben. Oder die Anzeige bestimmter Visuals in einem Bericht dauert sehr lange, nachdem ein Schieberegler angepasst wurde. Über die Leistungsanalyse können ermitteln, welches Visual die Ursache dafür ist, und Sie können ermitteln, welche Aspekte des Visuals die längste Verarbeitungsdauer aufweisen. 

Nach dem Start der Aufzeichnung wird die Schaltfläche **Aufzeichnung starten** abgeblendet dargestellt (die Schaltfläche ist inaktiv, weil die Aufzeichnung bereits begonnen hat), und die Schaltfläche **Beenden** ist aktiv. 

Die Leistungsanalyse sammelt und zeigt die Informationen zur Leistungsmessung in Echtzeit an. Deshalb zeigt die Leistungsanalyse bei jedem Klick auf ein Visual, beim Verschieben eines Slicers oder bei einer anderen Form der Interaktion sofort die Leistungsergebnisse im zugehörigen Fenster an.

Wenn der Bereich mehr Informationen enthält, als angezeigt werden können, erscheint eine Bildlaufleiste, um zu den Zusatzinformationen zu navigieren zu können.

Jede Interaktion im Bereich weist einen Abschnittsbezeichner auf. Dieser Bezeichner beschreibt die Aktion, die den Protokolleintrag ausgelöst hat. Im Screenshot unten bestand die Interaktion darin, dass der Benutzer einen Slicer geändert hat.

![Abschnitte basierend auf Interaktionstyp](media/desktop-performance-analyzer/performance-analyzer-04.png)

Die Protokollinformationen zu jedem Visual beinhalten die aufgewendete Zeit (Dauer) zum Ausführen der folgenden Aufgabenkategorien:

* **DAX-Abfrage**: Wenn eine DAX-Abfrage erforderlich war, ist dies die Zeit zwischen dem Sendevorgang der Abfrage durch das Visual und der Rückgabe der Ergebnisse durch Analysis Services.
* **Visuelle Anzeige**: Die Zeit, die zum Zeichnen des Visuals auf dem Bildschirm benötigt wird. Dies schließt die Zeit ein, die für das Abrufen von Webbildern oder eine Geocodierung benötigt wird. 
* **Andere**: Die Zeit, die das Visual für das Vorbereiten von Abfragen, das Warten auf den Abschluss anderer Visuals oder das Durchführen einer weiteren Hintergrundverarbeitung benötigt.

Die Werte für **Dauer (ms)** geben jeweils den Unterschied zwischen einem *Start*- und *End*-Zeitstempel eines Vorgangs an. Die meisten Vorgänge für den Zeichenbereich und Visuals werden sequenziell in einem einzelnen Benutzeroberflächenthread ausgeführt, der von mehreren Vorgängen gemeinsam genutzt wird. Die gemeldeten Zeiträume umfassen die Zeit, die in der Warteschlange verbracht wurde, während andere Vorgänge ausgeführt wurden. Das [Beispiel für die Leistungsanalyse](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer) auf GitHub und die dazugehörige [Dokumentation](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx) enthalten Informationen darüber, wie Visuals Daten abfragen und wie sie rendern.


![Elemente in Protokollinformationen](media/desktop-performance-analyzer/performance-analyzer-06.png)

Nachdem Sie mithilfe der Leistungsanalyse mit Berichtselementen interagiert haben, deren Leistung Sie messen möchten, können Sie auf die Schaltfläche **Beenden** klicken. Die Leistungsinformationen werden zur weiteren Analyse auch nach dem Klicken auf **Beenden** weiterhin im Bereich angezeigt.

Um die Informationen aus dem Bereich „Leistungsanalyse“ zu entfernen, klicken Sie auf **Löschen**. Bei Auswahl von **Löschen** werden alle Informationen entfernt, und es werden keine Daten gespeichert. Im nächsten Abschnitt erfahren Sie, wie Sie Informationen in Protokollen speichern können. 

## <a name="refreshing-visuals"></a>Aktualisieren von Visuals

Durch Auswahl von **Visuals aktualisieren** im Bereich „Leistungsanalyse“ können Sie alle Visuals auf der aktuellen Seite des Berichts aktualisieren, um über die Leistungsanalyse Informationen zu all diesen Visuals zu erfassen.

Sie können auch einzelne Visuals aktualisieren. Wenn über die Leistungsanalyse eine Aufzeichnung durchgeführt wird, können Sie oben rechts in jedem Visual auf **Dieses Visual aktualisieren** klicken, um das betreffende Visual zu aktualisieren und zugehörige Leistungsinformationen zu erfassen.

![Aktualisieren einzelner Visuals](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Speichern von Leistungsinformationen

Sie können die von der Leistungsanalyse generierten Informationen zu einem Bericht speichern, indem Sie auf die Schaltfläche **Exportieren** klicken. Durch das Auswählen von **Exportieren** wird eine JSON-Datei mit Informationen aus dem Bereich „Leistungsanalyse“ erstellt. 

![Speichern der Protokolldatei für die Leistungsanalyse](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Weitere Schritte
Weitere Informationen zu **Power BI Desktop** und den ersten Schritten finden Sie in den folgenden Artikeln.

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datenquellen in Power BI-Desktop](desktop-data-sources.md)
* [Verbinden mit Daten in Power BI Desktop](desktop-connect-to-data.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Allgemeine Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)   

Weitere Informationen zum Beispiel für Leistungsanalyse finden Sie in den folgenden Ressourcen.

* [Beispiel für die Leistungsanalyse](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer)
* [Dokumentation zum Beispiel für die Leistungsanalyse](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx)