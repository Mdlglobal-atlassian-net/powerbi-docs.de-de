---
title: DirectQuery und SAP Business Warehouse (BW) in Power BI
description: Überlegungen zur Verwendung von DirectQuery mit SAP Business Warehouse (BW)
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ceaa557be31625c9573a7285602a1a4ef8164fb7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83292660"
---
# <a name="connect-to-sap-business-warehouse-by-using-directquery-in-power-bi"></a>Verbinden mit SAP Business Warehouse über DirectQuery in Power BI
Sie können sich mit **SAP Business Warehouse (BW)** -Datenquellen direkt über **DirectQuery** verbinden. Da SAP BW multidimensional ist bzw. OLAP einsetzt, gibt es viele wesentliche Unterschiede zwischen DirectQuery via SAP BW und über relationalen Datenquellen wie SQL Server. Die Unterschiede werden im Folgenden dargestellt:

* Es gibt bei **DirectQuery** über relationale Datenquellen einen Satz von Abfragen (wie in den Dialogfeldern **Get Data** (Daten abrufen) und **Query Editor** (Abfrage-Editor) definiert), die die im Feld verfügbaren Daten logisch definieren. Bei der Verbindung mit einer OLAP-Quelle wie SAP BW ist dies *nicht* der Fall. Bei der Verbindung mit dem SAP-Server mit **Daten abrufen** wird stattdessen nur die Abfrage „Infocube“ oder „BEx“ verwendet. Anschließend stehen alle Kennzahlen und Dimensionen der Infocube/BEx-Abfrage in der Feldliste zur Verfügung.   
* Ebenso gibt es keinen **Abfrage-Editor**, wenn Sie mit SAP BW verbunden sind. Die Einstellungen der Datenquelle (z.B. der Servername) können unter **Edit Queries > Data source settings** (Abfragen bearbeiten > Datenquelleneinstellungen) geändert werden. Die Einstellungen eines Parameters können unter **Abfragen bearbeiten > Parameter verwalten** geändert werden.
* Aufgrund der eindeutigen Natur von OLAP-Quellen gibt es zusätzlich zu den üblichen von DirectQuery vorgegebenen Einschränkungen weitere Einschränkungen (sowohl bei der Modellierung als auch bei der Visualisierung). Diese Einschränkungen werden weiter unten in diesem Artikel beschrieben.

Weiterhin ist es *essentiell*, dass Ihnen bewusst ist, dass SAP BW viele Funktionen hat, die in Power BI nicht unterstützt werden. Zudem gibt es Fälle, in denen die in Power BI angezeigten Ergebnisse nicht denen in einem SAP-Tool entsprechen. Dies ist auf die Beschaffenheit der öffentlichen Schnittstelle von SAP BW zurückzuführen. Diese Einschränkungen werden weiter unten in diesem Artikel beschrieben. Sie sollten sich diese Einschränkungen und Verhaltensunterschiede genau anschauen, um sicherzustellen, dass die in Power BI angezeigten Ergebnisse, die von der öffentlichen SAP-Schnittstelle zurückgegeben werden, korrekt interpretiert werden.  

> [!NOTE]
> Die Möglichkeit zur Verwendung von DirectQuery über SAP BW wurde bis zum Update von Power BI Desktop im März 2018 in der Vorschau angekündigt. Während der Vorschau wurden durch Feedback und Verbesserungsvorschläge Änderungen veranlasst, die Auswirkungen auf mit dieser Vorschauversion erstellte Berichte hatten. Nun, da die allgemeine Verfügbarkeit von DirectQuery über SAP BW veröffentlicht wurde, *müssen* Sie alle vorhandenen (vorschaubasierten) Berichte löschen, die DirectQuery über SAP BW verwenden und mit der Vorgängerversion der allgemeinen Verfügbarkeit erstellt wurden. In Berichten, die mit der Vorgängerversion der allgemeinen Verfügbarkeit von DirectQuery über SAP BW erstellt wurden, treten beim Aufrufen von „Aktualisieren“ infolge des Versuchs, die Metadaten mit Änderungen an dem zugrunde liegenden SAP BW-Cube zu aktualisieren, Fehler auf. Erstellen Sie diese Berichte erneut über einen leeren Bericht, und verwenden Sie dabei die Version der allgemeinen Verfügbarkeit von DirectQuery über SAP BW. 

