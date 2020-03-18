---
title: Einführung in die Verwendung von Formatierungshilfsprogramme in Power BI-Visuals
description: Dieser Artikel beschreibt, wie Sie mithilfe von Formatierungshilfsprogrammen Werte formatieren und die Lokalisierung auf Werte in Power BI-Visuals anwenden können.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: dc2d036ab1e3e3dab551269163ced2f066a71626
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378022"
---
# <a name="formatting-utils"></a>Formatierungshilfsprogramme

Formatierungshilfsprogramme enthalten die Klassen, Schnittstellen und Methoden zur Formatierung von Werten. Sie enthalten auch Erweiterungsmethoden zur Verarbeitung von Zeichenfolgen und zur Messung der Textgröße in SVG- bzw. HTML-Dokumenten.

## <a name="text-measurement-service"></a>Textmessungsdienst

Das Modul stellt die folgenden Funktionen und Schnittstellen zur Verfügung:

### <a name="textproperties-interface"></a>TextProperties-Schnittstelle

Die Schnittstelle beschreibt die allgemeinen Eigenschaften des Texts.

```typescript
interface TextProperties {
    text?: string;
    fontFamily: string;
    fontSize: string;
    fontWeight?: string;
    fontStyle?: string;
    fontVariant?: string;
    whiteSpace?: string;
}
```

### <a name="measuresvgtextwidth"></a>measureSvgTextWidth

Die Funktion misst die Breite des Texts mit den angegebenen SVG-Texteigenschaften.

```typescript
function measureSvgTextWidth(textProperties: TextProperties, text?: string): number;
```

Beispiel für die Verwendung von `measureSvgTextWidth`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
import TextProperties = textMeasurementService.TextProperties;
// ...

let textProperties: TextProperties = {
    text: "Microsoft PowerBI",
    fontFamily: "sans-serif",
    fontSize: "24px"
};

textMeasurementService.measureSvgTextWidth(textProperties);

// returns: 194.71875
```

### <a name="measuresvgtextrect"></a>measureSvgTextRect

Diese Funktion gibt ein rect-Element mit den angegebenen SVG-Texteigenschaften zurück.

```typescript
function measureSvgTextRect(textProperties: TextProperties, text?: string): SVGRect;
```

Beispiel für die Verwendung von `measureSvgTextRect`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
import TextProperties = textMeasurementService.TextProperties;
// ...

let textProperties: TextProperties = {
    text: "Microsoft PowerBI",
    fontFamily: "sans-serif",
    fontSize: "24px"
};

textMeasurementService.measureSvgTextRect(textProperties);

// returns: { x: 0, y: -22, width: 194.71875, height: 27 }
```

### <a name="measuresvgtextheight"></a>measureSvgTextHeight

Die Funktion misst die Höhe des Texts mit den angegebenen SVG-Texteigenschaften.

```typescript
function measureSvgTextHeight(textProperties: TextProperties, text?: string): number;
```

Beispiel für die Verwendung von `measureSvgTextHeight`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
import TextProperties = textMeasurementService.TextProperties;
// ...


let textProperties: TextProperties = {
    text: "Microsoft PowerBI",
    fontFamily: "sans-serif",
    fontSize: "24px"
};

textMeasurementService.measureSvgTextHeight(textProperties);

// returns: 27
```

### <a name="estimatesvgtextbaselinedelta"></a>estimateSvgTextBaselineDelta

Diese Funktion gibt eine Baseline mit den angegebenen SVG-Texteigenschaften zurück.

```typescript
function estimateSvgTextBaselineDelta(textProperties: TextProperties): number;
```

Beispiel:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
import TextProperties = textMeasurementService.TextProperties;
// ...

let textProperties: TextProperties = {
    text: "Microsoft PowerBI",
    fontFamily: "sans-serif",
    fontSize: "24px"
};

textMeasurementService.estimateSvgTextBaselineDelta(textProperties);

// returns: 5
```

### <a name="estimatesvgtextheight"></a>estimateSvgTextHeight

Die Funktion schätzt die Höhe des Texts mit den angegebenen SVG-Texteigenschaften.

