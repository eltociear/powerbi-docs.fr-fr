---
title: Utilitaires d’interactivité visuels Power BI
description: L'article décrit comment ajouter des sélections à des visuels Power BI en utilisant des utilitaires d’interactivité
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379257"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Utilitaires d’interactivité visuels Power BI

Les Utilitaires d’interactivité (`InteractivityUtils`) sont un ensemble de fonctions et de classes pouvant être utilisés pour simplifier l’implémentation de la sélection croisée et du filtrage croisé.

> [!NOTE]
> Les nouvelles mises à jour des utilitaires d’interactivité ne prennent en charge que la dernière version des outils (version 3.x.x et ultérieures).

## <a name="installation"></a>Installation

1. Pour installer le package, exécutez la commande suivante dans le répertoire contenant votre projet visuel Power BI actuel.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Si vous utilisez la version 3.0 ou une version ultérieure, ou l’outil, installez `powerbi-models` pour résoudre les dépendances.

    ```bash
    npm install powerbi-models --save
    ```

3. Pour utiliser les utilitaires d’interactivité, importez le composant requis dans le code source du visuel Power BI.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Inclusion des fichiers CSS

Pour utiliser le package avec votre visuel Power BI, importez le fichier CSS suivant dans votre fichier `.less`.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importez le fichier CSS sous la forme d’un fichier `.less`, car l’outil des visuels Power BI encapsule les règles CSS externes.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>Propriétés SelectableDataPoint

Les points de données contiennent généralement des sélections et des valeurs. L’interface étend l’interface `SelectableDataPoint`.

`SelectableDataPoint` contient déjà des propriétés comme décrit ci-dessous.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Définition d’une interface pour les points de données

1. Créer une instance des utilitaires d’interactivité et enregistrer l’objet en tant que propriété du visuel

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

2. Étendez la classe de comportement de base.

    > [!NOTE]
    > `BaseBehavior` a été introduit dans la [version 5.6.x des utilitaires d’interactivité](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Si vous utilisez une version plus ancienne, créez une classe de comportement à partir de l’exemple ci-dessous.

3. Définissez l’interface pour les options de la classe de comportement.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Définissez une classe pour `visual behavior`. Ou, étendez la classe `BaseBehavior`.

    **Définition d’une classe pour `visual behavior`**

    La classe est chargée de gérer les événements de souris `click` `contextmenu`.

    Quand un utilisateur clique sur des éléments de données, le visuel appelle le gestionnaire de sélection pour choisir des points de données. Si l’utilisateur clique sur l’élément en arrière-plan du visuel, il appelle le gestionnaire pour effacer la sélection.

    La classe comporte les méthodes correspondantes suivantes :
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **Extension de la classe `BaseBehavior`**

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

5. Pour gérer le clic sur les éléments, appelez la méthode `on` d’objet de sélection *d3*. Cela vaut également pour `elementsSelection` et `clearCatcherSelection`.

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

6. Ajoutez un gestionnaire similaire pour l'événement `contextmenu` afin d’appeler la méthode `showContextMenu` du gestionnaire de sélection.

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

7. Pour assigner des fonctions aux gestionnaires, les utilitaires d’interactivité appellent la méthode `bindEvents`. Ajoutez les appels suivants à la méthode `bindEvents` :
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. La méthode `renderSelection` est chargée de la mise à jour de l’état visuel des éléments du graphique. Voici un exemple d’implémentation de `renderSelection`.

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

9. La dernière étape est la création d’une instance de `visual behavior` et l’appel de la méthode `bind` de l’instance des utilitaires d’interactivité.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` est l’objet de sélection *d3*, qui représente tous les éléments sélectionnables du visuel.
    * `select(this.target)` est l’objet de sélection *d3*, qui représente les éléments DOM principaux du visuel.
    * `this.categories` sont des points de données avec des éléments, où l’interface est `VisualDataPoint` ou `categories: VisualDataPoint[];`.
    * `this.behavior` est une nouvelle instance de `visual behavior` créée dans le constructeur du visuel, comme illustré ci-dessous.

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
## <a name="next-steps"></a>Étapes suivantes

* [Découvrez comment gérer les sélections lors du changement de signets](bookmarks-support.md#visuals-with-selection)

* [Découvrez comment ajouter un menu contextuel pour les points de données de visuels](context-menu.md)

* [Découvrez comment utiliser le gestionnaire de sélection pour ajouter des sélections à des visuels Power BI](selection-api.md)
