---
title: Organisieren der Arbeit in den neuen Power BI-Arbeitsbereichen
description: Lernen Sie die neuen Arbeitsbereiche kennen, die Sammlungen von Dashboards und Berichten sind, die konzipiert wurden, um Schlüsselmetriken für Ihre Organisation bereitzustellen.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c534a72594692c5cf404b095492e7d6425f23329
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273659"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organisieren der Arbeit in den neuen Power BI-Arbeitsbereichen

*Arbeitsbereiche* sind Orte für die Zusammenarbeit mit Kollegen, um Sammlungen von Dashboards, Berichten, Datasets und paginierten Berichten zu erstellen. In der neuen Benutzeroberfläche für Arbeitsbereiche können Sie den Zugriff auf Inhalte besser verwalten. Dieser Artikel beschreibt die neuen Arbeitsbereiche und ihre Unterschiede zu den klassischen Arbeitsbereichen.  Wie klassische Arbeitsbereiche verwenden Sie die neuen weiterhin zum Erstellen und Verteilen von Apps. Möchten Sie einen neuen Arbeitsbereich erstellen? Weitere Informationen finden Sie unter [Erstellen einer neuen Arbeitsbereichsoberfläche](service-create-the-new-workspaces.md).

Neue, aktualisierte Arbeitsbereiche können parallel zu vorhandenen klassischen Arbeitsbereichen vorhanden sein. Die neue Benutzeroberfläche für Arbeitsbereiche ist der Standardarbeitsbereichstyp. Sie können weiterhin bei Bedarf [klassische Arbeitsbereiche](service-create-workspaces.md) basierend auf Office 365-Gruppen erstellen und verwenden. Sind Sie bereit, Ihren klassischen Arbeitsbereich zu migrieren? Einzelheiten finden Sie unter [Aktualisieren klassischer Arbeitsbereiche auf die neuen Arbeitsbereiche in Power BI](service-upgrade-workspaces.md).

Mit den neuen Arbeitsbereichen können Sie Folgendes durchführen:

- Arbeitsbereichsrollen Benutzergruppen zuweisen: Sicherheitsgruppen, Verteilerlisten, Office 365-Gruppen und Einzelpersonen.
- Erstellen Sie einen Arbeitsbereich in Power BI, ohne eine zugrundeliegende, zugehörige Office 365-Gruppe anzulegen. Die gesamte Arbeitsbereichsverwaltung findet in Power BI statt, nicht in Office 365.
- Sie können auf Wunsch den Zugriff der Benutzer auf Inhalte weiterhin über Office 365-Gruppen verwalten. Fügen Sie einfach eine Office 365-Gruppe in die Zugriffsliste des Arbeitsbereichs ein.
- Genauere Arbeitsbereichsrollen für flexiblere Verwaltung von Berechtigungen in einem Arbeitsbereich verwenden.

Power BI listet weiterhin alle Office 365-Gruppen auf, deren Mitglied Sie sind. Dadurch wird das Ändern vorhandener Workflows vermieden.

## <a name="new-and-classic-workspace-differences"></a>Unterschiede zwischen neuen und klassischen Arbeitsbereichen

Mit den neuen Arbeitsbereichen wurden einige Features neu gestaltet. Im Folgenden werden die Hauptunterschiede erläutert.

* Durch das Erstellen dieser Arbeitsbereiche werden, anders als bei klassischen Arbeitsbereichen, keine Office 365-Gruppen erstellt. Sie können jedoch jetzt eine Office 365-Gruppe verwenden, um Benutzern Zugriff auf Ihren Arbeitsbereich zu gewähren, indem Sie ihm eine Rolle zuweisen. 
* In den klassischen Arbeitsbereichen können Sie den Listen der Mitglieder und Administratoren nur Einzelpersonen hinzufügen. In den neuen Arbeitsbereichen können Sie zu diesen Listen mehrere Active Directory-Sicherheitsgruppen, Verteilerlisten oder Office 365-Gruppen hinzufügen, um die Benutzerverwaltung zu vereinfachen. 
- Sie können ein organisationsbezogenes Inhaltspaket über einen klassischen Arbeitsbereich erstellen. Über den neuen Arbeitsbereich können Sie diese nicht erstellen.
- Sie können ein organisationsbezogenes Inhaltspaket über einen klassischen Arbeitsbereich nutzen. Über die neuen Arbeitsbereiche können Sie dieses nicht nutzen.

