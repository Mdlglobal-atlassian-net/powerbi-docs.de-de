---
title: Änderungsprotokoll für Power BI-Visuals-API
description: In diesem Artikel werden die wichtigsten Änderungen in verschiedenen Versionen der Power BI Visuals-API beschrieben.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: fa8759d7edb519240140263bcd01bfdddd9c7d86
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141055"
---
# <a name="power-bi-visuals-api-changelog"></a>Änderungsprotokoll für Power BI-Visuals-API
Diese Seite enthält eine Kurzübersicht über die API-Versionen. Die hier aufgeführten Versionen gelten als stabil und werden nicht geändert.

## <a name="api-v26"></a>API 2.6
  * Fügt **isInFocus** zur Aktualisierungsoption und die **switchFocusModeState**-Methode zum Host des Visuals hinzu
  * Unterstützt die Anpassung von **Zwischensummen**

## <a name="api-v25"></a>API 2.5
  * Unterstützt den **[Bereich „Analyse“](./analytics-pane.md)**
  * Unterstützt die `SelectionIdBuilder`-Methoden **withMatrixNode** und **withTable**
  * Keine Unterstützung mehr für die `DataRepetitionSelector`-Schnittstelle, die durch die `data.CustomVisualOpaqueIdentity`-Schnittstelle ersetzt wurde

## <a name="api-v23"></a>API 2.3
  * **[API der Angebotsseite](./landing-page.md)**
  * **[API für lokalen Speicher](./local-storage.md)**
  * **[Tupelfilter-API (Filter für mehrere Spalten)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API für das Rendern von Ereignissen](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v22"></a>API 2.2
  * Unterstützt das **[Wiederherstellen eines JSON-Filters aus DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[ContextMenu-API](./context-menu.md)**

## <a name="api-v21"></a>API 2.1
  * Leistungsverbesserungen:
    * Schnellere Ladezeiten
    * Kleinerer Bedarf an Arbeitsspeicher
    * Optimierte Daten- und Ereignistransaktionen  

**Versionshinweise**
* Umgestaltete Filter-APIs werden in API 2.2 verfügbar sein und von API 2.1 nicht unterstützt.
* Visuals erhalten nur den dataView-Typ, der in ihren Einstellungen deklariert wurde. Grafiken, die mehrere dataView-Typen verwendet haben, funktionieren als Folge dieses Updates nicht mehr.
* Nicht mehr unterstützt wird die `DataViewScopeIdentity`-Schnittstelle, die durch die `data.DataRepetitionSelector`-Schnittstelle ersetzt wurde. Wenn Sie die Schlüsseleigenschaft der `DataViewScopeIdentity`-Schnittstelle verwendet haben, können Sie sie durch `JSON.stringify(identity)` ersetzen.
* `undefined` wird innerhalb von dataView durch `null` ersetzt. Wenn mit `var item in myArray` eine Iteration über ein Array erfolgt, wird zwar `undefined`, aber nicht `null` übersprungen. Visuals mit diesem Muster funktionieren aufgrund dieses Updates möglicherweise nicht mehr. Prüfen Sie in Arrays unbedingt auf `null`:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* Die `proto`-Eigenschaft speichert innerhalb von dataView keine ausgeblendeten Metadaten/Daten mehr. Visuals, die über `proto` auf Eigenschaften zugreifen, funktionieren aufgrund dieses Updates möglicherweise nicht mehr.

## <a name="api-v113"></a>API 1.13
* Unterstützt **[Slicer synchronisieren](./enable-sync-slicers.md)** . Beachten Sie, dass dies aufgrund des aktuellen Zustands des PBI-Codes nur für Slicer für Einzelfelder funktioniert. [Hier erfahren Sie mehr](/power-bi/desktop-slicers).
* Barrierefreiheit: [Unterstützung für hohen Kontrast](./high-contrast-support.md) 
* Barrierefreiheit: Flag „Tastaturfokus“ zulassen

## <a name="api-v112"></a>API 1.12
* Unterstützt Designs
* Unterstützt **[fetchMoreData](./fetch-more-data.md)** . Beachten Sie, dass für die**API zum Abrufen zusätzlicher Daten** der harte Grenzwert von 30.000 Datenpunkten nicht mehr gilt.
* **[Canvas-QuickInfo-API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v111"></a>API 1.11
* **[FilterManager-API](./filter-api.md)**
* Unterstützt **[Lesezeichen](./bookmarks-support.md)** 

## <a name="api-v110"></a>API 1.10
* Fügt `ILocalizationManager` hinzu
* **Authentifizierungs-API**

## <a name="api-v19"></a>API 1.9
* **[launchUrl-API](./launch-url.md)**

## <a name="api-v18"></a>API 1.8
* Unterstützt den neuen Typ **fillRule** (Gradient) im Schema „capabilities“
* Unterstützt die **rule**-Eigenschaft im Schema „capabilities“ für Objekteigenschaften

## <a name="api-v17"></a>API 1.7
* Unterstützt **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API 1.6.2
* Unterstützt **[Bearbeitungsmodus](./advanced-edit-mode.md)** , damit das Visual in den visualinternen Bearbeitungsmodus wechseln kann
* Unterstützt **[Interaktive (HTML-) R Power BI-Visuals](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** basierend auf HTML

## <a name="api-v150"></a>API 1.5.0
* Unterstützt **[Interaktionen zulassen](./visuals-interactions.md)** für die Interaktivität von Visuals

## <a name="api-v140"></a>API 1.4.0
* Unterstützt **[Lokalisierung](./localization.md)**

## <a name="api-v130"></a>API 1.3.0
* Unterstützt **[QuickInfo](./add-tooltips.md)**

## <a name="api-v120"></a>API 1.2.0
* Fügt **colorPalette** hinzu, um die Farben zu verwalten, die in Ihrem Visual verwendet werden.
* Unterstützt **Mehrfachauswahl**: selectionManager kann ein Array von `SelectionId`akzeptieren.
* Unterstützt **[R-Visuals](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** mithilfe von R-Skripts

## <a name="api-v110"></a>API 1.1.0
* Unterstützt das Debuggen des Visuals in iFrame
* Fügt schlanke Sandbox mit schnellerer iFrame-Initialisierung hinzu
* Behebt das Problem [Capabilities.objects unterstützt nicht den Typ „text“](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)
* Unterstützt `pbiviz update` zum Aktualisieren der Typdefinitionen und des Schemas der Visual-API
* Unterstützt das Flag `--api-version` in `pbiviz new`, um Visuals mit einer bestimmten API-Version zu erstellen
* Unterstützt das Alpha-Release von API 1.2.0

**Host des Visuals**
* Fügt **createSelectionIdBuilder** hinzu, um eindeutige Bezeichner für die Datenauswahl zu erstellen
* Fügt **createSelectionManager** hinzu, um den Auswahlzustand des Visuals zu verwalten, und überträgt Änderungen an den Host des Visuals
* Fügt ein Array standardmäßiger **Farben** zur Verwendung in Visuals hinzu

## <a name="api-v100"></a>API 1.0.0
* Erstes Release der API
