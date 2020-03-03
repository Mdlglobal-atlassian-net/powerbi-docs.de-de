---
title: Von Power BI unterstützte Einblicke
description: Schnelle Einblicke und „Einblicke anzeigen“ in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/24/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: a89cb77b99356f9f282b522c2041e96210a026e9
ms.sourcegitcommit: 4d98274aa0b9aa09db99add2dda91a3ba8fed40b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576762"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Von Power BI unterstützte Einblicke

Mit Power BI können Sie Ihre Daten durchsehen und interessante Trends und Muster finden. Diese Trends und Muster werden in Form von Visuals angezeigt, die *Erkenntnisse* genannt werden. 

Informationen zur Verwendung von Erkenntnissen finden Sie unter [Anzeigen von Erkenntnissen auf Dashboardkacheldaten mit Power BI](end-user-insights.md).

![Mehrere Erkenntnisse](media/end-user-insight-types/power-bi-insight.png)

## <a name="how-does-insights-work"></a>Wie funktionieren Einblicke?
Power BI durchsucht schnell verschiedene Teilmengen Ihres Datasets. Während der Suche nutzt Power BI mehrere hoch entwickelte Algorithmen, um potenziell interessante Erkenntnisse zu ermitteln. *Power BI-Benutzer* können Erkenntnisse auf Dashboardkacheln ausführen.

## <a name="some-terminology"></a>Terminologie
Power BI verwendet statistische Algorithmen, um Erkenntnisse zu gewinnen. Die Algorithmen werden im nächsten Abschnitt dieses Artikels aufgeführt und beschrieben. Bevor sich mit den Algorithmen befasst wird, finden Sie hier Definitionen für einige Begriffe, die Ihnen vielleicht nicht vertraut sind. 

* **Measure**: ein Measure ist ein quantitatives (numerisches) Feld, das für Berechnungen verwendet werden kann. Es können z. B. Summen, der Durchschnitt oder Mindestwerte berechnet werden. Wenn das Unternehmen in diesem Beispiel Skateboards herstellt und verkauft, können die Measures die Anzahl der verkauften Skateboards und der durchschnittliche Jahresgewinn sein.  
* **Dimension:** Dimensionen sind kategorische (Text-)Daten. Eine Dimension beschreibt eine Person, ein Objekt, ein Element, ein Produkt, einen Ort und eine Uhrzeit. In einem Dataset bieten Dimensionen die Möglichkeit, *Measures* in nützliche Kategorien zu gruppieren. Für das Beispiel des Skateboardunternehmens enthalten manche Dimensionen möglicherweise die Prüfung der Verkäufe (ein Measure) anhand des Modells, der Farbe, dem Land oder der Marketingkampagne.   
* **Korrelation:** eine Korrelation gibt Aufschluss darüber, wie bestimmte Verhaltensweisen miteinander verknüpft sind.  Wenn sich die Anstiegs- oder Rückgangsmuster ähneln, besteht eine positive Korrelation. Wenn die Muster gegenteilig sind, besteht eine negative Korrelation. Wenn z. B. nach jeder Marketingkampagne im Fernsehen mehr rote Skateboards verkauft werden, besteht eine positive Korrelation zwischen dem Verkauf von roten Skateboards und der Marketingkampagne im Fernsehen.
* **Zeitreihe:** eine Zeitreihe ist eine Möglichkeit, die Zeit als aufeinander folgende Datenpunkte anzuzeigen. Diese Datenpunkte können Inkremente wie Sekunden, Stunden, Monate oder Jahre sein.  
* **Kontinuierliche Variable:** eine kontinuierliche Variable kann einen beliebigen Wert zwischen dem Mindest- und dem Maximalwert aufweisen; andernfalls handelt es sich um eine diskrete Variable. Beispiele hierfür sind Temperatur, Gewicht, Alter und Zeit. Kontinuierliche Variablen können Teilwerte enthalten. Die Gesamtzahl der verkauften blauen Skateboards ist eine diskrete Variable, da kein halbes Skateboard verkauft werden kann.  

## <a name="what-types-of-insights-can-you-find"></a>Nach welchen Typen von Erkenntnissen kann gesucht werden?
Dies sind die Algorithmen, die Power BI verwendet: 

### <a name="category-outliers-topbottom"></a>Kategorieausreißer (oben/unten)
Dieser hebt Fälle hervor, in denen ein oder zwei Kategorien viel größere Werte als andere Kategorien aufweisen.  

![Beispiel für Kategorieausreißer](./media/end-user-insight-types/pbi-auto-insight-types-category-outliers.png)

