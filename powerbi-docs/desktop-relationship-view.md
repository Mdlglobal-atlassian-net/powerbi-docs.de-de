---
title: Modellansicht in Power BI Desktop
description: Modellansicht in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ea568c061142e66e79351de8a6c0f0603a46f775
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753221"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Arbeiten mit der Modellansicht in Power BI Desktop

In der *Modellansicht* werden alle Tabellen, Spalten und Beziehungen in Ihrem Modell angezeigt. Dies kann besonders hilfreich sein, wenn Ihr Modell über komplexe Beziehungen zwischen vielen Tabellen verfügt.

Klicken Sie auf das **Modellsymbol** am Rand des Fensters, um das vorhandene Modell abzurufen. Zeigen Sie mit dem Mauszeiger auf eine Beziehungslinie, um die verwendeten Spalten anzuzeigen.

![Modellansicht, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

In der obigen Abbildung verfügt die Tabelle *Stores* (Geschäfte) über eine Spalte namens *StoreKey* (Geschäftsschlüssel), die mit der Tabelle *Sales* (Verkäufe) verknüpft ist, die ebenfalls eine *StoreKey*-Spalte (Geschäftsschlüssel) aufweist. Zwischen den beiden Tabellen besteht eine *n:1*-Beziehung (\*:1). Ein Pfeil in der Mitte der Linie zeigt die Richtung des Kontextflusses des Filters an. Die doppelten Pfeile bedeuten, dass die Kreuzfilterrichtung auf *Beide* festgelegt ist.

Doppelklicken Sie auf eine Beziehung, um sie im Dialogfeld **Beziehung bearbeiten** zu öffnen. Weitere Informationen über Beziehungen finden Sie unter [Erstellen und Verwalten von Beziehungen in Power BI Desktop](desktop-create-and-manage-relationships.md).
