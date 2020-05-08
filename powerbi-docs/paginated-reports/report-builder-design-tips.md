---
title: Berichtsentwurfstipps im Power BI-Berichts-Generator
description: Nutzen Sie die folgenden Tipps, die Sie beim Entwerfen von paginierten Berichten in Power BI Report Builder unterstützen.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 13b9e37d4a64493dfdcac02d9df86a1e19a1c24b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921169"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Berichtsentwurfstipps im Power BI-Berichts-Generator
  Nutzen Sie die folgenden Tipps, die Sie beim Entwerfen von paginierten Berichten in Power BI Report Builder unterstützen.  
  
   
  
##  <a name="designing-reports"></a><a name="DesigningReports"></a> Entwerfen von Berichten  
  
-   Ein sorgfältig entworfener Bericht vermittelt Informationen, die zu Aktionen führen. Identifizieren Sie die Fragen, deren Beantwortung der Bericht unterstützt. Berücksichtigen Sie diese Fragen beim Entwurf des Berichts.  
  
-   Um effektive Datenvisualisierungen zu entwerfen, überlegen Sie, wie Informationen angezeigt werden können, die für den Benutzer des Berichts leicht verständlich sind. Wählen Sie einen Datenbereich aus, der sich gut für die Daten eignet, die Sie visualisieren möchten. Ein Diagramm vermittelt zusammenfassende und aggregierte Informationen z.B. besser als eine Tabelle, die viele Seiten mit detaillierten Informationen umfasst. Sie können Daten aus einem Dataset in einem beliebigen Datenbereich visuell darstellen, einschließlich Diagrammen, Karten, Indikatoren, Sparklines, Datenbalken und Tabellendaten in verschiedenen Rasterlayouts auf Grundlage einer Tablix. 
  
-   Wenn Sie planen, den Bericht in einem bestimmten Exportformat zu übermitteln, testen Sie rechtzeitig das Exportformat im Entwurf. Die Unterstützung von Funktionen variiert abhängig vom Renderer, den Sie auswählen.  
  
-   Wenn Sie komplexe Layouts erstellen, können Sie das Layout in Phasen entwerfen. Sie können Rechtecke als Container verwenden, um Berichtselemente zu organisieren. Sie können Datenbereiche direkt auf der Entwurfsoberfläche erstellen, um den Arbeitsbereich zu maximieren, und dann jeweils beim Abschließen in den Rechteckcontainer ziehen. Wenn Sie Rechtecke als Container verwenden, können Sie den gesamten Inhalt in einem Schritt positionieren. Mit Rechtecken können Sie auch mühelos steuern, wie Berichtselemente auf den einzelnen Seiten gerendert werden.  
  
-   Um einen Bericht übersichtlicher zu gestalten, können Sie auch die bedingte Sichtbarkeit bestimmter Berichtselemente verwenden, sodass der Benutzer die Elemente wahlweise anzeigen kann. Sie können die Sichtbarkeit auf Grundlage eines Parameters oder einer Textfeldumschaltfläche festlegen. Sie können bedingt ausgeblendete Textfelder hinzufügen, um Zwischenausdrucksergebnisse anzuzeigen. Wenn ein Bericht unerwartete Daten anzeigt, können Sie diese Zwischenergebnisse zum Debuggen von Ausdrücken anzeigen.  
  
-   Wenn Sie mit geschachtelten Elementen in Tablixzellen oder Rechtecken arbeiten, können Sie verschiedene Hintergrundfarben für den Container und die darin enthaltenen Elemente festlegen. Standardmäßig ist die Farbe des Hintergrunds **Keine Farbe**. Elemente mit einer bestimmten Hintergrundfarbe scheinen durch Elemente, für die **Keine Farbe** als Hintergrundfarbe festgelegt ist. Mit diesem Verfahren können Sie das richtige Element auswählen, um Anzeigeeigenschaften festzulegen, z.B. die Rahmensichtbarkeit bei Tablixzellen.  
  
 Weitere Informationen zu Aspekten, die Sie beim Entwerfen des Berichts berücksichtigen müssen, finden Sie unter [Planen eines Berichts im Power BI-Berichts-Generator](report-builder-planning-report.md).  
  
##  <a name="naming-conventions-for-reports-data-sources-and-datasets"></a><a name="NamingConventions"></a> Benennungskonventionen für Berichte, Datenquellen und Datasets  
  
-   Verwenden Sie Benennungskonventionen für Datenquellen und Datasets, die die Quelle der Daten dokumentieren.  
  
    1.  **Datenquellen.** Wenn Sie aus Sicherheitsgründen keinen tatsächlichen Server oder keine tatsächliche Datenbank verwenden möchten, verwenden Sie einen Alias, der dem Benutzer die Quelle der Daten angibt.  
  
    2.  **Datasets.** Verwenden Sie einen Namen, der die Datenquelle angibt, auf dem es basiert.  
  
