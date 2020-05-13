---
title: Sicherheit auf Zeilenebene (row-level security; RLS) mit Power BI
description: Erfahren Sie, wie Sie die Sicherheit auf Zeilenebene für importierte Datasets in DirectQuery im Power BI-Dienst konfigurieren.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.author: kfollis
ms.date: 12/05/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 6622bff6123ac6985a5275ec72be3a78b13908e6
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274634"
---
# <a name="row-level-security-rls-with-power-bi"></a>Sicherheit auf Zeilenebene (row-level security; RLS) mit Power BI

Die Sicherheit auf Zeilenebene (row-level security; RLS) mit Power BI kann zum Einschränken des Datenzugriffs für bestimmte Benutzer verwendet werden. Filter beschränken den Datenzugriff auf Zeilenebene, und Sie können Filter in Rollen definieren. Beachten Sie, dass Mitglieder eines Arbeitsbereichs im Power BI-Dienst über Zugriff auf die Datasets im Arbeitsbereich verfügen. RLS schränkt den Zugriff auf diese Daten nicht ein.

Sie können RLS für Datenmodelle konfigurieren, die mithilfe von Power BI Desktop in Power BI importiert wurden. Sie können auch RLS für Datasets konfigurieren, die DirectQuery verwenden, z. B. SQL Server. Bisher konnte RLS nur in lokalen Analysis Services-Modellen außerhalb von Power BI implementiert werden. Bei Analysis Services- oder Azure Analysis Services-Liveverbindungen konfigurieren Sie die Sicherheit auf Zeilenebene im Modell, nicht in Power BI Desktop. Die Sicherheitsoption wird nicht für Liveverbindungsdatasets angezeigt.

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

Standardmäßig werden beim Filtern mit Sicherheit auf Zeilenebene einzelne unidirektionale Filter verwendet, unabhängig davon, ob die Beziehungen als unidirektional oder bidirektional festgelegt wurden. Sie können die bidirektionale Kreuzfilterung mit Sicherheit auf Zeilenebene manuell aktivieren, indem Sie die Beziehung auswählen und das Kontrollkästchen **Sicherheitsfilter in beide Richtungen anwenden** aktivieren. Sie sollten dieses Kontrollkästchen aktivieren, wenn Sie auch dynamische Sicherheit auf Zeilenebene auf der Serverebene implementiert haben, wo die Sicherheit auf Zeilenebene auf Grundlage eines Benutzernamens oder der Anmelde-ID bereitstellt wird.

Weitere Informationen finden Sie unter [Bidirektionale Kreuzfilterung mithilfe von DirectQuery in Power BI Desktop](../transform-model/desktop-bidirectional-filtering.md) und im Artikel [Securing the Tabular BI Semantic Model](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx) (Sichern des semantischen BI-Tabellenmodells, in englischer Sprache).

![Anwenden eines Sicherheitsfilters](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Verwalten der Sicherheitseinstellungen Ihres Modells

Zum Verwalten der Sicherheitseinstellungen Ihres Datenmodells sollten Sie wie folgt vorgehen:

1. Wählen Sie die **Ellipse (...)** für ein Dataset aus.
2. Wählen Sie **Sicherheit** aus.
   
   ![Sicherheitsfilter in beide Richtungen anwenden](media/service-admin-rls/rls-security.png)

Dadurch gelangen Sie zur RLS-Seite, wo Sie Mitglieder zu einer Rolle hinzufügen können, die Sie in Power BI Desktop erstellt haben. Die Sicherheit ist nur für die Besitzer des Datasets verfügbar. Wenn das Dataset zu einer Gruppe gehört, können nur Administratoren der Gruppe die Sicherheitsoption sehen. 

Sie können Rollen nur in Power BI Desktop erstellen oder ändern.

## <a name="working-with-members"></a>Arbeiten mit Mitgliedern

### <a name="add-members"></a>Hinzufügen von Mitgliedern

Sie können der Rolle ein Mitglied hinzufügen, indem Sie die E-Mail-Adresse oder den Namen des Benutzers, der Sicherheitsgruppe oder der Verteilerliste eingeben, den bzw. die Sie hinzufügen möchten. Sie können keine in Power BI erstellten Gruppen hinzufügen. Sie können [Ihrer Organisation externe Mitglieder hinzufügen](../guidance/whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Hinzufügen eines Mitglieds](media/service-admin-rls/rls-add-member.png)

Anhand der Zahl in Klammern neben dem Rollennamen oder neben „Mitglieder“ können Sie zudem sehen, wie viele Mitglieder Teil der Rolle sind.

![Mitglieder in der Rolle](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Entfernen von Mitgliedern

Sie können Mitglieder entfernen, indem Sie das „X“ neben ihrem Namen auswählen. 

![Entfernen eines Mitglieds](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Überprüfen der Rolle im Power BI-Dienst

Sie können überprüfen, ob die von Ihnen definierte Rolle ordnungsgemäß funktioniert, indem Sie sie testen. 

1. Wählen Sie **Weitere Optionen** (...) neben der Rolle aus.
2. Wählen Sie **Daten als Rolle testen** aus.

![Als Rolle testen](media/service-admin-rls/rls-test-role.png)

Es werden dann die für diese Rolle verfügbaren Berichte angezeigt. Dashboards werden in dieser Ansicht nicht angezeigt. Auf der blauen Leiste oben sehen Sie, was angewendet wird.

![Anzeige als <Rolle>](media/service-admin-rls/rls-test-role2.png)

Sie können andere Rollen oder eine Kombination von Rollen testen, indem Sie **Now viewing as** (Jetzt anzeigen als) auswählen.

![Testen von anderen Rollen](media/service-admin-rls/rls-test-role3.png)

Sie können auch Daten als eine bestimmte Person anzeigen oder eine Kombination der verfügbaren Rollen auswählen, um deren ordnungsgemäße Funktion zu überprüfen. 

Um zur normalen Ansicht zurückzukehren, wählen Sie **Zurück zur Sicherheit auf Zeilenebene** aus.

[!INCLUDE [include-short-name](../includes/rls-usernames.md)]

## <a name="using-rls-with-workspaces-in-power-bi"></a>Verwenden von RLS mit Arbeitsbereichen in Power BI

Wenn Sie Ihren Power BI Desktop-Bericht in einem Arbeitsbereich im Power BI-Dienst veröffentlichen, werden die Rollen auf Mitglieder mit Lesezugriff angewendet. Sie müssen in den Einstellungen angeben, dass Mitglieder die Power BI-Inhalte nur im Arbeitsbereich anzeigen können.

> [!WARNING]
> Wenn Sie den Arbeitsbereich so konfiguriert haben, dass dessen Mitglieder über Bearbeitungsberechtigungen verfügen, werden die RLS-Rollen nicht auf diese angewendet. Benutzer können dann alle Daten einsehen.

![Gruppeneinstellungen](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Nächste Schritte
[Sicherheit auf Zeilenebene (Row-Level Security; RLS) mit Power BI Desktop](../create-reports/desktop-rls.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

