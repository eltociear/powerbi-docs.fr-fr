---
title: Résolution des problèmes des pipelines de déploiement
description: Résoudre les problèmes des pipelines de déploiement dans Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: fda846a19b5c6081c59f08f2bf9f94eddbc9852c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148547"
---
# <a name="deployment-pipelines-troubleshooting-preview"></a>Résolution des problèmes liés aux pipelines de déploiement (préversion)

Utilisez cet article pour résoudre les problèmes liés aux pipelines de déploiement.

## <a name="general"></a>Général

### <a name="whats-deployment-pipelines-in-power-bi"></a>Pipelines de déploiement dans Power BI

Pour comprendre les pipelines de déploiement dans Power BI, reportez-vous à la [présentation des pipelines de déploiement](deployment-pipelines-overview.md).

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>Comment prendre en main les pipelines de déploiement ?

Commencez à utiliser les pipelines de déploiement à l’aide de nos [instructions de prise en main](deployment-pipelines-get-started.md).

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>Pourquoi ne puis-je pas voir le bouton de pipelines de déploiement ?

Si les conditions suivantes ne sont pas remplies, vous ne pourrez pas voir le bouton de pipelines de déploiement.

* Vous êtes un [utilisateur Power BI Pro](../admin/service-admin-purchasing-power-bi-pro.md)

* Vous appartenez à une organisation qui dispose d’une capacité Premium

* Un espace de travail ne peut être affecté qu’à un seul pipeline

* Vous êtes administrateur d’un nouvel espace de travail

## <a name="licensing"></a>Licences

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>Quelles sont les licences nécessaires pour travailler avec les pipelines de déploiement ?

