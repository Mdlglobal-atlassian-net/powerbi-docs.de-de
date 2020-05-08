---
title: Hinzufügen von Kommentaren zu Dashboards und Berichten
description: In diesem Dokument wird erläutert, wie Kommentare einem Dashboard, Bericht oder Visual hinzugefügt und dazu verwendet werden, Unterhaltungen mit Projektmitarbeitern zu führen.
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: 59ba4d0e62613ed25569efd0602815e3d98aec4d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77496493"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>Hinzufügen von Kommentaren zu einem Dashboard oder Bericht

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Sie können einem Dashboard oder Bericht einen persönlichen Kommentar hinzufügen oder über ein Dashboard oder einen Bericht eine Unterhaltung mit Ihren Kollegen beginnen. Das Feature **Kommentare** ist nur eine der Möglichkeiten, wie ein *Endbenutzer* mit anderen Personen interagieren kann. 

![Video zu Kommentaren](media/end-user-comment/comment.gif)

> [!NOTE]
> Für die Zusammenarbeit mit anderen Benutzern, beispielsweise für das Hinzufügen von Kommentaren zu freigegebenen Berichten, ist eine Power BI Pro- oder Power BI Premium-Lizenz erforderlich. [Welchen Lizenztyp habe ich?](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>Verwenden des Features „Kommentare“
Kommentare können einem gesamten Dashboard, einzelnen Visuals auf einem Dashboard, einer Berichtseite, einem paginierten Bericht und einzelnen Visuals auf einer Berichtseite hinzugefügt werden. Sie können einen allgemeinen Kommentar oder einen Kommentar hinzufügen, der sich an bestimmte Kollegen richtet.  

Wenn Sie einem Bericht einen Kommentar hinzufügen, erfasst Power BI die aktuellen Filter- und Slicerwerte. Das bedeutet, dass sich beim Auswählen oder Beantworten eines Kommentars die Berichtsseite oder das Berichtsvisual ändern kann, um Ihnen die Filter- und Slicerwerte anzuzeigen, die beim ersten Hinzufügen des Kommentars aktiv waren.  

![Video über Bericht mit Filtern](media/end-user-comment/power-bi-comment.gif)

Warum ist dies wichtig? Nehmen wir an, eine Kollegin hat einen Filter angewendet, der einen interessanten Einblick gewährt, den sie mit dem Team teilen möchte. Ohne dass dieser Filter ausgewählt ist, ergibt der Kommentar möglicherweise keinen Sinn.

Wenn Sie einen paginierten Bericht verwenden, können Sie nur einen allgemeinen Kommentar zu Ihrem Bericht hinterlassen.  Das Hinterlassen von Kommentaren in einzelnen paginierten Berichtsvisuals wird nicht unterstützt.

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>Hinzufügen eines allgemeinen Kommentars zu einem Dashboard oder Bericht
Die Vorgehensweise zum Hinzufügen von Kommentaren zu einem Dashboard oder Bericht ist ähnlich.  In diesem Beispiel wird ein Dashboard verwendet. 

1. Öffnen Sie ein Power BI-Dashboard oder einen Power BI-Bericht, und klicken Sie auf das Symbol **Kommentare**. Daraufhin wird das Dialogfeld „Kommentare“ geöffnet.

    ![Symbol „Kommentare“](media/end-user-comment/power-bi-comment-menu.png)

    Auf der folgenden Abbildung hat der Ersteller des Dashboards bereits einen allgemeinen Kommentar hinzugefügt.  Jedem Benutzer mit Zugriff auf dieses Dashboard wird dieser Kommentar angezeigt.

    ![Symbol „Kommentare“](media/end-user-comment/power-bi-first-comments.png)

2. Klicken Sie zum Beantworten auf **Antworten**, geben Sie Ihre Antwort ein, und klicken Sie anschließend auf **Post** (Posten).  

    ![Symbol zum Beantworten von Kommentaren](media/end-user-comment/power-bi-comment-reply.png)

    Standardmäßig leitet Power BI Ihre Antwort an den Kollegen weiter, der den Kommentarthread gestartet hat, in diesem Fall Aaron. 

    ![Kommentar mit Antwort](media/end-user-comment/power-bi-respond.png)

 3. Wenn Sie einen Kommentar nicht zu einem vorhandenen Thread hinzufügen möchten, geben Sie Ihren Kommentar in das obere Textfeld ein.

    ![Symbol zum Beantworten von Kommentaren](media/end-user-comment/power-bi-new-comments.png)

    Die Kommentare für dieses Dashboard werden jetzt wie folgt dargestellt:

    ![Unterhaltungen in „Kommentare“](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>Hinzufügen eines Kommentars zu einem bestimmten Dashboard- oder Berichtsvisual
Sie können Kommentare nicht nur zu einem vollständigen Dashboard oder zu einer gesamten Berichtsseite, sondern auch zu einzelnen Dashboardkacheln und einzelnen Berichtsvisuals hinzufügen. Die Vorgehensweisen sind sehr ähnlich, und in diesem Beispiel wird ein Bericht verwendet.

1. Zeigen Sie auf das Visual, und klicken Sie auf **Weitere Optionen** (...).    
2. Wählen Sie in der Dropdownliste **Kommentare öffnen** aus.

    ![Erste Auswahl: Kommentar hinzufügen](media/end-user-comment/power-bi-report-comment.png)  

3.  Das Dialogfeld **Kommentare** wird geöffnet, und die anderen Visuals auf der Seite sind abgeblendet. Zu diesem Visual gibt es noch keine Kommentare. 

    ![Hinzufügen eines Kommentars an sich selbst](media/end-user-comment/power-bi-comment-column.png)  

4. Geben Sie Ihren Kommentar ein, und klicken Sie auf **Post** (Posten).

    ![Hinzufügen eines Kommentars an sich selbst](media/end-user-comment/power-bi-comment-logistics.png)  

    - Wird auf einer Berichtsseite ein Kommentar ausgewählt, der in einem Visual erstellt wurde, wird dieses Visual hervorgehoben (siehe oben).

    - Auf einem Dashboard gibt das Diagrammsymbol ![Kommentar mit Diagrammsymbol](media/end-user-comment/power-bi-comment-chart-icon.png) an, dass ein Kommentar an ein bestimmtes Visual gebunden ist. Kommentare, die für das gesamte Dashboard gelten, haben kein spezielles Symbol. Wird das Diagrammsymbol ausgewählt, wird das zugehörige Visual auf dem Dashboard hervorgehoben.
    

    ![Hervorhebung des zugehörigen Visuals](media/end-user-comment/power-bi-highlight.png)

5. Klicken Sie auf **Schließen**, um zum Dashboard oder zum Bericht zurückzukehren.

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>Kollegen mit dem @-Zeichen auf Kommentare aufmerksam machen
Egal, ob Sie einen Kommentar für ein Dashboard, einen Bericht, eine Kachel oder ein Visual erstellen, können Sie durch Verwenden des \@-Zeichens die Aufmerksamkeit Ihrer Kollegen erlangen.  Wenn Sie das \@-Zeichen eingeben, wird in Power BI eine Dropdownliste geöffnet, in der Sie nach Personen in Ihrer Organisation suchen und diese auswählen können. Überprüfte Namen, denen ein \@-Zeichen vorangestellt wurde, werden in blauer Schrift dargestellt. 

Hier ist eine Konversation mit dem *Designer* der Visualisierung zu sehen. Er verwendet das @-Zeichen, um sicherzustellen, dass ich den Kommentar sehe. Ich weiß, dass dieser Kommentar für mich ist. Wenn ich dieses App-Dashboard in Power BI öffne, wähle ich in der Kopfzeile **Kommentare** aus. Im Bereich **Kommentare** wird unsere Konversation angezeigt.

![Hinzufügen eines Kommentars mit Erwähnung](media/end-user-comment/power-bi-comment-convo.png)  



## <a name="next-steps"></a>Nächste Schritte
Zurück zu [Visualisierungen für Consumer](end-user-visualizations.md)    
<!--[Select a visualization to open a report](end-user-open-report.md)-->
