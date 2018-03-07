---
title: Automatisches Erstellen von Einblicken in Daten mit Power BI
description: Hier erfahren Sie, wie Sie Einblicke in Ihre Datasets und Dashboardkacheln erhalten.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: et_MLSL2sA8
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: mihart
ms.openlocfilehash: 01e4f19cc1a3a57179be37cf0f36adf15ac47fdc
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Automatisches Erstellen von Einblicken in Daten mit Power BI
Sie besitzen ein neues Dataset und wissen nicht, womit Sie beginnen sollen?  Sie müssen schnell ein Dashboard erstellen?  Sie möchten nach Einblicken suchen, die Sie möglicherweise übersehen haben?

Führen Sie schnelle Einblicke aus, um interessante interaktive Visualisierungen auf Grundlage Ihrer Daten zu generieren. Schnelle Einblicke können für ein gesamtes Dataset (schnelle Einblicke) oder eine bestimmte Dashboard-Kachel (bereichsbezogene Einblicke) ausgeführt werden. Sie können sogar Einblicke für einen Einblick ausführen.

> **HINWEIS**: Einblicke funktionieren nicht mit DirectQuery. Das Feature kann nur für in Power BI hochgeladene Daten verwendet werden.
> 
> 

Das Feature „Einblicke“ basiert auf einer wachsenden Reihe [erweiterter analytischer Algorithmen](service-insight-types.md), die in Verbindung mit Microsoft Research entwickelt wurden. Wir möchten damit auch in Zukunft noch mehr Benutzern auf neue und intuitive Weise Einblicke in ihre Daten bieten.

## <a name="run-quick-insights-on-a-dataset"></a>Ausführen von schnellen Einblicken für ein Dataset
Lassen Sie sich von Amanda zeigen, wie Sie das Feature „Schnelle Einblicke“ auf ein Dataset anwenden, einen Einblick im Fokusmodus öffnen, einen der Einblicke als Kachel an das Dashboard anheften und dann Einblicke für eine Dashboardkachel abrufen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Jetzt sind sie dran. Erkunden Sie Einblicke anhand des [Analysebeispiels für die Lieferantenqualität](sample-supplier-quality.md).

1. Wählen Sie auf der Registerkarte **Datasets** die Auslassungspunkte (...) und dann **Einblicke erhalten** aus.
   
    ![](media/service-insights/power-bi-ellipses.png)
   
    ![](media/service-insights/power-bi-tab.png)
2. Power BI verwendet [verschiedene Algorithmen](service-insight-types.md) zum Suchen nach Trends in Ihrem Dataset.
   
    ![](media/service-insights/pbi_autoinsightssearching.png)
3. Innerhalb von Sekunden sind Ihre Einblicke bereit.  Wählen Sie **Einblicke anzeigen** aus, um Visualisierungen anzuzeigen.
   
    ![](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **HINWEIS**: Einige Datasets können keine Einblicke generieren, da die Daten statistisch nicht signifikant sind.  Weitere Informationen finden Sie unter [Optimieren von Daten für Einblicke](service-insights-optimize.md).
   > 
   > 
1. Die Visualisierungen werden in einem speziellen Bereich für **schnelle Einblicke** mit bis zu 32 getrennten Einblickkarten angezeigt. Jede Karte enthält ein Diagramm oder eine Grafik und eine kurze Beschreibung.
   
    ![](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interaktion mit Karten für Einblicke
  ![](media/service-insights/pbi_hover.png)

1. Zeigen Sie auf eine Karte, und wählen Sie das Anheftsymbol aus, um die Visualisierung einem Dashboard hinzuzufügen.
2. Halten Sie den Mauszeiger über eine Karte, wählen Sie die Auslassungspunkte (...) aus, und wählen Sie dann **Einblicke anzeigen** aus. Hiermit wird ein Einblick im Vollbildmodus geöffnet.
   
    ![](media/service-insights/power-bi-insight-focus.png)
3. In diesem Modus haben Sie folgende Möglichkeiten:
   
   * Filtern Sie die Visualisierungen.  Um die Filter anzuzeigen, wählen Sie in der oberen rechten Ecke das Pfeilsymbol aus, um den Filterbereich zu erweitern.
     
        ![](media/service-insights/power-bi-insights-filter-new.png)
   * Heften Sie die Einblickkarte an ein Dashboard an, indem Sie das Stecknadelsymbol ![](media/service-insights/power-bi-pin-icon.png) oder **Visual anheften** auswählen.
   * Führen Sie Einblicke für die Karte selbst aus. Dies wird häufig auch als **bereichsbezogene Einblicke** bezeichnet. Wählen Sie in der oberen rechten Ecke das Glühbirnensymbol ![](media/service-insights/power-bi-bulb-icon.png) oder **Einblicke erhalten** aus.
     
       ![](media/service-insights/pbi-autoinsights-tile.png)
     
     Der Einblick wird auf der linken Seite angezeigt, und neue Karten (ausschließlich abhängig von den Daten in diesem Einblick) werden rechts angezeigt.
     
       ![](media/service-insights/power-bi-insights-on-insights-new.png)
4. Wenn Sie zum Bereich für Einblicke zurückkehren möchten, wählen Sie links oben **Fokusmodus beenden** aus.

## <a name="run-insights-on-a-dashboard-tile"></a>Ausführen von Einblicken auf einer Dashboardkachel
Anstatt ein gesamtes Dataset nach Einblicken zu durchsuchen, können Sie die Suche auf die zum Erstellen einer einzelnen Dashboardkachel verwendeten Daten einschränken. Dies wird häufig als **bereichsbezogene Einblicke** bezeichnet.

1. Öffnen Sie ein Dashboard.
2. Zeigen Sie auf eine Kachel. Wählen Sie die Auslassungspunkte (...) und dann **Einblicke anzeigen** aus. Die Kachel wird im [Fokusmodus](service-focus-mode.md) geöffnet. Die Einblickkarten werden rechts angezeigt.    
   
    ![](media/service-insights/pbi-insights-tile.png)    
4. Ist einer der Einblicke für Sie interessant? Wählen Sie die entsprechende Einblickkarte aus, um weitere Informationen zu erhalten. Der ausgewählte Einblick wird auf der linken Seite angezeigt, und neue Einblickkarten (ausschließlich abhängig von den Daten in diesem Einblick) werden rechts angezeigt.    
6. Schlüsseln Sie Ihre Daten weiter auf. Wenn Sie für Sie interessante Einblicke finden, können Sie sie an Ihr Dashboard anheften, indem Sie rechts oben auf **Visualisierung anheften** klicken.

## <a name="next-steps"></a>Nächste Schritte
Wenn Sie ein Dataset besitzen, können Sie es [für Schnelleinblicke optimieren](service-insights-optimize.md).

Erfahren Sie mehr über die [Typen verfügbarer schneller Einblicke](service-insight-types.md).

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
