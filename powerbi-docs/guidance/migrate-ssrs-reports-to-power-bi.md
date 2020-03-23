---
title: Effectuer la migration des rapports SQL Server Reporting Services vers Power BI
description: Conseils concernant la migration des rapports SQL Server Reporting Services (SSRS) vers Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: b87848953722d33235a11729a3643c627cca7234
ms.sourcegitcommit: 646d2de454a2897dc52cbc02b7743aaa021bac04
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525611"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Effectuer la migration des rapports SQL Server Reporting Services vers Power BI

Cet article s’adresse aux auteurs de rapports SQL Server Reporting Services (SSRS), ainsi qu’aux administrateurs Power BI. Il vous fournit des conseils concernant la migration de vos rapports [RDL](/sql/reporting-services/reports/report-definition-language-ssrs) vers Power BI.

> [!NOTE]
> Seuls les rapports RDL peuvent faire l’objet d’une migration. Dans Power BI, les rapports RDL sont appelés _rapports paginés_.

Ces conseils sont répartis selon quatre étapes. Nous vous recommandons de lire l’article dans son intégralité avant d’effectuer la migration de vos rapports.

1. [Avant de commencer](#before-you-start)
1. [Étape de prémigration](#pre-migration-stage)
1. [Étape de migration](#migration-stage)
1. [Étape de post-migration](#post-migration-stage)

Vous pouvez effectuer la migration sans arrêter vos serveurs SSRS ni perturber les utilisateurs de vos rapports. Il est important de savoir qu’il n’est pas nécessaire de supprimer des données ou des rapports. Cela signifie que vous pouvez conserver votre environnement actuel jusqu’à sa mise hors service.

## <a name="before-you-start"></a>Avant de commencer

Avant de commencer la migration, vous devez vérifier que votre environnement répond à certains prérequis. Nous décrirons ces prérequis, puis nous vous présenterons un outil de migration.

### <a name="preparing-for-migration"></a>Préparation à la migration

Lorsque vous préparez la migration de vos rapports vers Power BI, vérifiez d’abord que votre organisation dispose d’un abonnement [Power BI Premium](../service-premium-what-is.md). Cet abonnement est nécessaire pour héberger et exécuter vos rapports paginés Power BI.

### <a name="supported-versions"></a>Versions prises en charge

Vous pouvez effectuer la migration d’instances SSRS qui sont exécutées localement ou sur des machines virtuelles hébergées par des fournisseurs cloud, comme Azure.

La liste suivante fournit les versions de SQL Server qui sont prises en charge pour la migration vers Power BI :

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

La migration à partir de Power BI Report Server est également possible.

### <a name="migration-tool"></a>Outil de migration

Nous vous recommandons d’utiliser l’[outil de migration RDL](https://github.com/microsoft/RdlMigration) pour préparer et effectuer la migration de vos rapports. Cet outil a été développé par Microsoft pour aider les utilisateurs à effectuer la migration des rapports RDL entre leurs serveurs SSRS et Power BI. Il est disponible sur GitHub et fournit une procédure complète pour un scénario de migration.

L’outil automatise les tâches suivantes :

* La recherche des [sources de données non prises en charge](../paginated-reports/paginated-reports-data-sources.md) et des [fonctionnalités de rapport non prises en charge](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
* La conversion de toutes les ressources _partagées_ en ressources _incorporées_ :
  * Les **sources de données** partagées deviennent des sources de données incorporées
  * Les **jeux de données** partagés deviennent des jeux de données incorporés
* La publication des rapports (qui ont été validés) sous forme de rapports paginés, dans un espace de travail Power BI spécifié (sur une capacité Premium)

L’outil ne modifie pas et ne supprime pas vos rapports existants. À l’issue de l’opération, il génère un récapitulatif de toutes les actions terminées, qu’elles aient réussi ou non.

L’outil fera probablement l’objet d’améliorations de la part de Microsoft. La communauté est également encouragée à apporter sa contribution en vue de l’améliorer.

## <a name="pre-migration-stage"></a>Étape de prémigration

Lorsque vous avez vérifié que votre organisation répond bien aux prérequis, vous pouvez passer à l’étape de _prémigration_. Cette étape comporte trois phases :

1. Découvrir
1. Évaluer
1. Préparer

### <a name="discover"></a>Découvrir

L’objectif de la phase de _découverte_ est d’identifier vos instances SSRS existantes. Ce processus implique l’analyse du réseau dans le but d’identifier toutes les instances SQL Server de votre organisation.

Vous pouvez utiliser [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). Également appelé « MAP Toolkit », cet outil permet de découvrir et de générer des rapports sur vos instances SQL Server, ainsi que sur vos versions et vos fonctionnalités installées. Il s’agit d’un outil puissant pour l’inventaire, l’évaluation et la création de rapports, qui peut simplifier la planification de votre migration.

### <a name="assess"></a>Évaluer

Après la découverte de vos instances SSRS, l’objectif de la phase d’_évaluation_ est de comprendre les rapports SSRS (ou les éléments de serveur) qui ne peuvent pas faire l’objet d’une migration.

Seuls les rapports RDL peuvent faire l’objet d’une migration entre vos serveurs SSRS et Power BI. Après leur migration, les rapports RDL deviennent des rapports paginés Power BI.

Toutefois, les types d’éléments SSRS suivants ne peuvent pas faire l’objet d’une migration vers Power BI :

- Sources de données partagées <sup>1</sup>
- Jeux de données partagés <sup>1</sup>
- Ressources, comme des fichiers image
- Indicateurs de performance clés (SSRS 2016 ou version ultérieure — Enterprise Edition uniquement)
- Rapports mobiles (SSRS 2016 ou version ultérieure — Enterprise Edition uniquement)
- Modèles de rapport (dépréciés)
- Parties de rapport (dépréciées)

<sup>1</sup> L’[outil de migration RDL](https://github.com/microsoft/RdlMigration) convertit automatiquement les sources de données partagées et les jeux de données partagés, à condition qu’ils utilisent des sources de données prises en charge.

Si vos rapports RDL s’appuient sur des fonctionnalités qui ne sont [pas encore prises en charge par les rapports paginés Power BI](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), vous pouvez envisager de les redévelopper comme des rapports [Power BI](../consumer/end-user-reports.md). Même si vos rapports RDL peuvent faire l’objet d’une migration, nous vous recommandons de les moderniser sous forme de rapports Power BI, quand cela vous paraît judicieux.

Si vos rapports RDL doivent récupérer des données à partir de _sources de données locales_, ils ne peuvent pas utiliser l’authentification unique (SSO). Actuellement, toutes les extractions de données à partir de ces sources sont effectuées dans le contexte de sécurité du _compte d’utilisateur de la source de données de la passerelle_. Il n’est pas possible pour SQL Server Analysis Services (SSAS) d’appliquer la Sécurité au niveau des lignes (SNL) pour chaque utilisateur.

En général, les rapports paginés Power BI sont optimisés pour l’**impression** et la **génération de PDF**. Les rapports Power BI sont optimisés pour l’**exploration et l’interactivité**. Pour plus d’informations, consultez [Quand utiliser des rapports paginés dans Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Préparer

L’objectif de la phase de _préparation_ consiste à s’assurer que tout est prêt. Il comprend la configuration de l’environnement Power BI, la planification de la sécurisation et de la publication de vos rapports, ainsi que des idées de redéveloppement des éléments SSRS qui n’ont pas fait l’objet d’une migration.

1. Vérifiez que la [charge de travail Rapports paginés](../service-admin-premium-workloads.md#paginated-reports) est activée pour votre capacité Power BI Premium et qu’elle dispose de suffisamment de mémoire.
1. Vérifiez la prise en charge des [sources de données](../paginated-reports/paginated-reports-data-sources.md) de votre rapport et configurez une instance de [Power BI Gateway](../service-gateway-onprem.md) pour permettre la connectivité à toutes les sources de données locales.
1. Familiarisez-vous avec la sécurité Power BI et planifiez la [reproduction de vos dossiers et de vos autorisations SSRS](/sql/reporting-services/security/secure-folders) avec des [espaces de travail et des rôles d’espace de travail Power BI](../service-new-workspaces.md).
1. Familiarisez-vous avec le partage Power BI et planifiez la façon dont vous allez distribuer le contenu en publiant des [applications Power BI](../service-create-distribute-apps.md).
1. Vous pouvez utiliser des [jeux de données Power BI partagés](../service-datasets-build-permissions.md) à la place de vos sources de données partagées SSRS.
1. Utilisez [Power BI Desktop](../desktop-what-is-desktop.md) pour développer des rapports optimisés pour les appareils mobiles (par exemple à l’aide du [visuel personnalisé Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview)) au lieu de vos rapports mobiles et de vos indicateurs de performance clés SSRS.
1. Réévaluez l’utilisation du champ prédéfini **UserID** dans vos rapports. Si vous vous fiez à **UserID** pour sécuriser les données des rapports, sachez que, pour les rapports paginés (lorsqu’ils sont hébergés dans le service Power BI), il retourne le nom d’utilisateur principal (UPN). Ainsi, au lieu de renvoyer le nom du compte NT, par exemple _AW\mblythe_, le champ intégré renvoie un résultat du type _m.blythe&commat;adventureworks.com_. Vous devrez réviser vos définitions de jeu de données, et éventuellement les données sources. Après révision et publication, nous vous recommandons de bien vérifier que les autorisations de données fonctionnent comme prévu dans vos rapports.
1. Réévaluez l’utilisation du champ prédéfini **ExecutionTime** dans vos rapports. Pour les rapports paginés (lorsqu’ils sont hébergés dans le service Power BI), le champ prédéfini retourne la date/heure _au format UTC (temps universel coordonné)_ . Cela peut avoir un impact sur les valeurs par défaut des paramètres et les étiquettes de durée d’exécution des rapports (généralement ajoutées aux pieds de page des rapports).
1. Si votre source de données est SQL Server (au niveau local), vérifiez que les rapports n’utilisent pas de visualisations de carte. La visualisation de carte repose sur des types de données spatiales SQL Server qui ne sont pas pris en charge par la passerelle. Pour plus d’informations, consultez l’[aide sur l’extraction de données pour les rapports paginés (types de données SQL Server complexes)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Vérifiez que vos auteurs de rapports ont installé [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md) et que les versions ultérieures peuvent être facilement distribuées dans l’ensemble de votre organisation.

## <a name="migration-stage"></a>Étape de migration

Une fois que vous avez préparé votre environnement et vos rapports Power BI, vous êtes prêt pour l’étape de _migration_.

Il existe deux types de migration : _manuelle_ et _automatisée_. La migration manuelle convient pour un petit nombre de rapports ou pour des rapports nécessitant une modification avant la migration. La migration automatisée convient à la migration d’un grand nombre de rapports.

### <a name="manual-migration"></a>Migration manuelle

Toute personne autorisée à accéder à l’instance SSRS et à l’espace de travail Power BI peut procéder manuellement à la migration des rapports vers Power BI. Voici la procédure à suivre :

1. Ouvrez le portail SSRS qui contient les rapports devant faire l’objet d’une migration.
1. Téléchargez chaque définition de rapport, en enregistrant les fichiers .rdl localement.
1. Ouvrez la _dernière version_ de Power BI Report Builder et connectez-vous au service Power BI à l’aide de vos informations d’identification Azure AD.
1. Ouvrez chaque rapport dans Power BI Report Builder, puis :
   1. Vérifiez que toutes les sources de données et tous les jeux de données sont incorporés dans la définition du rapport, et qu’il s’agit bien de [sources de données prises en charge](../paginated-reports/paginated-reports-data-sources.md).
   1. Affichez un aperçu du rapport pour vérifier qu’il s’affiche correctement.
   1. Choisissez l’option _Enregistrer sous_, puis sélectionnez _Service Power BI_.
   1. Sélectionnez l’espace de travail qui contiendra le rapport.
   1. Vérifiez que le rapport a bien été enregistré. Si certaines fonctionnalités de votre rapport ne sont pas encore prises en charge, l’action d’enregistrement échouera. Vous serez informé des raisons de cet échec. Vous devrez alors modifier la conception de votre rapport et retenter l’enregistrement.

### <a name="automated-migration"></a>Migration automatisée

Il existe deux options pour la migration automatisée. Vous pouvez utiliser :

- L’outil de migration RDL
- Les API disponibles publiquement pour SSRS et Power BI

L’[outil de migration RDL](#migration-tool) a déjà été décrit dans cet article.

Vous pouvez également utiliser les API SSRS et Power BI disponibles publiquement pour automatiser la migration de votre contenu. Étant donné que l’outil de migration RDL utilise déjà ces API, vous pouvez développer un outil personnalisé adapté à vos besoins.

Pour plus d’informations sur les API, consultez :

- [Informations de référence sur l’API REST de Power BI](../developer/automation/rest-api-reference.md)
- [API REST SQL Server Reporting Services](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Étape de post-migration

Une fois la migration terminée, vous pouvez passer à l’étape de _post-migration_. Cette étape implique l’utilisation d’une série de tâches de post-migration visant à garantir que tout fonctionne correctement et efficacement.

### <a name="configure-data-sources"></a>Configurer des sources de données

Une fois la migration des rapports vers Power BI terminée, vous devez vérifier que leurs sources de données sont correctement configurées. Cela peut impliquer l’affectation à des sources de données de passerelle, ainsi que le [stockage sécurisé des informations d’identification de la source de données](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication). Ces actions ne sont pas effectuées par l’outil de migration RDL.

### <a name="review-report-performance"></a>Examiner les performances du rapport

Nous vous recommandons vivement d’effectuer les actions suivantes pour garantir la meilleure expérience possible aux utilisateurs des rapports :

1. Testez les rapports dans chaque [navigateur pris en charge par Power BI](../power-bi-browsers.md) pour vérifier que le rendu du rapport est correct.
1. Exécutez des tests pour comparer les temps d’affichage du rapport dans SSRS et dans Power BI. Vérifiez que les rapports Power BI s’affichent dans un délai acceptable.
1. Si l’affichage des rapports Power BI échoue en raison d’une mémoire insuffisante, allouez des [ressources supplémentaires à la capacité Power BI Premium](../service-admin-premium-workloads.md#paginated-reports).
1. Pour les rapports qui sont longs à s’afficher, vous pouvez demander à Power BI de les envoyer aux utilisateurs de votre rapport sous la forme d’[abonnements e-mail dans lesquels les rapports sont ajoutés en pièces jointes](../consumer/paginated-reports-subscriptions.md).
1. Pour les rapports Power BI basés sur des jeux de données Power BI, vérifiez les conceptions des modèles pour être sûr qu’elles sont entièrement optimisées.

### <a name="reconcile-issues"></a>Résoudre les problèmes

La phase de post-migration est essentielle pour résoudre les problèmes, notamment au niveau des performances. L’ajout de la charge de travail Rapports paginés à une capacité peut contribuer à ralentir les performances des rapports paginés _et des autres types de contenu_ stockés dans la capacité.

Pour plus d’informations sur ces problèmes, notamment sur leur compréhension et leur atténuation, consultez les articles suivants :

- [Optimiser les capacités Premium](../service-premium-capacity-optimize.md)
- [Superviser les capacités Premium avec l’application](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Présentation des rapports paginés dans Power BI Premium](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Aide sur l’extraction de données pour les rapports paginés](report-paginated-data-retrieval.md)
- [Quand utiliser des rapports paginés dans Power BI](report-paginated-or-power-bi.md)
- [Rapports paginés dans Power BI : Questions fréquentes (FAQ)](../paginated-reports/paginated-reports-faq.md)
- [Cours en ligne : Rapports paginés en une journée](../paginated-reports/paginated-reports-online-course.md)
- [Questions fréquentes Power BI Premium](../service-premium-faq.md)
- [Outil de migration RDL](https://github.com/microsoft/RdlMigration)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)

Les partenaires Power BI sont là pour aider votre organisation dans son processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
