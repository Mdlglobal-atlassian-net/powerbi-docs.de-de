---
title: Wann sollten paginierte Berichte in Power BI verwendet werden?
description: Leitfaden für die Verwendung von paginierten Berichten in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 049b6ac14c6d35d68815eac32520a4eaa654ad42
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920732"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Wann sollten paginierte Berichte in Power BI verwendet werden?

Dieser Artikel richtet sich an Berichtsautoren wie Sie, die Berichte für Power BI entwerfen. Er enthält Vorschläge, die Ihnen bei der Wahl des Zeitpunkts für die Entwicklung von [paginierten Berichten in Power BI Reports](../paginated-reports/paginated-reports-report-builder-power-bi.md) helfen.

> [!NOTE]
> Für die Veröffentlichung von paginierten Berichten in Power BI ist ein Power BI Premium-Abonnement erforderlich. Berichte werden nur dann gerendert, wenn sie sich in einem Arbeitsbereich mit einer dedizierten Kapazität befinden, in dem die [Workload für paginierte Berichte aktiviert ist](../service-admin-premium-workloads.md#paginated-reports).

Paginierte Berichte in Power BI sind für den **Druckvorgang** oder die **PDF-Erstellung** optimiert. Sie bieten Ihnen auch die Möglichkeit, stark formatierte, pixelgenaue Layouts zu erstellen. Daher sind paginierte Berichte ideal für betriebliche Berichte wie Verkaufsrechnungen.

Im Gegensatz dazu sind die Power BI-Berichte für **Recherche und Interaktivität optimiert**. Außerdem können sie Ihre Daten mit einem umfangreichen Angebot an hochmodernen visuellen Elementen präsentieren. Power BI-Berichte sind daher ideal für analytische Berichte, die es Ihren Berichtsanwendern ermöglichen, Daten zu untersuchen und Beziehungen und Muster zu entdecken.

Wir empfehlen Ihnen in folgenden Situationen die Verwendung eines paginierten Berichts in Power BI in Betracht zu ziehen:

- Sie wissen, dass der Bericht gedruckt oder als PDF-Dokument ausgegeben werden muss.
- Datenrasterlayouts könnten sich erweitern und überlaufen. Bedenken Sie, dass eine Tabelle oder Matrix in einem Power BI-Bericht nicht dynamisch in der Größe verändert werden kann, um alle Daten anzuzeigen – stattdessen stellt sie Scrollleisten zur Verfügung. Aber beim Drucken ist ein Scrollen nicht möglich, um Daten anzuzeigen, die außerhalb des Sichtbereichs liegen.
- Features und Funktionen für die Paginierung in Power BI arbeiten zu Ihren Gunsten. Viele solcher Berichtsszenarien werden später in diesem Artikel beschrieben.

## <a name="legacy-reports"></a>Ältere Berichte

Wenn Sie bereits über [RDL](/sql/reporting-services/reports/report-definition-language-ssrs)-Berichte (Report Definition Language) der SQL Server Reporting Services (SSRS) verfügen, können Sie diese als [Power BI-Berichte](../consumer/end-user-reports.md) neu entwickeln oder als paginierte Berichte zu Power BI migrieren. Weitere Informationen finden Sie unter [Migrieren von SQL Server Reporting Services-Berichten zu Power BI](migrate-ssrs-reports-to-power-bi.md).

Nach der Veröffentlichung in einem Power BI-Arbeitsbereich stehen die paginierten Berichte neben den Power BI-Berichten zur Verfügung. Sie können dann einfach über [Power BI-Apps](../service-create-distribute-apps.md) verteilt werden.

Sie könnten erwägen, SSRS-Berichte neu zu entwickeln, anstatt sie zu migrieren. Dies gilt insbesondere für die Berichte, die analytische Erfahrungen liefern sollen. In diesen Fällen werden die Power BI-Berichte wahrscheinlich bessere Benutzererfahrungen hinsichtlich der Berichte liefern.

## <a name="paginated-report-scenarios"></a>Szenarien für paginierte Berichte

Es gibt viele überzeugende Szenarien, in denen Sie die Entwicklung eines paginierten Berichts in Power BI bevorzugen könnten. Viele sind Features oder Funktionen, die von Power BI-Berichten nicht unterstützt werden.

- **Druckreif**: Paginierte Berichte sind für den Druckvorgang oder die PDF-Erstellung optimiert. Bei Bedarf können Datenbereiche auf kontrollierte Weise auf mehrere Seiten erweitert werden und überlaufen. Ihre Berichtslayouts können Ränder sowie Kopf- und Fußzeilen definieren.
- **Renderformate**: Power BI kann paginierte Berichte in verschiedenen Formaten rendern. Zu den Formaten zählen Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML und MHTML. (Das MHTML-Format wird vom Power BI-Dienst zum Rendern von Berichten verwendet.) Ihre Berichtsbenutzer können sich für den Export in dem für sie geeigneten Format entscheiden.
- **Präzisionslayout**: Sie können stark formatierte, pixelgenaue Layouts entwerfen – in exakter Größe und an genau der Stelle, die auf einen Bruchteil eines Zolls oder Zentimeters konfiguriert werden kann.
- **Dynamisches Layout**: Sie können sehr reaktionsfähige Layouts erstellen, indem Sie viele Berichtseigenschaften auf die Verwendung von VB.NET-Ausdrücken festlegen. Ausdrücke haben Zugriff auf viele zentrale .NET Framework-Bibliotheken.
- **Renderspezifisches Layout**: Mithilfe von Ausdrücken können Sie das Berichtslayout auf der Grundlage des verwendeten Renderingformats ändern. Sie können den Bericht z. B. so gestalten, dass das Umschalten der Sichtbarkeit deaktiviert wird (um einen Drilldown und Drillup zu erreichen), wenn er in einem nicht interaktiven Format wie PDF gerendert wird.
- **Native Abfragen**: Sie müssen nicht zuerst ein Power BI-Dataset entwickeln. Sie können für jede [unterstützte Datenquelle](../paginated-reports/paginated-reports-data-sources.md) native Abfragen erstellen (oder gespeicherte Prozeduren verwenden). Die Abfragen können eine Parametrierung einbeziehen.
- **Grafische Abfrage-Designer**: Power BI Report Builder enthält grafische Abfrage-Designer, die Sie beim Schreiben und Testen Ihrer Datasetabfragen unterstützen.
- **Statische Datasets**: Sie können ein Dataset definieren und Daten direkt in Ihre Berichtsdefinition eingeben. Diese Fähigkeit ist besonders nützlich, um eine Demo zu unterstützen oder einen Proof of Concept (POC) bereitzustellen.
- **Datenintegration**: Sie können Daten aus verschiedenen Datenquellen oder mit statischen Datasets kombinieren. Dies erfolgt durch die Erstellung benutzerdefinierter Felder mithilfe von VB.NET-Ausdrücken.
- **Parametrisierung**: Sie können hochgradig angepasste Parametrierungserfahrungen entwerfen, einschließlich datengesteuerter und kaskadierender Parameter. Es ist auch möglich, Standardwerte für Parameter zu definieren. Diese Erfahrungen können so gestaltet werden, dass Ihre Berichtsbenutzer schnell geeignete Filter festlegen können. Außerdem müssen die Parameter nicht die Berichtsdaten filtern; sie können zur Unterstützung von „Was-wäre-wenn“-Szenarien oder zur dynamischen Filterung oder Formatierung verwendet werden.
- **Bilddaten**: In Ihrem Bericht können Bilder gerendert werden, wenn sie im Binärformat in einer Datenquelle gespeichert sind.
- **Benutzerdefinierter Code**: Sie können Codeblöcke von VB.NET-Funktionen in Ihrem Bericht entwickeln und diese in beliebigen Berichtsausdrücken verwenden.
- **Unterberichte**: Sie können andere paginierte Power BI-Berichte (aus demselben Arbeitsbereich) in Ihren Bericht einbetten.
- **Flexible Datenraster**: Sie verfügen über eine präzise Steuerung für Rasterlayouts, indem Sie den Tablix-Datenbereich verwenden. Er unterstützt auch komplexe Layouts, einschließlich geschachtelter und angrenzender Gruppen. Zudem kann er so konfiguriert werden, dass Überschriften beim Drucken über mehrere Seiten wiederholt werden. Außerdem kann er einen Unterbericht oder andere visuelle Elemente einbetten, einschließlich Datenbalken, Sparklines und Indikatoren.
- **Räumliche Datentypen**: Der Kartendatenbereich kann [räumliche SQL Server-Datentypen](/sql/relational-databases/spatial/spatial-data-sql-server) visualisieren. Daher können die Datentypen GEOGRAPHY und GEOMETRY zur Darstellung von Punkten, Linien oder Polygonen verwendet werden. Es ist auch möglich, in ESRI-Shape-Dateien definierte Polygone darzustellen.
- **Moderne Messgeräte**: Radiale und lineare Messgeräte können zur Anzeige von KPI-Werten und Statusinformationen verwendet werden. Sie können sogar in Rasterdatenbereiche eingebettet werden, die sich innerhalb von Gruppen wiederholen.
- **HTML-Rendering**: Sie können umfangreich formatierten Text anzeigen, wenn er als HTML gespeichert ist.
- **Seriendruck**: Sie können Platzhalter für Textfelder verwenden, um Datenwerte in den Text einzufügen. Auf diese Weise können Sie einen Seriendruckbericht erstellen.
- **Interaktivitätsfeatures**: Zu den interaktiven Features gehören das Umschalten der Sichtbarkeit (um einen Drilldown und Drillup zu erreichen), Links, interaktive Sortierung und QuickInfos. Sie können auch Links hinzufügen, die einen Drillthrough zu Power BI-Berichten oder anderen paginierten Berichten in Power BI durchführen. Links können sogar zu einer anderen Stelle innerhalb desselben Berichts springen.
- **Abonnements**: Power BI kann paginierte Berichte nach einem Zeitplan als E-Mails mit Berichtsanlagen in einem beliebigen unterstützten Format liefern.
- **Layouts pro Benutzer**: Sie können reaktionsfähige Berichtslayouts basierend auf dem authentifizierten Benutzer, der den Bericht öffnet, erstellen. Sie können den Bericht so gestalten, dass Daten unterschiedlich gefiltert, Datenbereiche oder Visualisierungen ausgeblendet, unterschiedliche Formate angewendet oder benutzerspezifische Standardwerte für Parameter festgelegt werden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Migrieren von SQL Server Reporting Services-Berichten zu Power BI](migrate-ssrs-reports-to-power-bi.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
