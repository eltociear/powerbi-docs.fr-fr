---
title: "Se connecter à Salesforce avec Power BI"
description: Salesforce pour Power BI
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
ms.openlocfilehash: 6998f273a7e40cae2c7a50f043f79eec540b4789
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-salesforce-with-power-bi"></a>Se connecter à Salesforce avec Power BI
Avec Power BI, vous pouvez facilement vous connecter à votre compte Salesforce.com. Créez cette connexion pour récupérer vos données et disposer automatiquement d’un tableau de bord et de rapports connexes basés sur vos données.

Connectez-vous au [pack de contenu Salesforce](https://app.powerbi.com/getdata/services/salesforce) pour Power BI ou consultez des informations supplémentaires sur l’[intégration de Salesforce](https://powerbi.microsoft.com/integrations/salesforce) à Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Cliquez sur **Salesforce**, puis sélectionnez **Obtenir**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Sélectionnez **Connexion** pour lancer le processus de connexion.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. Quand vous y êtes invité, entrez vos informations d’identification Salesforce. Cliquez sur **Autoriser** pour que Power BI ait accès à vos informations et données Salesforce de base.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Configurez ce que vous souhaitez importer dans Power BI à l’aide de l’option de liste déroulante :
   
   * **Tableau de bord**
     
     Sélectionnez un tableau de bord prédéfini basé sur un rôle (tel que **Responsable des ventes**). Ces tableaux de bord récupèrent un ensemble spécifique de données standard de Salesforce et n’incluent pas de champs personnalisés.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Rapports**
     
     Sélectionnez un ou plusieurs rapports personnalisés à partir de votre compte Salesforce. Ces rapports correspondent à vos vues dans Salesforce et peuvent inclure des données de champs personnalisés ou d’objets.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Si vous ne voyez aucun rapport, ajoutez-en ou créez-en dans votre compte Salesforce, puis reconnectez-vous.
7. Cliquez sur **Se connecter** pour commencer le processus d’importation. Pendant l’importation, une notification vous indique que l’importation est en cours. Une fois l’importation terminée, un tableau de bord, un rapport et un jeu de données pour vos données Salesforce sont répertoriés dans le volet de navigation de gauche.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Vous pouvez modifier ce tableau de bord pour afficher vos données comme vous le souhaitez. Vous pouvez poser des questions dans la zone Q&R, ou bien cliquer sur une vignette pour [ouvrir le rapport sous-jacent](service-dashboard-tiles.md) et [modifier les vignettes](service-dashboard-edit-tile.md) du tableau de bord.

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](service-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
* Être connecté avec un compte Salesforce de production qui autorise l’accès des API.
* Autorisation accordée à l’application Power BI pendant la connexion.
* Compte disposant de suffisamment d’appels d’API pour extraire et actualiser les données.
* Un jeton d’authentification valide est nécessaire pour l’actualisation. Salesforce imposant une limite de 5 jetons d’authentification par application, vérifiez qu’au maximum 5 jeux de données Salesforce sont importés.

## <a name="troubleshooting"></a>Résolution des problèmes
Si vous rencontrez des erreurs, reportez-vous à la configuration requise ci-dessus. Notez également que la connexion à un domaine personnalisé ou sandbox n’est pas prise en charge pour l’instant.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données](service-get-data.md)

