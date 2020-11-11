---
title: Bien démarrer avec la mise en forme des visualisations Power BI
description: Personnaliser le titre, l’arrière-plan et la légende d’une visualisation
author: msftrien
ms.reviewer: mihart
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/06/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 0d19d7366dce571e2d89ba5cbc6ffbe936ec50e2
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93410989"
---
# <a name="customize-visualization-titles-backgrounds-and-legends"></a>Personnaliser les titres, les arrière-plans et les légendes des visualisations

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    


Ce tutoriel présente quelques façons de personnaliser vos visualisations. Il existe autant d’options permettant de personnaliser vos visualisations. La meilleure façon de les découvrir toutes consiste à Explorer le volet **Mise en forme** (sélectionnez l’icône rouleau de peinture). Pour vous aider à commencer, cet article explique comment personnaliser le titre, la légende et l’arrière-plan d’une visualisation, et comment ajouter un thème.

Vous ne pouvez pas personnaliser toutes les visualisations. Consultez le [la liste complète](#visualization-types-that-you-can-customize) des visualisations pour plus d’informations.


## <a name="prerequisites"></a>Prérequis

- Service Power BI ou Power BI Desktop

- Exemple de rapport Analyse de la vente au détail

> [!NOTE]
> Pour que vous puissiez partager votre rapport avec un collègue Power BI, il faut que vous disposiez tous deux de licences individuelles Power BI Pro ou que le rapport soit enregistré dans une capacité Premium. Consultez [partage des rapports](../collaborate-share/service-share-reports.md).

## <a name="customize-visualization-titles-in-reports"></a>Personnaliser les titres des visualisations dans les rapports

Pour poursuivre, connectez-vous à Power BI Desktop, puis ouvrez le rapport [Exemple Analyse de la vente au détail](../create-reports/sample-datasets.md).

> [!NOTE]
> Quand vous épinglez une visualisation à un tableau de bord, elle prend la forme d’une vignette de tableau de bord. Vous pouvez également personnaliser les vignettes proprement dites [en modifiant leurs titres et sous-titres, en leur ajoutant des liens hypertexte et en les redimensionnant](../create-reports/service-dashboard-edit-tile.md).

1. Accédez à la page **New Stores** du rapport **Exemple Analyse de la vente**.

1. Sélectionnez l’histogramme groupé **Open Store Count by Open Month and Chain**.

1. Dans le volet **Visualisations** , sélectionnez l’icône représentant un rouleau pour afficher les options de mise en forme.

1. Sélectionnez **Titre** pour développer cette section.

   ![Capture d’écran du volet Mise en forme avec l’icône en forme de rouleau et une flèche vers la liste déroulante des titres.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Déplacez le curseur **Titre** sur **Activé**.

1. Pour modifier le titre, tapez *Store count by month opened **(Nombre d’ouvertures de magasins pas mois) dans le champ** Texte du titre*.

    ![Capture d’écran du volet Format avec le texte du titre entré.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Définissez le blanc comme **Couleur de police** et le bleu comme **Couleur d’arrière-plan**.    

    a. Sélectionnez la flèche déroulante et choisissez une couleur dans **Couleurs du thème** , **Couleurs récentes** ou **Couleur personnalisée**.
    
    ![Capture d’écran des options Couleur de police et Couleur d’arrière-plan.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. Sélectionnez la flèche déroulante pour fermer la fenêtre des couleurs.


1. Augmentez la taille du texte à **16 pt**.

1. Vous allez effectuer une dernière personnalisation : aligner le titre du graphique au centre de la visualisation.

    ![Capture d’écran des contrôles d’alignement avec l’option Centrer sélectionnée.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    À ce stade du tutoriel, le titre de votre histogramme groupé doit ressembler à ceci :

    ![Capture d’écran de l’histogramme groupé nouvellement configuré.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Enregistrez les modifications que vous avez apportées, puis passez à la section suivante.

Si vous devez annuler toutes les modifications, sélectionnez **Rétablir les valeurs par défaut** en bas du volet de personnalisation **Titre**.

![Capture d’écran de l’option Rétablir les valeurs par défaut.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Personnaliser les arrière-plans des visualisations

En reprenant le même histogramme groupé, développez les options **Arrière-plan**.

1. Déplacez le curseur **Arrière-plan** sur **Activé**.

1. Sélectionnez la liste déroulante et choisissez une couleur grise.

1. Changez la **Transparence** à **74 %** .

À ce stade du tutoriel, l’arrière-plan de votre histogramme groupé doit ressembler à ceci :

![Capture d’écran de l’histogramme groupé avec la couleur d’arrière-plan mise à jour.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Enregistrez les modifications que vous avez apportées, puis passez à la section suivante.

Si vous devez annuler toutes les modifications, sélectionnez **Rétablir les valeurs par défaut** en bas du volet de personnalisation **Arrière-plan**.

## <a name="customize-visualization-legends"></a>Personnaliser les légendes des visualisations

1. Ouvrez la page de rapport **Présentation** et sélectionnez le graphique **Total Sales Variance par FiscalMonth et directeur régional** (Variance du nombre de ventes totales par MoisFiscal et directeur régional).

1. Dans l’onglet **Visualisation** , sélectionnez l’icône en forme de rouleau pour ouvrir le volet Mise en forme.

1. Développez les options de **Légende**  :

    ![Capture d’écran de la carte Légende.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Déplacez le curseur **Légende** sur **Activé**.

1. Déplacez la légende à gauche de la visualisation.

1. Ajoutez un titre de légende en basculant le **Titre** sur **Activé**.

1. Entrez *Gestionnaire* dans le champ **Nom de la légende**.

1. Définissez le noir comme **Couleur**.

Enregistrez les modifications que vous avez apportées, puis passez à la section suivante.

Si vous devez annuler toutes les modifications, sélectionnez **Rétablir les valeurs par défaut** en bas du volet de personnalisation **Légende**.

## <a name="customize-colors-using-a-theme"></a>Personnaliser les couleurs à l’aide d’un thème

Avec les thèmes de rapport, vous pouvez appliquer des changements de conception à l’ensemble de votre rapport, par exemple en utilisant les couleurs de votre entreprise, en changeant des jeux d’icônes ou en appliquant une nouvelle mise en forme visuelle par défaut. Quand vous appliquez un thème de rapport, tous les visuels du rapport utilisent les couleurs et la mise en forme du thème sélectionné.

Pour appliquer un thème à votre rapport, sélectionnez **Changer de thème** dans la barre de menus. Choisissez un thème.  Le rapport ci-dessous utilise le thème **Solaire**.

 
![Rapport utilisant le thème Solaire des jaunes, des oranges et des rouges](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Types de visualisations que vous pouvez personnaliser

Voici une liste des visualisations et des options de personnalisation respectivement disponibles :

| Visualisation | Titre | Arrière-plan | Légende |
|:--- |:--- |:--- |:--- |
| Zone | oui | oui |oui |
| Barres | oui | oui |oui |
| Carte | oui | oui |n/a |
| Carte à plusieurs lignes | oui | oui | n/a |
| Colonne | oui | oui | oui |
| Combiné | oui | oui | oui |
| Graphique en anneau | oui | oui | oui |
| Carte choroplèthe | oui | oui | oui |
| Entonnoir | oui | oui | n/a |
| Jauge | oui | oui | n/a |
| Influenceur clé | oui | oui | n/a |
| KPI | oui | oui | n/a |
| Ligne | oui | oui | oui |
| Carte | oui | oui | oui |
| Matrice | oui | oui | n/a |
| Secteurs | oui | oui | oui |
| Questions et réponses | oui | oui | n/a |
| Nuage de points | oui | oui | oui |
| Forme | oui | oui | oui |
| Segment | oui | oui | n/a |
| Table | oui | oui | n/a |
| Zone de texte | non | oui | n/a |
| Treemap | oui | oui | oui |
| Cascade | oui | oui | oui |

## <a name="next-steps"></a>Étapes suivantes

- [Personnaliser les propriétés des axes X et Y](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Prise en main de la mise en forme des couleurs et des propriétés d’axe](service-getting-started-with-color-formatting-and-axis-properties.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)


