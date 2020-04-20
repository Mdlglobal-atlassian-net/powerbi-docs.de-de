---
title: Verwenden von DirectQuery mit Power BI
description: Verstehen der Verwendung von DirectQuery mit Power BI und bewährte Methoden für die Verwendung von DirectQuery oder anderen Optionen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0f2d6bae607383eb8934b3f395add540c6754690
ms.sourcegitcommit: 915cb7d8088deb0d9d86f3b15dfb4f6f5b1b869c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2020
ms.locfileid: "81006708"
---
# <a name="about-using-directquery-in-power-bi"></a>Verwenden von DirectQuery in Power BI

Sie können eine Verbindung mit allen möglichen verschiedenen Datenquellen herstellen, wenn Sie  *Power BI Desktop* oder den *Power BI-Dienst* verwenden, und es gibt unterschiedliche Möglichkeiten, diese Datenverbindungen herzustellen. Sie können Daten in Power BI *importieren*, was die gängigste Methode ist, um Daten abzurufen. Alternativ können Sie eine Direktverbindung zu Daten im ursprünglichen Quellrepository herstellen, was als *DirectQuery* bekannt ist. Dieser Artikel beschreibt DirectQuery-Funktionen:

* Verschiedene Konnektivitätsoptionen für DirectQuery
* Leitfaden für die Situation, in der Sie DirectQuery dem Import vorziehen sollten
* Nachteile der Verwendung von DirectQuery
* Bewährte Methoden für die Verwendung von DirectQuery

Befolgen Sie bewährte Methoden für die Verwendung von Import und DirectQuery:

* Importieren Sie Dateien in Power BI, wann immer dies möglich ist. Das Importieren nutzt die leistungsstarke Abfrage-Engine von Power BI, und Sie erhalten eine hoch interaktive und vollständig ausgestattete Erfahrung.
* Wenn Ihre Ziele nicht durch den Import von Daten erreicht werden können, erwägen Sie, DirectQuery zu verwenden. DirectQuery ist womöglich die beste Wahl, wenn sich die Daten z.B. oft ändern und Berichte die neuesten Daten wiedergeben müssen. Die Verwendung von DirectQuery ist jedoch nur möglich, wenn die zugrunde liegende Datenquelle interaktive Abfragen (weniger als fünf Sekunden für die typische Aggregatabfrage) bereitstellen und die generierte Abfragelast verarbeiten kann. Darüber hinaus muss die Liste der Einschränkungen für die Verwendung von DirectQuery sorgfältig geprüft werden.

Die Reihe der Funktionen, die von Power BI für Import und DirectQuery angeboten wird, wird mit der Zeit weiterentwickelt. Änderungen umfassen die Bereitstellung einer erhöhten Flexibilität beim Verwenden importierter Daten, damit der Import in mehr Fällen genutzt werden kann. Es werden zudem einige Nachteile der Verwendung von DirectQuery beseitigt. Unabhängig von den Verbesserungen bleibt die Leistung der zugrunde liegenden Datenquelle bei Verwendung von DirectQuery immer ein wichtiger Gesichtspunkt. Wenn die zugrunde liegende Datenquelle langsam ist, kann DirectQuery für diese Quelle nicht verwendet werden.

