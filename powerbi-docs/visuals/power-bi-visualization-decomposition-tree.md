---
title: Analysebaum
description: 'Tutorial: Erstellen einer Analysebaumvirtualisierung in Power BI'
author: mihart
manager: kvivek
ms.reviewer: juluczni
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: f7c907d31d4d58a9f39ad982e7d94f3f5ba3f118
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865566"
---
# <a name="create-and-view-decomposition-tree-visuals-in-power-bi-preview"></a>Erstellen und Anzeigen des visuellen Analysebaumelements in Power BI (Vorschau)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Mit dem Analysebaumvisual in Power BI ist es möglich, dimensionsübergreifend Daten zu visualisieren. Es aggregiert Daten automatisch und ermöglicht einen Drilldown für Ihre Dimensionen in beliebiger Reihenfolge. Gleichzeitig handelt es sich um eine KI-Visualisierung, sodass Sie basierend auf bestimmten Kriterien eine Suche nach der nächsten Dimension anfordern können, für die Sie einen Drilldown durchführen möchten. Dies macht es zu einem nützlichen Werkzeug für die Ad-hoc-Erkundung und die Durchführung von Ursachenanalysen.

![Analysebaum](media/power-bi-visualization-decomposition-tree/tree-full.png)

In diesem Tutorial werden zwei Beispiele verwendet:

- Ein Lieferkettenszenario, das den Prozentsatz der Produkte analysiert, die ein Unternehmen nicht vorrätig hat (Produkt ist vergriffen).  
- Ein Vertriebsszenario, das den Verkauf von Videospielen nach zahlreichen Faktoren wie Spielgenre und Herausgeber aufgliedert.

> [!NOTE]
> Eine Freigabe Ihres Berichts für einen Power BI-Kollegen erfordert, dass Sie und Ihr Kollege jeweils eine eigene Power BI Pro-Lizenz haben oder dass der Bericht in der Premium-Kapazität gespeichert wird.    

## <a name="get-started"></a>Erste Schritte
Wählen Sie im Bereich „Visualisierungen“ das Symbol für den Analysebaum aus.
![Analysebaum: Wasserzeichen](media/power-bi-visualization-decomposition-tree/tree-watermark.png)

Die Visualisierung erfordert zwei Arten von Eingaben.

**Analyse**: Die Metrik, die Sie analysieren möchten. Hierbei muss es sich um ein Measure oder um ein Aggregat handeln.  
**Erläuterung nach**: Mindestens eine Dimension, für die ein Drilldown durchgeführt werden soll.

Sobald Sie Ihr Measure in das Feld ziehen, wird die Visualanzeige mit dem aggregierten Measure aktualisiert. Im Beispiel unten wird die durchschnittliche Anzahl von Produkten mit Lieferrückstand in Prozent angezeigt (5,07 %) ![Analysebaum: Stammknoten](media/power-bi-visualization-decomposition-tree/tree-root.png)

Im nächsten Schritt werden Dimensionen eingeführt, für die ein Drilldown durchgeführt werden soll. Fügen Sie die Felder im Bereich **Erläuterung nach** hinzu. Beachten Sie, dass neben Ihrem Stammknoten ein Pluszeichen angezeigt wird. Durch Auswahl des Pluszeichens (+) können Sie auswählen, für welche Felder ein Drilldown durchgeführt werden soll (der Drilldown kann in beliebiger Reihenfolge erfolgen).
![Menü für Analysebaum](media/power-bi-visualization-decomposition-tree/tree-menu.png)

Das Auswählen von **Prognosetrend** führt dazu, dass der Baum erweitert und das Measure nach den Werten in der Spalte aufgeschlüsselt wird. Dieser Vorgang kann wiederholt werden, um einen anderen Knoten für den Drilldown auszuwählen.
![Analysebaumerweiterung](media/power-bi-visualization-decomposition-tree/tree-expansion.png)

Durch die Auswahl eines Knotens aus der letzten Ebene wird eine Kreuzfilterung für die Daten durchgeführt. Durch die Auswahl eines Knotens aus einer vorherigen Ebene wird der Pfad geändert.

![Menü für Analysebaum](media/power-bi-visualization-decomposition-tree/tree-interaction.gif)

Durch eine Interaktion mit anderen Visuals wird eine Kreuzfilterung für den Analysebaum durchgeführt. Dadurch kann sich die Reihenfolge der Knoten innerhalb der Ebenen ändern.
Im Beispiel unten erfolgt eine Kreuzfilterung nach Ubisoft. Der Pfad wird aktualisiert, und die Xbox-Verkäufe verschieben sich vom ersten auf den zweiten Platz – hinter PlayStation. 

Wenn wir dann eine Kreuzfilterung des Baums nach Nintendo durchführen, sind die Xbox-Verkäufe leer, weil keine Nintendo-Spiele für Xbox entwickelt werden. Xbox wird zusammen mit dem nachfolgenden Pfad aus der Ansicht herausgefiltert.

