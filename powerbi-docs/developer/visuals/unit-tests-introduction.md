---
title: Présentation des tests unitaires
description: Comment écrire des tests unitaires pour un projet de visuel Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 4b16eaad9b541bf6e5d8df49ffda99d9bbd5bbf2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424536"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Didacticiel : ajouter des tests unitaires pour un projet de visuel Power BI

Ce didacticiel décrit les principes fondamentaux de l’écriture de tests unitaires pour vos visuels Power BI.

Dans ce didacticiel, nous allons aborder les sujets suivants :

* comment utiliser l’exécuteur de test karma.js, l’infrastructure de test - Jasmine.js
* comment utiliser le package powerbi-visuals-utils-testutils
* la façon dont les simulacres et les substituts permettent de simplifier les tests unitaires pour les visuels Power BI.

## <a name="prerequisites"></a>Conditions préalables

* Vous avez un projet de visuel Power BI
* Environnement Node.JS configuré

## <a name="install-and-configure-karmajs-and-jasmine"></a>Installer et configurer karma.js et jasmine

Ajoutez les bibliothèques requises dans package.json à la section `devDependencies` :

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

Pour en savoir plus sur le package, consultez la description ci-dessous.

Enregistrer `package.json` et exécuter sur la ligne de commande à l’emplacement `package.json` :

```cmd
npm install
```

Le gestionnaire de package installe tous les nouveaux packages ajoutés à `package.json`

Pour l’exécution de tests unitaires, nous devons configurer l’exécuteur d’essai et la configuration `webpack`. L’exemple de configuration que vous trouverez ici :

Exemple de `test.webpack.config.js` :

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

Exemple de `karma.conf.ts`

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

Vous pouvez modifier cette configuration si nécessaire.

Certains paramètres de `karma.conf.js` :

* La variable `recursivePathToTests` localise l’emplacement du code des tests.

* La variable `srcRecursivePath` localise le code JS de sortie après la compilation.

* La variable `srcCssRecursivePath` localise le CSS de sortie après la compilation d’un fichier avec des styles.

* La variable `srcOriginalRecursivePath` localise le code source de votre visuel.

* `coverageFolder` : la variable détermine l’emplacement où le rapport de couverture sera créé.

Certaines propriétés de configuration :

* `singleRun: true` : les tests s’exécutent sur le système d’intégration continue. Et c’est suffisant pour une seule fois.
Vous pouvez basculer vers `false` pour déboguer vos tests. Karma continuera d’exécuter le navigateur et vous permettra d’utiliser la console pour le débogage.

* `files: [...]` : dans ce tableau, vous pouvez définir des fichiers pour le chargement dans le navigateur.
En règle générale, il existe des fichiers sources, des cas de test, des bibliothèques (Jasmine, utilitaires d’essai). Vous pouvez ajouter à la liste d’autres fichiers si nécessaire.

* `preprocessors` : cette section de configuration vous permet de configurer les actions qui s’exécutent avant l’exécution des tests unitaires. Il existe une précompilation du code TypeScript vers JS et une préparation des fichiers de mappage source et la génération du rapport de couverture du code. Vous pouvez désactiver `coverage` pour déboguer vos tests. La couverture génère du code supplémentaire pour vérifier le code pour la couverture de test et complique le débogage des tests.

