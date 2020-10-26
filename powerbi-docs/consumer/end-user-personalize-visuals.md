---
title: Personnaliser les visuels dans un rapport
description: Créez votre propre vue d’un rapport, sans modifier ce dernier.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/13/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 718363da3bd1f66de199db8d854d8d23d6de3eb5
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256742"
---
# <a name="personalize-visuals-in-a-report"></a>Personnaliser les visuels dans un rapport

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

Il est difficile de créer un visuel qui réponde aux exigences de tout le monde. Toutefois, lorsqu’un collègue partage un rapport avec vous, vous souhaiterez peut-être apporter des modifications aux visuels sans avoir à demander à votre collègue d’effectuer les modifications pour vous. 

Par exemple, vous pourriez vouloir permuter les données de l’axe, changer le type de visuel ou ajouter un élément à l’info-bulle. Avec la fonctionnalité **Personnaliser ce visuel**, effectuez les modifications vous-même. Une fois le visuel conforme à vos attentes, enregistrez-le comme [favori](end-user-bookmarks.md) pour pouvoir y revenir. Vous n’avez même pas besoin de l’autorisation Modifier pour le rapport.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="Personnalisation d’un visuel":::
 
## <a name="what-you-can-change"></a>Ce que vous pouvez modifier

Cette fonctionnalité vous aide à obtenir davantage d’insights grâce à l’exploration ad hoc des visuels d’un rapport Power BI. Voici quelques-unes des modifications que vous pouvez apporter. Les options disponibles varient selon le type de visuel. 

- Changer de type de visualisation
- Permuter une mesure ou une dimension
- Ajouter ou supprimer une légende
- Comparer deux ou plusieurs mesures
- Modifier les agrégations

Cette fonctionnalité offre non seulement de nouvelles fonctionnalités d’exploration, mais également des moyens de capturer et de partager vos modifications :

- Capturer vos modifications
- Partager vos modifications
- Réinitialiser toutes vos modifications pour un rapport
- Réinitialiser toutes vos modifications pour un visuel
- Effacer vos modifications récentes

> [!IMPORTANT]
> La possibilité de personnaliser un visuel doit être activée par le Concepteur de *rapports*. Si vous ne voyez pas l’icône **Personnaliser ce visuel** ![icône Personnaliser ce visuel](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png), cela signifie qu’il n’a pas activé cette fonctionnalité pour le rapport actuel. Contactez le propriétaire du rapport ou votre administrateur Power BI pour activer la fonctionnalité. Pour afficher les informations de contact du propriétaire du rapport, sélectionnez le nom du rapport dans la barre de menus Power BI.

## <a name="personalize-visuals-in-the-power-bi-service"></a>Personnalisation des visuels dans le service Power BI

En personnalisant un visuel, vous pouvez explorer vos données de multiples façons, sans quitter le [mode Lecture de rapport](end-user-reading-view.md). Les exemples suivants illustrent différentes manières dont vous pouvez modifier une visualisation en fonction de vos besoins. 

1. Ouvrez un rapport en mode lecture dans le service Power BI.

