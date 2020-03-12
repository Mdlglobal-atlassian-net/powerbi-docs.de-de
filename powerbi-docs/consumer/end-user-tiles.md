---
title: Dashboardkacheln im Power BI-Dienst für Verbraucher
description: Alle wichtigen Informationen über Dashboardkacheln in Power BI für Verbraucher. Dies schließt Kacheln ein, die über SQL Server Reporting Services (SSRS) erstellt wurden.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 0481a09aaeac4f6c76c49d3a816ac880cdb9d60b
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114054"
---
# <a name="dashboard-tiles-in-power-bi"></a>Dashboardkacheln in Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Eine Kachel ist eine Momentaufnahme Ihrer Daten, die von einem *Designer* an das Dashboard geheftet wurde. *Designer* können Kacheln aus einem Bericht, einem Dataset, einem Dashboard, dem Q&A-Fragefeld, Excel, SSRS (SQL Server Reporting Services) und noch mehr erstellen.  Der Screenshot zeigt viele verschiedene Kacheln, die an ein Dashboard angeheftet sind.

![Power BI-Dashboard](./media/end-user-tiles/power-bi-dash.png)


Neben den Kacheln, die an das Dashboard geheftet werden, können *Designer* eigenständige Kacheln mit **Kachel hinzufügen** direkt zum Dashboard hinzufügen. Eigenständige Kacheln können Textfelder, Bilder, Videos, Streamingdaten und Webinhalte enthalten.

Benötigen Sie Hilfe, um die Grundkomponenten zu verstehen, aus denen Power BI besteht?  Weitere Informationen finden Sie unter [Power BI – Grundkonzepte](end-user-basic-concepts.md).


## <a name="interacting-with-tiles-on-a-dashboard"></a>Interagieren mit Kacheln in einem Dashboard

1. Zeigen Sie auf die Kachel, um die Auslassungspunkte anzuzeigen.
   
    ![Kachel „Auslassungspunkte“](./media/end-user-tiles/ellipses_new.png)
2. Wählen Sie die Auslassungspunkte (...) aus, um das Aktionsmenü zu öffnen. Die verfügbaren Optionen variieren je nach Typ des Visuals und Methode, die zum Erstellen der Kachel verwendet wurde. Im folgenden werden einige Beispiele aufgeführt, die Ihnen möglicherweise angezeigt werden.

    - Kachel, die mit Q&A erstellt wurde
   
        ![Symbol „Auslassungspunkte“](./media/end-user-tiles/power-bi-options-1.png)

    - Kachel, die aus einer Arbeitsmappe erstellt wurde
   
        ![Symbol „Auslassungspunkte“](./media/end-user-tiles/power-bi-options-2.png)

    - Kachel, die aus einem Bericht erstellt wurde
   
        ![Symbol „Auslassungspunkte“](./media/end-user-tiles/power-bi-options-3.png)
   
    Hier können Sie Folgendes tun:
   
   * [Den Bericht öffnen, mit dem diese Kachel erstellt wurde ](end-user-reports.md) ![Symbol „Bericht“](./media/end-user-tiles/chart-icon.jpg)  
   
   * [Die Q&A-Frage öffnen, mit der die Kachel erstellt wurde](end-user-reports.md) ![Q&A-Symbol](./media/end-user-tiles/qna-icon.png)  
   

   * [Die Arbeitsmappe öffnen, mit der diese Kachel erstellt wurde](end-user-reports.md) ![Arbeitsmappensymbol](./media/end-user-tiles/power-bi-open-worksheet.png)  
   * [Die Kachel im Fokusmodus anzeigen](end-user-focus.md) ![Fokussymbol](./media/end-user-tiles/fullscreen-icon.jpg)  
   * [Erkenntnisse anzeigen](end-user-insights.md) ![Symbol „Erkenntnisse“](./media/end-user-tiles/power-bi-insights.png)
   * [Einen Kommentar hinzufügen und eine Diskussion starten](end-user-comment.md) ![Kommentarsymbol](./media/end-user-tiles/comment-icons.png)
   * [Warnungen für eine Dashboardkachel verwalten](end-user-alerts.md) ![Warnsymbol](./media/end-user-tiles/power-bi-alert-icon.png)
   * [Die Daten in Excel öffnen](end-user-export.md) ![Exportsymbol](./media/end-user-tiles/power-bi-export-icon.png)


