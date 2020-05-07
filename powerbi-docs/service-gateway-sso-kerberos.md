---
title: Konfigurieren des Kerberos-basierten einmaligen Anmeldens (Single Sign-On, SSO) im Power BI-Dienst bei lokalen Datenquellen
description: Konfigurieren des Gateways mit Kerberos für SSO von Power BI bei lokalen Datenquellen
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 02/20/2020
LocalizationGroup: Gateways
ms.openlocfilehash: aacab1541f336ed12c36dab8243d0096c9a6ed19
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77558659"
---
# <a name="configure-kerberos-based-sso-from-power-bi-service-to-on-premises-data-sources"></a>Konfigurieren des Kerberos-basierten einmaligen Anmeldens (Single Sign-On, SSO) im Power BI-Dienst bei lokalen Datenquellen

Durch das Aktivieren von SSO für Power BI-Berichte und -Dashboards können Daten aus lokalen Datenquellen unter Beachtung der für diese Quellen konfigurierten Benutzerberechtigungen einfacher aktualisiert werden. Verwenden Sie die [eingeschränkte Kerberos-Delegierung](/windows-server/security/kerberos/kerberos-constrained-delegation-overview), um eine nahtlose SSO-Konnektivität zu ermöglichen. 

## <a name="prerequisites"></a>Voraussetzungen

Damit die eingeschränkte Kerberos-Delegierung ordnungsgemäß funktioniert, müssen verschiedene Elemente konfiguriert werden, u. a. _Dienstprinzipalnamen_ (SPN) und Delegierungseinstellungen für Dienstkonten.

### <a name="install-and-configure-the-microsoft-on-premises-data-gateway"></a>Installieren und Konfigurieren des lokalen Datengateways von Microsoft

Dieses lokale Datengateway unterstützt das direkte Upgrade sowie die _Übernahme der Einstellungen_ von vorhandenen Gateways.

### <a name="run-the-gateway-windows-service-as-a-domain-account"></a>Ausführen des Gateway-Windows-Diensts als Domänenkonto

In einer Standardinstallation wird das Gateway als Dienstkonto des lokalen Computers,**NT Service\PBIEgwService**, ausgeführt.

![Dienstkonto des lokalen Computers](media/service-gateway-sso-kerberos/service-account.png)

Zum Aktivieren der eingeschränkten Kerberos-Delegierung muss das Gateway als Domänenkonto ausgeführt werden, es sei denn, Ihre Instanz von Azure Active Directory (Azure AD) ist bereits mit Ihrer lokalen Active Directory-Instanz synchronisiert (mittels Azure AD DirSync/Connect). Weitere Informationen zum Wechseln zu einem Domänenkonto finden Sie unter [Ändern des Dienstkontos für das lokale Datengateway](/data-integration/gateway/service-gateway-service-account).

> [!NOTE]
> Wenn Azure AD Connect konfiguriert ist und Benutzerkonten synchronisiert werden, muss der Gatewaydienst zur Laufzeit keine lokalen Azure AD-Suchläufe ausführen. Stattdessen können Sie einfach die lokale Dienst-SID für den Gatewaydienst verwenden, um alle erforderlichen Konfigurationen in Azure AD vorzunehmen. Die in diesem Artikel beschriebenen Schritte für die Konfiguration der eingeschränkten Kerberos-Delegierung sind identisch mit den Konfigurationsschritten im Azure AD-Kontext. Sie werden auf das Computerobjekt des Gateways (entsprechend der Identifizierung anhand der Dienst-ID) in Azure AD statt auf das Domänenkonto angewendet.

## <a name="obtain-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Abrufen von Domänenadministratorrechten zum Konfigurieren von SPNs (SetSPN) und Einstellungen für die eingeschränkte Kerberos-Delegierung

Um SPNs und Kerberos-Delegierungseinstellungen zu konfigurieren, darf der Domänenadministrator keine Rechte an einen Benutzer ohne Domänenadministrationsrechte erteilen. Die empfohlenen Konfigurationsschritte werden im folgenden Abschnitt ausführlicher erläutert.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Konfigurieren der eingeschränkten Kerberos-Delegierung für das Gateway und die Datenquelle

Konfigurieren Sie als Domänenadministrator bei Bedarf einen SPN für das Domänenkonto des Gatewaydiensts sowie Delegierungseinstellungen für dieses Domänenkonto.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Konfigurieren eines SPN für das Gatewaydienstkonto

