---
title: Sources de données Power BI
description: Cet article liste les sources de données qui sont prises en charge par Power BI, y compris des informations sur DirectQuery et sur la passerelle de données locale.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2020
ms.author: davidi
ms.openlocfilehash: 0bc6b844457f625d0287f2ec85f582a6ea874624
ms.sourcegitcommit: 6d3a37eb636e1b71c7dcb9d1c3a9e495b78dec97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681856"
---
# <a name="power-bi-data-sources"></a>Sources de données Power BI

Le tableau suivant montre les sources de données qui sont prises en charge par Power BI pour les jeux de données, y compris des informations sur DirectQuery et sur la passerelle de données locale. Pour plus d'informations sur les dataflows, voir [Se connecter à des sources de données pour les dataflows Power BI](../transform-model/service-dataflows-data-sources.md).

> [!NOTE]
> Bon nombre de connecteurs de données pour Power BI Desktop ont besoin d’Internet Explorer 10 (ou une version plus récente) pour l’authentification. 


| Paramètres | Connexion à partir de Desktop | Connexion et actualisation à partir du service | DirectQuery/Connexions actives | Passerelle (prise en charge) | Passerelle (obligatoire) |
|---|---|---|---|---|---|---|---|
| Base de données Access | Oui | Oui | Non | Oui <sup>1</sup> | Oui |
| ActiveDirectory | Oui | Oui | Non | Oui | Oui |
| Adobe Analytics | Oui | Oui | Non | Non | Non |
| Amazon Redshift | Oui | Oui | Oui | Oui | Non |
| appFigures | Oui | Oui | Non | Non | Non |
| Cubes AtScale | Oui | Oui | Oui | Oui | Non |
| Azure Analysis Services | Oui | Oui | Oui | Non | Non |
| Stockage Blob Azure | Oui | Oui | Non | Oui | Non |
| Azure Cosmos DB | Oui | Oui | Non | Non | Non |
| Azure Cost Management | Oui | Oui | Non | Non | Non |
| Azure Data Explorer (Kusto) | Oui | Oui | Oui | Non | Non |
| Azure Data Lake Storage Gen1 | Oui | Oui | Non | Non | Non |
| Azure Data Lake Storage Gen2 | Oui | Oui | Non | Oui | Non |
| Azure DevOps | Oui | Oui | Non | Non | Non |
| Azure DevOps Server | Oui | Oui | Non | Oui | Oui |
| Azure HDInsight (HDFS) | Oui | Oui | Non | Non | Non |
| Azure HDInsight Spark | Oui | Oui | Oui | Non | Non |
| Azure SQL Database | Oui | Oui | Oui | Oui <sup>2</sup> | Non |
| Azure SQL Data Warehouse | Oui | Oui | Oui | Oui <sup>2</sup> | Non |
| Stockage Table Azure | Oui | Oui | Non | Oui | Non |
| Connecteur BI | Oui | Oui | Oui | Oui | Oui |
| BI360 - Budgets & Rapports financiers | Oui | Oui | Non | Non | Non |
| Common Data Service | Oui | Oui | Non | Non | Non |
| Data.World - Obtenir le jeu de données | Oui | Oui | Non | Non | Non |
| Denodo | Oui | Oui | Oui | Oui | Oui |
| Dremio | Oui | Oui | Oui | Oui | Oui |
| Dynamics 365 (Online) | Oui | Oui | Non | Non | Non |
| Dynamics 365 Business Central | Oui | Oui | Non | Non | Non |
| Dynamics 365 Business Central (local) | Oui | Oui | Non | Non | Non |
| Dynamics 365 Customer Insights | Oui | Oui | Non | Non | Non |
| Dynamics NAV | Oui | Oui | Non | Non | Non |
| Emigo Data Source | Oui | Oui | Non | Non | Non |
| Entersoft Business Suite | Oui | Oui | Non | Non | Non |
| Essbase | Oui | Oui | Oui | Oui | Oui |
| Exasol | Oui | Oui | Oui | Oui | Oui |
| Excel | Oui <sup>3</sup> | Oui <sup>3</sup> | Non | Oui <sup>3</sup> | Non <sup>4</sup> |
| Facebook | Oui | Oui | Non | Non | Non |
| Fichier | Oui | Oui | Non | Oui | Oui |
| Dossier | Oui | Oui | Non | Oui | Oui |
| GitHub | Oui | Oui | Non | Non | Non |
| Google Analytics | Oui | Oui | Non | Non | Non |
| Google BigQuery | Oui | Oui | Oui | Non | Non |
| Fichier Hadoop (HDFS) | Oui | Non | Non | Non | Non |
| HDInsight Interactive Query | Oui | Oui | Oui | Non | Non |
| IBM DB2 | Oui | Oui | Oui | Oui | Non |
| Base de données Informix IBM | Oui | Oui | Non | Oui | Non |
| IBM Netezza | Oui | Oui | Oui | Oui | Oui |
| Impala | Oui | Oui | Oui | Oui | Oui |
| Indexima | Oui | Oui | Oui | Oui | Oui |
| Industrial App Store | Oui | Oui | Non | Non | Non |
| Information Grid | Oui | Oui | Non | Non | Non |
| InterSystems IRIS | Oui | Oui | Oui | Oui | Oui |
| Entrepôt de données Intune | Oui | Oui | Non | Non | Non |
| Jethro ODBC | Oui | Oui | Oui | Oui | Oui |
| JSON | Oui | Oui | Non | Oui** | Non <sup>4</sup> |
| Kyligence Enterprise | Oui | Oui | Oui | Oui | Oui |
| MailChimp | Oui | Oui | Non | Non | Non |
| Marketo | Oui | Oui | Non | Non | Non |
| MarkLogic ODBC | Oui | Oui | Oui | Oui | Oui |
| Microsoft Azure Consumption Insights | Oui | Oui | Non | Non | Non |
| Microsoft Exchange | Oui | Oui | Non | Oui | Non |
| Microsoft Exchange Online | Oui | Oui | Non | Non | Non |
| Microsoft Graph Security | Oui | Oui | Non | Oui | Non |
| Mixpanel | Oui | Oui | Non | Non | Non |
| MySQL | Oui | Oui | Non | Oui | Oui |
| OData | Oui | Oui <sup>7</sup> | Non | Oui | Non |
| ODBC | Oui | Oui | Non | Oui | Oui |
| OleDb | Oui | Oui | Non | Oui | Oui |
| Oracle | Oui | Oui | Oui | Oui | Oui |
| Paxata | Oui | Oui | Non | Oui | Non |
| PDF | Oui | Oui | Non | Oui | Non <sup>4</sup> |
| Planview Enterprise One - CTM | Oui | Oui | Non | Non | Non |
| Planview Enterprise One - PRM | Oui | Oui | Non | Non | Non |
| Planview Projectplace | Oui | Oui | Non | Non | Non |
| PostgreSQL | Oui | Oui | Oui | Oui | Non |
| Dataflows Power BI | Oui | Oui | Non | Non | Non |
| Jeux de données Power BI | Oui | Oui | Oui | Non | Non |
| Dataflows Power Platform | Oui | Oui | Non | Non | Non |
| Script Python | Oui | Oui <sup>5</sup> | Non | Oui <sup>5</sup> | Oui |
| QubolePresto | Oui | Oui | Oui | Oui | Oui |
| Quick Base | Oui | Oui | Non | Oui | Oui |
| QuickBooks Online | Oui | Oui | Non | Non | Non |
| Script R | Oui | Oui <sup>5</sup> | Non | Oui <sup>5</sup> | Non |
| Roamler | Oui | Oui | Non | Oui | Non |
| Objets Salesforce | Oui | Oui | Non | Non | Non |
| Rapports Salesforce | Oui | Oui | Non | Non | Non |
| Serveur de messages SAP Business Warehouse | Oui | Oui | Oui | Oui | Oui |
| Serveur SAP Business Warehouse | Oui | Oui | Oui | Oui | Oui |
| SAP HANA | Oui | Oui | Oui | Oui | Oui |
| Dossier SharePoint | Oui | Oui | Non | Oui | Non <sup>4</sup> |
| Liste SharePoint | Oui | Oui | Non | Oui | Non <sup>4</sup> |
| Liste SharePoint Online | Oui | Oui | Non | Oui <sup>2</sup> | Non |
| Smartsheet | Oui | Oui | Non | Non | Non |
| Snowflake | Oui | Oui | Oui | Oui | Non |
| Spark | Oui | Oui | Oui | Oui | Non |
| SparkPost | Oui | Oui | Non | Non | Non |
| SQL Server | Oui | Oui | Oui | Oui | Oui |
| SQL Server Analysis Services | Oui | Oui | Oui | Oui | Oui |
| Stripe | Oui | Oui | Non | Non | Non |
| SurveyMonkey | Oui | Oui | Non | Oui | Non |
| SweetIQ | Oui | Oui | Non | Non | Non |
| Sybase | Oui | Oui | Non | Oui | Oui |
| TeamDesk | Oui | Oui | Non | Oui | Non |
| Tenforce | Oui | Oui | Non | Non | Non |
| Teradata | Oui | Oui | Oui | Oui | Oui |
| Texte/CSV | Oui | Oui | Non | Oui | Non <sup>4</sup> |
| Twilio | Oui | Oui | Non | Non | Non |
| tyGraph | Oui | Oui | Non | Non | Non |
| Vertica | Oui | Oui | Oui | Oui | Oui |
| Web | Oui | Oui | Non | Oui | Oui <sup>6</sup> |
| Webtrends | Oui | Oui | Non | Non | Non |
| Workforce Dimensions | Oui | Oui | Non | Oui | Non |
| XML | Oui | Oui | Non | Oui | Non <sup>4</sup> |
| Zendesk | Oui | Oui | Non | Non | Non |
| | | | | | | | |

<sup>1</sup> Pris en charge par le [fournisseur OLEDB ACE](https://www.microsoft.com/download/details.aspx?id=54920) installé sur le même ordinateur que la passerelle.

<sup>2</sup> Pris en charge avec la même fonction M que la version locale, ce qui entraîne des options d’authentification restreinte (la passerelle ne prend pas en charge OAuth).

<sup>3</sup> Les fichiers Excel 1997-2003 (.xls) exigent le [fournisseur OLEDB ACE](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Obligatoire pour la version locale de l’outil.

<sup>5</sup> Pris en charge uniquement avec la [passerelle personnelle](service-gateway-personal-mode.md).

<sup>6</sup> Requis pour les bases de données Access, .html et .xls

<sup>7</sup> Le service Power BI ne prend pas en charge les flux OData qui requièrent une authentification.

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
