---
title: Vignettes de tableau de bord dans Power BI pour les utilisateurs professionnels
description: Toutes les informations dont vous avez besoin sur les vignettes de tableau de bord dans Power BI pour les utilisateurs professionnels. Cela inclut les vignettes créées à partir de SQL Server Reporting Services (SSRS).
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 10/06/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: 67291ca77b161fab289ee0520287d832cce838f8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96389503"
---
# <a name="dashboard-tiles-in-power-bi"></a>Vignettes d’un tableau de bord dans Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Une vignette est une capture instantanée de vos données, épinglée à un tableau de bord par un *concepteur*. Les *concepteurs* peuvent créer des vignettes à partir d’un rapport, d’un jeu de données, d’un tableau de bord, de la zone Questions et réponses, d’Excel et de SSRS (SQL Server Reporting Services), et plus encore.  Cette capture d’écran montre différentes vignettes épinglées à un tableau de bord.

![tableau de bord Power BI](./media/end-user-tiles/power-bi-dash.png)


En plus des vignettes épinglées à partir de rapports, les *concepteurs* peuvent ajouter des vignettes autonomes directement sur le tableau de bord à l’aide de l’option **Ajouter une vignette**. Les vignettes autonomes incluent des zones de texte, des images, des vidéos, des données de streaming et du contenu web.

Vous avez du mal à comprendre les éléments qui composent Power BI ?  Consultez [Power BI - Concepts de base](end-user-basic-concepts.md).


## <a name="interacting-with-tiles-on-a-dashboard"></a>Interaction avec des vignettes dans un tableau de bord

1. Placez le curseur sur la vignette pour afficher les points de suspension.
   
    ![points de suspension de la vignette](./media/end-user-tiles/power-bi-ellipsis.png)
2. Sélectionnez les points de suspension pour ouvrir le menu des actions de la vignette. Les options disponibles varient en fonction de vos autorisations, du type de visuel et de la méthode utilisée pour créer la vignette. Par exemple, les éléments de menu disponibles pour les vignettes épinglées à partir de Q&A un sont différentes de celles épinglées à partir d’un rapport. Voici un menu d’actions pour une vignette créée à l’aide de Q&A.


   
    ![Capture d’écran montrant le menu avec neuf options.](./media/end-user-tiles/power-bi-qna-menu.png)

   
    Voici quelques-unes des actions disponibles à partir de ces menus :
   
   * [Ouvrir le rapport utilisé pour créer la vignette ](end-user-reports.md) ![icône de rapport](./media/end-user-tiles/chart-icon.jpg)  
   
   * [Ouvrir la question de Questions et réponses qui a été utilisée pour créer la vignette ](end-user-reports.md) ![icône Questions et réponses](./media/end-user-tiles/qna-icon.png)  
   

   * [Ouvrir le classeur utilisé pour créer la vignette ](end-user-reports.md) ![icône de classeur](./media/end-user-tiles/power-bi-open-worksheet.png)  
   * [Afficher la vignette en mode Focus](end-user-focus.md) ![icône de focus](./media/end-user-tiles/fullscreen-icon.jpg)  
   * [Voir les insights ](end-user-insights.md) ![icône insights](./media/end-user-tiles/power-bi-insights.png)
   * [Ajouter un commentaire et démarrer une discussion](end-user-comment.md) ![icône de commentaire](./media/end-user-tiles/comment-icons.png)
   * [Gérer les alertes définies sur une vignette de tableau de bord](end-user-alerts.md) ![icône d’alerte](./media/end-user-tiles/power-bi-alert-icon.png)
   * [Ouvrir les données dans Excel](end-user-export.md) ![icône d’exportation](./media/end-user-tiles/power-bi-export-icon.png)


3. Pour fermer le menu d’actions, sélectionnez une zone vide dans la zone de dessin.

### <a name="select-click-a-tile"></a>Sélectionner (cliquer sur) une vignette
Lorsque vous sélectionnez une vignette, ce qui se passe ensuite dépend de la façon dont la vignette a été créée et de la présence ou non d’un [lien personnalisé dessus](../create-reports/service-dashboard-edit-tile.md). Si elle comporte un lien personnalisé, la sélection de la vignette vous fait accéder à ce lien. Dans le cas contraire, sélectionner la vignette ouvre le rapport, le classeur Excel en ligne, le rapport SSRS en local, ou la question Q&R qui a été utilisée pour créer la vignette.

> [!NOTE]
> La seule exception concerne les vignettes vidéo ajoutées aux tableaux de bord par des *concepteurs*. En sélectionnant une vignette de vidéo (créée de cette façon), la vidéo est lue directement dans le tableau de bord.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Si rien ne se produit lorsque vous sélectionnez (cliquez sur) une vignette ou si vous recevez un message d’erreur, voici quelques raisons possibles :
  - Le rapport qui a été utilisé pour créer la visualisation n’a pas été enregistré ou a été supprimé.
  - La vignette a été créée à partir d’un classeur dans Excel Online, et vous n’avez pas au moins des autorisations en lecture sur ce classeur.
  - Si la vignette a été créée à partir de SSRS et que vous n’avez pas l’autorisation d’accéder au rapport SSRS ou si vous n’avez pas accès au réseau sur lequel se trouve le serveur SSRS.
* Pour les vignettes créées directement sur le tableau de bord avec l’option **Ajouter une vignette**, si un lien hypertexte personnalisé a été défini, vous pouvez ouvrir cette URL en sélectionnant le titre, le sous-titre et/ou la vignette.  Sinon, par défaut, la sélection d’une de ces vignettes créées directement sur le tableau de bord pour une image, du code web ou une zone de texte ne produit aucune action.
* Si la visualisation d’origine utilisée pour créer la vignette change, la vignette ne change pas.  Par exemple, si le *concepteur* a épinglé un graphique en courbes à partir d’un rapport, puis transformé ce graphique en graphique à barres, la vignette du tableau de bord continue à afficher un graphique en courbes. Les données s’actualisent, mais pas le type de visualisation.

## <a name="next-steps"></a>Étapes suivantes
[Actualisation des données](../connect-data/refresh-data.md)

[Power BI – Concepts de base](end-user-basic-concepts.md)


