---
title: Tabellen, Matrizen und Listen im Power BI-Berichts-Generator
description: Im Power BI Report Builder sind Tabellen, Matrizen und Listen Datenbereiche, die die Daten aus paginierten Berichten in Zellen darstellen, die wiederum in Zeilen und Spalten organisiert sind.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 02ac131325dab59590cb88c524ace68a1226fc69
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921491"
---
# <a name="tables-matrixes-and-lists-in-power-bi-report-builder"></a>Tabellen, Matrizen und Listen im Power BI-Berichts-Generator
 Im Berichts-Generator sind Tabellen, Matrizen und Listen *Datenbereiche*, die die Daten aus paginierten Berichten in Zellen darstellen, die wiederum in Zeilen und Spalten organisiert sind. Die Zellen enthalten in der Regel Textdaten wie Text, Datumsangaben und Zahlen. Sie können jedoch auch Messgeräte, Diagramme oder Berichtselemente wie Bilder enthalten. Tabellen, Matrizen und Listen werden häufig unter dem Begriff *Tablix-Datenbereiche* zusammengefasst.  
  
 Die Vorlagen für Tabellen, Matrizen und Listen basieren auf dem Tablix-Datenbereich. Dabei handelt es sich um ein flexibles Raster, das Daten in Zellen darstellen kann. In den Vorlagen für Tabellen und Matrizen sind Zellen in Zeilen und Spalten organisiert. Da es sich bei Vorlagen um Variationen des zugrunde liegenden generischen Tablix-Datenbereichs handelt, können Sie zur Darstellung von Daten eine Kombination der Vorlagenformate verwenden und eine Tabelle, Matrix oder Liste ändern, um die Features anderer Datenbereiche einzufügen, während Sie Ihren Bericht erstellen. Wenn Sie beispielsweise eine Tabelle hinzufügen und dann feststellen, dass diese Ihre Anforderungen nicht erfüllt, können Sie Spaltengruppen hinzufügen, um die Tabelle in eine Matrix umzuwandeln.  
  
 Die Datenbereiche für Tabellen und Matrizen können komplexe Datenbeziehungen darstellen, indem geschachtelte Tabellen, Matrizen, Listen, Diagramme und Messgeräte hinzugefügt werden. Tabellen und Matrizen haben ein Tabellenlayout, und die Daten stammen aus einem einzelnen Dataset, das auf einer einzelnen Datenquelle basiert. Der Hauptunterschied zwischen Tabellen und Matrizen besteht darin, dass Tabellen nur Zeilengruppen enthalten können, während Matrizen Zeilengruppen und Spaltengruppen enthalten können.  
  
 Listen unterscheiden sich hiervon. Sie unterstützen Freiformlayouts und können mehrere Peertabellen oder Matrizen enthalten, die jeweils Daten aus einem anderen Dataset verwenden. Listen können auch für Formulare wie Rechnungen verwendet werden.  
  
 Auf der folgenden Abbildung sehen Sie einfache Berichte mit einer Tabelle, Matrix oder Liste.  

![Tabelle, Matrix und Liste im Berichts-Generator](media/report-builder-tables-matrices-lists/report-builder-table-matrix-list.png)
  
##  <a name="tables"></a><a name="Table"></a> Tabellen  
 Verwenden Sie eine Tabelle, um Detaildaten darzustellen und/oder Daten in Zeilengruppen zu organisieren. Die Tabellenvorlage enthält drei Spalten mit einer Tabellenkopfzeile und einer Detailzeile für Daten. Die folgende Abbildung zeigt die ursprüngliche Tabellenvorlage für die Auswahl auf der Entwurfsoberfläche:  

![Berichts-Generator: Tabellenvorlage auf der Entwurfsoberfläche (ausgewählt)](media/report-builder-tables-matrices-lists/report-builder-new-table.png)
  
 Sie können Daten nach einzelnen Feldern, mehreren Feldern oder unter Verwendung eigener Ausdrücke gruppieren. Sie können geschachtelte Gruppen oder unabhängige, angrenzende Gruppen erstellen und aggregierte Werte für gruppierte Daten anzeigen oder Gesamtergebnisse zu Gruppen hinzufügen. Wenn in Ihrer Tabelle beispielsweise eine Zeilengruppe namens **Category** (Kategorie) vorhanden ist, können Sie eine Zwischensumme für jede Gruppe und ein Gesamtergebnis für den Bericht hinzufügen. Sie können Zellen zusammenführen und Daten und Tabellenkopfzeilen formatieren, um die Darstellung der Tabelle zu verbessern und die relevanten Daten hervorzuheben.  
  
 Sie können nun Details oder gruppierte Daten ausblenden und Drilldownschaltflächen hinzufügen, mit denen die Benutzer entscheiden können, welche Daten angezeigt werden sollen.  
  
