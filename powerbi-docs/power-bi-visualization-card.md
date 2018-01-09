---
title: "Visualisations de carte (vignettes représentant un grand nombre)"
description: "Créer une visualisation de carte dans Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/24/2017
ms.author: mihart
ms.openlocfilehash: 1136aae9af4481a1d55ca3d11ed300242aab187b
ms.sourcegitcommit: 74fbbca81a056dda19b3647ae058005aba5296f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2018
---
# <a name="card-visualizations"></a>Visualisations de carte
Vous pouvez parfois vouloir suivre un nombre unique dans votre tableau de bord ou rapport Power BI pour l’importance qu’il représente, qu’il s’agisse du total des ventes, de la part de marché d’une année sur l’autre ou du nombre total d’opportunités. Ce type de visualisation est appelé *carte*. Avec la plupart des visualisations Power BI natives, des cartes peuvent être créées à l’aide de l’éditeur de rapport ou dans Questions et réponses.

![visualisation de carte](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Créer une carte à l’aide de l’éditeur de rapport
Ces instructions s’appliquent à l’exemple Analyse de la vente au détail. Pour effectuer la procédure, [téléchargez l’exemple](sample-datasets.md) pour le service Power BI (app.powerbi.com) ou Power BI Desktop.   

1. Démarrez sur une [page de rapport vierge](power-bi-report-add-page.md), puis sélectionnez le champ **Store (Magasin)** \> **Open store count (Nombre de magasins ouverts)**. Si vous utilisez le service Power BI, vous devez ouvrir le rapport en [mode Édition](service-interact-with-a-report-in-editing-view.md).

    Power BI crée un histogramme à partir d’un seul nombre.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. Dans le volet Visualisations, sélectionnez l’icône Carte.

   ![](media/power-bi-visualization-card/pbi_changechartcard.png)
6. Pointez le curseur sur la carte, puis sélectionnez l’icône en forme d’épingle ![](media/power-bi-visualization-card/pbi_pintile.png) pour ajouter la visualisation au tableau de bord.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Épinglez la vignette à un tableau de bord existant ou à un nouveau tableau de bord.

   * Tableau de bord existant : sélectionnez le nom du tableau de bord dans la liste déroulante.
   * Nouveau tableau de bord : tapez le nom du nouveau tableau de bord.
8. Sélectionnez **Épingler**.

   Un message de réussite (dans l’angle supérieur droit) vous indique que la visualisation a été ajoutée, sous forme de vignette, à votre tableau de bord.

   ![](media/power-bi-visualization-card/power-bi-pin-success-message.png)
9. Sélectionnez **Accéder au tableau de bord**. Ici, vous pouvez [modifier et déplacer](service-dashboard-edit-tile.md) la visualisation épinglée.


## <a name="create-a-card-from-the-qa-question-box"></a>Créer une carte à partir de la zone de question Questions et réponses
La zone de question Questions et réponses est le moyen le plus simple de créer une carte. Elle est disponible dans le service Power BI (app.powerbi.com) à partir d’un tableau de bord ou rapport. Les étapes ci-dessous décrivent la création d’une carte à partir d’un tableau de bord dans le service Power BI. Si vous souhaitez créer une carte à l’aide de Questions et réponses dans Power BI Desktop, [suivez ces instructions](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA) pour accéder à la préversion de Questions et réponses pour les rapports Power BI Desktop.

1. Créez un [tableau de bord](service-dashboards.md) et [obtenez des données](service-get-data.md). Cet exemple utilise l’[exemple Analyse des opportunités](sample-opportunity-analysis.md).

1. En haut de votre tableau de bord, commencez à taper ce que vous voulez savoir sur vos données dans la zone de question. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

>**Conseil** : à partir d’un rapport Power BI, en [mode Édition](service-reading-view-and-editing-view.md), sélectionnez **Poser une question** dans la barre de menus supérieure. Dans un rapport Power BI Desktop, recherchez un espace vide et double-cliquez pour ouvrir une zone de question.

3. Par exemple, tapez « nombre d’opportunités » dans la zone de question.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   Celle-ci vous propose des suggestions et des nouvelles formulations, puis affiche le nombre total.  
4. Sélectionnez l’icône d’épingle ![](media/power-bi-visualization-card/pbi_pintile.png) dans l’angle supérieur droit pour ajouter la carte à un tableau de bord.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. Épinglez la carte, sous forme de vignette, à un tableau de bord existant ou nouveau.

   * Tableau de bord existant : sélectionnez le nom du tableau de bord dans la liste déroulante. Votre choix est limité aux tableaux de bord figurant à l’intérieur de l’espace de travail actuel.
   * Nouveau tableau de bord : tapez le nom du nouveau tableau de bord pour ajouter celui-ci à votre espace de travail actuel.
6. Sélectionnez **Épingler**.

   Un message de réussite (dans l’angle supérieur droit) vous indique que la visualisation a été ajoutée, sous forme de vignette, à votre tableau de bord.  

   ![](media/power-bi-visualization-card/power-bi-success.png)
7. Sélectionnez **Accéder au tableau de bord** pour voir la nouvelle vignette. Vous pouvez [renommer, redimensionner et repositionner la vignette, et y ajouter également un lien hypertexte](service-dashboard-edit-tile.md) depuis votre tableau de bord.

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
- Si vous ne voyez pas de zone de question, contactez l’administrateur système ou du locataire.    
- Si vous utilisez Power BI Desktop et que le fait de double-cliquer sur un espace vide dans un rapport n’ouvre pas Questions et réponses, vous devez peut-être l’activer.  Sélectionnez **Fichier > Options et paramètres > Options > Fonctionnalités en préversion** et redémarrez Power BI Desktop.


## <a name="next-steps"></a>Étapes suivantes
[Vignettes d’un tableau de bord dans Power BI](service-dashboard-tiles.md)

[Tableaux de bord dans Power BI](service-dashboards.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