2. Dans la barre de menus du visuel, sélectionnez l’icône **Personnaliser ce visuel** ![icône Personnaliser ce visuel](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Changer de type de visualisation

Vous trouvez que les données s’afficheraient mieux sous la forme d’un histogramme empilé ? Modifiez le **type de visualisation**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Personnalisation d’un visuel":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Permuter une mesure ou une dimension
Remplacez le champ utilisé pour l’axe X en sélectionnant le champ que vous souhaitez remplacer, puis en sélectionnant un autre champ.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Personnalisation d’un visuel":::
 
### <a name="add-or-remove-a-legend"></a>Ajouter ou supprimer une légende
En ajoutant une légende, vous pouvez attribuer un code de couleurs à un visuel selon la catégorie. Dans cet exemple, nous utilisons un code de couleurs basé sur le nom de la société. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Personnalisation d’un visuel":::

### <a name="change-the-placement-of-fields"></a>Modifier le positionnement des champs

À l’aide de la fonction glisser-déposer, vous pouvez modifier le positionnement des champs dans la même propriété visuelle ou même entre différentes propriétés visuelles. Par exemple, vous pouvez rapidement déplacer un champ de la légende vers l’axe d’un visuel.

:::image type="content" source="media/end-user-personalize-visuals/personalize-drag-and-drop.png" alt-text="Personnalisation d’un visuel":::

Vous pouvez également réorganiser rapidement les colonnes d’une table ou d’une matrice.

:::image type="content" source="media/end-user-personalize-visuals/personalize-reorder-columns.png" alt-text="Personnalisation d’un visuel":::

### <a name="compare-two-or-more-different-measures"></a>Comparer deux ou plusieurs mesures différentes
Comparez et confrontez des valeurs pour différentes mesures à l’aide de l’icône +, qui permet d’ajouter plusieurs mesures pour un visuel. Pour supprimer une mesure, sélectionnez **Plus d’options (...)** et choisissez **Supprimer le champ**.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Personnalisation d’un visuel":::

### <a name="change-aggregations"></a>Modifier les agrégations
Changez le mode de calcul d’une mesure en modifiant l’agrégation dans le volet **Personnaliser**. Sélectionnez **Plus d’options (...)** et choisissez l’agrégation à utiliser.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Personnalisation d’un visuel":::

### <a name="capture-changes"></a>Capturer les modifications 
À l’aide des signets personnels, capturez vos modifications pour pouvoir revenir à votre affichage personnalisé. Sélectionnez **Signets** > **Signets personnels** et attribuez un nom au signet. 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Personnalisation d’un visuel":::
 
Vous pouvez également faire du signet votre affichage par défaut.

### <a name="share-changes"></a>Partager les modifications 
Si vous avez des autorisations de lecture et de repartage, vous pouvez choisir d’inclure vos modifications lorsque vous partagez le rapport.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Personnalisation d’un visuel":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Réinitialiser toutes les modifications dans un rapport

Dans le coin supérieur droit de votre canevas de rapport, sélectionnez **Rétablir les valeurs par défaut**. Cela supprime toutes les modifications que vous avez apportées au rapport et revient au dernier affichage du rapport enregistré par l’auteur.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Personnalisation d’un visuel":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Réinitialiser toutes les modifications dans un visuel

À partir de la barre de menus pour le visuel, sélectionnez **Réinitialiser ce visuel** pour supprimer toutes les modifications que vous avez apportées à un visuel en particulier et revenir au dernier affichage du visuel enregistré par l’auteur.

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Personnalisation d’un visuel":::
 
### <a name="clear-recent-changes"></a>Effacer les modifications récentes

Sélectionnez l’icône représentant une gomme pour effacer toutes les modifications récentes que vous avez effectuées depuis que vous avez ouvert le volet **Personnaliser**.  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Personnalisation d’un visuel":::

## <a name="limitations"></a>Limites

La fonctionnalité présente actuellement quelques limitations à connaître.

- **Personnaliser ce visuel** peut être désactivé pour un rapport entier ou pour un visuel particulier. Si vous n’avez pas la possibilité de personnaliser un visuel, contactez l’administrateur Power BI ou le propriétaire du rapport. Pour afficher les informations de contact du propriétaire du rapport, sélectionnez le nom du rapport dans la barre de menus Power BI.
- Les explorations des utilisateurs ne sont pas automatiquement conservées. Vous devez enregistrer votre affichage dans les signets personnels pour capturer vos modifications.
- Cette fonctionnalité est prise en charge dans les applications mobiles Power BI pour les tablettes iOS et Android, ainsi que dans l’application Windows Power BI. Elle n’est pas prise en charge dans les applications mobiles Power BI pour les téléphones. Toutefois, les modifications de visuels enregistrées dans un signet personnel au sein du service Power BI sont respectées dans les applications mobiles Power BI.

## <a name="next-steps"></a>Étapes suivantes
[Copier un visuel de rapport sous forme d’image statique](../visuals/power-bi-visualization-copy-paste.md)    
D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
