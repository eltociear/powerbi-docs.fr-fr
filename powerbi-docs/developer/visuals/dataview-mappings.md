---
title: Mappages de vues de données
description: Comment Power BI transforme les données avant de les transmettre aux visuels
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ff70b2f12921694617a736164484df1326471eea
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425180"
---
# <a name="data-view-mappings-in-power-bi-visuals"></a>Mappages de vues de données dans les visuels Power BI

Un mappage `dataViewMappings` décrit comment les rôles de données sont liés les uns aux autres et vous permet de spécifier des exigences conditionnelles pour eux.
Il existe une section pour chacun des `dataMappings`.

Chaque mappage valide doit produire une `DataView`, mais comme nous prenons uniquement en charge l’exécution d’une seule requête par visuel pour le moment, dans la plupart des cas, vous n’obtiendrez qu’une seule `DataView`. Toutefois, vous pouvez fournir plusieurs mappages de données avec des conditions différentes, ce qui permet :

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

> [!NOTE]
> Il est important de noter que Power BI crée un mappage à une vue DataView si et seulement si le mappage valide est renseigné dans `dataViewMappings`.

En d’autres termes, si `categorical` est défini dans `dataViewMappings`, mais que d’autres mappages, comme `table`, `single`, etc. ne le sont pas comme dans l’exemple suivant :
```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

Power BI produit une `DataView` avec un mappage `categorical` unique (`table` et d’autres mappages sont `undefined`) :
```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>Conditions

Décrit les conditions d’un mappage de données particulier. Vous pouvez fournir plusieurs ensembles de conditions et, si les données correspondent à l’un des ensembles de conditions décrits, le visuel accepte les données comme étant valides.

Actuellement, pour chaque champ, vous pouvez spécifier une valeur minimale et une valeur maximale. Cela représente le nombre de champs qui peuvent être liés à ce rôle de données. 

> [!NOTE]
> Si un rôle de données est omis dans la condition, il peut contenir n’importe quel nombre de champs.

### <a name="example-1"></a>Exemple 1

Vous pouvez faire glisser plusieurs champs dans chaque rôle de données. Dans cet exemple, nous limitons la catégorie à un champ de données et la mesure à deux champs de données.

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>Exemple 2

Dans cet exemple, l’une des deux conditions est requise. Soit exactement un champ de données de catégorie et précisément deux mesures, soit exactement deux catégories et précisément une mesure.

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>Mappage de données unique

Le mappage de données unique est la forme la plus simple du mappage de données. Il accepte un champ de mesure unique et vous donne le total. Si le champ est numérique, vous obtenez la somme. Dans le cas contraire, vous obtenez un nombre de valeurs uniques.

Pour utiliser un mappage de données unique, vous devez définir le nom du rôle de données que vous souhaitez mapper. Ce mappage ne fonctionne qu’avec un seul champ de mesure. Si un deuxième champ est affecté, aucune vue de données n’est générée. C’est pourquoi, il est également recommandé d’inclure une condition qui limite les données à un seul champ.

> [!NOTE]
> Ce mappage de données ne peut pas être utilisé conjointement avec d’autres mappages de données. Il est destiné à réduire les données en une seule valeur numérique.

### <a name="example-3"></a>Exemple 3

```json
"dataViewMappings": {
    "conditions": [
        { "Y": { "max": 1 } }
    ],
    "single": {
        "role": "Y"
    }
}  
```

La vue de données résultante contient toujours les autres types (table, catégorie, etc.), mais chaque mappage ne contient que la valeur unique. Il est recommandé d’accéder uniquement à la valeur unique.

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

## <a name="categorical-data-mapping"></a>Mappage de données par catégorie

Un mappage de données par catégorie permet de récupérer un ou deux regroupements indépendants de données.

### <a name="example-4"></a>Exemple 4

Voici la définition de notre exemple précédent de DataRoles.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

À présent, pour le mappage :

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

Exemple simple exprimé clairement : « mapper mon DataRole `category` de façon à ce que pour chaque champ que je fais glisser dans `category`, ses données soient mappées à `categorical.categories`. Mapper également mon DataRole `measure` à `categorical.values`. »

