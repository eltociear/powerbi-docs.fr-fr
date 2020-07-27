---
title: Ajout de plusieurs champs à un segment de hiérarchie
description: Découvrez comment créer un segment de hiérarchie contenant plusieurs champs dans une hiérarchie.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 5fbaeaafb14fc935e26b4a2d13acf9dc09ea188f
ms.sourcegitcommit: 11deeccf596e9bb8f22615276a152614f7579f35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86409554"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Ajout de plusieurs champs à un segment de hiérarchie

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Pour filtrer plusieurs champs associés dans un même segment, créez ce que l’on appelle un segment de *hiérarchie*, soit dans Power BI Desktop, soit dans le service Power BI.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Capture d’écran du segment de hiérarchie dans Power BI":::

Lorsque plusieurs champs sont ajoutés au segment, il présente par défaut une flèche ou un *chevron* à côté des éléments dont les éléments du niveau suivant peuvent être développés.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Capture d’écran de la liste déroulante du segment de hiérarchie dans Power BI":::
 
 
Lorsqu’un ou plusieurs enfants d’un élément sont sélectionnés, un cercle semi-sélectionné apparaît pour l’élément de niveau supérieur.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Capture d’écran du segment de hiérarchie à sélection unique dans Power BI":::

## <a name="format-the-slicer"></a>Mettre en forme le segment

Le comportement du segment n’a pas changé. Vous pouvez également appliquer le style de votre choix à votre segment, par exemple, le définir en mode de sélection unique ou basculer entre une liste et une liste déroulante. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Capture d’écran du segment de hiérarchie sous forme de segment déroulant":::

Vous pouvez également apporter les modifications suivantes à la mise en forme.

### <a name="change-the-title"></a>Changer le titre

Vous pouvez modifier le titre de n’importe quel segment, ce qui est particulièrement utile pour les segments de hiérarchie. Par défaut, le nom d’un segment de hiérarchie correspond à la liste des noms de champs de la hiérarchie.

Dans cet exemple, le titre du segment liste les trois champs de la hiérarchie : Type, Platform et Name.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="Capture d’écran du segment de hiérarchie avec les champs Type, Platform et Name.":::

Pour modifier le nom, sélectionnez le segment, puis sélectionnez le volet **Format**. Sous **En-tête de segment**, vous voyez le nom actuel du segment dans la zone **Texte du titre**.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="Capture d’écran du volet Format avec le titre actuel.":::

Sélectionnez le texte et ajoutez un nom.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="Capture d’écran du nouveau titre du segment de hiérarchie.":::


### <a name="change-the-expandcollapse-icon"></a>Modification de l’icône Développer/Réduire

Les segments de hiérarchie proposent d’autres options de mise en forme. Vous pouvez remplacer la flèche par défaut de l’icône Développer/Réduire par un signe plus/moins ou un caret.

1. Sélectionnez le segment, puis **Format**.
1. Développez **Éléments** et sélectionnez **Icône Développer/Réduire**.
1. Choisissez entre **Chevron**, **Signe plus/moins** et **Caret**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Capture d’écran de la sélection d’une icône Développer/Réduire pour le segment de hiérarchie.":::
 
### <a name="change-the-indentation"></a>Modification de la mise en retrait

Si l’espace est limité sur votre rapport, vous pouvez réduire le retrait des éléments enfants. La mise en retrait est par défaut de 15 pixels, mais vous pouvez l’augmenter ou la réduire. 

1. Sélectionnez le segment, puis **Format**.
1. Développez **Éléments**, puis faites glisser **Mise en retrait de la disposition échelonnée** vers la gauche (plus petite) ou vers la droite (plus grande). Vous pouvez également taper simplement un nombre dans la zone.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Capture d’écran de la définition de la mise en retrait du segment de hiérarchie.":::

## <a name="next-steps"></a>Étapes suivantes

- [Segments dans Power BI](../visuals/power-bi-visualization-slicers.md)
- D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)