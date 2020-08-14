---
title: Données de rapport dans le Générateur de rapports Power BI
description: La première étape de la conception d’un rapport dans Power BI Report Builder consiste à créer des sources de données et des jeux de données qui représentent les données sous-jacentes du rapport.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 08/04/2020
ms.openlocfilehash: fe6ca733a5498c0e576ec30e6992ffbf26d54319
ms.sourcegitcommit: 65822b51810a5239fea9d3d0af1fc286436c6cad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87837586"
---
# <a name="report-data-in-power-bi-report-builder"></a>Données de rapport dans le Générateur de rapports Power BI

Les données de rapport peuvent provenir de plusieurs sources de données de votre organisation. La première étape de la conception d’un rapport du Générateur de rapports Power BI consiste à créer des sources de données et des jeux de données qui représentent les données sous-jacentes du rapport. Chaque source de données comprend des informations de connexion de données. Chaque jeu de données comprend une commande de requête qui définit l’ensemble des champs à utiliser comme données d’une source de données. Pour visualiser les données de chaque jeu de données, ajoutez une région de données, comme un tableau, une matrice, un graphique ou une carte. Lors du traitement du rapport, les requêtes s’exécutent sur la source de données et chaque région de données se développe au besoin pour afficher les résultats de requête pour le jeu de données.  

Découvrez comment [Créer une source de données incorporée pour rapports paginés dans le Générateur de rapports Power BI](paginated-reports-embedded-data-source.md).


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> Terminologie  
  
- **Connexion de données.** Également appelée *source de données*. Une connexion de données comprend un nom et des propriétés de connexion qui dépendent du type de connexion. Par défaut, une connexion de données ne comprend pas d’informations d’identification. Une connexion de données ne spécifie pas les données à récupérer dans la source de données externe. Pour cela, spécifiez une requête lorsque vous créez un jeu de données.  
  
- **Chaîne de connexion.** Une chaîne de connexion est une version de chaîne des propriétés de connexion qui sont nécessaires pour se connecter à une source de données. Les propriétés de connexion varient en fonction du type de connexion de données. 

    > [!NOTE]
    > Les chaînes de connexion à la source de données ne peuvent pas être basées sur une expression.
  
- **Source de données incorporée.** Également appelée *source de données spécifique aux rapports*. Il s'agit d'une source de données définie dans un rapport et utilisée uniquement par ce dernier.  
  
- **Informations d’identification.** Les informations d'identification sont des informations d'authentification qui doivent être fournies pour vous permettre d'accéder à des données externes.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> Conseils pour spécifier les données de rapport

 Utilisez les informations suivantes pour concevoir votre stratégie de données de rapport.  
  
- **Filtrer les données** Les données de rapport peuvent être filtrées dans la requête ou dans le rapport. Vous pouvez utiliser des datasets et interroger des variables pour créer des paramètres en cascade et fournir à l'utilisateur la possibilité de limiter les choix parmi des milliers de sélections à un nombre plus gérable. Vous pouvez filtrer les données dans une table ou un graphique en fonction des valeurs des paramètres ou d'autres valeurs que vous spécifiez.  
  
- **Paramètres** Les commandes de requête de datasets qui incluent des variables de requêtes créent automatiquement les paramètres de rapport correspondants. Vous pouvez également créer des paramètres manuellement. Lorsque vous affichez un rapport, la barre d'outils Rapport affiche les paramètres. Les utilisateurs peuvent sélectionner des valeurs pour contrôler l'apparence des données de rapport ou du rapport. Pour personnaliser les données du rapport pour un public donné, vous pouvez créer des ensembles de paramètres de rapport avec différentes valeurs par défaut liées à la même définition de rapport ou utiliser le champ prédéfini **UserID** . 
  
- **Groupe et données agrégées** Les données de rapport peuvent être regroupées et agrégées dans la requête ou dans le rapport. Si vous agrégez des valeurs dans la requête, vous pouvez continuer à combiner des valeurs dans le rapport dans des limites de ce qui est explicite.  
  
- **Trier des données** Les données de rapport peuvent être triées dans la requête ou dans le rapport. Dans les tables, vous pouvez également ajouter un bouton de tri interactif pour permettre à l'utilisateur de contrôler l'ordre de tri.  
  
- **Données basées sur des expressions** Comme la plupart des propriétés de rapport peuvent être basées sur des expressions, et que les expressions peuvent inclure des références à des champs de dataset et à des paramètres de rapport, vous pouvez écrire des expressions puissantes pour contrôler les données et l’apparence du rapport. Vous pouvez fournir à l'utilisateur la possibilité de contrôler les données qu'il consulte en définissant des paramètres.  
  
- **Afficher les données d'un dataset** Les données d'un dataset sont généralement affichées sur une ou plusieurs régions de données, par exemple, une table et un graphique.  
  
- **Afficher les données de plusieurs datasets**  Vous pouvez écrire des expressions dans une région de données basée sur un dataset qui recherche des valeurs ou des agrégats dans d'autres datasets. Vous pouvez inclure des sous-rapports dans une table selon un dataset pour afficher les données d'une source de données différente.  
  
 Utilisez la liste suivante pour définir les sources de données d'un rapport.  
  
- Comprenez l'architecture de la couche de données logicielle de votre organisation et les problèmes potentiels résultant des types de données. Comprenez comment les extensions de données et les extensions pour le traitement des données peuvent affecter les résultats de la requête. Les types de données diffèrent entre la source de données, les fournisseurs de données et les types de données stockés dans le fichier de définition de rapport (.rdl).  
  
- Les jeux de données et les sources de données sont créés dans un rapport et publiés sur le service Power BI. Après leur publication, vous pouvez configurer des informations d’identification directement dans le service Power BI ou dans votre passerelle d’entreprise. 

## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)  
- [Conseils pour extraire des données pour les rapports paginés](../guidance/report-paginated-data-retrieval.md)
