---
title: Kombinationsdiagramm in Power BI
description: In diesem Tutorial zu Kombinationsdiagrammen wird erläutert, wann sie verwendet werden sollten und wie sie im Power BI-Dienst und in Power BI Desktop erstellt werden.
author: mihart
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 03a426947787cbd2720661267cac4601a4b9b13a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880938"
---
# <a name="combo-chart-in-power-bi"></a>Kombinationsdiagramm in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Ein Kombinationsdiagramm in Power BI ist eine einzelne Visualisierung, die ein Liniendiagramm und ein Säulendiagramm kombiniert. Die Kombination von zwei Diagrammen in einem ermöglicht einen schnelleren Vergleich von Daten.

Kombinationsdiagramme können ein oder zwei y-Achsen haben.

## <a name="when-to-use-a-combo-chart"></a>Einsatz von Kombinationsdiagrammen
Kombinationsdiagramme sind gut für folgende Zwecke geeignet:

* Bei einem Liniendiagramm und ein Säulendiagramm mit der gleichen X-Achse
* Zum Vergleichen mehrerer Kennzahlen mit verschiedenen Wertebereichen
* Zum Verdeutlichen der Zusammenhänge zweier Kennzahlen in einer Visualisierung
* Zum Prüfen, ob eine Kennzahl das durch eine andere Kennzahl vorgegebene Ziel erfüllt
* Zur Platzersparnis im Zeichenbereich

### <a name="prerequisites"></a>Voraussetzungen
In diesem Tutorial wird die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) verwendet.

1. Wählen Sie im oberen linken Bereich der Menüleiste **Datei** > **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.



## <a name="create-a-basic-single-axis-combo-chart"></a>Erstellen eines einfachen Kombinationsdiagramms mit einer Achse
In diesem Video sehen Sie, wie ein Kombinationsdiagramm anhand des Beispiels für Vertrieb und Marketing erstellt wird.
   > [!NOTE]
   > Dieses Video verwendet eine ältere Version von Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a>

