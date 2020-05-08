---
title: Leitfaden zum Datenabruf von paginierten Berichten
description: Dies ist ein Leitfaden zum Erstellen von Datenquellen und Datasets für paginierte Power BI-Berichte.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377648"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Leitfaden zum Datenabruf von paginierten Berichten

Dieser Artikel richtet sich an Berichtsautoren, die [paginierte Berichte](../paginated-reports/paginated-reports-report-builder-power-bi.md) in Power BI entwerfen. Er enthält Empfehlungen für das Entwerfen eines effektiven und effektiven Datenabrufs.

## <a name="data-source-types"></a>Datenquellentypen

Paginierte Berichte verfügen über native Unterstützung für relationale und analytische Datenquellen. Die Quellen werden entweder als cloudbasiert oder lokal kategorisiert. Lokale Datenquellen benötigen unabhängig davon, ob sie lokal oder auf einem virtuellen Computer gehostet werden, ein Datengateway, damit Power BI eine Verbindung herstellen kann. Cloudbasiert bedeutet, dass Power BI über eine Internetverbindung direkt eine Verbindung herstellen kann.

Wenn Sie den Datenquellentyp auswählen können (bei einem neuen Projekt eventuell möglich), wird empfohlen, cloudbasierte Datenquellen zu verwenden. Bei paginierten Berichten kann insbesondere dann eine Verbindung mit geringerer Netzwerklatenz hergestellt werden, wenn sich die Datenquellen in derselben Region wie Ihr Power BI-Mandant befinden. Außerdem ist es möglich, mithilfe des einmaligen Anmeldens (Single Sign-on, SSO) eine Verbindung zu diesen Quellen herzustellen. Dies bedeutet, dass die Identität des Berichtsbenutzers an die Datenquelle weitergeleitet werden kann, sodass benutzerspezifische Berechtigungen auf Zeilenebene erzwungen werden können. Derzeit wird das einmalige Anmelden für lokale Datenquellen nicht unterstützt (d. h. SQL Server Analysis Services kann keine spezifischen Berechtigungen auf Zeilenebene erzwingen).

> [!NOTE]
> Obwohl es derzeit nicht möglich ist, mithilfe von SSO eine Verbindung mit lokalen Datenbanken herzustellen, können Sie weiterhin Berechtigungen auf Zeilenebene erzwingen. Dies erfolgt durch das Übergeben des integrierten **UserID**-Felds an einen Datasetabfrageparameter. Die Datenquelle muss Benutzerprinzipalnamenwerte so speichern, dass Abfrageergebnisse ordnungsgemäß gefiltert werden können.
>
> Beachten Sie beispielsweise, dass jeder Vertriebsmitarbeiter als Zeile in der Tabelle für **Vertriebsmitarbeiter** gespeichert wird.  Die Tabelle enthält Spalten für Benutzerprinzipalnamen und die Vertriebsbereich von Vertriebsmitarbeitern. Zur Abfragezeit wird die Tabelle nach dem Benutzerprinzipalnamen des Berichtsbenutzers gefiltert und ist auch mit Umsatzdaten verknüpft, die einen inneren Join verwenden. Auf diese Weise kann bei der Abfrage effektiv nach Umsatzdatenzeilen zu den Vertriebsbereichen des Berichtsbenutzers gefiltert werden.

### <a name="relational-data-sources"></a>Relationale Datenquellen

Im Allgemeinen sind relationale Datenquellen für Berichte im operativen Stil (wie z. B. Verkaufsrechnungen) gut geeignet. Sie sind auch für Berichte geeignet, die sehr große Datasets abrufen müssen (mehr als 10.000 Zeilen). Relationale Datenquellen können auch gespeicherte Prozeduren definieren, die von Berichtsdatasets ausgeführt werden können. Gespeicherte Prozeduren bieten zahlreiche Vorteile:

