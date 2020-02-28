---
title: Struktur von Visualprojekten in Power BI
description: Dieser Artikel beschreibt die Ordner- und Dateistruktur eines Power BI-Visualprojekts.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 58c226fd66c2551565f85ee75bd06469a46c4128
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427068"
---
# <a name="power-bi-visual-project-structure"></a>Struktur von Visualprojekten in Power BI

Der einfachste Weg, ein neues Power BI-Visual zu erstellen, ist die Verwendung des Tools [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) für Power BI-Visuals.

Um ein neues Power BI-Visual zu erstellen, navigieren Sie zu dem Verzeichnis, in dem Sie das Visual speichern möchten, und führen Sie den folgenden Befehl aus:

`pbiviz new <visual project name>`

Dieser Befehl erstellt einen Ordner für Power BI-Visuals, der die folgenden Dateien enthält:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Beschreibung von Ordnern und Dateien

Diese Abschnitt stellt Informationen zu allen Ordnern und Dateien im Verzeichnis bereit, die vom **pbiviz**-Tool für Power BI-Visuals erstellt werden.  

### <a name="vscode"></a>.vscode

Dieser Ordner enthält die Einstellungen für das VS-Codeprojekt.

Bearbeiten Sie die Datei `.vscode/settings.json`, um Ihren Arbeitsbereich zu konfigurieren.

Weitere Informationen finden Sie unter [Benutzer- und Arbeitsbereichseinstellungen](https://code.visualstudio.com/docs/getstarted/settings).

### <a name="assets"></a>Assets

Dieser Ordner enthält die Datei `icon.png`.

Das Tool für Power BI-Visuals verwendet diese Datei als neues Power BI-Visualsymbol im Power BI-Visualisierungsbereich.

<!--- ![Visualization pane](./media/visualization-pane-analytics-tab.png) --->

### <a name="src"></a>src

Dieser Ordner enthält den Quellcode des Visuals.

In diesem Ordner erstellt das Tool für Power BI-Visuals die folgenden Dateien:
* `visual.ts`: Dies ist der Hauptquellcode des Visuals.
* `settings.ts`: Dies ist der Code für die Einstellungen des Visuals. Die Klassen in der Datei stellen eine Schnittstelle für die Definition der [Eigenschaften Ihres Visuals](./objects-properties.md#properties) bereit.

### <a name="style"></a>Format

Dieser Ordner enthält die Datei `visual.less`, in der sich die Formatvorlagen für das Visual befinden.

### <a name="capabilitiesjson"></a>capabilities.json

Diese Datei enthält die wichtigsten Eigenschaften und Einstellungen (oder [Funktionen](./capabilities.md)) für das Visual. Damit kann das Visual unterstützte Features, Objekte, Eigenschaften und [Zuordnungen von Datenansichten](./dataview-mappings.md) deklarieren.

### <a name="package-lockjson"></a>package-lock.json

Diese Datei wird automatisch für Vorgänge generiert, in denen *npm* entweder die `node_modules`-Struktur oder die Datei `package.json` ändert.

Weitere Informationen zu dieser Datei finden Sie in der offiziellen Dokumentation zu [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json).

### <a name="packagejson"></a>package.json

Diese Datei beschreibt das Projektpaket. Sie enthält Informationen zum Projekt, z. B. Autoren, Beschreibung und Abhängigkeiten des Projekts.

Weitere Informationen zu dieser Datei finden Sie in der offiziellen Dokumentation zu [npm-package.json](https://docs.npmjs.com/files/package.json.html).

### <a name="pbivizjson"></a>pbiviz.json

Diese Datei enthält die Metadaten des Visuals.

Eine `pbiviz.json`-Beispieldatei mit Kommentaren, die die Metadateneinträge beschreiben, finden Sie im Abschnitt [Metadateneinträge](#metadata-entries).

### <a name="tsconfigjson"></a>tsconfig.json

Eine Konfigurationsdatei für [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

Diese Datei muss den Pfad zur **\*.ts**-Datei enthalten, in der sich die Hauptklasse des Visuals befindet, wie in der `visualClassName`-Eigenschaft der Datei `pbiviz.json` angegeben.

### <a name="tslintjson"></a>tslint.json

Diese Datei enthält die [TSLint-Konfiguration](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Metadateneinträge

Die Kommentare im folgenden Code aus der Datei `pbiviz.json` beschreiben die Metadateneinträge.

> [!NOTE]
> * Ab Version 3.x.x des **pbiviz**-Tools wird `externalJS` nicht mehr unterstützt.
> * Um die Lokalisierung zu unterstützen, [fügen Sie Ihrem Visual das Power BI-Gebietsschema hinzu](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Nächste Schritte

* Informationen zu den Interaktionen zwischen einem Visual, einem Benutzer und Power BI finden Sie unter [Power BI-Visualkonzepte](./power-bi-visuals-concept.md).

* Entwickeln Sie eigene Power BI-Visuals anhand dieser [Schrittanleitung](./custom-visual-develop-tutorial.md) von Grund auf neu.
