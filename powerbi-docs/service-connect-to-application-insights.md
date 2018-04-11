---
title: Se connecter à Application Insights Connect dans Power BI
description: Application Insights pour Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 04cc92bd33f342097b9952a744d8dfffced22bb3
ms.sourcegitcommit: d91b7bf18d5c504037134f375886633379f28ede
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2018
---
# <a name="connect-to-application-insights-with-power-bi"></a>Se connecter à Application Insights avec Power BI
Power BI permet de créer de puissants tableaux de bord personnalisés à partir de la télémétrie [Application Insight](https://azure.microsoft.com/documentation/articles/app-insights-overview/). Envisagez la télémétrie de votre application autrement. Combinez des mesures de plusieurs applications ou services de composants sur un tableau de bord unique. La première version du pack de contenu Power BI pour Application Insights inclut des widgets pour des mesures courantes relatives à l’utilisation, telles que les utilisateurs actifs, l’affichage de page, les sessions, la version du navigateur et du système d’exploitation, et la répartition géographique des utilisateurs sur une carte.

Connectez-vous au [pack de contenu Application Insights pour Power BI](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>L’accès au panneau Vue d’ensemble d’Application Insights pour votre application dans le portail Azure en version préliminaire est nécessaire pour se connecter. Vous trouverez plus d’informations sur la configuration requise ci-dessous.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
    ![Bouton Get Data](media/service-connect-to-application-insights/pbi_getdata.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
    ![Bouton Get Services](media/service-connect-to-application-insights/pbi_getservices.png)
3. Sélectionnez **Application Insights** > **Obtenir**.
   
    ![Pack de contenu Application Insights](media/service-connect-to-application-insights/appinsights.png)
4. Fournissez les détails de l’application à laquelle vous souhaitez vous connecter, à savoir le **nom de la ressource Application Insights**, le **groupe de ressources**et l’ **ID d’abonnement**. Pour plus de détails, consultez [Recherche de vos paramètres Application Insights](#FindingAppInsightsParams) ci-dessous.
   
    ![Boîte de dialogue de connexion à Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Sélectionnez **Se connecter** , puis suivez les instructions affichées pour vous connecter.
   
    ![Connexion à Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. Le processus d’importation commence automatiquement. Lorsque vous avez terminé, une notification s’affiche et de nouveaux tableau de bord, rapport et jeu de données apparaissent dans le volet de navigation, marqués d’un astérisque.  Sélectionnez le tableau de bord pour afficher vos données importées.
   
    ![Tableau de bord d’Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu Application Insights contient les tables et les métriques suivantes :  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Vos informations Nom de ressource, Groupe de ressources et ID d’abonnement sont toutes disponibles dans le portail Azure. La sélection du nom entraîne l’ouverture d’une vue détaillée, et vous pouvez utiliser la liste déroulante Bases pour rechercher toutes les valeurs dont vous avez besoin.

![Paramètres d’Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Copiez et collez celles-ci dans les champs correspondants de Power BI :

![Paramètres d’Application Insights](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

