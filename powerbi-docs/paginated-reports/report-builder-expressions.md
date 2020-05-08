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
ms.openlocfilehash: 96c62fec55f87a31970b624a79314656ced0c159
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921122"
---
# <a name="expressions-in-power-bi-report-builder"></a>Expressions dans le Générateur de rapports Power BI
  Les expressions sont largement utilisées dans les rapports paginés Power BI Report Builder pour récupérer, calculer, afficher, regrouper, trier, filtrer, paramétrer et mettre en forme les données. 
  
  Vous pouvez définir un grand nombre de propriétés d’élément de rapport dans une expression. Les expressions vous permettent de contrôler le contenu, la conception et l’interactivité de votre rapport. Les expressions sont écrites en Microsoft Visual Basic, enregistrées dans la définition de rapport et évaluées par le processeur de rapports quand vous exécutez le rapport.  
  
 Contrairement aux applications comme Microsoft Office Excel où vous utilisez les données directement dans une feuille de calcul, dans un rapport, vous utilisez des expressions qui sont des espaces réservés pour les données. Pour voir les données réelles des expressions évaluées, vous devez afficher un aperçu du rapport. Quand vous exécutez le rapport, le processeur de rapports évalue chaque expression en combinant les données de rapport et les éléments de disposition de rapport comme les tableaux et les graphiques.  
  
 Lorsque vous concevez un rapport, de nombreuses expressions pour les éléments de rapport sont définies pour vous. Par exemple, quand vous faites glisser un champ du volet de données vers une cellule de tableau sur l’aire de conception du rapport, la valeur de zone de texte est définie dans une expression simple pour le champ. Dans la figure suivante, le volet Données de rapport affiche les champs de jeu de données ID, Name, SalesTerritory, Code et Sales. Trois champs ont été ajoutés au tableau : [Name], [Code] et [Sales]. La notation [Name] sur l’aire de conception représente l’expression sous-jacente `=Fields!Name.Value`.  
  
