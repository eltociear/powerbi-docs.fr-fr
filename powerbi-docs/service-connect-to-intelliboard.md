---
title: "Se connecter à IntelliBoard avec Power BI"
description: IntelliBoard pour Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: f668a1c9bfefb1b0b0c7c15f9d68c82312d38105
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Se connecter à IntelliBoard avec Power BI
IntelliBoard offre un accès simplifié à vos données du système de gestion d’apprentissage Moodle par le biais de services de reporting. Le pack de contenu IntelliBoard pour Power BI propose des analyses supplémentaires, y compris des indicateurs sur les cours, les utilisateurs inscrits, les performances globales et votre activité LMS.

Connectez-vous au [pack de contenu IntelliBoard](https://app.powerbi.com/getdata/services/intelliboard) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Sélectionnez **IntelliBoard**, puis **Obtenir**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Sélectionnez **OAuth 2**, puis **Se connecter**. Quand vous y êtes invité, indiquez vos informations d’identification IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Après connexion, un tableau de bord, un rapport et un ensemble de données sont chargés automatiquement. Les vignettes sont ensuite mises à jour avec des données de votre compte IntelliBoard.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](service-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu inclut les tables suivantes :  

    - Activity  
    - Agents  
    - Auth  
    - Countries  
    - CoursesProgress  
    - Enrollments
    - Lang  
    - Platform  
    - Totals  
    - UsersProgress    

## <a name="system-requirements"></a>Configuration requise
Un compte IntelliBoard avec des autorisations sur les tables ci-dessus est nécessaire afin d'instancier ce pack de contenu.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Power BI – Concepts de base](service-basic-concepts.md)

