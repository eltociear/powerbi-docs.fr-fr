---
title: "Explorer une visualisation dans Power BI"
description: Ce document montre comment explorer une visualisation dans le service Microsoft Power BI et Power BI Desktop.
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: MNAaHw4PxzE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: 22dc1c9b703b500625a5aed23b6187fd3f616dde
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>Explorer une visualisation dans Power BI
## <a name="drill-down-requires-a-hierarchy"></a>La fonction de descente dans la hiérarchie nécessite une hiérarchie
Quand un visuel a une hiérarchie, vous pouvez l’explorer pour révéler des détails supplémentaires. Par exemple, vous pouvez avoir une visualisation qui examine le nombre de médailles olympiques avec une hiérarchie constituée de sports, disciplines et événements. Par défaut, la visualisation indique le nombre de médailles olympiques par sport (gymnastique, ski, sports aquatiques, etc.). Mais, comme elle possède une hiérarchie, en sélectionnant un des éléments visuels (par exemple une barre, une ligne ou des bulles), elle affiche une image encore plus détaillée. Sélectionnez l’élément **aquatics** (sports aquatiques) afin d’afficher les données relatives à la natation, la plongée et le water polo.  Sélectionnez l’élément **diving** (plongée) pour afficher les détails relatifs au plongeoir, à la plateforme et aux événements de plongeon synchronisé.

Vous pouvez ajouter des hiérarchies aux rapports que vous possédez mais pas à ceux partagés avec vous.
Vous ne savez pas quelles visualisations Power BI contiennent une hiérarchie ?  Passez la souris sur une visualisation. Si vous voyez ces contrôles de descente dans la hiérarchie dans les angles supérieurs, la visualisation a une hiérarchie.

![](media/power-bi-visualization-drill-down/power-bi-drill-icon4.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon3.png)
![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) ![](media/power-bi-visualization-drill-down/power-bi-drill-icon6.png)  

