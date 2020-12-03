---
title: Déployer sur Power BI
description: Conseils sur le déploiement, le support et la surveillance du contenu lors d’une migration vers Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: bfa3ffad111c7ab819ed1269586a7b32ccf43bba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419265"
---
# <a name="deploy-to-power-bi"></a>Déployer sur Power BI

Cet article décrit l’**étape 5**, qui concerne le déploiement, le support et la surveillance du contenu lors d’une migration vers Power BI.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Image illustrant les étapes d’une migration vers Power BI. Cet article se concentre sur l’étape 5.":::

> [!NOTE]
> Pour obtenir une explication complète de l’illustration ci-dessus, consultez [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md).

L’objectif principal de l’étape 5 est de déployer la nouvelle solution Power BI en production.

La finalité de cette étape est d’obtenir une solution prête à être utilisée en production par l’entreprise. Quand vous utilisez une méthodologie agile, il est acceptable de planifier certaines améliorations à apporter à une future itération. Le support et la surveillance sont également des sujets importants à ce stade et en continu.

> [!TIP]
> À l’exception de l’exécution en parallèle et de la désactivation des rapports hérités, deux points qui sont traités ci-dessous, les sujets abordés dans cet article s’appliquent également à tout projet d’implémentation Power BI standard.

## <a name="deploy-to-test-environment"></a>Déployer dans un environnement de test

Pour les solutions gérées par le service informatique, ou les solutions qui sont essentielles à la productivité de l’entreprise, un environnement de test est généralement prévu. L’environnement de test s’intercale entre les environnements de développement et de production, mais il n’est pas obligatoire pour toutes les solutions Power BI. Un espace de travail de test peut faire office d’emplacement stable, séparé du développement, où vous effectuez les tests d’acceptation utilisateur (UAT) avant la mise en production.

Si votre contenu a été publié dans un espace de travail sur une capacité Premium, les [pipelines de déploiement](../create-reports/deployment-pipelines-overview.md) peuvent simplifier le processus de déploiement dans les espaces de travail de développement, de test et de production. La publication peut également être effectuée manuellement ou à l’aide de [scripts PowerShell](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/).

### <a name="deploy-to-test-workspace"></a>Déployer dans l’espace de travail de test

Un déploiement dans l’espace de travail de test inclut généralement les activités principales suivantes :

- **Chaînes de connexion et paramètres :** adaptez les chaînes de connexion au jeu de données si la source de données diffère entre le développement et le test. Le [paramétrage](../connect-data/service-parameters.md) permet de gérer efficacement les chaînes de connexion.
- **Contenu de l’espace de travail :** publiez les jeux de données et les rapports dans l’espace de travail de test, et créez des tableaux de bord.
- **Application.** publiez une [application](../consumer/end-user-apps.md) avec le contenu de l’espace de travail de test, s’il doit faire partie du processus de test d’acceptation utilisateur. En règle générale, les autorisations sur l’application sont limitées à un petit nombre de personnes participant aux tests d’acceptation utilisateur.
- **Actualisation des données :** [planifiez l’actualisation des jeux de données](../connect-data/refresh-scheduled-refresh.md) pour tous les jeux de données Import pendant la période de réalisation des tests d’acceptation utilisateur.
- **Sécurité :** mettez à jour ou vérifiez les [rôles d’espace de travail](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). L’accès à l’espace de travail de test est réservé à un petit nombre de personnes participant aux tests d’acceptation utilisateur.

> [!NOTE]
> Pour plus d’informations sur les options de déploiement à des fins de développement, de test et de production, consultez la section 9 du [livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP).

### <a name="conduct-user-acceptance-testing"></a>Réaliser des tests d’acceptation utilisateur

En général, les tests d’acceptation utilisateur sont effectués par des employés qui sont des experts métier. Une fois qu’ils ont vérifié le contenu, ces testeurs approuvent que le nouveau contenu est correct, qu’il remplit les exigences et qu’il peut être déployé et mis à la disposition générale des autres consommateurs.

Le niveau de formalité de ce processus de test d’acceptation utilisateur, y compris les validations par écrit, dépend de vos pratiques de gestion des changements.

## <a name="deploy-to-production-environment"></a>Déployer dans l’environnement de production

Il y a plusieurs points à prendre en compte pour le déploiement dans l’environnement de production.

### <a name="conduct-a-staged-deployment"></a>Effectuer un déploiement de préproduction

Si vous souhaitez réduire les risques et les interruptions des utilisateurs, ou si d’autres problèmes se posent, vous pouvez choisir d’effectuer un déploiement de préproduction. Le premier déploiement de production peut impliquer un petit groupe d’utilisateurs du pilote. Avec un pilote, il peut être demandé aux pilotes de fournir activement leurs commentaires.

Accordez de plus en plus d’autorisations dans l’espace de travail de production, ou sur l’application, graduellement jusqu’à ce que tous les utilisateurs cibles aient l’autorisation d’accéder à la nouvelle solution Power BI.

