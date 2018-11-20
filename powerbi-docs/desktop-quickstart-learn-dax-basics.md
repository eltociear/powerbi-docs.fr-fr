---
title: Principes fondamentaux de DAX dans Power BI Desktop
description: Principes fondamentaux de DAX dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a171dd2aa375f8d12830b051dd8ce6437e4b3236
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679452"
---
# <a name="dax-basics-in-power-bi-desktop"></a>Principes fondamentaux de DAX dans Power BI Desktop
Cet article s’adresse aux utilisateurs qui débutent avec Power BI Desktop. Il est destiné à vous fournir une introduction rapide et simple de la façon dont vous pouvez utiliser le langage DAX (Data Analysis Expressions) pour résoudre un certain nombre de problèmes d’analyse de données et de calcul de base. Nous aborderons des informations conceptuelles, une série de tâches que vous pourrez effectuer et quelques questionnaires pour tester ce que vous aurez appris. À la fin de cet article, vous aurez acquis une bonne compréhension des concepts fondamentaux du langage DAX.

## <a name="what-is-dax"></a>Qu’est-ce que DAX ?
DAX est une collection de fonctions, d’opérateurs et de constantes qui peuvent être utilisés dans une formule, ou une expression, pour calculer et retourner une ou plusieurs valeurs. En termes simples, DAX vous aide à créer des informations à partir des données déjà présentes dans votre modèle.

## <a name="why-is-dax-so-important"></a>Pourquoi DAX est-il si important ?
Il est relativement facile de créer un nouveau fichier Power BI Desktop et d’y importer des données. Vous pouvez même créer des rapports montrant des analyses importantes sans utiliser aucune formule DAX. En revanche, comment procéder si vous avez besoin d’analyser un pourcentage de croissance sur plusieurs catégories de produits et pour différentes périodes ? Ou si vous devez calculer la croissance année après année en comparaison avec les tendances du marché ? Les formules DAX fournissent cette fonctionnalité, ainsi que de nombreuses autres. Apprendre à créer des formules DAX efficaces vous permettra de tirer le meilleur parti possible de vos données. L’obtention des informations dont vous avez besoin vous permet d’envisager de résoudre des problèmes concrets dans votre entreprise, qui affectent vos résultats. C’est là toute la puissance de Power BI et DAX vous aide à l’exploiter.

## <a name="prerequisites"></a>Conditions préalables
Vous connaissez peut-être déjà bien la création de formules dans Microsoft Excel. Ces connaissances vous aideront à mieux comprendre DAX. Toutefois, même si vous n’avez aucune expérience des formules Excel, les concepts décrits ici vous permettront de créer des formules DAX et de résoudre des problèmes décisionnels concrets immédiatement.

Nous allons tâcher de comprendre les formules DAX dans le cadre des calculs, et plus spécifiquement, dans les mesures et les colonnes calculées. Vous devez déjà bien connaître Power BI Desktop, l’importation de données, l’ajout de champs dans un rapport, ainsi que les concepts fondamentaux des [mesures](desktop-measures.md) et des [colonnes calculées](desktop-calculated-columns.md).

**Exemple de classeur**

La meilleure façon d’apprendre le langage DAX consiste à créer des formules de base, à les utiliser avec des données réelles et à examiner les résultats obtenus. Les exemples et les tâches mentionnés dans cet article utilisent le fichier Contoso Sales Sample for Power BI Desktop Preview. Il s’agit du même fichier d’exemple que celui utilisé dans l’article [Didacticiel : Créer vos propres mesures dans Power BI Desktop](desktop-tutorial-create-measures.md). Voici le [fichier d’exemple](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) à télécharger.

## <a name="lets-begin"></a>Au travail !
Nous allons bâtir notre compréhension de DAX autour de trois concepts fondamentaux : la *syntaxe* , les *fonctions* et le *contexte* . Bien entendu, il existe d’autres concepts importants propres à DAX, mais la compréhension de ces trois concepts fournit un socle optimal sur lequel vous pourrez développer vos compétences DAX.

### <a name="syntax"></a>Syntaxe
Avant de créer vos propres formules, examinez la syntaxe des formules DAX. La syntaxe inclut les différents éléments qui constituent une formule, ou plus simplement, la manière dont la formule est écrite. Par exemple, examinons une formule DAX simple.

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Cette formule inclut les éléments syntaxiques suivants :

**A.** Le nom de la mesure **Total Sales**.

