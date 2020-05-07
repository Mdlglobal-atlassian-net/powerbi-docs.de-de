---
title: Hinzufügen eines Filters zu einem Bericht in Power BI
description: Hinzufügen eines Seiten-, Visualisierungs- oder Berichtsfilters zu einem Bericht in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/20/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 143851013679dd0356c1ea5036c3d724b1dc436d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73875173"
---
# <a name="add-a-filter-to-a-report-in-power-bi"></a>Hinzufügen eines Filters zu einem Bericht in Power BI

[!INCLUDE [power-bi-service-new-look-include](includes/power-bi-service-new-look-include.md)]

Dieser Artikel erläutert, wie Sie einem Bericht in Power BI einen Seiten-, Visualisierungs-, Berichts- oder Drillthroughfilter hinzufügen. Die Beispiele in diesem Artikel stammen aus dem Power BI-Dienst. Die dargestellten Schritte sind fast identisch mit denen in Power BI Desktop.

**Wussten Sie schon?** Power BI umfasst eine neue Filterfunktion. Erfahren Sie mehr über die [neue Filteroberfläche in Power BI-Berichten](power-bi-report-filter.md).

![Neue Filteroberfläche](media/power-bi-report-add-filter/power-bi-filter-reading.png)

Power BI bietet eine Reihe verschiedener Arten von Filtern, von manuellen und automatischen Filtern bis hin zu Drillthrough und Pass-through. Erfahren Sie mehr über die [verschiedenen Arten von Filtern](power-bi-report-filter-types.md).

## <a name="filters-in-editing-view-or-reading-view"></a>Filter in der Bearbeitungs- und Leseansicht
Sie können mit Berichten in zwei verschiedenen Ansichten interagieren: in der Leseansicht und in der Bearbeitungsansicht. Die verfügbaren Filterfunktionen hängen von der verwendeten Ansicht ab. Mehr erfahren Sie unter [Informationen zu Filtern und Hervorhebungen in Power BI-Berichten](power-bi-reports-filters-and-highlighting.md).

Dieser Artikel beschreibt, wie Sie Filter im Bericht **Bearbeitungsansicht** erstellen.  Weitere Informationen zu Filtern in der Leseansicht finden Sie unter [Interagieren mit Filtern in der Leseansicht von Berichten](consumer/end-user-report-filter.md).

Da Filter *beibehalten werden*, wenn Sie den Bericht verlassen, behält Power BI Ihre Filter, Slicer und andere vorgenommene Änderungen an der Datenansicht bei. Wenn Sie zum Bericht zurückkehren, können Sie also dort weitermachen, wo Sie aufgehört haben. Wenn Sie Ihre Filteränderungen nicht übernehmen möchten, wählen Sie in der oberen Menüleiste **Auf Standardwert zurücksetzen** aus.

![Schaltfläche „Permanente Filter“](media/power-bi-report-add-filter/power-bi-reset-to-default.png)

## <a name="levels-of-filters-in-the-filters-pane"></a>Filterebenen im Bereich „Filter“
Der Bereich „Filter“ wird auf der rechten Seite des Zeichenbereichs für den Bericht angezeigt, egal ob Sie den Desktop- oder Power BI-Dienst verwenden. Wenn der Filterbereich nicht angezeigt wird, wählen Sie das Symbol „>“ in der oberen rechten Ecke aus, um ihn zu erweitern.

Sie können Filter auf drei verschiedenen Ebenen für den Bericht festlegen: Visual-, Seiten- und Berichtsebene. Sie können auch Drillthroughfilter einrichten. Dieser Artikel beschreibt die verschiedenen Ebenen.

