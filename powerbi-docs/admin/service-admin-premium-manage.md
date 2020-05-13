---
title: Konfigurieren und Verwalten von Kapazitäten in Power BI Premium
description: Erfahren Sie, wie Sie Power BI Premium verwalten und den Zugriff auf Inhalte für Ihre gesamte Organisation aktivieren können.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: f4bf863d7d87bd908165976940b868be55e367f9
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83138436"
---
# <a name="configure-and-manage-capacities-in-power-bi-premium"></a>Konfigurieren und Verwalten von Kapazitäten in Power BI Premium

Das Verwalten von Power BI Premium umfasst das Erstellen, Verwalten und Überwachen von Premium-Kapazitäten. Dieser Artikel enthält Schrittanleitungen. Einen Überblick über Kapazitäten finden Sie unter [Verwalten von Premium-Kapazitäten](service-premium-capacity-manage.md).

Hier erfahren Sie, wie Sie Power BI Premium- und Power BI Embedded-Kapazitäten verwalten können, um dedizierte Ressourcen für Ihre Inhalte bereitzustellen.

![Bildschirm für Power BI-Kapazitätseinstellungen](media/service-admin-premium-manage/premium-capacity-management.png)

*Kapazität* ist der Kern von Power BI Premium und Power BI Embedded. Sie stellt eine Sammlung von Ressourcen dar, die exklusiv für die Nutzung durch Ihre Organisation reserviert sind. Wenn Sie über dedizierte Kapazität verfügen, können Sie Dashboards, Berichte und Datasets für Benutzer in Ihrer Organisation veröffentlichen, ohne separate Lizenzen für diese erwerben zu müssen. Außerdem bietet sie eine zuverlässige, beständige Leistung für die in der Kapazität gehosteten Inhalte. Weitere Informationen finden Sie unter [What is Power BI Premium? (Was ist Power BI Premium?)](../service-premium.md).

## <a name="manage-capacity"></a>Verwalten der Kapazität

Nachdem Sie Kapazitätsknoten in Office 365 erworben haben, können Sie die Kapazität im Power BI-Verwaltungsportal einrichten. Sie können Power BI Premium-Kapazitäten im Portalabschnitt **Kapazitätseinstellungen** verwalten.

![Kapazitätseinstellungen im Verwaltungsportal](media/service-admin-premium-manage/admin-portal-premium.png)

Sie können eine Kapazität verwalten, indem Sie deren Namen auswählen. Dadurch werden Sie zur Kapazitätsverwaltungsseite weitergeleitet.

![Auswählen des Kapazitätsnamens, um den Bildschirm für die Kapazitätszuweisung zu öffnen](media/service-admin-premium-manage/capacity-assignment.png)

