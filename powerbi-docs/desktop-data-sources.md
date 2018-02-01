---
title: "Sources de données dans Power BI Desktop"
description: "Sources de données dans Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 04/29/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 42acbc0823f798ee0c0d762fc124c0f371494bd9
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="data-sources-in-power-bi-desktop"></a>Sources de données dans Power BI Desktop
Power BI Desktop vous permet de vous connecter aux données de nombreuses sources différentes. La liste complète des sources de données disponibles figure au bas de cette page.

Pour vous connecter à des données, sélectionnez **Obtenir des données** à partir du ruban **Accueil**. Sélectionnez la flèche orientée vers le bas ou le texte **Obtenir les données** sur le bouton pour afficher le menu des types de données **Les plus courantes** illustré dans l’image suivante.

![](media/desktop-data-sources/data-sources_1.png)

En sélectionnant **Plus...** dans le menu **Les plus courantes**, vous accédez à la fenêtre **Obtenir les données**. Vous pouvez également faire apparaître la fenêtre **Obtenir les données** (et ignorer le menu **Les plus courantes** ) en sélectionnant directement le **bouton d’icône** **Obtenir les données**.

![](media/desktop-data-sources/data-sources_2.png)

> [!NOTE]
> L’équipe Power BI enrichit en permanence les sources de données disponibles pour **Power BI Desktop** et le **service Power BI**. Par conséquent, les premières versions des sources de données en cours de création sont souvent marquées de la mention *Bêta* ou *Préversion*. Une source de données marquée de la mention *Bêta* ou *Préversion* a un support et des fonctionnalités limités et ne doit pas être utilisée dans les environnements de production.
> 
> 

## <a name="data-sources"></a>Sources de données
Les types de données sont organisés dans les catégories suivantes :

* Toutes
* Fichier
* Base de données
* Azure
* Online Services
* Autre

La catégorie **Toutes** comprend tous les types de connexion de données de toutes les catégories.

La catégorie **Fichier** fournit les connexions de données suivantes :

* Excel
* Texte/CSV
* XML
* JSON
* Dossier
* Dossier SharePoint

L’image suivante montre la fenêtre **Obtenir les données** pour **Fichier**.

![](media/desktop-data-sources/data-sources_3.png)

> [!NOTE]
> Dans les versions précédentes de Power BI Desktop, **CSV** et **Texte** étaient des types de connexion de données distincts. Ils sont maintenant regroupés en type **CSV/texte**.
> 
> 

La catégorie **Base de données** fournit les connexions de données suivantes :

* Base de données SQL Server
* Base de données Access
* Base de données SQL Server Analysis Services
* Base de données Oracle
* Base de données IBM DB2
* Base de données Informix IBM (bêta)
* IBM Netezza (bêta)
* Base de données MySQL
* Base de données PostgreSQL
* Base de données Sybase
* Base de données Teradata
* Base de données SAP HANA
* Serveur SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery (bêta)
* Snowflake

> [!NOTE]
> Certains connecteurs de base de données doivent être activés. Pour cela, sélectionnez **Fichier > Options et paramètres > Options**, puis sélectionnez **Fonctionnalités en version préliminaire** et activez le connecteur. Si vous ne voyez pas certains des connecteurs mentionnés ci-dessus et que vous souhaitez les utiliser, vérifiez les paramètres **Fonctions en version préliminaire**. Notez également qu’une source de données marquée de la mention *Bêta* ou *Préversion* a un support et des fonctionnalités limités et ne doit pas être utilisée dans les environnements de production.
> 
> 

L’image suivante montre la fenêtre **Obtenir les données** pour **Base de données**.

![](media/desktop-data-sources/data-sources_4.png)

La catégorie **Azure** fournit les connexions de données suivantes :

* Azure SQL Database
* Azure SQL Data Warehouse
* Base de données Azure Analysis Services (bêta)
* Stockage Blob Azure
* Stockage Table Azure
* Azure Cosmos DB (bêta)
* Azure Data Lake Store
* Azure HDInsight (HDFS)
* Azure HDInsight Spark (bêta)

L’image suivante montre la fenêtre **Obtenir les données** pour **Azure**.

![](media/desktop-data-sources/data-sources_5.png)

La catégorie **Services en ligne** fournit les connexions de données suivantes :

* Service Power BI
* Liste SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (en ligne)
* Dynamics 365 for Financials (bêta)
* Common Data Service (bêta)
* Microsoft Azure Consumption Insights (bêta)
* Visual Studio Team Services (version bêta)
* Objets Salesforce
* Rapports Salesforce
* Google Analytics
* appFigures (bêta)
* comScore Digital Analytix (bêta)
* Dynamics 365 pour Insights client (bêta)
* Facebook
* GitHub (bêta)
* Kusto (bêta)
* MailChimp (bêta)
* Mixpanel (bêta)
* Planview Enterprise (bêta)
* Projectplace (bêta)
* QuickBooks Online (bêta)
* Smartsheet
* SparkPost (bêta)
* SQL Sentry (bêta)
* Stripe (bêta)
* SweetIQ (bêta)
* Troux (bêta)
* Twilio (bêta)
* tyGraph (bêta)
* Webtrends (bêta)
* Zendesk (bêta)

L’illustration suivante montre la fenêtre **Obtenir les données** pour **Services en ligne**

![](media/desktop-data-sources/data-sources_6b.png)

La catégorie **Autre** fournit les connexions de données suivantes :

* Vertica (bêta)
* Web
* Liste SharePoint
* Flux OData
* Active Directory
* Microsoft Exchange
* Fichier Hadoop (HDFS)
* Spark (bêta)
* Script R
* ODBC
* OLE DB
* Requête vide

L’image suivante montre la fenêtre **Obtenir les données** pour **Autre**.

![](media/desktop-data-sources/data-sources_7a.png)

> [!NOTE]
> À ce stade, il n’est pas possible de se connecter aux sources de données personnalisées sécurisées à l’aide d’Azure Active Directory.
> 
> 

## <a name="connecting-to-a-data-source"></a>Connexion à une source de données
Pour vous connecter à une source de données, sélectionnez la source de données dans la fenêtre **Obtenir les données** et sélectionnez **Se connecter**. Dans l’image suivante, l’option **Web** est sélectionnée dans la catégorie de connexions de données **Autre**.

![](media/desktop-data-sources/data-sources_7b.png)

Une fenêtre de connexion s’affiche, spécifique au type de connexion de données. Si des informations d’identification sont requises, vous êtes invité à les fournir. L’image suivante montre la saisie d’une URL pour établir une connexion à une source de données web.

![](media/desktop-data-sources/datasources_fromwebbox.png)

Une fois l’URL ou les informations de connexion à la ressource entrées, sélectionnez **OK**. Power BI Desktop établit la connexion à la source de données et présente les sources de données disponibles dans le **Navigateur**.

![](media/desktop-data-sources/datasources_fromnavigatordialog.png)

Vous pouvez charger les données en sélectionnant le bouton **Charger** situé en bas du volet **Navigateur**, ou modifier la requête avant de charger les données en sélectionnant le bouton **Modifier**.

C’est là tout ce qu’il faut savoir pour se connecter à des sources de données dans Power BI Designer ! Essayez de vous connecter à des données à partir de notre liste grandissante de sources de données et consultez-la régulièrement : nous continuons de l’enrichir en permanence.

## <a name="next-steps"></a>Étapes suivantes
Power BI Desktop vous permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Types de données dans Power BI Desktop](desktop-data-types.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)    

