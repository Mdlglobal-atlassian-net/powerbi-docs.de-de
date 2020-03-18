---
title: Authentifizieren von Benutzern und Abrufen eines Azure AD-Zugriffstokens für die Anwendung
description: Erfahren Sie, wie Sie eine Anwendung zum Einbetten von Power BI-Inhalten in Azure Active Directory registrieren können.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/04/2019
ms.openlocfilehash: 7bd184c02c0bbfd947fa9283890a4f1110177583
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79492282"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Abrufen eines Azure AD-Zugriffstokens für Ihre Power BI-Anwendung

In diesem Artikel erfahren Sie, wie Sie Benutzer in Ihrer Power BI-Anwendung authentifizieren und ein Zugriffstoken für die Verwendung mit der [Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/) abrufen.

Bevor Ihre App die REST-API abruft, müssen Sie ein Azure Active Directory-**Authentifizierungszugriffstoken** (Azure AD) abrufen. Ihre App verwendet ein Token für den Zugriff auf Power BI-Dashboards, Kacheln und Bericht. Weitere Informationen finden Sie unter [Authorize access to Azure Active Directory web applications using the OAuth 2.0 code grant flow (Autorisieren des Zugriffs auf Azure Active Directory-Webanwendungen mit )](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

Je nachdem, wie Sie Inhalte einbetten, wird das Zugriffstoken auf andere Weise abgerufen. In diesem Artikel werden zwei verschiedene Ansätze erläutert.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Zugriffstoken für Power BI-Benutzer (Benutzer ist Besitzer der Daten)

Dieses Beispiel ist auf eine Situation ausgelegt, in der sich Ihre Benutzer mit ihren Organisationsanmeldeinformationen manuell bei Azure AD anmelden. Diese Aufgabe wird zum Einbetten von Inhalten für Benutzer verwendet, die auf den Power BI-Dienst zugreifen können.

### <a name="get-an-azure-ad-authorization-code"></a>Abrufen eines Azure AD-Autorisierungscodes

Der erste Schritt beim Abrufen eines **Zugriffstokens** ist das Abrufen eines Autorisierungscodes von **Azure AD**. Erstellen Sie eine Abfragezeichenfolge mit den folgenden Eigenschaften und leiten diese an **Azure AD** weiter.

#### <a name="authorization-code-query-string"></a>Abfragezeichenfolge für den Autorisierungscode

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

Nachdem Sie eine Abfragezeichenfolge erstellt haben, leiten Sie diese weiter an **Azure AD**, um einen **Autorisierungscode** abzurufen.  Im Folgenden finden Sie eine vollständige C#-Methode zum Erstellen einer Abfragezeichenfolge für den **Autorisierungscode** und leiten diese an **Azure AD** weiter. Verwenden Sie dann den **Autorisierungscode**, um ein **Zugriffstoken** abzurufen.

In „redirect.aspx.cs“ wird [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) aufgerufen, um das Token zu generieren.

#### <a name="get-authorization-code"></a>Abrufen des Autorisierungscodes

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Abrufen eines Zugriffstokens aus dem Autorisierungscode

Nach der Weiterleitung durch **Azure AD** mit einem **Autorisierungscode** an Ihre Web-App können Sie es zum Abrufen eines Zugriffstokens verwenden. Unten finden Sie ein C#-Beispiel, das Sie für Ihre Umleitungsseite und das `Page_Load`-Ereignis von „default.aspx“ verwenden können.

Sie können den Namespace **Microsoft.IdentityModel.Clients.ActiveDirectory** aus dem NuGet-Paket der [Active Directory-Authentifizierungsbibliothek](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) abrufen.

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Zugriffstoken für Benutzer, die kein Power BI verwenden (App ist Besitzer der Daten)

Dieser Ansatz wird normalerweise für Anwendungen des Typs „unabhängiger Softwarehersteller“ (Independent Software Vendor, ISV) verwendet, bei denen die App Zugriff auf die Daten hat. Bei den Benutzern handelt es sich nicht unbedingt um Power BI-Benutzer, und die Anwendung steuert die Benutzerauthentifizierung und den Zugriff.

### <a name="access-token-with-a-master-account"></a>Zugriffstoken mit einem Masterkonto

Bei diesem Ansatz verwenden Sie ein einziges *Masterkonto*, das einen Power BI Pro-Benutzer darstellt. Die Kontoanmeldeinformationen werden zusammen mit der Anwendung gespeichert. Die Anwendung authentifiziert sich mit diesen gespeicherten Anmeldeinformationen bei Azure AD. Der Beispielcode unten stammt aus dem [Beispiel zu Daten im Besitz der App](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Zugriffstoken mit Dienstprinzipal

Bei diesem Ansatz verwenden Sie einen [Dienstprinzipal](embed-service-principal.md), d.h. ein Token **nur für Anwendungen**. Die Anwendung authentifiziert sich mit einem Dienstprinzipal bei Azure AD. Der Beispielcode unten stammt aus dem [Beispiel zu Daten im Besitz der App](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Problembehandlung

Fehlermeldung: "'AuthenticationContext' doesn't contain a definition for 'AcquireToken' and no accessible 'AcquireToken' accepting a first argument of type 'AuthenticationContext' could be found (are you missing a using directive or an assembly reference?)" (‚AuthenticationContext‘ enthält keine Definition für ‚AcquireToken‘, und es konnte kein zugängliches ‚AcquireToken‘ gefunden werden, das das erste Argument des Typs ‚AuthenticationContext‘ akzeptiert (Fehlt möglicherweise eine using-Direktive oder ein Assemblyverweis?)).

   Laden Sie [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) herunter, wenn dieser Fehler angezeigt wird.

## <a name="next-steps"></a>Nächste Schritte

Nun verfügen Sie über das Zugriffstoken und können die Power BI-REST-API aufrufen, um Inhalte einzubetten. Weitere Informationen finden Sie unter [Einbetten von Power BI-Inhalt](embed-sample-for-customers.md#embed-content-within-your-application).

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
