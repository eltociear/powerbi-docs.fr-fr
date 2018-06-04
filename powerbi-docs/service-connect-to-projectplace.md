---
title: Se connecter à Projectplace avec Power BI
description: Projectplace pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 70dcc7beb4525c84f1d52c511fa6a9f2ba666f94
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34249180"
---
# <a name="connect-to-projectplace-by-planview-with-power-bi"></a>Se connecter à Projectplace by Planview avec Power BI
Le pack de contenu Projectplace by Planview vous permet de visualiser les données de votre projet collaboratif de manière entièrement nouvelle dans Power BI. Utilisez vos informations de connexion Projectplace pour afficher de façon interactive les statistiques clés du projet, découvrir qui sont les membres de votre équipe les plus productifs et actifs, et identifier des cartes et activités à risque dans des projets de votre compte Projectplace. Vous pouvez également étendre le tableau de bord et les rapports prêts à l’emploi pour obtenir les informations les plus importantes pour vous.

[Se connecter au pack de contenu Projectplace dans Power BI](https://app.powerbi.com/getdata/services/projectplace)

>[!NOTE]
>Pour importer vos données Projectplace dans Power BI, vous devez être un utilisateur de Projectplace. Consultez les conditions supplémentaires ci-dessous.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
    ![](media/service-connect-to-projectplace/get.png)
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
    ![](media/service-connect-to-projectplace/services.png)
3. Dans la page Power BI, sélectionnez **Projectplace by Planview**, puis sélectionnez **Obtenir** :  
   
    ![](media/service-connect-to-projectplace/projectplace.png)
4. Dans la zone de texte URL du flux OData, entrez l’URL du flux OData de Projectplace que vous souhaitez utiliser, comme illustré dans l’image suivante :
   
    ![](media/service-connect-to-projectplace/params.png)
5. Dans la liste Méthode d’authentification, sélectionnez **OAuth** si cette option n’est pas sélectionnée. Appuyez sur **Se connecter** , puis suivez le flux de connexion.  
   
   ![](media/service-connect-to-projectplace/creds.png)
6. Dans le volet gauche, sélectionnez **Projectplace** dans la liste des tableaux de bord. Power BI importe les données de Projectplace dans le tableau de bord. Notez que le chargement des données peut prendre un certain temps.  
   
    Le tableau de bord contient des vignettes qui affichent des données de votre base de données Projectplace. L’image suivante présente un exemple du tableau de bord Projectplace par défaut dans Power BI.
   
    ![](media/service-connect-to-projectplace/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
Pour importer vos données Projectplace dans Power BI, vous devez être un utilisateur de Projectplace. Cette procédure suppose que vous vous êtes déjà connecté à la page d’accueil Microsoft Power BI avec un compte Power BI. Si vous n’avez pas de compte Power BI, créez-en un gratuit dans la page d’accueil de Power BI, puis cliquez sur Obtenir des données.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Power BI – Concepts de base](service-basic-concepts.md)

