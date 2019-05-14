---
title: Performances de la passerelle monitoring (préversion publique)
description: Cet article fournit des informations sur l’analyse des performances des activités de passerelle de données sur site.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535364"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Performances de la passerelle monitoring (préversion publique)

Pour surveiller les performances, les administrateurs de passerelle traditionnellement dépendant manuellement surveillance des compteurs de performances via l’outil Analyseur de performances Windows. Nous offrons désormais la journalisation des requêtes supplémentaires et un [fichier de modèle de passerelle performances PBI](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) pour visualiser les résultats. Cette fonctionnalité fournit des informations concernant l’utilisation de la passerelle et vous permet de résoudre les problèmes des requêtes lentes.

> [!NOTE]
> Cette fonctionnalité est actuellement disponible uniquement pour la passerelle de données sur site en mode standard et non pour le mode personnel.

## <a name="enable-performance-logging"></a>Activer la journalisation des performances

Pour activer cette fonctionnalité, apportez les modifications suivantes à la *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* de fichiers dans le « \Program Files\On-passerelle de données locale « dossier :

1. Mise à jour **QueryExecutionReportOn** à _True_ pour activer la journalisation supplémentaire pour les requêtes exécutées à l’aide de la passerelle. L’activation de cette option crée le rapport d’exécution de requête et les fichiers de rapport de requête d’exécution d’agrégation.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Mise à jour **SystemCounterReportOn** à _True_ pour activer la journalisation supplémentaire pour la mémoire et d’UC du système. L’activation de cette option crée le fichier de rapport d’agrégation des compteurs système.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. D’autres valeurs sont dans le fichier de configuration que vous pouvez mettre à jour en fonction des besoins.

    - **ReportFilePath**: Détermine le chemin d’accès où les trois fichiers journaux sont stockés. Par défaut, ce chemin d’accès est « \Users\PBIEgwService\AppData\Local\Microsoft\On-premises données gateway\Report » ou « site Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On données gateway\Report », selon la version du système d’exploitation. Si vous utilisez un compte de service pour la passerelle autre que _PBIEgwService_, remplacez cette partie du chemin d’accès avec le nom de compte de service.
    - **ReportFileCount**: Détermine le nombre de fichiers journaux de chaque type à conserver. La valeur par défaut est 10.
    - **ReportFileSizeInBytes**: Détermine la taille du fichier à mettre à jour. La valeur par défaut est 104857600 octets autorisée.
    - **QuerExecutionAggregationTimeInMinutes**: Détermine le nombre de minutes pour lequel les informations d’exécution de requête sont agrégées. La valeur par défaut est 5.
    - **SystemCounterAggregationTimeInMinutes**: Détermine le nombre de minutes pour lequel les compteurs système sont agrégées. La valeur par défaut est 5.

1. Une fois que vous avez apporté les modifications au fichier de configuration, redémarrez la passerelle pour ces valeurs de configuration entrent en vigueur. Vous allez maintenant commencer à voir les fichiers de rapport générés à l’emplacement que vous avez spécifié pour **ReportFilePath**.

    > [!NOTE]
    > Il peut prendre jusqu'à 10 minutes, ainsi que la quantité de temps définie pour **QuerExecutionAggregationTimeInMinutes** dans le fichier de configuration jusqu'à ce que les fichiers s’affiche dans le dossier.

## <a name="understand-performance-logs"></a>Comprendre les journaux de performances

Lorsque vous activez cette fonctionnalité, nous créons trois nouveaux fichiers journaux :

- Le rapport d’exécution de requête
- Le rapport de d’agrégation de l’exécution de requête
- Le rapport d’agrégation du compteur système

Le rapport d’exécution de requête contient des informations sur l’exécution de requête détaillées. Nous capturons les attributs suivants :

|Attribut |Description |
| ---- | ---- |
|**GatewayObjectId** |Identificateur unique pour la passerelle. |
|**RequestId** |Identificateur unique pour une demande de passerelle. Il peut être le même pour plusieurs requêtes. |
|**DataSource** |Contient le type de source de données et la source de données. |
|**QueryTrackingId** |Identificateur unique pour une requête. |  
|**QueryExecutionEndTimeUTC** |Heure de fin de l’exécution des requêtes. |
|**QueryExecutionDuration**(ms) |Durée d’exécution d’une requête. |
|**QueryType** |Type de requête - par exemple, la requête passée peut être un actualisation de Power BI/DirectQuery ou des requêtes à partir de PowerApps et Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Heure auxquelles les activités telles que la mise en attente, extraction de données, la compression, traitement des données et ainsi de suite terminé le traitement des données. |
|**DataProcessingDuration**(ms) |Durée de traitement des données des activités telles que la mise en attente, extraction de données, la compression, traitement des données et ainsi de suite. |
|**Réussite** |Indique si la requête a réussi ou échoué. |
|**ErrorMessage** |Si la requête a échoué, indique le message d’erreur. |
| | |

