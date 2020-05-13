---
title: Utilisation de métadonnées de jeu de données avancées dans Power BI Desktop (préversion)
description: Cet article explique comment utiliser des métadonnées de jeu de données avancées dans Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 87b4be55b1b811f63dbb7fe271bc3c3fa4af2755
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347421"
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

> [!IMPORTANT]
> L’activation de la caractéristique **métadonnées de jeu de données améliorées** entraîne une mise à niveau irréversible des rapports. Les rapports Power BI chargés ou créés avec Power BI Desktop, une fois les **métadonnées de jeu de données améliorées** activées, sont converties de manière irréversible au format de métadonnées de jeu de données améliorées.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Dans la préversion, les limitations suivantes s’appliquent lorsque la fonctionnalité en préversion est activée.

### <a name="unsupported-features-and-connectors"></a>Fonctionnalités et connecteurs non pris en charge
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

### <a name="lineage-view"></a>Vue de traçabilité
Les jeux de données qui utilisent le nouveau format de métadonnées n’affichent actuellement pas de liens vers les flux de données dans la vue de la traçabilité du service Power BI.

## <a name="next-steps"></a>Étapes suivantes

Power BI Desktop permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Nouveautés dans Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Vue d’ensemble des requêtes dans Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
