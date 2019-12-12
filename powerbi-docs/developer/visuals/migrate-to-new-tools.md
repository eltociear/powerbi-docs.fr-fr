---
title: Migrer vers powerbi-visuals-tools 3.x
description: Démarrage avec la nouvelle version de powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 245475feeb43ee544117aaa54969f2de1e207cd5
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696279"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migrer vers la nouvelle version de powerbi-visuals-tools 3.x.x

À partir de la version 3, Power BI Visuals Tools utilise Webpack pour créer des visuels personnalisés.
La nouvelle version offre de nombreuses nouvelles possibilités aux développeurs pour créer des visuels :

* TypeScript v3.x.x par défaut. À partir de TypeScript 1.5, la nomenclature a été modifiée. [En savoir plus sur les modules TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

* Les modules ES6 sont pris en charge. Plus besoin d'utiliser [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries), utilisez plutôt les importations ES6.

* Les nouvelles versions de [D3v5](https://d3js.org/) et d'autres bibliothèques basées sur des modules ES6 sont prises.

* Taille de package réduite. Webpack utilise [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) pour supprimer le code inutilisé. Il réduit le code de JS et, par conséquent, vous obtenez de meilleures performances lors du chargement d’un visuel.

* Performances API améliorées.

* La bibliothèque Globalize.js [est intégrée](migrate-to-new-tools.md#remove-globalizejs-library) aux utilitaires de formatage.

* Tools utilise [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) pour afficher la base de code du visuel.

Toutes les étapes de la migration pour la nouvelle version de Power BI Visuals Tools sont décrites ci-dessous.

## <a name="backward-compatibility"></a>Compatibilité descendante

Les nouveaux outils assurent la compatibilité descendante pour l’ancienne base de code des visuels, mais peuvent nécessiter quelques modifications supplémentaires pour charger des bibliothèques externes.

Les bibliothèques, qui prennent en charge les systèmes de modules, seront importées sous forme de modules Webpack. Toutes les autres bibliothèques et le code source du visuel seront regroupés dans un même module.

Les variables globales comme JQuery et Lodash qui étaient utilisées dans les outils pbiviz précédents sont maintenant obsolètes. Cela signifie que si l'ancien code du visuel s'appuie sur des variables globales, ce visuel risque d’être tronqué dans ce cas.

La version précédente de Power BI Visuals Tools nécessaire pour définir une classe visuelle sous le module `powerbi.extensibility.visual`.

## <a name="how-to-install-powerbi-visuals-tools"></a>Comment installer powerbi-visuals-tools

Les nouveaux outils peuvent être installés en exécutant la commande

```cmd
npm install -g powerbi-visuals-tools
```

Exemple de visuel sampleBarChart visuel et [changements](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) correspondants dans `package.json` :

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Comment installer l'API des visuels personnalisés Power BI ?

La nouvelle version de powerbi-visual-tools n’inclut pas toutes les versions de l’API. Par conséquent, le développeur devra installer une version spécifique du package [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api). La version du package correspond à la version de l’API des visuels personnalisés Power BI et fournit toutes les définitions de type pour cette API.

Ajoutez `powerbi-visuals-api` aux dépendances d’un projet en exécutant la commande `npm install --save-dev powerbi-visuals-api`.
Vous devez supprimer le lien vers les anciennes définitions de type d'API, car les types de `powerbi-visuals-api` sont automatiquement inclus par Webpack. Les changements correspondants figurent dans [cette](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) ligne de `package.json`.

## <a name="update-tsconfigjson"></a>Mettre à jour `tsconfig.json`

Pour utiliser des modules externes, vous devez basculer l'option `out` sur `outDir`.
`"outDir": "./.tmp/build/",` à la place de `"out": "./.tmp/build/visual.js",`.

Cette opération est nécessaire car les fichiers TypeScript seront indépendamment compilés dans des fichiers JavaScript. C'est pourquoi vous n'avez plus besoin de spécifier le fichier visual.js comme sortie.

Vous pouvez également remplacer l’option `target` par `ES6` si vous voulez utiliser JavaScript moderne comme sortie. [Ceci est facultatif](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Mettre à jour les utilitaires de visuels personnalisés

Si vous utilisez l’un des utilitaires powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), vous devez également les mettre à jour vers la dernière version.

Exécutez la commande `npm install powerbi-visuals-utils-<UTILNAME> --save`. (Ex. `npm install powerbi-visuals-utils-dataviewutils --save`) pour obtenir la nouvelle version avec les modules externes de TypeScript.

Vous trouverez un exemple dans le [référentiel](https://github.com/Microsoft/powerbi-visuals-mekkochart) MekkoChart.
Ce visuel utilise tous les utilitaires.

## <a name="remove-globalizejs-library"></a>Supprimer la bibliothèque Globalize.js

La nouvelle version de [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) comprend global. js prêt à l’emploi.
Vous n'avez pas besoin d'inclure cette bibliothèque manuellement dans le projet.
Toutes les localisations requises seront automatiquement ajoutées au package final.

## <a name="fix-loading-external-libraries"></a>Correction du chargement de bibliothèques externes

Incluez plutôt le nouveau fichier JS après les bibliothèques dans le tableau `externalJS` de `pbiviz.json`. Exemple :

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importez les bibliothèques dans les sources. Exemple pour `lodash-es` :

```JS
import * as _ from "lodash-es";
```

où `_` est la variable globale pour la bibliothèque `lodash`.

## <a name="changes-in-the-visuals-sources"></a>Changements dans les sources de visuels

Le principal changement consiste à convertir les modules internes en modules externes car vous ne pouvez pas utiliser les modules externes dans les modules internes.

Ces changements décrivent les modifications qui ont été apportées à l'exemple de graphique à barres

Des descriptions détaillées des changements sont présentées ci-dessous :

1. Supprimer toutes les définitions de modules de chaque fichier de [code source](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importer des définitions d'API de visuels personnalisées Power BI](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) les interfaces ou classes nécessaires à partir du module interne `powerbi`.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) la bibliothèque D3.js

    ```typescript
    import * as d3 from "d3";
    ```

    Ou importer uniquement les modules de la bibliothèque d3 requis

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) des utilitaires, classes, interfaces définies dans le projet visuel vers le fichier source principal

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importer des styles CSS

La nouvelle version des outils permet aux développeurs d'importer un style CSS, LESS directement dans le code TypeScript.

Ainsi, la [section styles](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) précédemment utilisée sera ignorée par un compilateur.

Pour utiliser votre feuille de style, ouvrez le fichier ts principal et ajoutez la ligne suivante :  

```typescript
import "./../style/visual.less";
```  

Vos styles CSS, LESS seront automatiquement compilés.  

### <a name="externaljs-section-in-pbivizjson"></a>Section externalJS dans pbiviz.json

Les outils [n'ont pas besoin](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) d'une liste de `externalJS` pour se charger dans le bundle visuel. Parce que webpack inclut toutes les bibliothèques importées.

**La section externalJS dans pbivi.json devrait être vide.**

Appelez les commandes typiques `npm run package` pour créer le package visuel ou `npm run start` pour démarrer le serveur dev.

## <a name="updating-d3js-library-to-version-5"></a>Mise à jour de la bibliothèque D3.js vers la version 5

De nouveaux outils vous permettent de commencer à utiliser la nouvelle version de la bibliothèque D3.js.

Commandes d'appel pour mettre à jour D3 dans votre projet visuel

`npm install --save d3@5` pour installer la nouvelle bibliothèque D3.js.

`npm install --save-dev @types/d3@5` pour installer les nouvelles définitions de type pour D3.js.

Il existe plusieurs changements importants et vous devez modifier votre code pour utiliser la nouvelle bibliothèque D3.js.

1. L’interface `d3.Selection<T>` [a été remplacée](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) par `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. Vous ne pouvez pas appliquer plusieurs attributs à l’aide d’un seul appel de la méthode `attr`. Vous [devez passer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) chaque attribut dans un appel différent de la méthode `attr`. C'est [également](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) le cas pour la méthode `style`.

3. Dans D3.js v4, la nouvelle méthode de fusion est introduite. Cette méthode est couramment utilisée pour fusionner la saisie et mettre à jour des sélections après une fusion de données. [Appelez la méthode de fusion](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) pour utiliser correctement d3.

[En savoir plus](https://github.com/d3/d3/blob/master/CHANGES.md) sur les changements dans la bibliothèque D3.js.

## <a name="babel"></a>Babel

À partir de la version 3.1, les outils utilisent Babel pour compiler le nouveau code JS moderne dans l’ancien ES5 afin de prendre en charge une large gamme de navigateurs.

Cette option est activée par défaut, mais vous devez importer manuellement le package [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill).

Exécutez la commande pour installer le package

`npm install --save @babel/polyfill`

et importez le package au point de départ du code visuel (en général le fichier src/visual.ts) :

`import "@babel/polyfill";`

En savoir plus sur Babel [dans la documentation](https://babeljs.io/docs/en/).

Enfin, exécutez [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) pour afficher la base de code du visuel.  

![Statistiques de code du visuel](./media/webpack-stats.png)
