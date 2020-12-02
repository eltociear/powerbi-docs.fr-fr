---
title: Modifier les paramètres des rapports Power BI
description: Modifier les paramètres des rapports dans le service Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: dbb173c65ecfc5d1ca464387ed43ae615cdcbca1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396173"
---
# <a name="change-settings-for-power-bi-reports"></a>Modifier les paramètres des rapports Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Avec les paramètres de rapport dans Power BI Desktop et le service Power BI, vous pouvez contrôler la façon dont les lecteurs de rapports interagissent avec votre rapport. Par exemple, vous pouvez les autoriser à enregistrer des filtres pour le rapport, à personnaliser les visuels qu’il contient ou à en afficher les pages sous la forme d’onglets dans la partie inférieure du rapport plutôt que sur le côté.

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Capture d’écran du volet Paramètres du rapport dans le service Power BI.":::

Il peut s’avérer utile de lire ces articles au préalable :

- [Créer un rapport dans le service Power BI en important un jeu de données](service-report-create-new.md), pour comprendre l’expérience de création de rapport.
- [Rapports dans Power BI](../consumer/end-user-reports.md), pour comprendre l’expérience de vos lecteurs de rapports.

 Commençons.

## <a name="prerequisites"></a>Prérequis

- Pour créer des rapports avec Power BI Desktop, consultez [Affichage du rapport Desktop](desktop-report-view.md).
- [S’inscrire au service Power BI](../fundamentals/service-self-service-signup-for-power-bi.md). 
- Vous devez disposer de l’autorisation de modification pour le rapport dans le service Power BI. Consultez [Rôles dans les nouveaux espaces de travail](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) pour plus d’informations sur cette autorisation.
- Si vous n’avez pas encore de rapport dans le service Power BI, vous pouvez [installer un exemple de pack de contenu](sample-datasets.md#install-built-in-content-packs) qui comprend un tableau de bord, un rapport et un jeu de données.

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>Ouvrir le volet Paramètres dans Power BI Desktop

1. sélectionnez **Fichier** > **Options et paramètres** > **Options**.
1. Sous **Fichier actuel**, sélectionnez **Paramètres du rapport**.

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Capture d’écran du volet Paramètres du rapport dans Power BI Desktop":::

    Le reste de cet article mentionne certains paramètres de rapport spécifiques.

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>Ouvrir le volet Paramètres dans le service Power BI

1. En mode Lecture du rapport, sélectionnez **Fichier** > **Paramètres**.

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="Capture d’écran du menu fichier et de l’option Paramètres.":::

1. Dans le volet **Paramètres**, vous voyez plusieurs bascules que vous pouvez définir, uniquement pour ce rapport. Le reste de cet article en mentionne certains.

## <a name="set-featured-content"></a>Définir le contenu proposé

Vous pouvez proposer des tableaux de bord, des rapports et des applications pour qu’ils s’affichent dans la section Proposé de la page d’accueil Power BI de vos collègues. Découvrez-en plus sur la [manière de proposer du contenu](../collaborate-share/service-featured-content.md).

## <a name="set-the-pages-pane"></a>Définir le volet Pages

Actuellement, vous pouvez uniquement modifier le paramètre du volet Pages dans le service Power BI. Quand vous activez le **volet Pages**, les lecteurs de rapports voient les onglets de page au bas du rapport en mode Lecture, plutôt que sur le côté. En mode Edition, les onglets de page se trouvent déjà au bas du rapport.

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="Capture d’écran de la définition du volet Pages.":::

## <a name="control-filters"></a>Contrôler les filtres

Le volet **Paramètres** d’un rapport comporte trois paramètres permettant de contrôler les interactions du lecteur avec les filtres inclus dans votre rapport. Pour plus d’informations sur chaque paramètre, consultez les liens suivants vers l’article [Conception de filtres dans les rapports Power BI](power-bi-report-filter.md).

- Les **filtres persistants** permettent aux lecteurs d’[enregistrer des filtres sur le rapport](power-bi-report-filter.md#allow-saving-filters).
- L’**expérience de filtrage** offre deux paramètres supplémentaires :
    
    Autoriser les lecteurs de rapports à [modifier les types de filtres](power-bi-report-filter.md#restrict-changes-to-filter-type).

    Activer la [recherche dans le volet de filtre](power-bi-report-filter.md#filters-pane-search).

## <a name="export-data"></a>Exporter des données

Par défaut, [les lecteurs de rapports peuvent exporter des données résumées ou sous-jacentes](../consumer/end-user-export.md) à partir des visuels de votre rapport. L’option **Exporter des données** leur permet d’exporter uniquement des données résumées ou de ne rien exporter du tout de votre rapport.

## <a name="personalize-visuals"></a>Personnaliser les visuels

Autorisez vos lecteurs à modifier et à personnaliser les visuels inclus dans votre rapport. Découvrez-en plus sur la [personnalisation des visuels par les lecteurs de rapports](power-bi-personalize-visuals.md).

## <a name="next-steps"></a>Étapes suivantes

* [Proposer du contenu dans les pages d’accueil d’autres personnes](../collaborate-share/service-featured-content.md)
* [Permettre aux lecteurs de rapports de personnaliser des visuels dans un rapport](power-bi-personalize-visuals.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
