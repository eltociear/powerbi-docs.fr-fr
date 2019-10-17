---
title: Se connecter à Microsoft Azure Consumption Insights avec Power BI
description: Microsoft Azure Consumption Insights pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020442"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Se connecter à Microsoft Azure Consumption Insights avec Power BI
Explorez et analysez vos données de consommation de Microsoft Azure dans le service Power BI avec le pack de contenu de Power BI. Les données sont automatiquement actualisées une fois par jour.

Connectez-vous au [Pack de contenu d’informations sur la consommation de Microsoft Azure](https://app.powerbi.com/getdata/services/azureconsumption) pour le service Power BI.

> [!NOTE]
> Pour bénéficier d’une configuration personnalisée, utilisez le [connecteur Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) dans Power BI Desktop.

## <a name="how-to-connect"></a>Comment se connecter
1. Dans le service Power BI, sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
    ![Obtenir les données](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![Get Services](media/service-connect-to-azure-consumption-insights/services.png)
3. Sélectionnez **Microsoft Azure Consumption Insights** (informations sur la consommation de Microsoft Azure) \> **Obtenir maintenant**. 
   
   ![Obtenir maintenant](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Spécifiez le nombre de mois de données à importer ainsi que votre numéro d’inscription Azure Enterprise. Consultez les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
    ![Se connecter à Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Fournissez votre clé d’accès pour la connexion. Vous trouverez votre clé d'inscription sur le portail Azure EA. 
   
    ![Microsoft Azure Consumption Insights : clé](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Le processus d’importation commence automatiquement. Une fois le processus terminé, de nouveaux tableau de bord, rapport et modèle apparaissent dans le volet de navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
   ![Tableau de bord Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Même si une actualisation quotidienne de votre jeu de données est planifiée, vous pouvez modifier la planification de l’actualisation ou essayer d’actualiser le jeu de données sur demande à l’aide de l’option **Actualiser maintenant**.

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu Microsoft Azure Consumption Insights contient des données de rapports mensuelles correspondant à la plage de mois que vous avez indiquée lors de la connexion. La plage est dynamique, ce qui signifie que les dates incluses sont mises à jour quand le jeu de données est actualisé.

## <a name="system-requirements"></a>Configuration requise
Le pack de contenu exige l’accès aux fonctionnalités d’entreprise dans le portail Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Les rapports Power BI sont disponibles pour les clients directs, les partenaires et les clients indirects d’EA qui peuvent afficher des informations de facturation. Pour plus d’informations sur la recherche de chacune des valeurs qu’attend le flux de connexion, lisez ci-dessous.

**Nombre de mois**

* Le nombre de mois (1 à 36) de données que vous souhaitez importer à partir d'aujourd'hui.

**Numéro d’inscription**

* Votre numéro d’inscription à Azure Enterprise, qui se trouve sur l’écran d’accueil d’[Azure Enterprise Portal](https://ea.azure.com/) sous les **détails de l’inscription**.
  
    ![Numéro d’inscription](media/service-connect-to-azure-consumption-insights/params2.png)

**Clé d’accès**

* Vous trouverez votre clé d’accès dans le portail Azure Enterprise, sous **Télécharger l’utilisation** > **Clé d’accès API**.
  
    ![Clé d’accès](media/service-connect-to-azure-consumption-insights/creds2.png)

**Aide supplémentaire**

* Pour obtenir de l'aide supplémentaire sur la configuration du pack Azure Enterprise Power BI, connectez-vous au portail Azure Enterprise et consultez le fichier d'aide de l'API sous **Aide**. Vous trouverez des instructions supplémentaires sous **Rapports** -> **Télécharger l’utilisation** -> **Clé d’accès API**.
* Pour bénéficier d’une configuration personnalisée, utilisez le [connecteur Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) dans Power BI Desktop.

## <a name="next-steps"></a>Étapes suivantes

[Connecteur Azure Consumption Insights](desktop-connect-azure-consumption-insights.md) dans Power BI Desktop

[Obtenir des données dans Power BI](service-get-data.md)

