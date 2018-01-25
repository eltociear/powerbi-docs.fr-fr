---
title: "Se connecter à Project Online avec Power BI"
description: Project Online pour Power BI
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
ms.openlocfilehash: 778453840e5ab311f635fd20228186ac3f3fc39c
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-project-online-with-power-bi"></a>Se connecter à Project Online avec Power BI
Microsoft Project Online est une solution en ligne flexible pour la gestion de portefeuille de projets (PPM) et les tâches quotidiennes. Project Online permet aux organisations de prendre en main et de hiérarchiser les investissements de portefeuille de projet, ainsi que de produire la valeur commerciale souhaitée. Le pack de contenu Project Online pour Power BI vous permet d’explorer les données de votre projet avec des métriques prêtes à l’emploi, telles que la conformité du statut du portefeuille et des projets.

Connectez-vous au [pack de contenu Project Online](https://app.powerbi.com/getdata/services/project-online) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
    ![](media/service-connect-to-project-online/getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-project-online/services.png)
3. Sélectionnez **Microsoft Project Online** \> **Obtenir**.
   
   ![](media/service-connect-to-project-online/mproject.png)
4. Dans la zone de texte **URL Project Web App** , entrez l’URL du projet Web App (PWA) auquel vous souhaitez vous connecter, puis appuyez sur **Suivant**. Notez que cela peut différer de l’exemple si vous avez un domaine personnalisé.
   
    ![](media/service-connect-to-project-online/params.png)
5. Pour la méthode d’authentification, sélectionnez **oAuth2** \> **Se connecter**. Quand vous y êtes invité, entrez vos informations d’identification Project Online et suivez le processus d’authentification.
   
    ![](media/service-connect-to-project-online/creds.png)
6. Une notification indiquant que vos données sont en cours de chargement s’affiche. Selon la taille de votre compte, cela peut prendre un certain temps. Une fois les données importées dans Power BI, vous verrez un nouveau tableau de bord, un nouveau rapport et un nouveau jeu de données dans le volet de navigation gauche. Il s’agit du tableau de bord par défaut créé par Power BI pour afficher vos données. Vous pouvez modifier ce tableau de bord pour afficher vos données comme vous le souhaitez.
   
   ![](media/service-connect-to-project-online/dashboard2.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

