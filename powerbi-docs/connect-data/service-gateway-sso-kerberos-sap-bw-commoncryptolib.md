---
title: Verwenden von Kerberos-Single Sign-On für Einmaliges Anmelden (SSO) bei SAP BW mithilfe von CommonCryptoLib (sapcrypto.dll)
description: Konfigurieren Ihres SAP BW-Servers, um einmaliges Anmelden vom Power BI-Dienst mithilfe von CommonCryptoLib (sapcrypto.dll) zu aktivieren
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 12/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b060252a9f6d77d42136b38fa7fa980d0784ed46
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83283690"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>Verwenden von Kerberos-Single Sign-On für Einmaliges Anmelden (SSO) bei SAP BW mithilfe von CommonCryptoLib (sapcrypto.dll)

In diesem Artikel wird beschrieben, wie Sie Ihre SAP BW-Datenquelle so konfigurieren, dass SSO (Einmaliges Anmelden, Single Sign-On) vom Power BI-Dienst mithilfe von CommonCryptoLib (sapcrypto.dll) aktiviert wird.

> [!NOTE]
> Bevor Sie versuchen, einen auf SAP BW basierenden Bericht zu aktualisieren, der Kerberos SSO verwendet, führen Sie beide Schritte in diesem Artikel und die Schritte in [Kerberos SSO konfigurieren](service-gateway-sso-kerberos.md) aus. Die Verwendung von CommonCryptoLib als SNC-Bibliothek ermöglicht SSO-Verbindungen mit SAP BW-Anwendungsservern und SAP BW-Nachrichtenservern.

## <a name="configure-sap-bw-to-enable-sso-using-commoncryptolib"></a>Konfigurieren von SAP BW zum Aktivieren von SSO mithilfe von CommonCryptoLib

> [!NOTE]
> Das lokale Datengateway ist eine 64-Bit-Software und erfordert daher die 64-Bit-Version von CommonCryptoLib (sapcrypto.dll), um SSO für SAP BW durchzuführen. Wenn Sie die SSO-Verbindung mit Ihrem SAP BW-Server auf der SAP-Benutzeroberfläche (GUI) testen möchten, bevor Sie eine SSO-Verbindung über das Gateway herstellen (empfohlen), benötigen Sie außerdem die 32-Bit-Version von CommonCryptoLib, da es sich bei SAP GUI um eine 32-Bit-Software handelt.

1. Stellen Sie sicher, dass Ihr BW-Server ordnungsgemäß mithilfe von CommonCryptoLib für Kerberos-SSO konfiguriert ist. Ist dies der Fall, können Sie SSO mithilfe eines SAP-Tools wie SAP GUI, das für die Verwendung von CommonCryptoLib konfiguriert wurde, für den Zugriff auf Ihren BW-Server zu verwenden (entweder direkt oder über einen SAP BW-Nachrichtenserver). 

   Weitere Informationen zu den Setupschritten finden Sie unter [SAP Single Sign-On: Authentifizieren mit Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). Ihr BW-Server sollte CommonCryptoLib als SNC-Bibliothek verwenden und einen SNC-Namen haben, der mit *CN=* beginnt, z. B. *CN=BW1*. Weitere Informationen zu SNC-Namensanforderungen (insbesondere zum Parameter „snc/identity/as“) finden Sie unter [SNC-Parameter für die Kerberos-Konfiguration](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/360534094511490d91b9589d20abb49a.html).

