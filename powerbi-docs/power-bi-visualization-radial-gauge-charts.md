---
title: "Didacticiel - Graphiques jauge radiale dans Power BI"
description: "Didacticiel : graphiques en jauge radiale dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: xmja6Epqa
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/21/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5b0b5861c567997bb5636c4fe00085535debc8f2
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="radial-gauge-charts-in-power-bi-tutorial"></a>Jauges radiales dans Power BI (didacticiel)
Un graphique en jauge radiale est en forme d’arc de cercle. Il affiche une seule valeur qui mesure la progression vers un objectif/indicateur de performance clé.  L’objectif (valeur cible) est représenté par la ligne (aiguille). La progression vers l’objectif est représentée par l’ombrage.  La valeur représentant cette progression est indiquée en caractères gras à l’intérieur de l’arc. Toutes les valeurs possibles sont réparties uniformément le long de l’arc, de la valeur minimale (la plus à gauche) à la valeur maximale (la plus à droite).

Dans l’exemple ci-dessous, un concessionnaire automobile effectue le suivi de la moyenne des ventes mensuelles réalisées par son équipe de vente. L’objectif, représenté par l’aiguille noire, est d’atteindre 140 ventes.  La moyenne minimale de ventes mensuelles possible est 0 et la moyenne maximale a été définie à 200.  L’ombrage bleu indique une moyenne actuelle de 120 ventes ce mois-ci. Heureusement, il reste encore une semaine pour atteindre l’objectif fixé.

![](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

## <a name="when-to-use-a-radial-gauge"></a>Quand faut-il utiliser un graphique en jauge radiale ?
Les graphiques en jauge radiale sont conseillés pour :

* montrer la progression vers un objectif ;
* représenter une mesure en centiles, comme un indicateur de performance clé ;
* montrer l’intégrité d’une seule mesure ;
* afficher des informations faciles à comprendre et à analyser.

### <a name="prerequisites"></a>Conditions préalables
 - Service Power BI ou Power BI Desktop
 - Classeur Excel d’exemples financiers : [télécharger directement l’exemple](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Créer une jauge radiale simple
Ces instructions utilisent le service Power BI. Pour suivre la procédure, connectez-vous à Power BI et ouvrez le fichier Excel d’exemple financier.  

Vous pouvez également écouter Will qui vous montre comment créer des éléments visuels de métrique uniques : jauges, cartes et indicateurs de performance clés.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

### <a name="step-1-open-the-financial-sample-excel-file"></a>Étape 1 : Ouvrir le fichier Excel d’exemple financier
1. [Téléchargez le fichier Excel d’exemple financier](sample-financial-download.md) si ce n’est pas déjà fait. Notez l’endroit où vous l’enregistrez.

2. Ouvrez le fichier dans le ***service Power BI*** en sélectionnant **Obtenir des données \>Fichiers** et en accédant à l’emplacement où vous avez enregistré le fichier. Sélectionnez **Importer**. L’exemple financier est ajouté à votre espace de travail en tant que jeu de données.

3. Dans la liste de contenu **Jeu de données**, sélectionnez **Financial Sample** (Exemple financier) pour l’ouvrir en mode Exploration.

    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Étape 2 : créer une jauge pour effectuer le suivi du chiffre d’affaires brut
1. Dans le volet **Champs** , sélectionnez **Gross Sales**(Chiffre d’affaires brut).
   
   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)
2. Changez l’agrégation en **Moyenne**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)
3. Sélectionnez l’icône en forme de jauge ![](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) pour convertir l’histogramme en jauge.
   
   Par défaut, Power BI crée un graphique en jauge où la valeur actuelle (dans cet exemple, le chiffre d’affaires brut moyen) est présumée être au milieu de la jauge. Le chiffre d’affaires brut moyen étant de 182 760 $, la valeur de départ (Minimum) est définie sur 0 et la valeur de fin (Maximum) est définie sur le double de la valeur actuelle.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

### <a name="step-3-set-a-target-value"></a>Étape 3 : sélectionner la valeur cible
1. Faites glisser **COGS** vers **Valeur cible** .
2. Changez l’agrégation en **Moyenne**.
   Power BI ajoute une aiguille pour représenter la valeur cible **145 480 $**. Comme vous pouvez le remarquer, l’objectif a même été dépassé.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)
   
   > [!NOTE]
   > Vous pouvez également entrer manuellement une valeur cible.  Consultez « Utiliser les options de mise en forme pour définir manuellement les valeurs Minimum, Maximum et Cible » ci-dessous.
   > 
   > 

### <a name="step-4-set-a-maximum-value"></a>Étape 4 : définir une valeur maximale
Dans l’étape 2, Power BI a utilisé le champ Valeur pour définir automatiquement un minimum (valeur de départ) et un maximum (valeur de fin).  Comment faire pour définir votre propre valeur maximale ?  Supposons qu’au lieu de définir la valeur maximale possible au double de la valeur actuelle, vous souhaitez la définir au chiffre d’affaires brut le plus élevé dans votre jeu de données ? 

1. Faites glisser **Gross Sales** (Chiffre d’affaires brut) de la liste **Champs** vers **Valeur maximale** .
2. Changez l’agrégation en **Maximum**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)
   
   La jauge est redessinée avec une nouvelle valeur de fin (1,21 million de chiffre d’affaires brut).
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Étape 5 : enregistrer le rapport
1. [Enregistrez le rapport](service-report-save.md).
2. [Ajoutez le graphique en jauge sous forme de vignette de tableau de bord](service-dashboard-tiles.md). 

## <a name="use-formatting-options-to-manually-set-minimum-maximum-and-target-values"></a>Utilisez les options de mise en forme pour définir manuellement les valeurs Minimum, Maximum et Cible.
1. Supprimez **Max of Gross Sales** (Chiffre d’affaires brut maximum) de **Valeur maximale** .
2. Ouvrez le volet de mise en forme en sélectionnant l’icône en forme de rouleau.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)
3. Développez l’ **axe de la jauge** et entrez des valeurs pour **Min** et **Max**.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)
4. Supprimez la valeur cible actuelle en supprimant la coche à côté de **COGS**.
   
    ![](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)
5. Lorsque le champ **Cible** apparaît sous **Axe de la jauge**, entrez une valeur.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)
6. Éventuellement, continuez la mise en forme de votre graphique de type Jauge.

## <a name="next-steps"></a>Étapes suivantes
[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Ajouter une visualisation à un rapport](power-bi-report-add-visualizations-i.md)

[Épingler une visualisation à un tableau de bord](service-dashboard-pin-tile-from-report.md)

[Power BI - Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

