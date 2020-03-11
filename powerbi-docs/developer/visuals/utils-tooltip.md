---
title: Einführung in die Verwendung von QuickInfo-Hilfsprogrammen in Power BI-Visuals
description: Dieser Artikel erläutert die Verwendung von QuickInfo-Hilfsprogrammen zur einfacheren Anpassung von QuickInfos für Power BI-Visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 6f4aa276438d84825c4c7aba6872210b5f3a6564
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264218"
---
# <a name="tooltip-utils"></a>QuickInfo-Hilfsprogramme
Dieser Artikel unterstützt Sie beim Installieren, Importieren und Verwenden von QuickInfo-Hilfsprogrammen (utils). Dieses Hilfsprogramm eignet sich für die Anpassung jeglicher QuickInfos in Power BI-Visuals.

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

> In der folgenden Anleitung zur Verwendung wird eine öffentliche API des Pakets beschrieben. Hier finden Sie eine Beschreibung sowie Beispiele für jede öffentliche Schnittstelle des Pakets.

Mit diesem Paket können Sie `TooltipServiceWrapper` und Methoden zum Verarbeiten von QuickInfo-Aktionen erstellen. Es verwendet QuickInfo-Schnittstellen: `ITooltipServiceWrapper`, `TooltipEventArgs` und `TooltipEnabledDataPoint`. 

Es verfügt auch über spezifische Methoden (Ereignishandler für Berührungsereignisse) für die Entwicklung für Mobilgeräte: `touchEndEventName`, `touchStartEventName` und `usePointerEvents`.

`TooltipServiceWrapper` bietet die einfachste Möglichkeit zur Bearbeitung von QuickInfos.

Dieses Modul stellt die folgende Schnittstelle und Funktion zur Verfügung:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Schnittstellen](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Berührungsereignisse](#touch-events)

### `createTooltipServiceWrapper`
Diese Funktion erstellt eine Instanz von ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

Der ```ITooltipService``` ist in [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335) verfügbar.

**Beispiel**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Sie können sich den Beispielcode des benutzerdefinierten Visuals [hier](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391) ansehen.

### `ITooltipServiceWrapper`
Diese Schnittstelle beschreibt öffentliche Methoden von TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Diese Methode fügt der aktuellen Auswahl QuickInfos hinzu.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Beispiel**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Sie können sich den Beispielcode des benutzerdefinierten Visuals [hier](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931) ansehen.

Beachten Sie auch das Beispiel für die Anpassung von QuickInfos in benutzerdefinierten Gantt-Visuals, das Sie [hier](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648) finden.

### `ITooltipServiceWrapper.hide`

Diese Methode blendet die QuickInfo aus.

```typescript
hide(): void;
```

**Beispiel**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Diese Schnittstellen werden während der Erstellung und Verwendung von TooltipServiceWrapper verwendet. Sie wurden auch [hier](#itooltipservicewrapperaddtooltip) in Beispielen des vorherigen Themas erwähnt.

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

QuickInfo-Hilfsprogramme sind in der Lage, mehrere Berührungsereignisse zu verarbeiten, und eignen sich daher gut für die Entwicklung für Mobilgeräte.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Diese Methode gibt den Namen des Ereignisses für den Beginn der Berührung zurück.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Diese Methode gibt den Namen des Ereignisses für das Ende der Berührung zurück.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Diese Methode gibt Informationen dazu zurück, ob sich das aktuelle touchStart-Ereignis auf einen Zeiger bezieht oder nicht.
