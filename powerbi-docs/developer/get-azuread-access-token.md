---
title: Authentifier les utilisateurs et obtenir un jeton d’accès Azure AD pour votre application
description: Découvrez comment inscrire une application dans Azure Active Directory afin de l’utiliser avec l’incorporation de contenu Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 08/11/2017
ms.author: maghan
ms.openlocfilehash: 51ad188479c11f5a0d16768eee8c533bdc71c59c
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39359929"
---
# <a name="authenticate-users-and-get-an-azure-ad-access-token-for-your-power-bi-app"></a>Authentifier les utilisateurs et obtenir un jeton d’accès Azure AD pour votre application Power BI
Découvrez comment authentifier les utilisateurs au sein de votre application Power BI et récupérer un jeton d’accès à utiliser avec l’API REST.

Avant de pouvoir appeler l’API REST Power BI, vous devez obtenir un **jeton d’accès d’authentification** (jeton d’accès) Azure Active Directory (Azure AD). Un **jeton d’accès** est utilisé pour autoriser l’accès de votre application aux tableaux de bord, rapports et vignettes **Power BI**. Pour en savoir plus sur le flux **de jetons d’accès** dans Azure Active Directory, consultez [Flux d’octroi d’un code d’autorisation Azure AD](https://msdn.microsoft.com/library/azure/dn645542.aspx).

La récupération du jeton d’accès varie selon la façon dont vous incorporez du contenu. Cet article décrit deux approches.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Pour un jeton d’accès pour les utilisateurs Power BI (l’utilisateur possède les données)
Cet exemple illustre les situations où vos utilisateurs se connectent manuellement à Azure AD en utilisant les informations de connexion fournies par leur organisation. Il est utilisé lors de l’incorporation de contenu pour les utilisateurs Power BI qui accèdent à leur contenu dans le service Power BI.

### <a name="get-an-authorization-code-from-azure-ad"></a>Obtenir un code d’autorisation à partir d’Azure AD
La première étape pour obtenir un **jeton d’accès** est de vous procurer un code d’autorisation depuis **Azure AD**. Pour ce faire, vous créez une chaîne de requête avec les propriétés suivantes, et redirigez vers **Azure AD**.

**Chaîne de requête de code d’autorisation**

```
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
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

Après avoir créé une chaîne de requête, vous redirigez vers **Azure AD** pour obtenir un **code d’autorisation**.  Voici une méthode C# complète pour créer une chaîne de requête de **code d’autorisation** et rediriger vers **Azure AD**. Une fois que vous avez le code d’autorisation, vous obtenez un **jeton d’accès** à l’aide du **code d’autorisation**.

Dans redirect.aspx.cs, le système appelle [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) pour générer le jeton.

**Obtenir un code d’autorisation**

```
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
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.windows.net/common/oauth2/authorize/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Obtenir un jeton accès à partir du code d’autorisation
Vous devez maintenant avoir un code d’autorisation d’Azure AD. Une fois **qu’Azure AD** vous redirige vers votre application web avec un **code d’autorisation**, vous utilisez le **code d’autorisation** pour obtenir un jeton d’accès. Voici un exemple C# que vous pouvez utiliser dans votre page de redirection et l’événement Page_Load pour votre page default.aspx.

L’espace de noms **Microsoft.IdentityModel.Clients.ActiveDirectory** peut être récupéré à partir du package NuGet [ADAL (Active Directory Authentication Library)](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).

```
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

**Redirect.aspx.cs**

```
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

**Default.aspx**

```
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
Cette approche est généralement utilisée pour les applications de type ISV où l’application est propriétaire de l’accès aux données. Les utilisateurs ne sont pas nécessairement des utilisateurs Power BI et l’application contrôle l’authentification et l’accès pour le compte des utilisateurs finaux.

Dans cette approche, vous utilisez un seul compte *principal* qui est un utilisateur Power BI Pro. Les informations d’identification pour ce compte sont stockées avec l’application. L’application s’authentifie auprès d’Azure AD en utilisant ces informations d’identification stockées. L’exemple de code ci-dessous provient de l’exemple [L’application possède les données](https://github.com/guyinacube/PowerBI-Developer-Samples/tree/master/App%20Owns%20Data)

**HomeController.cs**

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;

// Create a user password cradentials.
var credential = new UserPasswordCredential(Username, Password);

// Authenticate using created credentials
var authenticationContext = new AuthenticationContext(AuthorityUrl);
var authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, ClientId, credential);

if (authenticationResult == null)
{
    return View(new EmbedConfig()
    {
        ErrorMessage = "Authentication Failed."
    });
}

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

Pour plus d’informations sur l’utilisation de l’instruction **await**, consultez [await (référence C#)](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/await)

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez le jeton d’accès, vous pouvez appeler l’API REST Power BI pour incorporer le contenu. Pour plus d’informations sur l’incorporation de votre contenu, consultez [Incorporation de vos tableaux de bord, rapports et vignettes Power BI](embed-sample-for-customers.md#embed-your-content-within-your-application).

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)