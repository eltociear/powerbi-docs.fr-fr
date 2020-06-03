---
title: Rôles d’espace de travail Power BI
description: Tableau des rôles d’espace de travail Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 05/26/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 708599eb3f39d4c627a11753cb964d6425f75640
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120417"
---
|Fonctionnalité   | Administrateur  | Membre  | Contributeur  | Visionneuse |
|---|---|---|---|---|
| Mettre à jour et supprimer l’espace de travail.  |  |   |   |   | 
| Ajouter/supprimer des personnes, y compris d’autres administrateurs.  |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Ajouter des membres ou d’autres rôles avec des autorisations inférieures.  |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publier et mettre à jour une application. |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Partager un élément ou une application.<sup>1</sup> |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Permettre à d’autres utilisateurs de repartager des éléments.<sup>1</sup> |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Proposer des applications sur la page d’accueil de collègues |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Proposer des tableaux de bord et des rapports sur la page d’accueil de collègues |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Créer, modifier et supprimer du contenu dans l’espace de travail.  |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publier des rapports sur l’espace de travail, supprimer du contenu.  |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Créer un rapport dans un autre espace de travail à partir d’un jeu de données de cet espace de travail.<sup>2</sup> |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Copier un rapport.<sup>2</sup> | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Planifier l’actualisation des données via la passerelle locale.<sup>3</sup> | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modifier les paramètres de connexion à la passerelle.<sup>3</sup> | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Voir et utiliser un élément.<sup>4</sup> |  ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Lire les données stockées dans les flux de données des espaces de travail | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Coche Oui](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Les contributeurs et les lecteurs peuvent aussi partager des éléments dans un espace de travail s’ils ont des autorisations de repartage.

<sup>2</sup> Pour copier un rapport et pour créer un rapport dans un autre espace de travail à partir d’un jeu de données de cet espace de travail, vous avez besoin de l’[autorisation Créer pour le jeu de données](../connect-data/service-datasets-build-permissions.md). Pour les jeux de données de cet espace de travail, les utilisateurs ayant un rôle Administrateur, Membre ou Contributeur disposent automatiquement de l’autorisation Créer via leur rôle d’espace de travail.

<sup>3</sup> N’oubliez pas que vous avez également besoin d’autorisations sur la passerelle. Ces autorisations sont gérées ailleurs, indépendamment des rôles et des autorisations de l’espace de travail. Consultez [Gérer une passerelle locale](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) pour plus d’informations.

<sup>4</sup> Même si vous n’avez pas de licence Power BI Pro, vous pouvez voir et utiliser les éléments du service Power BI s’ils se trouvent dans un espace de travail d’une capacité Premium.

