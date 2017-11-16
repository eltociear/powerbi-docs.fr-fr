---
title: "Vignettes de tableau de bord dans Power BI"
description: "Toutes les informations dont vous avez besoin sur les vignettes de tableau de bord dans Power BI. Cela inclut les vignettes créées à partir de SQL Server Reporting Services (SSRS)."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: d1960ea42bee8b00cc6dd095e94ebf6f6303bce8
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="dashboard-tiles-in-power-bi"></a>Vignettes d’un tableau de bord dans Power BI
Les tableaux de bord et vignettes de tableau de bord caractérisent le service Power BI et non Power BI Desktop. Si vous ne pouvez pas créer ou épingler des vignettes de tableau de bord dans Power BI Mobile, vous [pouvez les afficher et les partager](mobile-tiles-in-the-mobile-apps.md). Par ailleurs, Power BI Mobile vous permet d’[ajouter des images à votre tableau de bord avec votre application iPhone](mobile-iphone-app-get-started.md).

## <a name="dashboard-tiles"></a>Vignettes d’un tableau de bord
![](media/service-dashboard-tiles/power-bi-dashboard.png)

Une vignette est une capture instantanée de vos données, épinglée au tableau de bord. Une vignette peut être créée à partir d’un rapport, d’un jeu de données, d’un tableau de bord, de la zone Q&R, d’Excel et de SSRS (SQL Server Reporting Services) ou d’autres sources.  Cette capture d’écran montre différentes vignettes épinglées à un tableau de bord.

En plus de les épingler, vous pouvez créer des vignettes directement dans votre tableau de bord à l’aide de l’option [Ajouter une vignette](service-dashboard-add-widget.md). Les vignettes autonomes incluent des zones de texte, des images, des vidéos, des données de streaming et du contenu web.

Vous avez du mal à comprendre les éléments qui composent Power BI ?  Consultez [Power BI – Concepts de base](service-basic-concepts.md).

> [!NOTE]
> Si la visualisation d’origine utilisée pour créer la vignette change, la vignette ne change pas.  Par exemple, si vous avez épinglé un graphique en courbes à partir d’un rapport et que vous changez ce graphique en graphique à barres, la vignette du tableau de bord continue à afficher un graphique en courbes. Les données s’actualisent, mais pas le type de visualisation.
> 
> 

## <a name="pin-a-tile-from"></a>Épingler une vignette à partir de...
Vous pouvez ajouter (épingler) une vignette à un tableau de bord de plusieurs manières. Vous pouvez épingler des vignettes à partir de :

