---
title: Créer un lien vers un emplacement spécifique dans les applications mobiles Power BI
description: Apprenez à créer un lien ciblé qui pointe vers un rapport, une vignette ou un tableau de bord spécifique dans l’application mobile Power BI à l’aide d’un URI (Uniform Resource Identifier).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: maggies
ms.openlocfilehash: 1f9503980ba19b290fa5d0fd1f521bb85ef93759
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983574"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Créer un lien vers un emplacement spécifique dans les applications mobiles Power BI
Vous pouvez créer et utiliser un URI pour créer un lien vers un emplacement spécifique (*lien ciblé*) dans les applications mobiles Power BI sur toutes les plateformes mobiles : iOS, Android et Windows 10.

Les liens d’URI peuvent pointer directement vers des tableaux de bord, des vignettes et des rapports.

La destination du lien ciblé détermine le format de l’URI. Pour créer des liens ciblés vers différents emplacements, suivez les étapes ci-après. 

## <a name="open-the-power-bi-mobile-app"></a>Ouvrir l’application mobile Power BI
Pour ouvrir l’application mobile Power BI sur un appareil, utilisez l’URI suivant :

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>Ouvrir un tableau de bord spécifique
Cet URI ouvre l’application mobile Power BI sur un tableau de bord spécifique :

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

Pour rechercher l’ID d’objet de tableau de bord contenant 36 caractères, accédez au tableau de bord spécifique dans le service Power BI (https://powerbi.com)). Par exemple, consultez la section en surbrillance de cette URL :

`https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**`

Si le tableau de bord est dans un groupe autre que Mon espace de travail, ajoutez `&GroupObjectId=<36-character-group-id>` avant ou après l’ID de tableau de bord. Par exemple : 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Notez l’esperluette (&) entre les deux.

## <a name="open-to-a-specific-tile-in-focus"></a>Ouvrir une vignette spécifique en mode focus
Cet URI ouvre une vignette spécifique en mode focus dans l’application mobile Power BI :

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

Pour rechercher les ID d’objet de vignette et de tableau de bord contenant 36 caractères, accédez au tableau de bord spécifique dans le service Power BI (https://powerbi.com)) et ouvrez la vignette en mode focus. Par exemple, consultez les sections en surbrillance de cette URL :

`https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus`

Pour cette vignette, l’URI est le suivant :

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

Notez l’esperluette (&) entre les deux.

Si le tableau de bord est dans un groupe autre que Mon espace de travail, ajoutez `&GroupObjectId=<36-character-group-id>`.

## <a name="open-to-a-specific-report"></a>Ouvrir un rapport spécifique
Cet URI ouvre un rapport spécifique dans l’application mobile Power BI :

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

Pour rechercher l’ID d’objet de rapport contenant 36 caractères, accédez au rapport spécifique dans le service Power BI (https://powerbi.com)). Par exemple, consultez la section en surbrillance de cette URL :

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300`

Si le rapport est dans un groupe autre que Mon espace de travail, ajoutez `&GroupObjectId=<36-character-group-id>` avant ou après l’ID de rapport. Par exemple : 

mspbi://app/OpenReport?ReportObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Notez l’esperluette (&) entre les deux.

## <a name="open-to-a-specific-report-page"></a>Ouvrir une page de rapport spécifique
Cet URI ouvre une page de rapport spécifique dans l’application mobile Power BI :

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

La page de rapport porte le nom « ReportSection » suivi d’un nombre. Là encore, ouvrez le rapport dans le service Power BI (https://powerbi.com)) et accédez à la page de rapport spécifique. 

Par exemple, consultez la section en surbrillance de cette URL :

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/ReportSection11`

## <a name="open-in-full-screen-mode"></a>Ouvrir en mode plein écran
Ajoutez le paramètre en gras pour ouvrir un rapport spécifique en mode plein écran :

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

Par exemple : 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>Ajouter un contexte (facultatif)
Vous pouvez également ajouter le contexte dans la chaîne. Par la suite, si vous avez besoin de nous contacter, nous pouvons utiliser ce contexte pour filtrer nos données dans votre application. Ajouter `&context=<app-name>` au lien

Par exemple, consultez la section en surbrillance de cette URL : 

`https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/&context=SlackDeepLink`

## <a name="next-steps"></a>Étapes suivantes
Vos commentaires nous aident à développer les futurs processus d’implémentation. N’oubliez pas de voter pour les fonctionnalités que vous aimeriez voir dans les applications mobiles Power BI. 

* [Applications Power BI pour appareils mobiles](mobile-apps-for-mobile-devices.md)
* Suivez @MSPowerBI sur Twitter
* Rejoindre la conversation de la [Communauté Power BI](http://community.powerbi.com/)
* [Qu’est-ce que Power BI ?](../../power-bi-overview.md)

