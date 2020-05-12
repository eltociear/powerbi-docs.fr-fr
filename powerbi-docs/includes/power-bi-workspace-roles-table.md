---
title: Rôles d’espace de travail Power BI
description: Tableau des rôles d’espace de travail Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781344"
---
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
| Copier un rapport.<sup>2</sup> | X | X | X |  |
| Planifier l’actualisation des données via la passerelle locale.<sup>3</sup> | X | X | X |  |
| Modifier les paramètres de connexion à la passerelle.<sup>3</sup> | X | X | X |  |
| Voir et utiliser un élément.<sup>4</sup> |  X | X  | X  | X  |
| Lire les données stockées dans les flux de données des espaces de travail | X | X | X | X |

1. Les contributeurs et les lecteurs peuvent partager des éléments dans un espace de travail s’ils ont des autorisations de repartage.
2. Pour copier un rapport et pour créer un rapport dans un autre espace de travail à partir d’un jeu de données de cet espace de travail, vous avez besoin de l’autorisation Créer pour le jeu de données. Pour les jeux de données de cet espace de travail, les utilisateurs ayant un rôle Administrateur, Membre ou Contributeur disposent de l’autorisation Créer via leur rôle d’espace de travail.
3. N’oubliez pas que vous avez également besoin d’autorisations sur la passerelle. Ces autorisations sont gérées ailleurs, indépendamment des rôles et des autorisations de l’espace de travail. Consultez [Gérer une passerelle locale](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) pour plus d’informations.
4. Même si vous n’avez pas de licence Power BI Pro, vous pouvez voir et utiliser les éléments du service Power BI s’ils se trouvent dans un espace de travail d’une capacité Premium.

