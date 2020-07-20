---
title: Se connecter à Recherche Azure avec Power BI
description: Recherche Azure pour Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 11389b5986d0dd627b0077808a74db5ab2769a65
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216306"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Se connecter à Recherche Azure avec Power BI
Azure Search Traffic Analytics vous permet de surveiller et de comprendre le trafic vers votre service Recherche Azure. Le pack de contenu Recherche Azure pour Power BI fournit des informations détaillées sur vos données de recherche, notamment les recherches, indexations, statistiques du service et latences des 30 derniers jours. Pour plus de détails, consultez ce [billet de blog Azure](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

Connectez-vous au [pack de contenu Recherche Azure](https://app.powerbi.com/getdata/services/azure-search) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation.
   
   ![Capture d’écran d’Obtenir des données dans Power BI Desktop, montrant le bouton dans le volet du navigateur.](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![Capture d’écran de la boîte de dialogue Services, montrant le bouton Obtenir.](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Sélectionnez **Azure Search** \> **Obtenir**.
   
   ![Capture d’écran de la boîte de dialogue Services Azure, montrant le lien Obtenir.](media/service-connect-to-azure-search/azuresearch.png)
4. Indiquez le nom du compte Stockage Table sous lequel votre analyse Recherche Azure est stockée.
   
   ![Capture d’écran de la boîte de dialogue de connexion de Recherche Azure, montrant le champ du nom du compte de stockage Azure.](media/service-connect-to-azure-search/params.png)
5. Sélectionnez **Clé** comme mécanisme d’authentification et fournissez la clé de votre compte de stockage. Cliquez sur **Connexion** et commencez le processus de chargement.
   
   ![Capture d’écran de la boîte de dialogue de connexion de Recherche Azure, montrant l’option Clé entrée dans le champ Méthode d’authentification.](media/service-connect-to-azure-search/creds.png)
6. Une fois le chargement terminé, un nouveau tableau de bord, un nouveau rapport et un nouveau modèle apparaissent dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
    ![Capture d’écran du volet de navigation, montrant le tableau de bord, le rapport et le modèle.](media/service-connect-to-azure-search/dashboard2.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](../consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](../create-reports/service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](../consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="system-requirements"></a>Configuration requise
Le pack de contenu Recherche Azure exige l’activation d’Azure Search Traffic Analytics sur le compte.

## <a name="troubleshooting"></a>Résolution des problèmes
Vérifiez que le nom du compte de stockage et la clé d’accès complète sont correctement entrés. Le nom du compte de stockage doit correspondre au compte configuré avec Azure Search Traffic Analytics.

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI ?](../fundamentals/power-bi-overview.md)

[Concepts de base pour les concepteurs du service Power BI](../fundamentals/service-basic-concepts.md)
