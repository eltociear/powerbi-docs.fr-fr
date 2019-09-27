---
title: Options de tri pour les visuels Power BI
description: Cet article décrit le comportement de tri par défaut pour les visuels Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: a360f619428a01c4e7a30481374d042b8e368682
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193919"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Options de tri pour les visuels Power BI

Cet article décrit comment les options de *tri* spécifient le comportement de tri pour les visuels Power BI. 

La fonction de tri nécessite l’un des paramètres suivants.

## <a name="default-sorting"></a>Tri par défaut

L’option `default` est la forme la plus simple. Elle permet de trier les données présentées dans la section « DataMappings ». Cette option permet à l’utilisateur de trier les mappages de données, et spécifie le sens du tri.

```json
    "sorting": {
        "default": {   }
    }
```

![Options de tri dans le menu contextuel](./media/sorting.png)

## <a name="implicit-sorting"></a>Tri implicite

Le tri implicite est un tri avec le paramètre de tableau `clauses`, qui décrit le tri pour chaque rôle de données. `implicit` signifie que l’utilisateur du visuel ne peut pas changer l’ordre de tri. Power BI n’affiche pas les options de tri dans le menu du visuel. Toutefois, Power BI trie les données en fonction des paramètres spécifiés.

Les paramètres `clauses` peuvent contenir plusieurs objets avec deux paramètres :

- `role` : détermine `DataMapping` pour le tri.
- `direction` : détermine le sens du tri (1 = croissant, 2 = décroissant).

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Tri personnalisé

Le tri personnalisé signifie que le tri est géré par le développeur dans le code du visuel.
