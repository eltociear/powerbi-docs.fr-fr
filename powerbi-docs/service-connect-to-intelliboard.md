---
title: Se connecter à IntelliBoard avec Power BI
description: IntelliBoard pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c397ec0f302ec558e0277c92a871a94dd7f28e87
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34241504"
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

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
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

