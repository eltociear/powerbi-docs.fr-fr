---
title: Gérer le stockage de données dans vos espaces de travail
description: Découvrez comment gérer le stockage de données dans votre espace de travail pour être sûr de pouvoir continuer à publier des rapports et des jeux de données.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: f8e7240b34e20a3d18443cadb5265c5d0d870790
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73873660"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gérer le stockage de données dans les espaces de travail Power BI

Découvrez comment gérer le stockage de données dans votre espace de travail pour être sûr de pouvoir continuer à publier des rapports et des jeux de données.

Les utilisateurs et les espaces de travail ont leurs propres capacités de données :

* Tous les utilisateurs disposent d’un espace de stockage de données maximal de 10 Go.
* Les utilisateurs disposant d’une licence Power BI Pro peuvent créer des espaces de travail avec pour chacun une capacité de stockage de données maximale de 10 Go.
* Les espaces de travail inclus dans une fonctionnalité Premium ne sont pas comptabilisés dans l’espace de stockage d’un utilisateur Power BI Pro.

Au niveau du locataire, l’utilisation totale ne peut pas dépasser 10 Go par utilisateur Pro parmi tous les utilisateurs et espaces de travail Pro du locataire.

Découvrez plus en détail les autres fonctionnalités du [modèle de tarification de Power BI](https://powerbi.microsoft.com/pricing).

Vos propres jeux de données et rapports Excel, ainsi que ceux que d’autres personnes ont partagés avec vous, sont inclus dans votre espace de stockage des données. Les jeux de données correspondent à toutes les sources de données que vous avez chargées ou auxquelles vous vous êtes connecté. Ces sources de données incluent les fichiers Power BI Desktop et les classeurs Excel que vous utilisez. Les éléments suivants sont également inclus dans votre capacité de données.

* Plages Excel épinglées aux tableaux de bord.
* Visualisations locales Reporting Services épinglées à un tableau de bord Power BI.
* Images téléchargées.

La taille d’un tableau de bord que vous partagez varie en fonction de ce qui est épinglé dessus. Par exemple, si vous épinglez des éléments provenant de deux rapports qui font partie de deux jeux de données différents, la taille inclut ces deux jeux de données.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Gérer les éléments dont vous êtes propriétaire

Consultez l’espace de stockage des données que vous utilisez dans votre compte Power BI et gérez votre compte.

1. Pour gérer votre propre stockage, accédez à **Mon espace de travail** dans le volet de navigation.
   
    ![Mon espace de travail](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Sélectionnez l’icône représentant un engrenage ![Icône Engrenage](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) située en haut à droite \> **Gérer le stockage personnel**.
   
    La barre supérieure montre la part de votre limite de stockage que vous avez utilisée.
   
    ![Gérer la limite de stockage](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Les jeux de données et rapports sont répartis sous deux onglets :
   
    **Je suis propriétaire :** vous avez chargé ces rapports et jeux de données sur votre compte Power BI, y compris les jeux de données de services tels que Salesforce et Dynamics CRM.  
    **Les propriétaires sont des tiers :** ces rapports et ces jeux de données ont été partagés avec vous par d’autres personnes.
1. Pour supprimer un jeu de données ou un rapport, sélectionnez l’icône représentant une corbeille ![Corbeille](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

N’oubliez pas que vous-même ou une autre personne pouvez avoir des rapports et des tableaux de bord basés sur un jeu de données. Si vous supprimez le jeu de données, les rapports et les tableaux de bord ne fonctionneront plus.

## <a name="manage-your-workspace"></a>Gérer votre espace de travail
1. Sélectionnez la flèche à côté de **Espaces de travail** \>, puis sélectionnez le nom de l’espace de travail.
   
    ![Sélectionner un espace de travail](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Sélectionnez l’icône représentant un engrenage ![Icône Engrenage](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) située en haut à droite \> **Gérer le stockage de groupe**.
   
    La barre supérieure montre la part de la limite de stockage du groupe qui est utilisée.
   
    ![Gérer le stockage de l’espace de travail](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Les jeux de données et rapports sont répartis sous deux onglets :
   
    **Nous sommes propriétaires :** vous-même ou une autre personne avez chargé ces rapports et jeux de données sur le compte Power BI du groupe, y compris les jeux de données de services comme Salesforce ou Dynamics CRM.
    **Les propriétaires sont des tiers :** ces rapports et ces jeux de données ont été partagés avec votre groupe par d’autres personnes.
3. Pour supprimer un jeu de données ou un rapport, sélectionnez l’icône représentant une corbeille ![Corbeille](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Tous les membres dotés d’autorisations de modification pour un espace de travail sont autorisés à supprimer les jeux de données et les rapports qu’il contient.
   > 
   > 

N’oubliez pas que vous-même ou un autre membre du groupe pouvez avoir des rapports et des tableaux de bord basés sur un jeu de données. Si vous supprimez le jeu de données, les rapports et les tableaux de bord ne fonctionneront plus.

## <a name="dataset-limits"></a>Limites de jeu de données
Power BI limite chaque jeu de données importé à 1 Go. Si vous conservez l’expérience Excel au lieu d’importer les données, la limite s’élève à 250 Mo par jeu de données.

## <a name="what-happens-when-you-reach-a-limit"></a>Que se passe-t-il lorsque vous atteignez une limite ?
Lorsque vous atteignez la limite de capacité de données, le service vous en informe. 

L’icône représentant un engrenage ![icône d’engrenage](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)permet d’afficher une barre rouge indiquant que la limite de capacité de données est dépassée.

![Limite de stockage atteinte](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Cette limite est également indiquée dans **Gérer le stockage personnel**.

 ![Gérer le stockage personnel, limite de stockage atteinte](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Lorsque vous essayez d’effectuer une action qui vous fait atteindre l’une des limites, un message vous en informe. Vous pouvez [gérer](#manage) votre stockage afin de réduire votre volume de stockage ou obtenir la possibilité de dépasser la limite.

 ![Limite de stockage dépassée](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

