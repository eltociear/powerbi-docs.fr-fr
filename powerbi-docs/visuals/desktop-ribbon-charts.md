---
title: Utiliser des graphiques de ruban dans Power BI
description: Créer et utiliser des graphiques de ruban dans le service Power BI et dans Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 08a2de32b092ba24b66ddd9f173be1eaea8819ab
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61394467"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Utiliser des graphiques de ruban dans Power BI
Vous pouvez utiliser des graphiques de ruban pour visualiser des données et rapidement découvrir la catégorie de données qui a le rang le plus élevé (valeur la plus grande). Les graphiques de ruban sont efficaces pour l’affichage de changements de rangs, la plage (valeur) la plus élevée étant toujours affichée en première position pour chaque période de temps. 

![graphique de ruban](media/desktop-ribbon-charts/ribbon-charts_01.png)

## <a name="create-a-ribbon-chart"></a>Créer un graphique de ruban
Pour suivre la procédure, ouvrez l’[exemple de rapport d’analyse de la vente au détail](../sample-retail-analysis.md). 

1. Pour créer un graphique de ruban, sélectionnez **Graphique de ruban** dans le volet **Visualisations**.

    ![modèles de visualisation](media/desktop-ribbon-charts/ribbon-charts_02.png)

    Les graphiques de ruban connectent une catégorie de données sur toute la période visualisée à l’aide des rubans, ce qui permet de voir comment une catégorie donnée se classe tout le long de l’axe X du graphique (généralement la chronologie).

2. Sélectionner des champs pour l’**axe**, la **légende** et la **valeur**.  Dans cet exemple, nous avons utilisé : **Date**, **Category** et **This year sales**.  

    ![champs sélectionnés](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Comme le jeu de données contient des données pour une seule année, nous avons aussi supprimé le champ **Année** de l’**axe**. 

3. Le graphique de ruban indique le rang pour tous les autres mois. Notez l’évolution du rang dans le temps.  Par exemple, la catégorie Home passe du troisième au quatrième, pour ensuite revenir au troisième. La catégorie Juniors passe du troisième au cinquième en juillet. 

    ![graphique de ruban](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Mettre en forme un graphique de ruban
Lorsque vous créez un graphique de ruban, vous avez accès aux options de mise en forme disponibles dans la section **Format** du volet **visualisations**. Les options de mise en forme des graphiques de ruban sont similaires à celles des histogrammes empilés, mais comprennent des options supplémentaires spécifiques des rubans.

![modèle de ruban dans le volet de visualisation](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Les options suivantes de mise en forme des graphiques de ruban vous permettent d’apporter des ajustements :

* **Espacement** permet d’ajuster l’espace entre les rubans. Le nombre correspond à un pourcentage de la hauteur maximale de la colonne.
* **Faire correspondre la couleur de la série** permet d’assortir la couleur des rubans avec celle de la série. Si cette option est **désactivée**, les rubans sont gris.
* **Transparence** spécifie le degré de transparence des rubans, la valeur par défaut étant définie sur 30.
* **Bordure** permet de placer une bordure sombre en haut et en bas des rubans. Par défaut, les bordures sont désactivées.

Comme le graphique de ruban n’a pas d’étiquettes sur l’axe Y, vous pouvez ajouter des étiquettes de données. Dans le volet Mise en forme, sélectionnez **Étiquettes de données**. 

![options de mise en forme pour les étiquettes de données](media/desktop-ribbon-charts/power-bi-labels.png)

Définissez les options de mise en forme de vos étiquettes de données.  Dans cet exemple, nous avons défini la couleur du texte sur blanc, le nombre de décimales sur zéro et les unités d’affichage sur les milliers. 

![modèle de ruban dans le volet de visualisation](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Étapes suivantes

[Nuages de points et graphiques en bulles dans Power BI](power-bi-visualization-scatter.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)