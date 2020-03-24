---
title: Hinzufügen von Unterstützung für Drilldowns
description: In diesem Artikel wird beschrieben, wie Sie die Unterstützung für Drilldowns zu Power BI-Visuals hinzufügen.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: dd8510230a66a9897023686aefb72990ac01a5fd
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380401"
---
# <a name="add-drill-down-support"></a>Hinzufügen von Unterstützung für Drilldowns

In Power BI-Visuals können Power BI-Drilldowns verwendet werden.

Weitere Informationen zu Power BI-Drilldowns finden Sie [hier](./../../consumer/end-user-drill.md).

## <a name="enable-drill-down-support-in-the-visual"></a>Aktivieren der Drilldownunterstützung im Visual

Um einen Drilldown im Visual zu unterstützen, fügen Sie ein neues Feld zu `capabilities.json` mit dem Namen „Drilldown“ hinzu, das über eine Eigenschaft verfügt:

    *roles - the name of the dataRole you want to enable drill-down on.

> [!NOTE]
> Der Drilldown „dataRole“ muss vom Typ `Grouping` sein.
> Die `max`-Eigenschaft in den dataRole-Bedingungen muss auf 1 gesetzt sein.

Nachdem Sie die Rolle einem Drilldown hinzugefügt haben, können Benutzer mehrere Felder in die Datenrolle ziehen.

