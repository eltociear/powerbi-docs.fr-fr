---
title: Introduction aux tableaux de bord pour les concepteurs Power BI
description: Les tableaux de bord sont une fonctionnalité clé du service Power BI. Un tableau de bord est une page unique, souvent appelée canevas, qui raconte une histoire au moyen de visualisations.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: eb2c513e8ee8ad1c8ad93866f688e40f6c5af56d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160785"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Introduction aux tableaux de bord pour les concepteurs Power BI

Un *tableau de bord* Power BI est une page unique, souvent appelée canevas, qui raconte une histoire au moyen de visualisations. Comme il est limité à une seule page, un tableau de bord bien conçu contient uniquement les éléments clés de cette histoire. Les lecteurs peuvent afficher des rapports connexes pour obtenir plus de détails.

![Dashboard](media/service-dashboards/power-bi-dashboard2.png)

Les tableaux de bord sont une fonctionnalité du service Power BI. Ils ne sont pas disponibles dans Power BI Desktop. Vous ne pouvez pas créer de tableaux de bord sur des appareils mobiles, mais vous pouvez [les afficher et les partager](mobile-apps-view-dashboard.md) sur ceux-ci.

## <a name="dashboard-basics"></a>Principes de base des tableaux de bord 

Les visualisations que vous voyez sur le tableau de bord sont appelées des *vignettes*. Vous *épinglez* les vignettes provenant de rapports à un tableau de bord. Si vous débutez dans Power BI, vous pouvez acquérir de bonnes bases en lisant [Concepts de base pour les concepteurs dans le service Power BI](service-basic-concepts.md).

Les visualisations sur un tableau de bord proviennent de rapports, et chaque rapport est basé sur un jeu de données. Un tableau de bord est en quelque sorte une porte d’accès aux rapports et aux jeux de données sous-jacents. La sélection d’une visualisation vous amène au rapport et au jeu de données sur lesquels elle est basée.

![Diagramme montrant la relation entre les tableaux de bord, les rapports, les jeux de données](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Avantages des tableaux de bord
Les tableaux de bord constituent un moyen formidable de superviser votre activité et de voir vos métriques les plus importantes en un coup d’œil. Les visualisations sur un tableau de bord peuvent provenir d’un ou plusieurs jeux de données sous-jacents et d’un ou plusieurs rapports sous-jacents. Un tableau de bord combine des données locales et cloud, offrant ainsi une vue centralisée, quel que soit l’endroit où les données résident.

Un tableau de bord n’est pas qu’une jolie image. Il est extrêmement interactif, les vignettes se mettent à jour dès que changent les données sous-jacentes.

## <a name="who-can-create-a-dashboard"></a>Qui peut créer un tableau de bord ?
La capacité de créer un tableau de bord est une fonctionnalité de *créateur* qui nécessite des autorisations de modification du rapport. Ces autorisations sont réservées aux créateurs de rapports et aux collègues à qui les premiers ont accordé l’accès. Par exemple, si David crée un rapport dans l’espace de travail ABC et vous ajoute comme membre de cet espace de travail, David et vous aurez tous deux des autorisations de modification. Si, à l’inverse, le rapport a été partagé avec vous directement ou dans le cadre d’une [application Power BI](service-create-distribute-apps.md), vous êtes *consommateur* du rapport. Vous ne pourrez pas épingler de vignettes à un tableau de bord. 

> [!IMPORTANT]
> Vous devez être titulaire d’une licence [Power BI Pro](service-free-vs-pro.md) pour créer des tableaux de bord dans des espaces de travail. Vous pouvez créer des tableaux de bord dans votre propre espace de travail sans licence Power BI Pro.


## <a name="dashboards-versus-reports"></a>Tableaux de bord et rapports
Les [rapports](service-reports.md) et les tableaux de bord semblent similaires, car ils sont tous les deux des canevas composés de visualisations. Mais il existe des différences majeures, comme vous pouvez le voir dans le tableau suivant.

| **Fonctionnalité** | **Tableaux de bord** | **Rapports** |
| --- | --- | --- |
| Pages |Une seule page |Une ou plusieurs pages |
| Sources de données |Un ou plusieurs rapports et un ou plusieurs jeux de données par tableau de bord |Un seul jeu de données par rapport |
| Disponible dans Power BI Desktop |Non | Oui. Possibilité de créer et d’afficher des rapports dans Power BI Desktop |
| S’abonner |Oui. Possibilité de s’abonner à un tableau de bord |Oui. Possibilité de s’abonner à une page de rapport |
| Filtrage |No. Impossible de filtrer ou découper |Oui. Différentes manières de filtrer, mettre en surbrillance et découper |
| Sélection |Oui. Possibilité de définir un tableau de bord comme tableau de bord *par défaut* |Non |
| Favori | Oui. Possibilité de définir plusieurs tableaux de bord comme *Favoris* | Oui. Possibilité de définir plusieurs rapports comme *Favoris*
| Définir des alertes |Oui. Disponible pour les vignettes de tableau de bord dans certaines circonstances |Non |
| Requêtes en langage naturel (Questions et réponses) |Oui | Oui, pour autant que vous disposiez d’autorisations de modification sur me rapport et son jeu de données sous-jacent |
| Possibilité d’afficher les tables et les champs sous-jacents d’un jeu de données |No. Possibilité d’exporter les données, mais pas de voir les tables et les champs dans le tableau de bord |Oui |


## <a name="next-steps"></a>Étapes suivantes
* Familiarisez-vous avec les tableaux de bord en effectuant une visite guidée d’un de nos [exemples de tableau de bord](sample-tutorial-connect-to-the-samples.md).
* Découvrez-en plus sur les [vignettes de tableau de bord](service-dashboard-tiles.md).
* Si vous souhaitez effectuer le suivi d’une vignette du tableau de bord et recevoir un e-mail lorsqu’elle atteint un certain seuil ? [Créer une alerte sur une vignette](service-set-data-alerts.md).
* Découvrez comment utiliser [Power BI Q&A](power-bi-tutorial-q-and-a.md) pour poser une question concernant vos données et obtenir la réponse sous la forme d’une visualisation.
