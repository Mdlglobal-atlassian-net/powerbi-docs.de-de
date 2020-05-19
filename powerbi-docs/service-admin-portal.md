---
title: Power BI-Verwaltungsportal
description: Das Verwaltungsportal ermöglicht die Mandantenverwaltung von Power BI in Ihrer Organisation. Es enthält Elemente wie z. B. Nutzungsmetriken und Zugriff auf das Microsoft 365 Admin Center sowie auf die Einstellungen.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/27/2020
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: c073973b8829209fdd5d2342dcb51b9d08b5dd95
ms.sourcegitcommit: 9dd6dc8c06091ea02dee5e9ddc45a2922877b1f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2020
ms.locfileid: "82991484"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>Verwalten von Power BI im Verwaltungsportal

Mit dem Verwaltungsportal können Sie einen Power BI-*Mandanten* für Ihre Organisation verwalten. Es enthält Elemente wie z. B. Nutzungsmetriken und Zugriff auf das Microsoft 365 Admin Center sowie auf die Einstellungen.

Auf das vollständige Verwaltungsportal können alle Benutzer zugreifen, die globale Administratoren in Office 365 sind oder der Power BI-Dienstadministratorrolle zugewiesen wurden. Wenn Sie keiner dieser Rollen angehören, können Sie im Portal nur die **Kapazitätseinstellungen** anzeigen. Weitere Informationen zur Power BI-Dienstadministratorrolle finden Sie unter [Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md).

## <a name="how-to-get-to-the-admin-portal"></a>Gewusst wie: Anzeigen des Verwaltungsportals

Ihr Konto muss in Office 365 oder Azure Active Directory (Azure AD) als **Globaler Administrator** markiert oder der Rolle „Power BI-Dienstadministrator“ zugewiesen sein, damit Sie Zugriff auf das Power BI-Verwaltungsportal erhalten. Weitere Informationen zur Power BI-Dienstadministratorrolle finden Sie unter [Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md). Führen Sie zum Zugreifen auf das Power BI-Verwaltungsportal die folgenden Schritte aus.

1. Wählen Sie das Zahnradsymbol für die Einstellungen oben rechts im Power BI-Dienst aus.

1. Wählen Sie **Verwaltungsportal** aus.

    ![Einstellungen im Verwaltungsportal](media/service-admin-portal/powerbi-admin-settings.png)

Das Portal umfasst neun Registerkarten. In den verbleibenden Abschnitten dieses Artikels erhalten Sie Informationen zu jeder dieser Registerkarten.

![Navigation im Verwaltungsportal](media/service-admin-portal/powerbi-admin-landing-page.png)

