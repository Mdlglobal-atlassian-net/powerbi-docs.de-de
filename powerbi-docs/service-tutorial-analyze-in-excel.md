---
title: 'Tutorial: Verwenden von „In Excel analysieren“'
description: In diesem Tutorial beginnen Sie in Excel und stellen eine Verbindung zu der Seite „Power BI-Datasets“ her, um Datasets in Excel zu importieren.
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/13/2020
ms.author: tekulka
LocalizationGroup: Connect to services
ms.openlocfilehash: 9a8dd1eb7aa6b239cc542884ab3fae3679997017
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80464598"
---
# <a name="tutorial-use-power-bi-analyze-in-excel-starting-in-excel"></a>Tutorial: Verwenden von „In Excel analysieren“

Wenn in Ihrer Organisation Power BI für die Freigabe des Datenzugriffs verwendet wird, Sie starten die Power BI-Funktion „In Excel analysieren“ aus Excel, um PivotTables und PivotCharts in Excel zu erstellen. Diese können zusätzlichen Kontext in Ihre Analyse einbringen oder den Zeitaufwand reduzieren, relevante Datasets zu finden und zu importieren.

Klicken Sie zum Einstieg in ein Power BI-Dataset in Excel auf „In Excel analysieren“. Sie werden daraufhin durch die Erstellung einer PivotTable geführt, die die Daten verwendet.  

Wenn Sie zur Seite „Datasets“ zurückkehren, können Sie zusätzliche, von Ihrer Organisation freigegebene Datasets finden.

Klicken Sie im entsprechenden Schritt im Flow darunter auf **Nein**, und senden Sie Feedback über das verlinkte Formular, falls zu irgendeinem Zeitpunkt Probleme auftreten sollten.  

In diesem Tutorial erhalten Sie Informationen zu den folgenden Vorgängen:

> [!div class="checklist"]
> * Herunterladen einer ODC-Datei von der Seite „Power BI-Datasets“
> * Aktivieren des Zugriffs auf Ihr Dataset aus Excel
> * Verwenden des Datasets, um PivotTables, PivotCharts und Arbeitsblätter zu erstellen

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial benötigen Sie Folgendes:

* Ein Power BI-Konto. Wenn Sie noch nicht bei Power BI registriert sind, müssen Sie sich zuerst für eine [kostenlose Testversion registrieren](https://app.powerbi.com/signupredirect?pbi_source=web).

* Stellen Sie sicher, dass Sie sich mit allen Schritten im [Tutorial: Erste Schritte mit dem Power BI-Dienst](https://docs.microsoft.com/power-bi/service-get-started) gut auskennen.

* Wenn Sie ein Power BI Premium-Dataset und eine Power BI Pro-Lizenz benötigen, finden Sie im Artikel [Was ist Power BI Premium?](https://docs.microsoft.com/power-bi/service-premium-what-is) weitere Informationen.

* Der Artikel [In Excel analysieren](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements) enthält eine vollständige Liste aller Voraussetzungen.

* Sie benötigen ein aktives [Microsoft Office E5-Abonnement](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab).

## <a name="get-started"></a>Erste Schritte

Öffnen Sie Excel, klicken Sie auf die Option zum Erstellen von PivotTables mit freigegebenen Power BI-Daten, und navigieren Sie zur Seite „Power BI-Datasets“.

![Seite „Datasets“](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

Während Sie den Workflow „In Excel analysieren“ verwenden, werden mehrere Aufforderungen angezeigt, die Sie durch die Schritte führen und Ihnen angeben, ob Sie jeden einzelnen abgeschlossen haben und fortfahren können. Klicken Sie auf **Nein**, und senden Sie Ihr Feedback über das entsprechende Formular, falls zu irgendeinem Zeitpunkt Probleme auftreten.

![Workflowanleitung](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>Herunterladen und Öffnen der ODC-Datei

Wählen Sie Ihr Dataset aus der entsprechenden Liste und dem dazugehörigen Arbeitsbereich aus, und klicken Sie dann auf „In Excel analysieren“. Anschließend erstellt Power BI eine ODC-Datei und lädt sie aus dem Browser auf Ihren Computer herunter.

![Dataset auswählen](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

Wenn Sie die Datei in Excel öffnen, wird eine leere PivotTable und die Liste „Felder“ mit allen Tabellen, Feldern und Measures aus dem Power BI-Dataset angezeigt. Sie können PivotTables und Diagramme erstellen und das Dataset wie bei Verwendung eines lokalen Dataset in Excel analysieren.

## <a name="enable-data-connections"></a>Aktivieren von Datenverbindungen

Sie werden möglicherweise dazu aufgefordert, die Verbindung als vertrauenswürdig einzustufen, um Power BI-Daten in Excel analysieren zu können. Administratoren können die Verwendung des Features „In Excel analysieren“ über das Power BI-Verwaltungsportal für lokale Datasets deaktivieren, die in Analysis Services-Datenbanken gespeichert sind.

![Aktivieren der Verbindung](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>Installieren von Updates und Authentifizieren

Möglicherweise werden Sie beim ersten Öffnen einer ODC-Datei auch dazu aufgefordert, sich mit Ihrem Power BI-Konto zu authentifizieren.  Falls Probleme auftreten, finden Sie im Artikel [In Excel analysieren](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi ) umfassende Informationen zu diesem Thema. Stattdessen können Sie im Workflow auch auf „Nein“ klicken.

![Aktivieren der Verbindung](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>Trotzdem analysieren

Ähnlich wie bei anderen lokalen Arbeitsmappen können Sie mithilfe von „In Excel analysieren“ PivotTables und PivotCharts erstellen, Daten hinzufügen und verschiedene Arbeitsmappen mit Ansichten Ihrer Daten erstellen. Das Feature „In Excel analysieren“ macht alle Detaildaten für jeden Benutzer verfügbar, der eine Zugriffsberechtigung für das Dataset hat. Sie können diese Arbeitsmappe zwar speichern, allerdings nicht veröffentlichen, zurück in Power BI importieren oder für andere Benutzer in Ihrer Organisation freigeben. Weitere Informationen und Anwendungsfälle finden Sie unter [In Excel analysieren](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away).

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Interaktionen mit dem Power BI-Dienst und der Seite „Datasets“ sollten auf das Herunterladen der ODC-Datei und das Durchklicken des Workflows beschränkt sein. Falls bei einem dieser Schritte Probleme auftreten, können Sie im entsprechenden Schritt **Nein** angeben und Feedback über das verlinkte Formular senden. Das Formular enthält einen Link zu weiteren Informationen über das Problem. Rufen Sie noch einmal die Seite „Datasets“ auf, um den Vorgang zu wiederholen oder ein anderes Dataset auszuwählen.

## <a name="next-steps"></a>Nächste Schritte

Folgende Artikel könnten Sie ebenfalls interessieren:

* [Use cross-report drillthrough in Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through) (Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop)

* [Verwenden von Slicern in Power BI Desktop](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
