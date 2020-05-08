---
title: Verwenden von Power BI Q&A zur Untersuchung und Erstellung von Visuals
description: Hier erfahren Sie, wie Sie Power BI Q&A verwenden, um neue Visualisierungen in Dashboards und Berichten zu erstellen.
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 71a727d1d7e39661ed86a4fdf574e3f1fa8fb595
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488865"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Verwenden von Power BI Q&A zur Untersuchung Ihrer Daten und Erstellung von Visuals

Manchmal ist die schnellste Möglichkeit, um eine Antwort auf Basis Ihrer Daten zu erhalten, eine Frage in natürlicher Sprache zu stellen. Mit dem Q&A-Feature in Power BI können Sie Ihre Daten in Ihren eigenen Worten untersuchen.  Der erste Teil dieses Artikels zeigt, wie Sie Q&A in Dashboards im Power BI-Dienst einsetzen. Der zweite Teil zeigt, was Sie mit Q&A bei der Erstellung von Berichten entweder im Power BI-Dienst oder in Power BI Desktop machen können. Weitere Informationen finden Sie im Artikel [Q&A für Power BI-Nutzer](consumer/end-user-q-and-a.md). 

[Q&A in den Power BI Mobile-Apps](consumer/mobile/mobile-apps-ios-qna.md) sowie [Q&A mit Power BI Embedded](developer/embedded/qanda.md) werden in eigenen Artikeln behandelt. 

Q&A ist interaktiv und sogar unterhaltsam. Häufig führt eine Frage zur nächsten, weil die Visualisierungen interessante Aspekte für eine Weiterverfolgung aufwerfen. Sehen Sie sich an, wie Amanda mithilfe von Q&A Visualisierungen erstellt, diese Visuals erläutert und sie an Dashboards anheftet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Teil 1: Verwenden von Q&A in einem Dashboard im Power BI-Dienst

Im Power BI-Dienst (app.powerbi.com) enthält ein Dashboard angeheftete Kacheln aus einem oder mehrere Datasets, sodass Sie Fragen zu allen Daten in einem dieser Datasets stellen können. Um festzustellen, welche Berichte und Datasets zum Erstellen des Dashboards verwendet wurden, wählen Sie auf der Menüleiste **Verwandte Inhalte anzeigen** aus.

