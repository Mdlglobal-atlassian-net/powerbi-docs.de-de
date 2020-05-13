---
title: 'Anheften einer gesamten Berichtsseite an ein Power BI-Dashboard '
description: Dokumentation zum Anheften einer gesamten Live-Berichtsseite aus einem Bericht an ein Power BI-Dashboard.
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: efcde5ab5f2b0a24409387cce0cb2e9300ae13af
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83340822"
---
# <a name="pin-an-entire-report-page-as-a-live-tile-to-a-power-bi-dashboard"></a>Heften Sie eine gesamte Berichtsseite als Live-Kachel an ein Power BI-Dashboard an
Eine weitere Möglichkeit, eine neue [Dashboardkachel](../consumer/end-user-tiles.md) hinzuzufügen, besteht im Anheften einer ganzen Berichtsseite. Dies ist eine einfache Möglichkeit, mehr als eine Visualisierung gleichzeitig anzuheften.  Wenn Sie eine gesamte Seite anheften, werden Ihre Kacheln zudem *live* geschaltet. Sie können dann damit direkt auf dem Dashboard interagieren. Änderungen, die Sie im Berichts-Editor an Visualisierungen vornehmen, z. B. Hinzufügen eines Filters oder Ändern der im Diagramm verwendeten Felder, werden von der Dashboardkachel übernommen.  

Das Anheften von Livekacheln aus Berichten an Dashboards ist nur im Power BI-Dienst (app.powerbi.com) möglich.

> [!NOTE]
> Sie können keine Kacheln aus Berichten anheften, die mit Ihnen geteilt wurden.
> 
> 

## <a name="pin-a-report-page"></a>Anheften einer Berichtsseite
Sehen Sie, wie eine Liveberichtsseite an ein Dashboard angeheftet wird, und befolgen Sie dann die Schritte unter dem Video, um es selbst zu probieren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/EzhfBpPboPA" frameborder="0" allowfullscreen></iframe>


1. Öffnen Sie einen Bericht in der [Bearbeitungsansicht](service-interact-with-a-report-in-editing-view.md).
2. Wählen Sie auf der Menüleiste **Live-Seite anheften** aus, ohne eine Visualisierung auszuwählen.
   
   ![Symbol „Live-Seite anheften“](media/service-dashboard-pin-live-tile-from-report/pbi-pin-live-page.png) 
3. Heften Sie die Kachel an ein vorhandenes oder neues Dashboard an. Beachten Sie den hervorgehobenen Text: *Durch das Anheften einer Live-Seite können Änderungen an Berichten in der Dashboardkachel angezeigt werden, sobald die Seite aktualisiert wird.*
   
   * Vorhandenes Dashboard: Wählen Sie den Namen des Dashboards aus der Dropdownliste aus. Dashboards, die für Sie freigegeben wurden, werden nicht in der Dropdownliste angezeigt.
   * Neues Dashboard: Geben Sie den Namen des neuen Dashboards ein.
     
     ![Dialogfeld „An das Dashboard anheften“](media/service-dashboard-pin-live-tile-from-report/pbi-pin-live-page-dialog.png)
4. Wählen Sie **Live anheften**aus. Eine Erfolgsmeldung (in der Nähe der oberen rechten Ecke) weist Sie darauf hin, dass die Seite Ihrem Dashboard als Kachel hinzugefügt wurde.

## <a name="open-the-dashboard-to-see-the-pinned-live-tile"></a>Öffnen Sie das Dashboard, um die angeheftete Livekachel anzuzeigen.
1. Wählen Sie im Navigationsbereich das Dashboard mit der neuen Live-Kachel aus. Hier können Sie die angeheftete Berichtsseite beispielsweise [umbenennen, verknüpfen, verschieben und in der Größe ändern](service-dashboard-edit-tile.md).  
2. Interagieren Sie mit der Live-Kachel.  Im nachstehenden Screenshot erfolgte durch Auswählen eines Balkens im Säulendiagramm eine Kreuzfilterung und Kreuzhervorhebung in den anderen Visualisierungen auf der Kachel.
   
    ![Dashboard mit einer Live-Kachel](media/service-dashboard-pin-live-tile-from-report/pbi-live-tile.png)

## <a name="next-steps"></a>Weitere Schritte
[Dashboards in Power BI](../consumer/end-user-dashboards.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