```typescript
function estimateSvgTextHeight(textProperties: TextProperties, tightFightForNumeric?: boolean): number;
```

Beispiel für die Verwendung von `estimateSvgTextHeight`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
import TextProperties = textMeasurementService.TextProperties;
// ...

let textProperties: TextProperties = {
    text: "Microsoft PowerBI",
    fontFamily: "sans-serif",
    fontSize: "24px"
};

textMeasurementService.estimateSvgTextHeight(textProperties);

// returns: 27
```

Sie können sich den Beispielcode des benutzerdefinierten Visuals [hier](https://github.com/Microsoft/powerbi-visuals-sankey/blob/4d544ea145b4e15006083a3610dfead3da5f61a4/src/visual.ts#L372) ansehen.

### <a name="measuresvgtextelementwidth"></a>measureSvgTextElementWidth

Die Funktion misst die Breite von „svgElement“.

```typescript
function measureSvgTextElementWidth(svgElement: SVGTextElement): number;
```

Beispiel für die Verwendung von „measureSvgTextElementWidth“:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
// ...

let svg: D3.Selection = d3.select("body").append("svg");

svg.append("text")
    .text("Microsoft PowerBI")
    .attr({
        "x": 25,
        "y": 25
    })
    .style({
        "font-family": "sans-serif",
        "font-size": "24px"
    });

let textElement: D3.Selection = svg.select("text");

textMeasurementService.measureSvgTextElementWidth(textElement.node());

// returns: 194.71875
```

### <a name="getmeasurementproperties"></a>getMeasurementProperties

Diese Funktion ruft die Eigenschaften der Textmessung des angegebenen DOM-Elements ab.

```typescript
function getMeasurementProperties(element: Element): TextProperties;
```

Beispiel für die Verwendung von `getMeasurementProperties`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
// ...

let element: JQuery = $(document.createElement("div"));

element.text("Microsoft PowerBI");

element.css({
    "width": 500,
    "height": 500,
    "font-family": "sans-serif",
    "font-size": "32em",
    "font-weight": "bold",
    "font-style": "italic",
    "white-space": "nowrap"
});

textMeasurementService.getMeasurementProperties(element.get(0));

/* returns: {
    fontFamily:"sans-serif",
    fontSize: "32em",
    fontStyle: "italic",
    fontVariant: "",
    fontWeight: "bold",
    text: "Microsoft PowerBI",
    whiteSpace: "nowrap"
}*/
```

### <a name="getsvgmeasurementproperties"></a>getSvgMeasurementProperties

Diese Funktion ruft die Eigenschaften der Textmessung des angegebenen SVG-Textelements ab.

```typescript
function getSvgMeasurementProperties(svgElement: SVGTextElement): TextProperties;
```

Beispiel für die Verwendung von `getSvgMeasurementProperties`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
// ...

let svg: D3.Selection = d3.select("body").append("svg");

let textElement: D3.Selection = svg.append("text")
    .text("Microsoft PowerBI")
    .attr({
        "x": 25,
        "y": 25
    })
    .style({
        "font-family": "sans-serif",
        "font-size": "24px"
    });

textMeasurementService.getSvgMeasurementProperties(textElement.node());

/* returns: {
    "text": "Microsoft PowerBI",
    "fontFamily": "sans-serif",
    "fontSize": "24px",
    "fontWeight": "normal",
    "fontStyle": "normal",
    "fontVariant": "normal",
    "whiteSpace": "nowrap"
}*/
```

## <a name="getdivelementwidth"></a>getDivElementWidth

Die Funktion gibt die Breite eines div-Elements zurück.

```typescript
function getDivElementWidth(element: JQuery): string;
```

Beispiel für die Verwendung von `getDivElementWidth`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
// ...

let svg: Element = d3.select("body")
    .append("div")
    .style({
        "width": "150px",
        "height": "150px"
    })
    .node();

textMeasurementService.getDivElementWidth(svg)