* [Nutzungsmetriken](#usage-metrics)
* [Benutzer](#users)
* [Überwachungsprotokolle](#audit-logs)
* [Mandanteneinstellungen](#tenant-settings)
* [Kapazitätseinstellungen](#capacity-settings)
* [Einbindungscodes](#embed-codes)
* [Visuals für Organisationen](#organizational-visuals)
* [Dataflowspeicher (Vorschau)](#dataflowStorage)
* [Arbeitsbereiche](#workspaces)
* [Benutzerdefiniertes Branding](#custom-branding)

## <a name="usage-metrics"></a>Nutzungsmetriken

Mithilfe der **Nutzungsmetriken** können Sie die Power BI-Nutzung für Ihre Organisation überwachen. Außerdem können Sie darüber feststellen, welche Benutzer und Gruppen in Power BI für Ihre Organisation am aktivsten sind. 

> [!NOTE]
> Beim ersten Zugriff auf das Dashboard oder beim Anzeigen des Dashboards nach einem längeren Zeitraum wird zunächst wahrscheinlich ein Ladebildschirm angezeigt, während das Dashboard geladen wird.

Nachdem das Dashboard geladen wurde, werden zwei Abschnitte mit Kacheln angezeigt. Der erste Abschnitt umfasst Nutzungsdaten für einzelne Benutzer, der zweite Abschnitt enthält ähnliche Informationen für die Gruppen in Ihrer Organisation.

Im Folgenden sehen Sie, was in den einzelnen Kacheln angezeigt wird:

* Anzahl der verschiedenen Dashboards, Berichte und Datasets im Arbeitsbereich eines Benutzers.
  
    ![Anzahl der verschiedenen Dashboards, Berichte, Datasets](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* Das am häufigsten verwendete Dashboard nach Anzahl von Benutzern, die darauf zugreifen können. Wenn Sie z.B. ein Dashboard für drei Benutzer freigegeben und dieses auch einem Inhaltspaket hinzugefügt haben, mit dem zwei weitere Benutzer verbunden sind, beträgt die Anzahl 6 (1 + 3 + 2).
  
    ![Am häufigsten verwendete Dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Der beliebteste Inhalt, mit dem Benutzer Verbindungen herstellen. Dies kann alles sein, worauf Benutzer durch den Vorgang zum Abrufen von Daten zugreifen können, z. B. SaaS-Pakete, organisationsbezogene Inhaltspakete, Dateien oder Datenbanken.
  
    ![Am häufigsten verwendete Pakete](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Eine Ansicht der aktivsten Benutzer basierend auf der Anzahl von Dashboards. Dies können von den Benutzern selbst erstellte Dashboards sein, aber auch Dashboards, die für sie freigegeben wurden.
  
    ![Aktivste Benutzer – Dashboards](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Eine Ansicht der aktivsten Benutzer basierend auf der Anzahl von Berichten.
  
    ![Aktivste Benutzer – Berichte](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

Der zweite Abschnitt zeigt dieselben Informationen basierend auf Gruppen an. So können Sie sehen, welche Gruppen in Ihrer Organisation besonders aktiv sind und welche Art von Inhalten sie verwenden.

Anhand dieser Informationen gewinnen Sie wichtige Erkenntnisse zur Verwendung von Power BI in Ihrer Organisation. Außerdem können Sie ermitteln, welche Benutzer und Gruppen in Ihrer Organisation besonders aktiv sind.

## <a name="control-usage-metrics"></a>Steuern von Nutzungsmetriken

Berichte zu Nutzungsmetriken sind ein Feature, das Power BI- oder Office 365-Administratoren aktivieren oder deaktivieren können. Administratoren können präzise steuern, welche ihrer Benutzer Zugriff auf Nutzungsmetriken haben. Sie sind standardmäßig für alle Benutzer in der Organisation **eingeschaltet**.

Die Administratoren können außerdem entscheiden, ob Inhaltsautoren benutzerspezifische Daten in den Nutzungsmetriken sehen können. 

Details zu den eigentlichen Berichten finden Sie unter [Überwachen von Nutzungsmetriken für Power BI-Dashboards und Berichte](service-usage-metrics.md).

### <a name="usage-metrics-for-content-creators"></a>Nutzungsmetriken für Inhaltsersteller

1. Wählen Sie im Verwaltungsportal **Mandanteneinstellungen** > **Nutzungsmetriken für Inhaltsersteller** aus.

    ![Mandanteneinstellungen für Nutzungsmetriken im Verwaltungsportal](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. Nutzungsmetriken aktivieren (oder deaktivieren) > **Übernehmen**.

    ![Nutzungsmetriken aktiviert](media/service-usage-metrics/power-bi-tenant-settings-updated.png)


### <a name="per-user-data-in-usage-metrics"></a>Benutzerspezifische Daten in Nutzungsmetriken

Die benutzerspezifischen Daten sind standardmäßig für die Nutzungsmetriken aktiviert, und die Kontoinformationen des Inhaltsnutzers sind im Bericht zu den Nutzungsmetriken enthalten. Wenn Sie diese Informationen für einige oder alle Benutzer nicht miteinbeziehen möchten, deaktivieren Sie das Feature für angegebene Sicherheitsgruppen oder eine gesamte Organisation. Die Kontoinformationen werden im Bericht dann als *Unnamed* (Unbenannt) angezeigt.

![Benutzerspezifische Nutzungsdaten](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>Löschen aller vorhandenen Inhalte von Nutzungsmetriken

Beim Deaktivieren von Nutzungsmetriken für die gesamte Organisation können Administratoren darüber hinaus eine oder beide Optionen auswählen:

- **Alle vorhandenen Inhalte von Nutzungsmetriken löschen**, um alle vorhandenen Berichte und Dashboardkacheln zu löschen, die mit den Berichten und Datasets der Nutzungsmetriken erstellt wurden. Durch diese Option wird jeglicher Zugriff auf Nutzungsmetriken für alle Benutzer der Organisation entfernt, die diese möglicherweise bereits nutzen. 
- **Alle vorhandenen benutzerbezogenen Daten im aktuellen Inhalt von Nutzungsmetriken löschen**: Diese Option entfernt den Zugriff auf benutzerspezifische Daten für alle Benutzer in der Organisation, die bereits mit diesen arbeiten. 

Gehen Sie umsichtig vor, da das Löschen vorhandener Nutzungsmetriken und benutzerspezifischen Metriken nicht rückgängig gemacht werden kann.

## <a name="users"></a>Benutzer

Power BI-Benutzer, -Gruppen und -Administratoren verwalten Sie im Microsoft 365 Admin Center. Die Registerkarte **Benutzer** umfasst einen Link zum Admin Center für Ihren Mandanten.

![„Go to Microsoft 365 admin center“ (Microsoft 365 Admin Center aufrufen)](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>Überwachungsprotokolle

Sie verwalten Power BI-Überwachungsprotokolle im Office 365 Security & Compliance Center. Die Registerkarte **Überwachungsprotokolle** umfasst einen Link zum Security & Compliance Center für Ihren Mandanten. [Weitere Informationen](service-admin-auditing.md)

Um Überwachungsprotokolle zu verwenden, stellen Sie sicher, dass die Einstellung [**Überwachungsprotokolle für interne Aktivitätsüberwachung und Compliance erstellen**](#create-audit-logs-for-internal-activity-auditing-and-compliance) aktiviert ist.

## <a name="tenant-settings"></a>Mandanteneinstellungen

Die Registerkarte **Mandanteneinstellungen** ermöglicht eine fein abgestufte Steuerung der Features, die für Ihre Organisation zur Verfügung stehen. Wenn Sie über vertrauliche Daten verfügen, die besonders geschützt werden müssen, sind einige der Features möglicherweise nicht für Ihre Organisation geeignet bzw. bestimmte Funktionen sollten nur für eine bestimme Gruppe bereitgestellt werden.

Die folgende Abbildung zeigt mehrere Einstellungen auf der Registerkarte **Mandanteneinstellungen**.

![Mandanteneinstellungen](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Es kann bis zu zehn Minuten dauern, bis eine Einstellungsänderung für alle Benutzer in Ihrem Mandanten wirksam wird.

Einstellungen können drei Zustände aufweisen:

* **Für die gesamte Organisation deaktiviert:** Keine Person in Ihrer Organisation kann dieses Feature verwenden.

    ![Einstellung für alle deaktiviert](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **Für die gesamte Organisation aktiviert:** Jede Person in Ihrer Organisation kann dieses Feature verwenden.

    ![Einstellung für alle aktiviert](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **Für eine Teilmenge der Organisation aktiviert:** Eine bestimmte Teilmenge der Benutzer oder Gruppen in Ihrer Organisation kann dieses Feature verwenden.

    Sie können das Feature für die gesamte Organisation mit Ausnahme einer bestimmten Gruppe von Benutzern aktivieren.

    ![Einstellung für eine Teilmenge aktiviert](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    Sie können das Feature auch für eine bestimmte Gruppe von Benutzern aktivieren und gleichzeitig für eine Gruppe von Benutzern deaktivieren. So stellen Sie sicher, dass bestimmte Benutzer auch dann keinen Zugriff auf das Feature erhalten, wenn sie Mitglied der Gruppe sind, für die der Zugriff aktiviert ist.

    ![Einstellung mit Ausnahme aktivieren](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

Die nächsten Abschnitte bieten einen Überblick über die verschiedenen Arten von Mandanteneinstellungen.

## <a name="help-and-support-settings"></a>Hilfe- und Supporteinstellungen

### <a name="publish-get-help-information"></a>Informationen zu "Hilfe anfordern" veröffentlichen

Benutzer in der Organisation können über das Hilfemenü von Power BI zur internen Hilfe und zu Supportressourcen gelangen. Insbesondere ändern diese Parameter das Verhalten der Menüelemente „Weitere Informationen“, „Community“ und „Hilfe erhalten“.

Durch die Angabe einer URL für Lizenzanforderungen passen Sie außerdem die Ziel-URL der Schaltfläche **Upgrade für Konto ausführen** an. Benutzer ohne Power BI Pro-Lizenz sehen diese Schaltfläche im Dialogfeld **Update to Power BI Pro (Aktualisierung auf Power BI Pro)** sowie auf der Seite **Persönlichen Speicher verwalten**. Außerdem bietet Power BI nicht mehr die Schaltfläche **Pro kostenlos testen** in diesem Dialogfeld oder auf der Speicherseite an. Dadurch wird sichergestellt, dass Power BI Ihre Benutzer zuverlässig durch die in Ihrer Organisation definierten Prozesse durch Ihre Lizenzverwaltungslösung führt.

![Einstellung mit Ausnahme aktivieren](media/service-admin-portal/powerbi-admin-tenant-settings-gethelp.png)

### <a name="receive-email-notifications-for-service-outages-or-incidents"></a>E-Mail-Benachrichtigungen bei Dienstausfällen oder Incidents

E-Mail-aktivierte Sicherheitsgruppen erhalten E-Mail-Benachrichtigungen, wenn dieser Mandant von einem Dienstausfall oder einem Incident betroffen ist. Weitere Informationen finden Sie unter [Dienstunterbrechungsbenachrichtigungen](service-interruption-notifications.md).

## <a name="workspace-settings"></a>Arbeitsbereichseinstellungen

Im Verwaltungsportal gibt es in **Mandanteneinstellungen** zwei Abschnitte zum Steuern von Arbeitsbereichen:

- Neue Arbeitsbereichsoberfläche erstellen
- Datasets arbeitsbereichsübergreifend verwenden

### <a name="create-the-new-workspaces"></a>Erstellen neuer Arbeitsbereiche

In Arbeitsbereichen können Benutzer gemeinsam an Dashboards, Berichten und anderen Inhalten arbeiten. Administratoren geben mit der Einstellung **Arbeitsbereiche erstellen (neue Arbeitsbereichsoberfläche)** an, welche Benutzer in der Organisation Arbeitsbereiche erstellen können. Administratoren können zulassen, dass alle oder keine Benutzer in einer Organisation neue Arbeitsbereichsoberflächen erstellen. Sie können auch die Erstellung von Mitgliedern bestimmter Sicherheitsgruppen beschränken. Erfahren Sie mehr über [Arbeitsbereiche](service-new-workspaces.md).

:::image type="content" source="media/service-admin-portal/power-bi-admin-workspace-settings.png" alt-text="Neue Arbeitsbereichsoberflächen erstellen":::

Für klassische Arbeitsbereiche auf Grundlage von Office 365-Gruppen wird die Verwaltung weiterhin im Office 365-Verwaltungsportal und Azure Active Directory durchgeführt.

> [!NOTE]
> Standardmäßig erlaubt die Einstellung **Arbeitsbereiche erstellen (neue Arbeitsbereichsoberfläche)** nur Benutzern, die Office 365-Gruppen erstellen können, das Erstellen der neuen Power BI-Arbeitsbereiche. Achten Sie darauf, dass Sie im Power BI-Verwaltungsportal einen Wert festlegen, um sicherzustellen, dass die gewünschten Benutzer diese erstellen können.

**Liste mit Arbeitsbereichen**

Das Verwaltungsportal hat einen weiteren Abschnitt mit Einstellungen zu den Arbeitsbereichen Ihres Mandanten. In diesem Abschnitt können Sie die Liste der Arbeitsbereiche sortieren und filtern und die Details zu jedem Arbeitsbereich anzeigen. Weitere Informationen finden Sie in diesem Artikel unter [Arbeitsbereiche](#workspaces).

**Inhaltspakete und Apps veröffentlichen**

Im Verwaltungsportal steuern Sie auch, welche Benutzer über Berechtigungen zum Verteilen von Apps für die Organisation verfügen. Nähere Informationen finden Sie in diesem Artikel unter [Inhaltspakete und Apps für die gesamte Organisation veröffentlichen](#publish-content-packs-and-apps-to-the-entire-organization).

### <a name="use-datasets-across-workspaces"></a>Datasets arbeitsbereichsübergreifend verwenden

Administratoren können steuern, welche Benutzer in der Organisation Datasets in verschiedenen Arbeitsbereichen verwenden dürfen. Wenn diese Einstellung aktiviert ist, benötigen Benutzer immer noch die erforderliche Berechtigung „Erstellen“ für ein bestimmtes Dataset.

:::image type="content" source="media/service-admin-portal/power-bi-admin-datasets-workspaces.png" alt-text="Datasets arbeitsbereichsübergreifend verwenden":::

Weitere Informationen finden Sie unter [Einführung in die Verwendung von Datasets in mehreren Arbeitsbereichen](service-datasets-across-workspaces.md).


## <a name="export-and-sharing-settings"></a>Einstellungen für Export und Freigabe

### <a name="share-content-with-external-users"></a>Inhalt für externe Benutzer freigeben

Benutzer in der Organisation können Dashboards, Berichte und Apps für Benutzer außerhalb der Organisation freigeben. Erfahren Sie mehr über die [externe Freigabe](service-share-dashboards.md#share-a-dashboard-or-report-outside-your-organization).

![Einstellung für externe Benutzer](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

Die folgende Abbildung zeigt die Meldung, die bei der Freigabe für einen externen Benutzer angezeigt wird.

![Freigabe für externen Benutzer](media/service-admin-portal/powerbi-admin-sharing-external.png)  

> [!IMPORTANT]
> Diese Option steuert, ob Benutzer in Power BI externe Benutzer über Power BI einladen können, Azure Active Directory B2B- Gastbenutzer (Azure AD B2B) in Ihrer Organisation zu werden. Falls aktiviert, können Benutzer, die in Azure AD die Rolle „Gasteinladender“ haben, externe E-Mail-Adressen hinzufügen, wenn sie Berichte, Dashboards und Power BI-Apps freigeben. Der externe Empfänger wird eingeladen, Ihrer Organisation als Azure AD B2B-Gastbenutzer beizutreten. Wichtig ist, dass bei Deaktivieren dieser Einstellung externe Benutzer, die bereits Azure AD B2B-Gastbenutzer in Ihrer Organisation sind, weiterhin auf den Benutzeroberflächen zur Personenauswahl in Power BI angezeigt werden und Zugriff auf Elemente, Arbeitsbereiche und Apps erhalten können.

### <a name="publish-to-web"></a>Im Web veröffentlichen

Als Administrator für einen Power BI-Mandanten verfügen Sie über die Einstellung **Im Web veröffentlichen** über Optionen, für die Benutzer Einbindungscode zum Veröffentlichen von Berichten im Web erstellen können. Diese Funktionalität stellt den Bericht und die enthaltenen Daten für jeden im Web zur Verfügung. Weitere Informationen finden Sie unter [Veröffentlichen im Web](service-publish-to-web.md).

> [!NOTE]
> Nur Power BI-Administratoren können das Erstellen neuer Einbindungscodes für die Veröffentlichung im Web erlauben. Organisationen verfügen möglicherweise bereits über Einbindungscodes. Im Abschnitt [Einbindungscodes](service-admin-portal.md#embed-codes) des Verwaltungsportals können Sie die derzeit veröffentlichten Berichte einsehen.

Die folgende Abbildung zeigt das Menü **Weitere Optionen** für einen Bericht an, wenn die Einstellung **Im Web veröffentlichen** aktiviert ist.

![Einstellung „Im Web veröffentlichen“ im Menü „Weitere Optionen“](media/service-admin-portal/power-bi-more-options-publish-web.png)

Die Einstellung **Im Web veröffentlichen** im Verwaltungsportal stellt Optionen bereit, für die Benutzer Einbindungscodes erstellen können.

![Einstellung „Im Web veröffentlichen“](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Administratoren können **Im Web veröffentlichen** auf **Aktiviert** und **Funktionsweise von Einbindungscodes auswählen** auf **Nur vorhandene Codes zulassen** festlegen. In diesem Fall können Benutzer Einbindungscodes erstellen, aber sie müssen den Power BI-Administrator kontaktieren, damit dieser dies erlaubt.

![„Im Web veröffentlichen“-Aufforderung](media/service-publish-to-web/publish_to_web_admin_prompt.png)

Den Benutzer werden basierend auf der Einstellung **Im Web veröffentlichen** unterschiedliche Optionen in der Benutzeroberfläche angezeigt.

|Feature |Für die gesamte Organisation aktiviert |Für die gesamte Organisation deaktiviert |Sicherheitsgruppen angeben   |
|---------|---------|---------|---------|
|**Im Web veröffentlichen** im Menü **Weitere Optionen** des Berichts|Für alle aktiviert|Nicht für alle sichtbar|Nur für autorisierte Benutzer oder Gruppen sichtbar|
|**Einbindungscodes verwalten** unter **Einstellungen**|Für alle aktiviert|Für alle aktiviert|Für alle aktiviert<br><br>Option * **Löschen** nur für autorisierte Benutzer oder Gruppen<br>* **Codes abrufen** für alle aktiviert|
|**Einbindungscodes** im Verwaltungsportal|Es wird einer der folgenden Statuswerte angezeigt:<br>* Aktiv<br>* Nicht unterstützt<br>* Blockiert|Angezeigter Status **Deaktiviert**|Es wird einer der folgenden Statuswerte angezeigt:<br>* Aktiv<br>* Nicht unterstützt<br>* Blockiert<br><br>Wenn ein Benutzer gemäß den Mandanteneinstellungen nicht autorisiert ist, wird der Status **Verletzt** angezeigt.|
|Vorhandene veröffentlichte Berichte|Alle aktiviert|Alle deaktiviert|Berichte werden weiterhin für alle gerendert.|

### <a name="export-data"></a>Daten exportieren

Benutzer in der Organisation können Daten aus einer Kachel oder Visualisierung exportieren. Dadurch werden die Features „In Excel analysieren“, „In CSV exportieren“, Datasetdownloads (PBIX) und „Live Connect“ des Power BI-Diensts gesteuert. Informieren Sie sich über das [Exportieren der Daten, die zum Erstellen einer Visualisierung verwendet wurden](visuals/power-bi-visualization-export-data.md).

>[!NOTE]
> Vor der Einführung der Einstellung „Nach Excel exportieren“ wurde von dieser Einstellung auch das Exportieren von Daten in Excel-Dateien gesteuert. Weitere Informationen finden Sie im [Hinweis unter dem Abschnitt zu „Nach Excel exportieren“](#export-to-excel).

![Dateneinstellungen exportieren](media/service-admin-portal/powerbi-admin-portal-export-data-setting.png)

Die folgende Abbildung zeigt die Option zum Exportieren von Daten aus einer Kachel.

![Exportieren von Daten aus einer Kachel](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Durch das Deaktivieren von **Daten exportieren** wird zudem verhindert, dass Benutzer das Feature [In Excel analysieren](service-analyze-in-excel.md) sowie die Liveverbindung des Power BI-Diensts verwenden können.

### <a name="export-to-excel"></a>Nach Excel exportieren

Benutzer in der Organisation können die Daten aus einer Visualisierung in eine Excel-Datei exportieren.

![Einstellung „Nach Excel exportieren“](media/service-admin-portal/powerbi-admin-portal-export-to-excel-setting.png)

>[!IMPORTANT]
> Vor der Einführung der Einstellung „Nach Excel exportieren“ wurde der Export in eine Excel-Datei durch die Einstellung „Daten exportieren“ gesteuert. Deshalb werden Mandantenadministratoren für Mandanten, die schon vor der Einführung der Einstellung „Nach Excel exportieren“ vorhanden waren, auch *Nicht übernommene Änderungen* bei Betrachtung der Einstellung „Nach Excel exportieren“ angezeigt. Sie müssen diese Änderungen anwenden, damit die neue Einstellung wirksam wird. Andernfalls wird der Export in eine Excel-Datei weiterhin von der Einstellung „Daten exportieren“ gesteuert.

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>Exportieren von Berichten als PowerPoint-Präsentationen oder PDF-Dokumente

Benutzer in der Organisation können Power BI-Berichte als PowerPoint-Dateien oder PDF-Dokumente exportieren. [Weitere Informationen](consumer/end-user-powerpoint.md)

In der folgenden Abbildung wird das Menü **Datei** für einen Bericht gezeigt, wenn die Einstellung **Berichte als PowerPoint-Präsentationen oder PDF-Dokumente exportieren** aktiviert ist.

![Berichte als PowerPoint-Präsentationen exportieren](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Dashboards und Berichte drucken

Benutzer in der Organisation können Dashboards und Berichte drucken. [Weitere Informationen](consumer/end-user-print.md)

Die folgende Abbildung zeigt die Option zum Drucken eines Dashboards.

![Dashboard drucken](media/service-admin-portal/powerbi-admin-print-dashboard.png)

Die folgende Abbildung zeigt das Menü **Datei** für einen Bericht, wenn die Einstellung **Dashboards und Berichte drucken** aktiviert ist.

![Bericht drucken](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>Externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Organisation erlauben

Azure AD-B2B-Gastbenutzer können Inhalte in der Organisation bearbeiten und verwalten. [Weitere Informationen](service-admin-azure-ad-b2b.md)

In der folgenden Abbildung wird die Option „Allow external guest users to edit and manage content in the organization“ (Externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Organisation erlauben) angezeigt.

![Externen Gastbenutzern das Bearbeiten und Verwalten von Inhalten in der Organisation erlauben](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

Im Verwaltungsportal steuern Sie auch, welche Benutzer über Berechtigungen zum Einladen externer Benutzer zur Organisation verfügen. Details finden Sie in diesem Artikel unter [Inhalt für externe Benutzer freigeben](#export-and-sharing-settings).

### <a name="email-subscriptions"></a>E-Mail-Abonnements
Benutzer in der Organisation können E-Mail-Abonnements erstellen und verwenden. Erfahren Sie mehr über [Abonnements](service-report-subscribe.md).

![Aktivieren von E-Mail-Abonnements](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

### <a name="featured-content"></a>Empfohlene Inhalte

Sie können einigen oder allen Berichterstellern in Ihrer Organisation erlauben, ihre Inhalte im Bereich „Empfohlen“ auf der Power BI-Startseite anzuzeigen. Neuen Benutzern werden die empfohlenen Inhalte oben auf ihrer Power BI-Startseite angezeigt. Wenn Benutzer **Favoriten**, **Häufig aufgerufen** und **Zuletzt geöffnet** hinzufügen, werden die empfohlenen Inhalte auf der Startseite weiter unten angezeigt. 

Es empfiehlt sich, zunächst nur wenigen Personen diese Möglichkeit zu geben. Wenn alle Mitglieder einer Organisation Inhalte auf der Startseite anzeigen können, wird es schwierig, den Überblick über die empfohlenen Inhalte zu bewahren. 

Nachdem Sie empfohlene Inhalte aktiviert haben, können Sie sie im Verwaltungsportal verwalten. Im Abschnitt [Verwalten empfohlener Inhalte](#manage-featured-content) dieses Artikels finden Sie weitere Informationen zum Verwalten empfohlener Inhalte in Ihrer Domäne.

## <a name="content-pack-and-app-settings"></a>Einstellungen für das Inhaltspaket und die App

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>Inhaltspakete und Apps für die gesamte Organisation veröffentlichen

Administratoren legen mit dieser Einstellung fest, welche Benutzer Inhaltspakete und Apps für die gesamte Organisation veröffentlichen können, nicht nur für bestimmte Gruppen. Erfahren Sie mehr über das [Veröffentlichen von Apps](service-create-distribute-apps.md).

Die folgende Abbildung zeigt die Option **Meine gesamte Organisation** beim Erstellen eines Inhaltspakets.

![Veröffentlichen von Inhaltspaketen für die Organisation](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>Erstellen von Vorlagen-Apps und Organisationsinhaltspaketen

Benutzer in der Organisation können Vorlagen-Apps und Organisationsinhaltspakete erstellen, die Datasets verwenden, die auf einer Datenquelle in Power BI Desktop basieren. Weitere Informationen finden Sie unter [Vorlagen-Apps](template-content-pack-authoring.md).

### <a name="push-apps-to-end-users"></a>Apps mithilfe von Push an Endbenutzer übertragen

Berichtersteller können Apps direkt und ohne Installation aus [AppSource](https://appsource.microsoft.com) für Endbenutzer freigeben. Erfahren Sie mehr über [automatisches Installieren von Apps für Endbenutzer](service-create-distribute-apps.md#automatically-install-apps-for-end-users).

## <a name="integration-settings"></a>Integrationseinstellungen

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Verwenden von In Excel analysieren mit lokalen Datasets

Benutzer in der Organisation können Excel verwenden, um lokale Power BI-Datasets anzuzeigen und mit ihnen zu interagieren. [Weitere Informationen](service-analyze-in-excel.md)

> [!NOTE]
> Durch das Deaktivieren von **Daten exportieren** wird außerdem verhindert, dass Benutzer das Feature **In Excel analysieren** verwenden.

### <a name="use-arcgis-maps-for-power-bi"></a>ArcGIS Maps for Power BI verwenden

Benutzer in der Organisation können die Visualisierung ArcGIS Maps for Power BI von Esri verwenden. [Weitere Informationen](visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Verwenden der globalen Suche für Power BI (Vorschau)

Benutzer in der Organisation können externe Suchfeatures verwenden, die auf Azure Search basieren.

## <a name="power-bi-visuals-settings"></a>Einstellungen für Power BI-Visuals

### <a name="add-and-use-power-bi-visuals"></a>Hinzufügen und Verwenden von Power BI-Visuals

Benutzer in der Organisation können mit Power BI-Visuals interagieren und diese freigeben. [Weitere Informationen](developer/visuals/power-bi-custom-visuals.md)

> [!NOTE]
> Diese Einstellung kann für die gesamte Organisation gelten oder auf bestimmte Gruppen beschränkt werden.

Power BI Desktop unterstützt (ab der Version von März 2019) die Verwendung des Tools **Gruppenrichtlinie**, um die Verwendung von Power BI-Visuals auf allen in einer Organisation bereitgestellten Computern zu deaktivieren.

<table>
<tr><th>Attribut</th><th>Wert</th>
</tr>
<td>Schlüssel</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

Mit dem Wert 1 (dezimal) wird die Verwendung von Power BI-Visuals in Power BI aktiviert (Standardeinstellung).

Mit dem Wert 0 (dezimal) wird die Verwendung von Power BI-Visuals in Power BI deaktiviert.

### <a name="allow-only-certified-visuals"></a>Ausschließlich zertifizierte Visuals zulassen

Benutzer in der Organisation, denen Berechtigungen zum Hinzufügen und Verwenden von Power BI-Visuals gewährt wurden (gekennzeichnet durch die Einstellung „Power BI-Visuals hinzufügen und verwenden“), können nur [zertifizierte Power BI-Visuals](https://go.microsoft.com/fwlink/?linkid=2002010) verwenden (nicht zertifizierte Visuals werden blockiert, und es wird eine Fehlermeldung angezeigt, wenn diese verwendet werden). 


Power BI Desktop unterstützt (ab der Version von März 2019) die Verwendung des Tools **Gruppenrichtlinie**, um die Verwendung von nicht zertifizierten Power BI-Visuals auf allen in einer Organisation bereitgestellten Computern zu deaktivieren.

<table>
<tr><th>Attribut</th><th>Wert</th>
</tr>
<td>Schlüssel</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

Mit dem Wert 1 (dezimal) wird die Verwendung von nicht zertifizierten Power BI-Visuals in Power BI aktiviert (Standardeinstellung).

Mit dem Wert 0 (dezimal) wird die Verwendung von nicht zertifizierten Power BI-Visuals in Power BI deaktiviert. Diese Option aktiviert nur die Verwendung von [zertifizierten Power BI-Visuals](https://go.microsoft.com/fwlink/?linkid=2002010).

## <a name="r-visuals-settings"></a>Einstellungen für R-Visualisierungen

### <a name="interact-with-and-share-r-visuals"></a>Mit visuellen R-Elementen interagieren und diese freigeben

Benutzer in der Organisation können mit visuellen Elementen, die mit R-Skripts erstellt wurden, interagieren und diese freigeben. [Weitere Informationen](visuals/service-r-visuals.md)

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

## <a name="audit-and-usage-settings"></a>Überwachungs- und Nutzungseinstellungen

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Überwachungsprotokolle für interne Aktivitätsüberwachung und Compliance erstellen

Benutzer in der Organisation können Aktionen überwachen, die in Power BI von anderen Benutzern in der Organisation ausgeführt werden. [Weitere Informationen](service-admin-auditing.md)

Diese Einstellung muss aktiviert sein, damit Überwachungsprotokolleinträge aufgezeichnet werden. Es kann bis zu 48 Stunden nach der Aktivierung der Überwachung dauern, bis Sie Überwachungsdaten einsehen können. Wenn Sie nicht umgehend Daten sehen, überprüfen Sie die Überwachungsprotokolle später noch einmal. Es kann zu einer ähnlichen Verzögerung kommen, nachdem Ihnen die Leseberechtigung für Überwachungsprotokolle erteilt wurde und bis Sie die Protokolle ansehen können.

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

### <a name="usage-metrics-for-content-creators"></a>Nutzungsmetriken für Inhaltsersteller

Benutzer in der Organisation können Nutzungsmetriken für von ihnen erstellte Dashboards und Berichte anzeigen. [Weitere Informationen](service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>Benutzerspezifische Daten in Nutzungsmetriken für Inhaltsersteller

Nutzungsmetriken für Inhaltsersteller machen Anzeigenamen und E-Mail-Adressen von Benutzern verfügbar, die auf Inhalte zugreifen. [Weitere Informationen](service-usage-metrics.md)

Die benutzerspezifischen Daten sind standardmäßig für die Nutzungsmetriken aktiviert, und die Kontoinformationen vom Ersteller des Inhalts sind im Bericht zu den Nutzungsmetriken enthalten. Wenn Sie diese Informationen nicht für alle Benutzer sammeln möchten, können Sie das Feature für angegebene Sicherheitsgruppen oder eine gesamte Organisation deaktivieren. Die Kontoinformationen für ausgeschlossene Benutzer werden im Bericht dann als *Unnamed* (Unbenannt) angezeigt.

## <a name="dashboard-settings"></a>Dashboardeinstellungen

### <a name="data-classification-for-dashboards"></a>Datenklassifizierung für Dashboards

Benutzer in der Organisation können Dashboards mit Klassifizierungen markieren, die Dashboardsicherheitsstufen angeben. [Weitere Informationen](service-data-classification.md)

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

## <a name="developer-settings"></a>Entwicklereinstellungen

### <a name="embed-content-in-apps"></a>Inhalt in Apps einbetten

Benutzer in der Organisation können Power BI-Dashboards und -Berichte in SaaS-Anwendungen (Software as a Service) einbetten. Ist diese Einstellung deaktiviert, können Benutzer die REST-APIs nicht dazu verwenden, um Power BI-Inhalt in ihre Anwendungen einzubetten. [Weitere Informationen](developer/embedded/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Dienstprinzipalen die Verwendung von Power BI-APIs gestatten

In Azure Active Directory (Azure AD) registrierte Web-Apps verwenden einen zugewiesenen Dienstprinzipal, um ohne angemeldeten Benutzer auf Power BI-APIs zuzugreifen. Damit eine App die Dienstprinzipalauthentifizierung verwenden kann, muss der entsprechende Dienstprinzipal in einer zugelassenen Sicherheitsgruppe enthalten sein. [Weitere Informationen](developer/embedded/embed-service-principal.md)

> [!NOTE]
> Dienstprinzipale erben die Berechtigungen für alle Power BI-Mandanteneinstellungen von ihrer Sicherheitsgruppe. Wenn Berechtigungen eingeschränkt werden sollen, erstellen Sie eine dedizierte Sicherheitsgruppe für Dienstprinzipale und fügen diese der Liste „Ausgenommen spezifische Sicherheitsgruppen“ für die relevanten, aktivierten Power BI-Einstellungen hinzu.

## <a name="dataflow-settings"></a>Datafloweinstellungen

### <a name="create-and-use-dataflows"></a>Erstellen und Verwenden von Dataflows

Benutzer in der Organisation können Dataflows erstellen und verwenden. Weitere Informationen zu Dataflows finden Sie unter [Self-Service-Datenaufbereitung in Power BI](service-dataflows-overview.md). Informationen zum Aktivieren von Dataflows in einer Premium-Kapazität finden Sie im Abschnitt „Konfigurieren von Workloads“ unter [Verwalten von Kapazitäten in Power BI Premium und Power BI Embedded](service-admin-premium-workloads.md).

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

## <a name="template-apps-settings"></a>Einstellungen für Vorlagen-Apps

Drei Einstellungen steuern die Fähigkeit von Vorlagen-Apps zum Veröffentlichen oder Installieren von Vorlagen-Apps.

![Einstellungen für Vorlagen-Apps im Power BI-Verwaltungsportal](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>Veröffentlichen von Vorlagen-Apps

Benutzer in der Organisation können Arbeitsbereiche für Vorlagen-Apps erstellen. Steuern Sie, welche Benutzer Vorlagen-Apps veröffentlichen oder sie über [AppSource](https://appsource.microsoft.com) oder andere Verteilungsmethoden an Clients außerhalb Ihrer Organisation verteilen können.

![Vorlagen-App-Einstellung im Power BI-Verwaltungsportal erstellen](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>Installieren von Vorlagen-Apps auf AppSource

Benutzer in der Organisation können Vorlagen-Apps **nur** über [AppSource](https://appsource.microsoft.com) herunterladen und installieren. Steuern Sie, welche Benutzer oder Sicherheitsgruppen Vorlagen-Apps über AppSource installieren können.

![Power BI-Verwaltungsportal, Installieren der Vorlagen-Apps-Einstellung](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>Installieren von Vorlagen-Apps, die nicht auf AppSource aufgelistet sind

Steuern Sie, welche Benutzer in der Organisation **nicht auf [AppSource](https://appsource.microsoft.com) aufgelistete** Vorlagen-Apps herunterladen und installieren können.

![Power BI-Verwaltungsportal, Installieren der Vorlagen-Apps-Einstellung](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>Kapazitätseinstellungen

### <a name="power-bi-premium"></a>Power BI Premium

Über die Registerkarte **Power BI Premium** können Sie jede Power BI Premium-Kapazität (EM- oder P-SKU) verwalten, die für Ihre Organisation erworben wurde. Alle Benutzer in Ihrer Organisation sehen die Registerkarte **Power BI Premium**, können deren Inhalt aber nur anzeigen, wenn sie entweder als *Kapazitätsadministrator* oder als Benutzer mit Zuweisungsberechtigungen konfiguriert sind. Hat ein Benutzer keine Berechtigungen, wird die folgende Meldung angezeigt.

![Kein Zugriff auf Premium-Einstellungen](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

Auf der Registerkarte **Power BI Embedded** können Sie die Power BI Embedded-Kapazitäten (A-SKU) anzeigen, die Sie für Ihren Kunden erworben haben. Da es nur möglich ist, A-SKUs von Azure zu erwerben, können Sie [verwaltete Embedded-Kapazitäten in Azure](developer/embedded/azure-pbie-create-capacity.md) über das **Azure-Portal** verwalten.

Weitere Informationen zum Verwalten von Power BI Embedded-Einstellungen (A-SKU) finden Sie unter [Was ist Power BI Embedded?](developer/embedded/azure-pbie-what-is-power-bi-embedded.md).

## <a name="embed-codes"></a>Einbindungscodes

Als Administrator können Sie die Einbindungscodes anzeigen, die für Ihren Mandanten generiert werden, um Berichte öffentlich zu teilen. Sie können Codes auch widerrufen oder löschen. [Weitere Informationen](service-publish-to-web.md)

![Einbindungscodes innerhalb des Power BI-Verwaltungsportals](media/service-admin-portal/embed-codes.png)

 ## <a name=""></a><a name="organizational-visuals">Visuals für Organisationen</a> 

Auf der Registerkarte **Organisationsvisuals** können Sie Power BI-Visuals in Ihrer Organisation bereitstellen und verwalten. Mit Organisationsvisuals können Sie ganz einfach proprietäre Visuals in Ihrer Organisation bereitstellen. Berichtsautoren können diese Visuals dann erkunden und in ihre Berichte in Power BI Desktop importieren. [Weitere Informationen](developer/visuals/power-bi-custom-visuals-organization.md)

> [!WARNING]
> Ein benutzerdefiniertes Visual kann Code mit Sicherheits- oder Datenschutzrisiken enthalten. Stellen Sie sicher, dass Sie dem Autor und der Quelle des benutzerdefinierten Visuals vertrauen können, bevor Sie dieses im Repository der Organisation bereitstellen.

Die folgende Abbildung zeigt alle Power BI-Visuals, die derzeit im Repository der Organisation bereitgestellt sind.

![Verwalten von Organisationsvisuals](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>Hinzufügen eines neuen benutzerdefinierten Visuals

Um der Liste ein neues benutzerdefiniertes Visual hinzufügen, führen Sie die folgenden Schritte aus. 

1. Wählen Sie auf der rechten Seite den Eintrag **Benutzerdefiniertes Visual hinzufügen**.

    ![Formular zu Power BI-Visuals](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. Füllen Sie das Formular **Benutzerdefiniertes Visual hinzufügen** aus:

    * **PBIVIZ-Datei auswählen** (erforderlich): Wählen Sie eine benutzerdefinierte Visualdatei zum Hochladen aus. Nur Power BI-Visuals mit API-Versionsangabe werden unterstützt (lesen Sie hier nach, was dies bedeutet).

    Bevor Sie ein benutzerdefiniertes Visual hochladen, sollten Sie dieses auf Sicherheit und Datenschutz überprüfen, um sicherzustellen, dass das Visual die Standards Ihrer Organisation erfüllt.

    * **Benutzerdefiniertes Visual benennen** (erforderlich): Geben Sie dem Visual einen kurzen Titel, damit die Benutzer von Power BI Desktop den Zweck leichter nachvollziehen können.

    * **Symbol:** Die Symboldatei, die auf der Benutzeroberfläche von Power BI Desktop angezeigt wird.

    * **Beschreibung**: Eine kurze Beschreibung des Visuals, um den Benutzern zusätzlichen Kontext bereitzustellen

1. Klicken Sie auf **Hinzufügen**, um die Uploadanforderung zu initiieren. Wenn der Upload erfolgreich ist, wird das neue Element in der Liste angezeigt. Ist der Vorgang nicht erfolgreich, erhalten Sie eine entsprechende Fehlermeldung.

### <a name="delete-a-custom-visual-from-the-list"></a>Löschen eines benutzerdefinierten Visuals aus der Liste

Klicken Sie im Repository beim Visual auf das Papierkorbsymbol, um das Visual dauerhaft zu löschen.

> [!IMPORTANT]
> Der Löschvorgang ist nicht umkehrbar. Sobald das Visual gelöscht wurde, wird es in vorhandenen Berichten nicht mehr gerendert. Selbst wenn Sie das gleiche Visual erneut hochladen, ersetzt es nicht das vorherige Visual, das gelöscht wurde. Benutzer können jedoch das neue Visual erneut importieren und die Instanz in ihren Berichten ersetzen.

### <a name="disable-a-custom-visual-in-the-list"></a>Deaktivieren eines benutzerdefinierten Visuals in der Liste

Um das Visual im Organisationsspeicher zu deaktivieren, wählen Sie das Zahnradsymbol aus. Deaktivieren Sie das benutzerdefinierte Visual im Abschnitt **Zugriff**.

Nachdem Sie das Visual deaktiviert haben, wird es in vorhandenen Berichten nicht mehr gerendert, und es wird die nachstehende Fehlermeldung angezeigt.

*Dieses benutzerdefinierte Visual ist nicht mehr verfügbar. Wenden Sie sich an Ihren Administrator, um Einzelheiten zu erfahren.*

Visuals, für die ein Lesezeichen festgelegt wurde, funktionieren jedoch weiterhin.

Power BI Desktop-Benutzer müssen die Anwendung nach einem Update oder einer Administratoränderung neu starten oder den Browser im Power BI-Dienst aktualisieren, um die Aktualisierungen anzuzeigen.

### <a name="update-a-visual"></a>Aktualisieren eines Visuals

Um das Visual im Store der Organisation zu aktualisieren, wählen Sie das Zahnradsymbol aus. Suchen Sie nach einer neuen Version des Visuals, und laden Sie diese hoch.

Stellen Sie sicher, dass die Visual-ID unverändert bleibt. Die neue Datei ersetzt die vorherige Datei für alle Berichte in der gesamten Organisation. Wenn jedoch die neue Version des Visuals irgendeine Verwendung oder Datenstruktur der vorherigen Version des Visuals beeinträchtigen könnte, ersetzen Sie die vorherige Version nicht. Stattdessen sollten Sie einen neuen Eintrag für die neue Version des Visuals erstellen. Fügen Sie beispielsweise eine neue Versionsnummer (Version X.X) zum Titel des neuen gelisteten Visuals hinzu. Auf diese Weise wird deutlich, dass es sich nur um das gleiche Visual mit einer aktualisierten Versionsnummer handelt, sodass die Funktionalität bestehender Berichte nicht beeinträchtigt wird. Stellen Sie erneut sicher, dass die Visual-ID unverändert bleibt. Wenn die Benutzer das Repository der Organisation das nächste Mal über Power BI Desktop verwenden, können sie die neue Version importieren. Sie werden in diesem Fall aufgefordert, die aktuelle Version zu ersetzen, die sich im Bericht befindet.

Weitere Informationen finden Sie in den [häufig gestellten Fragen zu Power BI-Organisationsvisuals](developer/visuals/power-bi-custom-visuals-faq.md#organizational-power-bi-visuals).

## <a name=""></a><a name="dataflowStorage">Dataflowspeicher (Vorschau)</a>

Mit Power BI verwendete Daten werden standardmäßig im internen Speicher von Power BI gespeichert. Mit der Integration von Dataflows und Azure Data Lake Storage Gen2 (ADLS Gen2) können Sie Ihre Dataflows im Azure Data Lake Storage Gen2-Konto Ihrer Organisation speichern. Weitere Informationen finden Sie unter [Dataflows und Azure Data Lake-Integration (Vorschauversion)](service-dataflows-azure-data-lake-integration.md).

## <a name="workspaces"></a>Arbeitsbereiche

Als Administrator können Sie die Arbeitsbereiche anzeigen, die in Ihrem Mandanten vorhanden sind. Sie können die Liste der Arbeitsbereiche sortieren und filtern und die Details zu jedem Arbeitsbereich anzeigen. Die Tabellenspalten entsprechen den von der [Power BI Admin-Rest-API](/rest/api/power-bi/admin) für Arbeitsbereiche zurückgegebenen Eigenschaften. Persönliche Arbeitsbereiche sind vom Typ **PersonalGroup**, klassische Arbeitsbereiche vom Typ **Group** und moderne Arbeitsbereiche vom Typ **Workspace**. Weitere Informationen finden Sie unter [Organisieren der Arbeit in den neuen Arbeitsbereichen](service-new-workspaces.md).

Administratoren können Arbeitsbereiche auch mithilfe des Verwaltungsportals oder von PowerShell-Cmdlets verwalten und wiederherstellen. 

![Liste der Arbeitsbereiche](media/service-admin-portal/workspaces-list.png)

Auf der Registerkarte **Arbeitsbereiche** sehen Sie den *Status* für jeden Arbeitsbereich. In der folgenden Tabelle finden Sie weitere Informationen zur Bedeutung dieser Status.

|Staat  |Beschreibung  |
|---------|---------|
| Aktiv | Ein normaler Arbeitsbereich. Es zeigt nichts über die Verwendung an oder das, was sich darin befindet, sondern nur, dass der Arbeitsbereich selbst „normal“ ist. |
| Verwaist | Ein Arbeitsbereich ohne Administratorbenutzer. |
| Gelöscht | Ein gelöschter Arbeitsbereich. Wir pflegen genügend Metadaten, um den Arbeitsbereich auf Wunsch für zu 90 Tage wiederherzustellen. |
| Wird entfernt | Ein Arbeitsbereich, der gerade gelöscht wird, aber noch vorhanden ist. Benutzer können ihre eigenen Arbeitsbereiche löschen, indem sie Dinge in „Entfernen“ und schließlich in „Gelöscht“ verschieben. |

## <a name="custom-branding"></a>Benutzerdefiniertes Branding

Als Administrator können Sie das Aussehen von Power BI für Ihre gesamte Organisation anpassen. Derzeit gibt es drei Hauptoptionen:

![Benutzerdefinierte Brandingoptionen](media/service-admin-portal/power-bi-custom-branding.png)

* **Logo hochladen**: Laden Sie für optimale Ergebnisse ein Logo hoch, das als PNG-Datei gespeichert ist, eine Größe von 10 KB oder weniger und mindestens 200 x 30 Pixel aufweist.

* **Coverbild hochladen**: Laden Sie für optimale Ergebnisse ein Coverbild hoch, das als JPG- oder PNG-Datei gespeichert ist, eine Größe von 1 MB oder weniger und mindestens 1920 x 160 Pixel aufweist.

* **Designfarbe auswählen**: Sie können Ihr Design als Hexadezimalzahl oder RGB-Wert angeben oder es aus der integrierten Palette auswählen.


Weitere Informationen finden Sie unter [Benutzerdefiniertes Branding für Ihre Organisation](https://aka.ms/orgBranding).

![Liste der Arbeitsbereiche](media/service-admin-portal/workspaces-list.png)

## <a name="manage-featured-content"></a>Verwalten empfohlener Inhalte

Als Administrator eines Mandanten können Sie alle Berichte, Dashboards und Apps verwalten, die im Bereich „Empfohlen“ auf der Startseite in Power BI für Ihre Organisation angezeigt werden.

- Klicken Sie im Verwaltungsportal auf **Ausgewählte Inhalte**.

Hier sehen Sie eine Übersicht darüber, wer den Inhalt empfohlen hat und wann er empfohlen wurde. Außerdem werden alle dazugehörigen Metadaten angezeigt. Wenn Sie etwas Verdächtiges bemerken, oder wenn Sie den Bereich „Empfohlen“ bereinigen möchten, können Sie die empfohlenen Inhalte entsprechend entfernen.

Im Abschnitt [Empfohlene Inhalte](#featured-content) dieses Artikels finden Sie weitere Informationen zum Aktivieren empfohlener Inhalte.

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Power BI in Ihrer Organisation](service-admin-administering-power-bi-in-your-organization.md)  
[Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md)  
[Überwachen von Power BI in Ihrer Organisation](service-admin-auditing.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
