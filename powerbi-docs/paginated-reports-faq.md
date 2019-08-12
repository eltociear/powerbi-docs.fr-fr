---
title: 'Rapports paginés dans Power BI : FORUM AUX QUESTIONS'
description: Cet article répond aux questions fréquemment posées sur les rapports paginés. Ces rapports sont mis en forme, optimisés au pixel près pour la sortie par impression ou la génération de fichiers PDF.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 07/15/2019
ms.openlocfilehash: 2e59499b93f4d1b4879cdec5b807f863a80718aa
ms.sourcegitcommit: 805d52e57a935ac4ce9413d4bc5b31423d33c5b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68665373"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Rapports paginés dans Power BI : FORUM AUX QUESTIONS 

Cet article répond aux questions fréquemment posées sur les rapports paginés. Ces rapports sont mis en forme, optimisés au pixel près pour la sortie par impression ou la génération de fichiers PDF. Ils sont appelés « paginés », car ils sont mis en forme pour tenir sur plusieurs pages. Les rapports paginés sont basés sur la technologie de rapport RDL dans SQL Server Reporting Services. 

Cet article répond aux nombreuses questions courantes que l’on se pose concernant les rapports paginés dans Power BI Premium, d’une part, et le Générateur de rapports, l’outil autonome de création de rapports paginés, d’autre part. Vous avez besoin d’une licence Power BI Pro pour publier un rapport sur le service. Vous pouvez publier et partager des rapports paginés sous Mon espace de travail ou dans les espaces de travail de l’application tant que l’espace de travail est dans une capacité Power BI Premium. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>De quelle taille de capacité Premium ai-je besoin pour des rapports paginés ?

La charge de travail des rapports paginés est disponible sur les références SKU P1 à P3.  Vous pouvez également l’utiliser avec des références SKU A4 à A6 pour les scénarios d’incorporation SaaS.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Quel seuil de mémoire maximal puis-je placer pour les rapports paginés dans ma capacité ?

Vous pouvez utiliser jusqu'à 100 % de la mémoire pour cette charge de travail d'ici à la fin juin 2019. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Comment fonctionne l’accès utilisateur aux rapports paginés ?

L’accès utilisateur aux rapports paginés est le même que l’accès utilisateur à tout autre contenu du service Power BI. 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Comment activer/désactiver la charge de travail de mes rapports paginés ?

L’administrateur de capacité peut activer ou désactiver la charge de travail des rapports paginés à la page du portail d’administration des capacités.  Par défaut, la charge de travail est activée pour toutes les nouvelles capacités que vous créez.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Comment puis-je surveiller l’utilisation de rapports paginés dans mon client ?

Les journaux d'audit d’Office 365 détaillent l'utilisation de ce type de rapport dans les événements suivants : 

- Afficher un rapport Power BI
- Supprimer un rapport Power BI
- Créer un rapport Power BI
- Rapport Power BI téléchargé

Le champ ReportType a la valeur « PaginatedReport » pour identifier les rapports paginés par opposition aux rapports Power BI.

Les journaux d’audit fournissent également les événements suivants pour les rapports paginés :

- Jeu de données Power BI lié à la passerelle
- Découvrir la source de données Power BI
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Puis-je surveiller cette charge de travail via l’application de surveillance de capacité Premium ?

Oui, la surveillance est disponible en tant que nouvel onglet avec les mêmes détails pertinents que pour vos jeux de données Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Ai-je besoin d’une licence Pro pour créer et publier des rapports paginés ?

Vous pouvez charger des rapports paginés vers Mon espace de travail sans licence Pro, à condition que l’espace de travail de travail figure dans une capacité Premium.  Pour les autres espaces de travail, vous devez disposer d'une licence Pro afin d’y créer et d’y publier du contenu. Nous vous recommandons de télécharger et d’utiliser le Générateur de rapports Power BI même sans la licence Pro, mais vous ne pourrez pas publier les rapports paginés que vous créez. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Que se passe-t-il si j’ai un rapport paginé dans un espace de travail et que la charge de travail est désactivée ?

