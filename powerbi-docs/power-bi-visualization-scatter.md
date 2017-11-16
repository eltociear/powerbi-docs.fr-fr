---
title: "Nuages de points dans Power BI (didacticiel)"
description: "Didacticiel : Nuages de points dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: PVcfPoVE3Ys
qualityfocus: identified
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: c1801db4135d6d97a940e593de37ca2886194b53
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="scatter-charts-and-bubble-charts-in-power-bi-tutorial"></a>Nuages de points et graphiques en bulles dans Power BI (didacticiel)
Un nuage de points a toujours deux axes de valeur pour afficher un jeu de données numériques sur l’axe horizontal et un autre jeu de valeurs numériques sur l’axe vertical. Le graphique affiche les points à l’intersection d’une valeur numérique x et y, en associant ces valeurs en points de données uniques. Ces derniers peuvent être distribués uniformément ou non sur l’axe horizontal, en fonction des données.

Un graphique en bulles remplace les points de données par des bulles, la *taille* de la bulle représentant une dimension supplémentaire des données.

![](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>Choix de l’utilisation d’un nuage de points ou d’un graphique en bulles
### <a name="scatter-charts-are-a-great-choice"></a>Les nuages de points sont conseillés dans les cas suivants :
* Pour afficher les relations entre 2 (nuage de points) ou 3 (bulles) valeurs **numériques** .
* Pour tracer les deux groupes de nombres sous la forme d’une série de coordonnées xy.
* À la place d’un graphique en courbes lorsque vous souhaitez modifier l’échelle de l’axe horizontal.    
* Pour transformer l’axe horizontal en échelle logarithmique.
* Pour afficher les données de feuille de calcul qui incluent des paires ou des jeux groupés de valeurs. Dans un nuage de points, vous pouvez ajuster les échelles indépendantes des axes pour afficher plus d’informations sur les valeurs groupées.
* Pour afficher des modèles dans de grands jeux de données, par exemple en affichant des valeurs hors norme, des clusters et des tendances linéaires ou non linéaires.
* Pour comparer un grand nombre de points de données sans distinction de temps. Plus vous incluez de données dans un nuage de points, meilleures sont les comparaisons possibles.

### <a name="bubble-charts-are-a-great-choice"></a>Les graphiques en bulles sont conseillés dans les cas suivants :
* Si vos données ont 3 séries de données qui contiennent chacune un jeu de valeurs.
* Pour présenter des données financières.  Différentes tailles de bulles sont utiles pour souligner visuellement des valeurs spécifiques.
* Pour utiliser avec des quadrants.

## <a name="create-a-scatter-chart"></a>Créer un nuage de points
<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Ouvrez l’exemple Analyse de la vente au détail en [Mode Édition](service-interact-with-a-report-in-editing-view.md) et [ajoutez une nouvelle page de rapport](power-bi-report-add-page.md).
2. Dans le volet Champs, sélectionnez **Ventes** > **Ventes par mètre carré** et **Ventes** > **Pourcentage d’écart des ventes totales**.
3. Dans le volet Champs, sélectionnez **District > District**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_pre_convert.png)
4. Effectuez la conversion en nuage de points. Dans le volet Visualisation, sélectionnez l’icône de nuage de points.
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_icon.png).
5. Faites glisser **District** depuis **Détails** vers **Légende**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_new.png)

Nous disposons désormais d’un nuage de points qui trace le pourcentage d’écart des ventes totales sur l’axe Y et les ventes par mètre carré sur l’axe X.  Les couleurs de points de données représentent des districts.  Ajoutons à présent une troisième dimension.

## <a name="create-a-bubble-chart"></a>Créer un graphique en bulles
1. Dans le volet Champs, faites glisser **Ventes** > **Ventes de cette année** > **Valeur** vers la zone **Taille**. 
   
   ![](media/power-bi-visualization-scatter/pbi_scatter_chart_size.png)
2. Pointez sur une bulle.  La taille de la bulle reflète la valeur de la zone **Ventes de cette année**.
   
    ![](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)
3. Si vous le souhaitez, [mettez en forme les couleurs, étiquettes, titres, arrière-plan, etc. de la visualisation](service-getting-started-with-color-formatting-and-axis-properties.md).

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
### <a name="your-scatter-chart-has-only-one-data-point"></a>**Votre nuage de points a un seul point de données**
Votre nuage de points a-t-il uniquement un point de données qui regroupe toutes les valeurs sur les axes X et Y ?  Ou regroupe-t-il toutes les valeurs le long d’une unique ligne horizontale ou verticale ?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Ajoutez un champ à la zone **Détails** pour indiquer à Power BI comment regrouper les valeurs. Le champ doit être unique pour chaque point à tracer.  
Comme un simple numéro de ligne ou un champ ID :

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Ou, si vous n’en avez pas dans vos données, créez un champ qui concatène les valeurs X et Y pour les convertir en élément unique par point :

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Pour créer un champ, [utilisez l’éditeur de requête Power BI Desktop pour ajouter une colonne d’index](desktop-add-custom-column.md) à votre jeu de données.  Ajoutez ensuite cette colonne à la zone **Détails** de la visualisation.

## <a name="next-steps"></a>Étapes suivantes
 [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Essayez-le gratuitement !](https://powerbi.com/)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

