---
title: Sources de données Power BI
description: Cet article liste les sources de données qui sont prises en charge par Power BI, y compris des informations sur DirectQuery et sur la passerelle de données locale.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/07/2020
ms.author: davidi
ms.openlocfilehash: ae6047950256a783172ef871c2bd58dc15ff033a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297597"
---
# <a name="power-bi-data-sources"></a>Sources de données Power BI

Le tableau suivant montre les sources de données qui sont prises en charge par Power BI pour les jeux de données, y compris des informations sur DirectQuery et sur la passerelle de données locale. Pour plus d'informations sur les dataflows, voir [Se connecter à des sources de données pour les dataflows Power BI](../transform-model/service-dataflows-data-sources.md).

| Paramètres | Connexion à partir de Desktop | Connexion et actualisation à partir du service | DirectQuery/Connexions actives | Passerelle (prise en charge) | Passerelle (obligatoire) | Dataflows Power BI |
|---|---|---|---|---|---|---|---|
| Base de données Access | Oui | Oui | Non | Oui <sup>1</sup> | Oui | Oui |
| ActiveDirectory | Oui | Oui | Non | Oui | Oui | Oui |
| Adobe Analytics | Oui | Oui | Non | Non | Non | Non |
| Amazon Redshift | Oui | Oui | Oui | Oui | Non | Oui |
| appFigures | Oui | Oui | Non | Non | Non | Non |
| Cubes AtScale | Oui | Oui | Oui | Oui | Non | Non |
| Azure Analysis Services | Oui | Oui | Oui | Non | Non | Non |
| Stockage Blob Azure | Oui | Oui | Non | Oui | Non | Oui |
| Azure Cosmos DB | Oui | Oui | Non | Non | Non | Non |
| Azure Cost Management | Oui | Oui | Non | Non | Non | Non |
| Azure Data Explorer (Kusto) | Oui | Oui | Oui | Oui | Non | Oui |
| Azure Data Lake Storage Gen1 | Oui | Oui | Non | Non | Non | Non |
| Azure Data Lake Storage Gen2 | Oui | Oui | Non | Oui | Non | Oui |
| Azure DevOps | Oui | Oui | Non | Non | Non | Non |
| Azure DevOps Server | Oui | Oui | Non | Oui | Oui | Non |
| Azure HDInsight (HDFS) | Oui | Oui | Non | Non | Non | Non |
| Azure HDInsight Spark | Oui | Oui | Oui | Non | Non | Oui |
| Azure SQL Database | Oui | Oui | Oui | Oui | Non | Oui |
| Azure SQL Data Warehouse | Oui | Oui | Oui | Oui | Non | Oui |
| Stockage de table Azure | Oui | Oui | Non | Oui | Non | Oui |
| Connecteur BI | Oui | Oui | Oui | Oui | Oui | Non |
| BI360 - Budgets & Rapports financiers | Oui | Oui | Non | Non | Non | Non |
| Common Data Service | Oui | Oui | Non | Non | Non | Oui |
| Data.World - Obtenir le jeu de données | Oui | Oui | Non | Non | Non | Non |
| Denodo | Oui | Oui | Oui | Oui | Oui | Non |
| Dremio | Oui | Oui | Oui | Oui | Oui | Non |
| Dynamics 365 (Online) | Oui | Oui | Non | Non | Non | Non |
| Dynamics 365 Business Central | Oui | Oui | Non | Non | Non | Non |
| Dynamics 365 Business Central (local) | Oui | Oui | Non | Non | Non | Non |
| Dynamics 365 Customer Insights | Oui | Oui | Non | Non | Non | Non |
| Dynamics NAV | Oui | Oui | Non | Non | Non | Non |
| Emigo Data Source | Oui | Oui | Non | Non | Non | Non |
| Entersoft Business Suite | Oui | Oui | Non | Non | Non | Non |
| Essbase | Oui | Oui | Oui | Oui | Oui | Non |
| Exasol | Oui | Oui | Oui | Oui | Oui | Non |
| Excel | Oui <sup>3</sup> | Oui <sup>3</sup> | Non | Oui <sup>3</sup> | Non <sup>4</sup> | Oui |
| Facebook | Oui | Oui | Non | Non | Non | Non |
| Fichier | Oui | Oui | Non | Oui | Oui | Oui |
| Dossier | Oui | Oui | Non | Oui | Oui | Oui |
| GitHub | Oui | Oui | Non | Non | Non | Non |
| Google Analytics | Oui | Oui | Non | Non | Non | Non |
| Google BigQuery | Oui | Oui | Oui | Non | Non | Oui |
| Fichier Hadoop (HDFS) | Oui | Non | Non | Non | Non | Non |
| LLAP Hive | Oui | Oui | Oui | Oui | Non | Non |
| HDInsight Interactive Query | Oui | Oui | Oui | Non | Non | Non |
| IBM DB2 | Oui | Oui | Oui | Oui | Non | Oui |
| Base de données Informix IBM | Oui | Oui | Non | Oui | Non | Non |
| IBM Netezza | Oui | Oui | Oui | Oui | Oui | Non |
| Impala | Oui | Oui | Oui | Oui | Oui | Oui |
| Indexima | Oui | Oui | Oui | Oui | Oui | Non |
| Industrial App Store | Oui | Oui | Non | Non | Non | Non |
| Information Grid | Oui | Oui | Non | Non | Non | Non |
| InterSystems IRIS | Oui | Oui | Oui | Oui | Oui | Non |
| Entrepôt de données Intune | Oui | Oui | Non | Non | Non | Non |
| Jethro ODBC | Oui | Oui | Oui | Oui | Oui | Non |
| JSON | Oui | Oui | Non | Oui** | Non <sup>4</sup> | Oui |
| Kyligence Enterprise | Oui | Oui | Oui | Oui | Oui | Non |
| MailChimp | Oui | Oui | Non | Non | Non | Non |
| Marketo | Oui | Oui | Non | Non | Non | Non |
| MarkLogic ODBC | Oui | Oui | Oui | Oui | Oui | Non |
| Microsoft Azure Consumption Insights | Oui | Oui | Non | Non | Non | Non |
| Microsoft Exchange | Oui | Oui | Non | Oui | Non | Non |
| Microsoft Exchange Online | Oui | Oui | Non | Non | Non | Oui |
| Microsoft Graph Security | Oui | Oui | Non | Oui | Non | Non |
| Mixpanel | Oui | Oui | Non | Non | Non | Non |
| MySQL | Oui | Oui | Non | Oui | Oui | Oui |
| OData | Oui | Oui <sup>7</sup> | Non | Oui | Non | Oui |
| ODBC | Oui | Oui | Non | Oui | Oui | Oui |
| OleDb | Oui | Oui | Non | Oui | Oui | Non |
| Oracle | Oui | Oui | Oui | Oui | Oui | Oui |
| Paxata <sup>8</sup> | Oui | Oui | Non | Oui | Non | Non |
| PDF | Oui | Oui | Non | Oui | Non <sup>4</sup> | Oui |
| Planview Enterprise One - CTM | Oui | Oui | Non | Non | Non | Non |
| Planview Enterprise One - PRM | Oui | Oui | Non | Non | Non | Non |
| Planview Projectplace | Oui | Oui | Non | Non | Non | Non |
| PostgreSQL | Oui | Oui | Oui | Oui | Non | Oui |
| Dataflows Power BI | Oui | Oui | Non | Non | Non | Oui |
| Jeux de données Power BI | Oui | Oui | Oui | Non | Non | Non |
| Dataflows Power Platform | Oui | Oui | Non | Non | Non | Oui |
| Script Python | Oui | Oui <sup>5</sup> | Non | Oui <sup>5</sup> | Oui | Non |
| QubolePresto | Oui | Oui | Oui | Oui | Oui | Non |
| Quick Base | Oui | Oui | Non | Oui | Oui | Non |
| QuickBooks Online | Oui | Oui | Non | Non | Non | Non |
| Script R | Oui | Oui <sup>5</sup> | Non | Oui <sup>5</sup> | Non | Non |
| Roamler | Oui | Oui | Non | Oui | Non | Non |
| Objets Salesforce | Oui | Oui | Non | Non | Non | Oui |
| Rapports Salesforce | Oui | Oui | Non | Non | Non | Oui |
| Serveur de messages SAP Business Warehouse | Oui | Oui | Oui | Oui | Oui | Oui |
| Serveur SAP Business Warehouse | Oui | Oui | Oui | Oui | Oui | Oui |
| SAP HANA | Oui | Oui | Oui | Oui | Oui | Oui |
| Dossier SharePoint | Oui | Oui | Non | Oui | Non <sup>4</sup> | Oui |
| Liste SharePoint | Oui | Oui | Non | Oui | Non <sup>4</sup> | Oui |
| Liste SharePoint Online | Oui | Oui | Non | Oui | Non | Oui |
| Smartsheet | Oui | Oui | Non | Non | Non | Oui |
| Snowflake | Oui | Oui | Oui | Oui | Non | Oui |
| Spark | Oui | Oui | Oui | Oui | Non | Oui |
| SparkPost | Oui | Oui | Non | Non | Non | Non |
| SQL Server | Oui | Oui | Oui | Oui | Oui | Oui |
| SQL Server Analysis Services | Oui | Oui | Oui | Oui | Oui | Non |
| Stripe | Oui | Oui | Non | Non | Non | Non |
| SurveyMonkey | Oui | Oui | Non | Oui | Non | Non |
| SweetIQ | Oui | Oui | Non | Non | Non | Non |
| Sybase | Oui | Oui | Non | Oui | Oui | Oui |
| TeamDesk | Oui | Oui | Non | Oui | Non | Non |
| Tenforce | Oui | Oui | Non | Non | Non | Non |
| Teradata | Oui | Oui | Oui | Oui | Oui | Oui |
| Texte/CSV | Oui | Oui | Non | Oui | Non <sup>4</sup> | Oui |
| Twilio | Oui | Oui | Non | Non | Non | Non |
| tyGraph | Oui | Oui | Non | Non | Non | Non |
| Vertica | Oui | Oui | Oui | Oui | Oui | Oui |
| Web | Oui | Oui | Non | Oui | Oui <sup>6</sup> | Oui |
| Webtrends | Oui | Oui | Non | Non | Non | Non |
| Workforce Dimensions | Oui | Oui | Non | Oui | Non | Non |
| XML | Oui | Oui | Non | Oui | Non <sup>4</sup> | Oui |
| Zendesk | Oui | Oui | Non | Non | Non | Non |
| | | | | | | | |

