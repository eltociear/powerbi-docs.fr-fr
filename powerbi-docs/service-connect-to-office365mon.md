---
title: Se connecter à Office365Mon avec Power BI
description: Office365Mon pour Power BI
author: teddybercovitz
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 8/29/2019
ms.author: tebercov
LocalizationGroup: Connect to services
ms.openlocfilehash: 5d31eccd52164bb4d1ff37532d89dc7e147693d3
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060832"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Se connecter à Office365Mon avec Power BI
Grâce à Power BI et à l’application modèle Office365Mon, vous pouvez facilement analyser les pannes d’Office 365 et les données de performances d’intégrité. Power BI récupère vos données, notamment celles des pannes et des sondes d’intégrité, puis établit un tableau de bord prêt à l’emploi et des rapports basés sur ces données.

Connectez-vous à l’[application modèle Office365Mon](https://app.powerbi.com/groups/me/getdata/services/office365mon) pour Power BI.

>[!NOTE]
>Vous devez disposer d’un compte d’administrateur Office365Mon pour vous connecter à l’application modèle Power BI et la charger.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Sélectionnez **Office365Mon** \> **Obtenir**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Pour la méthode d’authentification, sélectionnez **oAuth2** \> **Se connecter**.
   
   Quand vous y êtes invité, entrez vos informations d’identification d’administrateur Office365Mon et suivez le processus d’authentification.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Une fois les données importées dans Power BI, vous verrez un nouveau tableau de bord, un nouveau rapport et un nouveau jeu de données dans le volet de navigation gauche. Les nouveaux éléments sont signalés par un astérisque jaune (\*). Sélectionnez l’entrée Office365Mon.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="troubleshooting"></a>Résolution des problèmes
Si vous obtenez une erreur **« Échec de l’ouverture de session »** après avoir utilisé vos informations d’identification Office365Mon pour vous connecter, cela signifie que le compte que vous utilisez ne dispose pas des autorisations requises pour récupérer les données Office365Mon à partir de votre compte. Vérifiez qu’il s’agit d’un compte d’administrateur et réessayez.

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI ?](fundamentals/power-bi-overview.md)

[Obtenir des données pour Power BI](service-get-data.md)

