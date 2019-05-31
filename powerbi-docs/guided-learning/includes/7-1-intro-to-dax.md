---
ms.openlocfilehash: 8af5b1cf243d599ab68e9c2db1a3c6003f82c29f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273400"
---
Bienvenue dans la partie **Formation guidée** de Power BI conçue pour vous présenter **DAX**.

**DAX** signifie **Data Analysis Expressions**. Il s’agit du langage de formule utilisé dans Power BI (ce langage est également utilisé par Power BI en arrière-plan). DAX se retrouve également dans d’autres produits Microsoft, notamment Power Pivot et le modèle tabulaire SSAS, mais cet ensemble de sujets de formation guidée se concentre sur la manière dont DAX est utilisé, et peut être utilisé par vous, dans Power BI.

## <a name="dax-and-this-guided-learning-video-series"></a>DAX et cette série de vidéos de formation guidée
L’objectif de cette **formation guidée** est de vous apprendre les concepts de base et notions fondamentales de DAX : comment envisager DAX, comment il fonctionne et les fonctionnalités les plus utiles, comme vous l’explique (et l’a appris avec beaucoup d’expérience) [Alberto Ferrari](http://www.sqlbi.com/learning-dax), un expert réputé de DAX.

![Portrait d’Alberto Ferrari](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

Les vidéos de cette **formation guidée** sur **DAX** vous apprennent les concepts de base de DAX en se basant sur le fonctionnement du langage de formule DAX. Cela s’avère utile lors de la création de formules DAX de bout en bout, mais est également très utile pour comprendre comment Power BI crée ces formules DAX quand vous créez des requêtes dans l’**éditeur de requête**.

## <a name="in-this-video---introduction-to-dax"></a>Dans cette vidéo - présentation de DAX
Les concepts de DAX sont simples et explicites, mais DAX n’en est pas moins un langage puissant. DAX utilise certains concepts et modèles de programmation uniques, qui peuvent le rendre difficile à utiliser et à comprendre parfaitement. Les méthodes traditionnelles d’apprentissage des langages peuvent ne pas être la meilleure approche pour DAX. L’objectif de cette vidéo consiste donc à vous apprendre les concepts et les principes qui seront utiles par la suite dans votre utilisation de Power BI.

DAX est un *langage fonctionnel*, ce qui signifie que le code exécuté complet est contenu dans une fonction.

Dans DAX, les fonctions peuvent contenir d’autres fonctions imbriquées, des instructions conditionnelles et des références à des valeurs. L’exécution de DAX commence à partir de la fonction ou du paramètre le plus profond, et progresse vers l’extérieur. Dans Power BI, les formules DAX sont écrites dans une seule ligne. Par conséquent, pour une meilleure lisibilité, il est important que le format de vos fonctions soit correct.

DAX est conçu pour fonctionner avec des tables, par conséquent, il a simplement deux types de données primaire : **Numérique** et **autres**. Le type **Numérique** peut inclure des *entiers*, des *décimales* et une *devise*. Le type **Autre** peut inclure des *chaînes* et des *objets binaires*. Cela signifie que si vous créez votre fonction DAX pour travailler sur un type de nombre, vous avez la garantie qu’elle fonctionnera sur n’importe quelles autres données de type Numérique.

DAX utilise la surcharge d’opérateur, ce qui signifie que vous pouvez combiner des types de données dans vos calculs, et que les résultats changent en fonction du type de données utilisé dans les entrées. La conversion s’effectue automatiquement. Cela signifie que vous n’avez pas à connaître les types de données des colonnes avec lesquelles vous travaillez dans Power BI, mais cela suppose également que la conversion peut parfois se produire de façon inattendue. Il est conseillé de comprendre les données que vous utilisez pour vérifier que vos opérateurs se comportent comme prévu.

Il existe un type de données en particulier que vous allez probablement être avec beaucoup travailler dans Power BI : **Date/heure**. **DateTime** est stocké en tant que valeur à virgule flottante avec la partie entière et la partie décimale. DateTime peut être utilisé précisément pour les calculs d’une période ultérieure au 1er mars 1900.

> Contenu vidéo fourni par [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

