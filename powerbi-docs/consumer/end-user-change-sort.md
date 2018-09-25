---
title: Modifier le mode tri d’un graphique dans un rapport Power BI
description: Modifier le mode tri d’un graphique dans un rapport Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: dd8eeda3ba2bbc8da49a06199fa00dc3d731faaa
ms.sourcegitcommit: 70192daf070ede3382ac13f6001e0c8b5fb8d934
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46565886"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modifier le mode tri d’un graphique dans un rapport Power BI
Dans un rapport Power BI, vous pouvez trier la plupart des visualisations par ordre alphabétique en fonction des noms de catégories du graphique ou des valeurs numériques de chaque catégorie. Par exemple, ce graphique est trié par nom de magasin.

![](media/end-user-change-sort/pbi_chartsortcategory.png)

Il est facile de passer du tri par catégorie (nom de magasin) au tri par valeur (ventes par mètres carrés).

1. Sélectionnez les points de suspension (...) et choisissez **Trier par Sales Per Sq Ft** (Ventes par m²).
2. Si nécessaire, sélectionnez l’icône de tri ![](media/end-user-change-sort/sorticon.png) pour passer à un tri **Décroissant**.

   ![](media/end-user-change-sort/sortby.gif)

   **REMARQUE**: certains éléments visuels ne peuvent pas être triés.  C’est le cas, par exemple, des visuels suivants : Treemap, Carte géographique, Carte choroplèthe, Nuage de points, Jauge, Carte, Carte de plusieurs ligne, Cascade.

## <a name="saving-changes-you-make-to-sort-order"></a>Enregistrement de vos modifications de l’ordre de tri
Les rapports Power BI conservent les filtres, les sélecteurs, le tri et les autres changements que vous apportez aux vues de données. Ainsi, si vous quittez un rapport et que vous y revenez plus tard, vos modifications sont enregistrées.  Si vous voulez annuler vos modifications et revenir aux paramètres de l’auteur du rapport, sélectionnez **Rétablir les valeurs par défaut** dans la barre de menus du haut. 

![Tri persistant](./media/end-user-change-sort/power-bi-reset-to-default.png)

Cependant, si le bouton **Rétablir les valeurs par défaut** est grisé, cela signifie que l’auteur du rapport a désactivé la possibilité d’enregistrer vos modifications.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Tri à l’aide d’autres critères
Il peut parfois être utile de trier un visuel selon un autre champ ou d’autres critères.  Par exemple, vous pouvez être amené à effectuer un tri par mois (et non par ordre alphabétique) ou bien un tri par nombres entiers plutôt qu’un tri par chiffre (0, 1, 9, 20 et non 0, 1, 20, 9).  

Dans certains cas, vous pouvez trier le visuel de la manière souhaitée, par exemple, par mois.  Si ce n’est pas possible, ce peut être parce que le jeu de données sous-jacent au rapport a besoin de quelques ajustements. Plusieurs solutions s’offrent à vous :

* Dans Power BI Desktop, [utilisez l’onglet Modélisation des outils de données pour trier par une autre colonne](../desktop-sort-by-column.md).
* Dans Excel, si vous êtes le propriétaire du jeu de données, ajoutez une nouvelle colonne qui concatène le nom et le numéro du mois. Ensuite, actualisez ou réimportez le jeu de données pour afficher la nouvelle colonne dans la zone Champs.
* Dans Excel, vérifiez que vos colonnes numériques sont marquées au format « nombre entier » ou « décimal », et non au format « texte ».

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](../visuals/power-bi-report-visualizations.md).

[Power BI – Concepts de base](end-user-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
