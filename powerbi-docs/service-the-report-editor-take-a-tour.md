---
title: Visite guidée de l’éditeur de rapport
description: L’éditeur de rapport du service Power BI et l’éditeur de rapport de Power BI Desktop sont très similaires.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/19/2018
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 70eb50c493c6828ca03b1161138e1a4f4b1fae8e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54284418"
---
# <a name="tour-of-the-report-editor-in-power-bi"></a>Présentation de l’éditeur de rapport de Power BI

L’*éditeur de rapport* du service Power BI et l’éditeur de rapport de Power BI Desktop sont très similaires. La vidéo montre l’éditeur de rapport dans Power BI Desktop et cet article montre l’éditeur de rapport dans le service Power BI. 

En tant qu’auteur de rapport, vous créez et modifiez des tableaux de bord et des rapports. Ensuite, vous les distribuez à vos consommateurs. Ces derniers peuvent manipuler vos tableaux de bord et rapports en mode Lecture dans le service Power BI, mais ils ne peuvent pas les modifier. En savoir plus sur les différences entre le [mode Lecture et le mode Édition dans le service Power BI](consumer/end-user-reading-view.md) 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

Dans le service Power BI, l’éditeur de rapport est uniquement disponible en mode Édition. Pour ouvrir un rapport en mode Édition, vous devez être le propriétaire ou l’auteur de ce rapport, ou bien un collaborateur au sein de l’espace de travail d’application qui héberge ce rapport.

L’éditeur de rapport Power BI comprend trois sections :  

1. les volets **Champs**, **Visualisations**, et **Filtres**
2. barres de navigation supérieures    
3. canevas de rapport     

![Sections de l’éditeur de rapport](media/service-the-report-editor-take-a-tour/power-bi-report-canvas.png)

## <a name="1-the-report-editor-panes"></a>1. Volets de l’éditeur de rapport
![éditeur de rapport Power BI](media/service-the-report-editor-take-a-tour/power-bi-report-panes.png)

Trois volets sont visibles lorsque vous ouvrez un rapport : Visualisations, Filtres et Champs. Les volets du côté gauche, Visualisations et Filtres, contrôlent l’aspect de vos visualisations : type, couleurs, filtrage, mise en forme.  Le volet du côté droit, Champs, gère les données sous-jacentes utilisées dans les visualisations. 

Le contenu affiché dans l’éditeur de rapport varie en fonction des sélections effectuées dans le canevas de rapport.  Par exemple, quand vous sélectionnez un visuel individuel :

|  |  |
| --- | --- |
| ![Volets de l’éditeur de rapport](media/service-the-report-editor-take-a-tour/power-bi-panes.png) |<ul><li>La partie supérieure du volet Visualisations identifie le type de visuel en cours d’utilisation. Dans cet exemple, il s’agit d’un histogramme groupé.<br><br></li> <li>La partie inférieure du volet Visualisations (il se peut que vous deviez défiler vers le bas) affiche les champs utilisés dans le visuel. Ce graphique utilise les champs FiscalMonth, DistrictManager et Total Sales Variance. <br><br></li><li>Le volet Filtres (il se peut que vous deviez faire défiler vers le bas) affiche tous les filtres appliqués. <br><br></li><li>Le volet Champs répertorie les tables disponibles et, si vous développez le nom d’une table, les champs qui composent celle-ci. Une police de couleur jaune indique qu’au moins un champ de cette table est utilisé dans la visualisation.<br><br></li><li>![icône de rouleau de peinture](media/service-the-report-editor-take-a-tour/power-bi-paint-roller-icon.png) Pour afficher le volet de mise en forme pour la visualisation sélectionnée, choisissez l’icône de rouleau de peinture.<br><br></li><li>![icône de loupe](media/service-the-report-editor-take-a-tour/power-bi-magnifying-icon.png) Pour afficher le volet d’analytique, sélectionnez l’icône de loupe.</ul> |

## <a name="the-visualizations-pane"></a>Volet Visualisations
![haut du volet Visualisation](media/service-the-report-editor-take-a-tour/selectviz.png)

