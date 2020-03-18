---
title: Abrufen eines Authentifizierungszugriffstokens
description: 'Exemplarische Vorgehensweise zum Übertragen von Daten mithilfe von Push: Abrufen eines Authentifizierungszugriffstokens'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488267"
---
# <a name="step-2-get-an-authentication-access-token"></a>Schritt 2: Abrufen eines Authentifizierungszugriffstokens

Dieser Artikel ist der zweite Schritt in der Reihe [Push data into a Power BI dataset (Übertragen von Daten in ein Power BI-Dataset mithilfe von Push)](walkthrough-push-data.md).

In Schritt 1 haben Sie [eine Client-App in Azure AD registriert](../embedded/register-app.md). In diesem Schritt rufen Sie ein Authentifizierungszugriffstoken ab. Power BI-Apps sind in Azure Active Directory integriert, um eine sichere Anmeldung und Autorisierung bei Ihrer App zu ermöglichen. Ihre App verwendet ein Token für die Authentifizierung bei Azure AD und den Zugriff auf Power BI-Ressourcen.

## <a name="get-an-authentication-access-token"></a>Abrufen eines Authentifizierungszugriffstokens

Bevor Sie beginnen, sollten Sie sicherstellen, dass Sie den [vorherigen Schritt](../embedded/register-app.md) der Reihe [Push data into a Power BI dataset (Übertragen von Daten in ein Power BI-Dataset mithilfe von Push)](walkthrough-push-data.md) abgeschlossen haben. 

Für dieses Verfahren ist Visual Studio 2015 oder eine höhere Version erforderlich.

1. Erstellen Sie in Visual Studio ein neues C#-Projekt des Typs **Konsolenanwendung**.

2. Installieren Sie das [NuGet-Paket mit der Azure AD-Authentifizierungsbibliothek für .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). Ihre .NET-App benötigt dieses Paket, um ein Authentifizierungssicherheitstoken abzurufen. 

     a. Klicken Sie auf **Tools** > **NuGet-Paket-Manager** > **Paket-Manager-Konsole**.

     b. Geben Sie **Install-Package „Microsoft.IdentityModel.Clients.ActiveDirectory – Version 2.21.301221612“** ein.

     c. Fügen Sie der „Program.cs“-Datei `using Microsoft.IdentityModel.Clients.ActiveDirectory;` hinzu.

3. Fügen Sie der „Program.cs“-Datei den im Folgenden aufgeführten Beispielcode hinzu.

4. Ersetzen Sie „{ClientID}“ durch die **Client-ID**, die Sie in den [vorherigen Schritten](../embedded/register-app.md) beim Registrieren der App erhalten haben.

5. Führen Sie die Konsolen-App aus, und melden Sie sich bei Ihrem Power BI-Konto an. 

   Im Konsolenfenster sollte eine Tokenzeichenfolge angezeigt werden.

**Beispielcode zum Abrufen des Authentifizierungssicherheitstokens**

Fügen Sie diesen Code „Program {...}“ hinzu.

* Eine Tokenvariable zum Aufrufen von Vorgängen: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* In „static void Main(string[]args)“:
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Eine „GetToken()“-Methode hinzu:

```csharp
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
           string authorityUri = "https://login.microsoftonline.net/common/";

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
```

Nach dem Abruf eines Authentifizierungstokens können Sie sämtliche Power BI-Vorgänge aufrufen.

Im nächsten Artikel dieser Reihe wird das [Erstellen eines Datasets in Power BI](walkthrough-push-data-create-dataset.md) erläutert.


## <a name="complete-code-listing"></a>Vollständige Codeliste

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

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

    }
}
```



## <a name="next-steps"></a>Nächste Schritte

* Der nächste Artikel in dieser Reihe ist [Erstellen eines Datasets in Power BI](walkthrough-push-data-create-dataset.md).
* [Übersicht über Power BI-REST-API](overview-of-power-bi-rest-api.md)  
* [Power BI-REST-APIs](https://docs.microsoft.com/rest/api/power-bi/)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)