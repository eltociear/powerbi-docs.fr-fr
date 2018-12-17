---
title: Jeux de données volumineux, limites de point de données et stratégies de données
description: Limites des données pour les visuels et stratégies de réduction des données
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 125787bab3892f2e9616866a9d5487837131d0ed
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52981488"
---
# <a name="data-point-limits-and-strategies-by-visual-type"></a>Limites et stratégies par type de visuel du point de données

Lors du rendu d’un visuel dans Power BI, la visualisation doit être rapide et précise. Cela nécessite des algorithmes sous-jacents configurés pour chaque type de visuel. Les visuels dans Power BI doivent être suffisamment flexibles pour gérer différentes tailles de jeux de données. Certains jeux de données n’ont que peu de points de données, tandis que d’autres jeux de données ont plusieurs pétaoctets de points de données. Cet article explique les stratégies utilisées par Power BI pour afficher des visualisations.

## <a name="data-reduction-strategies"></a>Stratégies de réduction des données
Chaque visuel utilise une ou plusieurs *stratégies de réduction des données* afin de gérer les volumes potentiellement volumineux de données en cours d’analyse. Même une simple table utilise une stratégie pour éviter de charger l’intégralité du jeu de données sur le client.  La stratégie de réduction utilisée varie en fonction du type de visuel. Chaque visuel effectue une sélection dans les *stratégies de réduction des données* prises en charge dans le cadre de la génération de la demande de données envoyée au serveur. 

Chaque visuel contrôle les paramètres sur ces stratégies pour influencer la quantité globale de données.   

## <a name="strategies"></a>Stratégies
Pour chaque stratégie, il existe des valeurs par défaut en fonction de la forme et du type de données affichées. Mais les valeurs par défaut peuvent être remplacées, dans le volet Mise en forme de Power BI, pour fournir une expérience utilisateur appropriée. 

* **Fenêtrage des données** (Segmentation) : Permet aux utilisateurs de parcourir les données dans un visuel en chargeant progressivement les fragments du jeu de données global.
* **TopN** : Affiche uniquement les N premiers éléments
* **Exemple simple** : Affiche le premier élément, le dernier élément et N éléments répartis uniformément entre les deux.
* **BottomN** : Affiche les N derniers éléments.  Utile pour l’analyse des données fréquemment mises à jour.
* **Échantillonnage à haute densité** : algorithme d’échantillonnage amélioré qui respecte mieux les valeurs hors norme et/ou la forme d’une courbe.
    * **Échantillonnage de lignes placées dans un compartiment** : exemples de points de données basés sur des valeurs hors norme dans des compartiments sur un axe
    * **Échantillonnage de points se chevauchant** : exemples de points de données basés sur des valeurs se chevauchant pour conserver les valeurs hors norme

## <a name="statistics"></a>Statistiques
Certains modèles peuvent fournir des statistiques sur le nombre de valeurs pour certaines colonnes. Lorsque ces informations sont présentes, nous en tirons parti pour fournir un meilleur équilibrage sur plusieurs hiérarchies, si un visuel ne remplace pas explicitement le nombre de valeurs pour une stratégie.

