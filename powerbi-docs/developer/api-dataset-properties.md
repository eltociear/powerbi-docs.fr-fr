---
title: Propriétés du jeu de données Power BI
description: En savoir plus sur les propriétés des API de jeu de données Power BI
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b0fabcb5915a4f642abc1af03979a4597e2aa2f7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864958"
---
# <a name="dataset-properties"></a>Propriétés du jeu de données

La version v1 actuelle de l’API de jeux de données permet uniquement de créer un jeu de données avec un nom et une collection de tables. Chaque table a un nom et une collection de colonnes. Chaque colonne a un nom et un type de données. Nous étendons ces propriétés, plus particulièrement avec la prise en charge des mesures et des relations entre les tables. Voici la liste complète des propriétés prises en charge pour cette version :

> [!IMPORTANT]
> Vous pouvez y accéder à la page [Groupes d’opérations de jeux de données](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Jeu de données

Nom  |Type  |Description  |En lecture seule  |Obligatoire
---------|---------|---------|---------|---------
id     |  Guid       | Identificateur unique à l’échelle du système pour le jeu de données.        | Vrai        | Faux        
name     | String        | Nom de jeu de données défini par l’utilisateur.        | Faux        | Vrai        
tables     | Table[]        | Collection de tables.        |  Faux       | Faux        
relationships     | Relationship[]        | Collection de relations entre les tables.        | Faux        |  Faux  
defaultMode     | Chaîne        | Détermine si le jeu de données est envoyé, diffusé en continu ou les deux, avec les valeurs « Push » et « Streaming ».         | False        |  Faux

## <a name="table"></a>Table

Nom  |Type  |Description  |En lecture seule  |Obligatoire
---------|---------|---------|---------|---------
name     | String        |  Nom de table défini par l’utilisateur. Sert également d’identificateur de la table.       | Faux        |  Vrai       
columns     |  column[]       |  Collection de colonnes.       | Faux        |  Vrai       
measures     | measure[]        |  Collection de mesures.       | Faux        |  Faux       
isHidden     | Boolean        | Si Vrai, la table est masquée dans les outils clients.        | Faux        | Faux        

## <a name="column"></a>Column

Nom  |Type  |Description  |En lecture seule  |Obligatoire
---------|---------|---------|---------|---------
name     |  String        | Nom de colonne défini par l’utilisateur.        |  Faux       | Vrai       
dataType     |  String       |  [Types de données EDM](https://msdn.microsoft.com/library/ee382832.aspx) pris en charge et restrictions. Consultez [Restrictions des types de données](#DataTypeRestrictions).      |  Faux       | Vrai        
formatString     | String        | Chaîne décrivant la façon dont la valeur doit être mise en forme lorsqu’elle est affichée. Pour en savoir plus sur la mise en forme des chaînes, consultez [Contenu FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx).      | Faux        | Faux        
sortByColumn    | String        |   Nom de chaîne d’une colonne dans la même table à utiliser pour trier la colonne en cours.     | Faux        | Faux       
dataCategory     | String        |  Valeur de chaîne à utiliser pour la catégorie de données qui décrit les données de cette colonne. Exemples de valeurs courantes : Address, City, Continent, Country, Image, ImageUrl, Latitude, Longitude, Organization, Place, PostalCode, StateOrProvince, WebUrl.       |  False       | Faux        
isHidden    |  Boolean       |  Propriété qui indique si la colonne est masquée. La valeur par défaut est Faux.       | Faux        | Faux        
summarizeBy     | String        |  Méthode d’agrégation par défaut pour la colonne. Voici les valeurs disponibles : default, none, sum, min, max, count, average, distinctCount     |  Faux       | Faux

## <a name="measure"></a>Mesure

Nom  |Type  |Description  |En lecture seule  |Obligatoire
---------|---------|---------|---------|---------
name     | String        |  Nom de mesure défini par l’utilisateur.       |  Faux       | Vrai        
expression     | String        | Expression DAX valide.        | Faux        |  Vrai       
formatString     | String        |  Chaîne décrivant la façon dont la valeur doit être mise en forme lorsqu’elle est affichée. Pour en savoir plus sur la mise en forme des chaînes, consultez [Contenu FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx).       | Faux        | Faux        
isHidden     | String        |  Si Vrai, la table est masquée dans les outils clients.       |  Faux       | Faux       

## <a name="relationship"></a>Relation

Nom  |Type  |Description  |En lecture seule  |Obligatoire 
---------|---------|---------|---------|---------
name     | String        | Nom de relation défini par l’utilisateur. Sert également d’identificateur de la relation.        | Faux       | Vrai        
crossFilteringBehavior     | Chaîne        |    Direction du filtrage de la relation : OneDirection (par défaut), BothDirections, Automatic.       | False        | Faux        
fromTable     | String        | Nom de la table de clé étrangère.        | Faux        | Vrai         
fromColumn    | String        | Nom de la colonne de clé étrangère.        | Faux        | Vrai         
toTable    | String        | Nom de la table de clé primaire.        | Faux        | Vrai         
toColumn     | String        | Nom de la colonne de clé primaire.        | Faux        | Vrai        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Restrictions des types de données (s’applique à la propriété dataType)

Type de données  |Restrictions  
---------|---------
Int64     |   Valeurs Int64.MaxValue et Int64.MinValue non autorisées.      
Double     |  Les valeurs Double.MaxValue et Double.MinValue ne sont pas autorisées. NAN non pris en charge. + Infinity et - Infinity non pris en charge dans certaines fonctions (par exemple, Min, Max).       
Boolean     |   Vrai ou Faux.
DateTime    |   Lors du chargement des données nous quantifions les valeurs avec des fractions de jour en multiples de 1/300ème de seconde (3.33ms).      
Chaîne     |  Autorise actuellement jusqu’à 4 000 caractères par valeur de chaîne.
Décimal|précision=28, échelle=4

## <a name="example"></a>Example
L’exemple de code suivant inclut un certain nombre de ces propriétés :

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```