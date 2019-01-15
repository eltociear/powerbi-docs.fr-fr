---
title: Utiliser l’affichage Modélisation dans Power BI Desktop (préversion)
description: Utilisez l’affichage Modélisation pour afficher des jeux de données complexes dans un format visuel dans Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 84e2bc663a4e3912608279c7315bc494b3c9844a
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296521"
---
# <a name="modeling-view-in-power-bi-desktop-preview"></a>Affichage Modélisation dans Power BI Desktop (préversion)

**L’affichage Modélisation** de **Power BI Desktop** permet d’afficher et d’utiliser des jeux de données complexes qui contiennent de nombreuses tables. Voici ses applications possibles :


## <a name="enabling-the-modeling-view-preview-feature"></a>Activer la fonctionnalité d’évaluation Affichage Modélisation

La fonctionnalité Affichage Modélisation, en préversion, doit être activée dans **Power BI Desktop**. Pour cela, sélectionnez **Fichier > Options et paramètres > Options > Fonctionnalités d’évaluation**, puis cochez la case **Affichage Modélisation** comme dans l’illustration suivante.

![Activer la fonctionnalité d'évaluation Affichage Modélisation dans Power BI Desktop](media/desktop-modeling-view/modeling-view_01.png)

Un message vous invitera à redémarrer **Power BI Desktop** pour activer la fonctionnalité d’évaluation. 

![Redémarrer Power BI Desktop pour activer les fonctionnalités d'évaluation](media/desktop-modeling-view/modeling-view_01b.png)

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
* [Modèles composites dans Power BI Desktop (préversion)](desktop-composite-models.md)
* [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md)
* [Relations plusieurs-à-plusieurs dans Power BI Desktop (préversion)](desktop-many-to-many-relationships.md)


Articles DirectQuery :

* [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI](desktop-directquery-data-sources.md)
