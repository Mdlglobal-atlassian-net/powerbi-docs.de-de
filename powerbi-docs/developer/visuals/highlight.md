---
title: Hervorhebungen
description: Hervorheben ausgewählter Datenpunkte in Power BI-Visuals
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: a472db6c6dcc1266a11e78d72ab8465df7682042
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114150"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Hervorheben von Datenpunkten in Power BI-Visuals

Wenn ein Element ausgewählt ist, wird das `values`-Array im `dataView`-Objekt standardmäßig nach den ausgewählten Werten gefiltert. Dadurch werden für alle anderen Visuals auf der Seite nur die ausgewählten Daten angezeigt.

![Standardverhalten beim Hervorheben von 'DataView'](media/highlight/highlight-dataview.png)

Wenn Sie die `supportsHighlight`-Eigenschaft in `capabilities.json` auf `true` festlegen, erhalten Sie ein gänzlich ungefiltertes `values`-Array zusammen mit einem `highlights`-Array. Das `highlights`-Array hat die gleiche Länge wie das Wertarray, und alle nicht ausgewählten Werte werden auf `null` festgelegt. Wenn diese Eigenschaft aktiviert ist, ist das Visual dafür zuständig, die entsprechenden Daten hervorzuheben. Dazu wird das `values`-Array mit dem `highlights`-Array verglichen.

![„dataview“ unterstützt Hervorhebungen](media/highlight/highlight-dataview-supports.png)

In diesem Beispiel sehen Sie, dass ein Balken ausgewählt ist. Dies ist auch der einzige Wert im highlights-Array. Beachten Sie außerdem, dass es Mehrfachauswahl sowie teilweise Hervorhebungen geben kann. Die hervorgehobenen Werte werden in der Datenansicht angezeigt.

> [!NOTE]
> Die Zuordnung von Tabellendaten in der Ansicht unterstützt das Feature „Highlights“ nicht.

## <a name="highlight-data-points-with-categorical-data-view-mapping"></a>Hervorheben von Datenpunkten mit Kategoriezuordnung in der Datenansicht

Die Visuals mit Kategoriezuordnung in der Datenansicht weisen `capabilities.json` mit dem Parameter `"supportsHighlight": true` auf. Beispiel:

```json
{
    "dataRoles": [
        {
            "displayName": "Category",
            "name": "category",
            "kind": "Grouping"
        },
        {
            "displayName": "Value",
            "name": "value",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "categorical": {
                "categories": {
                    "for": {
                        "in": "category"
                    }
                },
                "values": {
                    "for": {
                        "in": "value"
                    }
                }
            }
        }
    ],
    "supportsHighlight": true
}
```

Der Standardquellcode für ein Visual nach dem Entfernen von unnötigem Code sieht so aus:

```typescript
"use strict";

// ... default imports list

import DataViewCategorical = powerbi.DataViewCategorical;
import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
import PrimitiveValue = powerbi.PrimitiveValue;
import DataViewValueColumn = powerbi.DataViewValueColumn;

import { VisualSettings } from "./settings";

export class Visual implements IVisual {
    private target: HTMLElement;
    private settings: VisualSettings;

    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.host = options.host;

    }

    public update(options: VisualUpdateOptions) {
        this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
        console.log('Visual update', options);

    }

    private static parseSettings(dataView: DataView): VisualSettings {
        return <VisualSettings>VisualSettings.parse(dataView);
    }

    /**
     * This function gets called for each of the objects defined in the capabilities files and allows you to select which of the
     * objects and properties you want to expose to the users in the property pane.
     *
     */
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {
        return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
    }
}
```

Für den Import erforderliche Schnittstellen zum Verarbeiten von Daten aus Power BI:

```typescript
import DataViewCategorical = powerbi.DataViewCategorical;
import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
import PrimitiveValue = powerbi.PrimitiveValue;
import DataViewValueColumn = powerbi.DataViewValueColumn;
```

Erstellen des `div`-Stammelements für Kategoriewerte:

