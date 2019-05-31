---
title: Introduction aux tableaux de bord pour les concepteurs Power BI
description: Les tableaux de bord sont une fonctionnalité clé du service Power BI. Un tableau de bord est une page unique, souvent appelée canevas, qui raconte une histoire au moyen de visualisations.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 61d7bf9f9794545e963ca19c8f983d6d6cfefa54
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61150387"
---
# <a name="intro-to-dashboards-for-power-bi-designers"></a>Introduction aux tableaux de bord pour les concepteurs Power BI

Un ***tableau de bord*** Power BI est une page unique, souvent appelée canevas, qui raconte une histoire au moyen de visualisations. Comme il est limité à une seule page, un tableau de bord bien conçu contient uniquement les éléments clés de cette histoire. Les lecteurs peuvent afficher des rapports connexes pour obtenir plus de détails.

![tableau de bord](media/service-dashboards/power-bi-dashboard2.png)

Les tableaux de bord sont une fonctionnalité du service Power BI. Ils ne sont pas disponibles dans Power BI Desktop. Vous ne pouvez pas créer de tableaux de bord sur des appareils mobiles, mais vous pouvez [les afficher et les partager](mobile-apps-view-dashboard.md) sur ceux-ci.

## <a name="dashboard-basics"></a>Principes de base des tableaux de bord 

Les visualisations que vous voyez sur le tableau de bord sont appelées des *vignettes*. Vous *épinglez* les vignettes provenant de rapports à un tableau de bord. Si vous êtes novice dans Power BI, vous pouvez acquérir de bonnes bases en lisant [Power BI – Concepts de base](service-basic-concepts.md).

> [!IMPORTANT]
> Vous devez être titulaire d’une licence [Power BI Pro](service-free-vs-pro.md) pour créer des tableaux de bord.

Les visualisations sur un tableau de bord proviennent de rapports, et chaque rapport est basé sur un jeu de données. Un tableau de bord est en quelque sorte une porte d’accès aux rapports et aux jeux de données sous-jacents. La sélection d’une visualisation vous amène au rapport et au jeu de données sur lesquels elle est basée.

![diagramme montrant la relation entre les tableaux de bord, les rapports, les jeux de données](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Avantages des tableaux de bord
Les tableaux de bord constituent un moyen formidable de superviser votre activité et de voir vos métriques les plus importantes en un coup d’œil. Les visualisations sur un tableau de bord peuvent provenir d’un ou plusieurs jeux de données sous-jacents et d’un ou plusieurs rapports sous-jacents. Un tableau de bord combine des données locales et cloud, offrant ainsi une vue centralisée, quel que soit l’endroit où les données résident.

Un tableau de bord n’est pas qu’une jolie image. Il est extrêmement interactif, les vignettes se mettent à jour dès que changent les données sous-jacentes.

## <a name="dashboards-versus-reports"></a>Tableaux de bord et rapports
Les [rapports](service-reports.md) et les tableaux de bord semblent similaires, car ils sont tous les deux des canevas composés de visualisations. Mais il existe des différences majeures.

| **Fonctionnalité** | **Tableaux de bord** | **Rapports** |
| --- | --- | --- |
| Pages |Une seule page |Une ou plusieurs pages |
| Sources de données |Un ou plusieurs rapports et un ou plusieurs jeux de données par tableau de bord |Un seul jeu de données par rapport |
| Disponible dans Power BI Desktop |Non | Possibilité de créer et d’afficher des rapports dans Power BI Desktop |
| S’abonner |Possibilité de s’abonner à un tableau de bord |Possibilité de s’abonner à des pages de rapport |
| Filtrage |Impossible de filtrer ou découper |Différentes manières de filtrer, mettre en surbrillance et découper |
| Sélection |Possibilité de définir un tableau de bord comme votre tableau de bord « par défaut » |Impossible de créer un rapport proposé |
| Favori | Possibilité de définir des tableaux de bord comme *Favoris* | Possibilité de définir des rapports comme *Favoris*
| Définir des alertes |Disponible pour les vignettes de tableau de bord dans certaines circonstances |Non disponible à partir de rapports |
| Requêtes en langage naturel (Questions et réponses) |Disponible dans les tableaux de bord | Disponible dans les rapports |
| Possibilité d’afficher les tables et les champs sous-jacents d’un jeu de données |Non. Possibilité d’exporter les données, mais pas de voir les tables et les champs dans le tableau de bord. |Oui. Possibilité de voir les tables d’un jeu de données ainsi que les champs et les valeurs. |


## <a name="next-steps"></a>Étapes suivantes
* Familiarisez-vous avec les tableaux de bord en effectuant une visite guidée d’un de nos [exemples de tableau de bord](sample-tutorial-connect-to-the-samples.md).
* Découvrez-en plus sur les [vignettes de tableau de bord](service-dashboard-tiles.md).
* Si vous souhaitez effectuer le suivi d’une vignette du tableau de bord et recevoir un e-mail lorsqu’elle atteint un certain seuil ? [Créer des alertes sur les vignettes](service-set-data-alerts.md).
* Découvrez comment utiliser [Power BI Q&A](power-bi-tutorial-q-and-a.md) pour poser une question concernant vos données et obtenir la réponse sous la forme d’une visualisation.
