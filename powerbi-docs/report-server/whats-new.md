---
title: "Nouveautés dans Power BI Report Server"
description: "Découvrez les nouveautés dans Power BI Report Server. Cet article aborde les principaux domaines de fonctionnalités et est mis à jour à mesure que de nouveaux éléments sont publiés."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/31/2017
ms.author: asaxton
ms.openlocfilehash: d351a117307e86c7b0750e9bcdf813b08b28bb0f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="whats-new-in-power-bi-report-server"></a>Nouveautés dans Power BI Report Server
Découvrez les nouveautés dans Power BI Report Server. Cet article aborde les principaux domaines de fonctionnalités et est mis à jour à mesure que de nouveaux éléments sont publiés.

Pour télécharger Power BI Report Server et Power BI Desktop optimisé pour Power BI Report Server, accédez à la page [Rapports locaux avec Power BI Report Server](https://powerbi.microsoft.com/report-server/).

![conseil](media/whats-new/fyi-tip.png "conseil") Pour les notes de publication actuelles, voir [Notes de publication de Power BI Report Server](release-notes.md).

Pour plus d’informations sur les nouveautés, consultez :

* [Nouveautés dans le service Power BI](../service-whats-new.md)
* [Nouveautés dans Power BI Desktop](../desktop-latest-update.md)
* [Nouveautés dans les applications mobiles pour Power BI](../mobile-whats-new-in-the-mobile-apps.md)
* [Blog de l’équipe Power BI](https://powerbi.microsoft.com/blog/)

## <a name="october-2017-release"></a>Version d’octobre 2017
### <a name="power-bi-report-data-sources"></a>Sources de données de rapport Power BI
Les rapports Power BI dans Power BI Report Server peuvent se connecter à diverses sources de données. Vous pouvez importer des données et planifier une actualisation des données, ou les interroger directement à l’aide de DirectQuery ou d’une connexion active à SQL Server Analysis Services. Consultez la liste des sources de données qui prennent en charge l’actualisation planifiée et de celles qui prennent en charge DirectQuery dans « Sources de données de rapport Power BI dans Power BI Report Server ».

### <a name="scheduled-data-refresh-for-imported-data"></a>Actualisation des données planifiée pour des données importées
Dans Power BI Report Server, vous pouvez configurer une actualisation des données planifiée pour tenir les données à jour dans les rapports Power BI avec un modèle incorporé au lieu d’une connexion active ou de DirectQuery. Avec un modèle incorporé, vous importez les données de sorte qu’elles sont déconnectées de la source de données d’origine. Une mise à jour est nécessaire pour maintenir les données actualisées, et l’actualisation planifiée est la méthode appropriée pour cela. Pour en savoir plus, lisez « Actualisation planifiée pour les rapports Power BI dans Power BI Report Server ».

### <a name="editing-power-bi-reports-from-the-server"></a>Modification des rapports Power BI à partir du serveur
Vous pouvez ouvrir et modifier des fichiers de rapport Power BI (.pbix) à partir du serveur, mais que vous récupérez le fichier d’origine que vous avez chargé.  Cela signifie que **si les données ont été actualisées par le serveur, elles ne sont pas actualisées lorsque vous ouvrez le fichier pour la première fois**. Pour voir la modification, vous devez actualiser le fichier manuellement localement.

### <a name="large-file-uploaddownload"></a>Chargement/téléchargement de fichier volumineux
Vous pouvez charger des fichiers jusqu’à une taille de 2 Go, bien que, par défaut, cette limite soit fixée à 1 Go dans les paramètres du serveur de rapports dans SQL Server Management Studio (SSMS).  Ces fichiers sont stockés dans la base de données, comme ils le sont sur SharePoint, et aucune configuration particulière du catalogue SQL Server d’est requise.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Accès à des Jeux de données partagés en tant que flux OData
Vous pouvez accéder à des jeux de données partagés à partir de Power BI Desktop avec un flux OData. Pour plus d’informations, voir [Accès à des jeux de données partagés en tant que flux OData dans Power BI Report Server](access-dataset-odata.md).

### <a name="scale-out"></a>Montée en puissance parallèle
Cette version prend en charge la montée en puissance parallèle. Pour une expérience optimale, utilisez un équilibreur de charge et définissez l’affinité du serveur. Notez que, le scénario n’étant pas encore optimisé pour la montée en puissance parallèle, vous allez voir des modèles potentiellement répliqués sur plusieurs nœuds. Le scénario fonctionne sans équilibreur de charge réseau et sessions rémanentes. Toutefois, outre une surutilisation de la mémoire sur les nœuds résultant du fait que le modèle est chargé plusieurs fois, vous allez constater que les performances ralentissent entre les connexions pendant la diffusion en continu du modèle, quand celui-ci atteint un nouveau nœud entre des demandes.  

### <a name="administrator-settings"></a>Paramètres administrateur
Les administrateurs peuvent définir les propriétés suivantes dans les propriétés avancées de SSMS pour la batterie de serveurs :

* EnableCustomVisuals : True/False
* EnablePowerBIReportEmbeddedModels : True/False
* EnablePowerBIReportExportData : True/False
* MaxFileSizeMb : la valeur par défaut est désormais 1000
* ModelCleanupCycleMinutes : fréquence de vérification pour la suppression de modèles de la mémoire
* ModelExpirationMinutes : durée avant que le modèle expire et soit supprimé, en fonction de l’heure de la dernière utilisation
* ScheduleRefreshTimeoutMinutes : temps que l’actualisation de données peut prendre pour un modèle Par défaut, il s’agit de deux heures.  Il n’existe aucune limite supérieure.

**Fichier de configuration rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API Développeur
L’API développeur (API REST) introduite pour SSRS 2017 a été étendue pour que Power BI Report Server puisse travailler avec des fichiers Excel et .pbix. Un cas d’usage potentiel consiste à télécharger par programme des fichiers à partir du serveur, à les actualiser, puis à les republier. Il s’agit de la seule façon d’actualiser des classeurs Excel, par exemple, avec des modèles PowerPivot.

Notez qu’il existe une nouvelle API distincte pour les fichiers volumineux, qui sera mise à jour dans la version Power BI Report Server de Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) et l’encombrement mémoire de Power BI Report Server
Power BI Report Server héberge désormais en interne SQL Server Analysis Services (SSAS). Cela n’est pas spécifique à une actualisation planifiée. Un hébergement SSAS peut étendre considérablement l’encombrement de mémoire du serveur de rapports. Le fichier de configuration AS.ini étant disponible sur les nœuds de serveur, si vous êtes familiarisé avec SSAS, vous pouvez mettre à jour les paramètres, dont la limite maximale de mémoire et la mise en cache sur disque, etc. Pour plus de détails, voir [Propriétés du serveur dans Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services).

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Affichage de classeurs Excel et interaction avec ceux-ci
Excel et Power BI contiennent une panoplie d’outils unique dans ce secteur d’activité. Ensemble, ils permettent aux analystes de collecter, de mettre en forme, d’analyser et d’explorer visuellement leurs données avec beaucoup plus de facilité. Outre l’affichage de rapports Power BI sur le portail web, les utilisateurs professionnels peuvent désormais faire de même avec des classeurs Excel dans Power BI Report Server. Ils disposent ainsi d’un emplacement unique pour publier et consulter leur contenu Microsoft BI en libre-service.

Nous avons publié une [procédure pas à pas montrant comment ajouter Office Online Server (OOS) à votre environnement en préversion Power BI Report Server](excel-oos.md). Les clients titulaires d’un compte de licence en volume peuvent télécharger OOS gratuitement à partir du Centre MVLS et accéder aux fonctionnalités en lecture seule. Une fois configurés, les utilisateurs peuvent interagir avec des classeurs Excel qui :

* n’ont aucune dépendance de source de données externe ;
* disposent d’une connexion active à une source de données SQL Server Analysis Services externe ;
* disposent d’un modèle de données PowerPivot.

### <a name="support-for-new-table-and-matrix-visuals"></a>Prendre en charge des nouveaux visuels de table et de matrice
Power BI Report Server prend désormais en charge les nouveaux visuels de table et de matrice Power BI. Pour créer des rapports avec ces visuels, vous devez disposer d’une version mise à jour de Power BI Desktop pour la préversion d’octobre 2017. Une installation côte à côte avec la version de juin 2017 de Power BI Desktop n’est pas possible. Pour obtenir la dernière version de Power BI Desktop, dans la [page de téléchargement de Power BI Report Server](https://powerbi.microsoft.com/report-server/), sélectionnez **Options de téléchargement avancées**.

## <a name="june-2017"></a>Juin 2017
* Disponibilité générale (GA) de Power BI Report Server.

## <a name="may-2017"></a>Mai 2017
* Disponibilité de Power BI Report Server en version préliminaire
* Possibilité de publier des rapports Power BI localement
  * Prise en charge des visuels personnalisés
  * Prise en charge prochaine des connexions actives Analysis Services uniquement avec davantage de sources de données.
  * Application mobile Power BI mise à jour pour afficher des rapports Power BI hébergés dans Power BI Report Server
* Collaboration améliorée dans les rapports avec des commentaires

## <a name="next-steps"></a>Étapes suivantes
[Notes de publication de Power BI Report Server](release-notes.md)  
[Manuel de l’utilisateur](user-handbook-overview.md)  
[Manuel de l’administrateur](admin-handbook-overview.md)  
[Démarrage rapide : installer Power BI Report Server](quickstart-install-report-server.md)  
[Installer le Générateur de rapports](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Télécharger SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

