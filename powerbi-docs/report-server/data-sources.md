---
title: Sources de données de rapport Power BI dans Power BI Report Server
description: Les rapports Power BI (.pbix) peuvent se connecter à plusieurs sources de données. Selon la façon dont les données sont utilisées, différentes sources de données sont disponibles.
services: powerbi
documentationcenter: ''
author: markingmyname
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/23/2018
ms.author: maghan
ms.openlocfilehash: a32ef2e1e85b252a2a1071cb95c80149486c2604
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="power-bi-report-pbix-data-sources-in-power-bi-report-server"></a>Sources de données de rapport Power BI (.pbix) dans Power BI Report Server
Les rapports Power BI peuvent se connecter à plusieurs sources de données. Selon la façon dont les données sont utilisées, différentes sources de données sont disponibles. Des données peuvent être importées ou interrogées directement à l’aide de DirectQuery ou d’une connexion active à SQL Server Analysis Services.

Ces sources de données sont spécifiques des rapports Power BI utilisés dans Power BI Report Server. Pour plus d’informations sur les sources de données prises en charge avec des rapports paginés (.rdl), consultez [Sources de données prises en charge par Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Toutes les sources de données dans un rapport Power BI Desktop doivent prendre en charge la configuration de l’actualisation planifiée.
>  

## <a name="list-of-supported-data-sources"></a>Liste des sources de données prises en charge

D’autres sources de données non répertoriées sur la liste peuvent également fonctionner.

| **Source de données** | **Données mises en cache** | **Actualisation planifiée** | **Active/DirectQuery** |
| --- | --- | --- | --- |
| Base de données SQL Server |Oui |Oui |Oui |
| SQL Server Analysis Services |Oui |Oui |Oui |
| Azure SQL Database |Oui |Oui |Oui |
| Azure SQL Data Warehouse |Oui |Oui |Oui |
| Excel |Oui |Oui |Non |
| Base de données Access |Oui |Oui |Non |
| Active Directory |Oui |Oui |Non |
| Amazon Redshift |Oui |Non |Non |
| Stockage Blob Azure |Oui |Oui |Non |
| Azure Data Lake Store |Oui |Non |Non |
| Azure HDInsight (HDFS) |Oui |Non |Non |
| Azure HDInsight (Spark) |Oui |Oui |Non |
| Stockage Table Azure |Oui |Oui |Non |
| Dynamics 365 (en ligne) |Oui |Non |Non |
| Facebook |Oui |Non |Non |
| Dossier |Oui |Oui |Non |
| Google Analytics |Oui |Non |Non |
| Fichier Hadoop (HDFS) |Oui |Non |Non |
| Base de données IBM DB2 |Oui |Oui |Non |
| Impala |Oui |Non |Non |
| JSON |Oui |Oui |Non |
| Microsoft Exchange |Oui |Non |Non |
| Microsoft Exchange Online |Oui |Non |Non |
| Base de données MySQL |Oui |Oui |Non |
| Flux OData |Oui |Oui |Non |
| ODBC |Oui |Oui |Non |
| OLE DB |Oui |Oui |Non |
| Base de données Oracle |Oui |Oui |Oui |
| Base de données PostgreSQL |Oui |Oui |Non |
| Service Power BI |Non |Non |Non |
| Script R |Oui |Non |Non |
| Objets Salesforce |Oui |Non |Non |
| Rapports Salesforce |Oui |Non |Non |
| Serveur SAP Business Warehouse |Oui |Oui |Oui |
| Base de données SAP HANA |Oui |Oui |Oui |
| Dossier SharePoint (local) |Oui |Oui |Non |
| Liste SharePoint (local) |Oui |Oui |Non |
| Liste SharePoint Online |Oui |Non |Non |
| Snowflake |Oui |Non |Non |
| Base de données Sybase |Oui |Oui |Non |
| Base de données Teradata |Oui |Oui |Oui |
| Texte/CSV |Oui |Oui |Non |
| Web |Oui |Oui |Non |
| XML |Oui |Oui |Non |
| appFigures (bêta) |Oui |Non |Non |
| Base de données Azure Analysis Services |Oui |Non |Oui |
| Azure Cosmos DB (bêta) |Oui |Non |Non |
| Azure HDInsight Spark (bêta) |Oui |Non |Non |
| Common Data Service (bêta) |Oui |Non |Non |
| comScore Digital Analytix (bêta) |Oui |Non |Non |
| Dynamics 365 pour Insights client (bêta) |Oui |Non |Non |
| Dynamics 365 for Financials (bêta) |Oui |Non |Non |
| GitHub (bêta) |Oui |Non |Non |
| Google BigQuery (bêta) |Oui |Non |Non |
| Base de données Informix IBM (bêta) |Oui |Non |Non |
| IBM Netezza (bêta) |Oui |Non |Non |
| Kusto (bêta) |Oui |Non |Non |
| MailChimp (bêta) |Oui |Non |Non |
| Microsoft Azure Consumption Insights (bêta) |Oui |Non |Non |
| Mixpanel (bêta) |Oui |Non |Non |
| Planview Enterprise (bêta) |Oui |Non |Non |
| Projectplace (bêta) |Oui |Non |Non |
| QuickBooks Online (bêta) |Oui |Non |Non |
| Smartsheet |Oui |Non |Non |
| Spark (bêta) |Oui |Non |Non |
| SparkPost (bêta) |Oui |Non |Non |
| SQL Sentry (bêta) |Oui |Non |Non |
| Stripe (bêta) |Oui |Non |Non |
| SweetIQ (bêta) |Oui |Non |Non |
| Troux (bêta) |Oui |Non |Non |
| Twilio (bêta) |Oui |Non |Non |
| tyGraph (bêta) |Oui |Non |Non |
| Vertica (bêta) |Oui |Non |Non |
| Visual Studio Team Services (version bêta) |Oui |Non |Non |
| Webtrends (bêta) |Oui |Non |Non |
| Zendesk (bêta) |Oui |Non |Non |

> [!IMPORTANT]
> La sécurité au niveau des lignes configurée pour la source de données doit fonctionner pour certaines des connexions actives DirectQuery (SQL Server, Azure SQL Database, Oracle et Teradata) en supposant que Kerberos est correctement configuré dans votre environnement.
> 
> 

## <a name="list-of-supported-authentication-methods-for-model-refresh"></a>Liste des méthodes d’authentification prises en charge pour l’actualisation de modèle

Power BI Report Server ne prend pas en charge l’authentification OAuth pour l’actualisation de modèle. Certaines sources de données comme les bases de données Excel ou Access utilisent une étape distincte (p.ex., Fichier ou Web) pour se connecter aux données.

| **Source de données** | **Authentification anonyme** | **Authentification par clé** | **Nom d’utilisateur et mot de passe** | **Authentification Windows** |
| --- | --- | --- | --- | --- |
| Base de données SQL Server |Non |Non |Oui |Oui |
| SQL Server Analysis Services |Non |Non |Oui |Oui |
| Web |Oui |Non |Oui |Oui |
| Azure SQL Database |Non |Non |Oui |Non |
| Azure SQL Data Warehouse |Non |Non |Oui |Non |
| Active Directory |Non |Non |Oui |Oui |
| Amazon Redshift |Non |Non |Non |Non |
| Stockage Blob Azure |Oui |Oui |Non |Non |
| Azure Data Lake Store |Non |Non |Non |Non |
| Azure HDInsight (HDFS) |Non |Non |Non |Non |
| Azure HDInsight (Spark) |Oui |Oui |Non |Non |
| Stockage Table Azure |Non |Oui |Non |Non |
| Dynamics 365 (en ligne) |Non |Non |Non |Non |
| Facebook |Non |Non |Non |Non |
| Dossier |Non |Non |Non |Oui |
| Google Analytics |Non |Non |Non |Non |
| Fichier Hadoop (HDFS) |Non |Non |Non |Non |
| Base de données IBM DB2 |Non |Non |Oui |Oui |
| Impala |Non |Non |Non |Non |
| Microsoft Exchange |Non |Non |Non |Non |
| Microsoft Exchange Online |Non |Non |Non |Non |
| Base de données MySQL |Non |Non |Oui |Oui |
| Flux OData |Oui |Oui |Oui |Oui |
| ODBC |Oui |Non |Oui |Oui |
| OLE DB |Oui |Non |Oui |Oui |
| Base de données Oracle |Non |Non |Oui |Oui |
| Base de données PostgreSQL |Non |Non |Oui |Non |
| Service Power BI |Non |Non |Non |Non |
| Script R |Non |Non |Non |Non |
| Objets Salesforce |Non |Non |Non |Non |
| Rapports Salesforce |Non |Non |Non |Non |
| Serveur SAP Business Warehouse |Non |Non |Oui |Non |
| Base de données SAP HANA |Non |Non |Oui |Oui |
| Dossier SharePoint (local) |Oui |Non |Non |Oui |
| Liste SharePoint (local) |Oui |Non |Non |Oui |
| Liste SharePoint Online |Non |Non |Non |Non |
| Snowflake |Non |Non |Non |Non |
| Base de données Sybase |Non |Non |Oui |Oui |
| Base de données Teradata |Non |Non |Oui |Oui |
| appFigures (bêta) |Non |Non |Non |Non |
| Base de données Azure Analysis Services (bêta) |Non |Non |Non |Non |
| Azure Cosmos DB (bêta) |Non |Non |Non |Non |
| Azure HDInsight Spark (bêta) |Non |Non |Non |Non |
| Common Data Service (bêta) |Non |Non |Non |Non |
| comScore Digital Analytix (bêta) |Non |Non |Non |Non |
| Dynamics 365 pour Insights client (bêta) |Non |Non |Non |Non |
| Dynamics 365 for Financials (bêta) |Non |Non |Non |Non |
| GitHub (bêta) |Non |Non |Non |Non |
| Google BigQuery (bêta) |Non |Non |Non |Non |
| Base de données Informix IBM (bêta) |Non |Non |Non |Non |
| IBM Netezza (bêta) |Non |Non |Non |Non |
| Kusto (bêta) |Non |Non |Non |Non |
| MailChimp (bêta) |Non |Non |Non |Non |
| Microsoft Azure Consumption Insights (bêta) |Non |Non |Non |Non |
| Mixpanel (bêta) |Non |Non |Non |Non |
| Planview Enterprise (bêta) |Non |Non |Non |Non |
| Projectplace (bêta) |Non |Non |Non |Non |
| QuickBooks Online (bêta) |Non |Non |Non |Non |
| Smartsheet |Non |Non |Non |Non |
| Spark (bêta) |Non |Non |Non |Non |
| SparkPost (bêta) |Non |Non |Non |Non |
| SQL Sentry (bêta) |Non |Non |Non |Non |
| Stripe (bêta) |Non |Non |Non |Non |
| SweetIQ (bêta) |Non |Non |Non |Non |
| Troux (bêta) |Non |Non |Non |Non |
| Twilio (bêta) |Non |Non |Non |Non |
| tyGraph (bêta) |Non |Non |Non |Non |
| Vertica (bêta) |Non |Non |Non |Non |
| Visual Studio Team Services (version bêta) |Non |Non |Non |Non |
| Webtrends (bêta) |Non |Non |Non |Non |
| Zendesk (bêta) |Non |Non |Non |Non |

## <a name="list-of-supported-authentication-methods-for-directquery"></a>Liste des méthodes d’authentification prises en charge pour DirectQuery

Power BI Report Server ne prend pas en charge l’authentification OAuth pour DirectQuery.

| **Source de données** | **Authentification anonyme** | **Authentification par clé** | **Nom d’utilisateur et mot de passe** | **Authentification Windows** | **Authentification Windows intégrée** |
| --- | --- | --- | --- | --- | --- |
| Base de données SQL Server |Non |Non |Oui |Oui |Oui |
| SQL Server Analysis Services |Non |Non |Oui |Oui |Oui |
| Azure SQL Database |Non |Non |Oui |Non |Non |
| Azure SQL Data Warehouse |Non |Non |Oui |Non |Non |
| Base de données Oracle |Non |Non |Oui |Oui |Oui |
| Serveur SAP Business Warehouse |Non |Non |Oui |Non |Oui |
| Base de données SAP HANA |Non |Non |Oui |Oui |Non |
| Base de données Teradata |Non |Non |Oui |Oui |Oui |


## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous êtes connecté à votre source de données, [créez un rapport Power BI](quickstart-create-powerbi-report.md) à l’aide des données de cette source de données.

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

