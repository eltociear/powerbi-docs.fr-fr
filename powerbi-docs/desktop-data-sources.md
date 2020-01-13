---
title: Sources de données dans Power BI Desktop
description: Sources de données dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/25/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0f24675d4185efd7524d9e8c453c919d64e0364a
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "75222137"
---
# <a name="data-sources-in-power-bi-desktop"></a>Sources de données dans Power BI Desktop

Power BI Desktop vous permet de vous connecter aux données de nombreuses sources différentes. Pour obtenir la liste complète des sources de données disponibles, consultez [Sources de données Power BI](power-bi-data-sources.md).

Pour vous connecter à des données, sélectionnez **Obtenir des données** à partir du ruban **Accueil**. Sélectionnez la flèche orientée vers le bas ou le texte **Obtenir les données** sur le bouton pour afficher le menu des types de données **Les plus courantes** illustré dans l’image suivante :

![Obtenir des données dans Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

En sélectionnant **Plus...** dans le menu **Les plus courantes**, vous accédez à la fenêtre **Obtenir les données**. Vous pouvez également faire apparaître la fenêtre **Obtenir les données** (et ignorer le menu **Les plus courantes**) en sélectionnant directement le **bouton d’icône** **Obtenir les données**.

![Bouton Get Data](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> L’équipe Power BI enrichit en permanence les sources de données disponibles pour **Power BI Desktop** et le **service Power BI**. Par conséquent, les premières versions des sources de données en cours de création sont souvent marquées de la mention *Bêta* ou *Préversion*. Une source de données marquée de la mention *Bêta* ou *Préversion* a un support et des fonctionnalités limités et ne doit pas être utilisée dans les environnements de production. De plus, une source de données marquée de la mention *Bêta* ou *Préversion* pour **Power BI Desktop** risque de ne pas pouvoir être utilisée dans le **service Power BI** ou dans d’autres services Microsoft tant que la source de données n’a pas été mise à la disposition générale.

## <a name="data-sources"></a>Sources de données
Les types de données sont organisés dans les catégories suivantes :

* Tout
* Fichier
* Base de données
* Power BI
* Azure
* Services en ligne
* Autre

La catégorie **Toutes** comprend tous les types de connexion de données de toutes les catégories.

La catégorie **Fichier** fournit les connexions de données suivantes :

* Excel
* Texte/CSV
* XML
* JSON
* Dossier
* PDF
* Dossier SharePoint

L’image suivante montre la fenêtre **Obtenir les données** pour **Fichier**.

![Obtenir des données > Fichier](media/desktop-data-sources/data-sources-03.png)

La catégorie **Base de données** fournit les connexions de données suivantes :

* Base de données SQL Server
* Base de données Access
* Base de données SQL Server Analysis Services
* Base de données Oracle
* Base de données IBM DB2
* Base de données IBM Informix (bêta)
* IBM Netezza
* Base de données MySQL
* Base de données PostgreSQL
* Base de données Sybase
* Teradata
* Base de données SAP HANA
* Serveur d’applications SAP Business Warehouse
* Serveur de messages SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* Cubes AtScale
* Connecteur BI
* Dremio
* Exasol
* Indexima (bêta)
* InterSystems IRIS (bêta)
* Jethro (bêta)
* Kyligence Enterprise (bêta)
* MarkLogic (bêta)

> [!NOTE]
> Certains connecteurs de base de données doivent être activés. Pour cela, sélectionnez **Fichier > Options et paramètres > Options**, puis sélectionnez **Fonctionnalités en version préliminaire** et activez le connecteur. Si vous ne voyez pas certains des connecteurs mentionnés ci-dessus et que vous souhaitez les utiliser, vérifiez les paramètres **Fonctions en version préliminaire**. Notez également qu’une source de données marquée de la mention *Bêta* ou *Préversion* a un support et des fonctionnalités limités et ne doit pas être utilisée dans les environnements de production.

L’image suivante montre la fenêtre **Obtenir les données** pour **Base de données**.

![Obtenir des données > Bases de données](media/desktop-data-sources/data-sources-04.png)

La catégorie **Power Platform** fournit les connexions de données suivantes :

* Jeux de données Power BI
* Dataflows Power BI
* Common Data Service
* Dataflows Power Platform

L’image suivante représente la fenêtre **Obtenir des données** pour **Power Platform**.

![Obtenir des données > Power BI](media/desktop-data-sources/data-sources-05.png)

La catégorie **Azure** fournit les connexions de données suivantes :

* Azure SQL Database
* Azure SQL Data Warehouse
* Base de données Azure Analysis Services
* Stockage Blob Azure
* Stockage Table Azure
* Azure Cosmos DB
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Data Explorer (Kusto)
* Azure Cost Management
* Azure Time Series Insights (bêta)

L’image suivante montre la fenêtre **Obtenir les données** pour **Azure**.

![Obtenir des données > Azure](media/desktop-data-sources/data-sources-06.png)

La catégorie **Services en ligne** fournit les connexions de données suivantes :

* Liste SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (Online)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (local)
* Microsoft Azure Consumption Insights (bêta)
* Azure DevOps (bêta)
* Azure DevOps Server (bêta)
* Objets Salesforce
* Rapports Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (bêta)
* Data.World – Obtenir le jeu de données (bêta)
* Facebook
* GitHub (bêta)
* MailChimp (bêta)
* Marketo (bêta)
* Mixpanel (bêta)
* Planview Enterprise One - PRM (bêta)
* Planview Projectplace (bêta)
* QuickBooks Online (bêta)
* Smartsheet
* SparkPost (bêta)
* Stripe (bêta)
* SweetIQ (bêta)
* Planview Enterprise One - CMT (bêta)
* Twilio (bêta)
* tyGraph (bêta)
* Webtrends (bêta)
* Zendesk (bêta)
* Dynamics 365 Customer Insights (bêta)
* Emigo Data Source (Bêta)
* Entersoft Business Suite (bêta)
* Industrial App Store
* Intune Data Warehouse (bêta)
* Microsoft Graph Security (Bêta)
* Quick Base
* TeamDesk (bêta)


L’illustration suivante montre la fenêtre **Obtenir les données** pour **Services en ligne**

![Obtenir des données > Services en ligne](media/desktop-data-sources/data-sources-07.png)

La catégorie **Autre** fournit les connexions de données suivantes :

* Web
* Liste SharePoint
* Flux OData
* Active Directory
* Microsoft Exchange
* Fichier Hadoop (HDFS)
* Spark
* Script R
* Script Python
* ODBC
* OLE DB
* BI360 - Budgets & Rapports financiers (bêta)
* Denodo
* Information Grid (bêta)
* Paxata 
* QubolePresto (bêta)
* Roamler (bêta)
* SurveyMonkey (bêta)
* Tenforce (Smart) (bêta)
* Workforce Dimensions (bêta)
* Requête vide

L’image suivante montre la fenêtre **Obtenir les données** pour **Autre**.

![Obtenir des données > Autre](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> À ce stade, il n’est pas possible de se connecter aux sources de données personnalisées sécurisées à l’aide d’Azure Active Directory.

## <a name="connecting-to-a-data-source"></a>Connexion à une source de données
Pour vous connecter à une source de données, sélectionnez la source de données dans la fenêtre **Obtenir les données** et sélectionnez **Se connecter**. Dans l’image suivante, l’option **Web** est sélectionnée dans la catégorie de connexions de données **Autre**.

![Se connecter au web](media/desktop-data-sources/data-sources-08.png)

Une fenêtre de connexion s’affiche, spécifique au type de connexion de données. Si des informations d’identification sont requises, vous êtes invité à les fournir. L’image suivante montre la saisie d’une URL pour établir une connexion à une source de données web.

![saisie d’URL web](media/desktop-data-sources/datasources-fromwebbox.png)

Une fois l’URL ou les informations de connexion à la ressource entrées, sélectionnez **OK**. Power BI Desktop établit la connexion à la source de données et présente les sources de données disponibles dans le **Navigateur**.

![Écran de navigateur](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Vous pouvez charger les données en sélectionnant le bouton **Charger** situé en bas du volet **Navigateur**, ou modifier la requête avant de charger les données en sélectionnant le bouton **Modifier**.

C’est là tout ce qu’il faut savoir pour se connecter à des sources de données dans Power BI Designer ! Essayez de vous connecter à des données à partir de notre liste grandissante de sources de données et consultez-la régulièrement : nous continuons de l’enrichir en permanence.

## <a name="using-pbids-files-to-get-data"></a>Utilisation de fichiers PBIDS pour l’obtention de données

Les fichiers PBIDS sont des fichiers Power BI Desktop qui ont une structure spécifique et ont l’extension .PBIDS extension pour identifier qu’il s’agit de fichiers de source de données Power BI.

Vous pouvez créer un fichier .PBIDS pour simplifier l’expérience **Obtenir des données** pour les créateurs de rapports de votre organisation. Il est recommandé aux administrateurs de créer ces fichiers pour les connexions couramment utilisées, afin de faciliter l’utilisation des fichiers PBIDS pour les nouveaux auteurs de rapports. 

Lorsqu’un auteur ouvre un fichier .PBIDS, Power BI Desktop s’ouvre et invite l’utilisateur à fournir des informations d’identification pour s’authentifier et se connecter à la source de données spécifiée dans le fichier. La boîte de dialogue de navigation s’affiche et l’utilisateur doit sélectionner les tables de cette source de données à charger dans le modèle. Les utilisateurs peuvent également avoir besoin de sélectionner la ou les bases de données si aucune n’a été spécifiée dans le fichier .PBIDS. 

À partir de là, l’utilisateur peut commencer à créer des visualisations ou à réexaminer les *Sources récentes* pour charger un nouvel ensemble de tables dans le modèle. 

Actuellement, les fichiers .PBIDS prennent en charge une seule source de données dans un même fichier. La spécification de plusieurs sources de données génère une erreur. 

Pour créer le fichier .PBIDS, les administrateurs doivent spécifier les entrées requises pour une seule connexion et peuvent spécifier le mode de la connexion, **DirectQuery** ou **Importation**. Si **mode** manque ou est null dans le fichier, l’utilisateur qui ouvre le fichier dans Power BI Desktop est invité à sélectionner DirectQuery ou Importation. 

### <a name="pbids-file-examples"></a>Exemples de fichiers PBIDS

Cette section fournit des exemples de sources de données couramment utilisées. Le type de fichier .PBIDS prend uniquement en charge les connexions de données qui sont également prises en charge dans Power BI Desktop, à deux exceptions près : Les connexions actives et les requêtes vides. 

Le fichier .PBIDS n’inclut *pas* les informations d’authentification et les informations de table et de schéma.  

Voici plusieurs exemples courants de fichiers .PBIDS ; notez qu’ils ne sont pas complets ou exhaustifs. Pour les autres sources de données, vous pouvez vous reporter au [Format DSR (référence de source de données) pour les informations de protocole et d’adresse](https://docs.microsoft.com/azure/data-catalog/data-catalog-dsr#data-source-reference-specification).

Ces exemples sont destinés uniquement à des fins pratiques, ne sont pas pensés pour être exhaustifs et n’incluent pas tous les connecteurs pris en charge au format DSR. Les administrateurs ou les organisations peuvent créer leurs propres sources de données en utilisant ces exemples comme guides, et s’en servir pour créer et prendre en charge leurs propres fichiers de source de données. 


**Azure AS**
```
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```


 

**Dossier**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

**OData**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```
 
**SAP BW**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```
 
**SAP Hana**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

**Liste SharePoint**

L’URL doit pointer vers le site SharePoint proprement dit, et non vers une liste au sein du site. Les utilisateurs obtiennent un navigateur qui leur permet de sélectionner une ou plusieurs listes à partir de ce site, chacune d’elles devenant une table du modèle. 
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```
 
 
**SQL Server**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```
 

**Fichier texte**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```
 

**Web**
```
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```
 

**Dataflow**
```
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```


## <a name="next-steps"></a>Étapes suivantes
Power BI Desktop vous permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](desktop-what-is-desktop.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)    
