---
title: Utilisation de segments Power BI Desktop
description: Vous pouvez utiliser des segments dans Power BI Desktop pour filtrer, mettre en surbrillance et personnalisation des rapports
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: df4afe91de955eabfba6eeea9022cc5f9475cc33
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336849"
---
# <a name="using-slicers-power-bi-desktop"></a>Utilisation de segments Power BI Desktop

Vous pouvez utiliser un **segment** dans **Power BI Desktop** pour filtrer les résultats de visuels sur la page de votre rapport. Et les segments vous permettent d’ajuster facilement le filtre appliqué en interagissant avec le segment lui-même. Vous pouvez également spécifier des options pour définir l’apparence de votre segment et votre interaction avec lui. L’illustration suivante montre un segment et son menu déroulant *Type*. 

![segments dans Desktop](./media/desktop-slicers/desktop-slicers_01.png)

Un segment peut être affiché selon différents types :

* Liste
* Liste déroulante
* Entre
* Inférieur ou égal à
* Supérieur ou égal à

Vous pouvez ajouter un segment à un rapport en cliquant sur le visuel du **segment** dans le volet **Visualisations**.

![type de visuel de segment](./media/desktop-slicers/desktop-slicers_02.png)

Les segments se comportent de la même façon dans **Power BI Desktop** et le **service Power BI**. Pour obtenir un article sur l’utilisation des segments, consultez [Segments dans le service Power BI](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Synchroniser des segments entre les pages d’un rapport

Dans **Power BI Desktop** vous pouvez synchroniser des segments entre plusieurs pages d’un rapport. Pour synchroniser des segments, dans le volet **Affichage** du ruban, sélectionnez **Synchroniser les segments**. Lorsque vous synchronisez des segments, le volet **Synchroniser les segments** s’affiche, comme illustré dans l’image suivante.

![afficher le volet Synchroniser les segments](./media/desktop-slicers/desktop-slicers_03.png)

Dans le volet **Synchroniser les segments**, vous pouvez spécifier comment le segment doit être synchronisé entre les pages du rapport. Vous pouvez spécifier si chaque segment doit être **appliqué** à chaque page du rapport, et si le segment doit être **visible** sur chacune de ces pages.

Par exemple, vous pouvez placer un segment sur la **page 2** de votre rapport, comme illustré dans l’image suivante. Vous pouvez ensuite spécifier si ce segment doit *s’appliquer* à chaque page sélectionnée, et si ce segment doit être *visible* sur chaque page du rapport sélectionné. Vous pouvez appliquer n’importe quelle combinaison de ces options, pour chaque segment. 

![synchroniser les segments](./media/desktop-slicers/desktop-slicers_04.png)

Le lien **Ajouter à tous** du volet applique le segment sélectionné à toutes les pages du rapport.


Notez que les sélections indiquées dans le volet **Synchroniser les segments** s’appliquent uniquement au *segment sélectionné*. Vous pouvez appliquer plusieurs segments à différentes pages, et utiliser le volet pour définir la façon dont chaque segment est appliqué individuellement dans les différentes pages de votre rapport. 

Votre sélection de segments peut être synchronisée, mais d’autres sélections comme la définition du style, la modification et la suppression ne sont *pas* synchronisées. 

## <a name="advanced-options-for-slicers"></a>Options avancées pour les segments

Vous pouvez également appliquer un **nom de groupe** à une collection de segments dans la section **Options avancées** du volet **Synchroniser les segments**, et configurer la synchronisation des segments d’un même groupe dans toutes les pages. 

![nom du groupe de segments](./media/desktop-slicers/desktop-slicers_05.png)

Cette fonctionnalité vous permet de créer un groupe personnalisé de segments à maintenir synchronisés. Vous pouvez utiliser le nom par défaut fourni ou un nom de votre choix. 

Le nom de groupe rend l’utilisation des segments plus souple. Vous pouvez créer des groupes distincts pour synchroniser les segments qui utilisent le même champ, ou placer les segments avec des champs différents dans le même groupe. 

## <a name="how-filtering-affects-selection-in-slicers"></a>Comment le filtrage affecte la sélection dans les segments

Si vous effectuez une sélection dans un segment et appliquez ensuite un filtre qui supprimerait normalement l’élément sélectionné, celui-ci reste en bas de la liste des éléments dans le segment. Si le filtre est supprimé, la sélection est toujours présente dans le segment. Vous remarquerez que si vous désélectionnez l’élément dans le segment, il disparaît de la liste.

![sélection conservée dans les segments](./media/desktop-slicers/retained-selection-in-slicers.gif)


## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Segments dans le service Power BI](power-bi-visualization-slicers.md)
* [Utiliser le Sélecteur de plages numériques dans Power BI Desktop](../desktop-slicer-numeric-range.md)
* [Utiliser un segment et un filtre de date relative dans Power BI Desktop](desktop-slicer-filter-date-range.md)

