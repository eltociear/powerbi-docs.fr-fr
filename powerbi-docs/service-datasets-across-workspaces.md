---
title: Présentation du partage de jeux de données entre plusieurs espaces de travail (préversion)
description: Découvrez comment vous pouvez partager un jeu de données avec des utilisateurs dans toute l’organisation. Ils peuvent ensuite générer des rapports basés sur votre jeu de données dans leurs propres espaces de travail.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d30a8012161934ada4ff3cb2ce6852fe62f48892
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877198"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Présentation du partage de jeux de données entre plusieurs espaces de travail (préversion)

Le décisionnel est une activité de collaboration. Il est important de définir des jeux de données normalisés qui peuvent constituer la « source de vérité ». La découverte et la réutilisation de ces jeux de données normalisés sont donc primordiales. Quand les modélisateurs de données expérimentés de votre organisation créent et partagent des jeux de données optimisés, les créateurs de rapports peuvent démarrer avec ces jeux de données pour générer des rapports précis. Votre organisation dispose alors de données cohérentes pour prendre des décisions ainsi que d’une culture de données saine.

![Sélectionner un jeu de données partagé](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

Dans Power BI, les créateurs de jeux de données peuvent décider des utilisateurs qui sont autorisés à accéder à leurs données à l’aide de l’[autorisation de création](service-datasets-build-permissions.md). Les créateurs de jeux de données peuvent également *certifier* ou *promouvoir* des jeux de données afin que d’autres personnes puissent les découvrir. De cette façon, les auteurs de rapports savent quels jeux de données sont officiels et de bonne qualité, et ils peuvent utiliser ces jeux de données partout où ils créent dans Power BI. Les administrateurs de locataires ont un nouveau paramètre de locataire pour [régir l’utilisation des jeux de données dans des espaces de travail](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Partage de jeux de données et nouvelle expérience d’espace de travail

La génération de rapports basés sur des jeux de données dans divers espaces de travail ainsi que la copie des rapports dans différents espaces de travail sont étroitement liées à la [nouvelle expérience d’espace de travail](service-create-the-new-workspaces.md) :

- Dans le service, quand vous ouvrez le catalogue de jeux de données à partir d’une nouvelle expérience d’espace de travail, le catalogue montre les jeux de données qui sont dans votre espace de travail personnel et dans d’autres espaces de travail de nouvelle expérience. 
- Lorsque vous ouvrez le catalogue de jeux de données à partir d’un espace de travail classique, vous voyez uniquement les jeux de données dans cet espace de travail, et non ceux des autres espaces de travail.
- Dans Power BI Desktop, vous pouvez publier des rapports Live Connect sur différents espaces de travail, tant que leurs jeux de données se trouvent dans les espaces de travail nouvelle version.
- Lors de la copie de rapports dans des espaces de travail, l’espace de travail cible doit être un espace de travail de nouvelle expérience.

## <a name="discover-datasets-preview"></a>Découvrir des jeux de données (préversion)

Lorsque vous générez un rapport à partir d’un jeu de données existant, la première étape consiste à se connecter au jeu de données dans le service Power BI ou Power BI Desktop. En savoir plus sur la [découverte de jeux de données à partir de différents espaces de travail (préversion)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copier un rapport

Lorsque vous trouvez un rapport que vous aimez, dans un espace de travail ou une application, vous pouvez en effectuer une copie et le modifier selon vos besoins. Vous n’avez pas à vous soucier de la création du modèle de données. Il est déjà créé pour vous. En outre, il est beaucoup plus facile de modifier un rapport existant que de démarrer à partir de zéro. Découvrez plus en détail la [copie des rapports](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Autorisation de génération pour les jeux de données

Si vous êtes un créateur de jeux de données, l’autorisation de création vous permet de décider des utilisateurs de votre organisation qui sont autorisés à créer du contenu à partir de vos jeux de données. Les personnes qui disposent de cette autorisation peuvent également créer du contenu à partir du jeu de données en dehors de Power BI (par exemple, dans des feuilles Excel par le biais de la fonctionnalité Analyser dans Excel, XMLA et Export). Découvrez plus en détail l’[autorisation de génération](service-datasets-build-permissions.md).

## <a name="promotion-and-certification"></a>Promotion et certification

Si vous créez des jeux de données dont les autres peuvent bénéficier, vous pouvez faciliter leur découverte en faisant leur [promotion](service-datasets-promote.md). Vous pouvez également demander aux experts de votre organisation de [certifier votre jeu de données](service-datasets-certify.md).

## <a name="licensing"></a>Licensing

Les expériences et fonctionnalités spécifiques basées sur les capacités des jeux de données partagés sont concédées sous licence selon les scénarios existants. Par exemple :

- En règle générale, la découverte des jeux de données partagés et la connexion à ceux-ci sont à la portée de tout le monde : il ne s’agit pas d’une fonctionnalité réservée à la licence Premium.
- Les utilisateurs sans licence Pro peuvent utiliser des jeux de données sur plusieurs espaces de travail pour créer des rapports uniquement si ces jeux de données se trouvent dans leur espace de travail personnel (Mon espace de travail) ou dans un espace de travail sous licence Premium. La même restriction de licence s'applique, qu'ils créent des rapports dans Power BI Desktop ou dans le service Power BI.
- Vous avez besoin d’une licence Pro pour copier des rapports d’un espace de travail à un autre.
- La copie de rapports à partir d’une application requiert une licence Pro, comme pour les packs de contenu d’organisation.
- La promotion et la certification des jeux de données nécessitent également une licence Pro.

## <a name="considerations-and-limitations"></a>Considérations et limitations

- En tant qu’éditeur d’applications, vous devez vous assurer que votre public a accès à des jeux de données en dehors de l’espace de travail. Sinon, les utilisateurs rencontreront des problèmes lors de l'interaction avec votre application : les rapports ne s'ouvriront pas sans accès aux jeux de données, et les vignettes du tableau de bord apparaîtront comme verrouillées. Par ailleurs, les utilisateurs ne pourront pas ouvrir l'application si le premier élément de la navigation est un rapport sans accès au jeu de données.
- La génération d’un rapport à partir d’un jeu de données dans un autre espace de travail nécessite la nouvelle expérience d’espace de travail aux deux extrémités : Le rapport ainsi que le jeu de données doivent se trouver dans une nouvelle expérience d’espace de travail.
- Dans un espace de travail classique, l’expérience de découverte de jeux de données affiche uniquement les jeux de données dans cet espace de travail.
- Par défaut, « Publier sur le web » ne fonctionne pas pour un rapport basé sur un jeu de données partagé.
- Si deux personnes sont membres d’un espace de travail qui accède à un jeu de données partagé, il est possible que seule l’une d’entre elles puisse voir le jeu de données connexe dans l’espace de travail. Seuls les utilisateurs possédant au moins un accès en lecture au jeu de données peuvent voir le jeu de données partagé. 

## <a name="next-steps"></a>Étapes suivantes

- [Promouvoir les jeux de données](service-datasets-promote.md)
- [Certifier des jeux de données](service-datasets-certify.md)
- [Régir l’utilisation des jeux de données dans des espaces de travail](service-datasets-admin-across-workspaces.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
