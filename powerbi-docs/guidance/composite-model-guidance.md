---
title: Aide sur les modèles composites dans Power BI Desktop
description: Aide au développement de modèles composites.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/24/2019
ms.openlocfilehash: 53c0af04a76d4cf8cfacd49002434ecbc246fbe8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394379"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Aide sur les modèles composites dans Power BI Desktop

Cet article s’adresse aux modélisateurs de données qui développent des modèles composites Power BI Desktop. Il décrit les cas d’utilisation des modèles composites et donne des conseils de conception. Plus précisément, il vous permet de déterminer si un modèle composite est adapté à votre solution. Il vous aidera également, si c’est le cas, à concevoir un modèle optimal.

> [!NOTE]
> Cet article n’est pas une introduction aux modèles composites. Si vous ne connaissez pas les modèles composites, nous vous recommandons de lire d’abord l’article [Utiliser des modèles composites dans Power BI Desktop](../transform-model/desktop-composite-models.md).
>
> Étant donné que les modèles composites se composent d’au moins une source DirectQuery, il est également important de bien comprendre les [relations entre les modèles](../transform-model/desktop-relationships-understand.md), les [modèles DirectQuery](../connect-data/desktop-directquery-about.md) et [l’aide à la conception de modèles DirectQuery](directquery-model-guidance.md).

## <a name="composite-model-use-cases"></a>Cas d’utilisation des modèles composites

Dans la mesure du possible, il est préférable de développer un modèle en mode d’importation. Ce mode offre une plus grande flexibilité de conception et des performances optimales.

Toutefois, les modèles d’importation ne peuvent pas résoudre les problèmes liés aux gros volumes de données ou aux rapports basés sur des données en quasi temps réel. Dans ces deux cas, vous pouvez envisager un modèle DirectQuery, à condition que vos données soient stockées dans une source de données unique [prise en charge par le mode DirectQuery](../connect-data/power-bi-data-sources.md).

Vous pouvez également développer un modèle composite dans les situations suivantes.

- Votre modèle pourrait être un modèle DirectQuery, mais vous souhaitez améliorer les performances. Dans un modèle composite, il est possible d’améliorer les performances en configurant un stockage adapté à chaque table. Vous pouvez également ajouter des [agrégations](../transform-model/desktop-aggregations.md). Ces deux optimisations sont abordées plus loin dans cet article.
- Vous souhaitez combiner un modèle DirectQuery avec des données supplémentaires, qui doivent être importées dans le modèle. Les données importées peuvent être chargées à partir d’une autre source de données, ou à partir de tables calculées.
- Vous souhaitez combiner plusieurs sources de données DirectQuery dans un modèle unique.

