---
title: Grundlegendes zur Dienstadministratorrolle in Power BI
description: In diesem Artikel werden die Dienstadministratorrolle in Power BI sowie spezifische Rollen beschrieben, die Administratorrechte bereitstellen.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/02/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: fc1a0c524a3cb4a713cbaf049c259a4b96714131
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160809"
---
# <a name="understanding-power-bi-service-administrator-roles"></a>Grundlegendes zur Dienstadministratorrolle in Power BI

Sie müssen eine der folgenden Rollen haben, um einen Power BI-Mandanten zu verwalten: Power BI-Administrator, Power Platform-Administrator oder globaler Microsoft 365-Administrator. Administratoren für die Microsoft 365-Benutzerverwaltung weisen Benutzern im Microsoft 365 Admin Center oder mithilfe eines PowerShell-Skripts die Rolle des Power BI-Administrators oder des Power Platform-Administrators zu. Weitere Informationen finden Sie unter [Zuweisen von Rollen zu Benutzerkonten mit Office 365 PowerShell](/office365/enterprise/powershell/assign-roles-to-user-accounts-with-office-365-powershell).

Benutzer mit Power BI-Administratorrollen oder Power Platform-Administratorrollen verfügen über die vollständige Kontrolle über einen Power BI-Mandanten und die zugehörigen Verwaltungsfunktionen – mit Ausnahme der Lizenzierung. Sobald ein Benutzer zugewiesen wurde, erhält er Zugriff auf das [Power BI-Verwaltungsportal](service-admin-portal.md). Dort kann der Benutzer auf Nutzungsmetriken des Mandanten zugreifen und die Verwendung von Power BI-Funktionen im Mandanten steuern. Diese Administratorrollen sind ideal für Benutzer, die Zugriff auf das Power BI-Verwaltungsportal benötigen, ohne diesen Benutzern gleichzeitig den vollständigen Microsoft 365-Administratorzugriff zu gewähren.

> [!NOTE]
> In der Power BI-Dokumentation bezieht sich „Power BI-Administrator“ entweder auf Benutzer in der Power BI-Administratorrolle oder der Power Platform-Administratorrolle. In der Dokumentation wird deutlich, wenn die globale Microsoft 365-Administratorrolle für eine Aufgabe erforderlich ist.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Die Power BI-Dienstadministratorrollen und die Power Platform-Administratorrollen bieten nicht die folgenden Funktionen:

* Ändern von Benutzern und Lizenzen im Microsoft 365 Admin Center

* Zugreifen auf die Überwachungsprotokolle. Weitere Informationen finden Sie unter [Nachverfolgen von Benutzeraktivitäten in Power BI](service-admin-auditing.md).

Diese Funktionen erfordern die globale Microsoft 365-Administratorrolle.

## <a name="assign-users-to-an-admin-role-in-the-microsoft-365-admin-center"></a>Zuweisen von Benutzern zu einer Administratorrolle im Microsoft 365 Admin Center

Führen Sie die folgenden Schritte aus, um Benutzern im Microsoft 365 Admin Center eine Administratorrolle zuzuweisen.

1. Rufen Sie im [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage)**Benutzer** > **Aktive Benutzer** auf.

    ![Microsoft 365 Admin Center](media/service-admin-role/powerbi-admin-users.png)

1. Wählen Sie den Benutzer aus, dem Sie die Rolle zuweisen möchten.

1. Wählen Sie unter **Rollen** **Rollen verwalten** aus.

    ![Rollen verwalten](media/service-admin-role/powerbi-admin-edit-roles.png)

1. Erweitern Sie **Alle nach Kategorie anzeigen**, und wählen Sie dann **Power BI-Administrator** oder **Power Platform-Administrator** aus.

    ![Auswählen der Administratorrolle](media/service-admin-role/powerbi-admin-role.png)

1. Klicken Sie auf **Save changes** (Änderungen speichern).

## <a name="assign-users-to-the-admin-role-with-powershell"></a>Zuweisen von Benutzern zur Administratorrolle mit PowerShell

Sie können auch PowerShell verwenden, um Benutzer zu Rollen zuzuweisen. Benutzer werden in Azure Active Directory (Azure AD) verwaltet. Wenn Sie noch nicht über das Azure AD-PowerShell-Modul verfügen, [laden Sie die neueste Version herunter, und installieren Sie sie](https://www.powershellgallery.com/packages/AzureAD/).

1. Stellen Sie zunächst eine Verbindung mit Azure AD her:
   ```
   PS C:\Windows\system32> Connect-AzureAD
   ```

1. Rufen Sie dann die **ObjectId** für die Rolle **Power BI-Dienstadministrator** ab. Sie können den Befehl [Get-AzureADDirectoryRole](/powershell/module/azuread/get-azureaddirectoryrole) ausführen, um die **ObjectId** abzurufen.

    ```
    PS C:\Windows\system32> Get-AzureADDirectoryRole

    ObjectId                             DisplayName                        Description
    --------                             -----------                        -----------
    00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
    250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
    3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
    50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
    6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
    9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
    a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
    f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
    ```

    In diesem Fall lautet die **ObjectId** der Rolle „00f79122-c45d-436d-8d4a-2c0c6ca246bf“.

1. Rufen Sie als Nächstes die **ObjectId** des Benutzers ab. Diese können Sie mit dem Befehl [Get-AzureADUser](/powershell/module/azuread/get-azureaduser) ermitteln.

    ```
    PS C:\Windows\system32> Get-AzureADUser -ObjectId 'tim@contoso.com'

    ObjectId                             DisplayName UserPrincipalName      UserType
    --------                             ----------- -----------------      --------
    6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
    ```

1. Um das Mitglied der Rolle zuzuweisen, führen Sie den Befehl [Add-AzureADDirectoryRoleMember](/powershell/module/azuread/add-azureaddirectoryrolemember) aus.

    | Parameter | Beschreibung |
    | --- | --- |
    | ObjectId |Die ObjectId der Rolle |
    | RefObjectId |Die ObjectId des Mitglieds. |

    ```powershell
    Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
    ```

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Power BI in Ihrer Organisation](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI-Verwaltungsportal](service-admin-portal.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)