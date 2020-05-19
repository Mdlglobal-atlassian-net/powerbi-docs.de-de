---
title: Hinzufügen von Farben zu Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie Ihren Power BI-Visuals Farben hinzufügen und mit Datenpunkten für ein farbiges Visual umgehen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3f3574545d82ac11c762b7011afdc49cbe855224
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141151"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Hinzufügen von Farben zu Power BI-Visuals

In diesem Artikel wird beschrieben, wie Sie Ihren Power BI-Visuals Farben hinzufügen und mit Datenpunkten für ein farbiges Visual umgehen.

`IVisualHost` macht Farbe als einen seiner Dienste verfügbar.
Der Beispielcode in diesem Artikel modifiziert das Visual [SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Informationen zum Quellcode finden Sie unter [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Informationen zu den ersten Schritten bei der Erstellung von Visuals finden Sie unter [Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md).

## <a name="add-color-to-data-points"></a>Hinzufügen von Farbe zu Datenpunkten

Jede Farbe steht für einen anderen Datenpunkt.
Fügen Sie die Farbe zur `BarChartDataPoint`-Schnittstelle wie im folgenden Beispiel hinzu:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Verwenden des Farbpalettendiensts

Der Dienst `colorPalette` verwaltet die in Ihrem Visual verwendeten Farben.
Eine Instanz des Diensts ist für `IVisualHost` verfügbar.

Definieren Sie ihn in der `update`-Methode.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Zuweisen von Farbe zu Datenpunkten

Geben Sie als Nächstes `dataPoints` an.
In diesem Beispiel enthält jedes `dataPoints`-Element Werte, Kategorien und Farben.
`dataPoints` kann auch andere Eigenschaften einschließen.

In `SampleBarChart` kapselt die `visualTransform`-Methode die `dataPoints`-Berechnung.
Diese Methode gehört zum ViewModel „Balkendiagramm“.
Da die Methode eine Iteration durch die `dataPoints`-Berechnung in `visualTransform` vornimmt, eignet sie sich ideal, um wie im folgenden Code Farben zuzuweisen:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Wenden Sie dann Daten von `dataPoints` auf die [d3](https://d3js.org/)-Auswahl `barSelection` innerhalb der `update`-Methode an:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Power BI-Visuals finden Sie unter [Funktionen und Eigenschaften von Power BI-Visuals](capabilities.md).

Weitere Informationen zum Entwickeln von Power BI-Visuals finden Sie unter [Debuggen von Power BI-Visuals](visuals-how-to-debug.md) und [Problembehandlung bei Power BI-Visuals](power-bi-custom-visuals-troubleshoot.md).
