---
title: Administratorleitfaden zu Mandanteneinstellungen
description: Leitfaden zu Power BI-Mandanteneinstellungen
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: v-pemyer
ms.openlocfilehash: fdd7504823f088ed0e88657a6fcccaeb9a5a36d0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79487807"
---
# <a name="tenant-admin-settings-guidance"></a>Administratorleitfaden zu Mandanteneinstellungen

Dieser Artikel richtet sich an Power BI-Administratoren, die für das Einrichten und Konfigurieren der Power BI Umgebung in Ihrer Organisation verantwortlich sind.

Hier finden Sie Anleitungen für bestimmte Mandanteneinstellungen, mit denen Sie Power BI optimieren oder Ihre Organisation einem Risiko aussetzen können. Es wird empfohlen, dass Sie Ihren Mandanten immer so konfigurieren, dass er den Richtlinien und Prozessen Ihrer Organisation entspricht.

[Mandanteneinstellungen](../service-admin-portal.md#tenant-settings) werden im [Verwaltungsportal](https://app.powerbi.com/admin-portal/tenantSettings) verwaltet und können von einem [Power BI-Dienstadministrator](../service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi) konfiguriert werden. Viele Mandanteneinstellungen können Funktionen und Features auf eine begrenzte Anzahl von Benutzern einschränken. Daher ist es empfehlenswert, dass Sie sich zuerst mit den Einstellungen vertraut machen, um die benötigten Sicherheitsgruppen zu planen. Möglicherweise können Sie dieselbe Sicherheitsgruppe auf mehrere Einstellungen anwenden.

## <a name="improve-power-bi-experience"></a>Optimieren von Power BI

### <a name="publish-get-help-information"></a>Veröffentlichen von Informationen zu „Hilfe erhalten“

Es ist empfehlenswert, interne Power BI-bezogene Websites mit [Microsoft Teams](/microsoftteams) oder anderen Plattformen für die Zusammenarbeit einzurichten. Über diese Websites können z. B. Trainingsdokumentation gespeichert, Diskussionen gehostet, Lizenzanforderungen gesendet und auf Hilfeanfragen geantwortet werden.

In diesem Fall wird auch empfohlen, dass Sie die Einstellung **Informationen zu „Hilfe anfordern“ veröffentlichen** _für die gesamte Organisation_ aktivieren. Sie finden sie in der Gruppe **Hilfe- und Supporteinstellungen**. Sie können URLs für Folgendes festlegen:

- Trainingsdokumentation
- Diskussionsforen
- Lizenzierungsanforderungen
- Helpdesk

Diese URLs werden als Links im Power BI-Hilfemenü verfügbar gemacht.

> [!NOTE]
> Wenn Sie die URL **Lizenzierungsanforderungen** bereitstellen, verhindern Sie, dass einzelne Benutzer sich für die kostenlose 60-tägige Testversion von Power BI Pro registrieren. Stattdessen werden Sie zu Ihrer internen Website weitergeleitet, wo Sie darüber informiert werden, wie sie eine Lizenz erhalten, sowohl für die kostenlose als auch für die Pro-Version.

![Die Einstellung „Informationen zu ‚Hilfe anfordern´ veröffentlichen“ wird angezeigt.](media/admin-tenant-settings/publish-get-help-information.png)

## <a name="manage-risk"></a>Risikomanagement

### <a name="receive-email-notification-service-outages-or-incidents"></a>E-Mail-Benachrichtigungen bei Dienstausfällen oder Vorfällen

Sie können per E-Mail benachrichtigt werden, wenn Ihr Mandant von einem Dienstausfall oder Vorfall betroffen ist. So können Sie proaktiv auf Vorfälle reagieren.

Es wird empfohlen, dass Sie die Einstellung **Receive email notification service outages or incidents** (E-Mail-Benachrichtigungen bei Dienstausfällen oder Vorfällen erhalten) aktivieren. Sie finden sie in der Gruppe **Hilfe- und Supporteinstellungen**. Weisen Sie mindestens eine _E-Mail-aktivierte_ Sicherheitsgruppe zu.

![Die Einstellung „Receive email notifications for service outages or incidents“ (E-Mail-Benachrichtigungen bei Dienstausfällen oder Vorfällen erhalten) wird angezeigt.](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>Information Protection

Mit Information Protection können Sie Schutzeinstellungen wie die Verschlüsselung oder Wasserzeichen erzwingen, wenn Daten aus dem Power BI-Dienst exportiert werden.

Es gibt zwei Mandanteneinstellungen für Information Protection. Beide Einstellungen sind standardmäßig für die gesamte Organisation deaktiviert.

Es wird empfohlen, dass Sie diese Einstellungen aktivieren, wenn Sie sensible Daten verarbeiten und schützen müssen. Weitere Informationen finden Sie unter [Datenschutz in Power BI (Vorschauversion)](../admin/service-security-data-protection-overview.md).

### <a name="create-workspaces"></a>Erstellen von Arbeitsbereichen

Sie können konfigurieren, dass Benutzer keine Arbeitsbereiche erstellen dürfen. So steuern Sie, was innerhalb Ihrer Organisation erstellt wird.

> [!NOTE]
> Aktuell findet ein Übergang von der alten Benutzeroberfläche für Arbeitsbereiche zur neuen statt. Diese Mandanteneinstellung gilt nur für die neue Benutzeroberfläche.

Die Einstellung **Create workspaces** (Arbeitsbereiche erstellen) ist standardmäßig für die gesamte Organisation aktiviert. Sie finden sie in der Gruppe **Arbeitsbereichseinstellungen**.

Es wird empfohlen, dass Sie mindestens eine Sicherheitsgruppe zuweisen. Diesen Gruppen kann die Berechtigung, Arbeitsbereiche zu erstellen, erteilt _oder verweigert_ werden.

Achten Sie darauf, dass Ihre Benutzer (die nicht zum Erstellen von Arbeitsbereichen berechtigt sind) in Ihrer Dokumentation erfahren, wie sie einen neuen Arbeitsbereich anfordern können.

![Die Einstellung „Arbeitsbereichseinstellungen“ wird angezeigt.](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>Inhalten für externe Benutzer freigeben

Benutzer können Berichte und Dashboards für Personen außerhalb Ihrer Organisation freigeben.

Die Einstellung **Inhalt für externe Benutzer freigeben** ist standardmäßig für die gesamte Organisation aktiviert. Sie finden sie in der Gruppe **Einstellungen für Export und Freigabe**.

Es wird empfohlen, dass Sie mindestens eine Sicherheitsgruppe zuweisen. Diesen Gruppen kann die Berechtigung, Inhalte für externe Benutzer freizugeben, erteilt _oder verweigert_ werden.

![Die Einstellung „Inhalt für externe Benutzer freigeben“ wird angezeigt.](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>Webveröffentlichung

Mit dem Feature [Im Web veröffentlichen](../service-publish-to-web.md) können öffentliche Berichte im Internet veröffentlicht werden. Wenn das Feature unangemessen eingesetzt wird, besteht das Risiko, dass vertrauliche Informationen live im Internet verfügbar gemacht werden.

Die Einstellung **Im Web veröffentlichen** ist zwar standardmäßig für die gesamte Organisation aktiviert, allerdings dürfen Benutzer, die keine Administratoren sind, nur Einbindungscode erstellen. Sie finden sie in der Gruppe **Einstellungen für Export und Freigabe**.

Wenn sie aktiviert ist, wird empfohlen, dass Sie mindestens eine Sicherheitsgruppe zuweisen. Diesen Gruppen kann die Berechtigung, Berichte zu veröffentlichen, erteilt _oder verweigert_ werden.

Außerdem können Sie festlegen, wie Ihr Einbindungscode funktioniert. Die Standardeinstellung ist **Nur vorhandene Codes zulassen**. Das bedeutet, dass Benutzer darum gebeten werden, sich für das Erstellen von Einbindungscode mit einem Power BI-Administrator in Verbindung zu setzen.

![Die Einstellung „Im Web veröffentlichen“ wird angezeigt.](media/admin-tenant-settings/publish-to-web.png)

Es ist außerdem empfehlenswert, dass Sie die [Einbindungscodes für das Feature „Im Web veröffentlichen“](https://app.powerbi.com/admin-portal/embedCodes) regelmäßig überprüfen. Entfernen Sie Code, wenn er zu der Veröffentlichung von privaten oder vertraulichen Informationen führen würde.

### <a name="export-data"></a>Daten exportieren

Sie können festlegen, dass Benutzer keine Daten aus Dashboardkacheln oder Berichtsvisuals exportieren dürfen.

Die Einstellung **Daten exportieren** ist standardmäßig für die gesamte Organisation aktiviert. Sie finden sie in der Gruppe **Einstellungen für Export und Freigabe**.

Es wird empfohlen, dass Sie mindestens eine Sicherheitsgruppe zuweisen. Diesen Gruppen kann die Berechtigung, Berichte zu veröffentlichen, erteilt _oder verweigert_ werden.

> [!IMPORTANT]
> Wenn Sie die Einstellung deaktivieren, wird auch die Verwendung der Features [In Excel analysieren](../service-analyze-in-excel.md) und [Liveverbindung](../desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management) (Power BI-Dienst) eingeschränkt.

![Die Einstellung „Daten exportieren“ wird angezeigt.](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> Wenn Benutzer anderen Benutzern erlauben, Daten zu exportieren, können Sie für mehr Sicherheit sorgen, indem Sie [Datenschutz](../admin/service-security-data-protection-overview.md) erzwingen. Falls konfiguriert, dürfen unautorisierte Benutzer keine als sensibel gekennzeichneten Inhalte exportieren.

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Organisation erlauben

Es ist möglich, dass externe Gastbenutzer Power BI-Inhalte bearbeiten und verwalten können. Weitere Informationen finden Sie unter [Verteilen von Power BI-Inhalten an externe Gastbenutzer mit Azure AD B2B](../service-admin-azure-ad-b2b.md).

Die Einstellung **Externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Organisation erlauben** ist standardmäßig für die gesamte Organisation aktiviert. Sie finden sie in der Gruppe **Einstellungen für Export und Freigabe**.

Wenn Sie externe Benutzer dazu autorisieren müssen, Inhalte zu bearbeiten und zu verwalten, empfiehlt es sich, mindestens eine Sicherheitsgruppe zuzuweisen. Diesen Gruppen kann die Berechtigung, Berichte zu veröffentlichen, erteilt _oder verweigert_ werden.

![Die Einstellung „Externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Organisation erlauben“ wird angezeigt.](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>Entwicklereinstellungen

Es gibt zwei Mandanteneinstellungen für das [Einbetten von Power BI-Inhalten](../developer/embedded/embedding.md). Sie lauten wie folgt:

- Einbetten von Inhalten in Apps (standardmäßig aktiviert)
- Gestatten, dass Dienstprinzipale Power BI-APIs verwenden (standardmäßig deaktiviert)

Wenn Sie nicht vorhaben, mithilfe der Entwickler-APIs Inhalte einzubetten, sollten Sie diese deaktivieren. Andernfalls sollten Sie zumindest bestimmte Sicherheitsgruppen konfigurieren, die dies tun.

![Die Entwicklereinstellungen werden angezeigt.](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>Weitere Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [Was ist die Power BI-Verwaltung?](../service-admin-administering-power-bi-in-your-organization.md)
- [Verwalten von Power BI im Verwaltungsportal](../service-admin-portal.md)
- Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
- Vorschläge? [Einbringen von Ideen zur Verbesserung von Power BI](https://ideas.powerbi.com)
