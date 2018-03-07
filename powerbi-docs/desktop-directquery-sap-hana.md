---
title: "DirectQuery für SAP HANA in Power BI"
description: "Überlegungen zur Verwendung von DirectQuery mit SAP HANA"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: cd266118fa560b3d637a85b352f8c1f03d137ec6
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/24/2018
---
# <a name="directquery-and-sap-hana"></a>DirectQuery und SAP HANA
Sie können sich mit **SAP HANA**-Datenquellen direkt über **DirectQuery** verbinden. Beim Verbinden mit HANA stehen zwei Optionen zur Verfügung:

* **Treat HANA as a multi dimensional source (default)** (HANA als mehrdimensionale Quelle behandeln (Standard)): Diese Option befindet sich derzeit in der Vorschauversion und ist die neue Standardeinstellung. Bei Auswahl dieser Option ist das Verhalten mit dem vergleichbar, das bei einer Verbindung von Power BI mit anderen mehrdimensionalen Quellen wie SAP Business Warehouse oder Analysis Services besteht. Wenn mit dieser Einstellung eine Verbindung mit HANA hergestellt wird, wird eine analytische Ansicht oder Berechnungsansicht ausgewählt. Alle Measures, Hierarchien und Attribute dieser Ansicht sind in diesem Fall in der Feldliste verfügbar. Beim Erstellen von Visuals werden die Aggregatdaten immer von HANA abgerufen. Diese Vorgehensweise ist der Standardfall und wird empfohlen.

* **HANA als relationale Quelle behandeln:** Mit dieser Option behandelt Power BI HANA als relationale Quelle. Diese Vorgehensweise bietet mehr Flexibilität. Es muss jedoch darauf geachtet werden, dass Measures wie erwartet aggregiert und Leistungsprobleme vermieden werden.

Die Verbindungsmethode können Sie durch eine globale Tooloption festlegen. Rufen Sie dazu **Datei > Optionen und Einstellungen** und anschließend **Optionen > DirectQuery** auf. Klicken Sie dann wie in der folgenden Abbildung dargestellt auf das Kontrollkästchen neben **HANA als relationale Quelle behandeln**. 

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

Beachten Sie, dass sich der **SAP HANA-Connector** derzeit in der **Vorschauversion** befindet und aktiviert werden muss, bevor die oben genannte Option angezeigt wird. Wenn Sie das neue SAP HANA-Vorschaufeature aktivieren möchten, wählen Sie sie wie in der Abbildung unten gezeigt unter **Optionen > Vorschaufeatures** aus.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01b.png)

Nachdem Sie angegeben haben, dass HANA als relationale Quelle behandelt werden soll, wird diese Option auf alle *neu erstellten* Verbindungen angewendet. Sie hat weder Auswirkungen auf vorhandene HANA-Verbindungen im aktuellen Bericht noch auf Verbindungen in anderen Berichten, die geöffnet werden. Wenn die Option nicht aktiviert ist, wird beim Herstellen einer neuen Verbindung mit HANA über **Daten abrufen** HANA als mehrdimensionale Datenquelle für die Verbindung verwendet. Wenn jedoch ein anderer Bericht geöffnet wird, der ebenfalls eine Verbindung mit HANA herstellt, wird sich das Verhalten dieses Berichts an der Option orientieren, die *zum Zeitpunkt der Erstellung* festgelegt wurde. Dies bedeutet, dass alle Berichte, die eine Verbindung mit HANA herstellen und vor Februar 2018 erstellt wurden, HANA weiterhin als relationale Quelle behandeln. 

Die beiden Ansätze weisen unterschiedlichen Verhalten auf, weswegen es nicht möglich ist, für einen vorhandenen Bericht eine andere Vorgehensweise auszuwählen. 

Die beiden Ansätze werden im Folgenden genauer beschrieben.

## <a name="treat-hana-as-a-multi-dimensional-source-default"></a>Treat HANA as a multi-dimensional source (default) (HANA als mehrdimensionale Quelle behandeln (Standard))

