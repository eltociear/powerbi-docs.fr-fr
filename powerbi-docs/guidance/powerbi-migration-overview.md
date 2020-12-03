---
title: Vue d’ensemble de la migration Power BI
description: Découvrez comment planifier et réaliser la migration d’un autre outil décisionnel tiers vers Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 8f8e58f61d2baa66cd0baf351857656588cfbe9f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419242"
---
# <a name="power-bi-migration-overview"></a>Vue d’ensemble de la migration Power BI

Les clients standardisent de plus en plus Power BI pour piloter une culture des données, ce qui implique d’activer une informatique décisionnelle libre-service gérée (SSBI), de rationaliser la remise d’une informatique décisionnelle d’entreprise et de traiter les pressions économiques. L’objectif de cette série d’articles sur la migration vers Power BI est de vous fournir des conseils pour planifier et réaliser une migration depuis un outil décisionnel tiers vers Power BI.

Ces articles sont les suivants :

1. Vue d’ensemble de la migration Power BI (le présent article)
1. [Préparer la migration vers Power BI](powerbi-migration-pre-migration-steps.md)
1. [Déterminer les besoins de migration vers Power BI (étape 1)](powerbi-migration-requirements.md)
1. [Planifier le déploiement pour la migration vers Power BI (étape 2)](powerbi-migration-planning.md)
1. [Exécuter une preuve de concept pour migrer vers Power BI (étape 3)](powerbi-migration-proof-of-concept.md)
1. [Créer du contenu à migrer vers Power BI (étape 4)](powerbi-migration-create-validate-content.md)
1. [Déployer sur Power BI (étape 5)](powerbi-migration-deploy-support-monitor.md)
1. [En savoir plus sur les migrations Power BI du client](powerbi-migration-learn-from-customers.md)

Il existe deux hypothèses : Votre organisation a déjà une plateforme décisionnelle en place, mais a décidé de migrer officiellement son contenu et ses utilisateurs vers Power BI. Le principal sujet de cette série a trait à la migration vers le service Power BI. D’autres considérations peuvent s’appliquer aux clients cloud nationaux outre celles abordées dans cette série d’articles.

L’illustration suivante montre les quatre phases principales du déploiement de Power BI dans votre organisation.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="Image présentant les quatre phases principales, décrites dans le tableau suivant.":::

|Phase|Description|
|--------|-----------|
|![Phase 1.](media/common/icon-01-red-30x30.png)|**Installer et évaluer Power BI.** La première phase implique d’établir l’architecture initiale de Power BI. Le déploiement préliminaire et la planification de la gouvernance sont traités à ce stade, ainsi que les évaluations de Power BI, notamment son retour sur investissement et/ou l’analyse coûts-avantages.|
|![Phase 2.](media/common/icon-02-red-30x30.png)|**Créer rapidement des solutions dans Power BI.** Pendant la deuxième phase, les auteurs de contenu décisionnel libre-service peuvent commencer à utiliser et évaluer Power BI pour répondre à leurs besoins, puis obtenir rapidement une valeur ajoutée de Power BI. Les activités de la phase 2 attachent beaucoup d’importance à la souplesse et la valeur métier rapide, ce qui est essentiel pour faire accepter la sélection d’un nouvel outil décisionnel comme Power BI. C’est pourquoi, dans l’illustration, les activités de la phase 2 se produisent de concert avec les activités de migration de la phase 3.|
|![Phase 3.](media/common/icon-03-red-30x30.png)|**Migrer les ressources décisionnelles de l’ancienne plateforme vers Power BI.** La troisième phase s’intéresse à la migration vers Power BI. C’est le principal sujet de cette série d’articles sur la migration vers Power BI. Les cinq étapes de migration spécifiques sont décrits dans la section suivante.|
|![Phase 4.](media/common/icon-04-red-30x30.png)|**Adopter, contrôler et superviser Power BI.** La phase finale comprend des activités permanentes comme l’entretien d’une culture des données, la communication et la formation. Ces activités exercent un impact considérable sur une implémentation de Power BI efficace. Il est important d’avoir des stratégies et processus de gouvernance et de sécurité appropriés à votre organisation, ainsi que des audits et des supervisions pour faciliter la mise à échelle, la croissance et les améliorations en continu.|