Obwohl der Pfad nicht mehr angezeigt wird, bleiben die vorhandenen Ebenen (in diesem Fall das Spielgenre) weiter angeheftet. Bei Auswahl des Knotens „Nintendo“ wird der Baum deshalb automatisch auf das Spielgenre erweitert.

![Menü für Analysebaum](media/power-bi-visualization-decomposition-tree/tree-interaction-2.gif)


## <a name="ai-splits"></a>KI-Teilung

Sie können über „KI-Teilungen“ herausfinden, wonach Sie als Nächstes in den Daten suchen sollten. Diese Teilungen erscheinen oben in der Liste und sind mit einer Glühlampe gekennzeichnet. Die Teilungen unterstützen Sie dabei, automatisch hohe und niedrige Werte in den Daten zu ermitteln.

Die Analyse kann abhängig von Ihren Präferenzen auf zwei Arten erfolgen. Das Standardverhalten lautet wie folgt:

**Höchstwert**: Berücksichtigt alle verfügbaren Felder und ermittelt, für welches Feld ein Drilldown durchgeführt werden muss, um den höchsten Wert des zu analysierenden Measures zu erhalten.  
**Tiefstwert**: Berücksichtigt alle verfügbaren Felder und ermittelt, für welches Feld ein Drilldown durchgeführt werden muss, um den niedrigsten Wert des zu analysierenden Measures zu erhalten.  

Die Auswahl von **Höchstwert** im Beispiel zum Lieferrückstand führt zu diesen Ergebnissen: ![Analysebaumvisual: KI-Teilung](media/power-bi-visualization-decomposition-tree/tree-ai-split.png)

Die Glühlampe neben **Product Type** (Produkttyp) weist darauf hin, dass es sich um eine KI-Teilung handelt. Der Baum enthält außerdem eine gestrichelte Linie, die den Knoten **Patient Monitoring** (Patientenüberwachung) empfiehlt, weil der Lieferrückstand hier am höchsten ist (9,2 %). 

Bewegen Sie den Cursor über die Glühlampe, um eine QuickInfo anzuzeigen. In diesem Beispiel wird in der QuickInfo darauf hingewiesen, dass der Lieferrückstand (in Prozent) für Produkte aus dem Bereich der Patientenüberwachung am höchsten ist.

Sie können das Visual so konfigurieren, dass anstelle von **absoluten** KI-Teilungen **relative** KI-Teilungen ermittelt werden. 

Im relativen Modus wird nach Höchstwerten gesucht, die (im Vergleich zu den restlichen Daten in der Spalte) herausstechen. Betrachten wir zur Verdeutlichung das folgende Beispiel: ![Analysebaumvisual: absolute Teilung](media/power-bi-visualization-decomposition-tree/tree-ai-absolute.png)

Im Screenshot oben betrachten wir die Verkäufe von Videospielen in Nordamerika. Zuerst erfolgt eine Teilung des Baums nach **Publisher Name** (Herausgebername), dann wird ein Drilldown für Nintendo durchgeführt. Die Auswahl von **Höchstwert** führt zur Erweiterung von **Plattform „Nintendo“** . Da Nintendo (der Herausgeber) nur für Nintendo-Konsolen entwickelt, ist nur ein Wert vorhanden, und dieser ist wenig überraschend der höchste Wert.

Eine interessantere Teilung wäre jedoch die Betrachtung, welcher Wert sich relativ zu den anderen Werten in derselben Spalte abhebt. Wenn wir den Analysetyp von **Absolut** in **Relativ** ändern, erhalten wir für Nintendo das folgende Ergebnis: ![Analysebaumvisual: relative Teilung](media/power-bi-visualization-decomposition-tree/tree-ai-relative.png)

In diesem Fall lautet der empfohlene Wert **Plattform in Spielgenre**.  Die Plattform erzielt keinen höheren absoluten Wert als Nintendo (19.950.000 USD gegenüber 46.950.000 USD). Dennoch ist es ein Wert, der heraussticht.

Genauer gesagt: Da es 10 Werte für das Spielgenre gibt, würde der erwartete Wert für die Plattform bei einer gleichmäßigen Aufteilung 4,6 Mio. USD betragen. Der Plattformwert von knapp 20 Mio. USD ist interessant, weil er viermal höher ist als das erwartete Ergebnis.

Die Berechnung lautet wie folgt:

Verkäufe in Nordamerika für Plattform / Abs(Durchschn.(Verkäufe in Nordamerika für Spielgenre))  
im Vergleich zu  
Verkäufe in Nordamerika für Nintendo / Abs(Durchschn.(Verkäufe in Nordamerika für Plattform))  

Übersetzt:

19.550.000 / (19.550.000 + 11.140.000 + ... + 470.000 + 60.000 /10) = 4,25x  
im Vergleich zu  
46.950.000/ (46.950.000/1) = 1x  

