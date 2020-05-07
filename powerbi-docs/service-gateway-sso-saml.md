---
title: Verwenden von SAML (Security Assertion Markup Language) für SSO von Power BI bei lokalen Datenquellen
description: Konfigurieren Ihres Gateways mit SAML (Security Assertion Markup Language) zum Aktivieren von SSO von Power BI bei lokalen Datenquellen.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: bbb0584843f79445c4e5cca073f9c4b953d346aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74699358"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>Verwenden von SAML (Security Assertion Markup Language) für SSO von Power BI bei lokalen Datenquellen

Durch das Aktivieren von SSO für Power BI-Berichte und -Dashboards können Daten aus lokalen Datenquellen unter Beachtung der für diese Quellen konfigurierten Benutzerberechtigungen einfacher aktualisiert werden. Verwenden Sie [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) zum Aktivieren der nahtlosen SSO-Konnektivität. 

## <a name="supported-data-sources"></a>Unterstützte Datenquellen

Derzeit wird SAP HANA mit SAML unterstützt. Weitere Informationen zum Einrichten und Konfigurieren des einmaligen Anmeldens (SSO) für SAP HANA mit SAML finden Sie unter [SAML-SSO für die BI-Plattform mit HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA).

Mit [Kerberos](service-gateway-sso-kerberos.md) werden weitere Datenquellen unterstützt (einschließlich SAP HANA).

Für SAP HANA wird empfohlen, die Verschlüsselung zu aktivieren, bevor Sie eine SAML-SSO-Verbindung herstellen. Konfigurieren Sie zum aktivieren der Verschlüsselung den HANA-Server so, dass verschlüsselte Verbindungen akzeptiert werden, und konfigurieren Sie das Gateway für die Verwendung der Verschlüsselung zur Kommunikation mit Ihrem HANA-Server. Da der HANA-ODBC-Treiber SAML-Assertationen nicht standardmäßig verschlüsselt, wird die signierte SAML-Assertion *unverschlüsselt* vom Gateway an den HANA-Server gesendet und kann abgefangen und von Drittanbietern wiederverwendet werden. Anweisungen zum Aktivieren der Verschlüsselung für HANA mithilfe der OpenSSL-Bibliothek finden Sie unter [Aktivieren der Verschlüsselung für SAP HANA](/power-bi/desktop-sap-hana-encryption).

## <a name="configuring-the-gateway-and-data-source"></a>Konfigurieren des Gateways und der Datenquelle

Sie müssen eine Vertrauensstellung zwischen den HANA-Servern, für die Sie SSO aktivieren möchten, und dem Gateway herstellen, um SAML verwenden zu können. In diesem Szenario fungiert das Gateway als SAML-Identitätsanbieter (IdP). Es gibt verschiedene Möglichkeiten, diese Vertrauensstellung herzustellen. Sie können beispielsweise das X.509-Zertifikat des Gateway-IdP in den Zertifikatspeicher der HANA-Server importieren oder das X.509-Zertifikat des Gateways von einer Stammzertifizierungsstelle signieren lassen, die von den HANA-Servern als vertrauenswürdig eingestuft wird. Obwohl in diesem Leitfaden der zweite Ansatz beschrieben wird, können Sie bei Bedarf auch einen anderen verwenden.

Obwohl OpenSSL in dieser Anleitung als Kryptografieanbieter des HANA-Servers verwendet wird, empfiehlt SAP zum Abschließen der Setupschritte für die Vertrauensstellung stattdessen die SAP Cryptographic Library (auch unter dem Namen CommonCryptoLib oder sapcrypto bekannt) zu verwenden. Weitere Informationen finden Sie in der SAP-Dokumentation.

In den folgenden Schritten wird beschrieben, wie Sie mithilfe einer Stammzertifizierungsstelle, die vom HANA-Server als vertrauenswürdig eingestuft wird, das X.509-Zertifikat des Gateway-IdP signieren und auf diese Weise eine Vertrauensstellung zwischen dem HANA-Server und dem Gateway-IdP herstellen. So erstellen Sie diese Stammzertifizierungsstelle:

1. Erstellen Sie das X.509-Zertifikat und den privaten Schlüssel für die Stammzertifizierungsstelle. Geben Sie den folgenden Befehl ein, um beispielsweise das X.509-Zertifikat der Stammzertifizierungsstelle und den privaten Schlüssel im PEM-Format zu erstellen:

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    Stellen Sie sicher, dass der private Schlüssel der Stammzertifizierungsstelle ordnungsgemäß geschützt ist. Wenn dieser von einem Drittanbieter abgerufen wird, kann er für nicht autorisierten Zugriff auf den HANA-Server verwendet werden. 

 1. Fügen Sie das Zertifikat (z. B. mit dem Namen „CA_Cert.pem“) dem Zertifikatspeicher des HANA-Servers hinzu, sodass dieser Server alle erstellten Zertifikate, die von der erstellten Stammzertifizierungsstelle signiert werden, als vertrauenswürdig einstuft. 

    Sie finden den Speicherort des Zertifikatspeichers für den HANA-Server in der **ssltruststore**-Konfigurationseinstellung. Wenn Sie die Anweisungen in der SAP-Dokumentation zur Konfiguration von OpenSSL befolgt haben, stuft der HANA-Server möglicherweise bereits eine Stammzertifizierungsstelle als vertrauenswürdig ein, die dann wiederverwendet werden kann. Weitere Informationen finden Sie unter [Konfigurieren von OpenSSL-Verbindungen zwischen SAP HANA Studio und SAP HANA-Server](https://archive.sap.com/documents/docs/DOC-39571). Wenn Sie über mehrere HANA-Server verfügen, für die Sie SAML-SSO aktivieren möchten, müssen Sie sicherstellen, dass jeder Server diese Stammzertifizierungsstelle als vertrauenswürdig einstuft.

1. Erstellen Sie das X.509-Zertifikat für den Gateway-IdP. 

   Wenn Sie beispielsweise eine Zertifikatsignierungsanforderung (IdP_Req.pem) und einen privaten Schlüssel (IdP_Key.pem) erstellen möchten, die ein Jahr lang gültig sind, müssen Sie den folgenden Befehl ausführen:

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

 1. Signieren Sie die Zertifikatsignierungsanforderung mithilfe der Stammzertifizierungsstelle, die von Ihren HANA-Servern als vertrauenswürdig eingestuft wird. 

    Wenn Sie beispielsweise „IdP_Req.pem“ mithilfe von „CA_Cert.pem“ und „CA_Key.pem“ signieren möchten, müssen Sie den folgenden Befehl ausführen:

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```

     Das so erstellte IdP-Zertifikat ist ein Jahr lang gültig (siehe „-days“-Option). 

Importieren Sie Ihr IdP-Zertifikat in HANA Studio, um einen neuen SAML-Identitätsanbieter zu erstellen:

1. Klicken Sie in SAP HANA Studio mit der rechten Maustaste auf den SAP HANA-Servernamen, und navigieren Sie dann zu **Sicherheit** &gt; **Open Security Console** &gt; **SAML Identity Provider** &gt; **OpenSSL Cryptographic Library** (Sicherheitskonsole öffnen > SAML-Identitätsanbieter > OpenSSL-Kryptografiebibliothek).

    ![Identitätsanbieter](media/service-gateway-sso-saml/identity-providers.png)

1. Klicken Sie auf **Import** (Importieren), navigieren Sie zu „IdP_Cert.pem“, und importieren Sie diese.

1. Klicken Sie in SAP HANA Studio auf den Ordner **Security (Sicherheit)** .

    ![Sicherheitsordner](media/service-gateway-sso-saml/security-folder.png)

1. Erweitern Sie **Benutzer**, und wählen Sie dann den Benutzer aus, dem Sie Ihren Power BI-Benutzer zuordnen möchten.

1. Klicken Sie auf **SAML** und dann auf **Konfigurieren**.

    ![SAML konfigurieren](media/service-gateway-sso-saml/configure-saml.png)

1. Wählen Sie den Identitätsanbieter aus, den Sie in Schritt 2 erstellt haben. Geben Sie als **External Identity** (Externe Identität) den UPN des Power BI-Benutzers ein (in der Regel die E-Mail-Adresse, mit der sich der Benutzer bei Power BI anmeldet), und klicken Sie dann auf **Hinzufügen**. Geben Sie den Wert ein, der den ursprünglichen UPN des Power BI-Benutzers ersetzt, wenn Sie das Gateway für die Verwendung der Konfigurationsoption *ADUserNameReplacementProperty* konfiguriert haben. 

   Wenn Sie z. B. *ADUserNameReplacementProperty* auf **SAMAccountName** festlegen, sollten Sie den Wert **SAMAccountName** des Benutzers eingeben.

    ![Identitätsanbieter auswählen](media/service-gateway-sso-saml/select-identity-provider.png)

Nachdem Sie das Zertifikat und die Identität des Gateways konfiguriert haben, müssen Sie als Nächstes das Zertifikat in das PFX-Format konvertieren und das Gateway für die Verwendung des Zertifikats konfigurieren:

1. Konvertieren Sie das Zertifikat in das PFX-Format, indem Sie den folgenden Befehl ausführen. Dieser Befehl benennt die resultierende PFX-Datei „samlcert.pfx“ und legt *root* als Kennwort festlegt:

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. Kopieren Sie die PFX-Datei auf den Gatewaycomputer:

    1. Doppelklicken Sie auf die Datei „samltest.pfx“, und wählen Sie dann **Local Machine**&gt;**Next** (Lokaler Computer > Weiter) aus.

    1. Geben Sie das Kennwort ein, und klicken Sie auf **Next (Weiter)** .

    1. Klicken Sie zunächst auf **Place all certificates in the following store** (Alle Zertifikate in folgendem Speicher speichern) und dann auf **Durchsuchen** &gt; **Persönlich** &gt; **OK**.

    1. Klicken Sie auf **Weiter** und dann auf **Fertig stellen**.

       ![Zertifikat importieren](media/service-gateway-sso-saml/import-certificate.png)

1. Gewähren Sie dem Gatewaydienstkonto den Zugriff auf den privaten Schlüssel des Zertifikats:

    1. Führen Sie die Microsoft Management Console (MMC) auf dem Gatewaycomputer aus.

        ![MMC ausführen](media/service-gateway-sso-saml/run-mmc.png)

    1. Klicken Sie unter **Datei** auf **Add/Remove Snap-in (Snap-In hinzufügen/entfernen)** .

        ![Snap-In hinzufügen](media/service-gateway-sso-saml/add-snap-in.png)

    1. Klicken Sie auf **Certificates** &gt; **Hinzufügen** (Zertifikate), und dann auf **Computer account** &gt; **Weiter** (Computerkonto).

    1. Wählen Sie **Local Computer**&gt;**Finish**&gt;**OK** (Lokaler Computer > Fertig stellen > OK) aus.

    1. Erweitern Sie **Certificates**&gt;**Personal**&gt;**Certificates** (Zertifikate > Persönlich > Zertifikate), und suchen Sie nach dem Zertifikat.

    1. Klicken Sie mit der rechten Maustaste auf das Zertifikat, und navigieren Sie zu **All Tasks**&gt;**Manage Private Keys** (Alle Aufgaben > Private Schlüssel verwalten).

        ![Private Schlüssel verwalten](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Fügen Sie das Gatewaydienstkonto der Liste hinzu. Das Standardkonto ist **NT SERVICE\PBIEgwService**. Sie können herausfinden, welches Konto den Gatewaydienst ausführt, indem Sie **services.msc** ausführen, und nach **On-premises data gateway service** (Lokaler Datengatewaydienst) suchen.

        ![Gatewaydienst](media/service-gateway-sso-saml/gateway-service.png)

Führen Sie abschließend die folgenden Schritte aus, um den Zertifikatfingerabdruck zur Gatewaykonfiguration hinzuzufügen:

1. Führen Sie den folgenden PowerShell-Befehl aus, um die Zertifikate auf Ihrem Computer aufzulisten:

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. Kopieren Sie den Fingerabdruck des von Ihnen erstellten Zertifikats.

1. Navigieren Sie zum Gatewayverzeichnis, dessen Standardpfad folgendermaßen lautet: C:\Programme\Lokales Datengateway.

1. Öffnen Sie „PowerBI.DataMovement.Pipeline.GatewayCore.dll.config“, und suchen Sie nach dem Abschnitt *SapHanaSAMLCertThumbprint*. Fügen Sie den kopierten Fingerabdruck ein.

1. Starten Sie den Gatewaydienst neu.

## <a name="running-a-power-bi-report"></a>Ausführen eines Power BI-Berichts

Sie können jetzt die Seite **Manage Gateway** (Gateway verwalten) in Power BI verwenden, um die SAP HANA-Datenquelle zu konfigurieren. Aktivieren Sie unter **Erweiterte Einstellungen** SSO über SAML. Auf diese Weise können Sie Berichte und Datasets veröffentlichen, die an diese Datenquelle gebunden sind.

   ![Erweiterte Einstellungen](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Problembehandlung

Nachdem das auf SAML basierte einmalige Anmelden konfiguriert wurde, wird Ihnen im Power BI-Portal möglicherweise der folgende Fehler angezeigt: *"The credentials provided cannot be used for the SapHana source."* (Die bereitgestellten Anmeldeinformationen können nicht für die SapHana-Quelle verwendet werden.) Dieser Fehler bedeutet, dass die SAML-Anmeldeinformationen von SAP HANA nicht akzeptiert wurden.

In den Authentifizierungsablaufverfolgungen finden sich detaillierte Informationen zum Beheben von Fehlern bei Problemen mit Anmeldeinformationen bei SAP HANA. Befolgen Sie diese Schritte, um die Ablaufverfolgung für Ihren SAP HANA-Server zu konfigurieren:

1. Aktivieren Sie auf dem SAP HANA-Server die Authentifizierungsablaufverfolgung, indem Sie die folgende Abfrage ausführen:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduzieren Sie das Problem.

1. Öffnen Sie in HANA Studio die Administratorkonsole, und klicken Sie auf die Registerkarte **Diagnosis Files** (Diagnosedateien).

1. Öffnen Sie die aktuellste Indexserver-Ablaufverfolgung, und suchen Sie nach *SAMLAuthenticator.cpp*.

    Es sollte eine detaillierte Fehlermeldung angezeigt werden, die die Grundursache angibt. Beispiel:

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Deaktivieren Sie nach Abschluss der Problembehandlung die Authentifizierungsablaufverfolgung, indem Sie die folgende Abfrage ausführen:

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum lokalen Datengateway und zu DirectQuery finden Sie in den folgenden Ressourcen:

* [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
