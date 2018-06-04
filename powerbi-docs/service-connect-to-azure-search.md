---
title: Se connecter à Recherche Azure avec Power BI
description: Recherche Azure pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 1d67b100620d4517e657f92acb37e370f2bb540e
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34480954"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Se connecter à Recherche Azure avec Power BI
Azure Search Traffic Analytics vous permet de surveiller et de comprendre le trafic vers votre service Recherche Azure. Le pack de contenu Recherche Azure pour Power BI fournit des informations détaillées sur vos données de recherche, notamment les recherches, indexations, statistiques du service et latences des 30 derniers jours. Pour plus de détails, consultez ce [billet de blog Azure](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

Connectez-vous au [pack de contenu Recherche Azure](https://app.powerbi.com/getdata/services/azure-search) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Dans la zone **Services** , sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Sélectionnez **Recherche Azure**\>**Obtenir**.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Indiquez le nom du compte Stockage Table sous lequel votre analyse Recherche Azure est stockée.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Sélectionnez **Clé** comme mécanisme d’authentification et fournissez la clé de votre compte de stockage. Cliquez sur **Connexion** et commencez le processus de chargement.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Une fois le chargement terminé, un nouveau tableau de bord, un nouveau rapport et un nouveau modèle apparaissent dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](power-bi-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](service-dashboard-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
Le pack de contenu Recherche Azure exige l’activation d’Azure Search Traffic Analytics sur le compte.

## <a name="troubleshooting"></a>Résolution des problèmes
Vérifiez que le nom du compte de stockage et la clé d’accès complète sont correctement entrés. Le nom du compte de stockage doit correspondre au compte configuré avec Azure Search Traffic Analytics.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Power BI – Concepts de base](service-basic-concepts.md)

