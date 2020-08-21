---
title: Permettre aux utilisateurs de personnaliser les visuels dans un rapport
description: Laissez les lecteurs de rapports créer leur propre affichage d’un rapport, sans le modifier.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/12/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 8dd6e64943ea05f2219efa471cd3fcfa4152650b
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160484"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permettre aux utilisateurs de personnaliser les visuels dans un rapport

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Lorsque vous partagez un rapport avec un large public, il se peut que certains de vos utilisateurs veuillent voir des affichages légèrement différents des visuels : par exemple, permuter les données de l’axe, changer le type de visuel ou ajouter un élément à l’info-bulle. Il est difficile de créer un visuel qui réponde aux exigences de tout le monde. Avec cette nouvelle fonctionnalité, vous pouvez donner à vos consommateurs la possibilité d’explorer et de personnaliser des visuels, le tout en mode lecture de rapport. Ils peuvent ajuster le visuel à leur guise et l’enregistrer dans leurs signets pour y revenir par la suite. Ils n’ont besoin ni de disposer d’une autorisation de modification sur le rapport, ni de demander une modification à l’auteur du rapport.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personnalisation d’un visuel":::
 
## <a name="what-report-consumers-can-change"></a>Éléments modifiables par les consommateurs de rapports

Cette fonctionnalité permet aux consommateurs d’obtenir davantage d’insights grâce à l’exploration ad hoc des visuels d’un rapport Power BI. Pour découvrir comment utiliser cette fonctionnalité en tant que consommateur, consultez [Personnaliser les visuels dans vos rapports](../consumer/end-user-personalize-visuals.md). Elle est idéale pour les créateurs de rapports qui veulent proposer des scénarios d’exploration de base aux lecteurs de leurs rapports. Voici quelques-unes des modifications que ces derniers peuvent effectuer :

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

## <a name="use-perspectives-for-a-more-focused-view"></a>Utiliser les Perspectives pour une vue plus ciblée

Pour personnaliser les visuels, vous pouvez utiliser des **perspectives** pour choisir un sous-ensemble d’un modèle qui fournit une vue plus ciblée. Le choix d’un sous-ensemble peut être utile lors de l’utilisation d’un modèle de données volumineux, ce qui vous permet de vous concentrer sur un sous-ensemble gérable de champs et de ne pas saturer les lecteurs de rapports avec la collection complète des champs de ce modèle volumineux. 

![Personnaliser les visuels](media/power-bi-personalize-visuals/power-bi-personalize-perspective-01.png)

Tenez compte des points suivants lorsque vous travaillez avec les perspectives :

* Les perspectives ne sont pas censées servir de mécanisme de sécurité ; elles constituent plutôt un outil qui optimise l'expérience de l'utilisateur final. Toute la sécurité d'une perspective est héritée du modèle sous-jacent.

* Les perspectives sont prises en charge à la fois dans les modèles tabulaires et multidimensionnels. Toutefois, pour les perspectives dans les modèles multidimensionnels, vous pouvez uniquement définir la perspective pour qu’elle soit identique au cube de base pour le rapport.

* Avant de supprimer une perspective d’un modèle, vérifiez que la perspective n’est pas utilisée dans l’expérience Personnaliser les visuels. 

Pour utiliser les perspectives, vous devez activer Personnaliser les visuels pour le rapport. Vous devez également créer au moins une perspective qui comprend les dimensions et les mesures auxquelles les utilisateurs finaux peuvent interagir pour l’expérience Personnaliser les visuels.

