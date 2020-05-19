---
title: Erstellen von SSL-Zertifikaten für Power BI-Visuals
description: Erfahren Sie, wie SSL-Zertifikate mithilfe der Power BI-Visualtools unter Windows, Mac oder Linux oder manuell generiert werden können.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 37bd8f15dcf17cd0f967e819338a719edf2a3054
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276373"
---
# <a name="create-an-ssl-certificate"></a>Erstellen eines SSL-Zertifikats

In diesem Artikel wird beschrieben, wie SSL-Zertifikate (Secure Sockets Layer) für Power BI-Visuals generiert und installiert werden können.

Für die Verfahren unter Windows, macOS X und Linux muss das Paket **pbiviz** mit den Power BI-Visualtools installiert sein. Weitere Informationen finden Sie unter [Einrichten der Entwicklerumgebung](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Erstellen eines Zertifikats unter Windows

Führen Sie den folgenden Befehl aus, um ein Zertifikat mithilfe des PowerShell-Cmdlets `New-SelfSignedCertificate` unter Windows 8 oder höher zu erstellen:

```powershell
pbiviz --install-cert
```

Für Windows 7 erfordert das Tool `pbiviz`, dass das Hilfsprogramm OpenSSL an der Befehlszeile verfügbar ist. Um OpenSSL zu installieren, wechseln Sie zu [OpenSSL](https://www.openssl.org) oder [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

Weitere Informationen und Anweisungen zum Installieren eines Zertifikats finden Sie unter [Erstellen und Installieren eines Zertifikats für Windows](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#windows).

## <a name="create-a-certificate-on-macos-x"></a>Erstellen eines Zertifikats unter macOS X

Das Hilfsprogramm OpenSSL ist in der Regel in den Betriebssystemen Linux und macOS X verfügbar.

Sie können OpenSSL auch installieren, indem Sie einen der folgenden Befehle ausführen:

- Über den *Brew*-Paket-Manager:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Mithilfe von *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

Nachdem Sie das Hilfsprogramm OpenSSL installiert haben, führen Sie den folgenden Befehl aus, um ein neues Zertifikat zu generieren:

```cmd
pbiviz --install-cert
```

Weitere Informationen und Anweisungen finden Sie unter [Erstellen und Installieren eines Zertifikats für OS X](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial#osx).

## <a name="create-a-certificate-on-linux"></a>Erstellen eines Zertifikats unter Linux

Das Hilfsprogramm OpenSSL ist in der Regel im Betriebssystem Linux verfügbar.

Bevor Sie beginnen, führen Sie die folgenden Befehle aus, um sicherzustellen, dass `openssl` und `certutil` installiert sind:

```sh
which openssl
which certutil
```

Wenn `openssl` und `certutil` nicht installiert sind, installieren Sie die Hilfsprogramme `openssl` und `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Erstellen der SSL-Konfigurationsdatei

Erstellen Sie eine Datei namens */tmp/openssl.cnf* mit folgendem Text:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Generieren einer Stammzertifizierungsstelle

Führen Sie die folgenden Befehle aus, um eine Stammzertifizierungsstelle zum Signieren lokaler Zertifikate zu generieren:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Generieren eines Zertifikats für localhost 

Um ein Zertifikat für `localhost` unter Verwendung der generierten Zertifizierungsstelle und *openssl.cnf* zu generieren, führen Sie die folgenden Befehle aus:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Hinzufügen von Stammzertifikaten

Um der Datenbank des Browsers Chrome ein Stammzertifikat hinzuzufügen, führen Sie Folgendes aus:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Um der Datenbank des Browsers Firefox ein Stammzertifikat hinzuzufügen, führen Sie Folgendes aus:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

So fügen Sie ein systemweit geltendes Stammzertifikat hinzu

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Entfernen von Stammzertifikaten

Führen Sie zum Entfernen eines Stammzertifikats Folgendes aus:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Manuelles Generieren eines Zertifikats

Sie können ein SSL-Zertifikat mithilfe von OpenSSL auch manuell generieren. Sie können beliebige Tools angeben, um Ihre Zertifikate zu generieren.

Wenn das Hilfsprogramm OpenSSL bereits installiert ist, generieren Sie ein neues Zertifikat, indem Sie Folgendes ausführen:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

In der Regel können Sie die `PowerBI-visuals-tools`-Webserverzertifikate finden, indem Sie einen der folgenden Befehle ausführen:

- Für die globale Instanz der Tools:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Für die lokale Instanz der Tools:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM-Format

Wenn Sie das PEM-Format (Privacy Enhanced Mail) verwenden, speichern Sie die Zertifikatdatei als *PowerBIVisualTest_public.crt* und den privaten Schlüssel als *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>PFX-Format

Wenn Sie das PFX-Format (Personal Information Exchange) verwenden, speichern Sie die Zertifikatsdatei als *PowerBIVisualTest_public.pfx*.

Wenn Ihre PFX-Zertifikatsdatei eine Passphrase benötigt:

1. Legen Sie Folgendes in der Konfigurationsdatei fest:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. Legen Sie im Abschnitt `server` die Passphrase fest, indem Sie den Platzhalter \<YOUR PASSPHRASE> (Ihre Passphrase) ersetzen:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Nächste Schritte
- [Entwickeln eines Power BI-Visuals](custom-visual-develop-tutorial.md)
- [Beispiele von Power BI-Visuals](samples.md)
- [Veröffentlichen von Power BI-Visuals in AppSource](office-store.md)
