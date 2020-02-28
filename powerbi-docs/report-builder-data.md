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
ms.date: 06/06/2019
ms.openlocfilehash: f8f7d3b43cfc2d5a51b686598c1657ec21b44130
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527266"
---
# <a name="report-data-in-power-bi-report-builder"></a>Données de rapport dans le Générateur de rapports Power BI

Les données de rapport peuvent provenir de plusieurs sources de données de votre organisation. La première étape de la conception d’un rapport du Générateur de rapports Power BI consiste à créer des sources de données et des jeux de données qui représentent les données sous-jacentes du rapport. Chaque source de données comprend des informations de connexion de données. Chaque jeu de données comprend une commande de requête qui définit l’ensemble des champs à utiliser comme données d’une source de données. Pour visualiser les données de chaque jeu de données, ajoutez une région de données, comme un tableau, une matrice, un graphique ou une carte. Lors du traitement du rapport, les requêtes s’exécutent sur la source de données et chaque région de données se développe au besoin pour afficher les résultats de requête pour le jeu de données.  

Découvrez comment [Créer une source de données incorporée pour rapports paginés dans le Générateur de rapports Power BI](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Terminologie  
  
- **Connexion de données.** Également appelée *source de données*. Une connexion de données comprend un nom et des propriétés de connexion qui dépendent du type de connexion. Par défaut, une connexion de données ne comprend pas d’informations d’identification. Une connexion de données ne spécifie pas les données à récupérer dans la source de données externe. Pour cela, spécifiez une requête lorsque vous créez un jeu de données.  
  
- **Chaîne de connexion.** Une chaîne de connexion est une version de chaîne des propriétés de connexion qui sont nécessaires pour se connecter à une source de données. Les propriétés de connexion varient en fonction du type de connexion de données.  
  
- **Source de données incorporée.** Également appelée *source de données spécifique au rapport*. Source de données qui est définie dans un rapport et utilisée uniquement par ce rapport.  
  
- **Informations d’identification.** Les informations d’identification sont des informations d’authentification qui doivent être fournies pour vous permettre d’accéder aux données externes.  
  
##  <a name="BkMk_ReportDataTips"></a> Conseils pour spécifier les données de rapport

 Servez-vous des informations suivantes pour concevoir votre stratégie de données de rapport.  
  
- **Filtrer les données** Vous pouvez filtrer les données de rapport dans la requête ou le rapport. Vous pouvez utiliser des jeux de données et des variables de requête pour créer des paramètres en cascade et fournir à l’utilisateur la possibilité de passer de milliers de sélections à un nombre plus gérable. Vous pouvez filtrer les données d’un tableau ou d’un graphique sur les valeurs de paramètre ou d’autres valeurs que vous spécifiez.  
  
- **Paramètres** Des commandes de requête de jeu de données qui contiennent des variables de requête créent automatiquement les paramètres de rapport correspondants. Vous pouvez aussi créer des paramètres manuellement. Quand vous ouvrez un rapport, la barre d’outils du rapport affiche les paramètres. Les utilisateurs peuvent sélectionner des valeurs pour contrôler les données du rapport ou l’apparence du rapport. Pour personnaliser les données de rapport pour une audience spécifique, vous pouvez créer des jeux de paramètres de rapport avec différentes valeurs par défaut liées à la même définition de rapport, ou utiliser le champ **UserID** intégré. 
  
- **Regrouper et agréger les données** Les données de rapport peuvent être regroupées et agrégées dans la requête ou le rapport. Si vous agrégez des valeurs dans la requête, vous pouvez continuer à combiner des valeurs dans le rapport tant que cela a un sens.  
  
- **Trier les données** Vous pouvez trier les données de rapport dans la requête ou le rapport. Dans les tableaux, vous pouvez également ajouter un bouton de tri interactif pour permettre à l’utilisateur de contrôler l’ordre de tri.  
  
- **Données basées sur les expressions** Parce que les propriétés de rapport peuvent être basées sur des expressions et que les expressions peuvent inclure des références à des champs de jeu de données et à des paramètres de rapport, vous pouvez écrire des expressions puissantes pour contrôler les données et l’apparence du rapport. Vous pouvez fournir à un utilisateur la possibilité de contrôler les données qu’il voit en définissant des paramètres.  
  
- **Afficher les données d’un jeu de données** Les données d’un jeu de données sont généralement affichées dans une ou plusieurs régions de données, par exemple, un tableau et un graphique.  
  
- **Afficher les données de plusieurs jeux de données** Vous pouvez écrire des expressions dans une région de données basées sur un jeu de données qui recherchent des valeurs ou des agrégats dans d’autres jeux de données. Vous pouvez inclure des sous-rapports dans un tableau basés sur un jeu de données pour afficher des données d’une autre source de données.  
  
 Utilisez la liste suivante pour vous aider à définir des sources de données pour un rapport.  
  
- Comprenez l’architecture en couche des données logicielles de votre organisation et les problèmes potentiels résultant des types de données. Comprenez de quelle façon les extensions de données et les extensions de traitement des données peuvent affecter les résultats de requête. Les types de données varient en fonction de la source de données, des fournisseurs de données et des types de données stockés dans le fichier de définition de rapport (.rdl).  
  
- Les jeux de données et les sources de données sont créés dans un rapport et publiés sur le service Power BI. Après leur publication, vous pouvez configurer des informations d’identification directement dans le service Power BI ou dans votre passerelle d’entreprise. 

## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)  
- [Conseils pour extraire des données pour les rapports paginés](guidance/report-paginated-data-retrieval.md)