Ermitteln Sie zunächst, ob bereits ein SPN für das Domänenkonto erstellt wurde, das als Gatewaydienstkonto verwendet wird:

1. Starten Sie als Domänenadministrator das MMC-Snap-In (Microsoft Management Console) **Active Directory-Benutzer und -Computer**.

2. Klicken Sie im linken Bereich mit der rechten Maustaste auf den Domänennamen, wählen Sie **Suchen** aus, und geben Sie dann den Kontonamen des Gatewaydienstkontos ein.

3. Klicken Sie im Suchergebnis mit der rechten Maustaste auf das Gatewaydienstkonto, und wählen Sie **Eigenschaften** aus.

4. Wenn im Dialogfeld **Eigenschaften** die Registerkarte **Delegierung** angezeigt wird, wurde bereits ein SPN erstellt, sodass Sie mit [Festlegen des Typs der eingeschränkten Kerberos-Delegierung](#decide-on-the-type-of-kerberos-constrained-delegation-to-use) fortfahren können.

5. Wenn im Dialogfeld **Eigenschaften** keine Registerkarte **Delegierung** angezeigt wird, können Sie einen SPN für das Konto manuell erstellen, um sie zu aktivieren. Verwenden Sie das in Windows enthaltene [setspn-Tool](https://technet.microsoft.com/library/cc731241.aspx). (Für die SPN-Erstellung sind Domänenadministratorrechte erforderlich.)

   Angenommen, das Konto des Gatewaydiensts ist **Contoso\GatewaySvc**, und der Gatewaydienst wird auf einem Computer mit dem Namen **MyGatewayMachine** ausgeführt. Zum Festlegen des SPN für das Gatewaydienstkonto führen Sie den folgenden Befehl aus:

   ```setspn -a gateway/MyGatewayMachine Contoso\GatewaySvc```

   Sie können den SPN auch über das MMC-Snap-In **Active Directory-Benutzer und -Computer** festlegen.
   
### <a name="add-gateway-service-account-to-windows-authorization-and-access-group-if-required"></a>Hinzufügen eines Gatewaydienstkontos zur Windows-Autorisierungs- und -Zugriffsgruppe bei Bedarf

In einigen Szenarien muss das Gatewaydienstkonto zur Windows-Autorisierungs- und -Zugriffsgruppe hinzugefügt werden. Hierzu gehören Szenarien der Sicherheitshärtung der Active Directory-Umgebung sowie Situationen, in denen sich das Gatewaydienstkonto und die Benutzerkonten, deren Identität das Gateway annimmt, in getrennten Domänen oder Gesamtstrukturen befinden. Sie können das Gatewaydienstkonto auch dann zur Windows-Autorisierungs- und -Zugriffsgruppe hinzufügen, wenn für die Domäne bzw. Gesamtstruktur keine Härtung erfolgt ist, dies ist aber nicht erforderlich.

Weitere Informationen finden Sie unter [Windows-Autorisierungs- und -Zugriffsgruppe](/windows/security/identity-protection/access-control/active-directory-security-groups#bkmk-winauthaccess).

Um diesen Konfigurationsschritt abzuschließen, gehen Sie bei jeder Domäne mit Active Directory-Benutzern, deren Identität das Gatewaydienstkonto annehmen soll, folgendermaßen vor:
1. Melden Sie sich bei einem Computer in der Domäne an, und starten Sie das MMC-Snap-In „Active Directory-Benutzer und -Computer“.
2. Suchen Sie die **Windows-Autorisierungs- und Zugriffsgruppe**. Diese befindet sich in der Regel im Container **Builtin**.
3. Doppelklicken Sie auf die Gruppe, und klicken Sie auf die Registerkarte **Mitglieder**.
4. Klicken Sie auf **Hinzufügen**, und ändern Sie den Domänenstandort zu der Domäne, in der sich das Gatewaydienstkonto befindet.
5. Geben Sie den Namen des Gatewaydienstkontos an, und klicken Sie auf **Namen überprüfen**, um zu überprüfen, ob auf das Gatewaydienstkonto zugegriffen werden kann.
6. Klicken Sie auf **OK**.
7. Klicken Sie auf **Übernehmen**.
8. Starten Sie den Gatewaydienst neu.

### <a name="decide-on-the-type-of-kerberos-constrained-delegation-to-use"></a>Festlegen des Typs der eingeschränkten Kerberos-Delegierung

Sie können Delegierungseinstellungen entweder für die standardmäßige eingeschränkte Kerberos-Delegierung oder die ressourcenbasierte eingeschränkte Kerberos-Delegierung konfigurieren. Verwenden Sie die ressourcenbasierte Delegierung (Windows Server 2012 oder höher erforderlich), wenn Ihre Datenquelle zu einer anderen Domäne als Ihr Gateway gehört. Weitere Informationen zu den Unterschieden zwischen den beiden Delegierungsansätzen finden Sie auf der [Übersichtsseite zur eingeschränkten Kerberos-Delegierung](/windows-server/security/kerberos/kerberos-constrained-delegation-overview).

 Je nachdem, welchen Ansatz Sie verwenden möchten, fahren Sie mit einem der folgenden Abschnitte fort. Führen Sie nicht beide Abschnitte aus:
 - [Konfigurieren des Gatewaydienstkontos für die standardmäßige eingeschränkte Kerberos-Delegierung](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation)
- [Konfigurieren des Gatewaydienstkontos für die ressourcenbasierte eingeschränkte Kerberos-Delegierung](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation) 

## <a name="configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation"></a>Konfigurieren des Gatewaydienstkontos für die standardmäßige eingeschränkte Kerberos-Delegierung

> [!NOTE]
> Führen Sie die Schritte in diesem Abschnitt aus, wenn Sie die [standardmäßige eingeschränkte Kerberos-Delegierung](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) aktivieren möchten. Wenn Sie die ressourcenbasierte eingeschränkte Kerberos-Delegierung aktivieren möchten, führen Sie andernfalls die Schritte in [Konfigurieren des Gatewaydienstkontos für die ressourcenbasierte eingeschränkte Kerberos-Delegierung](#configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation) aus.

Wir legen nun die Delegierungseinstellungen für das Gatewaydienstkonto fest. Es gibt verschiedene Tools, mit denen Sie diese Schritte ausführen können. Hier verwenden wir das MMC-Snap-In **Active Directory-Benutzer und -Computer** zur Verwaltung und Veröffentlichung von Informationen im Verzeichnis. Es steht auf Domänencontrollern standardmäßig zur Verfügung, doch Sie können es auch über die Konfiguration von Windows-Features auf anderen Computern aktivieren.

Wir müssen die eingeschränkte Kerberos-Delegierung mit Protokollübertragung konfigurieren. Bei der eingeschränkten Delegierung müssen Sie explizit angeben, für welche Dienste Sie dem Gateway erlauben möchten, delegierte Anmeldeinformationen vorzulegen. Delegierungsaufrufe des Gatewaydienstkontos werden beispielsweise nur von SQL Server oder Ihrem SAP HANA-Server akzeptiert.

In diesem Abschnitt wird davon ausgegangen, dass Sie bereits SPNs für die zugrunde liegenden Datenquellen (wie SQL Server, SAP HANA, SAP BW, Teradata oder Spark) konfiguriert haben. Um zu erfahren, wie Sie diese SPNs des Datenquellenservers konfigurieren können, lesen Sie die technische Dokumentation des jeweiligen Datenbankservers und außerdem Sie den Abschnitt *What SPN does your app require?* (Welcher SPN ist für Ihre App erforderlich?) im Blogbeitrag [My Kerberos Checklist](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160) (Meine Kerberos-Checkliste).

In den folgenden Schritten wird davon ausgegangen, dass Sie über eine lokale Umgebung mit zwei Computern in derselben Domäne verfügen: einem Gatewaycomputer und einem Datenbankserver mit SQL Server, die bereits mit auf Kerberos basierendem SSO konfiguriert sind. Die Schritte können für eine der anderen unterstützten Datenquellen übernommen werden, sofern die Datenquelle bereits für Kerberos-basiertes SSO konfiguriert wurde. In diesem Beispiel geben wir die folgenden Einstellungen:

* Active Directory-Domäne (NetBIOS): **Contoso**
* Name des Gatewaycomputers: **MyGatewayMachine**
* Gatewaydienstkonto: **Contoso\GatewaySvc**
* Computername der SQL Server-Datenquelle: **TestSQLServer**
* Dienstkonto der SQL Server-Datenquelle: **Contoso\SQLService**

Konfigurieren Sie die Delegierungseinstellungen wie folgt:

1. Öffnen Sie das MMC-Snap-In **Active Directory-Benutzer und -Computer** mit Domänenadministratorrechten.

2. Klicken Sie mit der rechten Maustaste auf das Gatewaydienstkonto (**Contoso\GatewaySvc**), und wählen Sie **Eigenschaften** aus.

3. Wählen Sie die Registerkarte **Delegierung** aus.

4. Wählen Sie **Computer nur bei Delegierungen angegebener Dienste vertrauen** > **Beliebiges Authentifizierungsprotokoll verwenden** aus.

5. Wählen Sie unter **Dienste, für die dieses Konto delegierte Anmeldeinformationen verwenden kann** die Option **Hinzufügen** aus.

6. Wählen Sie im Dialogfeld „Neu“ **Benutzer oder Computer** aus.

7. Geben Sie das Dienstkonto für die Datenquelle ein, und wählen Sie dann **OK** aus.

   Beispielsweise kann eine SQL Server-Datenquelle ein Dienstkonto wie *Contoso\SQLService* haben. Auf diesem Konto sollte bereits ein entsprechender Dienstprinzipalname für die Datenquelle festgelegt sein. 

8. Wählen Sie den SPN aus, den Sie für den Datenbankserver erstellt haben. 

   In unserem Beispiel beginnt der SPN mit *MSSQLSvc*. Wenn Sie sowohl den FQDN als auch den NetBIOS-SPN für den Datenbankdienst hinzugefügt haben, wählen Sie beide aus. Möglicherweise wird nur einer angezeigt.

9. Wählen Sie **OK** aus. 

   Der Dienstprinzipalname sollte nun in der Liste der Dienste aufgeführt werden, für die das Gatewaydienstkonto delegierte Anmeldeinformationen verwenden kann.

    ![Dialogfeld „Eigenschaften von Gatewayconnector“](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

10. Um das Setup fortzusetzen, fahren Sie als Nächstes mit [Erteilen von lokalen Richtlinienrechten auf dem Gatewaycomputer für das Gatewaydienstkonto](#grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine) fort.

## <a name="configure-the-gateway-service-account-for-resource-based-kerberos-constrained-delegation"></a>Konfigurieren des Gatewaydienstkontos für die ressourcenbasierte eingeschränkte Kerberos-Delegierung

> [!NOTE]
> Führen Sie die Schritte in diesem Abschnitt aus, wenn Sie die [ressourcenbasierte eingeschränkte Kerberos-Delegierung](/windows-server/security/kerberos/kerberos-constrained-delegation-overview#resource-based-constrained-delegation-across-domains) aktivieren möchten. Wenn Sie die standardmäßige eingeschränkte Kerberos-Delegierung aktivieren möchten, führen Sie andernfalls die Schritte in [Konfigurieren des Gatewaydienstkontos für die standardmäßige eingeschränkte Kerberos-Delegierung](#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation) aus.

Verwenden Sie die [ressourcenbasierte eingeschränkte Kerberos-Delegierung](/windows-server/security/kerberos/kerberos-constrained-delegation-overview#resource-based-constrained-delegation-across-domains), um SSO-Konnektivität für Windows Server 2012 und höhere Versionen zu ermöglichen. Dieser Delegierungstyp lässt zu, dass sich Front-End- und Back-End-Dienste in unterschiedlichen Domänen befinden. Damit dies funktioniert, muss die Domäne des Back-End-Diensts der Domäne des Front-End-Diensts vertrauen.

In den folgenden Schritten wird davon ausgegangen, dass Sie eine lokale Umgebung mit zwei Computern in unterschiedlichen Domänen haben: einem Gatewaycomputer und einem Datenbankserver mit SQL Server, die bereits mit Kerberos-basiertem SSO konfiguriert sind. Die Schritte können für eine der anderen unterstützten Datenquellen übernommen werden, sofern die Datenquelle bereits für Kerberos-basiertes SSO konfiguriert wurde. In diesem Beispiel geben wir die folgenden Einstellungen:

* Active Directory-Front-End-Domäne (NetBIOS): **ContosoFrontEnd**
* Active Directory-Back-End-Domäne (NetBIOS): **ContosoBackEnd**
* Name des Gatewaycomputers: **MyGatewayMachine**
* Gatewaydienstkonto: **ContosoFrontEnd\GatewaySvc**
* Computername der SQL Server-Datenquelle: **TestSQLServer**
* Dienstkonto der SQL Server-Datenquelle: **ContosoBackEnd\SQLService**

Führen Sie die folgenden Konfigurationsschritte aus:

1. Stellen Sie mithilfe des MMC-Snap-Ins **Active Directory-Benutzer und -Computer** auf dem Domänencontroller für die Domäne **ContosoFrontEnd** sicher, dass für das Gatewaydienstkonto keine Delegierungseinstellungen angewendet wurden.

    ![Gatewayconnectoreigenschaften](media/service-gateway-sso-kerberos-resource/gateway-connector-properties.png)

2. Stellen Sie mithilfe von **Active Directory-Benutzer und -Computer** auf dem Domänencontroller für die Domäne **ContosoBackEnd** sicher, dass für das Back-End-Dienstkonto keine Delegierungseinstellungen gelten.

    ![SQL-Diensteigenschaften](media/service-gateway-sso-kerberos-resource/sql-service-properties.png)

3. Überprüfen Sie auf der Registerkarte **Attribut-Editor** der Kontoeigenschaften, dass das Attribut **msDS-AllowedToActOnBehalfOfOtherIdentity** nicht festgelegt ist.

    ![SQL-Dienstattribute](media/service-gateway-sso-kerberos-resource/sql-service-attributes.png)

4. Erstellen Sie in **Active Directory-Benutzer und -Computer** auf dem Domänencontroller für die Domäne **ContosoBackEnd** eine Gruppe. Fügen Sie das Gatewaydienstkonto **GatewaySvc** zur Gruppe **ResourceDelGroup** hinzu. 

    ![Gruppeneigenschaften](media/service-gateway-sso-kerberos-resource/group-properties.png)

5. Öffnen Sie die Eingabeaufforderung, und führen Sie auf dem Domänencontroller für die Domäne **ContosoBackEnd** die folgenden Befehle aus, um das Attribut **msDS-AllowedToActOnBehalfOfOtherIdentity** des Back-End-Dienstkontos zu aktualisieren:

    ```powershell
    $c = Get-ADGroup ResourceDelGroup
    Set-ADUser SQLService -PrincipalsAllowedToDelegateToAccount $c
    ```

6. In **Active Directory-Benutzer und -Computer** können Sie überprüfen, ob das Update auf der Registerkarte **Attribut-Editor** in den Eigenschaften für das Back-End-Dienstkonto angezeigt wird. 

## <a name="grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine"></a>Erteilen der lokalen Richtlinienrechte auf dem Gatewaycomputer für das Gatewaydienstkonto

Abschließend müssen dem Gatewaydienstkonto auf dem Computer, auf dem der Gatewaydienst (in diesem Beispiel **MyGatewayMachine**) ausgeführt wird, die lokalen Richtlinien **Annehmen der Clientidentität nach Authentifizierung** und **Einsetzen als Teil des Betriebssystems (SeTcbPrivilege)** erteilt werden. Führen Sie diese Konfiguration mit den lokalen Gruppenrichtlinien-Editor (**gpedit.msc**) aus.

1. Führen Sie auf dem Gatewaycomputer **gpedit.msc** aus.

2. Navigieren Sie zu **Richtlinie für „Lokaler Computer“** &gt; **Computerkonfiguration** &gt; **Windows-Einstellungen** &gt; **Sicherheitseinstellungen** &gt; **Lokale Richtlinien** &gt; **Zuweisen von Benutzerrechten**.

    ![Ordnerstruktur der Richtlinie für den lokalen Computer](media/service-gateway-sso-kerberos/user-rights-assignment.png)

3. Wählen Sie unter **Zuweisen von Benutzerrechten** in der Richtlinienliste den Eintrag **Annehmen der Clientidentität nach Authentifizierung** aus.

    ![Identität einer Clientrichtlinie annehmen](media/service-gateway-sso-kerberos/impersonate-client.png)
    
4. Klicken Sie mit der rechten Maustaste auf die Richtlinie, öffnen Sie **Eigenschaften**, und zeigen Sie dann die Liste der Konten an. 

    Die Liste muss das Gatewaydienstkonto enthalten (je nach Typ der eingeschränkten Delegierung **Contoso\GatewaySvc** oder **ContosoFrontEnd\GatewaySvc**).

5. Wählen Sie in der Liste der Richtlinien unter **Zuweisen von Benutzerrechten** den Eintrag **Als Teil des Betriebssystems fungieren (SeTcbPrivilege)** aus. Vergewissern Sie sich, dass das Gatewaydienstkonto in der Liste der Konten aufgeführt wird.

6. Starten Sie den Dienstprozess **Lokales Datengateway** neu.

### <a name="set-user-mapping-configuration-parameters-on-the-gateway-machine-if-necessary"></a>Festlegen von Konfigurationsparametern für die Benutzerzuordnung auf dem Gatewaycomputer (falls erforderlich)

Wenn Azure AD Connect nicht konfiguriert ist, führen Sie die folgenden Schritte aus, um einen Power BI-Dienstbenutzer einem lokalen Active Directory-Benutzer zuzuordnen. Jeder Active Directory Benutzer, der auf diese Weise zugeordnet wird, muss über SSO-Berechtigungen für Ihre Datenquelle verfügen. Weitere Informationen finden Sie in diesem [Guy in a Cube-Video](https://www.youtube.com/watch?v=NG05PG9aiRw).

1. Öffnen Sie die Hauptdatei für die Gatewaykonfiguration, „Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll“. Standardmäßig befindet sich diese Datei unter C:\Programme\Lokales Datengateway.

1. Legen Sie **ADUserNameLookupProperty** auf ein nicht verwendetes Active Directory-Attribut fest. In den folgenden Schritten verwenden wir `msDS-cloudExtensionAttribute1`. Dieses Attribut ist nur in Windows Server 2012 und höher verfügbar. 

1. Legen Sie **ADUserNameReplacementProperty** auf `SAMAccountName` fest, und speichern Sie dann die Konfigurationsdatei.

1. Klicken Sie auf der Registerkarte **Dienste** des Task-Managers mit der rechten Maustaste auf den Gatewaydienst, und wählen Sie **Neu starten** aus.

    ![Screenshot: Registerkarte „Dienste“ des Task-Managers](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Legen Sie für jeden Power BI-Dienstbenutzer, für den Sie Kerberos SSO aktivieren möchten, die Eigenschaft `msDS-cloudExtensionAttribute1` eines lokalen Active Directory-Benutzers (mit SSO-Berechtigung für Ihre Datenquelle) auf den vollständigen Benutzernamen (UPN) des Power BI-Dienstbenutzers fest. Wenn Sie sich beispielsweise als test@contoso.com beim Power BI-Dienst anmelden und diesen Benutzer einem lokalen Active Directory-Benutzer mit SSO-Berechtigungen, beispielsweise test@LOCALDOMAIN.COM, zuordnen möchten, legen Sie das Attribut `msDS-cloudExtensionAttribute1` des Benutzers auf test@contoso.com fest.

    Die Eigenschaft `msDS-cloudExtensionAttribute1` kann unter anderem über das MMC-Snap-In „Active Directory-Benutzer und -Computer“ festgelegt werden:
    
    1. Starten Sie **Active Directory-Benutzer und -Computer** als Domänenadministrator.
    
    1. Klicken Sie mit der rechten Maustaste auf den Domänennamen, wählen Sie **Suchen** aus, und geben Sie den Kontonamen des lokalen Active Directory-Benutzers ein, zu dem die Zuordnung erfolgen soll.
    
    1. Wählen Sie die Registerkarte **Attribute Editor** (Attribut-Editor) aus.
    
        Suchen Sie nach der Eigenschaft `msDS-cloudExtensionAttribute1`, und doppelklicken Sie darauf. Legen Sie den Wert auf den vollständigen Benutzernamen (UPN) fest, den Sie für die Anmeldung beim Power BI-Dienst verwenden.
    
    1. Wählen Sie **OK** aus.
    
        ![Fenster „Attribut-Editor für Zeichenfolgen“](media/service-gateway-sso-kerberos/edit-attribute.png)
    
    1. Klicken Sie auf **Übernehmen**. Vergewissern Sie sich in der Spalte **Value** (Wert), dass der korrekte Wert festgelegt wurde.

## <a name="complete-data-source-specific-configuration-steps"></a>Vervollständigen von datenquellenspezifischen Konfigurationsschritten

Für SAP HANA und SAP BW gelten zusätzliche datenquellenspezifische Konfigurationsanforderungen und Voraussetzungen, die erfüllt sein müssen, bevor Sie mit diesen Datenquellen eine SSO-Verbindung über das Gateway herstellen können. Weitere Informationen finden Sie unter [SAP HANA-Konfiguration](service-gateway-sso-kerberos-sap-hana.md) und auf der [ Konfigurationsseite für SAP BW – CommonCryptoLib (sapcrypto.dll)](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Es ist auch möglich, [SAP BW für die Verwendung mit der SNC-Bibliothek „gx64krb5“ zu konfigurieren](service-gateway-sso-kerberos-sap-bw-gx64krb.md), aber diese Bibliothek wird nicht empfohlen, da sie von SAP nicht mehr unterstützt wird. Sie sollten CommonCryptoLib _oder_ gx64krb5 als Ihre SNC-Bibliothek verwenden. Führen Sie nicht die Konfigurationsschritte für beide Bibliotheken aus.

> [!NOTE]
> Andere SNC-Bibliotheken funktionieren möglicherweise auch für einmaliges Anmelden bei SAP BW, werden aber von Microsoft nicht offiziell unterstützt.

## <a name="run-a-power-bi-report"></a>Ausführen eines Power BI-Berichts

Nach Abschluss aller Konfigurationsschritte können Sie in Power BI auf der Seite **Gateway verwalten** die von Ihnen verwendete Datenquelle für SSO konfigurieren. Wenn Sie über mehrere Gateways verfügen, stellen Sie sicher, dass Sie das Gateway auswählen, das Sie für Kerberos SSO konfiguriert haben. Sorgen Sie dann dafür, dass unter **Erweiterte Einstellungen** für die Datenquelle die Option **SSO über Kerberos für DirectQuery-Abfragen verwenden** oder **SSO über Kerberos für DirectQuery- und Importabfragen verwenden** für auf DirectQuery basierende Berichte und die Option **SSO über Kerberos für DirectQuery- und Importabfragen verwenden** für auf Aktualisierungen basierende Berichte aktiviert ist.

![Erweiterte Einstellungsoptionen](media/service-gateway-sso-kerberos/advanced-settings-02.png)

Wenn Sie einen auf DirectQuery basierenden Bericht in Power BI Desktop veröffentlichen und ihn einer Datenquelle zuordnen, für die die Option **SSO über Kerberos für DirectQuery-Abfragen verwenden** oder **SSO über Kerberos für DirectQuery- und Importabfragen verwenden** aktiviert ist, würde dieser Bericht Daten verwenden, auf die der Benutzer zugreifen kann, der dem (Azure) Active Directory-Benutzer entspricht, der sich beim Power BI-Dienst anmeldet.

Ähnlich verhält es sich, wenn Sie einen auf Aktualisierungen basierenden Bericht in Power BI Desktop veröffentlichen und ihn einer Datenquelle zuordnen, für die die Option **SSO über Kerberos für DirectQuery- und Importabfragen verwenden** aktiviert ist, und Sie müssen keine Anmeldeinformationen angeben. Die Aktualisierung wird im Kontext des aktiven Verzeichnisses des Besitzers des Datasets ausgeführt.

Wenn Sie den Bericht allerdings einer Datenquelle zuordnen, für die **SSO über Kerberos für DirectQuery- und Importabfragen verwenden** nicht aktiviert ist, verwendet die Aktualisierung die Anmeldeinformationen, die Sie in den Feldern **Benutzername** und **Kennwort** beim Erstellen der Datenquelle eingegeben haben. Das bedeutet, dass Kerberos-SSO *nicht* verwendet wird. 

 Wählen Sie beim Veröffentlichen das Gateway aus, das Sie für SSO konfiguriert haben, sofern Sie über mehrere Gateways verfügen. 

Diese Konfiguration funktioniert in den meisten Fällen. Bei Kerberos können jedoch je nach Umgebung unterschiedliche Konfigurationen vorhanden sein. Sollte der Bericht nicht geladen werden, wenden Sie sich zur weiteren Untersuchung an Ihren Domänenadministrator. Wenn SAP BW Ihre Datenquelle ist, können Sie, je nachdem, welche SNC-Bibliothek Sie ausgewählt haben, die Abschnitte zur Problembehandlung auf den datenquellenspezifischen Konfigurationsseiten für [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md#troubleshooting) und [gx64krb5/gsskrb5](service-gateway-sso-kerberos-sap-bw-gx64krb.md#troubleshooting) lesen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum lokalen Datengateway und zu DirectQuery finden Sie in den folgenden Ressourcen:

* [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
