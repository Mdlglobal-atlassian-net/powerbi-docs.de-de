---
title: Hinzufügen einer Landing Page zu Ihren Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie eine Landing Page zu Power BI-Visuals hinzugefügt werden kann.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 6f1590d5635ed6e55833350027c52379e5d7cf51
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379956"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Hinzufügen einer Landing Page zu Ihren Power BI-Visuals

Mit API 2.3.0 können Sie eine Landing Page zu Ihren Power BI-Visuals hinzufügen. Fügen Sie dazu `supportsLandingPage` den Funktionen hinzu, und legen Sie sie auf „true“ fest. Durch diese Aktion wird Ihr Visual initialisiert und aktualisiert, bevor Sie Daten hinzufügen. Da das Visual kein Wasserzeichen mehr anzeigt, können Sie Ihre eigene Landing Page so gestalten, dass Sie im Visual angezeigt wird, solange Sie keine Daten enthält.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Ein Beispiel für eine Landing Page ist in der folgenden Abbildung dargestellt:

![Screenshot einer Landing Page](media/landing-page/app-landing-page.png)
