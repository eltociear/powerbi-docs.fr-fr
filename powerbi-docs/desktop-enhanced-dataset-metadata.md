---
title: Utilisation de métadonnées de jeu de données avancées dans Power BI Desktop (préversion)
description: Cet article explique comment utiliser des métadonnées de jeu de données avancées dans Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3812f16489d304912ec9574352897e1effb29d4a
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201398"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Utilisation de métadonnées de jeu de données avancées (préversion)

Lorsque Power BI Desktop crée des rapports, il crée également des métadonnées de jeu de données dans les fichiers PBIX et PBIT correspondants. Auparavant, ces métadonnées étaient stockées dans un format spécifique à Power BI Desktop. Il utilisait des sources de données et des expressions M encodées en base 64, et des hypothèses étaient formulées sur le mode de stockage de ces métadonnées.

Avec la publication de la fonctionnalité de **métadonnées de jeu de données avancées**, un grand nombre de ces limitations sont supprimées. Quand la fonctionnalité de **métadonnées de jeu de données avancées** est activée, les métadonnées créées par Power BI Desktop utilisent un format similaire à celui utilisé pour les modèles tabulaires Analysis Services, en fonction du [modèle d’objet tabulaire](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La fonctionnalité de **métadonnées de jeu de données avancées** est stratégique et fondamentale, car les fonctionnalités Power BI futures seront générées à partir de ces métadonnées. Certaines capacités supplémentaires tirant parti des métadonnées de jeu de données avancées incluent [la lecture/l’écriture XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) pour la gestion des jeux de données Power BI, et la migration des charges de travail Analysis Services vers Power BI pour tirer parti des fonctionnalités de nouvelle génération.

## <a name="enable-enhanced-dataset-metadata"></a>Activer les métadonnées de jeu de données avancées

La fonctionnalité de **métadonnées de jeu de données avancées** est actuellement en préversion. Pour activer les métadonnées de jeu de données avancées, dans Power BI Desktop, sélectionnez **Fichier > Options et paramètres > Options > Fonctionnalités en préversion**, puis cochez la case **Stocker les jeux de données au format de métadonnées avancées**, comme illustré dans l’image suivante. 

![Activer la fonctionnalité de préversion](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Vous êtes invité à redémarrer Power BI Desktop.

![Invite de redémarrage](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Une fois la fonctionnalité en préversion activée, Power BI Desktop tente de mettre à niveau les fichiers PBIX et PBIT qui utilisent le format de métadonnées précédent. 

## <a name="considerations-and-limitations"></a>Considérations et limitations

Dans la préversion, les limitations suivantes s’appliquent lorsque la fonctionnalité en préversion est activée.

Après l’ouverture d’un fichier PBIX ou PBIT existant qui n’a pas été mis à niveau, la mise à niveau échoue si le jeu de données contient l’une des fonctionnalités ou l’un des connecteurs suivants. Si cet échec se produit, il ne doit pas y avoir d’impact immédiat sur l’expérience utilisateur et Power BI Desktop continue d’utiliser le format de métadonnées précédent.

* Scripts Python
* Connecteurs personnalisés
* Azure DevOps Server
* Connecteur BI
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* MarkLogic ODBC
* Qubole Presto
* Team Desk
* Expressions M contenant certaines combinaisons de caractères telles que «\\n » dans les noms de colonnes
* Lors de l’utilisation de jeux de données avec la fonctionnalité de **métadonnées de jeu de données avancées**, les sources de données d’authentification unique (SSO) ne peuvent pas être configurées dans le service Power BI

En outre, les fichiers PBIX et PBIT qui ont déjà été mis à niveau pour utiliser les **métadonnées de jeu de données avancées** *ne peuvent pas* utiliser les fonctionnalités ni les connecteurs ci-dessus dans la version actuelle.


## <a name="next-steps"></a>Étapes suivantes

Power BI Desktop permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](desktop-what-is-desktop.md)
* [Nouveautés dans Power BI Desktop](desktop-latest-update.md)
* [Vue d’ensemble des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)