##  <a name="matrixes"></a><a name="Matrix"></a> Matrizen  
 Verwenden Sie eine Matrix, um aggregierte Datenzusammenfassungen anzuzeigen, die ähnlich wie bei Pivottabellen oder Kreuztabellen in Zeilen und Spalten gruppiert sind. Die Anzahl der Zeilen und Spalten für Gruppen wird von der Anzahl der eindeutigen Werte für die einzelnen Zeilen- und Spaltengruppen bestimmt. Im Folgenden sehen Sie die leere Matrixvorlage, die auf der Entwurfsoberfläche ausgewählt wurde:  

![Berichts-Generator: neue über Toolbox hinzugefügte Matrix (ausgewählt)](media/report-builder-tables-matrices-lists/report-builder-new-matrix.png)
 
 Sie können Daten nach mehreren Feldern oder Ausdrücken in Zeilen- und Spaltengruppen gruppieren. Wenn die Berichtsdaten und die Datenbereiche zur Laufzeit kombiniert werden, wächst eine Matrix horizontal und vertikal in dem Maß, in dem auf der Seite Spalten für Spaltengruppen und Zeilen für Zeilengruppen hinzugefügt werden. Die Matrixzellen zeigen aggregierte Werte an, die auf die Schnittmenge der Zeilen- und Spaltengruppen beschränkt sind, zu denen die Zelle gehört. Wenn Ihre Matrix beispielsweise eine Zeilengruppe (Category) und zwei Spaltengruppen (Territory und Year) enthält, die die Summe der Verkäufe enthalten, zeigt der Bericht zwei Zellen mit den Summen der Verkäufe für jeden Wert in der Category-Gruppe an. Der Bereich der Zellen der zwei Schnittmengen sind: Kategorie und Gebiet sowie Kategorie und Jahr. Die Matrix kann geschachtelte und angrenzende Gruppen enthalten. Geschachtelte Gruppen haben eine Über-/Unterordnungsbeziehung, angrenzende Gruppen eine Peerbeziehung. Sie können Teilergebnisse für einzelne und alle Ebenen von geschachtelten Zeilen- und Spaltengruppen innerhalb der Matrix hinzufügen.  
  
 Sie können Zellen zusammenführen oder horizontal und vertikal teilen oder Daten und Gruppenüberschriften formatieren, um die Matrix besser lesbar zu gestalten und die relevanten Daten hervorzuheben.  
  
 Sie können auch Drilldownschaltflächen einfügen, die Detaildaten verbergen. Der Benutzer kann dann auf diese Schaltflächen klicken, um nach Bedarf mehr oder weniger Details anzuzeigen.  
  
##  <a name="lists"></a><a name="List"></a> Listen  
 Verwenden Sie eine Liste, um ein Freiformlayout zu erstellen. Sie können in einem solchen Layout Felder flexibel in der Liste platzieren, da es kein Raster gibt. Sie können eine Liste verwenden, um ein Formular zu erstellen, das für die Darstellung vieler Datasetfelder oder als Container für die gleichzeitige Darstellung mehrerer Datenbereiche für gruppierte Daten verwendet wird. Sie können beispielsweise eine Gruppe für eine Liste definieren, eine Tabelle, ein Diagramm und ein Bild hinzufügen und Werte in Tabellen- und Diagrammform für jeden Gruppenwert darstellen. Ein Anwendungsbeispiel hierfür sind Mitarbeiter- oder Patientenakten.  

![Berichts-Generator: neue über Toolbox hinzugefügte Liste (ausgewählt)](media/report-builder-tables-matrices-lists/report-builder-new-list.png)
  
