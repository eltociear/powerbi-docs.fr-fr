---
title: Obtenir un jeu de données pour ajouter des lignes
description: 'Procédure pas à pas pour transmettre des données : obtenir un jeu de données pour ajouter des lignes à une table Power BI'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: a150666eafd8dc11b573150455775d2ecf6f7f1b
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748307"
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>Étape 4 : Obtenir un jeu de données pour ajouter des lignes à une table Power BI

Cet article fait partie d’une procédure pas à pas pour [transmettre des données à un jeu de données](walkthrough-push-data.md).

À l’**étape 3** de la procédure Transmettre des données à un jeu de données intitulée [Créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md), vous avez appelé l’opération [Créer un jeu de données](/rest/api/power-bi/datasets) pour créer un jeu de données dans Power BI. Pendant cette étape, vous utilisez l’opération [Obtenir des jeux de données](/rest/api/power-bi/datasets/getdatasets) et Newtonsoft.Json pour obtenir un ID de jeu de données. Vous utilisez l’ID de jeu de données à l’étape 4 pour ajouter des lignes à un jeu de données. 

Pour transmettre des données à un jeu de données Power BI, vous devez référencer la table dans le jeu de données. Pour référencer une table dans un jeu de données, vous devez d’abord obtenir un **ID de jeu de données**. Vous obtenez un **ID de jeu de données** avec l’opération [Obtenir les jeux de données](/rest/api/power-bi/datasets/getdatasets). L’opération **Obtenir les jeux de données** retourne une chaîne JSON contenant la liste de tous les jeux de données dans Power BI. Pour désérialiser une chaîne JSON, il est recommandé d’utiliser [Newtonsoft.Json](https://www.newtonsoft.com/json).

Voici comment obtenir un jeu de données.

## <a name="get-a-power-bi-dataset"></a>Obtenir un jeu de données Power BI

> **REMARQUE** : Avant de commencer, veillez à suivre les étapes précédentes de la procédure pas à pas [Transmettre des données à un jeu de données](walkthrough-push-data.md).

1. Dans le projet Application console que vous avez créé à l’étape 2 de la procédure pas à pas pour transmettre des données, [Obtenir un jeton d’accès d’authentification](walkthrough-push-data-get-token.md), installez le package NuGet Newtonsoft.Json. Voici comment installer le package :

     a. Dans Visual Studio 2015, choisissez **Outils** > **Gestionnaire de package NuGet** > **Console du Gestionnaire de package**.

     b. Dans la **Console du Gestionnaire de package**, entrez Install-Package Newtonsoft.Json.
2. Une fois le package installé, ajoutez **using Newtonsoft.Json;** au fichier Program.cs.
3. Dans le fichier Program.cs, ajoutez le code ci-dessous pour obtenir un **ID de jeu de données**.
4. Exécutez l’application console, puis connectez-vous à votre compte Power BI. L’indication **ID de jeu de données :** suivie d’un ID doit apparaître dans la fenêtre de console.

**Exemple d’obtention d’un jeu de données**

Ajoutez ce code dans le fichier Program.cs.

* Dans static void Main(string[] args) :
  
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
* Ajoutez une méthode GetDatset() :
  
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

L’étape suivante vous montre comment [ajouter des lignes à une table Power BI](walkthrough-push-data-add-rows.md).

Ci-après figure le [listing du code complet](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Listing du code complet

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

## <a name="next-steps"></a>Étapes suivantes

* [Ajouter des lignes à une table Power BI](walkthrough-push-data-add-rows.md)  
* [Newtonsoft.Json](https://www.newtonsoft.com/json)  
* [Obtenir des jeux de données](/rest/api/power-bi/datasets/getdatasets)  
* [Transmettre des données à Power BI](walkthrough-push-data.md)  
* [Vue d’ensemble de l’API REST Power BI](overview-of-power-bi-rest-api.md)  
* [Référence de l’API REST de Power BI](/rest/api/power-bi/)  

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)