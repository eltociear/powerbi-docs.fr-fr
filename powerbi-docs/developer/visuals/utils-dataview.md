---
title: Introduction à l’utilisation des utilitaires de vue des données dans un visuel Power BI
description: Cet article décrit comment utiliser des utilitaires SVG pour simplifier l’analyse de l’objet DataView pour les visuels Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 79ad33a632a1f4935f462bcde0d36f2ccc55a2bd
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818982"
---
# <a name="dataviewutils"></a>DataViewUtils

`DataViewUtils` est un ensemble de fonctions et de classes permettant de simplifier l’analyse de l’objet DataView pour les visuels personnalisés Power BI

## <a name="installation"></a>Installation

Pour installer le package, vous devez exécuter la commande suivante dans le répertoire avec votre visuel personnalisé actuel :

npm install powerbi-visuals-utils-dataviewutils --save Cette commande installe le package et ajoute un package en tant que dépendance à votre package.json

## <a name="datarolehelper"></a>DataRoleHelper

`DataRoleHelper` fournit des fonctions permettant de vérifier les rôles de l’objet dataView.

Le module fournit les fonctions suivantes :

### <a name="getmeasureindexofrole"></a>getMeasureIndexOfRole

Cette fonction recherche la mesure par nom de rôle et retourne son index.

```typescript
function getMeasureIndexOfRole(grouped: DataViewValueColumnGroup[], roleName: string): number;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";
// ...

// This object is actually a part of the dataView object.
let columnGroup: DataViewValueColumnGroup[] = [{
    values: [
        {
            source: {
                displayName: "Microsoft",
                roles: {
                    "company": true
                }
            },
            values: []
        },
        {
            source: {
                displayName: "Power BI",
                roles: {
                    "product": true
                }
            },
            values: []
        }
    ]
}];

dataRoleHelper.getMeasureIndexOfRole(columnGroup, "product");

// returns: 1
```

### <a name="getcategoryindexofrole"></a>getCategoryIndexOfRole

Cette fonction recherche la catégorie par nom de rôle et retourne son index.

```typescript
function getCategoryIndexOfRole(categories: DataViewCategoryColumn[], roleName: string): number;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";
// ...

// This object is actually a part of the dataView object.
let categoryGroup: DataViewCategoryColumn[] = [
    {
        source: {
            displayName: "Microsoft",
            roles: {
                "company": true
            }
        },
        values: []
    },
    {
        source: {
            displayName: "Power BI",
            roles: {
                "product": true
            }
        },
        values: []
    }
];

dataRoleHelper.getCategoryIndexOfRole(categoryGroup, "product");

// returns: 1
```

### <a name="hasrole"></a>hasRole

Cette fonction vérifie si le rôle fourni est défini dans les métadonnées.

```typescript
function hasRole(column: DataViewMetadataColumn, name: string): boolean;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    roles: {
        "company": true
    }
};

DataRoleHelper.hasRole(metadata, "company");

// returns: true
```

### <a name="hasroleindataview"></a>hasRoleInDataView

Cette fonction vérifie si le rôle fourni est défini dans la dataView.

```typescript
function hasRoleInDataView(dataView: DataView, name: string): boolean;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let dataView: DataView = {
    metadata: {
        columns: [
            {
                displayName: "Microsoft",
                roles: {
                    "company": true
                }
            },
            {
                displayName: "Power BI",
                roles: {
                    "product": true
                }
            }
        ]
    }
};

DataRoleHelper.hasRoleInDataView(dataView, "product");

// returns: true
```

### <a name="hasroleinvaluecolumn"></a>hasRoleInValueColumn

Cette fonction vérifie si le rôle fourni est défini dans la colonne de valeur.

```typescript
function hasRoleInValueColumn(valueColumn: DataViewValueColumn, name: string): boolean;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewValueColumn = powerbi.DataViewValueColumn;
import { dataRoleHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let valueColumn: DataViewValueColumn = {
    source: {
        displayName: "Microsoft",
        roles: {
            "company": true
        }
    },
    values: []
};

dataRoleHelper.hasRoleInValueColumn(valueColumn, "company");

// returns: true
```

## <a name="dataviewobjects"></a>DataViewObjects

`DataViewObjects` fournit des fonctions permettant d’extraire les valeurs des objets.

Le module fournit les fonctions suivantes :

### <a name="getvalue"></a>getValue

Cette fonction retourne la valeur de l’objet donné.

```typescript
function getValue<T>(objects: DataViewObjects, propertyId: DataViewObjectPropertyIdentifier, defaultValue?: T): T;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

let property: DataViewObjectPropertyIdentifier = {
    objectName: "microsoft",
    propertyName: "bi"
};

// This object is actually a part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "microsoft": {
        "windows": 5,
        "bi": "Power"
    }
};

dataViewObjects.getValue(objects, property);

// returns: Power
```

