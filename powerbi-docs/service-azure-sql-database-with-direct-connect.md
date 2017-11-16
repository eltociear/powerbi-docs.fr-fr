---
title: Azure SQL Database avec DirectQuery
description: Azure SQL Database avec DirectQuery
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 83613f0ed915a03b65b90d4bf61e37568b922182
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database avec DirectQuery
Découvrez comment vous pouvez vous connecter directement à Azure SQL Database et créer des rapports qui utilisent des données actives. Vous pouvez conserver vos données à la source et pas dans Power BI.

Avec DirectQuery, les requêtes sont renvoyées à Azure SQL Database pendant que vous explorez les données dans l’affichage Rapport. Cette fonctionnalité est suggérée aux utilisateurs qui connaissent bien les bases de données et les entités auxquelles ils se connectent.

**Remarques :**

* Spécifiez le nom de serveur complet lors de la connexion (voir ci-dessous pour plus de détails)
* Vérifiez que les règles de pare-feu de la base de données sont définies sur [Autoriser l’accès aux services Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx).
* Chaque action, telle que la sélection d’une colonne ou l’ajout d’un filtre, renverra une requête à la base de données
* Les vignettes sont actualisées environ toutes les 15 minutes (il n’est pas nécessaire de planifier l’actualisation). Vous pouvez régler cet intervalle dans les paramètres avancés lorsque vous vous connectez.
* Q&R n’est pas disponible pour les jeux de données DirectQuery.
* Les modifications apportées aux schémas ne sont pas appliquées automatiquement

Ces points sont susceptibles de changer, car nous travaillons actuellement à améliorer le produit. Les étapes de connexion sont détaillées ci-dessous. 

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop et DirectQuery
Pour vous connecter à Azure SQL Database à l’aide de DirectQuery, vous devez utiliser Power BI Desktop. Cette approche offre des fonctionnalités et une flexibilité supplémentaires. Les rapports créés à l’aide de Power BI Desktop peuvent ensuite être publiés sur le service Power BI. Vous pouvez en savoir plus sur la connexion à [Azure SQL Database à l’aide de DirectQuery](desktop-use-directquery.md) dans Power BI Desktop. 

## <a name="connecting-through-power-bi"></a>Connexion par le biais de Power BI
Vous ne pouvez plus vous connecter à Azure SQL Database directement à partir du service Power BI. Lorsque vous sélectionnez le [connecteur Azure SQL Database](https://app.powerbi.com/getdata/bigdata/azure-sql-database-with-live-connect), vous êtes invité à établir la connexion dans Power BI Desktop. Vous pouvez ensuite publier vos rapports Power BI Desktop dans le service Power BI. 

![](media/service-azure-sql-database-with-direct-connect/azure-sql-database-in-power-bi.png)

### <a name="finding-parameter-values"></a>Recherche des valeurs de paramètres
Le nom complet de votre serveur et celui de votre base de données se trouvent dans le portail Azure.

![](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Étapes suivantes
[Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md)  
[Prise en main de Power BI](service-get-started.md)  
[Obtenir des données pour Power BI](service-get-data.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