Hierbei handelt es sich um das Standardverhalten, das sich im Moment noch in der Vorschauversion befindet. Führen Sie zum Aktivieren des Vorschaufeatures die Schritte im vorherigen Abschnitt aus. 

Nachdem das **Vorschaufeature** unter **Optionen > Vorschaufeatures** aktiviert wurde (siehe Abschnitt oben), wird diese Verbindungsmethode standardmäßig für alle neuen Verbindungen mit HANA verwendet, wodurch HANA als mehrdimensionale Quelle verwendet wird. Wenn HANA als relationale Datenquelle behandelt werden soll, sind folgende Schritte notwendig: Rufen Sie zuerst **Datei > Optionen und Einstellungen** auf, und aktivieren Sie anschließend unter **DirectQuery** das Kontrollkästchen neben „HANA als relationale Quelle behandeln“. Obwohl dieses Feature in der **Vorschauversion** verfügbar ist, können Berichte, die mit dem mehrdimensionalen Ansatz erstellt wurden, *nicht* im Power BI-Dienst veröffentlicht werden. Wenn das Feature dennoch verwendet wird, führt dies beim Öffnen des Berichts im Power BI-Dienst zu Fehlern.  

Wenn HANA bei einer Verbindung als mehrdimensionale Datenquelle behandelt wird, ist Folgendes zu beachten:

* Im Navigator **Daten abrufen** kann eine einzelne HANA-Ansicht ausgewählt werden. Individuelle Measures oder Attribute lassen sich nicht auswählen. Bei der Verbindungsherstellung wird im Gegensatz zum Datenimport keine Abfrage definiert. Dasselbe gilt, wenn DirectQuery zum Behandeln von HANA als relationale Datenquelle verwendet wird. Dies hat außerdem zur Folge, dass bei Auswahl dieser Verbindungsmethode eine HANA SQL-Abfrage nicht direkt ausgeführt werden kann.

* Alle Measures, Hierarchien und Attribute der ausgewählten Ansicht werden in der Feldliste angezeigt. 

* Wenn ein Measure in einem Visual verwendet wird, wird HANA abgefragt und ruft dabei den Measurewert auf der Ebene der Aggregation ab, die für das Visual erforderlich ist. Daher werden bei nicht additiven Measures (Zählern, Verhältnissen usw.) alle Aggregationen von HANA ausgeführt, während Power BI keine weitere Aggregation vornimmt. 

* Damit von HANA die richtigen Aggregatwerte abgerufen werden, müssen bestimmte Einschränkungen festgelegt werden. Beispielsweise ist es nicht möglich, berechnete Spalten hinzuzufügen oder Daten aus mehreren HANA-Ansichten innerhalb desselben Berichts zu kombinieren. 

Der Ansatz, HANA als mehrdimensionale Quelle zu behandeln, ist im Gegensatz zur *relationalen* Methode weniger flexibel. Er ist jedoch einfacher, garantiert bei komplexeren HANA-Measures korrekte Aggregatwerte und führt allgemein zu einer höheren Leistung. 

Die Liste **Fields** (Felder) umfasst alle Measures, Attribute und Hierarchien der HANA-Ansicht. Beachten Sie, dass bei dieser Verbindungsmethode folgende Verhalten auftreten:

* Alle Attribute, die in mindestens einer Hierarchie enthalten sind, werden standardmäßig ausgeblendet. Sie können sie sich allerdings bei Bedarf anzeigen lassen, indem Sie aus dem Kontextmenü der Feldliste den Eintrag **Ausgeblendete anzeigen** auswählen. Über dasselbe Kontextmenü lässt sich ggf. der Sichtbarkeitsstatus ändern.

