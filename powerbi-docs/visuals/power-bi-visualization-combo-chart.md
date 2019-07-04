---
title: Graphique combiné dans Power BI
description: Ce tutoriel sur les graphiques combinés explique quand les utiliser et comment les créer dans le service Power BI et dans Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/23/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e4b7b4b336b376f6ccec0bc0fe56de107ab8bd09
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67124291"
---
# <a name="combo-chart-in-power-bi"></a>Graphique combiné dans Power BI

Dans Power BI, un graphique combiné est une visualisation qui combine un graphique en courbes et un histogramme. Cette combinaison des deux graphiques vous permet de comparer plus rapidement les données.

Les graphiques combinés peuvent avoir un ou deux axes Y.

## <a name="when-to-use-a-combo-chart"></a>Quand faut-il utiliser un graphique combiné ?

Les graphiques combinés sont conseillés :

* Quand vous avez un graphique en courbes et un histogramme avec le même axe X.

* Pour comparer plusieurs mesures avec des plages de valeurs différentes.

* Pour illustrer la corrélation entre deux mesures dans la même visualisation.

* Pour vérifier si une mesure correspond à la cible qui est définie par une autre mesure.

* Pour utiliser moins d’espace sur le canevas.

## <a name="prerequisites"></a>Conditions préalables

Les graphiques combinés sont disponibles dans le service Power BI et dans Power BI Desktop. Ce tutoriel utilise le service Power BI pour créer un graphique combiné. Vérifiez que vous disposez des informations d’identification de l’utilisateur pour vous connecter à Power BI.

Regardez comment créer un graphique combiné à l’aide de l’exemple Vente et marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

## <a name="create-a-basic-single-axis-combo-chart"></a>Créez un graphique combiné simple, avec un seul axe

Pour effectuer la procédure, connectez-vous au service Power BI et sélectionnez l’**exemple Analyse de la vente au détail**. Pour créer votre propre graphique combiné, connectez-vous au service Power BI et sélectionnez **Obtenir des données**  > **Exemples** > **Exemple Analyse de la vente au détail** > **Connecter**. Le tableau de bord **Exemple Analyse de la vente au détail** s’affiche.

1. Dans le tableau de bord « Exemple Analyse de la vente au détail », sélectionnez la vignette **Total Stores** (Total magasins) pour ouvrir le rapport **Vue d’ensemble des ventes des magasins**.

1. Sélectionnez **Modifier le rapport** pour ouvrir le rapport en Mode Edition.

1. Au bas de la page, sélectionnez **+** pour ajouter une nouvelle page au rapport.

1. Créez un histogramme qui montre les ventes de cette année et la marge brute mensuelle.

    1. Dans le volet Champs, sélectionnez **Sales** \> **This Year Sales** > **Value** (Ventes > Ventes de cette année >Valeur).

    1. Faites glisser **Sales** \> **Gross Margin This Year** (Ventes > Marge brute cette année) vers **Valeur**.

    1. Sélectionnez **Time** \> **FiscalMonth** (Période > Mois fiscal) pour l’ajouter à **Axe**.

        ![Capture d’écran de l’histogramme nouvellement créé.](media/power-bi-visualization-combo-chart/combotutorial1new.png)

1. Sélectionnez les points de suspension (...) dans le coin supérieur droit de la visualisation, puis sélectionnez **Trier par > FiscalMonth**. Pour modifier l’ordre de tri, sélectionnez les points de suspension à nouveau et choisissez **Tri croissant** ou **Tri décroissant**.

1. Convertissez l’histogramme en graphique combiné. Deux graphiques combinés sont disponibles : **Graphique en courbes et histogramme empilé** et **Graphique en courbes et histogramme groupé**. Après avoir sélectionné l’histogramme, ouvrez le volet **Visualisations** et sélectionnez **Graphique en courbes et histogramme groupé**.

    ![Capture d’écran du volet des visualisations avec l’option de graphique en courbes et d’histogramme.](media/power-bi-visualization-combo-chart/converttocombo_new2.png)