## <a name="additional-modeling-restrictions"></a>Zusätzliche Modellierungseinschränkungen
Dies sind die wesentlichen zusätzlichen Modellierungseinschränkungen beim Herstellen einer Verbindung mit SAP BW mithilfe von DirectQuery in Power BI:

* **Keine Unterstützung für berechnete Spalten**: Das Erstellen von berechneten Spalten ist deaktiviert. Dies bedeutet zudem, dass Gruppierung und Clustering, mit denen berechnete Spalten erstellt werden, nicht zur Verfügung stehen.
* **Zusätzliche Einschränkungen von Measures**: Es gibt zusätzliche Einschränkungen von DAX-Ausdrücken, die in Measures verwendet werden können, damit die von SAP BW bereitgestellte Unterstützung übernommen wird.
* **Keine Unterstützung für das Definieren von Beziehungen**: Beziehungen sind in der externen SAP-Quelle verankert, und es können keine zusätzlichen Beziehungen im Modell definiert werden.
* **Keine Datenansicht**: Die **Datenansicht** zeigt in der Tabelle normalerweise Daten auf Detailebene an. Aufgrund der Beschaffenheit von OLAP-Quellen wie SAP BW ist diese Ansicht in SAP BW nicht verfügbar.
* **Details von Spalten und Measures sind unveränderlich**: Die in der Feldliste anzeigte Listen von Spalten und Measures sind in der zugrunde liegenden Quelle festgelegt und können nicht verändert werden. Es ist z.B. nicht möglich, eine Spalte oder deren Datentyp zu löschen (Sie können sie allerdings umbenennen).
* **Zusätzliche Einschränkungen in DAX**: Es gibt zusätzliche Einschränkungen für DAX, die in Measuredefinitionen verwendet wird, damit die Einschränkungen in der Quelle übernommen werden. Es ist z.B. nicht möglich, eine Aggregatfunktion über eine Tabelle zu verwenden.

## <a name="additional-visualization-restrictions"></a>Zusätzliche Visualisierungseinschränkungen
Dies sind die wesentlichen zusätzliche Visualisierungsseinschränkungen beim Verbinden mit SAP BW mit DirectQuery in Power BI:

* **Keine Spaltenaggregation:** Es ist nicht möglich, die Aggregation einer Spalte für ein Visual zu ändern. Die Einstellung lautet immer *Nicht zusammenfassen*.
* **Das Filtern von Measures ist deaktiviert**: Das Filtern von Measures ist deaktiviert, damit die von SAP BW bereitgestellte Unterstützung übernommen wird.
* **Auswählen und Einschließen/Ausschließen von mehreren Elementen**: Die Möglichkeit zum Auswählen von mehreren Datenpunkten in einem visuellen Element ist deaktiviert, wenn die Punkte für Werte stehen, die aus mehr als einer Spalte stammen. Wenn Sie z.B ein Balkendiagramm mit den Verkaufszahlen pro Land haben, wobei sich die Kategorie in der Legende befindet, ist es nicht möglich, die Punkte für „USA, Fahrräder“ und „Frankreich, Kleidung“ auszuwählen. Ebenso ist es nicht möglich, den Punkt für „USA, Fahrräder“ auszuwählen und diesen aus dem visuellen Element auszuschließen. Beide Einschränkungen sind vorgegeben, damit die von SAP BW bereitgestellte Unterstützung übernommen wird.

## <a name="support-for-sap-bw-features"></a>Unterstützung für Funktionen von SAP BW
In der folgenden Tabelle werden alle Funktionen von SAP BW aufgelistet, die nicht vollständig unterstützt werden oder die sich mit Power BI anders verhalten.   

