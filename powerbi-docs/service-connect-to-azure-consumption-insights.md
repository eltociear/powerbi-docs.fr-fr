---
title: Se connecter à Microsoft Azure Consumption Insights avec Power BI
description: Microsoft Azure Consumption Insights pour Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222123"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Se connecter à Microsoft Azure Consumption Insights avec Power BI
Explorez et analysez vos données de consommation de Microsoft Azure dans Power BI avec le pack de contenu de Power BI. Les données sont actualisées automatiquement une fois par jour.

Connectez-vous au [Pack de contenu d’informations sur la consommation de Microsoft Azure](https://app.powerbi.com/getdata/services/azureconsumption) pour Power BI.

## <a name="how-to-connect"></a>Comment se connecter
1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Dans la zone **Services**, sélectionnez **Obtenir**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Sélectionnez **Microsoft Azure Consumption Insights** \> **obtenez-le maintenant**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Spécifiez le nombre de mois de données à importer ainsi que votre numéro d’inscription Azure Enterprise. Consultez les détails sur la [recherche de ces paramètres](#FindingParams) ci-dessous.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Fournissez votre clé d’accès pour la connexion. Vous trouverez votre clé d’inscription dans le portail Azure EA. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Le processus d’importation commence automatiquement. Lorsque vous avez terminé, un nouveau tableau de bord, le rapport et le modèle s’affichent dans le volet de Navigation. Sélectionnez le tableau de bord pour afficher vos données importées.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Et maintenant ?**

* Essayez de [poser une question dans la zone Q&R](consumer/end-user-q-and-a.md) en haut du tableau de bord.
* [Modifiez les vignettes](service-dashboard-edit-tile.md) dans le tableau de bord.
* [Sélectionnez une vignette](consumer/end-user-tiles.md) pour ouvrir le rapport sous-jacent.
* Alors que votre jeu de données est planifiée pour actualiser tous les jours, vous pouvez modifier la planification d’actualisation ou essayer d’actualiser sur l’utilisation de la demande **Actualiser maintenant**

## <a name="whats-included"></a>Ce qui est inclus
Le pack de contenu Microsoft Azure Consumption Insights inclut tous les mois des rapports les données de la plage de mois que vous avez fourni lors de la connexion. La plage étant une fenêtre de déplacement, les dates incluses sont mises à jour comme actualise le jeu de données.

## <a name="system-requirements"></a>Configuration requise
Le pack de contenu requiert l’accès aux fonctionnalités d’entreprise au sein du portail Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Recherche de paramètres
Création de rapports Power BI est disponible pour EA Direct, partenaires et clients indirects qui peut afficher des informations de facturation. Lisez ce qui suit pour plus d’informations sur la recherche de chacune des valeurs qu'attend le flux de connexion.

**Nombre de mois**

* Le nombre de mois (1-36) de données à partir d’aujourd'hui que vous souhaitez importer.

**Numéro d’inscription**

* Votre numéro d’inscription Azure Enterprise, que vous pouvez trouver à le [Azure Enterprise Portal](https://ea.azure.com/) écran d’accueil sous **détails de l’inscription**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Clé d’accès**

* Vous pouvez trouver votre clé d’accès dans le portail Azure Enterprise, sous **télécharger l’utilisation** > **clé d’accès API**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Aide supplémentaire**

* Pour obtenir une aide supplémentaire configuration du Pack Azure Enterprise Power BI, connectez-vous à Azure Enterprise Portal et afficher le fichier d’aide API sous **aide**. Vous pouvez également trouver des instructions supplémentaires sous **rapports** -> **télécharger l’utilisation** -> **clé d’accès API**.

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)

[Obtenir des données dans Power BI](service-get-data.md)

