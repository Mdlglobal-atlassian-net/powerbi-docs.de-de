---
title: Aktivieren oder Deaktivieren von Self-Service-Registrierung und -Käufen
description: Informationen für Administratoren, wie sie die Registrierung für Power BI und den Kauf von Lizenzen für Benutzer deaktivieren können
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81447508"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Aktivieren oder Deaktivieren von Self-Service-Registrierung und -Käufen

In den meisten Organisationen ist die Self-Service-Registrierung standardmäßig aktiviert. Einzelbenutzer in Ihrer Organisation können sich mit ihrem Geschäfts-, Schul- oder Unikonto für Power BI registrieren. Benutzern kann auch die Option angeboten werden, direkt eine Power BI Pro-Lizenz zu erwerben, wenn sie versuchen, ein Pro-Feature zu verwenden. Als Administrator legen Sie fest, ob Sie die Self-Service-Registrierung aktivieren oder deaktivieren möchten. Sie können auch steuern, ob Benutzer in Ihrer Organisation Self-Service-Käufe tätigen können, um eigene Lizenzen zu erwerben.

> [!NOTE]
>Wenn Sie Power BI über einen Microsoft Cloud Solution Provider (CSP) erworben haben, ist die Einstellung möglicherweise deaktiviert, damit Benutzer sich nicht selbstständig registrieren können. Ihr CSP fungiert möglicherweise auch als globaler Administrator für Ihre Organisation, sodass Sie sich direkt an diesen wenden müssen, um die Einstellung zu ändern.
>
>

Verwenden Sie PowerShell-Befehle, um die Einstellungen für Self-Service-Registrierungen und -Käufe zu ändern. Es gibt zwei Einstellungen, mit denen gesteuert wird, ob Benutzer in Ihrer Organisation eine Self-Service-Registrierung durchführen oder Self-Service-Käufe tätigen können.

