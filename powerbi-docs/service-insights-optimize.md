---
title: "Optimieren von Daten für schnelle Einblicke in Power BI"
description: "Optimieren Sie Daten für schnelle Einblicke in Power BI. Wenn Power BI keine Einblicke in den Daten findet, finden Sie im Folgenden mögliche Lösungsansätze."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/02/2017
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 2936ac75684e4efe1870c556b27fcbdbc77d17ec
ms.sourcegitcommit: 0a16dc12bb2d39c19e6b0002b673a8c1d81319c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="optimize-your-data-for-power-bi-quick-insights"></a>Optimieren von Daten für schnelle Einblicke in Power BI
Sie möchten die Ergebnisse der schnellen Einblicke verbessern?  Wenn Sie Besitzer eines Datasets sind, probieren Sie Folgendes:

* Blenden Sie Spalten im Dataset aus oder ein. Für schnelle Einblicke in Power BI werden ausgeblendete Spalten nicht durchsucht.  Blenden Sie daher doppelt vorhandene oder nicht benötigte Spalten aus, und blenden Sie relevante Spalten ein.
* Verwenden Sie eine Mischung aus Datentypen wie z. B. Namen, Uhrzeiten, Datumsangaben und Zahlen.
* Vermeiden Sie Spalten mit doppelt vorhandenen Informationen (oder blenden Sie sie aus).  Die Suche nach sinnvollen Mustern nimmt wertvolle Zeit in Anspruch.  Dies gilt z. B. für eine Spalte mit ausgeschriebenen Namen von Bundesstaaten und eine anderen Spalte mit Namen deren Abkürzungen.
* Erhalten Sie eine Fehlermeldung, die besagt, dass Ihre Daten statistisch nicht signifikant sind?  Dies kann mit Modellen geschehen, die entweder sehr einfach sind, die über wenige Daten verfügen oder keine Daten oder keine Datumsspalten oder numerische Spalten aufweisen. Ihr Dataset muss über mindestens eine Dimension und ein Measure verfügen, um Einblicke zu generieren.

### <a name="next-steps"></a>Nächste Schritte
[Schnelle Einblicke in Power BI](service-insights.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
