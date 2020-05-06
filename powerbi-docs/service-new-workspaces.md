---
title: Organisieren der Arbeit in den neuen Power BI-Arbeitsbereichen
description: Lernen Sie die neuen Arbeitsbereiche kennen, die Sammlungen von Dashboards und Berichten sind, die konzipiert wurden, um Schlüsselmetriken für Ihre Organisation bereitzustellen.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/01/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 7f1815adeb83e68ea42d68b084752068c210e484
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781347"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organisieren der Arbeit in den neuen Power BI-Arbeitsbereichen

 *Arbeitsbereiche* sind Orte für die Zusammenarbeit mit Kollegen, um Sammlungen von Dashboards, Berichten und paginierten Berichten zu erstellen. In der neuen Benutzeroberfläche für Arbeitsbereiche können Sie den Zugriff auf Inhalte besser verwalten. Dieser Artikel beschreibt die neuen Arbeitsbereiche und ihre Unterschiede zu den klassischen Arbeitsbereichen.  Wie klassische Arbeitsbereiche verwenden Sie die neuen weiterhin zum Erstellen und Verteilen von Apps. Erfahren Sie mehr über das [Erstellen der neuen Arbeitsbereiche in Power BI](service-create-the-new-workspaces.md).

Die neue Benutzeroberfläche für Arbeitsbereiche hat die Allgemeine Verfügbarkeit (GA, General Availability) erreicht und ist jetzt der Standardarbeitsbereich. Sie können weiterhin [klassische Arbeitsbereiche](service-create-workspaces.md) basierend auf Office 365-Gruppen erstellen und verwenden. 

> [!NOTE]
> Um die Sicherheit auf Zeilenebene (Row-Level Security, RLS) für Benutzer zu erzwingen, die Inhalte in einem Arbeitsbereich durchsuchen, verwenden Sie die Rolle „Anzeigender Benutzer“. Veröffentlichen Sie eine Power BI-App für diese Benutzer, oder verwenden Sie die Freigabe zur Verteilung von Inhalt, um RLS zu erzwingen, ohne Zugriff auf den Arbeitsbereich zu gewähren.

Mit den neuen Arbeitsbereichen können Sie Folgendes durchführen:

- Arbeitsbereichsrollen Benutzergruppen zuweisen: Sicherheitsgruppen, Verteilerlisten, Office 365-Gruppen und Einzelpersonen.
- Einen Arbeitsbereich in Power BI erstellen, ohne eine Office 365-Gruppe zu erstellen.
- Genauere Arbeitsbereichsrollen für flexiblere Verwaltung von Berechtigungen in einem Arbeitsbereich verwenden.
- Der Power BI-Administrator kann steuern, wer Arbeitsbereiche in Power BI erstellen kann.

Wenn Sie einen der neuen Arbeitsbereiche erstellen, erstellen Sie keine zugrunde liegende, zugehörige Office 365-Gruppe. Die gesamte Arbeitsbereichsverwaltung findet in Power BI statt, nicht in Office 365. In der neuen Benutzeroberfläche für Arbeitsbereiche können Sie jetzt eine Office 365-Gruppe der Arbeitsbereich-Zugriffsliste hinzufügen, um den Benutzerzugriff auf Inhalte weiterhin über Office 365-Gruppen zu verwalten.

## <a name="administering-new-workspace-experience-workspaces"></a>Verwalten von Arbeitsbereichen der neuen Benutzeroberfläche für Arbeitsbereiche
Die Verwaltung von Arbeitsbereichen der neuen Benutzeroberfläche für Arbeitsbereiche erfolgt jetzt in Power BI; Power BI-Administratoren entscheiden, welche Benutzer in einer Organisation Arbeitsbereiche erstellen dürfen. Sie können Arbeitsbereiche auch mithilfe des Power BI-Verwaltungsportals oder mithilfe von PowerShell-Cmdlets verwalten und wiederherstellen. Für klassische Arbeitsbereiche auf Grundlage von Office 365-Gruppen wird die Verwaltung weiterhin im Office 365-Verwaltungsportal und Azure Active Directory durchgeführt.

Im Verwaltungsportal können Administratoren in **Arbeitsbereichseinstellungen** mit der Einstellung „Arbeitsbereiche erstellen (neue Benutzeroberfläche für Arbeitsbereiche)“ jedem oder niemand in einer Organisation das Erstellen neuer Arbeitsbereiche der neuen Benutzeroberfläche für Arbeitsbereiche ermöglichen. Sie können auch die Erstellung von Mitgliedern bestimmter Sicherheitsgruppen beschränken.

