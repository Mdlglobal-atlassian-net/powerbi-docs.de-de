---
title: Verwenden des Webanwendungsproxys und der Active Directory-Verbunddienste – Power BI-Berichtsserver
description: Erfahren Sie, wie Sie den Webanwendungsproxy (WAP) und die Active Directory-Verbunddienste (Active Directory Federated Services, AD FS) verwenden, um eine Verbindung mit dem Power BI-Berichtsserver sowie SQL Server Reporting Services (SSRS) 2016 und höher herzustellen.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 2caa96aceef90ad1d25a521cbf4a3f699a2a64e0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76042438"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Verwenden des Webanwendungsproxys und der Active Directory-Verbunddienste – Power BI-Berichtsserver

Dieser Artikel erläutert, wie Sie den Webanwendungsproxy (WAP) und die Active Directory-Verbunddienste (Active Directory Federated Services, AD FS) verwenden, um eine Verbindung mit dem Power BI-Berichtsserver sowie SQL Server Reporting Services (SSRS) 2016 und höher herzustellen. Durch diese Integration können Benutzer von außerhalb des Unternehmensnetzwerks über ihre Clientbrowser auf ihre Berichte aus dem Power BI-Berichtsserver und SSRS zugreifen und sind dabei per AD FS-Vorauthentifizierung geschützt. Für die mobilen Power BI-Apps müssen Sie auch [OAuth für die Verbindung mit dem Power BI-Berichtsserver und SSRS konfigurieren](../consumer/mobile/mobile-oauth-ssrs.md).

## <a name="prerequisites"></a>Voraussetzungen

### <a name="domain-name-services-dns-configuration"></a>DNS-Konfiguration (Domain Name Service)

- Ermitteln Sie die öffentliche URL, mit der Benutzer eine Verbindung herstellen. Diese sieht etwa so aus: `https://reports.contosolab.com`.
- Konfigurieren Sie den DNS-Eintrag für den Hostnamen – beispielsweise `reports.contosolab.com` – so, dass dieser auf die öffentliche IP-Adresse des WAP-Servers (Webanwendungsproxy) zeigt.
- Konfigurieren Sie einen öffentlichen DNS-Eintrag für den AD FS-Server. Ein Beispiel: Sie haben den AD FS-Server mit der folgenden URL konfiguriert: `https://adfs.contosolab.com`.
- Konfigurieren Sie den DNS-Eintrag für den Hostnamen so, dass dieser auf die öffentliche IP-Adresse des WAP-Servers zeigt, z. B. so: `adfs.contosolab.com`. Dieser wird als Teil der WAP-Anwendung veröffentlicht.

### <a name="certificates"></a>Zertifikate

Sie müssen sowohl für die WAP-Anwendung und als auch den AD FS-Server Zertifikate konfigurieren. Beide Zertifikate müssen zu einer gültigen Zertifizierungsstelle gehören, die von Ihren Geräten erkannt wird.

## <a name="1-configure-the-report-server"></a>1. Konfigurieren des Berichtsservers

Sie müssen sicherstellen, dass Sie über einen gültigen Dienstprinzipalnamen (Service Principal Name, SPN) verfügen. Mit dem gültigen SPN kann die korrekte Kerberos-Authentifizierung erfolgen, und dem Berichtsserver wird ermöglicht, die Authentifizierung auszuhandeln.

### <a name="service-principal-name-spn"></a>Dienstprinzipalname (Service Principal Name, SPN)

Bei dem SPN handelt es sich um einen eindeutigen Bezeichner für einen Dienst, der Kerberos-Authentifizierung verwendet. Stellen Sie sicher, dass ein gültiger HTTP-SPN für den Berichtsserver vorhanden ist.

