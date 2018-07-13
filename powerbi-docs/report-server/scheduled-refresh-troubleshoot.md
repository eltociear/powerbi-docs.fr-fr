---
title: Résoudre les problèmes d’actualisation planifiée dans Power BI Report Server
description: Cet article décrit les ressources disponibles pour résoudre les problèmes d’actualisation planifiée dans Power BI Report Server.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: a90f22c262a314b50981be94121e2573f9fe525a
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34296362"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Résoudre les problèmes d’actualisation planifiée dans Power BI Report Server
Cet article décrit les ressources disponibles pour résoudre les problèmes d’actualisation planifiée dans Power BI Report Server.

À mesure que des problèmes apparaîtront, cet article sera mis à jour avec des informations pour vous aider.

## <a name="common-issues"></a>Problèmes courants
Voici les problèmes les plus courants que allez rencontrer en tenant de planifier l’actualisation d’un rapport. 

### <a name="driver-related-problems"></a>Problèmes liés au pilote
La connexion à différentes sources de données peut nécessiter l’installation de pilotes tiers pour aboutir correctement. Non seulement vous devez les installer sur la machine sur laquelle vous utilisez Power BI Desktop, mais vous devez également vous assurer que le pilote est installé sur le serveur de rapports.

Le pilote peut également être disponible en versions 32 bits et 64 bits. Veillez à installer le pilote 64 bits, car Power BI Report Server est 64 bits.

Pour plus de détails sur la façon d’installer et de configurer des pilotes tiers, consultez le fabricant.

### <a name="memory-pressure"></a>Sollicitation de la mémoire
Une sollicitation de la mémoire peut se produire quand des rapports requièrent davantage de mémoire pour le traitement et la restitution. Planifier l’actualisation des rapports peut nécessiter une quantité significative de mémoire sur la machine. C’est le cas en particulier des rapports de grande taille. Une sollicitation de la mémoire peut entraîner des échecs de rapport, ainsi qu’un blocage du serveur de rapports.

Si vous rencontrez constamment une sollicitation de la mémoire, il peut être intéressant d’envisager un déploiement avec montée en puissance parallèle du serveur de rapports afin de répartir la charge des ressources. Vous pouvez également spécifier qu’un serveur de rapports donné est utilisé pour l’actualisation des données avec le paramètre `IsDataModelRefreshService` dans rsreportserver.config. Ce paramètre vous permet de définir un ou plusieurs serveurs faisant office de serveur frontal pour gérer les rapports à la demande, et un autre ensemble de serveurs à utiliser uniquement pour l’actualisation planifiée.

