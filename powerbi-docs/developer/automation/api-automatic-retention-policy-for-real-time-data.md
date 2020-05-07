---
title: Power BI-APIs mit automatischer Aufbewahrungsrichtlinie für Echtzeitdaten
description: Erfahren Sie mehr über die automatische Aufbewahrungsrichtlinie im Power BI-Dienst.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 3ac4c28b3f07cb1a19e241089b54ee4594a7a7dd
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378292"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Automatische Beibehaltungsrichtlinie für Echtzeitdaten

Die automatische Beibehaltungsrichtlinie im Power BI-Dienst ist eine Abfragezeichenfolge, die eine standardmäßige Beibehaltungsrichtlinie zum automatischen Bereinigen veralteter Daten aktiviert, während ein konstanter Fluss neuer Daten in das Dashboard gewahrt bleibt. Die erste Aufbewahrungsrichtlinie wird als *FIFO* (First In, First Out) bezeichnet. Wenn diese Richtlinie aktiviert ist, werden die Daten in einer Tabelle gesammelt, bis max. 200.000 Zeilen erreicht sind. Sobald die Daten über 200.000 Zeilen hinausgehen, werden die ältesten Zeilen aus dem Dataset gelöscht. Dadurch werden zwischen 200.000 und 210.000 Zeilen mit ausschließlich den neuesten Daten beibehalten.  
  
<center>

![Beibehaltungsrichtlinie](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Die Beibehaltungsrichtlinien werden beim ersten Erstellen Ihrer Datasets aktiviert. Dazu müssen Sie Ihrem POST-Aufruf für Datasets lediglich den Abfrageparameter „defaultRetentionPolicy“ hinzufügen und ihn auf *basicFIFO* festlegen.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}