![Der Bereich „Filter“ in der Leseansicht](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

## <a name="add-a-filter-to-a-visual"></a>Hinzufügen eines Filters zu einem Visual
Sie haben zwei Möglichkeiten, einem bestimmten Visual einen Filter auf Visualebene hinzuzufügen. 

* Filtern Sie ein Feld, das bereits von der Visualisierung verwendet wird.
* Identifizieren Sie ein Feld, das noch nicht von der Visualisierung verwendet wird, und fügen Sie dieses Feld direkt dem Bucket **Filter auf visueller Ebene** hinzu.


Dieses Verfahren verwendet übrigens ein Analysebeispiel für den Einzelhandel, das Sie sie herunterladen können, um es nachzuvollziehen. Herunterladen des Inhaltspakets für das [Beispiel „Einzelhandelsanalyse“](sample-retail-analysis.md#get-the-content-pack-for-this-sample).

### <a name="filter-the-fields-in-the-visual"></a>Filtern von Feldern im Visual

1. Wählen Sie **Weitere Optionen (...)**  > **Bericht bearbeiten** aus, um den Bericht in der Bearbeitungsansicht zu öffnen.
   
   ![Schaltfläche „ Bericht bearbeiten“](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Öffnen Sie den Bereich für die Visualisierungen und Filter und den Bereich für die Felder (falls nicht bereits geöffnet).
   
   ![Visualisierungen-, Filter- und Felderbereich](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. Wählen Sie eine Visualisierung aus, um ihn zu aktivieren. Alle Felder, die vom Visual verwendet werden, sind im Bereich **Felder** angegeben und auch im Bereich **Filter** unter der Überschrift **Filter auf visueller Ebene** aufgeführt.
   
   ![Auswählen von Filtern auf Visualebene](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. Jetzt wird einem Feld, das bereits von der Visualisierung verwendet wird, ein Filter hinzugefügt. 
   
    Scrollen Sie zum Bereich **Filter auf visueller Ebene**, und wählen Sie den Pfeil aus, um das Feld zu erweitern, das Sie filtern möchten. In diesem Beispiel wird nach **StoreNumberName** gefiltert.
     
    ![Der Pfeil erweitert den Filter.](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
    
    Legen Sie für die Filtersteuerelemente **Einfaches Filtern**, **Erweiterte Filterung** oder **Top N-Filter** fest. Suchen Sie für dieses Beispiel unter „Einfaches Filtern“ nach **cha**, und wählen Sie diese fünf Geschäfte aus.
     
    ![Suche bei einfachem Filtern](media/power-bi-report-add-filter/power-bi-search-filter.png) 
   
    Die Visualisierung ändert sich und spiegelt den neuen Filter wider. Wenn Sie Ihren Bericht mit dem Filter speichern, sehen Berichtsleser das Visual zunächst mit dem angewendeten Filter. Diesen können sie in der Leseansicht ändern und Werte auswählen oder löschen.
     
    ![Das gefilterte Visual](media/power-bi-report-add-filter/power-bi-search-visual-filter-results.png)
    
    Wenn Sie den Filter für ein Feld verwenden, das in dem Visual verwendet wird, in dem das Feld aggregiert ist (z. B. eine Summe, ein Durchschnitt oder eine Anzahl), filtern Sie nach dem *aggregierten* Wert in jedem Datenpunkt. Daher führt ein Filtern des obigen Visuals nach **This Year Sales > 500000** dazu, dass im Ergebnis nur der Datenpunkt **13 - Charleston Fashion Direct** angezeigt wird. Filter für [Modellmeasures](desktop-measures.md) gelten immer für den aggregierten Wert des Datenpunkts.

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>Filtern mit Feldern, die sich nicht im Visual befindet

Fügen Sie der Visualisierung nun ein neues Feld als Filter auf visueller Ebene hinzu.
   
1. Wählen Sie im Bereich „Felder“ das Feld aus, das Sie als neuen Filter auf visueller Ebene hinzufügen möchten, und ziehen Sie es in den Bereich **Filter auf visueller Ebene**.  In diesem Beispiel wird **District Manager** in den Bucket **Filter auf visueller Ebene** gezogen und **an** in das Suchfeld eingegeben. Dann werden diese drei Manager ausgewählt.
     
    ![Hinzufügen eines Felds zum Bereich „Filter“](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    Beachten Sie, dass **District Manager** der Visualisierung selbst *nicht* hinzugefügt wird. Die Visualisierung besteht weiterhin aus **StoreNumberName** als Achse und aus **This Year Sales** als Wert.  
     
    ![Das Feld ist nicht im Visual](media/power-bi-report-add-filter/power-bi-visualization.png)

    Die Visualisierung selbst wird nun gefiltert, um nur die diesjährigen Umsätze der ausgewählten Manager für die angegebenen Geschäfte anzuzeigen.
     
    ![Das gefilterte Visual](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    Wenn Sie Ihren Bericht mit dem Filter speichern, können Berichtsleser den Filter **District Manager** in der Leseansicht bearbeiten und Werte auswählen oder löschen.
    
    Wenn Sie eine *numerische Spalte* in den Filterbereich ziehen, um einen Filter auf visueller Ebene zu erstellen, wird der Filter auf *die zugrunde liegenden Datenzeilen* angewendet. Wenn Sie beispielsweise einen Filter für das **UnitCost**-Feld hinzufügen und für diesen Filter **UnitCost** > 20 festlegen, werden nur Daten für die Produktzeilen angezeigt, in denen die Stückkosten (UnitCost) größer als 20 sind, unabhängig von den Gesamtstückkosten für die Datenpunkte, die im Visual angezeigt werden.

## <a name="add-a-filter-to-an-entire-page"></a>Hinzufügen eines Filters zu einer kompletten Seite

Sie können auch einen Filter auf Seitenebene hinzufügen, um eine komplette Seite zu filtern.

1. Öffnen Sie im Power BI-Dienst den Bericht „Retail Analysis“ (Einzelhandelsanalyse), und wechseln Sie dann zur Seite **District Monthly Sales** (Monatlicher Umsatz Region). 

2. Wählen Sie **...**  > **Bericht bearbeiten** aus, um den Bericht in der Bearbeitungsansicht zu öffnen.
   
   ![Schaltfläche „ Bericht bearbeiten“](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. Öffnen Sie den Bereich für die Visualisierungen und Filter und den Bereich für die Felder (falls nicht bereits geöffnet).
3. Wählen Sie im Bereich „Felder“ das Feld aus, das Sie als neuen Filter auf Seitenebene hinzufügen möchten, und ziehen Sie es in den Bereich **Filter auf Seitenebene**.  
4. Wählen Sie die Werte aus, die Sie filtern möchten, und legen Sie für die Filtersteuerelemente **Einfaches Filtern** oder **Erweiterte Filterung** fest.
   
   Alle Visualisierungen auf der Seite werden neu gezeichnet, um die Änderung zu übernehmen.
   
   ![Hinzufügen eines Filters und Auswählen von Werten](media/power-bi-report-add-filter/filterpage.gif)

    Wenn Sie Ihren Bericht mit dem Filter speichern, können Berichtsleser den Filter in der Leseansicht bearbeiten und Werte auswählen oder löschen.

## <a name="add-a-drillthrough-filter"></a>Hinzufügen eines Drillthroughfilters
Mit Drillthrough im Power BI-Dienst und Power BI Desktop können Sie eine *Ziel*-Berichtseite erstellen, die auf eine bestimmte Entität fokussiert ist, z.B. einen Lieferanten, Kunden oder Hersteller. Nun können Benutzer auf den anderen Berichtseiten mit der rechten Maustaste auf einen Datenpunkt für die Entität klicken und einen Drillthrough für die fokussierte Seite ausführen.

### <a name="create-a-drillthrough-filter"></a>Erstellen eines Drillthroughfilters
Laden Sie hierfür das [Kundenrentabilitätsbeispiel](sample-customer-profitability.md#get-the-content-pack-for-this-sample) herunter. Angenommen, Sie benötigen eine Seite, die auf Managementgeschäftsbereiche fokussiert ist.

1. Öffnen Sie im Power BI-Dienst den Bericht „Retail Analysis“ (Einzelhandelsanalyse), und wechseln Sie dann zur Seite **District Monthly Sales** (Monatlicher Umsatz Region).

2. Wählen Sie **Weitere Optionen (...)**  > **Bericht bearbeiten** aus, um den Bericht in der Bearbeitungsansicht zu öffnen.
   
   ![Schaltfläche „ Bericht bearbeiten“](media/power-bi-report-add-filter/power-bi-edit-view.png)

1. Fügen Sie dem Bericht eine neue Seite hinzu, und benennen Sie diese **Team Executive** (Teammanager). Dies wird die *Ziel*-Drillthroughseite.
2. Fügen Sie Visualisierungen zum Verfolgen von Schlüsselmetriken für die Geschäftsbereiche der Teammanager hinzu.    
3. Ziehen Sie **Executive** (Führungskraft) aus der Tabelle **Executives** ebenfalls auf den Drillthroughfilter.    
   
    ![Hinzufügen eines Werts zu Drillthroughfiltern](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    Beachten Sie, dass Power BI der Berichtseite einen Zurück-Pfeil hinzufügt.  Wenn der Benutzer auf den Zurück-Pfeil klickt, kehrt er zur *Ausgangs*berichtseite zurück – zu der Seite, auf der er den Drillthrough ausgewählt hat. Halten Sie in der Bearbeitungsansicht die STRG-TASTE gedrückt, um den Pfeil „Zurück“ auszuwählen.
   
     ![Der Zurück-Pfeil](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>Verwenden des Drillthroughfilters
Im Folgenden wird beschrieben, wie der Drillthroughfilter funktioniert.

1. Starten Sie auf der Berichtseite **Team-Scorecard**.    
2. Angenommen, Sie sind Andrew Ma und möchten die „Team Executive“-Berichtseite so gefiltert anzeigen, dass nur Ihre Daten enthalten sind.  Klicken Sie im Flächendiagramm oben links mit der rechten Maustaste auf einen grünen Datenpunkt, um die Menüoption „Drillthrough“ zu öffnen.
   
    ![Starten der Drillthroughaktion](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. Wählen Sie **Drillthrough > Team Executive** aus, um einen Drillthrough zur Berichtseite **Team Executive** (Teammanager) durchzuführen. Die Seite wird so gefiltert, dass Informationen zum Datenpunkt angezeigt werden, auf den Sie mit der rechten Maustaste geklickt haben; in diesem Fall „Andrew Ma“. Alle Filter auf der Ursprungsseite werden auf die Drillthrough-Berichtsseite angewendet.  
   
    ![Auswählen der Drillthroughaktion](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-report-level-filter-to-filter-an-entire-report"></a>Hinzufügen eines Filters auf Berichtsebene zum Filtern eines gesamten Berichts

1. Wählen Sie **Bericht bearbeiten** aus, um den Bericht in der Bearbeitungsansicht zu öffnen.
   
   ![Schaltfläche „ Bericht bearbeiten“](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. Öffnen Sie den Bereich für die Visualisierungen und Filter und den Bereich für die Felder, falls sie nicht bereits geöffnet sind.
3. Wählen Sie im Bereich „Felder“ das Feld aus, das Sie als neuen Filter auf Berichtsebene hinzufügen möchten, und ziehen Sie es in den Bereich **Berichtsstufenfilter**.  
4. Wählen Sie die zu filternden Werte aus.

    Die Visuals auf der aktiven Seite und auf allen Seiten des Berichts ändern sich, um den neuen Filter widerzuspiegeln. Wenn Sie Ihren Bericht mit dem Filter speichern, können Berichtsleser den Filter in der Leseansicht bearbeiten und Werte auswählen oder löschen.

1. Wählen Sie den Zurück-Pfeil aus, um zur vorherigen Berichtseite zurückzukehren.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

- Wenn der Bereich „Felder“ nicht angezeigt wird, stellen Sie sicher, dass Sie die [Bearbeitungsansicht](service-interact-with-a-report-in-editing-view.md) des Berichts geöffnet haben.    
- Wenn Sie viele Änderungen an den Filtern vorgenommen haben und zu den Standardeinstellungen des Berichtsautors zurückkehren möchten, wählen Sie auf der oberen Menüleiste **Auf Standardwert zurücksetzen** aus.

## <a name="next-steps"></a>Weitere Schritte
[Überblick über den Berichtsbereich „Filter“](consumer/end-user-report-filter.md)

[Filter und Hervorhebungen in Berichten](power-bi-reports-filters-and-highlighting.md)

[Verschiedene Filtertypen in Power BI-Berichten](power-bi-report-filter-types.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

