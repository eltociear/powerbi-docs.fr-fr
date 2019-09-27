---
title: Extraire davantage de données de Power BI
description: Cet article explique comment permettre une extraction segmentée des jeux de données volumineux pour les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b67977abd93b3aa605430dd2d7fb516ca33bd51c
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194058"
---
# <a name="fetch-more-data-from-power-bi"></a>Extraire davantage de données de Power BI

Cet article explique comment charger davantage de données pour contourner la limite fixe d’un point de données de 30 Ko. Cette approche fournit les données en bloc. Pour améliorer les performances, vous pouvez configurer une taille de lot adaptée aux besoins de votre cas d’usage.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Permettre une extraction segmentée des jeux de données volumineux

Avec le mode de segment `dataview`, vous définissez une taille de fenêtre pour dataReductionAlgorithm dans le fichier *capabilities.json* du visuel pour le dataViewMapping requis. La valeur `count` détermine la taille de la fenêtre, qui limite le nombre de nouvelles lignes de données qu’il est possible d’ajouter à l’élément `dataview` à chaque mise à jour.

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

Vous pouvez déterminer si le visuel contient des données en vérifiant l’existence de `dataView.metadata.segment` :

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Vous pouvez également vérifier s’il s’agit de la première mise à jour ou d’une mise à jour ultérieure en utilisant `options.operationKind`. Dans le code suivant, `VisualDataChangeOperationKind.Create` fait référence au premier segment et `VisualDataChangeOperationKind.Append`, aux segments suivants.

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

Vous pouvez également appeler la méthode `fetchMoreData` à partir d’un gestionnaire d’événements d’interface utilisateur, comme illustré ici :

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

En réponse à l’appel de la méthode `this.host.fetchMoreData`, Power BI appelle la méthode `update` du visuel avec un nouveau segment de données.

> [!NOTE]
> Pour éviter les contraintes de mémoire client, Power BI limite actuellement le total de données extraites à 100 Mo. Vous savez que la limite a été atteinte quand fetchMoreData() retourne la valeur `false`.
