---
title: Benutzerdefinierte Layouts für eingebettete Inhalte aus Power BI
description: Informieren Sie sich über benutzerdefinierte Layouts für Power BI-Inhalte, die Sie in Ihre Anwendung einbetten.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: reference
ms.date: 12/19/2017
ms.openlocfilehash: e114c208093c9f3401c43e9ea44502e65d6d84fd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79493202"
---
# <a name="custom-layouts"></a>Benutzerdefinierte Layouts

Verwenden Sie benutzerdefinierte Layouts, um einen Bericht mit einem anderen Layout als im ursprünglichen Bericht einzubetten. Indem Sie ein neues Layout definieren, können Sie eine abweichende Seitengröße festlegen sowie die Größe, Position und Sichtbarkeit von Visuals steuern.

Um ein benutzerdefiniertes Layout zu definieren, definieren Sie ein Objekt für benutzerdefinierte Layouts und übergeben dieses an das Einstellungsobjekt in einer Einbettungskonfiguration. Außerdem legen Sie LayoutType auf Custom fest. Weitere Informationen finden Sie unter [Details zur Einbettungskonfiguration](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details).

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom,
            customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Objektdefinition

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: Mit pageSize steuern Sie die Größe des Zeichenbereichs (d.h. den weißen Bereich eines Berichts).
- `displayOptions`: Mögliche Werte: FitToWidth, FitToPage und ActualSize. Hiermit wird gesteuert, wie der Zeichenbereich skaliert wird, damit er in den iFrame passt.
- `pagesLayout`: Steuert das Layout für jedes Visual. Weitere Informationen finden Sie unter PagesLayout.

## <a name="pages-layout"></a>Seitenlayout

Indem Sie ein Seitenlayoutobjekt definieren, bestimmen Sie im Grunde ein Layout für jede Seite und ein Layout für jedes Visual auf den einzelnen Seiten.
PageLayout ist optional. Wenn Sie für eine Seite kein Layout definieren, wird das Standardlayout angewendet (das im Bericht gespeichert ist).

pagesLayout ist eine Zuordnung des Seitennamens zum PageLayout-Objekt. Definition:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout enthält eine Zuordnung visueller Layouts, die den Namen jedes Visuals einem Visuallayoutobjekt zuordnet:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Visuallayout

Um eine Visuallayout zu definieren, übergeben Sie eine neue Position und Größe und einen neuen Sichtbarkeitszustand.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: Definiert die neue Position des Visuals.
- `width`: Definiert die neue Größe des Visuals.
- `displayState`: Definiert die Sichtbarkeit des Visuals.

## <a name="update-layout"></a>Aktualisieren des Layouts

Mit der updateSettings-Methode können Sie jederzeit während des Ladens des Berichts das Berichtslayout aktualisieren. Weitere Informationen finden Sie unter [Aktualisieren der Einstellungen](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Codebeispiel

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;

var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom,
            customLayout: {
                pageSize: {
                    type: models.PageSizeType.Custom,
                    width: 1600,
                    height: 1200
                }
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};

// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');

// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);
```

## <a name="see-also"></a>Siehe auch

[Einbetten von Power BI-Dashboards, -Berichten und -Kacheln](embed-sample-for-customers.md)   
[Fragen an die Power BI-Community](https://community.powerbi.com/)
