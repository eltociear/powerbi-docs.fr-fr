---
title: Aide sur l’extraction de données pour les rapports paginés
description: Aide sur la création de sources de données et de jeux de données pour les rapports paginés Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 1e69c7eefe25da771ecc4d9602d6a21081f2c052
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920749"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Aide sur l’extraction de données pour les rapports paginés

Cet article s’adresse à vous en tant qu’auteur de [rapports paginés](../paginated-reports/paginated-reports-report-builder-power-bi.md) Power BI. Il fournit des recommandations pour vous aider à concevoir un processus d’extraction de données efficace.

## <a name="data-source-types"></a>Types de sources de données

Les rapports paginés prennent en charge les sources de données relationnelles et analytiques en mode natif. Ces sources sont également classées en deux catégories : cloud ou locales. Pour que Power BI puisse se connecter à des sources de données locales, qu’elles soient hébergées localement ou sur une machine virtuelle, une passerelle de données est nécessaire. En revanche, Power BI peut se connecter directement à des sources de données cloud à l’aide d’une connexion Internet.

Si vous pouvez choisir le type de source de données (par exemple dans un nouveau projet), nous vous recommandons d’utiliser des sources de données cloud. Les rapports paginés peuvent se connecter avec une latence réseau inférieure, en particulier si les sources de données résident dans la même région que votre locataire Power BI. Par ailleurs, il est possible d’utiliser l’authentification unique pour se connecter à ces sources. L’identité de l’utilisateur d’un rapport peut donc circuler jusqu’à la source de données, d’où la possibilité d’appliquer des autorisations par utilisateur au niveau des lignes. À l’heure actuelle, l’authentification unique n’est pas prise en charge pour les sources de données locales (SQL Server Analysis Services ne peut donc pas appliquer des autorisations par utilisateur au niveau des lignes).

> [!NOTE]
> Bien qu’il soit pour le moment impossible de se connecter à des bases de données locales à l’aide de l’authentification unique, vous pouvez toujours appliquer des autorisations au niveau des lignes. Pour cela, il suffit de passer le champ intégré le **UserID** à un paramètre de requête de jeu de données. La source de données doit stocker les valeurs UPN (nom d’utilisateur principal) de manière à pouvoir filtrer correctement les résultats de la requête.
>
> Par exemple, imaginez que chaque commercial soit stocké dans une ligne de la table **Salesperson**.  La table contient des colonnes pour l’UPN et le territoire de vente du commercial. Au moment de la requête, la table est filtrée par l’UPN de l’utilisateur de rapport et liée aux faits de vente à l’aide d’une jointure interne. De cette façon, la requête filtre les lignes de fait de vente pour ne retenir que celles du territoire de vente de l’utilisateur du rapport.

### <a name="relational-data-sources"></a>Sources de données relationnelles

En général, les sources de données relationnelles conviennent bien aux rapports opérationnels comme les factures de vente. Elles sont également adaptées aux rapports qui doivent extraire des jeux de données volumineux (de plus de 10 000 lignes). Les sources de données relationnelles peuvent également définir des procédures stockées qui sont exécutées par des jeux de données de rapport. Les procédures stockées offrent plusieurs avantages :

- Paramétrage
- Encapsulation de la logique de programmation, permettant une préparation plus complexe des données (par exemple, tables temporaires, curseurs ou fonctions scalaires définies par l’utilisateur)
- Maintenabilité améliorée, permettant de mettre facilement à jour la logique de la procédure stockée. Dans certains cas, vous pouvez le faire sans avoir à modifier et à republier les rapports paginés (les noms des colonnes et les types de données restent inchangés).
- Performances accrues, car leurs plans d’exécution sont mis en cache pour être réutilisés
- Réutilisation des procédures stockées dans plusieurs rapports

Dans Power BI Report Builder, vous pouvez utiliser le concepteur de requêtes relationnelles pour construire graphiquement une instruction de requête (uniquement pour les sources de données Microsoft).

### <a name="analytic-data-sources"></a>Sources de données analytiques

Les sources de données analytiques sont bien adaptées aux rapports opérationnels et analytiques. Elles peuvent aussi fournir rapidement des résultats de requête totalisés, même sur de très gros volumes de données. Les mesures de modèle et les KPI peuvent encapsuler des règles métier complexes en vue d’une totalisation des données. Toutefois, ces sources de données ne sont pas adaptées aux rapports qui doivent extraire des jeux de données volumineux (de plus de 10 000 lignes).

