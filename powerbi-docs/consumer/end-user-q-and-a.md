---
title: Q&A für Power BI-Verbraucher
description: Thema mit der Dokumentationsübersicht für Power BI Q&A zum Stellen von Fragen in natürlicher Sprache.
author: mihart
ms.reviewer: mohammad ali
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7739967443a8c6dc75cdaa3fbd0e472dcc090b9a
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488543"
---
# <a name="qa-for-power-bi-consumers"></a>Q&A für Power BI-Verbraucher

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

## <a name="what-is-qa"></a>Was ist Q&A?
Manchmal ist die schnellste Möglichkeit, um eine Antwort auf Basis Ihrer Daten zu erhalten, eine Frage in natürlicher Sprache zu stellen. Beispiel: „Wie lautet der Gesamtumsatz für das letzte Jahr“.

Verwenden Sie den Bereich für Fragen und Antworten (F&A), um Ihre Daten mithilfe intuitiver Möglichkeiten der natürlichen Sprache zu untersuchen und die entsprechenden Antworten in Form von Diagrammen und Grafiken zu erhalten. Der Bereich für Fragen und Antworten unterscheidet sich von einer Suchmaschine. Dieser Bereich stellt ausschließlich Ergebnisse zu den Daten in Power BI bereit.

## <a name="which-visualization-does-qa-use"></a>Welche Visualisierung verwendet Q&A?
Q&A wählt die beste Visualisierung basierend auf den angezeigten Daten aus. Gelegentlich werden Daten in den zugrunde liegenden Datasets als bestimmter Typ oder bestimmte Kategorie definiert. Dadurch weiß Q&A, wie sie angezeigt werden sollen. Wenn Daten z. B. als Datentyp definiert sind, müssen sie wahrscheinlich als Liniendiagramm angezeigt werden. Daten, die als eine Stadt kategorisiert werden, müssen wahrscheinlich als Karte angezeigt werden.

Sie können Q&A auch mitteilen, welches Visual verwendet werden soll, indem Sie Ihrer Frage diese Information hinzufügen. Bedenken Sie jedoch, dass Q&A Daten nicht immer im angeforderten Visualtyp anzeigen kann. Q&A fordert Sie mit einer Liste umsetzbarer Visualtypen zur Eingabe auf.

## <a name="where-can-i-use-qa"></a>Wo finde ich die Q&A-Funktion?
Die Q&A-Funktion ist im Power BI-Dienst in Dashboards enthalten, und in Power BI Mobile finden Sie sie ganz unten im Dashboard. Sie können mit Q&A Daten untersuchen, jedoch keine mit Q&A erstellten Visualisierungen speichern, es sei denn, der Designer hat Ihnen Bearbeitungsberechtigungen erteilt.

![Fragefeld](media/end-user-q-and-a/powerbi-qna.png)

Sie finden Q&A auch in Berichten, wenn der *Berichtdesigner* ein [Q&A-Visual](../visuals/power-bi-visualization-q-and-a.md) hinzugefügt hat.   

![Q&A-Visuals](media/end-user-q-and-a/power-bi-q-and-a-default.png)

## <a name="qa-on-dashboards"></a>Q&A für Dashboards

**Power BI Q&A** ist in Pro- und Premium-Lizenzen enthalten.  [Q&A in den Power BI Mobile-Apps](mobile/mobile-apps-ios-qna.md) sowie [Q&A mit Power BI Embedded](../developer/embedded/qanda.md) werden in eigenen Artikeln behandelt. Derzeit unterstützt **Power BI Q&A** nur die Beantwortung natürlichsprachlicher Anfragen in Englisch, obwohl es eine Vorschau für Spanisch gibt, die von Ihrem Power BI-Administrator aktiviert werden kann.


![Mit Q&A erstelltes Treemap-Diagramm](media/end-user-q-and-a/power-bi-treemap.png)

Fragen stellen ist erst der Anfang.  Viel Spaß bei Ihrer Reise, bei der Sie Daten optimieren oder eine Frage erweitern, vertrauenwürdige neue Informationen entdecken, sich die Details genauer ansehen und für eine breitere Übersicht den Fokus herausnehmen. Sie werden begeistert sein, welche Einblicke Sie gewinnen und Entdeckungen Sie machen werden.

Die Erfahrung ist wahrhaft interaktiv... und schnell! Unterstützt durch einen In-Memory-Speicher wird die Antwort nahezu unmittelbar zurückgegeben.


