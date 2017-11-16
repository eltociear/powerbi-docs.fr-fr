---
title: "Créer une vignette représentant un grand nombre à partir d’un rapport Power BI"
description: "Créer une vignette représentant un grand nombre à partir d’un rapport Power BI"
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 9f748ed1d3a34c6c6aceb14337bbb780598a15f9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="create-a-big-number-tile-from-a-power-bi-report"></a>Créer une vignette représentant un grand nombre à partir d’un rapport Power BI
Vous pouvez parfois vouloir suivre un nombre unique dans votre tableau de bord Power BI pour l’importance qu’il représente, qu’il s’agisse du total des ventes, de la part de marché d’une année sur l’autre ou du nombre total d’opportunités. Vous pouvez pour cela créer une vignette représentant un grand nombre en [posant une question dans la zone Q&R](power-bi-visualization-big-number.md) ou dans un rapport Power BI. Cet article explique comment en créer un dans un rapport.

1. Créez un [tableau de bord](service-dashboards.md) et [obtenez des données](service-get-data.md).
   
   Si vous voulez vous exercer sur des données, [téléchargez l’exemple Analyse de la vente au détail](sample-retail-analysis.md). 
2. Ouvrez le rapport en [mode Édition](service-reading-view-and-editing-view.md)
3. Dans le rapport, recherchez une page contenant un espace vide ou [ajoutez une nouvelle page au rapport](power-bi-report-add-page.md).
4. Dans la liste Champs, sélectionnez le champ numérique que vous voulez afficher.
   
   Dans cet exemple, **Open Store count** (Nombre de magasins ouverts) dans la table **Store** (Magasins). Power BI crée un histogramme à partir d’un seul nombre.
   
   ![](media/power-bi-visualization-big-number-report/pbi_rptnumbertilechart.png)
5. Dans le volet Visualisations, sélectionnez l’icône Carte.
   
   ![](media/power-bi-visualization-big-number-report/pbi_changechartcard.png)
6. Pointez le curseur sur une carte, puis sélectionnez l’icône en forme d’épingle ![](media/power-bi-visualization-big-number-report/pbi_pintile.png) pour ajouter la vignette au tableau de bord. 
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-icon.png)
7. Épinglez la vignette à un tableau de bord existant ou à un nouveau tableau de bord. 
   
   * Tableau de bord existant : sélectionnez le nom du tableau de bord dans la liste déroulante.
   * Nouveau tableau de bord : tapez le nom du nouveau tableau de bord.
8. Sélectionnez **Épingler**.
   
   Un message de réussite (dans l’angle supérieur droit) vous indique que la visualisation a été ajoutée, sous forme de vignette, à votre tableau de bord.
   
   ![](media/power-bi-visualization-big-number-report/power-bi-pin-success-message.png)
9. Sélectionnez **Accéder au tableau de bord**. Ici, vous pouvez [modifier et déplacer](service-dashboard-edit-tile.md) la visualisation épinglée.

## <a name="next-steps"></a>Étapes suivantes
[Vignettes d’un tableau de bord dans Power BI](service-dashboard-tiles.md)

[Tableaux de bord dans Power BI](service-dashboards.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

