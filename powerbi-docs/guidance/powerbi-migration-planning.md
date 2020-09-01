---
title: Planifier le déploiement pour la migration vers Power BI
description: Conseils sur la planification du déploiement pour la migration vers Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 590e28c727cab88b008d7a05e7df22244e8dabf0
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803236"
---
# <a name="plandeploymenttomigratetopowerbi"></a>Planifier le déploiement pour la migration vers Power BI

Cet article décrit l’**étape 2**, qui concerne la planification de la migration d’une solution Power BI unique.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Image illustrant les étapes d’une migration vers Power BI. Cet article se concentre sur l’étape 2.":::

> [!NOTE]
> Pour obtenir une explication complète de l’illustration ci-dessus, consultez [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md).

L’objectif de l’étape 2 est de définir la manière dont les exigences établies à l’étape 1 seront appliquées pour migrer une solution vers Power BI.

La finalité de l’étape 2 est de prendre le plus grand nombre de décisions spécifiques possible pour guider le processus de déploiement.

La prise de décision est ici un processus itératif et non linéaire. Une partie de la planification aura déjà été effectuée lors des [étapes de prémigration](powerbi-migration-pre-migration-steps.md). Les enseignements d’une preuve de concept (voir l’[étape 3](powerbi-migration-proof-of-concept.md)) peuvent être obtenus en parallèle de la planification du déploiement. Même pendant la création de la solution (décrite à l’[étape 4](powerbi-migration-create-validate-content.md)), des informations supplémentaires peuvent faire surface et influencer les décisions liées au déploiement.

> [!IMPORTANT]
> Les étapes 1 à 5 concernent des activités relatives à une solution spécifique. Certaines décisions et activités au niveau de l’organisation ou du locataire impactent le processus au niveau de la solution. Quelques-unes de ces activités de planification générale sont décrites dans l’article [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md). Quand il y a lieu, reportez-vous aux décisions prises au niveau de l’organisation pour plus d’efficacité et de cohérence.

> [!TIP]
> Les sujets abordés dans cet article s’appliquent également à tout projet d’implémentation standard de Power BI.

## <a name="choose-power-bi-product"></a>Choisir le produit Power BI

L’une des premières décisions est le choix du produit Power BI, à savoir le [service Power BI](../fundamentals/power-bi-service-overview.md) ou [Power BI Report Server](../report-server/get-started.md). Une fois que le contenu a été publié, beaucoup d’autres options deviennent disponibles, telles que l’incorporation, la livraison sur mobile et les abonnements par e-mail.

Pour plus d’informations sur les considérations architecturales, consultez la **section 3** du [livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP).

> [!CAUTION]
> Si vous êtes tenté de vous servir de fichiers Power BI Desktop stockés dans un système de fichiers, sachez qu’il ne s’agit pas d’une approche optimale. Le recours au service Power BI (ou à Power BI Report Server) présente des avantages significatifs pour la sécurité, la distribution du contenu et la collaboration. La possibilité d’auditer et de surveiller les activités est un autre avantage du service Power BI.

## <a name="decide-on-workspace-management-approach"></a>Choisir l’approche de gestion des espaces de travail

Les [espaces de travail](../collaborate-share/service-new-workspaces.md) sont un concept fondamental du service Power BI, ce qui fait de la gestion des espaces de travail un aspect important de la planification. Les questions à poser sont les suivantes :

