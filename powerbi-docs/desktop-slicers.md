---
title: Utilisation de segments Power BI Desktop
description: Vous pouvez utiliser des segments dans Power BI Desktop pour filtrer, mettre en surbrillance et personnalisation des rapports
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/05/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: fabbd56f94ae519f1ea88a7473683f93131b08c3
ms.sourcegitcommit: 65426de556cd7207cbc4f478198664e25c33a769
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="using-slicers-power-bi-desktop"></a>Utilisation de segments Power BI Desktop

Vous pouvez utiliser un **segment** dans **Power BI Desktop** pour filtrer les résultats de visuels sur la page de votre rapport. Et les segments vous permettent d’ajuster facilement le filtre appliqué en interagissant avec le segment lui-même. Vous pouvez également spécifier des options pour définir l’apparence de votre segment et votre interaction avec lui. L’illustration suivante montre un segment et son menu déroulant *Type*. 

![](media/desktop-slicers/desktop-slicers_01.png)

Un segment peut être affiché selon différents types :

* List
* Liste déroulante
* Entre
* Inférieur ou égal à
* Supérieur ou égal à

Vous pouvez ajouter un segment à un rapport en cliquant sur le visuel du **segment** dans le volet **Visualisations**.

![](media/desktop-slicers/desktop-slicers_02.png)

Les segments se comportent de la même façon dans **Power BI Desktop** et le **service Power BI**. Pour obtenir un didacticiel sur l’utilisation des segments, consultez [Segments dans le service Power BI (didacticiel)](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Synchroniser des segments entre les pages d’un rapport

Dans **Power BI Desktop** vous pouvez synchroniser des segments entre plusieurs pages d’un rapport. Pour synchroniser des segments, dans le volet **Affichage** du ruban, sélectionnez **Synchroniser les segments**. Lorsque vous synchronisez des segments, le volet **Synchroniser les segments** s’affiche, comme illustré dans l’image suivante.

![](media/desktop-slicers/desktop-slicers_03.png)

Dans le volet **Synchroniser les segments**, vous pouvez spécifier comment le segment doit être synchronisé entre les pages du rapport. Vous pouvez spécifier si chaque segment doit être **appliqué** à chaque page du rapport, et si le segment doit être **visible** sur chacune de ces pages.

Par exemple, vous pouvez placer un segment sur la **page 2** de votre rapport, comme illustré dans l’image suivante. Vous pouvez ensuite spécifier si ce segment doit *s’appliquer* à chaque page sélectionnée, et si ce segment doit être *visible* sur chaque page du rapport sélectionné. Vous pouvez appliquer n’importe quelle combinaison de ces options, pour chaque segment. 

![](media/desktop-slicers/desktop-slicers_04.png)

Le lien **Ajouter à tous** du volet applique le segment sélectionné à toutes les pages du rapport.

Notez que les sélections indiquées dans le volet **Synchroniser les segments** s’appliquent uniquement au *segment sélectionné*. Vous pouvez appliquer plusieurs segments à différentes pages, et utiliser le volet pour définir la façon dont chaque segment est appliqué individuellement dans les différentes pages de votre rapport. 

Votre sélection de segments peut être synchronisée, mais d’autres sélections comme la définition du style, la modification et la suppression ne sont *pas* synchronisées. 

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Segments dans le service Power BI (didacticiel)](power-bi-visualization-slicers.md)
* [Utiliser le Sélecteur de plages numériques dans Power BI Desktop](desktop-slicer-numeric-range.md)
* [Utiliser un segment et un filtre de date relative dans Power BI Desktop](desktop-slicer-filter-date-range.md)

