---
title: Collecter les exigences pour la migration vers Power BI
description: Conseils sur la collecte et la hiérarchisation des exigences pour la migration vers Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 2aee1be1d5e221f8feaeae05f8284f0388b4b8af
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418552"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>Collecter les exigences pour la migration vers Power BI

Cet article décrit l’**étape 1**, qui concerne la collecte et la hiérarchisation des exigences pour la migration vers Power BI.

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="Image illustrant les étapes d’une migration vers Power BI. Cet article se concentre sur l’étape 1.":::

> [!NOTE]
> Pour obtenir une explication complète de l’illustration ci-dessus, consultez [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md).

L’étape 1 est principalement consacrée à la collecte d’informations et à la planification de la migration d’une solution individuelle vers Power BI.

La finalité de l’étape 1 est notamment de connaître toutes les exigences de façon précise et hiérarchisée. Toutefois, des activités supplémentaires aux étapes 2 et 3 doivent être effectuées pour aboutir à une estimation complète du niveau d’effort.

> [!IMPORTANT]
> Les étapes 1 à 5 concernent des activités relatives à une solution spécifique. Certaines décisions et activités au niveau de l’organisation ou du locataire impactent le processus au niveau de la solution. Quelques-unes de ces activités de planification générale sont décrites dans l’article [Vue d’ensemble de la migration vers Power BI](powerbi-migration-overview.md). Quand il y a lieu, reportez-vous aux décisions prises au niveau de l’organisation pour plus d’efficacité et de cohérence.

> [!TIP]
> La plupart des sujets abordés dans cet article s’appliquent également à tout projet d’implémentation standard de Power BI.

## <a name="compile-requirements"></a>Établir une liste des exigences

L’inventaire des artefacts BI existants, répertoriés lors des [étapes de prémigration](powerbi-migration-pre-migration-steps.md), constitue le point de départ pour définir les exigences de la nouvelle solution à créer dans Power BI. La collecte des exigences vise à comprendre l’état actuel, mais aussi à savoir quels éléments les utilisateurs voudraient voir modifiés ou refactorisés lors du remaniement des rapports dans Power BI. Connaître les exigences en détail est utile pendant la planification du déploiement de la solution à l’[étape 2](powerbi-migration-planning.md), la création d’une preuve de concept à l’[étape 3](powerbi-migration-proof-of-concept.md) et la création de la solution prête pour la production à l’[étape 4](powerbi-migration-create-validate-content.md).

### <a name="gather-report-requirements"></a>Collecter les exigences relatives aux rapports

Rassemblez des informations complètes et faciles à renseigner sur les rapports, telles que celles-ci :

- **Objectif, audience et action attendue :** identifiez le but et le processus métier pour chaque rapport, ainsi que l’audience, le workflow analytique et l’action attendue de la part des consommateurs du rapport.
- **Mode d’utilisation du rapport par les consommateurs :** passez du temps auprès des consommateurs du rapport existant pour comprendre les usages qu’ils en font. Cela vous permet de voir si certains éléments du rapport pourraient être éliminés ou améliorés dans la nouvelle version de Power BI. Ce processus prend plus de temps, mais cet investissement vaut le coup pour les rapports critiques ou les rapports fréquemment utilisés.
- **Propriétaire et expert technique :** identifiez le propriétaire du rapport et tous les experts techniques en lien avec le domaine du rapport ou des données. Ces experts sont susceptibles de devenir ultérieurement les propriétaires des nouveaux rapports Power BI. Prenez en compte les exigences propres à la gestion des changements (qui diffèrent généralement entre les solutions gérées par le service informatique et celles gérées par l’entreprise), ainsi que les approbations et les validations, qui seront nécessaires pour apporter des modifications plus tard.
- **Méthode de livraison du contenu :** clarifiez les attentes des consommateurs du rapport en ce qui concerne la livraison du contenu. Il peut s’agir d’une exécution interactive, à la demande, incorporée dans une application personnalisée, ou d’une livraison planifiée avec un abonnement par e-mail. Il peut également y avoir des exigences pour le déclenchement des notifications d’alerte.
- **Besoins d’interactivité :** déterminez les exigences d’interactivité _impératives_ et _souhaitables_, comme les filtres, l’exploration ou l’extraction.
- **Sources de données :** assurez-vous que toutes les sources de données requises par le rapport sont connues et que les besoins en matière de latence des données (actualisation des données) sont évalués. Identifiez les exigences relatives aux données historiques, aux tendances et aux instantanés de données pour chaque rapport afin qu’elles soient alignées sur les exigences propres aux données. La documentation des sources de données peut également s’avérer utile plus tard, au moment de la validation des données d’un nouveau rapport avec ses données sources.
- **Exigences de sécurité :** clarifiez les exigences de sécurité (par exemple, les liseurs autorisés, les éditeurs autorisés et les besoins de sécurité au niveau des lignes), y compris les exceptions à la sécurité habituelle de l’organisation. Documentez les exigences relatives au niveau de sensibilité des données, à la confidentialité des données ou à la réglementation/conformité.
- **Calculs, indicateurs de performance clés et règles métier :** identifiez et documentez l’ensemble des calculs, des indicateurs de performance clés et des règles métier actuellement définis dans le rapport existant afin qu’ils soient alignés sur les exigences propres aux données.
- **Exigences en matière de convivialité, de disposition et d’apparence :** identifiez les exigences de convivialité, de disposition et d’apparence en lien avec les exigences de visualisation, de regroupement et de tri des données, et la visibilité conditionnelle. Incluez les considérations particulières pour la livraison sur les appareils mobiles.
- **Exigences relatives à l’impression et l’exportation :** déterminez s’il existe des exigences spécifiques pour l’impression, l’exportation ou le rendu parfait des pixels. Ces exigences conditionnent le type de rapport qui sera le plus approprié (par exemple, un rapport Power BI, Excel ou paginé). N’oubliez pas que les consommateurs de rapports ont tendance à attacher beaucoup d’importance à leurs habitudes de travail. N’ayez donc pas peur de remettre en question leurs modes de pensée. Parlez-leur d’_améliorations_ plutôt que de _changements_.
- **Risques ou préoccupations :** déterminez s’il existe d’autres exigences techniques ou opérationnelles pour les rapports, ou des risques ou des préoccupations quant aux informations présentées dans les rapports.
- **Problèmes ouverts et éléments du backlog :** identifiez les opérations de maintenance futures, les problèmes connus ou les demandes différées à ajouter au backlog à ce stade.

