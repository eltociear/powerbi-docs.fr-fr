---
title: 'Rapports paginés dans Power BI : FAQ (préversion)'
description: Cet article répond aux questions fréquemment posées sur les rapports paginés. Ces rapports sont mis en forme, optimisés au pixel près pour la sortie par impression ou la génération de fichiers PDF.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: 0ddf95563c52af135ac7ae4fe71aeddcd2ce7313
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51267277"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Rapports paginés dans Power BI : FAQ (préversion)

Cet article répond aux questions fréquemment posées sur les rapports paginés. Ces rapports sont mis en forme, optimisés au pixel près pour la sortie par impression ou la génération de fichiers PDF. Ils sont appelés « paginés », car ils sont mis en forme pour tenir sur plusieurs pages. Les rapports paginés sont basés sur la technologie de rapport RDL dans SQL Server Reporting Services. 

Cet article répond aux nombreuses questions courantes que l’on se pose concernant les rapports paginés dans Power BI Premium, d’une part, et le Générateur de rapports, l’outil autonome de création de rapports paginés, d’autre part. Vous avez besoin d’une licence Power BI Pro pour publier un rapport sur le service. Vous pouvez publier et partager des rapports paginés sous Mon espace de travail ou dans les espaces de travail de l’application tant que l’espace de travail est dans une capacité Power BI Premium. 

## <a name="administration"></a>Administration

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>De quelle taille de capacité Premium ai-je besoin pour des rapports paginés ?

La charge de travail des rapports paginés est disponible sur les référence SKU P1 à P3 pour la préversion publique.  Vous pouvez également l’utiliser pour les scénarios de test/développement avec des référence SKU A4 à A6.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Quel seuil de mémoire maximal puis-je placer pour les rapports paginés dans ma capacité ?

Actuellement, vous ne pouvez réserver que 50 % de la mémoire pour cette charge de travail. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Comment fonctionne l’accès utilisateur aux rapports paginés ?

L’accès utilisateur aux rapports paginés est le même que l’accès utilisateur à tout autre contenu du service Power BI. 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Comment activer/désactiver la charge de travail de mes rapports paginés ?

L’administrateur de capacité peut activer ou désactiver la charge de travail des rapports paginés à la page du portail d’administration des capacités.  

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

Pas encore. La surveillance sera disponible en préversion publique en tant que nouvel onglet dans le rapport existant, avec les mêmes détails pertinents dont vous disposez pour vos jeux de données Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Ai-je besoin d’une licence Pro pour créer et publier des rapports paginés ?

Oui. Vous ne pouvez pas charger de rapports dans l’espace de travail sans licence Pro. Vous pouvez télécharger et essayer le Générateur de rapports sans la licence Pro, mais pas publier les rapports paginés que vous créez. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Que se passe-t-il si j’ai un rapport paginé dans un espace de travail et que la charge de travail est désactivée ?

Vous recevez un message d’erreur et vous ne pouvez pas afficher votre rapport avant que la charge de travail ne soit à nouveau activée. Vous pouvez toujours supprimer le rapport à partir de l’espace de travail.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Quelle est la mémoire par défaut de chacune des références SKU Premium prises en charge pour des rapports paginés ?

Mémoire par défaut dans chaque référence SKU Premium pour des rapports paginés :

- **P1/A4** : 20 % par défaut ; 10 % minimum
- **P2/A5** : 10 % par défaut ; 5 % minimum
- **P3/A6** : 5 % par défaut ; 2,5 % minimum

## <a name="general"></a>Général

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quand dois-je utiliser un rapport paginé plutôt qu’un rapport Power BI ?

Les rapports paginés sont les mieux adaptés à des scénarios qui requièrent une mise en forme et une optimisation pour l'impression ou la génération de fichiers PDF.  Un compte de résultat est une bon exemple du type de rapport que vous souhaitez probablement créer sous forme de rapport paginé.  

Les rapports Power BI sont optimisés pour l’exploration et l’interactivité.  Un rapport de ventes où différents vendeurs souhaitent ventiler les données d’un même rapport par région/secteur/client spécifique et voir comment les chiffres évoluent est très bien servi par un rapport Power BI.

