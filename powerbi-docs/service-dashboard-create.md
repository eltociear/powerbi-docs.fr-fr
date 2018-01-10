---
title: "Créer un tableau de bord à partir d’un rapport"
description: "Créer un tableau de bord à partir d’un rapport"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/09/2017
ms.author: mihart
ms.openlocfilehash: 67cc9508d71fa29303d09e8901294a2d6b7f8a56
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Créer un tableau de bord à partir d’un rapport
Vous avez lu [Tableaux de bord dans Power BI](service-dashboards.md) et vous souhaitez maintenant créer vos propres tableaux de bord. Il existe de nombreuses façons de créer un tableau de bord : à partir d’un rapport, en partant de zéro, à partir d’un jeu de données, en dupliquant un tableau de bord existant, et bien plus encore.  Cette rubrique et la vidéo vous montrent comment créer un tableau de bord en épinglant des visualisations à partir d’un rapport existant.

> **REMARQUE**: les tableaux de bord sont une fonctionnalité du service Power BI et non de Power BI Desktop. Les tableaux de bord ne peut pas être créés dans l’application mobile Power BI, mais ils peuvent être [affichés et partagés](mobile-apps-view-dashboard.md).
> 
> 

![](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Vidéo : Créer un tableau de bord en épinglant des éléments visuels et des images provenant d’un rapport
Regardez Amanda créer un tableau de bord en épinglant des visualisations et des images provenant d’un rapport. Puis essayez vous-même, à l’aide de l’exemple Analyse de l’approvisionnement, en suivant les étapes indiquées sous la vidéo.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importer un jeu de données avec un rapport
Nous allons importer l’un des exemples de jeu de données Power BI et l’utiliser pour créer notre tableau de bord. L’exemple que nous allons utiliser est un classeur Excel avec deux feuilles PowerView. Lorsque Power BI importe le classeur, un jeu de données et un rapport sont ajoutés dans votre espace de travail.  Le rapport est automatiquement créé à partir des feuilles PowerView.

1. [Cliquez sur ce lien](http://go.microsoft.com/fwlink/?LinkId=529784) pour télécharger et enregistrer le fichier Excel de l’exemple Analyse de l’approvisionnement. Nous vous recommandons de l’enregistrer dans votre OneDrive Entreprise.
2. Ouvrez le service Power BI dans votre navigateur (app.powerbi.com).
3. Sélectionnez un espace de travail existant ou créez un espace de travail d’application.
4. Dans le volet de navigation de gauche, sélectionnez **Obtenir les données**.
   
    ![](media/service-dashboard-create/power-bi-get-data3.png)
5. Sélectionnez **Fichiers**.
   
   ![](media/service-dashboard-create/power-bi-select-files.png)
6. Naviguez jusqu'à l’emplacement où vous avez enregistré le fichier Excel de l’exemple Analyse de l’approvisionnement. Sélectionnez-le et choisissez **Connecter**.
   
   ![](media/service-dashboard-create/power-bi-connectnew.png)
7. Dans cet exercice, sélectionnez **Importer**.
   
    ![](media/service-dashboard-create/power-bi-import.png)
8. Lorsque le message de réussite s’affiche, sélectionnez **x** pour le fermer.
   
   ![](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>Ouvrir le rapport et épingler des vignettes à un tableau de bord
1. Sans quitter l’espace de travail, sélectionnez l’onglet **Rapports**. Le rapport nouvellement importé s’affiche avec un astérisque jaune. Sélectionnez le nom du rapport pour l’ouvrir.
   
    ![](media/service-dashboard-create/power-bi-reports.png)
2. Le rapport s’ouvre en [mode Lecture](service-reading-view-and-editing-view.md). Notez qu’il comporte deux onglets en bas : Discount Analysis (Analyse des remises) et Spend Overview (Vue d’ensemble des dépenses). Chaque onglet représente une page du rapport.
   
    ![](media/service-dashboard-create/power-bi-reading-view.png)
3. Pointez sur une visualisation pour afficher les options disponibles. Pour ajouter une visualisation à un tableau de bord, sélectionnez l’icône d’épingle ![](media/service-dashboard-create/power-bi-pin-icon.png).
   
    ![](media/service-dashboard-create/power-bi-hover.png)
4. Étant donné que nous créons un tableau de bord, sélectionnez l’option **Nouveau tableau de bord** et donnez-lui un nom. 
   
   ![](media/service-dashboard-create/power-bi-pin-tile.png)
5. Lorsque vous sélectionnez **Épingler**, Power BI crée un nouveau tableau de bord dans l’espace de travail actuel. Lorsque le message **Épinglé au tableau de bord** s’affiche, sélectionnez **Accéder au tableau de bord**. Si vous êtes invité à enregistrer le rapport, choisissez **Enregistrer**.
   
     ![](media/service-dashboard-create/power-bi-pin-success.png)
6. Power BI ouvre le nouveau tableau de bord et il existe une vignette : la visualisation que nous venons d’épingler. 
   
   ![](media/service-dashboard-create/power-bi-pinned.png)
7. Pour revenir au rapport, sélectionnez la vignette. Épinglez d’autres vignettes au nouveau tableau de bord. Cette fois, lorsque la fenêtre **Épingler au tableau de bord** s’affiche, sélectionnez **Tableau de bord existant**.  
   
   ![](media/service-dashboard-create/power-bi-existing-dashboard.png)

Félicitations pour la création de votre premier tableau de bord ! Maintenant que vous avez un tableau de bord, vous pouvez vous en servir pour de multiples usages.  Essayez l’une des **Étapes suivantes** suggérées ci-dessous ou commencez à vous exercer et à explorer les différentes possibilités qui s’offrent à vous.   

## <a name="next-steps"></a>Étapes suivantes
* [Redimensionner et déplacer des vignettes](service-dashboard-edit-tile.md)
* [Toutes les informations dont vous avez besoin sur les vignettes du tableau de bord](service-dashboard-tiles.md)
* [Partager votre tableau de bord en créant une application](service-create-distribute-apps.md)
* [Power BI – Concepts de base](service-basic-concepts.md)
* [Tableaux de bord dans Power BI](service-dashboards.md)
* [Conseils pour la conception d’un tableau de bord réussi](service-dashboards-design-tips.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

