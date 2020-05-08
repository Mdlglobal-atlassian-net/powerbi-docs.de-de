---
title: Einführung in die Verwendung der ChartUtils-Klasse in Power BI-Visuals
description: Dieser Artikel beschreibt die Verwendung der ChartUtils-Klasse zum Zeichnen von Achsen und Legenden in Power BI-Visuals.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 531da1ede8b83af9fb8093a3178c945f374b835c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379388"
---
# <a name="chart-utils"></a>ChartUtils

Die ChartUtils-Klasse umfasst eine Reihe von Schnittstellen und Methoden zur Erstellung von Achsen, Datenbezeichnungen und Legenden in Power BI-Visuals.

## <a name="installation"></a>Installation

Führen Sie den folgenden Befehl im Verzeichnis mit Ihrem aktuellen Visual aus, um das Paket zu installieren:

```bash
npm install powerbi-visuals-utils-chartutils --save
```

## <a name="axis-helper"></a>Hilfsprogramm für Achsen

Das Hilfsprogramm für Achsen (`axis`-Objekt in Hilfsprogrammen) stellt Funktionen bereit, um Manipulationen mit der Achse zu vereinfachen.

Das Modul stellt die folgenden Funktionen zur Verfügung:

### <a name="getrecommendednumberofticksforxaxis"></a>getRecommendedNumberOfTicksForXAxis

Diese Funktion gibt die empfohlene Anzahl von Teilstrichen entsprechend der Breite des Diagramms zurück.

```typescript
function getRecommendedNumberOfTicksForXAxis(availableWidth: number): number;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForXAxis(1024);

// returns: 8
```

### <a name="getrecommendednumberofticksforyaxis"></a>getRecommendedNumberOfTicksForYAxis

Diese Funktion gibt die empfohlene Anzahl von Teilstrichen entsprechend der Länge des Diagramms zurück.

```typescript
function getRecommendedNumberOfTicksForYAxis(availableWidth: number);
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForYAxis(100);

// returns: 3
```

### <a name="getbestnumberofticks"></a>getBestNumberOfTicks

Diese Funktion ruft die optimale Anzahl von Teilstrichen basierend auf dem Minimalwert, dem Maximalwert, den Metadaten und der maximalen Anzahl von Teilstrichen ab.

```typescript
function getBestNumberOfTicks(
  min: number,
  max: number,
  valuesMetadata: DataViewMetadataColumn[],
  maxTickCount: number,
  isDateTime?: boolean
): number;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
var dataViewMetadataColumnWithIntegersOnly: powerbi.DataViewMetadataColumn[] = [
  {
    displayName: "col1",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  },
  {
    displayName: "col2",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  }
];
var actual = axis.getBestNumberOfTicks(
  0,
  3,
  dataViewMetadataColumnWithIntegersOnly,
  6
);

// returns: 4
```

### <a name="getticklabelmargins"></a>getTickLabelMargins

Diese Funktion gibt die Begrenzung für die Bezeichnungen der Teilstriche zurück.

```typescript
function getTickLabelMargins(
  viewport: IViewport,
  yMarginLimit: number,
  textWidthMeasurer: ITextAsSVGMeasurer,
  textHeightMeasurer: ITextAsSVGMeasurer,
  axes: CartesianAxisProperties,
  bottomMarginLimit: number,
  properties: TextProperties,
  scrollbarVisible?: boolean,
  showOnRight?: boolean,
  renderXAxis?: boolean,
  renderY1Axis?: boolean,
  renderY2Axis?: boolean
): TickLabelMargins;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.getTickLabelMargins(
  plotArea,
  marginLimits.left,
  TextMeasurementService.measureSvgTextWidth,
  TextMeasurementService.estimateSvgTextHeight,
  axes,
  marginLimits.bottom,
  textProperties,
  /*scrolling*/ false,
  showY1OnRight,
  renderXAxis,
  renderY1Axis,
  renderY2Axis
);

// returns:  xMax, yLeft, yRight, stackHeigh;
```

### <a name="isordinal"></a>isOrdinal

Diese Funktion überprüft, ob eine Zeichenfolge NULL, nicht definiert oder leer ist.

```typescript
function isOrdinal(type: ValueTypeDescriptor): boolean;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
let type = ValueType.fromDescriptor({ misc: { barcode: true } });
axis.isOrdinal(type);

// returns: true
```

### <a name="isdatetime"></a>isDateTime

Diese Funktion überprüft, ob der Wert ein DateTime-Typ ist.

