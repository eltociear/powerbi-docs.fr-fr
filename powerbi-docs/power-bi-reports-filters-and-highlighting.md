---
title: Filtres et mise en évidence dans les rapports Power BI
description: À propos des filtres et de la mise en évidence dans les rapports Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 8084b8dbbc27c856633d84c6628727dcd426964d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187538"
---
# <a name="filters-and-highlighting-in-power-bi-reports"></a>Filtres et mise en évidence dans les rapports Power BI
 Cet article vous présente le filtrage et mise en évidence dans le service Power BI. L’expérience est presque la même dans Power BI Desktop. Les *filtres* masquent tout, sauf les données qui vous intéressent. *Mise en surbrillance* n’est pas le filtrage. Il ne supprime les données, mais au lieu de cela met en évidence un sous-ensemble des données visibles ; les données qui n’est pas mise en évidence restent visibles, mais sont estompées.

Il existe de nombreuses façons de filtrer et de mettre en évidence des rapports dans Power BI. Expliquer ces méthodes dans un seul article serait déroutant. Nous les avons donc réparties comme suit :

* Présentation des filtres et mise en surbrillance, de l’article vous lisez maintenant.
* Comment [créer et utiliser des filtres en mode édition](power-bi-report-add-filter.md) dans les rapports dans Power BI Desktop et le service Power BI. Quand vous disposez d’autorisations de modification d’un rapport, vous pouvez créer, modifier et supprimer les filtres dans ces rapports.
* Comment visuels [filtrer et mettre en surbrillance dans un rapport partagé avec vous](consumer/end-user-interactions.md), en mode lecture dans le service Power BI des rapports. Ce que vous pouvez faire est plus limité, mais vous disposez toujours d’un large éventail d’options de filtrage et de mise en surbrillance.  
* Visite guidée détaillée de la [de filtre et de mise en évidence des contrôles disponibles en mode édition](power-bi-report-add-filter.md) dans Power BI Desktop et le service Power BI. L’article prend un examen approfondi des types de filtres tels que la date et l’heure, numérique et le texte. Il couvre également les différences entre les options de base et avancées.
* Après avoir découvert le fonctionnement par défaut des filtres et de la mise en surbrillance, découvrez comment [modifier l’affichage des visualisations sur un filtre au niveau de la page et effectuer une mise en surbrillance](service-reports-visual-interactions.md)

**Le saviez-vous ?** Power BI a une nouvelle expérience de filtre, actuellement en préversion. En savoir plus sur [la nouvelle expérience de filtre dans les rapports Power BI](power-bi-report-filter-preview.md).

![Nouvelle expérience de filtre](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading.png)


## <a name="intro-to-the-filters-pane"></a>Présentation du volet Filtres

Vous pouvez appliquer des filtres dans le volet **Filtres** ou en [effectuant des sélections dans des segments](visuals/power-bi-visualization-slicers.md) directement dans le rapport. Le volet Filtres montre les tables et les champs utilisés dans le rapport et les filtres qui ont été appliqués, le cas échéant. 

