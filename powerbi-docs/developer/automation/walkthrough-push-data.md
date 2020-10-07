---
title: Transmission de données à un jeu de données
description: Transmission de données à un jeu de données Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 792afe42cf302ae552b7f8f1c14d5f232ade320f
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746697"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Transmission de données à un jeu de données Power BI

L’API Power BI vous permet de transmettre des données à un jeu de données Power BI. Dans cet article, nous vous montrons comment transmettre un jeu de données Sales Marketing contenant une table Product dans un jeu de données existant.

Avant de commencer, vous devez disposer d’un annuaire Azure Active Directory (Azure AD) et d’un [compte Power BI](../embedded/create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Étapes de transmission de données à un jeu de données

* Étape 1 : [Inscrire une application auprès d’Azure AD](../embedded/register-app.md)
* Étape 2 : [Obtenir un jeton d’accès d’authentification](walkthrough-push-data-get-token.md)
* Étape 3 : [Créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md)
* Étape 4 : [Obtenir un jeu de données pour ajouter des lignes à une table Power BI](walkthrough-push-data-get-datasets.md)
* Étape 5 : [Ajouter des lignes à une table Power BI](walkthrough-push-data-add-rows.md)

La section suivante est une présentation générale des opérations de l’API Power BI qui transmettent des données.

## <a name="power-bi-api-operations-to-push-data"></a>Opérations de l’API Power BI permettant de transmettre des données

Avec l’API REST Power BI, vous pouvez transmettre des sources de données à Power BI. Lorsqu'une application ajoute des lignes à un jeu de données, les vignettes du tableau de bord sont automatiquement mises à jour avec les nouvelles données. Pour transmettre les données, utilisez les opérations [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) et [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows). Pour trouver un jeu de données, utilisez l’opération [Obtenir des jeux de données](/rest/api/power-bi/datasets/getdatasets). Vous pouvez passer un ID de groupe afin d’utiliser un groupe pour chacune de ces opérations. Pour obtenir la liste des ID de groupe, utilisez l’opération [Obtenir des groupes](/rest/api/power-bi/groups/getgroups).

Voici les opérations permettant de transmettre des données à un jeu de données :

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Obtenir des jeux de données](/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Obtenir des groupes](/rest/api/power-bi/groups/getgroups)

Vous créez un jeu de données dans Power BI en passant une chaîne JSON (JavaScript Objet Notation) au service Power BI. Pour en savoir plus sur JSON, consultez [Présentation de JSON](https://json.org/).

La chaîne JSON d’un jeu de données est au format suivant :

**Objet JSON de jeu de données Power BI**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

Pour notre exemple de jeu de données Sales Marketing, vous transmettriez une chaîne JSON, comme dans l’exemple ci-dessous. Dans cet exemple, **SalesMarketing** est le nom du jeu de données et **Product** le nom de la table. Après avoir défini la table, vous définissez le schéma de table. Pour le jeu de données **SalesMarketing**, le schéma de table comporte ces colonnes : ProductID, Manufacturer, Category, Segment, Product, et IsCompete.

**Exemple d’objet JSON de jeu de données**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

Pour un schéma de table Power BI, vous pouvez utiliser les types de données suivants.

## <a name="power-bi-table-data-types"></a>Types de données de table Power BI

| **Type de données** | **Restrictions** |
| --- | --- |
| Int64 |Valeurs Int64.MaxValue et Int64.MinValue non autorisées. |
| Double |Les valeurs Double.MaxValue et Double.MinValue ne sont pas autorisées. NAN non pris en charge. + Infinity et - Infinity non pris en charge dans certaines fonctions (par exemple, Min, Max). |
| Booléen |Aucune |
| DateTime |Lors du chargement des données nous quantifions les valeurs avec des fractions de jour en multiples de 1/300e de seconde (3,33 ms). |
| Chaîne |Autorise actuellement jusqu’à 128 ko de caractères. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>En savoir plus sur la transmission de données à Power BI

Pour commencer à transmettre des données à un jeu de données, consultez [Étape 1 : Inscrire une application avec Azure AD](../embedded/register-app.md) dans le volet de navigation.

## <a name="next-steps"></a>Étapes suivantes

* [S’inscrire à Power BI](../embedded/create-an-azure-active-directory-tenant.md)  
* [Présentation de JSON](https://json.org/)  
* [Vue d’ensemble de l’API REST Power BI](overview-of-power-bi-rest-api.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)