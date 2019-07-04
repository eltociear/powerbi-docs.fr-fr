---
title: Graphiques en cascade dans Power BI
description: Graphiques en cascade dans Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408953"
---
# <a name="waterfall-charts-in-power-bi"></a>Graphiques en cascade dans Power BI

Les graphiques en cascade affichent un résultat cumulé à mesure que Power BI ajoute et soustrait des valeurs. Ces graphiques sont utiles pour comprendre de quelle façon une valeur initiale (par exemple, un revenu net) est affectée par une série de variations positives et négatives.

Grâce au codage par couleur des colonnes, vous repérez rapidement les hausses et les baisses. Les colonnes des valeurs initiales et finales [démarrer sur l’axe horizontal](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "démarrent généralement sur l’axe horizontal"), alors que les valeurs intermédiaires sont représentées par des colonnes flottantes. Les graphiques en cascade sont également appelés graphiques « bridge » (pont) en raison de leur forme.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Quand faut-il utiliser un graphique en cascade ?

Les graphiques en cascade sont conseillés pour :

* représenter les variations de la mesure sur plusieurs séries chronologiques ou des catégories différentes ;

* analyser les variations majeures qui ont un impact sur la valeur totale ;

* tracer le bénéfice annuel de votre société en affichant les différentes sources de revenus et indiquer le résultat net (gains ou pertes) ;

* illustrer l’évolution annuelle de l’effectif global de votre société ;

* visualiser vos revenus et vos dépenses par mois, et le solde courant de votre compte.

## <a name="prerequisites"></a>Conditions préalables

* Service Power BI ou Power BI Desktop

* Exemple de rapport Analyse de la vente au détail

## <a name="get-the-retail-analysis-sample-report"></a>Obtenir l’exemple de rapport Retail Analysis (Analyse de la vente au détail)

Ces instructions s’appliquent à l’exemple Analyse de la vente au détail. La création d’une visualisation nécessite des autorisations de modification du jeu de données et du rapport. Par chance, les exemples Power BI sont tous modifiables. Si quelqu’un partage un rapport avec vous, vous ne pourrez pas créer de visualisations dans les rapports. Pour suivre la procédure, obtenez l’[exemple de rapport Retail Analysis Sample (Analyse de la vente au détail)](../sample-datasets.md).

Une fois que vous obtenez le jeu de données **Retail Analysis Sample (Analyse de la vente au détail)** , vous pouvez commencer.

## <a name="create-a-waterfall-chart"></a>Créer un graphique en cascade

Vous allez créer un graphique en cascade qui affiche un écart sur les ventes (ventes estimées par rapport aux ventes réelles) par mois.

1. À partir de **Mon espace de travail**, sélectionnez l’onglet **Jeux de données** > **Créer un rapport**.

    ![Capture d’écran du menu Jeux de données > Créer un rapport.](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. Dans le volet **Champs**, sélectionnez **Ventes** > **Écart sur volume des ventes totales**.

   ![Capture d’écran du menu Ventes > Écart sur volume des ventes totales sélectionné et du visuel qui en résulte.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Sélectionnez l’icône cascade ![Capture d’écran de l’icône cascade](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) pour convertir le graphique en treemap.

    Si **Total Sales Variance** (Écart sur volume des ventes totales) ne figure pas dans la zone **Axe Y** , faites-le glisser vers cette zone.

    ![Modèles de visualisation](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. Sélectionnez **Time** > **FiscalMonth** (Période > Mois fiscal) pour l’ajouter à **Catégorie**.

    ![cascade](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Vérifiez que Power BI a trié le graphique en cascade dans l’ordre chronologique. Dans l’angle supérieur droit du graphique, sélectionnez les points de suspension (...).

    Vérifiez la présence d’un indicateur jaune à gauche des options **Tri croissant** et **MoisFiscal**

    ![Sélectionnez Trier par > MoisFiscal](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    Vous pouvez également examiner les valeurs de l’axe X et voir qu’elles apparaissent dans l’ordre de **Jan** à **Aoû**.

    Approfondissez un peu plus pour voir ce qui contribue le plus aux changements mois après mois.

1. Faites glisser **Magasin** > **Territoire** vers le compartiment **Répartition**.

    ![Affiche Magasin dans le compartiment Répartition](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Par défaut, Power BI ajoute les cinq premiers contributeurs aux augmentations ou diminutions par mois.

    ![Affiche Magasin dans le compartiment Répartition](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Nous ne nous intéressons qu’aux deux premiers contributeurs.

1. Dans le volet **Mise en forme**, sélectionnez **Répartition**, puis définissez **Décompositions maximales** sur **2**.

    ![Format > Décomposition](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    Un examen rapide révèle que les territoires de l’Ohio et de la Pennsylvanie sont les principaux contributeurs aux mouvements négatifs et positifs dans votre graphique en cascade.

    ![graphique en cascade](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    Le constat est intéressant. Les territoires de l’Ohio et de la Pennsylvanie ont-ils un tel impact parce que les ventes y sont beaucoup plus élevées que dans les autres territoires ? Vous pouvez vérifier cela.

1. Créons une carte présentant la valeur des ventes de cette année et les ventes de l’année dernière par territoire.

    ![plan rapproché sur la Pennsylvanie et l’Ohio](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    La carte étaie notre théorie. Elle révèle que ces deux territoires sont ceux qui ont réalisé le plus de ventes l’année dernière (taille des bulles) et cette année (ombrage des bulles).

## <a name="highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisé

Pour plus d’informations sur l’utilisation du volet **Filtres**, consultez [Ajouter un filtre à un rapport en mode Édition](../power-bi-report-add-filter.md).

La mise en surbrillance d’une colonne dans un graphique en cascade entraîne le filtrage croisé des autres visualisations sur la page du rapport, et inversement. Toutefois, la colonne **Total** ne déclenche pas la mise en surbrillance et ne répond pas à un filtrage croisé.

## <a name="next-steps"></a>Étapes suivantes

* [Modifier l’interaction des visuels dans un rapport Power BI](../service-reports-visual-interactions.md)

* [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