Voici où sélectionner un type de visualisation. Les petites images sont appelées *modèles*. Dans l’image ci-dessus, le graphique à barres groupées est sélectionné. Si vous ne sélectionnez pas de type de visualisation au départ, mais commencez à générer une visualisation en sélectionnant des champs, Power BI choisit le type de visualisation pour vous. Vous pouvez conserver la sélection de Power BI ou modifier le type en sélectionnant un autre modèle. Vous pouvez en changer autant de fois que nécessaire jusqu’à trouver le type de visualisation représentant le mieux vos données.

### <a name="manage-the-fields-in-your-visual"></a>Gérer les champs dans votre visuel
![centre du volet Visualisation](media/service-the-report-editor-take-a-tour/power-bi-field-list.png)

Les compartiments (parfois appelés *puits*) affichés dans ce volet varient en fonction du type de visualisation que vous avez sélectionné.  Par exemple, si vous avez sélectionné un graphique à barres, des compartiments s’affichent pour : Valeurs, Axe et Légende. Lorsque vous sélectionnez un champ, ou que vous le faites glisser sur le canevas, Power BI ajoute ce champ à l’un des compartiments.  Vous pouvez également faire glisser des champs de la liste Champs directement vers les compartiments.  Certains compartiments sont limités à certains types de données.  Par exemple, **Valeurs** n’accepte pas les champs non numériques. Par conséquent, si vous faites glisser un champ **employeename** dans le compartiment **Valeurs**, Power BI le remplace par **count of employeename**.

### <a name="remove-a-field"></a>Supprimer un champ
Pour supprimer un champ de la visualisation, sélectionnez le **X** à droite de son nom.

![Supprimer StoreType dans la légende](media/service-the-report-editor-take-a-tour/deletefield.png)

Pour plus d’informations, consultez [Ajouter des visualisations à un rapport Power BI](visuals/power-bi-report-add-visualizations-i.md).

### <a name="format-your-visuals"></a>Mettre en forme vos éléments visuels
Sélectionnez l’icône Rouleau de peinture pour afficher le volet de mise en forme. Les options disponibles varient selon le type de la visualisation sélectionnée.

![Volet Mise en forme dans l’éditeur de rapport](media/service-the-report-editor-take-a-tour/power-bi-formatting.png)

Les possibilités de mise en forme sont pratiquement illimitées.  Pour en savoir plus, explorez par vous-même ou consultez les articles suivants :

* [Personnalisation du titre, de l’arrière-plan et de la légende de la visualisation](visuals/power-bi-visualization-customize-title-background-and-legend.md)
* [Mise en forme des couleurs](visuals/service-getting-started-with-color-formatting-and-axis-properties.md)
* [Personnalisation des propriétés des axes X et Y](visuals/power-bi-visualization-customize-x-axis-and-y-axis.md)

### <a name="add-analytics-to-your-visualizations"></a>Ajouter des analyses à vos visualisations
Sélectionnez l’icône Loupe pour afficher le volet Analyse. Les options disponibles varient selon le type de la visualisation sélectionnée.

![Volet Analytique dans l’éditeur de rapport](media/service-the-report-editor-take-a-tour/power-bi-analytics.png)    
Le volet Analyse du service Power BI vous permet d’ajouter des lignes de référence dynamiques aux visualisations et de vous focaliser sur les tendances ou informations importantes. Pour en savoir plus, voir [Volet Analyse du service Power BI](service-analytics-pane.md) ou [Volet Analyse de Power BI Desktop](desktop-analytics-pane.md).

- - -
## <a name="the-filters-pane"></a>Le volet Filtres
Utilisez le volet Filtres pour afficher, définir et modifier des filtres permanents sur vos rapports au niveau de la page, du rapport, de l’extraction et du visuel. Certes, vous pouvez effectuer un filtrage ad hoc sur les pages et les visuels des rapports en sélectionnant certains éléments ou en utilisant des outils comme les segments, mais, avec le volet Filtres, l’état des filtres est enregistré avec le rapport. 

Le volet Filtres a une autre fonctionnalité puissante : la possibilité de filtrer sur un champ ***non encore utilisé dans les visuels du rapport***. Qu’est-ce que cela signifie ? Lors de la création d’une page de rapport, Power BI ajoute automatiquement tous les champs utilisés dans les visualisations au volet Filtres, dans la zone correspondant aux filtres au niveau des visuels.  Pour définir un visuel, une page, une extraction ou un filtre de rapport à l’aide d’un champ qui n’est pas utilisé actuellement dans une visualisation, il suffit de le faire glisser dans un des compartiments Filtres.   