![Mode Création du Générateur de rapports](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 Quand vous affichez un aperçu du rapport, le processeur de rapports combine la région de données de tableau avec les données réelles de la connexion de données et affiche une ligne dans le tableau pour chaque ligne du jeu de résultats.  
  
 Pour entrer manuellement des expressions, sélectionnez un élément sur l’aire de conception et utilisez les menus contextuels et les boîtes de dialogue pour définir les propriétés de l’élément. Quand vous voyez le bouton ***(fx)*** ou la valeur `<Expression>` dans une liste déroulante, vous savez que vous pouvez définir la propriété dans une expression. 
  
##  <a name="understanding-simple-and-complex-expressions"></a><a name="Types"></a> Présentation d’expressions simples et complexes  
 Les expressions commencent par un signe égal (=) et sont écrites en Microsoft Visual Basic. Les expressions peuvent inclure une combinaison de constantes, d’opérateurs et de références à des valeurs prédéfinies (champs, collections et fonctions) et à du code externe ou personnalisé.  
  
 Vous pouvez utiliser des expressions pour spécifier la valeur d’un grand nombre de propriétés d’élément de rapport. Les propriétés les plus courantes sont les valeurs pour les zones de texte et le texte des espaces réservés. En règle générale, si une zone de texte contient une seule expression, l’expression est la valeur de la propriété de zone de texte. Si une zone de texte contient plusieurs expressions, chaque expression est la valeur du texte d’espace réservé dans la zone de texte.  
  
 Par défaut, les expressions s’affichent sur l’aire de conception du rapport en tant qu’expressions *simples* ou *complexes*.  
  
-   **Simple** Une expression simple contient une référence à un seul élément dans une collection prédéfinie, par exemple, un champ de jeu de données, un paramètre ou un champ prédéfini. Sur l’aire de conception, une expression simple apparaît entre crochets. Par exemple, `[FieldName]` correspond à l’expression sous-jacente `=Fields!FieldName.Value`. Les expressions simples sont créées automatiquement lorsque vous créez la disposition du rapport et que vous faites glisser des éléments du volet Données de rapport vers l’aire de conception. Pour plus d’informations sur les symboles qui représentent les différentes collections prédéfinies, consultez [Présentation des symboles de préfixe pour les expressions simples](#DisplayText).  
  
-   **Complexe** Une expression complexe contient des références à plusieurs références, opérateurs et appels de fonction prédéfinis. Une expression complexe apparaît sous la forme <\<Expr>> quand la valeur de l’expression inclut plusieurs références simples. Pour voir l’expression, pointez dessus et utilisez l’info-bulle. Pour modifier l’expression, ouvrez-la dans la boîte de dialogue **Expression**.  
  
 La figure suivante montre des expressions simples et complexes typiques pour les zones de texte et le texte des espaces réservés.  
  
![Format par défaut des expressions du Générateur de rapports](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Pour afficher des exemples de valeurs à la place de texte pour les expressions, appliquez une mise en forme à la zone de texte ou au texte d’espace réservé. La figure suivante montre l’aire de conception du rapport activée pour afficher des exemples de valeurs :  
  
![Exemple de format des expressions du Générateur de rapports](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="understanding-prefix-symbols-in-simple-expressions"></a><a name="DisplayText"></a> Présentation des symboles de préfixe dans des expressions simples  

Les expressions simples utilisent des symboles pour indiquer si la référence est à un champ, un paramètre, une collection prédéfinie ou la collection ReportItems. Le tableau suivant montre des exemples de texte d’affichage et d’expression :  
  
|Article|Exemple de texte d’affichage|Exemple de texte d’expression|  
|----------|--------------------------|-----------------------------|  
|Champs de jeu de données|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Paramètres de rapport|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Champs prédéfinis|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Caractères littéraux utilisés pour le texte d’affichage|`\[Sales\]`|`[Sales]`|  
  
##  <a name="writing-complex-expressions"></a><a name="References"></a> Écriture d’expressions complexes  
 Les expressions peuvent inclure des références à des fonctions, des opérateurs, des constantes, des champs, des paramètres, des éléments de collections prédéfinies, ainsi qu’à du code personnalisé incorporé ou à des assemblys personnalisés.  
  
 Le tableau suivant liste les types de références que vous pouvez inclure dans une expression :  
  
|Références|Description|Exemple|  
|----------------|-----------------|-------------|  
|Constantes|Décrit les constantes auxquelles vous pouvez accéder de manière interactive pour les propriétés qui demandent des valeurs de constante comme les couleurs de police.|`="Blue"`|  
|Operators|Décrit les opérateurs que vous pouvez utiliser pour combiner des références dans une expression. Par exemple, l’opérateur **&** est utilisé pour concaténer des chaînes.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Collections prédéfinies|Décrit les collections prédéfinies que vous pouvez inclure dans une expression, comme `Fields`, `Parameters` et `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Fonctions d’agrégation et de rapport prédéfinies|Décrit les fonctions prédéfinies, comme `Sum` ou `Previous`, auxquelles vous pouvez accéder à partir d’une expression.|`=Previous(Sum(Fields!Sales.Value))`|  
|Références à du code et des assemblys personnalisés dans les expressions dans le Générateur de rapports |Décrit comment vous pouvez accéder aux classes CLR prédéfinies `xref:System.Math` et `xref:System.Convert`, à d’autres classes CLR, aux fonctions de la bibliothèque runtime Visual Basic ou aux méthodes à partir d’un assembly externe.<br /><br /> Décrit comment vous pouvez accéder à du code personnalisé qui est incorporé dans votre rapport, ou que vous compilez et installez en tant qu’un assembly personnalisé sur le client de rapports et le serveur de rapports.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="validating-expressions"></a><a name="Valid"></a> Validation des expressions  
 Lorsque vous créez une expression pour une propriété d’élément de rapport spécifique, les références que vous pouvez inclure dans une expression dépendent des valeurs que la propriété d’élément de rapport peut accepter et de l’étendue dans laquelle la propriété est évaluée. Par exemple :  
  
-   Par défaut, l’expression [Sum] calcule la somme des données qui sont dans l’étendue au moment où l’expression est évaluée. Pour une cellule de tableau, l’étendue dépend des appartenances aux groupes de lignes et de colonnes. 
  
-   Pour la valeur d’une propriété de police, la valeur doit correspondre au nom d’une police.  
  
-   La syntaxe de l’expression est validée au moment de la conception. La validation de l’étendue de l’expression a lieu quand vous publiez le rapport. Pour la validation qui dépend de données réelles, les erreurs peuvent être détectées uniquement au moment de l’exécution. Certaines de ces expressions produisent #Error comme message d’erreur dans le rapport rendu. 

## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
