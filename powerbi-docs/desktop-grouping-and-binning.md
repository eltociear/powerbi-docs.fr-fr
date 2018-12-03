---
title: Utiliser le regroupement et le compartimentage dans Power BI Desktop
description: Découvrez comment utiliser des éléments de groupe et de compartimentage dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6363cbe3afdce351acc728fe29af8662702b8254
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670690"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>Utiliser le regroupement et le compartimentage dans Power BI Desktop
Lorsque **Power BI Desktop** crée des visuels, il regroupe vos données en blocs (ou groupes) en fonction des valeurs trouvées dans les données sous-jacentes. Cela suffit généralement, mais vous pouvez affiner la présentation de ces segments. Par exemple, vous pouvez placer trois catégories de produits dans une catégorie supérieure (un *groupe*). Ou vous pouvez souhaiter afficher les chiffres de ventes dans des compartiments de 1 000 000 dollars, au lieu de compartiments de 923 983 dollars divisés de façon égale.

Dans Power BI Desktop, vous pouvez **Grouper** des points de données pour vous aider à afficher, analyser et explorer plus clairement les données et les tendances de vos visuels. Vous pouvez également définir la **Taille du compartiment**, souvent appelée *quantification*, pour placer des valeurs dans des groupes de taille égale qui vous permettent de visualiser les données de manière explicite.

### <a name="using-grouping"></a>Utilisation du regroupement
Pour utiliser le regroupement, sélectionnez deux éléments ou plus d’un visuel à l’aide de Ctrl+clic pour sélectionner plusieurs éléments. Cliquez ensuite avec le bouton de droite sur les éléments sélectionnés, puis sélectionnez **Groupe** dans le menu qui s’affiche.

![](media/desktop-grouping-and-binning/grouping-binning_1.png)

Une fois créé, le groupe est ajouté au compartiment **Légende** du visuel et apparaît également dans la liste **Champs**.

![](media/desktop-grouping-and-binning/grouping-binning_2.png)

Une fois que vous disposez d’un groupe, vous pouvez facilement modifier les membres de ce groupe en cliquant avec le bouton de droite sur le champ à partir du compartiment **Légende** ou de la liste **Champs**, puis en sélectionnant **Modifier les groupes**.

![](media/desktop-grouping-and-binning/grouping-binning_3.png)

Dans la fenêtre **Groupes** qui s’affiche, vous pouvez créer des groupes ou modifier les groupes existants. Vous pouvez également *renommer* un groupe en double-cliquant sur le titre du groupe dans la boîte **Groupes et membres**, puis en appuyant sur un nouveau nom.

Vous pouvez réaliser toute sorte de choses avec les groupes. Vous pouvez ajouter des éléments de la liste **Valeurs non groupées** dans un nouveau groupe ou dans les groupes existants. Pour créer un nouveau groupe, sélectionnez deux éléments ou plus (à l’aide de Ctrl+clic) à partir de la boîte **Valeurs non groupées**, puis cliquez sur le bouton **Groupe** sous cette boîte.

Vous pouvez ajouter une valeur non groupée dans un groupe existant : sélectionnez simplement la valeur non groupée, puis le groupe existant auquel vous souhaitez l’ajouter et cliquez sur le bouton **Groupe**. Pour supprimer un élément d’un groupe, sélectionnez-le dans la zone **Groupes et membres**, puis cliquez sur **Dissocier**. Vous pouvez également indiquer si les catégories sans groupe doivent être placées dans le groupe **Autres** ou rester non groupées.

![](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> Vous pouvez créer des groupes pour n’importe quel champ de la zone **Champs** sans avoir à effectuer une sélection multiple à partir d’un visuel existant. Cliquez avec le bouton de droite et sélectionnez **Nouveau groupe** dans le menu qui s’affiche.
> 
> 

### <a name="using-binning"></a>Utilisation du compartimentage
Vous pouvez définir la taille de compartiment des champs numériques et horaires dans **Power BI Desktop.** Vous pouvez utiliser le compartimentage pour redimensionner correctement les données affichées par **Power BI Desktop**.

Pour appliquer une taille de compartiment, cliquez avec le bouton de droite sur un **Champ** et sélectionnez **Nouveau groupe**.

![](media/desktop-grouping-and-binning/grouping-binning_5.png)

Dans la fenêtre **Groupes**, configurez la **taille de compartiment** souhaitée.

![](media/desktop-grouping-and-binning/grouping-binning_6.png)

Lorsque vous sélectionnez **OK**, vous remarquez qu’un nouveau champ s’affiche dans le volet **Champs** et que *(compartiments)* a été ajouté. Vous pouvez ensuite faire glisser ce champ sur le canevas pour utiliser la taille de compartiment dans un visuel.

![](media/desktop-grouping-and-binning/grouping-binning_7.png)

Pour voir le **compartimentage** en action, regardez cette [vidéo](https://www.youtube.com/watch?v=BRvdZSfO0DY).

Voici tout ce que vous deviez savoir sur l’utilisation du **regroupement** et du **compartimentage** pour vous assurer que les visuels de vos rapports affichent vos données uniquement comme vous le souhaitez.