> [!NOTE]
> Standardmäßig erlaubt die Einstellung „Arbeitsbereiche erstellen (neue Benutzeroberfläche für Arbeitsbereiche)“ nur Benutzern, die Office 365-Gruppen erstellen können, die neuen Arbeitsbereiche in Power BI zu erstellen. Achten Sie darauf, dass Sie im Power BI-Verwaltungsportal einen Wert festlegen, um sicherzustellen, dass geeignete Benutzer Arbeitsbereiche der neuen Benutzeroberfläche für Arbeitsbereiche erstellen können.

![Arbeitsbereichseinstellungen im Verwaltungsportal](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

Im Power BI-Verwaltungsportal ist die [Arbeitsbereicheliste verfügbar](service-admin-portal.md#workspaces). 

![Liste der Arbeitsbereiche](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Neue Arbeitsbereiche parallel mit klassischen Arbeitsbereichen

Neue, aktualisierte Arbeitsbereiche und klassische Arbeitsbereiche existieren parallel, und Sie können beide erstellen. Die neue Benutzeroberfläche für Arbeitsbereiche ist der Standardarbeitsbereichstyp. Power BI listet weiterhin alle Office 365-Gruppen auf, in denen der Benutzer Mitglied in Power BI ist, um bestehende Workflows nicht zu verändern. Um zu erfahren, wie Sie einen neuen Arbeitsbereich erstellen, lesen Sie [Erstellen der neuen Arbeitsbereiche in Power BI](service-create-the-new-workspaces.md). Um zu erfahren, wie Sie einen klassischen Arbeitsbereich erstellen, lesen Sie [Erstellen der klassischen Arbeitsbereiche in Power BI](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Rollen in den neuen Arbeitsbereichen

Wenn Sie Zugriff auf einen neuen Arbeitsbereich gewähren möchten, fügen Sie Benutzergruppen oder Einzelpersonen einer der folgenden Arbeitsbereichsrollen hinzu: Administratoren, Mitglieder, Mitwirkende oder anzeigende Benutzer. Allen Mitgliedern einer Benutzergruppe wird die von Ihnen festgelegte Rolle zugewiesen. Wenn eine Person in mehreren Benutzergruppen Mitglied ist, erhält sie die höchsten zugewiesenen Berechtigungen.

Mit Rollen können Sie verwalten, wer welche Aktionen in einem Arbeitsbereich durchführen kann. So können Teams zusammenarbeiten. Mithilfe der neuen Arbeitsbereiche können Sie Einzelpersonen und Benutzergruppen Rollen zuweisen: Sicherheitsgruppen, Office 365-Gruppen und Verteilerlisten. 

Wenn Sie einer Benutzergruppe Rollen zuweisen, verfügen die Personen in der Gruppe über Zugriffsberechtigungen für Inhalte. Wenn Sie Benutzergruppen schachteln, verfügen alle Benutzer über die Berechtigung.

[!INCLUDE [power-bi-workspace-roles-table](includes/power-bi-workspace-roles-table.md)]

## <a name="licensing"></a>Lizenzierung
Alle Benutzer, die Sie einem Arbeitsbereich in der gemeinsam genutzten Kapazität hinzufügen, benötigen eine Power BI Pro-Lizenz. Im Arbeitsbereich ist die Zusammenarbeit aller Beteiligten beim Erstellen von Dashboards und Berichten möglich, die Sie für eine größere Zielgruppe oder sogar die gesamte Organisation veröffentlichen möchten. 

Wenn Sie Inhalte an andere Personen in Ihrer Organisation verteilen möchten, können Sie diesen Benutzern Power BI Pro-Lizenzen zuweisen oder den Arbeitsbereich in einer Power BI Premium-Kapazität hinzufügen.

Wenn sich der Arbeitsbereich in einer Power BI Premium-Kapazität befindet, können Benutzer mit der Rolle „Anzeigender Benutzer“ auch dann auf den Arbeitsbereich zugreifen, wenn sie keine Power BI Pro-Lizenz besitzen. Wenn Sie diesen Benutzern jedoch eine höhere Rolle wie Administrator, Mitglied oder Mitwirkender zuweisen, werden diese aufgefordert, eine Pro-Testversion zu starten, wenn sie versuchen, auf den Arbeitsbereich zuzugreifen. Damit Benutzer ohne Pro-Lizenzen als anzeigende Benutzer agieren können, stellen Sie sicher, dass sich die Benutzer in der Rolle „Anzeigender Benutzer“ nicht in anderen Arbeitsbereichsrollen befinden, weder einzeln noch über eine Benutzergruppe. 

> [!NOTE]
> Die Veröffentlichung von Berichten in der neuen Benutzeroberfläche für Arbeitsbereiche ist mit einer strengeren Durchsetzung der bestehenden Lizenzregeln verbunden. Benutzern, die versuchen, ohne Pro-Lizenz aus Power BI Desktop oder anderen Clienttools zu veröffentlichen, wird der Fehler „Nur Benutzer mit Power BI Pro-Lizenzen können in diesem Arbeitsbereich veröffentlichen“ angezeigt.

## <a name="how-the-new-workspaces-are-different"></a>Unterschiede zwischen den neuen Arbeitsbereichen

Mit den neuen Arbeitsbereichen wurden einige Features neu gestaltet. Im Folgenden werden die Änderungen aufgeführt, die dauerhaft Bestand haben werden. 

* Durch das Erstellen dieser Arbeitsbereiche werden, anders als bei klassischen Arbeitsbereichen, keine Office 365-Gruppen erstellt. Sie können jedoch jetzt eine Office 365-Gruppe verwenden, um Benutzern Zugriff auf Ihren Arbeitsbereich zu gewähren, indem Sie ihm eine Rolle zuweisen. 
* In den klassischen Arbeitsbereichen können Sie den Listen der Mitglieder und Administratoren nur Einzelpersonen hinzufügen. In den neuen Arbeitsbereichen können Sie zu diesen Listen mehrere AD-Sicherheitsgruppen, Verteilerlisten oder Office 365-Gruppen hinzufügen, um die Benutzerverwaltung zu vereinfachen. 
- Sie können ein organisationsbezogenes Inhaltspaket über einen klassischen Arbeitsbereich erstellen. Über den neuen Arbeitsbereich können Sie diese nicht erstellen.
- Sie können ein organisationsbezogenes Inhaltspaket über einen klassischen Arbeitsbereich nutzen. Über die neuen Arbeitsbereiche können Sie dieses nicht nutzen.

## <a name="workspace-contact-list"></a>Arbeitsbereichs-Kontaktliste
Mit dem neuen Feature **Kontaktliste** können Sie festlegen, welche Benutzer Benachrichtigungen über Probleme im Arbeitsbereich erhalten. Standardmäßig wird jeder Benutzer oder jede Gruppe benachrichtigt, der/die als Arbeitsbereichsadministrator angegeben ist, aber Sie können die Liste anpassen. Benutzer oder Gruppen, die in der Kontaktliste aufgeführt sind, werden in der Benutzeroberfläche (UI) angezeigt, um Benutzern Hilfe zum Arbeitsbereich bieten zu können. 

Erfahren Sie mehr über die [Arbeitsbereichs-Kontaktliste](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>OneDrive für Arbeitsbereich
Mit dem Feature OneDrive für Arbeitsbereich können Sie eine Office 365-Gruppe konfigurieren, deren SharePoint-Dokumentbibliothek-Speicher für Arbeitsbereichsbenutzer verfügbar ist. Die Gruppe muss außerhalb von Power BI erstellt werden. 

Power BI synchronisiert keine Berechtigungen von Benutzern oder Gruppen, für die der Arbeitsbereichszugriff mit der Office 365-Gruppenmitgliedschaft konfiguriert ist. Die beste Vorgehensweise besteht darin, den Zugriff auf den Arbeitsbereich über dieselbe Office 365-Gruppe zu verwalten, deren Dateispeicher Sie in dieser Einstellung konfigurieren. 

Erfahren Sie, wie Sie [OneDrive für Arbeitsbereich einstellen und darauf zugreifen können](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="auditing"></a>Überwachung

Die folgenden Aktivitäten werden von Power BI für Arbeitsbereiche der neuen Benutzeroberfläche für Arbeitsbereiche überwacht.

| Anzeigename | Vorgangsname |
|---|---|
| Created Power BI folder (Power BI-Ordner erstellt) | CreateFolder |
| Deleted Power BI folder (Power BI-Ordner gelöscht) | DeleteFolder |
| Updated Power BI folder (Power BI-Ordner aktualisiert) | UpdateFolder |
| Updated Power BI folder access (Ordnerzugriff für Power BI aktualisiert)| UpdateFolderAccess |

Informieren Sie sich ausführlicher über [Von Power BI überwachte Aktivitäten](service-admin-auditing.md).

## <a name="guest-users"></a>Gastbenutzer

Standardmäßig können [Azure AD-B2B-Gastbenutzer](service-admin-azure-ad-b2b.md) nicht auf Arbeitsbereiche zugreifen. Power BI-Administratoren können es [externen Gastbenutzern erlauben, Inhalte in der Organisation zu bearbeiten und zu verwalten](service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Die entsprechenden Gastbenutzer können auf die Arbeitsbereiche zugreifen, für die sie über eine Berechtigung verfügen.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Zu beachtende Einschränkungen:

- Arbeitsbereiche können maximal 1.000 Datasets oder 1.000 Berichte pro Dataset enthalten. 
- Eine Person mit einer Power BI Pro-Lizenz kann in maximal 1.000 Arbeitsbereichen Mitglied sein.
- Power BI Publisher für Excel wird nicht unterstützt.

## <a name="workspace-features-that-work-differently"></a>Arbeitsbereichsfeatures mit geänderter Funktionsweise

Einige Features funktionieren in den neuen Arbeitsbereichen anders als in den aktuellen Arbeitsbereichen. Diese Unterschiede sind beabsichtigt und basieren auf Feedback, das von Kunden gesammelt wurde. Mit diesen Änderungen wird ein flexiblerer Ansatz für die Zusammenarbeit in Arbeitsbereichen geboten:

- Lizenzierungserzwingung: Die Veröffentlichung von Berichten für die neue Benutzeroberfläche für Arbeitsbereiche setzt bestehende Lizenzregeln durch, die eine Power BI Pro-Lizenz für Benutzer erfordern, die in Arbeitsbereichen zusammenarbeiten oder Inhalte für andere im Power BI-Dienst freigeben. Benutzern ohne Pro-Lizenz wird die Fehlermeldung „Nur Benutzer mit Power BI Pro-Lizenzen können in diesem Arbeitsbereich veröffentlichen“ angezeigt.
- Mitglieder, die eine erneute Freigabe durchführen oder nicht durchführen können: ersetzt durch die Rolle „Mitwirkender“.
- Schreibgeschützte Arbeitsbereiche: Anstatt Benutzern schreibgeschützten Zugriff auf einen Arbeitsbereich zu gewähren, weisen Sie Benutzern die Rolle „Anzeigender Benutzer“ zu, die einen ähnlichen schreibgeschützten Zugriff auf den Inhalt eines Arbeitsbereichs umfasst.
- Wenn sich der Arbeitsbereich in einer Power BI Premium-Kapazität befindet, können Benutzer ohne Power BI Pro-Lizenz auch dann auf den Arbeitsbereich zugreifen, wenn sie die Rolle „Anzeigender Benutzer“ haben.
- Um Benutzern mit der Rolle „Anzeigender Benutzer“ den Export von Daten zu ermöglichen, stellen Sie sicher, dass sie die Berechtigung zum Erstellen für die Datasets im Arbeitsbereich haben. Erfahren Sie mehr über die [Erstellungsberechtigung für Datasets](service-datasets-build-permissions.md).
- Es gibt keine Schaltfläche **Arbeitsbereich verlassen**.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Sind Links zu bestehenden Inhalten von der allgemeinen Verfügbarkeit der neuen Benutzeroberfläche für Arbeitsbereiche betroffen?**

Nein. Links zu vorhandenen Elementen in den klassischen Arbeitsbereichen werden nicht durch die neue Benutzeroberfläche für Arbeitsbereiche beeinflusst. Die allgemeine Verfügbarkeit (GA) der neuen Benutzeroberfläche für Arbeitsbereiche ändert den Standardarbeitsbereich, den Sie erstellen, jedoch nicht vorhandene Arbeitsbereiche. 

**Werden vorhandene Arbeitsbereiche auf die neue Benutzeroberfläche für Arbeitsbereiche mit allgemeiner Verfügbarkeit aktualisiert?**

Nein. Aufgrund der allgemeinen Verfügbarkeit der neuen Benutzeroberfläche für Arbeitsbereiche wird nur der Standardarbeitsbereichstyp in die neue Benutzeroberfläche für Arbeitsbereiche geändert. Vorhandene klassische Arbeitsbereiche, die auf Office 365-Gruppen basieren, bleiben unverändert.

**Werden Arbeitsbereiche weiterhin automatisch für Office 365-Gruppen erstellt?**

Ja. Da wir beide Typen von Arbeitsbereichen gleichzeitig unterstützen, listen wir weiterhin alle Office 365-Gruppen auf, auf die der Benutzer in der Liste der Arbeitsbereiche Zugriff hat.

## <a name="next-steps"></a>Nächste Schritte
* [Erstellen der neuen Arbeitsbereiche in Power BI](service-create-the-new-workspaces.md)
* [Erstellen der klassischen Arbeitsbereiche](service-create-workspaces.md)
* [Installieren und Verwenden von Apps in Power BI](service-create-distribute-apps.md)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