Wenn der Kapazität keine Arbeitsbereiche zugewiesen wurden, wird eine entsprechende Meldung angezeigt, über die Sie der Kapazität [Arbeitsbereiche zuweisen](#assign-a-workspace-to-a-capacity) können.

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Einrichten einer neuen Kapazität (Power BI Premium)

Das Verwaltungsportal zeigt die Anzahl der *virtuellen Kerne* (V-Kerne) an, die Sie verwendet haben und Ihnen noch zur Verfügung stehen. Die Gesamtanzahl der V-Kerne ist abhängig von den Premium-SKUs, die Sie erworben haben. Wenn Sie beispielsweise eine P3- und eine P2-SKU erwerben, sind 48 Kerne verfügbar – 32 aus P3 und 16 aus P2.

![Verwendete und verfügbare V-Kerne für Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Wenn Sie verfügbare V-Kerne haben, können Sie Ihre neue Kapazität mit den folgenden Schritten einrichten.

1. Klicken Sie auf **Set up new capacity** (Neue Kapazität einrichten).

1. Benennen Sie Ihre Kapazität.

1. Legen Sie einen Administrator für diese Kapazität fest.

1. Wählen Sie den Kapazitätsumfang aus. Die verfügbaren Optionen hängen von der Anzahl der verfügbaren V-Kerne ab. Sie können keine Option mit einer Anzahl wählen, die größer als die verfügbare Anzahl ist.

    ![Verfügbare Premium-Kapazitätsumfänge](media/service-admin-premium-manage/premium-capacity-size.png)

1. Klicken Sie auf **Einrichten**.

    ![Einrichten einer neuen Kapazität](media/service-admin-premium-manage/set-up-capacity.png)

Die Kapazität wird Kapazitätsadministratoren sowie Administratoren von Power BI und globalen Administratoren von Office 365 im Verwaltungsportal angezeigt.

### <a name="capacity-settings"></a>Kapazitätseinstellungen

1. Sie können auf der Verwaltungsseite für Premium-Kapazitäten unter **AKTIONEN** auf das **Zahnradsymbol** klicken, um Einstellungen zu überprüfen und zu aktualisieren. 

    ![Kapazitätsaktionen im Kapazitätsverwaltungsbereich](media/service-admin-premium-manage/capacity-actions.png)

1. Sie können die jeweiligen Dienstadministratoren, die SKU/Größe und Region der Kapazität sehen.

    ![Kapazitätseinstellungen](media/service-admin-premium-manage/capacity-settings.png)

1. Sie können außerdem eine Kapazität umbenennen oder löschen.

    ![Schaltflächen zum Löschen und Anwenden für Kapazitätseinstellungen in Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> Power BI Embedded-Kapazitätseinstellungen werden im Microsoft Azure-Portal verwaltet.

### <a name="change-capacity-size"></a>Kapazitätsumfang ändern

Power BI-Administratoren und globale Administratoren von Office 365 können Power BI Premium-Kapazitäten ändern. Kapazitätsadministratoren, die keine Power BI-Administratoren oder globale Administratoren von Office 365 sind, verfügen nicht über diese Option.

1. Klicken Sie auf **Kapazitätsumfang ändern**.

    ![Ändern des Power BI Premium-Kapazitätsumfangs](media/service-admin-premium-manage/change-capacity-size.png)

1. Auf der Anzeige **Kapazitätsumfang ändern** können Sie nach Bedarf ein Upgrade oder Downgrade Ihrer Kapazität ausführen.

    ![Dropdownliste zum Ändern des Power BI Premium-Kapazitätsumfangs](media/service-admin-premium-manage/change-capacity-size2.png)

    Administratoren können Knoten erstellen, löschen und ihre Größe ändern, solange sie über die erforderliche Anzahl von V-Kernen verfügen.

    P-SKUs können nicht auf EM-SKUs herabgestuft werden. Sie können auf eine deaktivierte Option zeigen, um deren Erläuterung anzuzeigen.



> [!IMPORTANT]
> Wenn Ihre Power BI Premium-Kapazität einen hohen Ressourcenverbrauch aufweist, der zu Leistungs- oder Zuverlässigkeitsproblemen führt, erhalten Sie eine E-Mail-Benachrichtigung, damit Sie das Problem identifizieren und lösen können. Weitere Informationen finden Sie unter [Benachrichtigungen zu Kapazität und Zuverlässigkeit](service-interruption-notifications.md#capacity-and-reliability-notifications).


### <a name="manage-user-permissions"></a>Verwalten von Benutzerberechtigungen

Sie können zusätzliche Kapazitätsadministratoren zuweisen sowie Benutzer mit *Berechtigungen zur Kapazitätszuweisung*. Benutzer mit Zuweisungsberechtigungen können einer Kapazität einen Arbeitsbereich zuweisen, wenn sie Administrator dieses Arbeitsbereichs sind. Außerdem können sie der Kapazität ihren persönlichen Arbeitsbereich (*Mein Arbeitsbereich*) zuweisen. Benutzer mit Zuweisungsberechtigungen haben keinen Zugang zum Verwaltungsportal.

> [!NOTE]
> Kapazitätsadministratoren für Power BI Embedded werden im Microsoft Azure-Portal definiert.

Erweitern Sie unter **Benutzerberechtigungen** **Benutzer mit Zuweisungsberechtigungen** und fügen Sie dann die gewünschten Benutzer oder Gruppen hinzu.

![Benutzerberechtigungen zur Kapazitätszuweisung](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>Zuweisen eines Arbeitsbereichs zu einer Kapazität

Es gibt zwei Möglichkeiten, einer Kapazität einen Arbeitsbereich zuzuweisen: im Verwaltungsportal oder über einen Arbeitsbereich.

### <a name="assign-from-the-admin-portal"></a>Zuweisen über das Verwaltungsportal

Kapazitätsadministratoren können, genauso wie Administratoren von Power BI und globale Administratoren von Office 365, Massenzuweisungen von Arbeitsbereichen im Verwaltungsbereich für Premium-Kapazitäten im Verwaltungsportal durchführen. Beim Verwalten einer Kapazität wird Ihnen der Bereich **Arbeitsbereiche** angezeigt, in dem Sie Arbeitsbereiche zuweisen können.

![Bereich für die Zuweisung von Arbeitsbereichen in der Kapazitätsverwaltung](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Klicken Sie auf **Arbeitsbereiche zuweisen**. Diese Option ist an mehreren Stellen verfügbar.

1. Wählen Sie eine Option für **Übernehmen für:** .

    ![Arbeitsbereiche zuweisen](media/service-admin-premium-manage/assign-workspaces.png)

   | Auswahl | Beschreibung |
   | --- | --- |
   | **Arbeitsbereiche nach Benutzern** | Wenn Sie Ihre Arbeitsbereiche nach Benutzern oder Gruppen zuweisen, werden alle Arbeitsbereiche dieses Benutzers einer Premium-Kapazität zugewiesen, einschließlich seiner der persönlichen Arbeitsbereiche. Diese Benutzer erhalten automatisch Berechtigung zur Zuweisung von Arbeitsbereichen.<br>Dies gilt auch für Arbeitsbereiche, die bereits einer anderen Kapazität zugewiesen wurden. |
   | **Bestimmte Arbeitsbereiche** | Geben Sie den Namen eines bestimmten Arbeitsbereichs ein, den Sie der ausgewählten Kapazität zuweisen möchten. |
   | **Arbeitsbereiche der gesamten Organisation** | Wenn Sie die Arbeitsbereiche der gesamten Organisation einer Premium-Kapazität zuweisen, werden alle Arbeitsbereiche und „Meine Arbeitsbereiche“, die sich in Ihrer Organisation befinden, dieser Premium-Kapazität zugewiesen. Des Weiteren erhalten alle aktuellen und zukünftigen Benutzer die Berechtigung, einzelne Arbeitsbereiche erneut dieser Kapazität zuzuweisen. |
   | | |

1. Klicken Sie auf **Übernehmen**.

### <a name="assign-from-workspace-settings"></a>Zuweisen über Einstellungen von Arbeitsbereichen

Sie können einer Premium-Kapazität auch einen Arbeitsbereich über die Einstellungen dieses Arbeitsbereichs zuweisen. Um einen Arbeitsbereich in eine Kapazität zu verschieben, müssen Sie über Administratorberechtigungen für diesen Arbeitsbereich verfügen sowie über Berechtigungen zur Kapazitätszuweisung für diese Kapazität. Beachten Sie, dass Arbeitsbereichsadministratoren einen Arbeitsbereich jederzeit aus einer Premium-Kapazität entfernen können.

1. Sie können einen Arbeitsbereich bearbeiten, indem Sie auf die Auslassungspunkte **(...)** und dann auf **Edit workspace** (Arbeitsbereich bearbeiten) klicken.

    ![Bearbeiten des Arbeitsbereichs über das Kontextmenü mit den Auslassungspunkten](media/service-admin-premium-manage/edit-app-workspace.png)

1. Erweitern Sie unter **Bearbeiten des Arbeitsbereichs** **Erweitert**.

1. Wählen Sie die Kapazität aus, der Sie diesen Arbeitsbereich zuweisen möchten.

    ![Dropdownliste für die Kapazitätsauswahl](media/service-admin-premium-manage/app-workspace-advanced.png)

1. Wählen Sie **Speichern**.

Sobald Sie die Änderungen speichern, wird der Arbeitsbereich mitsamt seinen Inhalten in die Premium-Kapazität verschoben, ohne dass die Benutzererfahrung der Endbenutzer beeinträchtigt wird.

## <a name="power-bi-report-server-product-key"></a>Product Key für den Power BI-Berichtsserver

Auf der Registerkarte **Kapazitätseinstellungen** im Verwaltungsportal von Power BI haben Sie Zugang zum Product Key für den Power BI-Berichtsserver. Dieser steht nur globalen Administratoren oder Benutzern zur Verfügung, denen die Administratorrolle für den Power BI-Dienst zugewiesen wurde. Voraussetzung ist außerdem, dass Sie eine Power BI Premium-SKU erworben haben.

![Schlüssel für den Power BI-Berichtsserver in den Kapazitätseinstellungen](media/service-admin-premium-manage/pbirs-product-key.png)

Wenn Sie auf **Power BI Report Server key** (Schlüssel für den Power BI-Berichtsserver) klicken, wird ein Dialogfeld mit Ihrem Product Key angezeigt. Diesen können Sie kopieren und bei der Installation verwenden.

![Product Key für den Power BI-Berichtsserver](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Weitere Informationen finden Sie unter [Install Power BI Report Server (Installation vom Power BI-Berichtsserver)](../report-server/install-report-server.md).

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Premium-Kapazitäten](service-premium-capacity-manage.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