Le rapport d’agrégation de l’exécution de requête contient des informations de requête regroupées dans un intervalle de temps par **GatewayObjectId**, **DataSource**, **réussite**et **QueryType**. La valeur par défaut est de 5 minutes, mais vous pouvez l’ajuster comme décrit ci-dessous. Nous capturons les attributs suivants :

|Attribut |Description |
| ---- | ---- |
|**GatewayObjectId** |Identificateur unique pour la passerelle. |
|**AggregationStartTimeUTC** |Début de la fenêtre de temps pour lequel les attributs de la requête ont été agrégées. |
|**AggregationEndTimeUTC** |Fin de la fenêtre de temps pour la requête des attributs ont été agrégées. |
|**DataSource** |Contient le type de source de données et la source de données. |
|**Réussite** |Indique si la requête a réussi ou échoué. |
|**AverageQueryExecutionDuration**(ms) |Durée d’exécution de requête moyenne pour la fenêtre de temps d’agrégation. |
|**MaxQueryExecutionDuration**(ms) |Durée d’exécution de requête maximale pour la fenêtre de temps d’agrégation. |
|**MinQueryExecutionDuration**(ms) |Durée d’exécution de requête minimale pour la fenêtre de temps d’agrégation. |
|**QueryType** |Type de requête - par exemple, la requête passée peut être un actualisation de Power BI/DirectQuery ou des requêtes à partir de PowerApps et Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Temps moyen pour les activités de traitement des données telles que la mise en attente, extraction de données, la compression, traitement des données, et ainsi de suite de la fenêtre de temps d’agrégation. |
|**MaxDataProcessingDuration**(ms) |Durée maximale de la fenêtre de temps d’agrégation pour les activités de traitement des données telles que la mise en attente, extraction de données, la compression, traitement des données et ainsi de suite. |
|**MinDataProcessingDuration**(ms) |Temps minimal pour la fenêtre de temps d’agrégation pour les activités de traitement des données telles que la mise en attente, extraction de données, la compression, traitement des données et ainsi de suite. |
|**Count** |Nombre de requêtes. |
| | |

Le rapport d’agrégation de compteur système contient des valeurs de compteur système regroupés dans un intervalle de temps. La valeur par défaut est de 5 minutes, mais vous pouvez l’ajuster comme décrit ci-dessous. Nous capturons les attributs suivants :

|Attribut |Description |
| ---- | ---- |
|**GatewayObjectId** |Identificateur unique pour la passerelle. |
|**AggregationStartTimeUTC** |Début de la fenêtre de temps pour lequel les compteurs du système ont été agrégés. |
|**AggregationEndTimeUTC** |Fin de la fenêtre de temps pour quel système de compteurs ont été agrégés. |
|**CounterName** |Compteurs du système, incluant la mémoire et l’utilisation du processeur par la passerelle, mashup et globale par l’ordinateur qui héberge la passerelle. |
|**Max** |Valeur maximale pour le compteur de système pour la fenêtre de temps d’agrégation. |
|**Min** |Valeur minimale pour le compteur de système pour la fenêtre de temps d’agrégation. |
|**Moyenne** |Valeur moyenne du compteur de système pour la fenêtre de temps d’agrégation. |
| | |

## <a name="visualize-gateway-performance"></a>Visualiser les performances de la passerelle

Maintenant, vous pouvez visualiser les données qui se trouve dans les fichiers journaux.

1. Téléchargez le [modèle de passerelle performances PBI](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) et ouvrez-le à l’aide de Power BI desktop.

1. Dans la boîte de dialogue qui s’ouvre, vérifiez que le chemin d’accès du dossier correspond à la valeur dans **ReportFilePath**.

    ![Fenêtre contextuelle s’affiche pour le chemin d’accès de dossier](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Sélectionnez **charge**, et le fichier de modèle démarre le chargement des données à partir de vos fichiers journaux. Tous les visuels doivent ensuite être remplies à l’aide des données dans les rapports.

1. Si vous le souhaitez enregistrer ce fichier comme un fichier PBIX et publiez-le sur votre service pour les actualisations automatiques.

En outre, vous pouvez personnaliser ce fichier de modèle pour l’adapter à vos besoins. Pour plus d’informations sur les modèles de Power BI, consultez ce [billet de Blog Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).