**B.** L’opérateur signe égal (**=**) indique le début de la formule. Après le calcul, un résultat est retourné.

**C.** La fonction DAX **SUM** additionne tous les nombres figurant dans la colonne **Sales[SalesAmount]**. Vous en apprendrez davantage sur les fonctions ultérieurement.

**D.** Des parenthèses **()** entourent une expression contenant un ou plusieurs arguments. Toutes les fonctions nécessitent au moins un argument. Un argument passe une valeur à une fonction.

**E.** La table référencée **Sales**.

**F.** La colonne référencée **[SalesAmount]** dans la table Sales. Avec cet argument, la fonction SUM sait sur quelle colonne agréger une somme.

Pour mieux comprendre une formule DAX, il est souvent utile de séparer chaque élément en l’exprimant dans la langue qui vous est familière. Par exemple, vous pouvez lire cette formule :

> *Pour la mesure nommée Total Sales, calculer (=) la somme (SUM) des valeurs de la colonne [SalesAmount] dans la table Sales.*
> 
> 

Quand elle est ajoutée dans un rapport, cette mesure calcule et retourne des valeurs en effectuant la somme des montants des ventes pour chacun des autres champs que vous incluez, tels que les téléphones mobiles aux États-Unis.

Vous vous demandez peut-être si cette mesure revient au même que d’ajouter simplement le champ SalesAmount dans votre rapport. Vous avez raison. Toutefois, il y a une bonne raison de créer votre propre mesure qui calcule la somme des valeurs du champ SalesAmount : vous pouvez l’utiliser en tant qu’argument dans d’autres formules. Cela peut sembler un peu confus à ce stade, mais quand vos compétences en matière de formules DAX se seront développées, savoir cela améliorera l’efficacité de vos formules et de votre modèle. En fait, vous verrez la mesure Total Sales utilisée en tant qu’argument dans d’autres formules par la suite.

Attardons-nous sur quelques éléments concernant cette formule. En particulier, nous avons présenté une fonction, [SUM](https://msdn.microsoft.com/library/ee634387.aspx). Les fonctions sont des formules pré-écrites qui facilitent des calculs et des manipulations complexes avec des nombres, des dates, des heures, du texte, etc. Vous en apprendrez davantage sur les fonctions ultérieurement.

Vous constatez également que la colonne [SalesAmount] est précédée par la table Sales à laquelle la colonne appartient. On parle de nom de colonne qualifié complet du fait qu’il inclut le nom de la colonne précédé par le nom de la table. Pour des colonnes référencées dans une même table, le nom de la table n’est pas requis dans la formule. Cela permet de raccourcir de longue formules référençant de nombreuses colonnes et d’améliorer leur lisibilité. Toutefois, il est conseillé d’inclure le nom de la table dans les formules de mesure, même quand il s’agit d’une même table.

> [!NOTE]
> Si un nom de table contient des espaces, des mots clés réservés ou des caractères non autorisés, vous devez placer le nom de la table entre guillemets simples. Vous devez également placer un nom de table entre guillemets si le nom contient des caractères en dehors de la plage de caractères alphanumériques ANSI, que vos paramètres régionaux prennent en charge ou non le jeu de caractères.
> 
> 

Il est important que vos formules aient une syntaxe correcte. Dans la plupart des cas, si la syntaxe n’est pas correcte, une erreur de syntaxe est renvoyée. Dans d’autres cas, la syntaxe peut être correcte, mais les valeurs retournées peuvent ne pas être telles que prévues. L’éditeur DAX de Power BI Desktop offre une fonctionnalité de suggestions qui vous permet de créer des formules syntaxiquement correctes en vous aidant à sélectionner les éléments appropriés.

Nous allons créer une formule simple. Cette tâche vous aidera à mieux comprendre la syntaxe des formules et la manière dont la fonctionnalité de suggestions dans la barre de formule peut vous aider.

### <a name="task-create-a-measure-formula"></a>Tâche : créer une formule de mesure
Pour effectuer cette tâche, vous devez ouvrir le fichier Contoso Sales Sample Power BI Desktop.
    
1. Dans la vue Rapport, cliquez avec le bouton droit sur la table **Sales** figurant dans la liste des champs, puis cliquez sur Nouvelle mesure.
    
2. Dans la barre de formule, remplacez **Mesure** en tapant un nouveau nom de mesure, Previous Quarter Sales.
    
3. Après le signe égal, tapez les premières lettres **CAL**, puis double-cliquez sur la fonction que vous souhaitez utiliser. Dans cette formule, vous souhaitez utiliser la fonction **CALCULATE**.

   Vous utilisez la fonction CALCULATE pour filtrer les montants que vous souhaitez additionner par un argument que vous passez à la fonction CALCULATE. Ceci porte le nom d’imbrication de fonctions. La fonction CALCULATE possède au moins deux arguments. Le premier est l’expression à évaluer et le second est un filtre.
   
4. Après la parenthèse ouvrante **(** de la fonction **CALCULATE**, tapez **SUM** suivi d’un autre parenthèse ouvrante **(**. Nous devons à présent passer un argument à la fonction SUM.

5. Commencez à taper **Sal**, puis sélectionnez **Sales [SalesAmount]**, suivi d’une parenthèse fermante **)**. Il s’agit du premier argument de l’expression de votre fonction CALCULATE.
    
6. Tapez une virgule (**,**) suivie d’un espace pour spécifier le premier filtre, puis tapez **PREVIOUSQUARTER**. Il s’agit de notre filtre.
    
   La fonction temporelle PREVIOUSQUARTER sert à filtrer les résultats de SUM sur la base du trimestre précédent.
    
7. Après la parenthèse ouvrante **(** de la fonction PREVIOUSQUARTER, tapez **Calendar[DateKey]**.
    
   La fonction PREVIOUSQUARTER possède un seul argument, une colonne contenant une plage de dates contiguë. Dans notre cas, il s’agit de la colonne DateKey de la table Calendar.
    
8. Vérifiez que les deux arguments passés aux fonctions PREVIOUSQUARTER et CALCULATE sont fermés en tapant deux parenthèses fermantes **))**.
    
   La formule doit maintenant ressembler à ceci :
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
9. Cliquez sur la coche ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) dans la barre de formule, ou appuyez sur Entrée pour valider la formule et l’ajouter au modèle.

