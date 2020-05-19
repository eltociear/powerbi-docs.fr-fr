---
title: Exemples de visuels Power BI
description: Cet article présente des exemples de visuels Power BI, notamment des segments, plus de 20 types de graphiques, WebGL et des visuels et scripts R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132501"
---
# <a name="samples-of-power-bi-visuals"></a>Exemples de visuels Power BI

Vous pouvez télécharger, utiliser et modifier ces visuels Power BI à partir de GitHub. Ces exemples montrent comment gérer les situations courantes lors du développement avec Power BI.

## <a name="slicers"></a>Segments

Un segment réduit la partie des données affichées dans d’autres visualisations d’un rapport. Les segments sont une des différentes façons de filtrer les données dans Power BI.

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Segment Chiclet](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Afficher des boutons représentant une image ou du texte qui font office de filtres dans la zone de dessin sur d'autres visuels | [Timeline slicer](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Sélecteur de plage de dates graphique qui filtre par date | [Exemple de sélecteur](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Illustre l’utilisation de l’API de filtrage avancé

## <a name="charts"></a>Graphiques

Inspirez-vous de notre galerie, qui comprend des graphiques à barres, des graphiques à secteurs, des nuages de mots et autres.

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [Traçage Aster](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Variante du graphique en anneau standard, avec une deuxième valeur qui définit l'angle de balayage | [Graphique à cible](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Graphique à barres avec des éléments visuels supplémentaires pour fournir davantage de contexte, utile pour le suivi d'objectifs | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Méthode graphique qui affiche les relations entre les données dans une matrice
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [Graphique à points](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Montrer la distribution des fréquences avec style | [Dual KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Visualiser efficacement deux mesures dans le temps, en indiquant leur tendance sur une chronologie mixte | [Enhanced Scatter](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Améliorations apportées au graphique à nuages de points existant
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [Graphique de force](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Diagramme de disposition des forces avec des trajectoires courbes, utile pour montrer les connexions entre des entités | [Diagramme de Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Un graphique à barres qui illustre la chronologie ou la planification d'un projet avec des ressources | [Carte thermique Table](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Comparer de manière simple et intuitive les données d'une table en utilisant des couleurs
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [Histogramme](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualizes the distribution of data over a continuous interval or certain time period | [LineDot Chart](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Graphique en courbes avec des points animés qui retournent un public avec des données | [Graphique Mekko](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Combinaison d'un histogramme empilé et d'un graphique à barres empilées dans une seule et même vue
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Multi KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Visualisation de plusieurs indicateurs de performance clés avec plusieurs sparklines de données de soutien | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Puissant indicateur de performance clé avec graphique multiligne et étiquettes pour la date, la valeur et les écarts actuels | [Matrice des indicateurs de performance clé Power](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Surveiller des cartes de performances équilibrées et un nombre illimité de métriques et d’indicateurs de performance clés dans une liste compacte et facile à lire
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [Graphique de pulsations](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Ce graphique en courbes annoté avec des événements clés est parfait pour indiquer les récits avec des données| [Graphique en radar](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Présente le traçage de plusieurs mesures sur un axe de catégorie, ce qui est utile pour comparer des attributs | [Graphique de Sankey](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Diagramme de flux où la largeur de la série est proportionnelle à la quantité du flux
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [Graphique de flux](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Graphique en aires empilées avec interpolation fluide souvent utilisé pour afficher des valeurs dans le temps | [Graphique en rayons de soleil](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Graphique en anneau à plusieurs niveaux permettant de visualiser les données hiérarchiques| [Graphique en tornade](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Comparaison de l'importance relative des variables entre deux groupes
 | <img src="media/samples/word-cloud.png" width="200">
 | [Nuage de mots](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Créer un visuel amusant à partir de texte fréquent dans vos données

## <a name="webgl"></a>WebGL

WebGL permet au contenu web d’utiliser une API basée sur OpenGL ES 2.0 pour effectuer un rendu 2D et 3D dans un canevas HTML.

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Carte du monde](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Tracer des emplacements sur une carte 3D interactive

## <a name="r-visuals"></a>Visuels R

Ces exemples montrent comment tirer parti de la puissance d’analyse et visuelle des visuels R et des scripts R.

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [Règles d’association](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Découvrir des relations entre des données apparemment non liées à l’aide d’instructions if-then | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Rechercher des groupes de similarités dans vos données à l’aide d’un algorithme k-moyennes | [Clustering avec valeurs hors norme](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Rechercher des groupes de similarités et des valeurs hors norme dans vos données
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [Traçage de corrélation](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Mettre en surbrillance les variables les plus corrélées dans une table de données | [Graphique d’arbre de décision](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Diagramme schématique en forme d’arborescence permettant de déterminer la probabilité statistique à l’aide d’un partitionnement récursif | [Forecasting TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Prévisions de série chronologique pour les séries qui ont plusieurs saisonnalités à l’aide du modèle TBATS
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Forecasting with ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Prédire des valeurs futures sur la base des données historiques à l’aide de la moyenne mobile intégrée autorégressive (ARIMA) | [Graphique en entonnoir](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Trouvez des valeurs hors norme dans vos données à l'aide d'un graphique en entonnoir | [Détection des valeurs hors norme](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Rechercher les valeurs hors norme dans vos données à l’aide de la méthode et du tracé les plus appropriés
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [Graphique en courbes](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Visualiser et comprendre les données bruyantes | [Graphique de décomposition de série temporelle](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Comprendre les composants de série chronologique à l’aide de « Seasonal and Trend decomposition using Loess » | [Graphique de prévisions de série chronologique](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Using exponential smoothing model to predict future values based on previously observed values

## <a name="next-steps"></a>Étapes suivantes

Pour essayer la création de visuels Power BI, consultez le [Didacticiel : Développement d’un visuel Power BI](custom-visual-develop-tutorial.md)
