---
title: "Sources de données de rapport Power BI dans Power BI Report Server"
description: "Les rapports Power BI peuvent se connecter à différentes sources de données. Selon la façon dont les données sont utilisées, différentes sources de données sont disponibles."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: caa45aab2c31974abb041a82eb2216ebee2eb148
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Sources de données de rapport Power BI dans Power BI Report Server
Les rapports Power BI peuvent se connecter à différentes sources de données. Selon la façon dont les données sont utilisées, différentes sources de données sont disponibles. Des données peuvent être importées ou interrogées directement à l’aide de DirectQuery ou d’une connexion active à SQL Server Analysis Services.

Ces sources de données sont spécifiques des rapports Power BI utilisés dans Power BI Report Server. Pour plus d’informations sur les sources de données prises en charge avec des rapports paginés, voir [Sources de données prises en charge par Reporting Services (SSRS)](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

> [!IMPORTANT]
> Pour pouvoir configurer une actualisation planifiée, toutes les sources de données dans un rapport Power BI Desktop doivent être prises en charge.
> 
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
| Azure HDInsight (HDFS) |Oui |Oui |Non |
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
| Base de données Azure Analysis Services (bêta) |Oui |Non |Non |
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

## <a name="next-steps"></a>Étapes suivantes
Maintenant que votre source de données est sélectionnée, [créez un rapport](quickstart-create-powerbi-report.md) à l’aide des données à partir de cette source.

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

