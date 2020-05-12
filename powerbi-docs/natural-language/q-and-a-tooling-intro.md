---
title: Einführung in Q&A-Tools zum Trainieren von Power BI Q&A (Vorschau)
description: Einführung in Power BI Q&A-Tools
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
ms.openlocfilehash: 6178c9f157578110a09abf3fcbebccba54339f13
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866051"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Einführung in Q&A-Tools zum Trainieren von Power BI Q&A (Vorschau)

Mithilfe von Power BI Q&A-*Tools* können Sie die Funktionen für natürliche Sprache für Ihre Benutzer verbessern. Als Designer oder Administrator interagieren Sie mit der Engine für natürliche Sprache und nehmen Verbesserungen in drei Bereichen vor: 

- Überprüfen von Fragen, die Benutzer stellen
- Trainieren der Q&A-Engine im Hinblick auf das Verstehen von Fragen
- Verwalten von Begriffen, die Sie der Q&A-Engine beigebracht haben

Zusätzlich zu diesen dedizierten Toolfunktionen finden Sie auf der Registerkarte **Modellierung** in Power BI Desktop weitere Optionen:  

- Synonyme
- Zeilenbeschriftungen
- Für Q&A ausblenden
- Konfigurieren des linguistischen Schemas (erweitert)

## <a name="get-started-with-qa-tooling"></a>Erste Schritte mit Q&A-Tools

Q&A-Tools sind nur in Power BI Desktop verfügbar und unterstützen derzeit ausschließlich den Importmodus.

1. Öffnen Sie Power BI Desktop, und verwenden Sie Q&A, um ein Visual zu erstellen. 
2. Klicken Sie am Rand des Visuals auf das Zahnradsymbol. 

    ![Q&A-Visual: Zahnradsymbol](media/q-and-a-tooling-intro/qna-visual-gear.png)

    Dann wird die Seite „Erste Schritte“ geöffnet.  

    ![Q&A: „Erste Schritte“](media/q-and-a-tooling-intro/qna-tooling-dialog.png)

### <a name="review-questions"></a>Fragen prüfen

Klicken Sie auf **Fragen prüfen**, um eine Liste der Datasets aufzurufen, die im Power BI-Dienst für Ihren Mandanten verwendet werden. Auf der Seite **Fragen prüfen** werden auch der Besitzer des Datasets, der Arbeitsbereich und das Datum der letzten Aktualisierung angezeigt. Auf dieser Seite können Sie ein Dataset auswählen und prüfen, welche Fragen die Benutzer gestellt haben. Außerdem werden Wörter angezeigt, die nicht erkannt wurden. Es werden alle Daten der letzten 28 Tage angezeigt.

