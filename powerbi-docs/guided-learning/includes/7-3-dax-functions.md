---
ms.openlocfilehash: c3b1b7288d0d277fc866ea47887335d10279c6cc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799835"
---
DAX offre de nombreuses fonctions pour mettre en forme, former ou analyser vos données. Ces fonctions peuvent être regroupées dans plusieurs catégories :

* Fonctions d’**agrégation**
* Fonctions de **comptage**
* Fonctions **logiques**
* Fonctions d’**information**
* Fonctions de **texte**
* Fonctions de **date**

Comme c’est le cas dans Excel, quand vous commencez à taper votre formule dans la **barre de formule** de Power BI Desktop, une liste des fonctions disponibles s’affiche pour vous aider à déterminer quelle fonction sélectionner. À l’aide des flèches **haut** et **bas** de votre clavier, vous pouvez alors mettre en surbrillance une fonction disponible pour afficher une brève description.

Power BI affiche les fonctions qui correspondent aux lettres que vous avez tapées jusqu’ici. Ainsi, si vous tapez *S*, seules les fonctions qui commencent par un *S* sont répertoriées dans la liste. Si vous tapez *Su* , seules les fonctions qui *contiennent* la séquence de lettres *Su* dans leur nom sont affichées dans la liste (il n’est pas nécessaire qu’elles commencent par *Su* ; il suffit qu’elles contiennent cette séquence de lettres).

![](media/7-3-dax-functions/dax-functions_1.png)

Il est facile de faire des essais avec DAX de cette façon pour rechercher les diverses fonctions DAX disponibles dans Power BI. Il vous suffit de commencer à taper, Power BI s’occupe du reste.

Maintenant que nous savons comment démarrer avec la formule DAX, nous allons nous intéresser à chaque catégorie de fonctions tour à tour.

## <a name="aggregation-functions"></a>Fonctions d’agrégation
DAX possède plusieurs fonctions d’**agrégation**, notamment les fonctions couramment utilisées suivantes :

* SUM
* MOYENNE
* MIN
* MAX
* SUMX (et d’autres fonctions *X*)

Ces fonctions ne fonctionnent que sur des colonnes numériques et peuvent généralement agréger une seule colonne à la fois.

Toutefois, les fonctions d’agrégation spéciales qui se terminent par **X**, telles que **SUMX**, peuvent fonctionner sur plusieurs colonnes en même temps. Ces fonctions itèrent au sein de la table et évaluent l’expression pour chaque ligne.

## <a name="counting-functions"></a>Fonctions de comptage
Les fonctions de **comptage** couramment utilisées sont les suivantes :

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Ces fonctions comptent différents éléments, tels que des valeurs distinctes, des valeurs non vides et des lignes de table.

## <a name="logical-functions"></a>Fonctions logiques
La collection de fonctions **logiques** de DAX comprend :

* ET
* OU
* NOT
* IF
* IFERROR

Ces fonctions spéciales peuvent également être exprimées sous forme d’*opérateurs*. Par exemple, **AND** peut être tapé sous la forme (remplacé par) **&&** dans la formule DAX.

Vous pouvez utiliser des opérateurs (tels que **&&** ) quand vous avez besoin de plus de deux conditions dans votre formule. Sinon, il est recommandé d’utiliser le nom de la fonction (par exemple **AND**) pour faciliter la lecture du code DAX.

## <a name="information-functions"></a>Fonctions d’information
Les fonctions d’**information** de DAX incluent :

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Bien que ces fonctions puissent s’avérer utiles selon les circonstances, il est utile de connaître le type de données de vos colonnes à l’avance, plutôt que de vous fier uniquement à ces fonctions.

DAX utilise les fonctions **MAX** et **MIN** à la fois pour *agréger* des valeurs et *comparer* des valeurs.

## <a name="text-functions"></a>Fonctions de texte
Les fonctions de **texte** couramment utilisées sont les suivantes :

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Ces fonctions de **texte** fonctionnent de manière très similaire aux fonctions Excel du même nom. Ainsi, si vous savez comment Excel gère les fonctions de texte, vous avez déjà une longueur d’avance. Sinon, vous pouvez toujours faire des essais avec ces fonctions dans Power BI pour voir comment elles se comportent.

## <a name="date-functions"></a>Fonctions de date
DAX intègre les fonctions de **date** suivantes :

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Bien que ces fonctions soient utiles pour calculer et extraire des informations à partir de valeurs de *date*, elles ne s’appliquent pas à Time Intelligence, qui utilise une table de dates.

> Contenu vidéo fourni par [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