- Wenn Sie alle Self-Service-Registrierungen deaktivieren möchten, ändern Sie die Azure Active Directory-Einstellung **AllowAdHocSubscriptions** mithilfe von PowerShell-Befehlen für Azure AD. Befolgen Sie die Schritte in diesem Artikel, um die [Self-Service-Registrierung zu aktivieren oder zu deaktivieren](#enable-or-disable-self-service-signup). Mit dieser Option wird die Self-Service-Registrierung für *alle* cloudbasierten Microsoft-Apps und -Dienste deaktiviert.

- Wenn Sie verhindern möchten, dass Benutzer ihre eigene Pro-Lizenz erwerben, ändern Sie die Einstellung **AllowSelfServicePurchase** mithilfe von MSCommerce-PowerShell-Befehlen. Mit dieser Einstellung können Sie Self-Service-Käufe für bestimmte Produkte deaktivieren. Befolgen Sie die Schritte in diesem Artikel, um [Self-Service-Käufe für Power BI Pro-Lizenzen zu aktivieren oder zu deaktivieren](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Aktivieren oder Deaktivieren der Self-Service-Registrierung

Wenn die Self-Service-Registrierung aktiviert ist, ist für **AllowAdHocSubscriptions** der Wert *true* festgelegt. Hier sehen Sie, was geschieht, wenn Sie diesen in *false* ändern:

- Wenn Sie die Einstellung von „true“ in „false“ ändern, können sich neue Benutzer in Ihrer Organisation nicht mehr selbstständig registrieren. Alle Benutzer, die sich vor der Änderung der Einstellung für Power BI registriert haben, behalten ihre Lizenzen.

- Wenn Sie die Einstellung in „false“ ändern, können sich Benutzer, die bereits eine Power BI Free-Lizenz besitzen, sich trotzdem eine individuelle Power BI Pro-Testversion registrieren.

- Ein Administrator muss alle Power BI-Lizenzen neuen Benutzern zuweisen, die diese benötigen.

### <a name="before-you-begin"></a>Vorbereitung

Für diese Schritte werden PowerShell-Befehle für Azure Active Directory verwendet, um den Wert der Einstellung **AllowAdHocSubscriptions** zu ändern. Das Azure AD-Modul für PowerShell muss installiert sein, damit Sie diese Befehle verwenden können. Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Erste Schritte mit Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Starten Sie Windows PowerShell als Administrator, um das Azure AD-Modul zu installieren. Stellen Sie sicher, dass Ihre lokale Ausführungsrichtlinie das Ausführen von Skripts zulässt. Lesen Sie bei Problemen den Artikel zu [PowerShell-Ausführungsrichtlinien](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies), um zu erfahren, wie Sie Ihre lokale Richtlinie ändern.

Führen Sie den folgenden Befehl aus, um das Azure AD-Modul zu installieren:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Ändern der Richtlinie für die Self-Service-Registrierung

Führen Sie in PowerShell den folgenden Befehl aus, um eine Verbindung mit Azure AD herzustellen:

```powershell
Connect-MsolService
```

Geben Sie die Administratoranmeldeinformationen in das Anmeldedialogfeld ein, und führen Sie ggf. die zweistufige Authentifizierung durch. Nach der Überprüfung werden Sie wieder zum PowerShell-Fenster zurückgeleitet.

Führen Sie den folgenden Befehl aus, um die aktuelle Einstellung anzuzeigen. Die Ausgabe wird mithilfe des Parameters „fl“ an eine formatierte Liste weitergeleitet.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Führen Sie den folgenden Befehl aus, um die aktuelle Einstellung zu ändern:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Nachdem Sie diesen Befehl ausgeführt haben, ist die Self-Service-Registrierung für alle Benutzer deaktiviert. Führen Sie diesen Befehl noch mal aus, und legen Sie den Wert auf „$true“ fest, wenn Sie diese wieder aktivieren möchten.

## <a name="enable-or-disable-self-service-purchase"></a>Aktivieren oder Deaktivieren von Self-Service-Käufen

Wenn Self-Service-Käufe aktiviert sind, ist für **AllowSelfServicePurchase** der Wert *true* festgelegt. Hier sehen Sie, was geschieht, wenn Sie diesen in *false* ändern:

- Wenn Sie die Einstellung von „true“ in „false“ ändern, können Benutzer in Ihrer Organisation nicht mehr selbstständig Power BI Pro-Lizenzen erwerben. Alle Benutzer, die vor der Änderung der Einstellung eine Lizenz erworben haben, behalten ihre Lizenzen.

- Wenn Sie die Einstellung in „false“ ändern, können Benutzer, die bereits eine Power BI Free-Lizenz besitzen, keine Power BI Pro-Einzellizenz erwerben. 

- Ein Administrator muss allen Benutzern eine Pro-Lizenz zuweisen, die eine benötigen.

### <a name="before-you-begin"></a>Vorbereitung

Bei diesen Schritten werden MSCommerce-PowerShell-Befehle verwendet, um den Wert der Einstellung **AllowSelfServicePurchase** zu ändern. Das MSCommerce-Modul für PowerShell muss installiert sein, damit Sie diese Befehle verwenden können. Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Erste Schritte mit Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Starten Sie Windows PowerShell als Administrator, um das MSCommerce-Modul zu installieren. Stellen Sie sicher, dass Ihre lokale Ausführungsrichtlinie das Ausführen von Skripts zulässt. Lesen Sie bei Problemen den Artikel zu [PowerShell-Ausführungsrichtlinien](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies), um zu erfahren, wie Sie Ihre lokale Richtlinie ändern.

Führen Sie den folgenden Befehl aus, um das MSCommerce-Modul zu installieren:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Ändern der Richtlinie für die Self-Service-Registrierung

Führen Sie in PowerShell den folgenden Befehl aus, um eine Verbindung herzustellen:

```powershell
Connect-MSCommerce
```

Geben Sie die Administratoranmeldeinformationen in das Anmeldedialogfeld ein, und führen Sie ggf. die zweistufige Authentifizierung durch. Nach der Überprüfung zeigt das PowerShell-Fenster eine erfolgreiche Verbindung an.

Führen Sie den folgenden Befehl aus, um die aktuelle Einstellung anzuzeigen. Die Ausgabe wird mithilfe des Parameters „fl“ an eine formatierte Liste weitergeleitet, damit kein Text abgeschnitten wird.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Sie können Self-Service-Käufe für einzelne Produkte deaktivieren, indem Sie deren **ProductId**-Wert angeben. Führen Sie den folgenden Befehl aus, um die aktuelle Einstellung für den Power BI-Dienst zu ändern:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Nachdem Sie diesen Befehl ausgeführt haben, sind Self-Service-Käufe für Power BI für alle Benutzer deaktiviert. Führen Sie diesen Befehl noch mal aus, und legen Sie den Wert auf „$true“ fest, wenn Sie diese wieder aktivieren möchten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Self-Service-Käufen in Power BI und Power Platform finden Sie in den folgenden Artikeln:

- [FAQ zu Self-Service-Käufen](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Verwenden von AllowSelfServicePurchase für das MSCommerce-PowerShell-Modul](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