### <a name="workspace-features-that-work-differently"></a>Arbeitsbereichsfeatures mit geänderter Funktionsweise

Einige Features funktionieren in den neuen Arbeitsbereichen anders als in den aktuellen Arbeitsbereichen. Diese Unterschiede sind beabsichtigt und basieren auf Feedback, das von Kunden gesammelt wurde. Sie ermöglichen einen flexibleren Ansatz für die Zusammenarbeit mithilfe von Arbeitsbereichen.

- **Erzwingung der Lizenzierung**: Die Veröffentlichung von Berichten auf der neuen Benutzeroberfläche für Arbeitsbereiche ist mit der Erzwingung bestehenden Lizenzierungsregeln verbunden. Benutzer, die in Arbeitsbereichen zusammenarbeiten oder Inhalte für andere Benutzer des Power BI-Diensts freigeben, benötigen eine Power BI Pro-Lizenz. Benutzern ohne Pro-Lizenz wird die Fehlermeldung „Nur Benutzer mit Power BI Pro-Lizenzen können in diesem Arbeitsbereich veröffentlichen“ angezeigt.
- **Mitglieder können eine erneute Freigabe vornehmen oder nicht**: Die Rolle „Mitwirkender“ ersetzt diese Einstellung.
- **Schreibgeschützte Arbeitsbereiche**: Anstatt Benutzern schreibgeschützten Zugriff auf einen Arbeitsbereich zu gewähren, weisen Sie Benutzern die Rolle „Anzeigender Benutzer“ zu. Diese Rolle ermöglicht einen ähnlichen schreibgeschützten Zugriff auf den Inhalt eines Arbeitsbereichs.
- **Benutzer ohne Pro-Lizenz** können auf den Arbeitsbereich zugreifen, wenn der Arbeitsbereich sich in einer Power BI Premium-Kapazität befindet, auch wenn Benutzer nur die Rolle „Anzeigender Benutzer“ haben.
- **Benutzern das Exportieren von Daten erlauben**: Benutzer mit der Rolle „Anzeigender Benutzer“ können Daten exportieren, wenn sie die Berechtigung „Erstellen“ für die Datasets im Arbeitsbereich haben. Erfahren Sie mehr über die [Erstellungsberechtigung für Datasets](../connect-data/service-datasets-build-permissions.md).
- Es gibt keine Schaltfläche **Arbeitsbereich verlassen**.

### <a name="workspace-contact-list"></a>Arbeitsbereichs-Kontaktliste

Mit dem neuen Feature **Kontaktliste** können Sie festlegen, welche Benutzer Benachrichtigungen über Probleme im Arbeitsbereich erhalten. Standardmäßig wird jeder Benutzer oder jede Gruppe benachrichtigt, der/die als Arbeitsbereichsadministrator angegeben ist, aber Sie können die Liste anpassen. Benutzer oder Gruppen, die in der Kontaktliste aufgeführt sind, werden in der Benutzeroberfläche (UI) angezeigt, um Benutzern Hilfe zum Arbeitsbereich bieten zu können. 

