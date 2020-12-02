---
title: Actualisation planifiée de rapport Power BI dans Power BI Report Server
description: L’actualisation planifiée des rapports Power BI permet de tenir à jour les données d’un rapport avec un modèle incorporé.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/09/2020
ms.openlocfilehash: 4dd8914abe1f098b66d23daa299200b90b9bda6a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412572"
---
# <a name="power-bi-report-scheduled-refresh-in-power-bi-report-server"></a>Actualisation planifiée de rapport Power BI dans Power BI Report Server
L’actualisation planifiée des rapports Power BI permet de tenir à jour les données d’un rapport.

![Actualisation planifiée dans Power BI Report Server](media/scheduled-refresh/scheduled-refresh-success.png)

L’actualisation planifiée est spécifique des rapports Power BI avec un modèle incorporé. Ce qui signifie que vous avez importées des données dans le rapport au lieu d’utiliser une connexion active ou DirectQuery. Lors de l’importation de vos données, celles-ci sont déconnectées de la source de données d’origine et doivent être mises à jour pour rester actualisées. L’actualisation planifiée est la façon de conserver vos données à jour.

L’actualisation planifiée est configurée dans la section gestion d’un rapport. Pour plus d’informations sur la façon de configurer une actualisation planifiée, voir [Comment configurer une actualisation planifiée de rapport Power BI](configure-scheduled-refresh.md).

## <a name="how-this-works"></a>Principe de fonctionnement
Plusieurs composants sont impliqués lors de l’utilisation de l’actualisation planifiée pour vos rapports Power BI.

* SQL Server Agent est utilisé en tant que minuteur pour générer des événements planifiés.
* Les travaux planifiés sont ajoutés à une file d’attente d’événements et de notifications dans la base de données du serveur de rapports. Dans un déploiement avec montée en puissance parallèle, la file d'attente est partagée par tous les serveurs de rapports de la structure.
* Le traitement des rapports qui se produit à la suite d'un événement de planification est entièrement effectué en arrière-plan.
* Le modèle de données est chargé dans une instance Analysis Services.
* Pour certaines sources de données, le moteur mashup Power Query est utilisé pour se connecter aux sources de données et transformer les données. Une connexion à d’autres sources de données est possible directement à partir d’un service Analysis Services utilisé pour héberger les modèles de données pour Power BI Report Server.
* Les nouvelles données sont chargées dans le modèle de données à l’intérieur d’Analysis Services.
* Dans une configuration de scale-out, le modèle de données peut être répliqué entre les nœuds.
* Analysis Services traite les données et exécute tous les calculs nécessaire.

Power BI Report Server maintient une file d’attente des événements pour toutes les opérations planifiées. Il interroge régulièrement la file d'attente pour vérifier si elle contient de nouveaux événements. Par défaut, la file d'attente fait l'objet d'une analyse toutes les 10 secondes. Si vous souhaitez changer cette fréquence, modifiez les paramètres de configuration **PollingInterval**, **IsNotificationService** et **IsEventService** dans le fichier RSReportServer.config. **IsDataModelRefreshService** peut également être utilisé pour indiquer si un serveur de rapports traite les événements planifiés.

### <a name="analysis-services"></a>Analysis Services
Rendre un rapport Power BI ainsi qu’effectuer une actualisation planifiée nécessitent le chargement du modèle de données du rapport Power BI dans Analysis Services. Un processus Analysis Services s’exécute avec Power BI Report Server.

## <a name="considerations-and-limitations"></a>Observations et limitations
### <a name="when-scheduled-refresh-cant-be-used"></a>Quand une actualisation planifiée ne peut pas être utilisée
Il n’est pas possible de créer un plan d’actualisation planifiée sur certains rapports Power BI. La liste suivante répertorie les rapports Power BI sur lesquels il n’est pas possible de créer un plan d’actualisation planifiée.

* Votre rapport contient une ou plusieurs sources de données Analysis Services qui utilisent une connexion active.
* Votre rapport contient une ou plusieurs sources de données qui utilisent DirectQuery.
* Votre rapport ne contient aucune source de données. Par exemple, les données sont entrées manuellement via l’option *Entrer des données* ou un rapport contient uniquement du contenu statique tel que des images, du texte, etc.

En plus de la liste ci-dessus, il existe des scénarios spécifiques avec des sources de données en mode d’*importation*, pour lesquels vous ne pouvez pas créer des plans d’actualisation.

* Si une source de données *Fichier* ou *Dossier* est utilisée, et si le chemin d’accès du fichier est un chemin local (par exemple, C:\Users\user\Documents), il n’est pas possible de créer un plan d’actualisation. Le chemin d’accès doit être un chemin auquel le serveur de rapports peut se connecter, tel un partage réseau. Par exemple, *\\myshare\Documents*.
* Si la source de données peut être connectée uniquement à l’aide d’OAuth (par exemple, Facebook, Google Analytique, Salesforce, etc.), le plan d’actualisation du cache ne peut pas être créé. Actuellement, le serveur de rapports ne prend en charge l’authentification OAuth pour aucune source de données, que ce soit pour un rapport paginé, mobile ou Power BI.

### <a name="memory-limits"></a>Limites applicables à la mémoire
Traditionnellement, la charge de travail pour un serveur de rapports était similaire à celle d’une application web. La capacité à charger des rapports avec des données importées ou DirectQuery, ainsi que la possibilité d’effectuer une actualisation planifiée, reposent sur une instance Analysis Services hébergée à côté du serveur de rapports. Par conséquent, cela pourrait entraîner une sollicitation de la mémoire inattendue sur le serveur. Planifiez le déploiement de votre serveur en conséquence, sachant qu’Analysis Services peut consommer de la mémoire en même temps que le serveur de rapports.

Pour plus d’informations sur la façon de surveiller une instance Analysis Services, voir [Surveiller une instance Analysis Services](/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Pour plus d’informations sur les paramètres de mémoire dans Analysis Services, voir [Propriétés de mémoire](/sql/analysis-services/server-properties/memory-properties).

### <a name="data-model-size-limit"></a>Limite concernant la taille des modèles de données
Le modèle de données qui est chargé dans le moteur interne Analysis Services lors d’une actualisation planifiée a une taille maximale de 2 000 Mo (2 Go). Cette taille ne peut pas être configurée. Si votre modèle de données dépasse les 2 Go, l’erreur d’actualisation suivante s’affichera : « La longueur du résultat dépasse la limite de longueur (2 Go) du type cible ». Dans ce cas, nous vous recommandons d’héberger le modèle dans une instance Analysis Services, et d’utiliser une connexion active au modèle du rapport.

## <a name="next-steps"></a>Étapes suivantes
Configurez une [actualisation planifiée](configure-scheduled-refresh.md) sur un rapport Power BI.

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)