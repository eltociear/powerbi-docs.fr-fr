---
title: "Interagir avec un rapport en mode Lecture dans Power BI"
description: "Interagir avec un rapport en mode Lecture dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/15/2017
ms.author: mihart
ms.openlocfilehash: 54de712e0743801b3e8c565ca997bbc56e254c69
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="interact-with-a-report-in-reading-view-in-power-bi"></a>Interagir avec un rapport en mode Lecture dans Power BI
## <a name="reading-view"></a>Mode Lecture
Si le mode de lecture n’est pas aussi interactif que le [mode de modification](service-interact-with-a-report-in-editing-view.md), il offre de nombreuses options pour l’exploration des données. Cela peut s’avérer pratique pour l’affichage des rapports [partagés avec vous](service-share-dashboards.md) qui ne peuvent être ouverts qu’en mode de lecture.

Le mode lecture est un cadre amusant et une méthode sûre pour jouer et vous familiariser avec vos données. En mode Lecture vous pouvez mettre en surbrillance et filtrer en réticules plusieurs éléments visuels sur une page.  Il vous suffit de mettre en surbrillance ou de sélectionner une valeur dans l’un des visuels pour voir instantanément son impact sur les autres. Utilisez le volet Filtre pour ajouter et modifier des filtres sur une page de rapport et modifier la manière dont les valeurs sont triées dans une visualisation. Les filtrages ou mises en surbrillance que vous effectuez ne sont pas enregistrés avec le rapport.

## <a name="cross-highlight-the-related-visualizations-on-a-page"></a>Mettre en surbrillance en réticules les visualisations connexes sur une page
Les visualisations situées sur une même page de rapport sont toutes « connectées » les unes aux autres.  Cela signifie que si vous sélectionnez une ou plusieurs valeurs dans une visualisation, les autres visualisations qui utilisent la même valeur changent en fonction de cette sélection.

![](media/service-interact-with-a-report-in-reading-view/pagefilter3b.gif)

> [!NOTE]
> Pour sélectionner plusieurs éléments dans une visualisation, maintenez la touche Ctrl enfoncée.
> 
> 

## <a name="hover-over-visual-elements-to-see-the-details"></a>Pointez la souris sur les éléments visuels pour afficher les détails les concernant
![](media/service-interact-with-a-report-in-reading-view/amarillachart.png)

## <a name="sort-the-data-in-a-visualization"></a>Trier les données d’une visualisation
Sélectionnez les points de suspension (...) pour ouvrir le menu **Trier par**. Sélectionnez la flèche déroulante pour choisir le champ à trier ou sélectionnez l’icône AZ pour basculer de l’ordre croissant à l’ordre décroissant. 

![](media/service-interact-with-a-report-in-reading-view/pbi_changechartsort.gif) 

## <a name="interact-with-filters"></a>Interagir avec les filtres
Si l’auteur d’un rapport a ajouté des filtres à une page du rapport, vous pouvez interagir avec ces filtres en mode Lecture. Les modifications que vous apportez ne seront pas être enregistrées avec le rapport.

1. Sélectionnez l’icône de filtre située dans l’angle supérieur droit.
   
   ![](media/service-interact-with-a-report-in-reading-view/filters.png)  
2. Vous voyez tous les filtres appliqués à l’élément visuel sélectionné (filtres des éléments visuels), sur l’ensemble de la page de rapport (filtres de pages) et sur l’ensemble de la page de rapport (filtres de rapports).
   
   ![](media/service-interact-with-a-report-in-reading-view/power-bi-reading-filters.png)
3. Pointez sur un filtre et développez-le en sélectionnant la flèche bas.
   
   ![](media/service-interact-with-a-report-in-reading-view/power-bi-expan-filter.png)
4. Modifiez les filtres et constatez l’impact sur les visuels.  
   
   * Dans cet exemple, nous avons un filtre au niveau de la page pour **Chain**. Définissez-le sur **Fashions Direct** au lieu de **Lindseys** en désactivant l’un pour activer l’autre.
     
     ![](media/service-interact-with-a-report-in-reading-view/power-bi-filter-chain.png)
   * Vous pouvez également supprimer complètement le filtrage sur **Chain** en sélectionnant l’icône de gomme ![](media/service-interact-with-a-report-in-reading-view/power-bi-eraser-icon.png) ou les deux magasins de chaîne.
   * Sélectionnez le filtre au niveau de la page **District** et basculez sur **Filtrage avancé**. Définissez un filtre qui permet d’afficher uniquement les districts qui commencent par **FD** et qui ne contiennent pas le chiffre 4.
     
     ![](media/service-interact-with-a-report-in-reading-view/power-bi-advanced-filter.png)

Pour plus d’informations, consultez [Add a filter to a report (Ajouter un filtre à un rapport)](power-bi-report-add-filter.md) et [About filters and highlighting in reports (À propos des filtres et de la mise en surbrillance dans les rapports)](power-bi-reports-filters-and-highlighting.md)

## <a name="zoom-in-on-individual-visuals"></a>Zoom avant sur des éléments visuels individuels
Pointez sur l’élément visuel, puis sélectionnez l’icône du **Mode Focus** ![](media/service-interact-with-a-report-in-reading-view/pbi_popouticon.jpg). Lorsque vous ouvrez une visualisation en mode Focus, celle-ci se développe de manière à occuper entièrement la zone de dessin du rapport, comme illustré ci-dessous.

![](media/service-interact-with-a-report-in-reading-view/powerbi-focus-mode.png)

Pour afficher cette même visualisation sans les barres de menus, le volet des filtres et autres éléments superflus, sélectionnez l’icône **Plein écran** dans la barre de menus supérieure ![](media/service-interact-with-a-report-in-reading-view/power-bi-focus-icon.png).

![](media/service-interact-with-a-report-in-reading-view/power-bi-full-screen.png)

Pour en savoir plus, voir [Mode focus pour les rapports](service-focus-mode.md) et [Mode plein écran pour les rapports](service-fullscreen-mode.md).

## <a name="adjust-the-display-dimensions"></a>Ajuster les dimensions d’affichage
Les rapports peuvent être affichés sur différents appareils dont les tailles d’écran et les proportions peuvent varier.  Le rendu par défaut peut ne pas vous convenir sur certains appareils.  Pour ajuster, sélectionnez **Vue** et choisissez :

* Ajuster à la page : ajustez le contenu à la page
* Ajuster à la largeur : ajustez le contenu à la largeur de la page
* Taille réelle : affichez le contenu à sa taille réelle  

![](media/service-interact-with-a-report-in-reading-view/power-bi-view.png)

  En mode Lecture, l’option d’affichage que vous sélectionnez est temporaire. Elle n’est pas enregistrée quand vous fermez le rapport.

  Pour en savoir plus, voir [Didacticiel sur la modification des paramètres d’affichage d’un rapport](power-bi-change-report-display-settings.md).

## <a name="next-steps"></a>Étapes suivantes
[Rapports dans Power BI](service-reports.md)

[Ouvrir le mode Édition](service-reading-view-and-editing-view.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

