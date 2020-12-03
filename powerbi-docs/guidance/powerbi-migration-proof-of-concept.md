---
title: Exécuter une preuve de concept pour migrer vers Power BI
description: Conseils sur l’exécution d’une preuve de concept lors de la migration vers Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 77174da7fd47470974a292ba98f6b50c268b04fd
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419127"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>Exécuter une preuve de concept pour migrer vers Power BI

Cet article décrit l’**étape 3**, qui a trait à l’exécution d’une preuve de concept (POC) pour atténuer les risques et résoudre les problèmes inconnus le plus tôt possible lors de la migration vers Power BI.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Image illustrant les étapes d’une migration Power BI. L’étape 3 est mise en évidence pour cet article.":::

> [!NOTE]
> Pour obtenir une explication complète de l’illustration ci-dessus, consultez [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md).

L’objectif de l’étape 3 est de traiter les problèmes inconnus et d’atténuer les risques le plus tôt possible. Une preuve de concept technique s’avère utile pour valider des hypothèses. Elle peut être exécutée de manière itérative en même temps que la planification du déploiement de la solution (décrite à l’[étape 2](powerbi-migration-planning.md)).

Le résultat de cette étape est une solution Power BI dont l’étendue est limitée, qui traite les questions ouvertes initiales et qui est prête pour le travail supplémentaire de l’[étape 4](powerbi-migration-create-validate-content.md) visant à sa mise en production.

> [!IMPORTANT]
> Notre intention n’est pas que la preuve de concept soit un travail supprimable. Nous pensons plutôt qu’il s’agit d’une itération précoce de la solution prête pour la production. Dans votre organisation, vous pouvez considérer cette activité comme un prototype, un pilote, une maquette, un démarrage rapide ou un produit à viabilité minimale. L’exécution d’une preuve de concept n’est pas toujours nécessaire et peut même se produire de manière informelle.

> [!TIP]
> La plupart des sujets abordés dans cet article s’appliquent également à un projet d’implémentation standard de Power BI. À mesure que votre organisation acquiert de l’expérience avec Power BI, la nécessité d’exécuter des preuves de concept diminue. Toutefois, en raison de la cadence de publication rapide de Power BI et de l’introduction continue de nouvelles fonctionnalités, vous pouvez exécuter régulièrement des preuves de concept techniques à des fins d’apprentissage.

## <a name="set-poc-goals-and-scope"></a>Définir des objectifs et une étendue de preuve de concept

Quand vous exécutez une preuve de concept, concentrez-vous sur les objectifs suivants :

- Vérifiez vos hypothèses sur le fonctionnement d’une fonctionnalité.
- Renseignez-vous sur les différences entre le fonctionnement de Power BI et celui de l’ancienne plateforme décisionnelle.
- Vérifiez les compréhensions initiales de certaines exigences auprès des experts techniques.
- Créez un petit jeu de données avec des données réelles pour comprendre et détecter tout problème lié à la structure de données, aux relations, aux types de données ou aux valeurs de données.
- Faites des essais pour valider les expressions [de syntaxe DAX](/dax/) utilisées par les calculs de modèle.
- Testez la connectivité des sources de données à l’aide d’une passerelle (si la source doit être une passerelle).
- Testez l’actualisation des données à l’aide d’une passerelle (si la source doit être une passerelle).
- Vérifiez les configurations de sécurité, notamment la sécurité au niveau des lignes, le cas échéant.
- Faites des essais pour déterminer disposition et esthétique.
- Vérifiez que toutes les fonctionnalités du service Power BI marchent comme prévu.

L’étendue de la preuve de concept dépend des problèmes inconnus ou des objectifs à valider avec des collègues. Pour en réduire la complexité, préférez une preuve de concept aussi étroite que possible en termes d’étendue.

La plupart du temps, avec une migration, les exigences sont bien connues parce qu’il existe une solution existante à partir de laquelle commencer. En revanche, en fonction du degré des améliorations à apporter ou des compétences Power BI existantes, une preuve de concept apporte quand même une valeur ajoutée importante. De plus, un prototypage rapide avec des commentaires des consommateurs peut s’avérer utile pour clarifier rapidement les exigences, en particulier si des améliorations sont apportées.

> [!IMPORTANT]
> Même si une preuve de concept n’utilise qu’une partie des données, ou si elle inclut uniquement des visuels limités, il est souvent important de l’exécuter du début à la fin. Autrement dit, du développement dans Power BI Desktop au déploiement sur un espace de travail de développement dans le service Power BI. C’est la seule façon d’atteindre complètement les objectifs de la preuve de concept. Cela se vérifie particulièrement quand le service Power BI doit fournir des fonctionnalités critiques que vous n’avez pas utilisées auparavant, comme un jeu de données DirectQuery utilisant une authentification unique. Pendant la preuve de concept, concentrez vos efforts sur les aspects sur lesquels vous n’avez pas de certitudes ou que vous avez besoin de vérifier auprès d’autres personnes.