* In HANA kann ein Attribut so definiert werden, dass ein anderes Attribut als dessen Bezeichnung verwendet wird. Beispielsweise könnte ein Feld **Produkt** (mit den Werten 1, 2, 3 usw.) die Bezeichnung **Produktname** (mit den Werten „Fahrrad“, „Shirt“, „Handschuhe“ etc.) verwenden. In diesem Fall wird das Feld **Produkt** in der Feldliste angezeigt, deren Werte die Bezeichnungen „Fahrrad“, „Shirt“, „Handschuhe“ usw. sind. Die Bezeichnungen werden allerdings über die eindeutigen Schlüsselwerte 1, 2 und 3 identifiziert und nach diesen sortiert. Außerdem wird die ausgeblendete Spalte **Produkt.Schlüssel** erstellt, über die bei Bedarf auf die entsprechenden Schlüsselwerte zugegriffen werden kann. 

Alle in der zugrunde liegenden HANA-Quelle definierten Variablen werden zum Verbindungszeitpunkt angezeigt. Dabei können die erforderlichen Werte eingegeben werden können. Sie können diese Werte später ändern, indem Sie im Menüband auf **Abfragen bearbeiten** klicken und anschließend aus dem Dropdownmenü den Eintrag **Variablen bearbeiten** auswählen. 

Die zulässigen Modellierungsvorgänge sind restriktiver als bei der Verwendung von DirectQuery, da sichergestellt werden muss, dass die richtigen Aggregatdaten von HANA abgerufen werden können. Allerdings ist es weiterhin möglich, viele Ergänzungen und Änderungen vorzunehmen und beispielsweise Measures zu definieren, Felder umzubenennen und auszublenden sowie Anzeigeformate zu definieren. Alle Änderungen werden bei einer Aktualisierung beibehalten. Außerdem werden alle an der HANA-Ansicht vorgenommenen Änderungen, die zu keinen Konflikten führen, übernommen. 

### <a name="additional-modelling-restrictions"></a>Zusätzliche Modellierungseinschränkungen

Wenn über DirectQuery eine Verbindung mit SAP HANA hergestellt und SAP HANA als mehrdimensionale Quelle verwendet wird, sind v.a. die folgenden zusätzlichen Modellierungseinschränkungen zu berücksichtigen: 

* **Keine Unterstützung für berechnete Spalten**: Das Erstellen von berechneten Spalten ist deaktiviert. Dies bedeutet zudem, dass Gruppierung und Clustering, mit denen berechnete Spalten erstellt werden, nicht zur Verfügung stehen.
* **Zusätzliche Einschränkungen für Measures**: Für DAX-Ausdrücke, die in Measures verwendet werden können, gelten zusätzliche Einschränkungen, damit die von SAP HANA bereitgestellte Unterstützung übernommen wird.
* **Keine Unterstützung für das Definieren von Beziehungen:** Innerhalb eines Berichts können nur über eine einzelne Ansicht Abfragen gestellt werden. Daher können auch keine Beziehungen definiert werden.
* **Keine Datenansicht**: Die **Datenansicht** zeigt in der Tabelle normalerweise Daten auf Detailebene an. Aufgrund der Eigenschaften von OLAP-Quellen wie SAP HANA ist diese Ansicht in SAP HANA nicht verfügbar.
* **Details von Spalten und Measures sind unveränderlich**: Die in der Feldliste anzeigte Listen von Spalten und Measures sind in der zugrunde liegenden Quelle festgelegt und können nicht verändert werden. Es ist z.B. nicht möglich, eine Spalte oder deren Datentyp zu löschen. Sie können sie allerdings umbenennen.
* **Zusätzliche Einschränkungen in DAX**: Es gibt zusätzliche Einschränkungen für DAX, die in Measuredefinitionen verwendet wird, damit die Einschränkungen in der Quelle übernommen werden. Es ist z.B. nicht möglich, eine Aggregatfunktion für eine Tabelle zu verwenden.

### <a name="additional-visualization-restrictions"></a>Zusätzliche Visualisierungseinschränkungen

