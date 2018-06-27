---
title: 'Créer un rapport à partir d’un jeu de données '
description: Créez un rapport Power BI à partir d’un jeu de données.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/24/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 377ea4acc1a6fb41101571ac3ed0be2f3e50889b
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34246154"
---
# <a name="create-a-new-report-in-power-bi-service-by-importing-a-dataset"></a>Créer un nouveau rapport du service Power BI en important un jeu de données
Vous avez lu [apports dans Power BI](service-reports.md) et vous souhaitez maintenant créer vos propres rapports. Il existe de nombreuses façons de créer un rapport. Dans cet article, nous allons commencer par créer un rapport très basique à partir d’un jeu de données Excel à l’aide du service Power BI. Lorsque vous aurez compris les principes fondamentaux de la création d’un rapport, les **Étapes suivantes** plus bas vous dirigeront vers des rubriques plus avancées concernant les rapports.  

> **CONSEIL** : pour créer un rapport en copiant un rapport existant, voir [Copier un rapport](power-bi-report-copy.md).
> 
### <a name="prerequisites"></a>Conditions préalables
- Service Power BI (pour créer des rapports avec Power BI Desktop, consultez [Affichage du rapport Desktop](desktop-report-view.md))  
- Jeu de données d’exemple Analyse de la vente au détail

## <a name="import-the-dataset"></a>Importer le jeu de données
Cette méthode de création d’un rapport démarre avec un jeu de données et un canevas de rapport vide. Pour suivre la procédure, [téléchargez l’exemple de jeu de données Excel Analyse de la vente au détail](http://go.microsoft.com/fwlink/?LinkId=529778) et enregistrez-le dans OneDrive Entreprise (recommandé) ou localement.

1. Nous allons créer le rapport dans un espace de travail du service Power BI. Par conséquent, sélectionnez un espace de travail existant ou créez-en un.
   
   ![liste des espaces de travail d’application](media/service-report-create-new/power-bi-workspaces2.png)
2. En bas du volet de navigation gauche, sélectionnez **Obtenir des données**.
   
   ![Obtenir des données](media/service-report-create-new/power-bi-get-data3.png)
3. Sélectionnez **Fichiers**, puis accédez à l’emplacement dans lequel vous avez enregistré l’exemple Analyse de la vente au détail.
   
    ![sélectionner Fichiers](media/service-report-create-new/power-bi-select-files.png)
4. Dans cet exercice, sélectionnez **Importer**.
   
   ![sélectionner Importer](media/service-report-create-new/power-bi-import.png)
5. Une fois le jeu de données importé, sélectionnez **Afficher le jeu de données**.
   
   ![sélectionner Afficher le jeu de données](media/service-report-create-new/power-bi-view-dataset.png)
6. L’affichage d’un jeu de données a pour effet d’ouvrir l’éditeur de rapport.  Vous y voyez un canevas vide et des outils d’édition de rapports.
   
   ![éditeur de rapport](media/service-report-create-new/power-bi-blank-report.png)

> **CONSEIL** : si vous n’êtes pas familiarisé avec le canevas de modification de rapport ou si avez besoin de vous rafraîchir la mémoire, [suivez la visite guidée de l’éditeur de rapport](service-the-report-editor-take-a-tour.md) avant de continuer.
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Ajouter une jauge radiale au rapport
À présent que notre jeu de données est importé, commençons à répondre à quelques questions.  Notre Directrice marketing veut savoir où nous en sommes par rapport aux objectifs de ventes de cette année. Une jauge est un [bon choix de visualisation](power-bi-report-visualizations.md) pour l’affichage de ce type d’information.

1. Dans le volet Champs, sélectionnez **Sales (Ventes)** > **This Year Sales (Ventes de cette année)** > **Value (Valeur)**.
   
    ![histogramme dans l’éditeur de rapport](media/service-report-create-new/power-bi-report-step1.png)
2. Convertissez le visuel en jauge en sélectionnant le modèle Jauge ![icône de jauge](media/service-report-create-new/powerbi-gauge-icon.png) dans le volet **Visualisations**.
   
    ![visuel Jauge dans l’éditeur de rapport](media/service-report-create-new/power-bi-report-step2.png)
3. Faites glisser **Sales (Ventes)** > **This Year Sales (Ventes de cette année)** > **Goal (Objectif)** dans la zone **Target value (Valeur cible)**. Il semble que nous sommes très proches de notre objectif.
   
    ![visuel Jauge avec un objectif de Valeur cible](media/service-report-create-new/power-bi-report-step3.png)
4. Le moment est opportun pour [enregistrer votre rapport](service-report-save.md).
   
   ![menu Fichier](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Ajouter un graphique en aires et un segment au rapport
Notre Directrice marketing a des questions supplémentaires à nous poser. Elle souhaite savoir comment se comportent les ventes de cette année par rapport à l’année dernière. Elle souhaite voir les résultats par district.

1. Tout d’abord, nous allons libérer de l’espace sur notre canevas. Sélectionnez la jauge et déplacez-la dans l’angle supérieur droit. Ensuite, faites glisser un des angles de la jauge, puis réduisez la taille de celle-ci.
2. Désélectionnez la jauge. Dans le volet Champs, sélectionnez **Sales (Ventes)** > **This Year Sales (Ventes de cette année)** > **Value (Valeur)**, puis sélectionnez **Sales (Ventes)** > **Last Year Sales (Ventes de l’année dernière)**.
   
    ![éditeur de rapport avec une jauge et un histogramme](media/service-report-create-new/power-bi-report-step4.png)
3. Convertissez le visuel en graphique en aires en sélectionnant le modèle Graphique en aires ![icône de graphique](media/service-report-create-new/power-bi-areachart-icon.png) dans le volet **Visualisations**.
4. Sélectionnez **Time** > **Period** (Période) pour l’ajouter au puits **Axe**.
   
    ![éditeur de rapport avec un graphique en aires actif](media/service-report-create-new/power-bi-report-step5.png)
5. Pour trier la visualisation par période, sélectionnez les points de suspension, puis choisissez **Trier par période**.
6. Nous allons à présent ajouter le segment. Sélectionnez une zone vide sur le canevas et choisissez le modèle Segment ![icône de segment](media/service-report-create-new/power-bi-slicer-icon.png)    . Cela a pour effet d’ajouter un segment vide à notre canevas.
   
    ![canevas de rapport](media/service-report-create-new/power-bi-report-step6.png)    
7. Dans le volet Champs, sélectionnez **District** > **District**. Déplacez et redimensionnez le segment.
   
    ![Éditeur de rapport, ajouter District](media/service-report-create-new/power-bi-report-step7.png)  
8. Utilisez le segment pour rechercher des modèles et des informations par secteur.
   
   ![vidéo d’utilisation d’un segment](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continuer d’explorer vos données et d’ajouter des visualisations. Lorsque vous trouvez des informations particulièrement intéressantes, [épinglez-les à un tableau de bord](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Étapes suivantes
* [Ajouter une nouvelle page au rapport](power-bi-report-add-page.md)  
* Découvrez comment [épingler des visualisations à un tableau de bord](service-dashboard-pin-tile-from-report.md).   
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

