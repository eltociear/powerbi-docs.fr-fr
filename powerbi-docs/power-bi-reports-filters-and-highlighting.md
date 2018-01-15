---
title: "À propos des filtres et de la mise en évidence dans les rapports Power BI"
description: "À propos des filtres et de la mise en évidence dans les rapports Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: 0f81b0fa87af5af281b40224bac3b5815461cb9e
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="about-filters-and-highlighting-in-power-bi-reports"></a>À propos des filtres et de la mise en évidence dans les rapports Power BI
Les ***filtres*** masquent tout, sauf les données qui vous intéressent.  Contrairement au filtrage, qui masque les données, la ***mise en évidence*** met en évidence un sous-ensemble des données visibles ; les données qui ne sont pas mises en évidence restent visibles, mais sont estompées.

Il existe de nombreuses façons de filtrer et de mettre en évidence des rapports dans Power BI. Expliquer ces méthodes dans un seul article serait déroutant. Nous les avons donc réparties comme suit :

* Présentation des filtres et de la mise en évidence (cet article)
* Méthodes permettant de [créer et d’utiliser des filtres et la mise en évidence dans des rapports en mode Édition dont vous êtes propriétaire](power-bi-report-add-filter.md). Quand vous disposez d’autorisations de modification d’un rapport, vous pouvez créer, modifier et supprimer les filtres et la mise en évidence dans ce rapport.
* Méthodes permettant d’[utiliser des filtres et la mise en évidence dans un rapport partagé avec vous ou en mode Lecture](service-reading-view-and-editing-view.md). Ce que vous pouvez faire est plus limité, mais Power BI vous donne toujours un large éventail d’options de filtrage et de mise en évidence.  
* [Visite guidée détaillée des commandes de filtrage et de mise en évidence disponibles en mode Édition](power-bi-how-to-report-filter.md), y compris une présentation détaillée des types de filtre (date et heure, numérique, texte, etc.) et la différence entre les options de base et avancée.
* Maintenant que vous connaissez le fonctionnement par défaut des filtres et de la mise en évidence, [découvrez comment modifier l’affichage des visualisations sur un filtre au niveau de la page et effectuer une mise en évidence](service-reports-visual-interactions.md)

> [!TIP]
> Comment Power BI peut savoir la façon dont les données sont liées ?  Power BI utilise les relations entre les différentes tables et les différents champs du [modèle de données](https://support.office.com/article/Create-a-Data-Model-in-Excel-87e7a54c-87dc-488e-9410-5c75dbcb0f7b?ui=en-US&rs=en-US&ad=US) sous-jacent pour que les éléments d’une page de rapport interagissent les uns avec les autres.
> 
> 

## <a name="introduction-to-filters-and-highlighting-in-reports-using-the-filters-pane"></a>Présentation des filtres et de la mise en évidence dans les rapports à l’aide du volet Filtres
![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Les filtres et la mise en évidence peuvent être appliqués à l’aide du volet **Filtres** ou en effectuant des sélections directement sur le rapport lui-même (ad hoc, voir en bas de page). Le volet Filtres montre les tables et les champs utilisés dans le rapport et les filtres qui ont été appliqués, le cas échéant. Les filtres sont divisés en **filtres au niveau de la page**, **filtres au niveau du rapport** et **filtres au niveau de l’élément visuel**.  Les filtres au niveau de l’élément visuel s’affichent uniquement si vous avez sélectionné une visualisation sur le canevas de rapport.

> [!TIP]
> Si le filtre est accompagné du mot **Tout**, cela signifie que le champ entier est inclus en tant que filtre.  Par exemple, dans la capture d’écran ci-dessous, **Chain(Tout)** indique que cette page de rapport inclut des données sur toutes les chaînes de magasin.  En revanche, le filtre au niveau du rapport **AnnéeFiscale est 2013 ou 2014** indique que le rapport inclut des données uniquement pour les années fiscales 2013 et 2014.
> 
> 

## <a name="filters-in-reading-view-versus-editing-view"></a>Filtres en mode Lecture et en mode Édition
Il existe deux modes d’interaction avec les rapports : le [mode Lecture et le mode Édition](service-reading-view-and-editing-view.md).  Et les fonctionnalités de filtrage disponibles varient en fonction du mode dans lequel vous êtes.

* En mode Édition, vous pouvez ajouter des filtres de rapport, de page et d’élément visuel. Les filtres sont enregistrés en même temps que le rapport. Les personnes qui examinent le rapport en mode Lecture peuvent interagir avec les filtres que vous avez ajoutés, mais pas enregistrer leurs modifications.
* En mode Lecture, vous pouvez interagir avec les filtres de page et d’élément visuel qui existent déjà dans le rapport, mais vous ne pouvez pas enregistrer les modifications que vous apportez aux filtres.

### <a name="the-filters-pane-in-reading-view"></a>Volet Filtres en mode Lecture
Si vous avez uniquement accès à un rapport en mode Lecture, le volet Filtres a l’aspect suivant :

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Par conséquent, cette page de rapport a 6 filtres au niveau de la page et 1 filtre au niveau du rapport.

Pour voir si des filtres au niveau de l’élément visuel existent, sélectionnez un élément visuel. Dans l’image ci-dessous, 6 filtres ont été appliqués au graphique en bulles.

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

En mode Lecture, explorez les données en modifiant les filtres existants. Découvrez comment dans l’article [Interagir avec les filtres en mode Lecture](service-reading-view-and-editing-view.md)

### <a name="the-filters-pane-in-editing-view"></a>Volet Filtres en mode Édition
Quand vous disposez des autorisations de propriétaire sur un rapport et que vous ouvrez celui-ci en mode Édition, **Filtres** est l’un des volets d’édition disponibles.

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

En mode Lecture (ci-dessus), cette page de rapport a 6 filtres au niveau de la page et 1 filtre au niveau du rapport. Quand vous sélectionnez le graphique en bulles, vous voyez que 6 filtres au niveau de l’élément visuel s’appliquent.

Toutefois, en mode Édition, les filtres et la mise en évidence permettent d’effectuer de nombreuses autres opérations. La principale différence est que nous pouvons ajouter de nouveaux filtres. Découvrez comment et bien plus encore dans l’article [Ajouter un filtre à un rapport](power-bi-report-add-filter.md)

## <a name="ad-hoc-filterting-and-highlighting"></a>Mise en évidence et filtrage ad hoc
Sélectionnez un champ sur le canevas de rapport pour filtrer et mettre en évidence le reste de la page. Sélectionnez un espace vide dans ce même élément visuel pour le supprimer. Ce type de filtrage et de mise en évidence n’est pas enregistré avec le rapport mais c’est un moyen amusant d’explorer rapidement l’impact des données. Pour plus d’informations sur le filtrage croisé et la mise en évidence croisée, consultez [Interactions avec les visualisations](service-reports-visual-interactions.md).

![](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

## <a name="next-steps"></a>Étapes suivantes
[Interagir avec les filtres et la mise en évidence (en mode Lecture)](service-reading-view-and-editing-view.md)

[Ajouter un filtre à un rapport (en mode Édition)](power-bi-report-add-filter.md)

[Découvrir les filtres de rapport](power-bi-how-to-report-filter.md)

[Modifier la façon dont le filtrage croisé et la mise en évidence croisée affectent les visuels d’un rapport](service-reports-visual-interactions.md)

En savoir plus sur les [rapports dans Power BI](service-reports.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