```typescript
export class Visual implements IVisual {
    private target: HTMLElement;
    private settings: VisualSettings;

    private div: HTMLDivElement; // new property

    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.host = options.host;

        // create div element
        this.div = document.createElement("div");
        this.div.classList.add("vertical");
        this.target.appendChild(this.div);

    }
    // ...
}
```

Löschen des Inhalts von div-Elementen vor dem Rendern neuer Daten:

```typescript
// ...
public update(options: VisualUpdateOptions) {
    this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
    console.log('Visual update', options);

    while (this.div.firstChild) {
        this.div.removeChild(this.div.firstChild);
    }
    // ...
}
```

Abrufen von Kategorien und Measures aus dem `dataView`-Objekt:

```typescript
public update(options: VisualUpdateOptions) {
    this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
    console.log('Visual update', options);

    while (this.div.firstChild) {
        this.div.removeChild(this.div.firstChild);
    }

    const dataView: DataView = options.dataViews[0];
    const categoricalDataView: DataViewCategorical = dataView.categorical;
    const categories: DataViewCategoryColumn = categoricalDataView.categories[0];
    const categoryValues = categories.values;

    const measures: DataViewValueColumn = categoricalDataView.values[0];
    const measureValues = measures.values;
    const measureHighlights = measures.highlights;
    // ...
}
```

Hierbei sind `categoryValues` ein Array von Kategoriewerten, `measureValues` ein Array von Measures und `measureHighlights` die hervorgehobenen Teile von Werten.

> [!NOTE]
> Die Werte der Eigenschaft `measureHighlights` können kleiner als die Werte der Eigenschaft `categoryValues` sein.
> Dies bedeutet, dass ein Wert teilweise hervorgehoben wurde.

Zählen Sie das `categoryValues`-Array auf, und rufen Sie die entsprechenden Werte und Hervorhebungen ab:

```typescript
// ...
const measureHighlights = measures.highlights;

categoryValues.forEach((category: PrimitiveValue, index: number) => {
    const measureValue = measureValues[index];
    const measureHighlight = measureHighlights && measureHighlights[index] ? measureHighlights[index] : null;
    console.log(category, measureValue, measureHighlight);

});
```

Erstellen Sie die Elemente `div` und `p`, um die Werte der Datenansicht in einem visuellen DOM darzustellen:

```typescript
categoryValues.forEach((category: PrimitiveValue, index: number) => {
    const measureValue = measureValues[index];
    const measureHighlight = measureHighlights && measureHighlights[index] ? measureHighlights[index] : null;
    console.log(category, measureValue, measureHighlight);

    // div element. it contains elements to display values and visualize value as progress bar
    let div = document.createElement("div");
    div.classList.add("horizontal");
    this.div.appendChild(div);

    // div element to vizualize value of measure
    let barValue = document.createElement("div");
    barValue.style.width = +measureValue * 10 + "px";
    barValue.style.display = "flex";
    barValue.classList.add("value");

    // element to display category value
    let bp = document.createElement("p");
    bp.innerText = category.toString();

    // div element to vizualize highlight of measure
    let barHighlight = document.createElement("div");
    barHighlight.classList.add("highlight")
    barHighlight.style.backgroundColor = "blue";
    barHighlight.style.width = +measureHighlight * 10 + "px";

    // element to display highlighted value of measure
    let p = document.createElement("p");
    p.innerText = `${measureHighlight}/${measureValue}`;
    barHighlight.appendChild(bp);

    div.appendChild(barValue);

    barValue.appendChild(barHighlight);
    div.appendChild(p);
});
```

Wenden Sie die erforderlichen Formatvorlagen für Elemente an, die `flex box` verwenden sollen, und definieren Sie Farben für div-Elemente:

```css
div.vertical {
    display: flex;
    flex-direction: column;
}

div.horizontal {
    display: flex;
    flex-direction: row;
}

div.highlight {
    background-color: blue
}

div.value {
    background-color: red;
    display: flex;
}
```

Als Ergebnis sollten Sie zur folgenden Darstellung des Visuals gelangen.