Beispiel:

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
    "drilldown": {
        "roles": [
            "category"
        ]
    },
    "dataViewMappings": [
        {
            "categorical": {
                "categories": {
                    "for": {
                        "in": "category"
                    }
                },
                "values": {
                    "select": [
                        {
                            "bind": {
                                "to": "value"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

## <a name="create-the-visual-with-drill-down-support"></a>Erstellen des Visuals mit Drilldownunterstützung

Ausführen

```cmd
pbiviz new testDrillDown -t default
```

Auf diese Weise wird ein standardmäßiges Beispielvisual erstellt. Wenden Sie dann das obige Beispiel von `capabilities.json` auf das neu erstellte Visual an.

Erstellen Sie die Eigenschaft für `div`-Container, um HTML-Elemente des Visuals zu speichern:

```typescript
"use strict";

import "core-js/stable";
import "./../style/visual.less";
// imports

export class Visual implements IVisual {
    // visual properties
    // ...
    private div: HTMLDivElement; // <== NEW PROPERTY

    constructor(options: VisualConstructorOptions) {
        // constructor body
        // ...
    }

    public update(options: VisualUpdateOptions) {
        // update method body
        // ...
    }

    private static parseSettings(dataView: DataView): VisualSettings {
        return <VisualSettings>VisualSettings.parse(dataView);
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[] | VisualObjectInstanceEnumerationObject {
        return VisualSettings.enumerateObjectInstances(this.settings || VisualSettings.getDefault(), options);
    }
}
```

Aktualisieren Sie den Konstruktor des Visuals:

```typescript

export class Visual implements IVisual {
    // visual properties
    // ...
    private div: HTMLDivElement;

    constructor(options: VisualConstructorOptions) {
        console.log('Visual constructor', options);
        this.target = options.element;
        this.updateCount = 0;

        const new_p: HTMLElement = document.createElement("p");
        new_p.appendChild(document.createTextNode("Hierarchy level:"));
        const new_em: HTMLElement = document.createElement("em");
        this.textNode = document.createTextNode(this.updateCount.toString());
        new_em.appendChild(this.textNode);
        new_p.appendChild(new_em);
        this.target.appendChild(new_p);

        this.div = document.createElement("div"); // <== CREATE DIV ELEMENT
        this.target.appendChild(this.div);
    }
}
```

Aktualisieren Sie die `update`-Methode des Visuals, um `button`-Elemente zu erstellen:

```typescript
export class Visual implements IVisual {
    // ...

    public update(options: VisualUpdateOptions) {
        this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
        console.log('Visual update', options);

        const dataView: DataView = options.dataViews[0];
        const categoricalDataView: DataViewCategorical = dataView.categorical;

        // don't create elements if no data
        if (!options.dataViews[0].categorical ||
            !options.dataViews[0].categorical.categories) {
            return
        }

        // to display current level of hierarchy
        if (typeof this.textNode !== undefined) {
            this.textNode.textContent = categoricalDataView.categories[categoricalDataView.categories.length - 1].source.displayName.toString();
        }

        // remove old elements
        // for better performance use D3js pattern:
        // https://d3js.org/#enter-exit
        while (this.div.firstChild) {
            this.div.removeChild(this.div.firstChild);
        }

        // create buttons for each category value
        categoricalDataView.categories[categoricalDataView.categories.length - 1].values.forEach( (category: powerbi.PrimitiveValue, index: number) => {
            let button = document.createElement("button");
            button.innerText = category.toString();

            this.div.appendChild(button);
        })

    }
    // ...
```

Wenden Sie einfache Stile in `.\style\visual.less` an:

```less
button {
    margin: 5px;
    min-width: 50px;
    min-height: 50px;
}
```

Bereiten Sie Beispieldaten vor, um das Visual zu testen:

|   H1  |   H2    | H3  |   WERTE  |
|-----|-----|------|-------|
|   A   |    A1  |    A11 |    1   |
|   A    |    A1    |    A12    |    2    |
|   A    |    A2    |    A21    |    3    |
|   A    |    A2    |    A22    |    4    |
|   A    |    A3    |    A31    |    5    |
|   A    |    A3    |    A32    |    6    |
|   B    |    B1    |    B11    |    7    |
|   B    |    B1    |    B12    |    8    |
|   B    |    B2    |    B21    |    9    |
|   B    |    B2    |    B22    |    10    |
|   B    |    B3    |    B31    |    11    |
|   B    |    B3    |    B32    |    12    |

Und erstellen Sie eine Hierarchie in Power BI Desktop:

![Erstellen einer neuen Hierarchie](media/drill-down-support/create-new-hierarchy.png)

Schließen Sie alle Kategoriespalten (H1, H2, H3) in die neue Hierarchie ein:

![Erstellen einer neuen Hierarchie](media/drill-down-support/new-hierarchy.png)

Nachdem Sie diese Schritte ausgeführt haben, sollten Sie Folgendes Visual erhalten:

![Dev-Visual mit Schaltflächen](media/drill-down-support/dev-visual-drilldown1.png)

## <a name="add-context-menu-to-visual-elements"></a>Hinzufügen eines Kontextmenüs zu visuellen Elementen

In diesem Schritt fügen Sie das Kontextmenü der Schaltfläche im Visual hinzu:

![Kontextmenü im Visual](media/drill-down-support/dev-visual-drilldown-context-menu.png)

Um das Kontextmenü zu erstellen, speichern Sie das `host`-Objekt in den Eigenschaften des Visuals. Rufen Sie dann die `createSelectionManager`-Methode zum Erstellen des Auswahl-Managers auf, um ein Kontextmenü mit der Power BI-Visuals-API anzuzeigen.

```typescript
"use strict";

import "core-js/stable";
import "./../style/visual.less";
// imports

export class Visual implements IVisual {
    // visual properties
    // ...
    private div: HTMLDivElement;
    private host: IVisualHost; // <== NEW PROPERTY
    private selectionManager: ISelectionManager; // <== NEW PROPERTY

    constructor(options: VisualConstructorOptions) {
        // constructor body
        // save the host in the visuals properties
        this.host = options.host;
        // create selection manager
        this.selectionManager = this.host.createSelectionManager();
        // ...
    }

    public update(options: VisualUpdateOptions) {
        // update method body
        // ...
    }

    // ...
}
```

Ändern Sie den Text des `forEach`-Funktionsrückrufs in:

```typescript
    categoricalDataView.categories[categoricalDataView.categories.length - 1].values.forEach( (category: powerbi.PrimitiveValue, index: number) => {
        // create selectionID for each category value
        let selectionID: ISelectionID = this.host.createSelectionIdBuilder()
            .withCategory(categoricalDataView.categories[0], index)
            .createSelectionId();

        let button = document.createElement("button");
        button.innerText = category.toString();

        // add event listener to click event
        button.addEventListener("click", (event) => {
            // call select method in the selection manager
            this.selectionManager.select(selectionID);
        });

        button.addEventListener("contextmenu", (event) => {
            // call showContextMenu method to display context menu on the visual
            this.selectionManager.showContextMenu(selectionID, {
                x: event.clientX,
                y: event.clientY
            });
            event.preventDefault();
        });

        this.div.appendChild(button);
    });
```

Wenden Sie Daten auf das Visual an:

![Das Visual mit Daten](media/drill-down-support/dev-visual-drilldown-data.png)

Im letzten Schritt sollte das Visual mit Auswahlmöglichkeiten und einem Kontextmenü angezeigt werden:

![Das Visual mit Drilldownunterstützung](media/drill-down-support/dev-visual-drilldown-demo.gif)

## <a name="add-drill-down-support-for-matrix-data-view-mapping"></a>Hinzufügen von Drilldownunterstützung für die Zuordnung der Matrixdatenansicht

Bereiten Sie Beispieldaten vor, um das Visual mit Zuordnungen der Matrixdatenansicht zu testen:

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

Wenden Sie folgende Datenansichtszuordnung für das Visual an:

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
    "drilldown": {
        "roles": [
            "columns",
            "rows"
        ]
    },
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
    ]
}
```

Wenden Sie Daten auf das Visual an:

![Das Visual mit Daten](media/drill-down-support/dev-matrix-visual-drilldown-data.png)

Importieren Sie die erforderlichen Schnittstellen, um Zuordnungen der Matrixdatenansicht zu verarbeiten:

```typescript
// ...
import DataViewMatrix = powerbi.DataViewMatrix;
import DataViewMatrixNode = powerbi.DataViewMatrixNode;
import DataViewHierarchyLevel = powerbi.DataViewHierarchyLevel;
// ...
```

Erstellen Sie zwei Eigenschaften für zwei `div`-Zeilen- und -Spaltenelemente:

```typescript
export class Visual implements IVisual {
    // ...
    private rowsDiv: HTMLDivElement;
    private colsDiv: HTMLDivElement;
    // ...
    constructor(options: VisualConstructorOptions) {
        // constructor body
        // ...
        // Create div elements and append to main div of the visual
        this.rowsDiv = document.createElement("div");
        this.target.appendChild(this.rowsDiv);

        this.colsDiv = document.createElement("div");
        this.target.appendChild(this.colsDiv);
    }
    // ...
}
```

Überprüfen Sie die Daten vor dem Rendern von Elementen, und zeigen Sie die aktuelle Hierarchieebene an:

```typescript
export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // constructor body
    }

    public update(options: VisualUpdateOptions) {
        this.settings = Visual.parseSettings(options && options.dataViews && options.dataViews[0]);
        console.log('Visual update', options);

        const dataView: DataView = options.dataViews[0];
        const matrixDataView: DataViewMatrix = dataView.matrix;

        // if the visual doesn't receive the data no reason to continue rendering
        if (!matrixDataView ||
            !matrixDataView.columns ||
            !matrixDataView.rows ) {
            return
        }

        // to display current level of hierarchy
        if (typeof this.textNode !== undefined) {
            this.textNode.textContent = categoricalDataView.categories[categoricalDataView.categories.length - 1].source.displayName.toString();
        }
        // ...
    }
    // ...
}
```

Erstellen Sie die Funktion `treeWalker` zum Durchlaufen der Hierarchie:

```typescript
export class Visual implements IVisual {
    // ...
    public update(options: VisualUpdateOptions) {
        // ...

        // if the visual doesn't receive the data no reason to continue rendering
        if (!matrixDataView ||
            !matrixDataView.columns ||
            !matrixDataView.rows ) {
            return
        }

        const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
            // ...
            if (matrixNode.children) {
                // ...
                // traversing child nodes
                matrixNode.children.forEach((node, index) => treeWalker(node, index, levels, childDiv));
            }
        }

        // traversing rows
        const rowRoot: DataViewMatrixNode = matrixDataView.rows.root;
        rowRoot.children.forEach((node, index) => treeWalker(node, index, matrixDataView.rows.levels, this.rowsDiv));

        // traversing columns
        const colRoot = matrixDataView.columns.root;
        colRoot.children.forEach((node, index) => treeWalker(node, index, matrixDataView.columns.levels, this.colsDiv));
    }
    // ...
}
```

Generieren Sie die Auswahl für Datenpunkte.

```typescript
const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
    // generate selectionID for each node of matrix
    const selectionID: ISelectionID = this.host.createSelectionIdBuilder()
        .withMatrixNode(matrixNode, levels)
        .createSelectionId();
    // ...
    if (matrixNode.children) {
        // ...
        // traversing child nodes
        matrixNode.children.forEach((node, index) => treeWalker(node, index, levels, childDiv));
    }
}
```

Erstellen Sie für jede Hierarchieebene ein `div`-Element:

```typescript
const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
    // generate selectionID for each node of matrix
    const selectionID: ISelectionID = this.host.createSelectionIdBuilder()
        .withMatrixNode(matrixNode, levels)
        .createSelectionId();
    // ...
    if (matrixNode.children) {
        // create div element for level
        const childDiv = document.createElement("div");
        // add to current div
        div.appendChild(childDiv);
        // create paragraph element to display next
        const p = document.createElement("p");
        // display level name on paragraph element
        const level = levels[matrixNode.level];
        p.innerText = level.sources[level.sources.length - 1].displayName;
        // add paragraph element to created child div
        childDiv.appendChild(p);
        // traversing child nodes
        matrixNode.children.forEach((node, index) => treeWalker(node, index, levels, childDiv));
    }
}
```

Erstellen Sie `buttons`-Elemente, um mit dem Visual zu interagieren und ein Kontextmenü für Matrixdatenpunkte anzuzeigen:

```typescript
const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
    // generate selectionID for each node of matrix
    const selectionID: ISelectionID = this.host.createSelectionIdBuilder()
        .withMatrixNode(matrixNode, levels)
        .createSelectionId();

    // create button element
    let button = document.createElement("button");
    // display node value/name of the button's text
    button.innerText = matrixNode.value.toString();

    // add event listener on click
    button.addEventListener("click", (event) => {
        // call select method in the selection manager
        this.selectionManager.select(selectionID);
    });

    // display context menu on click
    button.addEventListener("contextmenu", (event) => {
        // call showContextMenu method to display context menu on the visual
        this.selectionManager.showContextMenu(selectionID, {
            x: event.clientX,
            y: event.clientY
        });
        event.preventDefault();
    });

    div.appendChild(button);

    if (matrixNode.children) {
        // ...
    }
}
```

Löschen Sie `div`-Elemente, bevor Sie Elemente nochmals rendern:

```typescript
public update(options: VisualUpdateOptions) {
    // ...
    const treeWalker = (matrixNode: DataViewMatrixNode, index: number, levels: DataViewHierarchyLevel[], div: HTMLDivElement)  => {
        // ...
    }

    // remove old elements
    // to better performance use D3js pattern:
    // https://d3js.org/#enter-exit
    while (this.rowsDiv.firstChild) {
        this.rowsDiv.removeChild(this.rowsDiv.firstChild);
    }
    // create label for row elements
    const prow = document.createElement("p");
    prow.innerText = "Rows";
    this.rowsDiv.appendChild(prow);

    while (this.colsDiv.firstChild) {
        this.colsDiv.removeChild(this.colsDiv.firstChild);
    }
    // create label for columns elements
    const pcol = document.createElement("p");
    pcol.innerText = "Columns";
    this.colsDiv.appendChild(pcol);

    // render elements for rows
    const rowRoot: DataViewMatrixNode = matrixDataView.rows.root;
    rowRoot.children.forEach((node, index) => treeWalker(node, index, matrixDataView.rows.levels, this.rowsDiv));

    // render elements for columns
    const colRoot = matrixDataView.columns.root;
    colRoot.children.forEach((node, index) => treeWalker(node, index, matrixDataView.columns.levels, this.colsDiv));
}
```

Im letzten Schritt sollte das Visual mit einem Kontextmenü angezeigt werden:

![Das Visual mit Drilldownunterstützung](media\drill-down-support\dev-visual-drilldown-demo.gif)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter [Grundlegendes zur Zuordnung von Datenansichten in Power BI-Visuals](dataview-mappings.md).
