---
title: API Filtres visuels
description: Comment les visuels Power BI peuvent filtrer d’autres visuels
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425042"
---
# <a name="power-bi-visual-filters-api"></a>API Filtres de visuels Power BI

Filter-Visual permet de filtrer les données. La principale différence entre les sélections est que les autres visuels sont filtrés de quelque manière que ce soit, en mettant en évidence la prise en charge par un autre visuel.

Pour activer le filtrage pour le visuel, le visuel doit contenir un objet `filter` dans la section `general` du contenu capabilities.json.

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

Les interfaces d’API Filtre sont disponibles dans un package [`powerbi-models`](https://www.npmjs.com/package/powerbi-models). Le package contient également des classes pour créer des instances de filtre.

```cmd
npm install powerbi-models --save
```

Si vous utilisez d’anciens outils de version (version antérieure à 3.x.x), vous devez inclure `powerbi-models` dans le package de visuels. [Guide succinct concernant l’inclusion du package](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Tous les filtres étendent l’interface `IFilter`.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` - colonne de table sur la source de données.

## <a name="basic-filter-api"></a>API Filtre de base

L’interface de filtre de base est

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` - est une énumération avec les valeurs « in », « NotIn », « All »

`values` - sont des valeurs de condition

Exemple de filtre de base :

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Le filtre signifie « donnez-moi toutes les lignes où `col1` est égal à l’une des valeurs 1, 2 ou 3 ».

L’équivalent SQL est

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Pour créer un filtre, vous pouvez utiliser la classe BasicFilter dans `powerbi-models`.

Si vous utilisez l’ancienne version des outils, vous devez récupérer une instance de modèles dans l’objet window par `window['powerbi-models']` :

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

Le visuel appelle le filtre à l’aide de la méthode applyJsonFilter() sur l’interface hôte IVisualHost fournie au visuel dans le constructeur.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>API Filtres avancés

L’[API Filtre avancé](https://github.com/Microsoft/powerbi-models) permet de sélectionner et de filtrer des requêtes de point de données visuelles complexes en fonction de plusieurs critères (tels que « LessThan », « Contains », « is », « IsBlank », etc.).

Le filtre a été introduit dans l’API Visuels 1.7.0.

L’API Filtre avancé requiert également `target` avec le nom `table` et `column`. Toutefois, les opérateurs de l’API Filtre avancé sont `"And" | "Or"`. 

En outre, le filtre utilise des conditions au lieu de valeurs avec l’interface :

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Les opérateurs de condition pour le paramètre `operator` sont `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

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

L’équivalent SQL est

```sql
SELECT * FROM table WHERE col1 < 0;
```

L’exemple de code complet de l’utilisation de l’API Filtre avancé se trouve dans le [`Sampleslicer visual`référentiel](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>API Filtre de tuple (filtre à plusieurs colonnes)

L’API Filtre de tuple a été introduite dans l’API Visuels 2.3.0.

L’API Filtre de tuple est similaire au filtre de base, mais elle permet de définir des conditions pour plusieurs colonnes et tables.

Et un filtre possède l’interface suivante : 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` est un tableau de colonnes avec des noms de tables :

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  Le filtre peut traiter des colonnes de différentes tables.

`$schema` est "http://powerbi.com/product/schema#tuple"

`filterType` est `FilterType.Tuple`

`operator` autorise uniquement l’utilisation de l’opérateur `"In"`

`values` est un tableau de tuples de valeur, où chaque tuple représente une combinaison autorisée des valeurs de la colonne cible. 

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
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
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

**L’ordre des noms de colonnes et des valeurs de condition est sensible.**

L’équivalent SQL est

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Restauration du filtre JSON à partir de DataView

À partir de l’API 2.2, les **filtres JSON** peuvent être restaurés à partir de **VisualUpdateOptions**

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

Power BI appelle la méthode `update` du visuel, lorsque l’utilisation des signets de commutateur et l’objet visuel correspond à l’objet `filter`.
[En savoir plus sur la prise en charge des signets](bookmarks-support.md)

### <a name="sample-json-filter"></a>Exemple de filtre JSON

![Capture d’écran du filtre JSON](./media/json-filter.png)

### <a name="clear-json-filter"></a>Effacer un filtre JSON

L’API Filtre accepte la valeur `null` du filtre comme réinitialiser ou effacement.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