### <a name="change-points-in-a-time-series"></a>Änderungspunkte in einer Zeitreihe
Hebt hervor, wenn es signifikante Trendänderungen in einer Zeitreihe von Daten gibt.

![Beispiel für Änderungspunkte im Laufe der Zeit](./media/end-user-insight-types/pbi-auto-insight-types-changepoint.png)

### <a name="correlation"></a>Korrelation
Dieser erkennt Fälle, in denen mehrere Measures ein ähnliches Muster oder einen ähnlichen Trend aufweisen, wenn diese in einer Kategorie oder in einem Wert im Dataset dargestellt werden.

![Beispiel für Korrelation](./media/end-user-insight-types/pbi-auto-insight-types-correlation.png)

### <a name="low-variance"></a>Geringe Abweichung
Erkennt Fälle, bei denen die Datenpunkte für eine Dimension nicht weit vom Mittelwert liegen, sodass die Abweichung gering ist. Angenommen, Sie verfügen über die Kennzahl „Umsatz“ und eine Dimension „Region“. Bei Betrachtung der Region sehen Sie, dass die Differenz zwischen den Datenpunkten und dem Mittelwert (der Datenpunkte) äußerst gering ist. Der Trigger wird ausgelöst, wenn die Abweichung bei den Umsatzzahlen in allen Regionen unter einem bestimmten Schwellenwert liegt. Mit anderen Worten, wenn in allen Regionen ähnliche Umsatzzahlen erfasst werden.

![Beispiel für geringe Abweichung](./media/end-user-insight-types/power-bi-low-variance.png)

### <a name="majority-major-factors"></a>Mehrheit (Hauptfaktoren)
Sucht nach Fällen, in denen eine Mehrheit eines Gesamtwerts beim Aufschlüsseln in eine andere Dimension einem einzelnen Faktor zugeordnet werden kann.  

![Beispiel für Hauptfaktoren](./media/end-user-insight-types/pbi-auto-insight-types-majority.png)

### <a name="overall-trends-in-time-series"></a>Allgemeine Trends in Zeitreihen
Entdeckt Trends nach oben oder unten in Zeitreihendaten.

![Beispiel für allgemeine Trends im Laufe der Zeit](./media/end-user-insight-types/pbi-auto-insight-types-trend.png)

### <a name="seasonality-in-time-series"></a>Saisonabhängigkeit in Zeitreihen
Sucht periodische Muster in Zeitreihendaten, z. B. wöchentliche, monatliche oder jährliche Saisonabhängigkeit.

![Beispiel für Saisonabhängigkeit](./media/end-user-insight-types/pbi-auto-insight-types-seasonality-new.png)

### <a name="steady-share"></a>Stetiger Anteil
Hebt Fälle hervor, in denen eine Beziehung von übergeordneten und untergeordneten Elementen zwischen dem Anteil eines untergeordneten Werts in Bezug auf den Gesamtwert des übergeordneten Elements für eine kontinuierliche Variable vorhanden ist. Die Erkenntnis „Marktanteil“ wird im Kontext einer Kennzahl, einer Dimension oder einer anderen Datum/Uhrzeit-Dimension verwendet. Der Trigger wird ausgelöst, wenn ein bestimmter Dimensionswert (z.B. die Region „Nordosten“) einen konstanten prozentualen Anteil des Gesamtumsatzes für die jeweilige Datum/Uhrzeit-Dimension aufweist.

Diese Erkenntnis ist mit der Erkenntnis „Geringe Abweichung“ vergleichbar, da sich beide Erkenntnisse auf eine nicht vorhandene Änderung eines Werts im Lauf der Zeit beziehen. Mit der Erkenntnis „Marktanteil“ wird jedoch eine nicht vorhandene Änderung des **prozentualen Anteils am Gesamtwert** im Lauf der Zeit gemessen, mit der Erkenntnis „Geringe Abweichung“ hingegen eine nicht vorhandene Änderung bei den absoluten Messwerten einer Dimension.

![Beispiel für stetigen Anteil](./media/end-user-insight-types/pbi-auto-insight-types-steadyshare.png)

### <a name="time-series-outliers"></a>Zeitreihenausreißer
Erkennt in Daten auf einer Zeitreihe, wenn bestimmte Datums- oder Zeitangaben mit sich deutlich von den übrigen Daten unterscheidenden Werten vorliegen.

![Beispiel für Ausreißer im Laufe der Zeit](./media/end-user-insight-types/pbi-auto-insight-types-time-series-outliers.png)

## <a name="next-steps"></a>Nächste Schritte
[Power BI-Einblicke](end-user-insights.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

