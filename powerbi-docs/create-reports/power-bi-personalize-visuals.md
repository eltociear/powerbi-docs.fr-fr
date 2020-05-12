---
title: Permettre aux utilisateurs de personnaliser les visuels dans un rapport
description: Laissez les lecteurs de rapports créer leur propre affichage d’un rapport, sans le modifier.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867113"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permettre aux utilisateurs de personnaliser les visuels dans un rapport

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Lorsque vous partagez un rapport avec un large public, il se peut que certains de vos utilisateurs veuillent voir des affichages légèrement différents des visuels : par exemple, permuter les données de l’axe, changer le type de visuel ou ajouter un élément à l’info-bulle. Il est difficile de créer un visuel qui réponde aux exigences de tout le monde. Avec cette nouvelle fonctionnalité, vous pouvez donner à vos consommateurs la possibilité d’explorer et de personnaliser des visuels, le tout en mode lecture de rapport. Ils peuvent ajuster le visuel à leur guise et l’enregistrer dans leurs signets pour y revenir par la suite. Ils n’ont besoin ni de disposer d’une autorisation de modification sur le rapport, ni de demander une modification à l’auteur du rapport.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personnalisation d’un visuel":::
 
## <a name="what-report-consumers-can-change"></a>Éléments modifiables par les consommateurs de rapports

Cette fonctionnalité permet aux consommateurs d’obtenir davantage d’insights grâce à l’exploration ad hoc des visuels d’un rapport Power BI. Elle est idéale pour les créateurs de rapports qui souhaitent proposer des scénarios d’exploration de base à leurs lecteurs de rapports. Voici quelques-unes des modifications que ces derniers peuvent effectuer :

- Changer de type de visualisation
- Permuter une mesure ou une dimension
- Ajouter ou supprimer une légende
- Comparer deux ou plusieurs mesures
- Modifier les agrégations

Cette fonctionnalité offre non seulement de nouvelles fonctionnalités d’exploration, mais aussi le moyen pour les consommateurs de capturer et de partager leurs modifications :

- Capturer leurs modifications
- Partager leurs modifications
- Réinitialiser toutes leurs modifications dans un rapport
- Réinitialiser toutes leurs modifications dans un visuel
- Effacer leurs modifications récentes

## <a name="turn-on-the-preview-feature"></a>Activation de la fonctionnalité d’évaluation

Comme cette fonctionnalité est en préversion, vous devez d’abord activer son commutateur. Sélectionnez **Fichier** > **Options et paramètres** > **Options**. Sous **Paramètres globaux** > **Fonctionnalités d’évaluation**, sélectionnez **Personnaliser les visuels**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Activation de Personnaliser les visuels":::

Vous devrez peut-être redémarrer Power BI Desktop pour le voir dans les paramètres du fichier actuel.

## <a name="enable-personalization-in-a-report"></a>Activation de la personnalisation dans un rapport

Après avoir activé le commutateur de préversion, vous devez l’autoriser spécifiquement pour les rapports dans lesquels vous souhaitez que les consommateurs puissent personnaliser les visuels.

Vous pouvez activer la fonctionnalité dans Power BI Desktop ou dans le service Power BI.

### <a name="in-power-bi-desktop"></a>Dans Power BI Desktop

Pour activer la fonctionnalité dans Power BI Desktop, accédez à **Fichier** > **Options et paramètres** > **Options** > **Fichier actuel** > **Paramètres du rapport**. Activez **Personnaliser les visuels (préversion)** .

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Activation de la personnalisation dans un rapport":::

### <a name="in-the-power-bi-service"></a>Dans le service Power BI

Si vous souhaitez plutôt activer la fonctionnalité dans le service Power BI, accédez aux **Paramètres** de votre rapport.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Paramètres du rapport dans le service Power BI":::

Activez **Personnaliser les visuels (préversion)**  > **Enregistrer**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Activation de Personnaliser les visuels dans le service":::

## <a name="select-visuals-that-can-be-personalized"></a>Sélection des visuels personnalisables

Lorsque vous activez ce paramètre pour un rapport donné, tous les visuels de ce rapport sont par défaut personnalisables. Si vous ne souhaitez pas que tous les visuels soient personnalisés, vous pouvez activer ou désactiver le paramètre visuel par visuel.

Sélectionnez le visuel > sélectionnez **Format** dans le volet **Visualisations** > développez **En-tête de visuel**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Sélection de En-tête de visuel":::
 
Faites glisser **Personnaliser le visuel** >  **Activé** ou **Désactivé**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Curseur Personnaliser le visuel activé ou désactivé":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Personnalisation des visuels dans le service Power BI

