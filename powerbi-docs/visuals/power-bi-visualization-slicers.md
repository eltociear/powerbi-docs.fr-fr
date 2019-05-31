---
title: 'Tutoriel : Segments dans Power BI'
description: Segments dans Power BI
author: v-thepet
manager: kvivek
ms.reviewer: ''
featuredvideoid: zIZPA0UrJyA
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/14/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f5eed81a5750bebb4df968a09cd1fcfd2aa069d1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710860"
---
# <a name="slicers-in-power-bi"></a>Segments dans Power BI
Vous souhaitez que vos lecteurs de rapports soient en mesure de rechercher des mesures de ventes globales, mais également de mettre en surbrillance des performances pour les responsables de région individuels et les différentes périodes. Vous pouvez créer des rapports distincts ou des graphiques de comparaison ou vous pouvez utiliser des segments. Un segment constitue un autre moyen de réduire la partie du jeu de données affichée dans les autres visualisations d’un rapport. 

Ce tutoriel utilise [Exemple Analyse de la vente au détail](../sample-retail-analysis.md) gratuit pour vous expliquer pas à pas comment créer, mettre en forme et utiliser des segments de plages de dates et de listes. Amusez-vous à découvrir les différentes mises en forme et utilisations possibles des segments. 

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

## <a name="create-slicers"></a>Créer des segments

Pour créer un nouveau segment, vous pouvez sélectionner l’icône de segment et puis sélectionnez le champ de données sur laquelle filtrer (ou faites-le glisser vers le **filtres** zone le **visualisations** volet), ou vous pouvez sélectionner ou faire glisser le champ de données tout d’abord vers créer une visualisation, puis sélectionnez l’icône de segment pour transformer la visualisation en segment. Différents types de données créent différents types de segments, avec des options et des effets différents. 

La première fois que vous modifiez un rapport, le bouton pour **Rétablir les valeurs par défaut** est activé. Il s’agit d’un rappel indiquant que vous avez changé les paramètres du rapport d’origine. Si vous quittez le rapport, ces modifications sont enregistrées. Quand vous revenez au rapport, vous ne devez pas resegmenter le rapport.  Cependant, si vous voulez rétablir les paramètres par défaut de l’auteur du rapport, sélectionnez le bouton **Rétablir les valeurs par défaut** dans la barre de menus du haut.

![Bouton Rétablir les valeurs par défaut](media/power-bi-visualization-slicers/power-bi-reset-to-default.png)

> [!NOTE]
> Si votre bouton **Rétablir les valeurs par défaut** reste désactivé, cela signifie que l’auteur du rapport a désactivé la fonctionnalité pour le rapport ou que le rapport contient un visuel personnalisé. Pointez simplement sur le bouton pour lire l’explication de l’info-bulle. 

**Créer un nouveau segment pour filtrer les données par le Gestionnaire de districts**

1. Dans Power BI Desktop ou le service Power BI, ouvrez le [Retail Analysis Sample](../sample-retail-analysis.md). (Dans le service Power BI, sélectionnez **Modifier le rapport** en haut à gauche.)
2. Dans la page Vue d’ensemble, rien n’est sélectionné sur le canevas, sélectionnez le **segment** icône ![icône segment](media/power-bi-visualization-slicers/slicer-icon.png) dans le **visualisations** volet pour créer un nouveau segment. 
3. Avec le nouveau segment sélectionné, dans le volet champs, sélectionnez **District** > **DM** pour remplir le segment. Le nouveau segment est une liste des boîtes de sélection avant les noms. 
    
    ![nouveau segment](media/power-bi-visualization-slicers/power-bi-new-slicer.png)
    
4. Redimensionnez et faites glisser le segment et autres éléments sur le canevas pour libérer de l’espace pour le segment. Notez que les éléments de segment sont tronqués si vous redimensionnez le segment trop petit. 
5. Sélectionnez les noms sur le segment et notez les effets sur les autres visualisations de la page. Sélectionnez à nouveau les noms pour les désélectionner, maintenez la touche **Ctrl** enfoncée pour sélectionner plusieurs noms. La sélection de tous les noms a le même effet que la sélection d’aucun nom. \

6. Ou bien, sélectionnez l’icône rouleau de peinture à mettre en forme votre segment. Il existe simplement trop nombreuses options pour les décrire tous ici : donc faire des essais et créer un segment qui fonctionne pour vous. Dans les exemples ci-dessous, le premier segment a été converti en une liste déroulante pour économiser l’espace et l’option à « Tout sélectionner » a été ajoutée.  Le deuxième segment a été mis en forme des couleurs et tailles de polices et autorise uniquement une seule sélection.

   ![nouveau segment](media/power-bi-visualization-slicers/power-bi-filter-examples.png)
