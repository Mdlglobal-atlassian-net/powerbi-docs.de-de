---
title: Bewährte Methoden für die Leistung von Power BI Embedded
description: Dieser Artikel enthält Anleitungen zu bewährten Methoden für Embedded Analytics
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: 7284532d95cce780f4022477faab9033adcd764a
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79492604"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Bewährte Methoden für die Leistung von Power BI Embedded

Dieser Artikel enthält Empfehlungen zum schnelleren Rendern von Berichten, Dashboards und Kacheln in Ihrer Anwendung.

> [!Note]
> Beachten Sie, dass die Ladezeit in der Hauptsache von Elementen abhängt, die für den eigentlichen Bericht und die Daten relevant sind, einschließlich visueller Elemente, der Größe der Daten und der Komplexität der Abfragen und berechneten Measures. Weitere Informationen finden Sie im [Leitfaden für die Optimierung von Power BI](../../guidance/power-bi-optimization.md).

## <a name="update-tools-and-sdk-packages"></a>Aktualisieren von Tools und SDK-Paketen

Halten Sie Tools und SDK-Pakete auf dem aktuellen Stand.

* Verwenden Sie immer die aktuellste Version von [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installieren Sie die aktuellste Version des [Power BI-Client-SDKs](https://github.com/Microsoft/PowerBI-JavaScript). Wir veröffentlichen fortlaufend weitere Verbesserungen, also sehen Sie von Zeit zu Zeit einmal nach.

## <a name="embed-parameters"></a>Einbettungsparameter

Die `powerbi.embed(element, config)`-Methode erhält ein Element und eine Konfiguration. Der Konfigurationsparameter enthält Felder, die Einfluss auf die Leistung haben.

### <a name="embed-url"></a>Einbettungs-URL

Vermeiden Sie es, die Einbettungs-URL selbst zu erstellen. Achten Sie stattdessen darauf, die Einbettungs-URL durch einen Aufruf der [Get reports](/rest/api/power-bi/reports/getreportsingroup)-, [Get dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup)- oder [Get tiles](/rest/api/power-bi/dashboards/gettilesingroup)-API abzurufen. Wir haben der URL einen neuen Parameter mit der Bezeichnung **_config_** hinzugefügt, der für Leistungsverbesserungen verwendet wird.

### <a name="permissions"></a>Berechtigungen

Erteilen Sie die Berechtigung **Ansicht**, wenn Sie keinen Bericht im Bearbeitungsmodus einbetten möchten. Auf diese Weise initialisiert der Einbettungscode keine Komponenten, die im Bearbeitungsmodus verwendet werden.

### <a name="filters-bookmarks-and-slicers"></a>Filter, Lesezeichen und Slicer

Normalerweise werden Visuals für Berichte mit zwischengespeicherten Daten gespeichert. Aufgrund der zwischengespeicherten Daten verbessert sich die gefühlte Leistung. Berichte können zwischengespeicherte Daten rendern, während die Abfragen ausgeführt werden. Wenn Filter, Textmarken oder Datenschnitte angegeben werden, sind zwischengespeicherte Daten nicht relevant, und die visuellen Elemente werden erst nach dem Abschluss der Abfrage der visuellen Elemente gerendert.

Beim Einbinden von Berichten mit den gleichen Filtern, Textmarken und Datenschnitten können Sie die Leistung verbessern, indem Sie den Bericht mit bereits angewendeten Filtern, Textmarken und Datenschnitten speichern. Dadurch wird der Bericht mit den zwischengespeicherten Daten gerendert, einschließlich der Filter, Textmarken und Datenschnitte.

## <a name="switching-between-reports"></a>Wechseln zwischen Berichten

Generieren Sie beim Einbetten mehrerer Berichte in den gleichen iFrame nicht für jeden Bericht einen neuen iFrame. Verwenden Sie stattdessen `powerbi.embed(element, config)` mit einer anderen Konfiguration, um den neuen Bericht einzubetten.

> [!NOTE]
> Das Wechseln zwischen Berichten in einem Szenario „App besitzt Daten“ ist aufgrund des Erfordernisses, ein neues Einbettungstoken zu generieren, möglicherweise nicht besonders effektiv.

## <a name="query-caching"></a>Zwischenspeicherung von Abfragen

Organisationen mit Power BI Premium-Funktionen oder Power BI Embedded-Funktionen können von der Zwischenspeicherung von Abfragen profitieren, um Berichte, die einem Dataset zugeordnet sind, zu beschleunigen.

[Weitere Informationen zum Zwischenspeichern von Abfragen in Power BI](../../power-bi-query-caching.md).

## <a name="preload"></a>Vorab Laden

Verwenden Sie `powerbi.preload()`, um die Leistung für Endbenutzer zu verbessern. Die Methode `powerbi.preload()` lädt Javascript, CSS-Dateien und andere Artefakte herunter, die später zum Einbetten eines Berichts verwendet werden.

Rufen Sie `powerbi.preload()` auf, wenn Sie den Bericht nicht sofort einbetten. Wenn beispielsweise die eingebetteten Power BI-Inhalte nicht auf der Startseite angezeigt werden, verwenden Sie `powerbi.preload()`, um die Artefakte, die zum Einbetten der Inhalte verwendet werden, herunterzuladen und zwischenzuspeichern.

## <a name="bootstrapping-the-iframe"></a>Bootstrapping des iFrames

> [!NOTE]
> [Power BI-Client SDK](https://github.com/Microsoft/PowerBI-JavaScript), Version 2.9, ist zum Bootstrappen des iFrames erforderlich.

`powerbi.bootstrap(element, config)` ermöglicht Ihnen, mit dem Einbetten zu beginnen, bevor alle erforderlichen Parameter verfügbar sind. Die Bootstrap-API bereitet den iFrame vor und initialisiert ihn.
Wenn Sie die Bootstrap-API verwenden, ist trotzdem ein Aufruf von `powerbi.embed(element, config)` für das gleiche HTML-Element erforderlich.

Beispielsweise besteht einer der Anwendungsfälle für diese Funktion in der parallelen Ausführung des iFrame-Bootstraps und der Back-End-Aufrufe zum Einbetten.
> [!TIP]
> Verwenden Sie die Bootstrap-API, wenn es möglich ist, den iFrame zu generieren, bevor er für den Endbenutzer sichtbar ist.

[Weitere Informationen über iFrame-Bootstrap](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Messen der Leistung

### <a name="performance-events"></a>Leistungsereignisse

Zum Messen der eingebetteten Leistung können Sie zwei Ereignisse verwenden:

1. Ereignis „Geladen“: Die Zeit bis zur Initialisierung des Berichts (das Power BI Logo verschwindet, wenn das Laden abgeschlossen ist).
2. Ereignis „Gerendert“: Die Zeit bis zum vollständigen Rendern des Berichts unter Verwendung der tatsächlichen Daten. Das Gerendert-Ereignis wird bei jedem erneuten Rendern des Berichts ausgelöst (beispielsweise nach der Anwendung von Filtern). Achten Sie bei der Messung eines Berichts darauf, die Berechnungen auf der Grundlage des zuerst ausgelösten Ereignisses durchzuführen.

Zwischengespeicherte Daten werden gerendert, wenn sie verfügbar sind, es wird aber kein zusätzliches Ereignis generiert.

[Weitere Informationen zum Ereignishandling](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Leistungsanalyse

Um die Leistung der Berichtselemente zu untersuchen, können Sie die Leistungsanalyse in Power BI Desktop verwenden.
Mit der Leistungsanalyse können Sie Protokolle aufzeichnen und anzeigen, die die Leistung jedes Ihrer Berichtselemente messen.

[Weitere Informationen zur Leistungsanalyse](../../desktop-performance-analyzer.md)

> [!NOTE]
> Denken Sie immer daran, die Leistung eines eingebetteten Berichts mit der Leistung auf powerbi.com zu vergleichen. Dies kann Ihnen dabei helfen, den Ursprung von Leistungsproblemen zu verstehen.

## <a name="next-steps"></a>Nächste Schritte

* [Leitfaden für die Optimierung von Power BI](../../guidance/power-bi-optimization.md)
* [Behandeln von Problemen mit Power BI Embedded](embedded-troubleshoot.md)
* [Power BI Embedded – FAQ](embedded-faq.md)
