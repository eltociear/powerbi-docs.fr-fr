---
title: "Se connecter à Visual Studio Team Services avec Power BI"
description: Visual Studio Team Services pour Power BI
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
ms.openlocfilehash: 20ea9117cf1eee3d7b05be21e5964226349a58c1
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-visual-studio-team-services-with-power-bi"></a>Se connecter à Visual Studio Team Services avec Power BI
Utilisez le pack de contenu Visual Studio Team Services pour Power BI afin d’acquérir une compréhension de vos projets d’équipe Git et TFVC. Une fois la connexion établie, vos données vous parviennent automatiquement dans un tableau de bord et dans des rapports. 

Connectez-vous au [pack de contenu Visual Studio Team Services](https://app.powerbi.com/getdata/services/visual-studio-online) ou consultez des informations supplémentaires sur l’[intégration de Visual Studio Team Services](https://powerbi.microsoft.com/integrations/visual_studio_online) avec Power BI.

>[!NOTE]
>Ce pack de contenu nécessite l’accès à un compte pour lequel l’authentification OAuth est activée. Vous trouverez plus d’informations sur la configuration requise ci-dessous.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.  
   ![](media/service-connect-to-visual-studio/pbi_getdata.png) 
2. Dans la zone **Services**, sélectionnez **Obtenir**.  
   ![](media/service-connect-to-visual-studio/pbi_getservices.png) 
3. Sélectionnez le pack de contenu **Visual Studio Team Services**, puis cliquez sur **Obtenir**.     
   ![](media/service-connect-to-visual-studio/vsts.png)
4. Entrez les informations relatives à votre compte Visual Studio Team Services. Consultez les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
   ![](media/service-connect-to-visual-studio/pbi_vsosignin.png)
   
   Le nom de votre compte se trouve au début de votre URL visualstudio.com :    
   ![](media/service-connect-to-visual-studio/urlimage.png)
   
   Le nom de votre projet est celui que vous voyez en haut de chaque page dans Visual Studio Team Services :  
   ![](media/service-connect-to-visual-studio/projectimage.png)
5. Authentifiez-vous auprès de Visual Studio Team Services à l’aide de l’authentification oAuth2. Une boîte de dialogue de connexion à Visual Studio Team Services peut alors s’afficher. 
   
   > [!IMPORTANT]
   > Certains déploiements de Visual Studio Team Services ne prennent pas en charge l’authentification oAuth2.  Si la connexion échoue, suivez les instructions de la section Résolution des problèmes.
   > 
   > 
   
   ![](media/service-connect-to-visual-studio/pbi_vsosignin2.png)
6. Suivez les écrans d’authentification de Visual Studio Team Services pour accorder au pack de contenu Visual Studio pour Power BI l’autorisation d’accéder aux données de votre projet d’équipe.   
   ![](media/service-connect-to-visual-studio/vsoauthorizeapp450.png)
7. Une fois que vous êtes connecté à votre projet Visual Studio Team Services, vous voyez un nouveau tableau de bord, un nouveau rapport et un nouveau jeu de données dans le volet de navigation gauche. Les nouveaux éléments sont signalés par un astérisque jaune \*.  
   ![](media/service-connect-to-visual-studio/visualstudioonline800px.png) 

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](service-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Visual Studio Team Services dans Power BI fournit une grande variété de tables et de champs pour vos rapports. La liste complète des éléments inclus dans le pack de contenu se trouve ici : <https://www.visualstudio.com/get-started/report/vso-pbi-whats-available-vs>

## <a name="system-requirements"></a>Configuration requise
* Un accès au compte Visual Studio Team Services avec autorisation de collecter les données à l’aide de l’API REST.  
* L’autorisation accordée à l’application « Power BI » lors de la connexion initiale. Pour déconnecter Power BI et supprimer son autorisation d’accéder à votre compte Visual Studio Team Services, vous pouvez révoquer l’accès dans Visual Studio Team Services. Consultez <https://www.visualstudio.com/get-started/setup/change-application-access-policies-vs>.  

Vous trouverez plus de détails à l’adresse <https://www.visualstudio.com/en-us/get-started/report/connect-vso-pbi-vs>.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Le nom de votre compte se trouve au début de votre URL visualstudio.com :    
    ![](media/service-connect-to-visual-studio/urlimage.png)

Le nom de votre projet correspond à celui qui apparaît en haut de chaque page dans Visual Studio Team Services :  
    ![](media/service-connect-to-visual-studio/projectimage.png)

Vous pouvez aussi utiliser des caractères génériques pour sélectionner plusieurs projets. Par exemple, vous pouvez sélectionner tous les projets en entrant simplement « \* », ou bien tous les projets qui commencent par « Azure » en entrant « Azure\* ».

## <a name="troubleshooting"></a>Résolution des problèmes
Quand vous tentez de vous connecter à Visual Studio Team Services, il peut arriver que vous receviez un message vous indiquant que la connexion a échoué.

L’échec d’authentification a deux raisons principales :

1) Vous vous êtes connecté avec un compte personnel, au lieu d’un compte d’entreprise ou d’établissement scolaire  

2) Votre déploiement de Visual Studio Team Services ne prend pas en charge l’authentification oAuth 

**Connexion à l’aide d’un compte professionnel ou scolaire**  
Si vous rencontrez ce problème, cela peut signifier que vous êtes déjà authentifié dans Visual Studio Team Services sous un compte différent de celui depuis lequel vous essayez de charger des données (par exemple, si vous vous êtes connecté à Visual Studio Team Services avec un compte Microsoft personnel, puis à Power BI avec un compte d’entreprise ou d’établissement scolaire).

Pour résoudre ce problème :  

* Quittez la boîte de dialogue de configuration  
* Déconnectez-vous de votre compte personnel dans Visual Studio Team Services  
* Connectez-vous à Visual Studio Online à l’aide de votre compte d’entreprise ou d’établissement scolaire  
* Redémarrez le processus d’obtention des données ci-dessus 

Connexion à l’aide d’un compte d’entreprise ou d’établissement scolaire (Azure Active Directory/AAD) :  
    ![](media/service-connect-to-visual-studio/vsologinscreen.png)

Si cette boîte de dialogue s’affiche, et si vous voulez vous connecter avec votre compte d’entreprise ou d’établissement scolaire (Azure Active Directory), cliquez sur le lien situé sur la gauche pour vous connecter avec ce compte. N’entrez pas vos informations d’identification Azure Active Directory dans le champ de droite, car celui-ci requiert un compte Microsoft (votre compte personnel).

**Déploiements de Visual Studio Team Services qui ne prennent pas en charge l’authentification oAuth2**  
Votre administrateur Visual Studio Team Services a peut-être désactivé l’authentification oAuth pour votre déploiement de Visual Studio Team Services.  Si c’est le cas, vous ne pourrez pas utiliser le pack de contenu Visual Studio pour Power BI. 

![](media/service-connect-to-visual-studio/oauth.png)

## <a name="next-steps"></a>Étapes suivantes
* [Prise en main de Power BI](service-get-started.md)
* [Obtenir des données](service-get-data.md)

