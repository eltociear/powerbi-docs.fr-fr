---
title: Créer un tableau de bord à partir d’un rapport
description: Créer un tableau de bord à partir d’un rapport
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/17/2019
ms.author: maggies
ms.openlocfilehash: 6d8a6a28d72ce6d0fa6123b15f9e692ed1cc4d44
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72543340"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Créer un tableau de bord à partir d’un rapport
Vous avez lu [Présentation des tableaux de bord dans Power BI](service-dashboards.md) et souhaitez maintenant créer les vôtres. Il existe différentes façons de créer un tableau de bord. Par exemple, vous pouvez créer un tableau de bord à partir d’un rapport, à partir de rien, à partir d’un jeu de données, en dupliquant un tableau de bord existant.  

Nous allons commencer par créer un tableau de bord simple et rapide affichant des visualisations d’un rapport déjà généré. 

Après avoir lu cet article, vous aurez une bonne compréhension des aspects suivants :
- Relation entre les tableaux de bord et les rapports
- Comment ouvrir le Mode Édition dans l’éditeur de rapport
- Comment épingler des vignettes 
- Comment naviguer entre un tableau de bord et un rapport 
 
![Tableau de bord](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

> [!NOTE] 
> Les tableaux de bord sont une fonctionnalité du service Power BI et non de Power BI Desktop. Vous ne créez pas de tableaux de bord dans les apps mobiles Power BI, mais vous pouvez [les afficher et les partager](consumer/mobile/mobile-apps-view-dashboard.md) à cet endroit.
>
> 

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Vidéo : Créer un tableau de bord en épinglant des éléments visuels et des images provenant d’un rapport
Regardez Amanda créer un tableau de bord en épinglant des visualisations et des images provenant d’un rapport. Ensuite, suivez les étapes décrites dans la section suivant [Importer un jeu de données avec un rapport](#import-a-dataset-with-a-report) pour essayer par vous-même avec l’exemple Analyse de l’approvisionnement.
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>Importer un jeu de données avec un rapport
Dans cette procédure étape par étape, nous allons importer l’un des exemples de jeu de données Power BI et l’utiliser pour créer notre tableau de bord. L’exemple que nous allons utiliser est un classeur Excel avec deux feuilles PowerView. Lorsque Power BI importe le classeur, il ajoute un jeu de données et un rapport à votre espace de travail. Le rapport est automatiquement créé à partir des feuilles PowerView.

1. Téléchargez le [fichier Excel](http://go.microsoft.com/fwlink/?LinkId=529784) exemple Analyse de l’approvisionnement. Nous vous recommandons de l’enregistrer dans votre OneDrive Entreprise.
2. Ouvrez le service Power BI dans votre navigateur (app.powerbi.com).
3. Dans le volet de navigation gauche, sélectionnez **Mon espace de travail**, puis **Obtenir les données**.

    ![Volet de navigation gauche](media/service-dashboard-create/power-bi-get-data-new-look.png)
5. Sous **Fichiers**, sélectionnez **Obtenir**.

   ![Obtenir les fichiers](media/service-dashboard-create/power-bi-select-files.png)
6. Naviguez jusqu'à l’emplacement où vous avez enregistré le fichier Excel de l’exemple Analyse de l’approvisionnement. Sélectionnez-le et choisissez **Connecter**.

   ![Se connecter aux fichiers](media/service-dashboard-create/power-bi-connectnew.png)
7. Dans cet exercice, sélectionnez **Importer**.

    ![fenêtre OneDrive Entreprise](media/service-dashboard-create/power-bi-import.png)
8. Lorsque le message de réussite s’affiche, sélectionnez **x** pour l’ignorer.

   ![Message de réussite](media/service-dashboard-create/power-bi-view-datasetnew.png)

> [!TIP]
> Le saviez-vous ? Vous pouvez réduire la barre de navigation de gauche en sélectionnant l'icône à trois lignes en haut ![Icône pour afficher ou masquer le volet de navigation](media/service-dashboard-create/power-bi-new-look-hide-nav-pane.png). Vous disposez ainsi de plus d’espace pour le rapport lui-même.

### <a name="open-the-report-and-pin-tiles-to-your-dashboard"></a>Ouvrir le rapport et épingler des vignettes à votre tableau de bord
1. Dans le même espace de travail, sélectionnez l’onglet **Rapports**, puis l’**Exemple Analyse de l’approvisionnement** pour ouvrir le rapport.

    ![Onglet Rapports](media/service-dashboard-create/power-bi-reports.png) Le rapport s’ouvre en mode Lecture. Notez qu’il comporte deux onglets sur la gauche : **Discount Analysis** (Analyse des remises) et **Spend Overview** (Vue d’ensemble des dépenses). Chaque onglet représente une page du rapport.

2. Sélectionnez **Plus d’options (...)**  > **Modifier le rapport** pour ouvrir le rapport en Mode Édition.

    ![Rapport en mode Lecture](media/service-dashboard-create/power-bi-reading-view.png)
3. Pointez sur une visualisation pour afficher les options disponibles. Pour ajouter une visualisation à un tableau de bord, sélectionnez l’icône d’épingle ![Icône Épingler](media/service-dashboard-create/power-bi-pin-icon.png).

    ![Pointer sur une vignette](media/service-dashboard-create/power-bi-hover.png)
4. Étant donné que nous créons un tableau de bord, sélectionnez l’option **Nouveau tableau de bord** et donnez-lui un nom.

    ![boîte de dialogue Épingler au tableau de bord](media/service-dashboard-create/power-bi-pin-tile.png)
5. Lorsque vous sélectionnez **Épingler**, Power BI crée un nouveau tableau de bord dans l’espace de travail actuel. Lorsque le message **Épinglé au tableau de bord** s’affiche, sélectionnez **Accéder au tableau de bord**. Si vous êtes invité à enregistrer le rapport, choisissez **Enregistrer**.

    ![Message de réussite](media/service-dashboard-create/power-bi-pin-success.png)

    Power BI ouvre le nouveau tableau de bord. Il comporte une vignette, la visualisation que vous venez d’épingler.

   ![tableau de bord avec une seule vignette](media/service-dashboard-create/power-bi-pinned.png)
7. Pour revenir au rapport, sélectionnez la vignette. Épinglez d’autres vignettes au nouveau tableau de bord. Lorsque la fenêtre **Épingler au tableau de bord** s’affiche, sélectionnez **Tableau de bord existant**.  

   ![boîte de dialogue Épingler au tableau de bord](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>Épingler la totalité d’une page de rapport à un tableau de bord
Au lieu d’épingler un visuel à la fois, vous pouvez [épingler une page de rapport tout entière comme *vignette dynamique*](service-dashboard-pin-live-tile-from-report.md). C’est parti.

1. Dans l’éditeur de rapport, sélectionnez l’onglet **Vue d’ensemble des dépenses** pour ouvrir la deuxième page du rapport.

   ![Onglet Rapport](media/service-dashboard-create/power-bi-page-tab.png)

2. Nous souhaitons afficher tous visuels du rapport sur votre tableau de bord. Dans le coin supérieur droit de la barre de menus, sélectionnez **Épingler une page dynamique**. Dans un tableau de bord, les vignettes de pages dynamiques se mettent à jour à chaque fois que la page est actualisée.

   ![Coin supérieur droit de l’éditeur de rapport](media/service-dashboard-create/power-bi-pin-live.png)

3. Lorsque la fenêtre **Épingler au tableau de bord** s’affiche, sélectionnez **Tableau de bord existant**.

   ![boîte de dialogue Épingler au tableau de bord](media/service-dashboard-create/power-bi-pin-live2.png)

4. Dès que le message de réussite s’affiche, sélectionnez **Accéder au tableau de bord**. Les vignettes que vous avez épinglées à partir du rapport apparaîtront. Dans l’exemple ci-dessous, nous avons épinglé deux vignettes provenant de la première page du rapport et une vignette dynamique correspondant à la deuxième page du rapport.

   ![Tableau de bord](media/service-dashboard-create/power-bi-dashboard.png)

## <a name="next-steps"></a>Étapes suivantes
Félicitations pour la création de votre premier tableau de bord ! Maintenant que vous avez un tableau de bord, vous pouvez vous en servir pour de multiples usages. Suivez l’un des articles suggérés ci-dessous, ou commencez à explorer par vous-même : 

* [Redimensionner et déplacer des vignettes](service-dashboard-edit-tile.md)
* [Toutes les informations dont vous avez besoin sur les vignettes du tableau de bord](service-dashboard-tiles.md)
* [Partager votre tableau de bord en créant une application](service-create-workspaces.md)
* [Power BI – Concepts de base](service-basic-concepts.md)
* [Conseils pour la conception d’un tableau de bord réussi](service-dashboards-design-tips.md)

D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).
