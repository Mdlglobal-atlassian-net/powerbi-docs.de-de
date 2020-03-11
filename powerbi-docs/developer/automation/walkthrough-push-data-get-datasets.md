---
title: Abrufen eines Datasets zum Hinzufügen von Zeilen
description: Exemplarische Vorgehensweise zum Übertragen von Daten per Push – Abrufen eines Datasets, um einer Power BI-Tabelle Zeilen hinzuzufügen
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: 5b4e6a2506555be6984a03e2a8f0fb8f4050f803
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079299"
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>Schritt 4: Abrufen eines Datasets, um einer Power BI-Tabelle Zeilen hinzuzufügen

Dieser Artikel ist Teil einer Anleitung zum [Übertragen von Daten in ein Dataset per Push](walkthrough-push-data.md).

In **Schritt 3** von „Übertragen von Daten in ein Dataset per Push“ haben Sie unter [Erstellen eines Datasets in Power BI](walkthrough-push-data-create-dataset.md) den Vorgang [Dataset erstellen](https://docs.microsoft.com/rest/api/power-bi/datasets) zum Erstellen eines Datasets in Power BI aufgerufen. In diesem Schritt verwenden Sie den Vorgang [Datasets abrufen](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) und „Newtonsoft.Json“, um eine Dataset-ID abzurufen. Sie verwenden die Dataset-ID in Schritt 4, um einem Dataset Zeilen hinzufügen. 

Um Daten per Push in ein Power BI-Dataset zu übertragen, müssen Sie auf die Tabelle im Dataset verweisen. Um auf eine Tabelle in einem Dataset zu verweisen, müssen Sie zuerst eine **Dataset-ID**abrufen. Mithilfe des Vorgangs [Datasets abrufen](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) rufen Sie eine **Dataset-ID** ab. Der Vorgang **Datasets abrufen** gibt eine JSON-Zeichenfolge mit einer Liste aller Datasets in Power BI zurück. Die empfohlene Methode zum Deserialisieren einer JSON-Zeichenfolge ist das Verwenden von [Newtonsoft.Json](https://www.newtonsoft.com/json).

Nachstehen erfahren Sie, wie Sie ein Dataset abrufen.

## <a name="get-a-power-bi-dataset"></a>Abrufen eines Power BI-Datasets

> **HINWEIS**: Wichtig ist, dass Sie zuvor die vorangegangenen Schritte der exemplarischen Vorgehensweise [Übertragen von Daten in ein Dataset per Push](walkthrough-push-data.md) ausgeführt haben.

1. Installieren Sie im Konsolenanwendungsprojekt, das Sie in „Schritt 2: Exemplarische Vorgehensweise zum Übertragen von Daten per Push“ unter [Abrufen eines Authentifizierungszugriffstokens](walkthrough-push-data-get-token.md) erstellt haben, das NuGet-Paket „Newtonsoft.Json“. Das Paket wird so installiert:

     a. Wählen Sie in Visual Studio 2015 **Tools** > **NuGet-Paket-Manager** > **Paket-Manager-Konsole**.

     b. Geben Sie in **Paket-Manager-Konsole**„Install-Package Newtonsoft.Json“ ein.
2. Fügen Sie nach der Installation des Pakets **using Newtonsoft.Json;** der Datei „Program.cs“ hinzu.
3. Fügen Sie in „Program.cs“ den folgenden Code hinzu, um eine **Dataset-ID**abzurufen.
4. Führen Sie die Konsolen-App aus, und melden Sie sich bei Ihrem Power BI-Konto an. Daraufhin sollte im Konsolenfenster **Dataset-ID:** gefolgt von einer ID angezeigt werden.

**Beispiel des Abrufs eines Datasets**

Fügen Sie diesen Code der Datei „Program.cs“ hinzu.

* In „static void Main(string[]args)“:
  
  ```csharp
  static void Main(string[] args)
  {
  
    //Get an authentication access token
    token = GetToken();
  
    //Create a dataset in Power BI
    CreateDataset();
  
    //Get a dataset to add rows into a Power BI table
    string datasetId = GetDataset();
  }
  ```
* Eine „GetDatset()“-Methode hinzu:
  
  ```csharp
    #region Get a dataset to add rows into a Power BI table
    private static string GetDataset()
    {
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "GET";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        string datasetId = string.Empty;
        //Get HttpWebResponse from GET request
        using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
        {
            //Get StreamReader that holds the response stream
            using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
            {
                string responseContent = reader.ReadToEnd();
  
                //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                //and add using Newtonsoft.Json
                var results = JsonConvert.DeserializeObject<dynamic>(responseContent);
  
                //Get the first id
                datasetId = results["value"][0]["id"];
  
                Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                Console.ReadLine();
  
                return datasetId;
            }
        }
    }
    #endregion
  ```

Im nächsten Schritt erfahren Sie, wie Sie [Zeilen einer Power BI-Tabelle hinzufügen](walkthrough-push-data-add-rows.md).

Nachstehend finden Sie die [vollständige Codeliste](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Vollständige Codeliste

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;
using Newtonsoft.Json;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

            //Get a dataset to add rows into a Power BI table
            string datasetId = GetDataset();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion

        #region Get a dataset to add rows into a Power BI table
        private static string GetDataset()
        {
            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "GET";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            string datasetId = string.Empty;
            //Get HttpWebResponse from GET request
            using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
            {
                //Get StreamReader that holds the response stream
                using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                {
                    string responseContent = reader.ReadToEnd();

                    //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                    //and add using Newtonsoft.Json
                    var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                    //Get the first id
                    datasetId = results["value"][0]["id"];

                    Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                    Console.ReadLine();

                    return datasetId;
                }
            }
        }
        #endregion
    }
}
```

## <a name="next-steps"></a>Nächste Schritte

* [Hinzufügen von Zeilen zu einer Power BI-Tabelle](walkthrough-push-data-add-rows.md)  
* [Newtonsoft.Json](https://www.newtonsoft.com/json)  
* [Get Datasets (Datasets abrufen)](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)  
* [Übertragen von Daten in Power BI per Push](walkthrough-push-data.md)  
* [Übersicht über Power BI-REST-API](overview-of-power-bi-rest-api.md)  
* [Referenz zur Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)