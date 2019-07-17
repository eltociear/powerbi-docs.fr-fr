---
title: Utiliser des jeux de données dans des espaces de travail (préversion) - Power BI
description: Découvrez comment vous pouvez partager un jeu de données avec des utilisateurs au sein de l’organisation. Ils peuvent ensuite générer des rapports basés sur votre jeu de données dans leurs propres espaces de travail.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17a8e1c9e0d46a56d6b6ff3e46c0fda6da8ffe12
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567848"
---
# <a name="use-datasets-across-workspaces-preview"></a>Utiliser des jeux de données dans des espaces de travail (préversion)

Le décisionnel est une activité de collaboration. Il est important de définir des jeux de données normalisés qui peuvent constituer la « source de vérité ». La découverte et la réutilisation de ces jeux de données normalisés sont donc primordiales. Quand les modélisateurs de données expérimentés de votre organisation créent et partagent des jeux de données optimisés, les créateurs de rapports peuvent démarrer avec ces jeux de données pour générer des rapports précis. Votre organisation dispose alors de données cohérentes pour prendre des décisions ainsi que d’une culture de données saine.

![Sélectionner un jeu de données partagé](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

Dans Power BI, les créateurs de jeux de données peuvent *certifier* ou *promouvoir* des jeux de données afin que d’autres personnes puissent les découvrir. De cette façon, les auteurs de rapports savent quel jeu de données est officiel et de bonne qualité, et ils peuvent utiliser ces jeux de données partout où ils créent dans Power BI. Les propriétaires de jeux de données peuvent garder le contrôle des utilisateurs autorisés à accéder à leurs données à l’aide de l’[autorisation de génération](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Les administrateurs de locataires ont un nouveau paramètre de locataire pour [régir l’utilisation des jeux de données dans des espaces de travail](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Partage de jeux de données et nouvelle expérience d’espace de travail

La génération de rapports basés sur des jeux de données dans divers espaces de travail ainsi que la copie des rapports dans différents espaces de travail sont étroitement liées à la [nouvelle expérience d’espace de travail](service-create-the-new-workspaces.md) :

- Dans le service, quand vous ouvrez le catalogue de jeux de données à partir d’une nouvelle expérience d’espace de travail, le catalogue montre les jeux de données qui sont dans votre espace de travail personnel et dans d’autres espaces de travail de nouvelle expérience. 
- Lorsque vous ouvrez le catalogue de jeux de données à partir d’un espace de travail classique, vous voyez uniquement les jeux de données dans cet espace de travail, et non ceux des autres espaces de travail.
- Dans Power BI Desktop, vous pouvez publier des rapports Live Connect sur différents espaces de travail, tant que leurs jeux de données sont dans les espaces de travail de nouvelle expérience.
- Lors de la copie de rapports dans des espaces de travail, l’espace de travail cible doit être un espace de travail de nouvelle expérience.

## <a name="build-permission-for-datasets"></a>Autorisation de génération pour les jeux de données

Avec le type d’autorisation de génération, vous pouvez autoriser d’autres personnes dans votre organisation à générer un nouveau contenu, tel que des rapports, des tableaux de bord et des vignettes épinglées à partir de Q&R sur un jeu de données existant. Elles peuvent également générer un nouveau contenu sur le jeu de données hors de Power BI, comme des feuilles Excel par le biais de la fonctionnalité Analyser dans Excel, XMLA et Export. Découvrez plus en détail l’[autorisation de génération](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Découvrir des jeux de données (préversion)

Lorsque vous générez un rapport à partir d’un jeu de données existant, la première étape consiste à se connecter au jeu de données, dans le service Power BI ou Power BI Desktop. En savoir plus sur la [découverte de jeux de données à partir de différents espaces de travail (préversion)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copier un rapport

Lorsque vous trouvez un rapport que vous aimez, dans un espace de travail ou une application, vous pouvez en effectuer une copie et le modifier selon vos besoins. Vous n’avez pas à vous soucier de la création du modèle de données. Il est déjà créé pour vous. En outre, il est beaucoup plus facile de modifier un rapport existant que de démarrer à partir de zéro. Découvrez plus en détail la [copie des rapports](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Promotion et certification

Si vous créez des jeux de données, quand vous en créez un qui peut bénéficier à d’autres utilisateurs, vous pouvez leur permettre de le découvrir facilement par la [promotion de votre jeu de données](service-datasets-promote.md). Vous pouvez également demander aux experts de votre organisation de [certifier votre jeu de données](service-datasets-certify.md).

## <a name="licensing"></a>Licensing

Les expériences et fonctionnalités spécifiques basées sur les capacités des jeux de données partagés sont concédées sous licence selon les scénarios existants.  Par exemple :

- En règle générale, la découverte des jeux de données partagés et la connexion à ceux-ci sont à la portée de tout le monde. Toutefois, les utilisateurs sans licence Pro peuvent uniquement se connecter aux jeux de données qui se trouvent dans leur espace de travail personnel ou dans des espaces de travail Premium.
- La promotion et la certification des jeux de données en dehors des espaces de travail personnels nécessite une licence Pro, car vous en avez besoin pour être membre d’un espace de travail d’application.
- La copie de rapports entre différents espaces de travail nécessite une licence Pro, car vous en avez là aussi besoin pour être membre d’un espace de travail d’application.
- La copie de rapports à partir d’une application requiert une licence Pro, comme pour les packs de contenu d’organisation.

## <a name="considerations-and-limitations"></a>Considérations et limitations

- La génération d’un rapport à partir d’un jeu de données dans un autre espace de travail nécessite la nouvelle expérience d’espace de travail aux deux extrémités : Le rapport ainsi que le jeu de données doivent se trouver dans une nouvelle expérience d’espace de travail.
- Dans un espace de travail classique, l’expérience de découverte de jeux de données affiche uniquement les jeux de données dans cet espace de travail.
- Vous pouvez créer des rapports dans des espaces de travail d’application qui sont basés sur des jeux de données dans un autre espace de travail. Toutefois, vous ne pouvez pas créer une application pour un espace de travail qui contient ces jeux de données.
- Les utilisateurs de la version gratuite de Desktop voient uniquement les jeux de données à partir de leur espace de travail personnel et des espaces de travail Premium.
- Si vous souhaitez ajouter un rapport basé sur un jeu de données partagé à une application, vous devez être membre de l’espace de travail du jeu de données. Il s’agit d’un problème connu.
- « Publier sur le web » ne fonctionne pas pour un rapport basé sur un jeu de données partagé. Cela est lié à la conception.
- Si deux personnes sont membres d’un espace de travail qui accède à un jeu de données partagé, il est possible que seule l’une d’entre elles puisse voir le jeu de données connexe dans l’espace de travail. Seuls les utilisateurs possédant au moins un accès en lecture au jeu de données peuvent voir le jeu de données partagé. 

## <a name="next-steps"></a>Étapes suivantes

- [Promouvoir les jeux de données](service-datasets-promote.md)
- [Certifier des jeux de données](service-datasets-certify.md)
- [Régir l’utilisation des jeux de données dans des espaces de travail](service-datasets-admin-across-workspaces.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
