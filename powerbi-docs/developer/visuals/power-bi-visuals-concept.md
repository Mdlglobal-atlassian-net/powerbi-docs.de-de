---
title: Power BI-Visuals – Konzepte
description: In diesem Artikel wird beschrieben, wie Visuals in Power BI integriert werden und wie ein Benutzer mit einem Visual in Power BI interagieren kann.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 96f1fd217a59ee95aed05b790800024dc9f72be9
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378139"
---
# <a name="visuals-in-power-bi"></a>Visuals in Power BI

In diesem Artikel wird beschrieben, wie Visuals in Power BI integriert werden und wie ein Benutzer mit einem Visual in Power BI interagieren kann. 

Die folgende Abbildung zeigt, wie gängige, auf Visuals basierende Aktionen, die von einem Benutzer ausgeführt werden – beispielsweise das Auswählen eines Lesezeichens –, in Power BI verarbeitet werden.

![Diagramm: Aktionen mit Power BI-Visuals](media/power-bi-visuals-concept/visual-concept.svg)

## <a name="visuals-get-updates-from-power-bi"></a>Visuals erhalten Aktualisierungen von Power BI

Ein Visual ruft eine `update`-Methode auf, um Aktualisierungen von Power BI zu erhalten. Die `update`-Methode enthält normalerweise die Hauptlogik des Visuals und ist für das Rendern eines Diagramms bzw. Visualisieren von Daten zuständig.

Updates werden ausgelöst, wenn das Visual die `update`-Methode aufruft.

## <a name="action-and-update-patterns"></a>Aktions- und Aktualisierungsmuster

Aktionen und anschließende Aktualisierungen in Power BI-Visuals erfolgen nach einem der folgenden drei Muster:

* Der Benutzer interagiert über Power BI mit einem Visual.
* Der Benutzer interagiert direkt mit dem Visual.
* Das Visual interagiert mit Power BI.

### <a name="user-interacts-with-a-visual-through-power-bi"></a>Der Benutzer interagiert über Power BI mit einem Visual

* Ein Benutzer öffnet den Eigenschaftenbereich eines Visuals.

    Wenn ein Benutzer den Eigenschaftenbereich eines Visuals öffnet, ruft Power BI unterstützte Objekte und Eigenschaften aus der Datei *capabilities.json* des Visuals ab. Um die tatsächlichen Werte der Eigenschaften abzurufen, ruft Power BI die `enumerateObjectInstances`-Methode des Visuals auf. Das Visual gibt die tatsächlichen Werte der Eigenschaften zurück.

    Weitere Informationen finden Sie unter [Funktionen und Eigenschaften von Power BI-Visuals](capabilities.md).

* Ein Benutzer [ändert eine Eigenschaft des Visuals](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) im Bereich „Format“.

    Wenn ein Benutzer im Formatbereich den Wert einer Eigenschaft ändert, ruft Power BI die `update`-Methode des Visuals auf. Power BI übergibt das neue `options`-Objekt an die `update`-Methode. Das Objekt enthält die neuen Werte.

    Weitere Informationen finden Sie unter [Objekte und Eigenschaften von Power BI-Visuals](objects-properties.md).

* Ein Benutzer ändert die Größe des Visuals.

    Wenn ein Benutzer die Größe eines Visuals ändert, ruft Power BI die `update`-Methode mit dem neuen `options`-Objekt auf. Das `options`-Objekt enthält geschachtelte `viewport`-Objekte mit der neuen Breite und Höhe des Visuals.

* Ein Benutzer wendet einen Filter auf Berichts-, Seiten- oder Visualebene an.

    Power BI filtert die Daten basierend auf den Filterbedingungen. Power BI ruft die `update`-Methode des Visuals auf, um das Visual mit neuen Daten zu aktualisieren.

    Das Visual erhält eine neue Aktualisierung der `options`-Objekte, wenn eins der geschachtelten Objekte neue Daten enthält. Der genaue Ablauf der Aktualisierung richtet sich nach der Konfiguration der Zuordnung für die Datenansicht des Visuals.

    Weitere Informationen finden Sie unter [Grundlegendes zur Zuordnung von Datenansichten in Power BI-Visuals](dataview-mappings.md).

* Ein Benutzer wählt einen Datenpunkt in einem anderen Visual im Bericht aus.

    Wenn ein Benutzer einen Datenpunkt in einem anderen Visual im Bericht auswählt, filtert oder hebt Power BI die ausgewählten Datenpunkte hervor und ruft die `update`-Methode des Datenpunkts auf. Das Visual erhält neue gefilterte Daten oder dieselben Daten mit einem Array von Hervorhebungen.

    Weitere Informationen finden Sie unter [Hervorheben von Datenpunkten in Power BI-Visuals](highlight.md).

