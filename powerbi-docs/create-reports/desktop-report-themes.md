---
title: Verwenden von Berichtdesigns in Power BI Desktop
description: Erfahren Sie, wie Sie eine benutzerdefinierte Farbpalette verwenden und auf einen gesamten Bericht in Power BI Desktop anwenden.
author: davidiseminger
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/16/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1f29d59d3b10f8dc963d8ba1965638bc01bae0c8
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83335693"
---
# <a name="use-report-themes-in-power-bi-desktop"></a>Verwenden von Berichtdesigns in Power BI Desktop

Mit *Berichtsdesigns* in Power BI Desktop können Sie Entwurfsänderungen auf den gesamten Bericht anwenden, z. B. Verwenden von Unternehmensfarben, Ändern von Symbolgruppen oder Anwenden der neuen Standardformatierung auf Visuals. Wenn Sie ein Berichtsdesign anwenden, verwenden alle Visuals im Bericht automatisch die Farben und die Formatierung des ausgewählten Designs. Es gibt einige Ausnahmen, die weiter unten in diesem Artikel beschrieben werden.

![Report themes](media/desktop-report-themes/report-themes-1a.png)

Es gibt zwei Arten von Berichtsdesigns, nämlich integrierte Berichtsdesigns und benutzerdefinierte Berichtsdesigndateien:

- Integrierte Berichtsdesigns bieten unterschiedliche Arten vordefinierter Farbschemas, die mit Power BI Desktop installiert werden. Sie wählen integrierte Berichtsdesigns direkt im Power BI Desktop-Menü aus.

