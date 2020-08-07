---
title: Modifier les valeurs des paramètres dans le service Power BI
description: Les paramètres de requête sont créés dans Power BI Desktop, mais vous pouvez les passer en revue et les mettre à jour dans le service Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 3b64c1dd502fd16199fbff9f64cd2c017006d1f1
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768471"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Modifier les valeurs des paramètres dans le service Power BI
Les créateurs de rapports ajoutent des paramètres de requête aux rapports dans Power BI Desktop. Ces paramètres leur permettent de rendre certaines parties des rapports dépendantes d’une ou plusieurs *valeurs* de paramètre. Par exemple, un créateur de rapports peut créer un paramètre qui limite les données à un seul pays/une seule région ou un paramètre qui définit les formats acceptables pour les champs de dates, d’heure, de texte ou autres.

![Onglet Accueil avec l’option Gérer les paramètres dans Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Passer en revue et modifier les paramètres dans le service Power BI

En tant que créateur de rapports, vous définissez les paramètres dans Power BI Desktop. Quand vous [publiez ce rapport sur le service Power BI](../create-reports/desktop-upload-desktop-files.md), les valeurs et sélections de paramètres l’accompagnent. Vous pouvez examiner et modifier les paramètres dans le service Power BI, mais pas les créer.

1. Dans le service Power BI, sélectionnez l’icône en forme de rouage ![icône de rouage](media/service-parameters/power-bi-cog.png) pour ouvrir **Paramètres**.

2. Sélectionnez l’onglet pour **Jeux de données** et mettez en surbrillance un jeu de données dans la liste. 
    
    ![Fenêtre Paramètres avec l’onglet Jeux de données sélectionné](media/service-parameters/power-bi-select-dataset2.png)

3. Développez **Paramètres**.  Si le jeu de données sélectionné ne contient pas de paramètres, un message s’affiche avec le lien En savoir plus sur les paramètres de requête. Si le jeu de données contient des paramètres, développez le titre **Paramètres** pour afficher ces paramètres. 

    ![Fenêtre Paramètres avec Paramètres développé](media/service-parameters/power-bi-settings.png)

    Passez en revue les valeurs des paramètres et modifiez-les si nécessaire. Les champs grisés ne peuvent pas être modifiés. 


## <a name="next-steps"></a>Étapes suivantes
Pour ajouter des paramètres simples en cas de besoin, vous pouvez [modifier l’URL](../collaborate-share/service-url-filters.md).
