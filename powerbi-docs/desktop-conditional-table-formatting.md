---
title: Mise en forme conditionnelle des tables dans Power BI Desktop
description: Appliquer une mise en forme personnalisée aux tables
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9599b40940c9d9cca254bb2ed2e87c161cce371f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="conditional-formatting-in-tables"></a>Mise en forme conditionnelle dans les tables
Avec la mise en forme conditionnelle dans les tables, vous pouvez spécifier des couleurs d’arrière-plan de cellule personnalisées en fonction des valeurs de cellule, ou d’autres valeurs ou champs, et également utiliser des couleurs de dégradé. Pour accéder à la mise en forme conditionnelle, dans la zone **Champs** du volet **Visualisations** de Power BI Desktop, sélectionnez la flèche vers le bas à côté de la valeur dans la zone **Valeurs** que vous voulez mettre en forme (ou cliquez avec le bouton droit sur le champ). Vous pouvez uniquement gérer la mise en forme conditionnelle des champs dans la zone **Valeurs** de la zone **Champs**.

![mise en forme conditionnelle dans les tables](media/desktop-conditional-table-formatting/table-formatting_1.png)

Dans la boîte de dialogue qui s’affiche, vous pouvez configurer la couleur, ainsi que les valeurs *Minimum* et *Maximum*. Si vous sélectionnez la zone **Divergent**, vous pouvez également configurer une valeur *Centrale* en option.

![couleurs divergentes](media/desktop-conditional-table-formatting/table-formatting_2.png)

Vous pouvez également définir le dégradé de couleurs sur la base d’un champ de votre modèle de données. De plus, vous pouvez spécifier le type d’agrégation du champ sélectionné (le champ sélectionné est indiqué dans le champ **Appliquer une couleur à** pour faciliter le suivi).

![couleurs basées sur un champ](media/desktop-conditional-table-formatting/table-formatting_2b.png)

La mise en forme personnalisée appliquée à une table selon la procédure décrite ci-dessus remplace les styles de table personnalisés appliqués aux cellules soumises à une mise en forme conditionnelle.

![mise en forme de la table](media/desktop-conditional-table-formatting/table-formatting_3.png)

Vous pouvez également appliquer une mise en forme conditionnelle à des champs de date et de texte, à condition de choisir une valeur numérique comme base de la mise en forme. 

Pour supprimer la mise en forme conditionnelle d’une visualisation, il suffit de cliquer à nouveau avec le bouton droit sur le champ et de sélectionner **Supprimer la mise en forme conditionnelle**.

![supprimer la mise en forme conditionnelle de la table](media/desktop-conditional-table-formatting/table-formatting_4.png)

