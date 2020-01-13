---
title: Introduction à l’utilisation des utilitaires SVG dans un visuel Power BI
description: Cet article explique comment utiliser les utilitaires SVG afin de simplifier les manipulations SVG pour les visuels personnalisés Power BI
author: vtkalek
ms.author: asander
manager: asander
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 15398c0e8d7322e29c502f49b8c1ea0798f52afe
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75308522"
---
# <a name="svg-utils"></a>Utilitaires pour les SVG

Les utilitaires SVG sont un ensemble de fonctions et de classes permettant de simplifier les manipulations SVG pour les visuels personnalisés Power BI

## <a name="installation"></a>Installation

Pour installer le package, vous devez exécuter la commande suivante dans le répertoire contenant votre visuel actuel :

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

Le module `CssConstants` fournit la fonction et l’interface spéciales permettant de travailler avec des sélecteurs de classe.

Le module `powerbi.extensibility.utils.svg.CssConstants` fournit la fonction et l’interface suivantes :

## <a name="classandselector"></a>ClassAndSelector

Cette interface décrit les propriétés communes du sélecteur de classe.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Cette fonction crée une instance de ClassAndSelector avec le nom donné de la classe.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Exemple :

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` fournit des fonctions spéciales permettant de générer des chaînes à utiliser avec la propriété transform SVG.

Le module fournit les fonctions suivantes :

### <a name="translate"></a>translate

Cette fonction crée une chaîne de traduction (translate) à utiliser avec la propriété transform SVG.

```typescript
function translate(x: number, y: number): string;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Cette fonction crée une chaîne translateX à utiliser avec la propriété transform SVG.

```typescript
function translateXWithPixels(x: number): string;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Cette fonction crée une chaîne de traduction (translate) à utiliser avec la propriété transform SVG.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Cette fonction crée une chaîne de traduction-rotation (translate-rotate) à utiliser avec la propriété transform SVG.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Cette fonction crée une chaîne de mise à l’échelle (scale) à utiliser dans une propriété transform CSS.

```typescript
function scale(scale: number): string;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Cette fonction crée une chaîne de transformation d’origine (transform-origin) à utiliser dans une propriété transform-origin CSS.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Cette fonction force l’exécution de chaque transition de D3.

```typescript
function flushAllD3Transitions(): void;
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Cette fonction analyse la chaîne de transformation (transform) avec la valeur « translate(x,y) ».

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Cette fonction crée une flèche.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Exemple :

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

Le module `Rect` fournit des fonctions spéciales pour manipuler les rectangles.

Le module fournit les fonctions suivantes :

### <a name="getoffset"></a>getOffset

Cette fonction retourne un décalage du rectangle.

```typescript
function getOffset(rect: IRect): IPoint;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Cette fonction retourne la taille du rectangle.

```typescript
function getSize(rect: IRect): ISize;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Cette fonction modifie la taille du rectangle.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Cette fonction retourne une position droite du rectangle.

```typescript
function right(rect: IRect): number;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Cette fonction retourne une position inférieure du rectangle.

```typescript
function bottom(rect: IRect): number;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Cette fonction retourne une position en haut à gauche du rectangle.

```typescript
function topLeft(rect: IRect): IPoint;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Cette fonction retourne une position en haut à droite du rectangle.

```typescript
function topRight(rect: IRect): IPoint;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Cette fonction retourne une position en bas à gauche du rectangle.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Cette fonction retourne une position en bas à droite du rectangle.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Exemple

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Cette fonction crée une copie du rectangle.

```typescript
function clone(rect: IRect): IRect;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Cette fonction convertit le rectangle en chaîne.

```typescript
function toString(rect: IRect): string;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Cette fonction applique un décalage donné au rectangle.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Cette fonction ajoute le premier rectangle au deuxième rectangle.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Cette fonction retourne le point le plus proche du rectangle au point donné.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Cette fonction compare les rectangles et retourne la valeur true s’ils sont identiques.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Cette fonction compare les rectangles en prenant en compte la précision des valeurs.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Cette fonction vérifie si le rectangle est vide.

```typescript
function isEmpty(rect: IRect): boolean;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Cette fonction vérifie si le rectangle contient le point.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Cette fonction vérifie si les rectangles s’entrecoupent.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Cette fonction retourne une intersection de rectangles.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Cette fonction combine des rectangles.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Cette fonction retourne un point central du rectangle.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Exemple :

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>pointeur

Le module `pointer` fournit une fonction spéciale permettant d’obtenir la position du pointeur.

Le module fournit la fonction suivante :

### <a name="getcoordinates"></a>getCoordinates

Cette fonction retourne la position du pointeur.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Exemple :

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
