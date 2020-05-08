---
title: Objets et propriétés des visuels Power BI
description: Cet article décrit les propriétés personnalisables des visuels Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ae548abd0d579414a69b0d970213ff9d69ff2f08
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79205869"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Objets et propriétés des visuels Power BI

Les objets décrivent des propriétés personnalisables associées à un visuel. Un objet peut avoir plusieurs propriétés, et chaque propriété a un type associé qui décrit ce que sera la propriété. Cet article fournit des informations sur les objets et les types de propriétés.

`myCustomObject` est le nom interne utilisé pour référencer l’objet dans `dataView` et `enumerateObjectInstances`.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Nom complet

`displayName` est le nom qui sera affiché dans le volet des propriétés.

## <a name="properties"></a>Propriétés

`properties` est une carte des propriétés définies par le développeur.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` est une propriété spéciale qui permet à un commutateur de basculer l’objet.

Exemple :

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Types de propriété

Il existe deux types de propriétés : `ValueTypeDescriptor` et `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Descripteur de type valeur

Les types `ValueTypeDescriptor` sont principalement primitifs et sont généralement utilisés comme objets statiques.

Voici quelques-uns des éléments `ValueTypeDescriptor` courants :

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descripteur de type structurel

Les types `StructuralTypeDescriptor` sont principalement utilisés pour les objets liés aux données.
Le type `StructuralTypeDescriptor` le plus courant est *fill*.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propriété gradient

La propriété gradient est une propriété qui ne peut pas être définie comme propriété standard. Au lieu de cela, vous devez définir une règle pour la substitution de la propriété du sélecteur de couleurs (type *fill*).

Le code suivant fournit un exemple :

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Notez bien les propriétés *fill* et *fillRule*. La première est le sélecteur de couleurs, et la seconde est la règle de substitution pour le dégradé qui remplace la *propriété fill*, `visually`, quand les conditions de la règle sont remplies.

Ce lien entre la propriété *fill* et la règle de substitution est défini dans la section `"rule"`>`"output"` de la propriété *fillRule*.

La propriété `"Rule"`>`"InputRole"` définit le rôle de données qui déclenche la règle (condition). Dans cet exemple, si le rôle de données `"Gradient"` contient des données, la règle est appliquée pour la propriété `"fill"`.

Le code suivant illustre un exemple du rôle de données qui déclenche la règle de remplissage (`the last item`) :

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>Méthode enumerateObjectInstances

Pour utiliser efficacement des objets, vous avez besoin d’une fonction dans votre visuel personnalisé nommée `enumerateObjectInstances`. Cette fonction remplit le volet de propriétés avec des objets, et détermine également où vos objets doivent être liés dans le dataView.  

Voici à quoi ressemble une installation classique :

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Propriétés

Les propriétés dans `enumerateObjectInstances` reflètent celles que vous avez définies dans vos fonctionnalités. Pour obtenir un exemple, accédez à la fin de cet article.

### <a name="objects-selector"></a>Sélecteur d’objets

Le sélecteur dans `enumerateObjectInstances` détermine où chaque objet est lié dans le dataView. Il existe quatre options distinctes.

#### <a name="static"></a>static

Cet objet est lié aux métadonnées `dataviews[index].metadata.objects`, comme illustré ici.

```typescript
selector: null
```

#### <a name="columns"></a>columns

Cet objet est lié aux colonnes avec le `QueryName` correspondant.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Cet objet est lié à l’élément pour lequel vous avez créé un `selectionID`. Dans cet exemple, partons du principe que nous avons créé des `selectionID` pour certains points de données, et que nous effectuons des boucles.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Scope identity

Cet objet est lié à des valeurs particulières à l’intersection de groupes. Par exemple, si vous avez des catégories `["Jan", "Feb", "March", ...]` et des séries `["Small", "Medium", "Large"]`, vous souhaiterez peut-être avoir un objet à l’intersection des valeurs correspondant à `Feb` et `Large`. Pour ce faire, vous pourriez obtenir le `DataViewScopeIdentity` des deux colonnes, les envoyer à la variable `identities` et utiliser cette syntaxe avec le sélecteur.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Exemple

L’exemple suivant montre à quoi ressemblerait un objectEnumeration pour un objet customColor avec une propriété *fill*. Nous souhaitons que cet objet soit lié de manière statique à `dataViews[index].metadata.objects`, comme illustré :

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
