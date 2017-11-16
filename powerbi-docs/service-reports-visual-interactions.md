---
title: "Modifier l’interaction des éléments visuels dans un rapport"
description: "Documentation pour savoir comment définir des interactions d’éléments visuels dans un rapport Microsoft Power BI."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 126bd40e98a88138a2732155f9792d65666e52c7
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>Interactions avec les visualisations dans un rapport Power BI
Par défaut, vous pouvez utiliser les visualisations d’une page de rapport pour filtrer et mettre en évidence les autres visualisations de la page. On parle alors de « filtrage croisé » et de « mise en évidence croisée ».
Par exemple, si vous sélectionnez un état sur une visualisation de carte, l’histogramme est mis en évidence et le graphique en courbes est filtré pour afficher uniquement les données qui s’appliquent à cet état.
Consultez [À propos du filtrage et de la mise en évidence](power-bi-reports-filters-and-highlighting.md).

Pour modifier ce comportement par défaut, utilisez le contrôle **Interaction visuelle**. Les interactions visuelles sont disponibles uniquement en [mode Édition](service-interact-with-a-report-in-editing-view.md). Si un rapport a été partagé avec vous, vous n’avez pas accès aux interactions visuelles.

> [!NOTE]
> Les termes *filtrage croisé* et *sélection croisée* permettent de distinguer le comportement décrit ici de celui qui résulte de l’utilisation du volet **Filtres** pour filtrer et mettre en évidence des visualisations.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Sélectionnez une visualisation pour l’activer.  
2. Activez le contrôle **Interactions avec l’élément visuel** en le sélectionnant dans la barre de menus supérieure. Notez les icônes de filtre et de mise en évidence qui apparaissent lorsque vous passez le curseur au-dessus des autres visualisations de la page de rapport.
   
    ![](media/service-reports-visual-interactions/pbi-visual-interaction-icon.png)
3. Déterminez l’impact de la visualisation sélectionnée sur les autres visualisations.  
   
   * Si elle doit filtrer l’autre visualisation (« filtrage croisé »), sélectionnez l’icône **filtre** ![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Si elle doit mettre en évidence cette visualisation (« mise en évidence croisée »), sélectionnez l’icône **mise en évidence** ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Si elle n’a aucun impact, sélectionnez l’icône **aucun impact** ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).
4. (Facultatif) Répétez cette opération pour toutes les autres visualisations dans la page de rapport.

### <a name="next-steps"></a>Étapes suivantes
[Utilisation des filtres de rapport](power-bi-how-to-report-filter.md)

[Filtres et mise en évidence dans les rapports](power-bi-reports-filters-and-highlighting.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

