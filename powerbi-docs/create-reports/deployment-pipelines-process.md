---
title: Processus des pipelines de déploiement
description: Comprendre le processus de pipeline de déploiement Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: contperfq1
ms.date: 09/22/2020
ms.openlocfilehash: a364d3dd2d2175e4509d05f4c34eec31a1a371b6
ms.sourcegitcommit: 37ec0e9e356b6d773d7d56133fb8ed6c06b65fd3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91024032"
---
# <a name="understand-the-deployment-process"></a>Comprendre le processus de déploiement

Le processus de déploiement vous permet de cloner le contenu d’une étape de pipeline vers une autre, en général du développement au test et du test à la production.

Pendant le déploiement, Power BI copie le contenu de l’étape actuelle vers le contenu cible. Les connexions entre les éléments copiés sont conservées lors du processus de copie. Power BI applique également les règles de jeu de données configurées au contenu mis à jour à l’étape cible. Le déploiement de contenu peut prendre un certain temps, en fonction du nombre d’éléments en cours de déploiement. Pendant ce temps, vous pouvez accéder à d’autres pages dans le portail Power BI, mais vous ne pouvez pas utiliser le contenu dans l’étape cible.

## <a name="deploying-content-to-an-empty-stage"></a>Déploiement de contenu dans une étape vide

Lorsque vous déployez du contenu dans une étape vide, les métadonnées des rapports, des tableaux de bord et des jeux de données de l’espace de travail à partir duquel vous effectuez le déploiement sont copiées dans l’étape vers laquelle vous effectuez le déploiement. Un nouvel espace de travail pour l’étape sur laquelle vous avez déployé est créé sur une capacité Premium.