##  <a name="working-with-data"></a><a name="Data"></a> Arbeiten mit Daten  
  
-   Rufen Sie im ersten Schritt alle Daten ab, mit denen Sie arbeiten möchten, damit sie im Bereich „Berichtsdaten“ angezeigt werden. Wenn Sie die Fragen verfeinern, die der Bericht beantworten soll, überlegen Sie, wie Sie die Daten in den Berichtsdatasets auf das Nötigste beschränken.  
  
-   Schließen Sie im Allgemeinen nur die Daten ein, die in einem Bericht angezeigt werden. Verwenden Sie Abfragevariablen in den Datasetabfragen, damit der Benutzer auswählen kann, welche Daten im Bericht angezeigt werden. Wenn Sie freigegebene Datasets erstellen, stellen Sie Filter auf Grundlage von Berichtsparametern bereit, um die gleiche Funktionalität bereitzustellen.  
  
-   Wenn Sie ein erfahrener Abfragenschreiber sind, sollten Sie für Zwischendatenmengen Daten im Bericht gruppieren und nicht in der Abfrage. Wenn Sie die ganze Gruppierung in der Abfrage durchführen, ist der Bericht eher eine Darstellung des Abfrageresultsets. Um andererseits aggregierte Werte für große Mengen von Daten in einem Diagramm oder einer Matrix anzuzeigen, müssen keine Detaildaten einbezogen werden.  
  
-   Je nach Ihren Anforderungen können Sie Namen und Speicherorte von Berichtsdatenquellen, Datasetabfrage-Befehlstext und Parameterwerte im Bericht anzeigen. Die erste Frage vieler neuer Benutzer ist, woher die Daten stammen. Um den Bericht übersichtlicher zu gestalten, können Sie Textfelder mit dieser Art von Informationen bedingt ausblenden und Benutzern die Wahl überlassen, sie anzuzeigen. Versuchen Sie, diese Informationen auf der letzten Seite des Berichts hinzuzufügen. Legen Sie die Textfeldsichtbarkeit auf Grundlage eines Parameters fest, den der Benutzer ändern kann.  
  
##  <a name="interacting-with-the-report-design-surface"></a><a name="DesignSurface"></a> Interaktion mit der Berichtsentwurfsoberfläche  
 Die Berichtsentwurfsoberfläche ist keine WYSIWYG-Oberfläche. Wenn Sie Berichtselemente auf der Entwurfsoberfläche platzieren, beeinflusst ihre relative Position die Art, in der die Elemente auf der gerenderten Berichtsseite angezeigt werden. Leerzeichen werden beibehalten.  
  
-   Verwenden Sie Ausrichtungslinien und Layoutschaltflächen, um Elemente auf der Berichtsentwurfsoberfläche auszurichten und anzuordnen. Beispielsweise können Sie die oberen Bereiche oder die Ränder ausgewählter Elemente ausrichten, ein Element an die Größe eines anderen Elements angleichen oder den Abstand zwischen Elementen anpassen.  
  
-   Passen Sie mit Pfeiltasten die Position und Größe ausgewählter Elemente auf der Entwurfsoberfläche an. Die folgenden Tastenkombinationen sind z.B. sehr nützlich:  
  
    -   **Pfeiltasten** Verschieben des ausgewählten Berichtselements.  
  
    -   **STRG+Pfeiltasten** Bewegen des ausgewählten Berichtselements.  
  
    -   **STRG+UMSCHALT+Pfeiltasten** Herauf- oder Herabsetzen der Größe des ausgewählten Berichtselements.  
  
-   Um einem Rechteck ein Element hinzuzufügen, verwenden Sie die linke obere Spitze der Maus, um auf die ursprüngliche Position des Elements im Rechteckcontainer zu zeigen. Verwenden Sie Tastenkombinationen, um ausgewählte Objekte zu positionieren. Das Rechteck wird automatisch erweitert, damit es der Größe der enthaltenen Elemente entspricht.  
  
-   Um mehrere Elemente einer Tablixzelle hinzuzufügen, fügen Sie zuerst ein Rechteck und dann die Elemente hinzu.  
  
     Standardmäßig enthält jede Tablixzelle ein Textfeld. Wenn Sie ein Rechteck einer Zelle hinzufügen, ersetzt das Rechteck das Textfeld. Platzieren Sie beispielsweise geschachtelte Indikatoren in einem Rechteck in einer Tablixzelle, um zu steuern, wie die Größe eines Diagramms oder Indikators erweitert wird, wenn Sie die Höhe der Zeile ändern, in der sich die Zelle befindet.  
  
