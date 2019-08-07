---
title: Favoris
description: Les visuels Power BI peuvent gérer le changement de signets
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425502"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Ajouter la prise en charge des signets pour les visuels Power BI

Les signets de rapport Power BI permettent de capturer l’affichage configuré d’une page de rapport, un état de sélection et l’état de filtrage du visuel. Toutefois, la prise en charge des signets et la réaction correcte aux modifications nécessitent des actions supplémentaires du côté des visuels personnalisés.

Pour en savoir plus sur les signets, consultez la [documentation](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Prise en charge des signets de rapport dans votre visuel

Si votre visuel interagit avec d’autres visuels, sélectionne des points de données ou filtre d’autres visuels, vous devez restaurer l’état à partir des propriétés.

## <a name="how-to-add-report-bookmarks-support"></a>Ajout de la prise en charge des signets de rapport

1. Installez (ou mettez à jour) l’utilitaire requis : `powerbi-visuals-utils-interactivityutils` (https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) version 3.0.0 ou supérieure. Il contient des classes supplémentaires à manipuler avec le filtre ou la sélection d’état. Il est requis pour les visuels de filtre et pour tout visuel utilisant le `InteractivityService`.

2. Mettez à jour l’API de visuel vers 1.11.0 pour utiliser `registerOnSelectCallback` dans l’instance de `SelectionManager`. Il est requis pour les visuels autres que de filtre utilisant le `SelectionManager` standard plutôt que le `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Interaction des visuels personnalisés avec Power BI dans le scénario de signets de rapport

Prenons l’exemple suivant : un utilisateur crée plusieurs signets dans la page de rapport, avec un état de sélection différent dans chaque signet.

L’utilisateur commence par sélectionner un point de données dans votre visuel. Le visuel interagit avec Power BI et d’autres visuels en transmettant des sélections à l’hôte. L’utilisateur sélectionne ensuite « Ajouter » dans `Bookmark panel`, et Power BI enregistre les sélections actuelles pour le nouveau signet.

Cela se produit à plusieurs reprises lorsque l’utilisateur modifie la sélection et ajoute de nouveaux signets.
Une fois que les signets sont créés, l’utilisateur peut basculer entre eux.

Quand les utilisateurs sélectionnent un signet, Power BI restaure l’état de sélection ou de filtre enregistré et le transmet aux visuels. Les autres visuels sont mis en surbrillance ou filtrés en fonction de l’état stocké dans le signet. L’hôte Power BI est responsable des actions. Votre visuel est chargé de refléter correctement le nouvel état de sélection (par exemple, la couleur modifiée des points de données affichés).

Le nouvel état de sélection est communiqué au visuel par le biais de la méthode `update`. L’argument `options` doit contenir une propriété spéciale : `options.jsonFilters`. Il s’agit de la propriété JSONFilter, qui peut contenir `Advanced Filter` et `Tuple Filter`.

Le visuel doit restaurer les valeurs de filtre pour afficher l’état correspondant du visuel pour le signet sélectionné.

Vous pouvez également utiliser la méthode `registerOnSelectCallback` enregistrée d’appel de fonction de rappel spéciale de ISelectionManager, si le visuel utilise uniquement des sélections.

### <a name="visuals-with-selections"></a>Visuels avec sélections

Si vos visuels interagissent avec d’autres visuels à l’aide de [sélections](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md). Vous pouvez ajouter des signets de deux façons.

* Vous pouvez utiliser la méthode `FilterManager.restoreSelectionIds` si vous **n’avez pas utilisé [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** auparavant dans votre visuel.

* Si votre visuel utilise déjà **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** pour gérer des sélections. Vous devez utiliser la méthode `applySelectionFromFilter` dans l’instance de `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Utilisation de `ISelectionManager.registerOnSelectCallback`

Lorsqu’un utilisateur clique sur des signets, Power BI appelle la méthode `callback` du visuel avec des sélections correspondantes. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Supposons que vous ayez un point de données dans votre visuel créé avec la méthode [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

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

Vous avez donc `visualDataPoints` en tant que points de données et le tableau `ids`, qui sont transmis à la fonction `callback`.

À ce stade, le visuel doit comparer le tableau de `ISelectionId[]` avec les sélections indiquées dans votre tableau `visualDataPoints` et marquer les points de données correspondants comme étant sélectionnés.

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

Une fois que vous avez mis à jour les points de données, ils doivent refléter l’état de sélection actuel stocké dans l’objet `filter`. Ensuite, lorsque les points de données sont affichés, l’état de sélection du visuel personnalisé doit correspondre à l’état du signet.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Utilisation de `InteractivityService` pour le contrôle des sélections dans le visuel

Si votre visuel utilise `InteractivityService`, vous n’avez pas besoin d’actions supplémentaires pour prendre en charge des signets dans votre visuel.

L’utilitaire gère l’état de sélection du visuel lorsque l’utilisateur sélectionne des signets.

### <a name="visuals-with-filter"></a>Visuels avec filtre

Supposons que le visuel crée un filtre de données par plage de dates. Nous avons donc `startDate` et `endDate` comme début et fin de la plage.
Le visuel crée un filtre avancé et appelle la méthode hôte `applyJsonFilter` pour filtrer les données selon les conditions appropriées.
La `target` est la table de filtrage.

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

Chaque fois qu’un utilisateur clique sur un signet, le visuel personnalisé reçoit un appel `update`.

Le visuel personnalisé doit vérifier le filtre dans l’objet :

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Si l’objet `filter` n’est pas Null, le visuel doit restaurer les conditions de filtre à partir de celui-ci :

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

Après quoi, le visuel doit modifier son état interne (points de données et objets de visualisation [lignes, rectangles, etc.]) pour refléter les conditions actuelles.

> [!IMPORTANT]
> Dans le scénario des signets de rapport, le visuel ne doit pas appeler `applyJsonFilter` pour filtrer d’autres visuels ; ils doivent déjà être filtrés par Power BI.

Le visuel Timeline Slicer change le sélecteur de plage pour qu’il corresponde aux plages de données.

Pour plus d’informations, consultez l’article [Timeline Slicer repository](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df) (Référentiel Timeline Slicer).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>État du filtre pour enregistrer les propriétés visuelles dans les signets

La propriété `filterState` est une propriété d’une partie du filtrage. Le visuel peut stocker différentes valeurs dans les signets.

Pour enregistrer la valeur de la propriété en tant qu’état de filtre, la propriété de l’objet doit être marquée comme `"filterState": true` dans le fichier `capabilities.json`.

Exemple : `Timeline Slicer` stocke les valeurs de la propriété `Granularity` dans le filtre. Il permet également de modifier la granularité actuelle en fonction du changement des signets par utilisateur.

Pour plus d’informations, consultez l’article [Timeline Slicer repository](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334) (Référentiel Timeline Slicer).
