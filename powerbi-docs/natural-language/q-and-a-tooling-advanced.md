---
title: Bearbeiten des linguistischen Schemas für Q&A und Hinzufügen von Ausdrücken in Power BI Desktop
description: Erfahren Sie, wie Sie mit Power BI Desktop das von Power BI Q&A verwendete linguistische Schema bearbeiten können.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 9499dd99d89619d096d86ac676c54ebb214c3a55
ms.sourcegitcommit: 220910f0b68cb1e265ccd5ac0cee4ee9c6080b26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82841846"
---
# <a name="edit-qa-linguistic-schema-and-add-phrasings-in-power-bi-desktop"></a>Bearbeiten des linguistischen Schemas für Q&A und Hinzufügen von Ausdrücken in Power BI Desktop 
Indem Sie gängige Ausdrücke und natürliche Sprache verwenden, können Sie Ihre Daten effizient auswerten. Noch besser können Sie profitieren, wenn Ihre Daten Antworten liefern. Wenn Sie Power BI eine Frage stellen, bemüht sich das Programm, diese richtig zu beantworten. Für eine noch bessere Interaktion mit Q&A können Sie die Antworten optimieren. Eine Möglichkeit hierzu besteht darin, das linguistische Schema zu bearbeiten. 

Alles beginnt mit Ihren Unternehmensdaten.  Je besser das Datenmodell, desto einfacher ist es für Benutzer, qualitativ hochwertige Antworten zu erhalten. Eine Möglichkeit zur Verbesserung des Modells besteht darin, ein linguistisches Schema hinzuzufügen, das Terminologie und Beziehungen zwischen Tabellen- und Spaltennamen in Ihrem Dataset definiert und kategorisiert. Ihre linguistischen Schemas verwalten Sie mit Power BI Desktop. 

Bei Q&A gibt es zwei Seiten.  Die erste Seite besteht in der Vorbereitung oder *Modellierung*.  Die zweite Seite ist das Stellen von Fragen und das Erkunden der Daten, die *Nutzung*. In einigen Unternehmen können Mitarbeiter, die als *Datenmodellierer* oder IT-Administratoren fungieren, die Datasets zusammenstellen, die Datenmodelle erstellen und die Datasets in Power BI veröffentlichen.  Eine andere Gruppe von Mitarbeitern, die „Consumer“, nutzen die Daten online.  In anderen Unternehmen werden diese Rollen ggf. kombiniert. 

Dieser Artikel richtet sich an Datenmodellierer – also Personen, die Datasets optimieren, um die bestmöglichen Q&A-Ergebnisse zu erzielen. 

## <a name="what-is-a-linguistic-schema"></a>Was ist ein linguistisches Schema?
Ein linguistisches Schema beschreibt Begriffe und Satzglieder, die Q&A für Objekte innerhalb eines Datasets verstehen soll, einschließlich Wortarten, Synonymen und Ausdrücken, die sich auf dieses Dataset beziehen. Beim Importieren oder Verbinden mit einem Dataset erstellt Power BI ein linguistisches Schema, das auf der Struktur des Datasets basiert. Wenn Sie Q&A eine Frage stellen, wird nach Übereinstimmungen und Beziehungen in den Daten gesucht, um die Absicht Ihrer Frage herauszufinden. Beispielsweise wird nach Nomen, Verben, Adjektiven, Ausdrücken und anderen Elementen gesucht. Außerdem wird nach Beziehungen gesucht, z.B. welche Spalten Objekte eines Verbs sind. 

Sie sind wahrscheinlich mit den verschiedenen Wortarten vertraut (falls nicht, siehe unten), das Konzept *Ausdrücke* ist Ihnen aber möglicherweise neu.  Mithilfe von *Ausdrücken* werden die Beziehungen zwischen Dingen beschrieben. Um beispielsweise die Beziehung zwischen Kunden und Produkten zu beschreiben, könnten Sie sagen: „Kunden kaufen Produkte“. Oder um die Beziehung zwischen Kunden und Alter zu beschreiben, könnten Sie sagen: „Das Lebensalter gibt an, wie alt Kunden sind“. Um die Beziehung zwischen Kunden und Telefonnummern zu beschreiben, könnten Sie einfach sagen: „Kunden haben Telefonnummern“.

