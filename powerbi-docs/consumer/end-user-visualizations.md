---
title: Arbeiten mit Visualisierungen (visuellen Elementen) als Benutzer
description: Konzepte und Terminologie für Power BI-Benutzer – Visualisierungen, visuelle Elemente. Was ist eine Power BI-Visualisierung bzw. ein visuelles Element.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1aaacfae3c9af4517f6b028852e46059884dd3d5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79113848"
---
# <a name="interact-with-visuals-in-reports-dashboards-and-apps"></a>Interagieren mit Visuals in Berichten, Dashboards und Apps

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

In ihrer einfachsten Form ist eine ***Visualisierung*** (oder ein *visuelles Element*) eine Art von Diagramm, das von einem Power BI-*Designer* mithilfe der Daten in Berichten und Datasets erstellt wurde. 

Visuals werden in Dashboards und in Berichten gefunden und können mit Power BI Q&A dynamisch erstellt werden. Wenn ein Designer ein Visual in einem Bericht erstellt, kann er dieses Visual an ein Dashboard *anheften*. Ein [Visual auf einem Dashboard wird als *Kachel* bezeichnet](end-user-tiles.md). Dieses Dashboard verfügt über acht Kacheln. 

![Dashboard mit Kacheln](media/end-user-visualizations/power-bi-dashboard.png)

> [!TIP]
> Es wird empfohlen, zunächst das Übersichtsthema [Power BI – Grundkonzepte für *Benutzer*](end-user-basic-concepts.md) zu lesen, bevor Sie diese detaillierteren Inhalte lesen.

## <a name="what-can-i-do-with-visuals"></a>Wofür kann ich visuelle Elemente verwenden?

Visuelle Elemente werden von Berichts- und Dashboard-*Designern* erstellt und mit *Benutzern* geteilt. Als Benutzer haben Sie viele Möglichkeiten zur Interaktion mit visuellen Elementen, um Einblicke zu erhalten und datenbasierte Geschäftsentscheidungen zu treffen. Die meisten dieser Optionen sind in der folgenden Tabelle zusammen mit Links zu ausführlichen Anweisungen aufgeführt.

Für viele dieser Optionen kann Ihr Administrator oder der *Designer* die Möglichkeit deaktivieren, diese Features anzuzeigen oder zu verwenden. Einige dieser Features funktionieren nur für bestimmte Visuals.  Falls Sie Fragen haben, wenden Sie sich an Ihren Administrator oder den Besitzer des Berichts oder Dashboards. Wählen Sie die Dashboard- oder Bericht-Dropdownliste aus, um den Besitzer zu suchen. 

![Titel-Dropdown mit Besitzer](media/end-user-visualizations/power-bi-owner.png)


> [!IMPORTANT]
> Aber zuerst ein Wort zu Q&A. Q&A ist das natürlichsprachliche Suchtool von Power BI. Sie geben eine Frage in natürlicher Sprache ein, und Q&A beantwortet die Frage in Form eines visuellen Elements. Q&A ist eine Möglichkeit für Benutzer, um ihre eigenen Visuals im Handumdrehen zu erstellen. Die visuellen Elemente, die Sie mit Q&A erstellen, lassen sich jedoch nicht speichern. Wenn Sie aber etwas bestimmtes aus den Daten erfahren möchten, und der Designer hat es nicht in einen Bericht oder ein Dashboard aufgenommen, ist Q&A eine hervorragende Option. Weitere Informationen zu Q&A finden Sie unter [Q&A für Benutzer](end-user-q-and-a.md).