| Funktion | Beschreibung |
| --- | --- |
| Lokale Berechnungen |In einer BEx-Abfrage definierte lokale Berechnungen wirken sich auf die Zahlen aus, die über Tools wie BEx Analyzer angezeigt werden. Sie spiegeln sich allerdings nicht in den von SAP über die öffentliche MDX-Schnittstelle zurückgegebenen Zahlen wider. <br/> <br/> **Daher entsprechen die im visuellen Element von Power BI angezeigten Datei nicht unbedingt denen in dem entsprechenden visuellen Element in einem SAP-Tool.**<br/> <br/>  Wenn Sie z.B. eine Verbindung mit einem Abfragecube von einer BEx-Abfrage aus herstellen, die die zu kumulierende Aggregation angibt (d.h. die laufende Summe), ruft Power BI die Basiszahlen ab und ignoriert die Einstellung.  Ein Analytiker könnte dann natürlich die Berechnung der laufenden Summe lokal in Power BI anwenden, müsste aber bei der Interpretation der Zahlen vorsichtig sein, wenn dies nicht gemacht wird. |
| Aggregationen |In einigen Fällen () entsprechen die von der öffentlichen SAP-Schnittstelle zurückgegebenen Aggregatzahlen nicht denen vom SAP-Tool. <br/> <br/> **Daher entsprechen die im visuellen Element von Power BI angezeigten Datei nicht unbedingt denen in dem entsprechenden visuellen Element in einem SAP-Tool.** <br/> <br/> Gesamtbeträge aus unterschiedlichen Währungen würden im BEx Analyzer z.B. als „*“ angezeigt, aber der Gesamtbetrag würde von der öffentlichen SAP-Schnittstelle ohne den Hinweis zurückgegeben werden, dass eine derartige Aggregatzahl keine Bedeutung hat. Dementsprechend würde die Zahl (die z.B. USD, EUR und AUD aggregiert) in Power BI angezeigt werden. |
| Formatierung von Währungen |Währungsformatierungen (z.B. $2.300 oder 4.000 AUD) werden in Power BI nicht übernommen. |
| Maßeinheiten |Maßeinheiten (z.B 230 kg) werden in Power BI nicht übernommen. |
| Schlüssel versus Text (kurz, mittel, lang) |Die Feldliste zeigt für Cost Center (ein Merkmal von SAP BW) die einzelne Spalte „Cost Center“ an.  Wenn Sie die Spalte verwenden, wir ein Standardtext angezeigt.  Wenn Sie ausgeblendete Felder anzeigen, können Sie auch die Spalte mit den eindeutigen Namen anzeigen (die den eindeutigen von SAP BW zugewiesenen Namen zurückgibt und die Grundlage der Eindeutigkeit ist).<br/> <br/>  Der Schlüssel und andere Textfelder sind nicht verfügbar. |
| Mehrere Hierarchien eines Merkmals |In **SAP** kann ein Merkmal mehrere Hierarchien haben. Wenn ein Merkmal in Tools wie BEx Analyzer in eine Abfrage eingeschlossen wird, kann der Benutzer die zu verwendende Hierarchie auswählen. <br/> <br/> In **Power BI** werden die unterschiedlichen Hierarchien in der Feldliste als verschiedene Hierarchien der gleichen Dimension angezeigt.  Wenn Sie allerdings mehrere Ebenen von zwei verschiedenen Hierarchien der gleichen Dimension auswählen, führt dies dazu, dass leere Daten von SAP zurückgegeben werden. |
| Behandlung von unausgeglichenen Hierarchien |![](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| Skalierungsfaktor/Umkehrung des Vorzeichens |In SAP kann eine Kennzahl einen Skalierungsfaktor (z.B. 1000) haben, der als Formatierungsoption definiert ist, was bedeutet, dass die Anzeige anhand dieses Faktors skaliert wird. <br/> <br/> Ebenso kann für sie eine Eigenschaft festgelegt werden, die das Vorzeichen umkehrt. Wenn Sie eine solche Kennzahl in Power BI verwenden (z.B. in einem visuellen Element oder in einer Berechnung), wird die nicht skalierte Zahl verwendet (und das Vorzeichen wird nicht umgekehrt). Der zugrunde liegende Skalierungsfaktor steht nicht zur Verfügung. In visuellen Elementen von Power BI können die auf der Achse (K, M, B) angezeigten Skalierungseinheiten beim Formatieren des visuellen Elements gesteuert werden. |
| Hierarchien, in denen Ebenen dynamisch angezeigt/nicht mehr angezeigt werden |Wenn Sie zum ersten Mal eine Verbindung mit SAP BW herstellen, werden Informationen zu den Ebenen einer Hierarchie abgerufen, wodurch Felder in der Feldliste hinzugefügt werden. Dies wird zwischengespeichert, und wenn die Ebenen sich ändern, ändern sich die Felder erst dann, wenn sie aktualisiert werden. <br/> <br/> Dies ist nur in **Power BI Desktop** möglich. Nach der Veröffentlichung können derartige Aktualisierungen zum Übernehmen von Änderungen von Ebenen nicht mehr durchgeführt werden. |
| Standardfilter |Ein BEx-Filter kann Standardfilter beinhalten, die automatisch von BEx Analyzer von SAP angewendet werden. Diese werden nicht verfügbar gemacht, und deshalb werden beim entsprechenden Gebrauch in Power BI nicht standardmäßig die gleichen Filter angewendet. |
| Ausgeblendete Kennzahlen |Eine BEx-Abfrage kann die Sichtbarkeit von Kennzahlen steuern. Ausgeblendete Kennzahlen werden nicht im BEx Analyzer von SAP angezeigt. Dies wird nicht in der öffentlichen API widergespiegelt, und deshalb werden ausgeblendete Kennzahlen trotzdem in der Feldliste angezeigt. Sie können dann allerdings wieder in Power BI ausgeblendet werden. |
| Numerische Formatierung |Es werden nicht automatisch alle numerischen Formatierungen (Anzahl von Dezimalstellen, Dezimaltrennzeichen usw.) in Power BI übernommen. Allerdings ist es möglich, diese Formatierungen in Power BI anzupassen. |
| Versionskontrolle von Hierarchien |Mit SAP BW können verschiedenen Versionen einer Hierarchie verwaltet werden, z.B. die Cost Center-Hierarchie von 2007 und 2008. In Power BI steht nur die aktuellste Version zur Verfügung, da Informationen zu den Versionen nicht von der öffentlichen API verfügbar gemacht werden. |
| Zeitabhängige Hierarchien |Zeitabhängige Hierarchien werden in Power BI zur aktuellen Zeit ausgewertet. |
| Währungskonvertierung |SAP BW unterstützt die Währungskonvertierung auf Grundlage der im Cube enthaltenen Kurse. Diese Funktionen werde nicht von der öffentlichen API verfügbar gemacht und stehen deshalb auch nicht in Power BI zur Verfügung. |
| Sortierreihenfolge |Die Sortierreihenfolge (nach Text oder Schlüssel) für ein Merkmal kann in SAP definiert werden. Diese Sortierreihenfolge wird in Power BI nicht übernommen. Monate werden z.B. als „April“ oder „Aug“ angezeigt, usw. <br/> <br/> Es ist nicht möglich, die Sortierreihenfolge in Power BI zu ändern. |
| Technische Namen |Unter **Daten abrufen** werden sowohl die Namen (Beschreibungen) von Merkmalen/Measures als auch die technischen Namen angezeigt. Die Feldliste enthält nur die Namen (Beschreibungen) von Merkmalen/Measures. |
| Attribute |Es ist nicht möglich, in Power BI auf die Attribute eines Merkmals zuzugreifen. |
| Einstellung der Sprache des Endbenutzers |Das Gebietsschema, mit dem die Verbindung zu SAP BW hergestellt wird, wird im Rahmen der Verbindungsdetails festgelegt und spiegelt nicht das Gebietsschema des letztendlichen Berichtnutzers wieder. |
| Textvariablen |Mit SAP BW können Feldnamen Platzhalter für Variablen enthalten (z.B. „$JAHR$ Ist“), die später durch die ausgewählten Werte ersetzt werden. Das Feld wird z.B. als „2016 Actuals“ in BEx-Tools angezeigt, wenn das Jahr 2016 für die Variable ausgewählt ist. <br/> <br/> Der Spaltenname wird in Power BI nicht abhängig vom Variablenwert geändert und wird deshalb als „YEAR$ Actuals“ angezeigt.  Allerdings kann der Spaltenname dann in Power BI geändert werden. |
| Benutzerdefinierte Exit-Variablen | Benutzerdefinierte Exit-Variablen werden nicht von der öffentlichen API zur Verfügung gestellt und deshalb nicht von Power BI unterstützt. |
| Charakteristische Strukturen | Charakteristische Strukturen in der zugrunde liegenden SAP BW-Quelle führen zum explosionsartigen Verfügbarmachen von Measures in Power BI. Wenn beispielsweise die beiden Measures „Sales“ und „Costs“ vorliegen sowie eine charakteristische Struktur, die „Budget“ und „Actual“ enthält, werden vier Measures zur Verfügung gestellt: Sales.Budget, Sales.Actual, Costs.Budget, Costs.Actual. |


## <a name="next-steps"></a>Weitere Schritte
Weitere Informationen zu DirectQuery finden Sie in den folgenden Ressourcen:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data Sources supported by DirectQuery (Von DirectQuery unterstützte Datenquellen)](power-bi-data-sources.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
