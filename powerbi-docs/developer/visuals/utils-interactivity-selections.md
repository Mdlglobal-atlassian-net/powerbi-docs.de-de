---
title: Interaktivitätshilfsprogramme für Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie Auswahlmöglichkeiten in Power BI-Visuals mithilfe von Interaktivitätshilfsprogrammen hinzufügen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379258"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Interaktivitätshilfsprogramme für Power BI-Visuals

Interaktivitätshilfsprogramme (`InteractivityUtils`) bestehen aus einer Reihe von Funktionen und Klassen, die für die Vereinfachung der Implementierung für die übergreifende Auswahl und Kreuzfilterung verwendet werden können.

> [!NOTE]
> Die neuen Updates der Interaktivitätshilfsprogramme unterstützen nur die neueste Toolversion (ab 3.x.x).

## <a name="installation"></a>Installation

1. Führen Sie den folgenden Befehl im Verzeichnis mit Ihrem aktuellen Power BI-Visualprojekt aus, um das Paket zu installieren.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Wenn Sie Version 3.0 oder höher oder des Tools verwenden, installieren Sie `powerbi-models`, um Abhängigkeiten aufzulösen.

    ```bash
    npm install powerbi-models --save
    ```

3. Wenn Sie Interaktivitätshilfsprogramme verwenden möchten, müssen Sie die erforderliche Komponente in den Quellcode des Power BI-Visuals importieren.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Einschließen der CSS-Dateien

Um das Paket mit Ihrem Power BI-Visual zu verwenden, importieren Sie die folgende CSS-Datei in Ihre `.less`-Datei.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importieren Sie die CSS-Datei als `.less`-Datei, da das Tool für Power BI-Visuals die externen CSS-Regeln umschließt.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint-Eigenschaften

Normalerweise enthalten Datenpunkte Auswahlmöglichkeiten und Werte. Die Schnittstelle erweitert die `SelectableDataPoint`-Schnittstelle.

`SelectableDataPoint` enthält bereits Eigenschaften wie nachstehend beschrieben.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definieren einer Schnittstelle für Datenpunkte

1. Erstellen Sie eine Instanz von Interaktivitätshilfsprogrammen, und speichern Sie anschließend das Objekt als Eigenschaft des Visuals.

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. Erweitern Sie die Klasse mit dem Basisverhalten.

    > [!NOTE]
    > `BaseBehavior` wurde in [Version 5.6.x der Interaktivitätshilfsprogramme](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) eingeführt. Wenn Sie eine ältere Version verwenden, erstellen Sie die Verhaltensklasse wie im nachstehenden Beispiel.

3. Definieren Sie die Schnittstelle für Optionen der Verhaltensklasse.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Definieren Sie eine Klasse für `visual behavior`. Oder erweitern Sie die `BaseBehavior`-Klasse.

    **Definieren einer Klasse für `visual behavior`**

    Die Klasse ist für das Verarbeiten der Mausereignisse `click` und `contextmenu` zuständig.

    Wenn ein Benutzer auf Datenelemente klickt, ruft das Visual den Auswahlhandler auf, um Datenpunkte auszuwählen. Wenn der Benutzer auf das Hintergrundelement des Visuals klickt, wird der Handler zum Aufheben der Auswahl aufgerufen.

    Die Klasse verfügt über die folgenden entsprechenden Methoden:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **Erweitern der `BaseBehavior`-Klasse**

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. Um Klicks auf Elemente zu verarbeiten, rufen Sie die `on`-Methode des Auswahlobjekts *d3* auf. Dies gilt auch für `elementsSelection` und `clearCatcherSelection`.

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. Fügen Sie ähnliche Handler für das `contextmenu`-Ereignis zum Aufrufen der `showContextMenu`-Methode des Auswahl-Managers hinzu.

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. Um Handlern Funktionen zuzuweisen, rufen die Interaktivitätshilfsprogramme die `bindEvents`-Methode auf. Fügen Sie der `bindEvents`-Methode die folgenden Aufrufe hinzu:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. Die `renderSelection`-Methode wird zum Aktualisieren des Status von Visuals von Elementen im Diagramm verwendet. Hier ist eine Beispielimplementierung von `renderSelection`.

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. Im letzten Schritt wird eine Instanz von `visual behavior` erstellt und die `bind`-Methode der Instanz von Interaktivitätshilfsprogrammen aufgerufen.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` ist das *d3*-Auswahlobjekt, das alle auswählbaren Elemente im Visual darstellt.
    * `select(this.target)` ist das *d3*-Auswahlobjekt, das die DOM-Hauptelemente im Visual darstellt.
    * `this.categories` sind Datenpunkte mit Elementen, wobei die Schnittstelle `VisualDataPoint` oder `categories: VisualDataPoint[];` ist.
    * `this.behavior` ist eine neue Instanz von `visual behavior`, die im Konstruktor des Visuals erstellt wird, wie unten gezeigt.

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>Nächste Schritte

* [Verarbeiten von Auswahlmöglichkeiten bei wechselnden Lesezeichen](bookmarks-support.md#visuals-with-selection)

* [Hinzufügen des Kontextmenüs für Datenpunkte von Visuals](context-menu.md)

* [Verwenden des Auswahl-Managers zum Hinzufügen von Auswahlmöglichkeiten für Power BI-Visuals](selection-api.md).