##  <a name="preparing-data"></a><a name="PreparingData"></a> Datenvorbereitung  
 In einem Tabellen-, Matrix- und Listendatenbereich werden Daten aus einem Dataset angezeigt. Sie können die Daten in der Abfrage vorbereiten, die die Daten für das Dataset abruft oder die entsprechenden Eigenschaften in der Tabelle, Matrix oder Liste konfigurieren.  
  
 Abfragesprachen wie Transact-SQL, die für das Abrufen der Daten für die Berichtsdatasets verwendet werden, können die Daten vorbereiten, indem Filter angewendet werden, damit nur eine Teilmenge der Daten verwendet wird. Hierfür werden NULL-Werte oder Leerzeichen durch Konstanten ersetzt, die den Bericht lesbarer gestalten und Daten sortieren und gruppieren.  
  
 Wenn Sie die Daten im Datenbereich einer Tabelle, Matrix oder Liste eines Berichts vorbereiten, legen Sie die Eigenschaften für den Datenbereich oder die Zellen des Datenbereichs fest. Wenn Sie die Daten filtern oder sortieren möchten, legen Sie die Eigenschaften für den Datenbereich fest. Das gilt beispielsweise, wenn Sie die Daten sortieren möchten, die Spalten festlegen möchten, nach denen sortiert werden soll, oder die Sortierrichtung festlegen möchten. Wenn Sie einen Alternativwert für ein Feld angeben möchten, bearbeiten Sie die Werte des Zellentexts, der das Feld darstellt. Wenn Sie beispielsweise „Blank“ anzeigen möchten, wenn ein Feld leer ist oder den Wert NULL aufweist, können Sie einen Ausdruck verwenden, um den Wert festzulegen.  
  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a> Erstellen und Konfigurieren von Tabellen, Matrizen und Listen  
 Wenn Sie Tabellen oder Matrizen zu Ihrem Bericht hinzufügen, können Sie den Assistenten für Tabellen und Matrizen verwenden oder diese manuell aus den Vorlagen des Berichts-Generators erstellen. Listen können nur manuell über Listenvorlagen erstellt werden.  
  
 Der Assistent führt Sie durch die Schritte zum Erstellen und Konfigurieren einer Tabelle oder Matrix. Sie können die Tablix-Datenbereiche nach Abschluss des Assistenten oder während Sie diese neu erstellen konfigurieren und optimieren. Die Dialogfelder, die über die Kontextmenüs der Datenbereiche verfügbar sind, erleichtern die Konfiguration der am häufigsten verwendeten Eigenschaften für Seitenumbrüche, der Wiederholbarkeit und Sichtbarkeit von Kopf- und Fußzeilen sowie der Anzeigeoptionen, Filter und Sortierung. Der Tablix-Datenbereich bietet jedoch viele zusätzliche Eigenschaften, die Sie nur über den Bereich „Eigenschaften“ des Berichts-Generators konfigurieren können. Wenn Sie beispielsweise möchten, dass eine Meldung angezeigt wird, wenn das Dataset für eine Tabelle, Matrix oder Liste leer ist, müssen Sie den Meldungstext in der Tablix-Eigenschaft „NoRowsMessage“ im Bereich „Eigenschaften“ eingeben.  
  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a> Wechsel zwischen Tablix-Vorlagen  
 Sie müssen nicht ausschließlich die Tablix-Vorlage verwenden, die Sie zuerst auswählen. Es kann beispielsweise vorkommen, dass Sie das Tablix-Design ändern möchten, während Sie Gruppen, Gesamtergebnisse und Bezeichnungen hinzufügen. Nehmen Sie an, dass Sie mit einer Tabelle beginnen und dann die Detailzeile löschen und Spaltengruppen hinzufügen.  
  
 Sie können weiterhin Ihre Tabelle, Matrix oder Liste erweitern, indem Sie Tablix-Features hinzufügen. Zu Tablix-Features zählt beispielsweise die Anzeige von Detaildaten oder das Aggregieren von gruppierten Daten in Zeilen und Spalten. Sie können geschachtelte Gruppen, unabhängige angrenzende Gruppen oder rekursive Gruppen erstellen. Sie können gruppierte Daten filtern und sortieren und Gruppen kombinieren, indem Sie mehrere Gruppenausdrücke zu einer Gruppendefinition hinzufügen.  
  
 Zudem können Sie Gesamtsummen für eine Gruppe oder den Datenbereich hinzufügen. Sie können Zeilen oder Spalten ausblenden, damit der Bericht übersichtlicher wird, und es dem Benutzer ermöglichen, Daten anzuzeigen oder auszublenden (z. B. in einem Drilldownbericht). 

## <a name="next-steps"></a>Weitere Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