1. Installieren Sie die x64-Version des [SAP .NET-Connectors](https://support.sap.com/en/product/connectors/msnet.html) auf dem Computer, auf dem das Gateway installiert ist, wenn dies noch nicht geschehen ist. 
   
   Sie können überprüfen, ob die Komponente installiert wurde, indem Sie versuchen, eine Verbindung mit Ihrem BW-Server in Power BI Desktop über den Gatewaycomputer herzustellen. Wenn Sie keine Verbindung mithilfe der 2.0-Implementierung herstellen können, ist der .NET-Connector nicht installiert oder nicht im globalen Assemblycache installiert.

1. Stellen Sie sicher, dass SAP Secure Login Client (SLC) auf dem Computer, auf dem das Gateway installiert ist, nicht ausgeführt wird. 

   SLC speichert Kerberos-Tickets auf eine Weise zwischen, die die Fähigkeit des Gateways, Kerberos für SSO zu verwenden, beeinträchtigen kann. 

1. Wenn SLC installiert ist, deinstallieren oder beenden Sie SAP Secure Login Client. Klicken Sie dazu mit der rechten Maustaste auf das Symbol auf der Taskleiste, und wählen Sie **Abmelden** und **Beenden** aus, bevor Sie eine SSO-Verbindung mithilfe des Gateways herstellen. 

   Für SLC wird die Verwendung auf Windows Server-Computern nicht unterstützt. Weitere Informationen finden Sie im [SAP-Hinweis 2780475](https://launchpad.support.sap.com/#/notes/2780475) (S-User erforderlich).

   ![SAP Secure Login Client](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

1. Wenn Sie SLC deinstallieren oder **Abmelden** und **Beenden** auswählen, öffnen Sie ein Befehlsfenster, und geben Sie `klist purge` ein, um zwischengespeicherte Kerberos-Tickets zu löschen, bevor Sie eine SSO-Verbindung über das Gateway herstellen.

1. Laden Sie 64-Bit-CommonCryptoLib (sapcrypto.dll), Version *8.5.25 oder höher*, aus dem SAP Launchpad herunter, und kopieren Sie es in einen Ordner auf Ihrem Gatewaycomputer. Erstellen Sie in demselben Verzeichnis, in das Sie „sapcrypto.dll“ kopiert haben, eine Datei mit dem Namen „sapcrypto.ini“ und dem folgenden Inhalt:

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    Die INI-Datei enthält Konfigurationsinformationen, die von CommonCryptoLib zum Aktivieren von SSO im Gatewayszenario benötigt werden.

    > [!NOTE]
    > Diese Dateien müssen am gleichen Speicherort gespeichert werden. Das bedeutet, dass _/path/to/sapcrypto/_ sowohl „sapcrypto.ini“ als auch „sapcrypto.dll“ enthalten sollte.

    Sowohl der Gatewaydienstbenutzer als auch der AD-Benutzer (Active Directory), dessen Identität der Dienstbenutzer annimmt, benötigen für beide Dateien Lese- und Ausführungsberechtigungen. Es wird empfohlen, der Gruppe „Authentifizierte Benutzer“ Berechtigungen für die INI- und DLL-Datei zu erteilen. Zu Testzwecken können Sie diese Berechtigungen auch explizit dem Gatewaydienstbenutzer und dem Active Directory-Benutzer erteilen, die Sie zum Testen verwenden möchten. Im folgenden Screenshot wurde der Gruppe „Authentifizierte Benutzer“ die Berechtigung zum **Lesen und Ausführen** für „sapcrypto.dll“ erteilt:

    ![Authentifizierte Benutzer](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Wenn Sie noch nicht über eine SAP BW-Datenquelle verfügen, die dem Gateway zugeordnet ist, durch das die SSO-Verbindung verlaufen soll, fügen Sie eine auf der Seite **Gateways verwalten** im Power BI-Dienst hinzu. Wenn Sie bereits über eine solche Datenquelle verfügen, bearbeiten Sie diese: 
    - Wählen Sie **SAP Business Warehouse** als **Datenquellentyp** aus, wenn Sie eine SSO-Verbindung zu einem BW-Anwendungsserver herstellen möchten. 
    - Wählen Sie **SAP Business Warehouse-Nachrichtenserver** aus, wenn Sie eine SSO-Verbindung mit einem BW-Nachrichtenserver herstellen möchten.

1. Wählen Sie als **SNC-Bibliothek** entweder die Umgebungsvariable **SNC\_LIB** oder **SNC\_LIB\_64** oder die Option **Benutzerdefiniert** aus. 

   - Wenn Sie **SNC\_LIB** auswählen, müssen Sie den Wert der Umgebungsvariablen **SNC\_LIB\_64** auf dem Gatewaycomputer auf den absoluten Pfad der 64-Bit-Kopie der Datei „sapcrypto.dll“ auf dem Gatewaycomputer festlegen. Beispiel: *C:\Benutzer\Test\Desktop\sapcrypto.dll*.

   - Wenn Sie **Benutzerdefiniert** auswählen, fügen Sie den absoluten Pfad zur Datei *sapcrypto.dll* in das Feld „Benutzerdefinierter SNC-Bibliothekspfad“ ein, das auf der Seite **Gateways verwalten** angezeigt wird. 

1. Geben Sie als **Name des SNC-Partners** den SNC-Namen des BW-Servers ein. Stellen Sie sicher, dass unter **Erweiterte Einstellungen** das Kontrollkästchen **SSO über Kerberos für DirectQuery-Abfragen verwenden** aktiviert ist. Füllen Sie die anderen Felder so aus, als ob Sie sie für die Einrichtung einer Windows-Authentifizierungsverbindung von PBI-Desktop konfigurieren würden.

1. Erstellen Sie eine **CCL\_PROFILE**-Systemvariable, und legen Sie deren Wert auf den Pfad der Datei „sapcrypto.ini“ fest.

    ![CCL\_PROFILE-Systemvariable](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Die Dateien „sapcrypto.dll“ und „sapcrypto.ini“ müssen sich am gleichen Speicherort befinden. Im obigen Beispiel befinden sich die beiden Dateien „sapcrypto.ini“ und „sapcrypto.dll“ auf dem Desktop.

1. Starten Sie den Gatewaydienst neu.

    ![Neustarten des Gatewaydiensts](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [Ausführen eines Power BI-Berichts](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Problembehandlung

Wenn der Bericht im Power BI-Dienst nicht aktualisiert werden kann, können Sie die Gateway-Ablaufverfolgung, CPIC-Ablaufverfolgung und CommonCryptoLib-Ablaufverfolgung verwenden, um das Problem zu diagnostizieren. Da es sich bei der CPIC-Ablaufverfolgung und bei CommonCryptoLib um SAP-Produkte handelt, kann Microsoft dafür keinen Support bereitstellen.

### <a name="gateway-logs"></a>Gatewayprotokolle

1. Reproduzieren Sie das Problem.

2. Öffnen Sie hierzu die [Gateway-App](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), und wählen Sie auf der Registerkarte **Diagnose** die Option **Protokolle exportieren** aus.

      ![Exportieren von Gatewayprotokollen](media/service-gateway-sso-kerberos/export-gateway-logs.png)

### <a name="cpic-tracing"></a>CPIC-Ablaufverfolgung

1. Legen Sie zum Aktivieren der CPIC-Ablaufverfolgung zwei Umgebungsvariablen fest: **CPIC\_TRACE** und **CPIC\_TRACE\_DIR**. 

   Mit der ersten Variablen wird die Ablaufverfolgungsebene festgelegt, die zweite Variable gibt das Verzeichnis für die Ablaufverfolgungsdatei an. Bei dem Verzeichnis muss es sich um einen Speicherort handeln, in den Mitglieder der Gruppe „Authentifizierte Benutzer“ schreiben können. 
 
2. Legen Sie **CPIC\_TRACE** auf *3* und **CPIC\_TRACE\_DIR** auf das Verzeichnis fest, in das die Ablaufverfolgungsdateien geschrieben werden sollen. Beispiel:

   ![CPIC-Ablaufverfolgung](media/service-gateway-sso-kerberos/cpic-tracing.png)

3. Reproduzieren Sie das Problem, und stellen Sie sicher, dass **CPIC\_TRACE\_DIR** Ablaufverfolgungsdateien enthält.
 
    Die CPIC-Ablaufverfolgung kann Probleme auf höherer Ebene diagnostizieren, z. B. einen Fehler beim Laden der sapcrypto.dll-Bibliothek. Im Folgenden finden Sie einen Codeausschnitt einer CPIC-Ablaufverfolgungsdatei, in der ein Fehler beim Laden einer DLL aufgetreten ist:

    ```
    [Thr 7228] *** ERROR => DlLoadLib()==DLENOACCESS - LoadLibrary("C:\Users\test\Desktop\sapcrypto.dll")
    Error 5 = "Access is denied." [dlnt.c       255]
    ```

    Wenn ein solcher Fehler auftritt, Sie aber die Berechtigungen zum Lesen und Ausführen in den Dateien „sapcrypto.dll“ und „sapcrypto.ini“ wie im [Abschnitt oben](#configure-sap-bw-to-enable-sso-using-commoncryptolib) beschrieben festgelegt haben, legen Sie die gleichen Lese- und Ausführungsberechtigungen in dem Ordner fest, der die Dateien enthält.

    Wenn Sie die DLL-Datei weiterhin nicht laden können, aktivieren Sie die [Überwachung für die Datei](/windows/security/threat-protection/auditing/apply-a-basic-audit-policy-on-a-file-or-folder). Die resultierenden Überwachungsprotokolle in der Windows-Ereignisanzeige können Ihnen helfen zu ermitteln, warum sich die Datei nicht laden lässt. Suchen Sie nach einem Fehlereintrag, der durch den Active Directory-Benutzer initiiert wurde, dessen Identität angenommen wurde. Für den Benutzer `MYDOMAIN\mytestuser`, dessen Identität angenommen wurde, würde ein Fehler im Überwachungsprotokoll beispielsweise folgendermaßen aussehen:

    ```
    A handle to an object was requested.

    Subject:
        Security ID:        MYDOMAIN\mytestuser
        Account Name:       mytestuser
        Account Domain:     MYDOMAIN
        Logon ID:       0xCF23A8

    Object:
        Object Server:      Security
        Object Type:        File
        Object Name:        <path information>\sapcrypto.dll
        Handle ID:      0x0
        Resource Attributes:    -

    Process Information:
        Process ID:     0x2b4c
        Process Name:       C:\Program Files\On-premises data gateway\Microsoft.Mashup.Container.NetFX45.exe

    Access Request Information:
        Transaction ID:     {00000000-0000-0000-0000-000000000000}
        Accesses:       ReadAttributes
                
    Access Reasons:     ReadAttributes: Not granted
                
    Access Mask:        0x80
    Privileges Used for Access Check:   -
    Restricted SID Count:   0
    ```

### <a name="commoncryptolib-tracing"></a>CommonCryptoLib-Ablaufverfolgung 

1. Aktivieren Sie die CommonCryptoLib-Ablaufverfolgung, indem Sie der zuvor erstellten Datei „sapcrypto.ini“ die folgenden Zeilen hinzufügen:

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

2. Geben Sie für die Option `ccl/trace/directory` einen Speicherort an, in den Mitglieder der Gruppe „Authentifizierte Benutzer“ schreiben können. 

3. Erstellen Sie alternativ eine neue INI-Datei, um dieses Verhalten zu ändern. Erstellen Sie in demselben Verzeichnis, in dem sich „sapcrypto.ini“ und „sapcrypto.dll“ befinden, eine Datei mit dem Namen „sectrace.ini“ und dem folgenden Inhalt. Ersetzen Sie die `DIRECTORY`-Option durch einen Speicherort auf Ihrem Computer, in den Mitglieder der Gruppe „Authentifizierte Benutzer“ schreiben können:

    ```
    LEVEL = 5
    DIRECTORY = <drive>:\logs\sectrace
    ```

4. Reproduzieren Sie das Problem, und prüfen Sie, ob der Speicherort, auf den **DIRECTORY** verweist, Ablaufverfolgungsdateien enthält. 

5. Wenn Sie fertig sind, deaktivieren Sie die CPIC- und CCL-Ablaufverfolgung.

    Weitere Informationen zur CommonCryptoLib-Ablaufverfolgung finden Sie in [SAP-Hinweis 2491573](https://launchpad.support.sap.com/#/notes/2491573) (S-User von SAP erforderlich).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum lokalen Datengateway und zu DirectQuery finden Sie in den folgenden Ressourcen:

* [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](power-bi-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