// returns: 150px
```

### <a name="gettailoredtextordefault"></a>getTailoredTextOrDefault

Diese Funktion vergleicht die Textgröße von Bezeichnungen mit der verfügbaren Größe und rendert Ellipsen, wenn die verfügbare Größe kleiner ist.

```typescript
function getTailoredTextOrDefault(textProperties: TextProperties, maxWidth: number): string;
```

Beispiel für die Verwendung von `getTailoredTextOrDefault`:

```typescript
import { textMeasurementService } from "powerbi-visuals-utils-formattingutils";
import TextProperties = textMeasurementService.TextProperties;
// ...

let textProperties: TextProperties = {
    text: "Microsoft PowerBI!",
    fontFamily: "sans-serif",
    fontSize: "24px"
};

textMeasurementService.getTailoredTextOrDefault(textProperties, 100);

// returns: Micros...
```

## <a name="string-extensions"></a>Zeichenfolgenerweiterungen

Das Modul stellt die folgenden Funktionen zur Verfügung:

## <a name="endswith"></a>endsWith

Die Funktion überprüft, ob eine Zeichenfolge mit einer Teilzeichenfolge endet.

```typescript
function endsWith(str: string, suffix: string): boolean;
```

Beispiel für die Verwendung von `endsWith`:

```typescript
import { stringExtensions } from "powerbi-visuals-utils-formattingutils";
// ...

stringExtensions.endsWith("Power BI", "BI");

// returns: true
```

### <a name="equalignorecase"></a>equalIgnoreCase

Diese Funktion vergleicht Zeichenfolgen, wobei Groß-/Kleinbuchstaben ignoriert werden.

```typescript
function equalIgnoreCase(a: string, b: string): boolean;
```

Beispiel für die Verwendung von `equalIgnoreCase`:

```typescript
import { stringExtensions } from "powerbi-visuals-utils-formattingutils";
// ...

stringExtensions.equalIgnoreCase("Power BI", "power bi");

// returns: true
```

### <a name="startswith"></a>startsWith

Die Funktion überprüft, ob eine Zeichenfolge mit einer Teilzeichenfolge beginnt.

```typescript
function startsWith(a: string, b: string): boolean;
```

Beispiel für die Verwendung von `startsWith`:

```typescript
import { stringExtensions } from "powerbi-visuals-utils-formattingutils";
// ...

stringExtensions.startsWith("Power BI", "Power");

// returns: true
```

### <a name="contains"></a>enthält

Diese Funktion überprüft, ob eine Zeichenfolge eine angegebene Teilzeichenfolge enthält.

```typescript
function contains(source: string, substring: string): boolean;
```

Beispiel für die Verwendung der `contains`-Methode:

```typescript
import { stringExtensions } from "powerbi-visuals-utils-formattingutils";
// ...

stringExtensions.contains("Microsoft Power BI Visuals", "Power BI");

// returns: true
```

### <a name="isnullorempty"></a>isNullOrEmpty

Diese Funktion überprüft, ob eine Zeichenfolge NULL, nicht definiert oder leer ist.

```typescript
function isNullOrEmpty(value: string): boolean;
```

Beispiel für die `isNullOrEmpty`-Methode:

```typescript
import { stringExtensions } from "powerbi-visuals-utils-formattingutils";
// ...

stringExtensions.isNullOrEmpty(null);

// returns: true
```

## <a name="value-formatter"></a>Wertformatierung

Das Modul stellt die folgenden Funktionen, Schnittstellen und Klassen zur Verfügung:

## <a name="ivalueformatter"></a>IValueFormatter

Diese Schnittstelle beschreibt öffentliche Methoden und Eigenschaften des Formatierers.

```typescript
interface IValueFormatter {
    format(value: any): string;
    displayUnit?: DisplayUnit;
    options?: ValueFormatterOptions;
}
```

### <a name="ivalueformatterformat"></a>IValueFormatter.format

Diese Methode formatiert den angegebenen Wert.

```typescript
function format(value: any, format?: string, allowFormatBeautification?: boolean): string;
```

Beispiele für `IValueFormatter.format`:

#### <a name="the-thousand-formats"></a>Tausenderformate

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ value: 1001 });

iValueFormatter.format(5678);

// returns: "5.68K"
```