### <a name="the-documentation-says-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>Selon la documentation, le Générateur de rapports est l’outil de création préféré. Puis-je créer des rapports paginés dans SQL Server Data Tools pour Power BI ?

Oui, mais le service Power BI ne vous permet de charger qu’un seul élément à la fois. Par conséquent, de nombreux scénarios que les auteurs utilisent avec SQL Server Data Tools (SSDT) ne sont pas encore pris en charge. Afficher la [liste des fonctionnalités non prises en charge](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) complète disponible plus loin dans cette FAQ.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quelles versions du Générateur de rapports prenez-vous en charge ?

Utilisez la dernière version du Générateur de rapports SQL Server 2016 pour créer et publier vos rapports sur le service Power BI. Installer le [Générateur de rapports à partir du centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53613).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Comment déplacer les rapports existants que j’ai enregistrés dans SQL Server Reporting Services vers Power BI ?

Vous devez télécharger le rapport à partir du serveur, puis le charger vers Power BI via le portail.  Aucun outil de migration n’est disponible pour l’instant, mais nous envisageons d’en créer un lorsque nous aurons terminé la préversion publique et atteint le bon niveau de parité des fonctionnalités entre les produits.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Puis-je ouvrir des rapports et les publier directement sur le service ?

Pas à ce stade. Nous allons ajouter une prise en charge pour l’ouverture de rapports et leur publication directement sur le service à partir du Générateur de rapports à un moment donné, comme vous pouvez le faire avec Power BI Desktop.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quelles fonctionnalités de rapports paginés dans SSRS ne sont pas encore prises en charge dans Power BI ?

Actuellement, les rapports paginés ne prennent pas en charge les éléments suivants :

- Sources de données partagées
- Jeux de données partagés
- Sous-rapports
- Taux de clics et extraction
- Rapports liés
- Signets
- Couches de carte Bing
- Polices personnalisées
- Paramètres masqués

Le basculement et le tri interactif ne sont pas encore en production, mais sont attendus pour bientôt.    

Vous obtenez un message d’erreur si vous essayez de charger un fichier avec une fonctionnalité non prise en charge autre que basculer/trier dans le service Power BI.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quelles sources de données prenez-vous actuellement en charge pour les rapports paginés ?

Nous prenons en charge les modèles tabulaires Azure SQL Database, SQL Server et SQL Server Analysis Services (SSAS) à l’aide de la passerelle locale. Nous ne prenons actuellement pas en charge les modèles SSAS multidimensionnels (MDX).

Lorsque vous accédez à SSAS via la passerelle, l’utilisateur dont les informations d’identification sont stockées a besoin d’autorisations avec élévation de privilèges dans SSAS pour fonctionner via la passerelle.

### <a name="what-authentication-methods-do-you-support"></a>Quelles méthodes d’authentification prenez-vous en charge ?

Actuellement, vous devez stocker un nom d’utilisateur et un mot de passe avec la source de données dans le portail ou de la passerelle.  Des méthodes d’authentification supplémentaires pour prendre en charge des éléments tels que la sécurité au niveau des lignes seront disponibles plus tard dans la préversion.

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Puis-je utiliser un jeu de données Power BI comme source de données pour mon rapport paginé ?

Pas encore, mais cette prise en charge est prévue prochainement.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Puis-je utiliser des procédures stockées via la passerelle ?

Vous pouvez utiliser une procédure stockée via la passerelle, sauf si elle contient des paramètres.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quels sont les formats d’exportation disponibles pour mon rapport dans le service Power BI ?

Vous pouvez exporter vers Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF. CSV, XML et MHTML.

### <a name="can-i-print-paginated-reports"></a>Puis-je imprimer des rapports paginés ?

Actuellement, vous pouvez exporter au format PDF et imprimer le fichier. L’impression directement à partir d’un rapport paginé doit être disponible bientôt. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>Des abonnements par e-mail sont-ils disponibles pour des rapports paginés ?

Non, les abonnements par e-mail seront disponibles ultérieurement.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Quelles sont les fonctionnalités à partir de SSRS que vous prendrez en charge dans le service Power BI ?

Notre objectif est de fournir plus la plus grande parité possible entre les deux produits.  Il peut ne pas être judicieux d’essayer de modifier certaines choses dans SSRS et Power BI pour s’adapter à des modèles SSRS existants, tels que les différents modèles d’autorisation Power BI, mais nous tiendrons compte des commentaires des clients pour prendre ces types de décisions.

