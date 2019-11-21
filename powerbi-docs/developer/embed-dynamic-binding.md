---
title: Liaison dynamique
description: Découvrez comment incorporer un rapport à l’aide de la liaison dynamique.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8110023de4df28f65129bd53203cec9752acc1af
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864440"
---
# <a name="dynamic-binding"></a>Liaison dynamique

La liaison dynamique permet de sélectionner dynamiquement un jeu de données lors de l’incorporation d’un rapport. Le rapport et le jeu de données n’ont pas besoin de se trouver dans le même espace de travail. Les utilisateurs finaux voient des résultats différents en fonction du jeu de données sélectionné.

Les deux espaces de travail (celui contenant le rapport et celui contenant le jeu de données) doivent être affectés à une capacité.

L’incorporation d’un rapport à l’aide d’une liaison dynamique s’effectue en deux étapes :
1. Génération d’un jeton
2. Ajustement de l’objet de configuration

## <a name="generating-a-token"></a>Génération d’un jeton
Pour générer un jeton, utilisez l’[API permettant de générer un jeton incorporé pour plusieurs éléments](embed-sample-for-customers.md#multiEmbedToken).

La liaison dynamique est prise en charge dans ces deux scénarios d’incorporation : *Incorporation pour votre organisation* et *Incorporation pour vos clients*.

| Solution                   | Jeton                               | Configuration requise                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Incorporation pour votre organisation* | Jeton d’accès pour les utilisateurs de Power BI     | L’utilisateur dont le jeton Azure AD est utilisé doit avoir les autorisations appropriées sur tous les artefacts.                                                                    |
| *Incorporation pour vos clients*    | Jeton d’accès pour les clients qui n’utilisent pas Power BI | Doit inclure des autorisations à la fois pour le rapport et le jeu de données lié dynamiquement. Utilisez la nouvelle API pour générer un jeton incorporé qui prend en charge plusieurs artefacts. |

## <a name="adjusting-the-config-object"></a>Ajustement de l’objet de configuration
Ajoutez `datasetBinding` à l’objet de configuration. Utilisez l’exemple donné en bas de la page comme référence.

Si vous débutez avec l’incorporation dans Power BI, suivez ces tutoriels pour découvrir comment incorporer votre contenu Power BI :
* [Incorporer du contenu Power BI dans une application pour vos clients](embed-sample-for-customers.md)
* [Tutoriel : Incorporer du contenu Power BI dans une application pour votre organisation](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Example
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```