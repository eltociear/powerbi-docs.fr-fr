---
title: "Graphiques en anneau dans Power BI (didacticiel)"
description: "Didacticiel : graphiques en anneau dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 2f428095eb57c5358770f1d6d8572316d2b84c37
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Graphiques en anneau dans Power BI (didacticiel)
Un graphique en anneau est similaire à un graphique en secteurs, car il représente aussi la relation de parties par rapport à un ensemble. La seule différence est que le centre est vide et qu’il y a de la place pour une étiquette ou une icône.

## <a name="create-a-doughnut-chart"></a>Créer un graphique en anneau
Pour effectuer la procédure, connectez-vous à Power BI et sélectionnez **Obtenir des données** \> **Exemples** \> **Exemple Analyse de la vente au détail** \> **Se connecter**. 

1. Dans le tableau de bord, sélectionnez la vignette **Total Stores** (Nombre total de magasins) pour ouvrir le rapport « Exemple Analyse de la vente au détail ».
2. Sélectionnez **Modifier le rapport** pour ouvrir le rapport en Mode Edition.
3. [Ajoutez une nouvelle page au rapport](power-bi-report-add-page.md).
4. Créez un graphique en anneau qui affiche les ventes de cette année par catégorie.
   
   * Dans le volet **Champs**, sélectionnez **Sales**\>**Last Year Sales**(Ventes > Ventes de l’année dernière).
   * Convertissez le graphique en graphique en anneau. Si Last Year Sales (Ventes de l’année dernière) ne figure pas dans la zone **Valeurs** , faites-le glisser vers cette zone.
     
       ![](media/power-bi-visualization-doughnut-charts/convertdonut.png)
   * Sélectionnez **Élément** \> **Catégorie** pour l’ajouter à la zone **Légende**. 
     
       ![](media/power-bi-visualization-doughnut-charts/doughnuttutorial.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* La somme des valeurs du graphique en anneau doit atteindre 100 %.
* L’utilisation d’un trop grand nombre de catégories peut rendre le graphique difficile à lire et à analyser.
* Les graphiques en anneau sont davantage adaptés pour comparer une section spécifique par rapport à l’ensemble que pour comparer des sections individuelles entre elles. 

## <a name="next-steps"></a>Étapes suivantes
[Rapports dans Power BI](service-reports.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Visualisations dans des rapports Power BI](power-bi-report-visualizations.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

