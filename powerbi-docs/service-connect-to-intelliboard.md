---
title: Se connecter à IntelliBoard avec Power BI
description: IntelliBoard pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 06fc561d3fbe07cbf553be63c7b19de3ab11992e
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060961"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Se connecter à IntelliBoard avec Power BI
IntelliBoard offre un accès simplifié à vos données du système de gestion d’apprentissage Moodle par le biais de Reporting Services. Le pack de contenu IntelliBoard pour Power BI propose des analyses supplémentaires, y compris des indicateurs sur les cours, les utilisateurs inscrits, les performances globales et votre activité LMS.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

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

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
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
[Qu’est-ce que Power BI ?](fundamentals/power-bi-overview.md)

[Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)

