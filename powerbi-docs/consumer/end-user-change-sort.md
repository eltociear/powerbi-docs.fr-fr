---
title: Changer le mode tri d’un graphique dans un rapport
description: Modifier le mode tri d’un graphique dans un rapport Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/19/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 1a59618ea27944314465d8e08d5f0c249c3bed0b
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496476"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modifier le mode tri d’un graphique dans un rapport Power BI

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]


> [!IMPORTANT]
> **Cet article s’adresse aux utilisateurs de Power BI qui ne disposent pas d’autorisations de modification sur le rapport ou le jeu de données et qui travaillent uniquement avec la version en ligne de Power BI (le service Power BI). Si vous êtes *concepteur*, *administrateur* ou *propriétaire* de rapports, il se peut que cet article ne comporte pas toutes les informations dont vous avez besoin. Lisez plutôt [Trier par colonne dans Power BI Desktop](../desktop-sort-by-column.md)** .

Dans le service Power BI, vous pouvez changer l’apparence d’un visuel en le triant par différents champs de données. En changeant la façon dont vous triez un visuel, vous pouvez mettre en évidence les informations que vous voulez transmettre. Que vous utilisiez des données numériques (comme des chiffres de ventes) ou des données de texte (comme des noms d’État), vous pouvez trier vos visualisations comme vous le souhaitez. Power BI offre une grande souplesse sur le plan du tri et des menus rapides que vous pouvez utiliser. 

Les visuels affichés sur un tableau de bord ne peuvent pas être triés, mais dans un rapport Power BI, vous pouvez trier la plupart des visualisations 

## <a name="get-started"></a>Commencer

Pour commencer, ouvrez un rapport qui a été partagé avec vous. Sélectionnez un visuel (pouvant être trié) et choisissez **Plus d’actions** (...).  Il existe trois options pour le tri : **Tri décroissant**, **Tri croissant** et **Trier par**. 
    

![graphique à barres trié par l’axe des X](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Trier par ordre alphabétique ou par ordre numérique

Les visuels peuvent être triés par ordre alphabétique selon le nom textuel des catégories du visuel, ou la valeur numérique de chaque catégorie. Par exemple, ce graphique est trié par ordre alphabétique en fonction de la catégorie de l’axe X **Nom** des magasins.

![graphique à barres trié par l’axe des X](media/end-user-change-sort/powerbi-sort-category.png)

Il est facile de passer du tri par catégorie (nom de magasin) au tri par valeur (ventes par mètres carrés). Sélectionnez **Plus d’actions** (...), puis choisissez **Trier par**. Sélectionnez une valeur numérique utilisée dans le visuel.  Dans cet exemple, nous avons sélectionné **Sales Per Sq Ft** (Ventes par pied carré).

![Capture d’écran montrant la sélection de Trier par, puis d’une valeur](media/end-user-change-sort/power-bi-sort-value.png)

Si nécessaire, changez l’ordre de tri de croissant à décroissant.  Resélectionnez **Plus d’actions** (...), puis choisissez **Tri décroissant** ou **Tri croissant**. Le champ utilisé pour le tri est en gras et a une barre jaune.

   ![vidéo montrant la sélection de Trier par, puis Croissant et Décroissant](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Certains visuels ne peuvent pas être triés. C’est le cas, par exemple, des visuels suivants : treemap, carte géographique, carte choroplèthe, nuage de points, jauge, carte, cascade.

## <a name="saving-changes-you-make-to-sort-order"></a>Enregistrement de vos modifications de l’ordre de tri
Les rapports Power BI conservent les filtres, les segments, le tri et les autres changements que vous apportez aux vues de données, même si vous travaillez en [Mode Lecture](end-user-reading-view.md). Ainsi, si vous quittez un rapport et que vous y revenez plus tard, vos changements de tri sont enregistrés.  Si vous voulez annuler vos changements et revenir aux paramètres du *concepteur* du rapport, sélectionnez **Rétablir les valeurs par défaut** dans la barre de menus supérieure. 

![Tri persistant](media/end-user-change-sort/power-bi-reset.png)

Cependant, si le bouton **Rétablir les valeurs par défaut** est grisé, cela signifie que le *concepteur* du rapport a désactivé la possibilité d’enregistrer vos changements.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

### <a name="sorting-using-other-criteria"></a>Tri à l’aide d’autres critères
Il peut parfois être utile de trier un visuel selon un autre champ (non inclus dans le visuel) ou d’autres critères.  Par exemple, vous pouvez être amené à effectuer un tri par mois dans l’ordre séquentiel (et non par ordre alphabétique) ou bien un tri par nombres entiers plutôt qu’un tri par chiffre (0, 1, 9, 20, et non 0, 1, 20, 9).  

Seule la personne qui a conçu le rapport peut apporter ces changements pour vous. Vous pouvez trouver les informations de contact du *concepteur* en sélectionnant le nom du rapport dans la barre d’en-tête.

![Liste déroulante indiquant les informations de contact](media/end-user-change-sort/power-bi-contact.png)

Si vous êtes *concepteur* et que vous disposez d’autorisations de modification sur le contenu, lisez [Trier par colonne dans Power BI Desktop](../desktop-sort-by-column.md) pour savoir comment mettre à jour le jeu de données et autoriser ce type de tri.

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](end-user-visualizations.md).

[Power BI – Concepts de base](end-user-basic-concepts.md)
