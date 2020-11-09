---
title: Expressions dans le Générateur de rapports Power BI
description: Les expressions sont largement utilisées dans les rapports paginés Power BI Report Builder pour récupérer, calculer, afficher, regrouper, trier, filtrer, paramétrer et mettre en forme les données.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7dbda608fcab3457a45c4ad93abf7143a19abcd1
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298182"
---
# <a name="expressions-in-power-bi-report-builder"></a>Expressions dans le Générateur de rapports Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Les expressions sont largement utilisées dans les rapports paginés Power BI Report Builder pour récupérer, calculer, afficher, regrouper, trier, filtrer, paramétrer et mettre en forme les données. 
  
De nombreuses propriétés d'élément de rapport peuvent avoir la valeur d'une expression. Les expressions vous aident à contrôler le contenu, la conception et l'interactivité de votre rapport. Les expressions sont écrites en Microsoft Visual Basic, enregistrées dans la définition de rapport et évaluées par le processeur de rapports quand vous exécutez le rapport.  
  
 Contrairement aux applications comme Microsoft Office Excel où vous utilisez les données directement dans une feuille de calcul, dans un rapport, vous utilisez des expressions qui sont des espaces réservés pour les données. Pour consulter les données effectives des expressions évaluées, vous devez afficher un aperçu du rapport. Lorsque vous exécutez le rapport, le processeur de rapports évalue chaque expression au moment de combiner les données de rapport et les éléments de disposition du rapport tels que les tableaux et les graphiques.  
  
 Lorsque vous concevez un rapport, de nombreuses expressions relatives aux éléments de rapport sont définies automatiquement. Par exemple, lorsque vous faites glisser un champ du volet de données vers une cellule de tableau sur l'aire de conception du rapport, la zone de texte prend la valeur d'une expression simple pour le champ. Dans l'illustration suivante, le volet des données de rapport affiche l'ID des champs du dataset, Name, SalesTerritory, Code et Sales. Trois champs ont été ajoutés à la table : [Name], [Code] et [Sales]. La notation [Name] sur l'aire de conception représente l'expression sous-jacente `=Fields!Name.Value`.  
  