```typescript
function isDateTime(type: ValueTypeDescriptor): boolean;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.isDateTime(ValueType.fromDescriptor({ dateTime: true }));

// returns: true
```

### <a name="getcategorythickness"></a>getCategoryThickness

Diese Funktion verwendet die D3-Skala, um die aktuelle Kategoriestärke zu erhalten.

```typescript
function getCategoryThickness(scale: any): number;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let range = [0, 100];
let domain = [0, 10];
let scale = d3.scale
  .linear()
  .domain(domain)
  .range(range);
let actualThickness = axis.getCategoryThickness(scale);
```

### <a name="invertordinalscale"></a>invertOrdinalScale

Diese Funktion kehrt die Ordinalskala um. Wenn x < scale.range()[0] ist, dann wird scale.domain()[0] zurückgegeben.
Andernfalls wird das größte Element in scale.domain() zurückgegeben, das <=x ist.

```typescript
function invertOrdinalScale(scale: d3.scale.Ordinal<any, any>, x: number);
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let domain: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
  pixelSpan: number = 100,
  ordinalScale: d3.scale.ordinal = axis.createOrdinalScale(
    pixelSpan,
    domain,
    0.4
  );

axis.invertOrdinalScale(ordinalScale, 49);

// returns: 4
```

### <a name="findclosestxaxisindex"></a>findClosestXAxisIndex

Diese Funktion sucht den nächstgelegenen Index der X-Achse und gibt diesen zurück.

```typescript
function findClosestXAxisIndex(
  categoryValue: number,
  categoryAxisValues: AxisHelperCategoryDataPoint[]
): number;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

/**
 * Finds the index of the category of the given x coordinate given.
 * pointX is in non-scaled screen-space, and offsetX is in render-space.
 * offsetX does not need any scaling adjustment.
 * @param {number} pointX The mouse coordinate in screen-space, without scaling applied
 * @param {number} offsetX Any left offset in d3.scale render-space
 * @return {number}
 */
private findIndex(pointX: number, offsetX?: number): number {
    // we are using mouse coordinates that do not know about any potential CSS transform scale
    let xScale = this.scaleDetector.getScale().x;
    if (!Double.equalWithPrecision(xScale, 1.0, 0.00001)) {
        pointX = pointX / xScale;
    }
    if (offsetX) {
        pointX += offsetX;
    }

    let index = axis.invertScale(this.xAxisProperties.scale, pointX);
    if (this.data.isScalar) {
        // When we have scalar data the inverted scale produces a category value, so we need to search for the closest index.
        index = axis.findClosestXAxisIndex(index, this.data.categoryData);
    }

    return index;
}
```

### <a name="diffscaled"></a>diffScaled

Diese Funktion berechnet und gibt eine Differenz der Werte in der Skala zurück.

```typescript
function diffScaled(
  scale: d3.scale.Linear<any, any>,
  value1: any,
  value2: any
): number;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var scale: d3.scale.Linear<number, number>,
    range = [0, 999],
    domain = [0, 1, 2, 3, 4, 5, 6, 7, 8, 999];

scale = d3.scale.linear()
    .range(range)
    .domain(domain);

return axis.diffScaled(scale, 0, 0));

// returns: 0
```

### <a name="createdomain"></a>createDomain

Diese Funktion erstellt eine Dömäne mit Werten für die Achse.

