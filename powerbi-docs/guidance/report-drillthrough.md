---
title: Verwenden des Drillthrough für Berichtsseiten
description: Leitfaden zum Arbeiten mit Drillthroughs für Berichtsseiten
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2019
ms.author: v-pemyer
ms.openlocfilehash: d5599db57ef7b105575dcb7ee4b4342f374624f0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78290581"
---
# <a name="use-report-page-drillthrough"></a>Verwenden des Drillthrough für Berichtsseiten

Dieser Artikel richtet sich an Berichtsautoren wie Sie, die Power BI-Berichte entwerfen. Er enthält Vorschläge und Empfehlungen für das Erstellen von [Drillthroughs für Berichtsseiten](../desktop-drillthrough.md).

Es wird empfohlen, den Bericht so zu entwerfen, dass dieser Berichtsbenutzern den folgenden Flow ermöglicht:

1. Anzeigen einer Berichtsseite
2. Identifizieren eines visuellen Elements zur detaillierteren Analyse
3. Rechtsklick auf das visuelle Element für den Drillthrough
4. Durchführen einer ergänzenden Analyse
5. Zurückkehren zur Ausgangsberichtsseite

## <a name="suggestions"></a>Vorschläge

Es wird empfohlen, zwei Arten von Drillthroughszenarios in Erwägung zu ziehen:

- [Zusätzliche Tiefe](#additional-depth)
- [Breitere Perspektive](#broader-perspective)

### <a name="additional-depth"></a>Zusätzliche Tiefe

Wenn die Berichtsseite zusammengefasste Ergebnisse anzeigt, kann eine Drillthroughseite Berichtsbenutzer zu Details auf Transaktionsebene führen. Dieser Entwurfsansatz ermöglicht es Ihnen, unterstützende Transaktionen anzuzeigen, wenn Sie diese benötigen.

Das folgende Beispiel zeigt, was geschieht, wenn ein Berichtsbenutzer einen Drillthrough zu einer monatlichen Umsatzübersicht ausführt. Die Drillthroughseite enthält eine detaillierte Liste der Aufträge für einen bestimmten Monat.

![In dem Matrixvisual „Sales Summary“ (Umsatzübersicht) werden die Umsätze nach Jahr und Monat in Zeilen und die Länder in Spalten gruppiert. Eine Drillthroughseite wird ebenfalls angezeigt.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Breitere Perspektive

Mit einer Drillthroughseite kann das Gegenteil der zusätzlichen Tiefe erreicht werden. Dieses Szenario eignet sich hervorragend für einen Drillthrough zu einer ganzheitlichen Ansicht.

Das folgende Beispiel zeigt, was geschieht, wenn ein Berichtsbenutzer einen Drillthrough zu einer Postleitzahl ausführt. Die Drillthroughseite zeigt allgemeine Informationen zu dieser Postleitzahl an.

![Ein Tabellenvisual mit drei Spalten: „Zip Code“ (Postleitzahl), „Average of Violation Points“ (Durchschnittl. Verstöße) und „Average of Grade Rating“ (Durchschnittl. Bewertung). Eine Drillthroughseite wird ebenfalls angezeigt.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Empfehlungen

Zur Entwurfszeit des Berichts werden wir die folgenden Vorgehensweisen empfohlen:

- **Stil:** Verwenden Sie beim Entwerfen der Drillthroughseite ggf. dasselbe Design und denselben Stil wie im Bericht. Dadurch haben Benutzer das Gefühl, als würden sie mit dem Bericht arbeiten.
- **Drillthroughfilter:** Legen Sie Drillthroughfilter fest, damit Sie ein realistisches Ergebnis anzeigen können, während Sie die Drillthroughseite entwerfen. Achten Sie darauf, dass Sie diese Filter vor dem Veröffentlichen des Berichts entfernen.
- **Zusätzliche Funktionen:** Eine Drillthroughseite kann wie jede beliebige Berichtsseite verwendet werden. Sie können diese sogar um zusätzliche interaktive Funktionen wie Slicer oder Filter erweitern.
- **Leere Seiten:** Fügen Sie keine Visuals hinzu, die eine leere Seite anzeigen oder beim Anwenden von Drillthroughfiltern zu Fehler führen könnten.
- **Sichtbarkeit der Seite:** Denken Sie daran, Drillthroughseiten zu verbergen. Wenn Sie eine Drillthroughseite anzeigen möchten, stellen Sie sicher, dass Sie eine Schaltfläche hinzufügen, die es Benutzern ermöglicht, alle zuvor festgelegten Drillthroughfilter zu löschen. Weisen Sie der Schaltfläche ein [Lesezeichen](../desktop-bookmarks.md) zu. Das Lesezeichen sollte so konfiguriert werden, dass alle Filter entfernt werden.
- **Schaltfläche „Zurück“:** Eine [Schaltfläche](../desktop-buttons.md) „Zurück“ wird automatisch hinzugefügt, wenn Sie einen Drillthroughfilter zuweisen. Es wird empfohlen, diese beizubehalten, denn so können die Benutzer des Berichts einfach zur Ausgangsseite zurückkehren.
- **Auffinden:** Helfen Sie, die Aufmerksamkeit auf eine Drillthroughseite zu lenken, indem Sie einen Text für das Symbol im Visualheader festlegen oder Anweisungen zu einem Textfeld hinzufügen. Alternativ können Sie eine Überlagerung entwerfen, wie im [diesem Blogbeitrag](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/) beschrieben.

> [!TIP]
> Außerdem ist es möglich, Drillthroughs für Ihre paginierten Power BI-Berichte zu konfigurieren. Dazu fügen Sie zu den Power BI-Berichten Links hinzu. Über Links können [URL-Parameter](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/) definiert werden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Verwenden der Drillthroughfunktion in Power BI Desktop](../desktop-drillthrough.md)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com/)
