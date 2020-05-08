---
title: Einrichten der Dataset- und Dataflowzertifizierung (Vorschau)
description: Hier erfahren Sie, wie Sie in Ihrer Organisation den Zertifizierungsprozess für Datasets und Dataflows einrichten.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/22/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 1fc33b48613335f4fba97921e3d528175eb2a47f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "81267843"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>Einrichten der Dataset- und Dataflowzertifizierung (Vorschau)

Ihre Organisation kann Datasets und Dataflows zertifizieren, die die autoritative Quelle für kritische Informationen darstellen.

Als Power BI-Mandantenadministrator sind Sie für das Einrichten des Zertifizierungsprozesses in Ihrer Organisation verantwortlich. Dies bedeutet Folgendes:
* Aktivieren der Zertifizierung für Ihren Mandanten
* Definieren einer Liste von Gruppen und Benutzern, die zur Zertifizierung von Datasets und Dataflows autorisiert sind
* Bereitstellen der URL zur Zertifizierungsrichtlinie für Datasets, sofern vorhanden

Die Dataset- und Dataflowzertifizierung ist Teil des *Endorsements* von Datasets und Dataflows. Weitere Informationen finden Sie unter [Dataset-Endorsement](../service-datasets-promote.md) und [Dataflow-Endorsement](../transform-model/service-dataflows-promote-certify.md).


## <a name="set-up-certification"></a>Einrichten der Zertifizierung

1. Navigieren Sie im Verwaltungsportal zu „Mandanteneinstellungen“.
1. Erweitern Sie im Abschnitt „Einstellungen für Export und Freigabe“ den Abschnitt „Zertifizierung“.

   ![Einrichten der Dataset- und Dataflowzertifizierung](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Schalten Sie auf **Aktiviert** um.
1. Wenn Ihre Organisation über eine veröffentlichte Zertifizierungsrichtlinie für die Zertifizierung von Datasets verfügt, können Sie die entsprechende URL hier bereitstellen. Daraus wird der Link **Weitere Informationen** erstellt, der im Dialogfeld zu den [Einstellungen für das Dataflow-Endorsement](../service-datasets-promote.md#request-dataset-certification) im Abschnitt „Zertifizierung“ angezeigt wird. 
1. Geben Sie die Benutzer oder Gruppen an, die zur Zertifizierung von Datasets und Dataflows autorisiert sind. Nur diesen Benutzern ist es möglich, im Dialogfeld zu den Einstellungen für das Endorsement von [Datasets](../service-datasets-promote.md#request-dataset-certification) oder [Dataflows](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow) im Abschnitt „Zertifizierung“ die Schaltfläche „Zertifizierung“ zu verwenden.
1. Klicken Sie auf **Übernehmen**.

## <a name="next-steps"></a>Weitere Schritte
* [Höher Stufen von Datasets](../service-datasets-promote.md)
* [Zertifizieren von Datasets](../service-datasets-certify.md)
* [Höherstufen von Dataflows](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow)
* [Zertifizieren von Dataflows](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow)
* Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
