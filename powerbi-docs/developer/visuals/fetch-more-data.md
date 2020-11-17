---
title: Extraire davantage de données de Power BI
description: Cet article explique comment permettre une extraction segmentée des jeux de données volumineux pour les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483693"
---
# <a name="fetch-more-data-from-power-bi"></a>Extraire davantage de données de Power BI

Cet article explique comment charger davantage de données pour contourner la limite fixe d’un point de données de 30 Ko à l’aide de la méthode `fetchMoreData`. Cette approche fournit les données en bloc. Pour améliorer les performances, vous pouvez configurer une taille de lot adaptée aux besoins de votre cas d’usage.

## <a name="limitations-of-fetchmoredata"></a>Limitations de fetchMoreData

* La taille de la fenêtre est limitée à une plage comprise entre 2 et 30 000.
* Le nombre total de lignes d’un dataview est limité à 1 048 576 lignes.
* En mode d’agrégation de segments, la taille de mémoire du dataview est limitée à 100 Mo.

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Permettre une extraction segmentée des jeux de données volumineux

Avec le mode de segment `dataview`, vous définissez une taille de fenêtre pour `dataReductionAlgorithm` dans le fichier *capabilities.json* du visuel pour le `dataViewMapping` requis. La valeur `count` détermine la taille de la fenêtre, qui limite le nombre de nouvelles lignes de données qu’il est possible d’ajouter à l’élément `dataview` à chaque mise à jour.

Ajoutez le code suivant dans le fichier *capabilities.json* :

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Les nouveaux segments sont ajoutés à l’élément `dataview` existant et fournis au visuel sous la forme d’un appel `update`.

## <a name="usage-in-the-power-bi-visual"></a>Utilisation dans le visuel Power BI

Dans Power BI, vous pouvez utiliser `fetchMoreData` en mode d’agrégation de segments par défaut ou en mode de mises à jour incrémentielles. 

### <a name="using-segments-aggregation-mode-default"></a>Utilisation du mode d’agrégation de segments (par défaut)

Dans ce mode, le dataview fourni au visuel contient les données accumulées pour toutes les `fetchMoreData requests` précédentes. Par conséquent, la taille du dataview est censée croître à chaque mise à jour. Par exemple, si le nombre total de lignes attendues est de 100 000 et que la taille de fenêtre est définie sur 10 000, le dataview de la première mise à jour doit inclure 10 000 lignes, le dataview de la deuxième mise à jour doit inclure 20 000 lignes, et ainsi de suite.

Ce mode est sélectionné en appelant `fetchMoreData` avec `aggregateSegments = true`.

Vous pouvez déterminer s’il existe des données en vérifiant l’existence de `dataView.metadata.segment` :

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Vous pouvez également vérifier s’il s’agit de la première mise à jour ou d’une mise à jour suivante en vérifiant `options.operationKind`. Dans le code suivant, `VisualDataChangeOperationKind.Create` fait référence au premier segment et `VisualDataChangeOperationKind.Append` aux segments suivants.

Pour voir un exemple d’implémentation, reportez-vous à l’extrait de code ci-dessous :

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Vous pouvez aussi appeler la méthode `fetchMoreData` à partir d’un gestionnaire d’événements d’interface utilisateur, comme ici :

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

En réponse à l’appel de la méthode `this.host.fetchMoreData`, Power BI appelle la méthode `update` du visuel avec un nouveau segment de données.

> [!NOTE]
> Pour éviter les contraintes de mémoire client, Power BI limite actuellement le total de données extraites à 100 Mo. Vous savez que la limite a été atteinte quand `fetchMoreData()` retourne la valeur `false`.

### <a name="using-incremental-updates-mode"></a>Utilisation du mode de mises à jour incrémentielles

Dans ce mode, le dataview fourni au visuel contient uniquement des données incrémentielles. Par conséquent, la taille du dataview ne transmet pas la taille de fenêtre définie. Par exemple, si le nombre total de lignes attendues et de 101 000 et que la taille de fenêtre est définie sur 10 000, le visuel obtiendra 10 mises à jour avec une taille de dataview de 10 000 et une seule mise à jour avec un dataview d’une taille de 1 000.

Ce mode est sélectionné en appelant `fetchMoreData` avec `aggregateSegments = false`.

Vous pouvez déterminer s’il existe des données en vérifiant l’existence de `dataView.metadata.segment` :

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Vous pouvez également vérifier s’il s’agit de la première mise à jour ou d’une mise à jour suivante en vérifiant `options.operationKind`. Dans le code suivant, `VisualDataChangeOperationKind.Create` fait référence au premier segment et `VisualDataChangeOperationKind.Segment`, aux segments suivants.

Pour voir un exemple d’implémentation, reportez-vous à l’extrait de code ci-dessous :

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

Vous pouvez aussi appeler la méthode `fetchMoreData` à partir d’un gestionnaire d’événements d’interface utilisateur, comme ici :

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

En réponse à l’appel de la méthode `this.host.fetchMoreData`, Power BI appelle la méthode `update` du visuel avec un nouveau segment de données.

> [!NOTE]
> Bien que les données des dataviews d’une mise à jour à l’autre soient essentiellement exclusives, un chevauchement pourra être constaté entre les dataviews suivants.
> Pour le mappage de données de table et de catégorie, les N premières lignes du dataview contiennent les données copiées dans le dataview précédent.
> N peut être déterminé par `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`