![Die Visuals mit Kategoriezuordnung in der Datenansicht und Hervorherbung](media/highlight/dev-categorical-visual-highlight-demo.gif)

## <a name="highlight-data-points-with-matrix-data-view-mapping"></a>Hervorheben von Datenpunkten mit Zuordnung der Matrixdaten in der Ansicht

Die Visuals mit Zuordnung der Matrixdaten in der Ansicht weisen `capabilities.json` mit dem Parameter `"supportsHighlight": true` auf. Beispiel:

```json
{
    "dataRoles": [
        {
            "displayName": "Columns",
            "name": "columns",
            "kind": "Grouping"
        },
        {
            "displayName": "Rows",
            "name": "rows",
            "kind": "Grouping"
        },
        {
            "displayName": "Value",
            "name": "value",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "columns": {
                    "for": {
                        "in": "columns"
                    }
                },
                "rows": {
                    "for": {
                        "in": "rows"
                    }
                },
                "values": {
                    "for": {
                        "in": "value"
                    }
                }
            }
        }
    ],
    "supportsHighlight": true
}
```

Die Beispieldaten zum Erstellen der Hierarchie für die Zuordnung der Matrixdaten in der Ansicht:

|   Zeile1   |   Zeile2   |   Zeile3   |   Column1   |   Column2   |   Column3   |   Werte   |
|-----|-----|------|-------|-------|-------|-------|
|   F1   |   R11   |   R111   |   C1   |   C11   |   C111   |   1   |
|   F1   |   R11   |   R112   |   C1   |   C11   |   C112   |   2   |
|   F1   |   R11   |   R113   |   C1   |   C11   |   C113   |   3   |
|   F1   |   R12   |   R121   |   C1   |   C12   |   C121   |   4   |
|   F1   |   R12   |   R122   |   C1   |   C12   |   C122   |   5   |
|   F1   |   R12   |   R123   |   C1   |   C12   |   C123   |   6   |
|   F1   |   R13   |   R131   |   C1   |   C13   |   C131   |   7   |
|   F1   |   R13   |   R132   |   C1   |   C13   |   C132   |   8   |
|   F1   |   R13   |   R133   |   C1   |   C13   |   C133   |   9   |
|   F2   |   R21   |   R211   |   C2   |   C21   |   C211   |   10   |
|   F2   |   R21   |   R212   |   C2   |   C21   |   C212   |   11   |
|   F2   |   R21   |   R213   |   C2   |   C21   |   C213   |   12   |
|   F2   |   R22   |   R221   |   C2   |   C22   |   C221   |   13   |
|   F2   |   R22   |   R222   |   C2   |   C22   |   C222   |   14   |
|   F2   |   R22   |   R223   |   C2   |   C22   |   C223   |   16   |
|   F2   |   R23   |   R231   |   C2   |   C23   |   C231   |   17   |
|   F2   |   R23   |   R232   |   C2   |   C23   |   C232   |   18   |
|   F2   |   R23   |   R233   |   C2   |   C23   |   C233   |   19   |

Erstellen Sie das Visual-Standardprojekt, und übernehmen Sie das Beispiel von `capabilities.json`.

Der Visual-Standardquellcode nach dem Entfernen von unnötigem Code sieht so aus:

```typescript
"use strict";

// ... default imports

import { VisualSettings } from "./settings";

export class Visual implements IVisual {
    private target: HTMLElement;
    private settings: VisualSettings;


    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.host = options.host;
    }

    public update(options: VisualUpdateOptions) {
        this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
        console.log('Visual update', options);

    }

    private static parseSettings(dataView: DataView): VisualSettings {
        return <VisualSettings>VisualSettings.parse(dataView);
    }

    /**
     * This function gets called for each of the objects defined in the capabilities files and allows you to select which of the
     * objects and properties you want to expose to the users in the property pane.
     *
     */
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {
        return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
    }
}
```

Für den Import erforderliche Schnittstellen zum Verarbeiten von Daten aus Power BI:

