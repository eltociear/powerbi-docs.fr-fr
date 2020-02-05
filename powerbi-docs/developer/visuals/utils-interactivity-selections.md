---
title: Utilitaires d’interactivité visuels Power BI
description: L'article décrit comment ajouter des sélections à des visuels Power BI en utilisant des utilitaires d’interactivité
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818683"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Utilitaires d’interactivité visuels Microsoft Power BI

InteractivityUtils est un ensemble de fonctions et de classes visant à simplifier l’implémentation de la sélection croisée et du filtrage croisé pour les visuels personnalisés Power BI.

## <a name="installation"></a>Installation

> [!NOTE]
> Si vous continuez à utiliser l’ancienne version de powerbi-visuals-tools (numéro de version inférieur à 3.x.x), installez la nouvelle version des outils (3.x.x).

> [!IMPORTANT]
> Les nouvelles mises à jour des utilitaires d’interactivité ne prendront en charge que la dernière version des outils. [Découvrez plus en détail comment mettre à jour le code de votre visuel à utiliser avec les outils les plus récents](migrate-to-new-tools.md)

Pour installer le package, vous devez exécuter la commande suivante dans le répertoire avec votre visuel personnalisé actuel :

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

À partir de la version 3.0 ou ultérieure, vous devez également installer ```powerbi-models``` pour résoudre les dépendances.

```bash
npm install powerbi-models --save
```

Pour les utilitaires d’interactivité de l’utilisateur, vous devez importer le composant requis dans le code source du visuel.

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
> Vous devez importer le fichier .css en tant que fichier .less, car Power BI Visuals Tools encapsule les règles CSS externes.

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

La première étape de l’emploi des utilitaires d’interactivité consiste à créer une instance de ces utilitaires et à enregistrer l’objet comme une propriété du visuel

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
> BaseBehavior introduit dans la version [5.6.x des utilitaires d'interactivité](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Si vous utilisez l’ancienne version, créez une classe de comportement à partir de l’exemple ci-dessous (la classe `BaseBehavior` est identique) :

Définissez l’interface pour les options de la classe de comportement :

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

Définissez une classe pour `visual behavior`. La classe est chargée de gérer les événements de souris `click` et `contextmenu`.
Quand un utilisateur clique sur des éléments de données, le visuel appelle le gestionnaire de sélection pour choisir des points de données. Si l’utilisateur clique sur l’élément en arrière-plan du visuel, il appelle le gestionnaire pour effacer la sélection. Et la classe comporte les méthodes correspondantes `bindClick`, `bindClearCatcher` et `bindContextMenu`.

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

Les utilitaires d’interactivité appellent les méthodes `bindEvents` pour assigner des fonctions aux gestionnaires, ajouter des appels de `bindClick`, `bindClearCatcher` et `bindContextMenu` à la méthode `bindEvents` :

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

La méthode `renderSelection` est chargée de la mise à jour de l’état visuel des éléments du graphique.

Exemple d’implémentation de la méthode `renderSelection` :

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

La dernière étape est la création d’une instance de `visual behavior` et l’appel de la méthode `bind` de l’instance des utilitaires d’interactivité :

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` est l’objet de sélection D3, qui représente tous les éléments sélectionnables sur le visuel.

* `select(this.target)` est l’objet de sélection D3, qui représente les principaux éléments DOM du visuel.

* `this.categories` sont des points de données avec des éléments, où l’interface est `VisualDataPoint` (ou `categories: VisualDataPoint[];`)

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

Votre visuel est maintenant prêt à gérer la sélection.

## <a name="next-steps"></a>Étapes suivantes

* [Découvrez comment gérer les sélections lors du changement de signets](bookmarks-support.md#visuals-with-selection)

* [Découvrez comment ajouter un menu contextuel pour les points de données de visuels](context-menu.md)

* [Découvrez comment utiliser le gestionnaire de sélection pour ajouter des sélections à des visuels Power BI](selection-api.md)
