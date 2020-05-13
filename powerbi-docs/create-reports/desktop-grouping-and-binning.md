---
title: Verwenden von Gruppierung und Diskretisierung in Power BI Desktop
description: Erfahren Sie, wie in Power BI Desktop Elemente gruppiert und diskretisiert werden.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 525f7bf4c967722d8f98a9184127bc8c7907cea1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83309473"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Verwenden von Gruppierung und Diskretisierung in Power BI Desktop
Beim Erstellen von Visuals in Power BI Desktop werden die Daten basierend auf Werten in den zugrunde liegenden Daten in Blöcke (oder Gruppen) aggregiert. Häufig ist dies ausreichend, in manchen Situationen ist es jedoch sinnvoll, die Darstellung der Blöcke zu verfeinern. Beispielsweise möchten Sie eventuell drei Kategorien von Produkten in einer größeren Kategorie (einer *Gruppe*) anordnen. Alternativ sollen Umsatzzahlen in Diskretisierungen der Größe 1.000.000 US-Dollar statt in Blöcke von 923.983 US-Dollar unterteilt werden.

Sie können in Power BI Desktop Datenpunkte *gruppieren*, um Daten und Trends in den Visualisierungen deutlicher anzeigen, analysieren und untersuchen zu können. Sie können zudem die *Größe der Diskretisierung* festlegen, um Werte in Gruppen gleicher Größe zu unterteilen, die es ihnen erleichtern, Daten aussagekräftig zu visualisieren. Dieser Vorgang wird häufig als *Quantisierung* bezeichnet.

## <a name="using-grouping"></a>Verwenden von Gruppierung
Wählen Sie zum Verwenden der Gruppierung mindestens zwei Elemente in einem Visual aus. Über STRG+Klick können Sie mehrere Elemente auswählen. Klicken Sie dann mit der rechten Maustaste auf eines der ausgewählten Elemente, und klicken Sie im Kontextmenü auf **Gruppieren**.

![Befehl „Gruppieren“, Diagramm, Gruppierung, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_1.png)

Nachdem die Gruppe erstellt wurde, wird sie dem Bucket **Legende** für das Visual hinzugefügt. Die Gruppe wird auch in der Liste **Felder** angezeigt.

![Listen „Legende“ und „Felder“, Gruppierung, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_2.png)

Sie können die Mitglieder einer Gruppe problemlos bearbeiten. Klicken Sie mit der rechten Maustaste auf das Feld im Bucket **Legende** oder in der Liste **Felder**, und klicken Sie dann auf **Gruppen bearbeiten**.

![Befehl „Gruppen bearbeiten“, Listen „Legende“ und „Felder“, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_3.png)

Im Dialogfeld **Gruppen** können Sie neue Gruppen erstellen oder vorhandene Gruppen bearbeiten. Sie können *Gruppen* auch umbenennen. Doppelklicken Sie im Feld **Gruppen und Mitglieder** auf den Gruppentitel, und geben Sie dann einen neuen Namen ein.

Gruppen bieten Ihnen viele Möglichkeiten. Sie können Elemente von der Liste **Nicht gruppierte Werte** zu einer neuen oder einer existierenden Gruppe hinzufügen. Sie können eine neue Gruppe erstellen, indem Sie im Feld **Nicht gruppierte Werte** (mit STRG+Klick) mindestens zwei Elemente auswählen und dann auf die Schaltfläche **Gruppieren** klicken, die sich unter dem Feld befindet.

Sie können einen nicht gruppierten Wert zu einer bestehenden Gruppe hinzufügen, indem Sie einen der **nicht gruppierten Werte** und dann die bereits vorhandene Gruppe auswählen, der Sie den Wert hinzufügen möchten, und dann auf **Gruppieren** klicken. Sie können ein Element aus einer Gruppe zu entfernen, indem Sie im Feld **Gruppen und Mitglieder** auf das Element und dann auf **Gruppierung aufheben** klicken. Außerdem können Sie nicht gruppierte Kategorien in die Gruppe **Other** (Sonstiges) verschieben oder ungruppiert lassen.

![Dialogfeld „Gruppen“, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> Sie können im Bereich **Felder** Gruppen für jedes Feld erstellen, ohne mehrere Elemente in einem vorhandenen Visual auswählen zu müssen. Klicken Sie einfach mit der rechten Maustaste auf das Feld, und wählen Sie im angezeigten Menü **Neue Gruppe** aus.

## <a name="using-binning"></a>Verwenden von Diskretisierung
Sie können die Größe der Diskretisierung für numerische Felder und Zeitfelder in **Power BI Desktop** festlegen. Mit der Quantisierung können Sie die richtige Größe der in Power BI Desktop angezeigten Daten festlegen.

Sie können die Größe einer Quantisierung anwenden, indem Sie mit der rechten Maustaste auf ein **Feld** und dann auf **Neue Gruppe** klicken.

![Befehl „Neue Gruppe“, Liste „Felder“, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_5.png)

Legen Sie im Dialogfeld **Gruppen** die **Größe für Diskretisierung** nach Belieben fest.

![„Größe für Diskretisierung“, Dialogfeld „Gruppen“, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_6.png)

Wenn Sie auf **OK** klicken, wird im Bereich **Felder** ein neues Feld angezeigt, an das **(Container)** angefügt ist. Sie können das Feld dann in den Zeichenbereich ziehen, um die Größe der Diskretisierung in einer Visualisierung zu verwenden.

![bins-Feld in die Canvas ziehen, Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_7.png)

In diesem *Video* wird gezeigt, wie [Diskretisierung](https://www.youtube.com/watch?v=BRvdZSfO0DY) angewendet wird.

Nun verfügen Sie über die nötigen Informationen, um *Gruppierung* und *Diskretisierung* zu verwenden und um sicherzustellen, dass die Visualisierungen in den Berichten die Daten genau so anzeigen, wie Sie es wünschen.