**Description de toutes les configurations que vous pouvez trouver dans la [documentation](https://karma-runner.github.io/1.0/config/configuration-file.html) de karma.js**

Pour une utilisation pratique, vous pouvez ajouter une commande de test dans `scripts` :

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

Vous êtes donc prêt à commencer l’écriture de vos tests unitaires.

## <a name="simple-unit-test-for-check-dom-element-of-the-visual"></a>Test unitaire simple pour vérifier l’élément DOM du visuel

Pour tester un visuel, nous devons créer une instance de visuel.

### <a name="creating-visual-instance-builder"></a>Création du générateur d’instances visuelles

Ajoutez un fichier `visualBuilder.ts` dans le dossier `test` avec le code suivant :

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

Il existe une méthode `build` pour créer une instance de votre visuel. `mainElement` est une méthode GET, qui retourne une instance de l’élément DOM « racine » dans votre visuel. L’accesseur Get est facultatif, mais il facilite l’écriture de tests unitaires.

Nous avons donc le générateur d’une instance de visuel. Écrivons le cas de test. Il s’agit d’un cas de test pour vérifier ces éléments SVG créés lors de l’affichage de votre visuel.

### <a name="creating-typescript-file-to-write-test-cases"></a>Création d’un fichier TypeScript pour écrire des cas de test

Ajoutez un fichier `visualTest.ts` pour les cas de test avec les codes suivants :

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

Plusieurs méthodes sont appelées.

* La méthode [`describe`](https://jasmine.github.io/api/2.6/global.html#describe) décrit un cas de test. Dans un contexte de l’infrastructure Jasmine, souvent appelée suite ou groupe de spécifications.

* La méthode `beforeEach` est appelée avant chaque appel de la méthode `it`, qui est défini à l’intérieur de la méthode [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach).

* `it` définit une spécification unique. La méthode [`it`](https://jasmine.github.io/api/2.6/global.html#it) doit contenir un ou plusieurs `expectations`.

* [`expect`](https://jasmine.github.io/api/2.6/global.html#expect) : la méthode crée une attente de spécification. Une spécification réussit si toutes les attentes réussissent sans aucun échec.

* `toBeInDOM` : l’une des méthodes de correspondance. Vous pouvez lire la [documentation](https://jasmine.github.io/api/2.6/matchers.html) de l’infrastructure Jasmine concernant les correspondances existantes.

**Pour en savoir plus sur l’infrastructure Jasmine dans la [documentation](https://jasmine.github.io/) officielle.**

Après cela, vous pouvez exécuter votre test unitaire en tapant une commande dans l’outil en ligne de commande.

Ce test vérifie que l’élément SVG racine des visuels est créé.

### <a name="launch-unit-tests"></a>Lancer des tests unitaires

Pour exécuter le test unitaire, vous pouvez taper cette commande dans l’outil en ligne de commande.

```cmd
npm run test
```

`karma.js` exécute le navigateur Chrome et exécute le cas de test.

![KarmaJS lancé dans Chrome](./media/karmajs-chrome.png)

> [!NOTE]
> Google Chrome doit être installé en local.

Dans la ligne de commande, vous obtenez la sortie suivante :

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>Comment ajouter des données statiques pour les tests unitaires

Créez un fichier `visualData.ts` dans le dossier `test`. Avec les codes suivants :

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

La classe `SampleBarChartDataBuilder` étend `TestDataViewBuilder` et implémente une méthode abstraite `getDataView`.

Lorsque vous placez des données dans des compartiments de champs de données, Power BI produit un objet `dataview` catégorique basé sur vos données.

![Compartiments classés](./media/fields-buckets.png)

Dans les tests unitaires, vous n’avez pas de fonctions principales Power BI pour les reproduire. Toutefois, vous devez mapper vos données statiques à un `dataview` catégorique. Et la classe `TestDataViewBuilder` vous aidera à le faire.

[En savoir plus sur DataViewMapping](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md)

Dans la méthode `getDataView`, vous appelez simplement la méthode `createCategoricalDataViewBuilder` avec vos données.

Dans [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) du visuel `sampleBarChart`, nous disposons des objets dataRoles et dataViewMapping :

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

Pour générer le même mappage, vous devez définir les paramètres suivants sur la méthode `createCategoricalDataViewBuilder` :

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

Où le groupe de catégories `this.valuesCategory`.

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

et un tableau de mesures `this.valuesMeasure` pour chaque catégorie. Exemple :

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

À présent, vous pouvez utiliser la classe `SampleBarChartDataBuilder` dans votre test unitaire.

Classe `ValueType` définie dans un package `powerbi-visuals-utils-testutils`. La méthode `createCategoricalDataViewBuilder` exige la bibliothèque `lodash`.

Ajoutez ces packages aux dépendances.

Dans `package.json` à la section `devDependencies`

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

Appeler

```cmd
npm install
```

pour installer la bibliothèque `lodash-es`.

À présent, vous pouvez réexécuter le test unitaire. Vous devez recevoir cette sortie

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

Et vous devez voir le navigateur Chrome démarré avec votre visuel.

![Lancements d’UT dans Chrome](./media/karmajs-chrome-ut-runned.png)

Le résumé de la couverture a augmenté. Ouvrez `coverage\index.html` pour en savoir plus sur la couverture du code en cours

![Index de couverture d’UT](./media/code-coverage-index.png)

Ou dans l’étendue du dossier `src`

![Couverture du dossier src](./media/code-coverage-src-folder.png)

Dans l’étendue du fichier, vous pouvez consulter le code source. L’utilitaire `Coverage` marque l’arrière-plan de la ligne en rouge si un code n’a pas été exécuté pendant l’exécution des tests unitaires.

![Couverture du code du fichier visual.ts](./media/code-coverage-visual-src.png)

> [!IMPORTANT]
> Mais la couverture du code ne signifie pas que vous avez une bonne couverture des fonctionnalités du visuel. Un simple test unitaire fourni plus de 96 % de couverture dans `src\visual.ts`.

## <a name="next-steps"></a>Étapes suivantes

Lorsque votre visuel est prêt, vous pouvez soumettre votre visuel pour publication.

[En savoir plus sur la publication de visuels dans AppSource](../office-store.md)