>[!TIP]
>Par défaut, les éléments de segment de liste sont triés par ordre alphanumérique croissant. Pour inverser l’ordre de tri et utiliser l’ordre décroissant, sélectionnez les points de suspension ( **...** ) en haut à droite du segment et choisissez **Trier par Gestionnaire de districts** dans la liste déroulante. 

**Pour créer un nouveau segment pour filtrer les données par plage de dates**

1. Rien n’est sélectionné sur le canevas, la liste déroulante **Date** dans le volet champs, faites glisser **Date** à la **valeurs** zone dans le volet visualisations pour créer une visualisation.
2. Une fois la nouvelle visualisation sélectionnée, sélectionnez l’icône **Segment** pour convertir la nouvelle visualisation en segment. Ce segment est un segment de contrôle avec la plage de dates remplie.
    
    ![nouveau segment de plages](media/power-bi-visualization-slicers/power-bi-date-slicer.png)

    
4. Redimensionnez et faites glisser le segment et autres éléments sur le canevas pour libérer de l’espace pour le segment. Notez que le curseur est redimensionné selon la taille du segment, mais il disparaît et les dates sont tronquées si vous redimensionnez le segment trop petit. 
4. Sélectionnez des plages de dates différentes avec le curseur ou sélectionnez un champ de date pour entrer une valeur ou afficher un calendrier pour une sélection plus précise. Notez les effets sur les autres visualisations de la page.
    
    >[!NOTE]
    >Les types de données numériques et date/heure produisent des segments de curseur de plage par défaut. À compter de la mise à jour de Power BI de février 2018, les segments des types de données de nombres entiers s’alignent sur des valeurs de nombre entier plutôt que d’afficher des places décimales. 


5. Maintenant modifier la valeur du champ à partir de **Date** à **MonthIndex**.  Cela génère un **entre** type de segment de plage par défaut, mais vous pouvez le modifier à d’autres types de segment et les options de sélection. Pour modifier le type de segment, une fois le segment sélectionné, placez votre curseur sur la zone supérieure droite du segment, faites défiler vers le bas le carat qui s’affiche et choisissez une des autres options, telles que **Liste** ou **Avant**. Notez les changements d’apparence du segment et des options de sélection. 
 
    ![nouveau segment de plages](media/power-bi-visualization-slicers/power-bi-between-slicer.png)


Pour plus d’informations sur la création des segments de plages numériques et de dates, consultez [Utiliser le segment de plages numériques dans Power BI Desktop](../desktop-slicer-numeric-range.md) et regardez la vidéo suivante.
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe> 

## <a name="control-which-page-visuals-are-affected-by-slicers"></a>Contrôler l’impact des segments sur les visuels de la page
Par défaut, les segments des pages du rapport affectent toutes les autres visualisations sur cette page, y compris les unes par rapport aux autres. Lorsque vous choisissez des valeurs dans les curseurs de liste et de date que vous venez de créer, notez les effets sur les autres visualisations. Les données filtrées sont une intersection des valeurs sélectionnées dans les deux segments. 

Vous pouvez utiliser **Interactions avec le visuel** pour empêcher certaines visualisations de la page d’être affectées par les autres. Sur la page **Vue d’ensemble**, le graphique « Variance des ventes totales par FiscalMonth et Gestionnaire de districts » affiche des données comparatives générales pour les Gestionnaires de districts par Mois, que vous souhaitez laisser visibles à tout moment. Vous pouvez utiliser **Interactions visuelles** pour empêcher les sélections de segment de filtrer ce graphique. 

1. Une fois le segment Gestionnaire de districts sélectionné :
    - Dans Power BI Desktop, sélectionnez le menu **Format** sous **Outils d'élément visuel**, puis sélectionnez **Modifier les interactions**.
    - Dans le service Power BI, cliquez sur la liste déroulante **Interactions avec l’élément visuel** dans la barre de menus et activez **Modifier les interactions**. 
   
   Les contrôles de filtre ![contrôles de filtre](media/power-bi-visualization-slicers/filter-controls.png) s’affichent au-dessus de tous les autres visuels de la page. Au départ, toutes les icônes **Filtre** sont sélectionnées.
   
2. Sélectionnez l’icône **Aucun** au-dessus du graphique **Variance des ventes totales par FiscalMonth et Gestionnaire de districts** pour arrêter le filtrage par le segment. 
3. Sélectionnez le segment **Mois** et sélectionnez à nouveau l’icône **Aucun** au-dessus du graphique **Variance des ventes totales par FiscalMonth et Gestionnaire de districts** pour arrêter le filtrage par ce segment. Désormais, lorsque vous sélectionnez les noms et les plages de dates dans les segments, le graphique Variance des ventes totales par FiscalMonth et Gestionnaire de districts est inchangé. 