- Parametrisierung
- Kapselung der Programmierlogik, die eine komplexere Datenvorbereitung ermöglicht (z. B. temporäre Tabellen, Cursor oder benutzerdefinierte Skalarfunktionen)
- verbesserte Wartbarkeit, sodass die Logik gespeicherter Prozeduren problemlos aktualisiert werden kann. In einigen Fällen kann dies erreicht werden, ohne dass paginierte Berichte geändert und noch mal veröffentlicht werden müssen (die Angabe von Spaltennamen und Datentypen bleibt unverändert).
- höhere Leistung, da Ausführungspläne für die Wiederverwendung zwischengespeichert werden
- Wiederverwendung gespeicherter Prozeduren in mehreren Berichten

In Power BI Report Builder können Sie den relationalen Abfrage-Designer verwenden, um eine Abfrageanweisung grafisch zu erstellen (gilt jedoch nur für Microsoft-Datenquellen).

### <a name="analytic-data-sources"></a>Analytische Datenquellen

Analytische Datenquellen sind gut für operative und analytische Berichte geeignet und können schnell zusammengefasste Abfrageergebnisse für sehr große Datenvolumes bereitstellen. Modellmeasures und KPIs können komplexe Geschäftsregeln kapseln, um die Zusammenfassung der Daten zu erreichen. Diese Datenquellen sind jedoch nicht für Berichte geeignet, die sehr große Datasets abrufen müssen (mehr als 10.000 Zeilen).

In Power BI Report Builder stehen zwei Abfrage-Designer zur Auswahl: der Analysis Services-DAX-Abfrage-Designer und der Analysis Services-MDX-Abfrage-Designer. Diese Designer können für Power BI-Datasetdatenquellen, beliebige SQL Server Analysis Services- oder Azure Analysis Services-Modelle (tabellarisch oder mehrdimensional) verwendet werden.

Wir empfehlen Ihnen, den DAX-Abfrage-Designer zu verwenden, da die Bereitstellung vollständig Ihren Abfrageanforderungen entspricht. Wenn das Modell nicht die benötigten Measures definiert, müssen Sie in den Abfragemodus wechseln. In diesem Modus können Sie die Abfrageanweisung anpassen, indem Sie Ausdrücke hinzufügen (um eine Zusammenfassung zu erzielen).

Der MDX-Abfrage-Designer erfordert, dass das Modell Measures enthält. Der Designer verfügt über zwei Funktionen, die vom DAX-Abfrage-Designer nicht unterstützt werden. Dieser ermöglicht Ihnen Folgendes:

- Definieren berechneter Elemente auf Abfrageebene (in MDX)
- Konfigurieren von Datenbereichen, um [Serveraggregate](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) in Nicht-Detailgruppen anzufordern. Wenn Ihr Bericht Zusammenfassungen von semiadditiven oder nicht additiven Measures (z. B. Zeitintelligenzberechnungen oder unterschiedliche Zähler) enthalten muss, ist es wahrscheinlich effizienter, Serveraggregate zu verwenden, als Detailzeilen auf niedriger Ebene abzurufen und den Bericht Zusammenfassungen berechnen zu lassen.

## <a name="query-result-size"></a>Abfrageergebnisgröße

Im Allgemeinen empfiehlt es sich, nur die Daten abzurufen, die für Ihren Bericht erforderlich sind. Rufen Sie also keine Spalten oder Zeilen ab, die für den Bericht nicht erforderlich sind.

Zum Begrenzen von Zeilen sollten Sie immer die restriktivsten Filter anwenden und Aggregatabfragen definieren. Aggregatabfragen gruppieren Quelldaten und fassen diese zusammen, um Ergebnisse mit größerer Größe abzurufen. Nehmen Sie beispielsweise an, dass Ihr Bericht eine Zusammenfassung der Verkäufe von Vertriebsmitarbeitern enthalten muss. Anstatt alle Auftragszeilen abzurufen, erstellen Sie eine Datasetabfrage, die nach Vertriebsmitarbeiter gruppiert und die Umsätze für jede Gruppe zusammenfasst.

## <a name="expression-based-fields"></a>Ausdrucksbasierte Felder

