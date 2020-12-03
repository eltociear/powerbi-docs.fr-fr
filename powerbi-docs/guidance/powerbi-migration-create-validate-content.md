---
title: Créer du contenu à migrer vers Power BI
description: Aide sur la création et la validation de contenu lors de la migration vers Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 03a55f2f414ca8af7ca86f51dcafb0258efc88b7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418598"
---
# <a name="create-content-to-migrate-to-power-bi"></a>Créer du contenu à migrer vers Power BI

Cet article décrit l’**étape 4**, qui a trait à la création et à la validation du contenu lors de la migration vers Power BI.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Image illustrant les étapes d’une migration vers Power BI. Cet article se concentre sur l’étape 4.":::

> [!NOTE]
> Pour obtenir une explication complète de l’illustration ci-dessus, consultez [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md).

L’objectif de l’étape 4 est d’effectuer le travail réel de conversion de la preuve de concept (POC) en solution prête pour la production.

Le résultat de cette étape est une solution Power BI qui a été validée dans un espace de travail de développement et qui est prête pour le déploiement en production.

> [!TIP]
> La plupart des sujets abordés dans cet article s’appliquent également à tout projet d’implémentation standard de Power BI.

## <a name="create-the-production-solution"></a>Créer la solution de production

À ce stade, la personne qui a effectué la preuve de concept peut passer à la production de la solution Power BI. Ou, il peut s’agir d’une autre personne. Si la chronologie n’est pas mise en péril, il est intéressant d’impliquer les personnes responsables du développement de Power BI à l’avenir. Ainsi, ils peuvent apprendre activement.

> [!IMPORTANT]
> Réutilisez le plus possible le travail effectué dans le cadre de la preuve de concept.

### <a name="develop-new-import-dataset"></a>Développer un nouveau jeu de données d’importation

Vous pouvez choisir de créer un nouveau jeu de données d’importation quand aucun jeu de données Power BI n’existe déjà ou s’il n’est pas possible d’en améliorer un pour répondre à vos besoins.

Dans l’idéal, commencez par découpler le travail de développement des données et des rapports. Le [découplage des données et des rapports](report-separate-from-model.md) facilitera la séparation du travail et des autorisations, quand différentes personnes sont responsables de la modélisation des données et des rapports. Il offre une approche plus évolutive et encourage la réutilisation des données.

Les activités essentielles liées au développement d’un jeu de données d’importation sont les suivantes :

- [Obtenir des données](../connect-data/desktop-quickstart-connect-to-data.md) à partir d’une ou plusieurs sources de données (par exemple, un dataflow Power BI).
- [Mettre en forme, combiner et préparer](../connect-data/desktop-shape-and-combine-data.md) des données.
- Créer le [modèle de jeu de données](../transform-model/desktop-modeling-view.md), y compris des [tables de dates](../transform-model/desktop-date-tables.md).
- Créer et vérifier les [relations de modèles](../transform-model/desktop-create-and-manage-relationships.md).
- Définir des [mesures](../transform-model/desktop-measures.md).
- Configurer la [sécurité au niveau des lignes](../admin/service-admin-rls.md), si nécessaire.
- Configurer des synonymes et [optimiser les questions/réponses](../natural-language/q-and-a-best-practices.md).
- Planifier la scalabilité, les performances et la concurrence, susceptibles d’influencer vos décisions sur les modes de stockage des données, notamment l’utilisation d’un [modèle composite](../transform-model/desktop-composite-models.md) ou d’[agrégations](../transform-model/desktop-aggregations.md).

> [!TIP]
> Si vous avez des environnements de développement/test/production différents, envisagez de [paramétrer](/power-query/power-query-query-parameters) des sources de données. Elles faciliteront considérablement le déploiement décrit à l’[étape 5](powerbi-migration-deploy-support-monitor.md).

### <a name="develop-new-reports-and-dashboards"></a>Développer de nouveaux rapports et tableaux de bord

Les activités essentielles liées au développement d’un rapport ou d’un tableau de bord Power BI sont les suivantes :

