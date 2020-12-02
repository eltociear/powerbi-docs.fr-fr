---
title: Graphiques en entonnoir
description: Graphiques en entonnoir dans Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 3eae51d470fe2b25c5fdbb97f97ee6468900e32c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386181"
---
# <a name="create-and-use-funnel-charts"></a>Créer et utiliser des graphiques en entonnoir

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Un graphique en entonnoir vous permet de mieux visualiser un processus linéaire qui comporte des étapes séquentielles liées entre elles. Par exemple, un entonnoir de ventes qui effectue le suivi des clients à travers des étapes : Lead \> Qualified Lead \> Prospect \> Contract \> Close.  En regardant la forme de l’entonnoir, vous savez instantanément comment se déroule le processus dont vous effectuez le suivi.

Chaque étape de l’entonnoir représente un pourcentage du total. C’est pourquoi un graphique en entonnoir a généralement la forme d’un entonnoir, où la première étape est la plus large et chaque étape suivante est plus étroite que l’étape précédente.  Un entonnoir en forme de poire est également utile, car il peut indiquer un problème dans le processus.  Mais le plus souvent, la première étape (l’étape de départ) est la plus large.

![exemple de graphique en entonnoir bleu](media/power-bi-visualization-funnel-charts/funnelplain.png)

> [!NOTE]
> Pour que vous puissiez partager votre rapport avec un collègue Power BI, il faut que vous disposiez tous deux de licences individuelles Power BI Pro ou que le rapport soit enregistré dans une capacité Premium.    

## <a name="when-to-use-a-funnel-chart"></a>Quand faut-il utiliser un graphique en entonnoir ?
Les graphiques en entonnoir sont conseillés :

* quand les données sont séquentielles et portent sur au moins quatre étapes ;
* quand le nombre « d’éléments » à la première étape doit normalement être supérieur au nombre à l’étape finale ;
* pour calculer le potentiel (revenus/ventes/contrats/etc.) à chaque étape ;
* pour calculer et suivre des taux de conversion et de rétention ;
* pour révéler les goulots d’étranglement dans un processus linéaire ;
* pour effectuer le suivi d’un parcours d’achat en ligne ;
* pour suivre la progression et le résultat des campagnes de publicité/marketing (taux de clics).

## <a name="working-with-funnel-charts"></a>Utilisation des graphiques en entonnoir
Graphiques en entonnoir :

* peuvent être triés ;
* prennent en charge les multiples ;
* prennent en charge la mise en surbrillance et le filtrage croisé par d’autres visualisations sur la même page de rapport ;
* peuvent être utilisés pour la mise en surbrillance et le filtrage croisé d’autres visualisations sur la même page de rapport.
   > [!NOTE]
   > Regardez cette vidéo pour voir comment créer un graphique en entonnoir avec l’exemple Vente et marketing. Ensuite, suivez les étapes sous la vidéo pour essayer par vous-même avec le fichier PBIX de l’exemple Analyse des opportunités.
   > 
   > 
## <a name="prerequisite"></a>Prérequis

Ce tutoriel utilise le [fichier PBIX de l’exemple Analyse des opportunités](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix
).

1. Dans la section supérieure gauche de la barre de menus, sélectionnez **Fichier** > **Ouvrir**.
   
2. Rechercher votre copie du **fichier PBIX de l’exemple Analyse des opportunités**

1. Ouvrez le **fichier PBIX de l’exemple Analyse des opportunités** dans la vue Rapport ![Capture d’écran de l’icône de la vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.


## <a name="create-a-basic-funnel-chart"></a>Créer un graphique en entonnoir simple
Regardez cette vidéo pour voir comment créer un graphique en entonnoir avec l’exemple Vente et marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


À présent, créez votre propre graphique en entonnoir qui montre le nombre d’opportunités identifiées à chaque étape de vente.

1. Démarrez dans une page de rapport vierge, puis sélectionnez le champ **SalesStage** \> **Étape de vente**.
   
    ![sélectionner Étape de vente](media/power-bi-visualization-funnel-charts/funnelselectfield-new.png)

1. Sélectionnez l’icône Entonnoir ![Icône Graphique en entonnoir](media/power-bi-visualization-funnel-charts/power-bi-funnel-icon.png) pour convertir l’histogramme en graphique en entonnoir.

2. Dans le volet **Champs**, sélectionnez **Fait** \> **Nombre d’opportunités**.
   
    ![générer le graphique en entonnoir](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. Placez le curseur sur une barre pour afficher diverses informations :
   
   * Nom de l’étape
   * Nombre d’opportunités actuellement identifiées à cette étape
   * Taux de conversion global (% de prospect) 
   * Stage-to-stage (Taux d’abandon), qui est le pourcentage de l’étape précédente (dans ce cas, Proposal Stage/Solution Stage - Étape Proposition/Étape Solution).
     
     ![détails de la barre Proposal](media/power-bi-visualization-funnel-charts/funnelhover-new.png)

6. [Enregistrez le rapport](../create-reports/service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisé
Pour plus d’informations sur le volet Filtres, consultez [Ajouter un filtre à un rapport](../create-reports/power-bi-report-add-filter.md).

La mise en surbrillance d’une barre dans un graphique en entonnoir entraîne le filtrage croisé des autres visualisations sur la page du rapport, et vice versa. Pour suivre la procédure, ajoutez quelques éléments visuels de plus à la page de rapport qui contient le graphique en entonnoir.

1. Dans l’entonnoir, sélectionnez la barre **Proposal** (Proposition). Cela met en surbrillance croisée les autres visualisations sur la page. Utilisez la touche CTRL pour sélectionner simultanément plusieurs éléments.
   
   ![courte vidéo montrant les interactions des visuels](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Pour définir les préférences pour la mise en surbrillance croisée et le filtrage croisé des visuels entre eux, consultez [Interaction des éléments visuels dans Power BI](../create-reports/service-reports-visual-interactions.md).

## <a name="next-steps"></a>Étapes suivantes

[Jauges dans Power BI](power-bi-visualization-radial-gauge-charts.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)



