---
title: Erstellen eines Power BI-Dashboards aus einem Bericht
description: Erstellen eines Power BI-Dashboards aus einem Bericht
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
ms.openlocfilehash: 4b75e0058c1624040ab037d5f64ac0275788576d
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349561"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Erstellen eines Power BI-Dashboards aus einem Bericht
Sie haben die [Einführung in Dashboards in Power BI](service-dashboards.md) gelesen und möchten jetzt Sie Ihr eigenes erstellen. Es gibt viele Methoden zum Erstellen eines Dashboards. So können Sie beispielsweise ein Dashboard anhand eines Berichts, von Grund auf neu, anhand eines Datasets oder durch Duplizieren eines vorhandenen Dashboards erstellen.  

Wir erstellen zunächst schnell ein einfaches Dashboard, indem wir Visualisierungen aus einem Bericht anheften, der bereits erstellt wurde. 

Nach Lektüre dieses Artikels sind Sie mit den folgenden Themen bestens vertraut:
- Beziehung zwischen Dashboards und Berichten
- Öffnen der Bearbeitungsansicht im Berichts-Editor
- Anheften von Kacheln 
- Navigieren zwischen einem Dashboard und einem Bericht 
 
![Dashboard](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

> [!NOTE] 
> Dashboards sind ein Feature des Power BI-Diensts und nicht von Power BI Desktop. Obwohl Sie in den mobilen Power BI-Apps keine Dashboards erstellen, können Sie sie darin [anzeigen und freigeben](../consumer/mobile/mobile-apps-view-dashboard.md).
>
> 

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Video: Erstellen eines Dashboards durch Anheften von Visualisierungen und Bildern aus einem Bericht
Amanda zeigt Ihnen, wie Sie ein neues Dashboard erstellen, indem Sie Visualisierungen aus einem Bericht anheften. Befolgen Sie dann die Schritte im nächsten Abschnitt unter [Importieren eines Datasets mit einem Bericht](#import-a-dataset-with-a-report), um die Vorgehensweise anhand des Beispiels für die Beschaffungsanalyse selbst auszuprobieren.
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importieren eines Datasets mit einem Bericht
Wir werden in dieser Anleitung eines der Power BI-Beispieldatasets importieren, um damit unser neues Dashboard zu erstellen. Das Beispiel ist eine Excel-Arbeitsmappe mit zwei PowerView-Arbeitsblättern. Wenn Sie die Arbeitsmappe in Power BI importieren, werden Ihrem Arbeitsbereich ein Dataset und ein Bericht hinzugefügt. Der Bericht wird automatisch aus den PowerView-Tabellen erstellt.

1. Laden Sie die Excel-Datei mit dem [Beispiel der Beschaffungsanalyse](https://go.microsoft.com/fwlink/?LinkId=529784) herunter. Wir empfehlen, die Datei in OneDrive for Business zu speichern.
2. Öffnen Sie den Power BI-Dienst in einem Browser (app.powerbi.com).
3. Wählen Sie im Navigationsbereich **Mein Arbeitsbereich** und anschließend **Daten abrufen** aus.

    ![Navigationsbereich](media/service-dashboard-create/power-bi-get-data-new-look.png)
5. Klicken Sie unter **Dateien** auf **Abrufen**.

   ![Dateien abrufen](media/service-dashboard-create/power-bi-select-files.png)
6. Navigieren Sie zum Speicherort der Excel-Datei des Beispiels für die Beschaffungsanalyse. Wählen Sie die Datei und dann **Verbinden** aus.

   ![Verbinden mit Dateien](media/service-dashboard-create/power-bi-connectnew.png)
7. Wählen Sie für diese Übung **Importieren** aus.

    ![Fenster „OneDrive for Business“](media/service-dashboard-create/power-bi-import.png)
8. Wenn die Erfolgsmeldung angezeigt wird, klicken Sie auf das **x**, um sie auszublenden.

   ![Erfolgsmeldung](media/service-dashboard-create/power-bi-view-datasetnew.png)

> [!TIP]
> Schon gewusst...? Sie können den Navigationsbereich eingrenzen, indem Sie oben auf das Symbol mit den drei Linien klicken ![Symbol „Navigationsbereich ein- oder ausblenden“](media/service-dashboard-create/power-bi-new-look-hide-nav-pane.png). Dadurch erhalten Sie mehr Platz für den Bericht selbst.

### <a name="open-the-report-and-pin-tiles-to-your-dashboard"></a>Öffnen des Berichts und Anheften von Kacheln an Ihr Dashboard
1. Wählen Sie im gleichen Arbeitsbereich die Registerkarte **Berichte** und dann **Analysebeispiel für Beschaffung** aus, um den Bericht zu öffnen.

    ![Registerkarte „Berichte“](media/service-dashboard-create/power-bi-reports.png) Der Bericht wird in der Leseansicht geöffnet. Beachten Sie, dass auf der linken Seite zwei Registerkarten vorhanden sind: **Rabattanalyse** und **Übersicht über die Ausgaben**. Jede Registerkarte stellt eine Seite des Berichts dar.

2. Wählen Sie **Weitere Optionen (...)**  > **Bericht bearbeiten** aus, um den Bericht in der Bearbeitungsansicht zu öffnen.

    ![Bericht in der Leseansicht](media/service-dashboard-create/power-bi-reading-view.png)
3. Zeigen Sie auf eine Visualisierung, um die verfügbaren Optionen anzuzeigen. Um einem Dashboard eine Visualisierung hinzuzufügen, wählen Sie das Stecknadelsymbol ![Stecknadelsymbol](media/service-dashboard-create/power-bi-pin-icon.png).

    ![Zeigen auf die Kachel](media/service-dashboard-create/power-bi-hover.png)
4. Da wir ein neues Dashboard erstellen, wählen Sie die Option **Neues Dashboard** aus und geben ihm einen Namen.

    ![Dialogfeld „An das Dashboard anheften“](media/service-dashboard-create/power-bi-pin-tile.png)
5. Wenn Sie **Anheften** auswählen, erstellt Power BI das neue Dashboard im aktuellen Arbeitsbereich. Wenn die Meldung **An das Dashboard angeheftet** angezeigt wird, wählen Sie **Zum Dashboard wechseln** aus. Wenn Sie aufgefordert werden, den Bericht zu speichern, wählen Sie **Speichern** aus.

    ![Erfolgsmeldung](media/service-dashboard-create/power-bi-pin-success.png)

    Power BI öffnet das neue Dashboard. Es enthält eine Kachel: die soeben angeheftete Visualisierung.

   ![Dashboard mit einer Kachel](media/service-dashboard-create/power-bi-pinned.png)
7. Klicken Sie auf die Kachel, um zum Bericht zurückzukehren. Heften Sie einige weitere Kacheln an das neue Dashboard an. Wenn das Fenster **An das Dashboard anheften** angezeigt wird, wählen Sie **Vorhandenes Dashboard** aus.  

   ![Dialogfeld „An das Dashboard anheften“](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>Anheften einer vollständigen Berichtsseite an das Dashboard
Anstatt einzelne Visuals anzuheften, können Sie [eine vollständige Berichtsseite als *Live-Kachel* anheften](service-dashboard-pin-live-tile-from-report.md). Los geht‘s.

1. Wählen Sie im Berichts-Editor die Registerkarte **Ausgabenübersicht** aus, um die zweite Seite des Berichts zu öffnen.

   ![Registerkarte „Bericht“](media/service-dashboard-create/power-bi-page-tab.png)

2. Wir möchten auf Ihrem Dashboard alle visuellen Elemente im Bericht anzeigen. Wählen Sie in der oberen rechten Ecke der Menüleiste die Option **Live-Seite anheften**. Kacheln für Live-Seiten werden auf einem Dashboard jedes Mal aktualisiert, wenn die Seite aktualisiert wird.

   ![Oben rechts im Berichts-Editor](media/service-dashboard-create/power-bi-pin-live.png)

3. Wenn das Fenster **An das Dashboard anheften** angezeigt wird, wählen Sie **Vorhandenes Dashboard** aus.

   ![Dialogfeld „An das Dashboard anheften“](media/service-dashboard-create/power-bi-pin-live2.png)

4. Wenn die Erfolgsmeldung angezeigt wird, wählen Sie **Zum Dashboard wechseln** aus. Dort sehen Sie die Kacheln, die Sie aus dem Bericht angeheftet haben. Im unten gezeigten Beispiel haben wir zwei Kacheln von Seite 1 des Berichts sowie eine Live-Kachel angeheftet, die Seite 2 des Berichts darstellt.

   ![Dashboard](media/service-dashboard-create/power-bi-dashboard.png)

## <a name="next-steps"></a>Nächste Schritte
Glückwunsch, Sie haben Ihr erstes Dashboard erstellt! Da Sie jetzt über ein Dashboard verfügen, stehen Ihnen alle Möglichkeiten offen, die ein Dashboard bietet. Folgen Sie einem der unten angegebenen Artikel, oder beginnen Sie selbständig mit der Erkundung: 

* [Ändern der Größe und Position von Kacheln](service-dashboard-edit-tile.md)
* [Alle wichtigen Informationen über Dashboardkacheln](service-dashboard-tiles.md)
* [Freigeben des Dashboards durch Erstellen einer App](../collaborate-share/service-create-workspaces.md)
* [Power BI – Grundkonzepte](../fundamentals/service-basic-concepts.md)
* [Tipps zum Gestalten überzeugender Power BI-Dashboards](service-dashboards-design-tips.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/).
