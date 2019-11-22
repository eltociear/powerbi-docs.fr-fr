---
title: Utilitaires d’interactivité visuels Power BI
description: L'article décrit comment ajouter des sélections à des visuels Power BI en utilisant des utilitaires d’interactivité
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8a9218085b0da655d1ce4b3ece0b2666c4826c86
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061865"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Utilitaires d’interactivité visuels Microsoft Power BI

InteractivityUtils est un ensemble de fonctions et de classes visant à simplifier l'implémentation de la sélection croisée et du filtrage croisé pour les visuels personnalisés Power BI.

## <a name="installation"></a>Installation

> [!NOTE]
> Si vous continuez à utiliser l'ancienne version de powerbi-visuals-tools (numéro de version inférieur à 3.x.x), installez la nouvelle version des outils (3.x.x).

> [!IMPORTANT]
> Les nouvelles mises à jour des utilitaires d'interactivité ne prendront en charge que la dernière version des outils. [En savoir plus sur la mise à jour du code de vos visuels à utiliser avec les outils les plus récents](migrate-to-new-tools.md)

Pour installer le package, vous devez exécuter la commande suivante dans le répertoire avec votre visuel personnalisé actuel :

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

À partir de la version 3.0 ou ultérieure, vous devez également installer ```powerbi-models``` pour résoudre les dépendances.

```bash
npm install powerbi-models --save
```

Pour les utilitaires d’interactivité de l'utilisateur, vous devez importer le composant requis dans le code source du visuel.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Ajout d’artefacts CSS au visuel personnalisé

Pour utiliser le package avec vos visuels personnalisés, vous devez importer le fichier CSS suivant dans le fichier `your.less` :

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

En conséquence, vous obtenez la structure de fichiers suivante :

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Vous devriez importer le fichier .css en tant que fichier .css car Power BI Visuals Tools encapsule les règles CSS externes.

## <a name="usage"></a>Utilisation

### <a name="define-interface-for-data-points"></a>Définir l'interface pour les points de données

Les points de données contiennent généralement des sélections et des valeurs. L’interface étend l’interface `SelectableDataPoint`. `SelectableDataPoint` contient déjà des propriétés :

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

La première étape lors de l'utilisation des outils d'interactivité consiste à créer des instances d'outils d'interactivité et à sauvegarder l'objet comme une propriété du visuel

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

La seconde étape consiste à étendre la classe de comportement de base :

> [!NOTE]
> BaseBehavior introduit dans la version [5.6.x des utilitaires d'interactivité](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Si vous utilisez l'ancienne version, créez une classe de comportement à partir de l'exemple ci-dessous (la classe `BaseBehavior` est identique) :

Définissez l'interface pour les options de la classe de comportement :

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Définissez la classe pour `visual behaviour`. La classe chargée de gérer les événements de souris `click` et `contextmenu`.
Lorsque l’utilisateur clique sur des éléments de données, le visuel demande au gestionnaire de sélection de choisir des points de données. Ou d’effacer la sélection, si l'utilisateur clique sur un élément en arrière-plan du visuel. Et la classe comporte les méthodes correspondantes `bindClick`, `bindClearCatcher` et `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

ou vous pouvez étendre la classe `BaseBehavior` :

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Pour gérer le clic sur les éléments, appelez la méthode `on` de l'objet de sélection D3 (pour elementsSelection et clearCatcherSelection également) :

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Ajout d'un gestionnaire similaire pour l'événement `contextmenu` afin d’appeler la méthode `showContextMenu` du gestionnaire de sélection :

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Les utilitaires d’interactivité appellent les méthodes `bindEvents` pour assigner des fonctions aux gestionnaires, ajouter des appels de `bindClick`, `bindClearCatcher`,et `bindContextMenu` à la méthode `bindEvents` :

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

La méthode `renderSelection` chargée de la mise à jour de l'état des visuels des éléments du graphique.

L'échantillon de la méthode d’implémentation `renderSelection` :

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

La dernière étape est la création de l'instance de `visual behavior` et l'appel de la méthode `bind` de l’instance des utilitaires d'interactivité :

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` est un objet de sélection D3, qui représente tous les éléments sélectionnables sur le visuel.

* `select(this.target)` est l'objet de sélection D3, qui représente les éléments DOm principaux du visuel.

* Points de données `this.categories`, où l'interface est `VisualDataPoint` (ou `categories: VisualDataPoint[];`)

* `this.behavior` est une nouvelle instance de `visual behavior`

  créée dans le constructeur du visuel :

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Votre visuel est maintenant prêt pour la sélection du gestionnaire.

## <a name="next-steps"></a>Étapes suivantes

* [Découvrez comment gérer les sélections lors du changement de signets](bookmarks-support.md#visuals-with-selection)

* [Découvrez comment ajouter un menu contextuel pour les points de données de visuels](context-menu.md)

* [Découvrez comment utiliser le gestionnaire de sélection pour ajouter des sélections à des visuels Power BI](selection-api.md)