Wenn über DirectQuery eine Verbindung mit SAP HANA hergestellt und SAP HANA als mehrdimensionale Quelle verwendet wird, sind einige Einschränkungen bei Visuals zu beachten: 
* **Keine Spaltenaggregation**: Es ist nicht möglich, die Aggregation einer Spalte in einem Visual zu ändern. Sie verfügt immer über den Status *Nicht zusammenfassen*.

## <a name="treat-hana-as-a-relational-source"></a>HANA als relationale Quelle behandeln 

Wenn eine Verbindung mit HANA als relationale Datenquelle hergestellt wird, lassen sich erweiterte Funktionen nutzen. Sie können z.B. berechnete Spalten erstellen, Daten aus mehreren HANA-Ansichten einbeziehen und Beziehungen zwischen Tabellen erstellen. Wenn Sie SAP HANA auf diese Weise nutzen möchten, sollten Sie jedoch bestimmte Verbindungsaspekte berücksichtigen, um sicherzustellen, dass 

* die Ergebnisse richtig sind, wenn die SAP HANA-Ansicht nicht additive Measures (z.B. Distinct Count Measures oder Mittelwerte statt einfache Summen) enthält und
* Die resultierenden Abfragen besonders effizient sind

Es ist zunächst sinnvoll, sich mit dem Verhalten einer relationalen Quelle wie SQL Server zu befassen, wenn die Abfrage, die in **Daten abrufen** oder im **Abfrage-Editor** festgelegt ist, eine Aggregation ausführt. Im folgenden Beispiel gibt eine im **Abfrage-Editor** definierte Abfrage den Durchschnittspreis anhand der *ProductID* zurück.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Wenn die Daten in Power BI importiert werden (im Vergleich zur Verwendung von DirectQuery), würde sich das Folgende ergeben:

* Die Daten werden auf der Ebene der Aggregation importiert, die von der im **Abfrage-Editor** erstellten Abfrage definiert ist. Beispielsweise der Durchschnittspreis nach Produkt. Dies führt zu einer Tabelle mit den beiden Spalten *ProductID* und *AveragePrice*, die in visuellen Elementen verwendet werden können.
* In einem visuellen Element erfolgt jede nachträgliche Aggregation (z.B. *Summe*, *Durchschnitt*, *Min*, oder andere) über die importierten Daten. Wenn Sie beispielsweise *AveragePrice* aus einem Visual einbeziehen, wird das Aggregat *Sum* standardmäßig verwendet. So würde die Summe über den *AveragePrice*-Wert jeder *ProductID* zurückgegeben werden. In diesem Beispiel würde sie 13,67 betragen. Das gleiche gilt für andere Aggregatfunktionen (z.B. *Min*, *Average*, usw.), die in dem visuellen Element verwendet werden. *Average* von *AveragePrice* gibt z.B. den Durchschnitt von 6,66, 4 und 3 zurück, was 4,56 ergibt, und nicht den Durchschnitt von *Price* in den sechs Datensätzen in der zugrunde liegenden Tabelle, was 5,17 ergibt.
  
Wenn für dieselbe relationale Quelle **DirectQuery** anstelle der Option „Import“ (Importieren) verwendet wird, ist die gleiche Semantik anzuwenden, und die Ergebnisse wären identisch:  

* Bei der gleichen Abfrage werden logisch genau die gleichen Daten der Berichtsebene angezeigt – obwohl die Daten tatsächlich nicht importiert werden.

* In einem visuellen Element werden alle nachfolgenden Aggregationen (*Summe*, *Durchschnitt*, *Min*, andere) erneut über diese logische Tabelle aus der Abfrage ausgeführt. Und wieder gibt ein visuelles Element, das *Average* von *AveragePrice* enthält, das gleiche Ergebnis zurück, nämlich 4,56.
  