* **for...in** : inclut tous les éléments de ce rôle de données dans la requête de données.
* **bind...to** : produit le même résultat que for...in, mais s’attend à ce que le DataRole ait une condition le limitant à un champ unique.

### <a name="example-5"></a>Exemple 5

Dans cet exemple, nous allons utiliser les deux premiers DataRoles de l’exemple précédent, en définissant en plus `grouping` et `measure2`.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

À présent, pour le mappage :

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

Ici, la différence tient à la façon dont nous mappons les valeurs par catégorie. Nous indiquons : « Mapper mes rôles de données `measure` et `measure2` à regrouper dans le rôle de données `grouping` ».

### <a name="example-6"></a>Exemple 6

Voici les dataRoles.

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

Voici le dataViewMapping.

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

La `dataview` par catégorie peut être visualisée ainsi :

| Catégorie |  |  | | | |
|-----|-----|------|------|------|------|
| | Année | 2013 | 2014 | 2015 | 2016 |
| Pays | | |
| USA | | x | x | 125 | 100 |
| Canada | | x | 50 | 200 | x |
| Mexico | | 300 | x | x | x |
| Royaume-Uni | | x | x | 75 | x |

Power BI génère une vue de données par catégorie. Il s’agit de l’ensemble des catégories.

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "Mexico",
                    "UK",
                    "USA"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

Chaque catégorie est également mappée à un ensemble de valeurs. Chacune de ces valeurs est regroupée par série, c’est-à-dire des années.

Par exemple, les ventes du Canada en 2013 sont nulles, et elles se montent à 50 en 2014.

```JSON
{
    "values": [
        {
            "source": {...},
            "values": [
                null,
                300,
                null,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                50,
                null,
                150,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                200,
                null,
                null,
                125
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                null,
                null,
                null,
                100
            ],
            "identity": [...],
        }
    ]
}
```

## <a name="table-data-mapping"></a>Mappage de données de table

La vue de données de table est un mappage de données simple. En gros, il s’agit d’une liste de points de données, où les points de données numériques peuvent être agrégés.

### <a name="example-7"></a>Exemple 7

Avec les fonctionnalités données :

```json
"dataRoles": [
    {
        "displayName": "Values",
        "name": "values",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                }
            }
        }
    }
]
```

La table `dataview` peut être visualisée ainsi :  

| Pays| Année | Ventes |
|-----|-----|------|
| USA | 2016 | 100 |
| USA | 2015 | 50 |
| Canada | 2015 | 200 |
| Canada | 2015 | 50 |
| Mexico | 2013 | 300 |
| Royaume-Uni | 2014 | 150 |
| USA | 2015 | 75 |