Il existe deux façons de déployer du contenu d’une étape à l’autre. Vous pouvez déployer tout le contenu, ou vous pouvez [sélectionner les éléments de contenu à déployer](deployment-pipelines-get-started.md#selective-deployment).

Vous pouvez également déployer le contenu vers l’arrière, d’une étape ultérieure du pipeline de déploiement vers une ancienne.

Une fois le déploiement terminé, actualisez les jeux de données afin de pouvoir utiliser le contenu qui vient d’être copié. L’actualisation du jeu de données est nécessaire, car les données ne sont pas copiées d’une étape à l’autre. Pour savoir quelles propriétés d’élément sont copiées pendant le processus de déploiement et quelles propriétés ne le sont pas copiées, consultez la section [Propriétés d’élément copiées lors du déploiement](#item-properties-copied-during-deployment).

### <a name="creating-a-premium-capacity-workspace"></a>Création d’un espace de travail de capacité Premium

Lors du premier déploiement, les pipelines de déploiement vérifient si vous disposez d’autorisations de capacité Premium.  

Si vous disposez d’autorisations de capacité, le contenu de l’espace de travail est copié à l’étape vers laquelle vous effectuez le déploiement, et un nouvel espace de travail pour cette étape est créé sur la capacité Premium.

Si vous n’avez pas d’autorisations de capacité, l’espace de travail est créé, mais le contenu n’est pas copié. Vous pouvez demander à un administrateur de capacité d’ajouter votre espace de travail à une capacité ou demander l’attribution d’autorisations pour la capacité. Plus tard, lorsque l’espace de travail est affecté à une capacité, vous pouvez déployer le contenu dans cet espace de travail.

### <a name="workspace-and-content-ownership"></a>Propriété de l’espace de travail et du contenu

L’utilisateur qui effectue le déploiement devient automatiquement le propriétaire du jeu de données cloné et le seul administrateur du nouvel espace de travail.

## <a name="deploy-content-to-an-existing-workspace"></a>Déployer du contenu dans un espace de travail existant

Le déploiement de contenu dans un pipeline de production en cours d’utilisation, sur une étape disposant d’un espace de travail existant, inclut les éléments suivants :

* Déploiement de nouveau contenu en tant qu’ajout, à une étape qui contient déjà du contenu.

* Nouveau contenu déployé pour remplacer l’ancien contenu, dans une étape de travail actuelle.

### <a name="deployment-process"></a>Processus de déploiement

Le contenu de l’étape actuelle est copié vers l’étape cible. Power BI identifie le contenu existant de l’étape cible et le remplace. Pour identifier l’élément de contenu qui doit être remplacé, les pipelines de déploiement utilisent la connexion entre l’élément parent et ses clones. Cette connexion est conservée lors de la création de nouveau contenu. L’opération de remplacement remplace uniquement le contenu de l’élément. L’ID, l’URL et les autorisations de l’élément restent inchangés.

Dans l’étape cible, les [propriétés d’élément qui ne sont pas copiées](deployment-pipelines-process.md#item-properties-that-are-not-copied) restent telles qu’elles étaient avant le déploiement. Le nouveau contenu et les nouveaux éléments sont copiés de l’étape actuelle à l’étape cible.

### <a name="refreshing-the-dataset"></a>Actualisation du jeu de données

Les données du jeu de données cible sont conservées dans la mesure du possible. Si aucune modification n’est apportée à un jeu de données, les données sont conservées telles qu’elles étaient avant le déploiement.

Avec des modifications mineures, comme l’ajout d’une table ou de mesures, Power BI conserve les données d’origine, et l’actualisation est optimisée pour actualiser uniquement ce qui est nécessaire. Pour les modifications de schéma cassantes ou les modifications apportées à la connexion à la source de données, une actualisation complète est nécessaire.

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>Conditions requises pour le déploiement sur une étape avec un espace de travail existant

Tant que le contenu déployé réside sur une [capacité Premium](../admin/service-premium-what-is.md), un utilisateur qui remplit les conditions suivantes peut le déployer à une étape dans un espace de travail existant :

* Un [utilisateur Pro](../admin/service-admin-purchasing-power-bi-pro.md) qui est membre des deux espaces de travail dans les étapes de déploiement source et cible.

* Un propriétaire de tous les jeux de données de l’espace de travail cible qui vont être déployés.

Pour plus d'informations, consultez la section [Autorisations](#permissions).

## <a name="deployed-items"></a>Éléments déployés

Lorsque vous déployez du contenu d’une étape de pipeline vers une autre, le contenu copié contient les éléments Power BI suivants :

* Jeux de données

* Rapports

* Tableaux de bord

### <a name="unsupported-items"></a>Éléments non pris en charge

Les pipelines de déploiement ne prennent pas en charge les éléments suivants :

* Jeux de données qui ne proviennent pas d’un .pbix

* Rapports basés sur des jeux de données non pris en charge

* [Espaces de travail d’applications modèles](../connect-data/service-template-apps-create.md#create-the-template-workspace)

* Rapports paginés

* Dataflows

* Transmettre des jeux de données

* Classeurs

## <a name="item-properties-copied-during-deployment"></a>Propriétés de l’élément copiées lors du déploiement

Pendant le déploiement, les propriétés d’élément suivantes sont copiées et remplacent les propriétés de l’élément à l’étape cible :

* Sources de données (les [règles de jeu de données](deployment-pipelines-get-started.md#step-4---create-dataset-rules) sont prises en charge)

* Paramètres (les [règles de jeu de données](deployment-pipelines-get-started.md#step-4---create-dataset-rules) sont prises en charge)

* Visuels de rapport

* Pages d’un rapport

* Mise à jour des vignettes de tableau de bord

* Métadonnées du modèle

* Relations d’élément

### <a name="item-properties-that-are-not-copied"></a>Propriétés d’élément qui ne sont pas copiées

Les propriétés d’élément suivantes ne sont pas copiées lors du déploiement :

* Données : les données ne sont pas copiées, seules les métadonnées sont copiées

* URL

* ID

* Autorisations : pour un espace de travail ou un élément spécifique

* Paramètres de l’espace de travail : chaque étape a son propre espace de travail

* Contenu et paramètres de l’application : pour déployer vos applications, consultez [Déploiement d’applications Power BI](#deploying-power-bi-apps)

Les propriétés de jeu de données suivantes ne sont pas copiées non plus lors du déploiement :

* Attribution de rôle

* Planification de l’actualisation

* Informations d’identification de la source de données

* Paramètres de mise en cache des requêtes (peuvent être hérités de la capacité)

* Paramètres d’approbation

## <a name="incremental-refresh"></a>Actualisation incrémentielle

Les pipelines de déploiement prennent en charge [l’actualisation incrémentielle](../admin/service-premium-incremental-refresh.md), une fonctionnalité qui offre aux jeux de données volumineux des actualisations plus rapides et plus fiables, avec une consommation plus faible.

Avec les pipelines de déploiement, vous pouvez apporter des mises à jour à un jeu de données avec actualisation incrémentielle tout en conservant les données et les partitions. Lorsque vous déployez le jeu de données, la stratégie est copiée également.

### <a name="activating-incremental-refresh-in-a-pipeline"></a>Activation de l’actualisation incrémentielle dans un pipeline

[Activez l’actualisation incrémentielle dans Power BI Desktop](../admin/service-premium-incremental-refresh.md#configure-incremental-refresh), puis publiez votre jeu de données. Après publication, la stratégie d’actualisation incrémentielle est similaire dans tout le pipeline. Elle ne peut être créée que dans Power BI Desktop.

Une fois votre pipeline configuré avec l’actualisation incrémentielle, nous vous recommandons de suivre le flux suivant :

1. Apportez des modifications à votre fichier PBIX dans Power BI Desktop. Pour éviter un long temps d’attente, vous pouvez effectuer des modifications en utilisant un échantillon de vos données.

2. Chargez votre fichier PBIX à la phase de *développement*.

3. Déployez votre contenu à la phase de *test*. Après le déploiement, les modifications que vous avez apportées s’appliqueront à l’ensemble du jeu de données utilisé.

4. Vérifiez les modifications que vous avez apportées à la phase de *test*, puis effectuez le déploiement à la phase de *production*.

### <a name="usage-examples"></a>Exemples d'utilisation

Voici quelques exemples d’intégrations possibles de l’actualisation incrémentielle avec des pipelines de déploiement.

* [Créez un pipeline](deployment-pipelines-get-started.md#step-1---create-a-deployment-pipeline) et connectez-le à un espace de travail avec un jeu de données sur lequel l’actualisation incrémentielle est activée.

* Activez l’actualisation incrémentielle dans un jeu de données qui se trouve déjà dans un espace de travail de *développement* .  

* Créez un pipeline à partir d’un espace de travail de production comprenant un jeu de données qui utilise l’actualisation incrémentielle. Pour cela, affectez l’espace de travail à la phase de *production* d’un nouveau pipeline, puis utilisez le [déploiement en arrière](deployment-pipelines-get-started.md#backwards-deployment) pour effectuer un déploiement vers la phase de *test*, puis vers la phase de *développement*.

* Publiez un jeu de données qui utilise l’actualisation incrémentielle dans un espace de travail faisant partie d’un pipeline existant.

### <a name="limitations-and-considerations"></a>Considérations et limitations

Pour l’actualisation incrémentielle, les pipelines de déploiement ne prennent en charge que les jeux de données qui utilisent les [métadonnées de jeu de données avancées](../connect-data/desktop-enhanced-dataset-metadata.md). À partir de la version de septembre 2020 de Power BI Desktop, tous les jeux de données créés ou modifiés avec Power BI Desktop implémentent automatiquement les métadonnées de jeu de données avancées.

En cas de republication d’un jeu de données dans un pipeline actif sur lequel l’actualisation incrémentielle est activée, les modifications suivantes entraînent l’échec du déploiement en raison d’un risque de perte de données :

* Republication d’un jeu de données qui n’utilise pas l’actualisation incrémentielle pour en remplacer un autre sur lequel elle est activée

* Attribution d’un nouveau nom à une table sur laquelle l’actualisation incrémentielle est activée

* Attribution d’un nouveau nom à des colonnes non calculées dans une table sur laquelle l’actualisation incrémentielle est activée

D’autres modifications, comme l’ajout ou la suppression d’une colonne, ou l’attribution d’un nouveau nom à une colonne calculée, sont autorisées. Toutefois, si elles affectent l’affichage, une actualisation est nécessaire pour qu’elles deviennent visibles.

## <a name="deploying-power-bi-apps"></a>Déploiement d’applications Power BI

[Les applications Power BI](../consumer/end-user-apps.md) sont la méthode recommandée pour distribuer du contenu aux consommateurs Power BI gratuits. Avec les pipelines de déploiement, vous pouvez gérer des applications Power BI dans un pipeline de déploiement, afin de disposer de davantage de contrôle et de flexibilité lorsqu’il s’agit du cycle de vie de votre application.

Créez une application pour chaque étape du pipeline de déploiement, afin de pouvoir tester chaque mise à jour d’application du point de vue d’un utilisateur final. Un pipeline de déploiement vous permet de gérer facilement ce processus. Utilisez le bouton Publier ou Afficher de la carte de l’espace de travail pour publier ou afficher l’application dans une étape de pipeline spécifique.

[![Capture d’écran mettant en évidence le bouton de publication de l’application, situé en bas à droite de l’étape de production.](media/deployment-pipelines-process/publish.png)](media/deployment-pipelines-process/publish.png#lightbox)

Au cours de l’étape de production, le bouton d’action principal situé dans le coin inférieur droit ouvre la page Mettre à jour l’application dans Power BI, afin que toutes les mises à jour de contenu soient disponibles pour les utilisateurs de l’application.

[![Capture d’écran mettant en évidence le bouton de mise à jour de l’application, situé en bas à droite de l’étape de production.](media/deployment-pipelines-process/update-app.png)](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>Le processus de déploiement n’inclut pas la mise à jour du contenu ou des paramètres de l’application. Pour appliquer les modifications apportées au contenu ou aux paramètres, vous devez mettre à jour manuellement l’application dans l’étape de pipeline requise.

## <a name="permissions"></a>Autorisations

Les autorisations de pipeline et d’espace de travail sont accordées et gérées séparément. Par exemple, un utilisateur disposant d’un accès de pipeline qui n’a pas d’autorisations d’espace de travail pourra afficher le pipeline et le partager avec d’autres utilisateurs. Toutefois, cet utilisateur ne pourra pas afficher le contenu de l’espace de travail dans le pipeline, ni dans la page de l’espace de travail, et ne pourra pas effectuer de déploiements.

### <a name="user-with-pipeline-access"></a>Utilisateur avec accès au pipeline

Les utilisateurs disposant d’un accès au pipeline disposent des autorisations suivantes :

* Afficher le pipeline

* Partager le pipeline avec d’autres utilisateurs

* Modifier et supprimer le pipeline

>[!NOTE]
>L’accès au pipeline n’accorde pas d’autorisations pour afficher ou prendre des mesures sur le contenu de l’espace de travail.

### <a name="workspace-viewer"></a>Visionneuse d’espace de travail

Les visionneuses d’espace de travail qui ont *l’accès au pipeline* peuvent également effectuer les opérations suivantes :

* Consommer du contenu

>[!NOTE]
>Les visionneuses d’espace de travail ne peuvent pas accéder au jeu de données ou modifier le contenu de l’espace de travail.

### <a name="workspace-contributor"></a>Contributeur d’espace de travail

Les contributeurs d’espace de travail qui ont *l’accès au pipeline* peuvent également effectuer les opérations suivantes :

* Consommer du contenu

* Comparer les étapes

* Afficher les jeux de données

### <a name="workspace-member"></a>Membre de l’espace de travail

Les membres d’espace de travail qui ont *l’accès au pipeline* peuvent également effectuer les opérations suivantes :

* Voir le contenu de l'espace de travail

* Comparer les étapes

* Déployer des rapports et des tableaux de bord

* Supprimer des espaces de travail

### <a name="workspace-admin"></a>Administrateur de l’espace de service

Les administrateurs de l’espace de travail qui ont *l’accès au pipeline* peuvent effectuer les mêmes actions que les *membres de l’espace de travail* ainsi que les opérations suivantes :

* Assigner des espaces de travail

* Supprimer des espaces de travail

### <a name="dataset-owner"></a>Propriétaire du jeu de données

Les propriétaires de jeux de données qui sont des membres de l’espace de travail ou des administrateurs peuvent également effectuer les opérations suivantes :

* Mettre à jour les jeux de données

* Configurer des règles

>[!NOTE]
>Cette section décrit les autorisations des utilisateurs dans les pipelines de déploiement. Les autorisations indiquées dans cette section peuvent avoir des applications différentes dans d’autres fonctionnalités de Power BI.

## <a name="limitations"></a>Limites

Cette section répertorie la plupart des limitations dans les pipelines de déploiement.

* L’espace de travail doit résider sur une  [capacité Premium](../admin/service-premium-what-is.md).

* Les éléments Power BI, tels que les rapports et les tableaux de bord qui ont des [étiquettes de sensibilité](../admin/service-security-sensitivity-label-overview.md) Power BI ne peuvent pas être déployés.

* Le nombre maximal d’éléments Power BI pouvant être déployés dans un seul et même déploiement est 300.

* Pour obtenir la liste des limitations des espaces de travail, consultez [Limitations de l’affectation d’espaces de travail](deployment-pipelines-get-started.md#workspace-assignment-limitations).

* Pour obtenir la liste des éléments non pris en charge, consultez [Éléments non pris en charge](#unsupported-items).

### <a name="dataset-limitations"></a>Limitations du jeu de données

* Les jeux de données qui utilisent la connectivité des données en temps réel ne peuvent pas être déployés.

* Pendant le déploiement, si le jeu de données cible utilise une [connexion en direct](../connect-data/desktop-report-lifecycle-datasets.md), le jeu de données source doit également utiliser ce mode de connexion.

* Après le déploiement, le téléchargement d’un jeu de données (à partir de la phase où il a été déployé) n’est pas pris en charge.

* Pour obtenir la liste des limitations des règles de jeu de données, consultez [Limitations des règles de jeu de données](deployment-pipelines-get-started.md#dataset-rule-limitations).

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Présentation des pipelines de déploiement](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Meilleures pratiques pour les pipelines de déploiement](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[Bien démarrer avec les pipelines de déploiement](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Résolution des problèmes des pipelines de déploiement](deployment-pipelines-troubleshooting.md)
