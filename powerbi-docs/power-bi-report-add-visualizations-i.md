---
title: "Partie 1, Ajouter des visualisations à un rapport Power BI (didacticiel)"
description: "Didacticiel : Partie 1, Ajouter des visualisations à un rapport Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: IkJda4O7oGs
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/08/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b81061c25b453fc35e1490c3ded2d9c9770d4599
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="part-i-add-visualizations-to-a-power-bi-report-tutorial"></a>Partie 1, Ajouter des visualisations à un rapport Power BI (didacticiel)
Cet article explique brièvement comment créer une visualisation dans un rapport.  Pour un contenu plus avancé, [consultez la partie 2](power-bi-report-add-visualizations-ii.md). Regardez Amanda montrer différentes manières de créer, modifier et mettre en forme les visuels sur un canevas de rapport. Essayez ensuite par vous-même d’utiliser l’[exemple Ventes et marketing](sample-datasets.md) pour créer votre propre rapport.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Ouvrir un rapport et ajouter une page vierge
1. Ouvrez un [rapport en Mode Edition](service-reading-view-and-editing-view.md). Ce didacticiel s’appuie sur l’exemple [Vente et marketing](sample-datasets.md).
2. Si le volet Champs n’est pas visible, sélectionnez l’icône de flèche pour l’ouvrir. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. [Ajoutez une page vierge au rapport](power-bi-report-add-page.md).

## <a name="add-visualizations-to-the-report"></a>Ajouter des visualisations au rapport
1. Créez une visualisation en sélectionnant un champ dans le volet **Champs**.  
   
   **Commencez avec un champ numérique** tel que Sales > Sales $ (Ventes > Ventes en $) : Power BI crée un histogramme d’une seule colonne.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **Commencez avec un champ de catégorie**, tel que Name (Nom) ou Product (Produit) : Power BI crée une table et ajoute ce champ à la zone **Valeurs**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **Commencez avec un champ géographique** , tel que Zone géographique > City (Ville). Power BI et Bing Cartes créent une visualisation de carte.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Créez une visualisation, puis modifiez son type. Sélectionnez **Product > Count of Product** (Produit > Quantité), puis **Product > Category** (Produit > Catégorie) pour ajouter ces éléments au puits **Valeurs**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Changez la visualisation en histogramme en sélectionnant l’icône d’histogramme.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. Quand vous créez des visualisations dans votre rapport, vous pouvez les [épingler à votre tableau de bord](service-dashboard-pin-tile-from-report.md). Pour épingler la visualisation, sélectionnez l’icône d’épingle ![](media/power-bi-report-add-visualizations-i/pinnooutline.png).
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
5. Vous pouvez maintenant :
   
   passer à la [Partie 2 : Ajouter des visualisations à un rapport Power BI](power-bi-report-add-visualizations-ii.md) ;
   
   [interagir avec les visualisations](service-reading-view-and-editing-view.md) dans le rapport ;
   
   [exploiter encore davantage les visualisations](power-bi-report-visualizations.md),
   
   [enregistrer votre rapport](service-report-save.md).

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](power-bi-report-visualizations.md).

[Rapports dans Power BI](service-reports.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