Power BI génère une vue de données de table. Ne partez pas du principe qu’il y a un ordre.

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                50
            ],
            [
                "Canada",
                2015,
                200
            ],
            [
                "Mexico",
                2013,
                300
            ],
            [
                "UK",
                2014,
                150
            ],
            [
                "USA",
                2015,
                100
            ],
            [
                "USA",
                2015,
                75
            ],
            [
                "USA",
                2016,
                100
            ]
        ]
    }
}
```

Les données peuvent être agrégées en sélectionnant le champ souhaité et en cliquant sur Somme.  

![Agrégation des données](./media/data-aggregation.png)

## <a name="matrix-data-mapping"></a>Mappage de données de matrice

Le mappage de données de matrice est semblable au mappage de données de table, mais les lignes sont présentées de façon hiérarchique. Et l’une des valeurs `dataRole` peut être utilisée comme valeur d’en-tête de colonne.

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

Power BI crée une structure de données hiérarchique. La racine de l’arborescence comprend les données de la première colonne du rôle de données `Category` avec les enfants de la deuxième colonne du rôle de données.

Jeu de données :

| Parents | Enfants | Petits-enfants | Colonnes | Valeurs |
|-----|-----|------|-------|-------|
| Parent 1 | Enfant 1 | Petit-enfant 1 | Col 1 | 5 |
| Parent 1 | Enfant 1 | Petit-enfant 1 | Col 2 | 6 |
| Parent 1 | Enfant 1 | Petit-enfant 2 | Col 1 | 7 |
| Parent 1 | Enfant 1 | Petit-enfant 2 | Col 2 | 8 |
| Parent 1 | Enfant 2 | Petit-enfant 3 | Col 1 | 5 |
| Parent 1 | Enfant 2 | Petit-enfant 3 | Col 2 | 3 |
| Parent 1 | Enfant 2 | Petit-enfant 4 | Col 1 | 4 |
| Parent 1 | Enfant 2 | Petit-enfant 4 | Col 2 | 9 |
| Parent 1 | Enfant 2 | Petit-enfant 5 | Col 1 | 3 |
| Parent 1 | Enfant 2 | Petit-enfant 5 | Col 2 | 5 |
| Parent 2 | Enfant 3 | Petit-enfant 6 | Col 1 | 1 |
| Parent 2 | Enfant 3 | Petit-enfant 6 | Col 2 | 2 |
| Parent 2 | Enfant 3 | Petit-enfant 7 | Col 1 | 7 |
| Parent 2 | Enfant 3 | Petit-enfant 7 | Col 2 | 1 |
| Parent 2 | Enfant 3 | Petit-enfant 8 | Col 1 | 10 |
| Parent 2 | Enfant 3 | Petit-enfant 8 | Col 2 | 13 |

Le visuel Matrice principale de Power BI l’affiche sous forme d’une table.

![Visuel de tableau](./media/matrix-visual-smaple.png)

Le visuel obtient la structure de données décrite ci-dessous (seules les deux premières lignes sont présentées) :

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>Algorithme de réduction des données

Un `DataReductionAlgorithm` peut être appliqué si vous souhaitez contrôler la quantité de données reçues dans la DataView.

Par défaut, tous les visuels personnalisés ont le paramètre DataReductionAlgorithm top appliqué avec la valeur « count » définie sur 1 000 dataPoints. Cela revient à définir les propriétés suivantes dans le fichier capabilities.json :

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

Vous pouvez modifier la valeur « count » en la définissant sur n’importe quelle valeur entière allant jusqu’à 30 000. Les visuels personnalisés basés sur R peuvent prendre en charge jusqu’à 150 000 lignes.

## <a name="data-reduction-algorithm-types"></a>Types d’algorithmes de réduction des données

Il existe quatre types de paramètres `DataReductionAlgorithm` :

* `top` : si vous souhaitez limiter les données aux valeurs issues du haut du jeu de données. Les premières valeurs « count » sont extraites du jeu de données.
* `bottom` : si vous souhaitez limiter les données aux valeurs issues du bas du jeu de données. Les dernières valeurs « count » sont extraites du jeu de données.
* `sample` : réduit le jeu de données à l’aide d’un algorithme d’échantillonnage simple limité à un nombre « count » d’éléments. Cela signifie que les premier et dernier éléments sont inclus, avec un nombre « count » d’éléments dont les intervalles sont égaux.
Par exemple, si vous avez un jeu de données [0, 1, 2, ... 100] et un `count: 9`, vous recevez les valeurs suivantes [0, 10, 20... 100]
* `window` : charge une « fenêtre » de points de données à une heure contenant les éléments « count ». Actuellement, `top` et `window` sont équivalents. Un travail est en cours pour assurer la prise en charge totale d’un paramètre de fenêtrage.

## <a name="data-reduction-algorithm-usage"></a>Utilisation d’un algorithme de réduction des données

Un `DataReductionAlgorithm` peut être utilisé dans les mappages `dataview` de catégorie, table ou matrice.

Il peut être défini en `categories` ou section de groupe de `values` pour le mappage de données de catégorie.

### <a name="example-8"></a>Exemple 8

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

L’algorithme de réduction des données peut être appliqué à la section `rows` du mappage `dataview` de table.

### <a name="example-9"></a>Exemple 9

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                } 
            }
        }
    }
]
```

L’algorithme de réduction des données peut être appliqué à la section `rows` ou `columns` du mappage `matrix` `dataview`.