* [Q&R Power BI](service-dashboard-pin-tile-from-q-and-a.md)
* [Un rapport](service-dashboard-pin-tile-from-report.md)
* [Un autre tableau de bord](service-pin-tile-to-another-dashboard.md)
* [Un classeur Excel sur OneDrive Entreprise](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher pour Excel](publisher-for-excel.md)
* [Informations rapides](service-insights.md)
* [SSRS](https://msdn.microsoft.com/library/mt604784.aspx)

Les vignettes autonomes pour les images, les zones de texte, les vidéos, les données de streaming et le contenu web peuvent être créées directement dans le tableau de bord à l’aide de l’option [Ajouter une vignette](service-dashboard-add-widget.md).

  ![](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>Interaction avec des vignettes dans un tableau de bord
### <a name="move-and-resize-a-tile"></a>Déplacement et redimensionnement d'une vignette
Saisissez une vignette et [déplacez-la dans le tableau de bord](service-dashboard-edit-tile.md). Pointez et sélectionnez la poignée ![](media/service-dashboard-tiles/resize-handle.jpg) pour redimensionner la vignette.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Placer le curseur sur une vignette pour modifier son apparence et son comportement
1. Placez le curseur sur la vignette pour afficher les points de suspension.
   
    ![](media/service-dashboard-tiles/ellipses_new.png)
2. Sélectionnez les points de suspension pour ouvrir le menu des actions de la vignette.
   
    ![](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Vous pouvez ici :
   
   * [Ouvrir le rapport utilisé pour créer cette vignette ](service-reports.md) ![](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [Ouvrir la feuille de calcul utilisée pour créer cette vignette ](service-reports.md) ![](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
     * [Afficher en mode Focus](service-focus-mode.md) ![](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [Exporter les données utilisées dans la vignette](power-bi-visualization-export-data.md) ![](media/service-dashboard-tiles/export-icon.png)
     * [Modifier le titre et le sous-titre, ajouter un lien hypertexte, afficher l’heure de la dernière actualisation](service-dashboard-edit-tile.md) ![](media/service-dashboard-tiles/pencil-icon.jpg)
     * [Exécuter Insights ](service-insights.md)![](media/service-dashboard-tiles/power-bi-insights.png)
     * [Épingler la vignette sur un autre tableau de bord](service-pin-tile-to-another-dashboard.md)
       ![](media/service-dashboard-tiles/pin-icon.jpg)
   * [Supprimer la vignette](service-dashboard-edit-tile.md)
     ![](media/service-dashboard-tiles/trash-icon.png)
3. Pour fermer le menu d’actions, sélectionnez une zone vide dans la zone de dessin.

### <a name="select-click-a-tile"></a>Sélectionner (cliquer sur) une vignette
Lorsque vous sélectionnez une vignette, ce qui se passe ensuite dépend de la façon dont la vignette a été créée et de la présence ou non d’un [lien personnalisé dessus](service-dashboard-edit-tile.md). Si elle comporte un lien personnalisé, la sélection de la vignette vous fait accéder à ce lien. Dans le cas contraire, sélectionner la vignette ouvre le rapport, le classeur Excel en ligne, le rapport SSRS en local, ou la question Q&R qui a été utilisée pour créer la vignette.

> [!NOTE]
> La seule exception concerne les vignettes de vidéo créées directement sur le tableau de bord avec l’option **Ajouter une vignette**. En sélectionnant une vignette de vidéo (créée de cette façon), la vidéo est lue directement dans le tableau de bord.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Si le rapport utilisé pour créer la visualisation n'a pas été enregistré, sélectionner la vignette ne produit alors aucune action.
* Si la vignette a été créée à partir d'un classeur Excel en ligne et que vous ne disposez pas au moins des autorisations de lecture nécessaires pour ce classeur, vous ne pourrez pas ouvrir le classeur Excel en ligne en sélectionnant la vignette.
* Pour les vignettes créées directement sur le tableau de bord avec l’option **Ajouter une vignette**, si un lien hypertexte personnalisé a été défini, vous pouvez ouvrir cette URL en sélectionnant le titre, le sous-titre et/ou la vignette.  Sinon, par défaut, la sélection d’une de ces vignettes créées directement sur le tableau de bord pour une image, du code web ou une zone de texte ne produit aucune action.
* Si vous n’avez pas l’autorisation d’accéder au rapport dans SSRS, la sélection d’une vignette créée à partir de SSRS générera une page indiquant que vous n’avez pas accès (rsAccessDenied).
* Si vous n’avez pas accès au réseau où se trouve le serveur SSRS, la sélection d’une vignette créée à partir de SSRS générera une page indiquant que la localisation du serveur est impossible (HTTP 404). Votre appareil doit bénéficier de l’accès réseau au serveur de rapports pour afficher le rapport.
* Si la visualisation d’origine utilisée pour créer la vignette change, la vignette ne change pas.  Par exemple, si vous avez épinglé un graphique en courbes à partir d’un rapport et que vous remplacez le graphique en courbes à un graphique à barres, la vignette du tableau de bord continue à afficher un graphique en courbes. Les données s’actualisent, mais pas le type de visualisation.

## <a name="next-steps"></a>Étapes suivantes
[Créer une vignette représentant un grand nombre à partir d’un rapport](power-bi-visualization-big-number-report.md)

[Créer une vignette représentant un grand nombre à partir de Q&R](power-bi-visualization-big-number.md)

[Tableaux de bord dans Power BI](service-dashboards.md)  

[Actualisation des données](refresh-data.md)

[Power BI – Concepts de base](service-basic-concepts.md)

[Exporter une vignette vers Power Point](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[Épingler les éléments Reporting Services aux tableaux de bord Power BI](https://msdn.microsoft.com/library/mt604784.aspx)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