Nun wird SAP HANA vor dem Hintergrund einer relationalen Verbindungsquelle betrachtet. Power BI funktioniert mit *analytischen Ansichten* und *Berechnungsansichten* in SAP HANA, die beide Measures enthalten können. Mittlerweile folgt der Ansatz für SAP HANA aber denselben Prinzipien, die weiter oben beschrieben wurden: Die Abfrage, die in **Daten abrufen** oder im **Abfrage-Editor** definiert wird, legt fest, welche Daten verfügbar sind, und anschließend werden alle nachfolgenden Aggregationen in einem Visual für diese Daten ausgeführt. Das Gleiche gilt sowohl für die Option „Import“ (Importieren) als auch für DirectQuery.  
Angesichts der Beschaffenheit von HANA ist die im ersten Dialogfeld **Daten abrufen** oder im **Abfrage-Editor** definierte Abfrage immer eine Aggregatabfrage und enthält in der Regel Measures, bei denen die tatsächliche Aggregation, die verwendet wird, durch die HANA-Ansicht definiert ist.

Die Entsprechung des SQL-Servers im oben angeführten Beispiel ist, dass eine HANA-Sicht vorhanden ist, die *ID*, *ProductID*, *DepotID*, und Measures, einschließlich *Durchschnittspreis* enthält, was in der Ansicht als *Durchschnittspreis* definiert ist.  
    
Wenn unter **Daten abrufen** die Auswahl für die Measures **ProductID** und **AveragePrice** getroffen wurde, wird dadurch eine Abfrage über die Ansicht definiert, die die Aggregatdaten anfordert (im oben stehenden Beispiel wird der Einfachheit halber Pseudo-SQL verwendet, das nicht genau der Syntax von HANA SQL entspricht). Dann aggregieren alle weiteren Aggregationen, die in einem visuellen Element definiert sind, die Ergebnisse für eine solche Abfrage weiter. Wie oben bereits für SQL Server beschrieben, gilt dies sowohl für die Option „Import“ (Importieren) als auch für DirectQuery. Beachten Sie, dass im DirectQuery-Fall die Abfrage von **Daten abrufen** oder vom **Abfrage-Editor** in einer untergeordneten SELECT-Anweisung innerhalb einer einzelnen Abfrage verwendet wird, die an HANA gesendet wird. Daher handelt es sich nicht tatsächlich um den Fall, in dem alle Daten vor dem weiteren Aggregieren gelesen werden.  

Wenn DirectQuery für HANA verwendet wird, müssen daher die folgenden Überlegungen und Verhalten beachtet werden:  

* Berücksichtigt werden müssen alle weiteren Aggregationen, die in Visuals ausgeführt werden, wenn das Measure in HANA nicht additiv ist (z.B. keine einfache *Summe*, *Min*, oder *Max*).

* In **Daten abrufen** oder im **Abfrage-Editor** werden nur die erforderlichen Spalten einbezogen, um die erforderlichen Daten abzurufen, was widerspiegelt, dass das Ergebnis eine Abfrage sein wird, die eine sinnvolle Abfrage sein muss, die an HANA gesendet werden kann. Wenn z.B. Dutzende von Spalten ausgewählt wurden, um herauszufinden, ob sie möglicherweise in nachfolgenden visuellen Elementen benötigt werden, dann bedeutet ein einfaches visuelles Element selbst für DirectQuery, dass die Aggregatabfrage, die in der Unterauswahl verwendet wurde, diese Dutzenden Spalten enthält, was allgemein zu keiner guten Leistung führt.
  
Betrachten wir dazu ein Beispiel. Wenn Sie im folgenden Beispiel fünf Spalten (**CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**) im Dialogfeld **Daten abrufen** zusammen mit dem Measure *OrderQuantity* auswählen, bedeutet dies, dass später die Erstellung eines einfachen Visuals, das die Mindestbestellmenge (OrderQuantity) enthält, zu der folgenden SQL-Abfrage an HANA führt. Der schattierte Bereich ist die untergeordnete SELECT-Anweisung, die die Abfrage von **Daten abrufen** / **Abfrage-Editor** enthält. Wenn diese untergeordnete SELECT-Anweisung ein sehr hohes Kardinalitätsergebnis ergibt, ist es wahrscheinlich, dass die resultierende HANA-Leistung schlechter sein wird.  

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
Aufgrund dieses Verhaltens wird empfohlen, dass die Elemente, die in **Daten abrufen** oder im **Abfrage-Editor** ausgewählt werden, auf die erforderlichen Elemente beschränkt werden, solange sie weiterhin in einer sinnvollen Abfrage für HANA resultieren.  

