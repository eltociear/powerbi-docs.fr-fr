---
title: Préparer la migration vers Power BI
description: Conseils sur les étapes de prémigration à effectuer dans le cadre d’une migration vers Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: fba37d9f73ea0f61d8a43dc46cd13a5835d4d2a9
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525797"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Préparer la migration vers Power BI

Cet article décrit les actions que vous pouvez entreprendre avant de commencer la migration vers Power BI.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Image illustrant les étapes d’une migration vers Power BI. Cet article se concentre sur les étapes de prémigration.":::

> [!NOTE]
> Pour obtenir une explication complète de l’illustration ci-dessus, consultez [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md).

Les étapes de prémigration mettent l’accent sur la planification initiale, qui est une préparation importante avant de passer aux cinq étapes de la migration. La plupart des étapes de prémigration sont à effectuer une seule fois. Toutefois, dans les grandes organisations, certaines opérations doivent être réitérées pour chaque division ou service.

Les étapes de prémigration visent à produire au final un modèle de gouvernance initial, une planification initiale du déploiement général ainsi qu’un inventaire des rapports et des données à migrer. Vous aurez besoin de certaines informations complémentaires collectées lors des activités des étapes 1, 2 et 3 pour faire une estimation précise du niveau d’effort à prévoir pour la migration de chaque solution.

> [!TIP]
> La plupart des sujets abordés dans cet article s’appliquent également à tout projet d’implémentation standard de Power BI.

## <a name="create-costbenefit-analysis-and-evaluation"></a>Créer une analyse et une évaluation des coûts/avantages

Plusieurs choses importantes sont à faire lors de l’évaluation initiale, notamment :

- Clarifier le business case et la stratégie décisionnelle pour atteindre l’état futur spécifique souhaité.
- Préciser le sens de « réussite » ainsi que la façon de mesurer la progression et la réussite de l’initiative de migration.
- Estimer les coûts et calculer le retour sur investissement (ROI).
- Mener à bien plusieurs initiatives Power BI productives à plus petite échelle et moins complexes.

## <a name="identify-stakeholders-and-executive-support"></a>Identifier les parties prenantes et le soutien exécutif

Voici plusieurs éléments à prendre en considération pour identifier les parties prenantes :

- Assurez-vous que les parties prenantes sont en phase avec le business case et la stratégie décisionnelle.
- Incluez des représentants de toutes les divisions, même si la migration de leur contenu est prévue plus tard, pour comprendre leurs motivations et leurs préoccupations.
- Impliquez les champions Power BI dès le début.
- Établissez un plan de communication avec les parties prenantes et respectez-le.

> [!TIP]
> Si vous craignez de commencer à trop communiquer, c’est probablement bon signe.

## <a name="generate-initial-governance-model"></a>Générer un modèle de gouvernance initial

Voici plusieurs éléments importants à définir dès le départ dans une implémentation Power BI :

- Les objectifs propres à l’adoption de Power BI et la place tenue par Power BI dans la stratégie décisionnelle globale de l’organisation.
- La manière dont le rôle Administrateur Power BI sera géré, en particulier dans les organisations décentralisées.
- Les stratégies d’obtention de données approuvées : utilisation de sources de données faisant autorité, résolution des problèmes de qualité des données, et emploi d’une terminologie cohérente et de définitions communes.
- La stratégie de sécurité et de confidentialité des données à appliquer pour les sources de données, les modèles de données, les rapports et le contenu livré aux utilisateurs internes et externes.
- La manière dont les exigences d’audit, de réglementation et de conformité internes et externes seront remplies.