1. Beginnen Sie auf einer leeren Berichtsseite, und erstellen Sie ein Säulendiagramm, das den Absatz des laufenden Jahres und den Bruttogewinn pro Monat anzeigt.

    a.  Wählen Sie im Bereich „Felder“ die Option **Verkäufe** \> **Verkäufe in diesem Jahr**  >  **Wert**.

    b.  Ziehen Sie **Vertrieb** \>**Bruttogewinn in diesem Jahr** in den Bereich **Wert**.

    c. Wählen Sie **Zeit** \> **Geschäftsmonat** aus, um den Wert dem Bereich **Achse** hinzuzufügen.

    ![Beispiel eines Kombinationsdiagramms](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Wählen Sie **Weitere Optionen** (...) in der rechten oberen Ecke der Visualisierung und dann **Sortieren nach > FiscalMonth** aus. Wenn Sie die Sortierreihenfolge ändern möchten, klicken Sie erst erneut auf die Auslassungspunkte und anschließend auf **Aufsteigend sortieren** oder **Absteigend sortieren**. In diesem Beispiel wird **Aufsteigend sortieren** verwendet.

6. Konvertieren Sie das Säulendiagramm in ein Kombinationsdiagramm. Es gibt zwei Kombinationsdiagramme: **Linien- und gestapeltes Säulendiagramm** und **Linien- und gruppiertes Säulendiagramm**. Wenn Sie das Säulendiagramm ausgewählt haben, wählen Sie im Bereich **Visualisierungen** die Option **Linien- und gruppiertes Säulendiagramm** aus.

    ![Beispiel „In ein Kombinationsdiagramm konvertieren“](media/power-bi-visualization-combo-chart/converttocombo-new2.png)
7. Ziehen Sie aus dem Bereich **Felder** die Option **Vertrieb** \> **Verkäufe im letzten Jahr** in den Bucket **Zeilenwerte**.

   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   Das Kombinationsdiagramm sollten nun ungefähr so aussehen:

   ![Beispiel „Kombinationsdiagramm abgeschlossen“](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Erstellen eines Kombinationsdiagramms mit zwei Achsen
In dieser Aufgabe vergleichen wir Bruttogewinn und Umsätze.

1. Erstellen Sie ein neues Liniendiagramm, das den **Bruttogewinn in Prozent im letzten Jahr** nach **FiscalMonth** nachverfolgt. Klicken Sie auf die Auslassungspunkte, um **Aufsteigend** nach **Monat** zu sortieren.  
Im Januar lag der Prozentsatz des Bruttogewinns bei 35 %, der Höchststand im April lag bei 45 %, im Juli fiel der Wert, und im August erreichte er wieder einen Spitzenwert. Sehen wir ein ähnliches Muster bei den Umsätzen im letzten und in diesem Jahr?

   ![Beispiel eines Kombinationsdiagramms für die Umsätze](media/power-bi-visualization-combo-chart/combo1-new.png)
2. Fügen Sie dem Liniendiagramm **Verkäufe in diesem Jahr > Wert** und **Verkäufe im letzten Jahr** hinzu. Da der **Bruttogewinn % Vorjahr** wesentlich kleiner ist als die **Umsätze**, können diese Werte nur schwer verglichen werden.      

   ![Beispiel „Kombinationsdiagramm-Nulllinie“](media/power-bi-visualization-combo-chart/flatline-new.png)
3. Konvertieren Sie das Liniendiagramm zu einem Linien- und gestapelten Säulendiagramm, damit die Visualisierung besser gelesen und interpretiert werden kann.

   ![Beispiel „In ein Kombinationsdiagramm konvertieren“](media/power-bi-visualization-combo-chart/converttocombo-new.png)

4. Ziehen Sie **Bruttogewinn % Vorjahr** aus **Spaltenwerte** in **Zeilenwerte**. Power BI erstellt zwei Achsen, sodass die Datasets anders skaliert werden können. Die linke Achse gibt den Dollarbetrag der Umsätze an, die rechte Achse die Prozentzahl. Und hier sehen Sie die Antwort auf unsere Frage: Ja, wir sehen ein ähnliches Muster.

   ![Beispiel „Cluster-Kombinationsdiagramm“](media/power-bi-visualization-combo-chart/power-bi-clustered-combo.png)    

## <a name="add-titles-to-the-axes"></a>Hinzufügen von Titeln zu den Achsen
1. Wählen Sie das Farbrollensymbol 
1. ![Farbrollensymbol](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) zum Öffnen des Formatierungsbereichs.
1. Wählen Sie den Pfeil nach unten aus, um die Optionen für die **Y-Achse** zu erweitern.
1. Nehmen Sie für **Y-Achse (Spalte)** die folgenden Einstellungen vor: Wählen Sie für **Position** die Option **Links**, für **Titel** die Option **Ein**, für **Stil** die Option **Nur Titel anzeigen** und für **Anzeigeeinheiten** die Option **Millionen** aus.

   ![Beispiel „Y-Achse aktiviert im Kombinationsdiagramm“](media/power-bi-visualization-combo-chart/power-bi-open-y.png)
4. Scrollen Sie unter **Y-Achse (Spalte)** nach unten, bis **Sekundäre anzeigen** angezeigt wird. Da es so viele Optionen für die Y-Achsen gibt, müssen Sie möglicherweise beide Scrollleisten verwenden. Im Abschnitt „Sekundäre anzeigen“ werden für den Liniendiagrammanteil des Kombinationsdiagramms Formatierungsoptionen angezeigt.

   ![Beispiel „Sekundäre anzeigen im Kombinationsdiagramm“](media/power-bi-visualization-combo-chart/power-bi-secondary.png)
5. Unter **Y-Achse (Linie)** ist für **Position** bereits die hier benötigte Option **Rechts** aktiviert. Stellen Sie **Titel**  auf **Ein**, und wählen Sie für **Stil** die Option **Nur Titel anzeigen**.

   Das Kombinationsdiagramm verfügt nun über zwei Y-Achsen mit jeweils eigenem Titel.

   ![Beispiel „Titel im Kombinationsdiagramm“](media/power-bi-visualization-combo-chart/power-bi-2-titles.png)

6. Optional können Sie die Schriftart, den Schriftgrad und die Farbe des Texts ändern und weitere Formatierungsoptionen festlegen, um die Darstellung und Lesbarkeit des Diagramms zu verbessern.

Jetzt haben Sie folgende Möglichkeiten:

* [Fügen Sie das Kombinationsdiagramm als Dashboardkachel hinzu.](../service-dashboard-tiles.md)
* [Speichern Sie den Bericht](../service-report-save.md).
* [Barrierefreiheit in Power BI Desktop-Berichten](../desktop-accessibility.md)

## <a name="cross-highlighting-and-cross-filtering"></a>Kreuzhervorheben und Kreuzfiltern

Das Markieren einer Spalte oder Zeile in einem Kombinationsdiagramm ermöglicht das Kreuzhervorheben und Kreuzfiltern anderer Visualisierungen auf der Berichtsseite und umgekehrt. Verwenden Sie [Visualinteraktionen](../service-reports-visual-interactions.md), um dieses Standardverhalten zu ändern.

## <a name="next-steps"></a>Nächste Schritte

[Ringdiagramme in Power BI](power-bi-visualization-doughnut-charts.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
