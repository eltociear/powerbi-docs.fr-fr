---
title: "Obtenir des informations rapides dans Power BI"
description: "Documentation pour l’exécution et l’utilisation d’Informations rapides avec le service Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: et_MLSL2sA8
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/01/2017
ms.author: mihart
ms.openlocfilehash: 8b069f29737992817d20396007864cc8c005ca99
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="quick-insights-with-power-bi"></a>Informations rapides avec Power BI
Vous disposez d’un jeu de données et vous ne savez pas par quoi commencer ?  Vous voulez créer rapidement un tableau de bord ?  Vous souhaitez rechercher rapidement des informations que vous auriez manquées ?

Exécutez un aperçu rapide pour générer des visualisations interactives intéressantes basées sur vos données. Les Informations rapides peuvent être exécutées sur un jeu de données entier (Informations rapides) ou sur une vignette de tableau de bord spécifique (Informations rapides avec étendue). Vous pouvez même exécuter la fonction Informations rapides sur une information.

> **Remarque** : les informations rapides ne fonctionnent pas avec DirectQuery (seulement avec les données chargées sur Power BI).
> 
> 

La fonctionnalité d’aperçu rapide repose sur un [ensemble d’algorithmes analytiques avancées](service-insight-types.md) développés conjointement avec Microsoft Research que nous continuerons d’utiliser pour permettre à plus de personnes de tirer des enseignements de leurs données de façon innovante et intuitive.

## <a name="run-quick-insights-on-a-dataset"></a>Exécuter Informations rapides sur un jeu de données
Regardez Amanda exécuter la fonction Informations rapides sur un jeu de données, ouvrir une information en mode Focus, épingler l’une de ces Informations rapides en tant que vignette à son tableau de bord, et obtenir des Informations rapides sur un visuel.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Maintenant, à vous de jouer. Explorez les informations rapides en vous appuyant sur l’[exemple Analyse de la qualité des fournisseurs](sample-supplier-quality.md).

1. Sous l’onglet **Jeux de données**, sélectionnez les points de suspension (…) puis choisissez **Obtenir des informations**.
   
    ![](media/service-insights/power-bi-ellipses.png)
   
    ![](media/service-insights/power-bi-tab.png)
2. Power BI utilise [différents algorithmes](service-insight-types.md) pour rechercher des tendances dans votre jeu de données.
   
    ![](media/service-insights/pbi_autoinsightssearching.png)
3. En quelques secondes, vos informations sont prêtes.  Sélectionnez **Afficher les informations** pour afficher des visualisations.
   
    ![](media/service-insights/pbi_autoinsightsuccess.png)
   
   > **REMARQUE** : certains jeux de données ne peuvent pas générer d’Informations rapides perce que les données ne sont pas significatives d’un point de vue statistique.  Pour en savoir plus, consultez [Optimisez vos données pour en avoir un aperçu rapide dans Power BI](service-insights-optimize.md).
   > 
   > 
4. Les visualisations s’affichent dans une zone de dessin **Informations rapides** spéciale comprenant jusqu’à 32 cartes d’information distinctes. Chaque carte possède un graphique et une brève description.
   
    ![](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-quick-insight-cards"></a>Interagir avec les cartes d’informations rapides
  ![](media/service-insights/pbi_hover.png)

1. Pointez le curseur sur une carte, puis sélectionnez l’icône en forme d’épingle pour ajouter la visualisation à un tableau de bord.
2. Pointez le curseur sur une carte, puis sélectionnez l’icône du mode Focus pour afficher la carte en plein écran.
   
    ![](media/service-insights/power-bi-insight-focus.png)
3. Dans le mode Focus, vous pouvez :
   
   * [Filtrer](service-interact-with-a-report-in-reading-view.md) les visualisations.  Pour afficher les filtres, dans l’angle supérieur droit, sélectionnez la flèche pour développer le volet Filtres.
     
        ![](media/service-insights/power-bi-insights-filter-new.png)
   * Épinglez la carte d’information à un tableau de bord en sélectionnant l’icône Épingler ![](media/service-insights/power-bi-pin-icon.png) ou l’option **Épingler un élément visuel**.
   * Exécuter Informations rapides sur la carte elle-même. C’est ce que l’on appelle des **informations rapides avec étendue**. Dans l’angle supérieur droit, sélectionnez l’icône Ampoule ![](media/service-insights/power-bi-bulb-icon.png) ou l’option **Obtenir des informations**.
     
       ![](media/service-insights/pbi-autoinsights-tile.png)
     
     L’Information rapide s’affiche à gauche, et les nouvelles cartes basées uniquement sur les données de cette Information rapide s’affichent à droite.
     
       ![](media/service-insights/power-bi-insights-on-insights-new.png)
4. Pour revenir au canevas Informations rapides d’origine, dans le coin supérieur gauche, sélectionnez **Quitter le mode focus**.

## <a name="run-quick-insights-on-a-dashboard-tile"></a>Exécuter Informations rapides sur une vignette de jeu de données
Au lieu de rechercher des informations dans un jeu de données complet, limitez votre recherche aux données ayant servi à créer une vignette de tableau de bord. C’est ce que l’on appelle des  **avec étendue**.

1. Ouvrez un tableau de bord.
2. Sélectionnez une vignette puis [ouvrez-la en mode Focus](service-focus-mode.md).
3. En haut à droite, sélectionnez **Obtenir des informations**.
   
    ![](media/service-insights/pbi-autoinsights-tile.png)
4. Power BI affiche les cartes d’informations sur le côté droit de la vignette.
   
    ![](media/service-insights/pbi-insights-tile.png)
5. Une information suscite votre intérêt ? Sélectionnez la carte d’informations pour en savoir plus. L’Information rapide sélectionnée s’affiche à gauche, et les nouvelles cartes d’information basées uniquement sur les données de cette Information rapide s’affichent à droite.
6. Continuez à explorer vos données, puis, dès que vous trouvez une Information rapide intéressante, épinglez son visuel à votre tableau de bord en sélectionnant **Épingler un élément visuel** dans l’angle supérieur droit. Vous pouvez également formuler un commentaire pour faire savoir au propriétaire du jeu de données si une Information rapide a été utile ou non.
   
    ![](media/service-insights/useful.png)

## <a name="next-steps"></a>Étapes suivantes
Si vous possédez un jeu de données, [optimisez-le pour la fonction Informations rapides](service-insights-optimize.md).

Découvrez les [types d’Informations rapides disponibles](service-insight-types.md).

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