* Ein Benutzer wählt im Bereich „Lesezeichen“ des Berichts ein Lesezeichen aus.

    Wenn ein Benutzer im Lesezeichenbereich des Berichts ein Lesezeichen auswählt, kann eine von zwei Aktionen ausgeführt werden:

    * Power BI ruft eine Funktion auf, die von der `registerOnSelectionCallback`-Methode übergeben und registriert wird. Die Rückruffunktion ruft Array mit Auswahloptionen für das entsprechende Lesezeichen auf.

    * Power BI ruft die `update`-Methode mit einem entsprechenden `filter`-Objekt innerhalb des `options`-Objekts auf.

    In beiden Fällen muss das Visual seinen Zustand gemäß den empfangenen Auswahloptionen oder gemäß dem `filter`-Objekt ändern.

    Weitere Informationen zu Lesezeichen und Filtern finden Sie unter [API für visuelle Filter für Power BI-Visuals](filter-api.md).

### <a name="user-interacts-with-the-visual-directly"></a>Der Benutzer interagiert direkt mit dem Visual

* Ein Benutzer zeigt mit der Maus auf ein Datenelement.

    Ein Visual kann über die API für Power BI-QuickInfos weitere Informationen zu einem Datenpunkt anzeigen. Wenn ein Benutzer mit der Maus auf ein Visual zeigt, kann das Visual das Ereignis verarbeiten und Daten zum zugehörigen QuickInfo-Element anzeigen. Das Visual kann entweder eine standardmäßige QuickInfo oder eine QuickInfo der Berichtsseite anzeigen.

    Weitere Informationen finden Sie unter [QuickInfos in Power BI-Visuals](add-tooltips.md).

* Ein Benutzer ändert die Eigenschaften eines Visuals. (Beispiel: Ein Benutzer erweitert eine Struktur, und das Visual speichert den Zustand in den Visualeigenschaften.)

    Ein Visual kann mithilfe der Power BI-API Eigenschaftswerte speichern. Wenn ein Benutzer beispielsweise mit dem Visual interagiert, und das Visual Eigenschaftswerte speichern oder aktualisieren muss, kann es die `presistProperties`-Methode aufrufen.

* Ein Benutzer wählt eine URL aus.

    Standardmäßig kann ein Visual URLs nicht direkt öffnen. Stattdessen kann das Visual die `launchUrl`-Methode aufrufen und die URL als Parameter übergeben, um eine URL in einer neuen Registerkarte zu öffnen.

    Weitere Informationen finden Sie unter [Erstellen einer Start-URL](launch-url.md).

* Ein Benutzer wendet über das Visual einen Filter an.

    Ein Visual kann die `applyJsonFilter`-Methode aufrufen und Bedingungen übergeben, um nach Daten in anderen Visuals zu filtern. Es stehen verschiedene Arten von Filtern zur Verfügung, beispielsweise einfache Filter, erweiterte Filter und Tupelfilter.

    Weitere Informationen finden Sie unter [API für visuelle Filter für Power BI-Visuals](filter-api.md).

* Ein Benutzer wählt Elemente in einem Visual aus.

    Weitere Informationen zu Auswahloptionen in einem Power BI-Visual finden Sie unter [Power BI-Visuals interaktiv gestalten mithilfe von Auswahloptionen](selection-api.md).

### <a name="visual-interacts-with-power-bi"></a>Das Visual interagiert mit Power BI

* Ein Visual fordert mehr Daten von Power BI an.

    Ein Visual verarbeitet Daten nacheinander. Die API-Methode `fetchMoreData` fordert das nächste Datenfragment im Dataset an.

    Weitere Informationen finden Sie unter [Abrufen größerer Datenmengen von Power BI](fetch-more-data.md).

* Der Ereignisdienst wird ausgelöst.

    Power BI kann einen Bericht als PDF exportieren oder per E-Mail senden (gilt nur für zertifizierte Visuals). Um Power BI zu benachrichtigen, dass das Rendern abgeschlossen und das Visual zur Erfassung als PDF oder E-Mail bereit ist, muss das Visual die API zum Rendern von Ereignissen aufrufen.

    Weitere Informationen finden Sie unter [Exportieren von Power BI-Berichten als PDF-Dateien](../../consumer/end-user-pdf.md).

    Informationen zum Ereignisdienst finden Sie unter [Rendern von Ereignissen in Power BI-Visuals](event-service.md).

## <a name="next-steps"></a>Nächste Schritte

Möchten Sie eigene Visualisierungen erstellen und zu Microsoft AppSource hinzufügen? Informationen hierzu finden Sie in diesen Artikeln:

* [Entwickeln eines Power BI-Visuals](./custom-visual-develop-tutorial.md)
* [Veröffentlichen von Power BI-Visuals in Partner Center](office-store.md)
