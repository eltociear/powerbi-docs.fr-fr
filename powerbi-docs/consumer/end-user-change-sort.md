---
title: Changer le mode tri d’un graphique dans un rapport
description: Changer le mode tri d’un graphique dans un rapport Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: Conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 191dfdeba436322052befdbc6548fd08f96f0738
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280003"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Changer le mode tri d’un graphique dans un rapport Power BI
Dans un rapport Power BI, vous pouvez trier la plupart des visualisations par ordre alphabétique en fonction des noms de catégories du graphique ou des valeurs numériques de chaque catégorie. Par exemple, ce graphique est trié par la catégorie **nom de magasin**.

![graphique à barres trié par l’axe des X](media/end-user-change-sort/pbi_chartsortcategory.png)

Il est facile de passer du tri par catégorie (nom de magasin) au tri par valeur (ventes par mètres carrés).

1. Sélectionnez les points de suspension (...) et choisissez **Trier par > Sales Per Sq Ft** (Ventes par m²).
2. Si nécessaire, sélectionnez les points de suspension à nouveau et choisissez **Tri décroissant**.

   ![vidéo montrant la sélection de Trier par, puis Croissant et Décroissant](media/end-user-change-sort/sort.gif)

   **REMARQUE** : Certains visuels ne peuvent pas être triés.  Par exemple, les visuels suivants ne peuvent pas être triés : Arborescence, Carte géographique, Carte choroplèthe, Nuage de points, Jauge, Carte, Carte de plusieurs ligne, Cascade.

## <a name="saving-changes-you-make-to-sort-order"></a>Enregistrement de vos modifications de l’ordre de tri
Les rapports Power BI conservent les filtres, les sélecteurs, le tri et les autres changements que vous apportez aux vues de données. Ainsi, si vous quittez un rapport et que vous y revenez plus tard, vos modifications sont enregistrées.  Si vous voulez annuler vos modifications et revenir aux paramètres du créateur du rapport, sélectionnez **Rétablir les valeurs par défaut** dans la barre de menus du haut. 

![Tri persistant](media/end-user-change-sort/power-bi-reset-to-default.png)

Cependant, si le bouton **Rétablir les valeurs par défaut** est grisé, cela signifie que le créateur du rapport a désactivé la possibilité d’enregistrer vos modifications.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Tri à l’aide d’autres critères
Il peut parfois être utile de trier un visuel selon un autre champ ou d’autres critères.  Par exemple, vous pouvez être amené à effectuer un tri par mois (et non par ordre alphabétique) ou bien un tri par nombres entiers plutôt qu’un tri par chiffre (0, 1, 9, 20 et non 0, 1, 20, 9).  

Dans certains cas, vous pouvez trier le visuel de la manière souhaitée, par exemple, par mois.  Si ce n’est pas possible, ce peut être parce que le jeu de données sous-jacent au rapport a besoin de quelques ajustements. Demandez au créateur du rapport de mettre à jour le jeu de données.

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](end-user-visualizations.md).

[Power BI – Concepts de base](end-user-basic-concepts.md)