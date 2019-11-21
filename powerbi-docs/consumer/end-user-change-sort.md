---
title: Changer le mode tri d’un graphique dans un rapport
description: Modifier le mode tri d’un graphique dans un rapport Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852387"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Modifier le mode tri d’un graphique dans un rapport Power BI

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Dans le service Power BI, vous pouvez changer l’apparence d’un visuel en le triant par différents champs de données. En changeant la façon dont vous triez un visuel, vous pouvez mettre en évidence les informations que vous voulez transmettre et vérifier que le visuel reflète cette tendance (ou cette importance).

Que vous utilisiez des données numériques (par exemple des chiffres de ventes) ou des données texte (comme des noms d’État), vous pouvez trier vos visualisations comme vous le souhaitez et leur donner l’aspect souhaité. Power BI offre une grande souplesse sur le plan du tri et des menus rapides que vous pouvez utiliser. Sur n’importe quel visuel, sélectionnez **Autres actions** (...), puis sélectionnez le champ en fonction duquel vous souhaitez effectuer le tri.

![graphique à barres trié par l’axe des X](media/end-user-change-sort/power-bi-more-actions.png)

Les visuels sur un tableau de bord ne peuvent pas être triés, mais dans un rapport Power BI, vous pouvez trier la plupart des visualisations par ordre alphabétique en fonction des noms de catégories du graphique ou des valeurs numériques de chaque catégorie. Par exemple, ce graphique est trié par ordre alphabétique en fonction de la catégorie **nom de magasin**.

![graphique à barres trié par l’axe des X](media/end-user-change-sort/pbi-chartsortcategory.png)

Il est facile de passer du tri par catégorie (nom de magasin) au tri par valeur (ventes par mètres carrés).

1. Sélectionnez **Autres actions** (...) et choisissez **Trier par > Sales Per Sq Ft** (Ventes par m²).
2. Si nécessaire, resélectionnez **Autres actions** (...) et choisissez **Tri décroissant**. Le champ utilisé pour le tri est en gras et a une barre jaune.

   ![vidéo montrant la sélection de Trier par, puis Croissant et Décroissant](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Certains visuels ne peuvent pas être triés. C’est le cas, par exemple, des visuels suivants : treemap, carte géographique, carte choroplèthe, nuage de points, jauge, carte, cascade.

## <a name="saving-changes-you-make-to-sort-order"></a>Enregistrement de vos modifications de l’ordre de tri
Les rapports Power BI conservent les filtres, les sélecteurs, le tri et les autres changements que vous apportez aux vues de données. Ainsi, si vous quittez un rapport et que vous y revenez plus tard, vos modifications sont enregistrées.  Si vous voulez annuler vos changements et revenir aux paramètres du concepteur du rapport, sélectionnez **Rétablir les valeurs par défaut** dans la barre de menus plus haut. 

![Tri persistant](media/end-user-change-sort/power-bi-reset.png)

Cependant, si le bouton **Rétablir les valeurs par défaut** est grisé, cela signifie que le concepteur du rapport a désactivé la possibilité d’enregistrer vos changements.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Tri à l’aide d’autres critères
Il peut parfois être utile de trier un visuel selon un autre champ (non inclus dans le visuel) ou d’autres critères.  Par exemple, vous pouvez être amené à effectuer un tri par mois (et non par ordre alphabétique) ou bien un tri par nombres entiers plutôt qu’un tri par chiffre (0, 1, 9, 20 et non 0, 1, 20, 9).  Le concepteur de rapports peut mettre à jour le jeu de données pour activer ce type de tri. Vous pouvez trouver les informations de contact du concepteur en sélectionnant le nom du rapport dans la barre d’en-tête.

![Liste déroulante indiquant les informations de contact](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur les [visualisations dans les rapports Power BI](end-user-visualizations.md).

[Power BI – Concepts de base](end-user-basic-concepts.md)