![Mode Conception du Générateur de rapports](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Lorsque vous affichez un aperçu du rapport, le processeur de rapports combine la région de données de table avec les données effectives de la connexion de données, puis affiche une ligne dans la table pour chaque ligne du jeu de résultats.  
  
 Pour entrer manuellement des expressions, sélectionnez un élément dans l'aire de conception, puis utilisez les menus contextuels et boîtes de dialogue pour définir les propriétés de l'élément. Quand vous voyez le bouton * **(fx)** _ ou la valeur `<Expression>` dans une liste déroulante, vous savez que vous pouvez définir la propriété dans une expression. 
  
##  <a name="understanding-simple-and-complex-expressions"></a><a name="Types"></a> Présentation d’expressions simples et complexes  
 Les expressions commencent par un signe égal (=) et sont écrites en Microsoft Visual Basic. Les expressions peuvent se composer d'une combinaison de constantes, d'opérateurs et de références à des valeurs prédéfinies (champs, collections et fonctions) ainsi qu'à du code externe ou personnalisé.  
  
 Vous pouvez utiliser des expressions pour spécifier la valeur de nombreuses propriétés d'élément de rapport. Les propriétés les plus usuelles sont les valeurs des zones de texte et du texte de l'espace réservé. En règle générale, si une zone de texte contient une seule expression, celle-ci représente la valeur de la propriété de la zone de texte. Si une zone de texte contient plusieurs expressions, chaque expression représente la valeur du texte de l'espace réservé dans la zone de texte.  
  
 Par défaut, les expressions s’affichent dans l’aire de conception du rapport en tant qu’expressions _simples* ou *complexes*.  
  
-   **Simple** : une expression simple contient une référence à un élément unique dans une collection intégrée, par exemple un champ de dataset, un paramètre ou un champ prédéfini. Sur l'aire de conception, une expression simple apparaît entre parenthèses. Par exemple, `[FieldName]` correspond à l’expression sous-jacente `=Fields!FieldName.Value`. Les expressions simples sont créées automatiquement lorsque vous créez la mise en page du rapport et que vous faites glisser des éléments du volet des données de rapport vers l'aire de conception. Pour plus d’informations sur les symboles qui représentent les différentes collections intégrées, consultez [Présentation des symboles de préfixe dans les expressions simples](#DisplayText).  
  
-   **Complexe** : une expression complexe contient des références à plusieurs références intégrées, opérateurs et appels de fonction. Une expression complexe se présente sous la forme <\<Expr>> quand la valeur d’expression inclut plus qu’une simple référence. Pour consulter l'expression, pointez sur cette dernière et utilisez l'info-bulle. Pour modifier l’expression, ouvrez-la dans la boîte de dialogue **Expression** .  
  
 L'illustration suivante montre des expressions simples et complexes classiques pour des zones de texte et du texte d'espace réservé.  
  
![Format par défaut des expressions du Générateur de rapports](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Pour afficher des exemples de valeurs à la place du texte pour les expressions, appliquez la mise en forme à la zone de texte ou au texte de l'espace réservé. L'illustration suivante montre l'aire de conception du rapport de manière à afficher les exemples de valeurs :  
  
![Exemple de format des expressions du Générateur de rapports](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="understanding-prefix-symbols-in-simple-expressions"></a><a name="DisplayText"></a> Présentation des symboles de préfixe dans des expressions simples  

Les expressions simples utilisent des symboles pour indiquer si la référence est une référence à un champ, un paramètre, une collection intégrée ou la collection ReportItems. Le tableau suivant présente des exemples de texte affiché et de texte d'expression :  
  
|Élément|Exemple de texte affiché|Exemple de texte d'expression|  
|----------|--------------------------|-----------------------------|  
|Champs de dataset|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Paramètres du rapport|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Champs prédéfinis|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Caractères littéraux utilisés pour le texte affiché|`\[Sales\]`|`[Sales]`|  
  
##  <a name="writing-complex-expressions"></a><a name="References"></a> Écriture d’expressions complexes  
 Les expressions peuvent inclure des références à des fonctions, des opérateurs, des constantes, des champs, des paramètres, des éléments provenant de collections intégrées, ainsi que des références à du code personnalisé incorporé ou à des assemblys personnalisés.  
  
 Le tableau suivant répertorie les types de références que vous pouvez inclure dans une expression :  
  
|References|Description|Exemple|  
|----------------|-----------------|-------------|  
|Constantes|Décrit les constantes auxquelles vous pouvez accéder de manière interactive pour les propriétés qui requièrent des valeurs constantes ; par exemple les couleurs de police.|`="Blue"`|  
|Opérateurs|Décrit les opérateurs que vous pouvez utiliser pour combiner des références dans une expression. Par exemple, l’opérateur **&** sert à concaténer des chaînes.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Collections intégrées|Décrit les collections intégrées que vous pouvez inclure dans une expression ; par exemple, `Fields`, `Parameters`et `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Fonctions de rapport et d'agrégation intégrées|Décrit les fonctions intégrées, telles que `Sum` ou `Previous`, auxquelles vous pouvez accéder à partir d’une expression.|`=Previous(Sum(Fields!Sales.Value))`|  
|Références à du code et des assemblys personnalisés dans les expressions dans le Générateur de rapports |Décrit comment vous pouvez accéder aux classes CLR prédéfinies `xref:System.Math` et `xref:System.Convert`, à d’autres classes CLR, aux fonctions de la bibliothèque runtime Visual Basic ou aux méthodes à partir d’un assembly externe.<br /><br /> Explique comment vous pouvez accéder à du code personnalisé qui est incorporé dans votre rapport ou que vous compilez et installez en tant qu'assembly personnalisé à la fois sur le client de rapports et sur le serveur de rapports.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="validating-expressions"></a><a name="Valid"></a> Validation des expressions  
 Lorsque vous créez une expression pour une propriété d'élément de rapport spécifique, les références que vous pouvez inclure dans l'expression dépendent des valeurs que la propriété d'élément de rapport peut accepter et de l'étendue dans laquelle la propriété est évaluée. Par exemple :  
  
-   Par défaut, l'expression [Sum] calcule la somme des données qui se trouvent dans l'étendue au moment où l'expression est évaluée. Pour une cellule de tableau, l'étendue dépend des membres du groupe de lignes et de colonnes. 
  
-   Pour une propriété Font, la valeur doit correspondre au nom d’une police.  
  
-   La syntaxe de l'expression est validée au moment du design. La validation de l'étendue de l'expression se produit lorsque vous publiez le rapport. Lorsque la validation dépend des données effectives, les erreurs ne peuvent être détectées qu'au moment de l'exécution. Certaines de ces expressions produisent le message d'erreur #Error dans le rapport rendu. 

## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