#### <a name="the-million-formats"></a>Millionenformate

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ value: 1e6 });

iValueFormatter.format(1234567890);

// returns: "1234.57M"
```

#### <a name="the-billion-formats"></a>Milliardenformate

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ value: 1e9 });

iValueFormatter.format(1234567891236);

// returns: 1234.57bn
```

#### <a name="the-trillion-format"></a>Trillionenformat

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ value: 1e12 });

iValueFormatter.format(1234567891236);

// returns: 1.23T
```

#### <a name="the-exponent-format"></a>Exponentenformat

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ format: "E" });

iValueFormatter.format(1234567891236);

// returns: 1.234568E+012
```

### <a name="the-culture-selector"></a>Kulturauswahl

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let valueFormatterUK = valueFormatter.create({ cultureSelector: "en-GB" });

valueFormatterUK.format(new Date(2007, 2, 3, 17, 42, 42));

// returns: 03/03/2007 17:42:42

let valueFormatterUSA = valueFormatter.create({ cultureSelector: "en-US" });

valueFormatterUSA.format(new Date(2007, 2, 3, 17, 42, 42));

// returns: 3/3/2007 5:42:42 PM
```

#### <a name="the-percentage-format"></a>Prozentformat

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ format: "0.00 %;-0.00 %;0.00 %" });

iValueFormatter.format(0.54);

// returns: 54.00 %
```

#### <a name="the-dates-format"></a>Datumsformat

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let date = new Date(2016, 10, 28, 15, 36, 0),
    iValueFormatter = valueFormatter.create({});

iValueFormatter.format(date);

// returns: 11/28/2016 3:36:00 PM
```

#### <a name="the-boolean-format"></a>Boolesches Format

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({});

iValueFormatter.format(true);

// returns: True
```

#### <a name="the-customized-precision"></a>Angepasste Genauigkeit

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

let iValueFormatter = valueFormatter.create({ value: 0, precision: 3 });

iValueFormatter.format(3.141592653589793);

// returns: 3.142
```

Sie können sich den Beispielcode des benutzerdefinierten Visuals [hier](https://github.com/Microsoft/powerbi-visuals-sankey/blob/4d544ea145b4e15006083a3610dfead3da5f61a4/src/visual.ts#L359) ansehen.

## <a name="valueformatteroptions"></a>ValueFormatterOptions

Diese Schnittstelle beschreibt `options` der IValueFormatter-Schnittstelle und der Optionen der create-Funktion.

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";
import ValueFormatterOptions = valueFormatter.ValueFormatterOptions;

interface ValueFormatterOptions {
    /** The format string to use. */
    format?: string;
    /** The data value. */
    value?: any;
    /** The data value. */
    value2?: any;
    /** The number of ticks. */
    tickCount?: any;
    /** The display unit system to use */
    displayUnitSystemType?: DisplayUnitSystemType;
    /** True if we are formatting single values in isolation (e.g. card), as opposed to multiple values with a common base (e.g. chart axes) */
    formatSingleValues?: boolean;
    /** True if we want to trim off unnecessary zeroes after the decimal and remove a space before the % symbol */
    allowFormatBeautification?: boolean;
    /** Specifies the maximum number of decimal places to show*/
    precision?: number;
    /** Detect axis precision based on value */
    detectAxisPrecision?: boolean;
    /** Specifies the column type of the data value */
    columnType?: ValueTypeDescriptor;
    /** Specifies the culture */
    cultureSelector?: string;
}
```

## <a name="create"></a>Erstellen

Diese Methode erstellt eine Instanz von IValueFormatter.

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";
import create = valueFormatter.create;

function create(options: ValueFormatterOptions): IValueFormatter;
```

### <a name="example-of-using-create"></a>Beispiel für die Verwendung von „create“

```typescript
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";

valueFormatter.create({});

// returns: an instance of IValueFormatter.
```

## <a name="next-steps"></a>Nächste Schritte

[Hinzufügen des Gebietsschemas in Power BI für benutzerdefinierte Visuals](localization.md)  