> [!TIP]
> Examinez le [journal d’activité de Power BI](../admin/service-admin-auditing.md) pour connaître le degré d’adoption et d’usage de la nouvelle solution Power BI par les consommateurs.

### <a name="handle-additional-components"></a>Gérer des composants supplémentaires

Durant le processus de déploiement, vous devrez peut-être travailler avec vos administrateurs Power BI sur d’autres exigences à remplir pour prendre en charge l’ensemble de la solution, par exemple :

- **Maintenance de la passerelle :** l’inscription d’une [nouvelle source de données](../connect-data/service-gateway-data-sources.md) dans la passerelle de données est parfois nécessaire.
- **Connecteurs et pilotes de passerelle :** une nouvelle source de données propriétaire peut nécessiter l’installation d’un nouveau pilote ou connecteur personnalisé sur chaque serveur dans le cluster de passerelle.
- **Créer une capacité Premium :** vous pourrez peut-être utiliser une [capacité Premium](../admin/service-premium-capacity-manage.md) existante. Il peut également y avoir des situations où une nouvelle capacité Premium est justifiée, par exemple lorsque vous souhaitez délibérément séparer la charge de travail d’un service.
- **Configurer un dataflow Power BI :** les activités de préparation des données peuvent être configurées une seule fois dans un [dataflow Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md) à l’aide de Power Query Online. Cela évite la réplication du travail de préparation des données dans de nombreux fichiers Power BI Desktop différents.
- **Inscrire un nouveau visuel organisationnel :** l’inscription d’un [visuel organisationnel](../developer/visuals/power-bi-custom-visuals-organization.md) peut s’effectuer dans le portail administrateur pour les visuels personnalisés qui ne proviennent pas d’AppSource.
- **Définir le contenu proposé :** il existe un paramètre de locataire qui contrôle qui peut [proposer du contenu](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/) dans la page d’accueil du service Power BI.
- **Définir les étiquettes de sensibilité :** toutes les [étiquettes de sensibilité](../admin/service-security-data-protection-overview.md) sont intégrées dans Microsoft Information Protection.

### <a name="deploy-to-production-workspace"></a>Déployer dans l’espace de travail de production

Un déploiement dans l’espace de travail de production inclut généralement les activités principales suivantes :

- **Gestion des changements :** si nécessaire, faites approuver le déploiement et informez l’ensemble des utilisateurs en suivant vos pratiques de gestion des changements habituelles. Il peut y avoir une période de gestion des changements approuvée pendant laquelle les déploiements de production sont autorisés. En règle générale, cela s’applique davantage au contenu géré par le service informatique qu’au contenu libre-service.
- **Plan de restauration :** dans une migration, il est considéré qu’il s’agit de migrer une nouvelle solution pour la première fois. Si du contenu existe déjà, il vaut mieux établir un plan permettant de revenir à la version précédente au besoin. Conserver les versions antérieures des fichiers Power BI Desktop (à l’aide de la gestion de versions dans SharePoint ou OneDrive) est une bonne pratique.
- **Chaînes de connexion et paramètres :** adaptez les chaînes de connexion au jeu de données quand la source de données diffère entre le test et la production. Le [paramétrage](../connect-data/service-parameters.md) peut être utilisé efficacement à cet effet.
- **Actualisation des données :** [planifiez l’actualisation de chaque jeu de données](../connect-data/refresh-scheduled-refresh.md) importé.
- **Contenu de l’espace de travail :** publiez les jeux de données et les rapports dans l’espace de travail de production, et créez des tableaux de bord. Les [pipelines de déploiement](../create-reports/deployment-pipelines-overview.md) peuvent simplifier le processus de déploiement dans les espaces de travail de développement, de test et de production si votre contenu a été publié dans des espaces de travail sur une capacité Premium.
- **Application :** si les applications font partie de votre stratégie de distribution de contenu, publiez une [application](../consumer/end-user-apps.md) avec le contenu de l’espace de travail de production.
- **Sécurité :** mettez à jour et vérifiez les [rôles d’espace de travail](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) en fonction de votre stratégie de collaboration et de distribution de contenu.
- **Paramètres des jeux de données :** mettez à jour et vérifiez les paramètres de chaque jeu de données, notamment :
  - [Approbation](../collaborate-share/service-endorse-content.md) (par exemple, certifié ou promu)
  - Informations d’identification de la connexion à la passerelle ou de la source de données
  - Actualisation planifiée
  - [Questions proposées dans Questions et réponses](../create-reports/service-q-and-a-create-featured-questions.md)
