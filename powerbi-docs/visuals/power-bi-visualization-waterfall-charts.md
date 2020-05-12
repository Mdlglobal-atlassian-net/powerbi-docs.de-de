---
title: Wasserfalldiagramme in Power BI
description: Wasserfalldiagramme in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/5/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: d4e31d8c3d2bcbbfdf0d2d932be70cc2cd5f2625
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866493"
---
# <a name="waterfall-charts-in-power-bi"></a>Wasserfalldiagramme in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Wasserfalldiagramme zeigen eine laufende Summe an, während Power BI Werte hinzugefügt oder entfernt. Sie sind nützlich, um zu verdeutlichen, wie ein anfänglicher Wert (z.B. das Nettoeinkommen) durch eine Reihe von positiven und negativen Änderungen beeinflusst wird.

Die Säulen sind farbkodiert, damit Sie Zu- und Abnahmen der Werte schnell erkennen können. Die Säulen für den Anfangs- und den Endwert [gehen häufig von der horizontalen Achse aus](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "Starten Sie auf der horizontalen Achse"), während die Zwischenwerte unverankerte Säulen sind. Aufgrund dieses Aussehens werden Wasserfalldiagramme auch als „Brückendiagramme“ bezeichnet.

## <a name="when-to-use-a-waterfall-chart"></a>Einsatz von Wasserfalldiagrammen

Wasserfalldiagramme sind gut für folgende Zwecke geeignet:

* Bei Änderungen der Zahlen im Laufe der Zeit, für eine Serie oder über verschiedene Kategorien hinweg.

* Zum Überwachen der wichtigsten Änderungen am Gesamtwert.

* Zum Anzeigen des jährlichen Gewinns Ihres Unternehmens mithilfe einer Darstellung verschiedener Umsatzquellen und letztendlich des Gesamtgewinns (oder -verlusts).

* Zum Illustrieren der Mitarbeiterzahl Ihres Unternehmens zu Jahresbeginn und -ende.

* Zum Visualisieren Ihrer Einnahmen und Ausgaben pro Monat und des laufenden Kontostands für Ihr Konto.

## <a name="prerequisite"></a>Voraussetzung

Dieses Tutorial verwendet die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Wählen Sie im oberen linken Bereich der Menüleiste **Datei** > **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.

> [!NOTE]
> Eine Freigabe Ihres Berichts für einen Power BI-Kollegen erfordert, dass Sie und Ihr Kollege jeweils eine eigene Power BI Pro-Lizenz haben oder dass der Bericht in der Premium-Kapazität gespeichert wird.    

## <a name="create-a-waterfall-chart"></a>Erstellen eines Wasserfalldiagramms

Sie erstellen ein Wasserfalldiagramm, mit dem Abweichungen beim Umsatz (geschätzter Umsatz im Vergleich zu tatsächlichen Verkaufszahlen) nach Monat dargestellt werden.

### <a name="build-the-waterfall-chart"></a>Erstellen des Wasserfalldiagramms

1. Wählen Sie im Bereich **Felder** die Option **Verkäufe** > **Gesamtabweichung Verkäufe** aus.

   ![Screenshot der Auswahl von „Verkäufe > Gesamtabweichung Verkäufe“ und des resultierenden visuellen Elements](media/power-bi-visualization-waterfall-charts/power-bi-bar.png)

1. Wählen Sie das Wasserfallsymbol ![Screenshot des Wasserfallsymbols](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![Visualisierungsvorlagen](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. Wählen Sie **Zeit** > **FiscalMonth** aus, um den Wert dem Bereich **Kategorie** hinzuzufügen.

    ![Wasserfalldiagramm](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-month.png)

### <a name="sort-the-waterfall-chart"></a>Sortieren des Wasserfalldiagramms

1. Stellen Sie sicher, dass Power BI das Wasserfalldiagramm chronologisch nach Monat sortiert hat. Wählen Sie in der rechten oberen Ecke des Diagramms **Weitere Optionen** (...) aus.

    Wählen Sie für dieses Beispiel **Sortieren nach** und **FiscalMonth** dann aus. Ein gelber Indikator neben Ihrer Auswahl zeigt an, wenn die Auswahloption angewendet wird.

    ![Auswählen von „Sortieren nach > FiscalMonth“](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscalmonth.png)
    
    Um die Monate in chronologischer Reihenfolge anzuzeigen, wählen Sie **Aufsteigend sortieren** aus. Überprüfen Sie im nächsten Schritt, ob sich links von **Aufsteigend sortieren** ein gelber Indikator befindet. Dies gibt an, dass die ausgewählte Option angewendet wird.

    ![„Sortieren nach > Aufsteigend sortieren“ auswählen](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-ascending.png)

    

    Beachten Sie, dass das Diagramm für den Geschäftsmonat von Januar nach August sortiert ist.  

### <a name="explore-the-waterfall-chart"></a>Analysieren des Wasserfalldiagramms

Analysieren Sie die Informationen genauer, um zu ermitteln, was von Monat zu Monat am stärksten zu den Änderungen beiträgt.

1.  Wählen Sie **Laden** > **Gebiet** aus, wodurch dem Bucket **Aufschlüsselung** noch **Gebiet** hinzugefügt wird.

    ![Zeigt Store im Bucket „Aufschlüsselung“ an](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Power BI verwendet den Wert in **Aufschlüsselung**, um der Visualisierung weitere Daten hinzuzufügen. Power BI fügt die wichtigsten fünf Faktoren für die Steigerungen oder Verringerungen pro Geschäftsmonat hinzu. Dies bedeutet, dass der Februar nun z.B. über sechs Datenpunkte verfügt, anstatt nur einen.  

    ![Zeigt Store im Bucket „Aufschlüsselung“ an](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-default.png)

    Angenommen, Sie interessieren sich aber nur für die ersten beiden Faktoren.

1. Wählen Sie im Bereich **Format** **Aufschlüsselung** aus, und legen Sie für **Max. Aufschlüsselungen** **2** fest.

    ![„Format > Aufschlüsselung“](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-two.png)

    Ein kurzer Blick zeigt, dass die Gebiete „Ohio“ und „Pennsylvania“ im Wasserfalldiagramm den größten Anteil an positiven wie negativen Änderungen haben.

    ![Wasserfalldiagramm](media/power-bi-visualization-waterfall-charts/power-bi-axis-waterfall.png)

## <a name="next-steps"></a>Nächste Schritte

* [Ändern der Interaktion von Visualisierungen in einem Power BI-Bericht](../service-reports-visual-interactions.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