- Décidez d’utiliser une connexion active à un modèle de données existant ou de créer un modèle de données.
- Quand vous créez un modèle de données, choisissez le [mode de stockage des données](../transform-model/desktop-storage-mode.md) pour les tables de modèles (importation, DirectQuery ou composite).
- Choisissez l’outil de visualisation des données le mieux adapté à vos besoins : Power BI Desktop, Paginated Report Builder ou Excel.
- Déterminez les [meilleurs visuels](../consumer/end-user-visual-type.md) pour accompagner le rapport et répondre aux questions auxquelles le rapport doit répondre.
- Veillez à ce que tous les visuels présentent une terminologie claire, concise et conviviale.
- Répondez aux besoins d’interactivité.
- Quand vous utilisez une connexion active, ajoutez des [mesures au niveau du rapport](../transform-model/desktop-tutorial-create-measures.md).
- Créez un [tableau de bord](../create-reports/service-dashboards.md) dans le service Power BI, surtout quand les consommateurs veulent un moyen simple de superviser des métriques clés.

> [!NOTE]
> La plupart de ces décisions auront été prises pendant les étapes précédentes de planification ou pendant la preuve de concept technique.

## <a name="validate-the-solution"></a>Valider la solution

La validation d’une solution Power BI présente quatre aspects principaux :

1. Précision des données
2. Sécurité
3. Fonctionnalité
4. Performances

### <a name="validate-data-accuracy"></a>Valider la précision des données

À une seule reprise pendant la migration, vous devez vérifier que les données incluses dans le nouveau rapport correspondent à ce qui s’affiche dans l’ancien. Ou, en cas de différence constatée, être capable d’expliquer pourquoi. Plus souvent, vous penserez trouver une erreur dans l’ancienne solution qui sera corrigée dans la nouvelle.

Dans le cadre de vos efforts de validation des données, le nouveau rapport doit généralement être revérifié dans le système source d’origine. Dans l’idéal, cette validation est renouvelée chaque fois que vous publiez une modification dans un rapport.

### <a name="validate-security"></a>Valider la sécurité

Lors de la validation de la sécurité, il existe deux aspects principaux à prendre en compte :

- Autorisations des données
- Accès aux jeux de données, rapports et tableaux de bord

Dans un jeu de données d’importation, les autorisations des données sont appliquées en définissant la [sécurité au niveau des lignes](../admin/service-admin-rls.md). Il est également possible que les autorisations des données soient appliquées par le système source lors de l’utilisation du mode de stockage DirectQuery (éventuellement avec une [authentification unique](../connect-data/service-gateway-sso-overview.md)).

Les principales façons d’accorder l’accès au contenu Power BI sont les suivantes :

