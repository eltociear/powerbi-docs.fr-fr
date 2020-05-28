---
title: Descendre et monter dans la hiérarchie d’un visuel
description: Cet article montre comment descendre dans la hiérarchie d’un visuel dans le service Microsoft Power BI.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 9b1cd7e7bfd808edc89dc4490e252a89ac5acb3e
ms.sourcegitcommit: 2cb249fc855e369eed1518924fbf026d5ee07eb1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2020
ms.locfileid: "83813735"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Mode d’exploration d’un visuel dans Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Cet article montre comment descendre dans la hiérarchie d’un visuel dans le service Microsoft Power BI. En descendant et en montant dans la hiérarchie de vos points de données, vous pouvez explorer en profondeur les détails de vos données. 

## <a name="drill-requires-a-hierarchy"></a>L’exploration nécessite une hiérarchie

Quand un visuel a une hiérarchie, vous pouvez l’explorer pour révéler des détails supplémentaires. Par exemple, imaginez que vous avez un visuel qui montre le nombre de médailles olympiques selon une hiérarchie de sports, de disciplines et d’événements. Par défaut, le visuel indique le nombre de médailles olympiques par sport : gymnastique, ski, sports aquatiques, etc. Toutefois, comme il a une structure hiérarchique, si vous sélectionnez l’un de ses éléments (par exemple, une barre, une ligne ou une bulle), des insights encore plus détaillés s’affichent. Si vous sélectionnez l’élément **aquatics** (sports aquatiques), vous voyez les données pour la natation, la plongée et le water-polo.  Si vous sélectionnez ensuite l’élément **diving** (plongée), vous voyez les détails relatifs aux événements de plongeon tremplin, haut vol et synchronisé.

Les dates sont un type unique de hiérarchie.  Les concepteurs de rapports ajoutent souvent des hiérarchies de dates aux visuels. Une hiérarchie de dates courante est une hiérarchie qui contient l’année, le trimestre, le mois et le jour. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Identifier les visuels explorables
Vous ne savez pas quels visuels Power BI contiennent une hiérarchie ? Pointez sur un visuel. Si vous voyez une combinaison de ces contrôles d’exploration en haut, c’est que votre visuel a une hiérarchie.