|Task  |In einem Dashboard  |In einem Bericht  | In Q&A
|---------|---------|---------|--------|
|[Fügen Sie einem visuellen Element für sich selbst Kommentare hinzu, oder beginnen Sie ein Gespräch mit Kollegen über das visuelle Element](end-user-comment.md).     |  ja       |   ja      |  Nein  |
|[Öffnen und erkunden Sie den Bericht, in dem das visuelle Element erstellt wurde](end-user-tiles.md).     |    ja     |   NV      |  Nein |
|[Zeigen Sie eine Liste der Filter und Slicer an, die sich auf das Visual auswirken](end-user-report-filter.md).     |    wenn Sie es im Fokusmodus öffnen     |   ja      |  Nein |
|[Öffnen und erkunden Sie ein Visual in Q&A (wenn der *Designer* das Visual mit Q&A erstellt hat)](end-user-q-and-a.md).     |   ja      |   NV      |  NV  |
|[Erstellen Sie ein Visual in Q&A (zur Untersuchung können Sie es nicht speichern)](end-user-q-and-a.md).     |   ja      |   Wenn der Designer Q&A dem Bericht hinzugefügt hat      |  ja  |
|[Lassen Sie Power BI für Sie in den Daten des visuellen Elements nach interessanten Fakten oder Trends ](end-user-insights.md) zu suchen.  Diese automatisch generierten Visuals werden *Erkenntnisse* genannt.     |    ja, für Kacheln    |  Nein       | Nein   |
|[Zeigen Sie immer nur ein visuelles Element gleichzeitig an, indem Sie den *Fokus*modus](end-user-focus.md) verwenden.     | ja, für Kacheln        |   ja, für Visuals      | NV  |
|[Suchen Sie den Zeitpunkt, zu dem das Visual zum letzten Mal aktualisiert wurde](end-user-fresh.md).     |  ja       |    ja     | NV  |
|[Zeigen Sie immer nur ein Visual gleichzeitig ohne Ränder oder Navigationsbereiche an, indem Sie den *Vollbildmodus* verwenden](end-user-focus.md).     |   ja      |  ja       | Standardmäßig  |
|[Drucken](end-user-print.md).     |  ja       |   ja      | Nein  |
|[Untersuchen Sie das visuelle Element, indem Sie visuelle Filter hinzufügen und ändern.](end-user-report-filter.md)     |    Nein     |   ja      | Nein  |
|Zeigen Sie auf ein visuelles Element, um zusätzliche Details und QuickInfos anzuzeigen.     |    ja     |   ja      | ja  |
|[Kreuzfiltern Sie andere visuelle Elemente auf der Seite, oder heben Sie sie hervor.](end-user-interactions.md)    |   Nein      |   ja      | NV  |
|[Zeigen Sie die zum Erstellen des visuellen Elements verwendeten Daten an](end-user-show-data.md).     |  Nein       |   ja      | Nein  |
| [Ändern Sie die Art, in der das visuelle Element sortiert ist](end-user-change-sort.md). | Nein  | ja  | Sortierung kann durch Umformulieren der Frage geändert werden  |
| Fügen Sie einem visuellen Element ein Spotlight hinzu. | Nein  | ja  |  Nein |
| [Exportieren Sie nach Excel.](end-user-export.md) | ja | ja | Nein|
| [Erstellen Sie eine Warnung](end-user-alerts.md), um Sie zu benachrichtigen, wenn ein Wert einen von Ihnen festgelegten Schwellenwert überschreitet.  | ja  | Nein  | Nein |
| [Führen Sie an den anderen Visuals auf der Seite eine Kreuzfilterung und übergreifende Hervorhebung aus](end-user-report-filter.md).  | Nein      | ja  | NV |
| [Führen Sie ein Drillup an einem Visual mit einer Hierarchie aus](end-user-drill.md).  | Nein  | ja   | Nein |

## <a name="next-steps"></a>Weitere Schritte
Zurück zu [Grundlegende Konzepte für Benutzer](end-user-basic-concepts.md)    
[Auswählen eines visuellen Elements zum Öffnen eines Berichts](end-user-report-open.md)    
[In Power BI verfügbare Typen visueller Elemente](end-user-visual-type.md)