![Le volet Filtres](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Il existe quatre types de filtres.

- Un **filtre de page** s’applique à tous les visuels d’une page de rapport.     
- Un **filtre visuel** s’applique à un seul visuel d’une page de rapport. Les filtres au niveau du visuel s’affichent uniquement si vous avez sélectionné un visuel sur le canevas de rapport.    
- Un **filtre de rapport** s’applique à toutes les pages du rapport.    
- Un **filtre d’extraction** s’applique à une seule entité dans un rapport.    

Vous pouvez exécuter une recherche dans la page, le visuel et les filtres de rapport, en mode Lecture ou Édition, pour rechercher et sélectionner la valeur souhaitée. 

![Recherche dans un filtre](media/power-bi-reports-filters-and-highlighting/power-bi-search-filter.png)

Si le mot **Tout** s’affiche en regard du filtre, cela signifie que toutes les valeurs dans le champ sont incluses dans le filtre.  Par exemple, dans la capture d’écran ci-dessous, **Chain(Tout)** indique que cette page de rapport inclut des données sur toutes les chaînes de magasin.  En revanche, le filtre au niveau du rapport **AnnéeFiscale est 2013 ou 2014** indique que le rapport inclut des données uniquement pour les années fiscales 2013 et 2014.

## <a name="filters-in-reading-or-editing-view"></a>Filtres en mode Lecture ou Édition
Il existe deux modes d’interaction avec les rapports : le [mode Lecture](consumer/end-user-reading-view.md) et le mode Édition. Les fonctionnalités de filtrage disponibles varient en fonction du mode dans lequel vous êtes.

* En mode Édition, vous pouvez ajouter des filtres de rapport, de page, d’exploration et de visuel. Quand vous enregistrez le rapport, les filtres sont enregistrés avec le rapport, même si vous l’ouvrez dans une application mobile. Les personnes qui consultent le rapport en mode Lecture peuvent interagir avec les filtres que vous avez ajoutés, mais elles ne peuvent pas ajouter de nouveaux filtres.
* En mode Lecture, vous pouvez interagir avec les filtres qui déjà existent dans le rapport et enregistrer les sélections que vous effectuez. Vous ne pouvez pas ajouter de nouveaux filtres.

### <a name="filters-in-reading-view"></a>Filtres en mode Lecture
Si vous avez uniquement accès à un rapport en mode Lecture, le volet Filtres a l’aspect suivant :

![Filtres en mode Lecture](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Par conséquent, cette page de rapport a 6 filtres au niveau de la page et 1 filtre au niveau du rapport.

Chaque visuel peut avoir des filtres pour tous les champs dans le visuel et un auteur de rapport peut en ajouter d’autres. Dans l’image ci-dessous, 6 filtres ont été appliqués au graphique en bulles.

![Filtres au niveau du visuel](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

En mode Lecture, explorez les données en modifiant les filtres existants. Les modifications que vous avez apportées sont enregistrées avec le rapport, même si vous ouvrez le rapport dans une application mobile. Découvrez comment en [explorant le volet Filtres de rapport](consumer/end-user-report-filter.md)

Quand vous quittez le rapport, vos filtres sont enregistrés. Pour annuler votre filtrage et revenir au filtrage, à la segmentation, à l’extraction et au tri définis par défaut par l’auteur du rapport, sélectionnez **Rétablir les valeurs par défaut** dans la barre de menus du haut.

![Réinitialiser l’icône par défaut](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

### <a name="filters-in-editing-view"></a>Filtres en mode Édition
Quand vous disposez des autorisations de propriétaire sur un rapport et que vous ouvrez celui-ci en mode Édition, **Filtres** est l’un des volets d’édition disponibles.

![Volet filtres en mode édition](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

Comme en mode Lecture, cette page de rapport a 6 filtres au niveau de la page et 1 filtre au niveau du rapport. Quand vous sélectionnez le graphique en bulles, vous voyez que 6 filtres au niveau du visuel s’appliquent.

Il est possible d’en faire plus avec les filtres et la mise en surbrillance en mode Édition. Principalement, nous pouvons ajouter de nouveaux filtres. Découvrez comment [ajouter un filtre à un rapport](power-bi-report-add-filter.md) et bien plus encore.

## <a name="ad-hoc-highlighting"></a>Mise en évidence ad hoc
Sélectionner une étiquette de valeur ou un axe dans un visuel pour mettre en évidence les autres visuels sur la page. Pour supprimer la mise en surbrillance, sélectionnez à nouveau de la valeur, ou sélectionnez un espace vide dans le même visuel. Mise en surbrillance est un plaisir permet d’Explorer rapidement l’impact des données. Pour plus d’informations sur la mise en surbrillance croisée, consultez [Interactions entre les visuels](service-reports-visual-interactions.md).

![Mise en surbrillance croisée](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)


## <a name="next-steps"></a>Étapes suivantes

[La nouvelle expérience de filtre dans les rapports Power BI](power-bi-report-filter-preview.md)

[Ajouter un filtre à un rapport (en mode Édition)](power-bi-report-add-filter.md)

[Découvrir les filtres de rapport](consumer/end-user-report-filter.md)

[Modifier la façon dont le filtrage croisé et la mise en évidence croisée affectent les visuels d’un rapport](consumer/end-user-interactions.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