Dans Power BI Report Builder, vous avez le choix entre deux concepteurs de requêtes : le concepteur de requêtes DAX Analysis Services et le concepteur de requêtes MDX Analysis Services. Vous pouvez utiliser ces concepteurs pour des sources de données de jeu de données Power BI ou pour tout modèle SQL Server Analysis Services ou Azure Analysis Services (tabulaire ou multidimensionnel).

Nous vous suggérons d’utiliser le concepteur de requêtes DAX, à condition qu’il réponde entièrement à vos besoins en matière de requêtes. Si le modèle ne définit pas les mesures dont vous avez besoin, vous devez passer en mode requête. Dans ce mode, vous pouvez personnaliser l’instruction de requête en ajoutant des expressions (pour obtenir une totalisation).

Le concepteur de requêtes MDX exige que votre modèle inclue des mesures. Le concepteur a deux fonctionnalités non prises en charge par le concepteur de requêtes DAX. Plus précisément, il vous permet d’effectuer les opérations suivantes :

- Définir des membres calculés au niveau de la requête (dans MDX).
- Configurer des régions de données pour demander des [agrégats de serveurs](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) dans des groupes non détaillés. Si votre rapport doit présenter des totalisations de mesures semi-additives ou non-additives (comme des calculs Time Intelligence ou des nombres distincts), il est probablement plus efficace d’utiliser des agrégats de serveurs que d’extraire des lignes de détails de bas niveau et de demander au rapport de calculer des totalisations.

## <a name="query-result-size"></a>Taille du résultat de la requête

En général, il est recommandé d’extraire uniquement les données dont votre rapport a besoin. Veillez donc à ne pas extraire des colonnes ou des lignes inutiles.

Pour limiter les lignes, vous devez toujours appliquer les filtres les plus restrictifs et définir des requêtes d’agrégation. Les requêtes d’agrégation regroupent et totalisent les données sources pour extraire des résultats plus détaillés. Imaginons que vous deviez créer un rapport totalisant les ventes des représentants. Au lieu d’extraire toutes les lignes des commandes, créez une requête de jeu de données qui regroupe les commandes par vendeur et totalise les ventes de chaque groupe.

## <a name="expression-based-fields"></a>Champs basés sur des expressions

Il est possible d’étendre un jeu de données de rapport avec des champs basés sur des expressions. Par exemple, si votre jeu de données fournit le prénom et le nom de vos clients, vous pouvez avoir besoin d’un champ qui concatène les deux champs pour produire le nom complet des clients. Pour réaliser ce calcul, vous avez le choix entre deux options. Vous pouvez :

- Créer un _champ calculé_, qui est un champ de jeu de données basé sur une expression.
- Injecter une expression directement dans la requête de jeu de données (en utilisant la langue native de votre source de données), ce qui génère un champ de jeu de données standard.

Nous recommandons la dernière option dans la mesure du possible. L’injection d’expressions directement dans votre requête de jeu de données est préférable pour deux bonnes raisons :

- Il est possible que votre source de données soit optimisée pour évaluer l’expression plus efficacement que Power BI (ce qui est surtout vrai pour les bases de données relationnelles).
- Les performances des rapports sont améliorées, car Power BI n’a pas besoin de matérialiser des champs calculés avant de procéder au rendu des rapports. Les champs calculés peuvent augmenter considérablement le temps de rendu des rapports quand les jeux de données récupèrent un grand nombre de lignes.

## <a name="field-names"></a>Noms de champs

Quand vous créez un jeu de données, ses champs sont automatiquement nommés en fonction des colonnes de la requête. Il est possible que ces noms ne soient ni conviviaux ni intuitifs. Il peut également arriver que les noms des colonnes de la requête source contiennent des caractères interdits dans les identificateurs d’objet RDL (Report Definition Language), comme des espaces et des symboles. Dans ce cas, les caractères interdits sont remplacés par un caractère de soulignement (_).

