---
title: Transmission de données à un jeu de données
description: Transmission de données à un jeu de données Power BI
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222157"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Transmission de données à un jeu de données Power BI

L’API Power BI vous permet de transmettre des données à un jeu de données Power BI. Dans cet article, nous vous montrons comment transmettre un jeu de données Sales Marketing qui contient une table Product dans un dataset existant.

Avant de commencer, vous avez besoin d’un Azure Active Directory (Azure AD) et un [compte Power BI](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Étapes de transmission de données à un jeu de données

* Étape 1 : [Inscrire une application auprès d’Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Étape 2 : [Obtenir un jeton d’accès d’authentification](walkthrough-push-data-get-token.md)
* Étape 3 : [Créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md)
* Étape 4 : [Obtenir un jeu de données pour ajouter des lignes à une table Power BI](walkthrough-push-data-get-datasets.md)
* Étape 5 : [Ajouter des lignes à une table Power BI](walkthrough-push-data-add-rows.md)

La section suivante est une présentation générale des opérations de l’API Power BI qui transmettent des données.

## <a name="power-bi-api-operations-to-push-data"></a>Opérations de l’API Power BI permettant de transmettre des données

Avec l’API REST Power BI, vous pouvez transmettre des sources de données à Power BI. Lorsqu’une application ajoute des lignes à un jeu de données, les vignettes de tableau de bord mise à jour automatiquement avec les nouvelles données. Pour transmettre des données, utilisez le [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) et [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows) operations. Pour rechercher un jeu de données, utilisez le [obtenir des jeux de données](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) opération. Vous pouvez passer un ID de groupe pour travailler avec un groupe pour une de ces opérations. Pour obtenir une liste d’ID de groupe, utilisez le [obtenir des groupes](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) opération.

Voici les opérations permettant de transmettre des données à un jeu de données :

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Obtenir des jeux de données](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Obtenir des groupes](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Vous créez un jeu de données dans Power BI en passant une chaîne JSON (JavaScript Objet Notation) au service Power BI. Pour en savoir plus sur JSON, consultez [Présentation de JSON](http://json.org/).

La chaîne JSON d’un jeu de données est au format suivant :

**Objet JSON de jeu de données Power BI**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Dans notre exemple de jeu de données Sales Marketing, vous transmettriez une chaîne JSON, comme indiqué ci-dessous. Dans cet exemple, **SalesMarketing** est le nom du jeu de données, et **produit** est le nom de table. Après avoir défini la table, vous définissez le schéma de table. Pour le jeu de données **SalesMarketing**, le schéma de table comporte ces colonnes : ProductID, Manufacturer, Category, Segment, Product, et IsCompete.

**Exemple d’objet JSON de jeu de données**

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

Pour un schéma de table Power BI, vous pouvez utiliser les types de données suivants.

## <a name="power-bi-table-data-types"></a>Types de données de table Power BI

| **Type de données** | **Restrictions** |
| --- | --- |
| Int64 |Valeurs Int64.MaxValue et Int64.MinValue non autorisées. |
| Double |Les valeurs Double.MaxValue et Double.MinValue ne sont pas autorisées. NaN non pris en charge. + Infinity et - Infinity non pris en charge dans certaines fonctions (par exemple, Min, Max). |
| Booléen |Aucun |
| DateTime |Pendant le chargement de données, nous quantifions les valeurs avec des fractions de jour multiples entiers de 1/300 de seconde (3,33 ms). |
| Chaîne |Autorise actuellement jusqu'à 128 Ko de caractères. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>En savoir plus sur la transmission de données à Power BI

Pour commencer à transmettre des données à un jeu de données, consultez [Étape 1 : Inscrire une application avec Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) dans le volet de navigation gauche.

[Étape suivante >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Étapes suivantes

[S’inscrire à Power BI](create-an-azure-active-directory-tenant.md)  
[Présentation de JSON](http://json.org/)  
[Vue d’ensemble de l’API REST Power BI](overview-of-power-bi-rest-api.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)