Es ist möglich, ein Berichtsdataset mit Feldern zu erweitern, die auf Ausdrücken basieren. Wenn Ihr Dataset z. B. den Vornamen und den Nachnamen des Kunden erstellt, kann ein Feld, in dem die beiden Felder verkettet werden, den vollständigen Namen des Kunden bilden. Sie haben zwei Möglichkeiten, um diese Berechnung zu erreichen. Sie können:

- ein _berechnetes Feld_ erstellen, bei dem es sich um ein Datasetfeld handelt, das auf einem Ausdruck basiert.
- einen Ausdruck direkt in die Datasetabfrage einfügen (unter Verwendung der nativen Sprache der Datenquelle), was zu einem regulären Datasetfeld führt.

Wenn möglich, wird die letztere Option empfohlen. Es gibt zwei gute Gründe, warum das Einfügen von Ausdrücken direkt in die Datasetabfrage besser ist:

- Es ist möglich, dass Ihre Datenquelle optimiert ist, um den Ausdruck effizienter zu evaluieren als Power BI (dies ist insbesondere bei relationalen Datenbanken der Fall).
- Die Berichtsleistung wurde verbessert, da es nicht erforderlich ist, dass Power BI berechnete Felder vor dem Rendern des Berichts materialisiert. Berechnete Felder können die Berichtsrenderingzeit deutlich erweitern, wenn Datasets eine große Anzahl von Zeilen abrufen.

## <a name="field-names"></a>Feldnamen

Wenn Sie ein Dataset erstellen, werden dessen Felder automatisch nach den Abfragespalten benannt. Es ist möglich, dass diese Namen nicht benutzerfreundlich oder intuitiv sind. Es ist auch möglich, dass Spaltennamen der Quellabfrage Zeichen enthalten, die in RDL-Objektbezeichnern (Report Definition Language) unzulässig sind (z. B. Leerzeichen und Symbole). In diesem Fall werden die unzulässigen Zeichen durch einen Unterstrich (_) ersetzt.

Es wird empfohlen, zuerst zu überprüfen, ob alle Feldnamen zwar benutzerfreundlich und kurz, aber dennoch aussagekräftig sind. Wenn dies nicht der Fall ist, sollten Sie diese _vor_ dem Berichtslayout umbenennen. Dies liegt daran, dass umbenannte Felder keine Änderungen an den Ausdrücken vornehmen, die im Berichtslayout verwendet werden. Wenn Sie sich dafür entscheiden, Felder umzubenennen, nachdem Sie mit dem Berichtslayout begonnen haben, müssen Sie alle unterbrochenen Ausdrücke suchen und aktualisieren.

## <a name="filter-vs-parameter"></a>Filter im Vergleich zu Parametern

Es ist wahrscheinlich, dass Ihre paginierten Berichtsentwürfe Berichtsparameter aufweisen. Berichtsparameter werden häufig verwendet, um den Berichtsbenutzer aufzufordern, den Bericht zu filtern. Als Autor eines paginierten Berichts haben Sie zwei Möglichkeiten für die Berichtsfilterung. Berichtsparameter können den folgenden Elementen zugeordnet werden:

- einem _Datasetfilter_, in dessen Fall die Berichtsparameterwerte zum Filtern der bereits vom Dataset abgerufenen Daten verwendet werden
- einem _Datasetparameter_, in dessen Fall die Berichtsparameterwerte in die native Abfrage eingefügt werden, die an die Datenquelle gesendet wird

> [!NOTE]
> Alle Berichtsdatasets werden _sitzungsbasiert_ für bis zu zehn Minuten _nach der letzten Verwendung zwischengespeichert_. Ein Dataset kann beim Übermitteln neuer Parameterwerte (Filtern), beim Rendern des Berichts in einem anderen Format oder bei der Interaktion mit dem Berichtsentwurf auf irgendeine Weise wieder verwendet werden (z. B. beim Umschalten der Sichtbarkeit oder bei der Sortierung).