## <a name="handle-differences-in-power-bi"></a>Gérer les différences dans Power BI

Power BI peut servir d’_outil basé sur un modèle_ ou d’_outil basé sur un rapport_. Une solution basée sur un modèle implique le développement d’un modèle de données, tandis qu’une solution basée sur un rapport se connecte à un modèle de données déjà déployé.

En raison de sa flexibilité extrême, certains aspects de Power BI peuvent être fondamentalement différents de l’ancienne plateforme décisionnelle à partir de laquelle vous effectuez la migration.

### <a name="consider-redesigning-the-data-architecture"></a>Envisager de reconcevoir l’architecture de données

Si vous effectuez une migration à partir d’une ancienne plateforme décisionnelle qui a sa propre couche sémantique, la création d’un jeu de données d’importation est probablement une bonne idée. Power BI fonctionne mieux avec une conception de table de [schéma en étoile](star-schema.md). Ainsi, si la couche sémantique héritée n’est pas un schéma en étoile, il est possible qu’une reconception soit nécessaire pour tirer pleinement parti de Power BI. Déployer des efforts pour définir une couche sémantique qui respecte les principes de conception du schéma en étoile (notamment les relations, les mesures couramment utilisées et une terminologie organisationnelle conviviale) constitue un excellent point de départ pour les auteurs de rapports libre-service.

Si vous effectuez une migration à partir d’une ancienne plateforme décisionnelle dans laquelle les rapports font référence à des sources de données relationnelles à l’aide de requêtes SQL ou de procédures stockées, et si vous envisagez d’utiliser Power BI en [mode DirectQuery](../connect-data/desktop-use-directquery.md), vous avez des chances de réussir une migration individuelle du modèle de données.

> [!CAUTION]
> Si vous voyez qu’un grand nombre de fichiers Power BI Desktop comprenant une seule table importée sont créés, cela indique en général que la conception n’est pas optimale. Si vous rencontrez ce cas, déterminez si l’utilisation de [jeux de données partagés](../connect-data/service-datasets-across-workspaces.md) créés à l’aide d’une conception de [schéma en étoile](star-schema.md) permet d’obtenir un meilleur résultat.

### <a name="decide-how-to-handle-dashboard-conversions"></a>Conversations visant à déterminer comment gérer les tableaux de bord

En informatique décisionnelle, un tableau de bord est une collection de visuels qui présentent des métriques clés sur une seule page. En revanche, dans Power BI, un tableau de bord représente une fonctionnalité de visualisation spécifique qui peut uniquement être créée dans le service Power BI. Quand vous migrez un tableau de bord à partir d’une ancienne plateforme décisionnelle, vous avez deux possibilités :

1. Le tableau de bord hérité peut être recréé sous forme de _rapport_ Power BI. La plupart des rapports sont créés avec Power BI Desktop. Les rapports paginés et les rapports Excel sont des options alternatives, également.
2. Le tableau de bord hérité peut être recréé sous forme de _tableau de bord_ Power BI. Les [tableaux de bord](../fundamentals/service-basic-concepts.md#dashboards) sont une fonctionnalité de visualisation du service Power BI. Les visuels de tableau de bord sont souvent créés en épinglant des visuels issus d’un ou plusieurs rapports, de Questions et réponses ou de Quick Insights.

> [!TIP]
> Étant donné que les tableaux de bord sont un type de contenu Power BI, évitez d’utiliser le mot _tableau de bord_ dans le nom du rapport ou du tableau de bord.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>Se concentrer sur la situation dans son ensemble pour recréer des visuels

Chaque outil décisionnel comporte ses atouts et priorités. C’est pourquoi les visuels de rapport exacts dont vous dépendiez sur une ancienne plateforme décisionnelle peuvent ne pas avoir d’équivalent proche dans Power BI.

Quand vous recréez des visuels de rapport, concentrez-vous davantage sur les questions métier globales traitées par le rapport. La tentation de répliquer la conception de chaque visuel exactement de la même façon est ainsi oubliée. Alors que les consommateurs de contenu apprécient la cohérence des rapports migrés, il est important de ne pas se perdre dans des débats chronophages sur des détails peu importants.

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série sur la migration vers Power BI](powerbi-migration-create-validate-content.md), découvrez l’étape 4, qui concerne la création et la validation du contenu.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
