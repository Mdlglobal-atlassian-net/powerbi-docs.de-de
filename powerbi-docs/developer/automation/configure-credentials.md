---
title: Programmgesteuertes Konfigurieren von Anmeldeinformationen für Power BI
description: Programmgesteuertes Konfigurieren von Anmeldeinformationen beim Automatisieren von Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/23/2020
ms.openlocfilehash: bd7758be32d18fd3be06a7847edc7795c2b5f9e1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114771"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Programmgesteuertes Konfigurieren von Anmeldeinformationen für Power BI

Folgen Sie diesen Schritten, um Anmeldeinformationen für Power BI programmgesteuert zu konfigurieren.

## <a name="update-credentials-flow-for-data-sources"></a>Aktualisieren eines Anmeldeinformationsflows für Datenquellen

1. Rufen Sie [Datenquellen aufrufen](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) auf, um die Datenquellen des Datasets anzeigen zu lassen. Im Antworttext für jede Datenquelle sind Typ, Verbindungsdetails, Gateway und Datenquellen-ID angegeben.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Erstellen Sie je nach Anmeldeinformationstyp eine Anmeldeinformationenzeichenfolge gemäß der [Datenquellenupdatebeispiele](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource).

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Rufen Sie [Gateway abrufen](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) auf, um den öffentlichen Gateway-Schlüssel abzurufen.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Verschlüsseln Sie die Anmeldeinformationen.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    Verschlüsseln Sie die Zeichenfolge mit den Anmeldeinformationen mit dem öffentlichen Gatewayschlüssel aus Schritt 2. Verschiedene Gatewayversionen können unterschiedliche Größen für den öffentlichen Schlüssel aufweisen. Weitere Informationen finden Sie in den folgenden Beispielen im SDK-Code im [GitHub-Repository zu PowerBI-CSharp](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Erstellen Sie mit den verschlüsselten Anmeldeinformationen Details zu Anmeldeinformationen.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    Verwenden Sie die AssymetricKeyEncriptor-Klasse mit dem in **Schritt 3** abgerufenen öffentlichen Schlüssel.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. Rufen Sie [Datenquelle aktualisieren](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) auf, um Anmeldeinformationen festzulegen.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Konfigurieren einer neuen Datenquelle für ein Datengateway

1. Installieren Sie das [lokale Datengateway](https://powerbi.microsoft.com/gateway/) auf Ihrem Computer.

2. Rufen Sie [Gateway abrufen](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) auf, um die Gateway-ID und den öffentlichen Schlüssel abzurufen.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Erstellen Sie mithilfe des öffentlichen Gatewayschlüssels, den Sie in [Schritt 2](#update-credentials-flow-for-data-sources) abgerufen haben, Details zu Anmeldeinformationen. Eine Beschreibung dieses Vorgangs finden Sie unter **Aktualisieren eines Anmeldeinformationsflows für Datenquellen**.

4. Erstellen Sie den Anforderungstext.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Rufen Sie die [API zum Erstellen von Datenquellen](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) auf.

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Arten von Anmeldeinformationen

Wenn Sie [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Datenquelle erstellen) oder [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Datenquelle aktualisieren) in einem **lokalen Unternehmensgateway** mit der [Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/) aufrufen, müssen die Werte für die Anmeldeinformationen mithilfe des öffentlichen Schlüssels des Gateways verschlüsselt werden.

>[!NOTE]
>.NET SDK v3 kann auch die im Folgenden aufgeführten .NET SDK v2-Beispiele ausführen.

### <a name="windows-and-basic-credentials"></a>Windows und einfache Anmeldeinformationen

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Wichtige Anmeldeinformationen

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2-Anmeldeinformationen**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Anonyme Anmeldeinformationen**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Problembehandlung

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>No gateway and data source ID found when calling get data sources (Beim Aufrufen von „Get Datasource“ wurde keine Gateway- und Datenquellen-ID gefunden)

Dieser Fehler bedeutet, dass das Dataset nicht an ein Gateway gebunden ist. Beim Erstellen eines neuen Datasets wird im Cloudgateway des Benutzers für jede Cloudverbindung automatisch eine Datenquelle ohne Anmeldeinformationen erstellt. Dieses Gateway wird verwendet, um die Anmeldeinformationen für Cloudverbindungen zu speichern.

Nachdem Sie das Dataset erstellt haben, wird eine automatische Bindung zwischen dem Dataset und einem passenden Gateway hergestellt, die übereinstimmende Datenquellen für alle Verbindungen enthält. Wenn es kein solches Gateway oder mehrere passende Gateways gibt, schlägt die automatische Bindung fehl.

Wenn Sie lokale Datasets verwenden, erstellen Sie die fehlenden lokalen Datenquellen, und binden Sie das Dataset mithilfe von [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (An Gateway binden) manuell an ein Gateway.

Um Gateways zu ermitteln, die gebunden werden könnten, verwenden Sie [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Gateways entdecken).