---
title: Erstellen eines SSL-Zertifikats
description: Problemumgehung zum manuellen Erstellen von Zertifikaten für den Entwicklerserver
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: fab40863d7beae4892a56975aa5e92c4fe5486ac
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380270"
---
# <a name="create-an-ssl-certificate"></a>Erstellen eines SSL-Zertifikats

In diesem Artikel wird das Erstellen eines SSL-Zertifikats erläutert.

Führen Sie den folgenden Befehl aus, um das Zertifikat mithilfe des PowerShell-Cmdlets `New-SelfSignedCertificate` unter Windows 8 oder höher zu erstellen.

```cmd
pbiviz --install-cert
```

Das Tool erfordert eine OpenSSL-Installation für Windows 7. Das OpenSSL-Hilfsprogramm muss über die Befehlszeile verfügbar sein.

Rufen Sie die Website für [OpenSSL](https://www.openssl.org) oder [OpenSSL-Binärdateien](https://wiki.openssl.org/index.php/Binaries) auf, um OpenSSL zu installieren.

## <a name="create-a-certificate-mac-os-x"></a>Erstellen eines Zertifikats (Mac OS X)

Das OpenSSL-Hilfsprogramm ist in der Regel in den Betriebssystemen Linux und Mac OS X verfügbar.

Sie können es auch installieren, indem Sie einen der folgenden Befehle ausführen:

* Über den *Brew*-Paket-Manager:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* Mithilfe von *MacPorts*:

    ```cmd
    sudo port install openssl
    ```

Nachdem Sie das OpenSSL-Hilfsprogramm zum Erstellen eines neuen Zertifikats installiert haben, führen Sie den folgenden Befehl aus:

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>Erstellen eines Zertifikats (Linux)

Wenn das OpenSSL-Hilfsprogramm für Ihr Linux-Betriebssystem nicht verfügbar ist, können Sie es mithilfe von einem der folgenden Befehle installieren:

* *APT*-Paket-Manager:

    ```cmd
    sudo apt-get install openssl
    ```

* *Yellowdog Updater*:

    ```cmd
    yum install openssl
    ```

* *Redhat*-Paket-Manager:

    ```cmd
    rpm install openssl
    ```

Wenn das OpenSSL-Hilfsprogramm bereits auf Ihrem Betriebssystem verfügbar ist, erstellen Sie ein neues Zertifikat, indem Sie den folgenden Befehl ausführen:

```cmd
pbiviz --install-cert
```

Alternativ können Sie das OpenSSL-Hilfsprogramm über die Website für [OpenSSL](https://www.openssl.org) oder [OpenSSL-Binärdateien](https://wiki.openssl.org/index.php/Binaries) abrufen.

## <a name="generate-the-certificate-manually"></a>Manuelles Generieren des Zertifikats

Sie können festlegen, dass Ihre Zertifikate von beliebigen Tools generiert werden können.

Wenn das OpenSSL-Hilfsprogramm bereits auf Ihrem System installiert ist, generieren Sie ein neues Zertifikat, indem Sie die folgenden Befehle ausführen:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

In der Regel können Sie die PowerBI-visuals-tools-Webserverzertifikate finden, indem Sie einen der folgenden Befehle ausführen:

* Für die globale Instanz der Tools:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Für die lokale Instanz der Tools:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Wenn Sie das PEM-Format verwenden, speichern Sie die Zertifikatdatei als *PowerBICustomVisualTest_public.crt*, und speichern Sie privateKey als *PowerBICustomVisualTest_public.key*.

Wenn Sie das PFX-Format verwenden, speichern Sie die Zertifikatsdatei als *PowerBICustomVisualTest_public.pfx*.

Wenn Ihre PFX-Zertifikatsdatei eine Passphrase benötigt, gehen Sie wie folgt vor:
1. Legen Sie Folgendes in der Konfigurationsdatei fest:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. Legen Sie im Abschnitt `server` die Passphrase fest, indem Sie den Platzhalter „*YOUR PASSPHRASE*“ (Ihre Passphrase) ersetzen:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```