```typescript
import DataViewMatrix = powerbi.DataViewMatrix;
import DataViewMatrixNode = powerbi.DataViewMatrixNode;
import DataViewHierarchyLevel = powerbi.DataViewHierarchyLevel;
```

Erstellen Sie zwei `div`-Elemente für das Visual-Layout:

```typescript
constructor(options: VisualConstructorOptions) {
    // ...
    this.rowsDiv = document.createElement("div");
    this.target.appendChild(this.rowsDiv);

    this.colsDiv = document.createElement("div");
    this.target.appendChild(this.colsDiv);
    this.target.style.overflowY = "auto";
}
```

Überprüfen Sie die Daten in der `update`-Methode, um sicherzustellen, dass das Visual Daten erhält:

```typescript
public update(options: VisualUpdateOptions) {
    this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
    console.log('Visual update', options);

    const dataView: DataView = options.dataViews[0];
    const matrixDataView: DataViewMatrix = dataView.matrix;

    if (!matrixDataView ||
        !matrixDataView.columns ||
        !matrixDataView.rows ) {
        return
    }
    // ...
}
```

Löschen Sie die Inhalte der `div`-Elemente vor dem Rendern neuer Daten:

```typescript
public update(options: VisualUpdateOptions) {
    // ...

    // remove old elements
    // to better performance use D3js pattern:
    // https://d3js.org/#enter-exit
    while (this.rowsDiv.firstChild) {
        this.rowsDiv.removeChild(this.rowsDiv.firstChild);
    }
    const prow = document.createElement("p");
    prow.innerText = "Rows";
    this.rowsDiv.appendChild(prow);

    while (this.colsDiv.firstChild) {
        this.colsDiv.removeChild(this.colsDiv.firstChild);
    }
    const pcol = document.createElement("p");
    pcol.innerText = "Columns";
    this.colsDiv.appendChild(pcol);
    // ...
}
```

Erstellen Sie die `treeWalker`-Funktion zum Durchlaufen der Matrixdatenstruktur:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {

    }
    // ...
}
```

Dabei ist `matrixNode` der aktuelle Knoten, `levels` stellt Metadatenspalten der aktuellen Hierarchieebene dar, `div` ist das übergeordnete Element für untergeordnete HTML-Elemente.

Die `treeWalker`-Funktion ist rekursiv, es müssen `div`- und `p`-Elemente für den Text als Überschrift erstellt und die Funktion für die untergeordneten Elemente des Knotens aufgerufen werden:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...

        if (matrixNode.children) {
            const childDiv = document.createElement("div");
            childDiv.classList.add("vertical");
            div.appendChild(childDiv);

            const p = document.createElement("p");
            const level = levels[matrixNode.level]; // get current level column metadata from current node
            p.innerText = level.sources[level.sources.length - 1].displayName; // get column name from metadata

            childDiv.appendChild(p); // add paragraph element to div element
            matrixNode.children.forEach((node, index) => treeWalker(node, levels, childDiv, ++levelIndex));
        }
    }
    // ...
}
```

Rufen Sie die Funktion für die Stammelemente von Spalte und Zeile der Matrixstruktur der Datenansicht auf:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...
    }
    // ...
    // remove old elements
    // ...

    // ...
    const rowRoot: DataViewMatrixNode = matrixDataView.rows.root;
    rowRoot.children.forEach((node) => treeWalker(node, matrixDataView.rows.levels, this.rowsDiv));

    const colRoot = matrixDataView.columns.root;
    colRoot.children.forEach((node) => treeWalker(node, matrixDataView.columns.levels, this.colsDiv));
}
```

Generieren Sie die selectionID für Knoten und die Erstellen-Schaltflächen zum Anzeigen von Knoten:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        const selectionID: ISelectionID = this.host.createSelectionIdBuilder()
            .withMatrixNode(matrixNode, levels)
            .createSelectionId();

        let nodeBlock = document.createElement("button");
        nodeBlock.innerText = matrixNode.value.toString();

        nodeBlock.addEventListener("click", (event) => {
            // call select method in the selection manager
            this.selectionManager.select(selectionID);
        });

        nodeBlock.addEventListener("contextmenu", (event) => {
            // call showContextMenu method to display context menu on the visual
            this.selectionManager.showContextMenu(selectionID, {
                x: event.clientX,
                y: event.clientY
            });
            event.preventDefault();
        });
        // ...
    }
    // ...
}
```

