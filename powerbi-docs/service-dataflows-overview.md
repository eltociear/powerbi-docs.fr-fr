---
title: En savoir plus sur les flux de données dans Power BI
description: Découvrir comment les flux de données fonctionnent dans Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 360ffdd61525244bd75e57c8c9c9aad25131a13d
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51267237"
---
# <a name="self-service-data-prep-in-power-bi-preview"></a>Préparation des données en libre-service dans Power BI (préversion)

Au fur et à mesure que le volume de données continue d'augmenter, il devient de plus en plus difficile de transformer ces données en informations bien formées et exploitables. Nous voulons des données prêtes pour l'analyse, pour remplir des visuels, des rapports et des tableaux de bord, afin de pouvoir transformer rapidement nos volumes de données en informations exploitables. Avec **la préparation des données en libre-service** pour le Big Data dans Power BI, vous pouvez accéder à des insights de Power BI à partir de données en quelques clics seulement.

![Utiliser des flux de données dans Power BI](media/service-dataflows-overview/powerbi-dataflows_01.png)

Power BI présente les **flux de données** pour aider les organisations à unifier des données provenant de sources disparates et à les préparer pour la modélisation. Les analystes peuvent facilement créer des flux de données à l’aide des outils familiers en libre-service. Les flux de données sont utilisés pour ingérer, transformer, intégrer et enrichir du Big Data en définissant des connexions de source de données, une logique ETL, des planifications d’actualisation et bien plus encore. De plus, le nouveau moteur de calcul piloté par des modèles qui fait partie des flux de données rend le processus de préparation des données plus facile à gérer, plus déterministe et moins lourd pour les analystes de données comme pour les créateurs de rapports. Tout comme les feuilles de calcul gèrent les nouveaux calculs pour toutes les formules concernées, les flux de données gèrent les modifications d'une entité ou d'un élément de données en votre nom, automatisant les mises à jour et allégeant des contrôles logiques auparavant fastidieux et chronophages, même pour une actualisation des données de base. Grâce aux flux de données, des tâches qui devaient auparavant être supervisées par des scientifiques des données (et prenaient plusieurs heures ou jours) peuvent désormais être traitées en quelques clics par des analystes et des créateurs de rapports. 

