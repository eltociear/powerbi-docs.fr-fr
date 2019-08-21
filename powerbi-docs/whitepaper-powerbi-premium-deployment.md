---
title: Déploiement et gestion des capacités de Power BI Premium
description: Comprenez le potentiel de Power BI Premium et apprenez à concevoir, déployer, surveiller et dépanner des solutions évolutives.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: 1b3d455e0deff676d20c316422d4715773e0a85d
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69655057"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Déploiement et gestion des capacités de Power BI Premium

**Résumé :** Power BI Premium offre des performances plus cohérentes, une prise en charge des volumes de données volumineux et la flexibilité d’une plate-forme unifiée libre-service et d’entreprise décisionnelle pour tous les membres de votre organisation. Ce livre blanc technique de niveau 300 a été rédigé spécifiquement pour les administrateurs de Power BI, ainsi que pour les créateurs et les éditeurs de contenu. Il vise à les aider à comprendre le potentiel de Power BI Premium et à expliquer comment concevoir, déployer, surveiller et dépanner des solutions évolutives.

**Auteur :** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (MVP des plateformes de données et expert décisionnel indépendant avec des solutions au niveau du bit)

**Réviseurs techniques :** Adam Saxton, Akshai Mirchandani, Bhavik Merchant, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, Olivier matrat, swati Gupta

**S’applique à :** Capacités de service Power BI, Power BI Premium et Azure Power BI Embedded

> [!NOTE]
> Vous pouvez enregistrer ou imprimer ce livre blanc en sélectionnant **Imprimer** dans votre navigateur, puis **Enregistrer au format PDF**.

## <a name="introducing-power-bi"></a>Présentation de Power BI

Power BI est un service d’analyse commerciale conçu pour fournir des Insights qui permettent de prendre des décisions rapides et éclairées. Depuis sa sortie dans 2015, il a rapidement été utilisé pour fournir des solutions pour les plus petites entreprises aux plus grandes entreprises.

