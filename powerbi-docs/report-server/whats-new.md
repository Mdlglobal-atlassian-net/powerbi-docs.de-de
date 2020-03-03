---
title: Neuerungen in Power BI-Berichtsserver
description: Lernen Sie die Neuerungen in Power BI-Berichtsserver kennen. Dieser Artikel behandelt die wichtigsten Featurebereiche und wird aktualisiert, sobald neue Elemente veröffentlicht werden.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/27/2020
ms.openlocfilehash: 251f89dd031d9a2bda146266308dc528f05eddb2
ms.sourcegitcommit: ec4d2d0f52d737e8e0583f6a7b16e6fd87382510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782450"
---
# <a name="whats-new-in-power-bi-report-server"></a>Neuerungen in Power BI-Berichtsserver

Sie erhalten Informationen zu den Neuerungen im Power BI-Berichtsserver und in Power BI Desktop mit Optimierung für den Power BI-Berichtsserver. In diesem Artikel werden die wichtigsten Featurebereiche behandelt, und er wird mit jedem neuen Release aktualisiert.

Laden Sie den [Power BI-Berichtsserver und Power BI Desktop mit Optimierung für den Power BI-Berichtsserver](https://powerbi.microsoft.com/report-server/) herunter.

Informationen zu verwandten Power BI-Neuigkeiten finden Sie hier:

* [Neuigkeiten beim Power BI-Dienst](../service-whats-new.md)
* [Neuigkeiten in Power BI Desktop](../desktop-latest-update.md)
* [Neuigkeiten bei den mobilen Apps für Power BI](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>Januar 2020

Weitere Informationen finden Sie im Blogbeitrag zum Power BI-Berichtsserver von Januar 2020.

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>Power BI Desktop optimiert für Power BI-Berichtsserver

Dieses Release bietet viele neue Features wie die bedingte Formatierung für Schaltflächen, eine optimierte Datenprofilerstellung sowie weitere Formatierungseinstellungen für KPIs und Tabellenvisuals. Im Folgenden werden die Updates zusammengefasst:

**Berichterstellung**

- Festlegen eines Tabellenspalten- oder Matrixwerts als benutzerdefinierte URL
- Formatierungseinstellungen für KPI-Visuals
- Aktualisierungen des Filterbereichs

**Analyse**

- Bedingtes Formatieren von Schaltflächen
- Laden weiterer Analyseerkenntnisse
- Neue DAX-Funktion: Quartal

**Datenaufbereitung**

- Optimierte Datenprofilerstellung

**Sonstiges**

- Neues Dateiformat: .pbids
- Leistungsverbesserungen für Modellierungsvorgänge

**Berichterstellung**

*Festlegen eines Tabellenspalten- oder Matrixwerts als benutzerdefinierte URL*

Sie können Tabellenspalten- oder Matrixwerte als benutzerdefinierte URLs festlegen. Diese neue Option finden Sie unter der Karte für die bedingte Formatierung im Formatierungsbereich.

*Formatierungseinstellungen für KPI-Visuals*

Mit dem Release werden diesen Monat neue Formatierungsoptionen für KPIs eingeführt:

- Indikatortextformatierung (Schriftfamilie, Farbe und Ausrichtung)
- Transparenz der Trendachse
- Ziel- und Distanztextformatierung (Bezeichnungstext, Schriftfamilie, Farbe und Größe)
- Distanztextformatierung (Bezeichnungstext, positive Richtung, Schriftfamilie, Farbe und Größe)
- Hinzufügen einer Datumsbezeichnung mit Formatierung (Schriftfamilie, Farbe und Größe)

Sie können einige dieser neuen Formatierungsoptionen bedingt formatieren:

- Indikatorschriftfarbe
- Zielschriftfarbe und Zieldistanzschriftfarbe
- Farben für positive/negative/neutrale Statusangaben
- Schriftfarbe für Datumsangaben

*Aktualisierungen des Filterbereichs*

Im Rahmen der allgemein verfügbaren neuen Filteroption des [letzten Release](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane) wurde der Prozess zur Umstellung von aktuellen Berichten auf den neuen Bereich optimiert. Wenn Sie den Power BI-Berichtsserver zum ersten Mal öffnen, wird ein Dialogfeld zum automatischen Aktualisieren des Filterbereichs angezeigt. Zu diesen Aktualisierungen gehören auch Banner im Berichtsserver, wenn Berichte zur neuen Funktion migriert werden müssen.

**Analyse**

*Bedingte Formatierung von Schaltflächen*

Diese Updates der bedingten Formatierung gelten alle für Schaltflächen. Sie können jetzt die Formatierung für die folgenden Eigenschaften dynamisch festlegen:

- Schriftfarbe für Schaltflächentext
- Schaltflächentext
- Symbollinienfarbe
- Konturfarbe
- Füllfarbe
- QuickInfo zur Schaltfläche (unterhalb der Aktionskarte)

*Laden weiterer Analyseerkenntnisse*

Wenn Sie das Analysefeature ausführen, um Erkenntnisse aus Ihren Daten zu sammeln (z. B. um einen Anstieg zu erklären), werden die Machine Learning-Modelle nur für einen bestimmten Zeitraum ausgeführt, damit Ihnen schnell Ergebnisse präsentiert werden können. Wenn große Mengen an Daten analysiert werden müssen, können Sie die Analyse jetzt nach dem ursprünglichen Timeout fortsetzen.

*Neue DAX-Funktion: Quarter*

Diesen Monat wird die neue DAX-Funktion „Quarter“ eingeführt. Diese Funktion gibt das Quartal zum angegebenen Datum zurück.

**Datenaufbereitung**

*Verbesserungen bei der Datenprofilerstellung*

Diesen Monat führen wir einige bedeutende Verbesserungen an den Funktionen für die Datenprofilerstellung im Power Query-Editor ein. Beispiele:

- Mehrere Gruppierungsoptionen für das Spaltenprofilvisual für die Verteilung von Bereichswerten. Diese stehen in Abhängigkeit zum jeweiligen Spaltentyp und den bereits bestehenden „Nach Wert“-Kriterien.
- Text: Nach Textlänge (Anzahl der Zeichen)
- Nummer: Nach Zeichen (positiv/negativ) und Parität (gerade/ungerade)
- Date/Datetime: Nach Jahr, Monat, Tag, Kalenderwoche, Wochentag, Uhrzeit und Stunde innerhalb eines Tages.
- Sowie viele weitere Verbesserungen für andere Datentypen, z. B. logische TRUE-/FALSE-Rückgaben

*Filteroptionen*

In der Vergangenheit konnten Sie bereits im Verteilungsbereich „Spaltenprofile“ verschiedene typspezifische Gruppierungskriterien verwenden. Jetzt können Sie zudem innerhalb der Popups der einzelnen Werte im Verteilungsdiagramm filtern, wenn Gruppierungskriterien angewendet werden. Beispielsweise können Sie im Bereich „Datenprofile“ für eine Date/Datetime-Spalte alle Werte aus einem bestimmten Monat ausschließen.

**Sonstiges**

*Neues Dateiformat: .pbids*

Diesen Monat wird ein neues Dateiformat eingeführt: .pbids. Damit wird die Option „Daten abrufen“ für Berichtersteller in Ihrer Organisation optimiert. Es wird empfohlen, dass Administratoren diese Dateien für häufig verwendete Verbindungen erstellen.

Wenn ein Berichtersteller eine PBIDS-Datei öffnet, verlangt Power BI Desktop eine Authentifizierung zur Herstellung einer Verbindung mit der in der Datei angegebenen Datenquelle. Anschließend wählt der Benutzer die Tabellen aus, die in das Modell geladen werden sollen. Er muss möglicherweise auch die Datenbanken auswählen, wenn sie nicht in der Datei angegeben werden. Dann kann der Berichtersteller mit dem Erstellen von Visualisierungen beginnen.

Ausführliche Informationen und Beispiele finden Sie im Abschnitt [Verwenden von PBIDS-Dateien zum Abrufen von Daten](../desktop-data-sources.md#using-pbids-files-to-get-data) im Artikel „Datenquellen in Power BI Desktop“.

*Leistungsverbesserungen für Modellierungsvorgänge*

Die Leistung der Analysis Services-Engine wurde verbessert, um Modellierungsvorgänge wie das Hinzufügen von Measures oder berechneten Spalten und das Erstellen von Beziehungen zu beschleunigen. Der Umfang der Verbesserungen hängt vom Modell ab. Einige Kunden haben allerdings eine zwanzigfache Leistungsverbesserung für Aktionen wie das Öffnen einer Datei oder das Hinzufügen eines Measures festgestellt.

Das Release von Januar 2020 für den Power BI-Berichtsserver umfasst keine weiteren Neuerungen. Sie können uns gern weiter Feedback geben und für [Features abstimmen, die Sie sich für Power BI wünschen](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Power BI-Berichtsserver

#### <a name="export-to-excel-from-power-bi-reports"></a>Exportieren in Excel aus Power BI-Berichten

Das Exportieren eines Power BI-Berichts im Power BI-Berichtsserver in eine Excel-Datei funktioniert jetzt genauso wie im Power BI-Dienst. Sie können direkt in das XLSX-Format exportieren, und die Exportgrenze beträgt 150.000 Zeilen.

#### <a name="azure-sql-managed-instance-support"></a>Unterstützung verwalteter Azure SQL-Instanzen

Sie können jetzt einen Datenbankkatalog hosten, der für den Power BI-Berichtsserver in einer verwalteten Azure SQL-Datenbank-Instanz verwendet wird, die wiederum entweder in einer VM oder in Ihrem Rechenzentrum gehostet wird. Die Unterstützung ist auf die Verwendung von Datenbankanmeldeinformationen für das Herstellen einer Verbindung mit der verwalteten SQL-Datenbank-Instanz beschränkt.

#### <a name="power-bi-premium-dataset-support"></a>Unterstützung von Power BI Premium-Datasets

Sie können entweder den Microsoft-Berichts-Generator oder SQL Server Data Tools (SSDT) verwenden, um eine Verbindung zu Power BI-Datasets herzustellen. Anschließend können Sie diese Berichte mithilfe der SQL Server Analysis Services-Konnektivität im Power BI-Berichtsserver veröffentlichen. Benutzer müssen dafür einen gespeicherten Windows-Benutzernamen sowie das zugehörige Kennwort verwenden.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Unterstützung von alternativem Text (AltText) für Berichtselemente

Sie können zum Erstellen von Berichten QuickInfos verwenden, um für jedes Element in dem Bericht Text anzugeben. Diese QuickInfos werden von Sprachausgabetechnologien verwendet.

#### <a name="azure-active-directory-application-proxy-support"></a>Unterstützung für den Azure Active Directory-Anwendungsproxy

Mit dem Azure Active Directory-Anwendungsproxy müssen Sie Ihren eigenen Webanwendungsproxy nicht mehr verwalten, um für sicheren Zugriff über das Web oder über mobile Apps zu sorgen. Weitere Informationen erhalten Sie unter [Remotezugriff auf lokale Anwendungen über den Azure Active Directory-Anwendungsproxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

#### <a name="custom-headers"></a>Benutzerdefinierte Header

Diese legen Headerwerte für alle URLs fest, die mit dem angegebenen RegEx-Muster übereinstimmen. Benutzer können den benutzerdefinierten Headerwert durch gültigen XML-Code ersetzen, um Headerwerte für ausgewählte Anforderungs-URLs festzulegen. Administratoren können beliebig viele Header zum XML-Code hinzufügen. Weitere Informationen finden Sie im Artikel **Servereigenschaften (Seite erweitert)** zu Reporting Services im Abschnitt [Benutzerdefinierte Header](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders).

#### <a name="transparent-database-encryption"></a>Transparente Datenbankverschlüsselung

Der Power BI-Berichtsserver unterstützt jetzt Transparent Data Encryption für die Katalogdatenbank für den Power BI-Berichtsserver in den Editionen „Enterprise“ und „Standard“.

#### <a name="power-bi-visuals-api"></a>Power BI-Visualisierungs-API

In diesem Release ist die API-Version 2.6 enthalten.

#### <a name="microsoft-report-builder-update"></a>Update für den Berichts-Generator von Microsoft

Die kürzlich veröffentlichte Version des Berichts-Generators ist vollständig kompatibel mit den Reporting Services-Versionen von 2016, 2017 und 2019. Außerdem ist sie mit allen veröffentlichten und unterstützten Versionen des Power BI-Berichtsservers kompatibel.

## <a name="september-2019"></a>September 2019

Ausführliche Informationen zu den neuen Features finden Sie im Blogbeitrag zu [Power BI-Berichtsserver vom September 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/).

Das Update für Power BI-Berichtsserver vom September 2019 enthält viele Power BI-Berichtsfeatures. Im Folgenden werden einige Highlights aufgeführt:

- **Filter auf Visualebene für Slicer:** Sie können einen Filter auf Visualebene für Slicer hinzufügen. Dieser Filter funktioniert wie alle anderen Filter auf Visualebene. Nur der Slicer selbst wird gefiltert und keine anderen Visuals. Dieser Filter eignet sich zum Filtern leerer Felder oder für die Verwendung von Measurefiltern.
- **Symbole für Tabellen und Matrizen:** Mit KPI-Symbolen können Sie Regeln für die Anzeige verschiedener Symbolsätze in Ihren Tabellen und Matrizen ähnlich wie bei Symbolsätzen in Excel einrichten.
- **Gruppieren von Visuals:** Sie können nun Visuals, Formen, Textfelder, Bilder und Schaltflächen wie in PowerPoint auf einer Berichtsseite gruppieren. Wenn Sie Objekte gruppieren, können Sie sie alle gemeinsam verschieben und skalieren. Die Gruppierung vereinfacht die Arbeit in Berichten mit vielen geschichteten Objekten auf allen Seiten.
- **Neue Standarddesigns:** Die verfügbaren Designs für Berichte wurden aktualisieren, und das Standarddesign für neue Berichte wurde geändert, damit sie den neuen JSON-Optionen für Designs entsprechen. Das neue Standarddesign passt besser zur Designsprache von Microsoft und entspricht bewährten Designmethoden für Visuals. 
- **Aktualisiertes Bereichsdesign:** Ein Großteil der Benutzeroberfläche wurde überarbeitet. Alle Bereiche, die Fußzeile und der Ansicht-Switcher wurden in eine hellere Farbe geändert, ihre Abstände wurden angepasst und neue Symbole wurden eingeführt. Das neue Design ist der erste Schritt zur Überholung der gesamten Benutzeroberfläche.

In der folgenden Liste werden alle Features aufgeführt. 

### <a name="reporting"></a>Berichterstellung

- Aktualisiertes Bereichsdesign
- Filter auf Visualebene für Slicer
- Sortieren nach dem Bereich „Leistungsanalyse“
- QuickInfo für Visualheader
- Anpassung der Bezeichnung für Gesamtsumme für Tabellen und Matrizen
- Synchronisieren der Slicerunterstützung für Hierarchieslicer
- Konsistente Schriftgrade für Visuals
- Symbolsätze für Tabellen und Matrizen
- Unterstützung von Prozenten für bedingte Formatierung nach Regeln
- Der neue Filterbereich ist jetzt allgemein verfügbar
- Unterstützung für Datenfarben bei der Verwendung der Wiedergabeachse für Punktdiagramme
- Leistungsverbesserungen bei der Verwendung relativer Datums- und Dropdown-Slicer
- Gruppieren von Visuals
- Farb- und Textklassen in Designs
- Neue Standarddesigns

### <a name="analytics"></a>Analyse

- Benutzerdefinierte Zeichenfolgen
- Updates der Formatierungsoptionen für die bedingte Formatierung

    - Hintergrund- und Titelfarben für Visuals
    - Farben für das Kartenvisual
    - Füllen und Farben von Messgerätvisuals
    - Alternativer Text
    - Rahmenfarbe

- Warnungen für bedingte Formatierung
- Verbesserung der Drillthrougherkennbarkeit
- Neue DAX-Ausdrücke: REMOVEFILTERS und CONVERT
- Neuer DAX-Vergleichsoperatoren: „==“

### <a name="data-preparation"></a>Datenvorbereitung

- Verbesserung von M Intellisense
- Neue Transformation: Spalte nach Positionen teilen
- Kopieren in die Zwischenablage aus der Datenprofilerstellung


## <a name="may-2019"></a>Mai 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop für Power BI-Berichtsserver

Ausführliche Informationen zu den neuen Features finden Sie im Blogbeitrag zu [Power BI-Berichtsserver vom Mai 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/).

Im Folgenden werden einige Highlights des Release aufgeführt:

#### <a name="performance-analyzer"></a>Performance Analyzer 

Wenn Ihr Bericht langsamer als erwartet ausgeführt wird, verwenden Sie die Leistungsanalyse in Power BI Desktop. Wenn Sie die Leistungsanalyse starten, wird eine Protokolldatei mit Informationen zu allen Aktionen erstellt, die Sie im Bericht vornehmen. Weitere Informationen finden Sie unter [Leistungsanalyse](../desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Neue Modellierungsansicht

In der neuen Modellierungsansicht in Power BI Desktop können Sie komplexe Datasets mit vielen Tabellen anzeigen und mit diesen arbeiten. Zu den Highlights gehören mehrere Diagrammlayouts und die Massenbearbeitung von Spalten, Measures und Tabellen. Weitere Informationen finden Sie unter [Modellierungsansicht](../desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Zugängliche Interaktion mit Visuals

Sie können nun mithilfe der Tastaturnavigation auf die Datenpunkte vieler integrierter Visuals zugreifen. Weitere Informationen finden Sie unter [Barrierefreiheit in Power BI Desktop-Berichten](../desktop-accessibility.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Bedingte Formatierung für Titel und Web-URL-Aktionen

Power BI-Berichte sind interaktiv. Es ist sinnvoll, dass Titel in einem Bericht dynamisch sind, um den aktuellen Zustand des Berichts widerzuspiegeln. Sie können dieselbe ausdrucksbasierte Formatierung verwenden, um dynamische URLs für Ihre Schaltflächen, Formen und Bilder zu erstellen. Weitere Informationen finden Sie unter [Ausdrucksbasierte Titel](../desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Kreuzhervorhebung mit Achsenbezeichnungen

Wählen Sie die Achsenkategoriebezeichnungen in einem Visual aus, um die anderen Elemente auf einer Seite auf gleicher Weise übergreifend hervorzuheben, wie Sie Datenpunkte in einem Visual auswählen würden. Weitere Informationen finden Sie unter [Kreuzhervorhebung](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting).

#### <a name="all-the-new-features"></a>Alle neuen Features

Im Folgenden werden alle neuen Features aufgeführt:

#### <a name="reporting"></a>Berichterstellung

- Kreuzhervorhebung für einzelne Punkte in Liniendiagrammen 
- Zeilenumbruch bei Titeln 
- Update für die Standardinteraktion mit Visuals zum Kreuzfiltern
- Abgerundete Ecken bei Rahmen von Visuals 
- Einzelauswahlslicer  
- Wärmebildunterstützung für Bing Karten  
- Kreuzhervorhebung mit Achsenbezeichnungen  
- Standardformatierung von QuickInfos  
- Unterstützung statischer Web-URLs für Schaltflächen, Formen und Bilder  
- Optionen für Seitenausrichtung   
- Verbesserungen des Auswahlbereichs  
- Zugängliche Interaktion mit Visuals  
- Bedingte Formatierung für Titel von Visuals  
- Bedingte Formatierung für Web-URL-Aktionen für Schaltflächen, Formen und Bilder
- Leistungsanalysebereich
- Tastaturnavigation für Tabellen und Matrizen
- Positionssteuerelement für Datenbeschriftungen auf Zeilenebene
- Steuerelement für die Textgröße der Anzeige des KPI-Visuals

#### <a name="analytics"></a>Analyse

- Das Anzeigen von Datumsangaben als Hierarchie ist jetzt allgemein verfügbar  

#### <a name="modeling"></a>Modellierung

- Die neue Modellierungsansicht ist jetzt allgemein verfügbar
- Neue DAX-Funktionen
- Update der ALLSELECTED DAX-Funktion
- Deaktivieren der automatisch generierten Datumstabellen für neue Berichte

### <a name="power-bi-report-server"></a>Power BI-Berichtsserver

#### <a name="support-for-trusted-visuals"></a>Unterstützung für vertrauenswürdige Visuals

Die Unterstützung von vertrauenswürdigen Visuals wurde zu Power BI-Berichtsserver hinzugefügt. Derzeit werden die Visuals „Mapbox“ und „PowerOn“ unterstützt. (Esri, Visio und PowerApps werden in diesem Release nicht unterstützt.)

#### <a name="improved-security-features"></a>Verbesserte Sicherheitsfeatures

Administratoren können **RestrictedResourceMimeTypeForUpload** verwenden, um eine durch Kommas getrennte Liste gesperrter MIME-Typen festlegen können, z. B. Text oder HTML.

## <a name="january-2019"></a>Januar 2019

Folgende Features werden nun in Power BI-Berichten unterstützt:

[**Sicherheit auf Zeilenebene:**](row-level-security-report-server.md) Wenn Sie die Sicherheit auf Zeilenebene (Row Level Security, RLS) auf dem Power BI-Berichtsserver einrichten, können Sie den Datenzugriff für bestimmte Benutzer einschränken. Filter beschränken den Datenzugriff auf Zeilenebene, und Sie können Filter in Rollen definieren.

[**Erweitern und Reduzieren in den Zeilenüberschriften einer Matrix:**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) Es ist nun möglich, einzelne Zeilenüberschriften in Visuals zu erweitern oder zu reduzieren. Dieses Feature wurde sehr häufig gefordert.

[**Kopieren und Einfügen zwischen PBIX-Dateien:**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) Sie können Visuals zwischen PBIX-Dateien kopieren, indem Sie entweder das Kontextmenü des Visuals oder die Standardtastenkombination STRG+C verwenden. Fügen Sie die Datei anschließend mit STRG+V in einen anderen Bericht ein.

[**Intelligente Hinweise zur Ausrichtung:**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) Wenn Sie Objekte auf Ihrer Berichtsseite verschieben, werden Ihnen intelligente Hinweise zur Ausrichtung angezeigt (ähnlich wie in PowerPoint), damit Sie Ihre Seite optimaler gestalten können. Die intelligenten Hinweise werden immer angezeigt, wenn Sie ein Objekt auf der Seite ziehen oder dessen Größe ändern. Wenn Sie ein Objekt in die Nähe eines anderen verschieben, wird es an der Position des anderen Objekts ausgerichtet.

**Features für die Barrierefreiheit:** Es gibt viele Features für die Barrierefreiheit, z. B. [die Unterstützung für die Barrierefreiheit des Bereichs zum Auflisten von Feldern](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Der Bereich zum Auflisten von Feldern ist vollständig barrierefrei. Sie können in diesem Bereich navigieren, indem Sie nur die Tastatur und die Sprachausgabe verwenden. Über das Kontextmenü können Sie Felder zu Ihrer Berichtsseite hinzufügen.

#### <a name="custom-visuals"></a>Benutzerdefinierte Visuals

- In diesem Release ist API-Version 2.3 enthalten.

### <a name="administrator-settings"></a>Administratoreinstellungen

Administratoren können die folgenden Eigenschaften in den erweiterten SSMS-Eigenschaften für die Serverfarm festlegen:

**AllowedResourceExtensionsForUpload:** Sie können die Erweiterungen der Ressourcen einschränken, die auf den Berichtsserver hochgeladen werden können. Die Erweiterungen für integrierte Dateitypen wie &ast;.rdl und &ast;.pbix müssen nicht aufgeführt werden. Standardmäßig sind die Erweiterungen &ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt und &ast;.pptx” enthalten. 

**SupportedHyperlinkSchemes:** Legt eine durch Trennzeichen getrennte Liste der URI-Schemas fest, die in Hyperlinkaktionen definiert werden dürfen, die gerendert werden können. Alternativ wird „&ast;“ festgelegt, um alle Hyperlinkschemas zuzulassen. Mit der Einstellung „http,https“ sind beispielsweise Links zu „https://www. contoso.com“ zulässig, aber Hyperlinks zu „mailto:bill@contoso.com“ oder „javascript:window.open(‘www.contoso.com’, ‘_blank’)“ werden entfernt. Der Standardwert lautet „&ast;“.

## <a name="august-2018"></a>August 2018

Die für Power BI-Berichtsserver optimierte Version von Power BI Desktop von August 2018 enthält viele neue Features. Die nach Bereichen aufgeteilten neuen Features sind die folgenden:

- [Berichterstellung](#reporting)
- [Analyse](#analytics)
- [Modellierung](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Highlights des Release von August 2018

Diese neuen Features stechen besonders aus der langen Liste heraus. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/).

#### <a name="report-theming"></a>Berichtdesigns

Mithilfe von Berichtdesigns können Sie ab dem Power BI-Berichtsserver-Release von August 2018 die Farbe Ihrer Berichte schnell an ein Design oder ein Unternehmensbranding anpassen. Wenn Sie ein Design importieren, werden alle Diagramme automatisch aktualisiert, um die Farben des Designs zu verwenden, und Sie können auf die Designfarben aus der Farbpalette zugreifen. Sie können eine Designdatei hochladen, indem Sie unter **Design wechseln** die Option **Design importieren** auswählen.

Eine Designdatei ist eine JSON-Datei, die alle Farben enthält, die Sie in Ihrem Bericht mit jeder beliebigen Standardformatierung auf Visuals anwenden möchten.
Hier sehen Sie ein einfaches Beispiel für ein JSON-Design, das die Standardfarben des Berichts aktualisiert:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Bedingte Formatierung durch ein anderes Feld

Die Möglichkeit, eine Spalte nach einem anderen Feld im Modell zu formatieren, ist eine der deutlichen Verbesserungen für die bedingte Formatierung.

#### <a name="conditional-formatting-by-values"></a>Bedingte Formatierung nach Werten

Ein weiterer neuer Typ der bedingten Formatierung ist der Wert **Formatieren nach Feldwert**. Das Feld „Formatieren nach Feldwert“ ermöglicht es Ihnen, ein Measure oder eine Spalte zu verwenden, die eine Farbe entweder durch einen Hexadezimalcode oder einen Namen angibt und diese Farbe auf den Hintergrund oder die Schriftfarbe anwendet.

#### <a name="report-page-tooltips"></a>QuickInfos zur Berichtsseite

Das QuickInfo-Feature in Berichtsseiten ist im Power BI-Berichtsserver-Update von August 2018 enthalten. Dieses Feature ermöglicht es Ihnen, eine Berichtsseite zu entwerfen, die als benutzerdefinierte QuickInfo für andere Visuals in Ihrem Bericht verwendet werden kann.

#### <a name="log-axis-improvements"></a>Verbesserungen der Protokollachse

Wir haben die Protokollachse in kartesischen Diagrammen erheblich verbessert. Jetzt können Sie die logarithmische Skalierung für die numerische Achse jedes beliebigen kartesischen Diagramms wählen, einschließlich Kombinationsdiagramme, wenn Sie Daten verwenden, die komplett positiv oder komplett negativ sind.

#### <a name="sap-hana-sso-direct-query"></a>Direkte SAP HANA SSO-Abfrage

Die Unterstützung von direkten SAP HANA SSO-Abfragen mit Kerberos ist nun für Power BI-Berichte verfügbar.

>[!Note]
>Dieses Szenario wird nur unterstützt, wenn SAP HANA als relationale Datenquelle mit Berichten, die Sie in Power BI Desktop erstellt haben, behandelt wird.  Um dies in Power BI Desktop zu aktivieren, überprüfen Sie unter „Optionen“ im DirectQuery-Menü „SAP HANA als relationale Quelle behandeln“, und klicken Sie auf OK.

#### <a name="custom-visuals"></a>Benutzerdefinierte Visuals

- In diesem Release ist API-Version 1.13.0 enthalten.

- Für benutzerdefinierte Visuals kann jetzt ein Fallback auf eine vorherige Version ausgeführt werden, die mit der aktuellen Version der Server-API (falls verfügbar) kompatibel ist.

### <a name="reporting"></a>Berichterstellung 

- [Report Theming (Berichtdesigns)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Buttons to trigger actions (Schaltflächen zum Auslösen von Aktionen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Combo chart line styles (Linienarten für Kombinationsdiagramme)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Improved default sort for visuals (Verbesserte Standardsortierung für Visualisierungen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Numeric slicer (Numerischer Slicer)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Advanced slicer syncing (Erweiterte Slicersynchronisierung)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Log axis improvements (Verbesserungen der Protokollachse)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Data label options for funnel chart (Datenbeschriftungsoptionen für Trichterdiagramm)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Set line stroke width to zero (Strichstärke auf 0 festlegen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [High contrast support for reports (Unterstützung für hohen Berichtskontrast)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Donut radius control (Steuerung des Radius von Ringdiagrammen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Pie and donut detail labels position control (Positionssteuerelemente für Detailbeschriftungen in Kreis- und Ringdiagrammen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Format data labels separately for each measure in a combo chart (Separate Formatierung von Datenbeschriftungen für jedes Measure in Kombinationsdiagrammen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [New visual header with more flexibility and formatting (Neuer Visualheader mit mehr Flexibilität und Formatierungsoptionen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Wallpaper formatting (Hintergrundformatierung)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Tooltips for table & matrix (QuickInfos für Tabelle & Matrix)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Deaktivieren von QuickInfos für Visuals](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Slicer accessibility (Barrierefreiheit für Slicer)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Formatting pane improvements (Verbesserungen am Formatierungsbereich)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Stepped line support for line and combo charts (Unterstützung für abgestufte Linien für Linien- und Kombinationsdiagramme)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Sorting experience improvement (Verbesserungen an der Sortierung)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Print reports through Export to PDF (in Power BI Desktop) (Drucken von Berichten mithilfe von „In PDF exportieren“ (in Power BI Desktop))](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Create bookmark groups (Erstellen von Lesezeichengruppen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Slicer restatement (Filterneudarstellung)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Report page tooltips (QuickInfos zur Berichtsseite)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Analyse

- [Neue DAX-Funktion: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Measure drillthrough (Drillthrough messen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Conditional formatting by a different field (Bedingte Formatierung durch ein anderes Feld)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Bedingte Formatierung nach Werten (Bedingte Formatierung nach Werten)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modellierung

- [Filtering and sorting in data view (Filterung und Sortierung in der Datensicht)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Improved locale formatting (Verbesserung der Formatierung von Gebietsschemas)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Data categories for measures (Datenkategorien für Measures)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Statistical DAX functions (Statistische DAX-Funktionen)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>May 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Remotekonfiguration von mobilen Power BI-Apps für iOS für Berichtsserver

Als IT-Administrator können Sie nun das MDM-Tool Ihrer Organisation verwenden, um den Zugriff für mobile iOS-Apps für Power BI auf Berichtsserver remote zu konfigurieren. Weitere Informationen finden Sie unter [Configure Power BI iOS mobile app access to a report server remotely (Remotekonfiguration des Zugriffs der mobilen Power BI-App für iOS auf Berichtsserver)](configure-powerbi-mobile-apps-remote.md).

## <a name="march-2018"></a>März 2018

Das für Power BI-Berichtsserver optimierte Release von Power BI Desktop im März 2018 enthält viele neue Features. Die nach Bereichen aufgeteilten neuen Features sind die folgenden:

- [Visuals](#visuals-updates)
- [Berichterstellung](#reporting)
- [Analyse](#analytics)
- [Leistung](#performance)
- [Berichtsserver](#report-server)
- [Andere](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Highlights des Release von März 2018

Diese neuen Features stechen besonders aus der langen Liste heraus.

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Regelbasierte bedingte Formatierung für Tabellen und Matrizen](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Erstellen von Filtern, die unter bestimmten Bedingungen und abhängig von der spezifischen Geschäftslogik in Ihrer Tabelle oder Matrix die Farbe des Hintergrunds oder der Schriftfarbe einer Spalte verändern.

#### <a name="show-and-hide-pages"></a>[Ein- und Ausblenden von Seiten](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

Sie wollen Lesern den Zugriff auf Ihren Bericht gewähren, obwohl einige Seiten noch nicht fertig bearbeitet sind? Jetzt können Sie diese Seiten ausblenden, bis sie fertig bearbeitet sind. Oder Sie können Seiten ausblenden, die über die normale Navigationsleiste gesucht werden. Leser können diese Seiten mithilfe von Lesezeichen oder Drillthrough abrufen.

#### <a name="bookmarking"></a>[Hinzufügen von Lesezeichen](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Erstellen Sie Lesezeichen, um mit den Daten in Ihrem Bericht eine Geschichte zu erzählen.

- [Kreuzhervorhebung für Lesezeichen](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): Lesezeichen enthalten den Status der Kreuzhervorhebung einer Berichtsseite zum Zeitpunkt des Erstellens des Lesezeichens und zeigen diese an.
- [Mehr Flexibilität bei Lesezeichen](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): Lesezeichen reflektieren die von Ihnen im Bericht festgelegten Eigenschaften und haben nur Auswirkungen auf die von Ihnen gewählten Visuals.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Mehrfachauswahl von Datenpunkten aus mehreren Diagrammen](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Wählen Sie mehrere Datenpunkte aus mehreren Diagrammen aus, und wenden Sie den Kreuzfilter auf die ganze Seite an.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Synchronisieren von Slicern auf mehreren Seiten Ihres Berichts](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Ein Slicer kann für eine, zwei oder mehrere Seiten in einem Bericht angewendet werden.

#### <a name="quick-measures"></a>[Quickmeasures](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Erstellen Sie neue Measures, die auf bereits vorhandenen Measures und numerischen Spalten in einer Tabelle basieren.

#### <a name="drilling-down-filters-other-visuals"></a>[Drilldownfilter für andere Visuals](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Wenn Sie in einer bestimmten Kategorie eines Visuals einen Drilldown ausführen, können Sie alle Visuals auf der Seite nach derselben Kategorie filtern.

### <a name="visuals-updates"></a>Updates für Visuals

- [Zellenausrichtung in Tabellen und Matrizen](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Anzeigeeinheiten und Präzisionssteuerung für Tabellen- und Matrixspalten](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Datenbezeichungen für den Überlauf von Balken- und Säulendiagrammen](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [Steuern der Hintergrundfarbe von Datenbeschriftungen für kartesische Visuals und Kartenvisuals](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Steuerelement zum Auffüllen von Leisten und Spalten](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Vergrößern des für Achsenbezeichnungen verwendeten Bereichs in Diagrammen](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Punktdiagrammvisual aus x- und y-Achsengruppierungen](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [Stichprobenentnahme mit hoher Dichte für Karten auf Grundlage von Breiten- und Längengrad](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Dynamische Datenschnitte](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Hinzufügen eines Ankerdatums für einen relativen Datenschnitt mit Datum](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Berichterstellung

- [Deaktivieren des visuellen Headers im Lesemodus für einen Bericht](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Berichtsoptionen für langsame Datenquellen](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Verbesserte Standardplatzierung von Visuals](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [Steuern der Visualsortierung über den Auswahlbereich](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Sperren von Objekten im Bericht](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Durchsuchen der Bereiche „Formatierung“ und „Analyse“](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Bereich „Feldeigenschaften“ und Feldbeschreibungen](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Analyse

- [UTCNOW() und UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Markieren einer benutzerdefinierten Datumstabelle](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Drillfilter für andere Visuals](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Formatierung auf Zellenebene mehrdimensionaler AS-Modelle für mehrzeilige Zuordnung](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Leistung

- [Verbesserung der Filterleistung](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Leistungsverbesserungen für DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Leistungsverbesserungen beim Öffnen und Speichern](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Verbesserungen an „Elemente ohne Daten anzeigen“](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Berichtsserver

#### <a name="export-to-accessible-pdf"></a>Exportieren in eine zugängliche PDF

Wenn Sie einen paginierten Bericht (RDL) in eine PDF exportieren, erhalten Sie jetzt eine verfügbare/markierte PDF-Datei. Diese Datei ist zwar größer, aber für Sprachausgabedienste und andere unterstützende Technologien leichter zu lesen und zu navigieren. Sie können zugängliche PDFs aktivieren, indem Sie die Geräteinformationseinstellung **AccessiblePDF** auf **TRUE** festlegen. Informationen hierzu finden Sie unter [PDF Device Information Settings (PDF-Geräteinformationseinstellungen)](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings) und [Changing Device Information Settings (Ändern der Geräteinformationseinstellungen)](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Sonstige Verbesserungen

- [Verbesserung der Funktion „Spalte aus Beispielen hinzufügen“](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Schnellzugriff auf Beratungsdienste](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Verbesserte Fehlerberichtserstellung](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Anzeigen zuvor aufgetretener Fehler](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Oktober 2017

### <a name="power-bi-report-data-sources"></a>Power BI-Berichtsdatenquellen

Power BI-Berichte in Power BI-Berichtsserver können mit einer Vielzahl von Datenquellen verbunden werden. Sie können Daten importieren und die Datenaktualisierung planen oder die Daten mit DirectQuery oder über eine Liveverbindung mit SQL Server Analysis Services direkt abfragen. Siehe die Liste der Datenquellen, die die geplante Aktualisierung unterstützen, sowie die Liste der Datenquellen, die DirectQuery unterstützen, in „Datenquellen für Power BI-Berichte in Power BI-Berichtsserver“.

### <a name="scheduled-data-refresh-for-imported-data"></a>Geplante Datenaktualisierung für importierte Daten

In Power BI-Berichtsserver können Sie eine geplante Datenaktualisierung einrichten, um die Daten in Power BI-Berichten mit einem eingebetteten Modell und nicht über eine Liveverbindung oder DirectQuery auf dem aktuellen Stand zu halten. Mit einem eingebetteten Modell importieren Sie die Daten, sodass sie von der ursprünglichen Datenquelle getrennt sind. Die Aktualisierung ist erforderlich, um die Daten auf dem neuesten Stand zu halten, und dies können Sie mit einer geplanten Aktualisierung erreichen. Informieren Sie sich über die „geplante Aktualisierung für Power BI-Berichte in Power BI-Berichtsserver“.

### <a name="editing-power-bi-reports-from-the-server"></a>Bearbeiten von Power BI-Berichten auf dem Server

Sie können Power BI-Berichtsdateien (PBIX-Dateien) vom Server aus öffnen und bearbeiten, Sie erhalten jedoch die hochgeladene Originaldatei zurück. **Wenn die Daten durch den Server aktualisiert werden, werden sie beim ersten Öffnen der Datei nicht aktualisiert**. Sie müssen Sie lokal manuell aktualisieren, damit die Änderungen sichtbar werden.

### <a name="large-file-uploaddownload"></a>Hochladen/Herunterladen großer Dateien

Sie können Dateien mit einer Größe von bis zu 2 GB hochladen; standardmäßig ist die Beschränkung jedoch in den Berichtsservereinstellungen in SSMS (SQL Server Management Studio) auf 1 GB festgelegt.  Diese Dateien werden im unveränderten Zustand für SharePoint in der Datenbank gespeichert, und es bedarf keiner speziellen Konfiguration für den SQL Server-Katalog.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Zugreifen auf freigegebene Datasets als OData-Feeds

Sie können mit einem OData-Feed auf freigegebene Datasets aus Power BI Desktop zugreifen. Weitere Informationen erhalten Sie unter [Zugreifen auf freigegebene Datasets als OData-Feeds in Power BI-Berichtsserver](access-dataset-odata.md).

### <a name="scale-out"></a>Horizontales Hochskalieren

Diese Version unterstützt das horizontale Hochskalieren. Verwenden Sie einen Lastenausgleich, und legen Sie die Serveraffinität fest, um die optimale Leistung zu erhalten. Das Szenario ist noch nicht für das horizontale Hochskalieren optimiert. Daher werden Modelle möglicherweise knotenübergreifend repliziert. Das Szenario funktioniert ohne den Netzwerklastenausgleich und persistente Sitzungen. Sie stellen jedoch nicht nur knotenübergreifend eine übermäßige Speicherauslastung fest, da das Modell N-mal geladen wird, auch die Leistung zwischen den Verbindungen wird beeinträchtigt, weil das Modell beim Antreffen eines neuen Knotens zwischen Anforderungen gestreamt wird.  

### <a name="administrator-settings"></a>Administratoreinstellungen

Administratoren können die folgenden Eigenschaften in den erweiterten SSMS-Eigenschaften für die Serverfarm festlegen:

* EnableCustomVisuals: TRUE/FALSE
* EnablePowerBIReportEmbeddedModels: TRUE/FALSE
* EnablePowerBIReportExportData: TRUE/FALSE
* MaxFileSizeMb: Der Standardwert lautet jetzt 1000.
* ModelCleanupCycleMinutes: Häufigkeit der Überprüfungen zum Entfernen von Modellen aus dem Arbeitsspeicher.
* ModelExpirationMinutes: Zeitraum bis zum Ablauf und Entfernen des Modells, basierend auf dem Zeitpunkt der letzten Verwendung.
* ScheduleRefreshTimeoutMinutes: Mögliche Dauer der Datenaktualisierung für ein Modell. Der Standardwert ist zwei Stunden.  Es gibt keine feste Obergrenze.

**Konfigurationsdatei „rsreportserver.config“**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>Entwickler-API

Die für SSRS 2017 eingeführte Entwickler-API (REST-API) wurde für Power BI-Berichtsserver in Bezug auf die Arbeit mit Excel-Dateien und PBIX-Dateien ausgeweitet. Ein möglicher Anwendungsfall ist der programmgesteuerte Download von Dateien vom Server, deren Aktualisierung sowie die anschließende Neuveröffentlichung der Dateien. Dies ist beispielsweise die einzige Möglichkeit, Excel-Arbeitsmappen mit PowerPivot-Modellen zu aktualisieren.

Beachten Sie, dass eine neue separate API für große Dateien vorhanden ist, die in der Power BI-Berichtsserver-Version von Swagger aktualisiert wird. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>Speicherbedarf von SQL Server Analysis Services (SSAS) und Power BI-Berichtsserver

Power BI-Berichtsserver hostet SQL Server Analysis Services (SSAS) nun intern. Dies ist für die geplante Aktualisierung nicht spezifisch. Das Hosten von SSAS kann den Speicherbedarf für den Berichtsserver stark erhöhen. Die Konfigurationsdatei „AS.ini“ ist auf den Serverknoten verfügbar. Wenn Sie mit SSAS vertraut sind, können Sie die Einstellungen aktualisieren, u.a. die Obergrenze für Arbeitsspeicher und Datenträgerzwischenspeicherung. Einzelheiten finden Sie unter [Servereigenschaften in Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services).

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Anzeigen von und Interagieren mit Excel-Arbeitsmappen

Excel und Power BI enthalten ein Portfolio von Tools, das in der Branche einmalig ist. Gemeinsam ermöglichen sie es Wirtschaftsanalytikern, ihre Daten einfacher zu erfassen, zu strukturieren, zu analysieren und in visueller Form zu durchsuchen. Geschäftsanwender können nun nicht nur Power BI-Berichte im Webportal, sondern auch Excel-Arbeitsmappen in Power BI-Berichtsserver anzeigen. Damit verfügen sie über einen zentralen Ort zum Veröffentlichen und Anzeigen ihrer Microsoft BI-Self-Service-Inhalte.

Wir haben eine [exemplarische Vorgehensweise zum Hinzufügen von Office Online Server (OOS) zu Ihrer Power BI-Berichtsserver-Umgebung (Vorschauversion)](excel-oos.md) veröffentlicht. Kunden mit einem Volume Licensing-Konto können OOS kostenlos im Volume Licensing-Servicecenter herunterladen. Die Funktionalität für sie ist schreibgeschützt. Nach der Konfiguration können Benutzer Excel-Arbeitsmappen anzeigen und mit diesen interagieren. Für die Arbeitsmappen muss Folgendes gelten:

* Sie verfügen über keine Abhängigkeiten von externen Datenquellen.
* Sie verfügen über eine Liveverbindung mit einer SQL Server Analysis Services-Datenquelle.
* Sie weisen ein PowerPivot-Datenmodell auf.

### <a name="support-for-new-table-and-matrix-visuals"></a>Unterstützung für neue Tabellen- und Matrixvisuals

Power BI-Berichtsserver unterstützt nun die neuen Power BI-Tabellen- und Matrixvisuals. Wenn Sie Berichte mit diesen Visuals erstellen möchten, benötigen Sie eine Power BI Desktop-Version, die für Version vom Oktober 2017 aktualisiert ist. Eine parallele Installation mit dem Release von Power BI Desktop (Juni 2017) ist nicht möglich. Um die aktuelle Version von Power BI Desktop zu erhalten, wählen Sie auf der [Power BI-Berichtsserver-Downloadseite](https://powerbi.microsoft.com/report-server/) die Option **Erweiterte Downloadoptionen** aus.

## <a name="june-2017"></a>Juni 2017

* Allgemeine Verfügbarkeit von Power BI-Berichtsserver.

## <a name="may-2017"></a>Mai 2017

* Vorschauversion von Power BI-Berichtsserver jetzt verfügbar
* Möglichkeit zum lokalen Veröffentlichen von Power BI-Berichten
  * Unterstützung für benutzerdefinierte Visuals
  * Ausschließliche Unterstützung für **Liveverbindungen von Analysis Services** (weitere Datenquellen folgen)
  * Mobile Power BI-App so aktualisiert, dass in Power BI-Berichtsserver gehostete Power BI-Berichte angezeigt werden
* Bessere Zusammenarbeit in Berichten mit Kommentaren

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie sich folgende Quellen an, um sich über die neuesten Features in Power BI-Berichtsserver zu informieren.

* [Microsoft Power BI-Blog](https://powerbi.microsoft.com/blog/)
* [YouTube-Kanal „Guy in a Cube“](https://aka.ms/guyinacube)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
