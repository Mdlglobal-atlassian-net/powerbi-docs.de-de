---
title: Power BI kann einem O365-Partner nicht hinzugefügt werden
description: Power BI kann einem Office 365-Syndizierungspartner nicht hinzugefügt werden Das Syndizierungsmodell ist ein von Office 365 verwendetes Kaufmodell.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: cc85fb07f50a42952e9b293908a797b1cbac023f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74958354"
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>Power BI kann einem Office 365-Partnerabonnement nicht hinzugefügt werden

Office 365 ermöglicht es Unternehmen, Office 365 in ihre eigenen Lösungen integriert und gebündelt weiterzuverkaufen, wodurch Endkunden eine einzelne Anlaufstelle für Kauf, Abrechnung und Support zur Verfügung steht.

Wenn Sie sich für den Erwerb von Power BI in Kombination mit Ihrem Office 365-Abonnement interessieren, empfehlen wir Ihnen, sich zu diesem Zweck mit Ihrem Partner in Verbindung zu setzen. Wenn Ihr Partner Power BI derzeit nicht anbietet, stehen Ihnen verschiedene Wege offen.

## <a name="work-with-your-partner-to-purchase-power-bi"></a>Zusammenarbeit mit dem Partner zum Erwerben von Power BI

Wenn Sie ein Abonnement für Power BI Pro oder Power BI Premium erwerben möchten, setzen Sie sich mit Ihrem Partner in Verbindung, und besprechen Sie mit ihm, welche Optionen sich Ihnen bieten:

* Der Partner erklärt sich bereit, Power BI in sein Portfolio aufzunehmen, sodass sie bei ihm kaufen können.

* Der Partner kann Sie auf ein Modell umstellen, bei dem Sie Power BI direkt bei Microsoft oder einem anderen Partner erwerben können, der Power BI anbietet.

## <a name="purchase-from-microsoft-or-another-channel"></a>Erwerben bei Microsoft oder über einen anderen Kanal

Je nach Art der Beziehung zu Ihrem Partner können Sie Power BI möglicherweise direkt bei Microsoft oder einem anderen Partner erwerben. Im Microsoft 365 Admin Center können Sie überprüfen, ob Sie Power BI-Abonnements hinzufügen können (erfordert die Mitgliedschaft in den Rollen „Globaler Administrator“ oder „Abrechnungsadministrator“).

1. Navigieren Sie zum [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Öffnen Sie im linken Menü den Eintrag **Abrechnung**:

    * Wenn dort **Abonnements** angezeigt wird, können Sie den Dienst direkt bei Microsoft erwerben oder sich mit einem anderen Partner in Verbindung setzen, der Power BI anbietet.

        ![Abrechnung mit Abonnements](media/service-admin-syndication-partner/billingsub.png)

    * Wenn der Eintrag **Abonnements** nicht angezeigt wird, können Sie den Dienst nicht direkt bei Microsoft oder bei einem anderen Partner erwerben.

Wenn Ihr Partner Power BI nicht anbietet und Sie den Dienst nicht direkt bei Microsoft oder bei einem anderen Partner erwerben können, ziehen Sie in Betracht, sich für eine kostenlose Testversion zu registrieren.

## <a name="sign-up-for-a-free-trial"></a>Registrieren für eine kostenlose Testversion

Sie können sich für eine kostenlose Testversion von Power BI registrieren. Wenn Sie Power BI Pro am Ende des Testzeitraums nicht erwerben, steht Ihnen dennoch weiterhin eine kostenlose Lizenz zur Verfügung, mit denen Sie viele Power BI-Features nutzen können. Weitere Informationen finden Sie unter [Registrieren für Power BI als Einzelperson](service-self-service-signup-for-power-bi.md).

### <a name="enable-ad-hoc-subscriptions"></a>Aktivieren von Ad-hoc-Abonnements

Standardmäßig sind individuelle Registrierungen (sogenannte Ad-hoc-Abonnements) deaktiviert. In diesem Fall wird die folgende Meldung angezeigt, wenn Sie versuchen, sich zu registrieren: *Ihre IT-Abteilung hat die Registrierung für Microsoft Power BI deaktiviert*.

![Abbildung der Meldung](media/service-admin-syndication-partner/sorry.png)

Um Ad-Hoc-Abonnements zu aktivieren können Sie sich an Ihren Partner wenden und ihn auffordern, sie zu aktivieren. Wenn Sie Administrator Ihres Mandanten sind und wissen, wie Azure Active Directory-PowerShell-Befehle genutzt werden, können Sie Ad-Hoc-Abonnements selbst aktivieren. [Azure Active Directory-PowerShell für Graph](/powershell/azure/active-directory/install-adv2/)

1. Melden Sie sich mithilfe Ihrer Office 365-Anmeldeinformationen bei Azure Active Directory an. In der ersten Zeile des unten stehenden Skripts werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben. Die zweite Zeile stellt die Verbindung mit Azure Active Directory her.

    ```powershell
    $msolcred = get-credential
    connect-msolservice -credential $msolcred
    ```

    ![Eingeben der Anmeldeinformationen](media/service-admin-syndication-partner/aad-signin.png)

1. Wenn Sie angemeldet sind, führen Sie den folgenden Befehl aus, um die aktuelle Einstellung für `AllowAdHocSubscriptions` zu überprüfen.

    ```powershell
    Get-MsolCompanyInformation
    ```

1. Führen Sie den folgenden Befehl aus, um kostenlose Registrierungen zu ermöglichen.

    ```powershell
    Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

## <a name="next-steps"></a>Weitere Schritte

[Power BI licensing in your organization (Power BI-Lizenzierung in Ihrem Unternehmen)](service-admin-licensing-organization.md)

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)