Pour utiliser les pipelines de déploiement, vous devez être un [utilisateur Pro](../admin/service-admin-purchasing-power-bi-pro.md) avec une [capacité Premium](../admin/service-premium-what-is.md). Pour plus d’informations, consultez [Accès aux pipelines de déploiement](deployment-pipelines-get-started.md#accessing-deployment-pipelines).

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>Quel type de capacité puis-je attribuer à un espace de travail dans un pipeline ?

Tous les espaces de travail d’un pipeline de déploiement doivent se trouver dans une capacité dédiée pour que le pipeline soit fonctionnel. Toutefois, vous pouvez utiliser différentes capacités pour différents espaces de travail dans un pipeline. Vous pouvez également utiliser différents types de capacité pour différents espaces de travail dans le même pipeline.

Pour le développement et les tests, vous pouvez utiliser une capacité A ou EM en plus d’un compte Power BI Pro pour chaque utilisateur.

Pour les espaces de travail de production, vous avez besoin d’une capacité P. Si vous êtes un éditeur de logiciels indépendant distribuant du contenu via des applications incorporées, vous pouvez également utiliser les capacités A ou EM pour la production.

## <a name="technical"></a>Technique

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>Pourquoi ne puis-je pas voir tous mes espaces de travail lorsque j’essaie d’affecter un espace de travail à un pipeline ?

Pour affecter un espace de travail à un pipeline, les conditions suivantes doivent être remplies :

* L’espace de travail est une [nouvelle expérience d’espace de travail](../collaborate-share/service-create-the-new-workspaces.md)

* Vous êtes administrateur de l’espace de travail

* L’espace de travail n’est affecté à aucun autre pipeline

* L’espace de travail se trouve sur une capacité [Premium](../admin/service-premium-what-is.md)

Les espaces de travail qui ne respectent pas ces conditions ne sont pas affichés dans la liste des espaces de travail que vous pouvez sélectionner.

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>Comment puis-je attribuer des espaces de travail à toutes les étapes d’un pipeline ?

Vous pouvez affecter un espace de travail par pipeline. Une fois qu’un espace de travail est affecté à un pipeline, vous pouvez le déployer sur les étapes suivantes du pipeline. Lors du premier déploiement, un nouvel espace de travail est créé avec des copies des éléments à l’étape source. Les relations des éléments copiés sont conservées. Pour plus d’informations, consultez [Comment affecter un espace de travail à un pipeline de déploiement](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline).

### <a name="why-did-my-first-deployment-fail"></a>Pourquoi mon premier déploiement échoue-t-il ?

Votre premier déploiement peut avoir échoué pour plusieurs raisons. Certaines de ces raisons sont répertoriées dans le tableau ci-dessous.

|Erreur  |Action  |
|---------|---------|
|Vous n’avez pas [d’autorisations de capacité Premium](deployment-pipelines-process.md#creating-a-premium-capacity-workspace).     |Pour obtenir des autorisations de capacité Premium, demandez à un administrateur de capacité d’ajouter votre espace de travail à une capacité ou demandez l’attribution d’autorisations pour la capacité. Une fois que l’espace de travail est dans une capacité, redéployez-le.        |
|Vous n’avez pas les autorisations d’espace de travail.     |Pour déployer, vous devez être membre de l’espace de travail. Demandez à votre administrateur d’espace de travail de vous accorder les autorisations appropriées.         |
|Votre administrateur Power BI a désactivé la création d’espaces de travail.     |Contactez votre administrateur Power BI pour obtenir de l’aide.         |
|Votre espace de travail n’est pas une [nouvelle expérience d’espace de travail](../collaborate-share/service-create-the-new-workspaces.md).     |Créez votre contenu dans la nouvelle expérience d’espace de travail. Si vous disposez de contenu dans un espace de travail classique, vous pouvez le [mettre à niveau](../collaborate-share/service-upgrade-workspaces.md) vers une nouvelle expérience d’espace de travail.         |
|Vous utilisez le [déploiement sélectif](deployment-pipelines-get-started.md#selective-deployment) et ne sélectionnez pas le jeu de données de votre contenu.     |Effectuez l’une des opérations suivantes : </br></br>Désélectionnez le contenu lié à votre jeu de données. Le contenu non sélectionné (comme les rapports ou les tableaux de bord) ne sera pas copié à l’étape suivante. </br></br>Sélectionnez le jeu de données lié au contenu sélectionné. Votre jeu de données sera copié à l’étape suivante.         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>J’obtiens un avertissement indiquant que j’ai des « artefacts non pris en charge » dans mon espace de travail lorsque j’essaie de déployer. Comment puis-je savoir quels artefacts ne sont pas pris en charge ?

Pour obtenir une liste complète des éléments et artefacts qui ne sont pas pris en charge dans les pipelines de déploiement, consultez les sections suivantes :

* [Éléments non pris en charge](deployment-pipelines-process.md#unsupported-items)

* [Propriétés d’élément qui ne sont pas copiées](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>Pourquoi mon déploiement échoue-t-il en raison de règles non respectées ?

Si vous rencontrez des problèmes lors de la configuration des règles de jeu de données, consultez [Règles de jeu de données](deployment-pipelines-get-started.md#step-4---create-dataset-rules) et assurez-vous de suivre les [limitations des règles de jeu de données](deployment-pipelines-get-started.md#dataset-rule-limitations).

Si votre déploiement a précédemment réussi et subit soudainement un échec à cause de règles non respectées, il peut s’agir d’un problème de republication d’un jeu de données. Les modifications suivantes apportées au jeu de données source entraînent l’échec du déploiement :

**Règles de paramètre**

* Un paramètre supprimé

* Un nom de paramètre modifié

**Règles de source de données**

Il manque des valeurs dans les règles de votre jeu de données. Cela peut être dû à la modification de votre jeu de données.

![Règle non respectée](media/deployment-pipelines-troubleshooting/broken-rule.png)

En cas d’échec d’un déploiement précédemment réussi en raison de liens rompus, un avertissement s’affiche. Vous pouvez cliquer sur **Configurer les règles** pour accéder au volet Paramètres de déploiement, où le jeu de données ayant échoué est marqué. Lorsque vous cliquez sur le jeu de données, les règles non respectées sont marquées.

Pour déployer avec succès, corrigez ou supprimez les règles non respectées, puis redéployez.

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>Comment puis-je modifier la source de données dans les étapes de pipeline ?

Vous ne pouvez pas modifier la connexion à la source de données dans le service Power BI.

Si vous souhaitez modifier la source de données au cours des phases de test ou de production, vous pouvez utiliser des [règles de jeu de données](deployment-pipelines-get-started.md#step-4---create-dataset-rules) ou des [API](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup). Les règles de jeu de données sont prises en compte uniquement après le prochain déploiement.

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-click-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>J’ai résolu un bogue en production, mais je ne peux pas cliquer sur le bouton « Déployer sur une phase précédente ». Pourquoi le bouton est-il grisé ?

Vous pouvez uniquement revenir sur une étape vide. Si vous avez du contenu en phase de test, vous ne pourrez pas revenir en arrière à partir de la production.

Après avoir créé le pipeline, utilisez l’étape de développement pour développer votre contenu, et les étapes de test pour l’examiner et le tester. Vous pouvez résoudre les bogues lors de ces étapes, puis déployer l’environnement corrigé sur l’étape de production.

>[!NOTE]
>Le déploiement vers l’arrière prend uniquement en charge le [déploiement complet](deployment-pipelines-get-started.md#deploying-all-content). Il ne prend pas en charge le [déploiement sélectif](deployment-pipelines-get-started.md#selective-deployment)

### <a name="does-deployment-pipelines-support-multi-geo"></a>Les pipelines de déploiement prennent-ils en charge plusieurs zones géographiques ?

Les zones géographiques multiples sont prises en charge. Le déploiement de contenu entre différentes étapes dans différentes zones géographiques peut prendre plus de temps.

## <a name="permissions"></a>Autorisations

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>Qu’est-ce que le modèle d’autorisations de pipelines de déploiement ?

Le modèle d’autorisations de pipelines de déploiement est décrit dans la section [Autorisations](deployment-pipelines-process.md#permissions).

### <a name="who-can-deploy-content-between-stages"></a>Qui peut déployer le contenu entre les étapes ?

Le contenu peut être déployé sur une étape vide ou une étape qui contient du contenu. Le contenu doit résider sur une [capacité Premium](../admin/service-premium-what-is.md).

* **Déploiement sur une étape vide** : n’importe quel [utilisateur Pro](../admin/service-admin-purchasing-power-bi-pro.md) qui est membre ou administrateur dans l’espace de travail source.

* **Déploiement sur une étape avec du contenu** : n’importe quel [utilisateur Pro](../admin/service-admin-purchasing-power-bi-pro.md) qui est membre ou administrateur des deux espaces de travail dans les étapes de déploiement source et cible.

* **Substitution d’un jeu de données** : le déploiement remplace chaque jeu de données inclus dans l’étape cible, même si le jeu de données n’a pas été modifié. L’utilisateur doit être le propriétaire de tous les jeux de données de la phase cible spécifiés dans le déploiement.

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>Quelles sont les autorisations nécessaires pour configurer des règles de jeu de données ?

Pour configurer des règles de jeu de données dans les pipelines de déploiement, vous devez être propriétaire du jeu de données.

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>Pourquoi ne puis-je pas voir les espaces de travail dans le pipeline ?

Les autorisations de pipeline et d’espace de travail sont gérées séparément. Vous pouvez avoir des autorisations de pipeline, mais pas d’autorisations d’espace de travail. Pour plus d'informations, consultez la section [Autorisations](deployment-pipelines-process.md#permissions).

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Présentation des pipelines de déploiement](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Bien démarrer avec les pipelines de déploiement](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Comprendre le processus des pipelines de déploiement](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Meilleures pratiques pour les pipelines de déploiement](deployment-pipelines-best-practices.md)