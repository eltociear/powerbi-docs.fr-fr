---
title: Utilisation de métadonnées de jeu de données avancées dans Power BI Desktop (préversion)
description: Cet article explique comment utiliser des métadonnées de jeu de données avancées dans Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b1204b28ae5239bf4080472129b0862862446e5d
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878453"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Utilisation de métadonnées de jeu de données avancées (préversion)

Lorsque Power BI Desktop crée des rapports, il crée également des métadonnées de jeu de données dans les fichiers PBIX et PBIT correspondants. Auparavant, ces métadonnées étaient stockées dans un format spécifique à Power BI Desktop. Il utilisait des sources de données et des expressions M encodées en base 64, et des hypothèses étaient formulées sur le mode de stockage de ces métadonnées.

Avec la publication de la fonctionnalité de **métadonnées de jeu de données avancées**, un grand nombre de ces limitations sont supprimées. Quand la fonctionnalité de **métadonnées de jeu de données avancées** est activée, les métadonnées créées par Power BI Desktop utilisent un format similaire à celui utilisé pour les modèles tabulaires Analysis Services, en fonction du [modèle d’objet tabulaire](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La fonctionnalité de **métadonnées de jeu de données avancées** est stratégique et fondamentale, car les fonctionnalités Power BI futures seront générées à partir de ces métadonnées. Certaines capacités supplémentaires tirant parti des métadonnées de jeu de données avancées incluent [la lecture/l’écriture XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) pour la gestion des jeux de données Power BI, et la migration des charges de travail Analysis Services vers Power BI pour tirer parti des fonctionnalités de nouvelle génération.



## <a name="enable-enhanced-dataset-metadata"></a>Activer les métadonnées de jeu de données avancées

La fonctionnalité de **métadonnées de jeu de données avancées** est actuellement en préversion. Pour activer les métadonnées de jeu de données avancées, dans Power BI Desktop, sélectionnez **Fichier > Options et paramètres > Options > Fonctionnalités en préversion**, puis cochez la case **Stocker les jeux de données au format de métadonnées avancées**, comme illustré dans l’image suivante. 

![Activer la fonctionnalité de préversion](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Vous êtes invité à redémarrer Power BI Desktop.

![Invite de redémarrage](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Une fois la fonctionnalité en préversion activée, Power BI Desktop tente de mettre à niveau les fichiers PBIX et PBIT qui utilisent le format de métadonnées précédent. 

> [!IMPORTANT]
> L’activation de la caractéristique **métadonnées de jeu de données améliorées** entraîne une mise à niveau irréversible des rapports. Les rapports Power BI chargés ou créés avec Power BI Desktop, une fois les **métadonnées de jeu de données améliorées** activées, sont converties de manière irréversible au format de métadonnées de jeu de données améliorées.

## <a name="report-backup-files"></a>Fichiers de sauvegarde de rapport

La mise à jour d’un rapport pour utiliser la fonctionnalité de **métadonnées de jeu de données améliorées** est irréversible. Toutefois, pendant la mise à jour, un fichier de sauvegarde de rapport est créé pour enregistrer une version du rapport dans son format d’origine (d’avant la mise à jour). Le fichier de sauvegarde est supprimé au bout de 30 jours. 

Pour localiser le fichier de rapport de sauvegarde, procédez comme suit :

1. Accédez à l'emplacement suivant : ```C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\TempSaves\Backup```. Si vous utilisez la version Microsoft Store de Power BI Desktop, utilisez l’emplacement suivant : ```C:\Users\<user>\Microsoft\Power BI Desktop Store App\TempSaves\Backups``` 

2. Recherchez une copie du rapport à l’aide du nom et de l’horodatage du fichier d’origine.

3. Copiez le fichier à un emplacement de votre choix, afin de le conserver.

4. Assurez-vous que la fonctionnalité en préversion **Format de métadonnées amélioré** est désactivée dans Power BI Desktop si vous choisissez d’ouvrir ou d’utiliser le fichier d’origine. 

Le fichier de sauvegarde est créé lors de la mise à niveau du rapport ; ainsi, les modifications apportées après la mise à niveau ne sont pas incluses. Les nouveaux rapports créés lorsque la fonctionnalité **Format de métadonnées amélioré** est activée n’ont pas de fichier de sauvegarde.


## <a name="considerations-and-limitations"></a>Considérations et limitations

Dans la préversion, les limitations suivantes s’appliquent lorsque la fonctionnalité en préversion est activée.

### <a name="unsupported-features-and-connectors"></a>Fonctionnalités et connecteurs non pris en charge

Les limitations suivantes s’appliquent :

Après l’ouverture d’un fichier PBIX ou PBIT existant qui n’a pas été mis à niveau, la mise à niveau échoue si le jeu de données contient l’une des fonctionnalités ou l’un des connecteurs suivants. Si cet échec se produit, il ne doit pas y avoir d’impact immédiat sur l’expérience utilisateur et Power BI Desktop continue d’utiliser le format de métadonnées précédent.

* Tous les connecteurs personnalisés (limitation de la version de mai 2020)
* Scripts Python
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

Si vous utilisez la version de **juin 2020** de Power BI Desktop (ou une version ultérieure), tous les connecteurs personnalisés et tous les connecteurs intégrés *sont* pris en charge pour Power BI Desktop et le service Power BI. Pendant le processus de publication avec la version de juin 2020 ou une version ultérieure, si la passerelle rencontre des problèmes, le jeu de données est publié avec succès, mais les utilisateurs doivent republier le rapport afin d’actualiser les données. La boîte de dialogue **Paramètres de la source de données** est le seul indicateur pour lequel des problèmes se sont produits lors du processus de publication.

Les rapports qui utilisent des connecteurs ou des fonctionnalités non pris en charge ne seront pas mis à niveau vers le nouveau format. Les rapports qui ont déjà été mis à niveau ou qui ont été créés après l’activation de cette nouvelle fonctionnalité ne prennent pas en charge l’ajout des fonctionnalités ou connecteurs non pris en charge répertoriés. 

Les requêtes avec des sources de données dynamiques ne sont pas prises en charge. Les rapports qui ont des sources de données dynamiques ne sont pas mis à niveau vers le nouveau format, et les rapports qui ont déjà été mis à niveau ou qui ont été créés avec la fonctionnalité activée ne prennent pas en charge l’ajout de sources de données dynamiques. Une requête possède une source de données dynamique si la source change en fonction d’un paramètre, d’une entrée de fonction ou d’une fonction volatile. 

Les requêtes avec des erreurs dans les étapes en amont ou les branches ne sont pas prises en charge. 

En outre, les fichiers PBIX et PBIT qui ont déjà été mis à niveau pour utiliser les **métadonnées de jeu de données avancées** *ne peuvent pas* utiliser les fonctionnalités (ni les éventuels connecteurs non pris en charge).

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
