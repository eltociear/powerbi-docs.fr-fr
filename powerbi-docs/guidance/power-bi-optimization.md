---
title: Guide d’optimisation pour Power BI
description: Guide d’optimisation pour Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: d718c9c7f627d735c083a46c1483815e3744faca
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378866"
---
# <a name="optimization-guide-for-power-bi"></a>Guide d’optimisation pour Power BI

Cet article fournit des conseils qui permettent aux développeurs et aux administrateurs de créer et de gérer des solutions Power BI optimisées. Vous pouvez optimiser votre solution sur différentes couches architecturales. Les couches sont les suivantes :

- la ou les sources de données
- le modèle de données
- des visualisations, y compris des tableaux de bord, rapports Power BI et rapports paginés Power BI
- l’environnement, y compris les capacités, les passerelles de données et le réseau

## <a name="optimizing-the-data-model"></a>Optimisation du modèle de données

Le modèle de données prend en charge l’intégralité de l’expérience de visualisation. Les modèles de données sont hébergés de manière externe ou internes et dans Power BI ils sont appelés _jeux de données_. Il est important de comprendre vos options et de choisir le type de jeu de données approprié pour votre solution. Les trois modes de jeux de données sont les suivants : Import, DirectQuery et Composite. Pour plus d’informations, consultez [Jeux de données dans le service Power BI](../service-datasets-understand.md) et [Modes de jeux de données dans le service Power BI](../service-dataset-modes-understand.md).

Pour obtenir des instructions spécifiques sur les modes de jeux de données, consultez :