Erfahren Sie mehr über die [Arbeitsbereichs-Kontaktliste](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>OneDrive für Arbeitsbereich

Mit dem Feature OneDrive für Arbeitsbereich können Sie eine Office 365-Gruppe konfigurieren, deren SharePoint-Dokumentbibliothek-Speicher für Arbeitsbereichsbenutzer verfügbar ist. Sie erstellen die Gruppe außerhalb von Power BI.

Power BI synchronisiert keine Berechtigungen von Benutzern oder Gruppen, für die der Arbeitsbereichszugriff mit der Office 365-Gruppenmitgliedschaft konfiguriert ist. Die beste Vorgehensweise besteht darin, den Zugriff auf den Arbeitsbereich über dieselbe Office 365-Gruppe zu verwalten, deren Dateispeicher Sie in dieser Einstellung konfigurieren. 

Erfahren Sie, wie Sie [OneDrive für Arbeitsbereich einstellen und darauf zugreifen können](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Rollen in den neuen Arbeitsbereichen

Wenn Sie Zugriff auf einen neuen Arbeitsbereich gewähren möchten, fügen Sie Benutzergruppen oder Einzelpersonen einer der folgenden Arbeitsbereichsrollen hinzu: Administratoren, Mitglieder, Mitwirkende oder anzeigende Benutzer. Allen Mitgliedern einer Benutzergruppe wird die von Ihnen festgelegte Rolle zugewiesen. Wenn eine Person mehreren Benutzergruppen angehört, erhält sie die höchste Berechtigungsstufe entsprechend der ihr zugewiesenen Rollen.

Mit Rollen können Sie verwalten, wer welche Aktionen in einem Arbeitsbereich durchführen kann. So können Teams zusammenarbeiten. Mithilfe der neuen Arbeitsbereiche können Sie Einzelpersonen und Benutzergruppen Rollen zuweisen: Sicherheitsgruppen, Office 365-Gruppen und Verteilerlisten. 

Wenn Sie einer Benutzergruppe Rollen zuweisen, verfügen die Personen in der Gruppe über Zugriffsberechtigungen für Inhalte. Wenn Sie Benutzergruppen schachteln, verfügen alle Benutzer über die Berechtigung.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Um die Sicherheit auf Zeilenebene (Row-Level Security, RLS) für Benutzer zu erzwingen, die Inhalte in einem Arbeitsbereich durchsuchen, verwenden Sie die Rolle „Anzeigender Benutzer“. Veröffentlichen Sie eine Power BI-App für diese Benutzer, oder verwenden Sie die Freigabe zur Verteilung von Inhalt, um RLS zu erzwingen, ohne Zugriff auf den Arbeitsbereich zu gewähren.

## <a name="licensing"></a>Lizenzierung
Alle Benutzer, die Sie einem Arbeitsbereich in der gemeinsam genutzten Kapazität hinzufügen, benötigen eine Power BI Pro-Lizenz. Im Arbeitsbereich ist die Zusammenarbeit aller Beteiligten beim Erstellen von Dashboards und Berichten möglich, die Sie für eine größere Zielgruppe oder sogar die gesamte Organisation veröffentlichen möchten. 

Wenn Sie Inhalte an andere Personen in Ihrer Organisation verteilen möchten, können Sie diesen Benutzern Power BI Pro-Lizenzen zuweisen oder den Arbeitsbereich in einer Power BI Premium-Kapazität hinzufügen.

Wenn sich der Arbeitsbereich in einer Power BI Premium-Kapazität befindet, können Benutzer mit der Rolle „Anzeigender Benutzer“ auch dann auf den Arbeitsbereich zugreifen, wenn sie keine Power BI Pro-Lizenz besitzen. Wenn Sie diesen Benutzern jedoch eine höhere Rolle wie „Administrator“, „Mitglied“ oder „Mitwirkender“ zuweisen, werden diese aufgefordert, eine Pro-Testversion zu starten, wenn sie versuchen, auf den Arbeitsbereich zuzugreifen. Um die Rolle „Anzeigender Benutzer“ für Benutzer ohne Pro-Lizenz zu nutzen, stellen Sie sicher, dass sie nicht auch andere Arbeitsbereichsrollen haben, weder einzeln noch im Rahmen einer Benutzergruppe.

> [!NOTE]
> Die Veröffentlichung von Berichten in der neuen Benutzeroberfläche für Arbeitsbereiche ist mit einer strengeren Durchsetzung der bestehenden Lizenzregeln verbunden. Wenn Sie versuchen, ohne Pro-Lizenz in Power BI Desktop oder anderen Clienttools eine Veröffentlichung vorzunehmen, wird Ihnen der Fehler „Nur Benutzer mit Power BI Pro-Lizenzen können in diesem Arbeitsbereich veröffentlichen“ angezeigt.

## <a name="administering-new-workspace-experience-workspaces"></a>Verwalten von Arbeitsbereichen der neuen Benutzeroberfläche für Arbeitsbereiche

Die Verwaltung von Arbeitsbereichen mit neuer Oberfläche erfolgt jetzt im Power BI-Verwaltungsportal. Power BI-Administratoren entscheiden, wer in einem Unternehmen Arbeitsbereiche erstellen und Apps verteilen darf. Administratoren können den Zustand aller Arbeitsbereiche in ihrer Organisation einsehen. Sie können auch Arbeitsbereiche verwalten und wiederherstellen. Im Artikel zum Verwaltungsportal erfahren Sie mehr zum [Erstellen der neuen Arbeitsbereiche](../admin/service-admin-portal.md#create-the-new-workspaces).

## <a name="guest-users"></a>Gastbenutzer

Standardmäßig können [Azure AD-B2B-Gastbenutzer](../admin/service-admin-azure-ad-b2b.md) nicht auf Arbeitsbereiche zugreifen. Power BI-Administratoren können es [externen Gastbenutzern erlauben, Inhalte in der Organisation zu bearbeiten und zu verwalten](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Aktivierte Gastbenutzer können auf Arbeitsbereiche zugreifen, für die sie über eine Berechtigung verfügen.

## <a name="auditing"></a>Überwachung

Die folgenden Aktivitäten werden von Power BI für Arbeitsbereiche der neuen Benutzeroberfläche für Arbeitsbereiche überwacht.

| Anzeigename | Vorgangsname |
|---|---|
| Created Power BI folder (Power BI-Ordner erstellt) | CreateFolder |
| Deleted Power BI folder (Power BI-Ordner gelöscht) | DeleteFolder |
| Updated Power BI folder (Power BI-Ordner aktualisiert) | UpdateFolder |
| Updated Power BI folder access (Ordnerzugriff für Power BI aktualisiert)| UpdateFolderAccess |

Informieren Sie sich ausführlicher über [Von Power BI überwachte Aktivitäten](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Zu beachtende Einschränkungen:

- Arbeitsbereiche können maximal 1.000 Datasets oder 1.000 Berichte pro Dataset enthalten. 
- Eine Person mit einer Power BI Pro-Lizenz kann in maximal 1.000 Arbeitsbereichen Mitglied sein.
- Power BI Publisher für Excel wird nicht unterstützt.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Sind Links zu bestehenden Inhalten von der neuen Benutzeroberfläche für Arbeitsbereiche betroffen?**

Nein. Links zu vorhandenen Elementen in den klassischen Arbeitsbereichen werden nicht durch die neue Benutzeroberfläche für Arbeitsbereiche beeinflusst. Die allgemeine Verfügbarkeit (GA) der neuen Benutzeroberfläche für Arbeitsbereiche ändert den Standardarbeitsbereich, den Sie erstellen, jedoch nicht vorhandene Arbeitsbereiche. 

**Werden vorhandene Arbeitsbereiche auf die neue Benutzeroberfläche für Arbeitsbereiche mit allgemeiner Verfügbarkeit aktualisiert?**

Nein. Aufgrund der allgemeinen Verfügbarkeit der neuen Benutzeroberfläche für Arbeitsbereiche wird nur der Standardarbeitsbereichstyp in die neue Benutzeroberfläche für Arbeitsbereiche geändert. Vorhandene klassische Arbeitsbereiche, die auf Office 365-Gruppen basieren, bleiben unverändert.

**Werden Arbeitsbereiche weiterhin automatisch für Office 365-Gruppen erstellt?**

Ja. Da wir beide Typen von Arbeitsbereichen gleichzeitig unterstützen, listen wir weiterhin alle Office 365-Gruppen auf, auf die Sie in der Liste der Arbeitsbereiche Zugriff haben.

## <a name="next-steps"></a>Nächste Schritte

* [Erstellen der neuen Arbeitsbereiche in Power BI](service-create-the-new-workspaces.md)
* [Erstellen der klassischen Arbeitsbereiche](service-create-workspaces.md)
* [Installieren und Verwenden von Apps in Power BI](service-create-distribute-apps.md)
* Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