Dieser Artikel behandelt DirectQuery mit Power BI und nicht *SQL Server Analysis Services*. DirectQuery ist auch ein Feature von SQL Server Analysis Services. Viele der in diesem Artikel beschriebenen Details gelten für dieses Feature. Es gibt jedoch auch wichtige Unterschiede. Informationen zur Verwendung von DirectQuery mit SQL Server Analysis Services finden Sie unter [DirectQuery in SQL Server 2016 Analysis Services](https://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).

Dieser Artikel konzentriert sich auf den empfohlenen Workflow für DirectQuery, wo der Bericht in Power BI Desktop erstellt wird, es wird aber auch die direkte Verbindung im Power BI-Dienst behandelt.

## <a name="power-bi-connectivity-modes"></a>Power BI-Konnektivitätsmodi

Power BI stellt eine Verbindung mit einer Vielzahl unterschiedlicher Datenquellen her, was Folgendes umfasst:

* Online-Dienste (Salesforce, Dynamics 365 und andere)
* Datenbanken (SQL Server, Access, Amazon Redshift, andere)
* Einfache Dateien (Excel, JSON, andere)
* Andere Datenquellen (Spark, Websites, Microsoft Exchange, andere)

Für diese Datenquellen können die Daten in Power BI importiert werden. Es ist auch möglich, eine Verbindung mithilfe von DirectQuery herzustellen. Eine Übersicht über die Datenquellen, die DirectQuery unterstützen, finden Sie unter [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md). Viele Quellen werden in Zukunft für DirectQuery aktiviert, wobei man sich hauptsächlich auf Quellen konzentriert, von denen man erwarten kann, dass sie eine gute interaktive Abfrageleistung abliefern.

SQL Server Analysis Services ist ein Sonderfall. Beim Herstellen einer Verbindung mit SQL Server Analysis Services können Sie auswählen, die Daten zu importieren oder eine *Liveverbindung* zu nutzen. Die Verwendung einer Liveverbindung ist ähnlich wie DirectQuery. Es werden keine Daten importiert und die zugrunde liegende Datenquelle wird immer abgefragt, um ein visuelles Element zu aktualisieren. Eine Liveverbindung ist in vielerlei Hinsicht anders, daher wird ein anderer Begriff verwendet: *Liveverbindung* versus *DirectQuery*.

Die drei Optionen zum Herstellen einer Verbindung zu Daten sind: *Importieren*, *DirectQuery* und *Liveverbindung*.

### <a name="import-connections"></a>Importieren von Verbindungen

Wenn Sie zum Importieren die Option **Daten abrufen** in Power BI Desktop verwenden, um eine Verbindung zu einer Datenquelle wie SQL Server herzustellen, ist das Verhalten dieser Verbindung wie folgt:

* Während der ersten Erfahrung mit dem Abrufen von Daten definieren die ausgewählten Tabellen jeweils eine Abfrage, die eine Reihe von Daten zurückgeben wird. Diese Abfragen können vor dem Laden der Daten bearbeitet werden, um z. B. Filter anzuwenden, die Daten zu aggregieren oder verschiedene Tabellen zu verknüpfen.
* Nach dem Laden werden alle durch diese Abfragen definierten Daten in den Power BI-Cache importiert.
* Beim Erstellen eines visuellen Elements in Power BI Desktop werden die importierten Daten abgefragt. Der Power BI-Speicher sorgt für eine schnelle Abfrage. Alle Änderungen am visuellen Element werden sofort wiedergegeben.
* Änderungen an den zugrunde liegenden Daten werden in keinem visuellen Element wiedergegeben. Zum erneuten Importieren von Daten ist eine *Aktualisierung* erforderlich.
* Beim Veröffentlichen des Berichts als *PBIX-Datei* im Power BI-Dienst wird ein Dataset erstellt und in den Power BI-Dienst hochgeladen. Die importierten Daten ist in diesem Dataset enthalten. Es ist dann möglich, eine Aktualisierung der Daten zu planen, um die Daten z. B. jeden Tag neu zu importieren. Abhängig vom Speicherort der ursprünglichen Datenquelle ist es möglicherweise erforderlich, ein lokales Datengateway zu konfigurieren.
* Beim Öffnen eines vorhandenen Berichts im Power BI-Dienst oder beim Erstellen eines neuen Berichts werden die importierten Daten erneut abgefragt, wodurch die Interaktivität sichergestellt wird.
* Visuelle Elemente oder die gesamten Berichtsseiten können als Dashboardkacheln angeheftet werden. Die Kacheln werden automatisch aktualisiert, sobald das zugrunde liegende Dataset aktualisiert wird.

### <a name="directquery-connections"></a>DirectQuery-Verbindungen

Wenn Sie **Daten abrufen** für DirectQuery in Power BI Desktop verwenden, um eine Verbindung zu einer Datenquelle herzustellen, ist das Verhalten dieser Verbindung wie folgt:

* Während der anfänglichen Erfahrung von „Daten abrufen“ wird die Quelle ausgewählt. Für relationale Datenquellen wird ein Satz von Tabellen ausgewählt, und jede Tabelle definiert weiterhin eine Abfrage, die logisch einen Satz von Daten zurückgibt. Für mehrdimensionale Datenquellen wie SAP BW wird nur die Quelle ausgewählt.
* Beim Laden werden jedoch keine Daten in den Power BI-Speicher importiert. Stattdessen werden nach der Erstellung eines visuellen Elements in Power BI Desktop Abfragen an die zugrunde liegende Datenquelle gesendet, um die erforderlichen Daten abzurufen. Die Zeit, die für die Aktualisierung des visuellen Elements benötigt wird, hängt von der Leistung der zugrunde liegenden Datenquelle ab.
* Alle Änderungen an den zugrunde liegenden Daten werden nicht sofort in jedem vorhandenen visuellen Element wiedergegeben. Eine Aktualisierung ist trotzdem erforderlich. Die erforderlichen Abfragen werden für jedes visuelle Element erneut gesendet, und das visuelle Element wird bei Bedarf aktualisiert.
* Nach dem Veröffentlichen des Berichts im Power BI-Dienst ergibt sich erneut ein Dataset im Power BI-Dienst, genau wie beim Import. Allerdings sind in diesem Dataset *keine Daten* enthalten.
* Beim Öffnen eines vorhandenen Bericht oder beim Erstellen eines neuen im Power BI-Dienst wird die zugrunde liegende Datenquelle erneut abgefragt, um die benötigten Daten abzurufen. Abhängig vom Speicherort der ursprünglichen Datenquelle ist es möglicherweise erforderlich, ein lokales Datengateway zu konfigurieren. Dieses wird ebenso für den Importmodus benötigt, wenn die Daten aktualisiert werden.
* Visuelle Elemente oder die gesamten Berichtsseiten können als Dashboardkacheln angeheftet werden. Um sicherzustellen, dass das Öffnen eines Dashboards schnell ausgeführt wird, werden die Kacheln nach einem Zeitplan automatisch aktualisiert, z. B. einmal pro Stunde. Die Häufigkeit dieser Aktualisierung kann gesteuert werden, um widerzuspiegeln, wie oft sich die Daten ändern und wie wichtig es ist, die neuesten Daten zu sehen. Die Kacheln geben beim Öffnen eines Dashboards die Daten zum Zeitpunkt der letzten Aktualisierung wider und nicht unbedingt die neuesten Änderungen, die an der zugrunde liegenden Quelle vorgenommen wurden. Sie können ein geöffnetes Dashboard aktualisieren, um sicherzustellen, dass es aktuell ist.

### <a name="live-connections"></a>Liveverbindungen

Beim Herstellen einer Verbindung mit SQL Server Analysis Services besteht die Option zum Importieren von Daten aus oder zum Herstellen einer Liveverbindung zum ausgewählten Datenmodell. Wenn Sie sich für das Importieren entscheiden, definieren Sie eine Abfrage für die externe SQL Server Analysis Services-Quelle, und die Daten werden als „normal“ importiert. Wenn Sie „Live verbinden“ verwenden, gibt es keine definierte Abfrage, und das gesamte externe Modell wird in der Feldliste angezeigt.

Die im vorherigen Absatz beschriebene Situation gilt auch für das Herstellen einer Verbindung mit den folgenden Quellen, mit dem Unterschied, dass es keine Option zum Importieren der Daten gibt:

* Power BI-Datasets, z. B. beim Herstellen einer Verbindung zu einem Power BI-Dataset, das zuvor erstellt und im Dienst veröffentlicht wurde, und um einen neuen Bericht darüber zu erstellen.
* Common Data Services.

Das Verhalten von Berichten via SQL Server Analysis Services nach der Veröffentlichung im Power BI-Dienst ist den DirectQuery-Berichten in folgenden Punkten ähnlich:

* Beim Öffnen eines vorhandenen Berichts im Power BI-Dienst oder beim Schreiben eines neuen Berichts wird die zugrunde liegende SQL Server Analysis Services-Quelle abgefragt, wobei möglicherweise ein lokales Datengateway erforderlich ist.
* Dashboardkacheln werden automatisch nach einem Zeitplan aktualisiert, z. B. einmal pro Stunde.

Es gibt jedoch auch wichtige Unterschiede. Bei Liveverbindungen wird die Identität des Benutzers, der den Bericht öffnet, immer an die zugrunde liegende SQL Server Analysis Services-Quelle übermittelt.

Schieben wir nun diese Vergleiche beiseite und konzentrieren uns im restlichen Artikel nur auf DirectQuery.

## <a name="when-is-directquery-useful"></a>Wann ist DirectQuery sinnvoll?

In der folgenden Tabelle werden Szenarien beschrieben, in denen eine Verbindung mit DirectQuery besonders nützlich sein könnte. Sie umfasst Fälle, in denen es als vorteilhaft angesehen würde, die Daten in der ursprünglichen Quelle zu belassen. Die Beschreibung umfasst eine Diskussion darüber, ob das angegebene Szenario in Power BI verfügbar ist.

| Einschränkung | Beschreibung |
| --- | --- |
| Daten werden häufig geändert, und es ist eine Berichterstellung erforderlich, die näher an der Echtzeit ist. |Modelle mit importierten Daten können höchstens einmal pro Stunde aktualisiert werden (häufigere Aktualisierungen sind mit einem Power BI Pro- oder Power BI Premium-Abonnement möglich). Wenn sich die Daten kontinuierlich ändern, und Berichte die neuesten Daten zeigen müssen, ist die Verwendung des Imports mit geplanter Aktualisierung womöglich nicht für Anforderungen dieser Art geeignet. Sie können Daten direkt in Power BI streamen. Es gibt jedoch Grenzwerte für die unterstützten Datenvolumes. <br/> <br/> Wenn Sie im Gegensatz dazu DirectQuery verwenden, bedeutet dies, dass beim Öffnen oder Aktualisieren eines Berichts oder Dashboards immer die neuesten Daten in der Datenquelle angezeigt werden. Darüber hinaus können die Dashboardkacheln häufiger aktualisiert werden, bis hin zu alle 15 Minuten. |
| Die Datenmenge ist sehr groß |Wenn die Daten sehr groß sind, ist es nicht praktikabel, alle zu importieren. DirectQuery erfordert im Gegensatz dazu keinen großen Datentransfer, da die Abfrage direkt durchgeführt wird. <br/> <br/> Jedoch implizieren große Daten auch, dass die Leistung der Abfragen für die zugrunde liegende Quelle zu langsam ist, wie unter [Auswirkungen der Verwendung von DirectQuery](#implications-of-using-directquery) erläutert. Sie müssen nicht immer die vollständigen Detaildaten importieren. Stattdessen können die Daten während des Imports vorab aggregiert werden. Mit dem *Abfrage-Editor* können Sie während des Imports leicht die vorab erforderliche Aggregation durchführen. Im Extremfall wäre es möglich, genau die aggregierten Daten zu importieren, die für jedes Visual benötigt werden. Obwohl DirectQuery die einfachste Möglichkeit für große Daten ist, kann das Importieren von Aggregatdaten möglicherweise eine Lösung bieten, wenn die zugrunde liegende Quelle zu langsam ist. |
| Sicherheitsregeln werden in der zugrunde liegenden Datenquelle definiert |Wenn die Daten importiert werden, verbindet sich Power BI entweder über die aktuellen Anmeldeinformationen des Benutzers über Power BI Desktop oder mit den Anmeldeinformationen, die Teil der Konfigurierung der geplanten Aktualisierung sind (über Power BI), mit der Datenquelle. Wenn solch ein Bericht veröffentlicht und freigegeben wird, müssen Sie Sorgfalt walten lassen, damit dieser nur mit Benutzern geteilt wird, die dieselben Daten sehen dürfen oder dass Sicherheit auf Zeilenebene als Teil des Dataset definiert ist. <br/> <br/> Da DirectQuery immer die zugrunde liegende Datenquelle abfragt, würde diese Konfiguration im Idealfall jede Sicherheitsmaßnahme in dieser zugrunde liegenden Quelle zulassen, die angewendet werden soll. Allerdings stellt Power BI derzeit immer eine Verbindung mit der zugrunde liegenden Quelle mithilfe der gleichen Anmeldeinformationen her, die auch für den Import verwendet werden würden. <br/> <br/> Bis Power BI zulässt, dass die Identität des Berichtsconsumers an die zugrunde liegende Quelle übermittelt wird, bietet DirectQuery also keine Vorteile für die Datenquellensicherheit. |
| Einschränkungen der Datensouveränität gelten |Einige Organisationen verfügen über Richtlinien zur Datensouveränität, d. h., dass Daten die Organisation nicht verlassen können. Eine Lösung, die auf Import basiert, würde ganz klar Probleme darstellen. Im Gegensatz dazu verbleiben Daten mit DirectQuery in der zugrunde liegenden Quelle. <br/> <br/> Sogar mit DirectQuery werden einige Caches von Daten auf der visuellen Ebene im Power BI-Dienst aufgrund einer geplanten Aktualisierung von Kacheln beibehalten. |
| Die zugrunde liegende Datenquelle ist eine OLAP-Quelle und enthält Measures |Wenn die zugrunde liegende Datenquelle *Measures* enthält, z. B. SAP HANA oder SAP Business Warehouse, dann führt das Importieren der Daten zu anderen Problemen. Dies bedeutet, dass sich die importierten Daten auf einer bestimmten Aggregationsebene befinden, so wie von der Abfrage definiert. Ein Beispiel sind die Measures **TotalSales** nach **Class**, **Year** und **City**. Wenn ein visuelles Element erstellt und nach höher aggregierten Daten gefragt wird, z. B. **TotalSales** nach **Year**, wird der Aggregatwert weiter aggregiert. Für additive Measures wie **Sum** und **Min** ist diese Aggregation kein Problem. Für nicht additive Measure, z. B. **Average**, **DistinctCount**, kann dies ein Problem darstellen. <br/> <br/> Um das Abrufen der korrekten Aggregatdaten, die für ein bestimmtes visuelles Element benötigt werden, direkt aus der Quelle zu vereinfachen, wäre es notwendig, Abfragen per visuellem Element zu senden, so wie in DirectQuery. <br/> <br/> Beim Verbindungsaufbau zu SAP Business Warehouse (BW) ermöglicht die Auswahl von DirectQuery diese Behandlung von Measures. Weitere Informationen zu SAP BW finden Sie unter [DirectQuery und SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> Allerdings wird die Datenquelle derzeit von DirectQuery via SAP HANA genauso wie eine relationale Quelle behandelt, was sich beim Verhalten für den Import widerspiegelt. Dieser Ansatz wird unter [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md) weiter beschrieben. |

Zusammenfassend kann festgestellt werden, dass DirectQuery in Power BI mit seinen aktuellen Möglichkeiten in den folgenden Szenarien Vorteile bietet:

* Daten werden häufig geändert, und es ist eine Berichterstellung erforderlich, die näher an der „Echtzeit“ ist.
* Behandlung von sehr großen Datenmengen, ohne die Notwendigkeit, vorab zu aggregieren.
* Einschränkungen der Datensouveränität gelten.
* Die Quelle ist eine multidimensionale Quelle mit Measures, z. B. SAP BW.

Die Details in der vorherigen Liste beziehen sich auf die Verwendung von Power BI allein. Stattdessen könnten Sie ein externes SQL Server Analysis Services- oder Azure Analysis Services-Modell verwenden, um Daten zu importieren. Verwenden Sie dann Power BI, um eine Verbindung mit diesem Modell herzustellen. Während dieser Ansatz eine zusätzliche Konfiguration erfordern würde, bietet er jedoch größere Flexibilität. Es können wesentlich größere Datenmengen importiert werden. Es gibt keine Einschränkung, wie oft die Daten aktualisiert werden können.

## <a name="implications-of-using-directquery"></a>Auswirkungen der Verwendung von DirectQuery

Die Verwendung von DirectQuery hat negative Auswirkungen, die in diesem Abschnitt aufgeführt sind. Einige dieser Einschränkungen unterscheiden sich geringfügig je nach der genauen Quelle, die verwendet wird. Wir gehen auf Einschränkungen ein, wo dies zutrifft, und separate Artikel behandeln diese Quellen, die sich wesentlich unterscheiden.

### <a name="performance-and-load-on-the-underlying-source"></a>Leistung von und Last auf der zugrunde liegenden Quelle

Bei Verwendung von DirectQuery hängt die allgemeine Erfahrung sehr von der Leistung der zugrunde liegenden Datenquelle ab. Wenn das Aktualisieren jedes visuellen Elements, z. B. nach dem Ändern eines Slicerwerts, einige Sekunden dauert (normalerweise weniger als fünf Sekunden), wäre die Erfahrung angemessen. Die Erfahrung könnte sich im Vergleich zur sofortigen Reaktion beim Importieren der Daten in Power BI als zu langsam anfühlen. Wenn die Langsamkeit der Quelle dazu führt, dass einzelne visuelle Elemente länger als zehn Sekunden dauern, wird die Erfahrung äußerst schlecht. Abfragen können sogar ein Timeout bewirken.

Achten Sie neben der Leistung der zugrunde liegenden Quelle auch auf die Auslastung der Quelle. Die Auslastung wirkt sich auf die Leistung aus. Jeder Benutzer, der einen gemeinsamen Bericht öffnet, und jede Dashboardkachel, die aktualisiert wird, sendet mindestens eine Abfrage pro visuellem Element an die zugrunde liegende Quelle. Dies erfordert, dass die Quelle solch eine Abfragelast verarbeiten kann, während sie gleichzeitig eine akzeptable Leistung beibehält.

### <a name="security-implications-when-combining-data-sources"></a>Auswirkungen auf die Sicherheit, wenn Datenquellen kombiniert werden

In einem DirectQuery-Modell können, so wie beim Importieren von Daten, mehrere Datenquellen verwendet werden, indem mit [zusammengesetzten Modellen](desktop-composite-models.md) gearbeitet wird. Wenn Sie mehrere Datenquellen verwenden, ist es wichtig zu verstehen, wie Daten zwischen den zugrunde liegenden Datenquellen ausgetauscht werden und welche [Auswirkungen auf die Sicherheit](desktop-composite-models.md#security-implications) daraus resultieren.

### <a name="limited-data-transformations"></a>Begrenzte Datentransformationen

Es bestehen ähnliche Einschränkungen bei Datentransformationen, die innerhalb des Abfrage-Editors angewendet werden können. Mit importierten Daten kann eine ausgefeilte Reihe von Transformationen einfach angewendet werden, um die Daten zu bereinigen und neu zu gestalten, bevor diese zum Erstellen von visuellen Elementen verwendet werden, z. B. JSON-Dokumente analysieren oder Daten aus einer Spalte in eine Zeilenform pivotieren. Diese Transformationen sind in DirectQuery beschränkter.

Zunächst können beim Herstellen einer Verbindung zu einer OLAP-Quelle wie SAP Business Warehouse gar keine Transformationen definiert werden, und das gesamte externe Modell wird aus der Quelle übernommen. Für relationale Quellen wie SQL Server ist es noch immer möglich, mehrere Transformationen pro Abfrage zu bestimmen. Diese Transformationen sind jedoch aus Leistungsgründen eingeschränkt.

All diese Transformationen müssen auf jede Abfrage für die zugrunde liegende Quelle und nicht nur einmal auf die Datenaktualisierung angewendet werden, damit sie auf die Transformationen beschränkt sind, die halbwegs in eine einzelne native Abfrage übertragen werden können. Wenn Sie eine Transformation verwenden, die zu komplex ist, erhalten Sie einen Fehler, der angibt, dass sie entweder gelöscht oder das Modell in den Importmodus versetzt werden muss.

Zusätzlich wird die Abfrage, die sich aus dem Dialogfeld **Daten abrufen** oder Abfrage-Editor ergibt, in einem untergeordneten SELECT-Ausdruck zusammen mit den generierten Abfragen verwendet und versendet, um die erforderlichen Daten für das visuelle Element zu empfangen. Die im Abfrage-Editor definierte Abfrage muss in diesem Kontext gültig sein. Es ist insbesondere weder möglich, eine Abfrage mithilfe von allgemeinen Tabellenausdrücken zu verwenden, noch eine Abfrage, die gespeicherte Prozeduren aufruft.

### <a name="modeling-limitations"></a>Modellierungseinschränkungen

Der Begriff *Modellierung* bezeichnet in diesem Kontext den Vorgang zum Verfeinern und Anreichern der Rohdaten im Rahmen der Erstellung von Berichten, in denen sie verwendet werden. Beispiele:

* Definieren von Beziehungen zwischen Tabellen
* Hinzufügen von neuen Berechnungen (berechnete Spalten und Measures)
* Umbenennen und Ausblenden von Spalten und Measures
* Definieren von Hierarchien
* Definieren der Formatierung, Standardzusammenfassung und Sortierreihenfolge für eine Spalte
* Gruppierungs- oder Clusterwerte

Wenn Sie DirectQuery verwenden, können viele dieser Modellanreicherungen noch immer vorgenommen werden, und es existiert sicherlich noch immer das Prinzip, dass die Rohdaten angereichert werden, um den späteren Verbrauch zu verbessern. Allerdings sind einige Modellierungsfunktionen bei der Verwendung von DirectQuery überhaupt nicht oder nur eingeschränkt verfügbar. Im Allgemeinen werden Einschränkungen angewendet, um Leistungsprobleme zu vermeiden. Die Einschränkungen, die häufig für DirectQuery-Quellen angewendet werden, sind hier aufgeführt. Für einzelne Quellen können zusätzliche Einschränkungen gelten, wie in [Nächste Schritte](#next-steps) beschrieben.

* **Keine integrierte Datumshierarchie:** Wenn Sie Daten importieren, erhält jede date/datetime-Spalte eine integrierte Datumshierarchie, die standardmäßig verfügbar ist. Wenn Sie z.B. eine Tabelle mit Verkaufsaufträgen importieren, die eine Spalte **OrderDate** enthält, dann wird es vor der Verwendung von **OrderDate** in einem visuellen Element möglich sein, die zugehörige Ebene auszuwählen (Jahr, Monat, Tag), die verwendet werden soll. Diese integrierte Datumshierarchie ist nicht verfügbar, wenn Sie DirectQuery verwenden. Die DAX Time Intelligence-Funktionen können ganz normal verwendet werden, wenn eine **Datumstabelle** in der zugrunde liegenden Quelle verfügbar ist, wie es in vielen Data Warehouses üblich ist.
* **Datums-/Zeitunterstützung nur bis zur zweiten Genauigkeit:** Wenn Sie Zeitspalten in Ihrem Dataset verwenden, gibt Power BI nur Abfragen an die zugrunde liegende Quelle mit einem Detaillierungsgrad von Sekunden aus. Abfragen werden für Millisekunden nicht an die DirectQuery-Quelle gesendet. Entfernen Sie diesen Teil der Zeiten aus Ihren Quellspalten.
* **Einschränkungen in berechneten Spalten:** Berechnete Spalten sind darauf beschränkt, dass sie zeilenintern sind. Das bedeutet, dass sie sich nur auf Werte anderer Spalten derselben Tabelle beziehen können, ohne Aggregatfunktionen zu verwenden. Zusätzlich sind die erlaubten DAX-Skalarfunktionen, z. B. `LEFT()`, auf die Funktionen beschränkt, die per Push an die zugrunde liegende Quelle gesendet werden können. Die Funktionen variieren je nach den genauen Möglichkeiten der Quelle. Nicht unterstützte Funktionen werden nicht in AutoVervollständigen aufgelistet, wenn DAX für eine berechnete Tabelle erstellt wird, und würden bei Benutzung einen Fehler auslösen.
* **Keine Unterstützung für über- und untergeordnete DAX-Funktionen:** Wenn Sie sich im DirectQuery-Modus befinden, ist die Verwendung der `DAX PATH()`-Funktionsfamilie nicht möglich, die normalerweise die Strukturen der über- und untergeordneten Funktionen behandeln, etwa als Kontenplan oder Mitarbeiterhierarchien.
* **Berechnete Tabellen werden nicht unterstützt:** Die Möglichkeit zum Definieren einer berechneten Tabelle mithilfe eines DAX-Ausdrucks wird im DirectQuery-Modus nicht unterstützt.
* **Filtern von Beziehungen:** Informationen zur bidirektionalen Filterung finden Sie unter [Bidirektionale Kreuzfilterung](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx). Dieses Whitepaper stellt Beispiele im Zusammenhang mit SQL Server Analysis Services vor. Die grundlegenden Punkte gelten gleichermaßen für Power BI.
* **Kein Clustering:** Bei Verwendung von DirectQuery ist es nicht möglich, die Clusteringfunktion zu verwenden, um Gruppen automatisch zu suchen.

### <a name="reporting-limitations"></a>Einschränkungen bei der Berichterstattung

Fast alle Berichtsfunktionen werden für DirectQuery-Modelle unterstützt. Daher ist es möglich, solange die zugrunde liegenden Datenquelle ein geeignetes Maß an Leistung bietet, den gleichen Satz von Visualisierungen zu verwenden. Es gibt einige wichtigen Einschränkungen in einigen der anderen Funktionen des Power BI-Diensts, nachdem ein Bericht veröffentlicht wird:

* **Quick Insights wird nicht unterstützt:** Power BI Quick Insights durchsucht verschiedene Teilmengen des Datasets unter Verwendung eines hoch entwickelten Algorithmus, um möglicherweise interessante Erkenntnisse zu gewinnen. Da sehr leistungsstarke Abfragen vonnöten sind, ist diese Fähigkeit nicht für Datasets mit DirectQuery verfügbar.
* **Q&A wird nicht unterstützt:** Power BI Q&A ermöglicht Ihnen, Ihre Daten mithilfe intuitiver Möglichkeiten der natürlichen Sprache zu untersuchen und die entsprechenden Antworten in Form von Diagrammen und Grafiken zu erhalten. Jedoch wird dies derzeit nicht für Datasets mit DirectQuery unterstützt.
* **Die Verwendung von „In Excel untersuchen“ führt wahrscheinlich zu einer schlechteren Leistung:** Sie können Ihre Daten untersuchen, indem Sie die Funktion „Explore in Excel“ (In Excel untersuchen) verwenden. Durch diesen Ansatz können PivotTables und PivotCharts in Excel erstellt werden. Diese Funktion wird für Datasets mit DirectQuery unterstützt, die Leistung ist aber generell langsamer als beim Erstellen von visuellen Elementen in Power BI. Deshalb ist die Verwendung von Excel für Ihre Szenarios wichtig, darum sollten Sie diesen Punkt bei Ihrer Entscheidung, DirectQuery zu verwenden, bedenken.

### <a name="security"></a>Sicherheit

Wie weiter oben in diesem Artikel erläutert, wird ein Bericht in DirectQuery nach dem Veröffentlichen für den Power BI-Dienst immer dieselben festen Anmeldeinformationen zum Herstellen der Verbindung mit der zugrunde liegenden Datenquelle verwenden. Dieses Verhalten gilt für DirectQuery, nicht für Liveverbindungen zu SQL Server Analysis Services, was sich in dieser Hinsicht unterscheidet. Es ist sofort nach Veröffentlichung eines DirectQuery-Berichts notwendig, die Anmeldeinformationen des Benutzers zu konfigurieren, die verwendet werden. Bis Sie die Anmeldeinformationen konfigurieren, würde das Öffnen des Berichts über den Power BI-Dienst zu einem Fehler führen.

Sobald die Anmeldeinformationen des Benutzers bereitgestellt werden, werden diese verwendet, *ungeachtet vom Benutzer, der den Bericht öffnet*. Auf diese Weise verhält es sich genau wie bei importierten Daten. Jeder Benutzer sieht dieselben Daten, es sei denn, es wurde eine Sicherheit auf Zeilenebene als Teil des Berichts definiert. Die gleiche Aufmerksamkeit muss dem Freigeben des Berichts gelten, falls Sicherheitsregeln in der zugrunde liegenden Quelle definiert sind.

### <a name="behavior-in-the-power-bi-service"></a>Verhalten im Power BI-Dienst

Dieser Abschnitt beschreibt das Verhalten eines DirectQuery-Berichts im Power BI-Dienst, um den Grad an Last zu erläutern, die auf die Back-End-Datenquelle ausgeübt wird, angesichts der Anzahl der Benutzer, für die der Bericht und das Dashboard gemeinsam genutzt werden, der Komplexität des Berichts und der Frage, ob Sicherheit auf Zeilenebene im Bericht definiert wurde.

#### <a name="reports--opening-interacting-with-editing"></a>Berichte öffnen, mit ihnen interagieren, sie bearbeiten

Wenn ein Bericht geöffnet ist, werden alle visuellen Elemente auf der aktuell sichtbaren Seite aktualisiert. Jedes visuelle Element erfordert in der Regel mindestens eine Abfrage für die zugrunde liegenden Datenquelle. Einige visuelle Elemente erfordern möglicherweise mehr als eine Abfrage. Ein visuelles Element kann z. B. aggregierte Werte aus zwei verschiedenen Faktentabellen anzeigen oder ein komplexeres Measure oder die Summe eines nicht additiven Measure wie Count Distinct enthalten. Wenn Sie auf eine neue Seite wechseln, werden diese visuellen Elemente aktualisiert. Bei der Aktualisierung wird ein neuer Satz von Abfragen an die zugrunde liegende Quelle gesendet.

Jedes Eingreifen des Benutzers in den Bericht führt möglicherweise dazu, dass visuelle Elemente aktualisiert werden. Wenn Sie z. B. einen anderen Wert auf einem Datenschnitt auswählen, müssen Sie eine neue Reihe von Abfragen senden, um alle betroffenen visuellen Elemente zu aktualisieren. Dasselbe gilt für das Klicken auf ein visuelles Element, um andere visuelle Elemente hervorzuheben oder einen Filter zu ändern.

In ähnlicher Weise erfordert die Bearbeitung eines neuen Berichts das Senden von Abfragen für jeden Schritt auf dem Weg zur Erstellung des endgültigen visuellen Elements.

Es erfolgt eine Zwischenspeicherung der Ergebnisse. Die Aktualisierung eines visuellen Elements erfolgt augenblicklich, wenn vor kurzem genau dieselben Ergebnisse erzielt wurden. Wenn keine Sicherheit auf Zeilenebene definiert ist, werden solche Caches nicht von den Benutzern gemeinsam genutzt.

#### <a name="dashboard-refresh"></a>Dashboardaktualisierung

Einzelne visuelle Elemente oder die gesamte Seiten können als Kacheln an das Dashboard angeheftet werden. Die auf den DirectQuery-Datasets basierenden Kacheln werden automatisch nach einem Zeitplan aktualisiert. Kacheln senden Abfragen an die Back-End-Datenquelle. Standardmäßig werden Datasets einmal pro Stunde aktualisiert, können aber als Teil der Dataset-Einstellungen für einen Zeitraum zwischen „Wöchentlich“ oder „Alle 15 Minuten“ konfiguriert werden.

Wenn keine Sicherheit auf Zeilenebene im Modell definiert ist, wird jede Kachel einmal aktualisiert und die Ergebnisse werden für alle Benutzer freigegeben. Andernfalls kann sich ein großer Multiplikatoreffekt ergeben. Jede Kachel erfordert separate Abfragen pro Benutzer, die an die zugrunde liegende Quelle gesendet werden müssen.

Ein Dashboard mit zehn Kacheln, das mit 100 Benutzern geteilt und auf einem Dataset mit DirectQuery mit Sicherheit auf Zeilenebene erstellt wird, und so konfiguriert ist, dass es alle 15 Minuten aktualisiert wird, würde alle 15 Minuten zum Senden von mindestens 1000 Abfragen an die Back-End-Quelle führen.

Achten Sie sorgfältig auf die Verwendung der Sicherheit auf Zeilenebene und die Konfiguration des Aktualisierungszeitplans.

#### <a name="time-outs"></a>Timeouts

Ein Timeout von vier Minuten wird für einzelne Abfragen für den Power BI-Dienst angewendet. Abfragen, die mehr Zeit benötigen, schlagen fehl. Wie bereits erwähnt, wird empfohlen, DirectQuery für Quellen zu verwenden, die eine nahezu interaktive Abfrageleistung bieten. Diese Einschränkung soll verhindern, dass Probleme durch zu lange Ausführungszeiten entstehen.

### <a name="other-implications"></a>Andere Auswirkungen

Einige allgemeine Auswirkungen der Verwendung von DirectQuery sind die folgenden:

* **Wenn sich Daten ändern, ist es notwendig, eine Aktualisierung durchzuführen, damit die neuesten Daten angezeigt werden:** Hinsichtlich der Verwendung von Caches gibt es keine Garantie, dass das visuelle Element immer die neuesten Daten anzeigt. Ein visuelles Element kann möglicherweise die Transaktionen des letzten Tags anzeigen. Da ein Slicer geändert wird, kann ein visuelles Element aktualisiert werden, damit es die Transaktionen der letzten zwei Tage anzeigt. Die Transaktionen könnten neuere, neu eingetroffene Transaktionen umfassen. Die Umwandlung des Slicers in seinen ursprünglichen Wert würde dazu führen, dass wieder die zuvor abgerufenen zwischengespeicherten Werte angezeigt werden.

  Wenn Sie **Aktualisieren** auswählen, werden sämtliche Caches geleert, und alle visuellen Elemente auf der Seite werden aktualisiert, damit sie die neuesten Daten anzeigen.

* **Wenn Daten geändert werden, besteht keine Garantie der Konsistenz zwischen visuellen Elementen:** Andere Visuals, egal ob auf derselben Seite oder auf verschiedenen Seiten, werden möglicherweise zu unterschiedlichen Zeiten aktualisiert. Wenn die Daten in der zugrunde liegenden Quelle geändert werden, kann nicht garantiert werden, dass jedes visuelle Elemente die Daten zu exakt demselben Zeitpunkt anzeigt. Wenn tatsächlich davon ausgegangen wird, dass manchmal mehr als eine Abfrage für ein einzelnes visuelles Element benötigt wird, z. B. um die Details und Gesamtwerte abzurufen, kann die Konsistenz auch für ein einzelnes visuelles Element nicht garantiert werden. Damit diese Konsistenz gewährleistet werden kann, ist sobald ein visuelles Element aktualisiert wird, der Aktualisierungsaufwand aller visuellen Elemente erforderlich, zusammen mit dem Gebrauch der zahlungspflichtigen Funktionen wie der Momentaufnahmeisolation in der zugrunde liegenden Quelle.

  Dieses Problem kann weitgehend minimiert werden, indem Sie erneut **Aktualisieren** auswählen, wodurch alle visuellen Elemente auf der Seite aktualisiert werden. Auch wenn Sie den Importmodus verwenden, gibt es ein ähnliches Problem für die Garantie der Konsistenz, wenn Sie Daten aus mehr als einer Tabelle importieren.

* **Die Aktualisierung in Power BI Desktop ist notwendig, um Änderungen bei Metadaten widerzuspiegeln:** Nachdem ein Bericht veröffentlicht wurde, werden die visuellen Elemente im Bericht **aktualisiert**. Wenn das Schema der zugrunde liegenden Datenquelle geändert wurde, werden diese Änderungen nicht automatisch übernommen, um die verfügbaren Felder in der Feldliste zu ändern. Wenn Tabellen oder Spalten aus der zugrunde liegenden Datenquelle entfernt wurden, kann es dazu kommen, dass die Abfrage bei der Aktualisierung fehlschlägt. Wenn Sie einen Bericht in Power BI Desktop öffnen und **Aktualisieren** auswählen, werden die Felder im Modell aktualisiert, um die Änderungen anzuzeigen.

* **Beschränkung von einer Millionen Zeilen, die auf eine beliebige Abfrage zurückgegeben werden:** Für die Anzahl von Zeilen, die in einer einzelnen Abfrage an die zugrunde liegende Quelle zurückgegeben werden, gibt es eine festgelegte maximale Anzahl von einer Million Zeilen. Diese Beschränkung hat in der Regel keine praktische Auswirkung, und visuelle Elemente werden selbst nicht so viele Punkte anzeigen. Allerdings kann die Begrenzung in Fällen auftreten, in denen Power BI die gesendeten Abfragen nicht vollständig optimiert und Zwischenergebnisse angefragt werden, die diese Begrenzung übersteigen. Sie kann auch während der Erstellung eines visuellen Elements auf dem Pfad zu einem akzeptableren Endzustand auftreten. Beispielsweise würde das Einschließen von **Customer** und **TotalSalesQuantity** diese Begrenzung erreichen, falls es mehr als eine Million Kunden gibt, bis einige Filter angewendet werden.

  Der zurückgegebene Fehler wäre: „Das Resultset einer Abfrage einer externen Datenquelle hat die maximal zulässige Größe von '1000000' Zeilen überschritten.“

* **Ein Wechsel vom Import- in den DirectQuery-Modus ist nicht möglich:** Auch wenn es möglich ist, ein Modell vom DirectQuery- auf den Importmodus umzustellen, müssen dazu alle nötigen Daten importiert werden. Es ist auch nicht möglich, in den anderen Modus zurück zu wechseln. Dies liegt an den Features, die nicht im DirectQuery-Modus unterstützt werden. Aufgrund der anderen Verarbeitung externer Measures kann für DirectQuery-Modelle für mehrdimensionale Datenquellen wie SAP BW auch vom DirectQuery- in den Importmodus gewechselt werden.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery im Power BI-Dienst

Alle Quellen werden von Power BI Desktop unterstützt. Einige Quellen sind auch direkt im Power BI-Dienst verfügbar. Beispielsweise ist es möglich, dass ein Geschäftsbenutzer Power BI zum Herstellen einer Verbindung mit den Daten in Salesforce verwendet und sofort ohne die Verwendung von Power BI Desktop ein Dashboard abrufen kann.

Nur zwei der von DirectQuery aktivierten Quellen sind direkt im Dienst verfügbar.

* Spark
* Azure SQL Data Warehouse

Es wird jedoch empfohlen, dass jede Verwendung von DirectQuery über diese beiden Quellen innerhalb von Power BI Desktop stattfindet. Der Grund dafür ist, dass beim erstmaligen Herstellen der Verbindung im Power BI-Dienst viele wichtige Einschränkungen gelten. Während der Einstieg in den Power BI-Dienst einfach war, gibt es Einschränkungen bei der weiteren Verbesserung des resultierenden Berichts. Es ist dann z. B. nicht möglich, Berechnungen zu erstellen oder viele analytische Features zu verwenden oder sogar die Metadaten zu aktualisieren, um Änderungen des zugrunde liegenden Schemas widerzuspiegeln.

## <a name="guidance-for-using-directquery-successfully"></a>Leitfaden zur erfolgreichen Verwendung von DirectQuery

Wenn Sie DirectQuery verwenden möchten, finden Sie in diesem Abschnitt ausführliche Anleitungen, mit deren Hilfe Sie diese Funktion erfolgreich ausführen können. Die Anleitung in diesem Abschnitt wurde auf Basis der Auswirkungen der Verwendung von DirectQuery geschrieben, die in diesem Artikel beschrieben wurden.

### <a name="back-end-data-source-performance"></a>Leistung der Back-End-Datenquelle

Überprüfen Sie, ob einfache visuelle Elemente in angemessener Zeit aktualisiert werden. Die Aktualisierung sollte innerhalb von fünf Sekunden erfolgen, damit Sie eine akzeptable interaktive Erfahrung erhalten. Wenn visuelle Elemente länger als 30 Sekunden brauchen, ist es sehr wahrscheinlich, dass weitere Probleme nach der Veröffentlichung des Berichts auftreten. Diese Probleme können dazu führen, dass die Lösung nicht praktikabel ist.

Wenn Abfragen langsam sind, untersuchen Sie die Abfragen, die an die zugrunde liegende Quelle gesendet werden, und den Grund für die Abfrageleistung. In diesem Artikel wird die breite Palette der bewährten Methoden zur Datenbankoptimierung für die gesamten potenziellen zugrunde liegenden Quellen nicht behandelt. In diesem Artikel werden die Standardverfahren für Datenbanken behandelt, die für die meisten Situationen gelten:

* Beziehungen, die auf Integerspalten basieren, werden in der Regel besser ausgeführt, als Joins auf Spalten eines anderen Datentyps.
* Die entsprechenden Indizes sollten erstellt werden. Indexerstellung bedeutet im Allgemeinen die Verwendung von Columnstore-Indizes in den Quellen, die diese unterstützen, z. B. SQL Server.
* Es sollten alle notwendigen Statistiken in der Quelle aktualisiert werden.

### <a name="model-design-guidance"></a>Leitfaden zum Modellentwurf

Beachten Sie bei der Definition des Modells die folgenden Anleitungen:

* **Vermeiden Sie komplexe Abfragen im Abfrage-Editor.** Der Abfrage-Editor übersetzt eine komplexe Abfrage in eine einzelne SQL-Abfrage. Die einzelne Abfrage wird bei jeder an diese Tabelle gesendeten Abfrage in der Unterauswahl angezeigt. Wenn diese Abfrage komplex ist, kann es zu Leistungsproblemen bei jeder gesendeten Abfrage kommen. Die aktuelle SQL-Abfrage für eine Reihe von Schritten erhalten Sie, indem Sie den letzten Schritt im Abfrage-Editor und dann **View Native Query** (Native Abfrage anzeigen) aus dem Kontextmenü auswählen.
* **Halten Sie Measures einfach.** Zumindest am Anfang wird empfohlen, Measures auf einfache Aggregate zu beschränken. Wenn die Measures dann zufriedenstellend ausgeführt werden, können komplexere Measures definiert werden. Achten Sie jedoch auf die Leistung der einzelnen Measures.
* **Vermeiden Sie Beziehungen in berechneten Spalten.** Diese Anleitung ist für Datenbanken relevant, bei denen Sie mehrspaltige Joins durchführen müssen. Power BI lässt heute nicht zu, dass eine Beziehung auf mehreren Spalten als FS/PS vergeben wird. Die am meisten verwendete Problemumgehung ist, die Spalten mithilfe einer berechneten Spalte zu verknüpfen und dann den Join auf Basis dieser Spalte zu basieren. Während diese Problemumgehung für importierte Daten sinnvoll ist, führt sie bei DirectQuery zu einem Join für einen Ausdruck. Dieses Ergebnis verhindert in der Regel die Verwendung von Indizes und führt zu einer schlechten Leistung. Die einzige Problemumgehung ist tatsächlich, die vielen Spalten in eine einzige Spalte in der zugrunde liegenden Datenbank zu materialisieren.
* **Vermeiden Sie Beziehungen zwischen „uniqueidentifier“-Spalten.** Power BI verfügt nicht über die native Unterstützung für den Datentyp `uniqueidentifier`. Die Definition einer Beziehung zwischen Spalten vom Typ `uniqueidentifier`-Spalte führt zu einer Abfrage mit einem Join, der eine Umwandlung umfasst. Auch dieser Ansatz führt häufig zu schlechter Leistung. Bis dieser Fall speziell optimiert ist, besteht die einzige Umgehung dieses Problems darin, Spalten eines alternativen Typs in der zugrunde liegenden Datenbank zu materialisieren.
* **Blenden Sie die „to“-Spalte für Beziehungen aus.** Die *to*-Spalte für Beziehungen ist üblicherweise der Primärschlüssel in der *to*-Tabelle. Diese Spalte sollte ausgeblendet werden. Wenn sie ausgeblendet ist, wird sie nicht in der Feldliste angezeigt und kann nicht in visuellen Elementen verwendet werden. Häufig sind die Spalten, auf denen Beziehungen basieren, tatsächlich *Systemspalten*, z. B. Ersatzschlüssel in einem Data Warehouse. Es ist ohnehin eine bewährte Methode, solche Spalten auszublenden. Wenn die Spalte eine Bedeutung aufweist, führen Sie eine berechnete und sichtbare Spalte ein, die über einen einfachen Ausdruck verfügt, der mit dem Primärschlüssel identisch ist, wie im folgenden Beispiel:

  ```sql  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  ```

* **Überprüfen Sie alle Vorkommen von berechneten Spalten und Änderungen des Datentyps.** Die Verwendung dieser Fähigkeiten ist nicht unbedingt schädlich. Sie führen dazu, dass die Abfragen, die an die zugrundeliegende Quelle gesendet werden, Ausdrücke statt einfacher Verweise auf Spalten enthalten. Das wiederum kann dazu führen, dass Indizes nicht verwendet werden.
* **Vermeiden Sie die Verwendung der bidirektionalen Kreuzfilterung für Beziehungen.** Die Verwendung des bidirektionalen Kreuzfilterns kann zu Abfrageanweisungen führen, die nicht gut funktionieren.
* **Experimentieren Sie mit der Einstellung *Referenzielle Integrität voraussetzen*.** Die Einstellung „Referenzielle Integrität voraussetzen“ für Beziehungen lässt zu, dass Abfragen `INNER JOIN`-Anweisungen und nicht `OUTER JOIN`-Anweisungen verwenden. Diese Anleitung verbessert im Allgemeinen die Abfrageleistung, obwohl dies nicht von den Eigenheiten der Datenquelle abhängt.
* **Verwenden Sie nicht die relative Datenfilterung im Abfrage-Editor.** Es ist möglich, die relative Datenfilterung im Abfrage-Editor zu definieren. Ein Beispiel dafür ist es, nach Zeilen zu filtern, in denen das Datum im Zeitraum der letzten 14 Tage liegt.
  
  ![Zeilen für die letzten 14 Tage filtern](media/desktop-directquery-about/directquery-about_02.png)
  
  Dieser Filter wird jedoch in einen Filter übersetzt, der auf dem festen Datum basiert, wie dem Zeitpunkt der Erstellung der Abfrage. Dieses Ergebnis kann in der nativen Abfrage angezeigt werden.
  
  ![Zeilen in nativer SQL-Abfrage filtern](media/desktop-directquery-about/directquery-about_03.png)
  
  Dies ist vermutlich nicht das gewünschte Ergebnis. Um sicherzustellen, dass der Filter basierend auf dem Datum angewendet wird, an dem der Bericht ausgeführt wird, wenden Sie stattdessen den Filter im Bericht als Berichtsfilter an. Derzeit würde dieser Ansatz funktionieren, indem Sie eine berechnete Tabelle erstellen, die die Anzahl der vergangenen Tage mithilfe der `DAX DATE()`-Funktion berechnet, und dann diese berechnete Spalte in einem Filter verwenden.

### <a name="report-design-guidance"></a>Leitfaden zum Berichtsentwurf

Wenn Sie einen Bericht mithilfe einer DirectQuery-Verbindung erstellen, befolgen Sie diese Anweisungen:

* **Überlegungen für das Verwenden von Optionen zur Verringerung von Abfragen:** Power BI stellt Optionen im Bericht bereit, mit denen weniger Abfragen gesendet und bestimmte Interaktionen deaktiviert werden, die bei langer Ausführung der resultierenden Abfragen zu Leistungseinbußen führen würden. Navigieren Sie in Power BI Desktop zu **Datei** > **Optionen und Einstellungen** > **Optionen**, und wählen Sie **Abfrageverringerung** aus, um auf diese Optionen zuzugreifen.

   ![Optionen für die Abfrageverringerung](media/desktop-directquery-about/directquery-about_03b.png)

    Durch die Kontrollkästchen unter **Abfrageverringerung** können Sie die übergreifende Hervorhebung für den gesamten Bericht deaktivieren. Sie können auch eine **Anwenden**-Schaltfläche für Slicer- oder Filterauswahlen anzeigen. Dieser Ansatz ermöglicht es Ihnen, viele Slicer- und Filterauswahlen zu treffen, bevor Sie diese anwenden. Es werden keine Abfragen gesendet, bis Sie die Schaltfläche **Anwenden** für den Slicer auswählen. Ihre Auswahl kann dann zum Filtern der Daten verwendet werden.

    Diese Optionen gelten für Ihren Bericht, während Sie in Power BI Desktop mit ihm interagieren. Diese Optionen gelten auch, wenn Ihre Benutzer den Bericht im Power BI-Dienst verwenden.

* **Wenden Sie zuerst Filter an:** Wenden Sie anwendbare Filter immer zu Beginn der Erstellung eines Visuals an. Wenden Sie z. B. den Filter **Jahr** zu Beginn an, anstatt sich im **TotalSalesAmount** und **ProductName** zu bewegen und dann nach einem bestimmten Jahr zu filtern. Jeder Schritt beim Erstellen eines visuellen Elements sendet eine Abfrage. Obwohl es möglich ist, Änderungen durchzuführen, bevor die erste Abfrage abgeschlossen ist, hinterlässt dieser Ansatz dennoch unnötige Last auf der zugrunde liegenden Quelle. Wenn Filter früh angewendet werden, werden diese zwischenzeitlichen Abfragen generell günstiger. Darüber hinaus kann es dazu führen, dass die Begrenzung von eine Million Zeilen erreicht wird, wenn die Filter nicht frühzeitig angewendet werden.
* **Begrenzen Sie die Anzahl von Visuals auf einer Seite:** Wenn Sie eine Seite öffnen oder einen Slicer oder Filter auf Seitenebene ändern, werden alle visuellen Elemente auf einer Seite aktualisiert. Es gibt auch eine Begrenzung der Anzahl von Abfragen, die parallel gesendet werden. Wenn die Anzahl der visuellen Elemente steigt, werden auch einige visuelle Elemente nacheinander aktualisiert, wodurch viel mehr Zeit für die Aktualisierung der gesamten Seite benötigt wird. Aus diesem Grund wird empfohlen, die Anzahl von visuellen Elementen auf einer Seite zu begrenzen, und stattdessen mehr einfachere Seiten zu verwenden.
* **Erwägen Sie, die Interaktion zwischen Visuals zu deaktivieren:** Standardmäßig können Visualisierungen auf einer Berichtsseite für die Kreuzfilterung und -hervorhebung der anderen Visualisierungen auf der Seite verwendet werden. Wenn z. B. **1999** auf dem Kreisdiagramm ausgewählt ist, wird das Säulendiagramm übergreifend hervorgehoben, um die Verkäufe nach Kategorie für **1999** anzuzeigen.
  
  ![Mehrere visuelle Elemente mit Kreuzfiltern und übergreifendem Hervorheben](media/desktop-directquery-about/directquery-about_04.png)
  
  Die Kreuzfilterung und die übergreifende Hervorhebung in DirectQuery erfordern das Übermitteln von Abfragen an die zugrunde liegende Quelle. Die Interaktion sollte deaktiviert werden, wenn die Reaktionszeit auf die Auswahl der Benutzer unangemessen lang wäre. Sie können diese Interaktion deaktivieren. Deaktivieren Sie die Interaktion entweder für den gesamten Bericht, wie bereits für die Optionen der Abfrageverringerung beschrieben, oder von Fall zu Fall. Weitere Informationen finden Sie unter [Gegenseitige Kreuzfilterung von Visuals in einem Power BI-Bericht](consumer/end-user-interactions.md).

Zusätzlich zu den vorherigen Vorschlägen kann jede der folgenden Berichtsfunktionen Leistungsprobleme verursachen:

* **Measurefilter:** Visuelle Elemente, die Measures oder Aggregate von Spalten enthalten, können Filter in diesen Measures enthalten. Das visuelle Element unten zeigt z. B. **SalesAmount** nach **Category** an, aber nur einschließlich dieser Kategorien mit mehr als **20M** Verkäufen.
  
  ![Visuelles Element, das Measures anzeigt, die Filter enthalten](media/desktop-directquery-about/directquery-about_05.png)
  
  Dieser Ansatz führt dazu, dass zwei Abfragen an die zugrunde liegende Datenquelle gesendet werden:
  
  * Die erste Abfrage ruft die Kategorien ab, die die Bedingung erfüllen (**SalesAmount** größer als 20 Millionen).
  * Die zweite Abfrage ruft die notwendigen Daten für das visuelle Element ab, einschließlich der Kategorien, die die Bedingung in der `WHERE`-Klausel erfüllen.
  
  Dieser Ansatz funktioniert in der Regel gut, wenn es Hunderte oder Tausende von Kategorien gibt, wie in diesem Beispiel. Die Leistung kann sich verschlechtern, wenn die Anzahl der Kategorien viel größer ist. Die Abfrage schlägt bei mehr als einer Million Kategorien, die die Bedingung erfüllen, fehl. Die Beschränkung auf eine Million Zeilen wurde bereits früher erläutert.

* **TopN-Filter:** Erweiterte Filter können so definiert werden, dass nur die oberen oder unteren N Werte gefiltert werden, die nach einem bestimmten Measure geordnet sind. So können die Filter z. B. die zehn obersten Kategorien in dem vorherigen visuellen Element einbeziehen. Dieser Ansatz führt erneut dazu, dass zwei Abfragen an die zugrunde liegende Datenquelle gesendet werden. Allerdings gibt die erste Abfrage alle Kategorien der zugrunde liegenden Quelle zurück, dann werden die TopN basierend auf den zurückgegebenen Ergebnissen bestimmt. Abhängigkeit von der Kardinalität der beteiligten Spalte kann dieser Ansatz zu Leistungsproblemen oder Abfragefehlern aufgrund des Zeilengrenzwerts von einer Million führen.

* **Median:** Im Allgemeinen wird jede Aggregation wie `Sum` oder `Count Distinct` per Push an die zugrunde liegende Quelle gesendet. Dies gilt allerdings nicht für den Median, da dieses Aggregat normalerweise nicht von der zugrunde liegenden Quelle unterstützt wird. In solchen Fällen werden die Detaildaten aus der zugrunde liegenden Quelle abgerufen, und der Median wird aus den zurückgegebenen Ergebnissen berechnet. Dieser Ansatz ist sinnvoll, wenn der Median über eine relativ kleine Anzahl von Ergebnissen berechnet werden soll. Bei großer Kardinalität kommt es zu Leistungsproblemen oder Abfrageausfällen aufgrund des Zeilengrenzwerts von einer Million. Den **Median der Bevölkerungszahl** eines Landes zu ermitteln, kann sinnvoll sein, nicht jedoch die Ermittlung des **Medians von Verkaufspreisen**.

* **Erweiterte Textfilter (_enthält_ und ähnlich):** Wenn nach einer Textspalte gefiltert wird, erlaubt das erweiterte Filtern Filter wie *enthält* und *beginnt mit* usw. Diese Filter können sicherlich zu Leistungseinbußen bei einigen Datenquellen führen. Insbesondere sollte der Standardfilter *enthält* nicht verwendet werden, falls nach einer exakten Übereinstimmung gesucht wird. Obwohl das Ergebnis möglicherweise identisch ist, kann sich abhängig von den tatsächlichen Daten die Leistung aufgrund der Verwendung von Indizes erheblich unterscheiden.

* **Slicer mit Mehrfachauswahl:** Standardmäßig erlauben Slicer nur eine einzige Auswahl. Das Zulassen der Mehrfachauswahl in Filtern kann zu einigen Leistungsproblemen führen, da der Benutzer eine Reihe von Elementen im Slicer auswählt. Wenn der Benutzer z. B. die für ihn interessanten zehn Produkte auswählt, führt jede neue Auswahl dazu, dass Abfragen an die Quelle gesendet werden. Obwohl der Benutzer das nächste Element auswählen kann, bevor die Abfrage abgeschlossen ist, führt dieser Ansatz zu einer zusätzlichen Last für die zugrunde liegende Quelle.

* **Erwägen Sie, Summen in Visuals zu deaktivieren:** Standardmäßig werden in Tabellen und Matrizen Summen und Teilsummen angezeigt. In vielen Fällen müssen separate Abfragen an die zugrunde liegende Quelle gesendet werden, um die Werte für solche Summen abzurufen. Diese Tatsache gilt immer, wenn die Aggregation *DistinctCount* verwendet wird oder wenn DirectQuery über SAP BW oder SAP HANA verwendet wird. Solche Summen sollten mithilfe des Bereichs **Format** deaktiviert werden.

### <a name="maximum-number-of-connections-option-for-directquery"></a>Maximale Anzahl von Verbindungsoptionen für DirectQuery

Sie können einstellen, wie viele Verbindungen für jede zugrunde liegende Datenquelle von DirectQuery maximal geöffnet werden können, wodurch gesteuert wird, wie viele Abfragen gleichzeitig an jede Datenquelle gesendet werden.

DirectQuery öffnet standardmäßig eine maximale Anzahl von zehn gleichzeitigen Verbindungen. Sie können die maximale Anzahl für die aktuelle Datei in Power BI Desktop ändern. Öffnen Sie **Datei** > **Optionen und Einstellungen** > **Optionen**. Wählen Sie im Abschnitt **Aktuelle Datei** im linken Fensterbereich die Option **DirectQuery** aus.

![Festlegen der maximalen Anzahl von DirectQuery-Verbindungen](media/desktop-directquery-about/directquery-about_05b.png)

Die Einstellung ist nur aktiviert, wenn mindestens eine DirectQuery-Quelle im aktuellen Bericht vorhanden ist. Der Wert gilt für alle DirectQuery-Quellen sowie für alle neuen DirectQuery-Quellen, die dem gleichen Bericht hinzugefügt werden.

Die Erhöhung der Option **Maximale Verbindungsanzahl pro Datenquelle** stellt sicher, dass mehr Abfragen bis zu der angegebenen maximalen Anzahl an die zugrunde liegende Datenquelle gesendet werden können. Dieser Ansatz ist nützlich, wenn sich viele visuelle Elemente auf einer einzelnen Seite befinden oder viele Benutzer gleichzeitig auf einen Bericht zugreifen. Sobald die maximale Anzahl von Verbindungen erreicht ist, werden weitere Abfragen in die Warteschlange gestellt, bis eine Verbindung verfügbar wird. Ein Erhöhen dieses Grenzwerts führt zu mehr Last auf der zugrunde liegenden Quelle. Daher ist nicht garantiert, dass durch die Einstellung die Gesamtleistung verbessert wird.

Sobald ein Bericht veröffentlicht wird, hängt die maximale Anzahl der gleichzeitig an die zugrunde liegende Datenquelle gesendeten Abfragen ebenfalls von festen Grenzwerten ab. Die Grenzwerte hängen von der Zielumgebung ab, in der der Bericht veröffentlicht wird. Unterschiedliche Umgebungen wie Power BI, Power BI Premium oder Power BI-Berichtsserver können unterschiedliche Grenzwerte erfordern.

### <a name="diagnosing-performance-issues"></a>Diagnostizieren von Leistungsproblemen

Dieser Abschnitt beschreibt, wie Sie Leistungsprobleme diagnostizieren oder weitere Informationen darüber erhalten können, wie Berichte optimiert werden.

Es wird empfohlen, die Diagnose von Leistungsproblemen im Power BI Desktop und nicht im Power BI-Dienst zu starten. Leistungsprobleme basieren oft auf der Leistung der zugrunde liegenden Quelle. In der stärker isolierten Umgebung von Power BI Desktop können Sie Probleme leichter identifizieren und diagnostizieren. Dieser Ansatz verzichtet anfänglich auf bestimmte Komponenten wie das Power BI-Gateway. Wenn die Leistungsprobleme im Power BI Desktop nicht vorhanden sind, untersuchen Sie die Einzelheiten des Berichts im Power BI-Dienst. Die [Leistungsanalyse](desktop-performance-analyzer.md) ist ein nützliches Tool zum Erkennen von Problemen in diesem Prozess.

Es wird auch empfohlen, zu versuchen, zunächst Probleme eines visuellen Elements zu isolieren, anstatt viele visuelle Elemente auf einer Seite.

Nehmen wir an, die Schritte in den vorhergehenden Absätzen in diesem Abschnitt wurden bereits durchgeführt. Wir verfügen jetzt über ein einzelnes visuelles Element auf einer Seite in Power BI Desktop, das immer noch langsam ist. Verwenden Sie die [Leistungsanalyse](desktop-performance-analyzer.md), um die Abfragen zu bestimmen, die Power BI Desktop an die zugrunde liegende Quelle sendet. Es ist auch möglich, Ablaufverfolgungen und Diagnoseinformationen anzuzeigen, sofern solche von der zugrunde liegenden Datenquelle ausgegeben wurden. Ablaufverfolgungen können auch nützliche Details darüber enthalten, wie die Abfrage ausgeführt wurde und wie sie verbessert werden kann.

Darüber hinaus ist es möglich, die Abfragen, die von Power BI zusammen mit den Ausführungszeiten gesendet wurden, anzuzeigen, auch wenn keine Ablaufverfolgungen vorhanden sind, so wie im nächsten Abschnitt beschrieben.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Bestimmen der Abfragen von Power BI Desktop

Standardmäßig protokolliert Power BI Desktop während einer gegebenen Sitzung Ereignisse in einer Ablaufverfolgungsdatei mit dem Namen *FlightRecorderCurrent.trc*.

Bei einigen DirectQuery-Quellen enthält dieses Protokoll alle Abfragen, die an die zugrunde liegende Datenquelle gesendet wurden. Die übrigen DirectQuery-Quellen werden zukünftig einbezogen. Die folgenden Quellen senden Abfragen an das Protokoll:

* SQL Server
* Azure SQL-Datenbank
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

Sie finden die Ablaufverfolgungsdatei im *AppData*-Ordner für den aktuellen Benutzer:

*\<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces*

Wählen Sie zum Abrufen dieses Ordners in Power BI Desktop **Datei** > **Optionen und Einstellungen** > **Optionen** und dann **Diagnose** aus. Das folgende Dialogfeld wird angezeigt:

![Ein Link zum Öffnen des Ordners „Traces“](media/desktop-directquery-about/directquery-about_06.png)

Wenn Sie **Ordner mit Absturzabbild/Überwachungen öffnen** unter **Diagnoseoptionen** auswählen, wird der folgende Ordner geöffnet: *\<User>\AppData\Local\Microsoft\Power BI Desktop\Traces*.

Beim Navigieren zum übergeordneten Ordner des Ordners wird der Ordner angezeigt, der *AnalysisServicesWorkspaces* enthält, die einen Arbeitsbereichsordner für jede offene Instanz von Power BI Desktop enthält. Diese Ordner werden mit einem Integersuffix bezeichnet, z. B. *AnalysisServicesWorkspace2058279583*.

Innerhalb dieses Ordners befindet sich der Ordner *\\Data*. Er enthält die Ablaufverfolgungsdatei *FlightRecorderCurrent.trc* für die aktuelle Power BI-Sitzung. Der entsprechende Arbeitsbereichsordner wird gelöscht, wenn die zugehörige Power BI Desktop-Sitzung endet.

Die Ablaufverfolgungsdateien können mit dem Tool *SQL Server Profiler* gelesen werden. Sie erhalten es als Teil des kostenlosen Downloads von [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).

Nachdem Sie SQL Server Management Studio heruntergeladen und installiert haben, führen Sie den SQL Server Profiler aus.

![SQL Server Profiler](media/desktop-directquery-about/directquery-about_07.png)

Um die Ablaufverfolgungsdatei zu öffnen, gehen Sie folgendermaßen vor:

1. Wählen Sie in SQL Server Profiler **Datei** > **Öffnen** > **Ablaufverfolgungsdatei** aus.

1. Geben Sie den Pfad zur Ablaufverfolgungsdatei für die aktuell geöffnete Power BI-Sitzung ein, z.B.: *C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data*.

1. Öffnen Sie *FlightRecorderCurrent.trc*.

Es werden alle Ereignisse aus der aktuellen Sitzung angezeigt. Ein kommentiertes Beispiel ist hier dargestellt, das Gruppen von Ereignissen markiert. Jede Gruppe verfügt über folgende Ereignisse:

* Ein Ereignis für `Query Begin` und `Query End`, das den Beginn und das Ende einer DAX-Abfrage darstellt, die von der Benutzeroberfläche generiert wird, z. B. von einem visuellen Element oder durch Auffüllen einer Liste von Werten in der Filterbenutzeroberfläche.
* Ein oder mehrere Paare von Ereignissen für `DirectQuery Begin` und `DirectQuery End` stellen eine an die zugrunde liegende Datenquelle gesendete Abfrage als Teil der Auswertung der DAX-Abfrage dar.

Mehrere DAX-Abfragen können parallel ausgeführt werden, damit sich Ereignisse aus verschiedenen Gruppen überlappen können. Der Wert der `ActivityID` kann verwendet werden, um zu bestimmen, welche Ereignisse zur selben Gruppe gehören.

![SQL Server Profiler mit Ereignissen für den Abfragebeginn und das Abfrageende](media/desktop-directquery-about/directquery-about_08.png)

Andere interessante Spalten sind die folgenden:

* **TextData:** Die Textdetails des Ereignisses. Bei `Query Begin/End`-Ereignissen ist das Detail die DAX-Abfrage. Bei `DirectQuery Begin/End`-Ereignissen ist das Detail die SQL-Abfrage, die an die zugrunde liegende Quelle gesendet wird. Die Daten von **TextData** werden für das aktuell ausgewählte Ereignis auch im unteren Bereich angezeigt.
* **EndTime:** Die Zeit, zu der das Ereignis beendet wurde.
* **Duration:** Die Dauer in Millisekunden, die zur Ausführung der DAX- oder SQL-Abfrage benötigt wird.
* **Error:** Gibt an, ob ein Fehler aufgetreten ist. In diesem Fall wird das Ergebnis auch rot angezeigt.

In der Abbildung oben wurden einige weniger relevante Spalten verschmälert, damit andere Spalten einfacher gelesen werden können.

Wir empfehlen den folgenden Ansatz für die Erfassung einer Ablaufverfolgung, um die Diagnose eines potenziellen Leistungsproblems zu erleichtern:

* Öffnen Sie eine einzelne Power BI Desktop-Sitzung zur Vermeidung von Verwechslungen von mehreren Arbeitsbereichsordnern.
* Führen Sie die interessanten Aktionen in Power BI Desktop aus. Schließen Sie einige zusätzliche Aktionen mit ein, um sicherzustellen, dass die interessanten Ereignisse in die Ablaufverfolgungsdatei geleert werden.
* Öffnen Sie den SQL Server Profiler, und untersuchen Sie die Ablaufverfolgung, so wie vorher beschrieben. Denken Sie daran, dass beim Schließen von Power BI Desktop die Ablaufverfolgungsdatei gelöscht wird. Auch weitere Aktionen in Power BI Desktop werden nicht sofort angezeigt. Die Ablaufverfolgungsdatei sollte geschlossen und wieder geöffnet werden, um die neuen Ereignisse anzuzeigen.
* Halten Sie einzelne Sitzungen relativ klein, vielleicht zehn Sekunden mit Aktionen, nicht Hunderte Sekunden. Dieser Ansatz erleichtert die Interpretation der Ablaufverfolgungsdatei. Es gibt auch einen Grenzwert für die Größe der Ablaufverfolgungsdatei. Bei langen Sitzungen besteht die Möglichkeit, dass die frühen Ereignisse gelöscht werden.

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Grundlegendes zur Form der Abfrage, die von Power BI Desktop gesendet wird

Die Allgemeine Form von Abfragen, die durch Power BI Desktop gesendet werden, verwendet Unterabfragen für alle referenzierten Tabellen. Die Abfrage des Abfrage-Editors definiert den untergeordneten SELECT-Ausdruck. Nehmen wir z.B. an, dass die folgenden TPC-DS-Tabellen in SQL Server vorhanden sind:

![TPC-DS-Tabellen in SQL Server](media/desktop-directquery-about/directquery-about_09.png)

Bedenken Sie die folgende Abfrage:

![Beispielabfrage](media/desktop-directquery-about/directquery-about_10.png)

Diese Abfrage ergibt folgendes visuelles Element:

![Visuelles Ergebnis einer Abfrage](media/desktop-directquery-about/directquery-about_11.png)

Wenn Sie dieses visuelle Element aktualisieren, ergibt dies eine SQL-Abfrage, die hier gezeigt wird. Wie Sie erkennen können, gibt es drei untergeordnete SELECT-Ausdrücke für `Web Sales`, `Item` und `Date_dim`, die jeweils alle Spalten in der jeweiligen Tabelle zurückgeben, obwohl das visuelle Element tatsächlich nur auf vier Spalten verweist. Diese Abfragen in den untergeordneten schattierten SELECT-Ausdrücken sind genau die Ergebnisse der Abfragen, die im Abfrage-Editor definiert sind. Die Verwendung untergeordneter SELECT-Ausdrücke beeinträchtigt die Leistung nicht für Datenquellen, die bisher für DirectQuery unterstützt wurden. Datenquellen wie SQL Server optimieren die Verweise auf die anderen Spalten.

Power BI verwendet dieses Muster, da die verwendete SQL-Abfrage direkt vom Analytiker zur Verfügung gestellt werden kann. Es wird „wie vorgesehen“ verwendet, ohne dass versucht wird, es neu zu schreiben.

![Wie vorgesehen verwendete SQL-Abfrage](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Nächste Schritte

Dieser Artikel beschreibt Aspekte von DirectQuery, die für alle Datenquellen üblich sind. Es gibt bestimmte Details, die spezifisch für einzelne Datenquellen sind. Informationen finden Sie in den folgenden Artikeln, die bestimmte Quellen abdecken:

* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)

Weitere Informationen zu DirectQuery finden Sie in der folgenden Ressource:

* [Data Sources supported by DirectQuery (Von DirectQuery unterstützte Datenquellen)](desktop-directquery-data-sources.md)
