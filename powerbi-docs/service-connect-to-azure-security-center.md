---
title: "Se connecter à Azure Security Center avec Power BI"
description: Azure Security Center pour Power BI
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
ms.openlocfilehash: e26a26d7cba2ae3d68586a2e0dcdf87481009bd6
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="connect-to-azure-security-center-with-power-bi"></a>Se connecter à Azure Security Center avec Power BI
Obtenez des informations sur la sécurité de votre charge de travail Azure en connectant vos données de sécurité Azure à Power BI. En plus de pouvoir analyser et explorer les données grâce aux données du Centre de sécurité Azure, Power BI permet de créer automatiquement un tableau de bord et un rapport.

Connectez-vous au [pack de contenu Azure Security Center](https://app.powerbi.com/getdata/services/azure-security-center) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-azure-security-center/getdata.png)
2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-azure-security-center/services.png)
3. Sélectionnez **Azure Security Center** \> **Obtenir**.
   
   ![](media/service-connect-to-azure-security-center/asc.png)
4. Indiquez votre ID d’abonnement. Voir les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
   ![](media/service-connect-to-azure-security-center/params.png)
5. Pour la **Méthode d’authentification**, sélectionnez **oAuth2** \> **Se connecter**. Quand vous y êtes invité, entrez vos informations d’identification Azure.
   
    ![](media/service-connect-to-azure-security-center/creds.png)
6. Après l’approbation, le processus d’importation démarre automatiquement. Une fois terminé, de nouveaux tableau de bord, rapport et modèle apparaîtront dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
     ![](media/service-connect-to-azure-security-center/dashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu comporte des informations concernant les statistiques de sécurité des ressources, les analyses des alertes et les analyses de prévention.

## <a name="system-requirements"></a>Configuration requise
Ce pack de contenu requiert l’accès à un ID d’abonnement et le centre de sécurité Azure doit être activé. Pour plus d’informations, consultez [Azure Security Center](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityDashboardStartBladeV2) dans le portail Azure.

Le pack de contenu requiert également que l’utilisateur se connecte avec un compte professionnel (et non un compte personnel).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Il existe deux moyens faciles de trouver votre ID d’abonnement.

1. Sur https://portal.azure.com -&gt; Parcourir -&gt; Abonnements -&gt; ID d’abonnement
2. Sur https://manage.windowsazure.com -&gt; Paramètres -&gt; ID d’abonnement

Votre ID d’abonnement est une longue série de chiffres et de caractères, semblable à l’exemple à l’étape\#4 ci-dessus. 

## <a name="troubleshooting"></a>Résolution des problèmes
Les données peuvent prendre un certain temps à charger, selon la taille de votre compte. Si vous rencontrez une erreur lors de la connexion, vérifiez dans les paramètres que le Centre de sécurité Azure est bien activé.

Si le pack de contenu charge mais n’affiche pas toutes les données, confirmez que vous vous connectez avec un compte professionnel. Bien que les comptes personnels soient pris en charge par Azure Security Center, l’API (et par conséquent le pack de contenu) ne renvoie pas les valeurs attendues si l’utilisateur se connecte avec un compte non professionnel. Indiquez un compte professionnel et recommencez l’opération.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