Informationen zum Konfigurieren des richtigen Dienstprinzipalnamens (Service Principal Name, SPN) für den Berichtsserver finden Sie unter [Registrieren eines Dienstprinzipalnamens (SPN) für einen Berichtsserver](https://docs.microsoft.com/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server).

### <a name="enabling-negotiate-authentication"></a>Aktivieren der Aushandlungsauthentifizierung

Damit ein Berichtsserver die Kerberos-Authentifizierung verwenden kann, müssen Sie den Authentifizierungstyp des Berichtsservers als „RSWindowsNegotiate“ konfigurieren. Diese Konfiguration erfolgt in der Datei „rsreportserver.config“.

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

Weitere Informationen finden Sie unter [Ändern einer Reporting Services-Konfigurationsdatei (RSreportserver.config)](https://docs.microsoft.com/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config) und [Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver](https://docs.microsoft.com/sql/reporting-services/security/configure-windows-authentication-on-the-report-server).

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2. Konfigurieren der Active Directory-Verbunddienste

Sie müssen die Active Directory-Verbunddienste (Active Directory Federated Services, AD FS) auf einem Windows 2016-Server in Ihrer Umgebung konfigurieren. Die Konfiguration kann im Server-Manager unter „Verwalten“ mit Auswahl von „Rollen und Features hinzufügen“ erfolgen. Weitere Informationen finden Sie unter [Active Directory-Verbunddienste](https://docs.microsoft.com/windows-server/identity/active-directory-federation-services).

Führen Sie die folgenden Schritte in der AD FS-Verwaltungs-App auf dem AD FS-Server aus.

1. Klicken Sie mit der rechten Maustaste auf **Vertrauensstellungen der vertrauenden Seite** > **Vertrauensstellung der vertrauenden Seite hinzufügen**.

    ![Vertrauensstellung der vertrauenden Seite hinzufügen](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. Führen Sie die Schritte im **Assistenten zum Hinzufügen von Vertrauensstellungen der vertrauenden Seite** aus.

    Wählen Sie die Option **Ansprüche nicht unterstützend** aus, um die integrierte Windows-Sicherheit als Authentifizierungsmechanismus zu verwenden.

    ![Willkommen beim Assistenten zum Hinzufügen von Vertrauensstellungen der vertrauenden Seite](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    Geben Sie unter **Anzeigenamen angeben** den gewünschten Namen ein, und klicken Sie auf **Weiter**.
    Fügen Sie den Bezeichner der Vertrauensstellung der vertrauenden Seite hinzu: `<ADFS\_URL>/adfs/services/trust`.

    Beispiel: `https://adfs.contosolab.com/adfs/services/trust`

    ![Berichtsserver](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    Wählen Sie die **Zugriffssteuerungsrichtlinie** aus, die sich für Ihre Organisation am besten eignet, und klicken Sie auf **Weiter**.

    ![Zugriffssteuerung auswählen](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    Klicken Sie nacheinander auf **Weiter** und **Fertig stellen**, um den Assistenten zum **Hinzufügen von Vertrauensstellungen der vertrauenden Seite** abzuschließen.

    Nach Abschluss des Assistenten sollten die Eigenschaften der Vertrauensstellungen der vertrauenden Seite wie folgt aussehen.

    ![Vertrauensstellungen der vertrauenden Seite](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3. Konfigurieren des Webanwendungsproxys

Aktivieren Sie die Windows-Rolle „Webanwendungsproxy“ auf einem Server in Ihrer Umgebung. Dabei muss es sich um einen Windows 2016-Server handeln. Weitere Informationen finden Sie unter [Web-Anwendungsproxy in Windows Server 2016](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server) und [Veröffentlichen von Anwendungen mit AD FS-Vorauthentifizierung](https://docs.microsoft.com/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication).

### <a name="configure-constrained-delegation"></a>Konfigurieren der eingeschränkten Delegierung

Um von der Forms-Authentifizierung zur Windows-Authentifizierung zu wechseln, muss die eingeschränkte Delegierung mit Protokollübergang verwendet werden. Dieser Schritt ist Teil der Kerberos-Konfiguration. Sie haben bereits den SPN des Berichtsservers in der Berichtsserverkonfiguration definiert.

Nun muss die eingeschränkte Delegierung im Computerkonto des WAP-Servers in Active Directory konfiguriert werden. Möglicherweise müssen Sie einen Domänenadministrator hinzuziehen, wenn Sie keine Berechtigungen für Active Directory besitzen.

Führen Sie die folgenden Schritte aus, um die eingeschränkte Delegierung zu konfigurieren.

1. Starten Sie auf einem Computer mit Active Directory-Tools **Active Directory-Benutzer und -Computer**.
2. Suchen Sie das Computerkonto für den WAP-Server. Standardmäßig befindet dieses sich im Container **Computer**.
3. Klicken Sie mit der rechten Maustaste auf den WAP-Server, und wechseln Sie zu **Eigenschaften**.
4. Wählen Sie auf der Registerkarte **Delegierung** die Optionen **Computer nur bei Delegierungen angegebener Dienste vertrauen** und dann **Beliebiges Authentifizierungsprotokoll verwenden** aus.

    ![Diesem Computer vertrauen](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. Mit dieser Option wird die eingeschränkte Delegierung für das Computerkonto dieses WAP-Servers eingerichtet. Nun müssen die Dienste angegeben werden, an die dieser Computer delegieren kann.
2. Wählen Sie unter dem Feld „Dienste“ die Option **Hinzufügen** aus.

    ![Hinzufügen der Vertrauensstellung der AD FS](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. Wählen Sie **Benutzer oder Computer** aus.
2. Geben Sie das Dienstkonto ein, das Sie für den Berichtsserver verwenden. Hierbei handelt es sich um dasselbe Konto, das Sie weiter oben im Abschnitt [Konfigurieren des Berichtsservers](#1-configure-the-report-server) verwendet haben, um den HTTP-SPN hinzuzufügen. 

3. Wählen Sie den HTTP-SPN für den Berichtsserver aus, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Möglicherweise wird nur der NetBIOS-SPN angezeigt. Es werden aber sowohl der NetBIOS- als auch der FQDN-SPN ausgewählt, wenn beide vorhanden sind.

1. Wenn Sie das Kontrollkästchen **Erweitert** aktivieren, sollte das Ergebnis etwa wie das folgende Beispiel aussehen.

    ![WAP-Eigenschaften](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>Hinzufügen einer WAP-Anwendung

1. Öffnen Sie auf dem WAP-Server die Konsole **Remotezugriffsverwaltung**, und wählen Sie im Navigationsbereich **Webanwendungsproxy** aus. 

2. Klicken Sie im Bereich **Aufgaben** auf **Veröffentlichen**.

2. Klicken Sie auf der Begrüßungsseite auf **Weiter**.

    ![Willkommen beim Assistenten zum Veröffentlichen neuer Anwendungen](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. Wählen Sie auf der Seite **Vorauthentifizierung** die Option **Active Directory-Verbunddienste** aus, und klicken Sie dann auf **Weiter**.

    ![Vorauthentifizierung](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. Da Sie nur den Browserzugriff auf den Berichtsserver konfigurieren, nicht den Zugriff über eine mobile App, wählen Sie die Vorauthentifizierungsmethode **Web und MSOFBA** aus.

    ![Unterstützte Clients](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. Fügen Sie, wie unten gezeigt, die **vertrauende Seite** hinzu, die Sie im AD FS-Server erstellt haben, und klicken Sie dann auf **Weiter**.

    ![Veröffentlichen der vertrauenden Seite](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. Geben Sie im Abschnitt **Externe URL** die öffentlich zugängliche URL ein, die im WAP-Server konfiguriert ist. Fügen Sie die mit dem Berichtsserver (Berichtsserver-Konfigurations-Manager) konfigurierte URL, wie unten gezeigt, im Abschnitt **URL des Back-End-Servers** ein. Fügen Sie den SPN des Berichtsservers im Abschnitt **SPN des Back-End-Servers** ein.

    ![Veröffentlichungseinstellungen](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. Klicken Sie nacheinander auf **Weiter** und **Veröffentlichen**.
8. Führen Sie den folgenden PowerShell-Befehl aus, um die WAP-Konfiguration zu überprüfen.

    ```
    Get-WebApplicationProxyApplication "PBIRSBrowser" | FL
    ```

    ![PowerShell-Befehl](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>Herstellen einer Verbindung mit dem Berichtsserver über den Browser

Jetzt können Sie über einen Browser auf die öffentliche WAP-URL zugreifen, z. B. auf `https://reports.contosolab.com/ReportServer` für den Webdienst und auf `https://reports.contosolab.com/Reports` für das Webportal. Nachdem Sie sich erfolgreich authentifiziert haben, können Sie die Berichte anzeigen.

![Anmelden über AD FS](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>Nächste Schritte

* [Verwenden von OAuth zum Herstellen einer Verbindung mit dem Power BI-Berichtsserver und SSRS](../consumer/mobile/mobile-oauth-ssrs.md)
*[Was ist der Power BI-Berichtsserver?](get-started.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

