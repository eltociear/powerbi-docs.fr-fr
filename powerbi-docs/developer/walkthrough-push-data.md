---
title: Transmission de données à un jeu de données
description: Transmission de données à un jeu de données Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 01/05/2017
ms.author: maghan
ms.openlocfilehash: 96b29c9dc6c384b663ef375d4968dedb011bd05d
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34813109"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Transmission de données à un jeu de données Power BI
Avec l’API Power BI, vous pouvez transmettre des données à un jeu de données Power BI. Par exemple, vous voulez étendre un workflow d’entreprise existant pour transmettre des données clés à votre jeu de données. Dans ce cas, vous voulez transmettre un jeu de données Sales Marketing qui possède une table Product à un jeu de données.

Avant de commencer à transmettre des données à un jeu de données, vous devez disposer d’un annuaire Azure Active Directory (Azure AD) et d’un [compte Power BI](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Étapes de transmission de données à un jeu de données
* Étape 1 : [Inscrire une application auprès d’Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Étape 2 : [Obtenir un jeton d’accès d’authentification](walkthrough-push-data-get-token.md)
* Étape 3 : [Créer un jeu de données dans Power BI](walkthrough-push-data-create-dataset.md)
* Étape 4 : [Obtenir un jeu de données pour ajouter des lignes à une table Power BI](walkthrough-push-data-get-datasets.md)
* Étape 5 : [Ajouter des lignes à une table Power BI](walkthrough-push-data-add-rows.md)

La section suivante est une présentation générale des opérations de l’API Power BI qui transmettent des données.

## <a name="power-bi-api-operations-to-push-data"></a>Opérations de l’API Power BI permettant de transmettre des données
Avec l’API REST Power BI, vous pouvez transmettre des sources de données à Power BI. Lorsqu’une application ajoute des lignes à un jeu de données, les vignettes du tableau de bord sont automatiquement mises à jour avec les données modifiées. Pour pousser des données, utilisez l’opération [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) avec l’opération [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows). Pour trouver un jeu de données, vous utilisez l’opération [Obtenir des jeux de données](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets). Pour chacune de ces opérations, vous pouvez passer un ID de groupe pour utiliser un groupe. Utilisez l’opération [Obtenir des groupes](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) pour obtenir la liste des ID de groupe.

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

Ainsi, pour notre exemple de jeu de données Sales Marketing, vous transmettriez une chaîne JSON, comme dans l’exemple ci-dessous. Dans cet exemple, **SalesMarketing** est le nom du jeu de données et **Product** le nom de la table. Après avoir défini la table, vous définissez le schéma de table. Pour le jeu de données **SalesMarketing** , le schéma de table comporte ces colonnes : ProductID, Manufacturer, Category, Segment, Product et IsCompete.

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
| Double |Les valeurs Double.MaxValue et Double.MinValue ne sont pas autorisées. NAN non pris en charge. + Infinity et - Infinity non pris en charge dans certaines fonctions (par exemple, Min, Max). |
| Boolean |Aucun |
| DateTime |Lors du chargement des données nous quantifions les valeurs avec des fractions de jour en multiples de 1/300ème de seconde (3.33ms). |
| String |Autorise actuellement jusqu’à 128 Ko de caractères. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>En savoir plus sur la transmission de données à Power BI
Pour commencer à transmettre des données à un jeu de données, consultez [Étape 1 : Inscrire une application auprès d’Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) dans le volet de navigation gauche.

[Étape suivante >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Étapes suivantes
[S’inscrire à Power BI](create-an-azure-active-directory-tenant.md)  
[Présentation de JSON](http://json.org/)  
[Vue d’ensemble de l’API REST Power BI](overview-of-power-bi-rest-api.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