Pour plus d’informations sur la façon de surveiller une instance Analysis Services, voir [Surveiller une instance Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Pour plus d’informations sur les paramètres de mémoire dans Analysis Services, voir [Propriétés de mémoire](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Configuration Kerberos
L’établissement d’une connexion à une source de données avec des informations d’identification Windows peut nécessiter la configuration d’une délégation Kerberos contrainte. Pour plus d’informations sur la façon de configurer une délégation Kerberos contrainte, voir [Configurer Kerberos pour utiliser les rapports Power BI](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Problèmes connus
Des informations supplémentaires sur les problèmes connus seront répertoriées ici quand elles deviendront disponibles.

## <a name="configuration-settings"></a>Paramètres de configuration
Les paramètres suivants permettent d’affecter une actualisation planifiée. Les paramètres définis dans SQL Server Management Studio (SSMS) s’appliquent à tous les serveurs de rapports à l’intérieur d’un déploiement avec montée en puissance parallèle. Les paramètres configurés dans rsreportserver.config s’appliquent au serveur spécifique sur lequel ils sont définis.

**Paramètres dans SSMS :**

| Paramètre | Description |
| --- | --- |
| MaxFileSizeMb |Taille de fichier maximale des rapports chargés. La valeur par défaut est 1000 Mo (1 Go). La valeur maximale est 2000 Mo (2 Go). |
| ModelCleanupCycleMinutes |Définit la fréquence à laquelle le modèle est vérifié en vue de le supprimer de la mémoire. La valeur par défaut est 15 minutes. |
| ModelExpirationMinutes |Définit le temps restant avant l’expiration du modèle en fonction de la dernière heure d’utilisation et de suppression. La valeur par défaut est 60 minutes. |
| ScheduleRefreshTimeoutMinutes |Définit le temps que peut prendre l’actualisation des données pour un mode. La valeur par défaut est 120 minutes. Il n’existe aucune limite supérieure. |

**Paramètres dans rsreportserver.config :**

```
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Outils de résolution des problèmes
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Journaux pertinents pour l’actualisation planifiée des rapports Power BI
Les fichiers journaux qui contiennent des informations sur l’actualisation planifiée sont les journaux RSPowerBI_ logs. Ils se trouvent dans le dossier LogFiles de l’emplacement d’installation de votre serveur de rapports. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Condition d’erreur**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Actualisation réussie***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Informations d’identification incorrectes**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Activation de la journalisation détaillée
L’activation de la journalisation détaillée dans Power BI Report Server est la même que pour SQL Server Reporting Services.

1. Ouvrez `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Sous `<system.diagnostics>`, modifiez **DefaultTraceSwitch** en **4**.
3. Sous `<RStrace>`, modifiez **Composants** en **tous:4**. 

### <a name="executionlog"></a>ExecutionLog
Chaque fois qu’un rapport Power BI est rendu, ou un plan d’actualisation planifiée exécuté, les nouvelles entrées sont ajoutées au journal d’exécution dans la base de données. Ces entrées sont disponibles dans l’affichage **ExecutionLog3** dans la base de données du catalogue du serveur de rapports.

Les entrées de journal d’exécution pour les rapports Power BI diffèrent des entrées pour d’autres types de rapports.

* Les colonnes TimeRendering contiennent toujours 0. Le rendu des rapports Power BI se produit dans le navigateur, pas sur le serveur.
* Il existe 2 types de demandes et les actions d’élément suivantes :
  * **Interactives** : chaque fois qu’un rapport est consulté.
    * **ASModelStream** : quand le modèle de données est diffusé en continu vers Analysis Services à partir du catalogue.
    * **ConceptualSchema** : quand l’utilisateur clique sur l’affichage du rapport.
    * **QueryData** : chaque fois que des données sont demandées d’un client.
  * **Actualisation du cache** : chaque fois qu’un plan d’actualisation planifiée a été exécuté.
    * **ASModelStream** : chaque fois que le modèle de données est diffusé en continu vers Analysis Services à partir du catalogue.
    * **DataRefresh** : chaque fois que les données sont actualisées à partir d’une ou plusieurs sources de données.
    * **SaveToCatalog** : chaque fois que le modèle de données est réenregistré dans le catalogue.

## <a name="analysis-services"></a>Analysis Services
Il peut vous arriver de vouloir modifier Analysis Services pour diagnostiquer des problèmes ou ajuster des limites de mémoire.

> [!IMPORTANT]
> Ces paramètres sont réinitialisés dès que vous mettez à niveau le serveur de rapports. Veillez à conserver une copie de vos modifications et à les réappliquer si nécessaire.
> 
> 

### <a name="install-location"></a>Emplacement d’exploration
L’emplacement par défaut pour Power BI Report Server et Analysis Services est la suivante.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Configuration des paramètres d’Analysis Services (msmdsrv.ini)
Dans le répertoire `<install directory>\PBIRS\ASEngine`, vous trouverez le fichier *msmdsrv.ini* qui permet de contrôler différents paramètres d’Analysis Services. En ouvrant ce fichier, vous réalisez immédiatement qu’il ne contient pas tous les paramètres que vous vous attendez à trouver dans le fichier msmdsrv.ini. 

C’est parce que le processus réel d’Analysis Services exécuté par Power BI Report Server est lancé dans `<install directory>\PBIRS\ASEngine\workspaces`. Dans ce dossier, vous trouverez le fichier *msmdsrv.ini* complet auquel vous êtes habitué. Il est important de ne pas modifier le fichier dans le dossier des espaces de travail, car il est réécrit à chaque démarrage du processus Analysis Services. Si vous souhaitez contrôler un paramètre, faites-le en modifiant le fichier msmdsrv.ini dans le répertoire `<install directory>\PBIRS\ASEngine`.

Les paramètres suivants sont réinitialisés à chaque lancement du processus Analysis Services. Les modifications que vous y apportez seront ignorées.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Profilage du processus Analysis Services local
Une trace du Générateur de profils SQL peut être exécutée sur le processus Analysis Services local à des fins de diagnostic. Pour vous connecter à l’instance Analysis Services locale, procédez comme suit.

Une trace du Générateur de profils SQL Server est incluse dans [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

1. Démarrez **SQL Server Profiler** en tant qu’administrateur.
2. Sélectionnez le bouton **Nouvelle trace**.
3. Dans la boîte de dialogue **Se connecter au serveur**, sélectionnez **Analysis Services**, puis entrez **localhost:5132** pour le nom du serveur.
4. Dans la boîte de dialogue **Propriétés de la trace**, sélectionnez les événements que vous souhaitez capturer, puis choisissez **Exécuter**.

## <a name="lock-pages-in-memory-windows-privilege"></a>Privilège Windows Verrouiller les pages en mémoire
Si vous ne parvenez pas à rendre un rapport Power BI, l’assignation du privilège Windows **Verrouiller les pages en mémoire** au compte de services exécutant Power BI Report Server peut aider. Pour plus d’informations sur la configuration du privilège **Verrouiller les pages en mémoire**, voir [Privilèges Windows affectés au compte de service Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

