---
title: Verbinden mit Daten in Power BI Desktop
description: Verbinden mit Daten in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 751a53e2bfe0c9743a71cc41aa349afa23fd013a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76539144"
---
# <a name="connect-to-data-sources-in-power-bi-desktop"></a>Herstellen einer Verbindung mit Datenquellen in Power BI Desktop

Mit Power BI Desktop können Sie problemlos Verbindungen zur ständig wachsenden Welt der Daten herstellen. Wenn Sie noch nicht über Power BI Desktop verfügen, können Sie die Anwendung [herunterladen](https://go.microsoft.com/fwlink/?LinkID=521662) und installieren.

In Power BI Desktop sind *alle möglichen Arten* von in Power BI Desktop verfügbaren Datenquellen enthalten. In der folgenden Abbildung wird gezeigt, wie Sie eine Verbindung zu Daten herstellen, indem Sie **Get Data** > **Other** > **Web** (Daten abrufen > Sonstige > Web) auswählen.

![Abrufen von Daten aus dem Web](media/desktop-connect-to-data/get-data-from-the-web.png)

## <a name="example-of-connecting-to-data"></a>Beispiel für das Herstellen einer Verbindung mit einer Datenquelle

In diesem Beispiel wird die Verbindung mit einer **Web** -Datenquelle hergestellt.

Stellen Sie sich vor, Sie gehen in Rente. Sie möchten dort leben, wo die Sonne scheint und die Steuern sowie das Gesundheitswesen akzeptabel sind. Sie möchten dort leben, wo die Sonne scheint und die Steuern sowie das Gesundheitswesen akzeptabel sind. Vielleicht sind Sie auch Datenanalyst und benötigen diese Informationen, um Ihren Kunden zu helfen, die vielleicht Hersteller von Regenkleidung sind und ihre Umsätze auf Orte ausrichten möchten, wo es *viel* regnet.

In beiden Fällen finden Sie eine Webressource, die interessante Daten und mehr zu diesen Themen enthält:

[https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx](https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

Wählen Sie **Data** > **Other** > **Web** (Daten abrufen > Sonstige > Web) aus. Geben Sie in **Aus dem Web** die Adresse ein.

![Eingeben einer Webquelladresse](media/desktop-connect-to-data/connecttodata_3.png)

Mit der Auswahl von **OK** beginnt die *Abfragefunktion* von Power BI Desktop ihre Arbeit. Power BI Desktop kontaktiert die Webressource und gibt im Fenster **Navigator** die auf der Webseite gefundenen Ergebnisse zurück. In diesem Fall wurde eine Tabelle und das gesamte Dokument gefunden. Da Sie an der Tabelle interessiert sind, wählen Sie diese aus der Liste aus. Im Fenster **Navigator** wird eine Vorschau angezeigt.

![Vorschau der Daten im Fenster „Navigator“](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

An diesem Punkt können Sie die Abfrage vor dem Laden der Tabelle bearbeiten, indem Sie **Daten transformieren** am unteren Rand des Fensters wählen oder einfach die Tabelle laden.

Wählen Sie **Daten transformieren** aus, um die Tabelle zu laden und starten Sie den Power Query-Editor. Der Bereich **Abfrageeinstellungen** wird angezeigt. Wird dieser nicht angezeigt, wählen Sie **Anzeigen** aus dem Menüband aus, und wählen Sie dann **Abfrageeinstellungen** aus, um den Bereich **Abfrageeinstellungen** anzuzeigen. So sieht die Ansicht aus.

![Power Query-Editor mit Abfrageeinstellungen](media/desktop-connect-to-data/designer_gsg_editquery.png)

Alle diese Ergebnisse sind eher Text als Zahlen, aber wir benötigen Zahlen. Kein Problem. Klicken Sie einfach mit der rechten Maustaste auf die Spaltenüberschrift, und wählen Sie **Typ ändern**  > **Ganze Zahl** aus, um die Werte zu ändern. Wählen Sie zuerst eine Spalte aus, drücken Sie die UMSCHALTTASTE, und wählen Sie dann mit gedrückter Taste weitere angrenzende Spalten aus, um mehr als eine Spalte auszuwählen. Klicken Sie anschließend mit der rechten Maustaste auf eine Spaltenüberschrift, um alle ausgewählten Spalten zu ändern. Drücken Sie STRG, um nicht benachbarte Spalten auszuwählen.

![Ändern des Datentyps in „Ganze Zahl“](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

In den **Abfrageeinstellungen** werden alle vorgenommenen Änderungen unter **ANGEWENDETE SCHRITTE** angezeigt. Wenn Sie weitere Änderungen an den Daten vornehmen, werden diese Änderungen vom Power Query-Editor im Abschnitt **ANGEWENDETE SCHRITTE** gespeichert, den Sie bei Bedarf anpassen, nochmals besuchen, neu anordnen oder löschen können.

![Angewendete Schritte](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

Nach dem Laden können an der Tabelle weitere Änderungen vorgenommen werden. In diesem Fall brauchen wir dies aber nicht. Wenn Sie dies abgeschlossen haben, wählen Sie **Close & Apply** (Schließen und übernehmen) im Menüband **Home** aus. Daraufhin wendet Power BI Desktop die Änderungen an und schließt den Power Query-Editor.

![Close & Apply (Öffnen und Übernehmen)](media/desktop-connect-to-data/connecttodata_closenload.png)

Nachdem das Datenmodell in der **Berichtsansicht** in Power BI Desktop geladen ist, können wir mit der Erstellung von Visualisierungen beginnen, indem wir Felder in den Zeichenbereich ziehen.

![Ziehen eines Werts in den Zeichenbereich](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

Mit einer einzelnen Datenverbindung ist dieses Modell auf jeden Fall einfach. Die meisten Power BI Desktop-Berichte haben Verbindungen zu verschiedenen Datenquellen, die Ihren Anforderungen entsprechend aufgebaut sind, und zwar mit Beziehungen, die ein umfangreiches Datenmodell ergeben.

## <a name="next-steps"></a>Weitere Schritte
Mit Power BI Desktop können Sie viele Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Informationen zum Abfrage-Editor in Power BI Desktop](desktop-query-overview.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten in Power BI Desktop](desktop-shape-and-combine-data.md)
* [Durchführen allgemeiner Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)   

Möchten Sie uns Feedback senden? Sehr gut! Verwenden Sie das Menüelement **Vorschlag einreichen** in Power BI Desktop, oder besuchen Sie die Seite [Communityfeedback](https://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback). Wir freuen uns, von Ihnen zu hören!

![Senden von Vorschlägen](media/desktop-connect-to-data/sendfeedback.png)

