---
title: Afficher et modifier les paramètres de jeu de données dans le service Power BI
description: Les paramètres de requête sont créés dans Power BI Desktop, mais vous pouvez les passer en revue et les mettre à jour dans le service Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965156"
---
# <a name="what-is-a-query-parameter"></a>Qu’est-ce qu’un paramètre de requête ?
Les paramètres de requête sont ajoutés dans Power BI Desktop par les créateurs de rapports. Ces paramètres leur permettent de rendre certaines parties des rapports dépendantes d’une ou plusieurs *valeurs* de paramètre. Par exemple, un créateur de rapports peut créer un paramètre qui limite les données à un seul pays/une seule région ou un paramètre qui définit les formats acceptables pour les champs de dates, d’heure, de texte ou autres.

![Onglet Accueil avec l’option Gérer les paramètres dans Desktop](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>Passer en revue et modifier les paramètres dans le service Power BI

Une fois que les paramètres sont définis dans Desktop et que ce [rapport est publié dans le service Power BI](desktop-upload-desktop-files.md), les valeurs des paramètres et les sélections sont transférées avec ce rapport. Certains paramètres peuvent être passés en revue et modifiés dans le service Power BI (pas les paramètres qui limitent les données disponibles, mais ceux qui définissent et décrivent les valeurs acceptables).

1. Dans le service Power BI, sélectionnez l’icône en forme de rouage ![icône de rouage](media/service-parameters/power-bi-cog.png) pour ouvrir **Paramètres**.

2. Sélectionnez l’onglet pour **Jeux de données** et mettez en surbrillance un jeu de données dans la liste. 
    
    ![Fenêtre Paramètres avec l’onglet Jeux de données sélectionné](media/service-parameters/power-bi-select-dataset2.png)

3. Développez **Paramètres**.  Si le jeu de données sélectionné ne contient pas de paramètres, un message s’affiche avec le lien En savoir plus sur les paramètres de requête. Mais si le jeu de données contient des paramètres, le fait de développer le titre **Paramètres** a pour effet d’afficher ces paramètres. 

    ![Fenêtre Paramètres avec Paramètres développé](media/service-parameters/power-bi-settings.png)

    Passez en revue les valeurs des paramètres et modifiez-les si nécessaire. Les champs grisés ne peuvent pas être modifiés. 


## <a name="next-steps"></a>Étapes suivantes
Pour ajouter des paramètres simples en cas de besoin, vous pouvez [modifier l’URL](service-url-filters.md).