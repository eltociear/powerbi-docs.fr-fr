---
title: Organisation du contenu dans les espaces de travail
description: Découvrir plus d’informations sur les espaces de travail et les rôles d’espace de travail
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120157"
---
# <a name="collaborate-in-workspaces"></a>Collaborer dans des espaces de travail

 Les *espaces de travail* sont des emplacements où collaborer avec des collègues sur du contenu spécifique. Les espaces de travail sont créés par des *concepteurs* Power BI pour contenir des collections de tableaux de bord et de rapports. Le concepteur peut ensuite regrouper cette collection dans une *application* et la distribuer dans toute l’organisation, ou à des personnes ou des groupes spécifiques. 

 Toute personne utilisant le service Power BI a également un espace **Mon espace de travail**.  Mon espace de travail est votre bac à sable personnel, où vous pouvez créer du contenu pour vous-même.

 Vous pouvez voir vos espaces de travail depuis **Accueil** dans Power BI ou en sélectionnant **Espace de travail** ou **Mon espace de travail** dans le volet de navigation de gauche.

 ![Volet de navigation montrant deux types d’espaces de travail](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Types des espaces de travail
**Mon espace de travail** stocke tout le contenu qui vous appartient et que vous créez. Considérez-le comme votre zone de travail ou bac à sable personnel pour votre propre contenu. Pour de nombreux *consommateurs* Power BI, **Mon espace de travail** reste vide car votre travail n’implique pas la création de contenu. Les *consommateurs*, par définition, consomment les données créées par d’autres personnes et utilisent ces données pour prendre des décisions commerciales. Si vous recherchez créer un contenu, lisez [les articles Power BI pour les concepteurs](../create-reports/index.yml) à la place.

Les **espaces de travail d’application** regroupent tout le contenu d’une application spécifique. Quand un *concepteur* crée une application, il rassemble tout le contenu nécessaire à l’utilisation de cette application. Le contenu peut inclure des tableaux de bord, des rapports et des jeux de données. Chaque application n’est pas forcément configurée de la sorte. Une application peut contenir un seul tableau de bord, trois éléments de chaque type ou même vingt rapports. Tout dépend de ce que le *concepteur* décide d’inclure dans l’application. En général, les espaces de travail d’application pour les *consommateurs* n’incluent pas les jeux de données.

L’espace de travail de l’application Fig Sales ci-dessous contient trois rapports et un tableau de bord. 

![Volet de navigation montrant deux types d’espaces de travail](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Rôles dans les espaces de travail

Les rôles déterminent ce que vous pouvez faire dans un espace de travail, ce qui permet aux équipes de collaborer.  Lorsqu’ils accordent l’accès à un nouvel espace de travail, les *concepteurs* ajoutent des individus ou des groupes à l’un des rôles de l’espace de travail : **Lecteur**, **Membre**, **Contributeur** ou **Admin**. 


En tant que *consommateur* Power BI, vous allez généralement interagir dans les espaces de travail avec le rôle **Lecteur**. Un *concepteur* peut cependant aussi vous attribuer le rôle **Membre** ou le rôle **Contributeur**. Le rôle Lecteur vous permet de visualiser et d’interagir avec du contenu (tableaux de bord, rapports, applications) créé par d’autres et partagé avec vous. Et comme le rôle Lecteur ne peut pas accéder au jeu de données sous-jacent, il s’agit d’un moyen sûr d’interagir avec le contenu et de ne pas avoir à vous inquiéter de « nuire » aux données sous-jacentes.


Pour obtenir une liste détaillée de ce que vous pouvez faire en tant que *consommateur* avec le rôle Lecteur, consultez [Fonctionnalités de Power BI pour les consommateurs](end-user-features.md).


### <a name="workspace-roles"></a>Rôles d’espace de travail
Voici les quatre rôles : administrateurs, membres, contributeurs et lecteurs. Toutes ces fonctionnalités, à l’exception de l’affichage et de l’interaction, nécessitent une licence Power BI Pro.

|Fonctionnalité   | Administrateur  | Membre  | Contributeur  | Visionneuse |
|---|---|---|---|---|
| Mettre à jour et supprimer l’espace de travail.  | X  |   |   |   | 
| Ajouter/supprimer des personnes, y compris d’autres administrateurs.  | X  |   |   |   |
| Ajouter des membres ou d’autres rôles avec des autorisations inférieures.  |  X | X  |   |   |
| Publier et mettre à jour une application. |  X | X  |   |   |
| Partager un élément ou une application.<sup>1</sup> |  X | X  |   |   |
| Permettre à d’autres utilisateurs de repartager des éléments.<sup>1</sup> |  X | X  |   |   |
| Proposer des applications sur la page d’accueil de collègues |  X | X  |   |   |
| Proposer des tableaux de bord et des rapports sur la page d’accueil de collègues |  X | X  | X |   |
| Créer, modifier et supprimer du contenu dans l’espace de travail.  |  X | X  | X  |   |
| Publier des rapports sur l’espace de travail, supprimer du contenu.  |  X | X  | X  |   |
| Créer un rapport dans un autre espace de travail à partir d’un jeu de données de cet espace de travail.<sup>1</sup> |  X | X  | X  |   |
| Copier un rapport. | X | X | X |  |
| Voir et utiliser un élément.<sup>2</sup> |  X | X  | X  | X  |
| Lire les données stockées dans les flux de données des espaces de travail | X | X | X | X |

1. Les contributeurs et les membres peuvent partager des éléments dans un espace de travail s’ils ont les autorisations Repartager.

2. Même si vous n’avez pas de licence Power BI Pro, vous pouvez visualiser et interagir avec des éléments dans service Power BI s’ils se trouvent dans un espace de travail d’une capacité Premium.

## <a name="licensing-workspaces-and-capacity"></a>Licences, espaces de travail et capacité
La gestion des licences joue également un rôle concernant ce que vous pouvez et ne pouvez pas faire dans un espace de travail. De nombreuses fonctionnalités nécessitent que l’utilisateur dispose d’une licence Power BI *Pro*. La plupart des *consommateurs* travaillent avec une licence *gratuite*. 

Si vous disposez d’une licence gratuite et que l’espace de travail est stocké dans une *capacité Premium*, vous pouvez visualiser et interagir avec le contenu de cet espace de travail. Une icône de diamant identifie les espaces de travail et les applications qui sont stockés dans une capacité Premium.

![Espaces de travail sélectionnés](media/end-user-workspaces/power-bi-diamond.png) Pour plus d’informations, consultez [De quelle licence est-ce que je dispose ?](end-user-license.md)



## <a name="next-steps"></a>Étapes suivantes
* [Applications dans Power BI](end-user-apps.md)    

* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

