---
title: Graphiques en jauge radiale dans Power BI
description: Graphiques en jauge radiale dans Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e783b4357d4db39e09aabbb1df39e1bb5c84532e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880901"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Graphiques en jauge radiale dans Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un graphique en jauge radiale est en forme d’arc de cercle. Il affiche une seule valeur qui mesure la progression vers un objectif/indicateur de performance clé (KPI). La ligne (ou *aiguille*) représente l’objectif ou la valeur cible. L’ombrage représente la progression vers cet objectif. La valeur à l’intérieur de l’arc représente la valeur de la progression. Power BI répartit toutes les valeurs possibles uniformément le long de l’arc, de la valeur minimale (la plus à gauche) à la valeur maximale (la plus à droite).

![Capture d’écran de la jauge radiale.](media/power-bi-visualization-radial-gauge-charts/gauge-m.png)

Dans cet exemple, vous êtes un concessionnaire automobile et effectuez le suivi de la moyenne des ventes mensuelles réalisées par votre équipe de vente. L’aiguille correspond à un objectif de ventes de 140 véhicules. La moyenne minimale de ventes mensuelles possible est 0 et la moyenne maximale a été définie à 200.  L’ombrage bleu indique que l’équipe a atteint une moyenne de 120 ventes ce mois-ci. Heureusement, il reste encore une semaine pour atteindre l’objectif fixé.

Vous pouvez écouter Will qui vous montre comment créer des éléments visuels de métrique uniques : jauges, cartes et indicateurs de performance clés.
   > [!NOTE]
   > Cette vidéo utilise une version antérieure de Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Quand faut-il utiliser un graphique en jauge radiale ?

Les graphiques en jauge radiale sont conseillés pour :

* montrer la progression vers un objectif ;

* représenter une mesure en centiles, comme un indicateur de performance clé ;

* montrer l’intégrité d’une seule mesure ;

* montrer des informations faciles à analyser et à comprendre.

## <a name="prerequisites"></a>Prérequis

Ce tutoriel utilise le [fichier Excel d’exemple financier](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Dans la section supérieure gauche de la barre de menus, sélectionnez **Obtenir les données** > **Excel**.
   
2. Trouver votre copie de l’**du fichier Excel d’exemple financier**

1. Ouvrez le **fichier Excel d’exemple financier** dans la vue Rapport ![Capture d’écran de l’icône Vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionnez **financials** (données financières) et **Feuil1**

1. Cliquez sur **Charger**

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.



## <a name="create-a-basic-radial-gauge"></a>Créer une jauge radiale simple

### <a name="step-1-create-a-gauge-to-track-gross-sales"></a>Étape 1 : Créer une jauge pour effectuer le suivi du chiffre d’affaires brut

1. Démarrer sur une page de rapport vide

1. Dans le volet **Champs** , sélectionnez **Gross Sales** (Chiffre d’affaires brut).

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue-new.png)

1. Changez l’agrégation en **Moyenne**.

   ![Capture d’écran du volet Champs avec le chiffre d’affaires brut et la valeur moyenne globale.](media/power-bi-visualization-radial-gauge-charts/changetoaverage-new.png)

1. Sélectionnez l’icône jauge ![Capture d’écran de l’icône jauge.](media/power-bi-visualization-radial-gauge-charts/gaugeicon-new.png) pour convertir l’histogramme en un graphique en jauge.

    ![Capture d’écran du graphique en jauge.](media/power-bi-visualization-radial-gauge-charts/gauge-no-target.png)

    Selon le moment où vous téléchargez le fichier **Financial Sample** (exemple financier), les valeurs affichées peuvent ne pas correspondre à ces chiffres.

    > [!TIP]
    > Par défaut, Power BI crée un graphique en jauge où la valeur actuelle (dans cet exemple, le **chiffre d’affaires brut moyen**) est présumée être au milieu de la jauge. La valeur du **chiffre d’affaires brut moyen** étant de 182 760 $, la valeur de départ (Minimum) est définie sur 0 et la valeur de fin (Maximum) est définie sur le double de la valeur actuelle.

### <a name="step-3-set-a-target-value"></a>Étape 3 : Sélectionner la valeur cible

1. Faites glisser **COGS** du volet **Champs** vers le puits **Valeur cible** .

1. Changez l’agrégation en **Moyenne**.

   Power BI ajoute une aiguille pour représenter la valeur cible **145 480 $** .

   ![Capture d’écran du graphique en jauge avec la moyenne du coût des produits vendus ajoutée.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress-new.png)

    Comme vous pouvez le remarquer, l’objectif a même été dépassé.

   > [!NOTE]
   > Vous pouvez également entrer manuellement une valeur cible. Consultez la section [Utiliser les options de mise en forme pour définir manuellement les valeurs Minimum, Maximum et Cible](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Étape 4 : Définir une valeur maximale

Dans l’étape 2, Power BI a utilisé le champ **Valeur** pour définir automatiquement une valeur minimale et une valeur maximale. Comment définir votre propre valeur maximale ? Supposons qu’au lieu de définir la valeur maximale possible au double de la valeur actuelle, vous souhaitez la définir au chiffre d’affaires brut le plus élevé dans votre jeu de données.

1. Faites glisser **Gross Sales** (Chiffre d’affaires brut) du volet **Champs** vers le puits **Valeur maximale** .

1. Changez l’agrégation en **Maximum**.

   ![Capture d’écran du volet Champs avec le chiffre d’affaires brut et la valeur maximale globale.](media/power-bi-visualization-radial-gauge-charts/setmaximum-new.png)

   La jauge est redessinée avec une nouvelle valeur de fin (1,21 million de chiffre d’affaires brut).

   ![Capture d’écran du graphique en jauge terminé.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Étape 5 : Enregistrer votre rapport

1. [Enregistrez le rapport](../service-report-save.md).

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Utiliser les options de mise en forme pour définir manuellement les valeurs Minimum, Maximum et Cible

1. Supprimez **Max of Gross Sales** (Chiffre d’affaires brut maximum) de **Valeur maximale** .

1. Sélectionnez l’icône en forme de rouleau pour ouvrir le volet **Mise en forme**.

   ![Capture d’écran du graphique en jauge et du volet Mise en forme avec l’icône en forme de rouleau.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Développez l’**axe de la jauge** et entrez des valeurs pour **Min** et **Max**.

    ![Capture d’écran des options de l’axe de la jauge.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Effacez l’option **COGS** dans le volet **champs** pour supprimer la valeur cible.

    ![Capture d’écran de l’option COGS effacée.](media/power-bi-visualization-radial-gauge-charts/pbi-remove-target.png)

1. Lorsque le champ **Cible** apparaît sous **Axe de la jauge**, entrez une valeur.

     ![Capture d’écran des options de l’axe de la jauge avec la cible affichée.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Éventuellement, continuez la mise en forme de votre graphique de type Jauge.

Une fois que vous avez terminé ces étapes, vous disposez d’un graphique en jauge qui ressemble à ceci :

![Capture d’écran du graphique en jauge final.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Étape suivante

* [Visuels d’indicateur de performance clé (KPI)](power-bi-visualization-kpi.md)

* [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