Les dates sont un type unique de hiérarchie. Quand vous ajoutez un champ de date à une visualisation, Power BI ajoute automatiquement une hiérarchie de temps qui inclut l’année, le trimestre, le mois et le jour. Pour plus d’informations, consultez [Hiérarchies visuelles et comportement d’exploration](guided-learning/visualizations.yml#step-18) ou regardez la vidéo ci-dessous.

  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Pour savoir comment créer des hiérarchies à l’aide de Power BI Desktop, regardez la vidéo [Comment créer et ajouter des hiérarchies](https://youtu.be/q8WDUAiTGeU).
> 
> 

## <a name="two-methods-to-drill-down"></a>Deux méthodes d’exploration
Il existe deux méthodes pour descendre (et monter) dans la hiérarchie de votre visualisation.  Les deux sont décrites dans cet article. Les deux méthodes permettent d’accomplir la même chose : utilisez celle que vous appréciez le plus.

> [!NOTE]
> Pour suivre la procédure, [ouvrez l’exemple Analyse de la vente au détail](sample-datasets.md) dans le service Power BI et créez un graphique de compartimentage qui examine le **Nombre total d’unités cette année** (Valeurs) par **Secteur**, **Ville**, **Code postal** et **Nom** (groupe).  
> 
> 

## <a name="method-1-for-drill-down"></a>Méthode 1 pour descendre dans la hiérarchie
Cette méthode utilise les icônes de descente dans la hiérarchie qui apparaissent dans les angles supérieurs de la visualisation elle-même.

1. Dans Power BI, ouvrez un rapport en [mode Lecture ou en mode Édition](service-reading-view-and-editing-view.md). Pour pouvoir explorer une visualisation, celle-ci doit comporter une hiérarchie. 
   
   Une hiérarchie vous est présentée dans l’animation ci-dessous.  La visualisation a une hiérarchie constituée de secteurs, de villes, de codes postaux et de noms de ville. Chaque secteur a une ou plusieurs villes, chaque ville a un ou plusieurs codes postaux, etc. Par défaut, la visualisation affiche uniquement les données relatives au secteur, car le *secteur* (Territory) apparaît en premier dans la liste.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Pour activer l’exploration, sélectionnez l’icône de flèche dans l’angle supérieur droit de la visualisation. Une fois que l’icône est sombre, l’exploration est activée. Si vous n’activez pas la descente dans la hiérarchie, la sélection d’un élément visuel (par exemple une barre ou une bulle) effectue un filtrage croisé des autres graphiques sur la page de rapport.    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. Pour explorer ***un champ à la fois***, cliquez sur un des éléments de la visualisation : dans un graphique à barres, cliquez sur une des barres et dans un graphique à compartimentage, cliquez sur l’une des *feuilles*. Notez que le titre change à mesure que vous explorez puis revenez en arrière. Dans cette animation, il passe de « Total Units This Year by Territory » (Nombre total d’unités cette année par secteur) à « Total Units This Year by Territory and City » (Nombre total d’unités cette année par secteur et ville) à « Total Units This Year by Territory, City and PostalCode » (Nombre total d’unités cette année par secteur, ville et code postal) à « Total Units This Year by Territory, City, PostalCode, and Name » (Nombre total d’unités cette année par secteur, ville, code postal et nom). Par ailleurs, pour remonter d’un niveau, sélectionnez l’icône **Monter dans la hiérarchie** ![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png)dans l’angle supérieur gauche de la visualisation, comme indiqué ci-dessous.
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. Pour explorer ***tous les champs à la fois***, sélectionnez la flèche double dans l’angle supérieur gauche de la visualisation.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. Pour remonter d’un niveau, sélectionnez la flèche orientée vers le haut dans l’angle supérieur gauche de la visualisation.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-2-for-drill-down"></a>Méthode 2 pour descendre dans la hiérarchie
Cette méthode utilise la liste déroulante **Explorer** dans la barre de menus supérieure de Power BI.

1. Dans Power BI, ouvrez un rapport en [mode Lecture ou en mode Édition](service-reading-view-and-editing-view.md). Pour pouvoir explorer une visualisation, celle-ci doit comporter une hiérarchie. 
   
   Une hiérarchie vous est présentée dans l’image ci-dessous.  La visualisation a une hiérarchie constituée de secteurs, de villes, de codes postaux et de noms de ville. Chaque secteur a une ou plusieurs villes, chaque ville a un ou plusieurs codes postaux, etc. Par défaut, la visualisation affiche uniquement les données relatives au secteur, car le *secteur* (Territory) apparaît en premier dans la liste.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Pour activer la descente dans la hiérarchie, sélectionnez une visualisation pour l’activer, puis dans la barre de menus Power BI en haut, sélectionnez **Explorer** > **Descendre dans la hiérarchie**. L’icône de descente dans la hiérarchie située dans l’angle supérieur droit de la visualisation a alors un arrière-plan noir. ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. Après activation, descendez dans la hiérarchie d’un champ à la fois en sélectionnant l’une des feuilles du graphique de compartimentage. Dans cet exemple, j’ai sélectionné le secteur nommé **NC** pour afficher le nombre total d’unités vendues cette année en Caroline du Nord par ville.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. Pour explorer tous les champs à la fois, sélectionnez **Explorer** > **Afficher le niveau suivant**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. Pour remonter dans la hiérarchie, sélectionnez **Explorer** > **Monter dans la hiérarchie**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)
6. Pour voir les données utilisées pour créer l’élément visuel, sélectionnez **Voir les données**. Les données s’affichent dans un volet sous l’élément visuel. Ce volet reste affiché pendant que vous continuez d’explorer l’élément visuel. Pour plus d’informations, consultez [Afficher les données utilisées pour créer le visuel](service-reports-show-data.md).

## <a name="considerations-and-limitations"></a>Considérations et limitations
* Si l’ajout d’un champ de date à une visualisation ne crée pas de hiérarchie, c’est peut-être que le champ « date » n’est pas bien enregistré en tant que date. Si vous êtes le propriétaire du jeu de données, ouvrez-le dans la vue *Données* dans Power BI Desktop, sélectionnez la colonne qui contient la date, puis sous l’onglet Modélisation, définissez **Type de données** sur **Date** ou **Date/Heure**. Si le rapport a été partagé avec vous, contactez le propriétaire pour lui demander d’effectuer la modification.  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Étapes suivantes
[Visualisations dans des rapports Power BI](power-bi-report-visualizations.md)

[Rapports Power BI](service-reports.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