En personnalisant un visuel, vos consommateurs peuvent explorer vos données de multiples façons, sans quitter le mode lecture de rapport. Les exemples suivants illustrent différentes manières dont les utilisateurs peuvent modifier une visualisation en fonction de leurs besoins. 

1. Ouvrez un rapport en mode lecture dans le service Power BI.

2. Dans l’angle supérieur droit du visuel, sélectionnez l’icône **Personnaliser ce visuel** ![icône Personnaliser ce visuel](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Changer de type de visualisation

Vous pouvez afficher la visualisation dans une autre représentation en modifiant le **Type de visualisation**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Modifier le type de visualisation":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Permuter une mesure ou une dimension
Vous pouvez remplacer une mesure ou une dimension sur l’axe X en sélectionnant le champ concerné, puis une autre mesure ou dimension.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Modification de l’axe":::
 
### <a name="add-or-remove-a-legend"></a>Ajouter ou supprimer une légende
En ajoutant une légende, vous pouvez attribuer un code de couleurs à un visuel selon la catégorie. Pour éliminer le code de couleurs catégoriel, effacez la case **Légende** du volet **Personnaliser**. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Ajout ou suppression d’une légende":::

### <a name="compare-two-or-more-different-measures"></a>Comparer deux ou plusieurs mesures différentes
Vous pouvez comparer et confronter des valeurs pour différentes mesures à l’aide de l’icône +, qui permet d’ajouter plusieurs mesures pour un visuel.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Comparaison de mesures":::

### <a name="change-aggregations"></a>Modifier les agrégations
Vous pouvez changer le mode de calcul d’une mesure en modifiant l’agrégation dans le volet **Personnaliser**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Modification des agrégations":::

### <a name="capture-changes"></a>Capturer les modifications 
À l’aide des signets personnels, capturez vos modifications pour pouvoir revenir à votre affichage personnalisé. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Création d’un signet":::
 
Vous pouvez également faire du signet votre affichage par défaut.

### <a name="share-changes"></a>Partager les modifications 
Si vous avez des autorisations de lecture et de repartage, vous pouvez choisir d’inclure vos modifications lorsque vous partagez le rapport.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Partage des modifications":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Réinitialiser toutes les modifications dans un rapport

Sélectionnez **Réinitialiser** pour supprimer toutes les modifications que vous avez apportées au rapport et revenir au dernier affichage du rapport enregistré par l’auteur.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Réinitialisation de toutes les modifications":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Réinitialiser toutes les modifications dans un visuel

Sélectionnez **Réinitialiser ce visuel** pour supprimer toutes les modifications que vous avez apportées à un visuel en particulier et revenir au dernier affichage du visuel enregistré par l’auteur.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Réinitialisation de toutes les modifications du visuel":::
 
### <a name="clear-recent-changes"></a>Effacer les modifications récentes

Sélectionnez l’icône représentant une gomme pour effacer toutes les modifications récentes que vous avez effectuées depuis que vous avez ouvert le volet **Personnaliser**.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Restauration des modifications récentes":::

## <a name="limitations-and-known-issues"></a>Limitations et problèmes connus

La fonctionnalité présente actuellement quelques limitations à connaître.

- Cette fonctionnalité n’est pas prise en charge dans les scénarios d’incorporation, notamment la publication sur le web.
- Les explorations des utilisateurs ne sont pas automatiquement conservées. Vous devez enregistrer votre affichage dans les signets personnels pour capturer vos modifications.
- Il n’est pas possible de modifier les visuels dans les applications mobiles Power BI. Toutefois, les modifications de visuels enregistrées dans un signet personnel au sein du service Power BI sont respectées dans les applications mobiles.

Il existe également quelques problèmes connus que nous sommes en train de traiter :

- L’ajout d’une hiérarchie n’est pas pris en charge ; il est nécessaire d’ajouter les différents éléments enfants.
- Il n’est pas possible de remplacer une hiérarchie de dates par une date ou inversement. 
- Avec les signets personnels, les résultats obtenus risquent d’être légèrement différents selon la séquence sélectionnée. Ces incohérences sont possibles dans la mesure où nous ne capturons pas l’état complet du rapport, mais seulement les modifications apportées. La solution de contournement consiste à sélectionner **Réinitialiser**, puis à sélectionner le signet que vous souhaitez afficher. 

## <a name="next-steps"></a>Étapes suivantes

Essayez la nouvelle expérience de personnalisation de visuels. Faites-nous part de vos commentaires pour cette fonctionnalité et de la façon dont nous pouvons continuer à améliorer cette expérience, sur le [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