### <a name="getobject"></a>getObject

Cette fonction retourne un objet de l’objet donné.

```typescript
function getObject(objects: DataViewObjects, objectName: string, defaultValue?: IDataViewObject): IDataViewObject;
```

Exemple :

```typescript
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "microsoft": {
        "windows": 5,
        "bi": "Power"
    }
};

dataViewObjects.getObject(objects, "microsoft");

/* returns: {
    "bi": "Power",
    "windows": 5

}*/
```

### <a name="getfillcolor"></a>getFillColor

Cette fonction retourne une couleur unie des objets.

```typescript
function getFillColor(objects: DataViewObjects, propertyId: DataViewObjectPropertyIdentifier, defaultColor?: string): string;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

let property: DataViewObjectPropertyIdentifier = {
    objectName: "power",
    propertyName: "fillColor"
};

// This object is actually part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "power": {
        "fillColor": {
            "solid": {
                "color": "yellow"
            }
        },
        "bi": "Power"
    }
};

dataViewObjects.getFillColor(objects, property);

// returns: yellow
```

### <a name="getcommonvalue"></a>getCommonValue

Cette fonction est une fonction universelle permettant de récupérer la couleur ou la valeur d’un objet donné.

```typescript
function getCommonValue(objects: DataViewObjects, propertyId: DataViewObjectPropertyIdentifier, defaultValue?: any): any;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import { dataViewObjects } from "powerbi-visuals-utils-dataviewutils";

let colorProperty: DataViewObjectPropertyIdentifier = {
    objectName: "power",
    propertyName: "fillColor"
};

let biProperty: DataViewObjectPropertyIdentifier = {
    objectName: "power",
    propertyName: "bi"
};

// This object is actually part of the dataView object.
let objects: powerbi.DataViewObjects = {
    "power": {
        "fillColor": {
            "solid": {
                "color": "yellow"
            }
        },
        "bi": "Power"
    }
};

dataViewObjects.getCommonValue(objects, colorProperty); // returns: yellow
dataViewObjects.getCommonValue(objects, biProperty); // returns: Power
```

## <a name="dataviewobject"></a>DataViewObject

`DataViewObject` fournit des fonctions permettant d’extraire la valeur de l’objet.

Le module fournit les fonctions suivantes :

### <a name="getvalue"></a>getValue

Cette fonction retourne une valeur de l’objet par nom de propriété.

```typescript
function getValue<T>(object: IDataViewObject, propertyName: string, defaultValue?: T): T;
```

Exemple :

```typescript
import { dataViewObject } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let object: powerbi.DataViewObject = {
    "windows": 5,
    "microsoft": "Power BI"
};

dataViewObject.getValue(object, "microsoft");

// returns: Power BI
```

### <a name="getfillcolorbypropertyname"></a>getFillColorByPropertyName

Cette fonction retourne une couleur unie de l’objet par nom de propriété.

```typescript
function getFillColorByPropertyName(object: IDataViewObject, propertyName: string, defaultColor?: string): string;
```

Exemple :

```typescript
import { dataViewObject } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let object: powerbi.DataViewObject = {
    "windows": 5,
    "fillColor": {
        "solid": {
            "color": "green"
        }
    }
};

dataViewObject.getFillColorByPropertyName(object, "fillColor");

// returns: green
```

### <a name="converterhelper"></a>converterHelper

`converterHelper` fournit des fonctions permettant de vérifier les propriétés du dataView.

Le module fournit les fonctions suivantes :

### <a name="categoryisalsoseriesrole"></a>categoryIsAlsoSeriesRole

Cette fonction vérifie si la catégorie est également une série.

```typescript
function categoryIsAlsoSeriesRole(dataView: DataViewCategorical, seriesRoleName: string, categoryRoleName: string): boolean;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewCategorical = powerbi.DataViewCategorical;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";
// ...


// This object is actually part of the dataView object.
let categorical: DataViewCategorical = {
    categories: [{
        source: {
            displayName: "Microsoft",
            roles: {
                "power": true,
                "bi": true
            }
        },
        values: []
    }]
};

converterHelper.categoryIsAlsoSeriesRole(categorical, "power", "bi");

// returns: true
```

### <a name="getseriesname"></a>getSeriesName

Cette fonction retourne un nom de la série.

```typescript
function getSeriesName(source: DataViewMetadataColumn): PrimitiveValue;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    roles: {
        "power": true,
        "bi": true
    },
    groupName: "Power BI"
};

converterHelper.getSeriesName(metadata);

// returns: Power BI
```

### <a name="isimageurlcolumn"></a>isImageUrlColumn

Cette fonction vérifie si la colonne contient une URL d’image.

