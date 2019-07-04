---
title: Descendre et monter dans la hiérarchie d’une visualisation
description: Cet article montre comment explorer une visualisation dans le service Microsoft Power BI et Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 6/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 29823a2f1ca7f1448df54282e0ce081310974eb3
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67265272"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Mode Exploration pour une visualisation dans Power BI

Cet article montre comment explorer une visualisation dans le service Microsoft Power BI et Power BI Desktop. Les rapports Power BI permettent à plusieurs hiérarchies de données de vous fournir le maximum d’informations sur vos données. En descendant et en montant dans la hiérarchie de vos points de données, vous pouvez explorer en profondeur les détails de vos données. Vous pouvez même en tirer parti sur vos petits appareils mobiles.

## <a name="drill-requires-a-hierarchy"></a>L’exploration nécessite une hiérarchie

Quand une visualisation a une hiérarchie, vous pouvez l’explorer pour révéler des détails supplémentaires. Par exemple, vous pouvez avoir une visualisation qui examine le nombre de médailles olympiques avec une hiérarchie constituée de sports, disciplines et événements. Par défaut, la visualisation indique le nombre de médailles olympiques par sport (gymnastique, ski, sports aquatiques, etc.). Toutefois, comme elle a une hiérarchie, si vous sélectionnez un élément de visualisation (tel qu’une barre, une ligne ou une bulle), une image encore plus détaillée s’affiche. Sélectionnez l’élément **aquatics** (sports aquatiques) afin d’afficher les données relatives à la natation, la plongée et le water polo.  Sélectionnez l’élément **diving** (plongée) pour afficher les détails relatifs au plongeoir, à la plateforme et aux événements de plongeon synchronisé.

Vous pouvez ajouter des hiérarchies aux rapports que vous possédez, mais pas à ceux partagés avec vous.
Vous ne savez pas quelles visualisations Power BI contiennent une hiérarchie ? Pointez sur une visualisation. Si vous voyez ces contrôles Descendre dans la hiérarchie dans les angles supérieurs, la visualisation a une hiérarchie.

![Capture d’écran de l’icône de descente d’un niveau dans la hiérarchie.](./media/end-user-drill/power-bi-drill-icon4.png)  ![Capture d’écran de l’icône Descendre dans la hiérarchie activé/désactivé.](./media/end-user-drill/power-bi-drill-icon2.png)  ![Capture d’écran de l’icône Descendre dans la hiérarchie de tous les champs à la fois. ](./media/end-user-drill/power-bi-drill-icon3.png)
![icône Monter dans la hiérarchie](./media/end-user-drill/power-bi-drill-icon5.png) ![Capture d’écran de l’icône Développer vers le bas.](./media/end-user-drill/power-bi-drill-icon6.png)  