Pour plus d’informations, consultez [Nouveautés dans Analysis Services](https://docs.microsoft.com/en-us/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017)

## <a name="dynamic-limits"></a>Limites dynamiques
Outre les stratégies ci-dessus, les visuels avec deux hiérarchies de colonnes de regroupement (axe et légende ou catégorie et série) utilisent une stratégie supplémentaire appelée *Limites dynamiques*.  Les limites dynamiques sont conçues pour mieux équilibrer les points de données. 

Les limites dynamiques fournissent une meilleure sélection de points pour les données éparses que les limites statiques. Par exemple, un visuel peut être configuré pour sélectionner 100 catégories et 10 séries avec un total de 1 000 points. Mais les données réelles contiennent 50 catégories et 20 séries.  Lors de l’exécution de la requête, les limites dynamiques sélectionnent les 20 séries pour remplir les 1 000 points demandés.

Les limites dynamiques sont appliquées automatiquement lorsque le serveur en est capable, comme indiqué ci-dessous :

* Dans Power BI Desktop avec SSAS local version 2016 ou ultérieure [exploitant les capacités SuperDax du serveur](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* Dans Desktop et le service Power BI lors de l’utilisation d’un modèle importé, de Direct Query, avec une connexion en temps réel au service ou une connexion en temps réel à AS PaaS. 

* Dans le service Power BI, lors de la connexion via une passerelle locale à un SAAS local, nous ne pouvons pas utiliser les limites dynamiques. La passerelle locale ne prend pas entièrement en charge la stratégie de limites dynamiques qui retourne une structure différente de jeux de résultats à partir du SSAS local.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Stratégies et limites par type de visuel du point de données

### <a name="area-chart"></a>Graphique en aires
Consultez [Fonctionnement de l’échantillonnage de ligne](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Graphique à barres/histogramme
- En mode par catégorie
    - Catégories : Virtualisation à l’aide d’une fenêtre de 500 lignes à la fois
    - Séries : 60 premières
    - En mode scalaire (qui peut utiliser les limites dynamiques)
        - Points max. : 10 000
        - Catégories : Exemple de 500 valeurs
        - Séries : 20 premières valeurs

### <a name="card-multirow"></a>Carte (plusieurs lignes) 
- Valeurs : Virtualisation à l’aide d’une fenêtre de 200 lignes à la fois

### <a name="combo-chart"></a>Graphique combiné
 Utilise les mêmes stratégies que l’histogramme. Notez que la ligne dans le **graphique combiné** n’utilise pas l’algorithme haute densité utilisé par le **graphique en courbes**.

### <a name="custom-visuals"></a>Visuels personnalisés
Peut aller jusqu’à 30 000 mais c’est aux auteurs du visuel d’indiquer les stratégies à utiliser

### <a name="doughnut"></a>Anneau
- Points max. : 3,500
- Groupe : 500 premiers
- Détails : 20 premiers

### <a name="filled-map-choropleth"></a>Carte choroplèthe (thématique) 
La carte choroplèthe peut utiliser les statistiques ou les limites dynamiques. Power BI essaie d’utiliser la réduction dans l’ordre suivant : limites dynamiques, statistiques et enfin, la configuration. 
- Points max. : 10 000
- Catégories : 500 premiers
- Séries (lorsque X et Y sont présents) : 20 premiers

### <a name="funnel"></a>Entonnoir
- Points max. : 3,500
- Catégories : 3 500 premiers

### <a name="kpi"></a>KPI
- Axe de tendance
- 3 500 derniers

### <a name="line-chart"></a>Graphique en courbes
Consultez [Fonctionnement de l’échantillonnage de ligne](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Graphique en courbes, haute densité
Consultez [Échantillonnage à haute densité](../desktop-high-density-sampling.md)

### <a name="map"></a>Carte 
- Points max. : 3,500

Selon la configuration, une carte peut avoir :
- Emplacement : 3 500 premiers
- Emplacement, taille : 3 500 premiers
- Agrégats d’emplacement, de latitude et de longitude (+/- taille) : 3 500 premiers
- Latitude, longitude : consultez [Nuages de points à haute densité](desktop-high-density-scatter-charts.md)
- Latitude, longitude, taille : 3 500 premiers
- Légende, latitude, longitude : consultez [Nuages de points à haute densité](desktop-high-density-scatter-charts.md)
- Légende, latitude, longitude, taille : 233 premières légendes, 15 premières latitudes et longitudes (possibilité d’utiliser les statistiques ou les limites dynamiques)
- Emplacement, légende, latitude, longitude en tant qu’agrégats (+/- taille) : 233 premiers emplacements, 15 premières légendes (possibilité d’utiliser les statistiques ou les limites dynamiques)

### <a name="matrix"></a>Matrice
- Lignes : Virtualisation à l’aide d’une fenêtre de 500 lignes à la fois
- Colonnes : 100 premières colonnes de regroupement 
- Valeurs : plusieurs valeurs n’entrent pas dans la réduction des données

### <a name="radial-gauge"></a>Jauge radiale
Aucune stratégie de réduction

### <a name="slicer"></a>Segment
- Valeurs : Virtualisation à l’aide d’une fenêtre de 200 lignes à la fois

### <a name="scatter-chart-high-density"></a>Graphique en nuage de points (haute densité)
Consultez [Nuages de points à haute densité](https://docs.microsoft.com/en-us/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Secteurs
- Points max. : 3,500
- Groupe : 500 premiers
- Détails : 20 premiers

### <a name="r--python-visuals"></a>Visuels R & Python
Limite de 150 000 lignes. Si plus de 150 000 lignes sont sélectionnées, seules les 150 000 premières lignes sont utilisées.

### <a name="ribbon-chart"></a>Graphique de ruban
- En mode par catégorie
    - Catégories : Virtualisation (fenêtrage de données) à l’aide d’une fenêtre de 500 lignes à la fois
    - Séries : 60 premières
    - En mode scalaire (qui peut utiliser les limites dynamiques)
        - Points max. : 10 000
        - Catégories : Exemple de 500 valeurs
        - Séries : 20 premières valeurs

### <a name="shape-map"></a>Carte de formes
La carte choroplèthe peut utiliser les statistiques ou les limites dynamiques. 
- Points max. : 10 000
- Catégories : 500 premiers
- Séries (lorsque X et Y sont présents) : 20 premiers

### <a name="table"></a>Tableau
- Valeurs : Virtualisation (fenêtrage de données) à l’aide d’une fenêtre de 500 lignes à la fois

### <a name="tree-map-this-could-use-statistics-or-dynamic-limits"></a>Arborescence (possibilité d’utiliser les statistiques ou les limites dynamiques)
- Points max. : 3,500
- Groupe : 500 premiers
- Détails : 20 premiers

### <a name="waterfall-chart"></a>Graphique en cascade
- Lorsqu’il n’y a qu’un seul compartiment de catégorie
    - Points max. : 3,500
    - Catégorie uniquement - 3 500 premières
- Lorsque la catégorie et la répartition sont présentes
    - Catégorie : Virtualisation (fenêtrage de données) à l’aide d’une fenêtre de 30 lignes à la fois
    - Répartition - 200 premières valeurs


## <a name="next-steps"></a>Étapes suivantes
[Types de visualisation](power-bi-report-visualizations.md)