```typescript
function isImageUrlColumn(column: DataViewMetadataColumn): boolean;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    type: {
        misc: {
            imageUrl: true
        }
    }
};

converterHelper.isImageUrlColumn(metadata);

// returns: true
```

### <a name="isweburlcolumn"></a>isWebUrlColumn

Cette fonction vérifie si la colonne contient une URL web.

```typescript
function isWebUrlColumn(column: DataViewMetadataColumn): boolean;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import { converterHelper } from "powerbi-visuals-utils-dataviewutils";

// This object is actually a part of the dataView object.
let metadata: DataViewMetadataColumn = {
    displayName: "Microsoft",
    type: {
        misc: {
            webUrl: true
        }
    }
};

converterHelper.isWebUrlColumn(metadata);

// returns: true
```

### <a name="hasimageurlcolumn"></a>hasImageUrlColumn

Cette fonction vérifie si le dataView a une colonne avec une URL d’image.

```typescript
function hasImageUrlColumn(dataView: DataView): boolean;
```

Exemple :

```typescript
import DataView = powerbi.DataView;
import converterHelper = powerbi.extensibility.utils.dataview.converterHelper;

// This object is actually part of the dataView object.
let dataView: DataView = {
    metadata: {
        columns: [
            {
                displayName: "Microsoft"
            },
            {
                displayName: "Power BI",
                type: {
                    misc: {
                        imageUrl: true
                    }
                }
            }
        ]
    }
};

converterHelper.hasImageUrlColumn(dataView);

// returns: true
```

## <a name="dataviewobjectsparser"></a>DataViewObjectsParser

`DataViewObjectsParser` fournit le moyen le plus simple d’analyser les propriétés du panneau de mise en forme.

La classe fournit les méthodes suivantes :

### <a name="getdefault"></a>getDefault

Cette méthode statique retourne une instance de DataViewObjectsParser.

```typescript
static getDefault(): DataViewObjectsParser;
```

Exemple :

```typescript
import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";
// ...

dataViewObjectsParser.getDefault();

// returns: an instance of the DataViewObjectsParser
```

### <a name="parse"></a>parse

Cette méthode analyse les propriétés du panneau de mise en forme et retourne une instance de `DataViewObjectsParser`.

```typescript
static parse<T extends DataViewObjectsParser>(dataView: DataView): T;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import IVisual = powerbi.extensibility.IVisual;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";

/**
 * This class describes formatting panel properties.
 * Name of the property should match its name described in the capabilities.
 */
class DataPointProperties {
    public fillColor: string = "red"; // This value is a default value of the property.
}

class PropertiesParser extends dataViewObjectsParser.DataViewObjectsParser {
    /**
     * This property describes a group of properties.
     */
    public dataPoint: DataPointProperties = new DataPointProperties();
}

export class YourVisual extends IVisual {
    // implementation of the IVisual.

    private propertiesParser: PropertiesParser;

    public update(options: VisualUpdateOptions): void {
        // Parses properties.
        this.propertiesParser = PropertiesParser.parse<PropertiesParser>(options.dataViews[0]);

        // You can use the properties after parsing
        console.log(this.propertiesParser.dataPoint.fillColor); // returns "red" as default value, it will be updated automatically after any change of the formatting panel.
    }
}
```

## <a name="enumerateobjectinstances"></a>enumerateObjectInstances

Cette méthode statique énumère les propriétés et retourne une instance de `VisualObjectInstanceEnumeration`.

Exécutez-la dans la méthode `enumerateObjectInstances` du visuel.

```typescript
static enumerateObjectInstances(dataViewObjectParser: dataViewObjectsParser.DataViewObjectsParser, options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration;
```

Exemple :

```typescript
import powerbi from "powerbi-visuals-api";
import IVisual = powerbi.extensibility.IVisual;
import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions;
import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import { dataViewObjectsParser } from "powerbi-visuals-utils-dataviewutils";

/**
 * This class describes formatting panel properties.
 * Name of the property should match its name described in the capabilities.
 */
class DataPointProperties {
    public fillColor: string = "red";
}

class PropertiesParser extends dataViewObjectsParser.DataViewObjectsParser {
    /**
     * This property describes a group of properties.
     */
    public dataPoint: DataPointProperties = new DataPointProperties();
}

export class YourVisual extends IVisual {
    // implementation of the IVisual.

    private propertiesParser: PropertiesParser;

    public update(options: VisualUpdateOptions): void {
        // Parses properties.
        this.propertiesParser = PropertiesParser.parse<PropertiesParser>(options.dataViews[0]);
    }

    /**
     * This method will be executed only if the formatting panel is open.
     */
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        return PropertiesParser.enumerateObjectInstances(this.propertiesParser, options);
    }
}
```
