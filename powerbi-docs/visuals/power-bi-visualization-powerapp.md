---
title: Incorporer une nouvelle application Power Apps dans un rapport Power BI
description: Incorporer une application qui utilise la même source de données et peut être filtrée comme d’autres éléments de rapport
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 06/01/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 1c4086d6ab71bd96ba7ac6c6985161d28a4dcb8b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418874"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Tutoriel : Incorporer un nouveau visuel Power Apps dans un rapport Power BI

Dans ce tutoriel, vous utilisez le visuel Power Apps pour créer une application incorporée dans un exemple de rapport Power BI. Cette application interagit avec d’autres visuels de ce rapport.

Si vous n’avez pas d’abonnement Power Apps, [créez un compte gratuit](https://make.powerapps.com/signup?redirect=marketing&email=) avant de commencer.

Dans ce tutoriel, vous allez découvrir comment :
> [!div class="checklist"]
> * Ajouter un visuel Power Apps à un rapport Power BI
> * Utiliser Power Apps pour créer une nouvelle application qui utilise les données du rapport Power BI
> * Afficher et interagir avec le visuel Power Apps dans le rapport

## <a name="prerequisites"></a>Prérequis

* Navigateur[Google Chrome](https://www.google.com/chrome/browser/) ou [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* [Abonnement Power BI](../fundamentals/service-self-service-signup-for-power-bi.md), avec [l’exemple Analyse des opportunités](../create-reports/sample-opportunity-analysis.md#get-the-content-pack-for-this-sample) installé
* Savoir [créer des applications dans Power Apps](/powerapps/maker/canvas-apps/data-platform-create-app-scratch) et [modifier des rapports Power BI](../create-reports/service-the-report-editor-take-a-tour.md)



## <a name="create-a-new-app"></a>Créer une application
Quand vous ajoutez le visuel Power Apps à votre rapport, l’application lance Power Apps Studio avec une connexion de données active entre Power Apps et Power BI.

1. Ouvrez l’exemple de rapport Analyse des opportunités, puis sélectionnez la page *Upcoming Opportunities* (Opportunités à venir). 


2. Déplacez et redimensionnez certaines des vignettes de rapport afin de libérer de l’espace pour le nouveau visuel.

    ![Déplacer et redimensionner des vignettes de rapport](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. Dans le volet Visualisations, sélectionnez l’icône Power Apps, puis redimensionnez le visuel pour l’ajuster à l’espace que vous venez de créer.

    ![Volet Visualisation avec l’icône Power Apps sélectionnée](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. Dans le volet **Champs**, sélectionnez **Nom**, **Code du produit** et **Étape de vente**. 

    ![sélectionner des champs](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. Sur le visuel Power Apps, sélectionnez l’environnement Power Apps où vous souhaitez créer l’application, puis choisissez **Créer**.

    ![Créer une application](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    Dans Power Apps Studio, vous voyez qu’une application de base est créée avec une *galerie* qui affiche l’un des champs que vous avez sélectionnés dans Power BI.

    ![Power Apps s’ouvre](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Redimensionnez la galerie afin qu’elle n’occupe qu’une moitié de l’écran. 

6. Dans le volet gauche, sélectionnez **Screen1**, puis affectez « LightBlue » à la propriété **Fill** de l’écran (pour optimiser son affichage dans le rapport).

    ![palette de couleurs](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Libérez de l’espace pour un contrôle Étiquette. 

    ![modifier les dimensions de la galerie](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. Sous **Galerie**, insérez un contrôle Étiquette de texte.

   ![contrôle étiquette](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Faites glisser l’étiquette vers le bas de votre visuel. Définissez la propriété **Texte** sur `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Le nombre total d’opportunités dans le jeu de données est à présent affiché.

    ![Application avec la galerie redimensionnée](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![Application avec étiquette mise à jour](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Enregistrez l’application sous le nom « Application Opportunités ». 

    ![enregistrer l’application](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Afficher l’application dans le rapport
L’application est désormais disponible dans le rapport Power BI et interagit avec les autres visuels, car elle partage la même source de données.

![Application dans un rapport Power BI](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

Dans le rapport Power BI, sélectionnez **Jan** dans le segment pour filtrer le rapport entier, dont les données dans l’application.

![rapport filtré](media/power-bi-visualization-powerapp/power-bi-last.png)

Notez que le nombre d’opportunités dans l’application correspond au nombre figurant en haut à gauche du rapport. Vous pouvez sélectionner d’autres éléments dans le rapport et les données dans les mises à jour de l’application.


## <a name="clean-up-resources"></a>Nettoyer les ressources
Si vous ne souhaitez plus utiliser l’exemple Analyse des opportunités, vous pouvez supprimer le tableau de bord, le rapport et le jeu de données.

## <a name="limitations-and-considerations"></a>Considérations et limitations
Pour plus d’informations sur la résolution des problèmes, consultez [Visuel Power Apps pour Power BI](/powerapps/maker/canvas-apps/powerapps-custom-visual#limitations-of-the-power-apps-visual)

## <a name="next-steps"></a>Étapes suivantes
[Visuel de Questions et réponses](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[Tutoriel : Incorporer un visuel Power Apps dans un rapport Power BI](/powerapps/maker/canvas-apps/powerapps-custom-visual)