> [!NOTE]
> Les modèles composites ne peuvent pas combiner des sources Connexion active (par exemple, les [modèles hébergés en externe](../connect-data/service-datasets-understand.md#external-hosted-models) et les jeux de données de Power BI) ou des sources de bases de données analytiques DirectQuery (par exemple, SAP Business Warehouse et SAP HANA).

## <a name="optimize-model-design"></a>Optimiser la conception du modèle

Il est possible d’optimiser un modèle composite en configurant les [modes de stockage](../transform-model/desktop-storage-mode.md) table, et en ajoutant des [agrégations](../transform-model/desktop-aggregations.md).

### <a name="table-storage-mode"></a>Mode Stockage Table

Dans un modèle composite, vous pouvez configurer le mode de stockage pour chaque table (à l’exception des tables calculées) :

- **DirectQuery** : nous vous recommandons de définir ce mode pour les tables qui représentent de gros volumes de données ou qui doivent fournir des résultats en quasi temps réel. Les données ne seront jamais importées dans ces tables. Il s’agit en général de tables de type fait (utilisées pour le résumé).
- **Importer** : nous vous recommandons de définir ce mode pour les tables de type dimension (utilisées pour le filtrage et le regroupement). Il s’agit en fait de la seule option pour les tables basées sur des sources non prises en charge par le mode DirectQuery. Les tables calculées sont toujours des tables d’importation.
- **Double** : nous vous recommandons de définir ce mode pour les tables de type dimension, si elles sont potentiellement interrogées avec des tables de type fait DirectQuery à partir de la même source.

Plusieurs scénarios sont possibles lorsque Power BI interroge un modèle composite :

- **Interroge uniquement une ou plusieurs tables d’importation ou tables doubles** : toutes les données sont récupérées à partir du cache de modèle. Ce scénario offre les performances les plus rapides possibles. Il est courant pour les tables de type dimension interrogées par des filtres ou des visuels de segment.
- **Interroge une ou plusieurs tables doubles ou tables DirectQuery à partir de la même source** : toutes les données sont récupérées en envoyant une ou plusieurs requêtes natives à la source DirectQuery. Ce scénario offre les performances les plus rapides possibles, en particulier lorsque les tables sources comportent des index appropriés. Il est courant pour les requêtes qui associent des tables de type dimension et des tables de type fait DirectQuery. Ces requêtes étant _intra-îlots_, toutes les relations un-à-un ou un-à-plusieurs sont évaluées comme des [relations régulières](../transform-model/desktop-relationships-understand.md#regular-relationships).
- **Toutes les autres requêtes** : ces requêtes impliquent des relations entre îlots, soit parce qu’une table d’importation est associée à une table DirectQuery, soit parce qu’une table double est associée à une table DirectQuery à partir d’une autre source, auquel cas elle se comporte comme une table d’importation. Toutes les relations sont évaluées comme des [relations limitées](../transform-model/desktop-relationships-understand.md#limited-relationships). Cela signifie également que les regroupements appliqués aux tables non DirectQuery doivent être envoyés à la source DirectQuery en tant que table virtuelle. Dans ce cas, la requête native peut être inefficace, en particulier pour les jeux de regroupement volumineux. Elle risque par ailleurs d’exposer des données sensibles.

Suivez par conséquent les recommandations suivantes :

- Demandez-vous bien si un modèle composite est la bonne solution : s’il permet l’intégration au niveau du modèle de différentes sources de données, il présente également des complexités de conception avec des conséquences possibles.
- Définissez le mode de stockage sur **DirectQuery** lorsque la table est une table de type fait qui stocke de gros volumes de données, ou qu’elle doit fournir des résultats en quasi temps réel.
- Définissez le mode de stockage sur **Double** lorsque la table est une table de type dimension, et qu’elle sera interrogée avec des tables de type fait **DirectQuery** basées sur la même source.
- Configurez des fréquences d’actualisation permettant de maintenir la synchronisation du cache de modèle des tables doubles (et de toutes les tables calculées dépendantes) avec la ou les bases de données sources.
- Efforcez-vous de garantir l’intégrité des données entre les différentes sources de données (y compris le cache de modèle) : les relations limitées éliminent les lignes quand les valeurs de colonnes associées ne correspondent pas.
- Optimisez les sources de données DirectQuery avec les index appropriés pour obtenir des jointures, filtres et le regroupements efficaces.
- Ne chargez pas de données sensibles dans des tables d’importation ou des tables doubles s’il y a un risque d’interception d’une requête native. Pour plus d’informations, consultez [Utiliser des modèles composites dans Power BI Desktop (implications sur la sécurité)](../transform-model/desktop-composite-models.md#security-implications).

### <a name="aggregations"></a>Agrégations

Vous pouvez ajouter des agrégations à des tables DirectQuery dans votre modèle composite. Comme elles sont mises en cache dans le modèle, elles se comportent comme des tables d’importation (bien qu’elles ne soient pas utilisables comme une table de modèle). Leur fonction est d’améliorer les performances des requêtes « à grain élevé ». Pour plus d’informations, consultez [Agréations dans Power BI Desktop](../transform-model/desktop-aggregations.md).

Nous vous recommandons de suivre une règle de base pour les tables d’agrégation : son nombre de lignes doit être au moins 10 fois plus petit que la table sous-jacente. Par exemple, si la table sous-jacente stocke un milliard de lignes, la table d’agrégation ne doit pas dépasser 100 millions de lignes. Cette règle garantit un gain de performances adapté au coût de création et de maintenance de la table d’agrégation.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Utiliser des modèles composites dans Power BI Desktop](../transform-model/desktop-composite-models.md)
- [Relations de modèle dans Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [Modèles DirectQuery dans Power BI Desktop](../connect-data/desktop-directquery-about.md)
- [Utiliser DirectQuery dans Power BI Desktop](../connect-data/desktop-use-directquery.md)
- [Résolution des problèmes du modèle DirectQuery dans Power BI Desktop](../connect-data/desktop-directquery-troubleshoot.md)
- [Sources de données Power BI](../connect-data/power-bi-data-sources.md)
- [Mode de stockage dans Power BI Desktop](../transform-model/desktop-storage-mode.md)
- [Agrégations dans Power BI Desktop](../transform-model/desktop-aggregations.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)