> [!TIP]
> Essayez de hiérarchiser les exigences en les classifiant comme _impératives_ ou _souhaitables_. Souvent, les consommateurs demandent tout ce dont ils pourraient avoir besoin un jour, car ils craignent de ne pas avoir d’autre occasion de le faire par la suite. De plus, quand vous définissez les priorités sur plusieurs itérations, mettez le backlog à la disposition des parties prenantes. Cela facilite la communication, la prise de décision et le suivi des engagements en attente.

### <a name="gather-data-requirements"></a>Collecter les exigences relatives aux données

Rassemblez des informations détaillées sur les données, comme celles-ci :

- **Requêtes existantes :** déterminez s’il existe des requêtes de rapport ou des procédures stockées qui peuvent être utilisées par un [modèle DirectQuery](../connect-data/desktop-use-directquery.md) ou un [modèle Composite](../transform-model/desktop-composite-models.md), ou bien être converties en un modèle Import.
- **Types de sources de données :** listez les types de sources de données requises, y compris les sources de données centralisées (par exemple, un entrepôt de données d’entreprise) et les sources de données non standard (comme les fichiers plats ou les fichiers Excel utilisés en complément des sources de données d’entreprise à des fins de création de rapports). Il est également important de localiser les sources de données pour assurer la connectivité de la [passerelle de données](../connect-data/service-gateway-onprem.md).
- **Exigences en matière de structure et de nettoyage des données :** déterminez la structure de données pour chaque source de données requise et dans quelle mesure les activités de [nettoyage des données](../transform-model/desktop-query-overview.md) sont nécessaires.
- **Intégration des données** : déterminez comment gérer l’intégration des données en présence de sources de données multiples, et comment établir des [relations](../transform-model/desktop-create-and-manage-relationships.md) entre chaque table de modèle. Identifiez les éléments de données particuliers nécessaires pour simplifier le modèle et [réduire sa taille](import-modeling-data-reduction.md).
- **Latence de données acceptable :** déterminez la latence de données requise pour chaque source de données. Cela conditionne les décisions concernant le [mode de stockage des données](../transform-model/desktop-storage-mode.md) à utiliser. La fréquence d’actualisation des données dans les tables du modèle Import est importante à connaître aussi.
- **Volume de données et scalabilité :** évaluez le volume de données attendu, car cela impacte les décisions relatives à la [prise en charge de modèle de grande taille](../admin/service-premium-large-models.md) et à la conception de [modèles Composite](../transform-model/desktop-composite-models.md) ou DirectQuery. Les besoins en données historiques sont tout autant essentiels à connaître. Pour les jeux de données plus volumineux, il est également nécessaire de déterminer les règles d’[actualisation incrémentielle des données](../admin/service-premium-incremental-refresh.md).
- **Mesures, indicateurs de performance clés et règles métier :** évaluez les besoins en ce qui concerne les mesures, les indicateurs de performance clés et les règles métier. Ils auront un impact sur les décisions concernant l’emplacement d’application de la logique : dans le jeu de données ou dans le processus d’intégration des données.
- **Données de référence et catalogue de données :** prenez en compte les problèmes potentiels avec les données de référence qui nécessitent une attention particulière. Déterminez si l’intégration à un catalogue de données métier est pertinente pour améliorer la détectabilité, accéder aux définitions ou produire une terminologie cohérente acceptée par l’organisation.
- **Sécurité et confidentialité des données :** déterminez s’il existe des considérations spécifiques en matière de sécurité ou de confidentialité des données pour les jeux de données, y compris des exigences de [sécurité au niveau des lignes](../admin/service-admin-rls.md).
- **Problèmes ouverts et éléments du backlog :** identifiez les problèmes connus, les défauts de qualité des données, les opérations de maintenance futures ou les demandes différées à ajouter au backlog à ce stade.