Il est mis à disposition de deux manières: En tant que service Cloud et en tant que solution de création de rapports locale nommée **Power bi Report Server**. \[[1,0](#endnote-01)\]

Power bien tant que service Cloud est un service SaaS (Software-as-a \[-service) [2](#endnote-02)\]. Il représente un ensemble de services et d’applications qui permettent aux organisations de développer, de déployer, de gérer et de partager des solutions pour surveiller leur activité.

Ce livre blanc n’a pas pour but de fournir une description complète de la service Power BI. Au lieu de cela, elle se concentre sur les sujets relatifs à l’objet de Power BI Premium. Pour obtenir des informations générales sur Power BI, reportez-vous à la documentation complète sur [Power bi](service-admin-premium-multi-geo.md). Pour obtenir une explication plus détaillée de la service Power BI avec un point de vue de la réalisation de déploiements d’entreprise efficaces, reportez-vous au livre blanc sur la planification complète d' [un déploiement Power bi entreprise](https://aka.ms/pbienterprisedeploy) .

Dans le contexte de l’objet de ce livre blanc, cette section présente et décrit les capacités, les types de contenu Power BI, les modes de stockage de modèles et les licences. Une bonne compréhension de ces rubriques est essentielle pour réussir le déploiement et la gestion de Power BI Premium.

### <a name="capacities"></a>Capacities

Les **capacités** sont un concept de Power bi principal qui représente un ensemble de ressources (stockage, processeur et mémoire) utilisées pour héberger et distribuer du contenu Power bi. Les capacités sont partagées ou dédiées. Une **capacité partagée** est partagée avec d’autres clients Microsoft, tandis qu’une **capacité dédiée** est entièrement validée pour un seul client. Les capacités dédiées sont présentées dans la rubrique [capacités Premium](#premium-capacities) .

Dans une capacité partagée, les charges de travail s’exécutent sur des ressources de calcul partagées avec d’autres clients. Étant donné que la capacité doit partager des ressources, des restrictions sont imposées à garantir une «bonne lecture», comme la taille maximale du modèle (1 Go) et la fréquence d’actualisation quotidienne maximale (huit fois par jour).

### <a name="workspaces"></a>Workspaces

Power BI espaces de travail se trouvent dans des capacités et représentent des conteneurs de sécurité, de collaboration et de déploiement. Chaque utilisateur Power BI dispose d’un espace de travail personnel nommé **Mon espace de travail**. Vous pouvez créer d’autres espaces de travail pour la collaboration et le déploiement. Ces espaces sont appelés **espaces de travail d’application**. Par défaut, les espaces de travail, y compris les espaces de travail personnels, sont créés dans la capacité partagée.

### <a name="power-bi-content-types"></a>Types de contenu Power BI

Pour présenter Power BI Premium rubriques, il est important de commencer par une discussion complète sur Power BI architecture, y compris les types de contenu fondamentaux.

Tout le contenu Power BI est stocké et géré dans les espaces de travail qui sont des conteneurs pour le contenu Power BI. Chaque utilisateur Power BI possède son propre espace de travail personnel, mais la meilleure pratique générale consiste à créer des espaces de travail d’application. Les espaces de travail d’application permettent la copropriété du contenu et la possibilité de collaborer sur le contenu. Ils offrent également la possibilité de déployer et de distribuer du contenu à un grand public en tant qu’applications.

Le contenu de Power BI suivant est stocké dans les espaces de travail:

- Dataflows
- Groupes de données
- Classeurs
- Rapports
- Tableaux de bord

#### <a name="dataflows"></a>Dataflows

Power BI flux aide les organisations à unifier les données à partir de sources disparates. Ils peuvent être considérés comme des données préparées et prédéfinies pour une utilisation dans les modèles, mais ils ne peuvent pas être utilisés directement comme source pour la création de rapports. Ils tirent parti de la collection complète de connecteurs de données Microsoft, ce qui permet l’ingestion de données à partir de sources de données locales et basées sur le Cloud.

Les flux peuvent être créés et gérés uniquement dans des espaces de travail d’application, et stockés en tant qu’entités dans le modèle de données commun (CDM) de Azure Data Lake Storage Gen2. En règle générale, elles sont planifiées pour s’actualiser régulièrement pour stocker des données à jour.

Pour plus d’informations, reportez-vous au document de [préparation des données en libre-service dans Power bi (version préliminaire)](service-dataflows-overview.md) .

#### <a name="datasets"></a>Groupes de données

Les jeux de données Power BI représentent une source de données prête pour la création de rapports et la visualisation. Il existe de nombreux types de datasets, créés par:

- Connexion à un modèle de données existant qui n’est pas hébergé dans une capacité de Power BI
- Chargement d’un fichier de Power BI Desktop qui contient un modèle
- Téléchargement d’un classeur Excel (contenant une ou plusieurs tables Excel et/ou modèle de données de classeur) ou téléchargement d’un fichier de valeurs séparées par des virgules (CSV)
- Utilisation de l’service Power BI pour créer un jeu de données de transmission, de diffusion en continu ou de diffusion en continu hybride

À l’exception des jeux \[de données de streaming [3](#endnote-03)\], le jeu de données représente un modèle de données qui tire parti des technologies de modélisation mature de Analysis Services.

Notez que dans la documentation, parfois, les jeux de données et les modèles terminologiques sont interchangeables. En règle générale, du point de vue du service Power BI, il s’agit d’un **jeu de données** , et d’un point de vue du développement, il est appelé **modèle**. Dans le contexte de ce livre blanc, il s’agit d’une grande partie de la même chose.

##### <a name="externally-hosted-models"></a>Modèles hébergés de manière externe

La connexion à un modèle hébergé en externe implique l’installation de la [passerelle de données locale](service-gateway-onprem.md) pour se connecter à SQL Server Analysis Services, qu’il s’agisse d’une infrastructure IaaS (infrastructure en tant que service) locale ou hébergée sur un ordinateur virtuel. Azure Analysis Services ne nécessite pas de passerelle. Ce scénario est souvent utile lorsque les investissements existants du modèle existent, en général faisant partie de la Data Warehouse d’entreprise (EDW). Il permet à Power BI d’effectuer une **connexion active** (LC) pour Analysis Services et le fait en appliquant des autorisations de données à l’aide de l’identité de l’utilisateur de rapport Power bi. Par SQL Server Analysis Services, les modèles multidimensionnels (cubes) et les modèles tabulaires sont pris en charge. Comme indiqué dans l’image suivante, un jeu de données de connexion active passe des requêtes à des modèles hébergés en externe.

![Un jeu de données de connexion active passe des requêtes à des modèles hébergés en externe](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>Modèles développés par Power BI Desktop

Power BI Desktop-une application cliente destinée au développement Power BI-peut être utilisée pour développer un modèle qui est en fait un modèle tabulaire Analysis Services. Les modèles peuvent être développés en important des données à partir de flux, qui peuvent ensuite être intégrés à d’autres sources de données. Bien que les spécificités relatives à la façon dont la modélisation peut être obtenue n’entrent pas dans le cadre de ce livre blanc, il est important de comprendre qu’il existe trois types de modèles différents (ou modes) qui peuvent être développés à l’aide de Power BI Desktop. Ces modes déterminent si les données sont importées dans le modèle ou si elles restent dans la source de données. Les trois modes sont: Import, DirectQuery et composite. Une description complète de chaque mode est traitée dans la rubrique [modes de stockage de modèles](#model-storage-modes) .

Les modèles et modèles hébergés en externe développés dans Power BI Desktop peuvent appliquer la sécurité au niveau des lignes (RLS) pour limiter les données qui peuvent être récupérées pour un utilisateur donné. Par exemple, les utilisateurs affectés au groupe de sécurité vendeurs peuvent uniquement afficher les données de rapport de la région de vente à laquelle ils sont affectés. Les rôles RLS peuvent être dynamiques ou statiques. Les **rôles dynamiques** sont filtrés par l’utilisateur du rapport, tandis que les **rôles statiques** appliquent les mêmes filtres pour tous les utilisateurs attribués au rôle.

##### <a name="excel-workbook-models"></a>Modèles de classeur Excel

La création de jeux de données basés sur des classeurs Excel ou des fichiers CSV entraînera la création automatique d’un modèle. Les tables Excel et les données CSV seront importées pour créer des tables de modèle, tandis qu’un modèle de données de classeur Excel sera transposé pour créer un modèle de Power BI. Dans tous les cas, les données de fichier sont importées dans un modèle.

Les distinctions, ensuite, peuvent être effectuées sur Power BI jeux de données qui représentent des modèles:

- Ils sont hébergés dans le service Power BI ou sont hébergés en externe par Analysis Services
- Ils peuvent stocker des données importées ou émettre des demandes de requête directe à des sources de données sous-jacentes, ou une combinaison des deux

Voici un résumé des faits importants concernant les jeux de données Power BI qui représentent des modèles:

- SQL Server Analysis Services les modèles hébergés requièrent une passerelle pour exécuter des requêtes LC
- Modèles hébergés par Power BI qui importent des données
  - Doit être entièrement chargé en mémoire afin qu’il puisse être interrogé
  - Exiger l’actualisation pour conserver les données à jour et doit impliquer des passerelles lorsque les données sources ne sont pas accessibles directement via Internet
- Les modèles hébergés par Power BI qui utilisent le mode de stockage DirectQuery (DQ) requièrent la connectivité aux données sources. Lorsque le modèle est interrogé, Power BI émet des requêtes aux données sources pour récupérer les données actuelles. Ce mode doit impliquer des passerelles lorsque les données sources ne sont pas directement accessibles sur Internet.
- Les modèles peuvent appliquer des règles RLS, en appliquant des filtres pour limiter l’accès aux données à certains utilisateurs

Pour réussir le déploiement et la gestion de Power BI Premium, il est important de comprendre où les modèles sont hébergés, le mode de stockage, les dépendances sur les passerelles, la taille des données importées, ainsi que le type et la fréquence d’actualisation. Ils peuvent tous avoir un impact significatif sur les ressources de Power BI Premium. En outre, la conception du modèle lui-même, y compris ses requêtes et calculs de préparation des données, peut s’ajouter à la combinaison de considérations.

Il est également important de comprendre que les modèles d’importation hébergés par Power BI peuvent être actualisés en fonction de la planification ou déclenchés à la demande par un utilisateur dans le service Power BI.

La conception de modèles optimisés est décrite plus loin dans ce document technique dans la rubrique [optimisation des modèles](#optimizing-models) .

#### <a name="workbooks"></a>Workbooks

Les classeurs Power bi sont un type \[de contenu Power bi [4](#endnote-04)\]. Il s’agit de classeurs Excel qui ont été téléchargés vers le service Power BI et ne doivent pas être confondus avec les classeurs Excel chargés qui créent des jeux de données (modèles). Le type de contenu classeur représente une connexion à un classeur, qui peut être téléchargé vers le service Power BI ou rester dans le stockage cloud sur OneDrive ou SharePoint Online.

Il est important de comprendre que ce type de contenu n’est pas disponible en tant que source de données pour Power BI les visualisations de données. Au lieu de cela, il peut être ouvert en tant que classeur dans le service Power BI à l’aide d’Excel online. L’objectif principal de ce type de contenu est de permettre aux rapports de classeur Excel hérités d’être accessibles à partir de la service Power BI et d’autoriser l’épinglage de ses visualisations de données à Power BI tableaux de bord.

Pour plus d’informations, reportez-vous au document [obtenir des données à partir des fichiers de classeur Excel](service-excel-workbook-files.md) .

#### <a name="reports"></a>Rapports

Il existe deux types de rapports: Power BI des rapports et des rapports paginés.

Les **rapports de Power bi** fournissent une expérience de visualisation interactive des données qui se connecte à un seul jeu de données. Les rapports sont souvent conçus pour encourager la participation des utilisateurs, ce qui leur permet d’interagir avec un ensemble exceptionnel de fonctionnalités, notamment le filtrage, le découpage, le filtrage croisé et la mise en surbrillance, l’exploration, l’exploration, l’extraction, le perçage, Q & un naturel questions sur la langue, Focus, navigation entre les pages, mise en évidence, affichage des signets, et bien plus encore.

Dans le contexte de ce livre blanc, il est important de comprendre comment l’architecture Power BI, la conception de rapports Power BI et les interactions utilisateur peuvent tous avoir un impact sur les ressources de service Power BI:

- Pour charger et interagir avec des rapports basés sur des modèles d’importation, le modèle doit être entièrement chargé en mémoire (qu’il soit hébergé dans le service Power BI ou hébergé en externe).
- Chaque visuel de rapport émet une requête pour récupérer des données en interrogeant le modèle
- En règle générale, les interactions de filtre et de segment impliquent l’interrogation du modèle. Par exemple, si vous modifiez une sélection de segment, par défaut, vous devez recharger chaque élément visuel sur la \[page [5](#endnote-05)\]
- Les rapports de Power BI ne garantissent pas l’affichage des données actuelles et peuvent obliger l’utilisateur à actualiser le rapport pour recharger la page de rapport et ses éléments visuels
- Les utilisateurs peuvent s’associer à Q & une fonctionnalité en langage naturel pour poser des questions, en fournissant la conception de rapport Power BI et le jeu de données représente un modèle d’importation de données hébergé par un Power BI ou un jeu de données LC configuré pour activer Q & A

Les **rapports paginés** autorisent la publication et le rendu des rapports SQL Server Reporting Services (\*SSRS) (format. rdl). Comme leur nom l’indique, les rapports paginés sont couramment utilisés lorsque les exigences imposent la nécessité d’imprimer sur une taille de page fixe ou lorsqu’il existe des listes variables de données qui doivent être entièrement développées. Par exemple, une facture conçue pour le rendu de plusieurs pages (au lieu de faire défiler un visuel) et l’impression.

Les deux types de rapports pris en charge offrent le choix aux auteurs de rapports, ce qui leur permet de sélectionner le type en fonction des exigences et de l’utilisation prévue. En règle générale, les rapports Power BI sont idéaux pour des expériences interactives permettant à l’utilisateur d’explorer et de découvrir des informations à partir de données, tandis que les rapports paginés sont mieux adaptés aux mises en page pilotées par des paramètres.

Quel que soit le type de rapport, il est impératif de disposer d’une expérience utilisateur fiable et performante pour obtenir des mises à jour de données et de charge de rapport réactives (lorsque des filtres ou des paramètres sont modifiés).

#### <a name="dashboards"></a>Tableaux de bord

Les tableaux de bord Power BI sont conçus pour fournir des expériences de surveillance et sont conceptuellement très différents des rapports Power BI. Les tableaux de bord sont conçus pour s’afficher sur un seul volet de verre pour exprimer des valeurs et des visualisations de données dans des vignettes. En règle générale, les tableaux de bord offrent moins d’expériences d’interaction que les rapports Power BI, avec certaines conceptions de tableaux de bord qui n’attendent aucune interaction. Par exemple, un tableau de bord sans assistance présenté sur un écran non tactile dans une salle de serveurs. Une autre différence importante réside dans le fait que les tableaux de bord peuvent présenter des vignettes qui proviennent de données provenant de plusieurs DataSets, tandis qu’un rapport de Power BI ne peut être basé que sur un seul jeu de données.

Il est important de comprendre qu’un tableau de bord est conçu pour se charger rapidement et pour exprimer en permanence les données les plus récentes (connues de l’service Power BI). Pour ce faire, il met en cache les résultats de la requête de vignette et le fait pour chaque tableau de bord. En fait, il doit effectuer cette opération pour chaque utilisateur ayant accès à un tableau de bord basé sur des modèles qui appliquent la sécurité de la sécurité dynamique.

Le service Power BI met automatiquement à jour les caches de requête du tableau de bord immédiatement après l’actualisation des modèles d’importation hébergés sur Power BI. Dans le cas des modèles LC et DQ, le propriétaire du jeu de données dispose d’un degré de contrôle sur la fréquence à laquelle le service Power BI met à jour le cache, qui peut être configuré aussi souvent que toutes les 15 minutes, ou aussi rarement qu’une fois par semaine. Notez que les mises à jour du cache de requête LC interrogent d’abord les métadonnées du modèle pour déterminer si l’actualisation du modèle a eu lieu depuis la dernière mise à jour du cache, et ne poursuit pas la mise à jour du cache quand aucune actualisation n’a eu lieu depuis. Cette vérification n’est pas possible pour les modèles DQ. par conséquent, les mises à jour du cache ont lieu si les données sources ont été modifiées ou non.

Les mises à jour du cache de requête du tableau de bord basées sur les modèles DQ et LC peuvent avoir un impact significatif sur les ressources service Power BI et les sources de données externes. Prenons l’exemple d’un tableau de bord avec 20 vignettes, toutes basées sur un modèle de Azure Analysis Services qui applique la sécurité au niveau des lignes et qui est actualisée toutes les heures, et que ce tableau de bord est partagé avec 100 utilisateurs. Si le jeu de données est configuré pour s’actualiser toutes les heures, cela entraînerait au moins 2000 (20 x 100) requêtes LC. Cela peut entraîner une charge énorme sur le service Power BI et les sources de données externes, et il peut également dépasser les limites imposées aux ressources disponibles. Les ressources et les limites de capacité sont décrites dans la rubrique nœuds de [capacité](#capacity-nodes) .

Les utilisateurs peuvent interagir avec un tableau de bord de différentes façons, ce qui nécessite des ressources service Power BI. Plus précisément, ils peuvent:

- Déclencher une actualisation des vignettes de tableaux de bord, ce qui peut entraîner une actualisation à la demande de tous les modèles d’importation de données Power BI hébergées
- Faites appel à Q & une fonctionnalité en langage naturel pour poser des questions (en fournissant la conception du tableau de bord, et le jeu de données est un modèle d’importation de données hébergé Power BI ou un jeu de données LC configuré pour activer Q & A)
- Utilisez la fonctionnalité Quick Insights pour que Power BI Découvrez des Insights à partir d’un jeu de données sous-jacent et répondez avec des visuels qui les affichent et les décrivent (à condition que la vignette soit basée sur un DataSet qui est un modèle d’importation de données hébergé par Power BI)
- Configurez des alertes sur les vignettes du tableau de bord, en exigeant que le service Power BI compare les seuils aux valeurs des vignettes (parfois aussi souvent que toutes les heures) et notifie les utilisateurs lorsque les seuils sont dépassés (à condition que la vignette affiche une valeur numérique unique et soit basée sur un DataSet Power BI modèle d’importation de données hébergées par l’hôte)

### <a name="model-storage-modes"></a>Modes de stockage des modèles

Rappelez-vous que Power BI Desktop permet de développer un modèle dans l’un des trois modes. Il est important de comprendre le raisonnement pour chaque mode de stockage de modèle de données et les impacts possibles sur les ressources de service Power BI. Cette section présente les trois modes. Celles-ci seront abordées plus en détail plus loin dans ce livre blanc dans la rubrique Optimisation des modèles.

#### <a name="import-mode"></a>Mode d’importation

Le mode d’importation est le mode le plus courant utilisé pour développer des modèles en raison des performances extrêmement rapides associées à l’interrogation en mémoire, à la flexibilité de conception disponible pour les modélisateurs et à la prise en charge de fonctionnalités de service Power BI spécifiques (Q & A, Quick Insights , etc.). Il s’agit du mode par défaut lors de la création d’une solution de Power BI Desktop.

Il est important de comprendre que les données importées sont toujours stockées sur le disque et qu’elles doivent être entièrement chargées en mémoire pour être interrogées ou actualisées. Une fois en mémoire, les modèles d’importation permettent d’obtenir des résultats de requête extrêmement rapides. Il est également important de comprendre qu’aucun concept de modèle d’importation n’est partiellement chargé en mémoire.

Une fois actualisées, les données sont compressées et optimisées, puis stockées sur le disque par le moteur de stockage VertiPaq. Lorsqu’elles sont chargées à partir du disque en mémoire, il est possible de voir une compression 10x, et il est donc raisonnable de s’attendre à ce que 10 Go de données sources puissent être compressés à une taille d’environ 1 Go. La taille de stockage sur disque peut atteindre une réduction de 20% par-dessus. \[[6,3](#endnote-06)\]

La souplesse de conception peut être obtenue de trois façons. Les modélisateurs de données peuvent:

- Intégrer des données en mettant en cache des données à partir de plusieurs sources de données, quel que soit le type et le format de la source de données
- Tirez parti de l’ensemble complet des fonctions de Power Query langage de formule (appelées de manière informelle) lors de la création de requêtes de préparation des données
- Tirez parti de l’ensemble des fonctions DAX (Data Analysis Expressions) pour améliorer le modèle avec la logique métier, obtenue avec des colonnes calculées, des tables calculées et des mesures

Comme indiqué dans l’image suivante, un modèle d’importation peut intégrer des données à partir de n’importe quel nombre de types de sources de données pris en charge.

![Un modèle d’importation peut intégrer des données à partir de n’importe quel nombre de types de sources de données pris en charge](media/whitepaper-premium-deployment/import-model.png)

Toutefois, bien qu’il y ait des avantages intéressants associés aux modèles d’importation, il y a également des inconvénients:

- La totalité du modèle doit être chargée dans la mémoire avant que Power BI puisse interroger le modèle, ce qui peut placer de la pression sur les ressources disponibles à mesure que le nombre et la taille des modèles augmentent.
- Les données de modèle sont uniquement actualisées, et les modèles d’importation doivent donc être actualisés, de préférence sur une base planifiée
- Une actualisation complète supprime toutes les données de toutes les tables et les recharge à partir de la source de données. Cela peut être très coûteux en termes de temps et de ressources pour le service Power BI et la ou les sources de données. Power BI prend en charge l’actualisation incrémentielle, ce qui peut éviter la troncation et le rechargement de tables entières, ce qui est abordé dans la rubrique [optimisation des modèles hébergés](#optimizing-power-bi-hosted-models) sur les Power bi.

Du point de vue des ressources de service Power BI, les modèles d’importation requièrent:

- Mémoire suffisante pour charger le modèle lorsqu’il est interrogé ou actualisé
- Ressources de traitement et ressources mémoire supplémentaires pour actualiser les données

#### <a name="directquery-mode"></a>Mode DirectQuery

Les modèles développés en mode DirectQuery (DQ) n’importent pas de données. Au lieu de cela, ils se composent uniquement de métadonnées qui, lorsque interrogé, émet des requêtes natives à la source de données sous-jacente.

![Un modèle DirectQuery émet des requêtes natives à la source de données sous-jacente](media/whitepaper-premium-deployment/direct-query-model.png)

Il existe deux raisons principales pour envisager le développement d’un modèle DQ. La première raison est lorsque les volumes de données sont trop importants, même lorsque les méthodes de réduction des données sont appliquées, pour charger dans un modèle ou presque l’actualisation. La deuxième raison est que les rapports et les tableaux de bord doivent fournir des données en temps quasi-réel, au-delà de ce qui peut être atteint dans les limites d’actualisation planifiée (48 fois par jour pour une capacité dédiée).

Il existe plusieurs avantages associés aux modèles DQ:

- Les limites de taille du modèle d’importation ne s’appliquent pas
- Les modèles ne nécessitent pas d’actualisation
- Les utilisateurs de rapports voient les données les plus récentes lorsqu’ils interagissent avec les filtres et les segments de rapport et peuvent actualiser le rapport entier pour récupérer les données actuelles
- Les vignettes de tableau de bord, lorsqu’elles sont basées sur les modèles DQ, peuvent être mises à jour automatiquement toutes les 15 minutes

Toutefois, il existe de nombreux inconvénients et limitations associés aux modèles DQ:

- Le modèle doit être basé sur une seule source de données prise en charge et, par conséquent, toute intégration de données doit déjà être effectuée dans la source de données. Les sources de données prises en charge sont les systèmes relationnels et analytiques, avec \[la prise en charge de nombreux magasins de données populaires [7](#endnote-07)\].
- Les performances peuvent être lentes, ce qui peut avoir un impact négatif sur la service Power BI (les requêtes peuvent être très gourmandes en ressources processeur) et sur la source de données (qui peut ne pas être optimisée pour les requêtes analytiques)
- Les requêtes Power Query ne peuvent pas être trop complexes et sont limitées à M expressions et fonctions qui peuvent être transposées à des requêtes natives comprises par la source de données
- Les fonctions DAX sont limitées à celles qui peuvent être transposées à des requêtes natives comprises par la source de données, et il n’existe pas de prise en charge des tables calculées ou des fonctions Time Intelligence intégrées
- Par défaut, les requêtes de modèle qui nécessitent une récupération de plus de 1 million lignes échouent
- Les rapports et les tableaux de bord avec plusieurs visuels peuvent afficher des résultats incohérents, en particulier lorsque la source de données est volatile.
- Q & A et Quick Insights ne sont pas pris en charge

Du point de vue des ressources service Power BI, les modèles DQ requièrent les éléments suivants:

- Mémoire minimale pour charger le modèle (métadonnées uniquement) lors de l’interrogation
- Des ressources de processeur importantes pour générer et traiter des requêtes envoyées à la source de données

Pour plus d’informations, reportez-vous au document [utiliser une requête directe dans Power bi Desktop](desktop-use-directquery.md) .

#### <a name="composite-mode"></a>Mode composite

Les modèles développés en mode composite permettent de configurer le mode de stockage des tables de modèle individuelles. Par conséquent, il prend en charge une combinaison de tables import et DQ. Il prend également en charge les tables calculées (définies avec DAX) et plusieurs sources de données DQ.

Le mode de stockage de table peut être configuré en tant qu’importation, DirectQuery ou double. Une table configurée en mode double stockage est à la fois import et DirectQuery, ce qui permet au service Power BI de déterminer le mode le plus efficace à utiliser sur une requête en fonction de la requête.

![Un modèle composite est une combinaison de modes de stockage import et DQ, configurée au niveau de la table.](media/whitepaper-premium-deployment/composite-model.png)

Les modèles composites s’efforcent de fournir le meilleur des modes importation et DirectQuery. Lorsqu’elles sont configurées de manière appropriée, elles peuvent combiner des performances de requête élevées des modèles en mémoire avec la possibilité de récupérer des données en quasi temps réel à partir de sources de données.

Les modélisateurs de données qui développent des modèles composites sont susceptibles de configurer des tables de type dimension en mode d’importation ou double et en mode DirectQuery. Par exemple, considérez un modèle avec une table de type dimension de produit en mode double et une table de type fait de vente en mode DirectQuery. La table Product peut être interrogée de manière efficace et rapide à partir de la mémoire pour afficher un segment de rapport. La table Sales peut ensuite être interrogée en mode DirectQuery jointe à la table Product associée. La dernière requête peut permettre la génération d’une seule requête Native efficace pour joindre les tables Product et sales et filtrer les valeurs de segment.

En général, les avantages et les inconvénients associés à chaque mode de modèle peuvent être considérés comme s’appliquant au mode de stockage de table dans les modèles composites.

Pour plus d’informations, reportez-vous à la rubrique [utiliser des modèles composites dans Power bi Desktop](desktop-composite-models.md) document.

### <a name="licensing"></a>Gestion des licences

Power BI a trois licences:

- Power BI (version gratuite)
- Power BI Pro
- Power BI Premium

Le **Power bi licence gratuite** permet à un utilisateur de se connecter au service Power bi et de travailler dans son espace de travail personnel en publiant des modèles et des rapports. Il est important de comprendre qu’il n’est pas possible de partager du contenu Power BI à l’aide de cette licence. Cette licence, comme son nom le suggère, est gratuite.

La licence **Power bi Pro** permet à une personne de créer et de collaborer dans des espaces de travail d’application et de partager et distribuer du contenu Power bi. Ils peuvent également configurer l’actualisation pour que leurs jeux de données maintiennent automatiquement les données à jour, y compris à partir de sources de données locales. En outre, ils peuvent auditer et régir le mode d’accès et d’utilisation des données. Cette licence est nécessaire pour recevoir du contenu partagé par d’autres utilisateurs, sauf si l’utilisateur est associé à une capacité Power BI Premium dédiée.

La licence **Power bi Premium** est une licence au niveau du locataire. elle est décrite dans la section [Présentation de Power bi Premium](#introducing-power-bi-premium) .

Pour plus d’informations sur les licences Power BI, consultez la page de [tarification Power bi](https://powerbi.microsoft.com/pricing/) .

## <a name="introducing-power-bi-premium"></a>Présentation de Power BI Premium

Power BI Premium fournit une plate-forme unifiée libre-service et d’entreprise BI avec mise à l’échelle, des performances fiables et des coûts prévisibles. Pour ce faire, il fournit principalement des ressources dédiées pour exécuter les service Power BI pour votre organisation.

En outre, Power BI Premium propose de nombreuses fonctionnalités d’entreprise:

- La distribution de contenu économique, qui permet de partager du contenu Power BI avec un nombre illimité d’utilisateurs Power BI gratuits, y compris les utilisateurs externes
- Prise en charge des jeux \[de données volumineux [8](#endnote-08)\]
- Taux d’actualisation plus élevé des flux et des jeux de données (jusqu’à 48 fois par jour)
- Actualisation incrémentielle des flux et des jeux de données
- Les entités liées du flux de données et l’exécution parallèle des transformations
- Rapports paginés
- Power BI Report Server, pour la création de rapports locaux
- Possibilité d’incorporer du contenu dans des applications pour le compte des utilisateurs de l’application (PaaS)

La plupart de ces fonctionnalités peuvent être utilisées pour fournir des solutions d’entreprise efficaces et évolutives et sont couvertes dans la section [optimisation des capacités Premium](#optimizing-premium-capacities) .

### <a name="subscriptions-and-licensing"></a>Abonnements et licences

Power BI Premium est disponible via un abonnement Office 365 au niveau du locataire, avec deux familles de références SKU :

- **Em** Références SKU (EM1-EM3) pour l’incorporation, nécessitant un engagement annuel, facturé mensuellement
- **P** SKU (P1-P3) pour l’incorporation et les fonctionnalités d’entreprise, nécessitant un engagement mensuel ou annuel, facturé mensuellement et incluant une licence d’installation Power bi Report Server locale

Une autre approche consiste à acheter un abonnement Azure Power BI Embedded qui possède une famille de références SKU unique: Références (a1-a6) à des fins d’incorporation et de test de capacité uniquement.

Toutes les références SKU fournissent des v-cores \[pour créer des capacités [9](#endnote-09)\], mais les références (SKU) em sont limitées pour une incorporation plus réduite. Bien que ce livre blanc se concentre sur les références SKU P, la plupart des sujets abordés sont également pertinents pour les références SKU A.

Contrairement aux références SKU des abonnements Premium, les références SKU Azure n’impliquent aucune durée d’engagement et sont facturées à l’heure. Ils sont entièrement flexibles, vous permettant d’effectuer un scale-up, un scale-down, une suspension, une reprise et une suppression à tout moment.

Azure Power BI Embedded est en grande partie hors de portée pour ce livre blanc, mais il est abordé dans la rubrique approches de test en tant qu’option pratique et économique pour tester et mesurer les charges de travail.

Pour plus d’informations sur les références (SKU) Azure, reportez-vous à la [documentation azure Power bi Embedded](/azure/power-bi-embedded/).

Les abonnements Power BI Premium peuvent être achetés par les administrateurs dans le centre d’administration Microsoft 365. Plus précisément, seuls les administrateurs généraux Office 365 ou les administrateurs de facturation peuvent acheter des références SKU.

Une fois acheté, le locataire reçoit un nombre correspondant de v-cores à affecter aux capacités. ce nom est appelé « **regroupement v-Core**». Par exemple, l’achat d’une référence SKU P3 fournit au locataire 32 v-cores.

Pour plus d’informations, reportez-vous au document [Comment acheter Power bi Premium](service-admin-premium-purchase.md) .

### <a name="premium-capacities"></a>Capacités Premium

Contrairement à une capacité partagée où les charges de travail s’exécutent sur des ressources de calcul partagées avec d’autres clients, une **capacité dédiée** est réservée à une utilisation exclusive par une organisation. Il est isolé avec des ressources de calcul dédiées qui offrent des performances fiables et cohérentes pour le contenu hébergé.

Ce livre blanc se concentre sur la **capacité Premium** , ce qui signifie qu’il est associé à l’une des références em ou P.

#### <a name="capacity-nodes"></a>Nœuds de capacité

Comme décrit dans la rubrique abonnements et licences, il existe deux familles de Power BI Premium SKU: EM et P. Toutes les références SKU Power BI Premium sont disponibles en tant que nœuds de capacité, chacune représentant une quantité définie de ressources comprenant le processeur, la mémoire et le stockage. En plus des ressources, chaque référence (SKU) a des limites opérationnelles sur le nombre de connexions DirectQuery (DQ) et de connexion active (LC) par seconde, ainsi que le nombre d’actualisations de modèles parallèles.

Le traitement est effectué par un nombre défini de v-cores, répartis équitablement entre le back-end et le front-end.

Les **v-cores back-end** gèrent l’essentiel des fonctionnalités Power BI : traitement des requêtes, gestion du cache, exécution des services R, actualisation des modèles, traitement en langage naturel (questions-réponses), et rendu côté serveur des rapports et des images. Une quantité fixe de mémoire principale utilisée pour héberger des modèles, également appelés jeux de données actifs, est affectée aux v-cœurs principaux.

Les **v-cœurs frontend** sont responsables du service Web, du tableau de bord et de la gestion des documents de rapports, de la gestion des droits d’accès, de la planification, des API, des chargements et téléchargements, et en général de tout ce qui concerne l’expérience utilisateur.

Le stockage est défini à 100 to par nœud de capacité.

Les ressources et les limites de chaque référence (SKU) Premium (et dimensionnées de façon équivalente) sont décrites dans le tableau suivant.

| Nœuds de capacité | Total des v-cores | Cœurs virtuels backend | RAM (Go) | Cœurs virtuels frontend | DQ/LC (par seconde) | Parallélisme des actualisations de modèles |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5\. | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6\. |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>Charges de travail de capacité

Les charges de travail de capacité sont des services mis à la disposition des utilisateurs. Par défaut, les capacités Premium et Azure prennent uniquement en charge une charge de travail de jeu de données associée à l’exécution de requêtes Power BI qui ne peuvent pas être désactivées.

Des charges de travail supplémentaires peuvent être activées pour les rapports paginés, flux et IA. Chaque charge de travail supplémentaire requiert la configuration de la mémoire maximale (en pourcentage de la mémoire disponible totale) pouvant être utilisée par la charge de travail.

#### <a name="how-capacities-function"></a>Fonction des capacités

À tout moment, le service Power BI s’efforce de tirer le meilleur parti des ressources de capacité tout en ne dépassant pas les limites imposées à la capacité.

Les opérations de capacité sont classées comme étant interactives ou en arrière-plan. Les opérations interactives incluent l’affichage des requêtes et la réponse aux interactions utilisateur (filtrage, interrogation questions-réponses, etc.). En règle générale, l’interrogation du modèle d’importation est gourmande en ressources mémoire, tandis que l’interrogation des modèles LC/DQ est gourmande en ressources processeur. Les opérations d’arrière-plan incluent les actualisations des modèles de flux de données et d’importation, ainsi que la mise en cache des requêtes.

Il est important de comprendre que les opérations interactives sont toujours prioritaires sur les opérations en arrière-plan pour garantir une expérience utilisateur optimale. Si les ressources sont insuffisantes, les opérations d’arrière-plan sont ajoutées à une file d’attente en vue d’être traitées lorsque les ressources auront été libérées. Les opérations d’arrière-plan, telles que les actualisations de jeu de données et les fonctions IA, peuvent être arrêtées au milieu du processus par le service Power BI et ajoutés à une file d’attente.

Les modèles d’importation doivent être entièrement chargés en mémoire afin de pouvoir être interrogés ou actualisés. Le service Power BI gère l’utilisation de la mémoire à l’aide d’algorithmes sophistiqués pour garantir une utilisation maximale de la mémoire disponible et peut faire dépasser la capacité: Bien qu’il soit possible pour une capacité de stocker de nombreux modèles d’importation (jusqu’à 100 to par capacité Premium), lorsque leur stockage sur disque combiné dépasse la mémoire prise en charge (et que de la mémoire supplémentaire est nécessaire pour l’interrogation et l’actualisation), elles ne peuvent pas toutes être chargées en mémoire à même temps.

Les modèles d’importation sont donc chargés dans et supprimés de la mémoire en fonction de leur utilisation. Un modèle d’importation est chargé lorsqu’il est interrogé (opération interactive) et pas encore en mémoire, ou lorsqu’il doit être actualisé (opération en arrière-plan).

La suppression d’un modèle de la mémoire est appelée **éviction** et il s’agit d’une opération qui Power bi peut être exécutée rapidement en fonction de la taille des modèles. Si la capacité ne subit aucune pression liée à la mémoire, les modèles sont simplement chargés en mémoire et y restent. \[[10 Toutefois,](#endnote-10) lorsque la mémoire disponible est insuffisante pour charger un modèle, le service Power bi doit d’abord libérer de la mémoire.\] Il libère de la mémoire en détectant les modèles qui ont été inactifs en recherchant des modèles qui n’ont pas été utilisés au \[cours des trois dernières minutes [11](#endnote-11)\], puis les suppriment. S’il n’y a aucun modèle inactif à supprimer, le service Power BI cherche à supprimer les modèles qui ont été chargés pour des opérations d’arrière-plan. Cela peut inclure l’éviction des charges de travail en arrière-plan, comme la charge de travail d’intelligence artificielle. En dernier recours, après 30 secondes d’échecs de \[tentative [11](#endnote-11)\], est l’échec de l’opération interactive. Dans ce cas, l’utilisateur du rapport est informé normalement de l’échec avec une suggestion pour réessayer dans un instant.

Il est important de souligner que l’éviction du jeu de données est un comportement normal et attendu. Il s’efforce d’optimiser l’utilisation de la mémoire en chargeant et en déchargeant des modèles dont les tailles combinées peuvent dépasser la quantité de mémoire disponible. Ce comportement est prévu et les utilisateurs du rapport en sont informés. Un taux élevé d’évictions ne signifie pas nécessairement que la capacité ne contient pas suffisamment de ressources. Cela peut toutefois constituer un problème si la réactivité des actualisations ou des requêtes souffre de ces évictions.

Les actualisations des modèles d’importation sont toujours gourmandes en mémoire, car les modèles doivent être chargés en mémoire et une mémoire supplémentaire est nécessaire pour le traitement. Une actualisation complète peut utiliser environ le double de la mémoire nécessaire au modèle. Cela permet de s’assurer que le modèle peut être interrogé même lors de son traitement (les requêtes sont envoyées au modèle existant, jusqu’à ce que l’actualisation soit terminée et que les nouvelles données de modèle soient disponibles). Notez que l’actualisation incrémentielle requiert moins de mémoire et peut se terminer plus rapidement, ce qui peut réduire considérablement la pression sur les ressources de capacité. Les actualisations de modèles peuvent elles aussi solliciter le processeur de manière importante, en particulier pour les modèles qui contiennent des transformations Power Query complexes, ou des tables/colonnes calculées qui sont complexes ou basées sur des tables volumineuses.

Actualise les requêtes de type: nécessitent le chargement du modèle en mémoire. Si la mémoire est insuffisante, le service Power BI tente de supprimer les modèles inactifs, et si ce n’est pas possible (si tous les modèles sont actifs), l’actualisation est mise en file d’attente. Les actualisations sont généralement très gourmandes en ressources processeurs, et même plus que les requêtes. Pour cette raison, il existe des limites quant au nombre d’actualisations qui peuvent être effectuées simultanément. Ce nombre est égal à une fois et demi le nombre de v-cores back-end, arrondi au nombre supérieur. Si les actualisations simultanées sont trop nombreuses, une actualisation planifiée est mise en file d’attente. Dans de telles situations, l’actualisation met plus de temps à se terminer. Notez que les actualisations à la demande (déclenchées par une demande de l’utilisateur ou un appel d’API) \[réessaient trois fois [11](#endnote-11)\], puis échouent s’il n’y a toujours pas suffisamment de ressources.

## <a name="managing-power-bi-premium"></a>Gestion des Power BI Premium

La gestion des Power BI Premium implique l’achat d’abonnements et la création, la gestion et la surveillance des capacités Premium.

### <a name="creating-and-managing-capacities"></a>Création et gestion des capacités

La page **paramètres de capacité** du **Power bi** portail d’administration affiche le nombre de v-cores achetés et disponibles (c’est-à-dire qu’ils sont déjà affectés à une capacité) et répertorie les capacités Premium. La page permet aux administrateurs généraux Office 365 ou aux administrateurs de service Power BI de créer des capacités Premium à partir de v-cores disponibles ou de modifier les capacités Premium existantes.

Lors de la création d’une capacité Premium, l’administrateur doit définir les éléments suivants:

- Nom de la capacité (unique au sein du locataire)
- Administrateur (s) de capacité
- Taille de la capacité
- Région pour la résidence \[des données [12](#endnote-12)\]

Au moins un administrateur de capacité doit être affecté. Les utilisateurs affectés en tant qu’administrateurs de la capacité peuvent:

- Affecter des espaces de travail à la capacité
- Gérer les autorisations utilisateur, pour ajouter des administrateurs de capacité supplémentaires ou des utilisateurs disposant d’autorisations d’affectation (pour leur permettre d’affecter des espaces de travail à la capacité)
- Gérer les charges de travail, pour configurer l’utilisation maximale de la mémoire pour les rapports paginés et les charges de travail flux
- Redémarrez la capacité pour réinitialiser toutes les opérations en cas de \[surcharge système [13](#endnote-13)\]

Les administrateurs de capacité ne peuvent pas accéder au contenu de l’espace de travail (sauf autorisation explicite de l’espace de travail) et ils n’ont pas accès à tous les Power BI zones d’administration (sauf attribution explicite), telles que les métriques d’utilisation, les journaux d’audit ou les paramètres du locataire. Important, les administrateurs de capacité ne sont pas autorisés à créer de nouvelles capacités ou à mettre à l’échelle des capacités existantes. En outre, elles sont affectées en fonction de la capacité, garantissant qu’elles ne peuvent afficher et gérer que les capacités auxquelles elles sont affectées.

La taille de la capacité doit être sélectionnée à partir d’une liste d’options SKU disponibles qui est restreinte par le nombre de cœurs disponibles dans le pool. Il est possible de créer plusieurs capacités à partir du pool qui peuvent être issues d’une ou de plusieurs références (SKU) achetées. Par exemple, une référence (SKU) P3 (32 v-cores) peut être utilisée pour créer trois capacités: un P2 (16 v-cœurs) et deux P1 (2 x 8 v-cœurs). Il est possible d’améliorer les performances et la mise à l’échelle en créant des capacités de taille inférieure, et cette rubrique est présentée dans la section [optimisation des capacités Premium](#optimizing-premium-capacities) . L’illustration suivante montre un exemple de configuration de l’organisation fictive contoso composée de cinq capacités Premium (3 x P1 et 2 x P3) avec chaque espace de travail d’application, ainsi que plusieurs espaces de travail dans une capacité partagée.

![Exemple de configuration pour l’organisation fictive contoso](media/whitepaper-premium-deployment/contoso-organization-example.png)

Une capacité Premium peut être assignée à une région autre que la région d’hébergement du locataire Power BI, fournissant ainsi un contrôle administratif sur les centres de données (dans les régions géographiques définies) Power BI qui résident. \[[douze](#endnote-12)\]

Service Power BI administrateurs et les administrateurs généraux Office 365 peuvent modifier les capacités Premium. Plus précisément, ils peuvent:

- Modifiez la taille de la capacité pour augmenter ou réduire la taille des ressources. Toutefois, il n’est pas possible de rétrograder une référence (SKU) P vers une référence EM, ou de mettre à niveau le vice versa.
- Ajouter ou supprimer des administrateurs de capacité
- Ajouter ou supprimer des utilisateurs disposant d’autorisations d’affectation
- Ajouter ou supprimer des charges de travail supplémentaires
- Modifier les régions

Des autorisations d’affectation sont requises pour affecter un espace de travail à une capacité Premium spécifique. Les autorisations peuvent être accordées à l’ensemble de l’organisation, à des utilisateurs ou à des groupes spécifiques.

Par défaut, les capacités Premium prennent en charge les charges de travail associées à l’exécution de requêtes Power BI. Il prend également en charge trois charges de travail supplémentaires: **Rapports paginés**, **flux**et **IA**. Chaque charge de travail nécessite la configuration de la mémoire maximale (en pourcentage de la mémoire disponible totale) pouvant être utilisée par la charge de travail. Il est important de comprendre que l’amélioration de l’allocation de mémoire maximale peut avoir un impact sur le nombre de modèles actifs qui peuvent être hébergés et le débit des actualisations.

La mémoire est allouée dynamiquement aux flux de données, mais elle est allouée statiquement aux rapports paginés. La raison de l’allocation statique de la mémoire maximale est que les rapports paginés s’exécutent dans un espace contenu sécurisé de la capacité. Vous devez veiller à définir la mémoire paginée des rapports, car elle réduit la mémoire disponible pour le chargement des modèles.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Rapports paginés | S.O. | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| Dataflows | 20 % par défaut ; 8 % minimum  | 20 % par défaut ; 4 % minimum  | 20 % par défaut ; 2 % minimum | 20 % par défaut ; 1 % minimum  |
| Intelligence artificielle | S.O. | 20% par défaut; 20% minimum  | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum  |
| | | | | |

La suppression d’une capacité Premium est possible et n’entraîne pas la suppression de ses espaces de travail et de son contenu. Au lieu de cela, les espaces de travail affectés sont déplacés vers une capacité partagée. Lorsque la capacité Premium a été créée dans une autre région, l’espace de travail est déplacé vers la capacité partagée de la région d’hébergement.

### <a name="assigning-workspaces-to-capacities"></a>Affectation d’espaces de travail à des capacités

Les espaces de travail peuvent être attribués à une capacité Premium dans le**portail** d' **administration Power bi**ou-pour un espace de travail d’application, dans le volet **espace de travail** .

Les administrateurs de capacité, ainsi que les administrateurs généraux d’Office 365 ou les administrateurs de service Power BI, peuvent attribuer en bloc des espaces de travail dans le**portail**d' **administration Power bi**. L’attribution en bloc peut s’appliquer à:

- **Espaces de travail par utilisateur** : Tous les espaces de travail détenus par ces utilisateurs, y compris les espaces de travail personnels, sont attribués à la capacité Premium. Cela inclut la réaffectation des espaces de travail lorsqu’ils sont déjà affectés à une capacité Premium différente. En outre, les utilisateurs reçoivent également des autorisations d’affectation d’espace de travail.

- **Espaces de travail spécifiques**
- **Les espaces de travail de l’ensemble de l’organisation** : Tous les espaces de travail, y compris les espaces de travail personnels, sont attribués à la capacité Premium. En outre, tous les utilisateurs actuels et futurs se voient attribuer des autorisations d’affectation d’espace de travail. \[[14,5](#endnote-14)\]

Un espace de travail peut être ajouté à une capacité Premium à l’aide du volet **espace de travail** , car l’utilisateur est à la fois un administrateur d’espace de travail et dispose d’autorisations d’affectation.

![Utilisation du volet espace de travail pour affecter un espace de travail à une capacité Premium](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Les administrateurs de l’espace de travail peuvent supprimer un espace de travail d’une capacité (à capacité partagée) sans avoir besoin de l’autorisation d’attribution. La suppression des espaces de travail des capacités dédiées déplace efficacement l’espace de travail vers une capacité partagée. Notez que la suppression d’un espace de travail d’une capacité Premium peut avoir des conséquences négatives, par exemple, en cas d’indisponibilité d’un contenu partagé pour Power BI les utilisateurs titulaires d’une licence, ou la suspension de l’actualisation planifiée lorsqu’ils dépassent les allocations prises en charge par capacité partagée.

Dans le service Power BI, un espace de travail affecté à une capacité Premium est facilement identifié par l’icône en losange qui orne le nom de l’espace de travail.

![Identification d’un espace de travail affecté à une capacité Premium](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Surveillance des capacités

La surveillance des capacités Premium offre aux administrateurs une compréhension des performances des capacités. Les capacités peuvent être surveillées à l’aide de l’application de métriques de [capacité Power bi Premium](service-admin-premium-monitor-capacity.md) ou du [portail d’administration Power bi](service-admin-premium-monitor-portal.md).

#### <a name="interpreting-metrics"></a>Interprétation des métriques

Les mesures doivent être surveillées pour établir une compréhension de base de l’activité de la charge de travail et de l’utilisation des ressources. Si la capacité devient lente, il est important de comprendre les métriques à surveiller et les conclusions que vous pouvez effectuer.

Dans l’idéal, les requêtes doivent être exécutées en une seconde pour fournir des expériences réactives aux utilisateurs de rapport et permettre un débit de requête plus élevé. Il est généralement moins important que les processus d’arrière-plan, y compris les actualisations, prennent plus de temps pour s’exécuter.

En général, les rapports lents peuvent indiquer une capacité de surchauffage. Lorsque le chargement des rapports échoue, il s’agit d’une indication d’une capacité surchauffée. Dans les deux cas, la cause racine peut être imputable à de nombreux facteurs, notamment:

- Les **requêtes ayant échoué** indiquent certainement une sollicitation de la mémoire et qu’un modèle n’a pas pu être chargé en mémoire. Le service Power BI tente de charger un modèle pendant 30 secondes avant d’échouer.

- Des **temps d’attente de requête excessifs** peuvent être dus à plusieurs raisons:
  - La nécessité pour l’service Power BI d’éliminer d’abord les modèles, puis de charger le modèle de requête à être interrogée (Rappelez-vous que les taux d’éviction de jeu de données les plus élevés ne sont pas une indication de la contrainte de capacité, sauf s’ils sont accompagnés par des temps d’attente de requête longs qui indiquent une surcharge de mémoire)
  - Temps de chargement du modèle (particulièrement l’attente pour charger un grand modèle en mémoire)
  - Requêtes à long terme
  - Trop de connexions LC\DQ (dépassement des limites de capacité)
  - Saturation de l’UC
  - Conceptions de rapports complexes avec un nombre excessif d’éléments visuels sur une page (Rappelez-vous que chaque visuel est une requête)
- Des durées de **requête longues** peuvent indiquer que les conceptions de modèles ne sont pas optimisées, en particulier lorsque plusieurs jeux de données sont actifs dans une capacité, et qu’un seul jeu de données génère des durées de requête longues. Cela suggère que la capacité est suffisamment resourcelement et que le jeu de données en question est sous-optimal ou simplement lent. Les requêtes longues peuvent être problématiques, car elles peuvent bloquer l’accès aux ressources requises par d’autres processus.
- Des temps d' **attente d’actualisation de longue durée ou des temps d’attente d’appel ai** indiquent une mémoire insuffisante en raison de nombreux modèles actifs qui consomment de la mémoire, ou qu’une actualisation problématique bloque d’autres actualisations (dépassant les limites d’actualisation parallèle).

Une explication plus détaillée de l’utilisation des métriques est traitée à la suite de la section [optimisation des capacités Premium](#optimizing-premium-capacities) .

## <a name="optimizing-premium-capacities"></a>Optimisation des capacités Premium

En cas de problèmes de performances de capacité Premium, une première approche courante consiste à optimiser ou à régler les solutions déjà déployées pour restaurer des temps de réponse acceptables. La logique de remplacement consiste à éviter d’acheter une capacité Premium supplémentaire, sauf si elle peut être justifiée.

Quand une capacité Premium supplémentaire est requise, il existe deux options qui seront abordées plus loin dans cette section:

- Augmenter la capacité Premium
- Ajout d’une capacité Premium

Enfin, les approches de test et le dimensionnement de capacité Premium vont conclure cette section.

### <a name="general-best-practices"></a>Meilleures pratiques générales

Lorsque vous vous efforcez d’obtenir une utilisation et des performances optimales, il existe des pratiques recommandées qui peuvent être posées à la carte en tant que recommandations générales. Elles incluent notamment :

- Utilisation d’espaces de travail d’application au lieu d’espaces de travail personnels
- Séparation des activités BI critiques et en libre-service (décisionnel) en différentes capacités

  ![Séparation des informations décisionnelles libre-service et critiques pour l’entreprise en différentes capacités](media/whitepaper-premium-deployment/separate-capacities.png)

- Si vous partagez du contenu uniquement avec Power BI Pro utilisateurs, il n’est pas nécessaire de stocker le contenu dans une capacité dédiée
- Utilisez des capacités dédiées pour obtenir un temps d’actualisation spécifique, ou lorsque des fonctionnalités spécifiques sont requises, par exemple des jeux de données volumineux ou des rapports paginés.

### <a name="addressing-common-questions"></a>Répondre aux questions courantes

L’optimisation des déploiements de Power BI Premium est un sujet complexe qui implique une compréhension des exigences de charge de travail, des ressources disponibles et de leur utilisation effective.

Cette rubrique traite de sept questions de support courantes, qui décrivent les problèmes et les explications possibles, ainsi que des informations sur la façon de les identifier et de les résoudre.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Pourquoi la capacité est-elle lente et que puis-je faire ?

Il existe de nombreuses raisons pouvant contribuer à une capacité Premium lente. Cette question nécessite des informations supplémentaires pour comprendre ce qui est entendu comme lent. Le chargement des rapports est-il lent ? Le chargement échoue-t-il ? Les visuels de rapport sont-ils lents à charger ou à mettre à jour lorsque les utilisateurs interagissent avec le rapport ? Les actualisations prennent-elles plus de temps que prévu, ou déjà expérimenté?

Après avoir acquis une bonne compréhension de la raison, vous pouvez commencer à examiner. Les réponses aux six questions suivantes vous aideront à résoudre des problèmes plus spécifiques.

#### <a name="what-content-is-using-up-my-capacity"></a>Quel contenu utilise ma capacité ?

Vous pouvez utiliser l’application **Mesures de capacité Power BI Premium** pour filtrer par capacité et vérifier les mesures de performance pour le contenu de l’espace de travail. Il est possible de passer en revue les mesures de performance et l’utilisation des ressources par heure au cours des sept derniers jours pour tout le contenu stocké dans une capacité Premium. Il s’agit souvent de la première étape à entreprendre lors du dépannage d’une préoccupation générale concernant les performances de capacité Premium.

Les mesures clés à surveiller sont les suivantes :

- Nombre moyen d’UC et d’utilisation élevée
- Nombre moyen de mémoire et d’utilisation élevée, et utilisation de la mémoire pour des jeux de données spécifiques, flux et des rapports paginés
- Jeux de données actifs chargés en mémoire
- Durées moyenne et maximale des requêtes
- Temps d’attente moyen des requêtes
- Temps moyen d’actualisation des jeux de données et flux de données
- Durée moyenne des appels AI et temps d’attente

En outre, dans l’application de métriques de capacité Power BI Premium, la mémoire active affiche la quantité totale de mémoire allouée à un rapport qui ne peut pas être supprimée car elle est en cours d’utilisation au cours des trois dernières minutes. Un pic élevé du temps d’attente d’actualisation peut être mis en corrélation avec un jeu de données volumineux et/ou actif.

Le graphique «5 premiers par durée moyenne» met en évidence les cinq jeux de données les plus importants, les rapports paginés, les flux et les appels AI qui consomment des ressources de capacité. Le contenu des cinq premières listes est un candidat à l’investigation et une optimisation possible.

#### <a name="why-are-reports-slow"></a>Pourquoi les rapports sont-ils lents ?

Les tableaux suivants présentent les problèmes possibles et les moyens de les identifier et de les traiter.

##### <a name="insufficient-capacity-resources"></a>Ressources de capacité insuffisantes

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Mémoire active totale élevée (le modèle ne peut pas être supprimé car il est en cours d’utilisation au cours des trois dernières minutes)<br><br> Plusieurs pics élevés dans les temps d’attente de requête<br><br> Plusieurs pics élevés en temps d’attente d’actualisation | Surveiller les métriques \[de mémoire [18](#endnote-18)\]et les \[nombres d’évictions [19](#endnote-19)\] | Réduire la taille du modèle ou convertir en mode DirectQuery: consultez la rubrique [optimisation des modèles](#optimizing-models) dans cette section.<br><br> Augmenter la capacité<br><br> Attribuer le contenu à une capacité différente |

##### <a name="inefficient-report-designs"></a>Conceptions de rapports inefficaces

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Les pages de rapport contiennent de nombreux visuels (le filtrage interactif peut déclencher au moins une requête par visuel)<br><br> Les éléments visuels récupèrent plus de données que nécessaire | Examiner les conceptions de rapport<br><br> Les utilisateurs de rapports d’entretiens pour comprendre comment ils interagissent avec les rapports<br><br> Surveiller les métriques \[de requête de DataSet [20](#endnote-20)\] | Reconcevoir des rapports avec moins d’éléments visuels par page |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>Jeu de données lent (surtout lorsque les rapports ont été correctement exécutés)

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Volumes de données d’importation de plus en plus importants<br><br> Logique de calcul complexe ou inefficace, y compris les rôles RLS<br><br> Modèle non entièrement optimisé<br><br> (DQ/LC) Latence de la passerelle<br><br> Lenteur des temps de réponse des requêtes source DQ | Examiner les conceptions de modèle<br><br> Surveiller les compteurs de performances de la passerelle | Consultez la rubrique [optimisation des modèles](#optimizing-models) dans cette section. |

##### <a name="high-concurrent-report-usage"></a>Utilisation élevée de rapports en simultané

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Temps d’attente de requête élevé<br><br> Saturation de l’UC<br><br> Limites de connexion DQ/LC dépassées | Surveiller l’utilisation \[de l’UC [21](#endnote-21)\], les temps d’attente des requêtes \[et l’utilisation de DQ/LC [22](#endnote-22) \] métriques + durées des requêtes: si fluctuants peut indiquer des problèmes d’accès concurrentiel | Augmenter la capacité de la capacité ou attribuer le contenu à une capacité différente<br><br> Reconcevoir des rapports avec moins d’éléments visuels par page |

#### <a name="why-are-reports-not-loading"></a>Pourquoi les rapports ne se chargent-ils pas ?

Lorsque les rapports ne parviennent pas à se charger, il s’agit d’un scénario le plus défavorable et un certain signe que la capacité dispose d’une mémoire insuffisante et qu’elle est surchauffée. Cela peut se produire lorsque tous les modèles chargés sont activement interrogés et ne peuvent donc pas être supprimés, et toutes les opérations d’actualisation ont été suspendues ou retardées. Le service Power BI tentera de charger le jeu de données pendant 30 secondes, et l’utilisateur est normalement informé de l’échec en suggérant de réessayer dans un instant.

Il n’existe actuellement aucune mesure à surveiller pour les échecs de chargement des rapports. Vous pouvez identifier le potentiel de ce problème en surveillant la mémoire système, en particulier l’utilisation la plus élevée et le temps d’utilisation le plus élevé. Les évictions des jeux de données élevés et un temps d’attente moyen d’actualisation des jeux de données peuvent suggérer que ce problème se produit.

Si cela ne se produit que très rarement, cela peut ne pas être considéré comme un problème prioritaire. Les utilisateurs de rapports sont informés que le service est occupé et qu’ils doivent effectuer une nouvelle tentative dans très peu de temps. Si cela se produit trop fréquemment, le problème peut être résolu en mettant à l’échelle la capacité Premium ou en affectant le contenu à une capacité différente.

Les administrateurs de capacité (et les administrateurs du service Power BI) peuvent surveiller la métrique des **échecs de requête** pour déterminer quand cela se produit. Ils peuvent également redémarrer la capacité, réinitialisant ainsi toutes les opérations en cas de surcharge du système.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>Pourquoi les actualisations ne commencent-elles pas selon la planification ?

Les heures de démarrage d’actualisation planifiée ne sont pas garanties. Rappelez-vous que le service Power BI met la priorité sur les opérations interactives par rapport aux opérations d’arrière-plan. L’actualisation est une opération d’arrière-plan qui peut se produire lorsque deux conditions sont remplies :

- La mémoire est suffisante
- Le nombre d’actualisations simultanées prises en charge pour la capacité Premium n’est pas dépassé

Lorsque les conditions ne sont pas remplies, l’actualisation est mise en file d’attente jusqu’à ce que les conditions soient favorables.

Pour une actualisation complète, rappelez-vous qu’au moins deux fois la taille de la mémoire actuelle du jeu de données est requise. Si la mémoire disponible n’est pas suffisante, l’actualisation ne peut pas commencer tant que l’éviction du modèle n’a pas libéré de la mémoire, ce qui signifie qu’un ou plusieurs jeux de données deviennent inactifs et peuvent être supprimés.

Rappelez-vous que le nombre maximal d’actualisations simultanées pris en charge est défini à 1,5 fois les cœurs vCore du serveur principal, arrondi à l’entier supérieur.

Une actualisation planifiée échouera si elle ne peut pas commencer avant que la prochaine actualisation planifiée ne commence. Une actualisation à la demande déclenchée manuellement à partir de l’interface utilisateur tentera de s’exécuter jusqu’à trois fois avant d’échouer.

Les administrateurs de capacité (et les administrateurs de service Power BI) peuvent surveiller la métrique de **temps d’attente d’actualisation moyen (minutes)** pour déterminer le décalage moyen entre l’heure planifiée et le début de l’opération.

Bien qu’il ne s’agisse généralement pas d’une priorité administrative, assurez-vous que la mémoire disponible est suffisante pour influencer l’actualisation des données au moment prévu. Cela peut impliquer l’isolation des jeux de données aux capacités avec des ressources suffisantes. Il est également possible que les administrateurs puissent coordonner les propriétaires de jeux de données pour aider à échelonner ou à réduire les temps d’actualisation planifiés des données pour réduire les collisions. Notez qu’il n’est pas possible pour un administrateur d’afficher la file d’attente d’actualisation ou de récupérer des planifications de jeu de données.

#### <a name="why-are-refreshes-slow"></a>Pourquoi les actualisations sont-elles lentes ?

Les actualisations peuvent être lentes ou perçues ainsi (comme les adresses de questions courantes précédentes).

Lorsque l’actualisation est en fait lente, cela peut être dû à plusieurs raisons :

- PROCESSEUR insuffisant (l’actualisation peut nécessiter beaucoup de ressources processeur)
- Mémoire insuffisante, ce qui entraîne une suspension de l’actualisation (ce qui nécessite que l’actualisation redémarre lorsque les conditions sont favorables à la reprise)
- Raisons de non-capacité, y compris la réactivité du système de source de données, la latence du réseau, les autorisations non valides ou le débit de la passerelle
- Volume de données-bonne raison de configurer l’actualisation incrémentielle, comme indiqué ci-dessous

Les administrateurs de capacité (et les administrateurs de service Power BI) peuvent surveiller la métrique de **durée d’actualisation moyenne (minutes)** pour déterminer point de référence pour une comparaison au fil du temps, et les métriques **temps d’attente d’actualisation moyen (minutes)** pour déterminer le décalage moyen entre l’heure planifiée et le début de l’opération.

L’actualisation incrémentielle peut réduire considérablement la durée d’actualisation des données, en particulier pour les tables de modèles volumineuses. Quatre avantages sont associés à l’actualisation incrémentielle :

- **Les actualisations sont plus rapides** : Seul un sous-ensemble d’une table doit être chargé, ce qui réduit l’utilisation de l’UC et de la mémoire, et le parallélisme peut être plus élevé lors de l’actualisation de plusieurs partitions.
- Les **actualisations se produisent uniquement lorsque** cela est nécessaire: Les stratégies d’actualisation incrémentielle peuvent être configurées pour être chargées uniquement lorsque les données ont changé
- **Les actualisations sont plus fiables** : Des connexions plus courtes aux systèmes de source de données volatiles sont moins susceptibles d’être déconnectées
- Les **modèles restent** découpés: Les stratégies d’actualisation incrémentielle peuvent être configurées pour supprimer automatiquement l’historique au-delà d’une fenêtre glissante de temps.

Pour plus d’informations, reportez-vous à l' [actualisation incrémentielle dans Power bi Premium](service-premium-incremental-refresh.md) document.

#### <a name="why-are-data-refreshes-not-completing"></a>Pourquoi les actualisations de données ne se terminent-elles pas ?

Lorsque l’actualisation des données commence mais échoue, cela peut être dû à plusieurs raisons :

- Mémoire insuffisante, même s’il n’y a qu’un seul modèle dans la capacité Premium, c’est-à-dire que la taille du modèle est très importante
- Raisons de non-capacité, y compris la déconnexion du système de source de données, les autorisations non valides ou l’erreur de passerelle

Les administrateurs de capacité (et les administrateurs du service Power BI) peuvent surveiller la métrique **Actualiser les échecs engendrés par un manque de mémoire**.

#### <a name="why-are-ai-calls-failing"></a>Pourquoi les appels AI échouent-ils?

Les appels AI peuvent échouer pour plusieurs raisons. La mémoire minimale requise pour démarrer la charge de travail AI est de 5 Go, mais cela peut ne pas suffire pour certains jeux de données d’entrée. Par exemple, l’apprentissage automatique du modèle de Machine Learning nécessite au moins deux fois la taille du jeu de données d’entrée. En outre, un appel AI est interrompu s’il faut plus de deux heures pour s’exécuter. Pour les appels de formation automatisés du modèle de Machine Learning qui ne se terminent pas en deux heures, le meilleur modèle trouvé dans ces deux heures est retourné.  Les appels AI peuvent également être interrompus par des requêtes interactives, qui sont prioritaires.

Les administrateurs doivent surveiller les temps d’attente AI pour les signes d’autres demandes qui sont prioritaires. Les administrateurs peuvent également s’assurer que suffisamment de mémoire est disponible pour la charge de travail d’intelligence artificielle relative à la taille des données d’entrée. Cela peut impliquer l’isolation des charges de travail d’intelligence artificielle sur les capacités dont les ressources sont suffisantes. Il est également possible que les administrateurs puissent coordonner les propriétaires de flux de données pour aider à échelonner ou à réduire les temps d’actualisation des flux de données pour réduire les collisions. Notez qu’un administrateur n’est pas en mesure d’afficher la file d’attente des appels AI.

### <a name="optimizing-models"></a>Optimisation des modèles

Une conception de modèle optimale est essentielle pour la mise en œuvre d’une solution efficace et évolutive. Toutefois, cela n’entre pas dans le cadre de ce livre blanc pour fournir une discussion complète. Au lieu de cela, cette section fournit des domaines clés à prendre en compte lors de l’optimisation des modèles.

#### <a name="optimizing-power-bi-hosted-models"></a>Optimisation des modèles hébergés par Power BI

L’optimisation des modèles hébergés dans une capacité Premium peut être effectuée au niveau de la ou des sources de données et des couches de modèle.

Tenez compte des possibilités d’optimisation d’un modèle d’importation :

![Possibilités d’optimisation d’un modèle d’importation](media/whitepaper-premium-deployment/import-model-optimizations.png)

Au niveau de la couche de source de données:

- Les sources de données relationnelles peuvent être optimisées pour garantir l’actualisation la plus rapide possible en préintégrant des données, en appliquant des index appropriés, en définissant des partitions de table qui s’alignent sur des périodes d’actualisation incrémentielles et en matérialisé des calculs (à la place de calculées). modéliser des tables et des colonnes) ou ajouter une logique de calcul aux vues
- Les sources de données non relationnelles peuvent être pré-intégrées aux magasins relationnels
- Assurez-vous que les passerelles disposent d’assez de ressources, de préférence sur des machines dédiées, avec une bande passante réseau suffisante et à proximité des sources de données

Au niveau de la couche du modèle :

- Les conceptions de requêtes Power Query peuvent réduire ou supprimer des transformations complexes, et en particulier celles fusionnant des sources de données différentes (les entrepôts de données y parviennent pendant leur étape d’extraction-transformation-chargement). En outre, en veillant à ce que les niveaux de confidentialité appropriés de la source de données soient définis, il est possible d’éviter de demander à Power BI de charger des résultats complets pour produire un résultat combiné sur les requêtes.
- La structure du modèle détermine les données à charger et a un impact direct sur la taille du modèle. Il peut être conçu pour éviter le chargement de données inutiles en supprimant des colonnes ou des lignes (notamment des données historiques) ou en chargeant des données résumées (au détriment du chargement de données détaillées). Une réduction considérable de la taille peut être obtenue en supprimant les colonnes de cardinalité élevée (en particulier les colonnes de texte) qui ne sont pas stockées ou compressées très efficacement.
- Les performances des requêtes de modèle peuvent être améliorées en configurant des relations à sens unique, à moins qu’il y ait une raison impérieuse d’autoriser le filtrage bidirectionnel. Envisagez également d’utiliser la fonction CROSSFILTER au lieu du filtrage bidirectionnel.
- Les tables d’agrégation peuvent obtenir des réponses rapides aux requêtes en chargeant des données prérésumées, mais cela augmente la taille du modèle et engendre des temps d’actualisation plus longs. En règle générale, les tables d’agrégation doivent être réservées pour les modèles très volumineux ou les conceptions de modèles composites.
- Les tables et les colonnes calculées augmentent la taille du modèle et entraînent des temps d’actualisation plus longs. En règle générale, une plus petite taille de stockage et un temps d’actualisation plus rapide peuvent être atteints lorsque les données sont matérialisées ou calculées dans la source de données. Si ce n’est pas possible, l’utilisation des colonnes personnalisées Power Query peut offrir une meilleure compression du stockage.
- Il peut être possible de paramétrer des expressions DAX pour les mesures et les règles RLS, possiblement en réécrivant la logique afin d’éviter des formules coûteuses
- L’actualisation incrémentielle peut réduire considérablement le temps d’actualisation et économiser la mémoire et l’UC. L’actualisation incrémentielle peut également être configurée pour supprimer les données historiques, permettant ainsi de réduire la taille des modèles.
- Un modèle peut être repensé comme deux modèles lorsqu’il existe des modèles de requête différents et en conflit. Par exemple, certains rapports présentent des agrégats de haut niveau sur l’ensemble de l’historique et peuvent tolérer une latence de 24 heures. D’autres rapports sont concernés par les données actuelles et nécessitent un accès granulaire à des transactions individuelles. Au lieu de concevoir un modèle unique pour répondre à tous les rapports, créez deux modèles optimisés pour chaque besoin.

Tenez compte des possibilités d’optimisation d’un modèle DirectQuery. Étant donné que le modèle émet des demandes de requête à la source de données sous-jacente, l’optimisation de la source de données est essentielle pour la transmission de requêtes de modèle réactif.

 ![Possibilités d’optimisation d’un modèle DirectQuery](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

Au niveau de la couche de source de données:

- La source de données peut être optimisée pour garantir une interrogation la plus rapide possible en préintégrant les données (ce qui n’est pas possible au niveau de la couche de modèle), en appliquant des index appropriés, en définissant des partitions de table, en matérialiséant des données résumées (avec des vues indexées) et réduction de la quantité de calcul. La meilleure expérience est obtenue lorsque les requêtes passthrough ont uniquement besoin de filtrer et d’effectuer des jointures internes entre les tables ou les vues indexées.
- S’assurer que les passerelles disposent de suffisamment de ressources, de préférence sur des ordinateurs dédiés, avec une bande passante réseau suffisante et à proximité de la source de données

Au niveau de la couche du modèle :

- Power Query les conceptions de requêtes doivent de préférence appliquer aucune transformation. sinon, essayez de conserver les transformations à un minimum absolu
- Les performances des requêtes de modèle peuvent être améliorées en configurant des relations à sens unique, à moins qu’il y ait une raison impérieuse d’autoriser le filtrage bidirectionnel. En outre, les relations de modèle doivent être configurées pour supposer que l’intégrité référentielle est appliquée (lorsque c’est le cas) et entraîne des requêtes de source de données utilisant des jointures internes plus efficaces (au lieu de jointures externes).
- Évitez de créer des Power Query des colonnes personnalisées de requête ou des colonnes calculées de modèle-matérialisez-les dans la source de données, lorsque cela est possible.
- Il peut être possible de paramétrer des expressions DAX pour les mesures et les règles RLS, possiblement en réécrivant la logique afin d’éviter des formules coûteuses

Tenez compte des possibilités d’optimisation d’un modèle composite. Rappelez-vous qu’un modèle composite permet une combinaison de tables d’importation et DirectQuery.

![Possibilités d’optimisation pour un modèle composite](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- En règle générale, les rubriques d’optimisation des modèles import et DirectQuery s’appliquent aux tables de modèle composite qui utilisent ces modes de stockage.
- En général, efforcez-vous d’obtenir une conception équilibrée en configurant des tables de type dimension (représentant les entités métier) en tant que mode de stockage double et les tables de type Faits (souvent des tables volumineuses, représentant des faits opérationnels) en tant que mode de stockage DirectQuery. Le mode de stockage double signifie les modes de stockage import et DirectQuery, ce qui permet au service Power BI de déterminer le mode de stockage le plus efficace à utiliser lors de la génération d’une requête native pour passthrough.
- Assurez-vous que les passerelles disposent d’assez de ressources, de préférence sur des machines dédiées, avec une bande passante réseau suffisante et à proximité des sources de données
- Les tables d’agrégations configurées en mode de stockage d’importation peuvent offrir des améliorations de performances de requête spectaculaires lorsqu’elles sont utilisées pour résumer les tables de type Faits du mode de stockage DirectQuery. Dans ce cas, les tables d’agrégation augmentent la taille du modèle et donc le temps d’actualisation, et il s’agit souvent d’un compromis acceptable pour accélérer les requêtes.

#### <a name="optimizing-externally-hosted-models"></a>Optimisation des modèles hébergés de manière externe

De nombreuses possibilités d’optimisation présentées dans la rubrique [optimisation des modèles hébergés Power bi](#optimizing-power-bi-hosted-models) s’appliquent également aux modèles développés avec Azure Analysis Services et SQL Server Analysis Services. Les exceptions claires sont certaines fonctionnalités actuellement non prises en charge, y compris les modèles composites et les tables d’agrégation.

Une considération supplémentaire pour les jeux de données hébergés en externe est l’hébergement de base de données par rapport au service Power BI. Par Azure Analysis Services, cela implique la création de la ressource Azure dans la même région que le locataire Power BI (région d’hébergement). Par SQL Server Analysis Services, pour IaaS, cela implique l’hébergement de la machine virtuelle dans la même région et, pour l’environnement local, cela signifie garantir une configuration de passerelle efficace.

En outre, il peut être intéressant de noter que les bases de données Azure Analysis Services et les bases de données tabulaires SQL Server Analysis Services requièrent que leurs modèles soient entièrement chargés en mémoire et qu’ils y restent à tout moment pour prendre en charge l’interrogation. À l’instar du service Power BI, il doit y avoir suffisamment de mémoire pour l’actualisation si le modèle doit rester en ligne pendant l’actualisation. Contrairement au service Power BI, il n’existe aucun concept dans lequel les modèles sont automatiquement vieillis et sortis de la mémoire en fonction de leur utilisation. Par conséquent, Power BI Premium offre une approche plus efficace pour optimiser l’interrogation du modèle avec une utilisation plus faible de la mémoire.

### <a name="capacity-planning"></a>Planification de la capacité

La taille d’une capacité Premium détermine les ressources de mémoire et de processeur disponibles, ainsi que les limites imposées à la capacité. Le nombre de capacités Premium est également un facteur important, car la création de plusieurs capacités Premium peut aider à isoler les charges de travail les unes des autres. Notez que le stockage est de 100 To par nœud de capacité, ce qui est susceptible d’être plus que suffisant pour toute charge de travail.

La détermination de la taille et du nombre de capacités Premium peut être difficile, en particulier pour les capacités initiales que vous créez. La première étape lors du dimensionnement de la capacité consiste à comprendre la charge de travail moyenne représentant l’utilisation quotidienne prévue. Il est important de comprendre que toutes les charges de travail ne sont pas égales. Par exemple, à une extrémité d’un spectre, 100 utilisateurs simultanés qui accèdent à une page de rapport unique qui contient un seul visuel est un objectif facilement réalisable. Pourtant, à l’autre extrémité du spectre, 100 utilisateurs simultanés qui accèdent à 100 différents rapports, contenant chacun 100 éléments visuels sur la page de rapport, entraînent des besoins très différents en termes de ressources de capacité.

Les administrateurs de capacité doivent donc prendre en compte de nombreux facteurs spécifiques à votre environnement, au contenu et à l’utilisation prévue. L’objectif de substitution est d’optimiser l’utilisation de la capacité tout en assurant des temps de requête cohérents, des temps d’attente acceptables et des taux d’éviction. Les facteurs à prendre en compte peuvent être les suivants :

- **Caractéristiques des données et de la taille du modèle** : Les modèles d’importation doivent être entièrement chargés en mémoire pour permettre l’interrogation ou l’actualisation. Les jeux de données LC/DQ peuvent nécessiter beaucoup de temps du processeur et éventuellement une quantité de mémoire importante pour évaluer des mesures complexes ou des règles RLS. La taille de la mémoire et du processeur, ainsi que le débit des requêtes LC/DQ sont limités par la taille de la capacité.
- **Modèles actifs simultanés** : L’interrogation simultanée de différents modèles d’importation offre des performances et une réactivité optimales lorsqu’elles sont conservées en mémoire. Il doit y avoir suffisamment de mémoire pour héberger tous les modèles fortement interrogés, avec de la mémoire supplémentaire pour permettre leur actualisation.
- **Actualiser le modèle d’importation** : Le type d’actualisation (complète ou incrémentielle), la durée et la complexité des requêtes Power Query et la logique de table/colonne calculée peuvent avoir un impact sur la mémoire et plus particulièrement sur l’utilisation du processeur. Les actualisations simultanées sont restreintes par la taille de la capacité (1,5 fois les cœurs virtuels backend, arrondi).
- **Requêtes simultanées** : De nombreuses requêtes simultanées peuvent entraîner des rapports qui ne répondent pas lorsque le processeur ou les connexions LC/DQ dépassent la limite de capacité. C’est particulièrement le cas pour les pages de rapport incluant de nombreux visuels.
- **Flux, les rapports paginés et les fonctions IA** : La capacité peut être configurée pour prendre en charge les fonctions flux, les rapports paginés et les fonctions IA, chacune nécessitant un pourcentage maximal configurable de mémoire de capacité. La mémoire est allouée dynamiquement à flux, mais elle est allouée de manière statique aux rapports paginés et à la charge de travail AI.

En plus de ces facteurs, les administrateurs de capacité peuvent créer plusieurs capacités. Plusieurs capacités permettent d’isoler les charges de travail et peuvent être configurées pour garantir que les charges de travail prioritaires disposent de ressources garanties. Par exemple, deux capacités peuvent être créées pour séparer les charges de travail critiques de l’entreprise et les charges de travail décisionnelles libre-service (SSBI). La capacité critique de l’entreprise peut être utilisée pour isoler les grands modèles d’entreprise en leur fournissant des ressources garanties, avec l’accès de création accordé uniquement au service informatique. La capacité SSBI peut être utilisée pour héberger un nombre croissant de modèles plus petits, avec un accès accordé aux analystes de l’entreprise. La capacité SSBI peut parfois rencontrer des temps d’attente acceptables pour les requêtes ou une actualisation.

Au fil du temps, les administrateurs de capacité peuvent équilibrer les espaces de travail entre les capacités en déplaçant le contenu entre des espaces de travail, ou les espaces de travail entre des capacités, et en mettant à l’échelle les capacités. En règle générale, pour héberger des modèles plus volumineux que vous mettez à l’échelle et pour une concurrence plus élevée, augmentez la taille des instances.

Rappelez-vous que l’achat d’une licence fournit des cœurs vCore au client. L’achat d’un abonnement **P3** peut être utilisé pour en créer une ou jusqu’à quatre capacités Premium, c’est-à-dire 1 x P3 ou 2 x P2, ou 4 x P1. En outre, avant de migrer une capacité P2 vers une capacité P3, vous pouvez envisager de fractionner les cœurs vCore pour créer deux capacités P1.

### <a name="testing-approaches"></a>Approches de test

Une fois qu’une taille de capacité est déterminée, vous pouvez effectuer des tests en créant un environnement contrôlé. Une option pratique et économique consiste à créer une capacité Azure (référence SKU A), en notant qu’une capacité P1 est de la même taille qu’une capacité A4, les capacités P2 et P3 ayant la même taille que les capacités A5 et A6, respectivement. Les capacités Azure peuvent être créées rapidement et sont facturées sur une base horaire. Ainsi, une fois les tests terminés, elles peuvent être facilement supprimées pour arrêter l’accumulation des coûts.

Le contenu du test peut être ajouté aux espaces de travail créés sur la capacité Azure, puis, en tant qu’utilisateur unique, les rapports peuvent être exécutés pour générer une charge de travail réaliste et représentative des requêtes. S’il existe des modèles d’importation, une actualisation de chaque modèle doit également être effectuée. Les outils de surveillance peuvent ensuite être utilisés pour passer en revue toutes les métriques afin de comprendre l’utilisation des ressources.

Il est important que les tests soient reproductibles: Les tests doivent être exécutés plusieurs fois et ils doivent fournir approximativement le même résultat à chaque fois. Une moyenne de ces résultats peut être utilisée pour extrapoler et estimer une charge de travail dans de véritables conditions de production.

Si vous disposez déjà d’une capacité et des rapports pour lesquels vous souhaitez charger un test, utilisez l’[outil de génération de charge PowerShell](https://aka.ms/PowerBILoadTestingTool) pour générer rapidement un test de charge. L’outil vous permet d’estimer le nombre d’instances de chaque rapport que votre capacité peut exécuter en une heure. Vous pouvez utiliser l’outil pour évaluer l’aptitude de votre capacité à effectuer un rendu de rapport individuel ou à afficher plusieurs rapports en parallèle. Pour plus d’informations, consultez la vidéo [Microsoft Power BI: Capacité Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Pour générer un test plus complexe, envisagez de développer une application de test de charge simulant une charge de travail réaliste. Pour plus d’informations, consultez le webinaire [Applications Power BI de test de charge avec le test de charge Visual Studio](https://www.youtube.com/watch?v=UFbCh5TaR4w).

## <a name="exploring-real-world-scenarios"></a>Exploration des scénarios réels

Dans cette section, plusieurs scénarios réels seront introduits pour décrire les problèmes ou les défis courants, comment les identifier et comment les résoudre:

- [Tenir à jour les jeux de données](#keeping-datasets-up-to-date)
- [Identification des jeux de données à réponse lente](#identifying-slow-responding-datasets)
- [Identification des causes de jeux de données à réponse lente](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Déterminer si la mémoire est suffisante](#determining-whether-there-is-enough-memory)
- [Déterminer s’il y a suffisamment d’UC](#determining-whether-there-is-enough-cpu)

Les étapes, ainsi que les exemples de graphiques et de tableaux, sont tirés de l' **application de mesures de capacité Power bi Premium** (application) à laquelle un administrateur Power bi aura accès.

### <a name="keeping-datasets-up-to-date"></a>Tenir à jour les jeux de données

Dans ce scénario, une investigation a été déclenchée lorsque les utilisateurs se plaignaient que les données de rapport étaient parfois anciennes ou «obsolètes».

Dans l’application, l’administrateur interagit avec l' **actualisation** de l’objet visuel, en triant les jeux de données en fonction des statistiques de **temps d’attente maximales** dans l’ordre décroissant. Cela leur permet de révéler les jeux de données qui ont les temps d’attente les plus longs, regroupés par nom d’espace de travail.

![Actualisations du jeu de données triées par ordre décroissant du temps d’attente maximal, regroupés par espace de travail](media/whitepaper-premium-deployment/dataset-refreshes.png)

En outre, dans les **temps d’attente d’actualisation moyenne horaire** , ils remarquent que les temps d’attente d’actualisation atteignent régulièrement environ 16h00 chaque jour.

![Pics d’attente d’actualisation périodiques à 16H00](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Il existe plusieurs explications possibles pour ces résultats:

- Un trop grand nombre de tentatives d’actualisation peuvent être effectuées en même temps, ce qui dépasse les limites imposées par le nœud capacité (six actualisations simultanées sur un P1 avec allocation de mémoire par défaut).

- Les jeux de données à actualiser peuvent être trop volumineux pour tenir dans la mémoire disponible (ce qui nécessite au moins 2 fois la mémoire requise pour l’actualisation complète)
- Une logique de Power Query inefficace peut résulter en un pic d’utilisation de la mémoire lors de l’actualisation du jeu de données. Sur une capacité occupée, cela peut parfois atteindre la limite physique, échouer à l’actualisation et affecter potentiellement les autres opérations de vue de rapport sur la capacité.
- Les jeux de données fréquemment interrogés qui doivent rester en mémoire peuvent affecter la capacité des autres jeux de données à être actualisés, en raison de la mémoire disponible limitée

Pour vous aider à examiner cela, le Power BI administrateur peut rechercher:

- Mémoire disponible insuffisante au moment de l’actualisation des données, lorsque la mémoire disponible est inférieure à la taille du jeu de données à actualiser
- Les jeux de données qui n’ont pas été actualisés et qui ne se trouvaient pas dans la mémoire avant une actualisation, qui commençaient à afficher le trafic interactif pendant les temps d’actualisation intenses. Pour voir quels jeux de données ont été chargés en mémoire à un moment donné, un administrateur de Power BI peut consulter la zone jeux de données de l’onglet **jeux** de données dans l’application et effectuer un filtrage croisé à un moment donné en cliquant sur l’une des barres dans le **nombre de jeux de données à chargement horaire**. Un pic local (illustré dans l’image ci-dessous) indique une heure lorsque plusieurs jeux de données ont été chargés en mémoire, ce qui peut retarder le démarrage des actualisations planifiées
- Des évictions de jeu de données accrus ont lieu lorsque les actualisations de données sont planifiées pour démarrer, ce qui indique une forte sollicitation de la mémoire causée par le traitement d’un trop grand nombre de rapports interactifs avant l’actualisation. Les **évictions du jeu de données et la consommation de mémoire** peuvent indiquer clairement les pics d’éviction.

L’illustration suivante montre un pic local dans les jeux de données chargés, qui suggère un début différé de l’actualisation des requêtes interactives. La sélection d’une période dans le **nombre de jeux de données à chargement horaire** entraîne le filtrage croisé du visuel de tailles de jeu de **données** .

![Un pic local dans les jeux de données chargés suggère un début différé des actualisations](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

L’administrateur Power BI peut tenter de résoudre le problème en prenant des mesures pour garantir que la mémoire disponible pour les actualisations de données est suffisante pour démarrer:

- Contacter les propriétaires de jeux de données et leur demander d’échelonner et d’espacer les planifications d’actualisation des données
- Réduction de la charge des requêtes de jeu de données en supprimant les tableaux de bord ou les vignettes de tableau de bord inutiles, en particulier ceux qui appliquent la sécurité
- Accélérer l’actualisation des données en optimisant Power Query logique, modéliser des tables ou des colonnes calculées, réduire la taille des jeux de données ou configurer des jeux de données plus volumineux pour effectuer une actualisation incrémentielle des données

### <a name="identifying-slow-responding-datasets"></a>Identification des jeux de données à réponse lente

Dans ce scénario, une investigation a été déclenchée lorsque les utilisateurs se plaignaient que certains rapports prenaient beaucoup de temps à s’ouvrir, et parfois se sont bloqués.

Dans l’application, l’administrateur Power BI peut utiliser le visuel durées de **requête** pour déterminer les jeux de données les moins performants en triant les jeux de données par ordre décroissant de **durée moyenne**. Cet visuel affiche également le nombre de requêtes de DataSet, ce qui vous permet de voir la fréquence à laquelle les jeux de données sont interrogés.

![Révéler les jeux de données les moins performants](media/whitepaper-premium-deployment/worst-performing-datasets.png)

L’administrateur Power BI peut faire référence à l’ensemble de la **distribution durée** de la requête, qui illustre une distribution globale des performances des requêtes comprises (< = 30ms, 0 à 100 ms, etc.) pour la période filtrée. En règle générale, les requêtes qui prennent une seconde ou moins sont considérées comme réactives par la plupart des utilisateurs; les requêtes qui prennent plus de temps tendent à créer une perception de mauvaises performances.

Le visuel de la distribution de la **durée des requêtes toutes les heures** permet à l’administrateur Power bi d’identifier les périodes d’une heure où les performances de la capacité peuvent avoir été perçues comme médiocres. Plus les segments de la barre qui représentent les durées des requêtes sont grands, plus le risque de performances des utilisateurs est élevé.

L’objet visuel est interactif et lorsqu’un segment de la barre est sélectionné, le visuel de table durées de **requête** correspondant sur la page de rapport est filtré de façon croisée pour afficher les jeux de données qu’il représente. Ce filtrage croisé permet à l’administrateur Power BI d’identifier facilement les jeux de données qui répondent lentement.

L’illustration suivante montre un visuel filtré par les **distributions de durée de requête toutes les heures**, en se concentrant sur les jeux de données les moins performants dans les compartiments d’une heure. 

![Filtres des durées de requête horaire filtrées visuels affiche les jeux de données les moins performants](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

Une fois le jeu de données insuffisant dans un intervalle de temps de 1 heure spécifique, le Power BI administrateur peut déterminer si les performances sont médiocres, si la capacité est surchargée ou en raison d’un jeu de données ou rapport mal conçu. Pour ce faire, ils peuvent faire référence au visuel des **temps d’attente de requête** et trier des datasets par ordre décroissant du temps d’attente de requête moyen. Si un grand pourcentage de requêtes sont en attente, une demande élevée pour le jeu de données est probablement à l’origine de la plupart des attentes de requête. Si le temps d’attente moyen de la requête est substantiel (> 100 ms), il peut être utile de passer en revue le jeu de données et le rapport pour déterminer si des optimisations peuvent être effectuées. Par exemple, il peut y avoir moins de visuels sur des pages de rapport données ou une optimisation d’expression DAX.

![Le visuel des temps d’attente de requête permet de révéler des jeux de données peu performants](media/whitepaper-premium-deployment/query-wait-times.png)

Il existe plusieurs raisons possibles pour la génération de temps d’attente de requête dans des jeux de données:

- Conception de modèle sous-optimal, expressions de mesure ou conception de rapport, toutes les circonstances qui peuvent contribuer à des requêtes de longue durée qui consomment des niveaux élevés d’UC. Cela oblige les nouvelles requêtes à attendre que les threads de l’UC deviennent disponibles et puisse créer un effet de convoi (pensez au bourrage du trafic), généralement observé pendant les heures de pointe. La page d' **attente de requête** est la ressource principale pour déterminer si les jeux de données ont des temps d’attente de requêtes moyens élevés.
- Un grand nombre d’utilisateurs de capacité simultanée (des centaines à des milliers) qui consomment le même rapport ou jeu de données. Même les jeux de données bien conçus peuvent être exécutés au-delà d’un seuil d’accès concurrentiel. Cela est généralement indiqué par un jeu de données unique montrant une valeur beaucoup plus élevée pour les nombres de requêtes que les autres jeux de données (par exemple, les requêtes 300 000 pour un jeu de données par rapport à < requêtes attention pour tous les autres jeux de données). À un moment donné, la requête attend que ce jeu de données commence à s’échelonner, ce qui est visible dans le visuel durées de la **requête** .
- Un grand nombre de jeux de données disparates interrogés simultanément, provoquant un blocage lorsque les jeux de données sont souvent en mémoire et insuffisants. Ainsi, les utilisateurs subissent un ralentissement des performances lorsque le jeu de données est chargé en mémoire. Pour ce faire, l’administrateur Power BI peut se référer aux évictions du **jeu de données et** à la consommation de mémoire, ce qui peut indiquer qu’un grand nombre de jeux de données chargés en mémoire sont supprimés à plusieurs reprises.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identification des causes de jeux de données à réponse lente

Dans ce scénario, une investigation a été déclenchée lorsque les utilisateurs ont indiqué que les visuels de rapport étaient parfois trop lents à répondre ou pouvaient cesser de répondre, mais à d’autres moments, ils étaient réactifs.

Dans l’application, la section durées de la **requête** a été utilisée pour rechercher le jeu de données coupable de la façon suivante:

- Dans les durées de la **requête** , consultez le jeu de données filtré par l’administrateur par jeu de données (en commençant par les jeux de données les plus demandés) et examinez les barres filtrées croisées dans l’objet visuel distributions des **requêtes toutes les heures** .
- Lorsqu’une seule barre d’une heure affichait des changements significatifs dans le rapport entre tous les groupes de durée de requête et les autres barres d’une heure pour ce jeu de données (autrement dit, les ratios entre les couleurs changent radicalement), cela signifie que ce jeu de données a montré une modification sporadique dans garantie.
- Les barres d’une heure qui présentent une partie irrégulière des requêtes à performances médiocres, indiquaient une période dans laquelle ce jeu de données a été affecté par un effet de voisin bruyant, provoqué par d’autres activités de jeux de données.

L’image ci-dessous montre une heure le 30 janvier, où un regrettable significatif dans les performances d’un jeu de données s’est produit, indiqué par la taille du compartiment de la durée d’exécution «(3, 10s]». Le fait de cliquer sur cette barre d’une heure révèle tous les jeux de données chargés en mémoire pendant ce temps, ce qui permet de regrouper les jeux de données candidats qui provoquent l’effet de voisin bruyant.

![Barre présentant les pires performances par une grande partie](media/whitepaper-premium-deployment/worst-performing-queries.png)

Une fois qu’un intervalle de temps problématique est identifié (c’est-à-dire au cours du 30 janvier dans l’image ci-dessus), le Power BI administrateur peut supprimer tous les filtres de DataSet, puis filtrer uniquement par ce TimeSpan pour déterminer les jeux de données qui ont été interrogés activement pendant cette période. Le jeu de données coupable de l’effet de voisin bruyant est généralement le jeu de données le plus élevé interrogé ou celui ayant la durée de requête moyenne la plus longue.

Une solution à ce problème peut consister à distribuer les jeux de données défaillants sur différents espaces de travail sur des capacités Premium différentes ou sur une capacité partagée si la taille du jeu de données, les exigences de consommation et les modèles d’actualisation des données sont pris en charge.

L’inverse peut également avoir la valeur true. L’administrateur Power BI peut identifier les moments où les performances d’une requête de DataSet s’améliorent considérablement, puis recherchent ce qui a disparu. Si certaines informations sont manquantes à ce stade, cela peut aider à pointer vers le problème à l’origine du problème.

### <a name="determining-whether-there-is-enough-memory"></a>Déterminer si la mémoire est suffisante

Pour déterminer s’il y a suffisamment de mémoire pour que la capacité termine ses charges de travail, le Power BI administrateur peut faire référence à l’visuel **pourcentage de mémoire consommé** dans l’onglet **jeux de données** de l’application. **Tout** la mémoire (totale) représente la mémoire consommée par les jeux de données chargés en mémoire, qu’ils soient activement interrogés ou traités. La mémoire **active** représente la mémoire consommée par les jeux de données qui sont traités activement.

Dans une capacité saine, le visuel ressemblera à ce qui suit, en présentant un écart entre tout (total) et la mémoire active:

![Une capacité saine affichera un écart entre tout (total) et la mémoire active](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

Dans une capacité qui connaît la sollicitation de la mémoire, le même visuel affichera clairement la mémoire active et la mémoire totale convergé, ce qui signifie qu’il est impossible de charger des jeux de données supplémentaires en mémoire à ce moment précis. Dans ce cas, le Power BI administrateur peut cliquer sur redémarrage de la **capacité** (dans **Options avancées** de la zone paramètres de capacité du portail d’administration). Le redémarrage de la capacité entraîne le vidage de tous les jeux de données de la mémoire et leur permet d’être rechargées en mémoire en fonction des besoins (par les requêtes ou l’actualisation des données).

![\* * Mémoire active * * convergé avec * * tout * * mémoire](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Déterminer s’il y a suffisamment d’UC

En général, l’utilisation moyenne du processeur d’une capacité doit rester au-dessous de 80%. Le dépassement de cette valeur signifie que la capacité approche la saturation de l’UC.

Les effets de la saturation de l’UC sont exprimés par les opérations qui prennent plus de temps qu’elles ne le devraient en raison de la capacité à effectuer de nombreux changements de contexte d’UC lorsqu’elle tente de traiter toutes les opérations. Dans une capacité Premium avec un nombre élevé de requêtes simultanées, cette valeur est indiquée par des temps d’attente de requête élevés. Une conséquence des temps d’attente de requête élevés est plus lente que d’habitude. Le Power BI administrateur peut facilement identifier le moment où le processeur est saturé en affichant l’aperçu des distributions de **temps d’attente des requêtes toutes les heures** . Les pics périodiques du nombre de temps d’attente de requête indiquent une saturation de l’UC potentielle.

![Les pics périodiques d’attente de requêtes indiquent une possible saturation du processeur.](media/whitepaper-premium-deployment/peak-query-wait-times.png)

Un modèle similaire peut parfois être détecté dans les opérations en arrière-plan s’il contribue à la saturation de l’UC. Un administrateur Power BI peut rechercher un pic périodique dans les temps d’actualisation pour un jeu de données spécifique, qui peut indiquer la saturation de l’UC à ce moment-là (probablement en raison d’autres actualisations de jeu de données en cours et/ou de requêtes interactives). Dans ce cas, la référence à la vue **système** dans l’application peut ne pas révéler nécessairement que le processeur est à 100%. La vue **système** affiche des moyennes horaires, mais l’UC peut être saturée pendant plusieurs minutes d’opérations lourdes, qui apparaissent sous forme de pics de temps d’attente.

Il y a plus de nuances pour voir l’effet de la saturation de l’UC. Bien que le nombre de requêtes en attente soit important, le temps d’attente des requêtes se produira toujours dans une certaine mesure sans entraîner de dégradation des performances. Certains jeux de données (avec une durée moyenne des requêtes plus longue, indiquant la complexité ou la taille) sont plus sujets aux effets de la saturation de l’UC que d’autres. Pour identifier facilement ces jeux de données, le Power BI administrateur peut rechercher des modifications dans la composition des barres de l’objet visuel de **distribution du temps d’attente horaire** . Après avoir tacheté une barre hors norme, elle peut rechercher les jeux de données qui comportaient des attentes de requête pendant cette période et examiner le temps d’attente moyen de la requête par rapport à la durée moyenne de la requête. Lorsque ces deux métriques sont de la même amplitude et que la charge de travail de la requête pour le jeu de données est non triviale, il est probable que le jeu de données est affecté par un processeur insuffisant.

Cet effet peut être particulièrement évident lorsqu’un jeu de données est consommé par de courtes pics de requêtes à fréquence élevée par plusieurs utilisateurs (par exemple, dans une session de formation), ce qui entraîne une saturation de l’UC au cours de chaque rafale. Dans ce cas, des temps d’attente de requête significatifs sur ce jeu de données peuvent être rencontrés et avoir un impact sur d’autres jeux de données dans la capacité (effet de voisin bruyant).

Dans certains cas, Power BI administrateurs peuvent demander aux propriétaires de jeux de données de créer une charge de travail de requête moins volatile en créant un tableau de bord (qui effectue périodiquement des requêtes avec n’importe quelle actualisation de DataSet pour les vignettes mises en cache) au lieu d’un rapport. Cela peut aider à éviter les pics de charge lors du chargement du tableau de bord. Il se peut que cette solution ne soit pas toujours possible pour les besoins de l’entreprise, mais cela peut être un moyen efficace d’éviter la saturation de l’UC, sans avoir à modifier le jeu de données.

## <a name="conclusion"></a>Conclusion

Power BI Premium offre des performances plus cohérentes, une prise en charge des volumes de données volumineux et la flexibilité d’une plate-forme unifiée libre-service et d’entreprise décisionnelle pour tous les membres de votre organisation. Ce livre blanc technique de niveau 300 a été rédigé spécifiquement pour les administrateurs de Power BI, ainsi que pour les créateurs et les éditeurs de contenu. Il vise à les aider à comprendre le potentiel de Power BI Premium et à expliquer comment concevoir, déployer, surveiller et dépanner des solutions évolutives.

Pour déployer et gérer des capacités de Power BI Premium, les administrateurs et les développeurs de modèles auront besoin d’une bonne compréhension du fonctionnement des capacités, de la façon dont elles peuvent être gérées et surveillées et de la façon dont les modèles peuvent être optimisés, afin de répondre de manière appropriée à les problèmes de performances et les goulots d’étranglement devraient se produire.

## <a name="end-notes"></a>Notes de fin

<a name="endnote-01"></a>\[1\] ce document technique s’intéresse à Power bi Premium qui n’est pris en charge que par le service Cloud Power bi, et donc Power bi Report Server n’est pas dans l’étendue, sauf pour indiquer que la licence requise pour installer Power bi Report Server est incluse dans certains Références (SKU) Power BI Premium.

<a name="endnote-02"></a>\[2\] Power bien tant que service Cloud lorsqu’il est utilisé pour incorporer du contenu pour le compte des utilisateurs d’applications est Platform-as-a-service (PaaS). Ce type d’incorporation peut être effectué avec deux produits différents, dont l’un est Power BI Premium.

<a name="endnote-03"></a>\[3\] les jeux de données de type push, streaming et hybrides ne sont pas stockés dans les capacités Premium et ne sont donc pas pris en compte lors du déploiement, de la gestion et de la surveillance des capacités Premium.

<a name="endnote-04"></a>\[4\] les classeurs Excel en tant que type de contenu Power bi ne sont pas stockés dans les capacités Premium et ne sont donc pas pris en compte lors du déploiement, de la gestion ou de la surveillance des capacités Premium.

<a name="endnote-05"></a>\[5\] visuels peuvent être configurés pour ignorer les interactions de segment. Pour plus d’informations, reportez-vous aux [interactions de visualisation dans un document de rapport Power bi](service-reports-visual-interactions.md) .

<a name="endnote-06"></a>\[6\] la différence de taille peut être déterminée en comparant la taille du fichier Power bi Desktop avec la mémoire du gestionnaire des tâches utilisée pour le fichier.

<a name="endnote-07"></a>\[7\] la prise en charge des sources de données Microsoft inclut SQL Server, les briques de données Azure, Azure HDInsight Spark (bêta), Azure SQL Database et Azure SQL Data Warehouse. Pour plus d’informations sur les sources supplémentaires, reportez-vous à la rubrique [sources de données prises en charge par une requête directe dans Power bi](desktop-directquery-data-sources.md) document.

<a name="endnote-08"></a>\[8\] Power bi Premium prend en charge le chargement d’un fichier Power bi Desktop (. pbix) d’une taille maximale de 10 Go. Une fois chargé, un jeu de données peut atteindre jusqu’à 12 Go de taille suite à l’actualisation. La taille maximale de téléchargement varie en fonction de la référence SKU. Pour plus d’informations, reportez-vous au document [Power bi Premium support pour les jeux de données volumineux](service-premium-large-datasets.md) .

<a name="endnote-09"></a>\[9\] références SKU avec moins de quatre cœurs v ne s’exécutent pas sur une infrastructure dédiée. Cela comprend les références SKU EM1, EM2, a1 et a2.

<a name="endnote-10"></a>\[10\] bien que rares, les modèles peuvent être déchargés de la mémoire en raison des opérations de service.

<a name="endnote-11"></a>\[11\] ces minutages sont susceptibles d’être modifiés à tout moment.

<a name="endnote-12"></a>\[12\] on parle de «multi-géo», actuellement en version préliminaire. Le raisonnement pour un déploiement à plusieurs géoments est généralement pour la conformité de l’entreprise ou du gouvernement, plutôt que pour les performances et la mise à l’échelle. Le chargement de rapports et de tableaux de bord implique toujours des demandes à la région d’hébergement pour les métadonnées. Pour plus d’informations, reportez-vous au document [prise en charge de plusieurs zones géographiques pour Power bi Premium (version préliminaire)](service-admin-premium-multi-geo.md) .

<a name="endnote-13"></a>\[13\] il est possible que les utilisateurs puissent provoquer des problèmes de performances en surchargeant le service Power bi avec des travaux, en écrivant des requêtes trop complexes, en créant des références circulaires, etc.

<a name="endnote-14"></a>\[14\] l’option permettant d’attribuer les espaces de travail de toute l’organisation n’est pas recommandée, et une approche plus ciblée est recommandée. En règle générale, il n’est pas recommandé d’utiliser des espaces de travail personnels pour le contenu de production.

<a name="endnote-15"></a>\[15\] il est possible de surveiller une référence (SKU) dans l’application ou dans le portail Azure, mais pas dans le portail d’administration Power bi. Pour surveiller une référence (SKU), l’actualisation du rapport échoue si l’application n’a pas été ajoutée au rôle lecteur de la ressource. Pour plus d’informations, reportez-vous au document sur les [capacités d’analyse Power bi Premium et Power bi Embedded](service-admin-premium-monitor-capacity.md) .

<a name="endnote-16"></a>\[16\] actualisations peuvent attendre quand il n’y a pas assez d’UC ou de mémoire pour démarrer.

<a name="endnote-17"></a>\[17\] la taille du jeu de données en mémoire peut être supérieure à 20% par rapport à la taille sur le disque.

<a name="endnote-18"></a>\[18\] utilisation moyenne de la mémoire (Go) et consommation de mémoire la plus élevée (en Go)

<a name="endnote-19"></a>\[19\] évictions de jeu de données

<a name="endnote-20"></a>\[20\] requêtes de DataSet, durée moyenne de requête du jeu de données (MS), nombre d’attentes de DataSet et temps d’attente moyen des jeux de données (MS)

<a name="endnote-21"></a>\[21\] nombre d’utilisations de l’UC et temps processeur de l’utilisation la plus élevée (sept derniers jours)

<a name="endnote-22"></a>\[22\] DQ/LC-nombre élevé d’utilisation et DQ/LC-temps d’utilisation le plus élevé (sept derniers jours)