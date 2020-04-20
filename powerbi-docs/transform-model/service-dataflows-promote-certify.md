---
title: Höherstufen oder Zertifizieren von Dataflows (Vorschau)
description: Hier erfahren Sie, wie Sie Dataflows höher stufen oder zertifizieren.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/17/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 7634711e8d26c4f265752427c5086e0901b210d5
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2020
ms.locfileid: "81268878"
---
# <a name="promote-or-certify-dataflows-preview"></a>Höherstufen oder Zertifizieren von Dataflows (Vorschau)

Power BI bietet zwei Möglichkeiten, die Sichtbarkeit Ihrer wertvollen, hochwertigen Dataflows zu erhöhen: die **Höherstufung** und die **Zertifizierung**.

* **Werbung**: Die Höherstufung ermöglicht es Benutzern, Dataflows hervorzuheben, die ihrer Meinung nach für andere Benutzer wertvoll und nützlich sind. Auf diese Weise wird die gemeinsame Verbreitung von Dataflows innerhalb einer Organisation unterstützt. Jeder Besitzer eines Dataflows oder jedes Mitglied mit Schreibberechtigungen für den Arbeitsbereich, in dem sich ein Dataflow befindet, kann den Dataflow einfach höher stufen, wenn er der Ansicht ist, dass dieser freigegeben werden kann.

* **Zertifizierung**: Zertifizierung bedeutet, dass ein Dataflow von einem autorisierten Prüfer geprüft wurde und tatsächlich eine zuverlässige, autoritative Datenquelle darstellt, die in der gesamten Organisation genutzt werden darf. Eine ausgewählte Gruppe von Prüfern, die vom Administrator des Power BI-Mandanten bestimmt wird, legt fest, welche Dataflows zertifiziert werden sollen. Ein Benutzer, der einen bestimmten Dataflow zertifizieren lassen möchte, aber nicht selbst dazu autorisiert ist, sollte sich an den Mandantenadministrator wenden.

  Die Zertifizierung von Dataflows ist nur möglich, wenn sie [vom Administrator des Power BI-Mandanten eingerichtet wurde](../admin/service-admin-setup-certification.md).

Das Höherstufen oder Zertifizieren eines Dataflows wird auch als *Endorsement* (Bestätigung) bezeichnet. Ersteller von Power BI-Berichten verfügen häufig über viele verschiedene Dataflows, aus denen sie auswählen können. Das Endorsement hilft ihnen dabei, diejenigen Dataflows zu finden, die zuverlässig, vertrauenswürdig und autorisiert sind.

Bestätigte Dataflows sind an mehreren Stellen in Power BI eindeutig beschriftet. So können Ersteller von Berichten, die nach zuverlässigen Daten suchen, diese leichter finden, und Administratoren und Berichtersteller können einfacher verfolgen, wie die Dataflows in der gesamten Organisation verwendet werden.

In der folgenden Abbildung wird gezeigt, wie höher gestufte und zertifizierte Dataflows leicht in Power Query identifiziert werden können.

![Bestätigte Dataflows in Power Query hervorgehoben](media/service-dataflows-promote-certify/powerbi-dataflow-endorsement-power-query.png)

In diesem Artikel wird Folgendes beschrieben:
* Höherstufen eines Dataflows (Dataflowbesitzer oder beliebiger Benutzer mit Mitgliederberechtigungen für den Arbeitsbereich, in dem sich der Dataflow befindet)
* Zertifizieren eines Dataflows (autorisierter Dataflowzertifizierer, wie vom Mandantenadministrator festgelegt)

Informationen zum Einrichten der Dataflowzertifizierung (Mandantenadministrator) finden Sie unter [Einrichten der Dataset- und Dataflowzertifizierung (Vorschau)](../admin/service-admin-setup-certification.md).


## <a name="promote-a-dataflow"></a>Höherstufen eines Dataflows

Zum Höherstufen eines Dataflows müssen Sie über Schreibberechtigungen für den Arbeitsbereich verfügen, in dem sich der Dataflow befindet, den Sie höher stufen möchten.

1. Navigieren Sie im Arbeitsbereich zur Liste der Dataflows.
 
1. Klicken Sie im Dataflow, den Sie höher stufen möchten, auf **Weitere Optionen (...)** und dann auf **Einstellungen**.

    ![Auswählen der Auslassungspunkte im Dataflow](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Erweitern Sie den Endorsement-Abschnitt, und klicken Sie auf **Höher gestuft**.

    ![Auswählen von „Höher gestuft“ und „Übernehmen“](media/service-dataflows-promote-certify/power-bi-dataflow-promoted-endorsement.png)

1. Klicken Sie auf **Übernehmen**.

## <a name="certify-a-dataflow"></a>Zertifizieren eines Dataflows

Dieser Abschnitt richtet sich an Benutzer, die von ihrem Mandantenadministrator dazu autorisiert wurden, Dataflows zu zertifizieren. Das Zertifizieren von Dataflows ist eine große Verantwortung. In diesem Abschnitt wird der Zertifizierungsprozess erläutert.

1. Verschaffen Sie sich Schreibberechtigungen für den Arbeitsbereich, in dem sich der Dataflow befindet, den Sie zertifizieren möchten. Dazu müssen Sie sich entweder an den Besitzer des Dataflows oder an jemanden mit Administratorberechtigungen für den Arbeitsbereich wenden. 

1. Überprüfen Sie sorgfältig den Dataflow, und ermitteln Sie, ob er zertifizierbar ist.

1. Wenn Sie sich dafür entscheiden, den Dataflow zu zertifizieren, wechseln Sie zu dem Arbeitsbereich, in dem er sich befindet.
 
1. Suchen Sie den gewünschten Dataflow, und klicken Sie auf **Weitere Optionen (...)**  > **Einstellungen**.

    ![Auswählen der Auslassungspunkte im Dataset oder Dataflow](media/service-dataflows-promote-certify/power-bi-dataflow-settings.png)

1. Erweitern Sie den Endorsement-Abschnitt, und klicken Sie auf **Zertifiziert**. 

    ![Klicken auf den Link „Weitere Informationen“](media/service-dataflows-promote-certify/service-certify-datasets-dataflows.png)

2. Klicken Sie auf **Übernehmen**.

## <a name="next-steps"></a>Nächste Schritte

* [Einrichten der Dataset- und Dataflowzertifizierung (Vorschau)](../admin/service-admin-setup-certification.md)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)