![Anzeigen von verwandten Berichten und Datasets](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Das Q&A-Fragefeld befindet sich in der linken oberen Ecke des Dashboards, wo Sie Ihre Frage in natürlicher Sprache eingeben. Wird kein Q&A-Fragefeld angezeigt? Weitere Informationen hierzu finden Sie unter [Zu beachtende Aspekte und Problembehandlung](consumer/end-user-q-and-a.md#considerations-and-troubleshooting) im Artikel **Q&A für Power BI-Verbraucher**.  Q&A erkennt die Wörter, die Sie eingeben und prüft, wo (in welchem Dataset) die Antwort zu finden ist. Q&A unterstützt Sie mit automatischer Vervollständigung, Neuformulierung und anderen textlichen und visuellen Hilfsmitteln bei der Formulierung Ihrer Frage.

![Fragenfeld für Q&A](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

Die Antwort auf Ihre Frage wird als eine interaktive Visualisierung angezeigt und beim Ändern der Frage aktualisiert.

1. Öffnen Sie ein Dashboard, und platzieren Sie den Cursor im Fragefeld. Wählen Sie in der oberen rechten Ecke **New Q&A experience** (Neue Q&A-Oberfläche) aus.

    ![Neue Q&A-Oberfläche in Power BI](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Noch bevor Sie mit der Eingabe beginnen, zeigt Q&A einen neuen Bildschirm mit Vorschlägen für die Formulierung Ihrer Frage an. Sie sehen Phrasen und vollständige Fragen, die die Namen der Tabellen in den zugrunde liegenden Datensätzen enthalten, und können sogar vollständige Fragen aufgelistet sehen, wenn der Eigentümer des Datasets [ausgewählte Fragen](service-q-and-a-create-featured-questions.md) erstellt hat.

   ![Vorgeschlagene Fragen in Q&A](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Sie können eine dieser Fragen als Ausgangspunkt verwenden und die Frage verfeinern, um die genaue Antwort darauf zu erhalten. Alternativ können Sie einen Tabellennamen zum Formulieren einer neuen Frage verwenden.

2. Wählen Sie aus der Liste mit Fragen aus, oder beginnen Sie mit der Eingabe einer eigenen Frage, und wählen Sie Vorschläge aus der Dropdownliste aus.

   ![Auswählen einer Frage aus der Liste](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. Wenn Sie eine Frage eingeben, wählt Q&A die beste Visualisierung aus, um Ihre Antwort anzuzeigen.

   ![Q&A how many stores by state](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. Die Visualisierung ändert sich dynamisch, wenn Sie die Frage ändern.

   ![Q&A how many stores by state as bar chart](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Wenn Sie eine Frage eingeben, sucht Power BI nach der besten Antwort, unter Verwendung jedes Datasets, das über eine Kachel auf diesem Dashboard verfügt.  Wenn alle Kacheln von *DatasetA* stammen, ergibt sich Ihre Antwort ebenfalls aus *DatasetA*.  Wenn Kacheln aus *datasetA* und *datasetB* verfügbar sind, sucht Q&A in beiden Datasets nach der optimalen Antwort.

   > [!TIP]
   > Gehen Sie umsichtig vor. Wenn es für *datasetA* nur eine Kachel gibt und Sie diese aus dem Dashboard entfernen, hat Q&A keinen Zugriff mehr auf *datasetA*.
   >

5. Wenn Sie mit dem Ergebnis zufrieden sind, heften Sie die Visualisierung an ein Dashboard an, indem Sie das Anheftsymbol in der oberen rechten Ecke auswählen. Wenn das Dashboard für Sie freigegeben wurde oder Bestandteil einer App ist, können Sie die Visualisierung nicht anheften.

   ![Q&A Anheften des Visuals](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Teil 2: Verwenden von Q&A in einem Bericht im Power BI-Dienst oder in Power BI Desktop

Verwenden Sie Q&A, um das Dataset zu untersuchen und dem Bericht sowie Dashboards Visualisierungen hinzuzufügen. Ein Bericht basiert auf einem einzelnen Dataset. Er kann vollständig leer sein oder mit Visualisierungen gefüllte Seiten enthalten. Wenn ein Bericht leer ist, bedeutet dies jedoch nicht unbedingt, dass er keine Daten enthält, die Sie untersuchen können. Das Dataset ist mit dem Bericht verknüpft, und Sie können es untersuchen und Visualisierungen erstellen.  Um festzustellen, welches Dataset zum Erstellen eines Berichts verwendet wird, öffnen Sie den Bericht in der Leseansicht des Power BI-Diensts, und wählen Sie auf der Menüleiste **Verwandte Inhalte anzeigen** aus.

![Zugehörige Datasets anzeigen](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Sie benötigen Bearbeitungsberechtigungen für den Bericht und das zugrunde liegende Dataset, um Q&A in Berichten verwenden zu können. Im Artikel [Q&A für Power BI-Nutzer](consumer/end-user-q-and-a.md) wird dies als *Erstellerszenario* bezeichnet. Wenn Sie stattdessen einen Bericht *nutzen*, der mit Ihnen geteilt wurde, ist Q&A nicht verfügbar.

1. Öffnen Sie einen Bericht in der Bearbeitungsansicht (Power BI-Dienst) oder Berichtsansicht (Power BI Desktop), und wählen Sie auf der Menüleiste **Frage stellen** aus.

    **Power BI Desktop**    
    ![Auswählen von Q&A in Power BI Desktop](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Power BI-Dienst**    
    ![Auswählen von Q&A im Power BI-Dienst](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Das Q&A-Fragefeld wird im Zeichenbereich des Berichts angezeigt. Im folgenden Beispiel wird das Fragefeld auf einer anderen Visualisierung angezeigt. Dies ist in Ordnung, jedoch ist es möglicherweise besser, dem Bericht eine leere Seite hinzuzufügen, bevor Sie eine Frage stellen.

    ![Fragenfeld für Q&A](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Platzieren Sie den Cursor im Fragefeld. Während Sie Text eingeben, werden in Q&A Vorschläge angezeigt, die Sie bei der Formulierung der Frage unterstützen.

   ![Tippen Sie in das Q&A-Fragefeld.](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. Wenn Sie eine Frage eingeben, wählt Q&A die optimale [Visualisierung](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md), um Ihre Antwort anzuzeigen. Wenn Sie die Frage ändern, wird die Visualisierung dynamisch angepasst.

   ![Q&A erstellt eine Visualisierung.](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Sobald die gewünschte Visualisierung angezeigt wird, drücken Sie die EINGABETASTE. Wählen Sie zum Speichern der Visualisierung mit dem Bericht **Datei > Speichern** aus.

6. Interagieren Sie mit der neuen Visualisierung. Es spielt keine Rolle, wie Sie die Visualisierung erstellt haben – es sind immer die gleichen Interaktivitätsfunktionen, Formatierungen und Features verfügbar.

   ![Interagieren Sie mit der Visualisierung.](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Wenn Sie die Visualisierung im Power BI-Dienst erstellt haben, können Sie sie sogar [an ein Dashboard anheften](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Angeben der verwendeten Visualisierung für Q&A
Mit Q&A lassen Sie nicht nur Ihre Daten für sich selbst sprechen, Sie können sogar festlegen, wie die Antwort in Power BI angezeigt werden soll. Hängen Sie am Ende Ihrer Frage einfach den Zusatz „als <visualization type>“ an.  Beispiel: „Bestandsvolumen nach Werk als Karte anzeigen“ und „Gesamtvolumen als Karte anzeigen“.  Probieren Sie es einfach aus.

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
- Wenn Sie mit einer Liveverbindung oder über ein Gateway die Verbindung mit einem Dataset hergestellt haben, muss Q&A [für dieses Dataset aktiviert](service-q-and-a-direct-query.md) sein.

- Sie haben einen Bericht geöffnet, und die Q&A-Option wird nicht angezeigt. Wenn Sie den Power BI-Dienst verwenden, stellen Sie sicher, dass der Bericht in der Bearbeitungsansicht geöffnet ist. Wenn Sie die Bearbeitungsansicht nicht öffnen können, haben Sie keine Bearbeitungsberechtigungen für den Bericht und können Q&A für diesen bestimmten Bericht verwenden.

## <a name="next-steps"></a>Nächste Schritte

- [Q&A für Nutzer](consumer/end-user-q-and-a.md)   
- [Tipps zum Stellen von Fragen mit Q&A](consumer/end-user-q-and-a-tips.md)   
- [Vorbereiten einer Arbeitsmappe für Q&A](service-prepare-data-for-q-and-a.md)  
- [Vorbereiten eines lokalen Datasets für Q&A](service-q-and-a-direct-query.md)   
- [Anheften einer Kachel an das Dashboard aus Q&A](service-dashboard-pin-tile-from-q-and-a.md)
