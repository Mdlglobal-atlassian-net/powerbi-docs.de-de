---
title: Das Feature supportsMultiVisualSelection
description: In diesem Artikel werden die Verwendung des Features supportsMultiVisualSelection in Power BI-Visuals und seine Anforderungen beschrieben.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272693"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Verwenden des Features supportsMultiVisualSelection

Das Feature `supportsMultiVisualSelection` ermöglicht Ihnen, die Auswahl in mehreren Visuals in einem Bericht zu verwenden.

## <a name="example"></a>Beispiel

Wählen Sie in einem Bericht mit mehr als einem Visual zwei Werte aus, damit diese Werte auch für andere Visuals gelten. Wählen Sie beispielsweise im [Analysebeispiel für den Einzelhandel](../../create-reports/sample-retail-analysis.md) in einem Visual **Fashions Direct** aus. Wählen Sie STRG-TASTE und **Jan** in einem anderen Visual aus. Im Bericht gilt Ihre Auswahl für die anderen Visuals, die dieses Feature unterstützen. Andere Visualisierungen sind nun auf **Fashions Direct** und **Jan** begrenzt.

## <a name="requirements"></a>Anforderungen

Diese Feature erfordert mindestens die API-Version 3.2.0.

Sie können dieses Feature nicht auf Bildvisuals anwenden. Sie können es nicht auf einige erweiterte Visuals wie Haupttreiber, Analysebaum, Visuals für Fragen und Antworten, Textfeld und Messdiagramme anwenden.

## <a name="usage"></a>Verwendung

Um das Feature `supportsMultiVisualSelection` zu verwenden, fügen Sie den folgenden Code in die Datei `capabilities.json` Ihres Visuals ein.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Power BI-Konzepten finden Sie unter [Visuals in Power BI](power-bi-visuals-concept.md).

Informationen zum Ausprobieren der Power BI-Entwicklung finden Sie unter [Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md).
