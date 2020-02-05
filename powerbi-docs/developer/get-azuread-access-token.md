---
title: Authentifier les utilisateurs et obtenir un jeton d’accès Azure AD pour votre application
description: Découvrez comment inscrire une application dans Azure Active Directory afin de l’utiliser avec l’incorporation de contenu Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/04/2019
ms.openlocfilehash: cac59a4689eecd75c53ca1c62d7b097438b2ae53
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "74310838"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Obtenir un jeton accès Azure AD pour votre application Power BI

Cet article explique comment authentifier les utilisateurs dans votre application Power BI et récupérer un jeton d’accès à utiliser avec l’[API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/).

Avant de pouvoir appeler l’API REST, vous devez obtenir un **jeton d’accès d’authentification** Azure Active Directory (Azure AD). Votre application utilise un jeton pour accéder aux tableaux de bord, rapports et vignettes Power BI. Pour plus d’informations, consultez [Autoriser l’accès aux applications web Azure Active Directory à l’aide du flux d’octroi de code OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/v1-protocols-oauth-code).

La récupération du jeton d’accès varie selon la façon dont vous incorporez du contenu. Cet article montre deux approches différentes.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Pour un jeton d’accès pour les utilisateurs Power BI (l’utilisateur possède les données)

Cet exemple illustre les situations où vos utilisateurs se connectent manuellement à Azure AD avec les informations de connexion de leur organisation. Cette tâche est utilisée lors de l’incorporation de contenu pour les utilisateurs qui ont accès au service Power BI.

### <a name="get-an-azure-ad-authorization-code"></a>Obtenir du code d’autorisation Azure AD

La première étape pour obtenir un **jeton d’accès** est de vous procurer un code d’autorisation depuis **Azure AD**. Construisez une chaîne de requête avec les propriétés suivantes, et redirigez vers **Azure AD**.

#### <a name="authorization-code-query-string"></a>Chaîne de requête de code d’autorisation

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

Après avoir créé une chaîne de requête, vous redirigez vers **Azure AD** pour obtenir un **code d’autorisation**.  Voici une méthode C# complète pour créer une chaîne de requête de **code d’autorisation** et rediriger vers **Azure AD**. Vous utilisez ensuite le **code d’autorisation** pour obtenir un **jeton d’accès**.

Dans redirect.aspx.cs, des appels de [AuthenticationContext.AcquireTokenByAuthorizationCode](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) pour générer le jeton.

#### <a name="get-authorization-code"></a>Obtenir un code d’autorisation

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

### <a name="get-an-access-token-from-authorization-code"></a>Obtenir un jeton accès à partir du code d’autorisation

Une fois qu’**Azure AD** vous a redirigé vers votre application web avec un **code d’autorisation**, vous devez utiliser celui-ci pour obtenir un jeton d’accès. Voici un exemple en C# que vous pouvez utiliser dans votre page de redirection et l’événement `Page_Load` de default.aspx.

Vous pouvez récupérer l’espace de noms **Microsoft.IdentityModel.Clients.ActiveDirectory** à partir du package NuGet [ADAL (Active Directory Authentication Library)](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

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

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Jeton d’accès pour les utilisateurs non-Power BI (l’application possède les données)

Cette approche est généralement utilisée pour les applications de type ISV où l’application est propriétaire de l’accès aux données. Les utilisateurs ne sont pas nécessairement des utilisateurs Power BI, et l’application contrôle leur authentification et leur accès.

### <a name="access-token-with-a-master-account"></a>Jeton d’accès avec un compte principal

Dans cette approche, vous utilisez un seul compte *principal* qui est un utilisateur Power BI Pro. Les informations d’identification de compte sont stockées avec l’application. L’application s’authentifie auprès d’Azure AD avec ces informations d’identification stockées. L’exemple de code ci-dessous provient de l’exemple [L’application possède les données](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Jeton d’accès avec un principal du service

Pour cette approche, vous utilisez un [principal du service](embed-service-principal.md), qui est un jeton **application uniquement**. L’application s’authentifie auprès d’Azure AD avec un principal du service. L’exemple de code ci-dessous provient de l’exemple [L’application possède les données](https://github.com/guyinacube/PowerBI-Developer-Samples)

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

## <a name="troubleshoot"></a>Résoudre des problèmes

Message d’erreur : « AuthenticationContext' ne contient pas de définition pour 'AcquireToken', et aucun 'AcquireToken' accessible qui accepte un premier argument de type 'AuthenticationContext' n’a été trouvé (peut-être vous manque-t-il une directive using ou une référence d’assembly ?) ».

   Si vous voyez cette erreur, essayez de télécharger [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez le jeton d’accès, vous pouvez appeler l’API REST Power BI pour incorporer le contenu. Pour plus d’informations, consultez [Guide pratique pour incorporer votre contenu Power BI](embed-sample-for-customers.md#embed-content-within-your-application).

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