![Volet Filtres](media/service-the-report-editor-take-a-tour/power-bi-formatting-pane.png)

Pour plus d’informations, consultez [Ajouter un filtre à un rapport](power-bi-report-add-filter.md).

- - -
## <a name="the-fields-pane"></a>Le volet Champs
Le volet Champs affiche les tables et les champs qui existent dans vos données et sont disponibles pour créer des visualisations.

|  |  |
| --- | --- |
| ![volet Champs](media/service-the-report-editor-take-a-tour/reportfields.png) |<ul><li>Faites glisser un champ sur la page pour démarrer une nouvelle visualisation.  Vous pouvez également faire glisser un champ sur une visualisation existante pour y ajouter ce champ.<br><br></li> <li>Lorsque vous ajoutez une coche en regard d’un champ, Power BI ajoute ce champ à la visualisation active (ou nouvelle). Il choisit également le compartiment dans lequel placer ce champ.  Par exemple, le champ doit-il être utilisé en tant que légende, axe ou valeur ? Power BI fait la meilleure hypothèse et vous pouvez déplacer le champ de ce compartiment vers un autre si nécessaire. <br><br></li><li>Dans les deux cas, chaque champ sélectionné est ajouté au volet Visualisations dans l’éditeur de rapport.</li></ul> |

**REMARQUE** : Si vous utilisez Power BI Desktop, vous pouvez également afficher/masquer des champs, ajouter des calculs, etc.

### <a name="what-do-the-field-icons-mean"></a>Que signifient les icônes de champ ?
**∑ Agrégats** Un agrégat est une valeur numérique additionnée, ou qui fait l’objet d’une moyenne, par exemple. Les agrégats sont importés avec les données (définies dans le modèle de données sur lequel votre rapport est basé).
Pour plus d’informations, consultez [Agrégats dans des rapports Power BI](service-aggregates.md).

![icône de calculatrice](media/service-the-report-editor-take-a-tour/pbi_calculated_icon.png) **Mesures calculées (également appelées champs calculés)**  
Chaque champ calculé a sa propre formule codée en dur. Vous ne pouvez pas modifier le calcul ; par exemple, s’il s’agit d’une somme, il peut uniquement être une somme. Pour plus d’informations, voir [Présentation des mesures](desktop-measures.md).

![Icône de champ unique](media/service-the-report-editor-take-a-tour/icon.png) **Champs uniques**  
Les champs portant cette icône ont été importés à partir d’Excel et sont configurés pour afficher toutes les valeurs, même si elles ont des doublons. Par exemple, vos données peuvent avoir deux enregistrements pour les personnes nommées « John Smith », et chacun est traité comme étant unique. Ils ne seront pas additionnés.  

**![Icône de géographie](media/service-the-report-editor-take-a-tour/pbi_geo_icon.png) Champs de géographie**  
Les champs d’emplacement peuvent être utilisés pour créer des visualisations de cartes. 

**![Icône de hiérarchie](media/service-the-report-editor-take-a-tour/power-bi-hierarchy-icon.png) Hiérarchie**  
Sélectionnez la flèche pour afficher les champs qui composent la hiérarchie. 

## <a name="2-the-top-navigation-bar"></a>2. Barre de navigation supérieure
Les actions disponibles dans la barre de navigation supérieure sont nombreuses, et de nouvelles actions sont en permanence ajoutées. Pour plus d’informations sur une action en particulier, utilisez la zone de recherche ou la table des matières de la documentation de Power BI.

## <a name="3-the-report-canvas"></a>3. Canevas de rapport
Le canevas de rapport est l’emplacement où votre travail s’affiche. Lorsque vous utilisez les volets Champs, Filtres et Visualisations pour créer des visuels, ceux-ci sont générés et affichés sur le canevas de rapport. Chaque onglet au bas du canevas représente une page du rapport. Sélectionnez un onglet pour ouvrir cette page. 

## <a name="next-steps"></a>Étapes suivantes
[Créer un rapport](service-report-create-new.md)

Découvrez plus en détail les rapports dans le [service Power BI](service-report-create-new.md), [Power BI Desktop](desktop-report-view.md) et les [applications mobiles Power BI](consumer/mobile/mobile-apps-view-phone-report.md).

[Fondamentaux pour les concepteurs Power BI](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