> [!IMPORTANT]
> La réutilisation des données est possible avec des [jeux de données partagés](../connect-data/service-datasets-share.md), qui peuvent éventuellement être [certifiés](../collaborate-share/service-endorse-content.md) pour indiquer la fiabilité et améliorer la détectabilité. Réutiliser les informations de préparation des données peut se faire avec des [dataflows](../transform-model/dataflows/dataflows-introduction-self-service.md) pour réduire la logique répétitive entre des jeux de données multiples. Les dataflows permettent aussi de diminuer considérablement la charge sur les systèmes sources du fait que les données sont récupérées moins souvent ; plusieurs jeux de données peuvent donc importer des données à partir du même dataflow.

## <a name="identify-improvement-opportunities"></a>Identifier les opportunités d’amélioration

La plupart du temps, la migration donne lieu à des modifications et à des améliorations. Il est rare qu’une migration directe un-à-un soit réalisée sans refactorisation ni optimisation. Voici trois axes d’améliorations possibles :

- **Regroupement de rapports :** des rapports similaires peuvent être regroupés à l’aide de techniques comme les filtres, les signets ou la personnalisation. Le fait d’avoir moins de rapports, qui sont individuellement plus flexibles, peut améliorer nettement l’expérience des consommateurs de rapports. Essayez d’optimiser les jeux de données pour les [Questions et réponses (requêtes en langage naturel)](../natural-language/q-and-a-best-practices.md) afin d’offrir une flexibilité encore plus grande aux consommateurs des rapports, en leur permettant de créer leurs propres visualisations.
- **Améliorations pour plus d’efficacité :** durant la phase de collecte des exigences, des améliorations possibles sont souvent identifiées. C’est le cas, par exemple, quand des analystes compilent des chiffres manuellement ou qu’un workflow peut être simplifié. [Power Query](../transform-model/desktop-query-overview.md) peut jouer un rôle important dans le remplacement des activités manuelles qui sont actuellement effectuées. Si les analystes de l’entreprise sont régulièrement amenés à effectuer les mêmes activités pour nettoyer et préparer des données, les étapes de préparation des données Power Query reproductibles peuvent faire gagner beaucoup de temps et réduire les risques d’erreurs.
- **Centralisation du modèle de données :** un jeu de données certifié et faisant autorité sert de référence pour le décisionnel libre-service géré. Dans ce cas, les données sont gérées une fois, puis les analystes ont la possibilité d’utiliser et d’enrichir ces données en fonction de leurs besoins d’analyse et de création de rapports.

> [!NOTE]
> Pour plus d’informations sur la centralisation des modèles de données, consultez [Discipline au niveau de la base](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) et [Flexibilité en périphérie](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="prioritize-and-assess-complexity"></a>Hiérarchiser et évaluer la complexité

À ce stade, l’inventaire initial est terminé et inclut potentiellement des exigences spécifiques. Lors de la hiérarchisation de l’ensemble initial d’artefacts BI prêts pour la migration, les rapports et les données doivent être examinés collectivement, mais aussi indépendamment les uns des autres.

Identifiez les rapports de haute priorité, notamment les rapports qui :

- Apportent une grande valeur ajoutée à l’entreprise.
- Sont générés fréquemment.
- Sont demandés par la direction ou l’exécutif.
- Présentent un niveau de complexité raisonnable (pour améliorer les chances de succès lors des itérations de migration initiales).

Identifiez les données de haute priorité, en particulier celles qui :

- Comportent des éléments de données critiques.
- Sont des données organisationnelles communes servant à de nombreux cas d’usage.
- Peuvent être utilisées pour créer un jeu de données partagé, réutilisable dans les rapports et par de multiples auteurs de rapports.
- Présentent un niveau de complexité raisonnable (pour améliorer les chances de succès lors des itérations de migration initiales).

## <a name="next-steps"></a>Étapes suivantes

Dans l’[article suivant de cette série sur la migration vers Power BI](powerbi-migration-planning.md), découvrez l’étape 2, qui concerne la planification de la migration pour une solution Power BI unique.

Voici d’autres ressources utiles :

- [Transformation BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Livre blanc sur la planification d’un déploiement de Power BI en entreprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)

Les partenaires Power BI expérimentés sont là pour aider votre organisation à mener à bien le processus de migration. Pour contacter un partenaire Power BI, accédez au [portail des partenaires Power BI](https://powerbi.microsoft.com/partners/).