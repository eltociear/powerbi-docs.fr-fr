---
title: Introduction à l’utilisation des utilitaires de test dans un visuel Power BI
description: Cet article explique comment utiliser les utilitaires de test pour simplifier les simulations et l’utilisation de méthodes spécifiques dans les tests unitaires pour les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196603"
---
# <a name="power-bi-visuals-test-utils"></a>Utilitaires de test des visuels Power BI

Cet article vous aide à installer, importer et utiliser les utilitaires de test des visuels Power BI. Ces utilitaires de test peuvent servir aux tests unitaires et incluent des simulations et des méthodes pour des éléments comme des vues de données, des sélections et des schémas de couleurs.

## <a name="requirements"></a>Configuration requise

Pour utiliser ce package, vous devez installer les éléments suivants :

* [node.js](https://nodejs.org), utiliser la version LTS est recommandé
* [npm](https://www.npmjs.com/), version 3.0.0 ou ultérieure
* Le package [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)

## <a name="installation"></a>Installation

Pour installer les utilitaires de test et ajouter sa dépendance à votre fichier *package.json*, exécutez la commande suivante à partir de votre répertoire des visuels Power BI :

```bash
npm install powerbi-visuals-utils-testutils --save
```

Voici des descriptions et des exemples sur l’API publique des utilitaires de test.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Utilisé par **VisualBuilder** dans les tests unitaires avec les méthodes les plus fréquemment utilisées `build`, `update` et `updateRenderTimeout`. 

La méthode `build` retourne une instance créée du visuel.

Les méthodes `enumerateObjectInstances` et `updateEnumerateObjectInstancesRenderTimeout` sont nécessaires pour vérifier les modifications apportées au compartiment et aux options de mise en forme.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Pour obtenir d’autres exemples, consultez [Écriture de tests unitaires VisualBuilderBase](./unit-tests-introduction.md#create-a-visual-instance-builder) et un [scénario VisualBuilderBase d’utilisation réelle](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Utilisé par **TestDataViewBuilder**, ce module fournit une classe **CategoricalDataViewBuilder** utilisée dans la méthode `createCategoricalDataViewBuilder`. Il spécifie également les interfaces et les méthodes nécessaires pour travailler avec une **DataView** simulée dans des tests unitaires.

* `withValues` ajoute des colonnes de séries statiques et `withGroupedValues` ajoute des colonnes de séries dynamiques

  N’appliquez pas à la fois des séries dynamiques et des séries statiques dans un visuel **DataViewCategorical**. Vous pouvez uniquement les utiliser tous les deux dans la requête **DataViewCategorical**, où **DataViewTransform** est supposé les fractionner en objets **DataViewCategorical** visuels distincts.

* `build` retourne la DataView avec des métadonnées et DataViewCategorical

  `build` retourne **Non défini** si la combinaison de paramètres n’est pas autorisée, comme inclure des séries dynamiques et des séries statiques lors de la génération de la **DataView** du visuel.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Utilisé pour la création de **VisualData** dans les tests unitaires. Quand des données sont placées dans des compartiments de champs de données, Power BI produit un objet **DataView** basé sur les données. Le **TestDataViewBuilder** permet de simuler la création d’une **DataView** de catégories.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Voici une liste des interfaces les plus fréquemment utilisées lors de la création d’une `testDataView` :

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Pour obtenir d’autres exemples, consultez [Écriture de tests unitaires TestDataViewBuilder](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) et un [scénario TestDataViewBuilder d’utilisation réelle](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Simulations

### <a name="mockivisualhost"></a>MockIVisualHost

Implémente **IVisualHost** pour tester des visuels Power BI sans dépendances externes, comme l’infrastructure Power BI.

Les méthodes pratiques sont les propriétés `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` et getter.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` crée et retourne une instance de **IVisualHost**, en fait **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Exemple
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** est une implémentation factice de **IVisualHost** et doit être seulement utilisée avec des tests unitaires.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implémente **IColorPalette** pour tester des visuels Power BI sans dépendances externes, comme l’infrastructure Power BI.

**MockIColorPalette** fournit des propriétés utiles pour vérifier le schéma de couleurs ou le mode de contraste élevé dans les tests unitaires.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` crée et retourne une instance de **IColorPalette**, en fait **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Exemple
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** est une implémentation factice de **IColorPalette** et doit être seulement utilisée avec des tests unitaires.

### <a name="mockiselectionid"></a>MockISelectionId

Implémente **ISelectionId** pour tester des visuels Power BI sans dépendances externes, comme l’infrastructure Power BI.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` crée et retourne une instance de **ISelectionId**, en fait **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Exemple
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** est une implémentation factice de **ISelectionId** et doit être seulement utilisée avec des tests unitaires.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implémente **ISelectionIdBuilder** pour tester des visuels Power BI sans dépendances externes, comme l’infrastructure Power BI. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` crée et retourne une instance de **ISelectionIdBuilder**, en fait **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Exemple
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** est une implémentation factice de **ISelectionIdBuilder** et doit être seulement utilisée avec des tests unitaires.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implémente **ISelectionManager** pour tester des visuels Power BI sans dépendances externes, comme l’infrastructure Power BI. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` crée et retourne une instance de **ISelectionManager**, en fait **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Exemple
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** est une implémentation factice de **ISelectionManager** et doit être seulement utilisée avec des tests unitaires.

### <a name="mockilocale"></a>MockILocale

  Définit les paramètres régionaux et les change pour vos besoins pendant le processus de test unitaire.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` crée et retourne une instance de **MockILocale**
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simule `TooltipService` et l’appelle pour vos besoins au cours du processus de test unitaire.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` crée et retourne une instance de **MockITooltipService**
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` crée et retourne une instance de **MockIAllowInteractions**
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Fournit les capacités de base de **LocalizationManager** nécessaires pour les tests unitaires.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` crée et retourne une instance de **ILocalizationManager**, en fait **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Exemple
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simule l’utilisation de **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Création de `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simule le travail de **AuthenticationService** en fournissant un jeton AAD simulé.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` crée et retourne une instance de **IAuthenticationService**, en fait **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Vous permet d’utiliser **ILocalVisualStorageService** avec le même comportement que **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` crée et retourne une instance de **ILocalVisualStorageService**, en fait **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` crée et retourne une instance de **IVisualEventService**, en fait **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utilitaires

Les utilitaires incluent des méthodes d’assistance pour les tests unitaires des visuels Power BI, notamment des assistances liées aux couleurs, aux nombres et aux événements.

- `renderTimeout` retourne le délai d’expiration
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` aide à définir la fixture dans les tests unitaires
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Exemple
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Méthodes d’assistance liées aux couleurs

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Retourne la structure est la suivante :

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` compare des objets **RgbColor** analysés à partir des chaînes d’entrée
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` analyse la couleur à partir de la chaîne d’entrée et la retourne dans une **RgbColor** d’interface spécifiée
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Méthodes d’assistance liées aux nombres

- `getRandomNumbers` génère un nombre aléatoire en utilisant une valeur minimale et une valeur maximale. Vous pouvez spécifier une `exceptionList` et fournir une fonction pour la modification du résultat.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` fournit un tableau de nombres aléatoires générés par la méthode `getRandomNumber` avec la valeur minimale et la valeur maximale spécifiées
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Méthodes d’assistance liées aux événements
Les méthodes suivantes sont écrites pour la simulation d’événements de page web dans les tests unitaires.

- `clickElement` simule un clic sur l’élément spécifié
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` retourne un objet **Touch** pour simuler un événement tactile
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` retourne une liste d’événements **Touch** simulés
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` retourne **MouseEvent**
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` crée et retourne **MouseEvent**
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Méthodes d’assistance liées aux événements D3

Les méthodes suivantes sont utilisées pour simuler des événements D3 dans des tests unitaires.

- `flushAllD3Transitions` force l’exécution de toutes les transitions D3

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalement, les transitions « zéro délai » sont exécutées après un délai instantané (< 10 ms), mais cela peut entraîner un bref scintillement si le navigateur restitue la page deux fois : une fois à la fin de la première boucle d’événements, puis de nouveau immédiatement sur le premier rappel du minuteur.
  >
  > Ces scintillements sont plus perceptibles sur IE et avec un grand nombre de vues web ; ils ne sont pas recommandés pour iOS.
  > 
  > En vidant la file d’attente du minuteur à la fin de la première boucle d’événements, vous pouvez exécuter immédiatement toutes les transitions « zéro délai » et éviter le scintillement.

Les méthodes suivantes sont également incluses :
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Interfaces d’assistance
L’interface et les énumérations suivantes sont utilisées dans la fonction d’assistance.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Étapes suivantes

Pour écrire des tests unitaires pour des visuels Power BI basés sur un webpack, et pour effectuer des tests unitaires avec `karma` et `jasmine`, consultez par exemple [Tutoriel : Ajouter des tests unitaires pour des projets de visuels Power BI](./unit-tests-introduction.md).
