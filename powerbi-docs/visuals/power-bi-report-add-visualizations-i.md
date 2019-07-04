---
title: Partie 1, Ajouter des visualisations à un rapport Power BI
description: Partie 1, Ajouter des visualisations à un rapport Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299214"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Partie 1, Ajouter des visualisations à un rapport Power BI

Cet article explique brièvement comment créer une visualisation dans un rapport. Il s’applique à la fois au service Power BI et à Power BI Desktop. Pour un contenu plus avancé, [consultez la partie 2](power-bi-report-add-visualizations-ii.md) de cette série. Regardez Amanda montrer différentes manières de créer, modifier et mettre en forme les visuels sur un canevas de rapport. Essayez ensuite par vous-même d’utiliser l’[exemple Ventes et marketing](../sample-datasets.md) pour créer votre propre rapport.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Ouvrir un rapport et ajouter une page vierge

1. Ouvrez un [rapport en Mode Edition](../service-interact-with-a-report-in-editing-view.md).

    Ce didacticiel s’appuie sur l’exemple [Vente et marketing](../sample-datasets.md).

1. Si le volet **Champs** n’est pas visible, sélectionnez l’icône de flèche pour l’ouvrir.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Ajoutez une page vierge au rapport.

## <a name="add-visualizations-to-the-report"></a>Ajouter des visualisations au rapport

1. Créez une visualisation en sélectionnant un champ dans le volet **Champs**.

    Commencez par un champ numérique comme **SalesFact** > **Sales $** . Power BI crée un histogramme avec une seule colonne.

    ![Capture d’écran d’un histogramme avec une seule colonne.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    Ou commencez par un champ de catégorie, tel que **Nom** ou **Produit**. Power BI crée une table et ajoute ce champ à la zone **Valeurs**.

    ![Fichier GIF d’une personne en sélectionnant Produit, puis la catégorie, pour créer une table.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Ou, commencez par un champ géographique, tel que **Geo** > **Ville**. Power BI et Bing Cartes créent une visualisation de carte.

    ![Capture d’écran d’une visualisation de carte.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Créez une visualisation, puis modifiez son type. Sélectionnez **Produit** > **Catégorie**, puis **Produit** > **Quantité de produit** pour ajouter ces éléments à la zone **Valeurs**.

   ![Capture d’écran du volet Champs avec la zone Valeurs.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Changez la visualisation en histogramme en sélectionnant l’icône d’**histogramme empilé**.

   ![Capture d’écran du volet Visualisation avec l’icône de l’histogramme empilé.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Quand vous créez des visualisations dans votre rapport, vous pouvez les [épingler à votre tableau de bord](../service-dashboard-pin-tile-from-report.md). Pour épingler la visualisation, sélectionnez l’icône d’épingle ![Capture d’écran de l’icône d’épingle](media/power-bi-report-add-visualizations-i/pinnooutline.png).

   ![Capture d’écran de visualisation d’un histogramme avec l’icône d’épingle.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Étapes suivantes

 Passez à :

* [Partie 2 : Ajouter des visualisations à un rapport Power BI](power-bi-report-add-visualizations-ii.md)

* [interagir avec les visualisations](../consumer/end-user-reading-view.md) dans le rapport ;

* [exploiter encore davantage les visualisations](power-bi-report-visualizations.md),

* [enregistrer votre rapport](../service-report-save.md).
