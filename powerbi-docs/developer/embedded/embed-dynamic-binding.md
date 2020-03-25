---
title: Connecter un rapport à un jeu de données à l’aide de la liaison dynamique
description: Découvrez comment incorporer un rapport à l’aide de la liaison dynamique.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: e2c59ba84700aaf83c4cc9d16d009696c42dfc54
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114586"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Connecter un rapport à un jeu de données à l’aide de la liaison dynamique 

Quand un rapport est connecté à un jeu de données, vous pouvez utiliser la liaison dynamique. La connexion entre le rapport et le jeu de données est appelée *liaison*. Quand la liaison est déterminée au point d’incorporation, et non pas prédéterminée auparavant, la liaison est appelée « liaison dynamique ».

Lors de l’incorporation d’un rapport Power BI à l’aide de la *liaison dynamique*, vous pouvez connecter le même rapport à différents jeux de données en fonction des informations d’identification de l’utilisateur.

Cela signifie que vous pouvez utiliser un rapport pour afficher des informations différentes, en fonction du jeu de données auquel il est connecté. Par exemple, un rapport qui indique les valeurs de vente au détail peut être connecté à différents jeux de données du détaillant et produire des résultats différents, en fonction du jeu de données du détaillant auquel il est connecté.

Le rapport et le jeu de données n’ont pas besoin de se trouver dans le même espace de travail. Les deux espaces de travail (celui contenant le rapport et celui contenant le jeu de données) doivent être affectés à une [capacité](azure-pbie-create-capacity.md).

Dans le cadre du processus d’incorporation, assurez-vous que vous *générez un jeton avec des autorisations suffisantes* et *ajustez l’objet de configuration*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Génération d’un jeton avec des autorisations suffisantes

La liaison dynamique est prise en charge dans les deux scénarios : *Incorporation pour votre organisation* et *Incorporation pour vos clients*. Le tableau ci-dessous décrit les considérations relatives à chaque scénario.

|Scénario  |Propriété des données  |Jeton  |Configuration requise  |
|---------|---------|---------|---------|
|*Incorporation pour votre organisation*    |L’utilisateur possède les données         |Jeton d’accès pour les utilisateurs de Power BI         |L’utilisateur dont le jeton Azure AD est utilisé doit avoir les autorisations appropriées pour tous les artefacts.         |
|*Incorporation pour vos clients*     |L’application possède les données         |Jeton d’accès pour les clients qui n’utilisent pas Power BI         |Doit inclure des autorisations à la fois pour le rapport et le jeu de données lié dynamiquement. Utilisez [l’API pour générer un jeton incorporé pour plusieurs éléments](embed-sample-for-customers.md#multiEmbedToken), afin de générer un jeton d’incorporation qui prend en charge plusieurs artefacts.         |

## <a name="adjusting-the-config-object"></a>Ajustement de l’objet de configuration
Ajoutez `datasetBinding` à l’objet de configuration. Utilisez l’exemple ci-dessous comme référence.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Étapes suivantes

Si vous débutez avec l’incorporation dans Power BI, suivez ces tutoriels pour découvrir comment incorporer votre contenu Power BI :
* [Tutoriel : Incorporer du contenu Power BI dans une application pour vos clients](embed-sample-for-customers.md)
* [Tutoriel : Incorporer du contenu Power BI dans une application pour votre organisation](embed-sample-for-your-organization.md)