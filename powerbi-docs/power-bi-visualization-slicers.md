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
ms.date: 03/05/2018
ms.author: v-thepet
LocalizationGroup: Visualizations
ms.openlocfilehash: cfa4c0f17c67a036b7d01744da1b5247345c493a
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="slicers-in-power-bi-tutorial"></a>Segments dans Power BI (didacticiel)
Une responsable des ventes souhaite pouvoir examiner plusieurs métriques pour la division entière, ainsi que pour chaque directeur régional. Pour cela, elle peut soit créer un rapport distinct pour chaque directeur, soit utiliser un segment. Un segment réduit la partie du jeu de données affiché dans d’autres visualisations d’un rapport. Les segments sont une autre méthode de filtrage.

Ce didacticiel utilise l’exemple gratuit [Analyse de la vente au détail](sample-retail-analysis.md) pour vous expliquer pas à pas comment créer et mettre en forme un segment, puis comment l’utiliser pour filtrer les données d’un rapport. Amusez-vous à découvrir les différentes mises en forme et utilisations possibles des segments. 

![segment](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>Quand utiliser un segment
Les segments sont très utiles pour :

* Afficher les filtres couramment utilisés ou importants sur le canevas de rapport pour en faciliter l’accès.
* Déterminer plus rapidement l’état de filtrage actuel sans avoir à ouvrir une liste déroulante. 
* Filtrer les colonnes qui sont inutiles et masquées dans les tables de données.
* Créer des rapports plus ciblés en ajoutant des segments à côté des visuels importants.

Les segments Power BI présentent les limitations suivantes :

- Les segments ne prennent pas en charge les champs d’entrée.
- Les segments ne peuvent pas être épinglés à un tableau de bord.
- L’exploration n’est pas prise en charge pour les segments.
- Les segments ne prennent pas en charge les filtres au niveau des visuels.

## <a name="create-a-slicer"></a>Créer un segment

Ce didacticiel utilise un segment de liste. Les types de données numériques et de date/heure peuvent avoir des segments de plage. Pour plus d’informations sur la création et l’utilisation de segments de plage, consultez [Utiliser le sélecteur de plages numériques dans Power BI Desktop](desktop-slicer-numeric-range.md) ou regardez la vidéo suivante.
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>

1. Dans Power BI Desktop ou le service Power BI, ouvrez [l’exemple Analyse de la vente au détail](sample-retail-analysis.md) en [mode Édition](service-interact-with-a-report-in-editing-view.md) et [ajoutez une nouvelle page de rapport](power-bi-report-add-page.md).
2. Dans le volet Champs, sous District, sélectionnez **District Manager** pour créer une visualisation.
    
    ![nouveau graphique](media/power-bi-visualization-slicers/1-new-vis.png)
    
3. Sélectionnez l’icône **Segment** ![icône segment](media/power-bi-visualization-slicers/slicer-icon.png) dans le volet Visualisations pour convertir la nouvelle visualisation en segment. 
    
    ![convertir en segment](media/power-bi-visualization-slicers/2-slicer.png)

Vous pouvez également sélectionner l’icône Segment pour créer un segment, puis sélectionner ou faire glisser un champ de données dans la zone Champ pour la remplir.

>[!TIP]
>Vous pouvez trier les éléments du segment de liste en fonction des valeurs de données. Pour trier les éléments du segment dans l’ordre alphabétique inverse, sélectionnez les points de suspension (...) en haut à droite du segment et choisissez **Trier par District Manager**. Le tri s’effectue par ordre alphabétique croissant par défaut, mais vous pouvez basculer entre l’ordre croissant et l’ordre décroissant. 

## <a name="format-the-slicer"></a>Mettre en forme le segment
Appliquez la mise en forme souhaitée aux visuels du segment District Manager.
1. Une fois le segment sélectionné, dans le volet Visualisations, sélectionnez l’icône Format ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) pour afficher les commandes de mise en forme. 
    
    ![mise en forme](media/power-bi-visualization-slicers/3-format.png)
    
