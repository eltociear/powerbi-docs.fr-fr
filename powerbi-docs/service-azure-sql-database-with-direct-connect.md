---
title: Azure SQL Database avec DirectQuery
description: Azure SQL Database avec DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/20/2018
LocalizationGroup: Data from databases
ms.openlocfilehash: f03f4933566a8c18510ef0ce07b71db61ecfa8fd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770597"
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database avec DirectQuery

Découvrez comment vous pouvez vous connecter directement à Azure SQL Database et créer des rapports qui utilisent des données actives. Vous pouvez conserver vos données à la source et pas dans Power BI.

Avec DirectQuery, les requêtes sont renvoyées à Azure SQL Database pendant que vous explorez les données dans l’affichage Rapport. Cette fonctionnalité est suggérée aux utilisateurs qui connaissent bien les bases de données et les entités auxquelles ils se connectent.

**Remarques :**

* Spécifiez le nom de serveur complet lors de la connexion (voir ci-dessous pour plus de détails)
* Vérifiez que les règles de pare-feu de la base de données sont définies sur [Autoriser l’accès aux services Azure](https://msdn.microsoft.com/library/azure/ee621782.aspx).
* Chaque action, telle que la sélection d’une colonne ou l’ajout d’un filtre, renverra une requête à la base de données
* Les vignettes sont actualisées chaque heure (il n’est pas nécessaire de planifier l’actualisation). Vous pouvez régler cet intervalle dans les paramètres avancés lorsque vous vous connectez.
* Q&R n’est pas disponible pour les jeux de données DirectQuery.
* Les modifications apportées aux schémas ne sont pas appliquées automatiquement

Ces points sont susceptibles de changer, car nous travaillons actuellement à améliorer le produit. Les étapes de connexion sont détaillées ci-dessous.

> [!Important]
> Nous avons amélioré notre connectivité à Azure SQL Database.  Pour une expérience optimale de connexion à votre source de données Azure SQL Database, utilisez Power BI Desktop.  Une fois que vous avez créé votre modèle et votre rapport, vous pouvez publier ce dernier sur le service Power BI.  Le connecteur direct pour Azure SQL Database dans le service Power BI est désormais déprécié.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop et DirectQuery

Pour vous connecter à Azure SQL Database à l’aide de DirectQuery, vous devez utiliser Power BI Desktop. Cette approche offre des fonctionnalités supplémentaires et une flexibilité plus grande. Les rapports créés à l’aide de Power BI Desktop peuvent ensuite être publiés sur le service Power BI. Vous pouvez en savoir plus sur la connexion à [Azure SQL Database à l’aide de DirectQuery](desktop-use-directquery.md) dans Power BI Desktop.

## <a name="single-sign-on"></a>Authentification unique

Une fois que vous avez publié un jeu de données Azure SQL DirectQuery dans le service, vous pouvez activer l’authentification unique (SSO) via OAuth2 d’Azure Active Directory (Azure AD) pour vos utilisateurs finaux.

Pour activer l’authentification unique, accédez aux paramètres du jeu de données, ouvrez l’onglet **Sources de données**, puis cochez la case de l’authentification unique.

![Configurer la boîte de dialogue DQ de SQL Azure](media/service-azure-sql-database-with-direct-connect/sso-dialog.png)

Lorsque l’option d’authentification unique est activée et que vos utilisateurs accèdent aux rapports basés sur la source de données, Power BI envoie leurs informations d’identification Azure AD dans les requêtes à Azure SQL Database. Ainsi, Power BI est en mesure de respecter les paramètres de sécurité qui sont configurés au niveau de la source de données.

L’option d’authentification unique prend effet sur tous les jeux de données qui utilisent cette source de données. Elle n’affecte pas la méthode d’authentification utilisée pour les scénarios d’importation.

> [!Note]
> L’authentification multifacteur Azure (MFA) n’est pas pris en charge. Les utilisateurs qui souhaitent utiliser l’authentification unique avec Azure SQL DirectQuery doivent être exemptés de la MFA.

## <a name="finding-parameter-values"></a>Recherche des valeurs de paramètres

Le nom complet de votre serveur et celui de votre base de données se trouvent dans le portail Azure.

![Nouvelle mise à jour d’un port Azure](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Mise à jour du portail Azure](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Étapes suivantes

* [Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md)  
* [Qu’est-ce que Power BI ?](power-bi-overview.md)  
* [Obtenir des données pour Power BI](service-get-data.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