<sup>1</sup> Pris en charge par le [fournisseur OLEDB ACE](https://www.microsoft.com/download/details.aspx?id=54920) installé sur le même ordinateur que la passerelle.

<sup>3</sup> Les fichiers Excel 1997-2003 (.xls) exigent le [fournisseur OLEDB ACE](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Obligatoire pour la version locale de l’outil.

<sup>5</sup> Pris en charge uniquement avec la [passerelle personnelle](service-gateway-personal-mode.md).

<sup>6</sup> Requis pour les bases de données Access, .html et .xls

<sup>7</sup> Le service Power BI ne prend pas en charge les flux OData qui requièrent une authentification.

<sup>8</sup> Paxata est pris en charge dans la version de Power BI Desktop optimisée pour Power BI Report Server. Il n’est pas pris en charge dans les rapports Power Bi publiés sur le Power Bi Report Server. Pour obtenir une liste des sources de données prises en charge, consultez [Sources de données de rapports Power BI dans Power BI Report Server](../report-server/data-sources.md).

## <a name="considerations-and-limitations"></a>Considérations et limitations

- Beaucoup de connecteurs de données pour Power BI Desktop nécessitent Internet Explorer 10 (ou une version plus récente) pour l’authentification. 
- Certaines sources de données sont disponibles dans Power BI Desktop, optimisées pour Power BI Report Server, mais ne sont pas prises en charge lors de la publication dans Power BI Report Server. Pour obtenir une liste des sources de données prises en charge, consultez [Sources de données de rapports Power BI dans Power BI Report Server](../report-server/data-sources.md).

## <a name="single-sign-on-sso-for-directquery-sources"></a>Authentification unique (SSO) pour les sources DirectQuery

Quand l’option d’authentification unique est activée et que vos utilisateurs accèdent aux rapports basés sur la source de données, Power BI envoie leurs informations d’identification Azure AD dans les requêtes à la source de données sous-jacente. Ainsi, Power BI est en mesure de respecter les paramètres de sécurité qui sont configurés au niveau de la source de données.
L’option d’authentification unique prend effet sur tous les jeux de données qui utilisent cette source de données. Elle n’affecte pas la méthode d’authentification utilisée pour les scénarios d’importation. Les sources de données suivantes prennent en charge l’authentification unique pour les connexions via DirectQuery :

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Serveur de messages SAP BW
- Snowflake
- Spark
- SQL Server
- Teradata

> [!Note]
> L’authentification multifacteur Azure (MFA) n’est pas pris en charge. Les utilisateurs qui souhaitent utiliser l’authentification unique avec DirectQuery doivent être exemptés de l’authentification multifacteur (MFA).

## <a name="next-steps"></a>Étapes suivantes

[Se connecter aux données dans Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)  
[Données actives SQL Server Analysis Services dans Power BI](sql-server-analysis-services-tabular-data.md)  
[Qu’est-ce qu’une passerelle de données locale ?](service-gateway-onprem.md)  
[Sources de données de rapport Power BI dans Power BI Report Server](../report-server/data-sources.md)
