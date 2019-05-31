---
title: Optimiser des données Excel avec questions et réponses dans Power BI
description: Optimiser vos données avec Questions et réponses dans Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7ed8eb8e205c05582d2cfd93030ab056be77912a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65624986"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Optimiser des données Excel avec questions et réponses dans Power BI
Si vous êtes chargé de créer des modèles de données ou des classeurs Excel qui seront utilisés avec Power BI, continuez votre lecture…

Dans Power BI, Q&R peut effectuer des recherches dans des données structurées et choisir la visualisation qui convient le mieux à votre question. C’est ce qui en fait un outil incontournable.   

Le moteur Questions et réponses peut être utilisé sur n’importe quel fichier Excel chargé contenant des tableaux, des plages ou un modèle PowerPivot. Toutefois, plus vous optimisez et nettoyez vos données, meilleures sont les performances du moteur.  Si vous prévoyez de partager des rapports et tableaux de bord basés sur votre jeu de données, vous voulez que vos collègues puissent facilement poser des questions et obtenir des réponses de qualité.

## <a name="how-qa-works-with-excel"></a>Fonctionnement de Questions et réponses avec Excel
Q&R présente des capacités de compréhension de base du langage naturel qui peuvent être utilisées sur l’ensemble de vos données. Il comprend une recherche par mot clé dépendante du contexte pour les noms de tables, colonnes et champs calculés Excel. Il a également une connaissance intégrée de la manière dont les données doivent être filtrées, triées, agrégées, regroupées et affichées. 

Par exemple, si vous disposiez d’un tableau Excel nommé « Ventes » comprenant les colonnes « Produits », « Mois », « Unités vendues », « Ventes brutes » et « Bénéfices », vous pourriez poser des questions sur l’une de ces entités.  Vous pourriez demander d’afficher les ventes, le total des bénéfices par mois, les produits triés par unités vendues, et ainsi de suite. En savoir plus sur [à l’aide de Q & r dans les tableaux de bord et rapports](power-bi-tutorial-q-and-a.md), et [types de visualisations que vous pouvez spécifier dans une requête Q & r](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Préparer un jeu de données Excel pour Questions et réponses
Q&R s’appuie sur les noms des tables, des colonnes et des champs calculés pour répondre aux questions spécifiques aux données. Le nom que vous attribuez à vos entités est donc important.

Voici quelques conseils pour tirer le meilleur parti de Q&R.

* Assurez-vous que vos données se trouvent dans un tableau Excel. Voici [comment créer un tableau Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Assurez-vous que les noms des tables, des colonnes et des champs calculés sont explicites.
  
  Par exemple, si vous disposez d’une table qui contient des données de ventes, nommez-la « Ventes ». Les noms de colonnes tels que « Année », « Produit », « Commercial » et « Montant » vous permettront d’obtenir d’excellents résultats avec Q&R.

* si votre classeur contient un modèle de données Power Pivot, vous pouvez procéder à davantage d’optimisations. Pour plus d’informations, consultez cet article de notre équipe d’experts internes en langage naturel intitulé [Demystifying Power BI Q&A part 2 (Q&R : démystification de Power BI, partie 2)](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx).

* Ouvrez le jeu de données dans Power BI Desktop et créez des colonnes, créez des mesures calculées, concaténez des champs pour créer des valeurs uniques, classez les données par type (par exemple, dates, chaînes, données géographiques, images, URL) et bien plus encore.

## <a name="next-steps"></a>Étapes suivantes

- [Questions et réponses pour les consommateurs](consumer/end-user-q-and-a.md)  
- [Utiliser Q & r dans les tableaux de bord et rapports](power-bi-tutorial-q-and-a.md)
- [Préparer des jeux de données en local pour Q & A](service-q-and-a-direct-query.md)   
- [Obtenir des données (pour Power BI)](service-get-data.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

