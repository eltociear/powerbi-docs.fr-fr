---
title: Introduction à l’utilisation des utilitaires de type dans un visuel Power BI
description: Cet article explique comment utiliser les utilitaires SVG pour étendre les types de base pour les visuels Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 5a3cfb7ea9c9f398193b45652aa43c6b83c8f70b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79377992"
---
# <a name="type-utils"></a>Utilitaires pour les types

TypeUtils est un ensemble de fonctions et de classes permettant d’étendre les types de base pour les visuels de Power BI.

## <a name="installation"></a>Installation

Pour installer le package, vous devez exécuter la commande suivante dans le répertoire avec votre visuel personnalisé actuel :

npm install powerbi-visuals-utils-typeutils --save Cette commande installe le package et ajoute un package en tant que dépendance à votre package.json

## <a name="double"></a>Double

`Double` fournit des possibilités de manipulation de la précision des nombres.

Le module fournit les fonctions suivantes :

### <a name="pow10"></a>pow10

Cette fonction retourne une puissance de 10.

```typescript
function pow10(exp: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Cette fonction retourne un logarithme de base 10 du nombre.

```typescript
function log10(val: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Cette fonction retourne une puissance de 10 représentant la précision du nombre.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Cette fonction vérifie si un delta entre deux nombres est inférieur à la précision fournie.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Cette fonction vérifie si la première valeur est inférieure à la deuxième valeur.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Cette fonction vérifie si la première valeur est inférieure ou égale à la deuxième valeur.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Cette fonction vérifie si la première valeur est supérieure à la deuxième valeur.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Cette fonction vérifie si la première valeur est supérieure ou égale à la deuxième valeur.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Cette fonction arrondit le nombre à l’entier inférieur ou égal avec la précision fournie.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Cette fonction `ceils` le nombre à l’entier supérieur ou égal avec la précision fournie.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Cette fonction arrondit le nombre vers le bas à la précision fournie.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Cette fonction `ceils` le nombre vers le haut à la précision fournie.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Cette fonction arrondit le nombre à la précision fournie.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Cette fonction retourne un nombre compris entre le minimum et le maximum.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Cette fonction arrondit le nombre.

```typescript
function round(x: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Cette fonction supprime le bruit décimal.

```typescript
function removeDecimalNoise(value: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Cette fonction vérifie si le nombre est un entier.

```typescript
function isInteger(value: number): boolean;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Cette fonction incrémente le nombre du nombre fourni et retourne le nombre arrondi.

```typescript
function toIncrement(value: number, increment: number): number;
```

Exemple :

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototype

`Prototype` fournit des possibilités d’héritage d’objets.

Le module fournit les fonctions suivantes :

## <a name="inherit"></a>inherit

Cette fonction retourne un nouvel objet avec l’objet fourni comme son prototype.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Exemple :

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Cette fonction retourne un nouvel objet avec l’objet fourni comme son prototype si et seulement si le prototype n’a pas été défini.

```typescript
function inheritSingle<T>(obj: T): T;
```

Exemple :

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` offre la possibilité de convertir des pixels en points et des points en pixels.

Le module fournit les fonctions suivantes :

## <a name="tostring"></a>toString

Cette fonction convertit la valeur de pixel en chaîne.

```typescript
function toString(px: number): string;
```

Exemple :

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Cette fonction convertit la valeur de point fournie en valeur de pixel et retourne l’interprétation en chaîne.

```typescript
function fromPoint(pt: number): string;
```

Exemple :

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Cette fonction convertit la valeur de point fournie en valeur de pixel.

```typescript
function fromPointToPixel(pt: number): number;
```

Exemple :

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Cette fonction convertit la valeur de pixel fournie en valeur de point.

```typescript
function toPoint(px: number): number;
```

Exemple :

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