- [Rôles d’espace de travail](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (pour les éditeurs et viewers de contenu).
- [Autorisations d’application](../collaborate-share/service-create-distribute-apps.md#publish-your-app) appliquées à un package de contenu d’espace de travail (pour les viewers).
- [Partage](../collaborate-share/service-share-dashboards.md) d’un rapport ou tableau de bord individuel (pour les viewers).

> [!TIP]
> Nous vous recommandons de former les auteurs de contenu sur la manière de gérer efficacement la sécurité. Il est également important de disposer de tests, d’audits et d’une supervision fiables.

### <a name="validate-functionality"></a>Valider les fonctionnalités

C’est le moment de revérifier les détails de jeu de données, comme les noms de champs, la mise en forme, le tri et le comportement de synthèse par défaut. Les fonctionnalités de rapport interactives, comme les [segments](../visuals/power-bi-visualization-slicers.md), [le fait de descendre dans la hiérarchie](../consumer/end-user-drill.md), l’[extraction](../create-reports/desktop-drillthrough.md), les [expressions](../create-reports/desktop-conditional-format-visual-titles.md), les [boutons](../create-reports/desktop-buttons.md) ou les [signets](../create-reports/desktop-bookmarks.md) doivent également toutes être vérifiées.

Pendant le processus de développement, la solution Power BI doit être publiée régulièrement sur un espace de travail de développement dans le service Power BI. Vérifiez que toutes les fonctionnalités se comportent comme prévu dans le service, notamment quand il s’agit d’effectuer le rendu de visuels personnalisés. C’est également un bon moment pour effectuer d’autres tests. Testez l’[actualisation planifiée](../connect-data/refresh-scheduled-refresh.md), les [questions et réponses](../consumer/end-user-q-and-a.md), ainsi que la manière dont les rapports et tableaux de bord apparaissent sur un [appareil mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md).

### <a name="validate-performance"></a>Valider les performances

Les performances de la solution Power BI sont importantes pour l’expérience des consommateurs. La plupart des rapports doivent présenter des visuels en moins de 10 secondes. Si vous avez des rapports dont le chargement prend plus de temps, interrompez-vous et cherchez ce qui peut contribuer à ces délais. Vous devez évaluer régulièrement les performances des rapports dans le service Power BI, en plus de Power BI Desktop.

De nombreux problèmes de performances sont dus à des syntaxes [DAX (Data Analysis Expressions)](../transform-model/desktop-quickstart-learn-dax-basics.md) qui ne respectent pas les normes, à une conception médiocre du jeu de données ou à une conception de rapport qui n’est pas optimale (par exemple, une tentative d’affichage d’un trop grand nombre de visuels sur une seule page). Des problèmes liés à l’environnement technique, comme le réseau, une passerelle de données surchargée ou la configuration d’une capacité Premium, peuvent également générer des problèmes de performances. Pour plus d’informations, consultez le [Guide d’optimisation pour Power BI](power-bi-optimization.md) et [Résoudre les problèmes de performances de rapports dans Power BI](report-performance-troubleshoot.md).

## <a name="document-the-solution"></a>Documenter la solution

Il existe deux principaux types de documentation utiles pour une solution Power BI :

- Documentation du jeu de données
- Documentation du rapport

La documentation peut être stockée partout où elle est facilement accessible par le public cible. Les options courantes sont les suivantes :

- **Sur un site SharePoint :** Un site SharePoint peut exister pour votre centre d’excellence ou un site de communauté Power BI interne.
- **Dans une application :** Des URL peuvent être configurées lors de la publication d’une application Power BI pour diriger le consommateur vers plus d’informations.
- **Au sein de fichiers Power BI Desktop individuels :** Des éléments de modèle, comme des tables et colonnes, peuvent définir une description. Ces descriptions s’affichent sous forme d’info-bulles dans le volet **Champs** lors de la création de rapports.

> [!TIP]
> Si vous créez un site qui sert de hub pour la documentation relative à Power BI, envisagez de [personnaliser le menu Aide](../admin/service-admin-portal.md#publish-get-help-information) avec son emplacement d’URL.

### <a name="create-dataset-documentation"></a>Créer la documentation du jeu de données

La documentation du jeu de données est destinée aux utilisateurs qui vont gérer le jeu de données à l’avenir. Il est utile d’y inclure ce qui suit :

- Décisions de conception prises et pourquoi.
- Qui possède, gère et certifie les jeux de données.
- Besoins d’actualisation des données.
- Règles métier personnalisées définies dans les jeux de données.
- Exigences spécifiques en matière de sécurité et de confidentialité des données du jeu de données.
- Futurs besoins de maintenance.
- Problèmes ouverts connus ou éléments de backlog reportés.

Vous pouvez également choisir de créer un journal des modifications qui résume les modifications les plus importantes qui se sont produites dans le jeu de données au fil du temps.

### <a name="create-report-documentation"></a>Créer la documentation du rapport

La documentation du rapport, généralement structurée sous forme de procédure pas à pas destinée aux consommateurs du rapport, peut aider les utilisateurs à tirer davantage parti de vos rapports et tableaux de bord. Un petit tutoriel vidéo fonctionne souvent bien.

Vous pouvez également choisir d’ajouter une documentation sur une page masquée de votre rapport. Celle-ci peut inclure les décisions de conception et un journal des modifications.

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série sur la migration vers Power BI](powerbi-migration-deploy-support-monitor.md), découvrez l’étape 5, qui concerne le déploiement, l’assistance et la supervision du contenu.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).
