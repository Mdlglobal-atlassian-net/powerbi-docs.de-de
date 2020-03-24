---
title: Einführung in die Verwendung von Farbhilfsprogrammen in Power BI-Visuals
description: In diesem Artikel erfahren Sie, wie Farbhilfsprogramme das Anwenden von Designs und Paletten auf die Datenpunkte in Power BI-Visuals vereinfachen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 8de530871739a18c1afc72cee3e0da5fc70ebb16
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379350"
---
# <a name="color-utils"></a>Farbhilfsprogramme
Dieser Artikel unterstützt Sie beim Installieren, Importieren und Verwenden von Farbhilfsprogrammen (ColorUtils). In diesem Artikel erfahren Sie, wie Farbhilfsprogramme das Anwenden von Designs und Paletten auf die Datenpunkte in Power BI-Visuals vereinfachen.

## <a name="requirements"></a>Anforderungen
Zur Verwendung des Pakets benötigen Sie Folgendes:
* [node.js](https://nodejs.org) (die aktuelle LTS-Version wird empfohlen)
* [npm](https://www.npmjs.com/) (die unterstützte Mindestversion ist 3.0.0)
* Das mit [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) erstellte benutzerdefinierte Visual

## <a name="installation"></a>Installation

Führen Sie den folgenden Befehl im Verzeichnis mit Ihrem aktuellen Visual aus, um das Paket zu installieren:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Dieser Befehl installiert das Paket und fügt Ihrer ```package.json```-Datei ein Paket als Abhängigkeit hinzu.

## <a name="usage"></a>Verwendung

Wenn Sie Interaktivitätshilfsprogramme verwenden möchten, müssen Sie die erforderliche Komponente in den Quellcode des Visuals importieren.
```typescript
import { ColorHelper } from "powerbi-visuals-utils-colorutils";
```

Hier erfahren Sie, wie Sie Farbhilfsprogramme in Ihren Power BI-Visuals installieren und verwenden:

* [Nutzungsanleitung] In der Nutzungsanleitung wird eine öffentliche API des Pakets beschrieben. Hier finden Sie eine Beschreibung sowie Beispiele für jede öffentliche Schnittstelle des Pakets.

Dieses Paket enthält die folgenden Klassen und Module:
* [ColorHelper](#colorhelper): dient zum Generieren verschiedener Farben für die Diagrammwerte
* [colorUtils](#colorutils): dient zum Konvertieren von Farbformaten

## `ColorHelper`
Die `ColorHelper`-Klasse enthält die folgenden Funktionen und Methoden:

### `getColorForSeriesValue` 
Diese Methode ruft die Farbe für den angegebenen Reihenwert ab. Wenn keine explizite oder Standardfarbe festgelegt wurde, wird die Farbe dieser Reihe aus der Farbskala zugeordnet.
```typescript
getColorForSeriesValue(objects: IDataViewObjects, value: PrimitiveValue, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Beispiel
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;

import DataViewValueColumns = powerbi.DataViewValueColumns;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;

import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const valueColumns: DataViewValueColumns = visualUpdateOptions.dataViews[0].categorical.values,
            grouped: DataViewValueColumnGroup[] = valueColumns.grouped(),
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        for (let i = 0; i < grouped.length; i++) {
            let grouping: DataViewValueColumnGroup = grouped[i];

            let color = colorHelper.getColorForSeriesValue(grouping.objects, grouping.name); // returns a color of the series
        }
    }
}
```

### `getColorForMeasure`
Diese Methode ruft die Farbe für das angegebene Measure ab.
```typescript
 getColorForMeasure(objects: IDataViewObjects, measureKey: any, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Beispiel
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;
import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const objects: DataViewObjects = visualUpdateOptions.dataViews[0].categorical.categories[0].objects[0],
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        let color = colorHelper.getColorForMeasure(objects, ""); // returns a color
    }
}
```

### <a name="static-normalizeselector"></a>statischer `normalizeSelector`
Diese Methode gibt den normalisierten Selektor zurück.
```typescript
static normalizeSelector(selector: Selector, isSingleSeries?: boolean): Selector;
```
#### <a name="example"></a>Beispiel
```typescript
import ISelectionId = powerbi.visuals.ISelectionId;
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

let selectionId: ISelectionId = ...;
let selector = ColorHelper.normalizeSelector(selectionId.getSelector(), false);
```

Die Methoden `getThemeColor` und `getHighContrastColor` sind mit Farbdesignfarben verknüpft.
Außerdem bietet `ColorHelper` die Eigenschaft `isHighContrast`, die für die Überprüfung nützlich sein sollte.

### `getThemeColor`
Diese Methode gibt die Designfarbe zurück.
```typescript
 getThemeColor(themeColorName?: ThemeColorName): string;
```
### `getHighContrastColor`
 Diese Methode gibt die Farbe für den kontrastreichen Modus zurück.
```typescript
getHighContrastColor(themeColorName?: ThemeColorName, defaultColor?: string): string;
```
#### <a name="example-related-to-high-contrast-mode-usage"></a>Beispiel für die Verwendung des kontrastreichen Modus:
```typescript

import { ColorHelper } from "powerbi-visuals-utils-colorutils";

export class MyVisual implements IVisual {
        private colorHelper: ColorHelper;

        private init(options: VisualConstructorOptions): void {
            this.colors = options.host.colorPalette;
            this.colorHelper = new ColorHelper(this.colors);
        } 

            private createViewport(element: HTMLElement): void {
                const fontColor: string = "#131aea";
                const axisBackgroundColor: string = this.colorHelper.getThemeColor();
                
                // some d3 code before
                d3ElementName.attr("fill", colorHelper.getHighContrastColor("foreground", fontColor);
            }
                
            public static parseSettings(dataView: DataView, colorHelper: ColorHelper): VisualSettings {
                // some code that should be applied on formatting settings
                if (colorHelper.isHighContrast) {
                        this.settings.fontColor = colorHelper.getHighContrastColor("foreground", this.settings.fontColor);
                    }
            }
}
```


## `ColorUtils`
 Das Modul stellt die folgenden Funktionen zur Verfügung:

* [hexToRGBString](#hextorgbstring)
* [rotate](#rotate)
* [parseColorString](#parsecolorstring)
* [calculateHighlightColor](#calculatehighlightcolor)
* [createLinearColorScale](#createlinearcolorscale)
* [shadeColor](#shadecolor)
* [rgbBlend](#rgbblend)
* [channelBlend](#channelblend)
* [rgbBlend](#hexblend)

### <a name="hextorgbstring"></a>hexToRGBString
Konvertiert Hexadezimalfarbe in RGB-Zeichenfolge.

```typescript
function hexToRGBString(hex: string, transparency?: number): string
```

#### <a name="example"></a>Beispiel

```typescript
import  { hexToRGBString } from "powerbi-visuals-utils-colorutils";

hexToRGBString('#112233');

// returns: "rgb(17,34,51)"
```

### <a name="rotate"></a>rotate
Rotiert die RGB-Farbe.

```typescript
function rotate(rgbString: string, rotateFactor: number): string
```

#### <a name="example"></a>Beispiel

```typescript
import { rotate } from "powerbi-visuals-utils-colorutils";

rotate("#CC0000", 0.25); // returns: #66CC00
```

### <a name="parsecolorstring"></a>parseColorString
Analysiert eine beliebige Farbzeichenfolge in das RGB-Format.

```typescript
function parseColorString(color: string): RgbColor
```

#### <a name="example"></a>Beispiel

```typescript
import { parseColorString } from "powerbi-visuals-utils-colorutils";

parseColorString('#09f');
// returns: {R: 0, G: 153, B: 255 }

parseColorString('rgba(1, 2, 3, 1.0)');
// returns: {R: 1, G: 2, B: 3, A: 1.0 }
```

### <a name="calculatehighlightcolor"></a>calculateHighlightColor
Berechnen Sie die Hervorhebungsfarbe aus rgbColor basierend auf lumianceThreshold und Delta.

```typescript
function calculateHighlightColor(rgbColor: RgbColor, lumianceThreshold: number, delta: number): string
```

#### <a name="example"></a>Beispiel

```typescript
import { calculateHighlightColor } from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    yellowRGB = parseColorString(yellow);

calculateHighlightColor(yellowRGB, 0.8, 0.2);

// returns: '#CCCC00'
```

### <a name="createlinearcolorscale"></a>createLinearColorScale
Gibt für den angegebenen Zahlenbereich eine lineare Farbskala zurück.

```typescript
function createLinearColorScale(domain: number[], range: string[], clamp: boolean): LinearColorScale
```

#### <a name="example"></a>Beispiel

```typescript
import { createLinearColorScale } from "powerbi-visuals-utils-colorutils";

let scale = ColorUtility.createLinearColorScale(
    [0, 1, 2, 3, 4],
    ["red", "green", "blue", "black", "yellow"],
    true);

scale(1); // returns: green
scale(10); // returns: yellow
```

### <a name="shadecolor"></a>shadeColor
Konvertiert den hexadezimalen Zeichenfolgenausdruck in eine Zahl und berechnet Prozentsatz sowie R-, G-, B-Kanäle.
Wendet den Prozentsatz für jeden Kanal an und gibt den hexadezimalen Wert als Zeichenfolge mit Nummernzeichen zurück.

```typescript
function shadeColor(color: string, percent: number): string
```

#### <a name="example"></a>Beispiel

```typescript
import { shadeColor } from "powerbi-visuals-utils-colorutils";

shadeColor('#000000', 0.1); // returns '#1a1a1a'
shadeColor('#FFFFFF', -0.5); // returns '#808080'
shadeColor('#00B8AA', -0.25); // returns '#008a80'
shadeColor('#00B8AA', 0); // returns '#00b8aa'
```

### <a name="rgbblend"></a>rgbBlend
Überlagert eine Farbe mit Deckkraft über einer Hintergrundfarbe. Alphakanäle werden ignoriert.

```typescript
function rgbBlend(foreColor: RgbColor, opacity: number, backColor: RgbColor): RgbColor
```

#### <a name="example"></a>Beispiel

```typescript
import { rgbBlend} from "powerbi-visuals-utils-colorutils";

rgbBlend({R: 100, G: 100, B: 100}, 0.5, {R: 200, G: 200, B: 200});

// returns: {R: 150, G: 150, B: 150}
```

### <a name="channelblend"></a>channelBlend
Mischt einen einzelnen Kanal für zwei Farben.

```typescript
function channelBlend(foreChannel: number, opacity: number, backChannel: number): number
```

#### <a name="example"></a>Beispiel

```typescript
import { channelBlend} from "powerbi-visuals-utils-colorutils";

channelBlend(0, 1, 255); // returns: 0
channelBlend(128, 1, 255); // returns: 128
channelBlend(255, 0, 0); // returns: 0
channelBlend(88, 0, 88); // returns: 88
```

### <a name="hexblend"></a>hexBlend
Überlagert eine Farbe mit Deckkraft über einer Hintergrundfarbe.

```typescript
function hexBlend(foreColor: string, opacity: number, backColor: string): string
```

#### <a name="example"></a>Beispiel

```typescript
import { hexBlend} from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    black = "#000000",
    white = "#FFFFFF";

hexBlend(yellow, 0.5, white); // returns: "#FFFF80"
hexBlend(white, 0.5, yellow); // returns: "#FFFF80"

hexBlend(yellow, 0.5, black); // returns: "#808000"
hexBlend(black, 0.5, yellow); // returns: "#808000"
```