---
title: Utiliser le mode de modélisation dans Power BI Desktop
description: Utilisez l’affichage Modélisation pour afficher des jeux de données complexes dans un format visuel dans Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 1fdb6058a6306f63f53c770812f85ccd9f9113ea
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941344"
---
# <a name="modeling-view-in-power-bi-desktop"></a>Vue de modélisation dans Power BI Desktop

**L’affichage Modélisation** de **Power BI Desktop** permet d’afficher et d’utiliser des jeux de données complexes qui contiennent de nombreuses tables.


## <a name="using-modeling-view"></a>Utiliser l’affichage Modélisation

Pour accéder à l’affichage Modélisation, sélectionnez l’icône Affichage Modélisation qui se trouve sur le côté gauche de **Power BI Desktop**, comme dans l’illustration suivante.

![Icône Affichage Modélisation dans Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Créer des diagrammes séparés

Avec l’affichage Modélisation, vous pouvez créer des diagrammes de votre modèle qui ne contiennent qu’un sous-ensemble des tables de votre modèle. Vous aurez ainsi une vision plus claire des tables que vous souhaitez utiliser et pourrez travailler plus facilement avec des jeux de données complexes. Pour créer un diagramme comportant seulement un sous-ensemble des tables, cliquez sur le signe **+** à côté de l’onglet **Toutes les tables**, en bas de la fenêtre Power BI Desktop.

![Créer un diagramme en cliquant sur le signe + dans la section des onglets](media/desktop-modeling-view/modeling-view_03.png)

Vous pouvez ensuite faire glisser une table de la ligne **Champs** à la surface du diagramme. Cliquez avec le bouton droit sur la table, puis sélectionnez **Ajouter des tables associées** dans le menu qui s’affiche.

![Cliquer avec le bouton droit sur une table et sélectionner Ajouter des tables associées](media/desktop-modeling-view/modeling-view_04.png)

Les tables liées à la table d’origine s’affichent alors dans le nouveau diagramme. L’illustration suivante montre comment apparaissent les tables associées lorsque l’option de menu **Ajouter des tables associées** est sélectionnée.

![Afficher les tables associées](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Définir des propriétés communes

Pour sélectionner plusieurs objets à la fois dans l’affichage Modélisation, maintenez la touche **CTRL** enfoncée et cliquez sur plusieurs tables. Les tables sélectionnées sont mises en surbrillance dans l’affichage Modélisation. Les modifications effectuées dans le volet **Propriétés** s’appliquent à toutes les tables sélectionnées.

Supposons que vous souhaitiez modifier le [mode de stockage](desktop-storage-mode.md) de plusieurs tables dans votre affichage en diagrammes : maintenez la touche **CTRL** enfoncée, sélectionnez les tables, puis modifiez le paramètre du mode de stockage dans le volet **Propriétés**.

![Sélectionner plusieurs tables en maintenant la touche CTRL enfoncée, puis en définissant des propriétés communes à toutes les tables sélectionnées](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Étapes suivantes

Les articles suivants décrivent plus en détail les modèles de données ainsi que le mode DirectQuery.

* [Agrégations dans Power BI Desktop (préversion)](desktop-aggregations.md)
* [Modèles composites dans Power BI Desktop](desktop-composite-models.md)
* [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md)
* [Relations plusieurs à plusieurs dans Power BI Desktop](desktop-many-to-many-relationships.md)


Articles DirectQuery :

* [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI](desktop-directquery-data-sources.md)
