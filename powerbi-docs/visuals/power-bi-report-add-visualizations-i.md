---
title: Teil 1 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht
description: Teil 1 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b275d4e7fdb4e289d2331a2f58db504071ea609b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758598"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Hinzufügen von Visuals zu einem Power BI-Bericht (Teil 1)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Dieser Artikel enthält eine kurze Einführung in das Erstellen einer Visualisierung in einem Bericht. Er gilt sowohl für den Power BI-Dienst als auch für Power BI Desktop. Komplexere Inhalte [finden Sie in Teil 2](power-bi-report-add-visualizations-ii.md) dieser Serie. Sehen Sie, wie Amanda verschiedene Methoden zum Erstellen, Bearbeiten und Formatieren von Visuals im Berichtszeichenbereich demonstriert. Versuchen Sie es dann selbst, indem Sie das [Beispiel für Vertrieb und Marketing](../sample-datasets.md) verwenden, um einen eigenen Bericht zu erstellen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Voraussetzungen

In diesem Tutorial wird die [PBIX-Datei für Vertrieb und Marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix) verwendet.

1. Klicken Sie im oberen linken Bereich der Power BI Desktop-Menüleiste auf **Datei** > **Öffnen**.
   
2. Suchen Sie nach Ihrer Kopie der **PBIX-Beispieldatei für Vertrieb und Marketing**.

1. Öffnen Sie die **PBIX-Beispieldatei für Vertrieb und Marketing** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.

## <a name="add-visualizations-to-the-report"></a>Hinzufügen von Visualisierungen zum Bericht

1. Erstellen Sie eine Visualisierung durch Auswahl eines Felds aus dem Bereich **Felder** .

    Beginnen Sie mit einem numerischen Feld wie **Sales** > **TotalSales**. Power BI erstellt ein Säulendiagramm mit einer einzelnen Spalte.

    ![Screenshot eines Säulendiagramms mit einer einzelnen Spalte.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    Beginnen Sie alternativ mit einem Kategoriefeld, z.B. **Name** oder **Produkt**. Power BI erstellt eine Tabelle und fügt das Feld dem Bereich **Werte** hinzu.

    ![Screenshot einer Tabelle mit vier Kategorien](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Beginnen Sie alternativ mit einem geografischen Feld wie **Geo** > **City** (Stadt). Power BI und Bing Maps erstellen eine Kartenvisualisierung.

    ![Screenshot einer Kartenvisualisierung.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Ändern des Visualisierungstyps

 Erstellen Sie eine Visualisierung, und ändern Sie deren Typ. 
 
 1. Wählen Sie **Product** (Produkt) > **Category** (Kategorie) und dann **Product** > **Count of Product** (Produktanzahl) aus, um beide dem Bereich **Values** (Werte) hinzuzufügen.

    ![Screenshot des Bereichs „Felder“, wobei „Werte“ hervorgehoben ist.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Ändern Sie die Visualisierung in einem Säulendiagramm, indem Sie das Symbol **Gestapeltes Säulendiagramm** auswählen.

   ![Screenshot des Bereichs „Visualisierungen“ mit hervorgehobener Option „Gestapeltes Säulendiagramm“.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Um die Weise zu ändern, in der das Visual sortiert ist, wählen Sie **Weitere Aktionen** (...) aus.  Verwenden Sie die Sortieroptionen, um die Sortierrichtung der Sortierung (aufsteigend oder absteigend) und die Spalte, nach der sortiert wird (**Sortieren nach**), zu ändern.

   ![Screenshot des Dropdownfelds „Weitere Aktionen“.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Nächste Schritte

 Fahren Sie fort mit:

* [Teil 2: Hinzufügen von Visualisierungen zu einem Power BI-Bericht](power-bi-report-add-visualizations-ii.md)

* [Mit den Visualisierungen](../consumer/end-user-reading-view.md) im Bericht interagieren