## <a name="best-practices"></a>Best Practices 

Die Nutzungsempfehlungen für DirectQuery gelten auch für beide Ansätze zum Herstellen einer Verbindung mit SAP HANA. Dies ist insbesondere für die Best Practices der Fall, die eine zufriedenstellende Leistung garantieren sollen. Diese Empfehlungen werden ausführlich im Artikel [Verwenden von DirectQuery mit Power BI](desktop-directquery-about.md) beschrieben.
   
## <a name="limitations"></a>Einschränkungen

In der folgenden Liste werden alle Features von SAP HANA aufgelistet, die nicht vollständig unterstützt werden oder sich mit Power BI anders verhalten. 

* **Über-/untergeordnete Hierarchien**: Diese werden in Power BI nicht angezeigt.
Dies liegt daran, dass Power BI über die SQL-Schnittstelle auf HANA zugreift. Mit SQL ist ein vollständiger Zugriff auf über-/untergeordnete Hierarchien jedoch nicht möglich.
* **Andere Hierarchiemetadaten**: Die grundlegende Struktur von Hierarchien wird in Power BI angezeigt. Einige Hierarchiemetadaten (z.B. die Steuerung des Verhaltens unregelmäßiger Hierarchien) haben jedoch keine Auswirkung.
Auch dies ist auf die Einschränkungen zurückzuführen, die die SQL-Schnittstelle mit sich bringt.
* **Verbindung über SSL**: Sie könne keine Verbindung mit SAP HANA-Instanzen herstellen, die für die Nutzung von SSL konfiguriert wurden.
Unterstützung für Attributansichten: Power BI kann eine Verbindung mit analytischen Ansichten und Berechnungsansichten herstellen. Eine direkte Verbindung mit Attributansichten ist hingegen nicht möglich.
* **Unterstützung für Katalogobjekte**: Power BI kann keine Verbindung mit Katalogobjekten herstellen.
* **Änderungen an Variablen nach der Veröffentlichung**: Nachdem der Bericht veröffentlicht wurde, können Sie die Werte der HANA-Variablen nicht mehr direkt im Power BI-Dienst ändern. 
 
## <a name="known-issues"></a>Bekannte Probleme 
In der folgenden Liste werden alle bekannten Probleme beschrieben, die beim Herstellen einer Verbindung mit SAP HANA (DirectQuery) über Power BI auftreten. 

* **Problem mit HANA bei Abfragen für Zähler und andere Measures**: Falsche Daten werden von HANA zurückgegeben, wenn eine Verbindung mit einer analytischen Ansicht hergestellt wird und ein Zählermeasure sowie ein weiteres Verhältnismeasure in demselben Visual enthalten sind. Dieses Problem wird im SAP-Hinweis 2128928 (Unerwartete Ergebnisse beim Abfragen einer berechnete Spalte und eines Zählers) beschrieben. In diesem Fall ist das Verhältnismeasure falsch. 

* **Erstellung mehrerer Power BI-Spalten aus einer HANA-Spalte**: Bei einigen Berechnungsansichten, in denen eine HANA-Spalte in mehreren Hierarchien verwendet wird, stellt HANA zwei eigenständige Attribute bereit. Dies führt dazu, dass zwei Spalten in Power BI erstellt werden.  Diese werden allerdings standardmäßig ausgeblendet, und alle Abfragen im Zusammenhang mit Hierarchien oder Spalten verhalten sich korrekt. 
 
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu DirectQuery finden Sie in den folgenden Ressourcen:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [Lokales Datengateway](service-gateway-onprem.md)
