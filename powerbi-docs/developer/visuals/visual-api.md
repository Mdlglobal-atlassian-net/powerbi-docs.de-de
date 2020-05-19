---
title: Visual-API
description: In diesem Artikel wird beschrieben, wie Sie IVisual-API für Power PI-Visuals verwenden.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302964"
---
# <a name="visual-api"></a>Visual-API
Alle visuellen Elemente beginnen mit einer Klasse, mit der die `IVisual`-Schnittstelle implementiert wird. Sie können der Klasse einen beliebigen Namen geben. Es muss nur genau eine Klasse für die Implementierung der `IVisual`-Schnittstelle vorhanden sein.

> [!NOTE]
> Der Name der visuellen Klasse muss mit dem in der Datei *pbiviz.json* definierten Namen identisch sein.

Im Folgenden sehen Sie ein Beispiel für eine visuelle Klasse einschließlich der zu implementierenden Methoden:

* `constructor`, ein Standardkonstruktor zum Initialisieren des Zustands des visuellen Elements.
* `update`, zum Aktualisieren der Daten des visuelles Elements
* `enumerateObjectInstances`, zum Zurückgeben von Objekten, um den Eigenschaftenbereich (Formatierungsoptionen) aufzufüllen, in dem Sie sie nach Bedarf ändern können
* `destroy`, ein Standarddestruktor für Bereinigungen

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>Konstruktor

Der Konstruktor der visuellen Klasse wird beim Instanziieren des visuellen Elements aufgerufen. Er kann für alle vom visuellen Element benötigten Setupvorgänge verwendet werden.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, ein Verweis auf das DOM-Element, das das visuelle Element enthält
* `host: IVisualHost`, eine Reihe von Eigenschaften und Diensten, die für die Interaktion mit dem visuellen Host (Power BI) verwendet werden können

   `IVisualHost` enthält die folgenden Dienste:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, generiert und speichert Metadaten für auswählbare Elemente in der Visualisierung
   * `createSelectionManager`, erstellt die Kommunikationsbrücke, die verwendet wird, um den Host des visuellen Elements über Änderungen im Selection-Zustand zu benachrichtigen. Weitere Informationen finden Sie unter [Selection-API](./selection-api.md).
   * `createLocalizationManager`, generiert einen Manager zur Unterstützung der [Lokalisierung](./localization.md)
   * `allowInteractions: boolean`, ein boolesches Kennzeichen, das darauf hinweist, ob das visuelle Element interaktiv ist
   * `applyJsonFilter`, wendet bestimmte Filtertypen an. Siehe hierzu [Filter-API](./filter-api.md).
   * `persistProperties`, ermöglicht es Benutzern, Eigenschaften beizubehalten und zusammen mit der Definition des visuellen Elements zu speichern, sodass sie beim nächsten erneuten Laden verfügbar sind
   * `eventService`, gibt einen [Ereignisdienst](./event-service.md) zurück zur Unterstützung von **Renderingereignissen**
   * `storageService`, gibt einen Dienst zurück zur Unterstützung der Verwendung von [lokalem Speicher](./local-storage.md) im visuellen Element
   * `authenticationService`, generiert einen Dienst zur Unterstützung der Benutzerauthentifizierung
   * `tooltipService`, gibt einen [QuickInfo-Dienst](./add-tooltips.md) zurück zur Unterstützung der Verwendung von QuickInfos im visuellen Element
   * `launchUrl`, unterstützt das [Starten der URL](./launch-url.md) auf der nächsten Registerkarte
   * `locale`, gibt eine Zeichenfolge des Gebietsschemas zurück. Siehe hierzu [Lokalisierung](./localization.md).
   * `instanceId`, gibt eine Zeichenfolge zurück zum Identifizieren der aktuellen visuellen Instanz
   * `colorPalette`, gibt die Farbpalette zurück, die zum Anwenden von Farben auf Ihre Daten benötigt wird
   * `fetchMoreData`, unterstützt die Verwendung einer größeren Datenmenge als dies das Standardlimit (1.000 Zeilen) vorsieht
   * `switchFocusModeState`, unterstützt die Änderung des Fokusmoduszustands

## <a name="update"></a>aktualisieren

Alle visuellen Elemente müssen eine Methode zum öffentlichen Aktualisieren implementieren, die immer dann aufgerufen wird, wenn eine Änderung in der Daten -oder Hostumgebung vorgenommen wird.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, Dimensionen des Viewports, in dem das visuelle Element gerendert werden soll
* `dataViews: DataView[]`, das DataView-Objekt, das alle zum Rendering des visuelles Elements benötigten Daten enthält (in der Regel wird die kategorische Eigenschaft unter DataView verwendet).
* `type: VisualUpdateType`, Kennzeichen, die den Typ der Aktualisierung angeben (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**)
* `viewMode: ViewMode`, Kennzeichen, die den Ansichtsmodus des visuellen Elements angeben (**View** | **Edit** | **InFocusEdit**)
* `editMode: EditMode`, Kennzeichen, die den Bearbeitungsmodus des visuellen Elements angeben (**Standard** | **Advanced**) (Wenn das visuelle Element **AdvancedEditMode** unterstützt, werden dessen erweiterte UI-Steuerelemente nur dann gerendert, wenn **editMode** auf **Advanced** festgelegt ist. Weitere Informationen finden Sie unter [AdvancedEditMode](./advanced-edit-mode.md)).
* `operationKind?: VisualDataChangeOperationKind`, Kennzeichen, die den Typ der Datenänderung angeben (**Create** | **Append**)
* `jsonFilters?: IFilter[]`, Sammlung von angewendeten JSON-Filtern
* `isInFocus?: boolean`, Kennzeichen, das angibt, ob sich das visuelle Element im Fokusmodus befindet
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Diese Methode wird für jedes in den Funktionen aufgelistete Objekt aufgerufen. Wenn Sie die Optionen (derzeit nur den Namen) verwenden, wird ein `VisualObjectInstanceEnumeration`-Objekt mit Informationen zur Anzeige dieser Eigenschaft zurückgegeben.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, Name des Objekts

## <a name="destroy-optional"></a>destroy `optional`

Die Funktion „destroy“ (Löschen) wird aufgerufen, wenn das visuelle Element nicht geladen ist. Sie kann für Bereinigungsaufgaben verwendet werden, z. B. zum Entfernen von Ereignislistenern.

``` typescript
public destroy(): void
```

> [!Note]
> Power BI ruft die Funktion `destroy` in der Regel nicht auf, da es schneller ist, den gesamten IFRAME mit dem visuellen Element zu entfernen.