- [Techniques de réduction des données pour la modélisation des importations](import-modeling-data-reduction.md)
- [Aide sur le modèle DirectQuery dans Power BI Desktop](directquery-model-guidance.md)
- [Conseils sur les modèles composites dans Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Optimisation des visualisations

Les visualisations Power BI peuvent être des tableaux de bord, des rapports Power BI ou des rapports paginés Power BI. Chacun d’eux a des architectures différentes et, par conséquent, chacun possède ses propres conseils. 

### <a name="dashboards"></a>Tableaux de bord

Il est important de comprendre que Power BI conserve un cache pour vos mosaïques de tableaux de bord, à l’exception des mosaïques de rapport actif et des mosaïques de diffusion en continu. Pour plus d’informations, consultez [Actualisation des données dans Power BI (actualisation de la mosaïque)](../refresh-data.md#tile-refresh). Si votre jeu de données applique la [sécurité au niveau des lignes](../service-admin-rls.md) dynamique, veillez à comprendre les implications en matière de performances, car les mosaïques seront mises en cache par utilisateur.

Lorsque vous épinglez des mosaïques de rapports actifs à un tableau de bord, elles ne sont pas traitées à partir du cache de requête. Au lieu de cela, elles se comportent comme des rapports et effectuent des requêtes sur des cœurs dorsaux à la volée.

Comme son nom l’indique, la récupération des données à partir du cache offre des performances supérieures et plus cohérentes que par la source de données. Pour tirer parti de cette fonctionnalité, vous pouvez notamment définir les tableaux de bord comme page d’accueil pour vos utilisateurs. Épinglez les éléments visuels les plus utilisés et demandés aux tableaux de bord. Les tableaux de bord deviennent ainsi une « première ligne de défense » utile qui fournit des performances cohérentes et une charge moindre sur la capacité. Les utilisateurs peuvent encore cliquer pour accéder au rapport afin d’analyser les détails.

Pour les jeux de données de connexions actives et DirectQuery, le cache est mis à jour régulièrement en interrogeant la source de données. Par défaut, cela se produit toutes les heures, même si vous pouvez configurer une fréquence différente dans les paramètres du jeu de données. Chaque mise à jour du cache envoie des requêtes à la source de données sous-jacente pour mettre à jour le cache. Le nombre de requêtes générées dépend du nombre de visuels épinglés aux tableaux de bord qui dépendent de cette source de données. Notez que si la sécurité au niveau des lignes est activée, les requêtes sont générées pour chaque contexte de sécurité différent. Par exemple, considérez qu’il existe deux rôles différents qui catégorisent vos utilisateurs et qu’ils ont deux vues différentes des données. Au cours de l’actualisation du cache des requêtes, Power BI génère deux ensembles de requêtes.

### <a name="power-bi-reports"></a>Rapports Power BI

Il existe plusieurs suggestions pour l’optimisation des conceptions de rapport Power BI.

> [!NOTE]
> Lorsque les rapports sont basés sur un jeu de données DirectQuery, pour obtenir des optimisations de conception de rapport supplémentaires, consultez [Conseils de modèle DirectQuery dans Power BI Desktop (optimiser les conceptions de rapport)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Appliquer les filtres les plus restrictifs

Plus un élément visuel contient de données à afficher, plus son chargement est lent. Si ce principe semble évident, on a tendance à l’oublier. Par exemple, supposons que vous avez un jeu de données volumineux, À partir de ce jeu de données, vous créez un rapport avec une table. Les utilisateurs finaux utilisent les tranches sur la page pour accéder aux lignes qui les intéressent, généralement pas plus de quelques dizaines.

Une erreur fréquente consiste à utiliser la vue par défaut de la table non filtrée, soit la totalité des quelques 100 millions de lignes. Les données de ces lignes sont chargées en mémoire et décompressées à chaque actualisation. Ce traitement impose des charges énormes à la mémoire. La solution consiste à utiliser le filtre « N premiers » pour réduire le nombre maximal d’éléments à afficher dans la table. Vous pouvez définir un nombre maximal d’éléments supérieur à ce dont les utilisateurs peuvent avoir besoin, par exemple 10 000. Le résultat est que l’expérience de l’utilisateur final ne change pas, mais que l’utilisation de la mémoire chute considérablement. Et surtout, les performances sont améliorées.

Une approche de conception similaire à celle-ci est recommandée pour tous les éléments visuels de votre rapport. Demandez-vous si toutes les données présentes dans l’élément visuel sont nécessaires. Est-il possible de réduire la quantité de données affichées sur le visuel d’une manière ou d’une autre sans gêner l’utilisateur ? Souvenez-vous que les tables peuvent être coûteuses.

#### <a name="limit-visuals-on-report-pages"></a>Limiter le nombre d’éléments visuels sur les pages de rapport

Le principe ci-dessus s’applique également au nombre d’éléments visuels ajoutés à une page de rapport. Il est fortement recommandé de limiter le nombre d’éléments visuels sur une page de rapport au strict nécessaire. Les [pages d’extraction](report-drillthrough.md) et les [info-bulles des pages de rapport](report-page-tooltips.md) permettent d’ajouter des détails supplémentaires sans accumuler les éléments visuels sur la page.

#### <a name="evaluate-custom-visual-performance"></a>Évaluer les performances des éléments visuels personnalisés

Pour garantir des performances élevées, veillez à mettre à l’épreuve chaque élément visuel personnalisé. Les visuels Power BI mal optimisés peuvent réduire les performances de l’intégralité du rapport.

### <a name="power-bi-paginated-reports"></a>Rapports paginés Power BI

Les conceptions des rapports paginés Power BI peuvent être optimisées en appliquant la conception des meilleures pratiques à l’extraction des données du rapport. Pour plus d’informations, consultez les [conseils sur l’extraction de données pour les rapports paginés](report-paginated-data-retrieval.md).

En outre, assurez-vous que votre capacité dispose de suffisamment de mémoire allouée à la [charge de travail des rapports paginés](../service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Optimisation de l’environnement

Vous pouvez optimiser l’environnement Power BI en configurant les paramètres de capacité, en redimensionnant les passerelles de données et en réduisant la latence du réseau.

### <a name="capacity-settings"></a>Paramètres de capacité

Lorsque vous utilisez des capacités dédiées, disponibles avec Power BI Premium (niveaux tarifaires P) ou Power BI Embedded (niveaux tarifaires A, A4-A6), vous pouvez gérer les paramètres de capacité. Pour plus d’informations, consultez [Gestion des capacités Premium](../service-premium-capacity-manage.md). Pour obtenir des conseils sur la façon d’optimiser votre capacité, consultez [Optimisation des capacités Premium](../service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Dimensionnement de la passerelle

La passerelle est obligatoire chaque fois que Power BI doit accéder à des données qui ne sont pas directement accessibles sur Internet. Vous pouvez installer la [passerelle de données locale](../service-gateway-onprem.md) sur un serveur local ou sur une infrastructure IaaS (infrastructure as a service) hébergée sur une machine virtuelle.

Pour comprendre les charges de travail et les suggestions de dimensionnement de la passerelle, consultez [Dimensionnement des passerelles de données locales](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Latence du réseau

La latence du réseau peut affecter les performances du rapport en augmentant le temps nécessaire aux demandes pour atteindre le service Power BI et aux réponses pour être envoyées. Les abonnés de Power BI sont affectés à une région spécifique.

> [!TIP]
> Pour déterminer où se trouve votre abonné, consultez [Où est situé mon abonné Power BI ?](../service-admin-where-is-my-tenant-located.md)

Lorsque les utilisateurs d’un client accèdent au service Power BI, leurs requêtes sont acheminées vers cette région. Lorsque les requêtes atteignent le service Power BI, celui-ci peut ensuite envoyer des requêtes supplémentaires (par exemple, à la source de données sous-jacente ou à la passerelle) qui sont également soumises à la latence du réseau.

Des outils tels que [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) donnent une indication de la latence du réseau entre le client et la région Azure. De manière générale, pour minimiser l’impact de la latence du réseau, essayez de rapprocher le plus possible les sources de données, les passerelles et votre cluster Power BI. De préférence, elles se trouvent dans la même région. Si la latence du réseau pose problème, essayez de rapprocher les passerelles et les sources de données de votre cluster Power BI en les plaçant sur des machines virtuelles hébergées sur le cloud.

## <a name="monitoring-performance"></a>Analyse des performances

Vous pouvez surveiller les performances afin d’identifier les goulots d’étranglement. Les éléments visuels de requêtes ou de rapports lents doivent être au cœur de l’optimisation continue. La surveillance peut être effectuée au moment de la conception dans Power BI Desktop ou sur des charges de travail de production dans des capacités de Power BI Premium. Pour plus d’informations, consultez [Surveillance des performances de rapports dans Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Conseils sur Power BI](index.yml)
- [Surveillance des performances des rapports](monitor-report-performance.md)
- Livre blanc : [Planification d’un déploiement de Power BI en entreprise](https://go.microsoft.com/fwlink/?linkid=2057861)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
