---
title: Partie 2, Ajouter des visualisations à un rapport Power BI
description: Partie 2, Ajouter des visualisations à un rapport Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 5c3f98635d188aa1857be9c8d8e36dc296339ad7
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34292222"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>Partie 2, Ajouter des visualisations à un rapport Power BI
Dans la [partie 1](power-bi-report-add-visualizations-ii.md), vous avez créé une visualisation de base en cochant les cases en regard des noms de champs.  Dans la partie 2, vous allez apprendre à utiliser le glisser-déplacer et tirer pleinement parti des volets **Champs** et **Visualisations** pour créer et modifier des visualisations.

### <a name="prerequisites"></a>Conditions préalables
- [Partie 1](power-bi-report-add-visualizations-ii.md)
- Service Power BI - Il est possible d’ajouter des visualisations à des rapports à l’aide du service Power BI et de Power BI Desktop. Ce didacticiel utilise le service Power BI. 
- Retail Analysis sample

## <a name="create-a-new-visualization"></a>Créer une visualisation
Dans ce didacticiel, nous allons explorer notre jeu de données Analyse de vente au détail et créer quelques visualisations clés.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Ouvrez un rapport et ajoutez une nouvelle page vierge.
1. Ouvrez l’espace de travail dans lequel vous avez enregistré l’exemple Analyse de la vente au détail. Sélectionnez **Exemple Analyse de la vente au détail** pour ouvrir le rapport en mode Lecture.
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-report.png)
2. Sélectionnez **Modifier le rapport** pour ouvrir le rapport en Mode Edition.
   
   ![](media/power-bi-report-add-visualizations-ii/editreport1.png)
3. [Ajoutez une nouvelle page](power-bi-report-add-page.md) en sélectionnant l’icône représentant un signe « + » de couleur jaune au bas du canevas.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_addreportpage.png)

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Ajoutez une visualisation qui compare les ventes de cette année à celles de l’année dernière.
1. Dans la table **Sales** (Ventes), sélectionnez **This Year Sales** (Ventes de cette année) > **Value** (Valeur) **et Last Year Sales** (Ventes de l’année dernière). Power BI crée un histogramme.  Vous trouvez cela intéressant et vous voulez faire une exploration plus approfondie. Qu’en est-il des ventes par mois ?  
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_4bnew.png)
2. À partir de la table de temps, faites glisser **Mois** dans la zone **Axe**.  
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_5newnew.png)
3. [Changez la visualisation](power-bi-report-change-visualization-type.md) en graphique en aires.  Vous avez le choix entre plusieurs types de visualisation. Consultez [les descriptions, les bonnes pratiques et les didacticiels](power-bi-visualization-types-for-reports-and-q-and-a.md) liés à chaque type pour déterminer celui à utiliser. Dans le volet Visualisations, sélectionnez l’icône de graphique en aires.
4. Triez la visualisation en sélectionnant les points de suspension, puis en choisissant **Trier par mois**.
5. [Redimensionnez la visualisation](power-bi-visualization-move-and-resize.md) en sélectionnant la visualisation, en saisissant l’un des cercles de contour et en le faisant glisser. Élargissez-la suffisamment de façon à éliminer la barre de défilement, mais pas trop de sorte qu’il reste suffisamment de place pour ajouter une autre visualisation.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Enregistrez le rapport](service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Ajouter une visualisation de type carte géographique qui présente les ventes par magasin
1. Dans la table **Store** (Magasin), sélectionnez **Territory**(Territoire). Power BI reconnaît que Territory correspond à un lieu et crée une visualisation Carte.  
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_8newnew.png)
2. Faites glisser **Total Stores** (Total des magasins) dans la zone Taille.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-add-visual-to-a-reportnew.png)
3. Ajoutez une légende.  Pour afficher les données par nom de magasin, faites glisser **Chain** (Chaîne) dans la zone Legend (Légende).  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-add-visual-to-a-report-3new.png)

## <a name="next-steps"></a>Étapes suivantes
* Pour plus d’informations sur le volet Champs, consultez [Découverte de l’éditeur de rapport](service-the-report-editor-take-a-tour.md).   
* Pour savoir comment filtrer et mettre en évidence vos visualisations, consultez [Filtres et mise en évidence dans les rapports Power BI](power-bi-reports-filters-and-highlighting.md).  
* En savoir plus sur les [visualisations dans les rapports Power BI](power-bi-report-visualizations.md).  
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

