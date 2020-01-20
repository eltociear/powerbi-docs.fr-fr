---
title: Migration vers powerbi-visuals-tools version 3.x
description: Prise en main de la nouvelle version de powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1b819aeb0f59df9ee0d48d7c41807abe62efed08
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885148"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migrer vers la nouvelle version 3.*x* de powerbi-visuals-tools

À partir de la version 3, Power BI Visuals Tools (powerbi-visuals-tools, ou `pbiviz`) utilise webpack pour créer des visuels personnalisés.
La nouvelle version offre aux développeurs de nombreuses améliorations pour la création de visuels :

- TypeScript version 3.*x* est utilisé par défaut. À partir de TypeScript 1.5, la nomenclature a changé. [En savoir plus sur les modules TypeScript](https://www.typescriptlang.org/docs/handbook/modules.html).

- Les modules ES6 (ECMAScript 6) sont pris en charge. Utilisez maintenant les importations ES6 au lieu d’[externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Les nouvelles versions de D3v5 ([Data-Driven Documents](https://d3js.org/)) et d’autres bibliothèques basées sur des modules ES6 sont prises en charge.

- Taille de package réduite. [Tree shaking](https://webpack.js.org/guides/tree-shaking/) permet à webpack de supprimer le code inutilisé. Le code JavaScript est ainsi réduit et vous obtenez de meilleures performances dans le chargement des visuels.

- Performances API améliorées.

- La bibliothèque Globalize.js [est intégrée](migrate-to-new-tools.md#remove-the- globalizejs-library) aux utilitaires FormattingUtils.

- Power BI Visuals Tools utilise [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) pour afficher la base de code du visuel.

Cet article décrit toutes les étapes de la migration pour la nouvelle version de Power BI Visuals Tools.

## <a name="backward-compatibility"></a>Compatibilité descendante

Les nouveaux outils enregistrent les informations sur la compatibilité descendante pour l’ancienne base de code des visuels, mais peuvent nécessiter quelques modifications supplémentaires pour charger des bibliothèques externes.

Les bibliothèques qui prennent en charge les systèmes de modules sont importées sous forme de modules webpack. Toutes les autres bibliothèques et le code source du visuel sont regroupés dans un même module.

Les variables globales comme JQuery et Lodash qui étaient utilisées dans les outils Power BI Visuals Tools précédents sont maintenant obsolètes. Si l’ancien code de votre visuel s’appuie sur des variables globales, le visuel ne fonctionnera probablement pas avec les nouveaux outils.

La version précédente de Power BI Visuals Tools vous demandait de définir une classe visuelle sous le module `powerbi.extensibility.visual`. Avec la nouvelle version des outils, vous devez définir à la place une classe visuelle dans le fichier TypeScript (.ts) principal. En règle générale, ce fichier est `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Installer powerbi-visuals-tools

Exécutez cette commande pour installer les nouveaux outils :

```cmd
npm install -g powerbi-visuals-tools
```

Le code suivant provient du fichier `package.json` dans le [référentiel visuel sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), une fois que le projet visuel a été mis à jour pour utiliser les nouveaux outils :

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Installer l’API des visuels personnalisés Power BI

La nouvelle version de powerbi-visuals-tools n’inclut pas toutes les versions de l’API. Au lieu de cela, vous devez installer une version spécifique du package [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api). Choisissez la version du package qui correspond à la version d’API de vos visuels personnalisés Power BI. Le package fournit toutes les définitions de type pour l’API des visuels personnalisés Power BI.

Ajoutez `powerbi-visuals-api` aux dépendances d’un projet en exécutant la commande suivante :

```cmd
npm install --save-dev powerbi-visuals-api
```

Supprimez également tous les liens vers les anciennes définitions de type d’API, car webpack intègre automatiquement les types de `powerbi-visuals-api`. Les modifications correspondantes se trouvent dans [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) et [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Mettre à jour tsconfig.json

Pour utiliser des modules externes, remplacez l’option `out` par `outDir`. Par exemple, utilisez `"outDir": "./.tmp/build/",` au lieu de `"out": "./.tmp/build/visual.js",`.

Cette modification est nécessaire, car les fichiers TypeScript seront indépendamment compilés en fichiers JavaScript. C’est pourquoi vous n’avez plus besoin de spécifier le fichier visual.js comme sortie.

Vous pouvez également remplacer l’option `target` par `ES6` si vous voulez utiliser JavaScript moderne comme sortie. Cette modification est [facultative](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Mettre à jour les utilitaires de visuels personnalisés

Si vous utilisez l’un des packages [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils), vous devez également le mettre à jour vers la dernière version. Pour ce faire, exécutez la commande suivante :

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Par exemple, pour obtenir la nouvelle version avec les modules externes de TypeScript, exécutez : 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Pour obtenir un exemple d’un visuel qui utilise tous les packages `powerbi-visuals-utils`, consultez le [référentiel MekkoChart](https://github.com/Microsoft/powerbi-visuals-mekkochart).

## <a name="remove-the-globalizejs-library"></a>Supprimer la bibliothèque Globalize.js

La nouvelle version de [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) comprend Globalize.js. Vous n’avez donc pas besoin d’inclure cette bibliothèque manuellement dans votre projet. Toutes les localisations requises seront automatiquement ajoutées au package final.

## <a name="configure-loading-of-external-libraries"></a>Configurer le chargement des bibliothèques externes

Incluez les nouveaux fichiers JavaScript après les bibliothèques dans le tableau `externalJS` de `pbiviz.json`. Par exemple :

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importez les bibliothèques dans votre code source. Par exemple, pour `lodash-es`, utilisez l’instruction suivante :

```JS
import * as _ from "lodash-es";
```

Dans l’exemple précédent, `_` est la variable globale pour la bibliothèque `lodash`.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Apporter des modifications dans les sources de vos visuels

La principale modification que vous devez effectuer consiste à convertir les modules internes en modules externes. Vous ne pouvez pas utiliser des modules externes dans des modules internes.

Voici une description détaillée des modifications à apporter. Les modifications sont décrites dans le contexte de l’exemple de code de visuel personnalisé BarChart :

1. Supprimez toutes les définitions de modules de chaque fichier de [code source](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3) :

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importez les définitions de l’API des visuels personnalisés Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4) :

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importez les interfaces ou classes nécessaires](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) à partir du module interne `powerbi`.

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

4. [Importez la bibliothèque D3.js](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2) :

    ```typescript
    import * as d3 from "d3";
    ```

    Sinon, importez uniquement les modules nécessaires de la bibliothèque D3 :

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importez des utilitaires, classes et interfaces définis dans le projet visuel](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) vers le fichier source principal :

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

La nouvelle version des outils vous permet d’importer des styles `CSS` et `Less` directement dans le code TypeScript. La [section styles](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) qui était utilisée précédemment est désormais ignorée par le compilateur.

Pour utiliser votre feuille de style, ouvrez le fichier TypeScript (.ts) principal et ajoutez la ligne suivante :  

```typescript
import "./../style/visual.less";
```  

Vos styles `CSS` et `Less` seront automatiquement compilés.

### <a name="externaljs-section-in-pbivizjson"></a>Section externalJS dans pbiviz.json

Les outils [ne nécessitent pas une liste de bibliothèques `externalJS`](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) à charger dans le bundle visuel, car webpack comprend toutes les bibliothèques importées.

> [!NOTE]
> Dans `pbiviz.json`, laissez la section `externalJS` vide.

Utilisez la commande classique `npm run package` pour créer le package visuel ou `npm run start` pour démarrer le serveur de développement.

## <a name="update-the-d3js-library-to-version-5"></a>Mettre à jour la bibliothèque D3.js vers la version 5

Les nouveaux outils Visuals Tools vous permettent de commencer à utiliser la nouvelle version de la bibliothèque D3.js. Exécutez les commandes suivantes pour mettre à jour D3 dans votre projet visuel :

- `npm install --save d3@5` pour installer la nouvelle bibliothèque D3.js.

- `npm install --save-dev @types/d3@5` pour installer les nouvelles définitions de type pour D3.js.

> [!IMPORTANT]
> D3 version 5 introduit plusieurs changements cassants.

Modifiez votre code pour utiliser la nouvelle bibliothèque D3.js :

- L’interface `d3.Selection<T>` [a été remplacée](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) par `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Vous ne pouvez pas appliquer plusieurs attributs à l’aide d’un seul appel à la méthode `attr`. Au lieu de cela, vous devez [passer chaque attribut dans un appel séparé](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) à `attr`. Effectuez également [des appels séparés à la méthode `style`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- D3.js version 4 a introduit la nouvelle méthode `merge`. Cette méthode est couramment utilisée pour fusionner des sélections `enter` et `update` après une opération de jointure de données. Pour utiliser D3 correctement, [appelez la méthode `merge`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Découvrez-en plus](https://github.com/d3/d3/blob/master/CHANGES.md) sur les changements dans la bibliothèque D3.js.

## <a name="install-babel-and-core-js"></a>Installer Babel et core-js

À partir de la version 3.1, les outils Visuals Tools utilisent Babel pour compiler le code JavaScript moderne en ancien module ES5 (ECMAScript 5) afin de prendre en charge une large gamme de navigateurs.

L’option Babel est activée par défaut, mais vous devez importer manuellement le package [`core-js`](https://www.npmjs.com/package/core-js). Exécutez cette commande pour installer le package :

```cmd
npm install --save core-js
```

Ensuite, importez le package au point de départ du code visuel. En général, il s’agit du fichier « src/visual.ts ».

```JS
import "core-js/stable";
```

En savoir plus sur Babel [dans la documentation](https://babeljs.io/docs/en/).
