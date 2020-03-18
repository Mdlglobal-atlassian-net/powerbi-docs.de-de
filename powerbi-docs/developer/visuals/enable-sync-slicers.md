---
title: Aktivieren der Funktion „Slicer synchronisieren“ in Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie die Funktion „Slicer synchronisieren“ zu Power BI-Visuals hinzugefügt werden kann.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 88e7e4b83f303f2b366f276b5020194f55f21f25
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380715"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Synchronisieren von Slicern in Power BI-Visuals

Zur Unterstützung der Funktion [Slicer synchronisieren](https://docs.microsoft.com/power-bi/desktop-slicers) muss die benutzerdefinierte Slicer-Visual API-Version 1.13 oder höher verwenden werden.

Außerdem müssen Sie wie im folgenden Code veranschaulicht die Option in der Datei *capabilities.json* aktivieren:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Nachdem Sie die Datei *capabilities.json* aktualisiert haben, können Sie den Optionsbereich **Slicers synchronisieren** anzeigen, wenn Sie Ihr benutzerdefiniertes Slicer-Visual auswählen.

> [!NOTE]
> Die Funktion „Slicer synchronisieren“ unterstützt nicht mehr als ein Feld. Wenn Ihr Slicer mehr als ein Feld (**Kategorie** oder **Measure**) aufweist, ist die Funktion deaktiviert.

![Der Bereich „Slicer synchronisieren“](media/enable-sync-slicers/sync-slicers-panel.png)

Im Bereich **Slicer synchronisieren** sehen Sie, dass die Sichtbarkeit und Filterung des Slicers auf mehrere Berichtsseiten angewendet werden können.
