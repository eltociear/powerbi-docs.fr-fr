---
ms.openlocfilehash: 5c2b254f20bd1eba97840a464a1b554cc4fe1238
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273375"
---
L’utilisation de **variables** représente une partie extrêmement puissante d’une expression DAX.

![](media/7-4-dax-expressions/dax-variables_1.png)

Vous pouvez définir une variable n’importe où dans une expression DAX, à l’aide de la syntaxe suivante :

    VARNAME = RETURNEDVALUE

Les variables peuvent être de n’importe quel type de données, notamment des tables entières.

N’oubliez pas que chaque fois que vous référencez une variable de votre expression DAX, Power BI doit recalculer sa valeur en fonction de votre définition. C’est pourquoi il est conseillé d’éviter de répéter des variables dans votre fonction.

> Contenu vidéo fourni par [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

