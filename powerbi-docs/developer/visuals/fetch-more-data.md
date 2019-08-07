---
title: Récupérer d’autres données
description: Activer l’extraction segmentée des jeux de données volumineux pour les visuels Power BI
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425065"
---
# <a name="fetch-more-data-from-power-bi"></a>Extraire davantage de données de Power BI

Charger plus de données dans l’API permet de surmonter la limite stricte de 30 000 points de données. Les données sont chargées par blocs. La taille de bloc peut être configurée afin d’améliorer les performances en fonction du cas d’usage.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Activer l’extraction segmentée des jeux de données volumineux

Pour le mode de segment `dataview`, définissez une « fenêtre » dataReductionAlgorithm dans le fichier `capabilities.json` du visuel pour le dataViewMapping requis.
Le `count` détermine la taille de la fenêtre, qui limite le nombre de nouvelles lignes de données ajoutées à l’élément `dataview` dans chaque mise à jour.

Éléments à ajouter dans le fichier capabilities.json

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

## <a name="usage-in-the-custom-visual"></a>Utilisation dans le visuel personnalisé

Les données d’indication existent ou ne peuvent pas être déterminées en vérifiant l’existence de `dataView.metadata.segment` :

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Il est également possible de déterminer s’il s’agit de la première mise à jour ou d’une mise à jour ultérieure en vérifiant `options.operationKind`.

`VisualDataChangeOperationKind.Create` correspond au premier segment, et `VisualDataChangeOperationKind.Append` correspond aux segments suivants.

Pour obtenir un exemple d’implémentation, consultez l’extrait de code ci-dessous :

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

La méthode `fetchMoreData` peut également être appelée à partir d’un gestionnaire d’événements de l’interface utilisateur.

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI appelle la méthode `update` du visuel avec un nouveau segment de données comme réponse pour appeler la méthode `this.host.fetchMoreData`.

> [!NOTE]
> Power BI limite actuellement le total de données extraites à **100 Mo** pour éviter les contraintes de mémoire client. Vous pouvez déterminer que cette limite est atteinte quand fetchMoreData() retourne la valeur « false ».*