Nous vous recommandons d’abord de vérifier que tous les noms de champs sont conviviaux et concis tout en étant significatifs. Si ce n’est pas le cas, nous vous suggérons de les renommer _avant_ de commencer la mise en page du rapport. En effet, les champs renommés ne répercutent pas les modifications sur les expressions utilisées dans la mise en page de votre rapport. Si vous décidez de renommer les champs après avoir commencé la mise en page du rapport, vous devez rechercher et mettre à jour toutes les expressions endommagées.

## <a name="filter-vs-parameter"></a>Filtre et paramètre

Vos conceptions de rapports paginés auront probablement des paramètres de rapport. Les paramètres de rapport sont couramment utilisés pour demander à l’utilisateur du rapport de filtrer le rapport. En tant qu’auteur de rapport paginé, vous pouvez effectuer un filtrage de rapport de deux façons. Vous pouvez mapper un paramètre de rapport à :

- Un _filtre_ de jeu de données, auquel cas la ou les valeurs de paramètre de rapport sont utilisées pour filtrer les données déjà extraites par le jeu de données.
- Un _paramètre_ de jeu de données, auquel cas la ou les valeurs de paramètre de rapport sont injectées dans la requête native envoyée à la source de données.

> [!NOTE]
> Tous les jeux de données de rapport sont mis en cache _par session_ pendant 10 minutes maximum _au-delà de leur dernière utilisation_. Un jeu de données peut être réutilisé lors de l’envoi de nouvelles valeurs de paramètres (filtrage), du rendu du rapport dans un format différent ou de l’interaction avec la conception du rapport (comme le basculement de la visibilité ou le tri).

Prenons l’exemple d’un rapport de ventes comprenant un seul paramètre de rapport pour filtrer le rapport sur une seule année. Le jeu de données extrait les ventes pour _toutes les années_. Cela est dû au fait que le paramètre de rapport est mappé aux filtres de jeu de données. Le rapport affiche les données de l’année demandée, c’est-à-dire un sous-ensemble du jeu de données. Quand l’utilisateur du rapport change l’année du paramètre de rapport, puis affiche le rapport, Power BI n’a pas besoin d’extraire de données sources. Au lieu de cela, il applique un filtre différent au jeu de données déjà mis en cache. Une fois le jeu de données mis en cache, le filtrage peut être très rapide.

Examinons à présent une conception de rapport différente. Cette fois-ci, la conception de rapport mappe le paramètre de rapport de l’année des ventes à un paramètre de jeu de données. De cette façon, Power BI injecte la valeur de l’année dans la requête native, et le jeu de données extrait uniquement les données de cette année. Lorsque l’utilisateur du rapport change la valeur de l’année du paramètre de rapport et qu’il affiche le rapport, le jeu de données extrait un nouveau résultat de requête juste pour cette année.

Les deux approches de conception peuvent filtrer des données de rapport et fonctionner correctement pour vos conceptions de rapports. Toutefois, une conception optimisée dépendra des volumes de données, de la volatilité des données et des comportements attendus des utilisateurs de vos rapports.

Nous vous recommandons d’utiliser le _filtrage de jeu de données_ si vous prévoyez de réutiliser plusieurs fois un sous-ensemble différent de lignes du jeu de données (accélérant ainsi le rendu puisqu’il est inutile d’extraire de nouvelles données). Dans ce scénario, vous reconnaissez que le coût de l’extraction d’un jeu de données plus important peut être compensé par le nombre de fois qu’il est réutilisé. Il est donc utile pour les requêtes dont la génération prend du temps. Mais faites attention, car la mise en cache de grands jeux de données par utilisateur peut avoir un impact négatif sur les performances et le débit de capacité.

Nous vous recommandons d’utiliser le _paramétrage de jeu de données_ s’il est peu probable qu’un sous-ensemble différent de lignes du jeu de données soit demandé ou si le nombre de lignes du jeu de données à filtrer est susceptible d’être très élevé (rendant la mise en cache inefficace). Cette approche de conception fonctionne également bien avec un magasin de données volatile. Dans ce cas, chaque modification de la valeur du paramètre de rapport entraîne l’extraction de données à jour.

## <a name="non-native-data-sources"></a>Sources de données non natives