Vous avez réussi ! Vous venez de créer une mesure à l’aide de DAX et pas l’une des plus simples, qui plus est. Cette formule calcule le total des ventes du trimestre précédent en fonction des filtres appliqués dans un rapport. Par exemple, si vous placez SalesAmount et votre nouvelle mesure Previous Quarter Sales dans un graphique, puis ajoutez Year et QuarterOfYear comme segments, vous obtenez le résultat suivant :

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Plusieurs aspects importants des formules DAX viennent de vous être présentées. Tout d’abord, cette formule incluait deux fonctions. Notez que [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx), fonction à intelligence temporelle, est imbriquée en tant qu’argument passé à [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx), fonction de filtre. Les formules DAX peuvent contenir jusqu’à 64 fonctions imbriquées. Il est peu probable qu’une formule contienne jamais autant de fonctions imbriquées. En fait, une telle formule serait très difficile à créer et déboguer, et ne serait probablement pas très rapide non plus.

Dans cette formule, vous avez également utilisé des filtres. Les filtres limitent ce qui est calculé. Dans le cas présent, vous avez sélectionné un filtre en tant qu’argument, qui est en fait le résultat d’une autre fonction. Vous en apprendrez davantage sur les filtres ultérieurement.

Enfin, vous avez utilisé la fonction CALCULATE. Il s’agit de l’une des fonctions les plus puissantes de DAX. Quand vous créerez des modèles et des formules plus complexes, vous utiliserez probablement souvent cette fonction. L’étude de la fonction CALCULATE dépasse le cadre de cet article, mais au fur et à mesure que vos connaissances de DAX grandiront, portez une attention particulière à cette fonction.

### <a name="syntax-quickquiz"></a>Questionnaire rapide sur la syntaxe
1. À quoi sert ce bouton figurant sur la barre de formule ?
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Qu’est-ce qui entoure toujours un nom de colonne dans une formule DAX ?

Les réponses sont fournies à la fin de cet article.

### <a name="functions"></a>Fonctions
Les fonctions sont des formules prédéfinies qui effectuent des calculs en utilisant des valeurs spécifiques, appelées arguments, dans un ordre particulier ou dans une structure particulière. Les arguments peuvent être des fonctions, une formule, une expression, des références de colonne, des nombres, du texte, des valeurs logiques telles que TRUE ou FALSE, ou des constantes.