Les données sont stockées en tant qu’entités dans [le **Common Data Model** ](https://docs.microsoft.com/powerapps/common-data-model/overview) dans Azure Data Lake Storage Gen2. Des flux de données sont créés et gérés dans des espaces de travail de l’application à l’aide du service Power BI.  

> [!NOTE]
> la fonctionnalité de flux de données étant en préversion, elle est susceptible de changer et d’être mise à jour avant la disponibilité générale.

 
Les **flux de données** sont conçus pour utiliser le **Common Data Model**, une collection standardisée, modulaire et extensible de schémas de données publiés par Microsoft pour vous faciliter la création, l’utilisation et l’analyse des données. Avec ce modèle, vous pouvez accéder aux tableaux de bord Power BI à partir de sources de données sans pratiquement aucune friction.

Vous pouvez utiliser des flux de données pour ingérer des données à partir d’un ensemble vaste et toujours croissant de prises en charge en local et de sources de données cloud, notamment Dynamics 365, Salesforce, Azure SQL Database et Excel, SharePoint, entre autres.

Vous pouvez alors mapper des données à des entités standard dans le Common Data Model, modifier et étendre des entités existantes et créer des entités personnalisées. Les utilisateurs avancés peuvent créer des flux de données entièrement personnalisés à l'aide d'une expérience de création de Power Query intégrée en libre-service, avec ou sans code, similaire à celle de Power Query que des millions d'utilisateurs de Power BI Desktop et d'Excel connaissent déjà.  

Une fois que vous avez créé un flux de données, vous pouvez utiliser Power BI Desktop et le service Power BI pour créer des jeux de données, des rapports, des tableaux de bord et des applications qui tirent parti de la puissance du Common Data Model pour obtenir des insights approfondis sur vos activités métier. 

La planification de l’actualisation de flux de données est gérée directement à partir de l’espace de travail dans lequel votre flux de données a été créé, tout comme vos jeux de données. 

## <a name="how-dataflows-work"></a>Fonctionnement des flux de données

Voici quelques exemples de la manière dont les flux de données peuvent fonctionner pour vous :

* Les organisations peuvent mapper leurs données à des entités standard dans le Common Data Model ou créer leurs propres entités personnalisées. Ces entités peuvent ensuite servir de blocs de construction pour créer des rapports, des tableaux de bord et des applications prêts à l’emploi et les distribuer aux utilisateurs au sein de leur organisation. 

* Grâce à la vaste collection de connecteurs de données Microsoft, les entreprises peuvent connecter leurs propres sources de données aux flux de données, en utilisant Power Query pour mapper les données depuis leur origine et les intégrer à Power BI. Une fois que les données sont importées par un flux de données (et actualisées à une fréquence spécifiée), ces entités de flux de données peuvent être utilisées dans l’application Power BI Desktop pour créer des rapports et des tableaux de bord convaincants. 

## <a name="how-to-use-dataflows"></a>Comment utiliser des flux de données

La section précédente décrivait quelques façons d'utiliser des flux de données pour créer rapidement des analyses puissantes dans Power BI. Dans cette section, vous pouvez voir à quelle vitesse vous pouvez créer des insights à l’aide de flux de données dans une organisation ainsi qu’avoir un aperçu rapide de la manière dont des professionnels du décisionnel peuvent créer leurs propres flux de données et personnaliser des insights de leur propre organisation.

### <a name="extend-the-common-data-model-for-your-business-needs"></a>Étendre le modèle de données commun pour les besoins de votre entreprise
Dans les organisations qui veulent étendre le Common Data Model (CDM), les flux de données permettent aux professionnels du décisionnel de personnaliser les entités standards ou d’en créer de nouvelles. Cette approche libre-service de la personnalisation du modèle de données peut ensuite servir, avec des flux de données, à créer des applications et des tableaux de bord Power BI adaptés à une organisation.

### <a name="define-dataflows-programmatically"></a>Définir des flux de données par programmation
Vous souhaitez peut-être développer vos propres solutions par programmation pour créer des flux de données. Avec les API publiques et la capacité à créer par programmation des fichiers de définition de flux de données personnalisés (model.json), vous créez une solution personnalisée qui correspond aux données uniques de votre organisation et à ses besoins en matière d’analyse. 

Les API publiques offrent aux développeurs des moyens simples et faciles d’interagir avec Power BI et les flux de données.

### <a name="extend-your-capabilities-with-azure"></a>Étendre vos capacités avec Azure
Azure Data Lake Storage Gen2 est inclus dans chaque abonnement Power BI payant (10 Go par utilisateur, 100 To par nœud P1). Vous pouvez donc facilement commencer à préparer des données en libre-service sur Azure Data Lake. 

Power BI peut être configuré pour stocker les données de flux de données dans le compte Azure Data Lake Storage Gen2 de votre organisation. Lorsque Power BI est connecté à votre abonnement Azure, les développeurs de données et les scientifiques des données peuvent tirer parti des produits Azure puissants tels qu’Azure Machine Learning, Azure Databricks et Azure Data Factory, entre autres.

Power BI peut également se connecter à des dossiers avec des données schématisées au format Common Data Model stockées dans le compte Azure Data Lake Storage de votre organisation. Ces dossiers peuvent être créés par les services tels que les services de données Azure. En se connectant à ces dossiers, les analystes peuvent travailler de manière transparente sur ces données dans Power BI. 


## <a name="dataflow-capabilities-on-power-bi-premium"></a>Fonctionnalités de flux de données sur Power BI Premium

Pour que les fonctionnalités de flux de données et les charges de travail fonctionnent avec un abonnement Power BI Premium, la charge de travail du flux de données pour cette capacité Premium doit être activée. Pour en savoir plus sur Power BI Premium, lisez l’article [Présentation de Power BI Premium](service-premium.md). 

Le tableau suivant décrit les fonctionnalités de flux de données et leurs capacités lorsque vous utilisez un compte Power BI Pro et la comparaison à l’aide de Power BI Premium.


|Fonctionnalité de flux de données | Power BI Pro |   Power BI Premium |
|---------|---------|---------|
|Actualisation planifiée| 8 par jour|  48|
|Stockage total| 10 Go/utilisateur  |100 To/nœud|
|Création de flux de données avec Power Query en ligne|    +   |+|
|Gestion de flux de données dans Power BI|   +|  +|
|Connecteur de données de flux de données dans Power BI Desktop|  +|  +|
|Intégration à Azure|    +|  +|
|Entités calculées (transformations dans le stockage via M) | |   +|
|Nouveaux connecteurs|    +|  +|
|Actualisation incrémentielle du flux de données|  |   +|
|Exécution sur la capacité Power BI Premium/Exécution parallèle de transformations|   |   +|
|Entités liées à un flux de données| |        +|
|Schéma standardisé/Prise en charge intégrée pour le Common Data Model|  +|  +|



## <a name="summary-of-self-service-data-prep-for-big-data-in-power-bi"></a>Résumé de la préparation des données en libre-service pour le Big Data dans Power BI
Comme mentionné précédemment dans cet article, il existe de multiples scénarios et exemples où des **flux de données** peuvent vous permettre de mieux contrôler vos données métier et d’en tirer plus rapidement des insights. En utilisant un modèle de données standard (schéma) défini par le Common Data Model, les flux de données peuvent importer vos précieuses données d'entreprise et les rendre prêtes pour la modélisation et la création d’insights BI en très peu de temps... dans ce qui prenait auparavant des mois, voire plus, à créer. 

En stockant des données d’entreprise au format standardisé du **Common Data Model**, vos professionnels du décisionnel (ou vos développeurs) peuvent créer des applications qui génèrent rapidement, facilement et automatiquement des visuels et des rapports. Ceux-ci incluent, sans s’y limiter:


* Le mappage de vos données à des entités standard dans le Common Data Model pour unifier des données et tirer parti du schéma connu pour déclencher des analyses prêtes à l’emploi
* La création de vos propres entités personnalisées pour unifier des données dans toute votre organisation 
* L’utilisation et l’actualisation de **données externes** en tant que partie d’un flux de données et l’activation de l’importation de ces données pour favoriser les insights
* Prise en main des flux de données pour les développeurs





## <a name="next-steps"></a>Étapes suivantes

Cet article a fourni une vue d’ensemble de la préparation des données en libre-service pour le Big Data dans Power BI et les nombreuses manières dont vous pouvez l’utiliser. Les articles suivants définissent plus en détail les scénarios d’utilisation courants pour les flux de données. 

* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation d’entités calculées sur Power BI Premium (préversion)](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales (préversion)](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI (préversion)](service-dataflows-developer-resources.md)

Pour plus d’informations sur Power Query et l’actualisation planifiée, vous pouvez consulter ces articles :
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Configuration d’une actualisation planifiée](refresh-scheduled-refresh.md)

Pour plus d’informations sur le modèle Common Data Model, vous pouvez lire son article de présentation :
* [Vue d’ensemble du modèle CMD (Common Data Model) ](https://docs.microsoft.com/powerapps/common-data-model/overview)

