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
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 52c0211aea0462e0bf79d7a48808f1f826c09fb6
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "60978552"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>Partie 1, Ajouter des visualisations à un rapport Power BI
Cet article explique brièvement comment créer une visualisation dans un rapport à l’aide du service Power BI ou de Power BI Desktop.  Pour un contenu plus avancé, [consultez la partie 2](power-bi-report-add-visualizations-ii.md). Regardez Amanda montrer différentes manières de créer, modifier et mettre en forme les visuels sur un canevas de rapport. Essayez ensuite par vous-même d’utiliser l’[exemple Ventes et marketing](../sample-datasets.md) pour créer votre propre rapport.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Ouvrir un rapport et ajouter une page vierge
1. Ouvrez un [rapport en Mode Edition](../consumer/end-user-reading-view.md). Ce didacticiel s’appuie sur l’exemple [Vente et marketing](../sample-datasets.md).
2. Si le volet Champs n’est pas visible, sélectionnez l’icône de flèche pour l’ouvrir. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. Ajoutez une page vierge au rapport.

## <a name="add-visualizations-to-the-report"></a>Ajouter des visualisations au rapport
1. Créez une visualisation en sélectionnant un champ dans le volet **Champs**.  
   
   **Commencez par un champ numérique** comme SalesFact > Sales $ (Ventes USD). Power BI crée un histogramme avec une seule colonne.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **Ou, commencez avec un champ de catégorie**, comme Nom ou Produit : Power BI crée une table et ajoute ce champ au puits **Valeurs**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **Ou, commencez avec un champ géographique** , tel que Geo > City (Ville). Power BI et Bing Cartes créent une visualisation de carte.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Créez une visualisation, puis modifiez son type. Sélectionnez **Product > Category** (Produit > Catégorie), puis **Product > Count of Product** (Produit > Quantité) pour ajouter ces éléments au puits **Valeurs**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Changez la visualisation en histogramme en sélectionnant l’icône d’histogramme.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. Quand vous créez des visualisations dans votre rapport, vous pouvez les [épingler à votre tableau de bord](../service-dashboard-pin-tile-from-report.md). Pour épingler la visualisation, sélectionnez l’icône d’épingle ![](media/power-bi-report-add-visualizations-i/pinnooutline.png).
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>Étapes suivantes
 Passez à [Partie 2 : Ajouter des visualisations à un rapport Power BI](power-bi-report-add-visualizations-ii.md)
   
   [interagir avec les visualisations](../consumer/end-user-reading-view.md) dans le rapport ;
   
   [exploiter encore davantage les visualisations](power-bi-report-visualizations.md),
   
   [enregistrer votre rapport](../service-report-save.md).
