---
title: Dienstunterbrechungsbenachrichtigungen
description: Erfahren Sie, wie Sie E-Mail-Benachrichtigungen erhalten, wenn ein Power BI-Dienst unterbrochen oder beeinträchtigt ist.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: kfollis
ms.openlocfilehash: 85b26b68c4943e0bc100be7a298730cec34cfc78
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637772"
---
# <a name="service-interruption-notifications"></a>Dienstunterbrechungsbenachrichtigungen

Es ist entscheidend, dass Sie Einblicke in die Verfügbarkeit Ihrer unternehmenskritischen Geschäftsanwendungen haben. Power BI stellt eine Benachrichtigung für Incidents bereit, sodass Sie optional E-Mails erhalten können, wenn ein Dienst unterbrochen oder beeinträchtigt ist. Auch wenn solche Incidents durch die Power BI-SLA (Vereinbarung zum Servicelevel) von 99,9 % nur selten sind, möchten wir sicherstellen, dass Sie stets informiert sind. Im folgenden Screenshot wird dargestellt, wie die E-Mail aussieht, die Sie erhalten, falls Sie die Benachrichtigungen aktivieren:

![Benachrichtigungs-E-Mail zur Aktualisierung](media/service-interruption-notifications/refresh-notification-email.png)

Derzeit senden wir E-Mails zu folgenden _Zuverlässigkeitsszenarios_:

- Zuverlässigkeit des Öffnens eines Berichts
- Zuverlässigkeit der Aktualisierung eines Modells
- Zuverlässigkeit der Aktualisierung einer Abfrage

Benachrichtigungen werden gesendet, wenn eine _längere Verzögerung_ bei Vorgängen wie dem Öffnen von Berichten, dem Aktualisieren von Datasets oder dem Ausführen von Abfragen eintritt. Nachdem ein Incident aufgelöst wurde, erhalten Sie erneut eine E-Mail.

> [!NOTE]
> Diese Funktion ist zurzeit nur für dedizierte Kapazitäten in Power BI Premium verfügbar. Sie ist nicht für gemeinsam genutzte oder eingebettete Kapazität verfügbar.





## <a name="enable-notifications"></a>Aktivieren von Benachrichtigungen

Ein Power BI-Mandantenadministrator aktiviert Benachrichtigungen im Verwaltungsportal:

1. Ermitteln oder erstellen Sie eine E-Mail-fähige Sicherheitsgruppe, die Benachrichtigungen erhalten soll.

1. Wählen Sie im Verwaltungsportal **Mandanteneinstellungen** aus. Erweitern Sie unter **Hilfe- und Supporteinstellungen** die Option **E-Mail-Benachrichtigungen bei Dienstausfällen oder Incidents**.

1. Aktivieren Sie die Benachrichtigungen, geben Sie eine Sicherheitsgruppe ein, und klicken Sie auf **Anwenden**.

    ![Aktivieren von Dienstbenachrichtigungen](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI sendet Benachrichtigungen vom Konto no-reply-powerbi@microsoft.com aus. Stellen Sie sicher, dass dieses Konto in die Whitelist aufgenommen wird, damit Benachrichtigungen nicht in einem Spam- oder Junk-Ordner landen.

## <a name="next-steps"></a>Nächste Schritte

[Power BI Pro und Power BI Premium: Supportoptionen](service-support-options.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