![Capture d’écran des icônes d’exploration.](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>Découvrir comment descendre et monter dans la hiérarchie

Dans cet exemple, nous utilisons une arborescence qui a une hiérarchie composée du territoire, de la ville, du code postal et du nom du magasin. L’arborescence, avant l’exploration, affiche le nombre total d’unités vendues cette année par territoire. 

![Capture d’écran de l’arborescence et des filtres appliqués.](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Deux façons d’accéder aux fonctionnalités d’exploration

Vous avez deux façons d’accéder aux fonctionnalités d’exploration et de développement pour les visuels qui ont des hiérarchies. Essayez-les toutes les deux et utilisez celle que vous préférez.

- Première façon : pointez sur un visuel pour voir et utiliser les icônes.  

    ![Capture d’écran de l’exemple de pointage.](./media/end-user-drill/power-bi-hover.png)

- Deuxième façon : cliquez avec le bouton droit sur un visuel pour afficher et utiliser le menu.

    ![Capture d’écran de l’exemple de clic avec le bouton droit.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>Parcours d’exploration

### <a name="drill-down-all-fields-at-once"></a>Descendre dans la hiérarchie de tous les champs en même temps
![Icône Descendre dans la hiérarchie](./media/end-user-drill/power-bi-drill-icon3.png)

Vous pouvez descendre dans la hiérarchie de votre visuel de plusieurs manières. Si vous sélectionnez l’icône Descendre dans la hiérarchie, vous accédez au niveau en dessous dans la hiérarchie. Si vous examinez le niveau **Territory** (Territoire) pour le Kentucky et le Tennessee, vous pouvez descendre au niveau de la ville pour les deux États, puis au niveau du code postal pour les deux États et, enfin, au niveau du nom de magasin pour les deux États. Chaque étape de ce parcours vous montre de nouvelles informations.

![Diagramme montrant le parcours d’exploration](./media/end-user-drill/power-bi-drill-path.png)

Sélectionnez l’icône Monter dans la hiérarchie ![Icône Monter dans la hiérarchie](./media/end-user-drill/power-bi-drill-icon5.png) jusqu’à revenir au niveau « Total units this year by territory » (Unités totales pour cette année par territoire).

### <a name="expand-all-fields-at-once"></a>Développer tous les champs en même temps
![Icône Développer](./media/end-user-drill/power-bi-drill-icon6.png)

**Développer** ajoute un niveau de hiérarchie supplémentaire à la vue actuelle. Par conséquent, si vous regardez le niveau **Territory**, vous pouvez développer et ajouter les détails concernant la ville, le code postal et le nom à votre treemap. Chaque étape du parcours vous montre les mêmes informations et ajoute un niveau de nouvelles informations.

![Diagramme montrant le parcours de développement](./media/end-user-drill/power-bi-expand-path.png)

Vous pouvez également choisir de descendre dans la hiérarchie ou de développer un champ à la fois.


### <a name="drill-down-one-field-at-a-time"></a>Descendre dans la hiérarchie pour un champ à la fois


1. Sélectionnez l’icône Descendre dans la hiérarchie pour l’activer ![Capture d’écran de l’icône Descendre dans la hiérarchie activée/désactivée.](./media/end-user-drill/power-bi-drill-icon2.png).

    Vous avez maintenant la possibilité de descendre dans la hiérarchie d’**un champ à la fois** en sélectionnant un élément du visuel. Les éléments d’un visuel peuvent être une barre, une bulle ou une feuille, par exemple.

    ![Capture d’écran d’un visuel avec une flèche pointant vers l’icône activée Descendre dans la hiérarchie.](media/end-user-drill/power-bi-drill-icon-selected.png)

    Si vous n’activez pas Descendre dans la hiérarchie, la sélection d’un élément du visuel (par exemple, une barre, une bulle ou une feuille) n’entraîne pas l’affichage du niveau en dessous dans la hiérarchie. Au lieu de cela, il y aura un filtrage croisé des autres sur la page de rapport.

1. Sélectionnez le nœud terminal pour **TN**. Votre arborescence montre maintenant toutes les villes et territoires du Tennessee où il y a un magasin.

    ![Capture d’écran de la treemap montrant les données pour TN uniquement.](media/end-user-drill/power-bi-drill-down-one.png)

1. À ce stade, vous pouvez effectuer les opérations suivantes :

    1. Continuer Descendre dans la hiérarchie pour le Tennessee.

    1. Descendre dans la hiérarchie pour une ville spécifique du Tennessee.

    1. Développer à la place.

    Continuons à descendre dans la hiérarchie pour un champ à la fois.  Sélectionnez **Knoxville, TN**. Votre treemap montre maintenant le code postal de votre magasin de Knoxville.

    ![Capture d’écran de la treemap montrant le code postal 37919.](media/end-user-drill/power-bi-drill-two.png)

    Notez que le titre change à mesure que vous explorez puis revenez en arrière.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Développer tout et développer un champ à la fois

Une treemap qui nous montre uniquement un code postal n’apporte pas beaucoup d’informations.  Nous allons donc *développer* un niveau de la hiérarchie.  

1. Avec la treemap active, sélectionnez l’icône *Développer vers le bas*![Capture d’écran de l’icône Développer vers le bas](./media/end-user-drill/power-bi-drill-icon6.png). Votre treemap montre maintenant les deux niveaux de notre hiérarchie : le code postal et le nom du magasin.

    ![Capture d’écran de la treemap montrant le code postal et le nom du magasin](./media/end-user-drill/power-bi-expand-one.png)

1. Pour voir l’ensemble des quatre niveaux de hiérarchie des données pour Tennessee, sélectionnez la flèche Monter dans la hiérarchie jusqu’à atteindre le deuxième niveau, **Total units this year by territory and city**, de votre treemap.

    ![Capture d’écran de la treemap montrant toutes les données pour TN.](media/end-user-drill/power-bi-expand-two.png)

1. Vérifiez que l’icône Descendre dans la hiérarchie est toujours activée, ![Capture de l’icône Descendre dans la hiérarchie activée/désactivée.](./media/end-user-drill/power-bi-drill-icon2.png) et sélectionnez l’icône *Développer vers le bas*![Capture d’écran de l’icône Développer vers le bas](./media/end-user-drill/power-bi-drill-icon6.png). Votre arborescence montre maintenant le même nombre de feuilles (cases), mais chaque feuille affiche des détails supplémentaires. Au lieu de montrer seulement la ville et l’état, elle montre maintenant également le code postal.

    ![Capture d’écran de l’élément visuel montrant la ville, l’état et le code postal.](./media/end-user-drill/power-bi-expand-three.png)

1. Sélectionnez une fois de plus l’icône *Développer vers le bas* pour afficher les quatre niveaux de la hiérarchie des détails pour le Tennessee sur votre treemap. Pointez sur une feuille pour voir davantage de détails.

    ![Capture d’écran de la treemap montrant une info-bulle avec des données spécifiques au nœud terminal.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>Afficher les données pendant l’exploration
Utilisez **Afficher les données** pour savoir ce qui se passe en arrière-plan. Pour chaque exploration ou développement que vous effectuez, l’option **Afficher les données** montre les données utilisées pour générer le visuel. Cela peut vous aider à comprendre comment les hiérarchies, l’exploration et le développement fonctionnent ensemble pour créer des visuels. 

En haut à droite, sélectionnez **Plus d’options** (...), puis sélectionnez **Afficher les données**. 

![Capture d’écran du menu ...](./media/end-user-drill/power-bi-ellipses.png)

Le tableau suivant présente les résultats de l’exploration de tous les champs à la fois, du territoire au nom de magasin.  


![Capture d’écran montrant les données pour les quatre niveaux d’exploration.](./media/end-user-drill/power-bi-show-data.png)

Notez que les totaux sont les mêmes pour les champs **City** (Ville), **PostalCode** (Code postal) et **Name** (Nom). Ce n’est pas toujours le cas,  mais dans cet exemple de données, il n’y a qu’un seul magasin pour chaque code postal et dans chaque ville.  



## <a name="considerations-and-limitations"></a>Considérations et limitations
- Par défaut, l’exploration ne filtre pas les autres visuels d’un rapport. Le concepteur de rapports peut toutefois changer ce comportement par défaut. Au fur et à mesure de l’exploration, regardez s’il y a des interactions de filtrage croisé ou de sélection croisée sur les autres visuels de la page.

- Pour consulter un rapport partagé avec vous, vous devez avoir une licence Power BI Pro ou Premium. [Quelle est ma licence ?](end-user-license.md)


## <a name="next-steps"></a>Étapes suivantes

[Visuels dans les rapports Power BI](../visuals/power-bi-report-visualizations.md)

[Rapports Power BI](end-user-reports.md)

[Power BI – Concepts de base](end-user-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
