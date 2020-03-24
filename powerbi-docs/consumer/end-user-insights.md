---
title: Ausführen und Anzeigen von Einblicken auf Dashboardkacheln
description: Hier erfahren Sie, wie Sie als Power BI-Endbenutzer Einblicke in Ihre Datasets und Dashboardkacheln erhalten.
author: mihart
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 891a9b1a5afee26bdb2d6b363ccd2cee5f2461cb
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377282"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Anzeigen von Einblicken auf Dashboardkacheldaten mit Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Jede [Kachel](end-user-tiles.md) eines Visuals in Ihrem Dashboard ist ein Ausgangspunkt für das Durchsuchen von Daten. Wenn Sie eine Kachel auswählen, wird ein Bericht oder [Q&A geöffnet](end-user-q-and-a.md), in dem Sie filtern und sortieren und das dem Bericht zugrunde liegende Dataset detailliert analysieren können. Und wenn Sie Einblicke ausführen, erledigt Power BI das Durchsuchen der Daten für Sie.

![Auslassungspunkte-Menümodus](./media/end-user-insights/power-bi-insight.png)

Führen Sie Einblicke aus, um interessante interaktive Visuals auf Grundlage Ihrer Daten zu generieren. Einblicke können für eine bestimmte Dashboardkachel ausgeführt werden, und Sie können sogar Einblicke für einen Einblick durchführen.

Das Feature „Einblicke“ basiert auf einer wachsenden [Reihe erweiterter analytischer Algorithmen](end-user-insight-types.md), die in Verbindung mit Microsoft Research entwickelt wurden. Wir möchten damit auch in Zukunft noch mehr Benutzern auf neue und intuitive Weise Einblicke in ihre Daten bieten.

## <a name="run-insights-on-a-dashboard-tile"></a>Ausführen von Einblicken auf einer Dashboardkachel
Wenn Sie Einblicke für eine Dashboardkachel ausführen, durchsucht Power BI nur die Daten, die zum Erstellen dieser einzelnen Dashboardkachel verwendet wurden. 

1. [Öffnen Sie ein Dashboard](end-user-dashboards.md).
2. Zeigen Sie auf eine Kachel. Wählen Sie **Weitere Optionen** (...) und dann **Erkenntnisse anzeigen** aus. 

    ![Auslassungspunkte-Menümodus](./media/end-user-insights/power-bi-hovers.png)


3. Die Kachel wird im [Fokusmodus](end-user-focus.md) geöffnet. Die Einblickkarten werden rechts angezeigt.    
   
    ![Fokusmodus](./media/end-user-insights/power-bi-insights-tile.png)    
4. Ist einer der Einblicke für Sie interessant? Wählen Sie die entsprechende Einblickkarte aus, um weitere Informationen zu erhalten. Der ausgewählte Einblick wird auf der linken Seite angezeigt, und neue Einblickkarten (ausschließlich abhängig von den Daten in diesem Einblick) werden rechts angezeigt.    

 ## <a name="interact-with-the-insight-cards"></a>Interaktion mit Karten für Einblicke
Wenn Sie einen Einblick geöffnet haben, können Sie ihn weiter durchsuchen.

   * Filtern Sie das Visual im Zeichenbereich.  Um die Filter anzuzeigen, wählen Sie in der oberen rechten Ecke das Pfeilsymbol aus, um den Filterbereich zu erweitern.

      ![Einblick im Menü „Filter“ erweitert](./media/end-user-insights/power-bi-filters.png)
   
   * Führen Sie Einblicke für die Karte „Einblick“ selbst aus. Dies wird häufig auch als **verwandte Einblicke** bezeichnet. Wählen Sie eine Insight-Karte aus, um sie zu aktivieren. Sie wird im Berichtszeichenbereich angezeigt.
   
      ![Einblick im Menü „Filter“ erweitert](./media/end-user-insights/power-bi-insight-card.png)
   
   * Wählen Sie in der oberen rechten Ecke das Glühbirnensymbol ![„Einblicke erhalten“-Symbol](./media/end-user-insights/power-bi-bulb-icon.png) oder **Einblicke erhalten** aus. Der Einblick wird auf der linken Seite angezeigt, und neue Karten (ausschließlich abhängig von den Daten in diesem Einblick) werden rechts angezeigt.
     
     ![Menüleiste mit dem Symbol „Einblicke erhalten“](./media/end-user-insights/power-bi-related.png)
     
Um zu Ihrem Bericht zurückzukehren, wählen Sie in der oberen linken Ecke **Fokusmodus beenden** aus.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
- **Einblicke anzeigen** funktioniert nicht mit allen Arten von Dashboardkacheln. Beispielsweise ist diese Option nicht für Power BI-Visuals verfügbar.<!--[Power BI visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr über die [Typen verfügbarer schneller Einblicke](end-user-insight-types.md).