### <a name="can-i-run-custom-code-in-my-report"></a>Puis-je exécuter du code personnalisé dans mon rapport ?

Oui, nous prenons en charge la possibilité d’exécuter du code dans vos rapports comme vous pouvez le faire dans SSRS.

### <a name="does-this-mean-ssrs-is-going-away"></a>Ceci signifie-t-il que SSRS est amené à disparaître ?

Pas du tout.  Cette nouvelle offre propose aux clients une option basée sur le cloud pour leurs rapports paginés.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Puis-je utiliser Power BI Embedded pour incorporer mes rapports paginés dans une application que j’héberge ?

Nous prévoyons de prendre en charge ce scénario avec les API Power BI existantes, mais nous n’avons pas encore de calendrier pour savoir quand ce scénario sera disponible.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Puis-je passer d'un rapport Power BI à un rapport paginé ?

Pas encore, mais nous prévoyons absolument de prendre en charge ce scénario.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Puis-je partager mon contenu de rapport paginé via une application Power BI ?

Actuellement, vous pouvez partager des rapports paginés individuels avec d’autres utilisateurs via l’action de partage dans le portail. Nous ne prenons pas encore en charge le partage dans une application, mais ce sera bientôt le cas. Le bouton de partage se trouvera également dans la barre d’outils.

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>D’autres fonctionnalités spécifiques aux rapports dans Power BI, telles que l’épinglage pour reporter des mosaïques de rapports sur des tableaux de bord, fonctionneront-elles avec des rapports paginés ?

Nous prévoyons que les rapports prennent autant que possible en charge les mêmes scénarios principaux.  Dans l’idéal, bien que leur outil de création soit différent, du point de vue du consommateur il s’agit simplement d’un autre rapport de sa liste dans le portail. Peu lui importe la façon dont il a été créé s’il peut faire ce qu’il a à faire.  Un bon exemple de cette parité des fonctionnalités est la prise en charge prévue des commentaires. Bien que la fonctionnalité proprement dite puisse fonctionner de manière légèrement différente pour chaque type de rapport, vous serez en mesure d’utiliser les commentaires pour les deux types.

### <a name="are-you-planning-to-create-a-new-authoring-tool-for-paginated-reports-in-the-power-bi-service--we-cant-do-everything-we-need-to-with-report-builder-today"></a>Vous prévoyez de créer un nouvel outil de création de rapports paginés dans le service Power BI ?  Aujourd’hui, nous ne pouvons pas faire tout ce qui est nécessaire avec le Générateur de rapports.

Nous sommes toujours à la recherche de différentes options pour la meilleure histoire d'outillage, mais soyez assurés que nous aurons une prise en charge des fonctionnalités comme ALM, les extensions personnalisées et d'autres fonctionnalités qui peuvent n’être incluses que dans l'un des outils de création pour SSRS. 

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Un outil de migration qui permettrait aux clients SSRS de déplacer leurs ressources et rapports existants vers Power BI est-il prévu ?

Oui, mais pas avant que l’ensemble des fonctionnalités prises en charge dans le service Power BI ne soit complet.

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>Pourrai-je un jour créer des rapports paginés et des rapports Power BI dans un seul outil de création ?

Nous ne prévoyons actuellement pas d’outil de création unique, mais nous cherchons des moyens de distribuer potentiellement les outils de création ensemble en tant que suite BI unique au lieu de téléchargements/de marques individuels.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Y-a-t-il un contrôle de visionneuse de rapports pour les rapports paginés dans le service Power BI ?

Non, un contrôle de visionneuse de rapports n’est pas disponible actuellement.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Peut-on rechercher des rapports paginés à partir de la nouvelle page d’accueil dans le service Power BI ?

Non, vous ne pouvez actuellement pas rechercher vos rapports paginés depuis la page d’accueil.  Vous les voyez cependant dans les autres parties de la nouvelle page d’accueil.

## <a name="next-steps"></a>Étapes suivantes

- [Installer le Générateur de rapports à partir du centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53613)
- [Tutoriel : Créer un rapport paginé](paginated-reports-quickstart-aw.md)