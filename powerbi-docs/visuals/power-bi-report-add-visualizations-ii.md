---
title: Teil 2 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht
description: Teil 2 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/28/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 132c795724b6f3744e0648ac1f3229c5e6538a97
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758420"
---
# <a name="add-visuals-to-a-power-bi-report-part-2"></a>Hinzufügen von Visuals zu einem Power BI-Bericht (Teil 2)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

In [Teil 1](power-bi-report-add-visualizations-i.md) haben Sie eine einfache Visualisierung erstellt, indem Sie Kontrollkästchen neben Feldnamen aktiviert haben.  In Teil 2 lernen Sie, wie Sie Drag & Drop verwenden und die Funktionen der Bereiche **Felder** und **Visualisierungen** nutzen, um Visualisierungen zu erstellen und zu ändern.


## <a name="create-a-new-visualization"></a>Erstellen einer neuen Visualisierung
In diesem Tutorial verwenden wir unser Dataset mit Einzelhandelsdaten und erstellen einige wichtige Visualisierungen.

## <a name="prerequisites"></a>Voraussetzungen

In diesem Tutorial wird die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) verwendet.

1. Klicken Sie im oberen linken Bereich der Power BI Desktop-Menüleiste auf **Datei** > **Öffnen**.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Exklusiv ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.

## <a name="add-visualizations-to-the-report"></a>Hinzufügen von Visualisierungen zum Bericht

Erstellen Sie eine Visualisierung durch Auswahl eines Felds aus dem Bereich **Felder** . Dieser erstellte Visualisierungstyp hängt vom Typ des ausgewählten Feldes ab. In Power BI wird der Datentyp verwendet, um zu bestimmen, welche Visualisierung zum Anzeigen der Ergebnisse verwendet werden soll. Sie können die verwendete Visualisierung ändern, indem Sie im Bereich „Visualisierungen“ ein anderes Symbol auswählen. Beachten Sie, dass nicht alle Visualisierungen Ihre Daten anzeigen können. Beispielsweise werden geografische Daten mit einem Trichterdiagramm oder Liniendiagramm nicht gut angezeigt. 


### <a name="add-an-area-chart-that-looks-at-this-years-sales-compared-to-last-year"></a>Hinzufügen eines Flächendiagramms, mit dem der Umsatz dieses Jahres mit dem Umsatz des Vorjahrs verglichen wird

1. Wählen Sie in der Tabelle **Verkäufe** zunächst **Verkäufe in diesem Jahr** > **Wert** und dann **Verkäufe im letzten Jahr** aus. Power BI erstellt ein Säulendiagramm.  Dieses Diagramm sieht interessant aus, und Sie möchten noch mehr erfahren. Wie hoch sind die Verkäufe pro Monat?  
   
   ![Screenshot des Säulendiagramms](media/power-bi-report-add-visualizations-ii/power-bi-start.png)

2. Ziehen Sie aus der Zeittabelle **FiscalMonth** in den Bereich **Achse**.  
   ![Screenshot des Säulendiagramms mit „FiscalMonth“ als Achse](media/power-bi-report-add-visualizations-ii/power-bi-fiscalmonth.png)

3. [Ändern Sie die Visualisierung](power-bi-report-change-visualization-type.md) in ein Flächendiagramm.  Es gibt viele Arten von Visualisierung, aus denen Sie wählen können. In den dazugehörigen [Beschreibungen, Tipps für bewährte Methoden und Tutorials](power-bi-visualization-types-for-reports-and-q-and-a.md) finden Sie Hilfe zum Auswählen des geeigneten Typs. Wählen Sie im Bereich „Visualisierungen“ das Flächendiagrammsymbol ![Flächendiagrammsymbol im Bereich „Visualisierungen“](media/power-bi-report-add-visualizations-ii/power-bi-area-chart.png) aus.

4. Sortieren Sie die Visualisierungen, indem Sie **Weitere Optionen** (...) und dann **Sortieren nach** >   **FiscalMonth** auswählen.

5. [Ändern Sie die Größe der Visualisierung](power-bi-visualization-move-and-resize.md), indem Sie die Visualisierung auswählen und einen der Konturkreise per Ziehbewegung verschieben. Machen Sie die Visualisierung so breit, dass die Scrollleiste ausgeblendet wird, und klein genug, damit noch Platz für eine weitere Visualisierung ist.
   
   ![Screenshot des Flächendiagrammvisuals](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Speichern Sie den Bericht](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Hinzufügen einer Kartenvisualisierung für Verkäufe nach Standort

1. Wählen Sie in der Tabelle **Geschäft** **Gebiet** aus. Ziehen Sie **Läden gesamt** in den Bereich „Werte“. Power BI erkennt, dass „Gebiet“ ein Ort ist, und erstellt eine Kartenvisualisierung.  
   ![Flächendiagramm](media/power-bi-report-add-visualizations-ii/power-bi-map1.png)

2. Fügen Sie eine Legende hinzu.  Ziehen Sie **Store** > **Kette** in den Bereich „Legende“, um die Daten nach dem Namen des Geschäfts anzuzeigen.  
   ![Zeichenbereich für den Bericht mit einem Pfeil, der von „Kette“ in der Liste „Felder“ nach „Kette“ im Bucket „Legende“ zeigt](media/power-bi-report-add-visualizations-ii/power-bi-chain.png)

## <a name="next-steps"></a>Weitere Schritte
* Weitere Informationen zu [Visualisierungen in Power BI-Berichten](power-bi-report-visualizations.md).  
* Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

