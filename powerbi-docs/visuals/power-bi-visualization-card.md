---
title: Kartenvisualisierungen (Kacheln für große Zahlen)
description: Erstellen von Kartenvisualisierungen in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2b584c0664623f62b6d1d77cce74eaa51b0e9041
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75758035"
---
# <a name="create-card-visualizations"></a>Erstellen von Kartenvisualisierungen

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Manchmal ist eine einzelne Zahl das Wichtigste, das Sie in Ihrem Power BI-Dashboard oder Bericht nachverfolgen möchten, wie z.B. der Gesamtumsatz, der Marktanteil im Jahresverlauf oder die Gesamtverkaufschancen. Eine solche Visualisierung wird als *Karte* bezeichnet. Wie fast alle nativen Power BI-Visualisierungen können Karten im Berichts-Editor oder in Q&A erstellt werden.

![Kartenvisualisierung](media/power-bi-visualization-card/pbi-opptuntiescard.png)

## <a name="prerequisite"></a>Voraussetzung

In diesem Tutorial wird die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) verwendet.

1. Wählen Sie im oberen linken Bereich der Menüleiste **Datei** \> **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.

## <a name="option-1-create-a-card-using-the-report-editor"></a>Option 1: Erstellen einer Karte im Berichts-Editor

Eine Möglichkeit, eine Karte zu erstellen, besteht darin, den Berichts-Editor in Power BI Desktop zu verwenden.

1. Beginnen Sie mit einer leeren Berichtsseite, und wählen Sie das Feld **Store** \> **Anzahl offener Stores** aus.

    Power BI erstellt ein Säulendiagramm mit dieser einen Zahl.

   ![Kacheldiagramm mit Beispielzahl](media/power-bi-visualization-card/pbi-overview-chart.png)

2. Wählen Sie im Bereich „Visualisierungen“ das Kartensymbol aus.

   ![Titelkarte mit Beispielzahl](media/power-bi-visualization-card/power-bi-card-visualization.png)

Nun müssten Sie erfolgreich mithilfe des Berichts-Editors eine Karte erstellt haben. Im Folgenden wird die zweite Option zum Erstellen einer Karte mithilfe des Q&A-Fragefelds beschrieben.

## <a name="option-2-create-a-card-from-the-qa-question-box"></a>Option 2: Erstellen einer Karte aus dem Q&A-Fragefeld
Sie können als Alternative auch das Q&A-Fragefeld zum Erstellen von Karten verwenden. Das Q&A-Fragefeld ist in der Berichtsansicht von Power BI Desktop verfügbar.

1. Beginnen Sie mit einer leeren Berichtsseite.

1. Klicken Sie im oberen Bereich des Fensters auf das Symbol **Frage stellen**. 

    Power BI erstellt dann eine Karte und ein Feld für Ihre Frage. 

   ![Platzierung des Symbols „Frage stellen“](media/power-bi-visualization-card/power-bi-q-and-a-overview.png)

2. Geben Sie z. B. „Total Sales for Tina“ (Verkäufe insgesamt für Tina) in das Fragefeld ein.

    Im Fragefeld werden Vorschläge und Formulierungsalternativen angezeigt. Schließlich sehen Sie hier die Gesamtanzahl.  

   ![Beispiel für das Fragefeld](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

   ![Kartenbeispiel der Fragemethode](media/power-bi-visualization-card/power-bi-q-and-a-card.png)

Nun müssten Sie erfolgreich mithilfe des Q&A-Fragefelds eine Karte erstellt haben. Im Folgenden wird erläutert, wie Sie Ihre Karte entsprechend Ihrer Anforderungen formatieren können.

## <a name="format-a-card"></a>Formatieren einer Karte
Sie haben viele Möglichkeiten, Beschriftungen, Text, Farben usw. zu ändern. Der einfachste Weg, um dies zu lernen, ist eine Karten zu erstellen und dann den Formatierungsbereich zu erkunden. Hier sehen Sie ein paar Beispiele der verfügbaren Formatierungsoptionen. 

Der Bereich „Formatierung“ ist bei der Interaktion mit der Karte in einem Bericht verfügbar. 

1. Öffnen Sie den Bereich „Formatierung“, indem Sie zuerst das Farbrollersymbol auswählen. 

    ![Karte mit hervorgehobenem Farbrollersymbol](media/power-bi-visualization-card/power-bi-format-card-2.png)

2. Erweitern Sie **Datenbeschriftung**, wenn die Karte ausgewählt ist, und verändern Sie die Farbe, die Größe und die Schriftfamilie. Wenn Sie Tausende Filialen haben, können Sie **Anzeigeeinheiten** verwenden, um die Anzahl der Filialen in Tausenderschritten anzeigen und die Dezimalstellen ebenso zu steuern. Beispielsweise 125,8k anstatt 125.832,00.

    ![Beispiel für eine Karte mit Datenformat](media/power-bi-visualization-card/power-bi-card-format-2.png)

3.  Erweitern Sie die **Kategoriebeschriftung**, und ändern Sie Farbe und Größe.

    ![Beispiel für eine Karte mit Kategorie](media/power-bi-visualization-card/power-bi-card-format-category.png)

4. Erweitern Sie den **Hintergrund**, und verschieben Sie den Regler auf „On“ (Ein).  Sie können nun die Hintergrundfarbe und -transparenz ändern.

    ![Regler auf „ON“ (Ein) festgelegt](media/power-bi-visualization-card/power-bi-format-color-2.png)

5. Machen Sie sich weiter mit den Formatoptionen vertraut, bis Ihre Karte so aussieht, wie Sie es sich vorstellen. 

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
Wenn kein Fragefeld angezeigt wird, wenden Sie sich an den System- oder Mandantenadministrator.    

## <a name="next-steps"></a>Nächste Schritte
[Kombinationsdiagramm in Power BI](power-bi-visualization-combo-chart.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
