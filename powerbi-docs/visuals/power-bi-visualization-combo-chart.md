---
title: Graphique combiné dans Power BI
description: Ce didacticiel sur les graphiques combinés explique quand les utiliser et comment les créer dans le service Power BI et dans Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5d2a33b8dc50a4a30bb79406462f1342953528d9
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2018
ms.locfileid: "52830375"
---
# <a name="combo-chart-in-power-bi"></a>Graphique combiné dans Power BI
Dans Power BI, un graphique combiné est une visualisation qui combine un graphique en courbes et un histogramme. Combiner ces deux graphiques en un seul vous permet de comparer plus rapidement les données.

Les graphiques combinés peuvent avoir un ou deux axes Y.

## <a name="when-to-use-a-combo-chart"></a>Quand faut-il utiliser un graphique combiné ?
Les graphiques combinés sont conseillés :

* quand vous avez un graphique en courbes et un histogramme avec le même axe X ;
* pour comparer plusieurs mesures avec des plages de valeurs différentes ;
* pour illustrer la corrélation entre deux mesures dans la même visualisation ;
* pour vérifier si une mesure correspond à la cible qui est définie par une autre mesure ;
* pour utiliser moins d’espace sur le canevas.

### <a name="prerequisites"></a>Conditions préalables
Les graphiques combinés sont disponibles dans le service Power BI et dans Power BI Desktop. Ce didacticiel utilise le service Power BI pour créer un graphique combiné. Pour effectuer la procédure, connectez-vous au service Power BI et sélectionnez l’exemple Analyse de la vente au détail [instructions ci-dessous](#create)).


## <a name="create-a-basic-single-axis-combo-chart"></a>Créer un graphique combiné simple, avec un seul axe
Regardez comment créer un graphique combiné à l’aide de l’exemple Vente et marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a>Pour créer votre propre graphique combiné, connectez-vous au service Power BI et sélectionnez **Obtenir des données \> Exemples \> Exemple Analyse de la vente au détail > Se connecter > Accéder au tableau de bord**.

1. Dans le tableau de bord « Exemple Analyse de la vente au détail », sélectionnez la vignette **Total Stores** (Total magasins) pour ouvrir le rapport « Exemple Analyse de la vente au détail ».
2. Sélectionnez **Modifier le rapport** pour ouvrir le rapport en Mode Edition.
3. Ajoutez une nouvelle page au rapport.
4. Créez un histogramme qui affiche les ventes de cette année et la marge brute mensuelle.

    a.  Dans le volet Champs, sélectionnez **Sales** \> **This Year Sales** > **Value** (Ventes > Ventes de cette année >Valeur).

    b.  Faites glisser **Sales** \> **Gross Margin This Year** (Ventes > Marge brute cette année) vers **Valeur**.

    c.  Sélectionnez **Time** \> **FiscalMonth** (Période > Mois fiscal) pour l’ajouter à **Axe**.

    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Sélectionnez les points de suspension (...) dans le coin supérieur droit de la visualisation, puis sélectionnez **Trier par > MoisFiscal**. Pour modifier l’ordre de tri, sélectionnez les points de suspension à nouveau et choisissez **Tri croissant** ou **Tri décroissant**.

6. Convertissez l’histogramme en graphique combiné. Deux graphiques combinés sont disponibles : **Ligne et histogramme empilé** et **Ligne et histogramme groupé**. Après avoir sélectionné l’histogramme, ouvrez le volet **Visualisations** et sélectionnez **Graphique en courbes et histogramme groupé**.

    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. À partir du volet **Champs**, faites glisser **Sales** \> **Last Year Sales** (Ventes > Ventes de l’année dernière) vers **Valeurs de ligne**.

   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   Votre graphique combiné doit ressembler à ceci :

   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Créer un graphique combiné avec deux axes
Dans cette tâche, nous allons comparer les ventes et la marge brute.

1. Créez un graphique en courbes qui affiche le **pourcentage de marge brute de l’année précédente** par **mois**. Sélectionnez les points de suspension pour le trier par **mois** et dans l’ordre **croissant**.  
En janvier, la marge brute était de 35 %. Elle a subi un pic à 45 % en avril, a baissé en juillet et a augmenté à nouveau en août. Verrons-nous un modèle similaire dans les ventes de l’année dernière et de cette année ?

   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Ajoutez **This Year Sales > Value** (Ventes de l’année > Valeur) et **Last Year Sales** (Ventes de l’année dernière) au graphique en courbes. L’échelle utilisée pour **Gross Margin Last Year %** (Pourcentage de marge brute de l’année précédente) est beaucoup plus petite que l’échelle pour **Sales** (Ventes), ce qui rend difficile la comparaison des données.      

   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Pour faciliter la lecture et l’analyse de la visualisation, convertissez le graphique en courbes en un graphique en courbes et histogramme empilé.

   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Faites glisser **Gross Margin Last Year %** (Pourcentage de marge brute de l’année précédente) de **Valeurs de colonne** vers **Valeurs de ligne**. Power BI crée deux axes, ce qui permet de définir des échelles différentes pour les jeux de données. L’axe de gauche mesure le montant des ventes et l’axe de droite mesure le pourcentage. Et nous voyons la réponse à notre question : oui, nous notons un modèle similaire.

   ![](media/power-bi-visualization-combo-chart/power-bi-combochart.png)    

## <a name="add-titles-to-the-axes"></a>Ajouter des titres aux axes
1. Ouvrez le volet de mise en forme en sélectionnant l’icône en forme de rouleau ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png).
2. Sélectionnez la flèche déroulante pour développer les options de l’ **axe Y** .
3. Pour l’**axe Y (colonne)**, définissez les valeurs suivantes : **Position** sur **Gauche**, **Titre** sur **Activé**, **Style** sur **Afficher le titre uniquement** et **Afficher** sur **Millions**.

   ![](media/power-bi-visualization-combo-chart/power-bi-y-axis-column.png)
4. Sous l’**axe Y (colonne)**, faites défiler et vérifiez également que **Afficher l’élément secondaire** a la valeur **Activé**. Cela affiche les options de mise en forme de la partie graphique en courbes du graphique combiné.

   ![](media/power-bi-visualization-combo-chart/power-bi-show-secondary.png)
5. Pour l’**axe Y (ligne)**, laissez **Position** sur **Droite**, définissez **Titre** sur **Activé** et **Style** sur **Afficher le titre uniquement**.

   Le graphique combiné affiche maintenant les deux axes, chacun avec un titre.

   ![](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

6. Si vous le souhaitez, modifiez la police, la taille et la couleur de texte et définissez d’autres options de mise en forme pour améliorer l’affichage et la lisibilité du graphique.

À ce stade, vous souhaiterez effectuer les tâches suivantes :

* [Ajoutez le graphique combiné sous forme de vignette de tableau de bord](../service-dashboard-tiles.md).
* [Enregistrez le rapport](../service-report-save.md).
* [Rendez les rapports plus accessibles aux personnes handicapées](../desktop-accessibility.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisés

La mise en surbrillance d’une colonne ou d’une ligne dans un graphique combiné entraîne la mise en surbrillance et le filtrage croisés des autres visualisations sur la page du rapport, et vice versa. Utilisez le contrôle [Interactions entre les visuels](../service-reports-visual-interactions.md) pour modifier ce comportement par défaut.

## <a name="next-steps"></a>Étapes suivantes

[Graphiques en anneau dans Power BI](power-bi-visualization-doughnut-charts.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
