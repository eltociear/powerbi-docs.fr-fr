---
title: Chiffrer les informations d’identification
description: 'Procédure pas à pas : Chiffrer les informations d’identification pour les sources de données d’une passerelle locale'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836626"
---
# <a name="encrypt-credentials"></a>Chiffrer les informations d’identification

Quand vous appelez [Créer une source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) ou [Mettre à jour la source de données](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) sous une **passerelle locale d’entreprise** en utilisant l’[API Rest Power BI](https://docs.microsoft.com/rest/api/power-bi/), le valeur des informations d’identification doit être chiffrée à l’aide de la clé publique de la passerelle.

Consultez l’exemple de code ci-dessous, qui montre comment chiffrer les informations d’identification dans .NET.

Les informations d’identification fournies à la méthode EncodeCredentials ci-dessous doivent être dans un des formats suivants, en fonction du type des informations d’identification :

**Informations d’identification de base / Windows**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Informations d’identification de clé**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**Informations d’identification OAuth2**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Informations d’identification anonymes**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Chiffrer les informations d’identification**

Chiffrez la valeur des informations d’identification à l’aide de la clé publique de la passerelle. Différentes versions de passerelle peuvent avoir des tailles de clé publique différentes.

Reportez-vous à l’exemple dans le code du kit SDK, disponible dans le dépôt GitHub PowerBI-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)