Vous recevez un message d’erreur et vous ne pouvez pas afficher votre rapport avant que la charge de travail ne soit à nouveau activée. Vous pouvez toujours supprimer le rapport à partir de l’espace de travail.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Quelle est la mémoire par défaut de chacune des références SKU Premium prises en charge pour des rapports paginés ?

Mémoire par défaut dans chaque référence SKU Premium pour des rapports paginés :

- **P1/A4** : 20 % par défaut ; 10 % minimum
- **P2/A5** : 20 % par défaut ; 5 % minimum
- **P3/A6** : 20 % par défaut ; 2,5 % minimum

## <a name="general"></a>Général

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quand dois-je utiliser un rapport paginé plutôt qu’un rapport Power BI ?

Les rapports paginés sont les mieux adaptés à des scénarios qui requièrent une mise en forme et une optimisation pour l'impression ou la génération de fichiers PDF.  Un compte de résultat est une bon exemple du type de rapport que vous souhaitez probablement créer sous forme de rapport paginé.  

Les rapports Power BI sont optimisés pour l’exploration et l’interactivité.  Un rapport de ventes où différents vendeurs souhaitent ventiler les données d’un même rapport par région/secteur/client spécifique et voir comment les chiffres évoluent est très bien servi par un rapport Power BI.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>Selon la documentation, le Générateur de rapports Power BI est l’outil de création préféré. Puis-je créer des rapports paginés dans SQL Server Data Tools pour Power BI ?

Oui, mais le service Power BI ne vous permet de charger qu’un seul élément à la fois. Par conséquent, de nombreux scénarios que les auteurs utilisent avec SQL Server Data Tools (SSDT) ne sont pas encore pris en charge. Afficher la [liste des fonctionnalités non prises en charge](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) complète disponible plus loin dans cette FAQ.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quelles versions du Générateur de rapports prenez-vous en charge ?