- Benutzerdefinierte Berichtsdesigndateien sind Berichts Designs, die in JSON-Dateien erstellt werden, die ihre grundlegende Struktur definieren. Zum Anwenden eines benutzerdefinierten Berichtsdesigns importieren Sie die zugehörige JSON-Datei in Power BI Desktop und wenden sie auf Ihren Bericht an.

  Stattdessen können Sie das Design eines vorhandenen Berichts auch in Power BI Desktop über das [Dialogfeld **Design anpassen**](#create-and-customize-a-theme-in-power-bi-desktop) selbst festlegen.

Sie können nahezu alle Elemente, die im Abschnitt **Format** des Bereichs **Visualisierungen** aufgelistet sind, anpassen und standardisieren, und zwar entweder durch Anpassungen, die direkt in Power BI Desktop erfolgen, oder über eine JSON-Datei mit dem Berichtsdesign. Mit dieser Funktion sollen Sie die Möglichkeit erhalten, das Standarddesign Ihres Berichts umfassend und bis ins kleinste Detail zu steuern.

## <a name="how-report-themes-work"></a>Funktionsweise von Berichtdesigns

Um ein Berichtsdesign auf einen Power BI Desktop-Bericht anzuwenden, können Sie entweder eines der [verfügbaren integrierten Berichtsdesigns](#built-in-report-themes) auswählen oder [ein benutzerdefiniertes Design als JSON-Datei](#import-custom-report-theme-files) importieren. Alternativ können Sie auch das [Dialogfeld **Design anpassen** verwenden](#create-and-customize-a-theme-in-power-bi-desktop).

Weitere Informationen zu anpassbaren Standardwerten finden Sie weiter unten im Abschnitt [Format der JSON-Datei für Berichtsdesigns](#report-theme-json-file-format).

### <a name="built-in-report-themes"></a>Integriertes Berichtsdesign

So wählen Sie aus den verfügbaren integrierten Berichtdesigns aus

1. Wählen Sie im Menüband **Start** den Befehl **Design wechseln** aus.

   ![Auswählen eines Berichtsdesigns](media/desktop-report-themes/report-themes-2a.png)

2. Wählen in der Dropdownliste eines der vorhandenen Designs aus.

   Das Berichtsdesign wird auf den Bericht angewendet.

In der folgenden Tabelle sind die verfügbaren integrierten Berichtsdesigns aufgeführt.

| Integriertes Berichtsdesign | Standardfarbsequenz |
|------ |---------- |
| Standard | ![Standard](media/desktop-report-themes/report-themes-color-scheme-default.png)|
| Hochhaus | ![Hochhaus](media/desktop-report-themes/report-themes-color-scheme-highrise.png)|
| Executive | ![Executive](media/desktop-report-themes/report-themes-color-scheme-executive.png)|
| Grenze| ![Grenze](media/desktop-report-themes/report-themes-color-scheme-frontier.png)|
| Innovativ | ![Innovativ](media/desktop-report-themes/report-themes-color-scheme-innovative.png)|
| Blüte | ![Blüte](media/desktop-report-themes/report-themes-color-scheme-bloom.png)|
| Gezeiten| ![Gezeiten](media/desktop-report-themes/report-themes-color-scheme-tidal.png)|
| Temperatur | ![Temperatur](media/desktop-report-themes/report-themes-color-scheme-temperature.png)|
| Solar| ![Solar](media/desktop-report-themes/report-themes-color-scheme-solar.png)|
| Divergent | ![Divergent](media/desktop-report-themes/report-themes-color-scheme-divergent.png)|
| Sturm | ![Sturm](media/desktop-report-themes/report-themes-color-scheme-storm.png)|
| Klassisch | ![Klassisch](media/desktop-report-themes/report-themes-color-scheme-classic.png)|
| Stadtpark | ![Stadtpark](media/desktop-report-themes/report-themes-color-scheme-city-park.png)|
| Klassenzimmer | ![Klassenzimmer](media/desktop-report-themes/report-themes-color-scheme-classroom.png)|
| Geeignet bei Farbenblindheit | ![Geeignet bei Farbenblindheit](media/desktop-report-themes/report-themes-color-scheme-colorblind-safe.png)|
| Elektrisch | ![Elektrisch](media/desktop-report-themes/report-themes-color-scheme-electric.png)|
| Hoher Kontrast | ![Hoher Kontrast](media/desktop-report-themes/report-themes-color-scheme-high-contrast.png)|
| Sonnenuntergang | ![Sonnenuntergang](media/desktop-report-themes/report-themes-color-scheme-sunset.png)|
| Dämmerung | ![Dämmerung](media/desktop-report-themes/report-themes-color-scheme-twilight.png)|

## <a name="customize-report-themes"></a>Anpassen von Berichtsdesigns

Mit der Version von Power BI Desktop vom Dezember 2019 wurden zwei neue Möglichkeiten zum Anpassen von Berichtsdesigns eingeführt:

- [Erstellen und Anpassen eines Designs in Power BI Desktop](#create-and-customize-a-theme-in-power-bi-desktop)
- [Erstellen und Anpassen einer benutzerdefinierten JSON-Berichtsdesigndatei](#introduction-to-report-theme-json-files)

### <a name="create-and-customize-a-theme-in-power-bi-desktop"></a>Erstellen und Anpassen eines Designs in Power BI Desktop

So passen Sie ein Design direkt in Power BI Desktop an

1. Wählen Sie im Menüband **Start** die Befehle **Design wechseln** > **Aktuelles Design anpassen** aus.

   Ein Dialogfeld wird angezeigt, in dem die Möglichkeiten für das Anpassen des aktuell verwendeten Berichtsdesigns angezeigt werden.

   ![Anpassen des Designs](media/desktop-report-themes/report-themes_5b.png)

2. Wenn Ihnen ein vorhandenes Design gefällt und Sie einige Anpassungen vornehmen möchten, wählen Sie das Design aus, oder importieren Sie es, und klicken Sie dann auf **Aktuelles Design anpassen**.

   ![Anpassen eines aktuellen Designs](media/desktop-report-themes/report-themes_5c.png)

Anpassbare Designeinstellungen finden Sie in den folgenden Kategorien, die im Fenster **Design anpassen** angezeigt werden:

- **Name und Farben**: Zu den Einstellungen für Namen und Farben zählen u. a. [Design-](#how-report-theme-colors-stick-with-your-reports), Stimmungs- und [Strukturfarben](#setting-structural-colors) sowie abweichende Farben.
- **Text**: Zu den Texteinstellungen zählen z. B. die Schriftfamilie, Schriftgröße und Schriftfarbe. Damit werden [die Standardwerte der primären Textklassen](#setting-formatted-text-defaults) für Bezeichnungen, Titel, Karten und KPIs sowie Registerkartenüberschriften festgelegt.
- **Visuals**: Die Einstellungen für Visuals gelten z. B. für Hintergründe, Rahmen, Überschriften und QuickInfos.
- **Seite**: Zu den Einstellungen für Seitenelemente zählen Hintergrundbild und Hintergrund.
- **Filterbereich**: Einstellungen für den Filterbereich sind u. a. Hintergrundfarbe, Transparenz, Schrift- und Symbolfarbe, Größe und Filterkarten.

Nachdem Sie die Änderungen vorgenommen haben, wählen Sie **Anwenden und speichern** aus, um das Design zu speichern. Ihr Design kann nun im aktuellen Bericht verwendet und exportiert werden.

Auf diese Weise können Sie Ihr aktuelles Design schnell und einfach anpassen. Sie können jedoch detailliertere Anpassungen an Designs vornehmen, wozu eine Änderung der [JSON-Datei](#report-theme-json-file-format) des Designs erforderlich ist.

> [!TIP]
> Die wichtigsten Berichtsdesignoptionen lassen sich über die Steuerelemente im Dialogfeld **Design anpassen** konfigurieren. Wenn Sie weitere Komponenten des Berichts bearbeiten möchten, können Sie die JSON-Datei exportieren und manuell Feinjustierungen vornehmen, indem Sie die Einstellungen in dieser Datei manuell anpassen. Sie können diese optimierte JSON-Datei umbenennen und später importieren.

### <a name="import-custom-report-theme-files"></a>Importieren benutzerdefinierter Berichtsdesigndateien

So importieren Sie eine benutzerdefinierte Berichtsdesigndatei

1. Wählen Sie im Menüband **Start** den Befehl **Design wechseln** und dann im Dropdownmenü **Design importieren** aus.

   ![Design importieren](media/desktop-report-themes/report-themes-3a.png)

   Navigieren Sie im neu angezeigten Fenster zum Speicherort der JSON-Datei mit dem Design.

2. In der folgenden Abbildung sehen Sie einige Dateien mit Feiertagsdesigns. Wir wählen ein Feiertagsdesign für März aus, *St Patricks Day.json*.

   ![Feiertagsdesign](media/desktop-report-themes/report-themes_4.png)

   Wenn die Designdatei erfolgreich geladen wurde, zeigt Power BI Desktop eine Erfolgsmeldung an.

   ![Erfolgreicher Import des Designs](media/desktop-report-themes/report-themes_5.png)

## <a name="introduction-to-report-theme-json-files"></a>Einführung in JSON-Berichtdesigndateien

 Wenn Sie die im vorigen Abschnitt erwähnte einfache JSON-Datei (St. Patricks Day.json) öffnen, wird sie wie folgt angezeigt:

 ```json
    {
        "name": "St Patrick's Day",
        "dataColors": ["#568410", "#3A6108", "#70A322", "#915203", "#D79A12", "#bb7711", "#114400", "#aacc66"],
        "background":"#FFFFFF",
        "foreground": "#3A6108",
        "tableAccent": "#568410"
    }
```

Diese JSON-Datei mit dem Berichtsdesign weist die folgenden Zeilen auf:

- **name**: Den Namen des Berichtsdesigns. Dies ist das einzige Pflichtfeld.
- **dataColors**: Eine Liste mit Farben im Hexadezimalcode für Daten in Power BI Desktop-Visuals. Diese Liste kann wahlweise so viele oder so wenige Farben aufweisen, wie Sie möchten.
- **background**, **firstLevelElements** und **tableAccent** (etc.): Farbklassen. Mithilfe von Farbklassen können Sie mehrere Strukturfarben in Ihrem Bericht auf einmal festlegen.

Sie können diese JSON-Datei als Grundlage für die Erstellung Ihrer eigenen benutzerdefinierten Berichtsdesigndatei zum Importieren verwenden. Wenn Sie nur die Grundfarben Ihres Berichts anpassen möchten, ändern Sie den Namen und die Hexcodes in der Datei.

In einer JSON-Berichtsdesigndatei geben Sie nur die Formatierung an, die Sie ändern möchten. Alles, was Sie nicht in der JSON-Datei angeben, wird auf die Standardeinstellungen von Power BI Desktop zurückgesetzt.

Das Erstellen einer JSON-Datei bietet viele Vorteile. Sie können beispielsweise festlegen, dass für alle Diagramme der Schriftgrad 12 verwendet wird, dass für bestimmte Visuals eine bestimmte Schriftfamilie verwendet wird oder das Datenbeschriftungen für bestimmte Diagrammtypen deaktiviert sind. Mithilfe einer JSON-Datei können Sie eine Berichtsdesigndatei erstellen, die Ihre Diagramme und Berichte standardisiert. Dies verhilft Ihren Organisationsberichten zu einem einheitlichen Erscheinungsbild.

Weitere Informationen zum Format der JSON-Datei finden Sie unter [Format der JSON-Datei für Berichtsdesigns](#report-theme-json-file-format).

> [!NOTE]
> Ein benutzerdefinierter JSON-Bericht kann problemlos über das [Dialogfeld **Design anpassen**](#create-and-customize-a-theme-in-power-bi-desktop) bearbeitet werden.  Über das Dialogfeld lassen sich keine Einstellungen für das Berichtsdesign anpassen, auf die das Dialogfeld keinen Zugriff hat. Außerdem werden die am Bericht vorgenommenen Änderungen sofort übernommen.

## <a name="how-report-theme-colors-stick-with-your-reports"></a>Darstellung von Berichtdesignfarben in Berichten

Wenn Sie Berichte im Power BI-Dienst veröffentlichen, bleiben die Berichtdesignfarben erhalten. Der Abschnitt **Datenfarben** im Bereich **Format** spiegelt Ihr Berichtsdesign wider.

So zeigen Sie die in einem Berichtdesign verfügbaren Farben an

1. Wählen Sie ein Visual aus.

2. Wählen Sie im Bereich **Visualisierung** im Bereich **Format** die Option **Datenfarben** aus.

3. Wählen Sie die Dropdownliste eines Elements aus, um die Informationen zu **Designfarben** des Berichtsdesigns anzuzeigen.

   ![Designfarben](media/desktop-report-themes/report-themes_8.png)

Nachdem Sie in unserem Beispiel die Vielzahl der grünen und braunen Farben aus dem Berichtsdesign „St. Patrick's Day“ angewendet haben, sehen Sie sich die Designfarben an. Also alles im grünen Bereich. Das liegt daran, dass diese Farben Teil des Berichtsdesigns sind, das Sie importiert und angewendet haben.

Die Farben in der Farbpalette sind relativ zum aktuellen Design. Angenommen, Sie wählen für einen Datenpunkt die dritte Farbe der obersten Zeile aus. Wenn Sie später zu einem anderen Design wechseln, wird die Farbe dieses Datenpunkts automatisch in die dritte Farbe der obersten Zeile des neuen Designs geändert, wie dies auch beim Ändern von Designs in Microsoft Office der Fall ist.

### <a name="situations-when-report-theme-colors-wont-stick-to-your-reports"></a>Situationen, in denen Berichtdesignfarben in Berichten nicht dargestellt werden

Angenommen, Sie wenden eine benutzerdefinierte Farbpalette (oder eine einzelne Farbe) unter Verwendung der Option **Benutzerdefinierte Farbe** in der Farbauswahl auf einen bestimmten Datenpunkt in einem Visual an. Wenn Sie ein Berichtsdesign anwenden, überschreibt es *nicht* die angepasste Datenpunktfarbe.

Oder angenommen, Sie möchten die Farbe eines Datenpunkts manuell mithilfe des Abschnitts **Designfarben** festlegen. Wenn Sie ein neues Berichtsdesign anwenden, werden diese Farben *nicht* aktualisiert. Um Farben auf ihre Standardwerte zurückzusetzen, damit sie bei Anwenden eines neuen Berichtsdesigns aktualisiert werden, wählen Sie **Auf Standardwert zurücksetzen** oder in der Farbauswahl eine Farbe in der Palette **Designfarben** aus.

![Auf Standardwert zurücksetzen](media/desktop-report-themes/report-themes_9.png)

Viele Power BI-Visuals lassen sich nicht auf Berichtsdesigns anwenden.

## <a name="custom-report-theme-files-you-can-use-right-now"></a>Benutzerdefinierte Berichtdesigndateien zur sofortigen Verwendung

Möchten Sie gleich mit Berichtdesigns arbeiten? Sehen Sie sich die benutzerdefinierten Berichtdesigns im [Designkatalog](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) an, oder probieren Sie die folgenden vordefinierten JSON-Dateien mit benutzerdefinierten Berichtdesigns aus, die Sie herunterladen und in Ihren Power BI Desktop-Bericht importieren können:

- [Design „Wellenform“](https://community.powerbi.com/t5/Themes-Gallery/Waveform/m-p/140536). Dieses Berichtsdesign wurde in dem [Blogbeitrag](https://powerbi.microsoft.com/blog/power-bi-desktop-march-feature-summary/) vorgestellt, in dem die erste Veröffentlichung von Berichtsdesign angekündigt wurde. [Waveform.json herunterladen](https://go.microsoft.com/fwlink/?linkid=843924).

  ![Design „waveform.json“](media/desktop-report-themes/report-themes_10.png)

- [Design „Benutzerfreundlich bei Farbenblindheit“](https://community.powerbi.com/t5/Themes-Gallery/Color-Blind-Friendly/m-p/140597).
Dieses Berichtsdesign ist für Sehbehinderte leichter zu lesen. [ColorblindSafe-Longer.json herunterladen](https://go.microsoft.com/fwlink/?linkid=843923).

  ![Design „ColorblindSafe-Longer.json“](media/desktop-report-themes/report-themes_11.png).

- Power View-Designs mit Apothecary.json. [Laden Sie Power View-Designs in einer ZIP-Datei herunter](https://go.microsoft.com/fwlink/?linkid=843925).

  ![Design „Apothecary.json“](media/desktop-report-themes/report-themes_12.png)

- Design „Valentine‘s Day“.

  ![Design „Valentine‘s Day“](media/desktop-report-themes/report-themes_13.png)

  Hier der Code der JSON-Datei für den Valentinstag:

   ```json
       {
           "name": "Valentine's Day",
           "dataColors": ["#990011", "#cc1144", "#ee7799", "#eebbcc", "#cc4477", "#cc5555", "#882222", "#A30E33"],
           "background":"#FFFFFF",
           "foreground": "#ee7799",
           "tableAccent": "#990011"
       }
   ```

Hier sind einige weitere Berichtsdesigns, die Sie als Ausgangspunkt verwenden können:

- [Sunflower Twilight](https://community.powerbi.com/t5/Themes-Gallery/Sunflower-Twilight/m-p/140749) (Sonnenblumen in der Dämmerung)
- [Plum](https://community.powerbi.com/t5/Themes-Gallery/Plum/m-p/140711) (Pflaume)
- [Autumn](https://community.powerbi.com/t5/Themes-Gallery/Autumn/m-p/140746) (Herbst)
- [Color Blind Friendly](https://community.powerbi.com/t5/Themes-Gallery/Color-Blind-Friendly/m-p/140597) (Für Farbenblinde)

Mithilfe von Berichtdesigns können Ihre Power BI Desktop-Berichte ein lebendiges Bild von Ihnen, Ihrem Unternehmen oder sogar der aktuellen Saison oder Feiertagen vermitteln.

## <a name="export-report-themes-preview"></a>Exportieren von Berichtsdesigns (Vorschau)

Ab der Power BI Desktop-Version vom Dezember 2019 können Sie das aktuell angewendete Berichtsdesign direkt aus Power BI Desktop in eine JSON-Datei exportieren. Nachdem Sie ein Berichtsdesign exportiert haben, können Sie es in anderen Berichten wiederverwenden. Mit dieser Option können Sie die JSON-Datei für die meisten integrierten Designs exportieren. Die einzigen Ausnahmen sind die Standarddesigns „Klassisch“ und „Standard“, auf denen andere Designs beim Import aufbauen.

So exportieren Sie das aktuell angewendete Design aus Power BI Desktop

1. Wählen Sie **Datei** > **Optionen und Einstellungen** > **Optionen** aus.

2. Wählen Sie im Abschnitt **Vorschaufeatures** erst **Aktuelles Design anpassen** und dann **OK** aus.

   Möglicherweise werden Sie aufgefordert, Power BI Desktop neu zu starten, damit das Vorschaufeature aktiviert wird. Nach dem Neustart können Sie mit dem Exportieren des aktuell angewendeten Designs beginnen.

3. Wählen Sie im Menüband **Start** die Befehle **Design wechseln** > **Aktuelles Design exportieren** aus.

4. Wechseln Sie im Dialogfeld **Speichern unter** zu einem Verzeichnis, in dem die JSON-Datei gespeichert werden soll, und wählen Sie dann **Speichern** aus.

## <a name="report-theme-json-file-format"></a>Format der JSON-Datei für Berichtsdesigns

Auf der grundlegendsten Ebene benötigt die JSON-Designdatei nur eine Zeile: **name**.

```json
{
    "name": "Custom Theme"
}
```

Alles andere als **name** ist optional. Dies bedeutet, dass Sie die Möglichkeit haben, nur die Eigenschaften in der Designdatei hinzuzufügen, die Sie explizit formatieren möchten, und für den Rest weiterhin die Standardwerte von Power BI zu verwenden.

### <a name="setting-theme-colors"></a>Festlegen von Designfarben

Unter **name** können Sie die folgenden grundlegenden Eigenschaften von Datenfarben hinzufügen:

- **dataColors**: Eine Liste der Hexadezimalcodes der Farben, mit denen Formen koloriert werden, mit denen Daten in Power BI Desktop-Visuals dargestellt werden. Diese Liste kann wahlweise so viele oder so wenige Farben aufweisen, wie Sie möchten. Wenn alle Farben aus dieser Liste verwendet worden sind und das Visual noch weitere Farben benötigt, erfolgt die Zurücksetzung auf die Verwendung der Standardfarbpalette von Power BI.
- **good**, **neutral**, **bad**: Mit diesen Eigenschaften werden die vom Wasserfalldiagramm und dem KPI-Visual verwendeten Statusfarben festgelegt.
- **maximum**, **center**, **minimum**, **null**: Mit diesen Farben werden die verschiedenen Farbverlaufsfarben im Dialogfeld für bedingte Formatierung festgelegt.

Ein einfaches Design, das diese Farben definiert, sieht ungefähr so aus:

```json
{
    "name": "Custom Theme",
    "dataColors": [
        "#118DFF",
        "#12239E",
        "#E66C37",
        "#6B007B",
        "#E044A7",
        "#744EC2",
        "#D9B300",
        "#D64550",
        "#197278",
        "#1AAB40"
    ],
    "good": "#1AAB40",
    "neutral": "#D9B300",
    "bad": "#D64554",
    "maximum": "#118DFF",
    "center": "#D9B300",
    "minimum": "#DEEFFF",
    "null": "#FF7F48"
}
```

### <a name="setting-structural-colors"></a>Festlegen von Strukturfarben

Als Nächstes können Sie verschiedene Farbklassen hinzufügen, wie z. B. **background** und **firstLevelElements**. Mit diesen Farbklassen werden die Strukturfarben für Berichtselemente wie Achsengitternetzlinien, Hervorhebungsfarben und Hintergrundfarben für Visuals festgelegt.

Die folgende Tabelle enthält die sechs Farbklassen, die Sie formatieren können.  Die Namen von **Farbklassen** entsprechen den Namen im Unterabschnitt „Erweitert“ des Abschnitts „Name und Farben“ im [Dialogfeld **Design anpassen**](#create-and-customize-a-theme-in-power-bi-desktop).

|Farbklasse  |Formatiert Folgendes  |
|---------|---------|
| **firstLevelElements** <br> **foreground** (veraltet) | Hintergrundfarbe für Beschriftungen (außerhalb von Datenpunkten) <br> Trendlinienfarbe <br>  Textfeld-Standardfarbe <br> Schriftfarbe für Tabellen- und Matrixwerte und Summen Datenbalken-Achsenfarbe <br> Kartendatenbeschriftungen <br> Farbe für Messgerätlegendenwert <br> KPI-Zielfarbe <br>  KPI-Textfarbe <br> Slicerelementfarbe (im Fokusmodus)  <br> Schriftfarbe für Slicerdropdownelement <br> Schriftfarbe für numerische Slicereingabe <br> Schriftfarbe für Slicerkopfzeile <br> Punktdiagramm-Verhältnislinienfarbe <br> Farbe für Liniendiagramm-Vorhersagelinie <br> Kartenführungslinien-Farbe <br> Farbe für Filterbereich und Kartentext|
| **secondLevelElements** <br> **foregroundNeutralSecondary** (veraltet) | „helle“ [sekundäre Textklassen](#setting-formatted-text-defaults) <br> Beschriftungsfarben  <br> Farbe für Legendenbeschriftungen <br> Farbe für Achsenbeschriftungen <br> Schriftfarbe für Tabellen- und Matrixkopfzeile <br> Farbe für Messgerätziel und Zielführungslinie <br>  KPI-Trendachsenfarbe <br> Farbe für Slicerschieberegler <br> Schriftfarbe für Slicerelement <br> Farbe für Slicerkontur <br> Farbe beim Zeigen auf Liniendiagramm <br> Titelfarbe für mehrzeilige Karte <br> Strichfarbe für Menübanddiagramm <br> Rahmenfarbe für Formenzuordnung <br> Schriftfarbe für Schaltflächentext <br> Linienfarbe für Schaltflächensymbol <br> Schaltflächen-Konturfarbe |
| **thirdLevelElements** <br >**backgroundLight** (veraltet) | Achsengitternetzlinien-Farbe <br> Tabellen- und Matrixrasterfarbe <br> Hintergrundfarbe für Slicerkopfzeile (im Fokusmodus)  <br> Konturfarbe für mehrzeilige Karte  <br> Formfüllfarbe <br> Hintergrundfarbe für Messgerätbogen <br> Hintergrundfarbe für angewendete Filterkarte <br> Wenn background = FFFFFF: <br> Deaktivierte Füllfarbe für Schaltflächen <br> Deaktivierte Konturfarbe für Schaltflächen <br> |
| **fourthLevelElements** <br> **foregroundNeutralTertiary** (veraltet) | abgeblendete Legendenfarbe <br> Farbe für Kartenkategoriebeschriftung <br> Farbe für Kategoriebeschriftungen für mehrzeilige Karte <br> Balkenfarbe für mehrzeilige Karte <br> Strichfarbe für Trichterdiagramm-Konvertierungsrate <br> Deaktivierte Schriftfarbe für Schaltflächentext <br> Deaktivierte Linienfarbe für Schaltflächensymbol <br> |
| **background** | Hintergrundfarbe für Beschriftungen (innerhalb von Datenpunkten) <br> Hintergrundfarbe für Slicerdropdownelemente  <br> Ringdiagramm-Strichfarbe <br> Treemapstrichfarbe <br> Hintergrundfarbe des Kombinationsdiagramms <br> Füllfarbe für Schaltflächen <br> Farbe für Filterbereich und Hintergrund verfügbarer Filterkarten |
| **secondaryBackground** <br> **backgroundNeutral** (veraltet) | Tabellen- und Matrixraster-Konturenfarbe <br> Standardfarbe für Formenzuordnung <br> Menübanddiagramm-Füllfarbe (wenn Option „Serienfarbe abgleichen“ deaktiviert ist) <br> Wenn background != FFFFFF: <br> Deaktivierte Füllfarbe für Schaltflächen <br> Deaktivierte Konturfarbe für Schaltflächen <br> |
| **tableAccent** | Überschreibt die Tabellen- und Matrixraster-Konturfarbe, wenn vorhanden |

Im folgenden Beispieldesign werden die Farbklassen festlegt:

```json
{
    "name": "Custom Theme",
    "firstLevelElements": "#252423",
    "secondLevelElements": "#605E5C",
    "thirdLevelElements": "#F3F2F1",
    "fourthLevelElements": "#B3B0AD",
    "background": "#FFFFFF",
    "secondaryBackground": "#C8C6C4",
    "tableAccent": "#118DFF"
}
```

> [!TIP]
> Wenn Sie ein dunkles oder andere farbige Designs erstellen, die vom üblichen Stil eines schwarzen **firstLevelElements**- und einem weißem **background**-Elements abweichen, sollten Sie darauf achten, auch die Werte für andere Strukturfarben sowie die [Farben für die primären Textklassen](#setting-formatted-text-defaults) festzulegen.  So stellen Sie sicher, dass z. B. Datenbezeichnungen in Diagrammen, die einen Hintergrund haben, dem erwarteten Stil entsprechen und lesbar sind, und dass gleichzeitig die Achsengitternetzlinien sichtbar bleiben.

### <a name="setting-formatted-text-defaults"></a>Festlegen der Standardwerte für formatierten Text

Als Nächstes können Sie Ihrer JSON-Datei Textklassen hinzufügen. Textklassen ähneln Farbklassen, sind aber so konzipiert, dass Sie Schriftgrad, Farbe und Familie für Textgruppen im gesamten Bericht aktualisieren können.

Es gibt 12 Textklassen, aber Sie müssen nur vier Klassen festlegen, die als *primäre Klassen* bezeichnet werden, um die gesamte Textformatierung im Bericht zu ändern.  Diese vier primären Klassen können im [Dialogfeld **Design anpassen**](#create-and-customize-a-theme-in-power-bi-desktop) im Abschnitt „Text“ festgelegt werden: „Allgemein“ entspricht **Bezeichnung**, „Titel“ **Titel**, „Karten und KPIs“ **Legende** und „Registerkartentitel“ **Kopfzeile**.

Andere Textklassen, die als *sekundäre Klassen* gelten, erben ihre Eigenschaften automatisch von ihren entsprechenden primären Klassen bzw. die Eigenschaften werden davon abgeleitet. Häufig wählt eine sekundäre Klasse eine hellere Textfarbe oder eine prozentuell größere oder kleinere Schriftgröße als die primäre Klasse.

Nehmen wir die Klasse **label** als Beispiel. Die Standardformatierung für die **label**-Klasse ist Segoe UI, 252423 (eine dunkelgraue Farbe) und 12 Punkte. Diese Klasse wird verwendet, um die Werte in der Tabelle und Matrix zu formatieren. Meist haben die Summen in einer Tabelle oder Matrix eine ähnliche Formatierung, sind aber mit der Klasse **bold label** fett formatiert, damit sie auffallen. Sie müssen diese Klasse jedoch nicht in der JSON-Designdatei angeben, denn Power BI tut dies automatisch. Wenn Sie sich später entscheiden, Beschriftungen mit einer 14-Punkt-Schriftart in Ihrem Design festzulegen, müssen Sie die Klasse **bold label** nicht mehr aktualisieren, da sie die Textformatierung von der Klasse **label** erbt.

Die folgende Tabelle enthält die folgenden Informationen:

- Die vier primären Textklassen, was sie formatieren und ihre Standardeinstellungen
- Jede sekundäre Klasse, was sie formatiert und ihre Standardeinstellung, die im Vergleich zur primären Klasse eindeutig ist

|Primäre Klasse  |Sekundäre Klassen  |JSON-Klassenname  | Standardeinstellungen  |Zugeordnete visuelle Objekte  |
|---------|---------|---------|---------|---------|
| Legende | N/V | callout | DIN <br> 252423 <br> 45 pt |Kartendatenbeschriftungen <br> KPI-Indikatoren|
|Header|N/V|header|Segoe UI Semibold <br> 252423 <br> 12 pt |Kopfzeile für die wichtigsten Einflussfaktoren |
| Titel || title |DIN <br> 252423 <br> 12 pt |Titel der Kategorieachse <br> Titel der Wertachse <br> Titel der mehrzeiligen Karte * <br> Slicerkopfzeile|
|-| Großer Titel | largeTitle |14 pt |Visualtitel |
|Beschriftung ||label |Segoe UI<br>252423<br>10 pt |Tabellen- und Matrixspalten-Kopfzeile <br> Matrixzeilen-Kopfzeile<br>Tabellen- und Matrixraster<br>Tabellen- und Matrixwerte |
|-|Halbfett |semiboldLabel| Segoe UI Semibold | Profiltext für wichtige Einflussfaktoren
|-|Large |largeLabel |12 pt | Datenbeschriftungen für mehrzeilige Karte |
|-|Small |smallLabel |9 pt |Bezugslinienbeschriftungen * <br>Slicerdatumsbereichs-Beschriftungen<br> Textstil für numerische Slicereingabe<br>Slicersuchfeld<br>Text wichtiger Einflussfaktoren|
|-|Hell |lightLabel |605E5C |Legendentext<br>Schaltflächentext<br>Kategorieachsenbeschriftung<br>Trichterdiagramm-Datenbeschriftungen<br>Beschriftungen für Trichterdiagramm-Konvertierungsraten<br>Messgerätziel<br>Punktdiagramm-Kategoriebeschriftung<br>Slicerelemente|
|-|Fett |boldLabel |Segoe UI Bold |Matrixzwischensummen<br>Matrixgesamtsummen<br>Tabellensummen |
|-|Groß und dünn |largeLightLabel |605E5C<br>12 pt |Kartenkategoriebeschriftungen<br>Messgerätbeschriftungen<br>Kategoriebeschriftungen für mehrzeilige Karte |
|-|Klein und dünn |smallLightLabel |605E5C<br>9 pt |Datenbeschriftungen<br>Wertachsenbeschriftungen|

*\* Mit einem Asterisk versehene Elemente werden auch auf Grundlage der ersten Datenfarbe des Berichtsdesigns koloriert.*

> [!TIP]
> Die *helleren* Textklassen erhalten ihre helle Farbe von den oben definierten [Strukturfarben](#setting-structural-colors).  Wenn Sie ein dunkles Design erstellen, achten Sie darauf, auch die Farben „firstLevelElements“ (entsprechend der primären Textfarbe), „secondLevelElements“ (entsprechend der erwarteten hellen Textfarbe) und „background“ (mit ausreichend Kontrast zu den Farben der Elemente der ersten und zweiten Ebene) festzulegen.

Im folgenden Beispieldesign werden nur die primären Textklassen festlegt:

```json
{
    "name": "Custom Theme",
    "textClasses": {
        "callout": {
            "fontSize": 45,
            "fontFace": "DIN",
            "color": "#252423"
        },
        "title": {
            "fontSize": 12,
            "fontFace": "DIN",
            "color": "#252423"
        },
        "header": {
            "fontSize": 12,
            "fontFace": "Segoe UI Semibold",
            "color": "#252423"
        },
        "label": {
            "fontSize": 10,
            "fontFace": "Segoe UI",
            "color": "#252423"
        }
    }
}
```

Da sekundäre Klassen von den primären Klassen erben, müssen Sie sie nicht in der Designdatei festlegen. Aber wenn Ihnen die Vererbungsregeln nicht gefallen (weil Sie z. B. nicht möchten, dass Ihre Summenwerte in einer Tabelle fett formatiert sind), können Sie die sekundären Klassen ebenso wie die primären Klassen explizit in der Designdatei formatieren.

### <a name="setting-visual-property-defaults-visualstyles"></a>Festlegen der Standardwerte für Visualeigenschaften (`visualStyles`)

Um eine JSON-Datei in einem erweiterten Format zu erstellen, die eine detailliertere und präzisere Steuerung der gesamten Formatierung von Visuals in einem Bericht ermöglicht, können Sie der JSON-Datei schließlich den Abschnitt **visualStyles** hinzufügen, um Formatierungsangaben zu schachteln. Hier ein Beispiel des Abschnitts **visualStyles**:

```json
    "visualStyles": {
        "<visualName>": {
            "<styleName>": {
                "<cardName>": [{
                    "<propertyName>": <propertyValue>
                }]
            }
        }
    }
```

Verwenden Sie für die Abschnitte **visualName** und **cardName** einen spezifischen Visual- und Kartennamen. Derzeit ist **styleName** immer ein Sternchen (*), aber in einem künftigen Release können Sie unterschiedliche Formatvorlagen für Ihre Visuals erstellen und Ihnen Namen geben (ähnlich wie bei den Features Tabellenstil und Matrixformat). **propertyName** ist der Name der Formatierungsoption und **propertyValue** deren Wert.

Verwenden Sie für **visualName** und **cardName** ein Sternchen in Anführungszeichen, wenn Sie möchten, dass diese Einstellung für alle Visuals oder Karten gilt, die eine Eigenschaft haben. Wenn Sie ein Sternchen sowohl für den Visual- als auch für den Kartennamen verwenden, wenden Sie eine Einstellung global in Ihrem Bericht an, z. B. einen Schriftgrad oder eine bestimmte Schriftfamilie für alle Texte aller Visuals.

Im folgenden Beispiel werden einige Eigenschaften für alle Visualstile festgelegt:

```json
{
   "name":"Custom Theme",
   "visualStyles":{
      "*": {
         "*": {
            "*": [{
                "wordWrap": true
            }],
            "categoryAxis": [{
                "gridlineStyle": "dotted"
            }],
            "filterCard": [
              {
                "$id": "Applied",
                "foregroundColor": {"solid": {"color": "#252423" } }
              },
              {
                "$id":"Available",
                "border": true
              }
            ]
         }
      },
      "scatterChart": {
         "*": {
            "bubbles": [{
                  "bubbleSize": -10
            }]
         }
      }
   }
}
```

Dieses Beispiel legt die folgenden Einstellungen fest:

- Aktivieren des Zeilenumbruchs überall
- Festlegen des Gitternetzlinien-Stils auf „Gepunktet“ für alle Visuals mit einer Kategorieachse
- Festlegen einiger Formatierungen für die verfügbaren und angewendeten Filterkarten (beachten Sie, dass „$id“ verwendet wird, um die verschiedenen Versionen der Filterkarten festzulegen)
- Festlegen der Blasengröße für Punktdiagramme auf -10.

> [!NOTE]
> Sie müssen nur die Formatierungselemente angeben, die Sie anpassen möchten. Für alle Formatierungselemente, die nicht in der JSON-Datei enthalten sind, werden die Standardwerte und -einstellungen verwendet.

### <a name="visualstyles-definition-list"></a>Definitionsliste für `visualStyles`

In den Tabellen in diesem Abschnitt werden Visualnamen (**visualName**), Kartennamen (**cardName**), Eigenschaftennamen (**propertyName**) und die zum Erstellen der JSON-Datei erforderlichen Enumerationen definiert.

| Werte für visualName |
| --- |
| areaChart |
| barChart |
| basicShape |
| card |
| clusteredBarChart |
| clusteredColumnChart |
| columnChart |
| comboChart |
| donutChart |
| filledMap |
| Trichter |
| Tachometerdiagramm |
| hundredPercentStackedBarChart |
| hundredPercentStackedColumnChart |
| image |
| KPI |
| lineChart |
| lineClusteredColumnComboChart |
| lineStackedColumnComboChart |
| Karte |
| multiRowCard |
| pieChart |
| pivotTable |
| ribbonChart |
| scatterChart |
| shapeMap |
| Datenschnitt |
| stackedAreaChart |
| tableEx |
| Treemap |
| waterfallChart |

In der folgenden Tabelle sind die Werte von **cardName** definiert. Der erste Wert in jeder Zelle ist die Benennung der JSON-Datei. Der zweite Wert ist der Name der Karte, der auf der Benutzeroberfläche von Power BI Desktop angezeigt wird.

| Werte für cardName |
| --- |
| axis: Messachse |
| breakdown: Aufschlüsselung |
| bubbles: Blasen |
| calloutValue: Beschriftungswert |
| card: Karte |
| cardTitle: Kartentitel |
| categoryAxis: X-Achse |
| categoryLabels: Kategoriebeschriftungen |
| columnFormatting: Feldformatierung |
| columnHeaders: Spaltenüberschriften |
| dataLabels: Datenbeschriftungen |
| fill: Füllung |
| fillPoint: Füllpunkt |
| forecast: Prognose- |
| general: Allgemein |
| goals: Ziele |
| grid: Raster |
| header: Header |
| imageScaling: Skalierung |
| indicator: Indikator |
| items: Elemente |
| labels: Datenbeschriftungen |
| legend: Legende |
| lineStyles: Formen |
| mapControls: Kartensteuerelemente |
| mapStyles: Kartenstile |
| numericInputStyle: Numerische Eingaben |
| percentBarLabel: Beschriftung für Konvertierungsrate |
| plotArea: Zeichnungsfläche |
| plotAreaShading: Symmetrieschattierung |
| ratioLine: Verhältnislinie |
| referenceLine: Bezugslinie |
| ribbonChart: Menübänder |
| rotation: Drehung |
| rowHeaders: Zeilenüberschriften |
| selection: Auswahlsteuerelemente |
| sentimentColors: Stimmungsfarben |
| shape: Formen |
| slider: Schieberegler |
| status: Farbcodierung |
| subTotals: Zwischensummen |
| target: Ziel |
| total: Gesamtsumme |
| trend: Trendlinie |
| trendline: Trendachse |
| valueAxis: Y-Achse |
| values: Werte |
| wordWrap: Zeilenumbruch |
| xAxisReferenceLine: Bezugslinie für X-Achse |
| y1AxisReferenceLine: Bezugslinie |
| zoom: Zoom |

### <a name="properties-within-each-card"></a>Eigenschaften in jeder Karte

Im folgenden Abschnitt werden die Eigenschaften in jeder Karte definiert. Auf den Kartennamen folgt jeder Eigenschaftsname. Für jede Eigenschaft der Name, der angezeigt wird, wenn der Formatierungsbereich angezeigt wird, eine Beschreibung der Funktionsweise der Formatierungsoption und der Typ der Formatierungsoption. Mit diesem Ansatz erfahren Sie, welche Art von Werten Sie in der Designdatei verwenden können.

Wenn Sie **dateTime** verwenden, muss das Datum ein ISO-Datum in einfachen Anführungszeichen sein, dem „datetime“ vorangestellt ist. Sehen Sie sich folgendes Beispiel an:

  "datetime'2011-10-05T14:48:00.000Z'"

Boolesche Werte sind entweder „true“ oder „false“. Zeichenfolgen müssen in doppelte Anführungszeichen eingeschlossen werden, wie in "dies ist eine Zeichenfolge". Zahlen stehen für den Wert selbst, nicht in Anführungszeichen.

Farben verwenden das folgende Format, wobei Ihr benutzerdefinierter Hexadezimalcode im folgenden Beispiel „FFFFFF“ ersetzt:

    { "solid": { "color": "#FFFFFF" } }

Für eine Enumeration, die am häufigsten für Dropdownformatierungsoptionen verwendet wird, kann jede der im Bereich angezeigten Optionen festgelegt werden, z. B. „RightCenter“ für die Legendenposition oder „Datenwert, Prozent des Gesamtwerts“ für die Beschriftung von Kreisdiagrammdaten. Die Enumerationsoptionen werden unterhalb der Eigenschaftenliste angezeigt.

```json
{
      "general":{
        "responsive": {
          "type": [
            "bool"
          ],
          "displayName": [
            "(Preview) Responsive"
          ],
          "description": [
            "The visual will adapt to size changes"
          ]
        },
        "legend": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select the location for the legend"
          ]
        },
        "showTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Display a title for legend symbols"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "categoryAxis": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "axisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "start": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "end": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "axisType": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Type"
          ]
        },
        "showAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the X-axis",
            "Title for the Y-axis"
          ]
        },
        "axisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "concatenateLabels": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Concatenate labels"
          ],
          "description": [
            "Always concatenate levels of the hierarchy instead of drawing the hierarchy."
          ]
        },
        "preferredCategoryWidth": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Minimum category width"
          ]
        },
        "titleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "titleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "titleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "duration": {
          "type": [
            "numeric"
          ]
        }
      },
      "valueAxis": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "axisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "start": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "end": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "showAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the Y-axis",
            "Title for the X-axis"
          ]
        },
        "axisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "titleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "titleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "titleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        },
        "axisLabel": {
          "type": [
            "none"
          ],
          "displayName": [
            "Y-Axis (Column)"
          ]
        },
        "secShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show secondary"
          ]
        },
        "alignZeros": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Align zeros"
          ],
          "description": [
            "Align the zero tick marks for both value axes"
          ]
        },
        "secAxisLabel": {
          "type": [
            "none"
          ],
          "displayName": [
            "Y-Axis (Line)"
          ]
        },
        "secPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "secAxisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "secStart": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "secEnd": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "secShowAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the Y-axis"
          ]
        },
        "secAxisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "secLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "secFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "secFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "secLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "secLabelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "secTitleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "secTitleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "secTitleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        }
      },
      "dataPoint": {
        "defaultColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Default color",
            "Default Column Color"
          ]
        },
        "fill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Fill"
          ]
        },
        "defaultCategoryColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Default color",
            "Default Column Color"
          ]
        },
        "showAllDataPoints": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show all"
          ]
        }
      },
      "labels": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "showSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "showAll": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Customize series"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "labelDensity": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Label density"
          ]
        },
        "labelOrientation": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Orientation"
          ]
        },
        "labelPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ]
        },
        "percentageLabelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "% decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the percentages"
          ]
        },
        "labelStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Label style"
          ]
        }
      },
      "lineStyles": {
        "strokeWidth": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Stroke width"
          ]
        },
        "strokeLineJoin": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Join type"
          ]
        },
        "lineStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "showMarker": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show marker"
          ]
        },
        "markerShape": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Marker shape"
          ]
        },
        "markerSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Marker size"
          ]
        },
        "markerColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Marker color"
          ]
        },
        "showSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Customize series",
            "Show"
          ]
        },
        "shadeArea": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Shade area"
          ]
        }
      },
      "plotArea": {
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "trend": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set trend line name"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set trend line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for trend line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ],
          "description": [
            "Set trend line style"
          ]
        },
        "combineSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Combine Series"
          ],
          "description": [
            "Show one trend line per series or combine"
          ]
        }
      },
      "y1AxisReferenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "referenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set reference line name"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "line": {
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        },
        "weight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Weight"
          ]
        },
        "roundEdge": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Round edges"
          ]
        }
      },
      "fill": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "fillColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Fill color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "rotation": {
        "angle": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Rotation"
          ]
        }
      },
      "categoryLabels": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "wordWrap": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "dataLabels": {
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "cardTitle": {
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "card": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "outlineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Outline color"
          ],
          "description": [
            "Color of the outline"
          ]
        },
        "outlineWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Outline weight"
          ],
          "description": [
            "Thickness of the outline in pixels"
          ]
        },
        "barShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show bar"
          ],
          "description": [
            "Display a bar to the left side of the card as an accent"
          ]
        },
        "barColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Bar color"
          ]
        },
        "barWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Bar thickness"
          ],
          "description": [
            "Thickness of the bar in pixels"
          ]
        },
        "cardPadding": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Padding"
          ],
          "description": [
            "Background"
          ]
        },
        "cardBackground": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        }
      },
      "percentBarLabel": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "axis": {
        "min": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Min"
          ]
        },
        "max": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Max"
          ]
        },
        "target": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Target"
          ]
        }
      },
      "target": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "calloutValue": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        }
      },
      "forecast": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set forecast name"
          ]
        },
        "confidenceBandStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Confidence band style"
          ],
          "description": [
            "Set forecast confidence band style"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set forecast line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "transform": {
          "type": [
            "queryTransform"
          ]
        }
      },
      "bubbles": {
        "bubbleSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Size"
          ]
        }
      },
      "mapControls": {
        "autoZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto zoom"
          ]
        },
        "zoomLevel": {
          "type": [
            "numeric"
          ]
        },
        "centerLatitude": {
          "type": [
            "numeric"
          ]
        },
        "centerLongitude": {
          "type": [
            "numeric"
          ]
        }
      },
      "mapStyles": {
        "mapTheme": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Theme"
          ]
        }
      },
      "shape": {
        "map": {
          "type": [
            "geoJson"
          ]
        },
        "projectionEnum": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Projection"
          ],
          "description": [
            "Projection"
          ]
        }
      },
      "zoom": {
        "autoZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto zoom"
          ],
          "description": [
            "Zoom in on shapes with available data"
          ]
        },
        "selectionZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Selection zoom"
          ],
          "description": [
            "Zoom in on selected shapes"
          ]
        },
        "manualZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Manual zoom"
          ],
          "description": [
            "Allow user to zoom and pan"
          ]
        }
      },
      "xAxisReferenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "fillPoint": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "colorByCategory": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "plotAreaShading": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "upperShadingColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Upper shading"
          ],
          "description": [
            "Shading color of the upper region"
          ]
        },
        "lowerShadingColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Lower shading"
          ],
          "description": [
            "Shading color of the lower region"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "ratioLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        }
      },
      "grid": {
        "outlineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Outline color"
          ],
          "description": [
            "Color of the outline"
          ]
        },
        "outlineWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Outline weight"
          ],
          "description": [
            "Thickness of the outline in pixels"
          ]
        },
        "gridVertical": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Vert grid"
          ],
          "description": [
            "Show/Hide the vertical gridlines"
          ]
        },
        "gridVerticalColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Vert grid color"
          ],
          "description": [
            "Color for the vertical gridlines"
          ]
        },
        "gridVerticalWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Vert grid thickness"
          ],
          "description": [
            "Thickness of the vertical gridlines in pixels"
          ]
        },
        "gridHorizontal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Horiz grid"
          ],
          "description": [
            "Show/Hide the horizontal gridlines"
          ]
        },
        "gridHorizontalColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Horiz grid color"
          ],
          "description": [
            "Color for the horizontal gridlines"
          ]
        },
        "gridHorizontalWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Horiz grid thickness"
          ],
          "description": [
            "Thickness of the horizontal gridlines in pixels"
          ]
        },
        "rowPadding": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Row padding"
          ],
          "description": [
            "Padding in pixels applied to top and bottom of every row"
          ]
        },
        "imageHeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Image height"
          ],
          "description": [
            "The height of images in pixels"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "columnHeaders": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "autoSizeColumnWidth": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto-size column width"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        }
      },
      "values": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color scales"
          ]
        },
        "fontColorPrimary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the odd rows"
          ]
        },
        "backColorPrimary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the odd rows"
          ]
        },
        "fontColorSecondary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Alternate font color"
          ],
          "description": [
            "Font color of the even rows"
          ]
        },
        "backColorSecondary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Alternate background color"
          ],
          "description": [
            "Background color of the even rows"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "bandedRowHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Banded row style"
          ],
          "description": [
            "Apply banded row style to the last level of the row group headers, using the colors of the values."
          ]
        },
        "valuesOnRow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show on rows"
          ],
          "description": [
            "Show values in row groups rather than columns"
          ]
        }
      },
      "total": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "applyToHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Apply to labels"
          ]
        },
        "totals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Totals"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "columnFormatting": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "styleHeader": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color header"
          ]
        },
        "styleValues": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color values"
          ]
        },
        "styleTotal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color total"
          ]
        },
        "styleSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color subtotals"
          ]
        }
      },
      "rowHeaders": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "stepped": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Stepped layout"
          ],
          "description": [
            "Render row headers with stepped layout"
          ]
        },
        "steppedLayoutIndentation": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Stepped layout indentation"
          ],
          "description": [
            "Set the indentation, in pixels, applied to row headers"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        }
      },
      "subTotals": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "rowSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Total row"
          ]
        },
        "columnSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Total column"
          ]
        },
        "applyToHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Apply to labels"
          ]
        }
      },
      "selection": {
        "selectAllCheckboxEnabled": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Select All"
          ]
        },
        "singleSelect": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Single Select"
          ]
        }
      },
      "header": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        },
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "items": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        },
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "numericInputStyle": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        }
      },
      "slider": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        }
      },
      "dateRange": {
        "includeToday": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Include today"
          ]
        }
      },
      "sentimentColors": {
        "increaseFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Increase"
          ]
        },
        "decreaseFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Decrease"
          ]
        },
        "totalFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Total"
          ]
        },
        "otherFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Other"
          ]
        }
      },
      "breakdown": {
        "maxBreakdowns": {
          "type": [
            "integer"
          ],
          "displayName": [
            "Max breakdowns"
          ],
          "description": [
            "The number of individual breakdowns to show (rest grouped into Other)"
          ]
        }
      },
      "indicator": {
        "indicatorDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "indicatorPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "kpiFormat": {
          "type": [
            "text"
          ],
          "displayName": [
            "Format"
          ]
        }
      },
      "trendline": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "goals": {
        "showGoal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Goal"
          ]
        },
        "showDistance": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Distance"
          ]
        }
      },
      "status": {
        "direction": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Direction"
          ]
        },
        "goodColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Good Color"
          ]
        },
        "neutralColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Neutral Color"
          ]
        },
        "badColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Bad Color"
          ]
        }
      }
```



### <a name="enumerations-in-the-json-file"></a>Enumerationen in der JSON-Datei
Im folgenden Abschnitt werden die Enumerationen definiert, die Sie in der JSON-Datei verwenden können.

```json
    {
        "legend": {
            "position": [
                {
                    "value": "Top",
                    "displayName": "Top"
                },
                {
                    "value": "Bottom",
                    "displayName": "Bottom"
                },
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                },
                {
                    "value": "TopCenter",
                    "displayName": "Top Center"
                },
                {
                    "value": "BottomCenter",
                    "displayName": "Bottom Center"
                },
                {
                    "value": "LeftCenter",
                    "displayName": "Left Center"
                },
                {
                    "value": "RightCenter",
                    "displayName": "Right center"
                }
            ],
            "legendMarkerRendering": [
                {
                    "value": "markerOnly",
                    "displayName": "Markers only"
                },
                {
                    "value": "lineAndMarker",
                    "displayName": "Line and markers"
                },
                {
                    "value": "lineOnly",
                    "displayName": "Line only"
                }
            ]
        },
        "categoryAxis": {
            "axisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "axisType": [
                {
                    "value": "Scalar",
                    "displayName": "Continuous"
                },
                {
                    "value": "Categorical",
                    "displayName": "Categorical"
                }
            ],
            "axisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ],
            "gridlineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "position": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ]
        },
        "valueAxis": {
            "position": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ],
            "axisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "axisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ],
            "gridlineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "secPosition": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ],
            "secAxisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "secAxisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ]
        },
        "lineStyles": {
            "strokeLineJoin": [
                {
                    "value": "miter",
                    "displayName": "Miter"
                },
                {
                    "value": "round",
                    "displayName": "Round"
                },
                {
                    "value": "bevel",
                    "displayName": "Bevel"
                }
            ],
            "lineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "markerShape": [
                {
                    "value": "circle",
                    "displayName": "●"
                },
                {
                    "value": "square",
                    "displayName": "■"
                },
                {
                    "value": "diamond",
                    "displayName": "◆"
                },
                {
                    "value": "triangle",
                    "displayName": "▲"
                },
                {
                    "value": "x",
                    "displayName": "☓"
                },
                {
                    "value": "shortDash",
                    "displayName": " -"
                },
                {
                    "value": "longDash",
                    "displayName": "—"
                },
                {
                    "value": "plus",
                    "displayName": "+"
                }
            ]
        },
        "trend": {
            "style": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
            }
        ]
    },
    "y1AxisReferenceLine": {
        "style": [
            {
                "value": "dashed",
                "displayName": "Dashed"
            },
            {
                "value": "solid",
                "displayName": "Solid"
            },
            {
                "value": "dotted",
                "displayName": "Dotted"
            }
        ],
        "position": [
            {
                "value": "back",
                "displayName": "Behind"
            },
            {
                "value": "front",
                "displayName": "In Front"
            }
        ],
        "dataLabelText": [
            {
                "value": "Value",
                "displayName": "Value"
            },
            {
                "value": "Name",
                "displayName": "Name"
            },
            {
                "value": "ValueAndName",
                "displayName": "Name and Value"
            }
        ],
        "dataLabelHorizontalPosition": [
            {
                "value": "left",
                "displayName": "Left"
            },
            {
                "value": "right",
                "displayName": "Right"
            }
        ],
        "dataLabelVerticalPosition": [
            {
                "value": "above",
                "displayName": "Above"
            },
            {
                "value": "under",
                "displayName": "Under"
            }
        ]
    },
    "referenceLine": {
        "style": [
            {
                "value": "dashed",
                "displayName": "Dashed"
            },
            {
                "value": "solid",
                "displayName": "Solid"
            },
            {
                "value": "dotted",
                "displayName": "Dotted"
            }
        ],
        "position": [
            {
                "value": "back",
                "displayName": "Behind"
            },
            {
                "value": "front",
                "displayName": "In Front"
            }
        ],
        "dataLabelText": [
      {
        "value": "Value",
        "displayName": "Value"
      },
      {
        "value": "Name",
        "displayName": "Name"
      },
      {
        "value": "ValueAndName",
        "displayName": "Name and Value"
      }
    ],
    "dataLabelHorizontalPosition": [
      {
        "value": "left",
        "displayName": "Left"
      },
      {
        "value": "right",
        "displayName": "Right"
      }
    ],
    "dataLabelVerticalPosition": [
      {
        "value": "above",
        "displayName": "Above"
      },
      {
        "value": "under",
        "displayName": "Under"
      }
    ]
    },
    "labels": {
    "labelOrientation": [
      {
        "value": "vertical",
        "displayName": "Vertical"
      },
      {
        "value": "horizontal",
        "displayName": "Horizontal"
      }
    ],
    "labelPosition": [
      {
        "value": "Auto",
        "displayName": "Auto"
      },
      {
        "value": "InsideEnd",
        "displayName": "Inside End"
      },
      {
        "value": "OutsideEnd",
        "displayName": "Outside End"
      },
      {
        "value": "InsideCenter",
        "displayName": "Inside Center"
      },
      {
        "value": "InsideBase",
        "displayName": "Inside Base"
      }
    ],
    "labelStyle": [
      {
        "value": "Category",
        "displayName": "Category"
      },
      {
        "value": "Data",
        "displayName": "Data value"
      },
      {
        "value": "Percent of total",
        "displayName": "Percent of total"
      },
      {
        "value": "Both",
        "displayName": "Category, data value"
      },
      {
        "value": "Category, percent of total",
        "displayName": "Category, percent of total"
      },
      {
        "value": "Data value, percent of total",
        "displayName": "Data value, percent of total"
      },
      {
        "value": "Category, data value, percent of total",
        "displayName": "All detail labels"
      }
     ]
    },
    "card": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
         ]
    },
    "imageScaling": {
        "imageScalingType": [
          {
            "value": "Normal",
            "displayName": "Normal"
          },
          {
            "value": "Fit",
            "displayName": "Fit"
          },
          {
            "value": "Fill",
            "displayName": "Fill"
          }
        ]
    },
    "forecast": {
        "confidenceBandStyle": [
          {
            "value": "fill",
            "displayName": "Fill"
          },
          {
            "value": "line",
            "displayName": "Line"
          },
          {
            "value": "none",
            "displayName": "None"
          }
        ],
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ]
        },
        "mapStyles": {
        "mapTheme": [
          {
            "value": "aerial",
            "displayName": "Aerial"
          },
          {
            "value": "canvasDark",
            "displayName": "Dark"
          },
          {
            "value": "canvasLight",
            "displayName": "Light"
          },
          {
            "value": "grayscale",
            "displayName": "Grayscale"
          },
          {
            "value": "road",
            "displayName": "Road"
          }
        ]
    },
    "shape": {
        "projectionEnum": [
          {
            "value": "albersUsa",
            "displayName": "Albers USA"
          },
          {
            "value": "equirectangular",
            "displayName": "Equirectangular"
          },
          {
            "value": "mercator",
            "displayName": "Mercator"
          },
          {
            "value": "orthographic",
            "displayName": "Orthographic"
          }
        ]
        },
        "xAxisReferenceLine": {
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ],
        "position": [
          {
            "value": "back",
            "displayName": "Behind"
          },
          {
            "value": "front",
            "displayName": "In Front"
          }
        ],
        "dataLabelText": [
          {
            "value": "Value",
            "displayName": "Value"
          },
          {
            "value": "Name",
            "displayName": "Name"
          },
          {
            "value": "ValueAndName",
            "displayName": "Name and Value"
          }
        ],
        "dataLabelHorizontalPosition": [
          {
            "value": "left",
            "displayName": "Left"
          },
          {
            "value": "right",
            "displayName": "Right"
          }
        ],
        "dataLabelVerticalPosition": [
          {
            "value": "above",
            "displayName": "Above"
          },
          {
            "value": "under",
            "displayName": "Under"
          }
        ]
        },
        "ratioLine": {
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ]
        },
        "columnHeaders": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "values": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "total": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "rowHeaders": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "subTotals": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ],
        "rowSubtotalsPosition": [
          {
            "value": "Top",
            "displayName": "Top"
          },
          {
            "value": "Bottom",
            "displayName": "Bottom"
          }
        ]
        },
        "general": {
        "orientation": [
          {
            "value": "vertical",
            "displayName": "Vertical"
          },
          {
            "value": "horizontal",
            "displayName": "Horizontal"
          }
        ]
        },
        "data": {
        "relativeRange": [
          {
            "value": "Last",
            "displayName": "Last"
          },
          {
            "value": "Next",
            "displayName": "Next"
          },
          {
            "value": "This",
            "displayName": "This"
          }
        ],
        "relativePeriod": [
          {
            "value": "None",
            "displayName": "Select"
          },
          {
            "value": "Days",
            "displayName": "Days"
          },
          {
            "value": "Weeks",
            "displayName": "Weeks"
          },
          {
            "value": "Calendar Weeks",
            "displayName": "Weeks (Calendar)"
          },
          {
            "value": "Months",
            "displayName": "Months"
          },
          {
            "value": "Calendar Months",
            "displayName": "Months (Calendar)"
          },
          {
            "value": "Years",
            "displayName": "Years"
          },
          {
            "value": "Calendar Years",
            "displayName": "Years (Calendar)"
          }
        ],
        "mode": [
          {
            "value": "Between",
            "displayName": "Between"
          },
          {
            "value": "Before",
            "displayName": "Before"
          },
          {
            "value": "After",
            "displayName": "After"
          },
          {
            "value": "Basic",
            "displayName": "List"
          },
          {
            "value": "Dropdown",
            "displayName": "Dropdown"
          },
          {
            "value": "Relative",
            "displayName": "Relative"
          },
          {
            "value": "Single",
            "displayName": "Single Value"
          }
        ]
        },
        "header": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "items": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "status": {
        "direction": [
          {
            "value": "Positive",
            "displayName": "High is good"
          },
          {
            "value": "Negative",
            "displayName": "Low is good"
          }
         ]
       }
    }
  }
}
```

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Wenn Sie eines der ursprünglichen Designs verwenden, z. B. das klassische Design oder ein benutzerdefiniertes, das Sie zusätzlich importiert haben, ist der Textabschnitt des Designdialogfelds nicht konfigurierbar.

Integrierte Designs, die von dieser Einschränkung betroffen sind, sind z. B. die folgenden:
* Klassisch
* Stadtpark
* Klassenzimmer
* Geeignet bei Farbenblindheit
* Elektrisch
* Hoher Kontrast
* Sonnenuntergang
* Dämmerung

Wenn Sie eines der betroffenen Designs verwenden und die Texteinstellungen nicht ändern müssen, können Sie problemlos die anderen Registerkarten des Dialogfelds verwenden. Wenn Sie die Textklassen jedoch in einem der betroffenen Designs verwenden möchten, haben Sie einige Optionen:

- Die Textklassen lassen sich am schnellsten und einfachsten aktivieren, indem Sie die Optionen für das Standarddesign auswählen.
- Wenn Sie das aktuelle benutzerdefinierte Design beibehalten möchten, müssen Sie Folgendes tun, um die Textregisterkarte zu aktivieren:
  1. Exportieren Sie Ihr aktuelles Design.
  1. Wählen Sie das Standarddesign aus.
  1. Importieren Sie das benutzerdefinierte Design, das Sie im ersten Schritt exportiert haben.

Der Text in Ihrem Bericht wird zwar anders aussehen, aber Sie können im Designdialogfeld auf die Registerkarte „Text“ zugreifen.


