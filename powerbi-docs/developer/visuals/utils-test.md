---
title: Einführung in die Verwendung von Testhilfsprogrammen in Power BI-Visuals
description: In diesem Artikel wird erläutert, wie Sie Testhilfsprogramme verwenden, um Mocks zu vereinfachen. Außerdem wird die Verwendung bestimmter Methoden bei Komponententests für Power BI-Visuals beschrieben.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196604"
---
# <a name="power-bi-visuals-test-utils"></a>Testhilfsprogramme für Power BI-Visuals

Dieser Artikel unterstützt Sie bei der Installation, dem Import und der Verwendung der Testhilfsprogramme für Power BI-Visuals. Diese Testhilfsprogramme können für Komponententests verwendet werden. Zu den Programmen gehören Mocks und Methoden für Elemente wie Datenansichten, Auswahl und Farbschemas.

## <a name="requirements"></a>Anforderungen

Für die Verwendung dieses Pakets muss Folgendes installiert werden:

* [Node.js](https://nodejs.org). Es wird empfohlen, die TLS-Version zu verwenden.
* [npm](https://www.npmjs.com/) (Version 3.0.0 oder höher).
* Das Packet [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools).

## <a name="installation"></a>Installation

Führen Sie den folgenden Befehl in Ihrem Verzeichnis mit Power BI-Visuals aus, um Testhilfsprogramme zu installieren und die dazugehörige Abhängigkeit Ihrer Datei *package.json* hinzuzufügen:

```bash
npm install powerbi-visuals-utils-testutils --save
```

Im Folgenden erhalten Sie Beschreibungen und Beispiele für die öffentliche API der Testhilfsprogramme.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Wird von **VisualBuilder** bei Komponententests mit den am häufigsten verwendeten Methoden `build`, `update` und `updateRenderTimeout` verwendet. 

Die `build`-Methode gibt eine erstellte Instanz des Visuals zurück.

Die `enumerateObjectInstances`- und `updateEnumerateObjectInstancesRenderTimeout`-Methoden sind erforderlich, um Änderungen am Bucket und den Formatierungsoptionen zu überprüfen.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Weitere Beispiele finden Sie unter [Erstellen des Visualinstanz-Generators](./unit-tests-introduction.md#create-a-visual-instance-builder) und auf dieser [GitHub-Seite](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Wird von **TestDataViewBuilder** verwendet. Dieses Modul stellt eine in der `createCategoricalDataViewBuilder`-Methode verwendete **CategoricalDataViewBuilder**-Klasse bereit. Es gibt auch Schnittstellen und Methoden an, die erforderlich sind, um mit simulierten **DataView**-Klassen in Komponententests arbeiten zu können.

* `withValues` fügt statische Datenreihen in Spalten hinzu, und `withGroupedValues` fügt dynamische Datenreihen in Spalten hinzu.

  Wenden Sie nicht dynamische Datenreihen und statische Datenreihen in **DataViewCategorical** eines Visuals an. Sie können sie nur zusammen in der **DataViewCategorical**-Abfrage verwenden, wo **DataViewTransform** sie in eigenständige **DataViewCategorical**-Objekte eines Visuals teilen soll.

* `build` gibt DataView mit Metadaten und DataViewCategorical zurück.

  `build` gibt **Nicht definiert** zurück, wenn die Kombination der Parameter nicht zulässig ist, z. B. wenn sowohl dynamische als auch statische Datenreihen bei der Erstellung der **DataView**-Klasse des Visuals eingeschlossen werden.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Wird für die Erstellung von **VisualData** bei Komponententests verwendet. Wenn Daten in Datenfeldbuckets platziert werden, generiert Power BI ein kategorisches **DataView**-Objekt basierend auf den Daten. **TestDataViewBuilder** unterstützt die Simulierung der Erstellung des kategorischen **DataView**-Objekts.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Im Folgenden finden Sie die am häufigsten verwendeten Schnittstellen bei der Erstellung von `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Weitere Beispiele finden Sie unter [Hinzufügen statischer Daten zu Komponententests](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) und auf dieser [GitHub-Seite](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Mocks

### <a name="mockivisualhost"></a>MockIVisualHost

Implementiert **IVisualHost**, um Power BI-Visuals ohne externe Abhängigkeiten wie dem Power BI-Framework zu testen.

Zu den geeigneten Methoden gehören `createSelectionIdBuilder`, `createSelectionManager` und `createLocalizationManager` sowie Getter für Eigenschaften.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` erstellt eine Instanz von **IVisualHost** und gibt sie zurück, genau genommen **MockIVisualHost**.
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Beispiel
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> Bei **MockIVisualHost** handelt es sich um eine Fakeimplementierung von **IVisualHost**. MockIVisualHost sollte nur mit Komponententests verwendet werden.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementiert **IColorPalette**, um Power BI-Visuals ohne externe Abhängigkeiten wie dem Power BI-Framework zu testen.

**MockIColorPalette** stellt hilfreiche Eigenschaften für die Überprüfung des Farbschemas oder des Modus mit hohem Kontrast bei Komponententests bereit.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` erstellt eine Instanz von **IColorPalette** und gibt sie zurück, genau genommen **MockIColorPalette**.
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Beispiel
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> Bei **MockIColorPalette** handelt es sich um eine Fakeimplementierung von **IColorPalette**. MockIColorPalette sollte nur mit Komponententests verwendet werden.

### <a name="mockiselectionid"></a>MockISelectionId

Implementiert **ISelectionId**, um Power BI-Visuals ohne externe Abhängigkeiten wie dem Power BI-Framework zu testen.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` erstellt eine Instanz von **ISelectionId** und gibt sie zurück, genau genommen **MockISelectionId**.
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Beispiel
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> Bei **MockISelectionId** handelt es sich um eine Fakeimplementierung von **ISelectionId**. MockISelectionId sollte nur mit Komponententests verwendet werden.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementiert **ISelectionIdBuilder**, um Power BI-Visuals ohne externe Abhängigkeiten wie dem Power BI-Framework zu testen. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` erstellt eine Instanz von **ISelectionIdBuilder** und gibt sie zurück, genau genommen **MockISelectionIdBuilder**.
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Beispiel
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> Bei **MockISelectionIdBuilder** handelt es sich um eine Fakeimplementierung von **ISelectionIdBuilder**. MockISelectionIdBuilder sollte nur mit Komponententests verwendet werden.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementiert **ISelectionManager**, um Power BI-Visuals ohne externe Abhängigkeiten wie dem Power BI-Framework zu testen. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` erstellt eine Instanz von **ISelectionManager** und gibt sie zurück, genau genommen **MockISelectionManager**.
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Beispiel
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> Bei **MockISelectionManager** handelt es sich um eine Fakeimplementierung von **ISelectionManager**. MockISelectionManager sollte nur mit Komponententests verwendet werden.

### <a name="mockilocale"></a>MockILocale

  Legt das Gebietsschema fest und ändert es entsprechend Ihrer Anforderungen während des Komponententestprozesses.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` erstellt eine Instanz von **MockILocale** und gibt sie zurück.
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simuliert `TooltipService` und führt entsprechend Ihrer Anforderungen während des Komponententestprozesses einen Aufruf dafür aus.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` erstellt eine Instanz von **MockITooltipService** und gibt sie zurück.
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` erstellt eine Instanz von **MockIAllowInteractions** und gibt sie zurück.
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Stellt grundlegende Funktionen von **LocalizationManager** bereit, die für Komponententests erforderlich sind.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` erstellt eine Instanz von **ILocalizationManager** und gibt sie zurück, genau genommen **MockILocalizationManager**.
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Beispiel
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simuliert die Verwendung von **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Erstellung von `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simuliert die Arbeit von **AuthenticationService**, indem ein simuliertes AAD-Token bereitgestellt wird.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` erstellt eine Instanz von **IAuthenticationService** und gibt sie zurück, genau genommen **MockIAuthenticationService**.
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Ermöglicht Ihnen die Verwendung von **ILocalVisualStorageService** mit demselben Verhalten wie **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` erstellt eine Instanz von **ILocalVisualStorageService** und gibt sie zurück, genau genommen **MockIStorageService**.
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` erstellt eine Instanz von **IVisualEventService** und gibt sie zurück, genau genommen **MockIEventService**.
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Hilfsprogramme

Zu Hilfsprogrammen gehören Hilfsmethoden für Komponententests von Power BI-Visuals, einschließlich Hilfsprogrammen zu Farben, Zahlen und Ereignissen.

- `renderTimeout` gibt ein Timeout zurück.
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` unterstützt das Festlegen der Fixierung bei Komponententests.
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Beispiel
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Hilfsmethoden zu Farben

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Gibt die folgende Struktur zurück:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` vergleicht **RgbColor**-Objekte, die aus Eingabezeichenfolgen analysiert wurden.
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` analysiert Farben aus Eingabezeichenfolgen und gibt sie über die angegebene Schnittstelle **RgbColor** zurück.
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Hilfsmethoden zu Zahlen

- `getRandomNumbers`generiert eine zufällige Zahl mithilfe von Minimal- und Maximalwerten. Sie können `exceptionList` angeben und eine Funktion bereitstellen, damit sich das Ergebnis ändert.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` stellt ein Array zufälliger Zahlen bereit, die von der `getRandomNumber`-Methode mit den angegebenen Minimal- und Maximalwerten generiert werden.
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Hilfsmethoden zu Ereignissen
Die folgenden Methoden werden für die Simulation von Webseitenereignissen bei Komponententests geschrieben.

- `clickElement` simuliert einen Klick auf das angegebene Element.
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` gibt ein **Touch**-Objekt zurück, um die Simulation eines Fingereingabeereignisses zu unterstützen.
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` gibt eine Liste simulierter **Touch**-Ereignisse zurück.
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` gibt **MouseEvent** zurück.
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` erstellt **MouseEvent** und gibt entsprechende Werte zurück.
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Hilfsmethoden zu D3-Ereignissen

Die folgenden Methoden werden verwendet, um D3-Ereignisse bei Komponententests zu simulieren.

- `flushAllD3Transitions` erzwingt, dass alle D3-Übergänge abgeschlossen werden.

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalerweise werden Übergänge mit keiner Verzögerung nach einer sofortigen Verzögerung (< 10ms) ausgeführt. Das kann jedoch zu einem kurzen Flimmern führen, wenn der Browser die Seite zweimal rendert. Einmal am Ende der ersten Ereignisschleife, ein zweites Mal sofort beim ersten Timerrückruf.
  >
  > Dieses Flimmern fällt im Internet Explorer sowie bei vielen Webansichten stärker auf, weshalb es für iOS vermieden werden sollte.
  > 
  > Indem die Timerwarteschlange am Ende der ersten Ereignisschleife geleert wird, können Sie Übergänge ohne Verzögerung sofort ausführen und das Flimmern so verhindern.

Die folgenden Methoden sind hier ebenfalls relevant:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Hilfsschnittstellen
Die folgende Schnittstelle und die folgenden Enumerationen werden in der Hilfsfunktion verwendet.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Schreiben von Komponententests für Webpack-basierte Power BI-Visuals und Komponententests mit `karma` und `jasmine` finden Sie unter [Tutorial: Hinzufügen von Komponententests zu Power BI-Visualprojekten](./unit-tests-introduction.md).
