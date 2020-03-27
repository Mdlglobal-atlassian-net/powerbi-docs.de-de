---
title: Filtern eines Berichts mithilfe von Abfragezeichenfolgenparametern in der URL
description: Filtern Sie einen Bericht mithilfe von URL-Abfragezeichenfolgenparametern – bei Bedarf sogar für mehrere Felder.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/25/2020
LocalizationGroup: Reports
ms.openlocfilehash: 79f3fa8c9c175b698cb91784f95d3bb9d8ca0cc5
ms.sourcegitcommit: ad638d553d5f7f5831587791ffa7aa37a47dd6ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2020
ms.locfileid: "80273246"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtern eines Berichts mithilfe von Abfragezeichenfolgenparametern in der URL

Wenn Sie im Power BI-Dienst einen Bericht öffnen, hat jeder Seite des Berichts eine eigene eindeutige URL. Zum Filtern der jeweiligen Berichtsseite können Sie den Filterbereich des Berichtszeichenbereichs verwenden.  Sie können aber auch die URL mit Abfragezeichenfolgenparametern versehen, um den Bericht vorab zu filtern. Das ist beispielsweise hilfreich, wenn Sie Kollegen einen bereits vorgefilterten Bericht zeigen möchten. Zum Filtern können Sie etwa der Standard-URL des Berichts die gewünschten Filterparameter hinzufügen und dann die gesamte neue URL per E-Mail versenden.

