---
title: Obtenir un jeton d’accès d’authentification
description: Procédure pas à pas pour envoyer (push) des données - Obtenir un jeton d’accès d’authentification
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488266"
---
# <a name="step-2-get-an-authentication-access-token"></a>Étape 2 : Obtenir un jeton d’accès d’authentification

Cet article constitue la deuxième étape de la série [Envoyer (push) des données vers un jeu de données Power BI](walkthrough-push-data.md).

Dans l’étape 1, vous avez [inscrit une application cliente dans Azure AD](../embedded/register-app.md). Pendant cette étape, vous obtenez un jeton d’accès d’authentification. Les applications Power BI sont intégrées à Azure Active Directory dans le but de fournir un système de connexion et d’autorisation sécurisé à votre application. Votre application utilise un jeton pour s’authentifier auprès d’Azure AD et accéder aux ressources Power BI.

## <a name="get-an-authentication-access-token"></a>Obtenir un jeton d’accès d’authentification

Avant de commencer, vérifiez que vous avez effectué l’[étape précédente](../embedded/register-app.md) de la série [Envoyer (push) des données vers un jeu de données Power BI](walkthrough-push-data.md). 

Cette procédure nécessite Visual Studio 2015 ou version ultérieure.

1. Dans Visual Studio, créez un projet **Application console** en C#.

2. Installez le [package NuGet Bibliothèque d’authentification Azure AD pour .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). Votre application .NET a besoin de ce package pour obtenir un jeton de sécurité d’authentification. 

     a. Sélectionnez **Outils** > **Gestionnaire de package NuGet** > **Console du Gestionnaire de package**.

     b. Entrez **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**.

     c. Dans Program.cs, ajoutez `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Dans le fichier Program.cs, ajoutez l’exemple de code figurant après ces étapes.

4. Remplacez « {ClientID} » par l’**ID Client** que vous avez obtenu dans l’[article précédent de la série](../embedded/register-app.md), lorsque vous avez inscrit votre application.

5. Exécutez l’application console, puis connectez-vous à votre compte Power BI. 

   Une chaîne de jeton doit s’afficher dans la fenêtre de console.

**Exemple de code pour obtenir un jeton de sécurité d’authentification**

Ajoutez ce code à Program {...}.

* Une variable de jeton pour appeler des opérations : 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* Dans static void Main(string[] args) :
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Ajoutez une méthode GetToken() :

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

Après avoir obtenu un jeton d’authentification, vous pouvez appeler une opération Power BI.

L’article suivant de cette série vous montre comment [créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Listing du code complet

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



## <a name="next-steps"></a>Étapes suivantes

* L’article suivant de cette série est [Créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md)
* [Vue d’ensemble de l’API REST Power BI](overview-of-power-bi-rest-api.md)  
* [API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/)  

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)