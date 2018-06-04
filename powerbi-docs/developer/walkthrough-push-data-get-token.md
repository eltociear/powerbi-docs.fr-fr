---
title: Obtenir un jeton d’accès d’authentification
description: 'Procédure pas à pas pour transmettre des données : obtenir un jeton d’accès d’authentification'
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: maghan
ms.openlocfilehash: 640c6dac9a896cff55bddad46ceef8bce7ccae14
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34289369"
---
# <a name="step-2-get-an-authentication-access-token"></a>Étape 2 : Obtenir un jeton d’accès d’authentification
Cet article fait partie d’une procédure pas à pas pour [transmettre des données à un jeu de données](walkthrough-push-data.md).

À l’**étape 1** de la procédure de transmission des données à un jeu de données intitulée [Inscrire l’application auprès d’Azure AD](walkthrough-push-data-register-app-with-azure-ad.md), vous avez inscrit une application cliente dans Azure AD. Pendant cette étape, vous obtenez un jeton d’accès d’authentification. Les applications Power BI sont intégrées à **Azure AD** afin d’offrir une connexion et une autorisation sécurisées pour votre application. Vous utilisez un jeton pour vous authentifier auprès d’ **Azure AD** et accéder aux ressources Power BI.

Voici comment obtenir un jeton d’accès d’authentification.

## <a name="get-an-authentication-access-token"></a>Obtenir un jeton d’accès d’authentification
> **REMARQUE** : avant de commencer, veillez à suivre les étapes précédentes de la procédure pas à pas intitulée [Transmettre des données à un jeu de données](walkthrough-push-data.md).
> 
> 

1. Dans Visual Studio 2015, créez un projet **Application console** .
2. Installez le [package NuGet Bibliothèque d’authentification Azure AD pour .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/). Pour obtenir un jeton de sécurité d’authentification dans une application .NET, vous utilisez ce package. Voici comment installer le package :
   
     a. Dans Visual Studio 2015, choisissez **Outils** > **Gestionnaire de package NuGet** > **Console du Gestionnaire de package**.
   
     b. Dans la **Console du Gestionnaire de package**, entrez Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612.
3. Ajoutez le code ci-dessous dans la classe Program {...}.
4. Remplacez « {ClientID} » par l’ **ID client** que vous avez obtenu quand vous avez inscrit l’application. Consultez [Inscrire l’application auprès d’Azure AD](walkthrough-push-data-register-app-with-azure-ad.md).
5. Après avoir installé le package Microsoft.IdentityModel.Clients.ActiveDirectory, ajoutez **using Microsoft.IdentityModel.Clients.ActiveDirectory;** au fichier Program.cs.
6. Exécutez l’application console, puis connectez-vous à votre compte Power BI. Une chaîne de jeton doit apparaître dans la fenêtre de console.

**Exemple de code pour obtenir un jeton de sécurité d’authentification**

Ajoutez ce code à Program {...}.

* Une variable de jeton pour appeler des opérations :
  
  ```
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* Dans static void Main(string[] args) :
  
  ```
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Ajoutez une méthode GetToken() :

```
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
           string authorityUri = "https://login.windows.net/common/oauth2/authorize";

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

Après avoir obtenu un jeton d’authentification, vous pouvez appeler une opération Power BI. L’étape suivante vous montre comment appeler l’opération [Créer un jeu de données](https://msdn.microsoft.com/library/mt203562.aspx) pour créer un jeu de données afin de transmettre des données à un tableau de bord.

L’étape suivante vous montre comment [créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md).

Ci-après figure le [listing du code complet](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Listing du code complet
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
                string authorityUri = "https://login.windows.net/common/oauth2/authorize";

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


[Étape suivante >](walkthrough-push-data-create-dataset.md)

## <a name="next-steps"></a>Étapes suivantes
[Créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md)  
[Inscrire une application auprès d’Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)  
[Package NuGet Bibliothèque d’authentification Azure AD pour .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)  
[Transmettre des données à un jeu de données Power BI](walkthrough-push-data.md)  
[Vue d’ensemble de l’API REST Power BI](overview-of-power-bi-rest-api.md)  
[Référence de l’API REST de Power BI](https://msdn.microsoft.com/library/mt147898.aspx)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