![Power BI-Bericht im Dienst](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>Verwendungsmöglichkeiten für Abfragezeichenfolgenparameter

Angenommen, Sie arbeiten mit Power BI Desktop. Sie möchten einen Bericht erstellen, der Links zu anderen Power BI-Berichten enthält, aber nur einige der enthaltenen Informationen sollen in den anderen Berichten angezeigt werden. Filtern Sie zunächst die Berichte mithilfe von Abfragezeichenfolgenparametern, und speichern Sie die URLs. Erstellen Sie anschließend eine Tabelle mit diesen neuen Berichts-URLs in Power BI Desktop.  Veröffentlichen Sie den Bericht anschließend, und geben Sie ihn frei.

Auch beim Erstellen einer erweiterten Power BI-Lösung können Abfragezeichenfolgenparameter verwendet werden.  Mithilfe von DAX wird ein Bericht erstellt, der eine gefilterte Berichts-URL dynamisch basierend auf der Auswahl des Kunden im aktuellen Bericht generiert. Wenn Kunden auf die URL klicken, werden ihnen nur die gewünschten Informationen angezeigt. 

## <a name="query-string-parameter-syntax-for-filtering"></a>Syntax für Abfragezeichenfolgenparameter zum Filtern

Mit Parametern können Sie den Bericht nach mindestens einem Wert filtern, auch wenn dieser Wert Leerzeichen oder Sonderzeichen enthält. Die grundlegende Syntax ist recht einfach: Beginnen Sie mit der Berichts-URL, und fügen Sie dann ein Fragezeichen und Ihre Filtersyntax hinzu.

*URL*?filter=*Tabelle*/*Feld* eq '*Wert*'

![URL mit Filter](media/service-url-filters/power-bi-filter-urls7b.png)

* Bei den Namen für **Tabelle** und **Feld** muss die Groß-/Kleinschreibung beachtet werden, beim **Wert** nicht.
* Zum Filtern können auch Felder verwendet werden, die in der Berichtsansicht ausgeblendet sind.

### <a name="reports-in-apps"></a>Berichte in Apps

Wenn Sie einem Bericht in einer App einen URL-Filter hinzufügen möchten, sieht die Formatierung etwas anders aus. Für Links zu Berichten in einer App gibt es einen Abfrageparameter (ctid), der der URL hinzugefügt wird. Trennen Sie die Abfrageparameter durch ein kaufmännisches Und-Zeichen (&). Behalten Sie „?Filter=“ bei, und verschieben Sie den ctid-Parameter an das Ende der URL mit vorangestelltem kaufmännischen Und-Zeichen (&). 

Sehen Sie sich dazu das folgende Beispiel an:

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=*Table*/*Field* eq '*value*'&ctid=*ctid*

### <a name="field-types"></a>Feldtypen

Feldtypen können eine Zahl, ein datetime-Wert oder eine Zeichenfolge sein und müssen dem Typ entsprechen, der im Dataset festgelegt ist.  Das Festlegen einer Tabellenspalte auf „Zeichenfolge“ funktioniert beispielsweise nicht, wenn Sie nach einem Datums-/Uhrzeitwert oder einem numerischen Wert in einer Datasetspalte suchen, die auf „Datum“ festgelegt ist (z.B. Table/StringColumn eq 1).

* **Zeichenfolgen** müssen mit einfachen Anführungszeichen umschlossen werden, z. B. 'Managername'.
* Für **Zahlen** ist keine besondere Formatierung erforderlich. Weitere Details finden Sie in diesem Artikel unter [Numerische Datentypen](#numeric-data-types).
* **Datumsangaben und Uhrzeiten** finden Sie in diesem Artikel. unter [Date-Datentypen](#date-data-types). 

Auf all das gehen wir im weiteren Verlauf dieses Artikels noch näher ein.  

## <a name="filter-on-a-field"></a>Filtern nach einem Feld

Angenommen, die URL unseres Berichts lautet wie folgt:

![Ausgangs-URL](media/service-url-filters/power-bi-filter-urls6.png)

Und die Kartendarstellung (weiter oben) zeigt, dass wir über Filialen in North Carolina verfügen.

>[!NOTE]
>Dieses Beispiel basiert auf dem [Analysebeispiel für Einzelhandel](sample-datasets.md).
> 

Wenn Sie den Bericht filtern möchten, sodass nur Daten für Filialen in „NC“ (North Carolina) angezeigt werden, fügen Sie Folgendes an die URL an:

?filter=Store/Territory eq 'NC'

![URL mit Filter](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* ist als Wert im Feld **Territory** der Tabelle **Store** gespeichert.
> 

Der Bericht wird nach North Carolina gefiltert, und alle Visualisierungen auf der Berichtsseite zeigen nur noch Daten für North Carolina.

![Bericht gefiltert nach North Carolina](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-more-than-one-value-in-a-field"></a>In einem Feld nach mehr als einem Wert filtern

Verwenden Sie den Operator **in** anstelle von **and**, um im selben Feld nach mehr als einem Wert zu filtern. Die Syntax ist:

*URL*?filter=*Tabelle*/*Feld* **in** ('*Wert1*', '*Wert2*')

Für das Beispiel oben bedeutet das: Wenn Sie den Bericht filtern möchten, sodass nur Daten für Filialen in „NC“ (North Carolina) oder „TN“ (Tennessee) angezeigt werden, fügen Sie Folgendes an die URL an:

?filter=Store/Territory in ('NC', 'TN')

In der Tabelle [Operatoren](#operators) weiter unten im Artikel finden Sie eine Liste mit weiteren nützlichen Operatoren.

## <a name="filter-on-multiple-fields"></a>Filtern nach mehreren Feldern

Sie können auch nach mehreren Felder filtern, indem Sie weitere Parameter zu Ihrer URL hinzufügen. Hier nochmals der ursprüngliche Filterparameter.

```
?filter=Store/Territory eq 'NC'
```

Um nach weiteren Feldern zu filtern, fügen Sie ein **and** und ein weiteres Feld im selben Format wie oben hinzu. Es folgt ein Beispiel.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

## <a name="operators"></a>Operatoren

Power BI unterstützt außer **and** noch viele weitere Operatoren. In der folgenden Tabelle werden diese Operatoren zusammen mit dem Inhaltstyp, den sie unterstützen, aufgeführt:

|Operator  | Definition | Zeichenfolge  | Zahl | Datum |  Beispiel|
|---------|---------|---------|---------|---------|---------|
|**and**     | und |  Ja      | Ja |  Ja|  product/price le 200 and price gt 3.5 |
|**eq**     | Ist gleich |  Ja      | Ja   |  Ja       | Address/City eq 'Redmond' |
|**ne**     | Ungleich |   Ja      | Ja  | Ja        |  Address/City ne 'London' |
|**ge**     |  Größer als oder gleich       | Nein | Ja |Ja |  product/price ge 10
|**gt**     | Größer als        |Nein | Ja | Ja  | product/price gt 20
|**le**     |   Kleiner als oder gleich      | Nein | Ja | Ja  | product/price le 100
|**lt**     |  Kleiner als       | Nein | Ja | Ja |  product/price lt 20
|**in\*\***     |  Einschließlich       | Ja | Ja |  Ja | Student/Age in (27, 29)


\*\* Wenn Sie **in** verwenden, können die Werte auf der rechten Seite von **in** einer durch Kommas getrennten Liste entsprechen, die in Klammern eingeschlossen wird, oder einem einzelnen Ausdruck, der eine Sammlung zurückgibt.

### <a name="numeric-data-types"></a>Numerische Datentypen

Ein Filter für Power BI-URLs kann Zahlen in den folgenden Formaten enthalten:

|Zahlentyp  |Beispiel  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5L oder 5l      |
|**double**     |   5,5 oder 55e-1 oder 0,55e+1 oder 5D oder 5d oder 0,5e1D oder 0,5e1d oder 5,5D oder 5,5d oder 55e-1D oder 55e-1d     |
|**decimal**     |   5M oder 5m oder 5,5M oder 5,5m      |
|**float**     | 5F oder 5f oder 0,5e1F oder 0,5e-1d        |

### <a name="date-data-types"></a>Date-Datentypen

Power BI unterstützt OData V3 and V4 für **Date**- und **DateTimeOffset**-Datentypen. Für OData V3 müssen Daten mit einfachen Anführungszeichen umschlossen werden. Außerdem muss „datetime“ vorangestellt werden. Einfache Anführungszeichen und das Wort „datetime“ sind in OData V4 nicht erforderlich. 
  
Datumsangaben werden im EDM-Format (2019-02-12T00:00:00) dargestellt: Wenn Sie also ein Datum im Format YYYY-MM-DD angeben, interpretiert Power BI dieses als YYYY-MM-DDT00:00:00. Stellen Sie sicher, dass Sie Monate und Tage mit zwei Ziffern angeben, also MM und DD.

Warum ist diese Unterscheidung wichtig? Angenommen, Sie erstellen den Abfragezeichenfolgenparameter **Table/Date gt '2018-08-03'** .  Ist der 3. August 2018 in den Ergebnissen enthalten oder wird mit dem 4. August 2018 begonnen? Power BI übersetzt die Abfrage in **Table/Date gt '2018-08-03T00:00:00'** . Daher enthalten die Ergebnisse alle Datumsangaben, die einen Zeitabschnitt ungleich 0 aufweisen, da diese Datumsangaben größer als **'2018-08-03T00:00:00'** sind.

Es gibt weitere Unterschiede zwischen V3 und V4. OData V3 unterstützt keine Datumsangaben, sondern nur DateTime-Werte. Wenn Sie also das V3-Format verwenden, müssen Sie es mit dem vollständigen DateTime-Wert qualifizieren. Datumsliterale wie „datetime'2019-05-20'“ werden in der V3-Notation nicht unterstützt. Sie können sie jedoch in der V4-Notation einfach als „2019-05-20“ schreiben. Nachfolgend sehen Sie zwei äquivalente Filterabfragen in V3 und V4:

- OData V4-Format: filter=Table/Date gt 2019-05-20
- OData V3-Format: filter=Table/Date gt datetime'2019-05-20T00:00:00'


## <a name="special-characters-in-url-filters"></a>Sonderzeichen in URL-Filtern

Für Sonderzeichen und Leerzeichen sind zusätzliche Formatierungen erforderlich. Wenn Ihre Abfrage Leerzeichen, Bindestriche oder Nicht-ASCII-Zeichen enthält, stellen Sie diesen Sonderzeichen eine *Escapesequenz* voran, die mit einem Unterstrich und einem X ( **_x**) beginnt, gefolgt vom 4-stelligen **Unicode** und einem weiteren Unterstrich. Wenn der Unicode weniger als vier Zeichen enthält, müssen Sie diesen mit Nullen ergänzen. Hier sehen Sie einige Beispiele:

|Bezeichner  |Unicode  | Codierung für Power BI  |
|---------|---------|---------|
|**Tabellenname**     | Leerzeichen ist 0x20        |  Table_x0020_Name       |
|**Column**@**Number**     |   @ ist 0x40     |  Column_x0040_Number       |
|**[Column]**     |  [ is 0x005B ] is 0x005D       |  _x005B_Column_x005D_       |
|**Column+Plus**     | + ist 0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![Tabellenvisual, das Sonderzeichen rendert](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![Tabellenvisual, das Sonderzeichen rendert](media/service-url-filters/power-bi-special-characters2.png)

## <a name="use-dax-to-filter-on-multiple-values"></a>Verwenden von DAX, um nach mehreren Werten zu filtern

Eine andere Möglichkeit, nach mehreren Feldern zu filtern, besteht darin, eine berechnete Spalte zu erstellen, in der zwei Felder zu einem einzelnen Wert verkettet werden. Anschließend können Sie nach diesem Wert filtern.

Angenommen, es gibt zwei Felder: „Territory“ und „Chain“. In diesem Szenario können Sie in Power BI Desktop [eine neue berechnete Spalte](desktop-tutorial-create-calculated-columns.md) (Feld) namens „TerritoryChain“ erstellen. Beachten Sie, dass der **Feldname** keine Leerzeichen enthalten darf. Die DAX-Formel für diese Spalte sieht wie folgt aus:

TerritoryChain = [Territory] & " - " & [Chain]

Veröffentlichen Sie den Bericht für den Power BI-Dienst, und verwenden Sie die URL-Abfragezeichenfolge, um die Daten so zu filtern, dass nur Lindseys-Filialen in NC angezeigt werden.

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Anheften einer Kachel aus einem gefilterten Bericht

Nachdem Sie den Bericht mithilfe von Abfragezeichenfolgenparametern gefiltert haben, können Sie Visualisierungen aus diesem Bericht an Ihr Dashboard anheften.  Die Kachel auf dem Dashboard zeigt die gefilterten Daten, und wenn Sie die Dashboardkachel auswählen, wird der zugrunde liegende Bericht geöffnet.  Die Filterung, die Sie mit der URL ausgeführt haben, wird jedoch nicht mit dem Bericht gespeichert. Wenn Sie die Dashboardkachel auswählen, wird der Bericht im ungefilterten Zustand geöffnet.  Das heißt, die Daten auf der Dashboardkachel entsprechen nicht den Daten aus der Berichtsvisualisierung.

Diese Abweichung ist nützlich, wenn Sie unterschiedliche Ergebnisse anzeigen möchten (gefilterte Ergebnisse im Dashboard, ungefilterte Ergebnisse im Bericht).

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

Im Zusammenhang mit Abfragezeichenfolgenparametern müssen ein paar Dinge beachtet werden.

* Wenn Sie den *in*-Operator verwenden, müssen die Werte auf der rechten Seite von *in* einer durch Trennzeichen getrennten Liste entsprechen, die in Klammern eingeschlossen ist.    
* Der Power BI-Berichtsserver unterstützt auch die Möglichkeit, mithilfe des URL-Parameters „filter“ zusätzliche Filter anzugeben. Beispielsweise könnte die URL im Power BI-Berichtsserver wie folgt aussehen: `https://reportserver/reports/powerbi/Store Sales?rs:Embed=true&filter= Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'`
* Berichts-URL-Filter verfügen über eine Einschränkung von zehn Ausdrücken (zehn Filter die per AND verbunden sind).
* Der Datentyp „long“ ist aufgrund von Beschränkungen bei JavaScript (2^53–1).

URL-Filter werden in einigen eingebetteten Szenarios unterstützt, in anderen nicht.

- [Einbetten eines Berichts in ein sicheres Portal oder eine sichere Website](service-embed-secure.md) wird unterstützt.
- URL-Filter werden in Power BI Embedded unterstützt. Weitere Informationen finden Sie unter [Power BI Embedded: erweiterte URL-Filterfunktionen](https://azure.microsoft.com/updates/power-bi-embedded-advanced-url-filtering-capabilities).
- Das Filtern mittels Abfragezeichenfolge kann nicht für [Im Web veröffentlichen](service-publish-to-web.md) oder [In PDF exportieren](consumer/end-user-pdf.md) verwendet werden.
- Das [Einbetten mit dem Berichts-Webpart in SharePoint Online](service-embed-report-spo.md) unterstützt keine URL-Filter.
- Die Angabe einer URL ist für Teams nicht zulässig.

## <a name="next-steps"></a>Nächste Schritte

[Anheften einer Visualisierung an ein Dashboard](service-dashboard-pin-tile-from-report.md)  
[Registrieren Sie sich für eine kostenlose Testversion](https://powerbi.microsoft.com/get-started/)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