## <a name="use-qa-on-a-dashboard-in-the-power-bi-service"></a>Verwenden von Q&A in einem Dashboard im Power BI-Dienst
Im Power BI-Dienst (app.powerbi.com) enthält ein Dashboard angeheftete Kacheln aus einem oder mehrere Datasets, sodass Sie Fragen zu allen Daten in einem dieser Datasets stellen können. Um festzustellen, welche Berichte und Datasets zum Erstellen des Dashboards verwendet wurden, wählen Sie in der Dropdownliste **Weitere Aktionen** die Option **Verwandte Inhalte anzeigen** aus.

![Anzeigen verwandter Inhalte über die Menüleiste](media/end-user-q-and-a/power-bi-q-and-a-view-related.png)

## <a name="how-do-i-start"></a>Wie beginne ich?
Machen Sie sich zunächst mit dem Inhalt vertraut. Sehen Sie sich die Visuals auf dem Dashboard und im Bericht an. Verschaffen Sie sich ein Gefühl für den Typ und Bereich der Daten, die Ihnen zur Verfügung stehen. 

Beispiel:

* Wenn die Achsenbeschriftungen und -werte eines Visuals Begriffe wie „Umsätze“, „Konto“, „Monat“ und „Chancen“ enthalten, können Sie ganz einfach Fragen stellen wie z.B.: „Welches *Konto* hat die besten *Chancen*, oder *Umsätze* nach Monat als Balkendiagramm anzeigen“.

* Wenn Sie über Website-Leistungsdaten in Google Analytics verfügen, können Sie mit Q&A in Erfahrung bringen, wie viel Zeit auf einer Website verbracht wird, wie häufig einzelne Seiten aufgerufen werden und wie die Benutzerbindung aussieht. Wenn Sie demografische Daten benötigen, können Sie auch Alter und Haushaltseinkommen nach Ort erfragen.

Sobald Sie mit den Daten vertraut sind, navigieren Sie zurück zum Dashboard, und platzieren Sie Ihren Mauszeiger auf dem Fragefeld. Die Q&A-Anzeige wird geöffnet.

![Q&A-Anzeige](media/end-user-q-and-a/power-bi-suggested.png) 

Noch bevor Sie mit der Eingabe beginnen, zeigt Q&A einen neuen Bildschirm mit Vorschlägen für die Formulierung Ihrer Frage an. Es werden Ausdrücke und Fragen angezeigt, die die Namen von Tabellen in den zugrunde liegenden Datasets enthalten, und möglicherweise werden sogar *ausgewählte* Fragen aufgeführt, die der Besitzer des Datasets erstellt hat.

Sie können jede dieser Fragen auswählen, um sie dem Fragefeld hinzuzufügen und dann zu verfeinern, um eine bestimmte Antwort zu finden. 

![Q&A-Anzeige](media/end-user-q-and-a/power-bi-result.png) 