![Q&A: Fragen prüfen](media/q-and-a-tooling-intro/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Q&A trainieren

Im Abschnitt **Q&A-Training** können Sie die Q&A-Engine im Hinblick auf das Erkennen von Wörtern trainieren. Geben Sie zunächst eine Frage ein, die mindestens ein Wort enthält, das die Q&A-Engine nicht erkannt hat. Q&A fordert Sie dazu auf, diesen Begriff zu definieren. Geben Sie entweder einen Filter oder einen Feldnamen ein, der zu diesem Begriff passt. Q&A interpretiert anschließend die ursprüngliche Frage neu. Wenn Sie mit den Ergebnissen zufrieden sind, speichern Sie Ihre Eingabe. Weitere Informationen finden Sie unter [Q&A-Training](q-and-a-tooling-teach-q-and-a.md).

![Q&A-Training: Synonymvorschau](media/q-and-a-tooling-intro/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>Verwalten von Begriffen

Alle Elemente, die Sie dem Abschnitt „Q&A-Training“ entnommen und gespeichert haben, werden hier angezeigt, sodass Sie die von Ihnen definierten Begriffe prüfen oder löschen können. Derzeit ist es nicht möglich, vorhandene Definitionen zu bearbeiten. Wenn Sie einen Begriff neu definieren möchten, müssen Sie diesen löschen und einen neuen Eintrag erstellen.

![Q&A: Verwalten von Begriffen](media/q-and-a-tooling-intro/qna-manage-terms.png)

### <a name="suggest-questions"></a>Fragen vorschlagen

Wenn Sie keine Konfiguration vornehmen, schlägt das Q&A-Visual verschiedene Fragen vor, mit den gestartet wird. Diese Fragen werden automatisch entsprechend Ihrem Datenmodell generiert. In **Fragen vorschlagen** können Sie die automatisch generierten Fragen mit ihren eigenen Fragen überschreiben. 

Um damit zu beginnen, geben Sie die Frage, die Sie hinzufügen möchten, in das Textfeld ein. Im Vorschauabschnitt sehen Sie, wie das Ergebnis in dem Q&A-Visual aussehen wird. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-suggest-questions.png" alt-text="Q&A-Fragen vorschlagen":::
 
Wählen Sie die Schaltfläche **Hinzufügen** aus, um diese Frage zu **Ihre Vorschläge für Fragen** hinzuzufügen. Jede weitere Frage wird am Ende dieser Liste hinzugefügt. Die Fragen werden im Q&A-Visual in derselben Reihenfolge wie in dieser Liste angezeigt. 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-save-suggest-questions.png" alt-text="Vorgeschlagene Fragen speichern":::
 
Wählen Sie unbedingt **Speichern** aus, damit Ihre Liste der vorgeschlagenen Fragen im Q&A-Visual angezeigt wird. 


## <a name="other-qa-settings"></a>Weitere Q&A-Einstellungen

### <a name="bulk-synonyms"></a>Mehrere Synonyme

Die Registerkarte **Modellierung** in Power BI Desktop umfasst noch weitere Optionen zur Verbesserung der Q&A-Funktionen. 

1. Klicken Sie in Power BI Desktop auf die Ansicht „Modellierung“.

2. Klicken Sie auf ein Feld oder eine Tabelle, um den Bereich **Eigenschaften** anzuzeigen.  In diesem Bereich, der auf der rechten Seite der Canvas angezeigt wird, finden Sie mehrere Q&A-Aktionen. Eine der Optionen heißt **Synonyme**. Im Feld **Synonyme** können Sie ganz einfach Alternativen für die ausgewählte Tabelle oder das ausgewählte Feld definieren. Sie können zwar auch im Abschnitt **Q&A-Training** des Dialogfelds „Tooling“ (Tools) Synonyme definieren, aber es geht häufig schneller, wenn Sie die Synonyme für mehrere Felder in einer Tabelle über dieses Feld festlegen.

    ![Q&A-Modellierung: Bereich „Synonyme“](media/q-and-a-tooling-intro/qna-modelling-pane-synonyms.png)

3. Wenn Sie mehrere Synonyme für ein einzelnes Feld definieren möchten, trennen Sie die einzelnen Synonyme durch Kommas voneinander ab.

### <a name="hide-from-qa"></a>Für Q&A ausblenden

Sie können auch Felder und Tabellen ausblenden, damit sie nicht in den Q&A-Ergebnissen angezeigt werden. 

1. Klicken Sie in Power BI Desktop auf die Ansicht „Modellierung“.

2. Klicken Sie auf ein Feld oder eine Tabelle, um den Bereich **Eigenschaften** anzuzeigen, und legen Sie die Option **Ist verborgen** auf **On** (Ein) fest.

    Q&A berücksichtigt diese Einstellung und sorgt dafür, dass das Feld nicht erkannt wird. Sie sollten beispielsweise ID-Felder und Fremdschlüssel ausblenden, um unnötige Duplikate von Feldern mit demselben Namen zu vermeiden. Auch wenn Sie das Feld ausblenden, können Sie es weiterhin außerhalb von Q&A in Visuals in Power BI Desktop verwenden.

### <a name="set-a-row-label"></a>Festlegen einer Zeilenbeschriftung

Mithilfe einer Zeilenbeschriftung können Sie definieren, welche Spalte (oder welches *Feld*) eine einzelne Zeile in einer Tabelle am besten beschreibt. Für eine Tabelle mit dem Namen „Kunde“ lautet die Zeilenbeschriftung z. B. in der Regel „Anzeigename“. Durch die Angabe dieser zusätzlichen Metadaten kann Q&A nützlichere Visuals erstellen, wenn Benutzer z. B. die Aufforderung „Umsätze nach Kunden sortiert anzeigen“ eingeben. Q&A kann dann die Beschriftung „Anzeigename“ verwenden, anstatt den Begriff „Kunde“ als eine Tabelle zu behandeln, und ein Balkendiagramm mit den Umsätzen der einzelnen Kunden anzeigen. Sie können nur die Zeilenbeschriftung für die Ansicht „Modellierung“ festlegen. 

1. Klicken Sie in Power BI Desktop auf die Ansicht „Modellierung“.

2. Klicken Sie auf eine Tabelle, um den Bereich **Eigenschaften** anzuzeigen.

3. Wählen Sie im Feld **Zeilenbeschriftung** ein Feld aus.

## <a name="configure-the-linguistic-schema-advanced"></a>Konfigurieren des linguistischen Schemas (erweitert)

In Power BI können Sie die Engine für natürliche Sprache vollständig in Q&A trainieren und erweitern, einschließlich der Bewertung und Gewichtung der zugrunde liegenden Ergebnisse in natürlicher Sprache. Weitere Informationen finden Sie unter [Bearbeiten des linguistischen Schemas für Q&A und Hinzufügen von Ausdrücken](q-and-a-tooling-advanced.md).

## <a name="next-steps"></a>Nächste Schritte

Es gibt verschiedene Best Practices zur Verbesserung der Engine zur Verarbeitung natürlicher Sprache. Weitere Informationen finden Sie unter [Q&A: Best Practices](q-and-a-best-practices.md).
