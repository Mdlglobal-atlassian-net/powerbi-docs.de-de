---
title: Wo befindet sich mein Power BI-Mandant?
description: Hier erfahren Sie, wo sich der Power BI-Mandant befindet und wie dieser Ort ausgewählt wird. Dies ist wichtig zu wissen, da es sich auf Ihre Interaktionen mit dem Dienst auswirken kann.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 4a763b31333004a8cdecda5262967473817bc983
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83135993"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Wo befindet sich mein Power BI-Mandant?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Hier erfahren Sie, wo sich der Power BI-Mandant befindet und wie dieser Ort ausgewählt wird. Die Kenntnis des Speicherorts ist wichtig, da er sich auf Ihre Interaktionen mit dem Dienst auswirken kann.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>So bestimmen Sie, wo sich der Power BI-Mandant befindet

Um die Region zu suchen, in der sich Ihr Mandant befindet, führen Sie die folgenden Schritte aus.

1. Klicken Sie im Power BI-Dienst im oberen Menü auf das Hilfesymbol ( **?** ) und dann auf **Info zu Power BI**.

1. Betrachten Sie den Wert neben **Ihre Daten sind gespeichert in**. Dies ist die Region, in der sich Ihr Mandant befindet. Dieser Wert bezeichnet außerdem die Region, in der Ihre Daten gespeichert werden, sofern Sie nicht dedizierte Kapazitäten in verschiedenen Regionen für Ihre Arbeitsbereiche verwenden.

    ![Datenbereich](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>So wird der Datenbereich ausgewählt

Die Datenregion basiert auf dem Land, das Sie beim Erstellen des Mandanten auswählen. Die Auswahl betrifft die Registrierung für Office 365 ebenso wie die für Power BI, da diese Informationen gemeinsam verwendet werden. Wenn es sich um einen neuen Mandanten handelt, wählen Sie beim Registrieren das entsprechende Land aus der Liste aus.

![Auswahl des Landes](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI wählt eine Datenregion aus, die sich möglichst nah an Ihrer Auswahl befindet – damit wird festgelegt, wo die Daten für Ihren Mandanten gespeichert werden.

> [!IMPORTANT]
> Die Auswahl kann nach Erstellung des Mandanten nicht geändert werden.

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

