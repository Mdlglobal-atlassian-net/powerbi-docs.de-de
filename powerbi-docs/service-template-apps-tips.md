---
title: Tipps für die Erstellung von Vorlagen-Apps in Power BI
description: Tipps für die Erstellung von Abfragen, Datenmodellen, Berichten und Dashboards für gute Vorlagen-Apps
author: teddybercovitz
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: tebercov
ms.openlocfilehash: dcb7ba5dabbbb0387b92908f7e299d61f2145d44
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376590"
---
# <a name="tips-for-authoring-template-apps-in-power-bi"></a>Tipps für die Erstellung von Vorlagen-Apps in Power BI

Wenn Sie in Power BI [Ihre Vorlagen-App erstellen](service-template-apps-create.md), besteht ein Teil des Erstellungsprozesses in der Logistik für die Erstellung eines Arbeitsbereichs, für Tests und für die Produktionsphase. Der andere wichtige Teil besteht ganz klar in der Erstellung des Berichts und des Dashboards. Wir können den Erstellungsprozess in vier Hauptkomponenten unterteilen. Das Arbeiten mit diesen Komponenten hilft Ihnen dabei, die Vorlagen-App bestmöglich zu erstellen:

* Mit **Abfragen**[verbinden](desktop-connect-to-data.md) und [transformieren](desktop-query-overview.md) Sie die Daten, und Sie definieren [Parameter](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* In dem **Datenmodell** können Sie [Beziehungen](desktop-create-and-manage-relationships.md), [Measures](desktop-measures.md) und Q&A-Verbesserungen erstellen.  
* **[Berichtseiten](desktop-report-view.md)** enthalten Visuals und Filter für Einblicke in Ihre Daten.  
* **[Dashboards](consumer/end-user-dashboards.md)** und [Kacheln](service-dashboard-create.md) bieten eine Übersicht über die enthaltenen Einblicke.
* Dank der Beispieldaten kann Ihre App unmittelbar nach der Installation gefunden werden.

Möglicherweise sind Sie mit den einzelnen verfügbaren Power BI-Features vertraut. Beim Erstellen einer Vorlagen-App sind weitere Punkte für jedes Element zu beachten. Weitere Informationen finden Sie in den einzelnen Abschnitten unten.

<a name="queries"></a>

## <a name="queries"></a>Abfragen
Bei Vorlagen-Apps werden die in Power BI Desktop entwickelten Abfragen zum Herstellen einer Verbindung mit Ihrer Datenquelle und zum Importieren von Daten verwendet. Diese Abfragen sind erforderlich, um ein konsistentes Schema zurückzugeben. Sie werden für die geplante Datenaktualisierung unterstützt (DirectQuery wird nicht unterstützt).

### <a name="connect-to-your-api"></a>Herstellen einer Verbindung mit der API
Zunächst müssen Sie eine Verbindung mit der API aus Power BI Desktop herstellen, um Abfragen zu erstellen.

Sie können die in Power BI Desktop verfügbaren Datenconnectors verwenden, um eine Verbindung mit der API herzustellen. Sie können mit dem Web-Datenconnector („Daten abrufen“ > „Web“) eine Verbindung mit Ihrer Rest-API oder mit dem OData-Connector („Daten abrufen“ > „OData-Feed“) eine Verbindung mit dem OData-Feed herstellen.

> [!NOTE]
> Da Vorlagen-Apps derzeit keine benutzerdefinierten Connectors unterstützen, sollten Sie untersuchen, ob Sie Odatafeed Auth 2.0 als Ausgleich für einige der Verbindungsanwendungsfälle oder zum Übermitteln Ihres Connectors zur Zertifizierung verwenden können. Informationen zum Entwickeln eines Connectors und seiner Zertifizierung finden Sie in der [Dokumentation zu Datenconnectors](https://aka.ms/DataConnectors).

### <a name="consider-the-source"></a>Überlegungen zur Quelle
Die Abfragen definieren die Daten, die im Datenmodell enthalten sind. Abhängig von der Größe Ihres Systems sollten diese Abfragen auch Filter enthalten, um sicherzustellen, dass Ihre Kunden mit einer überschaubaren Größe arbeiten, die für Ihr Geschäftsszenario geeignet ist.

Power BI-Vorlagen-Apps können mehrere Abfragen parallel und für mehrere Benutzer gleichzeitig ausführen.  Planen Sie Ihre Strategie für die Bandbreitendrosselung und Parallelität im Voraus, und fragen Sie uns, wie Sie Ihre Vorlagen-App fehlertolerant erstellen können.

### <a name="schema-enforcement"></a>Schemaerzwingung
Stellen Sie sicher, dass Ihre Abfragen bei Änderungen im System stabil bleiben. Durch Änderungen am Schema bei der Aktualisierung kann das Modell unterbrochen werden. Wenn die Quelle unter Umständen bei einigen Abfragen ein Nullschema oder ein fehlendes Schema zurückgeben kann, empfiehlt es sich, eine leere Tabelle zurückzugeben oder eine aussagekräftige benutzerdefinierte Fehlermeldung auszugeben.

### <a name="parameters"></a>Parameter
Mit [Parametern](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) in Power BI Desktop können Benutzer Eingabewerte angeben, mit denen die von den Benutzern abgerufenen Daten angepasst werden. Machen Sie sich vorab Gedanken über die Parameter, und vermeiden Sie so die Nachbearbeitung nach der zeitaufwendigen Erstellung detaillierter Abfragen oder Berichte.

> [!NOTE]
> Vorlagen-Apps unterstützen alle Parameter mit Ausnahme von „Any“ und „Binary“.
>

### <a name="additional-query-tips"></a>Weitere Tipps zu Abfragen

* Stellen Sie sicher, dass alle Spalten richtig angegeben sind.
* Spalten müssen über aussagekräftige Namen verfügen (siehe [Q&A](#qa)).  
* Bei gemeinsam verwendeter Logik empfiehlt sich die Verwendung von Funktionen oder Abfragen.  
* Datenschutzebenen werden im Dienst derzeit nicht unterstützt. Wenn Sie eine Aufforderung zu Datenschutzebenen erhalten, müssen Sie die Abfrage möglicherweise neu schreiben, um relative Pfade zu verwenden.  

## <a name="data-models"></a>Datenmodelle

Durch ein klar definiertes Datenmodell wird sichergestellt, dass Ihre Kunden mühelos und intuitiv mit der Vorlagen-App interagieren können. Erstellen Sie das Datenmodell in Power BI Desktop.

> [!NOTE]
> Ein Großteil der grundlegenden Modellierung (Typisierung, Spaltennamen) sollte in den [Abfragen](#queries) erfolgen.

### <a name="qa"></a>Q&A
Die Modellierung wirkt sich auch darauf aus, inwiefern beim Q&A Ergebnisse für Ihre Kunden bereitgestellt werden können. Stellen Sie sicher, dass Sie für häufig verwendete Spalten Synonyme hinzufügen und dass Sie die Spalten in den [Abfragen](#queries) richtig benannt haben.

### <a name="additional-data-model-tips"></a>Weitere Tipps zum Datenmodell

Stellen Sie sicher, dass Sie:

* auf alle Wertspalten Formatierung angewendet haben. in der Abfrage Typen anwenden.  
* auf alle Measures Formatierung angewendet haben.
* Standardzusammenfassung eingestellt haben. wo zutreffend (z.B. für eindeutige Werte), „Nicht zusammenfassen“ eingestellt haben.  
* wenn zutreffend, Datenkategorie eingestellt haben.  
* nach Bedarf Beziehungen eingestellt haben.  

## <a name="reports"></a>Berichte
Die Berichtseiten bieten zusätzliche Einblicke in die in der Vorlagen-App enthaltenen Daten. Verwenden Sie die Seiten der Berichte, um die wichtigsten unternehmerischen Fragestellungen zu beantworten, auf die mit der Vorlagen-App eingegangen werden soll. Erstellen Sie den Bericht mithilfe von Power BI Desktop.


### <a name="additional-report-tips"></a>Weitere Tipps zu Berichten

* Verwenden Sie mehrere Visuals pro Seite für die Kreuzfilterung.  
* Richten Sie die Visuals sorgfältig aus (keine Überlappungen).  
* Das Layout der Seite ist auf den Modus „4:3“ oder „16:9“ festgelegt.  
* Alle dargestellten Aggregationen sind im Hinblick auf numerische Werte sinnvoll (Mittelwerte, eindeutige Werte).  
* Segmentierungen führen zu vernünftigen Ergebnissen.  
* Das Logo ist mindestens im obersten Bericht vorhanden.  
* Elemente sind weitestgehend im Farbschema des Kunden definiert.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Dashboards
Das Dashboard ist für Ihre Kunden der zentrale Ort der Interaktion mit Ihrer Vorlagen-App. Es sollte eine Übersicht über die Inhalte, insbesondere die wichtigen Metriken Ihres Geschäftsszenarios, enthalten.

Zum Erstellen eines Dashboards für Ihre Vorlagen-App laden Sie einfach Ihre PBIX-Datei über „Daten abrufen“ > „Dateien“ hoch, oder veröffentlichen Sie sie direkt über Power BI Desktop.


### <a name="additional-dashboard-tips"></a>Weitere Tipps zum Dashboard

* Behalten Sie beim Anheften dasselbe Design bei, sodass die Kacheln im Dashboard einheitlich sind.  
* Heften Sie ein Logo an das Design an, damit Kunden wissen, woher das Paket stammt.  
* Als Layout für die meisten Bildschirmauflösungen empfehlen sich fünf bis sechs kleine Kacheln in der Breite.  
* Alle Dashboardkacheln müssen über geeignete Titel bzw. Untertitel verfügen.  
* Ziehen Sie für verschiedene Szenarios vertikale oder horizontale Gruppierungen im Dashboard in Betracht.  

## <a name="sample-data"></a>Beispieldaten
Vorlagen-Apps umschließen als Teil der Erstellungsphase der App die Cachedaten im Arbeitsbereich als Teil der App:

* Dies ermöglicht der installierenden Person, Funktionalität und Zweck der App zu verstehen, bevor die Verbindung mit den Daten hergestellt wird.
* Dies schafft eine Erfahrung, die die installierende Person dazu veranlasst, die App-Funktionen weiter zu erforschen, was zum Herstellen der Verbindung mit dem App-Dataset führt.

Wir empfehlen Ihnen, vor dem Erstellen der App für qualitativ hochwertige Beispieldaten zu sorgen. Stellen Sie sicher, dass App-Bericht und Dashboards mit Daten gefüllt sind.

## <a name="publishing-on-appsource"></a>Veröffentlichen auf AppSource
Vorlagen-Apps können auf AppSource veröffentlicht werden – befolgen Sie diese Richtlinien, bevor Sie Ihre App an AppSource übermitteln:

* Achten Sie darauf, eine Vorlagen-App mit ansprechenden Beispieldaten zu erstellen, die der installierenden Person helfen zu verstehen, was die App kann (leerer Bericht und leeres Dashboard sind nicht erwünscht).
Vorlagen-Apps unterstützen Apps, die nur Beispieldaten enthalten; achten Sie darauf, das Kontrollkästchen „Statisch“ zu aktivieren. [Weitere Informationen](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Halten Sie Anweisungen für das Validierungsteam bereit, die Anmeldeinformationen und Parameter enthalten, die für das Herstellen der Verbindung mit Daten erforderlich sind.
* Die Anwendung muss in Power BI und in Ihrem CPP-Angebot ein App-Symbol enthalten. [Weitere Informationen](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Landing Page muss konfiguriert sein. [Weitere Informationen](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* Befolgen Sie die Dokumentation [Power BI-App-Angebot](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer).
* Falls ein Dashboard Teil Ihrer App ist, stellen Sie sicher, dass es nicht leer ist.
* Installieren Sie die App über den App-Link, bevor Sie sie übermitteln, stellen Sie sicher, dass Sie die Verbindung mit dem Dataset herstellen können und die App wie geplant funktioniert.
* Entladen Sie vor dem Hochladen der PBIX-Datei in den Vorlagenarbeitsbereich unbedingt alle unnötigen Verbindungen.
* Befolgen Sie [Bewährte Entwurfsmethoden für Berichte und Visualisierungen](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-best-practices) für Power BI, um den besten Eindruck bei Ihren Benutzern zu machen und die Genehmigung für die Verteilung zu erhalten.
<!--- * In general, only application with valuable functionality can be approved for general use on AppSource. Application with sample data content only must have either a guidance or statistical value.) -->

## <a name="create-a-download-link-for-the-app"></a>Erstellen eines Downloadlinks für die App

Nach der Veröffentlichung der Vorlagen-App in AppSource, sollten Sie auf Ihrer Website einen Downloadlink erstellen. Dieser sollte zu einem der beiden Ziele führen:
* AppSource-Downloadseite: Diese Seite ist öffentlich zugänglich. Den Link können Sie über Ihre AppSource-Seite erstellen.
* Power BI: Dieser Link kann von Power BI-Benutzern geöffnet werden.

Sehen Sie sich das folgende Codebeispiel an, um einen Benutzer über den Link zum Download der App in Power BI weiterzuleiten: [GitHub-Repository](https://github.com/microsoft/Template-apps-examples/tree/master/src).
[![Downloadlink für die App](media/service-template-apps-tips/service-template-apps-tips-download.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)



## <a name="known-limitations"></a>Bekannte Einschränkungen

| Feature | Bekannte Einschränkung |
|---------|---------|
|Inhalt:  Datasets   | Genau ein Dataset sollte vorhanden sein. Nur Datasets, die in Power BI Desktop erstellt wurden (.pbix-Dateien), sind zulässig. <br>Nicht unterstützt: Datasets aus anderen Vorlagen-Apps, arbeitsbereichübergreifende Datasets, paginierte Berichte (.rdl-Dateien), Excel-Arbeitsmappen |
|Inhalt: Dashboards | Echtzeitkacheln sind nicht zulässig (d. h. Push- oder Streamingdatasets werden nicht unterstützt). |
|Inhalt: Dataflows | Nicht unterstützt: Dataflows |
|Inhalte aus Dateien | Nur PBIX-Dateien sind zulässig. <br>Nicht unterstützt: .rdl-Dateien (paginierte Berichte), Excel-Arbeitsmappen   |
| Datenquellen | Datenquellen, die für geplante Datenaktualisierungen in der Cloud unterstützt werden, sind zulässig. <br>Nicht unterstützt: <li> DirectQuery</li><li>Liveverbindungen (ausgenommen Azure Analysis Services)</li> <li>Lokale Datenquellen (persönliche Gateways und Enterprise-Gateways werden nicht unterstützt)</li> <li>Echtzeit (Pushdataset wird nicht unterstützt)</li> <li>Zusammengesetzte Modelle</li></ul> |
| Dataset: arbeitsbereichübergreifend | Arbeitsbereichübergreifende Datasets sind nicht zulässig.  |
| Abfrageparameter | Nicht unterstützt: Parameter vom Typ „Any“ oder „Binary“ blockieren den Aktualisierungsvorgang für Datasets. |
| Power BI-Visuals | Es werden nur öffentlich verfügbare Power BI-Visuals unterstützt. [Power BI-Organisationsvisuals](developer/visuals/power-bi-custom-visuals-organization.md) werden nicht unterstützt. |

## <a name="next-steps"></a>Nächste Schritte

[Was sind Power BI-Vorlagen-Apps?](service-template-apps-overview.md)
