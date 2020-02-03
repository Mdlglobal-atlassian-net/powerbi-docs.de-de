---
title: Rendern von Ereignissen in Power BI-Visuals
description: Power BI kann von Power BI-Visuals benachrichtigt werden, dass sie für den Export in PowerPoint oder eine PDF-Datei bereit sind.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 873968a89a230171d8fecba81a7d528767ee7077
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819144"
---
# <a name="render-events-in-power-bi-visuals"></a>Rendern von Ereignissen in Power BI-Visuals

Die neue API umfasst drei Methoden (`started`, `finished` oder `failed`), die während des Renderings aufgerufen werden müssen.

Beim Start des Renderings wird vom Code des Power BI-Visuals die `renderingStarted`-Methode aufgerufen, um anzugeben, dass der Renderingvorgang gestartet wurde.

Wenn das Rendering erfolgreich abgeschlossen ist, wird im Code des Power BI-Visuals sofort die `renderingFinished`-Methode aufgerufen, um die Listener (hauptsächlich für *In PDF exportieren* und *Nach PowerPoint exportieren*) zu benachrichtigen, dass das Image des Visuals bereit ist für den Export.

Wenn während des Prozesses ein Problem auftritt, kann das Power BI-Visual nicht erfolgreich gerendert werden. Im Code des Power BI-Visuals muss die `renderingFailed`-Methode aufgerufen werden, durch die der Listener benachrichtigt wird, dass der Renderingvorgang noch nicht abgeschlossen wurde. Diese Methode stellt zusätzlich eine optionale Zeichenfolge zur Erläuterung der Fehlerursache bereit.

## <a name="usage"></a>Verwendung

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Beispiel: Das Visual zeigt keine Animationen an.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Beispiel: Das Visual zeigt Animationen an.

Wenn das Visual Animationen oder asynchrone Funktionen für das Rendering aufweist, muss nach der Animation oder innerhalb der asynchronen Funktion die `renderingFinished`-Methode aufgerufen werden.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Rendern von Ereignissen für die Zertifizierung von Visuals

Eine Anforderung für die Zertifizierung von Visuals besteht darin, dass das Visual das Rendern von Ereignissen unterstützen muss. Weitere Informationen finden Sie unter [certification requirements](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements) (Zertifizierungsanforderungen).