- **Paramètres des rapports et tableaux de bord :** mettez à jour et vérifiez les paramètres de chaque rapport et tableau de bord. Voici les paramètres les plus importants :
  - Description
  - Personne ou groupe à contacter
  - [Étiquette de sensibilité](../admin/service-security-apply-data-sensitivity-labels.md)
  - [Contenu proposé](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **Abonnements :** configurez des abonnements aux rapports, si nécessaire.

> [!IMPORTANT]
> À ce stade, vous avez atteint un jalon majeur. Bravo ! Vous avez réussi la migration.

### <a name="communicate-with-users"></a>Informer les utilisateurs

Annoncez aux consommateurs qu’une nouvelle solution est disponible. Indiquez-leur où ils peuvent trouver le contenu ainsi que la documentation, les FAQ et les tutoriels associées. Pour présenter le nouveau contenu, proposez une session d’apprentissage durant le déjeuner ou préparez quelques vidéos à la demande.

Veillez à fournir des instructions expliquant comment obtenir de l’aide et envoyer des commentaires.

### <a name="conduct-a-retrospective"></a>Mener une analyse rétrospective

Essayez d’analyser rétrospectivement ce qui a bien fonctionné pendant la migration et ce qui devrait être amélioré pour la prochaine migration.

## <a name="run-in-parallel"></a>Exécuter en parallèle

Dans de nombreux cas, la nouvelle solution s’exécutera en parallèle de la solution héritée pendant une durée prédéterminée. Les avantages de l’exécution en parallèle sont les suivants :

- Réduit les risques, en particulier avec les rapports considérés comme critiques.
- Laisse aux utilisateurs le temps de se familiariser avec la nouvelle solution Power BI.
- Permet de recouper les informations présentées dans Power BI avec les rapports hérités.

## <a name="decommission-the-legacy-report"></a>Désactiver le rapport hérité

À un moment donné, les rapports migrés vers Power BI doivent être désactivés dans la plateforme décisionnelle héritée. La désactivation des rapports hérités peut avoir lieu quand :

- La durée prédéterminée de l’exécution en parallèle, qui a normalement été communiquée à l’ensemble des utilisateurs, a expiré. Elle est le plus souvent comprise entre 30 et 90 jours.
- Tous les utilisateurs du système hérité ont accès à la nouvelle solution Power BI.
- Il n’y a plus d’activité significative sur le rapport hérité.
- Aucun problème n’a été rencontré avec la nouvelle solution Power BI qui pourrait impacter la productivité des utilisateurs.

## <a name="monitor-the-solution"></a>Surveiller la solution

Les événements du [journal d’activité de Power BI](../admin/service-admin-auditing.md) peuvent servir à comprendre les modèles d’usage de la nouvelle solution (ou ceux du [journal d’exécution](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view) pour le contenu déployé sur Power BI Report Server). L’analyse du journal d’activité peut aider à déterminer si l’usage réel diffère des attentes. Elle peut également attester la bonne prise en charge de la solution.

Voici des questions auxquelles l’examen du journal d’activité permet de répondre :

- À quelle fréquence le contenu est-il consulté ?
- Qui consulte le contenu ?
- Le contenu est-il généralement consulté par le biais d’une application ou d’un espace de travail ?
- La majorité des utilisateurs se servent-ils d’un navigateur ou d’une application mobile ?
- Des abonnements sont-ils utilisés ?
- Les nouveaux rapports créés sont-ils basés sur cette solution ?
- Le contenu est-il fréquemment mis à jour ?
- Comment la sécurité est-elle définie ?
- Y a-t-il des problèmes qui surviennent régulièrement, comme des échecs d’actualisation des données ?
- Y a-t-il des activités troublantes (par exemple, une activité d’exportation importante ou un grand nombre de partages de rapports individuels) qui pourraient révéler un besoin de formation supplémentaire ?

> [!IMPORTANT]
> Veillez à ce que quelqu’un examine régulièrement le journal d’activité. Simplement capturer et stocker l’historique est utile pour les besoins d’audit ou de conformité. Toutefois, le véritable intérêt est de pouvoir mener des actions proactives.

## <a name="support-the-solution"></a>Assurer le support de la solution

Même quand la migration est terminée, la période après la migration est vitale pour résoudre les problèmes et régler les soucis de performance. Au fil du temps, la solution migrée connaîtra probablement des changements à mesure que les besoins de l’entreprise évolueront.

Le support a tendance à prendre une forme légèrement différente en fonction du mode de gestion du décisionnel libre-service au sein de l’organisation. Les champions Power BI dans les divisions assurent souvent le support de première ligne. Bien qu’il s’agisse d’un rôle informel, il est essentiel de l’encourager.

Mettre en place un processus de support formel par le service informatique, avec des tickets de support, est également indispensable pour traiter les demandes courantes liées au système et faciliter l’escalade des problèmes.

Vous pouvez également avoir un [centre d’excellence](center-of-excellence-establish.md) qui joue le même rôle que les consultants internes qui s’occupent du support, de l’apprentissage et de l’administration de Power BI au sein de l’organisation. Un centre d’excellence peut être responsable du maintien d’un contenu Power BI utile dans un portail interne.

Enfin, les consommateurs du contenu doivent savoir précisément qui contacter pour poser des questions sur le contenu et comment transmettre leurs commentaires au sujet de problèmes ou d’améliorations.

## <a name="next-steps"></a>Étapes suivantes

Dans le [dernier article de cette série](powerbi-migration-learn-from-customers.md), apprenez des expériences de clients qui ont effectué une migration vers Power BI.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).