> [!IMPORTANT]
> Une migration formelle vers Power BI se produit presque toujours en parallèle avec le développement d’une nouvelle solution Power BI. Une _solution Power BI_ est un terme générique qui englobe l’utilisation à la dois des données et des rapports. Un simple fichier Power BI Desktop (pbix) peut contenir un modèle de données ou un rapport, ou les deux. La [séparation entre le modèle de données et les rapports](../guidance/report-separate-from-model.md) est encouragée à des fins de réutilisabilité des données, mais elle n’est pas obligatoire.
>
> L’utilisation de Power BI pour créer des exigences, quand vous planifiez et déroulez la migration formelle, vous permet d’en obtenir l’assentiment. Les phases simultanées offrent aux auteurs de contenu une expérience pratique et concrète avec Power BI.

## <a name="five-stages-of-a-power-bi-migration"></a>Cinq étapes d’une migration Power BI

La phase 3 de l’illustration traite de la migration vers Power BI. Cette phase se décompose en cinq étapes communes.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="Image représentant les étapes d’une migration Power BI, décrites ci-après.":::

Les étapes représentées dans l’illustration ci-dessus sont les suivantes :

- [Étapes de prémigration](#pre-migration-steps)
- [Étape 1 : Déterminer les besoins et hiérarchiser](#stage-1-gather-requirements-and-prioritize)
- [Étape 2 : Planifier le déploiement](#stage-2-plan-for-deployment)
- [Étape 3 : Exécuter une preuve de concept](#stage-3-conduct-proof-of-concept)
- [Étape 4 : Créer et valider du contenu](#stage-4-create-and-validate-content)
- [Étape 5 : Déployer, assister et superviser](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>Étapes de prémigration

Les étapes de pré-migration incluent des actions que vous envisager avant de commencer un projet de migration de contenu d’une ancienne plateforme décisionnelle vers Power BI. Cela comprend généralement la planification initiale du déploiement au niveau du locataire. Pour plus d’informations sur ces activités, consultez [Préparer la migration vers Power BI](powerbi-migration-pre-migration-steps.md).

### <a name="stage-1-gather-requirements-and-prioritize"></a>Étape 1 : Déterminer les besoins et hiérarchiser

L’accent de l’étape 1 est donné à la collecte d’informations et à la planification de la migration d’une solution unique. Ce processus doit être itératif et limité à un effort d’une ampleur raisonnable. Le résultat de l’étape 1 comprend un inventaire hiérarchisé des rapports et données à migrer. D’autres activités dans les étapes 2 et 3 sont nécessaires pour estimer complètement le niveau de l’effort. Pour plus d’informations sur les activités de l’étape 1, consultez [Déterminer les besoins de migration vers Power BI](powerbi-migration-requirements.md).

### <a name="stage-2-plan-for-deployment"></a>Étape 2 : Planifier le déploiement

L’étape 2 se concentre sur la manière de satisfaire aux besoins définis à l’étape 1 pour chaque solution spécifique. Le résultat de l’étape 2 comprend autant de détails que possible pour orienter le processus, bien qu’il s’agisse d’un processus itératif et non linéaire. La création d’une preuve de concept (étape 3) peut avoir lieu en parallèle avec cette étape. Même pendant la création de la solution (étape 4), des informations supplémentaires peuvent faire surface et influencer les décisions liées à la planification du déploiement. Ce type de planification du déploiement à l’étape 2 porte sur le niveau de la solution, tout en respectant les décisions déjà prises au niveau de l’organisation. Pour plus d’informations sur les activités de l’étape 2, consultez [Planifier le déploiement pour la migration vers Power BI](powerbi-migration-planning.md).

### <a name="stage-3-conduct-proof-of-concept"></a>Étape 3 : Exécuter une preuve de concept

L’objectif de l’étape 3 est de traiter les problèmes inconnus et d’atténuer les risques le plus tôt possible. Une preuve de concept (POC) technique s’avère utile pour valider des hypothèses. Elle peut être effectuée de manière itérative en même temps que la planification du déploiement (étape 2). Le résultat de cette étape est une solution Power BI dont l’étendue est étroite. Notez que notre intention n’est pas que la preuve de concept soit un travail supprimable. En revanche, un travail supplémentaire en phase 4 sera probablement nécessaire pour qu’elle soit prête à être mise en production. À cet égard, dans votre organisation, vous pouvez faire référence à cette activité comme un prototype, un pilote, une maquette, un démarrage rapide ou un produit à viabilité minimale. L’exécution d’une preuve de concept n’est pas toujours nécessaire et peut se dérouler de manière informelle. Pour plus d’informations sur les activités de l’étape 3, consultez [Exécuter une preuve de concept pour migrer vers Power BI](powerbi-migration-proof-of-concept.md).

### <a name="stage-4-create-and-validate-content"></a>Étape 4 : Créer et valider du contenu

L’étape 4 se produit quand le travail réel de conversion de la preuve de concept en solution prête pour la production est terminé. Le résultat de cette étape est une solution Power BI terminée qui a été validée dans un environnement de développement. Cette solution doit être prête pour le déploiement à l’étape 5. Pour plus d’informations sur les activités de l’étape 4, consultez [Créer du contenu à migrer vers Power BI](powerbi-migration-create-validate-content.md).

### <a name="stage-5-deploy-support-and-monitor"></a>Étape 5 : Déployer, assister et superviser

L’objectif principal de l’étape 5 est de déployer la nouvelle solution Power BI en production. Le résultat de cette étape est une solution de production activement utilisée par les utilisateurs métier. Quand vous utilisez une méthodologie souple, il est acceptable de planifier certaines améliorations à apporter à une future itération. Selon votre niveau d’aisance avec Power BI, par exemple pour réduire les risques et les perturbations pour les utilisateurs, vous pouvez choisir d’effectuer un déploiement progressif. Ou bien, vous pouvez effectuer un déploiement initial sur un petit groupe d’utilisateurs pilotes. L’assistance et la supervision sont également importantes à ce stade et en continu. Pour plus d’informations sur les activités de l’étape 5, consultez [Migrer vers Power BI](powerbi-migration-deploy-support-monitor.md).

> [!TIP]
> La plupart des concepts décrits dans cette série d’articles sur la migration Power BI s’appliquent aussi à un projet d’implémentation de Power BI standard.

## <a name="consider-migration-reasons"></a>Prendre en compte les raisons de la migration

Construire une culture des données productive et saine est l’un des objectifs principaux de nombreuses organisations. Power BI est un excellent outil pour atteindre cet objectif. Les trois raisons les plus citées pour lesquelles vous pouvez envisager une migration vers Power BI se répartissent comme suit :

- **Favoriser une informatique décisionnelle en libre-service gérée** en introduisant de nouvelles fonctionnalités qui autonomisent sa communauté d’utilisateurs. Power BI rend l’accès aux informations et à la prise de décision plus largement disponible, tout en s’appuyant moins sur des compétences de spécialistes éventuellement difficiles à trouver.
- **Rationaliser l’offre d’informatique décisionnelle de l’entreprise** pour satisfaire à des besoins qui ne sont pas remplis par les outils existants, tout en diminuant le niveau de complexité, réduisant le coût de possession et/ou standardisant les pratiques issues de plusieurs outils décisionnels déjà utilisés.
- **Gérer les pressions économiques** pour une productivité accrue avec moins de ressources, de temps et de personnel.

## <a name="achieve-power-bi-migration-success"></a>Réussir la migration Power BI

Chaque migration est légèrement différente. Elle peut dépendre de la structure de l’organisation, des stratégies de données, de la maturité de la gestion des données et des objectifs de l’organisation. En revanche, il existe des pratiques que nous voyons systématiquement chez nos clients qui réussissent parfaitement leur migration Power BI.

- **Parrainage exécutif :** Identifiez un parrain exécutif au tout début du processus. Cette personne doit soutenir activement le décisionnel dans l’organisation et s’investir personnellement pour obtenir réussir la migration. Idéalement, le parrain exécutif détient l’autorité ultime et la responsabilité des résultats liés à Power BI.
- **Formation, support et communication :** Reconnaissez qu’il ne s’agit pas simplement d’une initiative technologique. Tout projet de décisionnel ou d’analytique est également une initiative de personnes. Alors pensez à investir précocement dans la formation et le support des utilisateurs. De plus, créez un plan de communication qui explique de manière transparente à toutes les parties prenantes ce qui se passe et pourquoi, en définissant des attentes réalistes. Veillez à inclure une boucle de commentaires dans votre plan de communication pour recueillir les réactions des parties prenantes.
- **Gains rapides :** Au départ, hiérarchisez les éléments à valeur métier élevée tangible et urgents. Au lieu de tenter strictement de toujours migrer les rapports exactement comme ils apparaissent dans l’ancienne plateforme décisionnelle, concentrez-vous sur la question métier à laquelle le rapport tente de répondre (y compris sur les mesures à prendre) quand vous traitez le rapport remanié.
- **Modernisation et améliorations :** Soyez prêt à repenser la façon dont les choses ont toujours été effectuées. Une migration peut offrir une opportunité d’apporter des améliorations. Par exemple, elle permet d’éliminer la préparation manuelle des données ou de déplacer des règles métier qui se limitaient à un rapport unique. Envisagez de refactoriser, de moderniser et de consolider des solutions existantes lorsque l’effort peut être justifié. Une migration peut impliquer de rassembler plusieurs rapports en un seul, ou d’éliminer des artefacts hérités qui n’ont pas été utilisés depuis longtemps.
- **Apprentissage continu :** Préparez-vous à utiliser une approche progressive tout en continuant à apprendre et à vous adapter. Travaillez par cycle court et itératif pour apporter rapidement de la valeur. Réalisez régulièrement des petites preuves de concept pour réduire les risques liés aux problèmes inconnus, valider des hypothèses et découvrir de nouvelles fonctionnalités. Comme Power BI est un service cloud qui se met à jour tous les mois, il est important de se tenir informé des développements et de se former si besoin.
- **Résistance au changement :** Comprenez qu’il peut y avoir différents niveaux de résistance au changement ; certains utilisateurs rechignent à se former à un nouvel outil. De plus, certains professionnels qui ont consacré des efforts et un temps considérables à acquérir un savoir-faire avec un autre outil décisionnel risquent de se sentir menacés par cette évolution. Soyez prêt, car une migration peut entraîner des batailles politiques internes, en particulier dans les organisations très décentralisées.
- **Contraintes :** Soyez réaliste avec les plans de migration, en incluant le financement, les estimations de temps, ainsi que les rôles et responsabilités de toutes les personnes concernées.

## <a name="acknowledgments"></a>Remerciements

Cette série d’articles a été écrite par Melissa Coates, MVP des plateformes de données et propriétaire de [Coates Data Strategies](https://www.coatesdatastrategies.com/). Les contributeurs et réviseurs sont les suivants : Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger et Peter Myers.

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série sur la migration Power BI](powerbi-migration-pre-migration-steps.md), découvrez les étapes de prémigration.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Migrer les rapports SSRS vers Power BI](migrate-ssrs-reports-to-power-bi.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
