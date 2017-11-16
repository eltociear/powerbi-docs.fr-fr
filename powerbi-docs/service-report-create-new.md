---
title: "Créer un rapport à partir d’un jeu de données "
description: "Créez un rapport Power BI à partir d’un jeu de données."
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
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: f4afb1eaa1b3012fdbdb0eff35e9eff695cc32e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-new-power-bi-report-by-importing-a-dataset"></a>Créer un rapport Power BI en important un jeu de données
Vous avez lu [apports dans Power BI](service-reports.md) et vous souhaitez maintenant créer vos propres rapports. Il existe de nombreuses façons de créer un rapport. Dans cet article, nous allons commencer par créer un rapport très basique à partir d’un jeu de données Excel. Lorsque vous aurez compris les principes fondamentaux de la création d’un rapport, les **Étapes suivantes** plus bas vous dirigeront vers des rubriques plus avancées concernant les rapports.  

> **CONSEIL** : pour créer un rapport en copiant un rapport existant, voir [Copier un rapport](power-bi-report-copy.md).
> 
> 

## <a name="import-the-dataset"></a>Importer le jeu de données
Cette méthode de création d’un rapport démarre avec un jeu de données et un canevas de rapport vide. Pour suivre la procédure, [téléchargez l’exemple de jeu de données Excel Analyse de la vente au détail](http://go.microsoft.com/fwlink/?LinkId=529778) et enregistrez-le dans OneDrive Entreprise (recommandé) ou localement.

1. Nous allons créer le rapport dans un espace de travail du service Power BI. Par conséquent, sélectionnez un espace de travail existant ou créez-en un.
   
   ![](media/service-report-create-new/power-bi-workspaces2.png)
2. En bas de la barre de navigation de gauche, sélectionnez **Obtenir les données**.
   
   ![](media/service-report-create-new/power-bi-get-data3.png)
3. Sélectionnez **Fichiers**, puis accédez à l’emplacement dans lequel vous avez enregistré l’exemple Analyse de la vente au détail.
   
    ![](media/service-report-create-new/power-bi-select-files.png)
4. Dans cet exercice, sélectionnez **Importer**.
   
   ![](media/service-report-create-new/power-bi-import.png)
5. Une fois le jeu de données importé, sélectionnez **Afficher le jeu de données**.
   
   ![](media/service-report-create-new/power-bi-view-dataset.png)
6. L’affichage d’un jeu de données a pour effet d’ouvrir l’éditeur de rapport.  Vous y voyez un canevas vide et des outils d’édition de rapports.
   
   ![](media/service-report-create-new/power-bi-blank-report.png)

> **CONSEIL** : si vous n’êtes pas familiarisé avec le canevas de modification de rapport ou si avez besoin de vous rafraîchir la mémoire, [suivez la visite guidée de l’éditeur de rapport](service-the-report-editor-take-a-tour.md) avant de continuer.
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Ajouter une jauge radiale au rapport
À présent que notre jeu de données est importé, commençons à répondre à quelques questions.  Notre Directrice marketing veut savoir où nous en sommes par rapport aux objectifs de ventes de cette année. Une jauge est un [bon choix de visualisation](power-bi-report-visualizations.md) pour l’affichage de ce type d’information.

1. Dans le volet Champs, sélectionnez **Sales (Ventes)** > **This Year Sales (Ventes de cette année)** > **Value (Valeur)**.
   
    ![](media/service-report-create-new/power-bi-report-step1.png)
2. Convertissez l’élément visuel en Jauge en sélectionnant le modèle Jauge ![](media/service-report-create-new/powerbi-gauge-icon.png) dans le volet **Visualisations**.
   
    ![](media/service-report-create-new/power-bi-report-step2.png)
3. Faites glisser **Sales (Ventes)** > **This Year Sales (Ventes de cette année)** > **Goal (Objectif)** dans la zone **Target value (Valeur cible)**. Il semble que nous sommes très proches de notre objectif.
   
    ![](media/service-report-create-new/power-bi-report-step3.png)
4. Le moment est opportun pour [enregistrer votre rapport](service-report-save.md).
   
   ![](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Ajouter un graphique en aires et un segment au rapport
Notre Directrice marketing a des questions supplémentaires à nous poser. Elle souhaite savoir comment se comportent les ventes de cette année par rapport à l’année dernière. Elle souhaite voir les résultats par district.

1. Tout d’abord, nous allons libérer de l’espace sur notre canevas. Sélectionnez la jauge et déplacez-la dans l’angle supérieur droit. Ensuite, faites glisser un des angles de la jauge, puis réduisez la taille de celle-ci.
2. Désélectionnez la jauge. Dans le volet Champs, sélectionnez **Sales (Ventes)** > **This Year Sales (Ventes de cette année)** > **Value (Valeur)**, puis sélectionnez **Sales (Ventes)** > **Last Year Sales (Ventes de l’année dernière)**.
   
    ![](media/service-report-create-new/power-bi-report-step4.png)
3. Convertissez le visuel en graphique en aires en sélectionnant le modèle Graphique en aires ![](media/service-report-create-new/power-bi-areachart-icon.png) dans le volet **Visualisations**.
4. Sélectionnez **Time** > **Period** (Période) pour l’ajouter au puits **Axe**.
   
    ![](media/service-report-create-new/power-bi-report-step5.png)
5. Pour trier la visualisation, sélectionnez les points de suspension, puis choisissez **Trier par période**.
6. Nous allons à présent ajouter le segment. Sélectionnez une zone vide sur le canevas, puis choisissez le modèle de Segment ![](media/service-report-create-new/power-bi-slicer-icon.png). Cela a pour effet d’ajouter un segment vide à notre canevas.
   
    ![](media/service-report-create-new/power-bi-report-step6.png)    
7. Dans le volet Champs, sélectionnez **District** > **District**. Déplacez et redimensionnez le segment.
   
    ![](media/service-report-create-new/power-bi-report-step7.png)  
8. Utilisez le segment pour rechercher des modèles et des informations par secteur.
   
   ![](media/service-report-create-new/power-bi-slicer-video2.gif)  
9. Si vous le souhaitez, vous pouvez continuer à ajouter des visualisations.

## <a name="next-steps"></a>Étapes suivantes
* [Créer une copie d’un rapport](power-bi-report-copy.md)
* [Enregistrer le rapport](service-report-save.md)    
* [Ajouter une nouvelle page au rapport](power-bi-report-add-page.md)  
* Découvrez comment [épingler des visualisations à un tableau de bord](service-dashboard-pin-tile-from-report.md).    
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

