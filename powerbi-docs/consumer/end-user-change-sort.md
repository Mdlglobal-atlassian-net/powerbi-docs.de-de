---
title: Ändern der Sortierung eines Diagramms in einem Bericht
description: Ändern der Sortierung eines Diagramms in einem Power BI-Bericht
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/19/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 811e0513c1b4a16a731e6d9bd90cbc0689ca76e0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279777"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändern der Sortierung eines Diagramms in einem Power BI-Bericht

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]


> [!IMPORTANT]
> **Dieser Artikel richtet sich an Power BI-Benutzer, die nicht berechtigt sind, den Bericht oder das Dataset zu bearbeiten, und die nur die Onlineversion von Power BI (Power BI-Dienst) verwenden. Wenn Sie ein Berichts- *Designer*, *administrator* oder *besitzer* sind, finden Sie in diesem Artikel möglicherweise nicht alle Informationen, die Sie benötigen. Stattdessen sollten Sie den Artikel [Sortieren nach Spalten in Power BI Desktop](../create-reports/desktop-sort-by-column.md)** lesen.

Im Power BI-Dienst können Sie das Erscheinungsbild eines Visuals ändern, indem Sie es nach verschiedenen Datenfeldern sortieren. Indem Sie die Sortierung eines Visuals ändern, können Sie die Informationen hervorheben, die Sie vermitteln möchten. Ob Sie numerische Daten (z.B. Umsatzzahlen) oder Text (z.B. Ländernamen) verwenden – die Visualisierungen lassen sich wunschgemäß sortieren. Power BI bietet große Flexibilität beim Sortieren sowie Schnellmenüs. 

Visuals auf einem Dashboard können nicht sortiert werden, aber in einem Power BI-Bericht können Sie die meisten Visualisierungen sortieren. 

## <a name="get-started"></a>Erste Schritte

Öffnen Sie zunächst einen beliebigen Bericht, der mit Ihnen geteilt wurde. Wählen Sie ein Visual aus, das sortiert werden kann, und klicken Sie auf die Auslassungspunkte (...), um **Weitere Aktionen** anzuzeigen.  Es gibt drei Optionen für das Sortieren: **Absteigend sortieren**, **Aufsteigend sortieren** und **Sortieren nach**. 
    

![Balkendiagramm mit alphabetischer Sortierung an der X-Achse](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Alphabetisches oder numerisches Sortieren

Visuals lassen sich alphabetisch nach den Textnamen der Kategorien im Visual oder nach den numerischen Werten jeder Kategorie sortieren. In diesem Diagramm wird z.B. alphabetisch nach der Kategorie auf der X-Achse **Name** sortiert.

![Balkendiagramm mit alphabetischer Sortierung an der X-Achse](media/end-user-change-sort/powerbi-sort-category.png)

Sie können ganz einfach statt nach einer Kategorie (Geschäftsname) nach einem Wert (Umsatz pro Quadratfuß) sortieren. Wählen Sie die Auslassungspunkte (...) für **Weitere Aktionen** und **Sortieren nach** aus. Wählen Sie einen numerischen Wert aus, der im Visual verwendet wird.  In diesem Beispiel wird **Sales Per Sq Ft** ausgewählt.

![Screenshot mit Auswahl von „Sortieren nach“ und einem anschließenden Wert](media/end-user-change-sort/power-bi-sort-value.png)

Ändern Sie ggf. die Sortierreihenfolge von aufsteigend in absteigend oder umgekehrt.  Wählen Sie noch einmal **Weitere Aktionen** (...) und dann **Absteigend sortieren** bzw. **Aufsteigend sortieren** aus. Das Feld, das zum Sortieren verwendet wird, ist fett dargestellt und weist eine gelbe Leiste auf.

   ![Video: Auswählen von „Sortieren nach“ und dann „Aufsteigend sortieren“, „Absteigend sortieren“](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nicht alle Visuals können sortiert werden. Beispielsweise können die folgenden Visuals nicht sortiert werden: Treemaps, Karten, Flächenkartogramme, Punktdiagramme, Tachometerdiagramme, Kartendiagramme, Wasserfalldiagramme.

## <a name="saving-changes-you-make-to-sort-order"></a>Speichern der Änderungen an der Sortierreihenfolge
Power BI-Berichte behalten die von Ihnen vorgenommenen Änderungen an den Filtern, den Datenschnitten, der Sortierung und anderen Datenansichten bei, selbst wenn Sie in der [Leseansicht](end-user-reading-view.md) arbeiten. Wenn Sie also einen Bericht verlassen und später zurückkehren, werden Ihre Änderungen an der Sortierung gespeichert.  Klicken Sie auf der oberen Menüleiste auf **Auf Standardwert zurücksetzen**, wenn Sie Ihre Änderungen an den Einstellungen des Berichts-*Designers* zurücksetzen möchten. 

![Sortierung beibehalten](media/end-user-change-sort/power-bi-reset.png)

Ist die Schaltfläche **Auf Standardwert zurücksetzen** jedoch ausgegraut, bedeutet das, dass der *Designer* für Berichte die Option zum Speichern (Beibehalten) der Änderungen deaktiviert hat.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

### <a name="sorting-using-other-criteria"></a>Sortieren mithilfe anderer Kriterien
Zuweilen möchten Sie Ihre Visualisierung anhand eines anderen Felds (das nicht im Visual enthalten ist) oder anderer Kriterien sortieren,  beispielsweise nach Monat in einer sequenziellen Reihenfolge (anstatt in alphabetischer Reihenfolge) oder nach ganzen Zahlen anstatt nach Ziffer (z. B. 0, 1, 9, 20 und nicht 0, 1, 20, 9).  

Nur die Person, die den Bericht entworfen hat, kann diese Änderungen für Sie vornehmen. Kontaktinformationen zum *Designer* des Berichts können Sie erfahren, indem Sie den Namen des Berichts in der Kopfleiste auswählen.

![Dropdownfeld mit Kontaktinformationen](media/end-user-change-sort/power-bi-contact.png)

Wenn Sie ein *Designer* sind und über die Berechtigungen verfügen, den Inhalt zu bearbeiten, erfahren Sie im Artikel [Sortieren nach Spalten in Power BI Desktop](../create-reports/desktop-sort-by-column.md), wie Sie das Dataset aktualisieren und diese Art von Sortierung aktivieren.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu [Visualisierungen in Power BI-Berichten](end-user-visualizations.md).

[Power BI – Grundkonzepte](end-user-basic-concepts.md)
