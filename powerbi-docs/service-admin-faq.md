---
title: Verwalten von Power BI – häufig gestellte Fragen (FAQ)
description: Erfahren Sie die Antworten auf häufig gestellte Fragen zu Power BI-Registrierung, Mandantenverwaltung und anderen Verwaltungsaufgaben.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 0c9d346017dc3b18abd6a56d0d3a62e1305e6575
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698737"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Verwalten von Power BI – häufig gestellte Fragen (FAQ)

Dieser Artikel behandelt häufig gestellte Fragen zur Power BI-Verwaltung. Einen Überblick über die Power BI-Verwaltung finden Sie unter [Was ist die Power BI-Verwaltung?](service-admin-administering-power-bi-in-your-organization.md).

## <a name="whats-in-this-article"></a>Inhalt dieses Artikels

### <a name="sign-up-for-power-bi-section"></a>Registrieren bei Power BI

* [Verwenden von PowerShell](#using-powershell)
* [Wie können sich Benutzer für Power BI registrieren?](#how-do-users-sign-up-for-power-bi)
* [Wie können sich einzelne Benutzer aus meiner Organisation registrieren?](#how-do-individual-users-in-my-organization-sign-up)
* [Wie kann ich verhindern, dass Benutzer meinem vorhandenen Office 365-Mandanten beitreten?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [Wie kann ich Benutzern erlauben, meinem vorhandenen Office 365-Mandanten beizutreten?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [Wie prüfe ich, ob eine Sperre im Mandanten vorliegt?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Wie kann ich verhindern, dass vorhandene Benutzer mit der Nutzung von Power BI beginnen?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Wie kann ich meinen vorhandenen Benutzern erlauben, sich für Power BI zu registrieren?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Verwalten von Power BI

* [Wie ändert sich dadurch die Art und Weise, in der ich die Identitäten für Benutzer in meiner Organisation heute verwalte?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Wie verwalte ich Power BI?](#how-do-we-manage-power-bi)
* [Was ist der Prozess zum Verwalten eines Mandanten, der von Microsoft für meine Benutzer erstellt wurde?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Wenn ich mehrere Domänen habe, kann ich den Microsoft 365-Mandanten steuern, dem Benutzer hinzugefügt werden?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Wie entferne ich Power BI für Benutzer, die sich bereits registriert haben?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Wie erfahre ich, wenn meinem Mandanten neue Benutzer beigetreten sind?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Gibt es weitere Punkte, auf die ich mich vorbereiten sollte?](#are-there-any-additional-things-i-should-prepare-for)
* [Wo befindet sich mein Power BI-Mandant?](#where-is-my-power-bi-tenant-located)
* [Was ist das Power BI-SLA (Vereinbarung zum Servicelevel)?](#what-is-the-power-bi-sla)
* [Wie handhabt Power BI Hochverfügbarkeit und Failovers?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Sicherheit in Power BI

* [Erfüllt Power BI nationale, regionale und branchenspezifische Anforderungen an die Konformität?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Wie funktioniert die Sicherheit in Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Registrieren bei Power BI

### <a name="using-powershell"></a>Verwenden von PowerShell

Für einige der Verfahren in diesem Abschnitt sind Windows PowerShell-Skripts erforderlich. Wenn Sie mit PowerShell nicht vertraut sind, beginnen Sie am besten mit dem Leitfaden [Erste Schritte mit PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=286814). Installieren Sie zum Ausführen der Skripts zunächst die neueste 64-Bit-Version der [Azure Active Directory PowerShell für Graph](/powershell/azure/active-directory/).

### <a name="how-do-users-sign-up-for-power-bi"></a>Wie können sich Benutzer für Power BI registrieren?

Als Microsoft 365-Administrator können Sie sich auf der [Power BI-Website](https://powerbi.microsoft.com) oder im Microsoft 365 Admin Center auf der Seite [Dienste kaufen](https://admin.microsoft.com/AdminPortal/Home#/catalog) für Power BI registrieren. Wenn sich Microsoft 365-Administratoren für Power BI registrieren, können sie Benutzern, die Zugriff erhalten sollten, Benutzerlizenzen zuweisen.

Darüber hinaus können sich auch einzelne Benutzer in Ihrer Organisation auf der [Power BI-Website](https://powerbi.microsoft.com) für Power BI registrieren. Wenn sich ein Benutzer in Ihrer Organisation für Power BI registriert, wird dem Benutzer automatisch eine Power BI-Lizenz vom Dienst zugewiesen. Weitere Informationen finden Sie unter [Registrieren für Power BI als Einzelperson](service-self-service-signup-for-power-bi.md) und [Power BI-Lizenzierung in Ihrem Unternehmen](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Wie können sich einzelne Benutzer aus meiner Organisation registrieren?

Es gibt drei Szenarien, die ggf. für die Benutzer in Ihrer Organisation in Betracht kommen:

* **Szenario 1**: Ihre Organisation verfügt bereits über eine M 365-Umgebung, und der Benutzer, der sich für Power BI registriert, besitzt ein Microsoft 365-Konto.
    In diesem Szenario aktiviert Microsoft einfach den Power BI Free-Plan für das Konto, wenn der Benutzer bereits ein Geschäfts-, Schul- oder Unikonto für den Mandanten (z.B. „contoso.com“) hat, jedoch noch nicht über Power BI verfügt. Der Benutzer wird automatisch darüber benachrichtigt, wie er den Power BI-Dienst verwenden kann.

* **Szenario 2**: Ihre Organisation verfügt über eine Microsoft 365-Umgebung, doch der Benutzer, der sich für Power BI registriert, besitzt noch kein Microsoft 365-Konto.
    In diesem Szenario besitzt der Benutzer eine E-Mail-Adresse in der Domäne Ihrer Organisation (z.B. „contoso.com“), jedoch noch kein Microsoft 365-Konto. In diesem Fall kann sich der Benutzer für Power BI registrieren und erhält dann automatisch ein Konto. Durch diese Aktion erhalten Benutzer Zugriff auf den Power BI-Dienst. Wenn beispielsweise eine Mitarbeiterin namens Nancy ihre geschäftliche E-Mail-Adresse (z.B. nancy@contoso.com) für die Registrierung verwendet, fügt Microsoft Nancy automatisch der Microsoft 365-Umgebung von Contoso als Benutzerin hinzu und aktiviert Power BI für dieses Konto.

* **Szenario 3**: Ihre Organisation verfügt über keine Microsoft 365-Umgebung, die mit Ihrer E-Mail-Domäne verbunden ist.
    Es gibt keine administrativen Aktionen, die Ihre Organisation unternehmen muss, um die Vorteile von Power BI zu nutzen. Der Dienst fügt Benutzer einem neuen, ausschließlich cloudseitigen Benutzerverzeichnis hinzu. Sie haben auch die Möglichkeit, deren Verwaltung als globaler Microsoft 365-Administrator für den Mandanten zu übernehmen.

> [!IMPORTANT]
> Wenn Ihre Organisation über mehrere E-Mail-Domänen verfügt und Sie alle E-Mail-Adresserweiterungen in demselben Mandanten zusammenfassen möchten, fügen Sie alle E-Mail-Adressdomänen einem Azure Active Directory-Mandanten hinzu, bevor sich die einzelnen Benutzer registrieren. Nachdem Sie Benutzer erstellt haben, gibt es keine automatisierten Verfahren zum Verschieben von Benutzern zwischen Mandanten. Weitere Informationen dazu finden Sie weiter unten in diesem Artikel unter [Wenn ich mehrere Domänen habe, kann ich den Microsoft 365-Mandanten steuern, dem Benutzer hinzugefügt werden?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) und unter [Hinzufügen einer Domäne zu Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>Wie kann ich verhindern, dass Benutzer meinem vorhandenen Microsoft 365-Mandanten beitreten?

Sie können als globaler Microsoft 365-Administrator Schritte unternehmen, die verhindern, dass Benutzer Ihren vorhandenen Microsoft 365-Mandanten beitreten. Wenn Sie den Zugriff blockieren, können sich keine Benutzer registrieren. Es wird eine Nachricht angezeigt, in der die Benutzer aufgefordert werden, sich mit dem Administrator Ihrer Organisation in Verbindung zu setzen. Sie müssen diesen Vorgang nicht wiederholen, wenn Sie die automatische Verteilung von Lizenzen (z.B. Office 365 Education für Studenten, Bildungseinrichtungen und Lehrpersonal) bereits deaktiviert haben.

Verwenden Sie das folgende PowerShell-Skript, um zu verhindern, dass neue Benutzer einem verwalteten Mandanten beitreten. ([Hier erfahren Sie mehr über PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Die Zugriffssperre verhindert, dass sich neue Benutzer in Ihrer Organisation für Power BI registrieren. Benutzer, die sich für Power BI registriert haben, bevor Sie neue Registrierungen für Ihre Organisation deaktiviert haben, behalten ihre Lizenzen jedoch. Wie Sie Benutzer entfernen, erfahren Sie weiter unten in diesem Artikel unter [Wie entferne ich Power BI für Benutzer, die sich bereits registriert haben?](#how-do-i-remove-power-bi-for-users-that-already-signed-up).

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>Wie kann ich Benutzern erlauben, meinem vorhandenen Microsoft 365-Mandanten beizutreten?

Verwenden Sie das folgende PowerShell-Skript, damit neue Benutzer einem verwalteten Mandanten beitreten können. ([Hier erfahren Sie mehr über PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Wie prüfe ich, ob eine Sperre im Mandanten vorliegt?

Verwenden Sie das folgende PowerShell-Skript zum Prüfen der Einstellungen. *AllowEmailVerifiedUsers* muss auf FALSE festgelegt sein. ([Hier erfahren Sie mehr über PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Wie kann ich verhindern, dass vorhandene Benutzer mit der Nutzung von Power BI beginnen?

Die entsprechende Azure AD-Einstellung ist **AllowAdHocSubscriptions**. Für die meisten Mandanten ist sie auf *TRUE* festgelegt. Das bedeutet, dass sie aktiviert ist. Wenn Sie Power BI über einen Partner erworben haben, kann die Einstellung jedoch auf *FALSE* festgelegt sein, was bedeutet, dass sie deaktiviert ist.

Verwenden Sie das folgende PowerShell-Skript, um Ad-hoc-Abonnements zu deaktivieren. ([Erfahren Sie mehr über PowerShell][1].)

1. Melden Sie sich mithilfe Ihrer Microsoft 365-Anmeldeinformationen bei Azure Active Directory an. In der ersten Zeile des folgenden PowerShell-Skripts werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben. Die zweite Zeile stellt die Verbindung mit Azure Active Directory her.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Screenshot der Azure Active Directory-Anmeldung über PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Nachdem Sie sich angemeldet haben, führen Sie den folgenden Befehl aus, um festzustellen, wie Ihr Mandant derzeit eingerichtet ist.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Führen Sie den folgenden Befehl aus, um **AllowAdHocSubscriptions** zu aktivieren (`$true`) oder zu deaktivieren (`$false`).

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Verwenden Sie das Flag **AllowAdHocSubscriptions**, um verschiedene Benutzeroptionen in Ihrer Organisation zu steuern, einschließlich der Möglichkeit, dass Benutzer sich beim Azure Rights Management Service registrieren können. Das Ändern dieses Flags wirkt sich auf all diese Optionen aus. Mit der Einstellung *false* können Benutzer sich weiterhin für eine individuelle Power BI Pro-Testversion registrieren.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Wie kann ich meinen vorhandenen Benutzern erlauben, sich für Power BI zu registrieren?

Damit sich vorhandene Benutzer für Power BI registrieren können, führen Sie den Befehl für die vorherige Frage aus, übergeben Sie im letzten Schritt jedoch `$true` anstelle von `$false`.

## <a name="administration-of-power-bi"></a>Verwaltung von Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Wie ändert sich dadurch die Art und Weise, in der ich die Identitäten für Benutzer in meiner Organisation heute verwalte?

Es gibt drei Szenarien, die ggf. für die Benutzer in Ihrer Organisation in Betracht kommen:

* **Szenario 1**: Wenn Ihre Organisation bereits über eine Microsoft 365-Umgebung verfügt, und alle Benutzer in der Organisation Microsoft 365-Konten besitzen, ändert sich die Identitätsverwaltung nicht.

* **Szenario 2**: Wenn Ihre Organisation bereits über eine Microsoft 365-Umgebung verfügt, jedoch nicht alle Benutzer in Ihrer Organisation Microsoft 365-Konten haben, wird ein Benutzer im Mandanten erstellt, und Lizenzen werden anhand der Geschäfts-, Schul- oder Uni-E-Mail-Adresse des Benutzers zugewiesen.

    Dadurch steigt die Anzahl von Benutzern, die Sie zu einem bestimmten Zeitpunkt verwalten, wenn sich Benutzer in Ihrer Organisation für den Dienst registrieren.

* **Szenario 3**: Wenn Ihre Organisation nicht über eine Microsoft 365-Umgebung verfügt, die mit Ihrer E-Mail-Domäne verbunden ist, ändert sich die Identitätsverwaltung nicht.

    Der Dienst fügt Benutzer einem neuen, exklusiv für die Cloud angelegten Benutzerverzeichnis hinzu, dessen Verwaltung Sie als globaler Microsoft 365-Administrator übernehmen können.

### <a name="how-do-we-manage-power-bi"></a>Wie verwalte ich Power BI?

Power BI stellt ein Power BI-Verwaltungsportal für Benutzer mit der globalen Administratorrolle für Microsoft 365 und Benutzer mit der Administratorrolle für den Power BI-Dienst zur Verfügung. Damit Sie das Power BI-Verwaltungsportal verwenden können, müssen Sie Ihr Konto in Microsoft 365 oder Azure Active Directory als **Globaler Administrator** kennzeichnen, oder Ihrem Benutzerkonto muss die Power BI-Dienstadministratorrolle zugewiesen werden. Weitere Informationen finden Sie unter [Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md) und [Power BI-Verwaltungsportal](service-admin-portal.md). Das Portal bietet die Möglichkeit, die mandantenweiten Einstellungen zu steuern, Power BI-Nutzungsstatistiken anzuzeigen und enthält einen Link zum Microsoft 365 Admin Center zur Verwaltung von Benutzern und Gruppen.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Was ist der Prozess zum Verwalten eines Mandanten, der von Microsoft für meine Benutzer erstellt wurde?

Wenn sich ein Self-Service-Benutzer für einen Clouddienst mit Azure AD registriert, fügt ihn der Dienst basierend auf seiner E-Mail-Domäne einem nicht verwalteten Azure AD-Verzeichnis hinzu. Sie können einen von einem anderen Benutzer erstellten Mandanten über einen Prozess mit der Bezeichnung *Administratorübernahme* beanspruchen und verwalten. Weitere Informationen finden Sie unter [Übernehmen eines nicht verwalteten Verzeichnisses als Administrator in Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover). Die Art der Übernahme hängt davon ab, ob es einen bestehenden verwalteten Mandanten gibt, der mit Ihrer Domäne verbunden ist:

* Power BI unterstützt die interne Administratorübernahme. Wenn Sie eine _interne_ Administratorübernahme eines nicht verwalteten Azure-Verzeichnisses ausführen, werden Sie als globaler Administrator des nicht verwalteten Verzeichnisses hinzugefügt. Es werden keine Benutzer, Domänen oder Dienste zu anderen von Ihnen verwalteten Verzeichnissen migriert.

* Power BI unterstützt die externe Administratorübernahme nicht mehr. Beim Durchführen einer _externen_ Administratorübernahme fügen Sie den DNS-Domänennamen des nicht verwalteten Verzeichnisses Ihrem verwalteten Azure-Verzeichnis hinzu. Eine externe Übernahme führt zum Verlust des Zugriffs auf sämtliche Power BI-Inhalte in dem ursprünglichen unverwalteten Mandanten. Power BI-Berichte müssen im neuen Mandanten erneut veröffentlicht werden, und Power BI-Dashboards und -Apps müssen im neuen Mandanten neu erstellt werden.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Wenn ich mehrere Domänen habe, kann ich den Microsoft 365-Mandanten steuern, dem Benutzer hinzugefügt werden?

Wenn Sie nichts unternehmen, erstellt der Dienst einen Mandanten für jede E-Mail-Domäne und -Unterdomäne für Benutzer. Wenn sich alle Benutzer unabhängig von ihren E-Mail-Adresserweiterungen in demselben Mandanten befinden sollen, gehen Sie folgendermaßen vor: Erstellen Sie einen Zielmandanten im Voraus, oder verwenden Sie einen vorhandenen Mandanten. Fügen Sie dann alle vorhandenen Domänen und Unterdomänen hinzu, die in diesem Mandanten konsolidiert werden sollen. Alle Benutzer, deren E-Mail-Adressen auf diese Domänen und Unterdomänen enden, treten bei der Registrierung automatisch dem Zielmandanten bei.

> [!IMPORTANT]
> Nachdem Sie Benutzer erstellt haben, gibt es keine unterstützten automatisierten Verfahren zum Verschieben von Benutzern zwischen Mandanten. Informationen zum Hinzufügen von Domänen zu einem einzelnen Microsoft 365-Mandanten finden Sie unter dem Thema zum [Hinzufügen von Benutzern und Domänen zu Office 365](/office365/admin/setup/add-domain/).

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Wie entferne ich Power BI für Benutzer, die sich bereits registriert haben?

Wenn sich ein Benutzer für Power BI registriert hat, Sie aber nicht möchten, dass er weiterhin auf Power BI zugreifen kann, können Sie die Power BI-Lizenz für diesen Benutzer entfernen.

1. Navigieren Sie zum [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Wählen Sie im Navigationsbereich **Benutzer** > **Aktive Benutzer** aus.

1. Suchen Sie den Benutzer, dessen Lizenz Sie entfernen möchten, und wählen Sie seinen Namen aus.

    Sie können auch eine Batchverwaltung von Benutzerlizenzen durchführen. Wählen Sie dazu mehrere Benutzer und dann **Produktlizenzen bearbeiten** aus.

1. Wählen Sie auf der Seite „Benutzerdetails“ neben **Produktlizenzen** **Bearbeiten** aus.

1. Je nachdem, welche Lizenz für das jeweilige Konto gilt, legen Sie **Power BI Free** oder **Power BI Pro** auf **Aus** fest.

1. Wählen Sie **Speichern**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Wie erfahre ich, wenn meinem Mandanten neue Benutzer beigetreten sind?

Benutzern, die Ihrem Mandanten durch Self Service-Registrierung beigetreten sind, wird eine eindeutige Lizenz zugewiesen, nach der Sie innerhalb Ihres aktiven Benutzerbereichs im Verwaltungsdashboard filtern können. Gehen Sie wie folgt vor, um diese neue Ansicht zu erstellen.

1. Navigieren Sie zum [Microsoft 365 Admin Center](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Wählen Sie im Navigationsbereich **Benutzer** > **Aktive Benutzer** aus.

1. Wählen Sie im Menü **Ansichten** die Option **Benutzerdefinierte Ansicht hinzufügen** aus.

1. Benennen Sie die neue Ansicht, und wählen Sie unter **Zugewiesene Produktlizenz** **Power BI Free** oder **Power BI Pro** aus.

    Sie können nur eine Lizenz pro Ansicht auswählen. Wenn Sie in Ihrer Organisation über die beide Lizenzen **Power BI Free** und **Power BI Pro** verfügen, können Sie zwei Ansichten erstellen.

1. Geben Sie alle anderen gewünschten Bedingungen ein, und wählen Sie dann **Hinzufügen** aus.

1. Nachdem Sie die neue Ansicht erstellt haben, ist sie im Menü **Ansichten** verfügbar.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Gibt es weitere Punkte, auf die ich mich vorbereiten sollte?

Es kann häufiger zur Anfragen zur Kennwortrücksetzung kommen. Weitere Informationen zu diesem Vorgang finden Sie unter [Zurücksetzen eines Benutzerkennworts](/office365/admin/add-users/reset-passwords).

Sie können einen Benutzer über den Standardprozess im Microsoft 365 Admin Center aus Ihrem Mandanten entfernen. Wenn der Benutzer jedoch weiterhin über eine aktive E-Mail-Adresse in Ihrer Organisation verfügt, kann er erneut beitreten, es sei denn, Sie sperren den Beitritt für alle Benutzer.

### <a name="where-is-my-power-bi-tenant-located"></a>Wo befindet sich mein Power BI-Mandant?

Weitere Informationen zum Datenbereich Ihres Power BI-Mandanten finden Sie unter [Wo befindet sich mein Power BI-Mandant?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Was ist das Power BI-SLA?

Informationen zur Power BI-SLA (Vereinbarung zum Servicelevel) finden Sie auf der Microsoft-Website zur Lizenzierung im Bereich **Lizenzierung** im Artikel [Lizenzierungsbedingungen und Dokumentation](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Wie handhabt Power BI Hochverfügbarkeit und Failovers?

Informationen zur Hochverfügbarkeit und zu Failovers finden Sie in den [Power BI-FAQ zur Hochverfügbarkeit und Notfallwiederherstellung sowie zu Failovers](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Sicherheit in Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Erfüllt Power BI nationale, regionale und branchenspezifische Anforderungen an die Konformität?

Weitere Informationen zur Power BI-Konformität finden Sie im [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Wie funktioniert die Sicherheit in Power BI?

Microsoft hat Power BI auf der Grundlage von Microsoft 365 entwickelt, das wiederum auf Azure-Diensten wie Azure Active Directory basiert. Eine Übersicht über die Power BI-Architektur finden Sie unter [Sicherheit in Power BI](service-admin-power-bi-security.md).

## <a name="next-steps"></a>Nächste Schritte

[Power BI-Verwaltungsportal](service-admin-portal.md)  
[Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md)  
[Self-Service-Registrierung für Power BI](service-self-service-signup-for-power-bi.md)  
[Erwerb von Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Was ist Power BI Premium?](service-premium-what-is.md)  
[Erwerben von Power BI Premium](service-admin-premium-purchase.md)  
[Power BI Premium-Whitepaper](https://aka.ms/pbipremiumwhitepaper)  
[Verwalten Ihrer Gruppe in Power BI und Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365-Benutzerkontenverwaltung](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Office 365-Gruppenverwaltung](/office365/admin/email/create-edit-or-delete-a-security-group/)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
