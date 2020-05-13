---
title: Kennenlernen des Analysebeispiels für den Einzelhandel
description: Hier erhalten Sie Informationen über das Analysebeispiel für den Einzelhandel und erfahren, wie Sie es im Power BI-Dienst und in Power BI Desktop installieren.
author: maggiesMSFT
ms.reviewer: amac
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/27/2020
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 257385b42cb31c691c649abe4ea5ad5a88453f7c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349676"
---
# <a name="explore-the-retail-analysis-sample"></a>Kennenlernen des Analysebeispiels für den Einzelhandel

In diesem Tutorial wird Folgendes gezeigt: 
- Importieren des Beispielinhaltspakets für die Einzelhandelsanalyse, Hinzufügen des Pakets zum Power BI-Dienst und Öffnen des Inhalts. Ein *Inhaltspaket* ist ein Beispieltyp, in dem das Dataset mit einem Dashboard und einem Bericht gebündelt ist. 
- Öffnen der PBIX-Datei mit dem Analysebeispiel für den Einzelhandel in Power BI Desktop.

Wenn Sie weitere Hintergrundinformationen wünschen, lesen Sie [Welche Beispieldaten sind für die Verwendung mit Power BI verfügbar?](sample-datasets.md). In diesem Artikel erfahren Sie alles über die Beispiele: wie Sie sie erhalten, wo Sie sie speichern und wie Sie sie verwenden, sowie einige der Geschichten, die jedes Beispiel erzählen kann. 

## <a name="prerequisites"></a>Voraussetzungen
Die Beispiele sind für den Power BI-Dienst und für Power BI Desktop verfügbar. In diesem Tutorial wird das Analysebeispiel für den Einzelhandel verwendet.

Das in diesem Tutorial verwendete Beispielinhaltspaket zur *Einzelhandelsanalyse* besteht aus einem Dashboard, einem Bericht und einem Dataset.
Um sich mit diesem bestimmten Inhaltspaket und dessen Szenario vertraut zu machen, lesen Sie [Analysebeispiel für Einzelhandel für Power BI: Übersicht](sample-retail-analysis.md), bevor Sie beginnen.

## <a name="import-the-sample-in-the-power-bi-service"></a>Importieren des Beispiels in den Power BI-Dienst

1. Öffnen Sie den Power BI-Dienst (app.powerbi.com), melden Sie sich an, und öffnen Sie den Arbeitsbereich, in dem Sie das Beispiel speichern möchten. 

    Wenn Sie nicht über eine Power BI Pro-Lizenz verfügen, können Sie das Beispiel in Ihrem Arbeitsbereich speichern.

2. Wählen Sie unten im Navigationsbereich **Daten abrufen** aus. 

   ![„Daten abrufen“ auswählen](media/sample-datasets/power-bi-get-data.png)

   Wenn **Daten abrufen** nicht angezeigt wird, erweitern Sie den Navigationsbereich, indem Sie am oberen Rand des Bereichs das folgende Symbol auswählen: ![Hamburger-Symbol](media/sample-tutorial-connect-to-the-samples/expand-nav.png).

5. Klicken Sie auf der daraufhin angezeigten Seite **Daten abrufen** auf **Beispiele**.
   
