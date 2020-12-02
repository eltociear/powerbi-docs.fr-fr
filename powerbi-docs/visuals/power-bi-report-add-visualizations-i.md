---
title: Partie 1, Ajouter des visualisations à un rapport Power BI
description: Partie 1, Ajouter des visualisations à un rapport Power BI
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 4d4b04b10e45d67fdd4d7cb183e300587d4f2cc6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412480"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Ajouter des visuels à un rapport Power BI (partie 1)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Cet article explique brièvement comment créer une visualisation dans un rapport. Il s’applique à la fois au service Power BI et à Power BI Desktop. Pour un contenu plus avancé, [consultez la partie 2](power-bi-report-add-visualizations-ii.md) de cette série.

## <a name="prerequisites"></a>Prérequis

Ce tutoriel s’appuie sur le [fichier PBIX Vente et marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).

1. Dans la section supérieure gauche de la barre de menus Power BI Desktop, sélectionnez **Fichier** > **Ouvrir**
   
2. Recherchez votre copie du **fichier PBIX de l’exemple Vente et marketing**

1. Ouvrez le **fichier PBIX de l’exemple Vente et marketing** dans la vue Rapport ![Capture d’écran de l’icône de la vue Rapport.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.

> [!NOTE]
> Pour que vous puissiez partager votre rapport avec un collègue Power BI, il faut que vous disposiez tous deux de licences individuelles Power BI Pro ou que le rapport soit enregistré dans une capacité Premium. Voir [partage des rapports](../collaborate-share/service-share-reports.md)

## <a name="add-visualizations-to-the-report"></a>Ajouter des visualisations au rapport

1. Créez une visualisation en sélectionnant un champ dans le volet **Champs**.

    Commencez par un champ numérique comme **Sales** > **TotalSales** (Ventes > TotalVentes). Power BI crée un histogramme avec une seule colonne.

    ![Capture d’écran d’un histogramme avec une seule colonne.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    Ou commencez par un champ de catégorie, tel que **Nom** ou **Produit**. Power BI crée une table et ajoute ce champ à la zone **Valeurs**.

    ![Capture d’écran d’une table avec quatre catégories](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    Ou, commencez par un champ géographique, tel que **Geo** > **Ville**. Power BI et Bing Cartes créent une visualisation de carte.

    ![Capture d’écran d’une visualisation de carte.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Changer le type de visualisation

 Créez une visualisation, puis modifiez son type. 
 
 1. Sélectionnez **Produit** > **Catégorie**, puis **Produit** > **Quantité de produit** pour ajouter ces éléments à la zone **Valeurs**.

    ![Capture d’écran du volet Champs avec la zone Valeurs.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Changez la visualisation en histogramme en sélectionnant l’icône d’**histogramme empilé**.

   ![Capture d’écran du volet Visualisation avec l’icône de l’histogramme empilé.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Pour changer le mode de tri du visuel, sélectionnez **Autres actions** (...).  Utilisez les options de tri pour changer le sens du tri (croissant ou décroissant) et la colonne sur laquelle s’effectue le tri (**Trier par**).

   ![Capture d’écran de la liste déroulante Autres actions.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Étapes suivantes

 Passez à :

* [Partie 2 : Ajouter des visualisations à un rapport Power BI](power-bi-report-add-visualizations-ii.md)

* [interagir avec les visualisations](../consumer/end-user-reading-view.md) dans le rapport ;