- Faut-il prévoir un espace de travail supplémentaire pour cette nouvelle solution ?
- Des espaces de travail distincts seront-ils nécessaires pour les environnements de développement, de test et de production ?
- Des espaces de travail distincts seront-ils utilisés pour les données et les rapports, ou un seul espace de travail sera-t-il suffisant ? Les espaces de travail distincts offrent beaucoup d’avantages, en particulier pour la sécurisation des jeux de données. Quand c’est nécessaire, ils peuvent être gérés séparément des utilisateurs qui publient des rapports.
- Quelles sont les exigences de sécurité pour l’espace de travail ? Cela a une incidence sur la planification des [rôles d’espace de travail](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Quand une application est destinée à des consommateurs de contenu, les [autorisations pour l’application](../collaborate-share/service-create-distribute-apps.md#publish-your-app) sont gérées séparément de l’espace de travail. L’octroi d’autorisations distinctes aux lecteurs de l’application offre une plus grande souplesse pour respecter les exigences de sécurité applicables aux consommateurs qui utilisent en lecture seule les rapports ou tableaux de bord.
- Les groupes existants peuvent-ils être utilisés pour sécuriser le nouveau contenu ? Les groupes Azure Active Directory et Microsoft 365 sont pris en charge. Lorsqu’ils sont alignés sur des processus existants, les groupes permettent de gérer les autorisations plus facilement que les affectations à chacun des utilisateurs.
- Y a-t-il des considérations de sécurité particulières pour les utilisateurs invités externes ? Vous devrez peut-être travailler avec votre administrateur Azure Active Directory et votre administrateur Power BI pour configurer l’[accès utilisateur invité](../admin/service-admin-azure-ad-b2b.md).

> [!TIP]
> Envisagez de créer un espace de travail pour chaque projet ou activité métier spécifique. Vous pouvez être tenté de commencer à structurer les espaces de travail sur le modèle de votre organisation (par exemple, un espace de travail par division), mais cette approche finit souvent par être trop globale.

## <a name="determine-how-content-will-be-consumed"></a>Déterminer le mode de consommation du contenu

Il est utile de comprendre de quelle façon les consommateurs d’une solution préfèrent visualiser les rapports et les tableaux de bord. Les questions à poser sont les suivantes :

- Une [application Power BI](../consumer/end-user-apps.md) (qui comprend des rapports et des tableaux de bord issus d’un seul espace de travail) est-elle le meilleur moyen de livrer du contenu aux consommateurs, ou l’accès direct à un espace de travail est-il suffisant pour les lecteurs de contenu ?
- Certains rapports et tableaux de bord seront-ils incorporés ailleurs, par exemple dans [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), [SharePoint Online](../collaborate-share/service-embed-report-spo.md), ou un [portail ou site web sécurisé ](../collaborate-share/service-embed-secure.md) ?
- Les consommateurs accéderont-ils au contenu sur des [appareils mobiles](../consumer/mobile/mobile-apps-for-mobile-devices.md) ? La configuration requise pour livrer des rapports sur des petits appareils influencera certaines [décisions de conception des rapports](../create-reports/desktop-create-phone-report.md).

## <a name="decide-if-other-content-may-be-created"></a>Déterminer si la création de contenu est autorisée

Vous devez prendre plusieurs décisions importantes qui déterminent si les consommateurs sont autorisés à créer du contenu. Par exemple :

- Les consommateurs seront-ils autorisés à créer des rapports à partir du jeu de données publié ? Cette fonctionnalité peut être activée en accordant à un utilisateur l’[autorisation de génération](../connect-data/service-datasets-build-permissions.md).
- Les consommateurs pourront-ils [enregistrer une copie](../connect-data/service-datasets-copy-reports.md) d’un rapport et le personnaliser comme ils le souhaiteront ?

> [!CAUTION]
> La fonctionnalité _Enregistrer une copie_ est très utile, mais elle doit être utilisée avec précaution lorsque le rapport contient des graphismes ou des messages avec en-tête/pied de page. Étant donné que les logos, les icônes et les messages textuels sont souvent associés à des besoins de personnalisation ou de conformité réglementaire, il est important de contrôler soigneusement la manière dont ils sont livrés et distribués. Si la fonctionnalité _Enregistrer une copie_ est utilisée, mais que les graphismes ou les messages avec en-tête/pied de page d’origine ne sont pas modifiés par le nouvel auteur, cela peut entraîner une confusion sur qui a initialement créé le rapport. Cela peut également limiter l’intérêt de la personnalisation.

## <a name="evaluate-needs-for-premium-capacity"></a>Évaluer les besoins en capacité Premium

Des fonctionnalités supplémentaires sont disponibles quand un espace de travail est stocké sur une [capacité Premium](../admin/service-premium-what-is.md). Voici plusieurs raisons pour lesquelles les espaces de travail sur la capacité Premium peuvent être avantageux :

- Contenu accessible aux consommateurs sans licence Power BI Pro.
- Prise en charge des jeux de données volumineux.
- Actualisations des données plus fréquentes.
- Utilisation possible de l’ensemble complet de dataflows.
- Fonctionnalités d’entreprise, y compris les pipelines de déploiement et le point de terminaison XMLA.
- Prise en charge des rapports paginés (avec la charge de travail activée).

## <a name="determine-data-acquisition-method"></a>Déterminer la méthode d’acquisition des données

Les données requises pour un rapport peuvent influencer plusieurs décisions. Les questions à poser sont les suivantes :

- Est-il possible d’utiliser un [jeu de données Power BI partagé](../connect-data/service-datasets-share.md) existant, ou la création d’un nouveau jeu de données Power BI est-il préférable pour cette solution ?
- Un jeu de données partagé existant doit-il être enrichi avec de nouvelles données ou mesures pour répondre à d’autres besoins ?
- Quel [mode de stockage des données](../transform-model/desktop-storage-mode.md) sera le plus approprié ? Les options disponibles sont Import, DirectQuery, Composite ou Live Connection.
- Faut-il utiliser des [agrégations](../transform-model/desktop-aggregations.md) pour améliorer les performances des requêtes ?
- Créer un [dataflow](../transform-model/service-dataflows-overview.md) est-il utile et peut-il servir de source pour plusieurs jeux de données ?
- L’inscription d’une nouvelle [source de données de passerelle](../connect-data/service-gateway-data-sources.md) est-elle nécessaire ?

## <a name="decide-where-original-content-will-be-stored"></a>Déterminer l’emplacement de stockage du contenu d’origine

En plus de la planification de la destination du déploiement cible, il est également important de planifier l’emplacement de stockage du contenu d’origine (ou source) :

- Spécifiez un emplacement approuvé pour le stockage des fichiers Power BI Desktop (.pbix) d’origine. Dans l’idéal, cet emplacement doit être accessible uniquement aux personnes autorisés à modifier le contenu. L’emplacement doit être choisi dans le respect des paramètres de sécurité définis dans le service Power BI.
- Pour les fichiers Power BI Desktop d’origine, utilisez un emplacement qui inclut l’historique des versions ou le contrôle de code source. La gestion des versions permet à l’auteur du contenu de revenir à une version de fichier antérieure, si nécessaire. OneDrive Entreprise ou SharePoint sont deux solutions appropriées.
- Spécifiez un emplacement approuvé pour le stockage des données sources non centralisées, telles que les fichiers plats ou les fichiers Excel. Il doit s’agir d’un emplacement auquel les auteurs de jeux de données peuvent accéder sans problème et qui est sauvegardé régulièrement.
- Spécifiez un emplacement approuvé pour le contenu exporté à partir du service Power BI. L’objectif est de garantir que la sécurité configurée dans le service Power BI ne puisse pas être involontairement contournée.

> [!IMPORTANT]
> Il est particulièrement important de spécifier un emplacement protégé pour les fichiers Power BI Desktop d’origine qui contiennent des données importées.

## <a name="assess-the-level-of-effort"></a>Évaluer le niveau d’effort

Une fois que vous avez collecté suffisamment d’informations sur les exigences (définies à l’[étape 1](powerbi-migration-requirements.md)) et le processus de planification du déploiement de la solution, vous pouvez évaluer le niveau d’effort. Vous pourrez ensuite établir un plan de projet avec les tâches, une chronologie et les responsabilités.

> [!TIP]
> Les coûts de main-d’œuvre (salaires et primes) sont généralement l’une des dépenses les plus élevées dans la plupart des organisations. Bien que cela soit difficile à estimer avec précision, les hausses de la productivité ont un excellent retour sur investissement.

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série sur la migration vers Power BI](powerbi-migration-proof-of-concept.md), découvrez l’étape 3, qui concerne la création d’une preuve de concept pour atténuer les risques et résoudre les inconnues le plus tôt possible durant la migration vers Power BI.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
