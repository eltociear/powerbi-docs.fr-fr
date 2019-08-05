---
title: Objets et propriétés
description: Propriétés personnalisables de Power BI Visual
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424605"
---
# <a name="object-and-properties"></a>Objets et propriétés

Les objets décrivent des propriétés personnalisables associées au visuel.
Chaque objet peut avoir plusieurs propriétés et chaque propriété est associée à un type.
Les types font référence à ce que sera la propriété. Pour plus d’informations sur les types, voir ci-dessous.

`myCustomObject` est le nom interne utilisé pour référencer l’objet dans `dataView` et `enumerateObjectInstances`

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

`ValueTypeDescriptor` sont principalement des types primitifs et sont généralement utilisés comme un objet statique.
Voici quelques-uns des `ValueTypeDescriptor` courants

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Descripteur de type structurel

`StructuralTypeDescriptor` sont principalement utilisés pour les objets liés aux données.
Le remplissage est le plus courant `StructuralTypeDescriptor`

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Propriété gradient

La propriété gradient est une propriété qui ne peut pas être définie comme propriété standard. Au lieu de cela, vous devez définir une règle pour la substitution de la propriété du sélecteur de couleurs (type de remplissage).
Prenons l’exemple ci-dessous :

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

Faites attention aux propriétés `"fill"` et `"fillRule"`. La première est le sélecteur de couleurs, la seconde est la règle de substitution pour le dégradé qui remplace la propriété `visually` « Fill » lorsque les conditions de la règle sont remplies.

Ce lien entre la propriété Fill et la règle de substitution est défini dans la section `"rule"`->`"output"` de la propriété `"fillRule"`.

`"Rule"`->`"InputRole"` définit le rôle de données qui déclenche la règle (condition). Dans cet exemple, si le rôle de données `"Gradient"` contient des données, la règle sera appliquée pour la propriété `"fill"`.

Vous pouvez voir ci-dessous un exemple du rôle de données qui déclenche la règle de remplissage (`the last item`).

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

## <a name="enumerateobjectinstances-method"></a>Méthode `enumerateObjectInstances`

Pour utiliser efficacement des objets, vous avez besoin d’une fonction dans votre visuel personnalisé nommé `enumerateObjectInstances`. Cette fonction remplit le volet de propriétés avec des objets et détermine également où vos objets doivent être liés dans le dataView.  

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

Les propriétés en `enumerateObjectInstances` reflètent les propriétés que vous avez définies dans vos fonctionnalités. Consultez l’exemple en bas de la page.

### <a name="objects-selector"></a>Sélecteur d’objets

Le sélecteur dans `enumerateObjectInstances` détermine où chaque objet sera lié dans le dataView. Il existe quatre options distinctes.

#### <a name="static"></a>static

Cet objet sera lié aux métadonnées `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>columns

Cet objet sera lié aux colonnes avec le `QueryName` correspondant.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Cet objet sera lié à l’élément pour lequel nous avons créé un `selectionID`. Dans cet exemple, nous partons du principe que nous avons créé des `selectionID` pour certains points de données et que nous effectuons des boucles.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Scope identity

Cet objet sera lié à des valeurs particulières à l’intersection de groupes. Par exemple, si j’ai des catégories `["Jan", "Feb", "March", ...]` et des séries `["Small", "Medium", "Large"]`, je souhaite peut-être avoir un objet sur l’intersection des valeurs correspondant `Feb` à et `Large`. Pour ce faire, je pourrais obtenir le `DataViewScopeIdentity` des deux colonnes, les envoyer au `identities` variable et utiliser cette syntaxe avec le sélecteur.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Example

Dans cet exemple, nous allons montrer à quoi ressemble un objectEnumeration pour un objet customColor avec une propriété `fill`. Nous souhaitons que cet objet soit lié de manière statique à `dataViews[index].metadata.objects`

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