1. À partir du volet **Champs**, faites glisser **Sales**  >  **Last Year Sales** (Ventes > Ventes de l’année dernière) vers **Valeurs de ligne**.

    ![Capture d’écran des valeurs des courbes après y avoir fait glisser les ventes de l’année dernière.](media/power-bi-visualization-combo-chart/linevaluebucket.png)

    Votre graphique combiné doit ressembler à ceci :

    ![Capture d’écran de l’histogramme avec la valeur de la courbe des ventes de l’an dernier ajoutée.](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Créer un graphique combiné avec deux axes

Dans cette tâche, nous allons comparer les ventes et la marge brute.

1. Créez un graphique en courbes qui affiche le **pourcentage de marge brute de l’année précédente** par **mois**. Sélectionnez les points de suspension pour le trier par **mois** et dans l’ordre **croissant**.

    ![Capture d’écran du nouveau graphique en courbes.](media/power-bi-visualization-combo-chart/combo1_new.png)

     En janvier, la marge brute était de 35 %. Elle a subi un pic à 45 % en avril, a baissé en juillet et a augmenté à nouveau en août. Verrons-nous un modèle similaire dans les ventes de l’année dernière et de cette année ?

1. Ajoutez **This Year Sales** >  **Value** (Ventes de l’année > Valeur) et **Last Year Sales** (Ventes de l’année dernière) au graphique en courbes. L’échelle utilisée pour **Gross Margin Last Year %** (Pourcentage de marge brute de l’année précédente) est beaucoup plus petite que l’échelle pour **Sales** (Ventes). Une comparaison est difficile.

    ![Capture d’écran du graphique en courbes avec la valeur et les ventes de l’année dernière ajoutées.](media/power-bi-visualization-combo-chart/flatline_new.png)

1. Pour faciliter la lecture et l’analyse de la visualisation, convertissez le graphique en courbes en un graphique en courbes et histogramme empilé.

    ![Capture d’écran du volet de visualisation avec l’icône du graphique en courbes et de l’histogramme empilé.](media/power-bi-visualization-combo-chart/converttocombo_new.png)

1. Faites glisser **Gross Margin Last Year %** (Pourcentage de marge brute de l’année précédente) de **Valeurs de colonne** vers **Valeurs de ligne**. 

    ![Capture d’écran du graphique en courbes et de l’histogramme empilé](media/power-bi-visualization-combo-chart/power-bi-combochart.png)

    Power BI crée deux axes, ce qui permet au service de mettre différemment à l'échelle les jeux de données. Le montant des ventes est mesuré à gauche et le pourcentage à droite. Et nous voyons la réponse à notre question : Oui, nous voyons un modèle similaire.

## <a name="add-titles-to-the-axes"></a>Ajouter des titres aux axes

1. Sélectionnez l’icône de rouleau de peinture ![Capture d’écran de l’icône de rouleau de peinture.](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) pour ouvrir le volet Mise en forme.

1. Sélectionnez la flèche déroulante pour développer les options de l’ **axe Y** .

1. Pour **Axe y (colonne)** , sélectionnez ces options :

    | Paramètre | Valeur |
    | ------- | ----- |
    | Position | Sélectionnez **Gauche**. |
    | Unités d’affichage | Sélectionnez **Millions**. |
    | Titre | Déplacez le curseur sur **Activé**. |
    | Style | Sélectionnez **Afficher uniquement le titre**. |
    | Afficher l’élément secondaire | Déplacez le curseur sur **Activé**.  Cela montre les options de mise en forme de la partie graphique en courbes du graphique combiné. |

1. Pour **Axe y (ligne)** , sélectionnez ces options :

    | Paramètre | Valeur |
    | ------- | ----- |
    | Position | Sélectionnez **Droite**. |
    | Titre | Déplacez le curseur sur **Activé**. |
    | Style | Sélectionnez **Afficher uniquement le titre**. |

    Votre graphique combiné affiche maintenant les deux axes, chacun avec un titre.

    ![Capture d’écran du graphique en courbes et de l’histogramme empilé avec les titres activés.](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

1. Si vous le souhaitez, modifiez la police, la taille et la couleur de texte et définissez d’autres options de mise en forme pour améliorer l’affichage et la lisibilité du graphique.

À ce stade, vous souhaiterez effectuer les tâches suivantes :

* [Ajoutez le graphique combiné sous forme de vignette de tableau de bord](../service-dashboard-tiles.md).

* [Enregistrez le rapport](../service-report-save.md).

* [Rendez les rapports plus accessibles aux personnes handicapées](../desktop-accessibility.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisés

La mise en surbrillance d’une colonne ou d’une ligne dans un graphique combiné entraîne la mise en surbrillance et le filtrage croisés des autres visualisations sur la page du rapport. Utilisez le contrôle [Interactions entre les visuels](../service-reports-visual-interactions.md) pour modifier ce comportement par défaut.

## <a name="next-steps"></a>Étapes suivantes

[Graphiques en anneau dans Power BI](power-bi-visualization-doughnut-charts.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)