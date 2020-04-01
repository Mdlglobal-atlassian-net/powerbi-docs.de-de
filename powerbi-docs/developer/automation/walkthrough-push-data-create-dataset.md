---
title: Erstellen eines Datasets
description: Exemplarische Vorgehensweise – Übertragen von Daten in ein Dataset per Push – Erstellen eines Datasets in Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: 149b4f8663838c0a87609a1ec24358fb9ee9727e
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80403638"
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>Schritt 3: Erstellen eines Datasets in Power BI
Dieser Artikel ist Teil einer Anleitung zum [Übertragen von Daten in ein Dataset per Push](walkthrough-push-data.md).

In **Schritt 2** von „Übertragen von Daten in ein Dataset per Push“ ([Abrufen eines Authentifizierungszugriffstokens](walkthrough-push-data-get-token.md)) haben Sie ein Token für die Authentifizierung bei **Azure AD** abgerufen. In diesem Schritt verwenden Sie das Token zum Aufrufen des Vorgangs [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets).

Um einen Aufruf einer anderen Ressource zu erstellen, verwenden Sie eine URL zum Bestimmen der Ressource und senden eine JSON-Zeichenfolge (JavaScript Object Notation), die das Dataset beschreibt, an die Power BI-Dienstressource. Eine REST-Ressource gibt den Teil des Power BI-Diensts an, mit dem Sie arbeiten möchten. Beim Übertragen von Daten per Push in das Dataset ist die Zielressource ein **Dataset**. Die URL zum Bestimmen eines Datasets ist `https://api.PowerBI.com/v1.0/myorg/datasets`. Wenn Sie Daten in einer Gruppe per Push übertragen, ist die URL `https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets`.

Zum Authentifizieren eines Power BI-REST-Vorgangs fügen Sie das unter [Abrufen eines Authentifizierungszugriffstokens](walkthrough-push-data-get-token.md) abgerufene Token einem Anforderungsheader hinzu:

Durch Aufrufen des Vorgangs [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) wird ein neues Dataset erstellt. 

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

Im Folgenden wird das Erstellen eines Datasets in Power BI erläutert.

## <a name="create-a-dataset-in-power-bi"></a>Erstellen eines Datasets in Power BI
> [!NOTE]
> Wichtig ist, dass Sie zuvor die vorangegangenen Schritte der exemplarischen Vorgehensweise [Übertragen von Daten in ein Dataset per Push](walkthrough-push-data.md) ausgeführt haben.
> 
> 

1. Im Konsolenanwendungsprojekt, das Sie in [Schritt 2: Abrufen eines Authentifizierungszugriffstokens](walkthrough-push-data-get-token.md) erstellt haben, fügen Sie der Datei „Program.cs“ die Einträge **using System.Net;** und **using System.IO;** hinzu.
2. Fügen Sie „Program.cs“ den folgenden Code hinzu.
3. Führen Sie die Konsolen-App aus, und melden Sie sich bei Ihrem Power BI-Konto an. Daraufhin sollte im Konsolenfenster **Dataset erstellt** angezeigt werden. Sie können sich auch bei Power BI anmelden, um das neue Dataset anzuzeigen.

**Beispiel für das Übertragen von Daten in ein Dataset per Push**

Fügen Sie diesen Code der Datei „Program.cs“ hinzu.

* In „static void Main(string[]args)“:
  
    ```csharp
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Fügen Sie eine „CreateDataset()“-Methode hinzu:
  
    ```csharp
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
    ```

Im nächsten Schritt erfahren Sie, wie Sie ein [Dataset zum Hinzufügen von Zeilen zu einer Power BI-Tabelle abrufen](walkthrough-push-data-get-datasets.md).

Nachstehend finden Sie die [vollständige Codeliste](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Vollständige Codeliste

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;

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
    }
}
```

[Nächster Schritt >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>Nächste Schritte
* [Abrufen eines Datasets, um einer Power BI-Tabelle Zeilen hinzuzufügen](walkthrough-push-data-get-datasets.md)  
* [Abrufen eines Authentifizierungszugriffstokens](walkthrough-push-data-get-token.md)  
* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)  
[PostDatasetInGroup](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdatasetingroup)  
* [Übertragung von Daten in ein Power BI-Dashboard per Push](walkthrough-push-data.md)  
* [Übersicht über Power BI-REST-API](overview-of-power-bi-rest-api.md)  
* [Referenz zur Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

