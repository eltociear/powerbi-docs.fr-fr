---
title: Vignettes de tableau de bord dans Power BI pour les consommateurs
description: Toutes les informations dont vous avez besoin sur les vignettes de tableau de bord dans Power BI pour les consommateurs. Cela inclut les vignettes créées à partir de SQL Server Reporting Services (SSRS).
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 1e86403dbdb2972cc83b379efff8bbc17173a4e1
ms.sourcegitcommit: 35d763dfc75c229204d36fd8b35c1e860786b707
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52331893"
---
# <a name="dashboard-tiles-in-power-bi"></a>Vignettes d’un tableau de bord dans Power BI
Les tableaux de bord et vignettes de tableau de bord caractérisent le service Power BI et non Power BI Desktop. Si vous ne pouvez pas créer ou épingler des vignettes de tableau de bord dans Power BI Mobile, vous [pouvez les afficher et les partager](mobile/mobile-tiles-in-the-mobile-apps.md). 

## <a name="dashboard-tiles"></a>Mise à jour des vignettes de tableau de bord
![tableau de bord Power BI](./media/end-user-tiles/power-bi-dashboard.png)

Une vignette est une capture instantanée de vos données, épinglée au tableau de bord par un *concepteur*. Une vignette peut être créée à partir d’un rapport, d’un jeu de données, d’un tableau de bord, de la zone Questions et réponses, d’Excel et de SSRS (SQL Server Reporting Services), et plus encore.  Cette capture d’écran montre différentes vignettes épinglées à un tableau de bord.

En plus des vignettes épinglées à partir de rapports, les *concepteurs* peuvent ajouter des vignettes autonomes directement sur le tableau de bord à l’aide de l’option **Ajouter une vignette**. Les vignettes autonomes incluent des zones de texte, des images, des vidéos, des données de streaming et du contenu web.

Vous avez du mal à comprendre les éléments qui composent Power BI ?  Consultez [Power BI – Concepts de base](end-user-basic-concepts.md).


## <a name="interacting-with-tiles-on-a-dashboard"></a>Interaction avec des vignettes dans un tableau de bord

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Placer le curseur sur une vignette pour modifier son apparence et son comportement
1. Placez le curseur sur la vignette pour afficher les points de suspension.
   
    ![points de suspension de la vignette](./media/end-user-tiles/ellipses_new.png)
2. Sélectionnez les points de suspension pour ouvrir le menu des actions de la vignette. Les options disponibles varient en fonction du type de visuel et de la méthode utilisée pour créer la vignette. Voici quelques exemples de ce que vous pouvez voir.

    - vignette créée à l’aide de Questions et réponses
   
        ![icône des points de suspension](./media/end-user-tiles/power-bi-menu1.png)

    - vignette créée à partir d’un classeur
   
        ![icône des points de suspension](./media/end-user-tiles/power-bi-menu2.png)

    - vignette créée à partir d’un rapport
   
        ![icône des points de suspension](./media/end-user-tiles/power-bi-menu3.png)
   
    Vous pouvez ici :
   
   * [Ouvrir le rapport utilisé pour créer cette vignette ](end-user-reports.md) ![icône de rapport](./media/end-user-tiles/chart-icon.jpg)  
   
   * [Ouvrir la question de Questions et réponses qui a été utilisée pour créer la vignette ](end-user-reports.md) ![icône Questions et réponses](./media/end-user-tiles/qna-icon.png)  
   

   * [Ouvrir le classeur utilisé pour créer cette vignette ](end-user-reports.md) ![icône de classeur](./media/end-user-tiles/power-bi-open-worksheet.png)  
    * [Afficher la vignette en mode focus](end-user-focus.md) ![icône de focus](./media/end-user-tiles/fullscreen-icon.jpg)  
     * [Exécuter Insights ](end-user-insights.md) ![icône insights](./media/end-user-tiles/power-bi-insights.png)
    * [Ajouter un commentaire et démarrer une discussion](end-user-comment.md) ![icône de commentaire](./media/end-user-tiles/comment-icons.png)

3. Pour fermer le menu d’actions, sélectionnez une zone vide dans la zone de dessin.

### <a name="select-click-a-tile"></a>Sélectionner (cliquer sur) une vignette
Lorsque vous sélectionnez une vignette, ce qui se passe ensuite dépend de la façon dont la vignette a été créée et de la présence ou non d’un [lien personnalisé dessus](../service-dashboard-edit-tile.md). Si elle comporte un lien personnalisé, la sélection de la vignette vous fait accéder à ce lien. Dans le cas contraire, sélectionner la vignette ouvre le rapport, le classeur Excel en ligne, le rapport SSRS en local, ou la question Q&R qui a été utilisée pour créer la vignette.

> [!NOTE]
> La seule exception concerne les vignettes de vidéo créées directement sur le tableau de bord avec l’option **Ajouter une vignette**. En sélectionnant une vignette de vidéo (créée de cette façon), la vidéo est lue directement dans le tableau de bord.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Si le rapport utilisé pour créer la visualisation n'a pas été enregistré, sélectionner la vignette ne produit alors aucune action.
* Si la vignette a été créée à partir d'un classeur Excel en ligne et que vous ne disposez pas au moins des autorisations de lecture nécessaires pour ce classeur, vous ne pourrez pas ouvrir le classeur Excel en ligne en sélectionnant la vignette.
* Pour les vignettes créées directement sur le tableau de bord avec l’option **Ajouter une vignette**, si un lien hypertexte personnalisé a été défini, vous pouvez ouvrir cette URL en sélectionnant le titre, le sous-titre et/ou la vignette.  Sinon, par défaut, la sélection d’une de ces vignettes créées directement sur le tableau de bord pour une image, du code web ou une zone de texte ne produit aucune action.
* Si vous n’avez pas l’autorisation d’accéder au rapport dans SSRS, la sélection d’une vignette créée à partir de SSRS générera une page indiquant que vous n’avez pas accès (rsAccessDenied).
* Si vous n’avez pas accès au réseau où se trouve le serveur SSRS, la sélection d’une vignette créée à partir de SSRS générera une page indiquant que la localisation du serveur est impossible (HTTP 404). Votre appareil doit bénéficier de l’accès réseau au serveur de rapports pour afficher le rapport.
* Si la visualisation d’origine utilisée pour créer la vignette change, la vignette ne change pas.  Par exemple, si le *concepteur* a épinglé un graphique en courbes à partir d’un rapport, puis transformé ce graphique en graphique à barres, la vignette du tableau de bord continue à afficher un graphique en courbes. Les données s’actualisent, mais pas le type de visualisation.

## <a name="next-steps"></a>Étapes suivantes
[Actualisation des données](../refresh-data.md)

[Power BI – Concepts de base](end-user-basic-concepts.md)
