---
title: Azure SQL Database avec DirectQuery
description: Azure SQL Database avec DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.date: 09/16/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: e1f770ac43207666966d3844e1e3728020849346
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699771"
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database avec DirectQuery

Découvrez comment vous pouvez vous connecter directement à Azure SQL Database et créer des rapports qui utilisent des données actives. Vous pouvez conserver vos données à la source et pas dans Power BI.

Avec DirectQuery, les requêtes sont renvoyées à Azure SQL Database pendant que vous explorez les données dans l’affichage Rapport. Cette fonctionnalité est suggérée aux utilisateurs qui connaissent bien les bases de données et les entités auxquelles ils se connectent.

**Remarques :**

* Spécifiez le nom de serveur complet lors de la connexion (voir ci-dessous pour plus de détails).
* Vérifiez que les règles de pare-feu de la base de données sont configurées de manière à [autoriser l’accès aux services Azure](https://docs.microsoft.com/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services).
* Chaque action, telle que la sélection d’une colonne ou l’ajout d’un filtre, retourne une requête à la base de données.
* Les vignettes sont actualisées chaque heure (il n’est pas nécessaire de planifier l’actualisation). Vous pouvez ajuster la fréquence d’actualisation dans les paramètres avancés quand vous vous connectez.
* Il n’y a pas de Q&R disponible pour les jeux de données DirectQuery.
* Les modifications apportées aux schémas ne sont pas sélectionnées automatiquement.

Ces points sont susceptibles de changer, car nous travaillons actuellement à améliorer le produit. Les étapes de connexion sont détaillées ci-dessous.

> [!Important]
> Nous avons amélioré notre connectivité à Azure SQL Database.  Pour une expérience optimale de connexion à votre source de données Azure SQL Database, utilisez Power BI Desktop.  Une fois que vous avez créé votre modèle et votre rapport, vous pouvez publier ce dernier sur le service Power BI.  Le connecteur direct pour Azure SQL Database dans le service Power BI est désormais déprécié.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop et DirectQuery

Pour vous connecter à Azure SQL Database à l’aide de DirectQuery, vous devez utiliser Power BI Desktop. Cette approche offre des fonctionnalités supplémentaires et une flexibilité plus grande. Les rapports créés à l’aide de Power BI Desktop peuvent ensuite être publiés sur le service Power BI. Vous pouvez en savoir plus sur la connexion à [Azure SQL Database à l’aide de DirectQuery](desktop-use-directquery.md) dans Power BI Desktop.

## <a name="find-parameter-values"></a>Rechercher des valeurs de paramètre

Le nom complet de votre serveur et celui de votre base de données se trouvent dans le portail Azure.

![Nouvelle mise à jour du portail Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Mise à jour du portail Azure](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>Étapes suivantes

* [Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md)  
* [Qu’est-ce que Power BI ?](fundamentals/power-bi-overview.md)  
* [Obtenir des données pour Power BI](service-get-data.md)  

D’autres questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)