Pour créer la perspective, utilisez l’[éditeur tabulaire](https://tabulareditor.com/), que vous pouvez télécharger à partir de l’emplacement suivant : Téléchargement de l’éditeur tabulaire

Une fois que vous avez installé l’**éditeur tabulaire**, ouvrez votre rapport dans **Power BI Desktop** et lancez l’**éditeur tabulaire** à partir de l’onglet **Outils externes** du ruban, comme illustré dans l’image suivante.

![Éditeur tabulaire dans le ruban Outils externes](media/power-bi-personalize-visuals/power-bi-personalize-perspective-02.png)

Dans l’éditeur tabulaire, cliquez avec le bouton droit sur le dossier **Perspectives** pour créer une perspective.

![Créer un nouveau dossier Perspectives dans l’éditeur tabulaire](media/power-bi-personalize-visuals/power-bi-personalize-perspective-03.png)

Vous pouvez double-cliquer sur le texte pour renommer la perspective.

![Renommer la perspective](media/power-bi-personalize-visuals/power-bi-personalize-perspective-04.png)

Ensuite, ajoutez des champs à la perspective en ouvrant le dossier **Tables** dans l’éditeur tabulaire ; cliquez alors avec le bouton droit sur les champs que vous souhaitez afficher dans la perspective.

![Ajouter des champs à une perspective](media/power-bi-personalize-visuals/power-bi-personalize-perspective-05.png)

Répétez ce processus pour chaque champ que vous souhaitez ajouter à la perspective. Vous ne pouvez pas ajouter de champs dupliqués dans une perspective, donc tous les champs que vous avez déjà ajoutés à une perspective auront l’option d’ajout désactivée.

Une fois que vous avez ajouté tous les champs souhaités, veillez à enregistrer vos paramètres, à la fois dans l’éditeur tabulaire et dans Power BI Desktop.

![Enregistrer les paramètres des perspectives dans l’éditeur tabulaire et Power BI Desktop](media/power-bi-personalize-visuals/power-bi-personalize-perspective-06.png)

Une fois que vous avez enregistré la nouvelle perspective dans le modèle et enregistré le rapport Power BI Desktop, accédez au volet **Mise en forme** de la page, où vous voyez une nouvelle section pour **Personnaliser le visuel**.

![Section Personnaliser le visuel dans le volet Mise en forme](media/power-bi-personalize-visuals/power-bi-personalize-perspective-07.png)

La sélection pour *Perspective du lecteur du rapport* est définie sur *Champs par défaut* initialement. Une fois que vous avez sélectionné la flèche déroulante, vous voyez les autres perspectives que vous avez créées.

![Sélectionnez la flèche déroulante pour afficher les autres perspectives](media/power-bi-personalize-visuals/power-bi-personalize-perspective-08.png)

Une fois que vous avez défini la perspective pour la page de rapport, l’expérience Personnaliser les visuels de cette page est filtrée sur la perspective sélectionnée. Si vous sélectionnez **Appliquer à toutes les pages**, vous pouvez appliquer votre paramètre de perspective à toutes les pages existantes de votre rapport.

![Sélectionnez Appliquer à toutes les pages pour que la perspective s’applique à l’ensemble du rapport](media/power-bi-personalize-visuals/power-bi-personalize-perspective-09.png)


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


## <a name="limitations-and-known-issues"></a>Limitations et problèmes connus

La fonctionnalité présente actuellement quelques limitations à connaître.

- Cette fonctionnalité n’est pas prise en charge dans les scénarios d’incorporation, notamment la publication sur le web.
- Les explorations des utilisateurs ne sont pas automatiquement conservées. Vous devez enregistrer votre affichage dans les signets personnels pour capturer vos modifications.
- Cette fonctionnalité est prise en charge dans les applications mobiles Power BI pour les tablettes iOS et Android, ainsi que dans l’application Windows Power BI. Elle n’est pas prise en charge dans les applications mobiles Power BI pour les téléphones. Toutefois, les modifications de visuels enregistrées dans un signet personnel au sein du service Power BI sont respectées dans les applications mobiles Power BI.

Il existe également quelques problèmes connus que nous sommes en train de traiter :

- L’ajout d’une hiérarchie n’est pas pris en charge ; il est nécessaire d’ajouter les différents éléments enfants.
- Il n’est pas possible de remplacer une hiérarchie de dates par une date ou inversement. 
- Avec les signets personnels, les résultats obtenus risquent d’être légèrement différents selon la séquence sélectionnée. Ces incohérences sont possibles dans la mesure où nous ne capturons pas l’état complet du rapport, mais seulement les modifications apportées. La solution de contournement consiste à sélectionner **Réinitialiser**, puis à sélectionner le signet que vous souhaitez afficher. 

## <a name="next-steps"></a>Étapes suivantes

[Personnaliser les visuels dans vos rapport](../consumer/end-user-personalize-visuals.md).     

Essayez la nouvelle expérience de personnalisation de visuels. Faites-nous part de vos commentaires pour cette fonctionnalité et de la façon dont nous pouvons continuer à améliorer cette expérience, sur le [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

D’autres questions ? [Essayez la communauté Power BI](https://community.powerbi.com/)