-   Verwenden Sie das **Zoom** -Steuerelement, um die Sicht der Entwurfsoberfläche anzupassen. Sie können mit der ganzen Seite oder kleineren Abschnitten der Seite arbeiten.  
  
-   Wenn Sie Felder aus dem Bereich „Berichtsdaten“ in den Bereich „Gruppierung“ ziehen, vermeiden Sie es, das Feld über andere Berichtselemente auf der Entwurfsoberfläche zu ziehen, da dabei die anderen Objekte ausgewählt werden und die Auswahl des Tablixdatenbereichs aufgehoben wird. Ziehen Sie das Feld im Bereich „Berichtsdaten“ herunter und dann über den Bereich „Gruppierung“.  
  
###  <a name="selecting-items"></a><a name="Selecting"></a> Auswählen von Elementen  
 Um das gewünschte Objekt auf der Berichtsentwurfsoberfläche auszuwählen, verwenden Sie die ESC-Taste, das Rechtsklick-Kontextmenü, den Bereich Eigenschaften, den Gruppierungsbereich.  
  
-   -   Drücken Sie die ESC-Taste, um den Stapel von Berichtselementen durchzugehen, die den gleichen Platz auf der Entwurfsoberfläche einnehmen.  
  
    -   Versuchen Sie bei einigen Berichtselementen, das Rechtsklick-Kontextmenü zur Auswahl des gewünschten Berichtselements oder Teils des Berichtselements zu verwenden.  
  
    -   Die Eigenschaften für die aktuelle Auswahl werden im Eigenschaftenbereich angezeigt.  
  
    -   Um mit Zeilengruppen und Spaltengruppen in einem Tablixdatenbereich zu arbeiten, wählen Sie die Gruppe im Bereich „Gruppierung“ aus.  

  
##  <a name="working-with-specific-types-of-report-items"></a><a name="ReportItems"></a> Arbeiten mit bestimmten Typen von Berichtselementen  
  
###  <a name="working-with-parameters"></a><a name="Parameters"></a> Arbeiten mit Parametern  
  
-   Der primäre Zweck von Berichtsparametern ist das Filtern von Daten, sodass nur abgerufen wird, was für den Bericht benötigt wird.  
  
-   Finden Sie für Berichtsparameter ein Gleichgewicht zwischen den Aspekten, Interaktivität zu ermöglichen und Benutzern dabei zu helfen, die gewünschten Ergebnisse zu erhalten. Beispielsweise können Sie bei allgemein beliebten Werten Standardwerte für einen Parameter festlegen.  
  
###  <a name="working-with-text"></a><a name="Text"></a> Arbeiten mit Text  
  
-   Wenn Sie mehrere Zeilen in ein Textfeld einfügen, wird der Text als zusammenhängender Text hinzugefügt. Jeder zusammenhängende Text kann nur als Einheit formatiert werden. Um jede Zeile unabhängig zu formatieren, fügen Sie nach Bedarf durch Drücken der EINGABETASTE eine neue Zeile in den zusammenhängenden Text ein. Sie können dann Formatierung und Formate auf jede unabhängige Textzeile im Textfeld anwenden.  
  
-   Sie können Formateigenschaften und Aktionen für ein Textfeld oder einen Platzhaltertext im Textfeld festlegen. Wenn nur eine Textzeile vorhanden ist, ist es effizienter, Eigenschaften für das Textfeld statt für den Text festzulegen.  
  
###  <a name="working-with-expressions"></a><a name="Expressions"></a> Arbeiten mit Ausdrücken  
  
-   Informieren Sie sich über einfache und komplexe Ausdrücke. Sie können ein einfaches Ausdrucksformat direkt in Textfelder, Eigenschaften im Bereich „Eigenschaften“ oder an Positionen in Dialogfeldern, die einen Ausdruck akzeptieren, eingeben.
  
-   Wenn Sie einen Ausdruck erstellen, erleichtert dies, jeden Teil unabhängig zu erstellen und seinen Wert zu überprüfen. Sie können dann alle Teile in einem abschließenden Ausdruck kombinieren. Eine nützliche Technik ist das Hinzufügen eines Textfelds in einer Matrixzelle, die Anzeige jedes Teils des Ausdrucks und das Festlegen der bedingten Sichtbarkeit des Textfelds. Platzieren Sie zum Steuern von Rahmenart und Farbe bei ausgeblendetem Textfeld das Textfeld zuerst in einem Rechteck, und legen Sie dann die Rahmenart und die Farbe des Rechtecks der Matrix entsprechend fest.  
  