3. Wählen Sie zum Schließen des Aktionsmenüs eine leere Fläche im Zeichenbereich aus.

### <a name="select-click-a-tile"></a>Auswählen einer Kachel
Wenn Sie eine Kachel auswählen, hängt das anschließenden Vorgehen davon ab, wie die Kachel erstellt wurde und ob sie über einen [benutzerdefinierten Link](../service-dashboard-edit-tile.md) verfügt. Wenn sie einen benutzerdefinierten Link aufweist, bringt Sie das Auswählen der Kachel zum Ziel dieses Links. Andernfalls gelangen Sie nach Auswählen der Kachel zu dem Bericht, der Excel Online-Arbeitsmappe, dem lokalen SSRS-Bericht oder der Q&A-Frage, der/die zum Erstellen der Kachel verwendet wurde.

> [!NOTE]
> Eine Ausnahme sind Videokacheln, die mit **Kachel hinzufügen** direkt auf dem Dashboard erstellt wurden. Bei Auswählen einer Videokachel (die auf diese Weise erstellt wurde) wird das Video direkt auf dem Dashboard wiedergegeben.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
* Wenn der Bericht, der zum Erstellen der Visualisierung verwendet wurde, nicht gespeichert wurde, löst das Auswählen der Kachel keine Aktion aus.
* Wenn die Kachel anhand einer Arbeitsmappe in Excel Online erstellt wurde und Sie nicht mindestens Leseberechtigungen für diese Arbeitsmappe haben, wird durch Auswählen der Kachel die Arbeitsmappe nicht in Excel Online geöffnet.
* Wenn für Kacheln, die mit **Kacheln hinzufügen** direkt auf dem Dashboard erstellt wurden, ein benutzerdefinierter Link festgelegt wurde, wird die betreffende URL durch Auswählen des Titels, des Untertitels oder der Kachel geöffnet.  Standardmäßig erfolgt bei Auswahl einer dieser Kacheln direkt auf dem Dashboard für ein Bild, einen Webcode oder ein Textfeld keine Aktion.
* Wenn Sie über keine Berechtigungen zum Bericht in SSRS verfügen, führt die Auswahl einer über SSRS erstellten Kachel zur Anzeige einer Fehlerseite. Auf dieser werden Sie darauf hingewiesen, dass Sie keinen Zugriff haben (rsAccessDenied).
* Wenn Sie keinen Zugriff auf das Netzwerk mit SSRS haben, führt die Auswahl einer über SSRS erstellten Kachel zur Anzeige einer Fehlerseite. Auf dieser werden Sie darauf hingewiesen, dass der Server nicht gefunden wurde (HTTP 404). Ihr Gerät muss Netzwerkzugriff auf den Berichtsserver besitzen, um den Bericht anzeigen zu können.
* Wenn sich die ursprüngliche Visualisierung ändert, die zum Erstellen der Kachel verwendet wurde, ändert sich die Kachel nicht.  Wenn der *Designer* beispielsweise ein Liniendiagramm aus einem Bericht angeheftet und dann das Liniendiagramm in ein Balkendiagramm geändert hat, wird auf der Dashboardkachel weiterhin ein Liniendiagramm angezeigt. Die Daten werden aktualisiert, der Visualisierungstyp hingegen nicht.

## <a name="next-steps"></a>Nächste Schritte
[Datenaktualisierung](../refresh-data.md)

[Power BI – Grundkonzepte](end-user-basic-concepts.md)
