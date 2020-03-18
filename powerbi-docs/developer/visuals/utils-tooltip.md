---
title: Introduction à l’utilisation des info-bulles dans un visuel Power BI
description: Cet article décrit comment utiliser des utilitaires pour les info-bulles afin de simplifier la personnalisation des visuels Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 67470ec405806f44fdb483e857d222ad4ff05a45
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379165"
---
# <a name="tooltip-utils"></a>Utilitaires pour les info-bulles
Cet article va vous aider à installer, à importer et à utiliser les utilitaires pour les info-bulles. Cet utilitaire est utile pour toute personnalisation des info-bulles dans les visuels Power BI.

## <a name="requirements"></a>Configuration requise
Pour utiliser le package, vous avez besoin de ce qui suit :
* [node.js](https://nodejs.org) (nous vous recommandons de télécharger la version la plus récente de LTS)
* [npm](https://www.npmjs.com/) (la version la plus ancienne prise en charge est 3.0.0)
* Le visuel personnalisé créé par [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installation

Pour installer le package, vous devez exécuter la commande suivante dans le répertoire contenant votre visuel actuel :

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Cette commande installe le package et ajoute un package comme dépendance á votre ```package.json```

## <a name="usage"></a>Utilisation

> Le guide d’utilisation décrit une API publique du package. Vous trouverez une description et quelques exemples de chaque interface publique du package.

Ce contenu de package vous permet de créer `TooltipServiceWrapper` et des méthodes pour aider à gérer des actions d’info-bulles. Il utilise les interfaces de l’info-bulle : `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Il comporte également des méthodes spécifiques (gestionnaires d’événements tactiles) relatives au développement mobile : `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` fournit la méthode la plus simple pour manipuler les info-bulles.

Le module fournit l’interface et la fonction suivantes :
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [masquer](#itooltipservicewrapperhide)

* [Interfaces](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Événements tactiles](#touch-events)

### `createTooltipServiceWrapper`
Cette fonction crée une instance de ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

Le ```ITooltipService``` est disponible dans [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Exemple**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

Vous pouvez examiner l’exemple de code du visuel personnalisé [ici](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391).

### `ITooltipServiceWrapper`
Cette interface décrit les méthodes publiques de TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Cette méthode ajoute des info-bulles à la sélection actuelle.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Exemple**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

Vous pouvez examiner l’exemple de code du visuel personnalisé [ici](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931).

Tenez également compte de l’exemple suivant de personnalisation des info-bulles dans le visuel personnalisé Gantt [ici](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)

### `ITooltipServiceWrapper.hide`

Cette méthode masque l’info-bulle.

```typescript
hide(): void;
```

**Exemple**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Cette interfaces est utilisée pendant la création et l’utilisation de TooltipServiceWrapper. Elles ont également été mentionnées dans les exemples de la rubrique précédente [ici](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

L’info-bulle est maintenant capable de gérer plusieurs événements tactiles utiles pour le développement mobile.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Cette méthode retourne le nom de l’événement tactile de départ.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Cette méthode retourne le nom de l’événement tactile de départ.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Cette méthode indique si l’événement touchStart est lié ou non au pointeur.
