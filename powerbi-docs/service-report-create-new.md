---
title: Créer un rapport à partir d’un jeu de données
description: Créer un rapport Power BI à partir d’un jeu de données.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 6b69c2b1fa811d395a26403de852c44af33491c7
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770227"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>Créer un rapport dans le service Power BI en important un jeu de données
Vous avez lu [apports dans Power BI](consumer/end-user-reports.md) et vous souhaitez maintenant créer vos propres rapports. Il existe différentes façons de créer un rapport. Dans cet article, nous allons commencer en créant un rapport de base dans le service Power BI à partir d’un jeu de données Excel. Une fois que vous comprenez les principes fondamentaux de création d’un rapport, consultez le [étapes suivantes](#next-steps) à la fin pour en savoir plus avancée des rubriques de rapport.  

## <a name="prerequisites"></a>Conditions préalables
- [S’inscrire pour le service Power BI](service-self-service-signup-for-power-bi.md). Pour créer des rapports à l’aide de Power BI Desktop, consultez [affichage rapport Desktop](desktop-report-view.md). 
- [Télécharger le jeu de données Excel d’exemple Retail Analysis](http://go.microsoft.com/fwlink/?LinkId=529778) et l’enregistrer dans OneDrive entreprise ou localement.

## <a name="import-the-dataset"></a>Importer le jeu de données
Cette méthode de création d’un rapport démarre avec un jeu de données et un canevas de rapport vide. Vous pouvez suivre la procédure dans le jeu de données Excel d’exemple analyse de vente au détail.

1. Nous allons créer le rapport dans un espace de travail du service Power BI, par conséquent, sélectionnez un espace de travail existant ou créer un.
   
   ![liste des espaces de travail d’application](media/service-report-create-new/power-bi-workspaces2.png)
2. En bas du volet de navigation gauche, sélectionnez **obtenir des données**.
   
   ![Obtenir les données](media/service-report-create-new/power-bi-get-data3.png)
3. Sélectionnez **Fichiers**, puis accédez à l’emplacement dans lequel vous avez enregistré l’exemple Analyse de la vente au détail.
   
    ![sélectionner Fichiers](media/service-report-create-new/power-bi-select-files.png)
4. Dans cet exercice, sélectionnez **Importer**.
   
   ![sélectionner Importer](media/service-report-create-new/power-bi-import.png)
5. Une fois le jeu de données importé, sélectionnez **Afficher le jeu de données**.
   
   ![sélectionner Afficher le jeu de données](media/service-report-create-new/power-bi-view-dataset.png)
6. L’affichage d’un jeu de données a pour effet d’ouvrir l’éditeur de rapport.  Vous y voyez un canevas vide et des outils d’édition de rapports.
   
   ![éditeur de rapport](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Si vous n’êtes pas familiarisé avec le canevas de modification de rapport ou que vous avez besoin d’un rappel, [visite guidée de l’éditeur de rapport](service-the-report-editor-take-a-tour.md) avant de continuer. > 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Ajouter une jauge radiale au rapport
À présent que notre jeu de données est importé, commençons à répondre à quelques questions.  Notre Directrice marketing veut savoir où nous en sommes par rapport aux objectifs de ventes de cette année. Une jauge est un [bon choix de visualisation](visuals/power-bi-report-visualizations.md) pour l’affichage de ce type d’information.

1. Dans le volet Champs, sélectionnez **Sales (Ventes)**  > **This Year Sales (Ventes de cette année)**  > **Value (Valeur)** .
   
    ![histogramme dans l’éditeur de rapport](media/service-report-create-new/power-bi-report-step1.png)
2. Convertissez le visuel en jauge en sélectionnant le modèle Jauge ![icône de jauge](media/service-report-create-new/powerbi-gauge-icon.png) dans le volet **Visualisations**.
   
    ![visuel Jauge dans l’éditeur de rapport](media/service-report-create-new/power-bi-report-step2.png)
3. Faites glisser **Sales (Ventes)**  > **This Year Sales (Ventes de cette année)**  > **Goal (Objectif)** dans la zone **Target value (Valeur cible)** . Il semble que nous sommes très proches de notre objectif.
   
    ![visuel Jauge avec un objectif de Valeur cible](media/service-report-create-new/power-bi-report-step3.png)
4. Maintenant serait un bon moment pour enregistrer votre rapport.
   
   ![menu Fichier](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Ajouter un graphique en aires et un segment au rapport
Notre Directrice marketing a des questions supplémentaires à nous poser. Elle souhaite savoir comment se comportent les ventes de cette année par rapport à l’année dernière. Elle souhaite voir les résultats par district.

1. Tout d’abord, nous allons libérer de l’espace sur notre canevas. Sélectionnez la jauge et déplacez-la dans l’angle supérieur droit. Ensuite, faites glisser un des angles de la jauge, puis réduisez la taille de celle-ci.
2. Désélectionnez la jauge. Dans le volet Champs, sélectionnez **Sales (Ventes)**  > **This Year Sales (Ventes de cette année)**  > **Value (Valeur)** , puis sélectionnez **Sales (Ventes)**  > **Last Year Sales (Ventes de l’année dernière)** .
   
    ![éditeur de rapport avec une jauge et un histogramme](media/service-report-create-new/power-bi-report-step4.png)
3. Convertissez le visuel en graphique en aires en sélectionnant le modèle Graphique en aires ![icône de graphique](media/service-report-create-new/power-bi-areachart-icon.png) dans le volet **Visualisations**.
4. Sélectionnez **Time** > **Period** (Période) pour l’ajouter au puits **Axe**.
   
    ![éditeur de rapport avec un graphique en aires actif](media/service-report-create-new/power-bi-report-step5.png)
5. Pour trier la visualisation par période, sélectionnez les points de suspension, puis choisissez **Trier par période**.
6. Nous allons à présent ajouter le segment. Sélectionnez une zone vide sur le canevas et choisissez le modèle Segment ![icône de segment](media/service-report-create-new/power-bi-slicer-icon.png) . Nous disposons désormais d’un segment vide sur notre canevas.
   
    ![canevas de rapport](media/service-report-create-new/power-bi-report-step6.png)    
7. Dans le volet Champs, sélectionnez **District** > **District**. Déplacez et redimensionnez le segment.
   
    ![Éditeur de rapport, ajouter District](media/service-report-create-new/power-bi-report-step7.png)  
8. Utilisez le segment pour rechercher des modèles et des informations par secteur.
   
   ![vidéo d’utilisation d’un segment](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continuer d’explorer vos données et d’ajouter des visualisations. Lorsque vous trouvez des informations particulièrement intéressantes, [épinglez-les à un tableau de bord](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Étapes suivantes

* Découvrez comment [épingler des visualisations à un tableau de bord](service-dashboard-pin-tile-from-report.md).   
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