> [!IMPORTANT]
> Le modèle de gouvernance le plus performant est celui qui trouve le juste équilibre entre l’autonomisation des utilisateurs et le niveau de contrôle nécessaire. Pour plus d’informations, consultez [Discipline au niveau de la base](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) et [Flexibilité en périphérie](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="conduct-initial-deployment-planning"></a>Effectuer la planification initiale du déploiement

La planification initiale du déploiement consiste à définir les standards, les stratégies et les préférences pour l’implémentation de Power BI dans l’organisation.

Notez que l’[étape 2](powerbi-migration-planning.md) fait référence à la planification du déploiement au niveau de la solution. Les activités de l’étape 2 doivent être alignées autant que possible sur les décisions prises au niveau de l’organisation.

Voici des éléments critiques à définir dès le départ dans une implémentation Power BI :

- Les décisions relatives aux [paramètres du locataire Power BI](admin-tenant-settings.md), qui doivent être documentées.
- Les décisions liées à la [gestion des espaces de travail](../collaborate-share/service-new-workspaces.md), qui doivent être documentées.
- Les considérations et les préférences ayant trait aux données et aux [méthodes de distribution du contenu](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md), comme les applications, les espaces de travail, le partage, les abonnements et l’incorporation de contenu.
- Les préférences relatives aux [modes de jeu de données](../connect-data/service-dataset-modes-understand.md), comme l’utilisation du mode Import, du mode DirectQuery ou d’une combinaison de ces deux modes dans un [modèle Composite](composite-model-guidance.md).
- La [sécurisation des données et des accès](../admin/service-admin-power-bi-security.md).
- Le recours aux [jeux de données partagés](../connect-data/service-datasets-share.md) pour la réutilisation des données.
- L’application d’une [certification des données](../connect-data/service-datasets-certify.md) pour promouvoir l’utilisation de données faisant autorité et jugées fiables.
- L’utilisation de différents [types de rapports](../create-reports/index.yml), parmi lesquels les rapports Power BI, les rapports Excel ou les rapports paginés selon les cas d’usage ou les divisions.
- Les approches de gestion des changements pour les artefacts BI centralisés et les artefacts BI gérés par l’entreprise.
- Les plans de formation destinés aux consommateurs, aux modélisateurs de données, aux auteurs de rapports et aux administrateurs.
- Le support mis à la disposition des auteurs de contenu au moyen de [modèles Power BI Desktop](../create-reports/desktop-templates.md), de [visuels personnalisés](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/) et de standards documentés pour la conception des rapports.
- Les procédures et processus à prévoir pour répondre aux besoins des utilisateurs, comme la demande de nouvelles licences, l’ajout de nouvelles sources de données de passerelle, l’obtention d’une autorisation d’accès aux sources de données de passerelle, la demande de nouveaux espaces de travail, les modifications des autorisations sur les espaces de travail et diverses autres exigences courantes souvent observées.

> [!IMPORTANT]
> La planification du déploiement est un processus itératif. Les décisions relatives au déploiement seront affinées et complétées à de multiples reprises à mesure que votre organisation devient plus expérimentée avec Power BI et que le service Power BI évolue. Les décisions prises durant ce processus seront appliquées lors de la planification du déploiement au niveau de la solution, abordée à l’[étape 2](powerbi-migration-planning.md) du processus de migration.

## <a name="establish-initial-architecture"></a>Établir l’architecture initiale

Votre [architecture de solution décisionnelle](center-of-excellence-business-intelligence-solution-architecture.md) évoluera et mûrira avec le temps. Les tâches de configuration de Power BI à effectuer dès maintenant sont les suivantes :

- Configurer le locataire Power BI et l’intégrer à Azure Active Directory.
- Définir les [administrateurs Power BI](../admin/service-admin-role.md).
- Obtenir et attribuer les [licences utilisateur](../admin/service-admin-licensing-organization.md) initiales.
- Configurer et vérifier les [paramètres du locataire Power BI](admin-tenant-settings.md).
- Configurer les [rôles d’espace de travail](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) et attribuer l’accès aux utilisateurs et groupes de sécurité Azure Active Directory.
- Configurer un cluster de [passerelle de données](../connect-data/service-gateway-deployment-guidance.md) initial, avec un plan à mettre à jour régulièrement.
- Obtenir une [licence de capacité Premium](../admin/service-admin-premium-purchase.md) (s’il y a lieu).
- Configurer les [charges de travail de capacité Premium](../admin/service-admin-premium-workloads.md), avec un plan à gérer en continu.

## <a name="define-success-criteria-for-migration"></a>Définir les critères de réussite de la migration

La première tâche consiste à savoir ce que l’on entend par « réussir » la migration d’une solution individuelle. Les questions à poser sont notamment les suivantes :

- **Quels sont les motivations et les objectifs sous-jacents à cette migration ?** Pour plus d’informations, consultez [Vue d’ensemble de la migration vers Power BI (section sur les motifs de la migration à prendre en compte)](powerbi-migration-overview.md#consider-migration-reasons). Cet article décrit les motifs les plus fréquents d’une migration vers Power BI. Vous devez bien sûr définir vos objectifs au niveau de l’organisation. En fait, la migration peut avoir des objectifs différents : telle solution décisionnelle héritée sera migrée pour faire des économies substantielles, et telle autre solution BI héritée sera migrée principalement pour optimiser le workflow.
- **Quels sont les coûts/avantages ou le ROI attendus pour cette migration ?** Pour mesurer la réussite, il est utile d’avoir une compréhension claire des attentes en matière de coûts, d’accroissement des capacités, de simplification ou d’une plus grande agilité. Cela peut vous aider à établir des principes directeurs qui faciliteront la prise de décision pendant le processus de migration.
- **Quels indicateurs de performance clés (KPI) seront utilisés pour mesurer la réussite ?** Voici quelques exemples d’indicateurs de performance clés :
    - Nombre de rapports générés à partir d’une plateforme décisionnelle héritée, en baisse d’un mois sur l’autre.
    - Nombre de rapports générés à partir de Power BI, en hausse d’un mois sur l’autre.
    - Nombre de consommateurs de rapports Power BI, en hausse d’un trimestre sur l’autre.
    - Pourcentage de rapports migrés en production par date cible.
    - Réduction des coûts de licences d’une année sur l’autre.

> [!TIP]
> Le [journal d’activité de Power BI](../admin/service-admin-auditing.md) peut servir de source pour mesurer la progression des indicateurs de performance clés.

## <a name="prepare-inventory-of-existing-reports"></a>Préparer l’inventaire des rapports existants

La préparation d’un inventaire des rapports existants dans la plateforme décisionnelle héritée est une étape essentielle pour savoir précisément ce qui existe déjà. La finalité de cette étape est d’obtenir des informations permettant d’évaluer le niveau d’effort associé à la migration. La préparation d’un inventaire peut inclure les activités suivantes :

1. **Inventaire des rapports :** dressez une liste des rapports et des tableaux de bord susceptibles d’être migrés.
2. **Inventaire des sources de données :** dressez une liste de toutes les sources de données auxquelles les rapports existants accèdent. Cet inventaire doit inclure aussi bien les sources de données générales de l’entreprise que les sources de données spécifiques des services et des utilisateurs. Ce processus peut découvrir des sources de données qui ne sont pas connues du service informatique (ce que l’on désigne souvent sous le terme de _Shadow IT_).
3. **Journal d’audit :** récupérez les données du journal d’audit de la plateforme décisionnelle héritée pour comprendre les modèles d’usage et établir plus facilement les priorités. Les informations importantes à prendre du journal d’audit sont :
    - Le nombre moyen de fois où chaque rapport a été généré par semaine/mois/trimestre.
    - Le nombre moyen de consommateurs de chaque rapport par semaine/mois/trimestre.
    - Les consommateurs de chaque rapport, en particulier les rapports utilisés par l’exécutif.
    - La dernière date à laquelle chaque rapport a été généré.

> [!NOTE]
> La plupart du temps, le contenu n’est pas migré en l’état vers Power BI. La migration représente une occasion de repenser l’architecture des données et/ou d’améliorer la livraison des rapports. La compilation d’un inventaire des rapports est cruciale pour savoir ce qui existe déjà et commencer à évaluer ce qui aurait besoin d’être remanié. Les autres articles de cette série décrivent les améliorations possibles plus en détail.

## <a name="explore-automation-options"></a>Explorer les options d’automatisation

Il n’est pas possible d’automatiser tout un processus de migration vers Power BI de bout en bout.

Automatiser la réalisation de l’inventaire existant des données et des rapports est envisageable si vous disposez d’un outil offrant cette possibilité. Le degré d’automatisation de certaines parties du processus de migration, comme établir l’inventaire existant, dépend fortement des outils que vous avez à disposition.

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série sur la migration vers Power BI](powerbi-migration-requirements.md), découvrez l’étape 1, qui concerne la collecte et la hiérarchisation des exigences pour la migration vers Power BI.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