Nous avons récemment lancé le Générateur de rapports Power BI comme principal outil de création de rapports paginés dans le service Power BI. Installer le [Générateur de rapports Power BI à partir du centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Comment déplacer les rapports existants que j’ai enregistrés dans SQL Server Reporting Services vers Power BI ?

Vous devez télécharger le rapport à partir du serveur, puis le charger vers Power BI via le portail.  Aucun outil de migration n’est disponible pour l’instant, mais nous envisageons d’en créer un lorsque nous aurons terminé la préversion publique et atteint le bon niveau de parité des fonctionnalités entre les produits.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Puis-je ouvrir des rapports et les publier directement sur le service ?

Oui. Nous avons récemment ajouté une prise en charge pour l’ouverture de rapports et leur publication directement sur le service à partir du Générateur de rapports Power BI.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quelles fonctionnalités de rapports paginés dans SSRS ne sont pas encore prises en charge dans Power BI ?

Actuellement, les rapports paginés ne prennent pas en charge les éléments suivants :

- Sources de données partagées
- Jeux de données partagés
- Sous-rapports
- Extraction et navigation dans d’autres rapports
- Rapports liés
- Couches de carte Bing
- Polices personnalisées

Vous obtenez un message d’erreur si vous essayez de charger un fichier avec une fonctionnalité non prise en charge autre que basculer/trier dans le service Power BI.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quelles sources de données prenez-vous actuellement en charge pour les rapports paginés ?

Nous prenons en charge les sources de données suivantes : 

- Jeux de données Power BI (via l’authentification unique)
- Azure Analysis Services (via SSO et oAuth)
- Azure SQL Data Warehouse
- Azure SQL Database (nom d’utilisateur/mot de passe, authentification unique et OAuth)
- SQL Server*
- Modèles tabulaires (DAX) et multidimensionnels (MDX) SQL Server Analysis Services (SSAS)** 
- Oracle* 
- Teradata* 

* nécessite la passerelle locale.

Lorsque vous accédez à SSAS via la passerelle, l’utilisateur dont les informations d’identification sont stockées a besoin d’autorisations avec élévation de privilèges dans SSAS pour fonctionner via la passerelle.

### <a name="what-authentication-methods-do-you-support"></a>Quelles méthodes d’authentification prenez-vous en charge ?

Nous prenons en charge l’authentification unique pour les sources de données Azure Analysis Services, Azure SQL Database et Power BI.  Nous prenons également en charge OAuth pour Azure SQL Database et Azure Analysis Services.  Pour les autres sources de données, vous devez stocker un nom d’utilisateur et un mot de passe avec la source de données dans le portail ou de la passerelle.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Puis-je utiliser un jeu de données Power BI comme source de données pour mon rapport paginé ?

Oui, nous prenons en charge les jeux de données Power BI comme sources de données pour vos rapports paginés.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Puis-je utiliser des procédures stockées via la passerelle ?

Vous pouvez utiliser une procédure stockée via la passerelle, mais vous pouvez rencontrer des problèmes dans certains scénarios si la procédure stockée contient des paramètres.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quels sont les formats d’exportation disponibles pour mon rapport dans le service Power BI ?

Vous pouvez exporter vers Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF. CSV, XML et MHTML.

### <a name="can-i-print-paginated-reports"></a>Puis-je imprimer des rapports paginés ?

Oui, l’impression est disponible pour les rapports paginés, comprenant un nouvel aperçu amélioré de l’impression. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>Des abonnements par e-mail sont-ils disponibles pour des rapports paginés ?

Oui, les abonnements par e-mail sont entièrement pris en charge pour les rapports paginés, avec six différents formats de fichiers et valeurs de paramètre.

### <a name="can-i-run-custom-code-in-my-report"></a>Puis-je exécuter du code personnalisé dans mon rapport ?

Oui, nous prenons en charge la possibilité d’exécuter du code dans vos rapports comme vous pouvez le faire dans SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Puis-je utiliser Power BI Embedded pour incorporer mes rapports paginés dans une application que j’héberge ?

L’incorporation de SaaS est déjà prise en charge. L’incorporation de SaaS n’est pas prise en charge actuellement.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Puis-je passer d'un rapport Power BI à un rapport paginé ?

Pas encore, mais nous prévoyons absolument de prendre en charge ce scénario.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Puis-je partager mon contenu de rapport paginé via une application Power BI ?

Oui, les rapports paginés sont pris en charge pour être déployés avec les applications depuis les espaces de travail v1 et v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>D’autres fonctionnalités spécifiques aux rapports dans Power BI, telles que l’épinglage pour reporter des mosaïques de rapports sur des tableaux de bord, fonctionneront-elles avec des rapports paginés ?

Nous prévoyons que les rapports prennent autant que possible en charge les mêmes scénarios principaux.  Dans l’idéal, bien que leur outil de création soit différent, du point de vue du consommateur il s’agit simplement d’un autre rapport de sa liste dans le portail. Peu lui importe la façon dont il a été créé s’il peut faire ce qu’il a à faire.  Un bon exemple de cette parité des fonctionnalités est la prise en charge prévue des commentaires. Bien que la fonctionnalité proprement dite puisse fonctionner de manière légèrement différente pour chaque type de rapport, vous serez en mesure d’utiliser les commentaires pour les deux types.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Un outil de migration qui permettrait aux clients SSRS de déplacer leurs ressources et rapports existants vers Power BI est-il prévu ?

Nous évaluons les options présentes ici pour autoriser le déplacement du contenu vers Power BI de manière automatisée, mais cette option ne sera pas disponible avant la disponibilité générale.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Y-a-t-il un contrôle de visionneuse de rapports pour les rapports paginés dans le service Power BI ?

Non, un contrôle de visionneuse de rapports n’est pas disponible actuellement.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Peut-on rechercher des rapports paginés à partir de la nouvelle page d’accueil dans le service Power BI ?

Oui, vous pouvez maintenant rechercher vos rapports paginés depuis la page d’accueil.  Vous les voyez également dans les autres parties de la nouvelle page d’accueil.

## <a name="next-steps"></a>Étapes suivantes

- [Installer le Générateur de rapports Power BI à partir du Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutoriel : Créer un rapport paginé](paginated-reports-quickstart-aw.md)
