---
title: Einführung in die Verwendung der TypeUtils-Klasse in Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie SVGUtils verwenden, um die grundlegenden Typen der Power BI-Visuals zu erweitern.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 5a3cfb7ea9c9f398193b45652aa43c6b83c8f70b
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377993"
---
# <a name="type-utils"></a>TypeUtils

TypeUtils besteht aus mehreren Funktionen und Klassen, um die grundlegenden Typen für Power BI-Visuals zu erweitern.

## <a name="installation"></a>Installation

Führen Sie den folgenden Befehl im Verzeichnis mit ihrem aktuellen benutzerdefinierten Visual aus, um das Paket zu installieren.

„npm install powerbi-visuals-utils-typeutils --save“: Dieser Befehl installiert das Paket und fügt Ihrer JSON-Paketdatei ein Paket als Abhängigkeit hinzu.

## <a name="double"></a>Double

Das `Double`-Modul bietet die Möglichkeit, die Genauigkeit der Zahlen zu manipulieren.

Das Modul stellt die folgenden Funktionen zur Verfügung:

### <a name="pow10"></a>pow10

Diese Funktion gibt eine Zehnerpotenz zurück.

```typescript
function pow10(exp: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>LOG10

Diese Funktion gibt einen Logarithmus zur Basis 10 der Zahl zurück.

```typescript
function log10(val: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Diese Funktion gibt eine Zehnerpotenz zurück, die die Genauigkeit der Zahl darstellt.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Diese Funktion prüft, ob ein Delta zwischen zwei Zahlen kleiner als die angegebene Genauigkeit ist.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Diese Funktion überprüft, ob der erste Wert kleiner als der zweite Wert ist.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Diese Funktion überprüft, ob der erste Wert kleiner als der zweite Wert oder gleich dem zweiten Wert ist.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Diese Funktion überprüft, ob der erste Wert größer als der zweite Wert ist.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Diese Funktion überprüft, ob der erste Wert größer als der zweite Wert oder gleich dem zweiten Wert ist.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Diese Funktion rundet die Zahl mit der angegebenen Genauigkeit ab.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Diese Funktion rundet die Zahl mit der angegebenen Genauigkeit auf.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Diese Funktion gibt die Zahl mit der angegebenen Genauigkeit zurück.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Diese Funktion rundet die Zahl mit der angegebenen Genauigkeit auf.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Diese Funktion rundet die Zahl auf die angegebene Genauigkeit.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Diese Funktion gibt eine Zahl zurück, die zwischen dem Minimal- und Maximalwert liegt.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Diese Funktion rundet die Zahl.

```typescript
function round(x: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Mit dieser Funktion werden die Dezimalstellen reduziert.

```typescript
function removeDecimalNoise(value: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Diese Funktion überprüft, ob die Zahl eine ganze Zahl ist.

```typescript
function isInteger(value: number): boolean;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Diese Funktion erhöht die Zahl um die angegebene Zahl und gibt die gerundete Zahl zurück.

```typescript
function toIncrement(value: number, increment: number): number;
```

Beispiel:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototyp

`Prototype` bietet die Möglichkeit, Objekte zu erben.

Das Modul stellt die folgenden Funktionen zur Verfügung:

## <a name="inherit"></a>inherit

Diese Funktion gibt ein neues Objekt mit dem angegebenen Objekt als Prototyp zurück.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Beispiel:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Diese Funktion gibt ein neues Objekt mit dem angegebenen Objekt als Prototyp zurück, und zwar nur, wenn der Prototyp nicht festgelegt wurde.

```typescript
function inheritSingle<T>(obj: T): T;
```

Beispiel:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

Das `PixelConverter`-Modul bietet die Möglichkeit, Pixel in Punkte und Punkte in Pixel zu konvertieren.

Das Modul stellt die folgenden Funktionen zur Verfügung:

## <a name="tostring"></a>toString

Diese Funktion konvertiert den Pixelwert in eine Zeichenfolge.

```typescript
function toString(px: number): string;
```

Beispiel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Diese Funktion wandelt den angegebenen Punktwert in den Pixelwert um und gibt die Interpretation der Zeichenfolge zurück.

```typescript
function fromPoint(pt: number): string;
```

Beispiel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Diese Funktion konvertiert den angegebenen Punktwert in den Pixelwert.

```typescript
function fromPointToPixel(pt: number): number;
```

Beispiel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Diese Funktion konvertiert den Pixelwert in den Punktwert.

```typescript
function toPoint(px: number): number;
```

Beispiel:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
