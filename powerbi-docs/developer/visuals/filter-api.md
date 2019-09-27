---
title: API Filtres de visuels dans les visuels Power BI
description: Cet article explique comment les visuels Power BI peuvent filtrer d’autres visuels.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 98ebc87cf5a6b7bf8f0b8b88d4ff498edfd5bf9a
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194032"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>API Filtres de visuels dans les visuels Power BI

L’API Filtres de visuels vous permet de filtrer des données dans des visuels Power BI. La principale différence par rapport aux autres sélections est que les autres visuels seront filtrés de toute manière, malgré la prise en charge de la mise en évidence par un autre visuel.

Pour activer le filtrage pour le visuel, celui-ci doit contenir un objet `filter` dans la section `general` du code *capabilities.json*.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Les interfaces de l’API Filtres de visuels sont disponibles dans le package [powerbi-models](https://www.npmjs.com/package/powerbi-models). Le package contient également des classes pour créer des instances de filtre.

```cmd
npm install powerbi-models --save
```

Si vous utilisez une version plus ancienne (antérieure à 3.x.x) des outils, vous devez inclure `powerbi-models` dans le package de visuels. Pour plus d’informations, consultez le guide succinct intitulé [Add the Advanced Filter API to the custom visual](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md) (Ajouter l’API Filtre avancé au visuel personnalisé).

Tous les filtres étendent l’interface `IFilter`, comme illustré dans le code suivant :

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Où :
* `target` est la colonne de table sur la source de données.

## <a name="the-basic-filter-api"></a>API Filtre de base

L’interface de filtre de base est illustrée dans le code suivant :

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Où :
* `operator` est une énumération avec les valeurs *In*, *NotIn* et *All*.
* `values` sont des valeurs pour la condition.

Exemple de filtre de base :

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Le filtre signifie « Donnez-moi toutes les lignes où `col1` est égal à la valeur 1, 2 ou 3 ».

L’équivalent SQL est :

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Pour créer un filtre, vous pouvez utiliser la classe BasicFilter dans `powerbi-models`.

Si vous utilisez une version antérieure de l’outil, vous devez obtenir une instance de modèles dans l’objet de fenêtre à l’aide de `window['powerbi-models']`, comme illustré dans le code suivant :

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

Le visuel appelle le filtre à l’aide de la méthode applyJsonFilter() sur l’interface hôte, IVisualHost, qui est fournie au visuel dans le constructeur.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>API Filtre avancé

L’[API Filtre avancé](https://github.com/Microsoft/powerbi-models) permet de sélectionner et de filtrer des requêtes de point de données visuelles complexes en fonction de plusieurs critères tels que *LessThan*, *Contains*, *Is*, *IsBlank*, et ainsi de suite.

Le filtre a été introduit dans l’API Visuels 1.7.0.

L’API Filtre avancé nécessite également `target` avec un nom de `table` et de `column`. Toutefois, les opérateurs de l’API Filtre avancé sont *And* et *Or*. 

De plus, le filtre utilise des conditions au lieu de valeurs avec l’interface :

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Les opérateurs de condition pour le paramètre `operator` sont *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* et « IsNotBlank ».

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

L’équivalent SQL est :

```sql
SELECT * FROM table WHERE col1 < 0;
```

Pour obtenir l’exemple de code complet d’utilisation de l’API Filtre avancé, accédez au [dépôt de visuel Sampleslicer](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="the-tuple-filter-api-multi-column-filter"></a>API Filtre de tuple (filtre à plusieurs colonnes)

L’API Filtre de tuple a été introduite dans l’API Visuels 2.3.0. Elle est semblable à l’API Filtre de base, mais elle permet de définir des conditions pour plusieurs colonnes et tables.

L’interface de filtre est illustrée dans le code suivant : 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Où :
* `target` est un tableau de colonnes avec des noms de tables :

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  Le filtre peut traiter des colonnes de différentes tables.

* `$schema` est http://powerbi.com/product/schema#tuple.

* `filterType` est *FilterType.Tuple*.

* `operator` autorise l’utilisation uniquement dans l’opérateur *In*.

* `values` est un tableau de tuples de valeur, et chaque tuple représente une combinaison autorisée des valeurs de la colonne cible. 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Exemple complet :

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> L’ordre des noms de colonnes et des valeurs de condition est sensible.

L’équivalent SQL est :

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Restaurer le filtre JSON à partir de la vue des données

À compter de la version 2.2 de l’API, vous pouvez restaurer le filtre JSON à partir de *VisualUpdateOptions*, comme indiqué dans le code suivant :

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Quand vous changez de signet, Power BI appelle la méthode `update` du visuel, et le visuel obtient un objet `filter` correspondant. Pour plus d’informations, consultez [Ajouter la prise en charge des signets pour les visuels Power BI](bookmarks-support.md).

### <a name="sample-json-filter"></a>Exemple de filtre JSON

L’image suivante montre un exemple de code de filtre JSON :

![Code de filtre JSON](./media/json-filter.png)

### <a name="clear-the-json-filter"></a>Effacer le filtre JSON

L’API Filtre accepte la valeur `null` du filtre comme signifiant *réinitialiser* ou *effacer*.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