Der Hauptschritt beim Einsatz von Hervorhebung besteht in der Verarbeitung zusätzlicher Wertearrays.

Wenn Sie das Objekt des Terminalknotens untersuchen, können Sie sehen, dass das Wertearray zwei Eigenschaften aufweist – Wert und Hervorhebung:

```javascript
JSON.stringify(options.dataViews[0].matrix.rows.root.children[0].children[0].children[0], null, " ");
```

```json
{
 "level": 2,
 "levelValues": [
  {
   "value": "R233",
   "levelSourceIndex": 0
  }
 ],
 "value": "R233",
 "identity": {
  "identityIndex": 2
 },
 "values": {
  "0": {
   "value": null,
   "highlight": null
  },
  "1": {
   "value": 19,
   "highlight": 19
  }
 }
}
```

Dabei stellt die Eigenschaft `value` den Wert des Knotens dar, ohne eine Auswahl von einem anderen Visual anzuwenden, und die highlight-Eigenschaft gibt an, welcher Teil der Daten hervorgehoben wurde.

> [!NOTE]
> Der Wert der Eigenschaft `highlight` kann kleiner als der Wert der Eigenschaft `value` sein.
> Dies bedeutet, dass ein Wert teilweise hervorgehoben wurde.

Fügen Sie den Code zum Verarbeiten des `values`-Arrays des Knotens hinzu, wenn er dargestellt wird:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...

        if (matrixNode.values) {
            const sumOfValues = Object.keys(matrixNode.values) // get key property of object (value are 0 to N)
                .map(key => +matrixNode.values[key].value) // convert key property to number
                .reduce((prev, curr) => prev + curr) // sum of values

            let sumOfHighlights = sumOfValues;
            sumOfHighlights = Object.keys(matrixNode.values) // get key property of object (value are 0 to N)
                .map(key => matrixNode.values[key].highlight ? +matrixNode.values[key].highlight : null ) // convert key property to number if it exists
                .reduce((prev, curr) => curr ? prev + curr : null) // convert key property to number

            // create div container for value and highlighted value
            const vals = document.createElement("div");
            vals.classList.add("vertical")
            vals.classList.replace("vertical", "horizontal");
            // create paragraph element for label
            const highlighted = document.createElement("p");
            // Display complete value and highlighted value
            highlighted.innerText = `${sumOfHighlights}/${sumOfValues}`;

            // create div container for value
            const valueDiv = document.createElement("div");
            valueDiv.style.width = sumOfValues * 10 + "px";
            valueDiv.classList.add("value");

            // create div container for highlighted values
            const highlightsDiv = document.createElement("div");
            highlightsDiv.style.width = sumOfHighlights * 10 + "px";
            highlightsDiv.classList.add("highlight");
            valueDiv.appendChild(highlightsDiv);

            // append button and paragraph to div containers to parent div
            vals.appendChild(nodeBlock);
            vals.appendChild(valueDiv);
            vals.appendChild(highlighted);
            div.appendChild(vals);
        } else {
            div.appendChild(nodeBlock);
        }

        if (matrixNode.children) {
            // ...
        }
    }
    // ...
}
```

Als Ergebnis erhalten Sie das Visual mit Schaltflächen und den Werten `highlighted value/default value`

![Das Visual mit Zuordnung der Matrixdaten in der Ansicht und Hervorhebung](media/highlight/dev-matrix-visual-highlight-demo.gif)

## <a name="next-steps"></a>Weitere Schritte

* [Weitere Informationen zu Zuordnungen von Matrixdaten in der Ansicht](dataview-mappings.md#matrix-data-mapping)

* [Weitere Informationen über Funktionen von visuellen Elementen](capabilities.md)