Diese Ausdrücke gibt es in verschiedenen Formen und Ausprägungen. Einige entsprechen Beziehungen im Datenmodell direkt. Einige setzen Spalten mit Tabellen in Beziehung, in denen sie enthalten sind. Andere verknüpfen mehrere Tabellen und Spalten in komplexen Beziehungen. In allen Fällen beschreiben sie Zusammenhänge mit alltäglichen Begriffen.

Linguistische Schemas werden im YAML-Format gespeichert. Dieses Format ist mit dem beliebten JSON-Format verwandt, bietet aber eine flexiblere und leichter lesbare Syntax. Linguistische Schemas können bearbeitet, exportiert und in Power BI Desktop importiert werden.

## <a name="prerequisites"></a>Voraussetzungen

- Wenn Sie den Artikel [Verwenden von Q&A in Power BI Desktop für Abfragen in natürlicher Sprache](q-and-a-best-practices.md) noch nicht gelesen haben, sollten Sie diesen Artikel zuerst lesen. Er enthält zahlreiche Tipps zur Gestaltung und Verbesserung Ihres Datenmodells und einen wichtigen Abschnitt zum Hinzufügen von Synonymen.  
- Laden Sie die [YAML- und PBIX-Beispieldateien](https://go.microsoft.com/fwlink/?linkid=871858) herunter.   
- Installieren Sie einen YAML-Datei-Editor. Wir empfehlen die Verwendung von [Visual Studio Code](https://code.visualstudio.com/).

### <a name="set-up-an-editor-for-yaml-files"></a>Einrichten eines Editors für YAML-Dateien
Wir empfehlen, linguistische Schemadateien mit der Erweiterung YAML mit Visual Studio Code zu bearbeiten. Visual Studio Code unterstützt standardmäßig YAML-Dateien und kann zur spezifischen Validierung des linguistischen Schemaformats von Power BI erweitert werden.
1. Installieren Sie [Visual Studio Code](https://code.visualstudio.com/).    

2. Wählen Sie das linguistische Beispielschema aus, das Sie zuvor gespeichert haben: [YAML-Datei](https://go.microsoft.com/fwlink/?linkid=871858) (SummerOlympics.lsdl.yaml).    
4. Wählen Sie **Visual Studio Code** und **Always use this app to open .yaml files** (Immer diese App verwenden, um YAML-Dateien zu öffnen) aus.

    ![Wie möchten Sie diese Datei öffnen?](media/q-and-a-tooling-advanced/power-bi-visual-code.png)

4. Installieren Sie in Visual Studio Code die Erweiterung „YAML Support by Red Hat“.    
    a. Wählen Sie die Registerkarte **Erweiterungen** (die letzte auf der linken Seite) aus, oder drücken Sie STRG+UMSCHALT+X.    
    ![Erweiterungssymbol](media/q-and-a-tooling-advanced/power-bi-extensions.png)    
    b. Suchen Sie nach „yaml“, und wählen Sie in der Liste **YAML Support by Red Hat** aus.    
    c. Klicken Sie auf **Installieren > Neu laden**.


## <a name="working-with-linguistic-schemas"></a>Arbeiten mit linguistischen Schemas

Es gibt zwei Arten, mit linguistischen Schemas zu arbeiten. Eine Möglichkeit besteht darin, die YAML-Datei über das Menüband in Power BI Desktop zu bearbeiten, zu importieren und zu exportieren. Diese Methode wird im Power BI-Artikel [Einführung in die Q&A-Tools](q-and-a-tooling-intro.md) abgedeckt. Sie müssen die YAML-Datei nicht öffnen, um Q&A zu verbessern. 

Die andere Möglichkeit zur Bearbeitung eines linguistischen Schemas besteht darin, die YAML-Datei direkt zu exportieren und zu bearbeiten.  Wenn Sie die YAML-Datei eines linguistischen Schemas bearbeiten, kennzeichnen Sie Spalten in der Tabelle als unterschiedliche grammatikalische Elemente und legen Wörter fest, die ein Kollege verwenden könnte, um eine Frage zu formulieren. Sie können beispielsweise die Spalten angeben, die das Subjekt und das Objekt des Verbs darstellen. Sie können alternative Wörter hinzufügen, die Kollegen verwenden können, um auf Tabellen, Spalten und Measures in Ihrem Modell zu verweisen. 

![YAML-Beispieldatei eines linguistischen Schemas](media/q-and-a-tooling-advanced/power-bi-linguistic-schema.png)

Bevor Sie ein linguistisches Schema bearbeiten können, müssen Sie es in Power BI Desktop öffnen (exportieren). Das Speichern der YAML-Datei am gleichen Speicherort wird als Importieren bezeichnet.  Sie können stattdessen aber auch andere YAML-Dateien importieren.  Angenommen, Sie verfügen über ein ähnliches Dataset und haben bereits viel Arbeit in das Hinzufügen von Wortarten, das Bestimmen von Beziehungen sowie das Erstellen von Ausdrücken und Synonymen investiert. In diesem Fall können Sie die betreffende YAML-Datei in einer anderen Power BI Desktop-Datei verwenden. 

Q&A nutzt all diese Informationen zusammen mit allen Verbesserungen, die Sie vornehmen, um eine bessere Antwort, automatische Vervollständigung und Zusammenfassung der Fragen zu liefern.

## <a name="edit-a-linguistic-schema"></a>Bearbeiten eines linguistischen Schemas
Wenn Sie Ihr linguistisches Schema erstmals aus Power BI Desktop exportieren, werden die meisten oder alle Inhalte der Datei automatisch von der Q&A-Engine generiert. Diese generierten Entitäten, Wörter (Synonyme), Beziehungen und Ausdrücke werden mit dem Tag **State: Generated** gekennzeichnet. Sie sind in der Datei meist zu Informationszwecken enthalten, können aber ein nützlicher Ausgangspunkt für eigene Änderungen sein. 

> [!NOTE]
> Die in diesem Tutorial enthaltene YAML-Beispieldatei enthält keine **State:Generated**- oder **State:Deleted**-Tags, weil sie speziell für dieses Tutorial vorbereitet wurde. Um diese Tags zu sehen, öffnen Sie eine unbearbeitete PBIX-Datei in der Ansicht „Beziehung“ und exportieren das linguistische Schema.

![YAML-Datei mit Anzeige von „State:Generated“](media/q-and-a-tooling-advanced/power-bi-generated-state.png)

Wenn Sie Ihre linguistische Schemadatei wieder in Power BI Desktop importieren, wird alles, was mit **State: Generated** markiert ist, ignoriert und später neu generiert. Wenn Sie also generierte Inhalte ändern möchten, müssen Sie das zugehörige Tag **State: Generated** entfernen. Wenn Sie generierte Inhalte entfernen möchten, müssen Sie das Tag **State: Generated** in **State: Deleted** ändern, damit es nicht neu generiert wird, wenn Sie Ihre linguistische Schemadatei importieren.

### <a name="export-then-import-a-yaml-file"></a>Export und anschließender Import einer YAML-Datei

1. Öffnen Sie das Dataset in der Modellansicht von Power BI Desktop. 
2. Klicken Sie auf der Registerkarte **Modellierung** auf **Linguistisches Schema** > **Linguistisches Schema exportieren**.
3. Speichern Sie das Schema. Die Datei erhält die Erweiterung „.lsdl.yaml“.
4. Öffnen Sie die Datei in Visual Code oder einem anderen Editor.
4. Klicken Sie in der Modellansicht in Power BI Desktop auf der Registerkarte **Modellierung** auf **Linguistisches Schema** > **Linguistisches Schema importieren**. 
6. Navigieren Sie zum Speicherort der bearbeiteten YAML-Datei, und wählen Sie sie aus. Sie werden in einer Erfolgsmeldung darüber benachrichtigt, dass die YAML-Datei des linguistischen Schemas erfolgreich importiert wurde.

    ![Erfolgsmeldung](media/q-and-a-tooling-advanced/power-bi-success.png)

## <a name="phrasings-in-the-linguistic-schema"></a>Hinzufügen von Ausdrücken zum linguistischen Schema
Wie bereits erwähnt, werden mithilfe von Ausdrücken die Beziehungen zwischen Dingen beschrieben. Um beispielsweise die Beziehung zwischen Kunden und Produkten zu beschreiben, könnten Sie sagen: „Kunden kaufen Produkte“.

## <a name="where-do-phrasings-come-from"></a>Woher stammen Ausdrücke?
Power BI fügt dem linguistischen Schema viele einfache Ausdrücke automatisch hinzu. Dies basiert auf der Struktur des Modells und einigen Vermutungen über Spaltennamen. Beispiel:
- Die meisten Spalten werden durch einen einfachen Ausdruck wie „Produkte haben Beschreibungen“ mit der Tabelle in Beziehung gesetzt, in der sie enthalten sind.
- Modellbeziehungen resultieren in Standardausdrücken die für beide Richtungen der Beziehung gelten, z. B. „Bestellungen haben Produkte“ und „Produkte haben Bestellungen“.
- Einige Modellbeziehungen können basierend auf ihren Spaltennamen einen komplexeren Standardausdruck wie „Bestellungen werden an Städte geliefert“ erhalten.

Ihre Benutzer können jedoch Ausdrucksweisen verwenden, die Q&A nicht zuordnen kann. Deshalb können Sie manuell eigene Ausdrücke hinzufügen.

## <a name="why-add-phrasings"></a>Gründe für das Hinzufügen von Ausdrücken
Der erste Grund für das Hinzufügen eines Ausdrucks ist die Definition eines neuen Begriffs. Wenn Sie z.B. „die ältesten Kunden auflisten“ möchten, müssen Sie Q&A zunächst erläutern, was Sie mit „alt“ meinen. Dazu müssen Sie einen Ausdrucks wie „Das Lebensalter gibt an, wie alt die Kunden sind“ hinzufügen.

Der zweite Grund für das Hinzufügen einer Formulierung ist die Beseitigung von Unklarheiten. Mit der einfachen Stichwortsuche kommen Sie nicht weit, wenn Wörter mehr als eine Bedeutung haben. „Flüge nach Chicago“ bedeutet beispielsweise etwas anderes als „Flüge aus Chicago“. Q&A weiß jedoch nicht, was Sie meinen, wenn Sie nicht die Ausdrücke „Flüge gehen von Abflugorten ab“ und „Flüge kommen an Ankunftsorten an“ hinzufügen. Ebenso versteht Q&A den Unterschied zwischen „Autos, die John an Mary verkauft hat“ und „Autos, die John von Mary gekauft hat“ erst, wenn Sie die Ausdrücke „Kunden kaufen Autos von Mitarbeitern“ und „Mitarbeiter verkaufen Kunden Autos“ hinzufügen.

Der letzte Grund für das Hinzufügen eines Ausdrucks ist die Verbesserung von Neuformulierungen. Q&A sollte nicht „Kunden und ihre Produkte anzeigen“ zurückgeben, sondern eine deutlichere Aussage wie „Kunden und die Produkte, die sie gekauft haben, anzeigen“ oder „Kunden und die Produkte, die sie bewertet haben, anzeigen“ – je nachdem, wie Q&A die Frage verstanden hat. Das Hinzufügen benutzerdefinierter Ausdrücke ermöglicht eine deutlichere und eindeutigere Neuformulierung.


## <a name="kinds-of-phrasings"></a>Arten von Ausdrücken
Um die verschiedenen Arten von Ausdrücken zu verstehen, sollten Sie sich zunächst ein paar einfache Grammatikbegriffe ins Gedächtnis rufen:
- Ein *Nomen* ist eine Person, ein Ort oder eine Sache. 
    Beispiele: Auto, Teenager, Marty, Fluxkompensator
- Ein *Verb* ist eine Handlung oder ein Daseinszustand. 
    Beispiele: brüten, zerspringen, verschlingen, herauswerfen
- Ein *Adjektiv* ist ein beschreibendes Wort, das ein Nomen modifiziert. 
    Beispiele: leistungsstark, magisch, golden, gestohlen
- Eine *Präposition* ist ein Wort, das vor einem Nomen verwendet wird, um es mit einem vorangehenden Nomen, Verb oder Adjektiv in Beziehung zu setzen. Beispiele: von, für, aus
-  Ein *Attribut* ist eine Eigenschaft oder ein Merkmal von etwas.
-  Ein *Name* ist ein Wort oder eine Wortgruppe zum Benennen von oder Verweisen auf eine Person, ein Tier, einen Ort oder eine Sache.   


### <a name="attribute-phrasings"></a>Attributausdrücke
Attributausdrücke sind das Hauptarbeitsmittel von Q&A, das verwendet wird, wenn eine Sache als Attribut einer anderen Sache fungiert. Sie sind einfach, unkompliziert und leisten die meiste Arbeit, wenn Sie keinen präziseren, detaillierteren Ausdruck definiert haben. Attributausdrücke werden mit dem Basisverb „haben“ („Produkte haben Kategorien“ und „Gastgeberländer haben Gastgeberstädte“) beschrieben. Sie ermöglichen ebenfalls automatisch, Fragen mit den Präpositionen „von“ und „für“ („Kategorien von Produkten“, „Aufträge für Produkte“) und Fragen zu Besitzverhältnissen („Johns Aufträge“) zu stellen. In Fragen wie diesen werden Attributausdrücke verwendet:

- Welche Kunden haben Aufträge?
- Gastgeberstädte nach Land/Region aufsteigend auflisten
- Aufträge anzeigen, die Chai enthalten
- Kunden mit Aufträgen auflisten
- Was ist die Kategorie jedes Produkts?
- Aufträge von Robert König zählen    

Power BI generiert die Mehrheit der Attributausdrücke, die in Ihrem Modell benötigt werden, auf der Eigenständigkeit von Tabellen/Spalten und auf Modellbeziehungen basierend. In der Regel müssen Sie diese nicht selbst erstellen.
Hier sehen Sie ein Beispiel eines Attributausdrucks im linguistischen Schema:

```json
product_has_category:
  Binding: {Table: Products}
  Phrasings:
  - Attribute: {Subject: product, Object: product.category}
```
 
### <a name="name-phrasings"></a>Namensausdrücke
Namensausdrücke sind hilfreich, wenn Ihr Datenmodell eine Tabelle enthält, die benannte Objekte wie etwa Sportler- und Kundennamen enthält. Beispielsweise ist der Ausdruck „Produktnamen sind Namen von Produkten“ unerlässlich, um Produktnamen in Fragen verwenden zu können. Durch Namensausdrücke wird die Verwendung von „namens“ als Verb (z.B. „Kunden namens John Smith auflisten“) ermöglicht. Es ist jedoch besonders wichtig, dass in Kombination mit anderen Ausdrücken ein Namenswert verwendet werden kann, um auf eine bestimmte Tabellenzeile zu verweisen. Bei „Kunden, die Chai gekauft haben“ kann Q&A beispielsweise erkennen, dass sich der Wert „Chai“ auf die gesamte Zeile der Produkttabelle bezieht und nicht nur auf einen Wert in der Spalte mit dem Produktnamen. In Fragen wie diesen werden Namensausdrücke verwendet:    
- Welche Mitarbeiter heißen Robert König
- Wer heißt Ernst Handel
- Sportarten von Fernand De Montigny
- Anzahl der Sportler namens Marie
- Was hat Robert König gekauft?

Wenn Sie eine sinnvolle Namenskonvention für die Namensspalten im Modell gewählt haben (z.B. „Name“ oder „ProductName“ statt „PrdNm“), generiert Power BI die meisten Namensausdrücke, die für Ihr Modell benötigt werden, automatisch, sodass Sie diese in der Regel nicht selbst erstellen müssen.

Hier finden Sie ein Beispiel eines Namensausdrucks im linguistischen Schema:

```json
employee_has_name:
  Binding: {Table: Employees}
  Phrasings:
  - Name:
      Subject: employee
      Name: employee.name
```

 
### <a name="adjective-phrasings"></a>Adjektivausdrücke
Adjektivausdrücke definieren neue Adjektive, die Objekte in Ihrem Modell beschreiben. Beispiel: Der Ausdruck „Zufriedene Kunden sind Kunden mit einer Bewertung > 6“ ist nötig, um Fragen wie „Zufriedene Kunden in Düsseldorf auflisten“ zu stellen. Es gibt mehrere Typen von Adjektivausdrücken zur Verwendung in der jeweiligen Situation.

*Einfache Adjektivausdrücke* definieren ein neues Adjektiv auf Grundlage einer Bedingung, beispielsweise „Eingestellte Produkte sind Produkte mit dem Status = D“. In Fragen wie diesen werden einfache Adjektivausdrücke verwendet:
- Welche Produkte wurden eingestellt?
- Eingestellte Produkte auflisten
- Goldmedaillengewinner auflisten
- Produkte mit Lieferrückstand

Hier sehen Sie ein Beispiel eines einfachen Adjektivausdrucks im linguistischen Schema:

product_is_discontinued:

```json
Binding: {Table: Products}
  Conditions:
  - Target: product.discontinued
    Operator: Equals
    Value: true
  Phrasings:
  - Adjective:
      Subject: product
      Adjectives: [discontinued]
```

*Maßadjektivausdrücke* definieren ein neues Adjektiv basierend auf einem numerischen Wert, der eine Größe oder Ausdehnung angibt, für die das Adjektiv gilt, z. B. „Längen geben an, wie lang Flüsse sind“ und „Kleine Länder haben kleine Landflächen“. In Fragen wie diesen werden Maß-Adjektivausdrücke verwendet:
- Lange Flüsse auflisten
- Welche Flüsse sind am längsten?
- Die kleinsten Länder auflisten, die Gold im Handball gewonnen haben
- Wie lang ist der Rhein?

Hier sehen Sie ein Beispiel eines Maßadjektivausdrucks im linguistischen Schema:

river_has_length:

 ```json
Binding: {Table: Rivers}
  Phrasings:
  - Adjective:
      Subject: river
      Adjectives: [long]
      Antonyms: [short]
      Measurement: river.length
```

*Dynamische Adjektivausdrücke* definieren einen Satz neuer Adjektive basierend auf Werten in einer Spalte im Modell, beispielsweise „Farben beschreiben Produkte“ und „Wettkämpfe haben Wettkampfsgeschlechter“. In Fragen wie diesen werden dynamische Adjektivausdrücke verwendet:
- Rote Produkte auflisten
- Welche Produkte sind grün?
- Eislaufwettbewerbe für Frauen anzeigen
- Aktive Probleme zählen

Hier sehen Sie ein Beispiel eines dynamischen Adjektivausdrucks im linguistischen Schema:

product_has_color:
```json
Binding: {Table: Products}
  Phrasings:
  - DynamicAdjective:
      Subject: product
      Adjective: product.color
```

 
### <a name="noun-phrasings"></a>Nomenausdrücke
Nomenausdrücke definieren neue Nomen, die Teilmengen von Objekten in Ihrem Modell beschreiben. Sie enthalten oft eine Art modellspezifischer Messgröße oder Bedingung. Zum Beispiel können wir für das Olympia-Modell Ausdrücke hinzufügen, um Champions von Medaillengewinnern, Ballsportarten von Wassersportarten, Mannschaften von Einzelsportlern, Alterskategorien von Athleten (Jugendliche, Erwachsene, Senioren) usw. zu unterscheiden. Für unsere Filmdatenbank können wir Nomenausdrücke für „Flops sind Filme mit einem Nettogewinn < 0“ hinzufügen, damit wir Fragen wie „Flops nach Jahr zählen“ stellen können. Es gibt zwei Formen von Nomenausdrücken zur Verwendung in der jeweiligen Situation.

*Einfache Nomenausdrücke* definieren ein neues Nomen basierend auf einer Bedingung, wie z.B. „Auftragnehmer sind Mitarbeiter, bei denen Vollzeit = falsch" und „Champion ist Sportler mit einer Anzahl von Medaillen > 5“. In Fragen wie diesen werden einfache Nomenausdrücke verwendet:

- Welche Mitarbeiter sind Auftragnehmer?
- Auftragnehmer in Berlin zählen
- Wie viele Champions 2016

Hier sehen Sie ein Beispiel eines einfachen Nomenausdrucks im linguistischen Schema:

employee_is_contractor:

```json
Binding: {Table: Employees}
  Conditions:
  - Target: employee.full_time
    Operator: Equals
    Value: false
  Phrasings:
  - Noun:
      Subject: employee
      Nouns: [contractor]
```

*Dynamische Nomenausdrücke* definieren einen Satz neuer Nomen basierend auf Werten in einer Spalte im Modell, beispielsweise „Berufe definieren Teilmengen von Mitarbeitern“. In Fragen wie diesen werden dynamische Nomenausdrücke verwendet:

- Kassierer in Köln auflisten
- Welche Mitarbeiter sind Baristas?
- Schiedsrichter 1992 auflisten

Hier finden Sie ein Beispiel eines dynamischen Nomenausdrucks im linguistischen Schema „employee_has_job“:

 ```json
Binding: {Table: Employees}
  Phrasings:
  - DynamicNoun:
      Subject: employee
      Noun: employee.job
```

### <a name="preposition-phrasings"></a>Präpositionsausdrücke
Präpositionsausdrücke dienen zum Beschreiben, wie Objekte in Ihrem Modell über Präpositionen zusammenhängen. Beispielsweise verbessert der Ausdruck „Städte sind in Ländern“ das Verständnis für Fragen wie „Städte in NRW zählen“. Einige Präpositionsausdrücke werden automatisch erstellt, wenn eine Spalte als geografische Entität erkannt wird. In Fragen wie diesen werden Präpositionsausdrücke verwendet:

- Kunden in New York zählen
- Bücher über Linguistik auflisten
- In welcher Stadt befindet sich Robert King?
- Wie viele Bücher sind von Stephen Queen?
 
Hier finden Sie ein Beispiel eines Präpositionsausdrucks im linguistischen Schema „customers_are_in_cities“:

 ```json
Binding: {Table: Customers}
  Phrasings:
  - Preposition:
      Subject: customer
      Prepositions: [in]
      Object: customer.city
```

 
### <a name="verb-phrasings"></a>Verbausdrücke
Verbausdrücke dienen zum Beschreiben, wie Objekte in Ihrem Modell über Verben zusammenhängen. Zum Beispiel verbessert der Ausdruck „Kunden kaufen Produkte“ das Verständnis für Fragen wie „Wer hat Käse gekauft?“ und „Was hat Johann gekauft?“. Verbausdrücke sind die flexibelsten aller Arten von Ausdrücken, die oft mehr als zwei Dinge miteinander in Beziehung setzen, wie z.B. in „Mitarbeiter verkaufen Kunden Produkte“. In Fragen wie diesen werden Verbausdrücke verwendet:

- Wer hat was wem verkauft?
- Welcher Mitarbeiter hat Johann Chai verkauft?
- Wie viele Kunden haben Chai von Marie gekauft?
- Produkte auflisten, die Marie Johann verkauft hat
- Welche eingestellten Produkte wurden Kunden aus Köln von Mitarbeitern in Berlin verkauft?

Verbausdrücke können auch Präpositionsausdrücke enthalten und damit ihre Flexibilität erhöhen, z.B. bei „Sportler gewinnen Medaillen bei Wettkämpfen“ oder „Kunden erhalten Rückerstattungen für Produkte“. In Fragen wie diesen werden Verbausdrücke mit Präpositionsausdrücken verwendet:

- Wie viele Sportler haben eine Goldmedaille beim Alpencup gewonnen?
- Welche Kunden haben eine Rückerstattung für Käse erhalten?
- Bei welchem Wettkampf hat Daniel Ley eine Bronzemedaille gewonnen?

Einige Verbausdrücke werden automatisch erstellt, wenn erkannt wird, dass eine Spalte sowohl ein Verb als auch eine Präposition enthält.

Hier finden Sie ein Beispiel eines Verbausdrucks im linguistischen Schema „customers_buy_products_from_salespeople“:

```json
Binding: {Table: Orders}
  Phrasings:
  - Verb:
      Subject: customer
      Verbs: [buy, purchase]
      Object: product
      PrepositionalPhrases:
      - Prepositions: [from]
        Object: salesperson
```

### <a name="relationships-with-multiple-phrasings"></a>Beziehungen mit mehreren Ausdrücken
Häufig kann eine einzelne Beziehung auf mehrere Arten beschrieben werden. In diesem Fall kann eine einzelne Beziehung mehr als einen Ausdruck aufweisen. Es ist üblich, dass die Beziehung zwischen einer Tabellen- und einer Spaltenentität sowohl einen Attributausdruck als auch einen anderen Ausdruck besitzt. In der Beziehung zwischen Kunde und Kundenname soll beispielsweise sowohl ein Attributausdruck (z.B. „Kunden haben Namen“) als auch ein Namensausdruck (z.B. „Kundennamen sind die Namen von Kunden“) enthalten sein, damit Sie beide Arten von Fragen stellen können.

Hier finden Sie ein Beispiel einer Beziehung mit zwei Ausdrücken im linguistischen Schema „customer_has_name“:

  ```json
Binding: {Table: Customers}
  Phrasings:
    - Attribute: {Subject: customer, Object: customer.name}
    - Name:
        Subject: customer
        Object: customer.name
```

Ein weiteres Beispiel ist das Hinzufügen des alternativen Ausdrucks „Mitarbeiter verkaufen Kunden Produkte“ zur Beziehung „Kunden kaufen Produkte von Mitarbeitern“. Beachten Sie, dass Sie keine Varianten wie „Mitarbeiter verkaufen Produkte *an Kunden*“ oder „Produkte werden an Kunden *von Mitarbeitern* verkauft“ hinzufügen müssen, weil die Varianten „an“ und „von“ des Subjekts und des indirekten Objekts automatisch von Q&A hergeleitet werden.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
Wenn Sie eine Änderung an einer Datei vom Typ „.lsdl.yaml“ vornehmen, die nicht dem Format des linguistischen Schemas entspricht, werden nun Validierungssymbole angezeigt, die auf Probleme hinweisen: 

![YAML-Datei, die Fehler enthält](media/q-and-a-tooling-advanced/power-bi-yaml-errors.png)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)