DAX comprend des fonctions des catégories suivantes : [Date et heure](https://msdn.microsoft.com/library/ee634786.aspx), [Time Intelligence](https://msdn.microsoft.com/library/ee634763.aspx), [Information](https://msdn.microsoft.com/library/ee634552.aspx), [Logique](https://msdn.microsoft.com/library/ee634365.aspx), [Mathématique](https://msdn.microsoft.com/library/ee634241.aspx), [Statistique](https://msdn.microsoft.com/library/ee634822.aspx), [Texte](https://msdn.microsoft.com/library/ee634938.aspx), [Parent/enfant](https://msdn.microsoft.com/library/mt150102.aspx) et [Autre](https://msdn.microsoft.com/library/mt150101.aspx). Si vous connaissez bien les fonctions dans les formules Excel, un grande nombre des fonctions DAX vous paraîtront similaires. Toutefois, les fonctions DAX sont uniques du fait des particularités suivantes :

* Une fonction DAX fait toujours référence à une colonne ou à une table entière. Si vous souhaitez utiliser uniquement des valeurs particulières d’une table ou d’une colonne, vous pouvez ajouter des filtres à la formule.
* Si vous devez personnaliser des calculs ligne par ligne, DAX fournit des fonctions qui vous permettent d’utiliser la valeur de la ligne actuelle ou une valeur associée comme type d’argument, afin d’effectuer des calculs qui varient selon le contexte. Vous en apprendrez davantage sur le contexte ultérieurement.
* DAX inclut de nombreuses fonctions qui retournent une table plutôt qu’une valeur. Cette table n’est pas affichée, mais elle est utilisée comme entrée pour d’autres fonctions. Par exemple, vous pouvez récupérer une table et compter les valeurs distinctes qu’elle contient, ou calculer des sommes dynamiques sur l’ensemble des tables ou colonnes filtrées.
* DAX inclut une large variété de fonctions Time Intelligence. Ces fonctions vous permettent de définir ou de sélectionner des plages de dates, et d’effectuer des calculs dynamiques basés sur ces plages. Par exemple, vous pouvez comparer des sommes sur des périodes parallèles.
* Excel possède une fonction très populaire, RECHERCHEV. Les fonctions DAX n’acceptent pas une cellule ou une plage de cellules en tant que référence comme RECHERCHEV dans Excel. Les fonctions DAX acceptent une colonne ou une table comme référence. Gardez à l’esprit que vous utilisez un modèle de données relationnelles dans Power BI Desktop. La recherche de valeurs dans une autre table est vraiment très simple et, dans la plupart des cas, vous n’avez pas besoin de créer de formule du tout.
  
  Comme vous pouvez le voir, les fonctions DAX peuvent vous aider à créer des formules très puissantes. Nous avons vraiment à peine abordé les principes élémentaires des fonctions. Au fur et à mesure que vos compétences DAX se développeront, vous créerez des formules en utilisant de nombreuses fonctions différentes. La page [Informations de référence sur les fonctions DAX](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference) est l’une des meilleures ressources pour découvrir chaque fonction DAX en détail.

### <a name="functions-quickquiz"></a>Questionnaire rapide sur les fonctions
1. À quoi une fonction fait-elle toujours référence ?
2. Une formule peut-elle contenir plusieurs fonctions ?
3. Quelle catégorie de fonctions utiliseriez-vous pour concaténer deux chaînes de texte en une seule chaîne ?

Les réponses sont fournies à la fin de cet article.

### <a name="context"></a>Contexte
Le contexte représente l’un des concepts DAX les plus importants. Il existe deux types de contexte dans DAX, le contexte de ligne et le contexte de filtre. Examinons tout d’abord le contexte de ligne.

**Contexte de ligne**

La façon la plus simple de considérer le contexte de ligne est de penser à la ligne actuelle. Ce contexte s’applique chaque fois qu’une formule a une fonction qui applique des filtres pour identifier une ligne unique dans une table. La fonction applique de manière inhérente un contexte de ligne pour chaque ligne de la table qu’elle filtre. Ce type de contexte de ligne s’applique généralement aux mesures.

**Contexte de filtre**

Le contexte de filtre est un peu plus difficile à comprendre que le contexte de ligne. Vous pouvez aisément considérer le contexte de filtre comme : un ou plusieurs filtres appliqués dans un calcul qui détermine un résultat ou une valeur.

Le contexte de filtre ne se substitue pas au contexte de ligne. Il s’applique plutôt en plus du contexte de ligne. Par exemple, pour limiter encore les valeurs à inclure dans un calcul, vous pouvez appliquer un contexte de filtre qui non seulement spécifie le contexte de ligne, mais spécifie également une valeur particulière (filtre) dans ce contexte de ligne.

Le contexte de filtre est facilement visible dans vos rapports. Par exemple, quand vous ajoutez TotalCost à une visualisation et ajoutez ensuite Year et Region, vous définissez un contexte de filtre qui sélectionne un sous-ensemble de données basées sur une année et une région données.

Pourquoi le contexte de filtre est-il si important dans DAX ? Bien que le contexte de filtre puisse être appliqué aisément en ajoutant des champs à une visualisation, le contexte de filtre peut également être appliqué dans une formule DAX en définissant un filtre à l’aide de fonctions telles que ALL, RELATED, FILTER et CALCULATE, de relations et d’autres mesures et colonnes. Par exemple, examinons la formule suivante dans une mesure nommée Store Sales :

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Pour mieux comprendre cette formule, vous pouvez la décomposer, comme d’autres formules.

Cette formule inclut les éléments syntaxiques suivants :

**A.** Le nom de la mesure **Store Sales**.

**B.** L’opérateur signe égal (**=**) indique le début de la formule.

**C.** La fonction **CALCULATE** évalue une expression, en tant qu’argument, dans un contexte modifié par les filtres spécifiés.

**D.** Des parenthèses **()** entourent une expression contenant un ou plusieurs arguments.

**E.** Une mesure **[Total Sales]** dans la même table en tant qu’expression. La mesure Total Sales possède la formule : =SUM(Sales[SalesAmount]).

**F.** Une virgule (**,**) sépare le premier argument d’expression de l’argument de filtre.

**G.** La colonne complètement référencée, **Channel[ChannelName]**. Il s’agit du contexte de ligne. Chaque ligne de cette colonne spécifie un canal : Store, Online, etc.

**H.** La valeur particulière, **Store** en tant que filtre. Il s’agit du contexte de filtre.

Cette formule garantit que seuls les prix de vente définis par la mesure Total Sales (total des ventes) sont calculés uniquement pour les lignes de la colonne Channel[ChannelName] contenant la valeur « Store », en tant que filtre.

Comme vous pouvez l’imaginer, la possibilité de définir le contexte de filtre dans une formule offre d’immenses opportunités et de puissantes fonctionnalités. Pouvoir référencer uniquement une valeur particulière dans une table liée en est un simple exemple. Ne vous inquiétez pas si vous ne comprenez pas encore complètement le concept de contexte. Au fur et à mesure que vous créerez vos propres formules, vous comprendrez mieux le contexte et pourquoi il est si important dans DAX.

### <a name="context-quickquiz"></a>Questionnaire rapide sur le contexte
1. Quels sont les deux types de contexte ?
2. Qu’est-ce qu’un contexte de filtre ?
3. Qu’est-ce qu’un contexte de ligne ?

Les réponses sont fournies à la fin de cet article.

## <a name="summary"></a>Résumé
Maintenant que vous avez acquis une compréhension élémentaire des concepts les plus importants de DAX, vous pouvez commencer à créer par vous-même des formules DAX pour des mesures. Le langage DAX peut en effet être un peu difficile à apprendre, mais de nombreuses ressources sont à votre disposition pour vous aider. Après avoir lu cet article et essayé de créer quelques formules personnalisées, vous pouvez découvrir d’autres concepts et formules DAX qui pourront vous aider à résoudre des problèmes dans votre entreprise. De nombreuses ressources DAX sont à votre disposition. La page [Informations de référence sur DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) est la plus importante.

Le langage DAX est présent déjà depuis plusieurs années dans d’autres outils décisionnels de Microsoft, tels que Power Pivot et les modèles tabulaires Analysis Services, et ces outils fournissent des informations très utiles. Vous trouverez plus d’informations dans des manuels, des livres blancs et des blogs édités par Microsoft et par des professionnels de haut rang dans le secteur décisionnel. Le site Technet [DAX Resource Center Wiki](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) est également un excellent point de départ.

### <a name="quickquiz-answers"></a>Réponses aux questionnaires rapides
Syntaxe :

1. Valide et entre la mesure dans le modèle.
2. Des crochets [].

Fonctions :

1. Une table et une colonne.
2. Oui. Une formule DAX peuvent contenir jusqu’à 64 fonctions imbriquées.
3. [Fonctions de texte](https://msdn.microsoft.com/library/ee634938.aspx).

Contexte :

1. Le contexte de ligne et le contexte de filtre.
2. Un ou plusieurs filtres dans un calcul qui déterminent une valeur unique.
3. La ligne actuelle.