Darüber hinaus unterstützt Power BI Sie beim Stellen von Fragen mit folgenden Features: Eingabeaufforderungen, AutoVervollständigen und visuelle Hinweise. Power BI bietet diese Unterstützung für Q&A für Dashboards, Q&A in Berichten und mit dem Q&A-Visual. Diese Features werden weiter unten im Abschnitt [Erstellen eines Q&A-Visuals durch Eingabe einer Abfrage in natürlicher Sprache](#create-a-qa-visual-by-typing-a-natural-language-query) ausführlich erläutert.

<!-- ![video](../visuals/media/end-user-q-and-a/qna4.gif) -->


## <a name="the-qa-visual-in-power-bi-reports"></a>Das Q&A-Visual in Power BI-Berichten

Über das Q&A-Visual können Sie in natürlicher Sprache Fragen stellen und erhalten Antworten in Form eines visuellen Elements. Das Q&A-Visual unterstützt wie jedes andere visuelle Element in einem Bericht Kreuzfilterung, Kreuzhervorhebung, Lesezeichen und Kommentare. 

Sie erkennen ein Q&A-Visual anhand des Fragefelds im oberen Bereich. Hier geben Sie Fragen in natürlicher Sprache ein. Das Q&A-Visual kann beliebig oft verwendet werden, um Fragen zu Ihren Daten zu stellen. Wenn Sie den Bericht verlassen, wird das Q&A-Visual auf die zugehörigen Standardeinstellungen zurückgesetzt. 

![Screenshot eines standardmäßigen Q&A-Visuals](media/end-user-q-and-a/power-bi-q-and-a-default.png)


## <a name="use-qa"></a>Verwenden von Q&A 
Wählen Sie entweder eine der vorgeschlagenen Fragen aus oder geben eine eigene Frage in natürlicher Sprache ein, um Q&A für ein Dashboard oder das Q&A-Visual in einem Bericht zu verwenden. 

### <a name="create-a-qa-visual-by-using-a-suggested-question"></a>Erstellen eines Q&A-Visuals durch Verwendung einer vorgeschlagenen Frage

Hier wurde **top geo states by total units** (Wichtigste Staaten nach Gesamteinheiten) ausgewählt. Power BI wählt den am besten geeigneten Visualtyp aus. In diesem Fall ist dies eine Karte.

![Q&A-Visual mit Karte](media/end-user-q-and-a/power-bi-q-and-a-suggested.png)

Sie können Power BI aber auch mitteilen, welches Visual verwendet werden soll, indem Sie Ihrer Frage in natürlicher Sprache diese Information hinzufügen. Bedenken Sie jedoch, dass nicht jeder Visualtyp auch zu Ihren Daten passen muss. Mit diesen Daten könnten Sie beispielsweise kein sinnvolles Punktdiagramm erstellen. Ein Flächenkartogramm ist jedoch gut geeignet.

![Q&A-Visual mit Flächenkartogramm](media/end-user-q-and-a/power-bi-filled-map.png)

### <a name="create-a-qa-visual-by-typing-a-natural-language-query"></a>Erstellen eines Q&A-Visuals durch Eingabe einer Abfrage in natürlicher Sprache


Wenn Sie sich nicht sicher sind, welcher Fragetyp oder welche Terminologie verwendet werden sollte, erweitern Sie die Option **Alle Vorschläge anzeigen**. Alternativ können Sie sich auch die weiteren Visuals im Bericht ansehen. Auf diese Weise können Sie sich mit den Begriffen und Inhalten des Datasets vertraut machen.

1. Geben Sie Ihre Frage in natürlicher Sprache in das Q&A-Feld ein. Während Sie Ihre Frage eingeben, stellt Power BI automatische Vervollständigungen, visuelle Hinweise und Feedback bereit.

    **AutoVervollständigen**: Bei der Eingabe Ihrer Frage zeigt Power BI Q&A relevante und kontextuelle Vorschläge an, die Ihnen helfen, schnell mit natürlicher Sprache produktiv zu werden. Sie erhalten während der Eingabe sofort Feedback und Ergebnisse. Die Funktionalität ist vergleichbar mit der Eingabe in eine Suchmaschine.

    In diesem Beispiel ist der gewünschte Vorschlag der letzte. 

    ![Q&A mit einem blau unterstrichenen Wort](media/end-user-q-and-a/power-bi-autocomplete.png)

    **Rote/blaue Unterstreichungen**: Power BI Q&A zeigt Wörter mit Unterzeichnungen an, damit Sie sehen können, welche Wörter Power BI verstanden oder nicht erkannt hat. Eine durchgezogene blaue Unterstreichung zeigt an, dass Power BI das Wort erkannt hat. Das Beispiel unten zeigt, dass Q&A das Wort **store** verstanden hat.

    ![Q&A mit Vorschlägen aus der Dropdownliste zur Vervollständigung der Frage](media/end-user-q-and-a/power-bi-blue.png)

    Wählen Sie ein blau unterstrichenes Wort aus, um eine Dropdownliste mit vorgeschlagenen Fragen anzuzeigen. 

    ![Dropdownliste mit Vorschlägen zu „Sie können auf Folgendes versuchen“](media/end-user-q-and-a/power-bi-try.png)


    Bei der Eingabe eines Worts in Q&A wird dieses häufig rot unterstrichen. Eine rote Unterstreichung kann auf zwei potenzielle Probleme hinweisen. Der erste Problemtyp wird als „geringe Zuverlässigkeit“ kategorisiert. Wenn Sie ein ungenaues oder mehrdeutiges Wort eingeben, wird das Feld rot unterstrichen. Ein Beispiel hierfür ist das Wort „Speicherort“. Das Wort „Speicherort“ kann in verschiedenen Feldern enthalten sein, deshalb werden Sie vom System durch die rote Unterstreichung aufgefordert, das von Ihnen gemeinte Feld auszuwählen. In diesem Beispiel werden Sie von Power BI aufgefordert, das Feld auszuwählen, das Sie für „VanArsdel“ verwenden möchten.
    
    ![Rot unterstrichener Begriff im Q&A-Fragefeld](media/end-user-q-and-a/power-bi-q-and-a-red.png)
    
    Ein weiteres Beispiel für eine geringe Zuverlässigkeit läge vor, wenn Sie das Wort „Bereich“ eingeben, aber die Spalte das Wort „Bezirk“ enthält. Power BI Q&A erkennt dank Integration von Bing und Office Wörter mit gleicher Bedeutung. Q&A unterstreicht das betreffende Wort in Rot, damit Sie wissen, dass es sich nicht um eine direkte Übereinstimmung handelt.

    ![Q&A formuliert die Frage mit einem Synonym um](media/end-user-q-and-a/power-bi-red.png)

    Der zweite Problemtyp liegt vor, wenn Q&A das Wort überhaupt nicht erkennt. Ein Beispiel könnte die Verwendung des Worts „Geografie“ sein, obwohl es in den Daten nirgendwo enthalten ist. Das Wort ist in einem Wörterbuch enthalten, wird aber von Q&A mit einer roten Unterstreichung markiert. Power BI Q&A kann keine Visualisierung erstellen und schlägt Ihnen vor, dass Sie den Berichts-Designer bitten, den Begriff hinzuzufügen.

    ![Q&A mit dem Vorschlag, dass Sie den Designer bitten, das Wort „Geografie“ hinzuzufügen](media/end-user-q-and-a/power-bi-geography.png)

    **Vorschläge**: Wenn Sie mit der Eingabe der Frage fortfahren, erhalten Sie eine Rückmeldung von Power BI, falls die Frage nicht verstanden wird, und es werden weitere Vorschläge angezeigt. Im nachstehenden Beispiel schlägt Power BI unter „Meinten Sie...“ eine andere Möglichkeit der Formulierung vor, die die Terminologie des Datasets aufgreift. 

    ![Anzeige von vorgeschlagenen Korrekturen durch Q&A](media/end-user-q-and-a/power-bi-q-and-a-did-you-mean.png)

    Nachdem Sie einen Korrekturvorschlag von Power BI ausgewählt haben, werden Ihre Ergebnisse als Liniendiagramm angezeigt. 

    ![Q&A-Visualergebnisse als Liniendiagramm](media/end-user-q-and-a/power-bi-q-and-a-line.png)


    Sie können das Liniendiagramm aber auch in einen anderen Visualtyp ändern.  

    ![Q&A-Visual mit dem zur Frage hinzugefügten Zusatz „als Säulendiagramm“](media/end-user-q-and-a/power-bi-q-and-a-specify-type.png)



## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

**Frage**: Ich finde Q&A auf diesem Dashboard nicht.    
**Antwort 1**: Wenn Sie kein Fragefeld finden können, überprüfen Sie zunächst Ihre Einstellungen. Klicken Sie hierzu auf das Zahnradsymbol in der oberen rechten Ecke der Power BI-Symbolleiste.   
![Zahnradsymbol](media/end-user-q-and-a/power-bi-settings.png)

Klicken Sie dann auf **Einstellungen** > **Dashboards**. Stellen Sie sicher, dass die Option **Show the Q&A search box on this dashboard** (Q&A-Suchfeld auf diesem Dashboard anzeigen) aktiviert ist.    
![Q&A-Einstellungen für das Dashboard](media/end-user-q-and-a/power-bi-turn-on.png)  


**Antwort 2**: Es kann vorkommen, dass Sie keinen Zugriff auf die Einstellungen haben. Wenn Q&A durch den *Designer* des Dashboards oder Ihren Administrator deaktiviert wurde, können Sie sich erkundigen, ob eine erneute Aktivierung möglich ist.   

**Frage**: Ich erhalte nicht die Ergebnisse, die ich sehen möchte, wenn ich eine Frage eingebe.    
**Antwort**: Wählen Sie die Option zur Kontaktaufnahme mit dem Besitzer des Berichts oder des Dashboards aus. Die Kontaktaufnahme ist direkt über die Q&A-Dashboardseite oder das Q&A-Visual möglich. Alternativ können Sie den Besitzer über die Power BI-Kopfzeile ermitteln.  Es gibt viele Dinge, die der Designer tun kann, um die Q&A-Ergebnisse zu verbessern. Beispielsweise kann der Designer Spalten im Dataset umbenennen, um Begriffe zu verwenden, die einfacher zu verstehen sind (z.B. `CustomerFirstName` anstelle von `CustFN`). Da der Designer das Dataset sehr gut kennt, kann er hilfreiche Fragen formulieren und den von Q&A vorgeschlagenen Fragen hinzufügen.

![Anzeige von Kontaktinformationen](media/end-user-q-and-a/power-bi-q-and-a-contact.png)

## <a name="privacy"></a>Datenschutz

Microsoft verwendet Ihre Fragen möglicherweise, um Power BI zu verbessern. Weitere Informationen finden Sie in der [Microsoft-Datenschutzerklärung](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="next-steps"></a>Nächste Schritte
Informationen zum Erstellen eines Q&A-Visuals und dessen Verwaltung durch einen *Berichtdesigner* finden Sie unter [Q&A-Visualtyp](../visuals/power-bi-visualization-q-and-a.md).
