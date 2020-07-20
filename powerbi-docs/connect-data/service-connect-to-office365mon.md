---
title: Se connecter à Office365Mon avec Power BI
description: Office365Mon pour Power BI
author: paulinbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 422782c3036f94c1ea764f46135200116092d70c
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216227"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Se connecter à Office365Mon avec Power BI
Grâce à Power BI et à l’application modèle Office365Mon, vous pouvez facilement analyser les pannes d’Office 365 et les données de performances d’intégrité. Power BI récupère vos données, notamment celles des pannes et des sondes d’intégrité, puis établit un tableau de bord prêt à l’emploi et des rapports basés sur ces données.

Connectez-vous à l’[application modèle Office365Mon](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3) pour Power BI.

>[!NOTE]
>Vous devez disposer d’un compte d’administrateur Office365Mon pour vous connecter à l’application modèle Power BI et la charger.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation.
   
   ![Capture d’écran du bouton Obtenir des données, le montrant dans le volet de navigation.](media/service-connect-to-office365mon/pbi_getdata.png)
2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![Capture d’écran de la boîte de dialogue Services, montrant le bouton Obtenir.](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Sélectionnez **Office365Mon** \> **Obtenir**.
   
   ![Capture d’écran de la boîte de dialogue Office365Mon, montrant le lien Obtenir.](media/service-connect-to-office365mon/o365mon.png)
4. Comme méthode d’authentification, sélectionnez **oAuth2** \> **Se connecter**.
   
   Quand vous y êtes invité, entrez vos informations d’identification d’administrateur Office365Mon et suivez le processus d’authentification.
   
   ![Capture d’écran de la boîte de dialogue de connexion à Office365Mon, montrant l’option OAuth2 dans le champ Méthode d’authentification.](media/service-connect-to-office365mon/creds.png)
   
   ![Capture d’écran de la connexion à Office365Mon, montrant l’invite à entrer des informations d’identification.](media/service-connect-to-office365mon/creds2.png)
5. Une fois les données importées dans Power BI, vous voyez un nouveau tableau de bord, un nouveau rapport et un nouveau jeu de données dans le volet de navigation. Les nouveaux éléments sont signalés par un astérisque jaune (\*). Sélectionnez l’entrée Office365Mon.
   
   ![Capture d’écran du volet de navigation dans Power BI, montrant le tableau de bord, le rapport et le jeu de données.](media/service-connect-to-office365mon/dashboard4.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](../consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](../create-reports/service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](../consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="troubleshooting"></a>Résolution des problèmes
Si vous obtenez une erreur **« Échec de l’ouverture de session »** après avoir utilisé vos informations d’identification Office365Mon pour vous connecter, cela signifie que le compte que vous utilisez ne dispose pas des autorisations requises pour récupérer les données Office365Mon à partir de votre compte. Vérifiez qu’il s’agit d’un compte d’administrateur et réessayez.

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI ?](../fundamentals/power-bi-overview.md)

[Obtenir des données pour Power BI](service-get-data.md)