Les dates sont un type unique de hiérarchie. Quand vous ajoutez un champ de date à une visualisation, Power BI ajoute automatiquement une hiérarchie de temps qui inclut l’année, le trimestre, le mois et le jour. Pour plus d’informations, consultez [hiérarchies de visualisation et comportement d’exploration](../guided-learning/visualizations.yml?tutorial-step=18) ou regardez la vidéo ci-dessous.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Pour savoir comment créer des hiérarchies à l’aide de Power BI Desktop, regardez la vidéo [Comment créer et ajouter des hiérarchies](https://youtu.be/q8WDUAiTGeU).

## <a name="prerequisites"></a>Conditions préalables

1. Dans le service Power BI ou dans Power BI Desktop, l’exploration nécessite une visualisation avec une hiérarchie.

1. Pour suivre la procédure, ouvrez l’[exemple Analyse de la vente au détail](../sample-datasets.md). Créez une visualisation **Treemap** qui examine les points suivants :

    | Zone | Champ |
    | ---- | ----- |
    | Valeur |Ventes<br>\|\_ Nombre total d’unités cette année |
    | Grouper | Store<br>\|\_ Territoire<br>\|\_ Ville<br>\|\_ Code postal<br>\|\_ Nom

    La treemap a une hiérarchie constituée de secteurs, de villes, de codes postaux et de noms de ville. Chaque secteur a une ou plusieurs villes, chaque ville a un ou plusieurs codes postaux, etc. Par défaut, la visualisation montre uniquement les données relatives au secteur, car le *secteur* (Territory) apparaît en premier dans la liste.

    ![Capture d’écran du volet Visualisations avec le champ Territoire.](media/end-user-drill/power-bi-hierarcy-list.png)

1. Apprendre comment les différentes icônes d’exploration coopèrent peut être déroutant. Nous allons filtrer la treemap pour n’afficher que deux des plus petits territoires : **KY** et **TN**. Sélectionnez la treemap et, sous **Filtres au niveau de l’élément visuel**, développez **Territory** et sélectionnez **KY** et **TN**.

    ![Capture d’écran du volet Visualisations avec filtre pour KY et TN.](./media/end-user-drill/power-bi-filter.png)

    Seuls deux secteurs apparaissent maintenant dans la treemap.

    ![Capture d’écran du visuel avec KY et TN.](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-use-the-drill-features"></a>Trois façons d’utiliser les fonctionnalités d’exploration

Vous disposez de plusieurs options pour accéder aux fonctionnalités d’exploration permettant de monter et de descendre dans la hiérarchie, et de développer, pour les visualisations qui ont des hiérarchies. Cet article explique comment utiliser la première option ci-dessous. Lorsque vous aurez appris les principes fondamentaux de l’exploration au niveau du détail et du développement, vous saurez comment utiliser les trois. Elles font toutes les mêmes choses. Testez-les et choisissez celle que vous préférez.

- Pointez sur une visualisation pour voir et utiliser les icônes.  

    ![Capture d’écran de l’exemple de pointage.](./media/end-user-drill/power-bi-hover.png)

- Cliquez avec le bouton droit sur une visualisation pour faire apparaître et utiliser le menu.

    ![Capture d’écran de l’exemple de clic avec le bouton droit.](./media/end-user-drill/power-bi-drill-menu.png)

- Dans la barre de menus de Power BI, sélectionnez le bouton **Explorer**.

   ![Capture d’écran de la sélection Explorer montrant les icônes et les options d’exploration.](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>Parcours d’exploration

### <a name="drill-down"></a>Descendre dans la hiérarchie

Vous disposez de plusieurs moyens pour explorer votre visualisation. **Descendre dans la hiérarchie** vous amène au niveau suivant de la hiérarchie. Si vous regardez le niveau **Territory**, vous pouvez descendre dans la hiérarchie au niveau de la ville, puis au niveau du code postal, et enfin au niveau du nom. Chaque étape de ce parcours vous montre de nouvelles informations.

![Diagramme montrant le parcours d’exploration](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Développer

**Développer** ajoute un niveau de hiérarchie supplémentaire à la vue actuelle. Par conséquent, si vous regardez le niveau **Territory**, vous pouvez développer et ajouter les détails concernant la ville, le code postal et le nom à votre treemap. Chaque étape du parcours vous montre les mêmes informations et ajoute un niveau de nouvelles informations.

![Diagramme montrant le parcours de développement](./media/end-user-drill/power-bi-expand-path.png)

Vous pouvez également choisir de descendre dans la hiérarchie ou de développer sur un champ à la fois ou sur tous les champs en même temps.

## <a name="drill-down-all-fields-at-once"></a>Descendre dans la hiérarchie de tous les champs en même temps

1. Démarrez au plus haut niveau de la treemap montrant les données pour KY et TN. Élargissez votre treemap en sélectionnant une des poignées et en la faisant glisser vers la droite.

    ![Capture d’écran du visuel de treemap montrant KY et TN](./media/end-user-drill/power-bi-drill-down.png)

1. Pour descendre dans la hiérarchie de *tous les champs en même temps*, sélectionnez la flèche double en haut à gauche de la visualisation ![Icône Descendre dans la hiérarchie avec deux flèches](./media/end-user-drill/power-bi-drill-icon3.png). Votre treemap montre maintenant les données des villes pour le Kentucky et le Tennessee.

    ![Capture d’écran du visuel de treemap montrant la descente dans la hiérarchie jusqu’aux villes.](./media/end-user-drill/power-bi-drill-down1.png)

1. Descendez une nouvelle fois dans la hiérarchie au niveau du code postal.

    ![Capture d’écran du visuel de treemap montrant la descente dans la hiérarchie jusqu’au code postal.](./media/end-user-drill/power-bi-drill-down2.png)

1. Pour remonter d’un niveau, sélectionnez la flèche vers le haut en haut à gauche de la visualisation ![Capture d’écran de l’icône de montée d’un niveau dans la hiérarchie.](./media/end-user-drill/power-bi-drill-icon5.png).

## <a name="drill-down-one-field-at-a-time"></a>Descendre dans la hiérarchie pour un champ à la fois

Cette méthode utilise l’icône Descendre dans la hiérarchie qui apparaît en haut à droite de la visualisation elle-même.

1. Sélectionnez l’icône Descendre dans la hiérarchie pour l’activer ![Capture d’écran de l’icône Descendre dans la hiérarchie activée/désactivée.](./media/end-user-drill/power-bi-drill-icon2.png).

    Vous avez maintenant la possibilité de descendre dans la hiérarchie **un champ à la fois**.

    ![Capture d’écran de visuel avec une flèche pointant vers l’icône activé/désactivé Descendre dans la hiérarchie activé.](media/end-user-drill/power-bi-drill-icon-new.png)

    Si vous n’activez pas Descendre dans la hiérarchie, la sélection d’un élément de visualisation (par exemple, une barre, une bulle ou un nœud terminal) n’entraînera pas de descente dans la hiérarchie. Au lieu de cela, il y aura un filtrage croisé des autres sur la page de rapport.

1. Sélectionnez le nœud terminal pour **TN**. Votre treemap montre maintenant toutes les villes du Tennessee qui ont un magasin.

    ![Capture d’écran de la treemap montrant les données pour TN uniquement.](media/end-user-drill/power-bi-drill-down-one1.png)

1. À ce stade, vous pouvez effectuer les opérations suivantes :

    1. Continuer Descendre dans la hiérarchie pour le Tennessee.

    1. Descendre dans la hiérarchie pour une ville spécifique du Tennessee.

    1. Développer à la place (consultez **Développer tous les champs à la fois** ci-dessous).

    Continuons à descendre dans la hiérarchie pour un champ à la fois.  Sélectionnez **Knoxville, TN**. Votre treemap montre maintenant le code postal de votre magasin de Knoxville.

    ![Capture d’écran de la treemap montrant le code postal 37919.](media/end-user-drill/power-bi-drill-down-one2.png)

    Notez que le titre change à mesure que vous explorez puis revenez en arrière.

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Développer tout et développer un champ à la fois

Une treemap qui nous montre uniquement un code postal n’apporte pas beaucoup d’informations.  Développons donc un niveau de la hiérarchie.  

1. Avec la treemap active, sélectionnez l’icône *Développer vers le bas*![Capture d’écran de l’icône Développer vers le bas](./media/end-user-drill/power-bi-drill-icon6.png). Votre treemap montre maintenant les deux niveaux de notre hiérarchie : le code postal et le nom du magasin.

    ![Capture d’écran de la treemap montrant le code postal et le nom du magasin](./media/end-user-drill/power-bi-expand1.png)

1. Pour voir l’ensemble des quatre niveaux de hiérarchie des données pour Tennessee, sélectionnez la flèche Monter dans la hiérarchie jusqu’à atteindre le deuxième niveau, **Total units this year by territory and city**, de votre treemap.

    ![Capture d’écran de la treemap montrant toutes les données pour TN.](media/end-user-drill/power-bi-drill-down-one1.png)

1. Vérifiez que l’icône Descendre dans la hiérarchie est toujours activée, ![Capture de l’icône Descendre dans la hiérarchie activée/désactivée.](./media/end-user-drill/power-bi-drill-icon2.png) et sélectionnez l’icône *Développer vers le bas*![Capture d’écran de l’icône Développer vers le bas](./media/end-user-drill/power-bi-drill-icon6.png). Votre treemap montre maintenant des détails supplémentaires. Au lieu de montrer seulement la ville et l’état, elle montre maintenant également le code postal.

    ![Capture d’écran de l’élément visuel montrant la ville, l’état et le code postal.](./media/end-user-drill/power-bi-expand-one3.png)

1. Sélectionnez une fois de plus l’icône *Développer vers le bas* pour afficher les quatre niveaux de la hiérarchie des détails pour le Tennessee sur votre treemap. Pointez sur une feuille pour voir davantage de détails.

    ![Capture d’écran de la treemap montrant une info-bulle avec des données spécifiques au nœud terminal.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>L'exploration filtre les autres visuels

Quand vous travaillez en mode Exploration, vous devez décider comment les fonctionnalités Descendre dans la hiérarchie et Développer impactent les autres visualisations de la page.

Par défaut, l’exploration ne filtre pas les autres visuels d’un rapport. Vous pouvez activer cette fonctionnalité dans Power BI Desktop et dans le service Power BI.

1. Dans Power BI Desktop, sélectionnez l’onglet **Format** et cochez la case pour **Filtrages d’exploration sur les autres visuels**.

    ![Capture d’écran montrant le paramètre Filtrages d'exploration sur les autres visuels dans Power BI Desktop](./media/end-user-drill/power-bi-drill-filters-desktop.png)

1. Maintenant, quand vous descendez dans la hiérarchie, que vous montez dans la hiérarchie ou que vous développez dans une visualisation avec une hiérarchie, cette action filtre les autres visuels de la page.

    ![Capture d’écran du résultat dans Desktop.](./media/end-user-drill/power-bi-drill-filters.png)

    ![Capture d’écran de l’autre résultat dans Desktop.](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> Pour activer cette option dans le service Power BI, dans la barre de menus supérieure, sélectionnez **Interactions entre les visuels** > **Filtrages d’exploration sur les autres visuels**.
>
> ![Capture d’écran du paramètre Filtrages d'exploration sur les autres visuels dans le service Power BI](./media/end-user-drill/power-bi-drill-filters-service.png)

## <a name="learn-about-the-hierarchy-axis-and-hierarchy-group"></a>En savoir plus sur l’axe de hiérarchie et sur le groupe de hiérarchie

Vous pouvez considérer l’axe de hiérarchie et le groupe de hiérarchie comme les mécanismes à utiliser pour augmenter et diminuer la granularité des données à afficher. Toutes les données que vous pouvez organiser en catégories et en sous-catégories peuvent avoir une hiérarchie, notamment des dates et des heures.

Vous pouvez créer une visualisation dans Power BI avec une hiérarchie en sélectionnant un ou plusieurs champs de données à ajouter à la zone **Axe** ou la zone **Groupe**. Ensuite, ajoutez les données que vous souhaitez examiner en tant que champs de données dans la zone **Valeurs**. Vous savez si vos données sont hiérarchiques si les icônes du *Mode Exploration* apparaissent en haut à droite et à gauche de votre visualisation.

Fondamentalement, on peut dire qu’il existe deux types de données hiérarchiques :

- Données de date et d’heure : Si vous avez un champ de données avec un type de données DateTime, vous avez déjà des données hiérarchiques. Power BI crée automatiquement une hiérarchie pour n’importe quel champ de données. Vous pouvez analyser les valeurs dans une structure [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx). Vous devez uniquement ajouter un champ DateTime à la zone **Axe** ou **Groupe**.

- Données catégoriques : si Power BI dérive vos données de collections avec des sous-collections ou avec des lignes de données qui partagent des valeurs communes, vous avez des données hiérarchiques.

Power BI vous permet de développer les données d’un ou de tous les sous-ensembles. Vous pouvez descendre dans la hiérarchie de vos données pour afficher un seul sous-ensemble par niveau, ou vous pouvez descendre dans la hiérarchie pour afficher tous les sous-ensembles simultanément par niveau. Par exemple, vous pouvez explorer une année donnée ou afficher tous les résultats de chaque année à mesure que vous descendez dans la hiérarchie.

Vous pouvez également monter dans la hiérarchie de la même manière.

Les sections suivantes décrivent une descente dans la hiérarchie de la vue la plus élevée à la vue intermédiaire, puis à la vue la plus basse.

### <a name="hierarchical-data-and-time-data"></a>Données hiérarchiques et données temporelles

Pour cet exemple :

1. Pour cet exemple, reprenez [l’exemple Analyse de la vente au détail](../sample-datasets.md) et créez une visualisation d’histogramme empilé qui examine :

    | Zone | Champ |
    | ---- | ----- |
    | Axe | Heure<br>\|\_Mois |
    | Valeurs | Ventes<br>\|\_ TotalSales |

    Même si le champ de données Axe est **Mois**, il crée toujours une catégorie **Année** dans la zone **Axe**. C’est parce que Power BI fournit la structure DateTime complète pour toutes les valeurs qu’il lit. En haut de la hiérarchie se trouvent les données de l’année.

    ![Capture d’écran de la barre unique affichant les données regroupées par année](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

1. Avec le mode Descendre dans la hiérarchie activé, sélectionnez la barre du graphique pour descendre d’un niveau dans la hiérarchie. Vous voyez trois barres pour les données de trimestre disponibles.

1. Ensuite, à partir des icônes en haut à gauche, choisissez **Développer le niveau inférieur de toute la hiérarchie**.

1. Répétez l’opération pour accéder au niveau le plus bas de la hiérarchie, qui présente les résultats de chaque mois.

    ![Capture d’écran du graphique à barres pour afficher la barre par mois](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

En plus de la visualisation, nous pouvons voir la hiérarchie reflétée dans les données affichées pour chaque rapport. En haut à droite, sélectionnez les points de suspension (...), puis choisissez **Afficher les données**. Le tableau suivant montre les résultats de la descente dans la hiérarchie pour un seul mois ou pour tous les mois :

|Mode Développer|Année|Quarter|Month|Jour|
| --- |:---:|:---:|:---:|---|
|À sens unique|![une année](./media/end-user-drill/power-bi-hierarchical-year.png)|![un trimestre](media/end-user-drill/power-bi-hierarchical-quarter.png)|![un mois](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![un jour](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Tout|![toutes les années](./media/end-user-drill/power-bi-hierarchical-year.png)|![tous les trimestres](media/end-user-drill/power-bi-hierarchical-quarter.png)|![tous les mois](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![tous les jours](media/end-user-drill/power-bi-hierarchical-all-day.png)|

Notez que les données sont les mêmes pour les rapports **trimestriels** et **annuels**. Une fois que vous descendez dans la hiérarchie jusqu’au niveau de détail spécifié pour **Valeurs**, vous pouvez observer que le rapport pour un seul mois devient plus spécifique et que le rapport pour tous les mois a plus de données.

### <a name="hierarchical-category-data"></a>Données de catégorie hiérarchiques

Les données modélisées à partir de collections et de sous-collections sont hiérarchiques.

Les données de localisation en sont un bon exemple. Prenons une table dans une source de données avec des colonnes Pays, État, Ville et Code postal. Les données qui partagent les mêmes pays, état et ville sont hiérarchiques.

Pour cet exemple :

1. Reprenez [l’exemple Analyse de la vente au détail](../sample-datasets.md). Créer une visualisation d’histogramme empilé qui examine les points suivants :

    | Zone | Champ |
    | ---- | ----- |
    | Valeur |Ventes<br>\|\_ Nombre total d’unités cette année |
    | Axe | Store<br>\|\_ Territoire<br>\|\_ Ville : vous devrez peut-être faire glisser Ville de la zone **Légende** à la zone **Axe**.<br>\|\_ Code postal<br>\|\_ Nom |

    ![Capture d’écran du graphique à barres affichant les unités totales pour cette année par secteur de vente.](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

1. Avec le mode Descendre dans la hiérarchie activé, à partir des icônes en haut à gauche, choisissez **Développer le niveau inférieur de toute la hiérarchie** trois fois de suite.

    Vous accédez au niveau le plus bas de la hiérarchie, qui montre les résultats pour le secteur de vente, la ville et le code postal.

    ![Capture d’écran du graphique à barres montrant le niveau le plus bas de la hiérarchie, avec la plupart des détails.](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

En plus de la visualisation, nous pouvons voir la hiérarchie reflétée dans les données affichées pour chaque rapport. En haut à droite, sélectionnez les points de suspension (...), puis choisissez **Afficher les données**. Le tableau suivant montre les résultats de la descente dans la hiérarchie pour un seul secteur de vente ou pour tous les secteurs de vente.

| Mode Développer|Territoire|Ville|Code postal|Nom|
| ---|:---:|:---:|:---:|---|
|À sens unique|![un territoire](./media/end-user-drill/power-bi-hierarchical-territory.png)|![une ville](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![un code postal](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![un nom](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Tout|![tous les territoires](./media/end-user-drill/power-bi-hierarchical-territory.png)|![toutes les villes](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![tous les codes postaux](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![tous les noms](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|

 Quand vous descendez dans la hiérarchie, vous pouvez observer que le rapport **pour un seul secteur** de vente devient plus spécifique et que le rapport **pour tous les secteurs de vente** a plus de données.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Si l’ajout d’un champ de date à une visualisation ne crée pas de hiérarchie, c’est peut-être que le champ « date » n’est pas bien enregistré en tant que date. Si vous êtes propriétaire du jeu de données :

1. Ouvrez-le dans la vue *Données* dans Power BI Desktop.

1. Sélectionnez la colonne qui contient la date.

1. Dans l’onglet **Modélisation**, modifiez le **Type de données** en **Date** ou **Date/Heure**.

![Capture d’écran de la vue des données sélectionnées et, en haute à droite, vous pouvez voir Type de Date.](media/end-user-drill/power-bi-change-data-type2.png)

Si le rapport a été partagé avec vous, contactez le propriétaire pour lui demander d’effectuer la modification.

## <a name="next-steps"></a>Étapes suivantes

[Visualisations dans des rapports Power BI](../visuals/power-bi-report-visualizations.md)

[Rapports Power BI](end-user-reports.md)

[Power BI – Concepts de base](end-user-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