###  <a name="working-with-indicators"></a><a name="Indicators"></a> Arbeiten mit Indikatoren  
  
-   Standardmäßig zeigt ein Indikator mindestens drei Status an. Nachdem Sie einem Bericht einen Indikator hinzugefügt haben, können Sie ihn durch Hinzufügen oder Entfernen von Status konfigurieren. Wählen Sie zur einfacheren Anzeige durch Ihre Benutzer einen Indikator aus, der in Farbe und Form variiert.  
  
##  <a name="controlling-the-rendering-of-report-items-on-the-report-page"></a><a name="Rendering"></a> Steuern des Renderns von Berichtselementen auf der Berichtsseite  
  
-   Auf der Berichtsentwurfsoberfläche nehmen Berichtselemente an Größe zu, um Inhalte aus dem verknüpften Dataset, Ausdruck, Unterbericht oder Text aufzunehmen.  
  
    -   Wenn Sie ein Element auf der Berichtsseite positionieren, wird der Abstand zwischen dem Element und allen Elementen, die rechts davon beginnen, zum Mindestabstand, der beibehalten werden muss, wenn ein Berichtselement horizontal wächst. Ebenso wird der Abstand zwischen einem Element und dem Element darüber zum Mindestabstand, der beibehalten werden muss, wenn das oberste Element vertikal wächst.  
  
    -   Ein Element in einem Bericht wächst, um die Daten aufzunehmen, und drängt Peer-Elemente (Elemente innerhalb desselben übergeordneten Containers) mithilfe der folgenden Regeln zur Seite:  
  
    -   Jedes Element rückt nach unten, um den Mindestabstand zwischen sich selbst und den Elementen, die darüber enden, beizubehalten.  
  
    -   Jedes Element rückt nach rechts, um den Mindestabstand zwischen sich selbst und den Elementen, die links davon enden, beizubehalten. Bei Systemen mit „Rechts-nach-links“-Layouts rückt jedes Element nach links, um den Mindestabstand zwischen sich selbst und den Elementen, die rechts davon enden, beizubehalten.  
  
    -   Container werden erweitert, um den Wachstum von untergeordneten Elementen aufzunehmen. Für ein ausgewähltes Element im Eigenschaftenbereich bezeichnet die Parent-Eigenschaft den Container für das Element. Sie können auch den Bereich "Dokumentgliederung" verwenden, um die Kapselungshierarchie von Berichtselementen anzuzeigen.  
  
    -   In der **Layout**-Symbolleiste stehen mehrere Schaltflächen zum Ausrichten von Rändern, für Zentrierung und Abstand für Berichtselemente zur Verfügung. Um die **Layout**-Symbolleiste im Menü **Ansicht** zu aktivieren, zeigen Sie auf **Symbolleisten**, und klicken Sie dann auf **Layout**.  
  
-   Wenn Sie den Bericht als PDF-Datei speichern möchten, muss die Breite des Berichts explizit auf einen Wert festgelegt werden, mit dem Sie die gewünschten Ergebnisse im Exportdateiformat erhalten. Legen Sie die Breite der Berichtsseite z.B. genau auf 7,9375 Zoll fest und den linken und rechten Rand auf 0,5 Zoll.  
  
-   Verwenden Sie **Drucklayout** und **Seiteneinrichtung** auf der Berichts-Viewer-Symbolleiste, um einen Bericht in einer druckkompatiblen Ansicht zu rendern. Gehen Sie folgendermaßen vor, um unnötige leere Seiten zu entfernen:  
  
    1.  Entfernen Sie sämtlichen zusätzlichen Leerraum zwischen Datenbereichen und an den Rändern des Berichts.  
  
    2.  Reduzieren Sie Seitenränder im Dialogfeld **Berichtseigenschaften**.  
  
    3.  Verwenden Sie **Rechtecke** als Container, um zu steuern, wie Berichtselemente gerendert werden.  
  
    4.  Ändern Sie in Spaltenüberschriften die Textfeldeigenschaft WritingMode zur Verwendung vertikalen Texts.  

 Weitere Informationen finden Sie unter [Vermeiden von leeren Seiten beim Drucken paginierter Berichte](../guidance/report-paginated-blank-page.md).

 Die Kombination dieses Verhaltens, der Breiten- und Höheneigenschaften von Berichtselementen, der Größe des Berichtshauptteils, der Seitenhöhen- und Seitenbreitendefinition, die Seitenrandeinstellungen des übergeordneten Berichts und die rendererspezifische Unterstützung des Paginierens bestimmt, welche Berichtselemente zusammen auf eine gerenderte Seite passen.
 
## <a name="next-steps"></a>Weitere Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)  