2. Cliquez sur les flèches de liste déroulante à côté de chaque catégorie pour afficher et modifier les options. 

### <a name="general-options"></a>Options générales
1. Sélectionnez la couleur rouge sous **Couleur du contour** et changez la valeur **Épaisseur du contour** à « 2 ». Ces options définissent la couleur et l’épaisseur des contours ou soulignements de l’en-tête et des éléments, quand ils sont activés. 
2. Sous Orientation, la valeur Verticale est sélectionnée par défaut. Ce paramètre crée un segment de liste vertical où les éléments sont précédés de zones de sélection. Sélectionnez **Horizontale** pour créer un segment où les éléments sont organisés horizontalement. L’orientation horizontale permet d’organiser le texte, les boutons ou les vignettes de diverses façons, en fonction de la taille et de la forme du segment ainsi que de la mise en forme des éléments. 
    
    ![horizontale](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Activez la disposition **Dynamique** pour adapter la taille et l’organisation des éléments d’un segment horizontal à la taille et à la forme du segment. Quand il devient très petit, le segment s’affiche sous forme d’icône de filtre. 
    
    ![dynamique](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >Les changements de disposition dynamique peuvent substituer la mise en forme spécifique du titre et des éléments que vous avez définie. 
    
4. Définissez la position et la taille du segment avec une précision numérique sous **Position X**, **Position Y**, **Largeur** et **Hauteur**, ou déplacez et redimensionnez le segment directement sur le canevas, pour créer des tailles et organisations d’éléments différentes, par exemple, une ligne horizontale de boutons. 

    ![boutons horizontaux](media/power-bi-visualization-slicers/6-buttons.png)

Pour plus d’informations sur l’orientation horizontale et la mise en forme dynamique, consultez [Créer un segment réactif que vous pouvez redimensionner dans Power BI](power-bi-slicer-filter-responsive.md).

### <a name="selection-controls-options"></a>Options sous Contrôles de sélection
1. L’option Afficher "Sélectionner tout" est désactivée par défaut. **Activez-la** pour ajouter un élément Sélectionner tout au segment qui sélectionne ou désélectionne tous les éléments, le cas échéant. Quand tous les éléments sont sélectionnés, il suffit de cliquer sur un élément pour le désélectionner. C’est un filtre de type « n’est pas ». 
    
    ![sélectionner tout](media/power-bi-visualization-slicers/7-select-all.png)
    
2. L’option Sélection simple est activée par défaut. Pour sélectionner un seul élément, vous devez cliquer dessus. Pour sélectionner plusieurs éléments, vous devez cliquer sur chaque élément en maintenant la touche Ctrl enfoncée. **Désactivez** l’option Sélection simple pour pouvoir sélectionner plusieurs éléments sans avoir à maintenir la touche Ctrl enfoncée. Le fait de recliquer sur un élément sélectionné le désélectionne. 

### <a name="header-options"></a>Options sous En-tête
L’en-tête est activé par défaut. Il affiche le nom du champ de données en haut du segment. 
1. Mettez en forme le texte de l’en-tête en définissant les options **Couleur de police** sur rouge, **Taille du texte** sur 14 points et **Famille de polices** sur Arial Noir. 
2. Sous Contour, choisissez **Seulement le bas** pour ajouter un soulignement de la taille et de la couleur que vous avez définies dans les options Général. 

### <a name="item-options"></a>Options sous Éléments
1. Mettez en forme le texte et l’arrière-plan des éléments en définissant les options **Couleur de police** sur noir, **Arrière-plan** sur rouge clair, **Taille du texte** sur 10 points et **Famille de polices** sur Arial. 
2. Sous Contour, choisissez **Cadre** pour ajouter une bordure autour de chaque élément de la taille et de la couleur que vous avez définies dans les options Général. 
    
    ![mise en forme](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Avec l’orientation horizontale, les éléments désélectionnés affichent le texte et l’arrière-plan dans les couleurs choisies, alors que les éléments sélectionnés utilisent les couleurs par défaut du système (généralement, les arrière-plans sont en noir et le texte est en blanc). 
    >- Avec l’orientation verticale, les éléments s’affichent toujours dans les couleurs définies et les zones de sélection s’affichent toujours en noir quand elles sont sélectionnées. 

### <a name="other-formatting-options"></a>Autres options de mise en forme
Les autres options de mise en forme sont désactivées par défaut. Quand elles sont **activées** : 
- **Titre** : ajoute et met en forme un titre (en plus et indépendamment de l’en-tête) en haut du segment. 
- **Arrière-plan** : ajoute une couleur d’arrière-plan au segment entier et définit sa transparence.
- **Verrouiller l’aspect** : conserve la forme du segment quand il est redimensionné.
- **Bordure** : ajoute une bordure d’un pixel autour du segment et définit sa couleur. (Cette bordure de segment est distincte et indépendante des paramètres de contour définis sous Général.) 

## <a name="sync-and-use-the-slicer-on-other-pages"></a>Synchroniser et utiliser le segment dans d’autres pages
À compter de la mise à jour de février 2018 de Power BI, vous pouvez synchroniser un segment et l’utiliser dans toutes les pages d’un rapport ou dans certaines pages uniquement. 
1. Une fois le segment District Manager sélectionné, dans le menu Affichage, sélectionnez **Synchroniser les segments** dans Power BI Desktop, ou activez le **volet Synchroniser les segments** dans le service Power BI. Le volet Synchroniser les segments s’affiche. 
    
    ![synchroniser les segments](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
2. Dans la première colonne, sélectionnez la page **Overview** et toutes les autres pages avec lesquelles vous souhaitez synchroniser le segment, ou cliquez sur **Ajouter à toutes** pour effectuer la synchronisation du segment avec toutes les pages du rapport.  
3. Dans la colonne suivante, sélectionnez la page **Overview** et toutes les autres pages sur lesquelles vous souhaitez afficher le segment. 
4. Affichez la page **Overview** pour voir le segment et ses effets sur les autres visuels de la page. 
    - Effectuez et supprimez différentes sélections d’éléments pour expérimenter de quelle façon les autres visuels dans la page changent en conséquence. La sélection d’éléments dans une page impacte toutes les autres pages synchronisées.
    - Changez la taille, la forme, la position et/ou la mise en forme du segment dans la page Overview. Vous pouvez constater que la mise en forme du segment ne change pas dans les autres pages synchronisées. 

### <a name="control-which-page-visuals-are-affected-by-the-slicer"></a>Contrôler l’impact du segment sur les visuels de la page
Par défaut, un segment dans une page de rapport impacte toutes les autres visualisations de cette page. Utilisez **Interactions avec l’élément visuel** pour empêcher certaines visualisations de la page d’être modifiées.

1. Dans la page **Overview**, quand le segment est sélectionné :
    - Dans Power BI Desktop, cliquez sur le menu Format sous Outils pour les visuels, puis sélectionnez **Modifier les interactions**.
    - Dans le service Power BI, cliquez sur la liste déroulante **Interactions avec l’élément visuel** dans la barre de menus et activez **Modifier les interactions**. 
    
    Les contrôles de filtre s’affichent au-dessus de tous les autres visuels dans la page. ![contrôles de filtre](media/power-bi-visualization-slicers/filter-controls.png)
    
2. Sélectionnez l’icône **Aucun** au-dessus d’un visuel pour enlever le filtre appliqué par le segment. Sélectionnez l’icône **Filtre** pour réappliquer le filtre du segment au visuel. 

Pour plus d’informations sur la modification des interactions, consultez [Interactions entre les visuels dans un rapport Power BI](service-reports-visual-interactions.md).

## <a name="next-steps"></a>Étapes suivantes
[Essayez-le gratuitement !](https://powerbi.com/)

Avez-vous des idées pour améliorer Power BI ? [Soumettez une idée](https://ideas.powerbi.com/forums/265200-power-bi-ideas).

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

[Ajouter une visualisation à un rapport](power-bi-report-add-visualizations-i.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI – Concepts de base](service-basic-concepts.md)