Wenn Sie es vorziehen, keine KI-Teilungen im Baum zu verwenden, können Sie diese unter den Optionen **Analyseformatierung** deaktivieren:  

![Analysebaumvisual: Deaktivieren von KI-Teilungen](media/power-bi-visualization-decomposition-tree/tree-ai-disable.png)

## <a name="tree-interactions-with-ai-splits"></a>Bauminteraktionen mit KI-Teilungen

Es können mehrere aufeinanderfolgende KI-Ebenen vorhanden sein. Sie können auch verschiedene Arten von KI-Ebenen kombinieren (Wechsel von „Höchstwert“ zu „Tiefstwert“ und zurück zu „Höchstwert“): ![Analysebaum: verschiedene KI-Pfade](media/power-bi-visualization-decomposition-tree/tree-multi-ai-path.png)

Wenn Sie einen anderen Knoten im Baum auswählen, werden die KI-Teilungen von Grund auf neu berechnet. Im Beispiel unten wurde der ausgewählte Knoten in der Ebene **Prognosetrend** geändert. Die nachfolgenden Ebenen werden geändert, um die richtigen Höchst- und Tiefstwerte zu liefern. ![Analysebaum: KI-Interaktionen](media/power-bi-visualization-decomposition-tree/tree-ai-interactions.png)

Die KI-Ebenen werden auch neu berechnet, wenn Sie für den Analysebaum eine Kreuzfilterung anhand eines anderen Visuals durchführen. Im Beispiel unten ist ersichtlich, dass der Lieferrückstand in Prozent für „Plant #0477“ am höchsten ist.

![Analysebaum: Kreuzfilterung](media/power-bi-visualization-decomposition-tree/tree-ai-crossfilter1.png)

Aber wenn wir im Balkendiagramm **April** auswählen, gibt es für **Produkttyp „Advanced Surgical“** (Moderne Chirurgie) die meisten Änderungen. In diesem Fall wurden nicht nur die Knoten neu angeordnet, sondern es wurde eine komplett andere Spalte ausgewählt. 

![Analysebaum: Kreuzfilterung](media/power-bi-visualization-decomposition-tree/tree-ai-crossfilter2.png)

Wenn sich KI-Ebenen wie Nicht-KI-Ebenen verhalten sollen, klicken Sie auf die Glühlampe, um das Standardverhalten wiederherzustellen. 

Mehrere KI-Ebenen können verkettet werden, aber eine Nicht-KI-Ebene kann nicht auf eine KI-Ebene folgen. Wenn wir nach einer KI-Teilung eine manuelle Teilung durchführen, verschwindet die Glühbirne aus der KI-Ebene, und die Ebene wird in eine normale Ebene umgewandelt. 

## <a name="locking"></a>Sperrung

Ein Inhaltsautor kann Ebenen für Berichtsconsumer sperren. Wenn eine Ebene gesperrt ist, kann sie weder entfernt noch geändert werden. Ein Consumer kann unterschiedliche Pfade innerhalb der gesperrten Ebenen erkunden, aber die Ebene selbst nicht ändern. Als Inhaltsautor können Sie den Mauszeiger über vorhandene Ebenen bewegen, um das Schlosssymbol anzuzeigen. Sie können beliebig viele Ebenen sperren, aber gesperrten Ebenen können keine nicht gesperrten Ebenen vorangehen.

Im Beispiel unten sind die ersten zwei Ebenen gesperrt. Dies bedeutet, dass Berichtsconsumer die Ebenen 3 und 4 ändern und sogar nachfolgende Ebenen erstellen können. Die ersten zwei Ebenen können jedoch nicht geändert werden:

![Analysebaum: Sperrung](media/power-bi-visualization-decomposition-tree/tree-locking.png)

## <a name="known-limitations"></a>Bekannte Einschränkungen

Die maximale Anzahl der Ebenen für den Baum beträgt 50. Die maximale Anzahl von Datenpunkten, die gleichzeitig auf dem Baum visualisiert werden können, beträgt 5.000. Wir kürzen Ebenen, um die oberen „n“ anzuzeigen. Derzeit sind die oberen „n“ pro Ebene auf 10 festgelegt. 

Der Analysebaum wird in den folgenden Szenarien nicht unterstützt:  
-   Lokale Analysis Services-Instanzen

KI-Teilungen werden in den folgenden Szenarien nicht unterstützt:  
-   Azure Analysis Services
-   Direkte Abfrage
-   Power BI-Berichtsserver
-   Webveröffentlichung
-   Komplexe Measures und Measures aus Erweiterungsschemas in „Analyse“

Weitere Vorschaueinschränkungen:
- Power BI Mobile  
- Anheftung an das Dashboard
- Funktionalität zur Datenanzeige
- Unterstützung innerhalb von Q&A

## <a name="next-steps"></a>Nächste Schritte

[Power BI-Ringdiagramm](power-bi-visualization-doughnut-charts.md)

[Power BI-Visualisierungen](power-bi-report-visualizations.md)

