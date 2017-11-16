---
title: "Segments dans Power BI (didacticiel)"
description: "Didacticiel : Segments dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/30/2017
ms.author: mihart
ms.openlocfilehash: b6ce0c396f4a189489b97fe5cd86ab5cd8dbcc35
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="slicers-in-power-bi-service-tutorial"></a>Segments dans le service Power BI (didacticiel)
Votre responsable des ventes souhaite pouvoir examiner un certain nombre de mesures pour la division en entier, ainsi que pour chaque directeur régional. Elle peut soit créer une page de rapport distincte pour chaque directeur, soit utiliser un segment. Un segment réduit la partie du jeu de données affichée dans les autres visualisations de la page.  Les segments sont une autre méthode de filtrage.

![](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quand utiliser un segment
Les segments sont un bon choix dans les situations suivantes.

* Pour afficher des filtres couramment utilisés ou importants sur le canevas de rapport afin de faciliter l’accès.
* Pour faciliter la détermination de l’état filtré actuel sans avoir à ouvrir une liste déroulante pour rechercher les détails du filtrage.
* Lorsque vous souhaitez masquer des colonnes dont vous n’avez pas besoin tout en pouvant continuer à les utiliser pour filtrer (cela permet d’obtenir des tables plus étroites et plus propres).
* Pour créer des rapports plus focalisés ; étant donné que les segments sont des objets flottants, vous pouvez les placer en regard de la partie intéressante du rapport sur laquelle vous souhaitez que vos utilisateurs se concentrent.

## <a name="create-a-slicer"></a>Création d’un segment
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>


1. Ouvrez l’[exemple Analyse de la vente au détail](sample-retail-analysis.md) en [Mode Édition](service-interact-with-a-report-in-editing-view.md) et [ajoutez une nouvelle page de rapport](power-bi-report-add-page.md).
2. Dans le volet Champs, sélectionnez **District > Directeur de district**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_chartfirst.png)
3. Convertissez la visualisation en segment. Dans le volet Visualisations, sélectionnez l’icône de segment.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_select.png)

## <a name="format-the-slicer"></a>Mettre en forme le segment
1. Une fois le segment sélectionné, dans le volet Visualisations, sélectionnez l’icône en forme de rouleau ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) pour afficher les options de mise en forme.
2. Sélectionnez **Général > Couleur de contour**, puis choisissez le bleu foncé et définissez la valeur **Épaisseur** sur **6**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_outline2.png)
3. Sous **Contrôles de sélection**, par défaut, **Sélectionner tout** est **Désactivé** et **Sélection unique** est **Activé**. Cela signifie que je dois utiliser la touche CTRL pour sélectionner plusieurs noms à la fois. Définissez **Sélectionner tout** sur **Activé** et **Sélection unique** sur **Désactivé**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_selectioncontrols2.png)
   
   * Notez que le segment a maintenant une option **Sélectionner tout** en haut de la liste. Activez ou désactivez **Sélectionner tout** pour sélectionner tous les noms ou n’en sélectionner aucun.
   * Vous pouvez à présent sélectionner plusieurs noms sans avoir à utiliser la touche CTRL.
4. Sous **Éléments**, faites passer la taille du texte à 14pt.  Nous voulons être certains que nos collègues remarquent ce segment.
5. Enfin, définissez la valeur de **Couleur de police** sur rouge foncé.  Cela permet de distinguer les noms sélectionnés des noms non sélectionnés dans notre segment.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_font2.png)
6. Amusez-vous à explorer les autres options disponibles pour les segments.

## <a name="use-the-slicer-in-a-report"></a>Utilisation du segment dans un rapport
1. Ajoutez des visualisations supplémentaires à la page du rapport ou ouvrez l’[exemple de rapport Retail Analysis](sample-retail-analysis.md) et sélectionnez l’onglet **District Monthly Sales** (Ventes mensuelles du district).
   
    ![](media/power-bi-visualization-slicers/power-bi-retail-sample.png)
2. Segmentez la page de rapport pour Carlos. Notez comment les autres visualisations s’actualisent pour refléter ces sélections.
   
    ![](media/power-bi-visualization-slicers/slicer2.gif)
3. Triez le segment dans l’ordre alphabétique par nom de Directeur de district.  Sélectionnez les points de suspension (...) dans le coin supérieur droit du segment, puis choisissez **Directeur de district**.
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sort2.png)
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sorted.png)

## <a name="control-what-effect-the-slicer-has-on-other-visuals-on-the-page"></a>Contrôler l’effet du segment sur les autres éléments visuels de la page
Voulez-vous que le segment filtre uniquement certains éléments visuels de la page de rapport ?  Utilisez la commande **Interactions avec l’élément visuel** pour définir cette option.

**REMARQUE** : si vous ne voyez pas **Interactions avec l’élément visuel**, recherchez son icône à la place ![](media/power-bi-visualization-slicers/power-bi-slicer-visual-interactions.png). Si vous ne la voyez pas non plus, vérifiez que vous êtes dans le rapport en [mode Édition](service-reading-view-and-editing-view.md).

1. Sélectionnez le segment pour l’activer, puis dans la barre de menu, choisissez **Interactions avec l’élément visuel**.
   
    ![](media/power-bi-visualization-slicers/pbi-slicer-interactions.png)
2. Les commandes de filtre s’affichent au-dessus de tous les autres éléments visuels de la page. Si le segment doit filtrer un élément visuel, sélectionnez l’icône **Filtre**.  Si le segment ne doit pas avoir d’effet sur l’élément visuel, sélectionnez l’icône **Aucun**.
   
    ![](media/power-bi-visualization-slicers/filter-controls.png)

Pour plus d’informations, consultez [Interactions avec un élément visuel dans un rapport Power BI](service-reports-visual-interactions.md).

## <a name="considerations-and-troubleshooting-slicers-in-power-bi"></a>Considérations et résolution des problèmes de segments dans Power BI
Il existe quelques limitations concernant l’utilisation de segments dans Power BI :

1. Les segments ne prennent pas en charge les champs d’entrée.
2. Un segment unique ne peut pas être utilisé dans l’intégralité d’un rapport. Un segment a uniquement une incidence sur la page actuelle.
3. Les segments ne peuvent pas être épinglés à un tableau de bord.
4. L’exploration n’est pas prise en charge pour les segments.    
5. Les segments ne prennent pas en charge les filtres de niveau visuel.

Avez-vous des idées pour améliorer Power BI ? [Soumettez une idée](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

## <a name="next-steps"></a>Étapes suivantes
 [Ajouter une visualisation à un rapport](power-bi-report-add-visualizations-i.md)

 [Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

 [Power BI – Concepts de base](service-basic-concepts.md)

[Essayez-le gratuitement !](https://powerbi.com/)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