6. Wählen Sie das **Analysebeispiel für Einzelhandel** und dann **Verbinden** aus.   
   
   ![Schaltfläche „Verbinden“](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-was-imported"></a>Was wurde importiert?
Wenn Sie für ein Beispielinhaltspaket die Option **Verbinden** auswählen, ruft Power BI eine Kopie dieses Inhaltspakets ab und speichert das Paket für Sie in der Cloud. Da die Person, die das Inhaltspaket erstellt hat, ein Dataset, einen Bericht und ein Dashboard in das Paket eingebunden hat, erhalten Sie diese Komponenten, wenn Sie **Verbinden** auswählen. 

1. Wenn Sie **Verbinden** auswählen, erstellt Power BI das neue Dashboard und listet es auf der Registerkarte **Dashboards** auf. 
   
   ![Eintrag „Analysebeispiel für den Einzelhandel“](media/sample-retail-analysis/retail-entry.png)
2. Öffnen Sie die Registerkarte **Berichte**. Hier wird ein neuer Bericht mit dem Namen *Analysebeispiel für Einzelhandel* angezeigt.
   
   ![Eintrag für den Bericht „Analysebeispiel für den Einzelhandel“](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Sehen Sie sich die Registerkarte **Datasets** an. Auf dieser gibt es nun ein neues Dataset.
   
   ![Eintrag für das Dataset für „Analysebeispiel für den Einzelhandel“](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Untersuchen der neuen Inhalte
Untersuchen Sie jetzt selbstständig das Dashboard, das Dataset und den Bericht. Es gibt viele verschiedene Möglichkeiten, zu Dashboards, Berichten und Datasets zu navigieren. Eine dieser Möglichkeiten ist in der folgenden Vorgehensweise beschrieben.  

1. Navigieren Sie zurück zur Registerkarte **Dashboards**, und wählen Sie dann das Dashboard **Analysebeispiel für den Einzelhandel** aus, um es zu öffnen.       

   Das Dashboard wird geöffnet, und dessen Visualisierungskacheln werden angezeigt.   
 
1. Wählen Sie eine der Kacheln auf dem Dashboard aus, um den zugrunde liegenden Bericht zu öffnen. In diesem Beispiel wird das Flächendiagramm **This Year's Sales, Last Year's Sales by Fiscal Month** (Umsatz dieses Jahr, Vorjahresumsatz nach Geschäftsmonat) ausgewählt.  

   ![Dashboard „Analysebeispiel für den Einzelhandel“ mit markiertem visuellen Element](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)

   Der Bericht wird mit der Seite geöffnet, die das von Ihnen ausgewählte Flächendiagramm enthält. In diesem Fall ist dies die Berichtsseite **District Monthly Sales** (Monatliche Umsätze nach Bezirk).
   
   ![Berichtsseite „District Monthly Sales“ (Monatliche Umsätze nach Bezirk)](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Wurde die Kachel mit [Power BI Q&A](power-bi-tutorial-q-and-a.md) erstellt, wird stattdessen die Q&A-Seite geöffnet. Wurde die Kachel [aus Excel angeheftet](service-dashboard-pin-tile-from-excel.md), wird Excel Online in Power BI geöffnet.
   > 
   > 
1. Wenn eine Person ein Inhaltspaket für Kollegen freigibt, möchte diese Person normalerweise nur die Erkenntnisse freigeben, statt direkten Zugriff auf die Daten zu gewähren. Auf der Registerkarte **Datasets** haben Sie mehrere Möglichkeiten, das Dataset zu untersuchen. Sie können jedoch nicht die Zeilen und Spalten Ihrer Daten anzeigen, wie Sie dies in Power BI Desktop oder Excel tun können. 
   
   ![Eintrag für das Dataset für „Analysebeispiel für den Einzelhandel“](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)
   
1. Eine der Möglichkeiten zum Erkunden des Datasets besteht darin, Visualisierungen und Berichte von Grund auf neu zu erstellen. Klicken Sie auf das Diagrammsymbol, ![Diagrammsymbol](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) um das Dataset im Berichtsbearbeitungsmodus zu öffnen.
     
   ![Vollständig neuer Bericht](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)

1. Eine weitere Möglichkeit zum Erkunden des Datasets besteht darin, [Quick Insights](../consumer/end-user-insights.md) (Schnelleinblicke) auszuführen. Wählen Sie **Weitere Optionen** (...) und dann **Schnelle Einblicke gewinnen** aus. Wenn die Einblicke bereit sind, wählen Sie **Einblicke anzeigen** aus.
     
    ![Bericht zu Erkenntnissen](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="download-the-sample-in-power-bi-desktop"></a>Herunterladen des Beispiels in Power BI Desktop 
Wenn Sie die PBIX-Beispieldatei zum ersten Mal in Power BI Desktop öffnen, wird sie in der Berichtsansicht angezeigt, in der Sie beliebig viele Berichtsseiten mit Visualisierungen erkunden, erstellen und bearbeiten können. Die Berichtsansicht bietet nahezu den gleichen Funktionsumfang wie die Bearbeitungsansicht für Berichte im Power BI-Dienst. Sie können Visualisierungen verschieben, kopieren, einfügen, zusammenführen usw. 

Anders als Bearbeiten eines Berichts im Power BI-Dienst können Sie in Power BI Desktop auch mit Abfragen arbeiten und Daten modellieren, sodass Sie sicherstellen können, dass die Daten in Ihren Berichten optimale Einblicke bieten. Sie können die Power BI Desktop-Datei dann jederzeit entweder auf Ihrem lokalen Laufwerk oder in der Cloud speichern.

1. Laden Sie die [PBIX-Datei mit dem Analysebeispiel für den Einzelhandel](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) herunter, und öffnen Sie die Datei in Power BI Desktop. 

    ![Beispiel in der Berichtsansicht von Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. Die Datei wird in der Berichtsansicht geöffnet. Beachten Sie die vier Registerkarten am unteren Rand des Berichts-Editors. Diese Registerkarten entsprechen den vier Seiten in diesem Bericht. Für dieses Beispiel ist aktuell die Seite **New Stores** (Neue Geschäfte) ausgewählt. 

    ![Hervorgehobene Registerkarte „New Stores“ (Neue Geschäfte)](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

1. Detaillierte Informationen zum Berichts-Editor finden Sie unter [Einführung in den Berichts-Editor in Power BI](service-the-report-editor-take-a-tour.md).

## <a name="whats-in-your-report"></a>Welche Bestandteile hat der Bericht?
Wenn Sie eine PBIX-Beispieldatei herunterladen, wird nicht nur ein Bericht, sondern auch das *zugrunde liegende Dataset* heruntergeladen. Wenn Sie die Datei öffnen, lädt Power BI Desktop die Daten mit den zugehörigen Abfragen und Beziehungen. Sie können die zugrunde liegenden Daten und Beziehungen anzeigen, aber die zugrunde liegenden Abfragen können Sie nicht im Abfrage-Editor anzeigen.


1. Wechseln Sie mithilfe des Tabellensymbols ![Tabellensymbol](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png) zur [Datenansicht](../connect-data/desktop-data-view.md).
 
    ![Desktop-Datenansicht](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    In der Datenansicht können Sie Daten im Power BI Desktop-Modell überprüfen, untersuchen und verstehen. Die Ansicht unterscheidet sich davon, wie Sie Tabellen, Spalten und Daten im Abfrage-Editor anzeigen. Die Daten in der Datenansicht sind bereits in das Modell geladen.

    Beim Modellieren der Daten möchten Sie möglicherweise sehen, welcher Inhalt in den Zeilen und Spalten einer Tabelle tatsächlich vorhanden ist, ohne im Berichtszeichenbereich ein Visual erstellen zu müssen. Dies gilt insbesondere dann, wenn Sie Measures und berechnete Spalten erstellen oder einen Datentyp/eine Datenkategorie identifizieren müssen.

1. Wechseln Sie zur [Beziehungsansicht](../transform-model/desktop-relationship-view.md), indem Sie das folgende Symbol auswählen: ![Symbol für Beziehungsansicht](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png).
 
    ![Beziehungsansicht in Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    Die Beziehungsansicht zeigt alle Tabellen, Spalten und Beziehungen in Ihrem Modell an. Hier können Sie Beziehungen anzeigen, ändern und erstellen.

## <a name="next-steps"></a>Nächste Schritte
In dieser Umgebung können Sie sicher experimentieren, da Sie die Änderungen nicht speichern müssen. Wenn Sie sie speichern, können Sie jederzeit wieder auf **Daten abrufen** klicken, um ein neues Exemplar dieses Beispiels herunterzuladen.

Wir hoffen, diese Tour hat Ihnen gezeigt, wie Power BI-Dashboards, -Datasets, -Beziehungen und -Berichte Ihnen Einblicke in Beispieldaten geben können. Jetzt liegt es an Ihnen – stellen Sie Verbindungen mit Ihren eigenen Daten her. Mit Power BI können Sie Verbindungen mit einer Vielzahl von Datenquellen herstellen. Wenn Sie tiefer in die Materie eindringen möchten, lesen Sie [Tutorial: Erste Schritte mit dem Power BI-Dienst](../fundamentals/service-get-started.md) und [Erste Schritte mit Power BI Desktop](../fundamentals/desktop-getting-started.md).  

Weitere Informationen finden Sie unter:  
- [Grundlegende Konzepte für Designer im Power BI-Dienst](../fundamentals/service-basic-concepts.md)
- [Welche Beispieldaten sind für die Verwendung mit Power BI verfügbar?](sample-datasets.md)
- [Datenquellen für Power BI](../connect-data/service-get-data.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
