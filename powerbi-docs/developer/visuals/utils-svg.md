---
title: Einführung in die Verwendung der SVGUtils-Klasse in Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie die SVGUtils-Klasse verwenden, um SVG-Manipulationen für Power BI-Visuals zu vereinfachen.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: aa1ac8074e842a51b369c48f57c4b5016a80140c
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377970"
---
# <a name="svg-utils"></a>SVGUtils

SVGUtils besteht aus mehreren Funktionen und Klassen, um SVG-Manipulationen für Power BI-Visuals zu vereinfachen.

## <a name="installation"></a>Installation

Führen Sie den folgenden Befehl im Verzeichnis mit Ihrem aktuellen Visual aus, um das Paket zu installieren:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

Das Modul `CssConstants` bietet die spezielle Funktion und Schnittstelle für die Arbeit mit Klassenselektoren.

Das Modul `powerbi.extensibility.utils.svg.CssConstants` stellt die folgende Funktion und Schnittstelle zur Verfügung:

## <a name="classandselector"></a>ClassAndSelector

Die Schnittstelle beschreibt die allgemeinen Eigenschaften des Klassenselektors.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Diese Funktion erstellt eine Instanz von ClassAndSelector mit dem angegebenen Namen der Klasse.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Beispiel:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

Das Modul `manipulation` bietet einige spezielle Funktionen für die Erzeugung von Zeichenfolgen zur Verwendung mit der SVG-Transformationseigenschaft.

Das Modul stellt die folgenden Funktionen zur Verfügung:

### <a name="translate"></a>translate

Diese Funktion erstellt eine translate-Zeichenfolge zur Verwendung mit der SVG-Transformationseigenschaft.

```typescript
function translate(x: number, y: number): string;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Diese Funktion erstellt eine translateX-Zeichenfolge zur Verwendung mit der SVG-Transformationseigenschaft.

```typescript
function translateXWithPixels(x: number): string;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Diese Funktion erstellt eine translate-Zeichenfolge zur Verwendung mit der SVG-Transformationseigenschaft.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Diese Funktion erstellt eine translate-rotate-Zeichenfolge zur Verwendung mit der SVG-Transformationseigenschaft.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>Skalierung

Diese Funktion erstellt eine scale-Zeichenfolge zur Verwendung mit der CSS-Transformationseigenschaft.

```typescript
function scale(scale: number): string;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Diese Funktion erstellt eine transform-origin-Zeichenfolge zur Verwendung in der CSS-transform-origin-Eigenschaft.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Diese Funktion erzwingt jeden Übergang von D3, um diesen abzuschließen.

```typescript
function flushAllD3Transitions(): void;
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Diese Funktion analysiert die transform-Zeichenfolge mit dem Wert "translate(x,y)".

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Diese Funktion erstellt einen Pfeil.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Beispiel:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

Das Modul `Rect` stellt einige spezielle Funktionen zur Manipulation von Rechtecken zur Verfügung.

Das Modul stellt die folgenden Funktionen zur Verfügung:

### <a name="getoffset"></a>getOffset

Diese Funktion gibt einen Offset des Rechtecks zurück.

```typescript
function getOffset(rect: IRect): IPoint;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Diese Funktion gibt die Größe des Rechtecks zurück.

```typescript
function getSize(rect: IRect): ISize;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Diese Funktion ändert die Größe des Rechtecks.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Diese Funktion gibt eine right-Position des Rechtecks zurück.

```typescript
function right(rect: IRect): number;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Diese Funktion gibt eine bottom-Position des Rechtecks zurück.

```typescript
function bottom(rect: IRect): number;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Diese Funktion gibt eine top-left-Position des Rechtecks zurück.

```typescript
function topLeft(rect: IRect): IPoint;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Diese Funktion gibt eine top-right-Position des Rechtecks zurück.

```typescript
function topRight(rect: IRect): IPoint;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Diese Funktion gibt eine bottom-left-Position des Rechtecks zurück.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Diese Funktion gibt eine bottom-right-Position des Rechtecks zurück.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Beispiel

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>Klon

Diese Funktion erstellt eine Kopie des Rechtecks.

```typescript
function clone(rect: IRect): IRect;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Diese Funktion konvertiert das Rechteck in eine Zeichenfolge.

```typescript
function toString(rect: IRect): string;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Diese Funktion wendet den angegebenen Offset auf das Rechteck an.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Diese Funktion fügt das erste Rechteck zum zweiten Rechteck hinzu.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Diese Funktion gibt den nächstgelegenen Punkt des Rechtecks zum angegebenen Punkt zurück.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Diese Funktion vergleicht Rechtecke und gibt TRUE zurück, wenn sie gleich sind.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Diese Funktion vergleicht Rechtecke unter Berücksichtigung der Genauigkeit der Werte.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Diese Funktion prüft, ob das Rechteck leer ist.

```typescript
function isEmpty(rect: IRect): boolean;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Diese Funktion prüft, ob das Rechteck den Punkt enthält.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Diese Funktion prüft, ob sich die Rechtecke überschneiden.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Diese Funktion gibt einen Schnittpunkt von Rechtecken zurück.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Diese Funktion kombiniert Rechtecke.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Diese Funktion gibt einen Mittelpunkt des Rechtecks zurück.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Beispiel:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>Zeiger

Das Modul `pointer` stellt eine spezielle Funktion zur Verfügung, um die Position des Zeigers zu ermitteln.

Das Modul stellt die folgenden Funktionen zur Verfügung:

### <a name="getcoordinates"></a>getCoordinates

Diese Funktion gibt die Position des Zeigers zurück.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Beispiel:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