Si vous avez besoin de développer des rapports paginés basés sur des sources de données qui ne sont pas [prises en charge en mode natif par les rapports paginés](../paginated-reports/paginated-reports-data-sources.md), vous pouvez tout d’abord développer un modèle de données Power BI Desktop. De cette façon, vous pouvez vous connecter à plus de 100 [sources de données Power BI](../power-bi-data-sources.md). Au terme de la publication sur le service Power BI, vous pouvez développer un rapport paginé qui se connecte au jeu de données Power BI.

## <a name="data-integration"></a>Intégration des données

Pour combiner des données provenant de plusieurs sources de données, vous avez le choix entre deux options :

- **Combiner des jeux de données de rapport** : si les sources de données sont [prises en charge en mode natif par les rapports paginés](../paginated-reports/paginated-reports-data-sources.md), vous pouvez envisager de créer des champs calculés qui utilisent la fonction [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) ou [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function) de Report Builder.
- **Développer un modèle Power BI Desktop** : il est probablement plus efficace de développer un modèle de données dans Power BI Desktop. Vous pouvez utiliser Power Query pour combiner des requêtes basées sur n’importe quelle [source de données prise en charge](../power-bi-data-sources.md). Au terme de la publication sur le service Power BI, vous pouvez développer un rapport paginé qui se connecte au jeu de données Power BI.

## <a name="sql-server-complex-data-types"></a>Types de données SQL Server complexes

Étant donné que SQL Server est une source de données locale, Power BI doit se connecter au moyen d’une passerelle. Toutefois, la passerelle ne prend pas en charge l’extraction de données pour les types de données complexes. Les types de données complexes incluent des types intégrés comme les [types de données spatiales](/sql/relational-databases/spatial/spatial-data-sql-server) GEOMETRY et GEOGRAPHY et [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). Ils incluent également des types définis par l’utilisateur qui sont implémentés par le biais d’une classe d’un assembly dans le CLR (Common Language Runtime) Microsoft.NET Framework.

Le traçage des données spatiales et de l’analytique dans la visualisation de la carte nécessite des données spatiales SQL Server. Il est donc impossible d’utiliser la visualisation de la carte quand SQL Server est votre source de données. Pour être clair, cela fonctionne si votre source de données est Azure SQL Database, car Power BI ne se connecte pas par le biais d’une passerelle.

## <a name="data-related-images"></a>Images liées aux données

Vous pouvez utiliser des images pour ajouter des logos ou des photos à la mise en page de votre rapport. Quand des images se rapportent aux lignes extraites par un jeu de données de rapport, deux options s’offrent à vous :

- Il est possible que les données d’image puissent également être extraites de votre source de données (en cas de stockage préalable dans une table).
- Quand les images sont stockées sur un serveur web, vous pouvez utiliser une expression dynamique pour créer le chemin à l’URL des images.

Pour obtenir plus d’informations et des suggestions, consultez l’[aide sur les images pour les rapports paginés](report-paginated-image.md).

## <a name="redundant-data-retrieval"></a>Extraction de données redondante

Il est possible que votre rapport extraie des données redondantes. Cela peut se produire si vous supprimez des champs de requête de jeu de données ou si le rapport contient des jeux de données inutilisés. Évitez ces situations, car elles entraînent une charge inutile sur vos sources de données, le réseau et les ressources de capacité de Power BI.

### <a name="deleted-query-fields"></a>Champs de requête supprimés

Dans la page **Champs** de la fenêtre **Propriétés du jeu de données**, il est possible de supprimer les _champs de requête_ du jeu de données (les champs de requête sont mappés aux colonnes extraites par la requête de jeu de données). Toutefois, Report Builder ne supprime pas les colonnes correspondantes de la requête de jeu de données.

Si vous devez supprimer des champs de requête de votre jeu de données, nous vous recommandons de supprimer les colonnes correspondantes de la requête de jeu de données. Report Builder supprime automatiquement tous les champs de requête redondants. Si vous supprimez des champs de requête, veillez à modifier également l’instruction de requête de jeu de données pour supprimer les colonnes.

### <a name="unused-datasets"></a>Jeux de données inutilisés

Quand un rapport est exécuté, tous les jeux de données sont évalués, même s’ils ne sont pas liés à des objets de rapport. Pour cette raison, veillez à supprimer tous les jeux de données de test ou de développement avant de publier un rapport.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Sources de données prises en charge pour les rapports paginés Power BI](../paginated-reports/paginated-reports-data-sources.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
