---
title: Ajouter la prise en charge des signets pour les visuels Power BI
description: Les visuels Power BI peuvent gérer le changement de signets
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: aeea5ea3a9d1d2bd375c44b6c6b7eac57eb65aff
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748997"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Ajouter la prise en charge des signets pour les visuels Power BI

Avec les signets de rapport Power BI, vous pouvez capturer une vue configurée d’une page de rapport, l’état de sélection et l’état de filtrage du visuel. Toutefois, la prise en charge des signets et la réaction correcte aux modifications nécessitent des actions supplémentaires du côté des visuels Power BI.

Pour plus d'informations sur les signets, consultez [Utiliser des signets pour partager des insights et créer des récits dans Power BI](../../create-reports/desktop-bookmarks.md).

## <a name="report-bookmarks-support-in-your-visual"></a>Prise en charge des signets de rapport dans votre visuel

Si votre visuel interagit avec d’autres visuels, sélectionne des points de données ou filtre d’autres visuels, vous devez restaurer l’état à partir des propriétés.

## <a name="add-report-bookmarks-support"></a>Ajouter la prise en charge des signets de rapport

1. Installez (ou mettez à jour) l’utilitaire requis, [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) version 3.0.0 ou ultérieure. Cet utilitaire contient des classes supplémentaires à manipuler avec le filtre ou la sélection d’état. Il est nécessaire pour les visuels de filtre et tout visuel qui utilise `InteractivityService`.

2. Mettez à jour l’API des visuels vers la version 1.11.0 pour utiliser `registerOnSelectCallback` dans une instance de `SelectionManager`. Cette API est requise pour les visuels autres que les visuels de filtre qui utilisent le `SelectionManager` standard plutôt que `InteractivityService`.

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Interaction des visuels Power BI avec Power BI dans les signets de rapport

Prenons le scénario suivant : vous souhaitez créer plusieurs signets sur la page de rapport, avec un état de sélection différent dans chaque signet.

Pour commencer, vous sélectionnez un point de données dans votre visuel. Le visuel interagit avec Power BI et d’autres visuels en transmettant des sélections à l’hôte. Ensuite, vous sélectionnez **Ajouter** dans le panneau **Signet**. Power BI enregistre alors les sélections actuelles pour le nouveau signet.

Cette opération est répétée dès que vous changez la sélection et ajoutez de nouveaux signets. Une fois que vous avez créé les signets, vous pouvez basculer entre eux.

Quand vous sélectionnez un signet, Power BI restaure l’état de sélection ou de filtre enregistré, puis le passe aux visuels. Les autres visuels sont mis en surbrillance ou filtrés en fonction de l’état qui est stocké dans le signet. L’hôte Power BI gère les actions. Votre visuel s’occupe de refléter correctement le nouvel état de sélection (par exemple, de changer les couleurs des points de données affichés).

Le nouvel état de sélection est communiqué au visuel par le biais de la méthode `update`. L’argument `options` contient une propriété spéciale, `options.jsonFilters`. Sa propriété JSONFilter peut contenir `Advanced Filter` et `Tuple Filter`.

Le visuel doit restaurer les valeurs de filtre afin d’afficher l’état correspondant du visuel pour le signet sélectionné. Ou bien, si le visuel utilise uniquement des sélections, vous pouvez utiliser l’appel de fonction callback spécial qui est inscrit en tant que méthode `registerOnSelectCallback` de ISelectionManager.

### <a name="visuals-with-selection"></a>Visuels avec Selection

Si votre visuel interagit avec d’autres visuels à l’aide de [Selection](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), vous pouvez ajouter des signets de deux manières :

* Si le visuel n’a pas encore utilisé [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts), vous pouvez employer la méthode `FilterManager.restoreSelectionIds`.

* Si le visuel utilise déjà [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts) pour gérer les sélections, vous devez employer la méthode `applySelectionFromFilter` dans l’instance de `InteractivityService`.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>Utiliser ISelectionManager.registerOnSelectCallback

Quand vous sélectionnez un signet, Power BI appelle la méthode `callback` du visuel avec les sélections correspondantes. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Supposons que vous avez un point de données dans votre visuel qui a été créé dans la méthode [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

Et que l’élément `datapoints` ressemble à ceci :

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

Vous avez maintenant `visualDataPoints` comme points de données et le tableau `ids` qui est passé à la fonction `callback`.

À ce stade, le visuel doit comparer le tableau `ISelectionId[]` avec les sélections indiquées dans votre tableau `visualDataPoints` et marquer les points de données correspondants comme étant sélectionnés.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Une fois les points de données mis à jour, ils doivent refléter l’état de sélection actuel qui est stocké dans l’objet `filter`. Ensuite, quand les points de données sont affichés, l’état de sélection du visuel personnalisé doit correspondre à l’état du signet.

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>Utiliser InteractivityService pour les sélections de contrôle dans le visuel

Si votre visuel utilise `InteractivityService`, aucune action supplémentaire n’est requise pour la prise en charge des signets qu’il contient.

Quand vous sélectionnez des signets, l’utilitaire gère l’état de sélection du visuel.

### <a name="visuals-with-a-filter"></a>Visuels avec un filtre

Supposons que le visuel crée un filtre de données par plage de dates. `startDate` et `endDate` définissent les dates de début et de fin de la plage.

Le visuel crée un filtre avancé et appelle la méthode hôte `applyJsonFilter` pour filtrer les données selon les conditions appropriées.

La cible est la table qui est utilisée pour le filtrage.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Chaque fois que vous sélectionnez un signet, le visuel personnalisé reçoit un appel `update`.

Le visuel personnalisé doit vérifier le filtre dans l’objet :

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Si l’objet `filter` n’est pas Null, le visuel doit restaurer les conditions de filtre à partir de cet objet :

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Après quoi, le visuel doit changer son état interne pour refléter les conditions actuelles. L’état interne inclut les points de données et les objets de visualisation (lignes, rectangles, etc.).

> [!IMPORTANT]
> Dans le scénario des signets de rapport, le visuel ne doit pas appeler `applyJsonFilter` pour filtrer les autres visuels, car ceux-ci sont déjà filtrés par Power BI.

Le visuel Timeline Slicer change le sélecteur de plage pour refléter les plages de données correspondantes.

Pour plus d’informations, consultez l’article [Timeline Slicer repository](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df) (Référentiel Timeline Slicer).

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Filtrer l’état pour enregistrer les propriétés des visuels dans les signets

La propriété `filterState` est une propriété d’une partie du filtrage. Le visuel peut stocker diverses valeurs dans les signets.

Pour enregistrer la valeur de la propriété en tant qu’état de filtre, marquez la propriété de l’objet comme `"filterState": true` dans le fichier *capabilities.json*.

Par exemple, le visuel Timeline Slicer stocke les valeurs de propriété `Granularity` dans un filtre. Ainsi, la précision actuelle change en même temps que vous changez les signets.

Pour plus d’informations, consultez l’article [Timeline Slicer repository](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334) (Référentiel Timeline Slicer).