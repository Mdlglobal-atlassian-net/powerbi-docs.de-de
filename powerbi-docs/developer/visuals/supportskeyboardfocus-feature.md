---
title: Das Feature supportsKeyboardFocus
description: In diesem Artikel werden die Verwendung des Features supportsKeyboardFocus in Power BI-Visuals und seine Anforderungen beschrieben.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: c8cf0f4e896b8a44764d1c363c597182f55d30b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276511"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>Verwenden des Features supportsKeyboardFocus

In diesem Artikel wird beschrieben, wie Sie das Feature `supportsKeyboardFocus` in Power BI-Visuals verwenden.
Das Feature `supportsKeyboardFocus` ermöglicht Ihnen, mit nur der Tastatur zu den Datenpunkten des Visuals zu navigieren.

Weitere Informationen zur Tastaturnavigation für Visuals finden Sie unter [Tastaturnavigation](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Beispiel

Öffnen Sie ein Visual, das das Feature `supportsKeyboardFocus` verwendet. Wählen Sie einen beliebigen Datenpunkt innerhalb des Visuals und dann die TAB-TASTE aus. Jedes Mal, wenn Sie die TAB-TASTE auswählen, wechselt der Fokus zum nächsten Datenpunkt. Wählen Sie die EINGABETASTE aus, um den markierten Datenpunkt auszuwählen.

![Beispiel für die Unterstützung des Tastaturfokus](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Anforderungen

Diese Feature erfordert mindestens die API-Version 2.1.0.

Es kann auf alle Visuals mit Ausnahme von Bildvisuals angewendet werden.

## <a name="usage"></a>Verwendung

Um das Feature `supportsKeyboardFocus` zu verwenden, fügen Sie den folgenden Code in die Datei *capabilities.json* Ihres Visuals ein.
Diese Fähigkeit ermöglicht es dem Visual, den Fokus per Tastaturnavigation zu erhalten.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Features für Barrierefreiheit finden Sie unter [Entwerfen von Power BI-Berichten für die Barrierefreiheit](../../create-reports/desktop-accessibility-creating-reports.md).

Informationen zum Ausprobieren der Power BI-Entwicklung finden Sie unter [Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md).
