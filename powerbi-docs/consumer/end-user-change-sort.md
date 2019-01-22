---
title: Changer le mode tri d’un graphique dans un rapport
description: Modifier le mode tri d’un graphique dans un rapport Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: Conceptual
ms.date: 01/17/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e648257ecd657b07d02fbff69a3424159b636059
ms.sourcegitcommit: ccbe76a0a43c5c5e87354a33e617bf3cb291608e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394679"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modifier le mode tri d’un graphique dans un rapport Power BI
Dans un rapport Power BI, vous pouvez trier la plupart des visualisations par ordre alphabétique en fonction des noms de catégories du graphique ou des valeurs numériques de chaque catégorie. Par exemple, ce graphique est trié par la catégorie **nom de magasin**.

![graphique à barres trié par l’axe des X](media/end-user-change-sort/pbi_chartsortcategory.png)

Il est facile de passer du tri par catégorie (nom de magasin) au tri par valeur (ventes par mètres carrés).

1. Sélectionnez les points de suspension (...) et choisissez **Trier par > Sales Per Sq Ft** (Ventes par m²).
2. Si nécessaire, sélectionnez les points de suspension à nouveau et choisissez **Tri décroissant**.

   ![vidéo montrant la sélection de Trier par, puis Croissant et Décroissant](media/end-user-change-sort/sort.gif)

   **REMARQUE** : Certains visuels ne peuvent pas être triés.  Par exemple, les visuels suivants ne peuvent pas être triés : Arborescence, Carte géographique, Carte choroplèthe, Nuage de points, Jauge, Carte, Carte de plusieurs ligne, Cascade.

## <a name="saving-changes-you-make-to-sort-order"></a>Enregistrement de vos modifications de l’ordre de tri
Les rapports Power BI conservent les filtres, les sélecteurs, le tri et les autres changements que vous apportez aux vues de données. Ainsi, si vous quittez un rapport et que vous y revenez plus tard, vos modifications sont enregistrées.  Si vous voulez annuler vos changements et revenir aux paramètres du concepteur du rapport, sélectionnez **Rétablir les valeurs par défaut** dans la barre de menus du haut. 

![Tri persistant](media/end-user-change-sort/power-bi-reset-to-default.png)

Cependant, si le bouton **Rétablir les valeurs par défaut** est grisé, cela signifie que le concepteur du rapport a désactivé la possibilité d’enregistrer vos changements.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Tri à l’aide d’autres critères
Il peut parfois être utile de trier un visuel selon un autre champ ou d’autres critères.  Par exemple, vous pouvez être amené à effectuer un tri par mois (et non par ordre alphabétique) ou bien un tri par nombres entiers plutôt qu’un tri par chiffre (0, 1, 9, 20 et non 0, 1, 20, 9).  

Dans certains cas, vous pouvez trier le visuel de la manière souhaitée, par exemple, par mois.  Si ce n’est pas possible, ce peut être parce que le jeu de données sous-jacent au rapport a besoin de quelques ajustements. Demandez au concepteur du rapport de mettre à jour le jeu de données.

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](end-user-visualizations.md).

[Power BI – Concepts de base](end-user-basic-concepts.md)