```typescript
function createDomain(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

var domain = axis.createDomain(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="getcategoryvaluetype"></a>getCategoryValueType

Diese Funktion ruft die `ValueType`-Klasse der Kategoriespalte ab. Die Standardklasse ist `Text`, wenn der Typ nicht vorhanden ist.

```typescript
function getCategoryValueType(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

axis.getCategoryValueType(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="createaxis"></a>createAxis

Diese Funktion erstellt eine D3-Achse einschließlich der Skala. Diese kann entweder vertikal oder horizontal sein oder DateTime, numerisch oder Text sein.

```typescript
function createAxis(options: CreateAxisOptions): IAxisProperties;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";
// ...

var dataPercent = [0.0, 0.33, 0.49];

var formatStringProp: powerbi.DataViewObjectPropertyIdentifier = {
  objectName: "general",
  propertyName: "formatString"
};
let metaDataColumnPercent: powerbi.DataViewMetadataColumn = {
  displayName: "Column",
  type: ValueType.fromDescriptor({ numeric: true }),
  objects: {
    general: {
      formatString: "0 %"
    }
  }
};

var os = axis.createAxis({
  pixelSpan: 100,
  dataDomain: [dataPercent[0], dataPercent[2]],
  metaDataColumn: metaDataColumnPercent,
  formatString: valueFormatter.getFormatString(
    metaDataColumnPercent,
    formatStringProp
  ),
  outerPadding: 0.5,
  isScalar: true,
  isVertical: true
});
```

### <a name="applycustomizeddomain"></a>applyCustomizedDomain

Diese Funktion legt eine benutzerdefinierte Domäne fest, aber ändert diese nicht, wenn keine festgelegt ist.

```typescript
function applyCustomizedDomain(customizedDomain, forcedDomain: any[]): any[];
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let customizedDomain = [undefined, 20],
  existingDomain = [0, 10];

axis.applyCustomizedDomain(customizedDomain, existingDomain);

// returns: {0:0, 1:20}
```

### <a name="combinedomain"></a>combineDomain

Diese Funktion kombiniert die erzwungene Domäne mit der tatsächlichen Domäne, wenn einer der Werte festgelegt wurde.
Die erzwungene Domäne (forcedDomain) hat erste Priorität. Hier wird die Domäne erweitert, wenn ein Referenzpunkt dies erfordert.

```typescript
function combineDomain(
  forcedDomain: any[],
  domain: any[],
  ensureDomain?: NumberRange
): any[];
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let forcedYDomain = this.valueAxisProperties
  ? [this.valueAxisProperties["secStart"], this.valueAxisProperties["secEnd"]]
  : null;

let xDomain = [minX, maxX];

axis.combineDomain(forcedYDomain, xDomain, ensureXDomain);
```

### <a name="poweroften"></a>powerOfTen

Diese Funktion gibt an, ob die Zahl eine Potenz von 10 ist.

```typescript
function powerOfTen(d: any): boolean;
```

Beispiel:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.powerOfTen(10);

// returns: true
```

## <a name="datalabelmanager"></a>DataLabelManager

`DataLabelManager` unterstützt Sie bei der Erstellung und Verwaltung von Bezeichnungen. Diese Funktion ordnet Bezeichnungselemente mit Hilfe des Ankerpunktes oder Rechtecks an. Konflikte können automatisch erkannt werden, um Elemente neu zu positionieren oder auszublenden.

Die `DataLabelManager`-Klasse enthält die folgenden Methoden:

## <a name="hidecollidedlabels"></a>hideCollidedLabels

Diese Methode ordnet die Position und Sichtbarkeit der Bezeichnungen auf dem Zeichenbereich entsprechend der Bezeichnungsgröße und der Überlappung an.

```typescript
function hideCollidedLabels(
  viewport: IViewport,
  data: any[],
  layout: any,
  addTransform: boolean = false
): LabelEnabledDataPoint[];
```

Beispiel:

```typescript
let dataLabelManager = new DataLabelManager();
let filteredData = dataLabelManager.hideCollidedLabels(
  this.viewport,
  values,
  labelLayout,
  true
);
```

## <a name="isvalid"></a>IsValid

Diese statische Methode prüft, ob das angegebene Rechteck gültig ist (positive Breite und Höhe).

```typescript
function isValid(rect: IRect): boolean;
```

Beispiel:

```typescript
let rectangle = {
  left: 150,
  top: 130,
  width: 120,
  height: 110
};

DataLabelManager.isValid(rectangle);

// returns: true
```

## <a name="datalabelutils"></a>DataLabelUtils

`DataLabelUtils` stellt Hilfsprogramme zur Manipulation von Datenbezeichnungen bereit.

Das Modul stellt die folgenden Funktionen, Schnittstellen und Klassen zur Verfügung:

### <a name="getlabelprecision"></a>getLabelPrecision

Diese Funktion berechnet die Genauigkeit aus dem angegebenen Format.

```typescript
function getLabelPrecision(precision: number, format: string): number;
```

### <a name="getlabelformattedtext"></a>getLabelFormattedText

Diese Funktion berechnet die Formatgenauigkeit aus dem angegebenen Format.

```typescript
function getLabelFormattedText(options: LabelFormattedTextOptions): string;
```

Beispiel:

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let options: LabelFormattedTextOptions = {
  text: "some text",
  fontFamily: "sans",
  fontSize: "15",
  fontWeight: "normal"
};

dataLabelUtils.getLabelFormattedText(options);
```

### <a name="enumeratedatalabels"></a>enumerateDataLabels

Diese Funktion gibt VisualObjectInstance für Datenbezeichnungen zurück.

```typescript
function enumerateDataLabels(
  options: VisualDataLabelsSettingsOptions
): VisualObjectInstance;
```

### <a name="enumeratecategorylabels"></a>enumerateCategoryLabels

Diese Funktion fügt VisualObjectInstance für Kategoriedatenbezeichnungen zum Enumerationsobjekt hinzu.

```typescript
function enumerateCategoryLabels(
  enumeration: VisualObjectInstanceEnumerationObject,
  dataLabelsSettings: VisualDataLabelsSettings,
  withFill: boolean,
  isShowCategory: boolean = false,
  fontSize?: number
): void;
```

### <a name="createcolumnformattercachemanager"></a>createColumnFormatterCacheManager

Diese Funktion gibt den Cache-Manager zurück, der schnellen Zugriff auf formatierte Bezeichnungen bietet.

```typescript
function createColumnFormatterCacheManager(): IColumnFormatterCacheManager;
```

Beispiel:

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let value: number = 200000;

labelSettings.displayUnits = 1000000;
labelSettings.precision = 1;

let formattersCache = DataLabelUtils.createColumnFormatterCacheManager();
let formatter = formattersCache.getOrCreate(null, labelSettings);
let formattedValue = formatter.format(value);

// formattedValue == "0.2M"
```

## <a name="legend-service"></a>Legend-Dienst

Der `Legend`-Dienst bietet Hilfsprogrammschnittstellen zur Erstellung und Verwaltung von Power BI-Legenden für Power BI-Visuals.

Das Modul stellt die folgenden Funktionen und Schnittstellen zur Verfügung:

### <a name="createlegend"></a>createLegend

Diese Hilfsfunktion vereinfacht die Legendenerstellung in benutzerdefinierten Power BI-Visuals.

```typescript
function createLegend(
  legendParentElement: HTMLElement, // top visual element, container in which legend will be created
  interactive: boolean, // indicates that legend should be interactive
  interactivityService: IInteractivityService, // reference to IInteractivityService interface which need to create legend click events
  isScrollable: boolean = false, // indicates that legend could be scrollable or not
  legendPosition: LegendPosition = LegendPosition.Top // Position of the legend inside of legendParentElement container
): ILegend;
```

Beispiel:

```typescript
public constructor(options: VisualConstructorOptions) {
    this.visualInitOptions = options;
    this.layers = [];

    var element = this.element = options.element;
    var viewport = this.currentViewport = options.viewport;
    var hostServices = options.host;

    //... some other init calls

    if (this.behavior) {
        this.interactivityService = createInteractivityService(hostServices);
    }
    this.legend = createLegend(
        element,
        options.interactivity && options.interactivity.isInteractiveLegend,
        this.interactivityService,
        true);
}
```

### <a name="ilegend"></a>ILegend

Diese Schnittstelle implementiert alle Methoden, die für die Legendenerstellung notwendig sind.

```typescript
export interface ILegend {
  getMargins(): IViewport;
  isVisible(): boolean;
  changeOrientation(orientation: LegendPosition): void; // processing legend orientation
  getOrientation(): LegendPosition; // get information about current legend orientation
  drawLegend(data: LegendData, viewport: IViewport); // all legend rendering code is placing here
  /**
   * Reset the legend by clearing it
   */
  reset(): void;
}
```

### <a name="drawlegend"></a>drawLegend

Die Funktion misst die Höhe des Texts mit den angegebenen SVG-Texteigenschaften.

```typescript
function drawLegend(data: LegendData, viewport: IViewport): void;
```

Beispiel:

```typescript
private renderLegend(): void {
    if (!this.isInteractive) {
        let legendObjectProperties = this.data.legendObjectProperties;
        if (legendObjectProperties) {
            let legendData = this.data.legendData;
            LegendData.update(legendData, legendObjectProperties);
            let position = <string>legendObjectProperties[legendProps.position];
            if (position)
                this.legend.changeOrientation(LegendPosition[position]);

            this.legend.drawLegend(legendData, this.parentViewport);
        } else {
            this.legend.changeOrientation(LegendPosition.Top);
            this.legend.drawLegend({ dataPoints: [] }, this.parentViewport);
        }
    }
}
```

## <a name="next-steps"></a>Weitere Schritte

- [Verwenden der InteractivityUtils zum Hinzufügen von Auswahlmöglichkeiten für Power BI-Visuals](utils-interactivity-selections.md).
