---
title: Configurer les informations d’identification par programmation pour Power BI
description: Guide pratique pour configurer les informations d’identification par programmation pour Power BI à des fins d’automatisation
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: 2b4e2f5a4e95b412459dd8fe8d497966e541b389
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892836"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configurer les informations d’identification par programmation pour Power BI

Suivez ces étapes pour configurer par programmation les informations d’identification pour Power BI.

## <a name="configure-a-credential-flow-for-data-sources"></a>Configurer un flux d’informations d’identification pour les sources de données

1. Appelez [Obtenir des sources de données](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) pour découvrir les sources de données du jeu de données. Le corps de réponse de chaque source de données indique le type, les détails de la connexion, la passerelle et l’ID de source de données.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Générez la chaîne d’informations d’identification conformément aux [exemples de mise à jour de source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) selon le type d’informations d’identification.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Générez les détails des informations d’identification.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Appelez [Mettre à jour la source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) pour définir les informations d’identification. Utilisez pour cela la passerelle et l’ID de source de données de l’étape 1 ainsi que les détails d’informations d’identification de l’étape 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Flux d’informations d’identification ayant expiré de la source de données locale

1. [Suivez les étapes 1 et 2 du scénario précédent](#configure-credential-flow-for-data-sources).

2. Appelez [Obtenir la passerelle](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) pour récupérer la clé publique de la passerelle.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Chiffrez la chaîne d’informations d’identification avec la clé publique de la passerelle à l’aide de l’algorithme de chiffrement RSA.

    Utilisez la classe d’assistance suivante pour le chiffrement :

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

4. Générez les détails des informations d’identification avec des informations d’identification chiffrées.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Appelez [Mettre à jour la source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) pour définir les informations d’identification.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configurer une nouvelle source de données pour une passerelle de données

1. Installez la [passerelle de données locale](https://powerbi.microsoft.com/gateway/) sur votre ordinateur.

2. Appelez [Obtenir les passerelles](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) pour récupérer la clé publique et l’ID de la passerelle.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Générez les détails des informations d’identification comme dans le scénario précédent à l’aide de la clé publique de passerelle récupérée à l’étape [Flux d’informations d’identification ayant expiré de la source de données locale](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway).

4. générer le corps de la demande

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

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Passerelle et ID de source de données introuvables lors de l’appel en vue d’obtenir des sources de données

Ce problème signifie que le jeu de données n’est pas lié à une passerelle. Quand vous créez un jeu de données, une source de données sans informations d’identification est créée automatiquement pour chaque connexion cloud sur la passerelle cloud de l’utilisateur. Cette passerelle est utilisée pour stocker les informations d’identification des connexions cloud.

Une fois le jeu de données créé, une liaison automatique est établie entre le jeu de données et une passerelle appropriée, qui contient les sources de données correspondantes pour toutes les connexions. En l’absence d’une telle passerelle ou de plusieurs passerelles appropriées, la liaison automatique échoue.

Créez les sources de données locales manquantes, le cas échéant, et liez manuellement le jeu de données à une passerelle en utilisant [Lier à la passerelle](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Pour découvrir les passerelles pouvant être liées, utilisez [Découvrir des passerelles](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).