Sehen Sie sich ein Beispiel für einen Verkaufsbericht an, der über einen einzelnen Berichtsparameter verfügt, um den Bericht nach einem einzelnen Jahr zu filtern. Das Dataset ruft die _Umsätze für alle Jahre_ ab. Dies ist der Fall, da der Berichtsparameter den Datasetfiltern zugeordnet wird. Im Bericht werden Daten für das angeforderte Jahr angezeigt, bei dem es sich um eine Teilmenge der Datasetdaten handelt. Wenn der Berichtsbenutzer den Berichtsparameter in ein anderes Jahr ändert und dann den Bericht anzeigt, muss Power BI keine Quelldaten abrufen. Stattdessen wird ein anderer Filter auf das bereits zwischengespeicherte Dataset angewendet. Nachdem das Dataset zwischengespeichert wurde, kann das Filtern sehr schnell erfolgen.

Sehen Sie sich nun einen anderen Berichtsentwurf an. Dieses Mal ordnet der Berichtsentwurf den Berichtsparameter „Sales Year“ einem Datasetparameter zu. Auf diese Weise fügt Power BI den Jahreswert in die native Abfrage ein, und das Dataset ruft Daten nur für dieses Jahr ab. Jedes Mal, wenn der Berichtsbenutzer den Berichtsparameterwert für das Jahr ändert und dann den Bericht anzeigt, ruft das Dataset nur für dieses Jahr ein neues Abfrageergebnis ab.

Bei beiden Entwurfsansätzen können Berichtsdaten gefiltert werden, und beide Entwürfe können im Zusammenhang mit Ihren Berichtsentwürfen gut funktionieren. Ein optimierter Entwurf hängt jedoch von den erwarteten Datenmengen, der Datenvolatilität und dem erwarteten Verhalten ihrer Berichtsbenutzer ab.

Die _Datasetfilterung_ wird empfohlen, wenn Sie davon ausgehen, dass eine andere Teilmenge der Datasetzeilen mehrmals wiederverwendet wird (wodurch die Renderingzeit gespart wird, da neue Daten nicht abgerufen werden müssen). In diesem Szenario erkennen Sie, dass die Kosten für das Abrufen eines größeren Datasets mit der Häufigkeit, mit der es wieder verwendet wird, reduziert werden können. Es eignet sich also besonders für Abfragen, deren Generierung zeitaufwändig ist. Achten Sie jedoch darauf, dass sich das Zwischenspeichern großer Datasets auf Benutzerbasis negativ auf die Leistung und den Kapazitätsdurchsatz auswirkt.

Die _Datasetparametrisierung_ wird empfohlen, wenn Sie davon ausgehen, dass es unwahrscheinlich ist, dass eine andere Teilmenge von Datasetzeilen angefordert wird oder die Anzahl der zu filternden Datasetzeilen wahrscheinlich sehr groß (und ineffizient für den Cache) ist. Dieser Entwurfsansatz funktioniert auch gut, wenn der Datenspeicher flüchtig ist. In diesem Fall führt jede Änderung des Berichtsparameterwerts dazu, dass aktuelle Daten abgerufen werden.

## <a name="non-native-data-sources"></a>Nicht native Datenquellen

Wenn Sie paginierte Berichte auf der Grundlage von Datenquellen entwickeln müssen, die [nicht nativ von paginierten Berichten](../paginated-reports/paginated-reports-data-sources.md) unterstützt werden, können Sie zuerst ein Power BI Desktop-Datenmodell entwickeln. Auf diese Weise können Sie eine Verbindung mit [über 100 Power BI-Datenquellen](../power-bi-data-sources.md) herstellen. Nach der Veröffentlichung im Power BI-Dienst können Sie dann einen paginierten Bericht entwickeln, der eine Verbindung mit dem Power BI-Dataset herstellt.

## <a name="data-integration"></a>Datenintegration

Wenn Sie Daten aus mehreren Datenquellen kombinieren müssen, haben Sie zwei Möglichkeiten:

- **Kombinieren von Berichtsdatasets:** Wenn die Datenquellen [nativ von paginierten Berichten](../paginated-reports/paginated-reports-data-sources.md) unterstützt werden, können Sie berechnete Felder erstellen, die die Report Builder-Funktionen [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) oder [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) verwenden.
- **Entwickeln eines Power BI Desktop-Modells:** Wahrscheinlich ist es jedoch effizienter, ein Datenmodell in Power BI Desktop zu entwickeln. Sie können Power Query verwenden, um Abfragen basierend auf [unterstützten Datenquellen](../power-bi-data-sources.md) zu kombinieren. Nach der Veröffentlichung im Power BI-Dienst können Sie dann einen paginierten Bericht entwickeln, der eine Verbindung mit dem Power BI-Dataset herstellt.

## <a name="sql-server-complex-data-types"></a>Komplexe SQL Server-Datentypen

Da SQL Server eine lokale Datenquelle ist, muss Power BI eine Verbindung über ein Gateway herstellen. Das Gateway unterstützt jedoch nicht das Abrufen von Daten für komplexe Datentypen. Zu den komplexen Datentypen gehören integrierte Typen wie die [räumlichen Datentypen](/sql/relational-databases/spatial/spatial-data-sql-server) „GEOMETRY“ und „GEOGRAPHY“ sowie [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). Sie enthalten auch benutzerdefinierte Typen, die durch eine Klasse einer Assembly in der CLR (Common Language Runtime) von Microsoft .NET Framework implementiert werden.

Das Zeichnen räumlicher Daten und Analysen in der Kartenvisualisierung erfordert räumliche SQL Server-Daten. Daher ist es nicht möglich, mit der Kartenvisualisierung zu arbeiten, wenn SQL Server die Datenquelle ist. Dies funktioniert, wenn Ihre Datenquelle Azure SQL-Datenbank ist, da Power BI keine Verbindung über ein Gateway herstellt.

## <a name="data-related-images"></a>Datenbezogene Bilder

Bilder können zum Hinzufügen von Logos oder Bildern zum Berichtslayout verwendet werden. Wenn sich Bilder auf die von einem Berichtsdataset abgerufenen Zeilen beziehen, haben Sie zwei Möglichkeiten:

- Es ist möglich, dass Bilddaten auch aus der Datenquelle abgerufen werden können (sofern sie bereits in einer Tabelle gespeichert sind).
- Wenn die Bilder auf einem Webserver gespeichert werden, können Sie einen dynamischen Ausdruck verwenden, um den URL-Pfad der Bilder zu erstellen.

Weitere Informationen und Vorschläge finden Sie unter [Bilderleitfaden zu paginierten Berichten](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Redundanter Datenabruf

Es ist möglich, dass Ihr Bericht redundante Daten abruft. Dies kann vorkommen, wenn Sie Datasetabfragefelder löschen oder der Bericht nicht verwendete Datasets enthält. Vermeiden Sie diese Situationen, da sie unnötige Belastungen für Ihre Datenquellen, das Netzwerk und die Power BI-Kapazitätsressourcen verursachen.

### <a name="deleted-query-fields"></a>Gelöschte Abfragefelder

Auf der Seite **Felder** des Fensters **Dataseteigenschaften** können Sie _Abfragefelder_ für Datasets löschen (Abfragefelder werden den von der Datasetabfrage abgerufenen Spalten zugeordnet). Report Builder entfernt jedoch keine entsprechenden Spalten aus der Datasetabfrage.

Wenn Sie Abfragefelder aus dem Dataset löschen müssen, empfiehlt es sich, die entsprechenden Spalten aus der Datasetabfrage zu entfernen. Report Builder entfernt automatisch alle redundanten Abfragefelder. Achten Sie auch darauf, die Datasetabfrageanweisung zu ändern, um die Spalten zu entfernen, wenn Sie die Abfragefelder löschen.

### <a name="unused-datasets"></a>Nicht verwendete Datasets

Wenn ein Bericht ausgeführt wird, werden alle Datasets auch dann ausgewertet, wenn sie nicht an Berichtsobjekte gebunden sind. Aus diesem Grund sollten Sie alle Test- oder Entwicklungsdatasets entfernen, bevor Sie einen Bericht veröffentlichen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Unterstützte Datenquellen für paginierte Power BI-Berichte](../paginated-reports/paginated-reports-data-sources.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
