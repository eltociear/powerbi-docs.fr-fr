---
title: Azure SQL Data Warehouse avec DirectQuery
description: Azure SQL Data Warehouse avec DirectQuery
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/22/2018
ms.author: maghan
LocalizationGroup: Data from databases
ms.openlocfilehash: 87b49833b5c0d1d634d440e947659a12ac87b66c
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="azure-sql-data-warehouse-with-directquery"></a>Azure SQL Data Warehouse avec DirectQuery
Azure SQL Data Warehouse avec DirectQuery vous permet de créer des rapports dynamiques basés sur des données et mesures dont vous disposez déjà dans Azure SQL Data Warehouse. Avec DirectQuery, les requêtes sont renvoyées à Azure SQL Data Warehouse en temps réel pendant que vous explorez les données. Ceci, combiné à l’échelle de SQL Data Warehouse, permet aux utilisateurs de créer en quelques minutes des rapports dynamiques sur plusieurs téraoctets de données. De plus, l’introduction du bouton **Ouvrir dans Power BI** permet aux utilisateurs de connecter directement Power BI à leur entrepôt de données SQL sans avoir à spécifier manuellement les informations.

Lorsque vous utilisez le connecteur SQL Data Warehouse :

* Spécifiez le nom de serveur complet lors de la connexion (voir ci-dessous pour plus de détails).
* Vérifiez que les règles de pare-feu sont configurées pour « Autoriser l’accès aux services Azure ».
* Chaque action, telle que la sélection d’une colonne ou l’ajout d’un filtre, interroge directement l’entrepôt de données.
* Les vignettes étant configurées pour s’actualiser environ toutes les 15 minutes, il est inutile de planifier l’actualisation.  Vous pouvez régler cet intervalle dans les paramètres avancés lorsque vous vous connectez.
* Il n’y a pas de Q&R disponibles pour les jeux de données DirectQuery.
* Les modifications apportées aux schémas ne sont pas appliquées automatiquement.

Ces points sont susceptibles de changer, car nous travaillons actuellement à améliorer le produit. L’étape de connexion est détaillée ci-dessous.

## <a name="using-the-open-in-power-bi-button"></a>Utilisation du bouton « Ouvrir dans Power BI »
Le moyen le plus simple de basculer entre votre entrepôt de données SQL et Power BI consiste à utiliser le bouton **Ouvrir dans Power BI** dans le portail Azure en version préliminaire. Ce bouton vous permet de commencer à créer des tableaux de bord dans Power BI en toute transparence.

1. Pour commencer, accédez à votre instance d’entrepôt de données SQL dans le portail Azure en version préliminaire. Notez qu’à l’heure actuelle SQL Data Warehouse n’est présent que dans le portail Azure en version préliminaire.
2. Cliquez sur le bouton **Ouvrir dans Power BI** .
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/openinpowerbi.png)
3. Si nous ne pouvons pas vous connecter directement ou si vous n’avez pas de compte Power BI, vous devrez vous connecter.
4. Vous serez dirigé vers la page de connexion SQL Data Warehouse, où les informations de votre SQL Data Warehouse seront préremplies. Entrez vos informations d’identification et cliquez sur Se connecter pour créer une connexion.

## <a name="connecting-through-power-bi"></a>Connexion par le biais de Power BI
SQL Data Warehouse est également répertorié dans la page Obtenir des données de Power BI. 

1. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche.  
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/getdatabutton.png)
2. Dans **Bases de données**, sélectionnez **Obtenir**.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/databases.png)
3. Sélectionnez **Entrepôt de données SQL**\>**Se connecter**.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/azuresqldatawarehouseconnect.png)
4. Entrez les informations nécessaires pour vous connecter. La section **Recherche des valeurs de paramètres** ci-dessous indique l’emplacement de ces données dans votre portail Azure.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/servername.png)
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/servernamewithadvanced.png)
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/username.png)
   
   > [!NOTE]
   > Le nom d’utilisateur est un utilisateur qui est défini dans votre instance Azure SQL Data Warehouse.
   > 
   > 
5. Explorez le jeu de données en sélectionnant la nouvelle vignette ou le jeu de données nouvellement créé, indiqué par l’astérisque. Ce jeu de données a le même nom que votre base de données.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/dataset2.png)
6. Vous pouvez explorer toutes les tables et les colonnes. La sélection d’une colonne renverra une requête à la source, créant ainsi dynamiquement votre élément visuel. Les filtres seront aussi convertis en requêtes et renvoyés à votre entrepôt de données. Vous pouvez enregistrer ces éléments visuels dans un nouveau rapport et les épingler dans votre tableau de bord.
   
    ![](media/service-azure-sql-data-warehouse-with-direct-connect/explore3.png)

## <a name="finding-parameter-values"></a>Recherche des valeurs de paramètres
Le nom complet du serveur et celui de votre base de données se trouvent dans le portail Azure en version préliminaire. Notez qu’à l’heure actuelle SQL Data Warehouse n’est présent que dans le portail Azure en version préliminaire.

![](media/service-azure-sql-data-warehouse-with-direct-connect/azureportal.png)

> [!NOTE]
> Si votre locataire Power BI se trouve dans la même région qu’Azure SQL Data Warehouse, aucuns frais de sortie ne sont exigés. Vous pouvez déterminer l’emplacement de votre locataire Power BI en suivant [ces instructions](https://docs.microsoft.com/en-us/power-bi/service-admin-where-is-my-tenant-located).
>

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)  
[Obtenir des données pour Power BI](service-get-data.md)  
[Azure SQL Data Warehouse](https://azure.microsoft.com/en-us/documentation/services/sql-data-warehouse/)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)