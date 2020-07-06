---
title: Configurer les informations d’identification par programmation pour Power BI
description: Guide pratique pour configurer programmatiquement les informations d’identification lors de l’automatisation de Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/23/2020
ms.openlocfilehash: ed35775ac077be7c45807b950530e4e1277d5ac3
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85355004"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurer les informations d’identification par programmation pour Power BI

Suivez les étapes de cet article afin de configurer programmatiquement les informations d’identification pour Power BI.

>[!NOTE]
>* L’utilisateur appelant doit être propriétaire de jeu de données ou administrateur de passerelle. Vous pouvez également utiliser un [principal de service](../embedded/embed-service-principal-certificate.md). Par exemple, le principal de service peut être le propriétaire du jeu de données.
>* Les sources de données cloud et les informations d’identification correspondantes sont gérées au niveau utilisateur.

## <a name="update-credentials-flow-for-data-sources"></a>Mettre à jour un flux d’informations d’identification pour les sources de données

1. Appelez [Obtenir des sources de données](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) pour découvrir les sources de données du jeu de données. Le corps de réponse de chaque source de données, il y a le type, les détails de la connexion, la passerelle et l’ID de source de données.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Générez la chaîne d’informations d’identification conformément aux [exemples de mise à jour de source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) selon le type d’informations d’identification.

    # <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[Kit de développement logiciel (SDK) .NET v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Appelez [Obtenir la passerelle](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) pour récupérer la clé publique de la passerelle.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Chiffrez les informations d’identification.

    # <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[Kit de développement logiciel (SDK) .NET v2](#tab/sdk2)

    Chiffrez la chaîne d’informations d’identification avec la clé publique de la passerelle de l’étape 2. Différentes versions de passerelle peuvent avoir des tailles de clé publique différentes. Reportez-vous aux exemples suivants du code du kit de développement logiciel (SDK), disponibles dans le [référentiel GitHub PowerBI-CSharp](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions) :
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Générez les détails des informations d’identification avec des informations d’identification chiffrées.

    # <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

    Utilisez la classe AssymetricKeyEncriptor avec la clé publique récupérée à l’**étape 3**.

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

5. Appelez [Mettre à jour la source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) pour définir les informations d’identification.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurer une nouvelle source de données pour une passerelle de données

1. Installez la [passerelle de données locale](https://powerbi.microsoft.com/gateway/) sur votre ordinateur.

2. Appelez [Obtenir les passerelles](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) pour récupérer la clé publique et l’ID de la passerelle.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Générez les détails des informations d’identification comme décrit dans [mettre à jour le flux des informations d’identification pour les sources de données](#update-credentials-flow-for-data-sources) à l’aide de la clé publique de la passerelle récupérée à l’**étape 2**.

4. Créer le corps de la requête.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Appelez l’API [Créer une source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Types d'informations d'identification

Quand vous appelez [Créer une source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) ou [Mettre à jour la source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) sous une **passerelle locale d’entreprise** en utilisant l’[API Rest Power BI](https://docs.microsoft.com/rest/api/power-bi/), le valeur des informations d’identification doit être chiffrée à l’aide de la clé publique de la passerelle.

>[!NOTE]
>Le Kit de développement logiciel (SDK) .NET v3 peut également exécuter les exemples du kit de développement logiciel (SDK) .NET v2 répertoriés ci-dessous.

### <a name="windows-and-basic-credentials"></a>Informations d’identification Windows et de base

# <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[Kit de développement logiciel (SDK) .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Informations d’identification de clé

# <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[Kit de développement logiciel (SDK) .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**Informations d’identification OAuth2**

# <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[Kit de développement logiciel (SDK) .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Informations d’identification anonymes**

# <a name="net-sdk-v3"></a>[Kit de développement logiciel (SDK) .NET v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[Kit de développement logiciel (SDK) .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Passerelle et ID de source de données introuvables lors de l’appel en vue d’obtenir des sources de données

Ce problème signifie que le jeu de données n’est pas lié à une passerelle. Quand vous créez un jeu de données, une source de données sans informations d’identification est créée automatiquement pour chaque connexion cloud sur la passerelle cloud de l’utilisateur. Cette passerelle est utilisée pour stocker les informations d’identification des connexions cloud.

Une fois le jeu de données créé, une liaison automatique est créée entre le jeu de données et une passerelle appropriée, qui contient les sources de données correspondantes pour toutes les connexions. En l’absence d’une telle passerelle ou de plusieurs passerelles appropriées, la liaison automatique échoue.

Si vous utilisez des jeux de données locaux, créez les sources de données locales manquantes et liez manuellement le jeu de données à une passerelle en utilisant [Lier à la passerelle](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Pour découvrir les passerelles pouvant être liées, utilisez [Découvrir des passerelles](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).