Pour plus d’informations sur la modification des interactions, consultez [Interactions entre les visuels dans un rapport Power BI](../service-reports-visual-interactions.md).

## <a name="sync-and-use-slicers-on-other-pages"></a>Synchroniser et utiliser des segments dans d’autres pages
À compter de la mise à jour de février 2018 de Power BI, vous pouvez synchroniser un segment et l’utiliser dans toutes les pages d’un rapport ou dans certaines pages uniquement. 

Dans le rapport actuel, la page **Ventes mensuelles du district** comporte également un segment **Gestionnaire de districts**, mais il n’est pas synchronisé avec celui que vous avez créé sur la page **Vue d’ensemble** (les deux segments peuvent avoir des sélections d’éléments différentes). La page **Nouveaux magasins** comporte un seul segment **Nom de magasin**. Vous pouvez synchroniser votre nouveau segment **Gestionnaire de districts** avec ces pages, afin que les sélections du segment sur n’importe quelle page affectent les visualisations sur les trois pages. 

1. Dans le menu **Affichage**, sélectionnez **Synchroniser les segments** dans Power BI Desktop (ou activez le **volet Synchroniser les segments** dans le service Power BI). Le volet **Synchroniser les segments** s’affiche. 
2. Sur la page **Vue d’ensemble**, sélectionnez le segment **Gestionnaire de districts**. Notez que la page **Ventes mensuelles du district** est déjà sélectionnée dans la colonne **Visible**, car il existe aussi un segment Gestionnaire de districts sur cette page, mais il n’est pas sélectionné dans la colonne **Synchrone**. 
    
    ![synchroniser les segments](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
3. Dans la colonne **Synchrone**, sélectionnez la page **Nouveaux magasins** et la page **Ventes mensuelles du district** pour synchroniser le segment **Vue d’ensemble** pour ces pages. 
    
3. Dans la colonne **Visible**, sélectionnez la page **Nouveaux magasins** et laissez la page **Ventes mensuelles du district** sélectionnée. 
4. Observez les effets de la synchronisation du segment et de la visibilisation sur les autres pages. Sur la page **Ventes mensuelles du district**, le segment **Gestionnaire de districts** affiche alors les mêmes sélections que celui de la page **Vue d’ensemble**. Sur la page **Nouveaux magasins**, les sélections effectuées dans le segment **Gestionnaire de districts** affectent les sélections disponibles dans le segment **Nom de magasin**. 
    
    >[!TIP]
    >Bien que le segment apparaisse initialement dans les pages synchronisées à la même taille et dans la même position que sur la page d’origine, vous pouvez déplacer, redimensionner et mettre en forme des segments synchronisés sur les différentes pages indépendamment. 

>[!NOTE]
>Si vous synchronisez un segment sur une page mais ne le rendez pas visible sur cette page, les sélections de segment effectuées sur les autres pages filtrent toujours les données sur la page.
 
## <a name="format-slicers"></a>Mettre en forme des segments
Différentes options de mise en forme sont disponibles selon le type de segment. À l’aide de l’orientation **Horizontal**, de la disposition **Dynamique** et de la coloration des **Éléments**, vous pouvez produire des boutons ou mosaïques, plutôt que des éléments de liste standard et redimensionner les éléments de segment pour s’adapter aux différentes tailles et dispositions d’écran.  

1. Une fois le segment **Gestionnaire de districts** sélectionné sur une page, dans le volet **Visualisations**, sélectionnez l’icône **Format** ![](media/power-bi-visualization-slicers/power-bi-paintroller.png) pour afficher les contrôles de mise en forme. 
    
    ![mise en forme](media/power-bi-visualization-slicers/3-format.png)
    
2. Sélectionnez les flèches de liste déroulante à côté de chaque catégorie pour afficher et modifier les options. 

### <a name="general-options"></a>Options générales
1. Sélectionnez la couleur rouge sous **Couleur du contour** et changez la valeur **Épaisseur du contour** à « 2 ». Ces options définissent la couleur et l’épaisseur des contours ou soulignements de l’en-tête et des éléments, quand ils sont activés. 
2. Sous **Orientation**, **Vertical** est la valeur par défaut. Sélectionnez **Horizontal** pour produire un segment avec des mosaïques ou des boutons organisés horizontalement et utilisez les flèches pour accéder aux éléments qui ne tiennent pas dans le segment.
    
    ![horizontale](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. Activez la disposition **Dynamique** pour modifier la taille et la disposition des éléments de segment en fonction de la taille de l’écran et des segments. Pour les segments de la liste, la disposition dynamique est disponible uniquement dans une orientation horizontale et empêche que des éléments soient tronqués sur de petits écrans. Pour les segments de curseurs de plages, la mise en forme dynamique modifie le style du curseur et fournit un redimensionnement plus flexible. Les deux types de segments deviennent des icônes de filtre de très petite taille. 
    
    ![dynamique](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >Les changements de disposition dynamique peuvent substituer la mise en forme spécifique du titre et des éléments que vous avez définie. 
    
4. Définissez la position et la taille du segment avec une précision numérique sous **Position X**, **Position Y**, **Largeur** et **Hauteur** ou déplacez et redimensionnez le segment directement sur le canevas. Faites des essais avec des tailles d’éléments et des dispositions différentes et notez les modifications de la mise en forme dynamique en conséquence.  

    ![boutons horizontaux](media/power-bi-visualization-slicers/6-buttons.png)

Pour plus d’informations sur l’orientation horizontale et la disposition dynamique, consultez [Créer un segment réactif que vous pouvez redimensionner dans Power BI](../power-bi-slicer-filter-responsive.md).

### <a name="selection-controls-options-list-slicers-only"></a>Options des contrôles de sélection (uniquement pour les segments de liste)
1. L’option **Afficher Sélectionner tout** est **Désactivée** par défaut. **Activez-la** pour ajouter un élément **Sélectionner tout** au segment qui sélectionne ou désélectionne tous les éléments, le cas échéant. Quand tous les éléments sont sélectionnés, il suffit de cliquer ou d’appuyer sur un élément pour le désélectionner. Il s’agit d’un filtre de type « n’est pas ». 
    
    ![sélectionner tout](media/power-bi-visualization-slicers/7-select-all.png)
    
2. L’option **Sélection simple** est **Activée** par défaut. Pour sélectionner un seul élément, cliquez ou appuyez dessus et maintenez la touche **Ctrl** en cliquant ou en tapant pour sélectionner plusieurs éléments. **Désactivez** l’option **Sélection simple** pour pouvoir sélectionner plusieurs éléments sans avoir à maintenir la touche **Ctrl** enfoncée. Le fait de cliquer ou d’appuyer à nouveau sur un élément sélectionné le désélectionne. 

### <a name="header-options"></a>Options sous En-tête
**L’en-tête** est **Activé** par défaut. Il affiche le nom du champ de données en haut du segment. 
1. Mettez en forme le texte de l’en-tête en définissant les options **Couleur de police** sur rouge, **Taille du texte** sur 14 points et **Famille de polices** sur Arial Noir. 
2. Sous **Contour**, choisissez **Seulement le bas** pour produire un soulignement avec la taille et la couleur que vous avez définies dans les options **Général**. 

### <a name="item-options-list-slicers-only"></a>Options de l’élément (uniquement pour les segments de liste)
1. Mettez en forme le texte et l’arrière-plan des éléments en définissant les options **Couleur de police** sur noir, **Arrière-plan** sur rouge clair, **Taille du texte** sur 10 points et **Famille de polices** sur Arial. 
2. Sous **Contour**, choisissez **Cadre** pour dessiner une bordure autour de chaque élément avec la taille et la couleur que vous avez définies dans les options **Général**. 
    
    ![mise en forme](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- Avec **Orientation > Horizontal**, les éléments désélectionnés affichent le texte et l’arrière-plan dans les couleurs choisies, alors que les éléments sélectionnés utilisent les couleurs par défaut du système, généralement, les arrière-plans sont en noir et le texte est en blanc.
    >- Avec **Orientation > Vertical**, les éléments s’affichent toujours dans les couleurs définies et les boîtes de sélection s’affichent toujours en noir quand elles sont sélectionnées. 

### <a name="datenumeric-inputs-and-slider-options-range-slider-slicers-only"></a>Entrées de date/numériques et options du curseur (segments des curseurs de plage uniquement)
- Les options d’entrées de date/numériques sont les mêmes que les options **d’élément** pour les segments de la liste, sauf s’il n’y a aucun **Contour** ou soulignement.
- Les options de curseur vous permettent de définir la couleur du curseur de la plage ou **désactivez** le curseur, en laissant uniquement les entrées numériques.

### <a name="other-formatting-options"></a>Autres options de mise en forme
Les autres options de mise en forme sont désactivées par défaut. Quand elles sont **activées** : 
- **Titre :** ajoute et met en forme un titre (en plus et indépendamment de l’en-tête) en haut du segment. 
- **Arrière-plan :** ajoute une couleur d’arrière-plan au segment entier et définit sa transparence.
- **Verrouiller l’aspect :** conserve la forme du segment quand il est redimensionné.
- **Bordure :** ajoute une bordure d’un pixel autour du segment et définit sa couleur. (Cette bordure de segment est distincte et indépendante des paramètres de contour définis sous Général.) 

## <a name="next-steps"></a>Étapes suivantes
[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Tableaux dans Power BI](power-bi-visualization-tables.md)

