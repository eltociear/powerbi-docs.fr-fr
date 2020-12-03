---
title: Utiliser des paramètres en cascade dans les rapports paginés
description: Conseils pour la conception de rapports paginés à l’aide de paramètres en cascade.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: fca5d6556c296094e4536ecf965388e2a4224ed9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417908"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Utiliser des paramètres en cascade dans les rapports paginés

Cet article s’adresse à vous en tant qu’auteur de [rapports paginés](../paginated-reports/paginated-reports-report-builder-power-bi.md) Power BI. Il fournit des scénarios pour la conception de paramètres en cascade. Les paramètres en cascade sont des paramètres de rapport comportant des dépendances. Lorsqu’un utilisateur de rapport sélectionne une ou plusieurs valeurs de paramètres, cette option permet de définir les valeurs disponibles pour un autre paramètre.

> [!NOTE]
> Cet article n’aborde pas la présentation des paramètres en cascade et leur configuration. Si vous ne connaissez pas bien les paramètres en cascade, nous vous recommandons de lire d’abord l’article [Ajouter des paramètres en cascade à un rapport (Générateur de rapports et SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Scénarios de conception

Il existe deux scénarios de conception pour l’utilisation des paramètres en cascade. Ils peuvent être utilisés efficacement pour :

- Filtrer des _jeux volumineux_ d’éléments
- Présenter les éléments _pertinents_

### <a name="example-database"></a>Exemple de base de données

Les exemples présentés dans cet article sont basés sur une base de données Azure SQL. La base de données consigne les opérations de vente et contient diverses tables qui répertorient les revendeurs, produits et commandes.

Une table nommée **Reseller** (Revendeur) contient un enregistrement pour chaque revendeur et totalise plusieurs milliers d’enregistrements. La table **Reseller** comporte les colonnes suivantes :

- ResellerCode (entier)
- ResellerName
- Pays-Région
- État-Province
- Ville
- PostalCode

Il existe également une table nommée **Sales** (Ventes). Elle consigne les enregistrements de commandes et présente une relation de clé étrangère avec la table **Reseller**, au niveau de la colonne **ResellerCode**.

### <a name="example-requirement"></a>Exemple d’exigence

Un rapport Profil du revendeur doit être créé. Le rapport doit être conçu pour afficher des informations concernant un seul revendeur. Il n’est pas recommandé de demander à l’utilisateur du rapport d’entrer un code revendeur car ce code est rarement mémorisé.

## <a name="filter-large-sets-of-items"></a>Filtrer des jeux volumineux d’éléments

Examinons trois exemples pour vous aider à limiter les jeux volumineux d’éléments disponibles tels que les revendeurs. Il s'agit de :

- [Filtrer par colonnes associées](#filter-by-related-columns)
- [Filtrer par colonne de regroupement](#filter-by-a-grouping-column)
- [Filtrer par modèle de recherche](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filtrer par colonnes associées

Dans cet exemple, l’utilisateur du rapport interagit avec cinq paramètres de rapport. Il doit sélectionner pays-région, état-province, ville, puis code postal. Un dernier paramètre répertorie ensuite les revendeurs qui résident dans cet emplacement géographique.

![Capture d’écran des paramètres de rapport paginé Power BI montrant le filtre par colonnes associées.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

Voici comment vous pouvez développer les paramètres en cascade :

1. Créez les cinq paramètres de rapport, en les classant dans l’ordre approprié.
2. Créez le jeu de données **CountryRegion**, qui récupère des valeurs de pays-région distinctes, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Créez le jeu de données **StateProvince** qui récupère des valeurs d’état/province distinctes pour la valeur pays-région sélectionnée, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Créez le jeu de données **City** qui récupère des valeurs de ville distinctes pour les valeurs pays-région et état-province sélectionnées, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Continuez avec ce modèle afin de créer le jeu de données **PostalCode**.
6. Créez le jeu de données **Reseller** afin de récupérer tous les revendeurs pour les valeurs géographiques sélectionnées, en utilisant l’instruction de requête suivante :

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Pour chaque jeu de données à l’exception du premier, mappez les paramètres de requête aux paramètres de rapport correspondants.

> [!NOTE]
> Tous les paramètres de requête (précédés du symbole @) affichés dans ces exemples peuvent être incorporés dans des instructions SELECT ou passés à des procédures stockées.
>
> En règle générale, les procédures stockées constituent une meilleure approche de conception. Cela est dû au fait que leurs plans de requête sont mis en cache afin d’accélérer l’exécution et vous permettent de développer une logique plus sophistiquée, le cas échéant. Toutefois, ces procédures ne sont actuellement pas prises en charge pour les sources de données relationnelles de passerelle, c’est-à-dire SQL Server, Oracle et Teradata.
>
> Enfin, vous devez toujours veiller à ce qu’il existe des index appropriés pour prendre en charge une récupération efficace des données. Sinon, le traitement des paramètres de votre rapport risque d’être lent, et la base de données peut devenir surchargée. Pour plus d’informations sur l’indexation de SQL Server, consultez le [Guide de conception et d’architecture d’index SQL Server](/sql/relational-databases/sql-server-index-design-guide).

### <a name="filter-by-a-grouping-column"></a>Filtrer par colonne de regroupement

Dans cet exemple, l’utilisateur du rapport interagit avec un paramètre de rapport pour sélectionner la première lettre du revendeur. Un deuxième paramètre répertorie ensuite les revendeurs dont le nom commence par la lettre sélectionnée.

![Capture d’écran des paramètres de rapport paginé Power BI montrant un filtre par colonne de regroupement.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

Voici comment vous pouvez développer les paramètres en cascade :

1. Créez les paramètres de rapport **ReportGroup** et **Reseller**, en les classant dans l’ordre approprié.
2. Créez le jeu de données **ReportGroup** pour récupérer les premières lettres utilisées par tous les revendeurs, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Créez le jeu de données **Reseller** pour récupérer tous les revendeurs qui commencent par la lettre sélectionnée, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Mappez le paramètre de requête du jeu de données **Reseller** au paramètre de rapport correspondant.

Il est plus efficace d’ajouter la colonne de regroupement à la table **Reseller**. Si cette colonne est persistante et indexée, elle offre des résultats optimaux. Pour plus d'informations, consultez [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table).

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Cette technique peut offrir un potentiel encore plus grand. Considérons le script suivant, qui ajoute une nouvelle colonne de regroupement afin de filtrer les revendeurs par _bandes de lettres prédéfinies_. Ce script crée également un index pour récupérer efficacement les données requises par les paramètres de rapport.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filtrer par modèle de recherche

Dans cet exemple, l’utilisateur du rapport interagit avec un paramètre de rapport pour entrer un modèle de recherche. Un deuxième paramètre répertorie ensuite les revendeurs dont le nom contient le modèle.

![Capture d’écran des paramètres de rapport paginé Power BI montrant le filtre par modèle de recherche.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

Voici comment vous pouvez développer les paramètres en cascade :

1. Créez les paramètres de rapport **Search** et **Reseller**, en les classant dans l’ordre approprié.
2. Créez le jeu de données **Reseller** pour récupérer tous les revendeurs dont le nom contient le texte recherché, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Mappez le paramètre de requête du jeu de données **Reseller** au paramètre de rapport correspondant.

> [!TIP]
> Vous pouvez améliorer cette conception afin de fournir davantage de contrôle à vos utilisateurs de rapports. Ils peuvent ainsi définir leur propre valeur de correspondance de modèle. Par exemple, la valeur de recherche « red% » filtrera les revendeurs dont les noms _commencent_ par les caractères « red ».
>
> Pour plus d’informations, consultez [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql#using-the--wildcard-character).

Voici comment permettre aux utilisateurs de rapports de définir leur propre modèle.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Cependant, de nombreux professionnels peu familiarisés avec les bases de données ne connaissent pas le caractère générique pourcentage (%). Ils utilisent généralement le caractère astérisque (*). En modifiant la clause WHERE, vous leur permettez d’utiliser ce caractère.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Présenter les éléments pertinents

Dans ce scénario, vous pouvez utiliser des données de faits pour limiter les valeurs disponibles. Les utilisateurs de rapport recevront les éléments pour lesquels l’activité a été enregistrée.

Dans cet exemple, l’utilisateur du rapport interagit avec trois paramètres de rapport. Les deux premiers définissent une plage de dates de commandes des clients. Le troisième paramètre répertorie ensuite les revendeurs pour lesquels des commandes ont été créées au cours de cette période.

![Capture d’écran des paramètres de rapport paginé Power BI montrant trois paramètres de rapport : Start Order Date, End Order Date et Reseller.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

Voici comment vous pouvez développer les paramètres en cascade :

1. Créez les paramètres de rapport **OrderDateStart**, **OrderDateEnd** et **Reseller**, en les classant dans l’ordre approprié.
2. Créez le jeu de données **Reseller** pour récupérer tous les revendeurs qui ont créé des commandes dans cette plage de dates, à l’aide de l’instruction de requête suivante :

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Recommandations

Nous vous recommandons de concevoir vos rapports en utilisant autant que possible des paramètres en cascade. En effet, ces paramètres en cascade :

- Garantissent des expériences intuitives et utiles à vos utilisateurs de rapports
- Sont efficaces, car ils récupèrent des plus petits jeux de valeurs disponibles

Veillez à optimiser vos sources de données en procédant comme suit :

- Utilisez autant que possible des procédures stockées
- Ajoutez des index appropriés pour une récupération efficace des données
- Matérialisez les valeurs de colonnes (voire des lignes) pour éviter des évaluations coûteuses en temps de recherche

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Paramètres de rapport dans le Générateur de rapports Power BI](../paginated-reports/report-builder-parameters.md)
- [Ajouter des paramètres en cascade à un rapport (Générateur de rapports et SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)
