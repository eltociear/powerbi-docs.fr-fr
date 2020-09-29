---
title: Utilisation de métadonnées de jeu de données avancées dans Power BI Desktop
description: Cet article explique comment utiliser des métadonnées de jeu de données avancées dans Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/22/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 67141f67be85f5c292118d4e88cfe3c5a949ce4f
ms.sourcegitcommit: ff981839e805f523748b7e71474acccf7bdcb04f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91019857"
---
# <a name="using-enhanced-dataset-metadata"></a>Utilisation de métadonnées de jeu de données avancées

Lorsque Power BI Desktop crée des rapports, il crée également des métadonnées de jeu de données dans les fichiers PBIX et PBIT correspondants. Auparavant, ces métadonnées étaient stockées dans un format spécifique à Power BI Desktop. Il utilisait des sources de données et des expressions M encodées en base 64, et des hypothèses étaient formulées sur le mode de stockage de ces métadonnées.

Avec la publication de la fonctionnalité de **métadonnées de jeu de données avancées**, un grand nombre de ces limitations sont supprimées. À l’ouverture, les fichiers PBIX sont automatiquement mis à niveau vers les métadonnées avancées. Avec les **métadonnées de jeu de données avancées**, les métadonnées créées par Power BI Desktop suivent un format similaire à celui des modèles tabulaires Analysis Services, selon le [modèle d’objet tabulaire](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La fonctionnalité de **métadonnées de jeu de données avancées** est stratégique et fondamentale, car les fonctionnalités Power BI futures seront générées à partir de ces métadonnées. Certaines capacités supplémentaires tirant parti des métadonnées de jeu de données avancées incluent [la lecture/l’écriture XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) pour la gestion des jeux de données Power BI, et la migration des charges de travail Analysis Services vers Power BI pour tirer parti des fonctionnalités de nouvelle génération.


## <a name="next-steps"></a>Étapes suivantes

Power BI Desktop permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Nouveautés dans Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Vue d’ensemble des requêtes dans Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](../transform-model/desktop-common-query-tasks.md)