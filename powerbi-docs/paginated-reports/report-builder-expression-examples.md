---
title: Exemples d’expressions dans le Générateur de rapports Power BI
description: Les expressions sont fréquemment utilisées dans les rapports paginés Power BI Report Builder pour contrôler le contenu et l’apparence des rapports.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3a24724e67a931860296983fe3a116137d3b5361
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859518"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Exemples d’expressions dans le Générateur de rapports Power BI
Les expressions sont fréquemment utilisées dans les rapports paginés Power BI Report Builder pour contrôler le contenu et l’apparence des rapports. Les expressions sont écrites en Microsoft Visual Basic et elles peuvent utiliser des fonctions intégrées, du code personnalisé, des variables de rapport et de groupe, et des variables définies par l’utilisateur. Les expressions commencent par un signe égal (=).   

Cette rubrique fournit des exemples d’expressions qui peuvent être utilisées pour les tâches courantes dans un rapport.  
  
-   [Fonctions Visual Basic](#VisualBasicFunctions) Exemples pour les fonctions Visual Basic de date, de chaîne, de conversion et conditionnelles.  
  
-   [Fonctions de rapport](#ReportFunctions) Exemples pour les agrégats et d’autres fonctions de rapport intégrées.  
  
-   [Apparence des données de rapport](#AppearanceofReportData) Exemples pour la modification de l’apparence d’un rapport.  
  
-   [Propriétés](#Properties) Exemples pour la définition de propriétés d’éléments de rapport pour contrôler la mise en forme ou la visibilité.  
  
-   [Paramètres](#Parameters) Exemples d’utilisation de paramètres dans une expression.  
  
-   [Code personnalisé](#CustomCode) Exemples de code personnalisé incorporé.  
  
Pour plus d’informations sur les expressions simples et complexes, où vous pouvez utiliser des expressions et les types de références que vous pouvez inclure dans une expression, consultez les rubriques sous [Expressions dans le Générateur de rapports Power BI](report-builder-expressions.md). 
  
## <a name="functions"></a>Fonctions  
 Beaucoup d’expressions d’un rapport contiennent des fonctions. Vous pouvez mettre en forme des données, appliquer une logique et accéder aux métadonnées des rapports en utilisant ces fonctions. Vous pouvez écrire des expressions qui utilisent des fonctions de la bibliothèque de runtime Microsoft Visual Basic et des espaces de noms `xref:System.Convert` et `xref:System.Math`. Vous pouvez ajouter des références à des fonctions dans du code personnalisé. Vous pouvez également utiliser des classes de Microsoft .NET Framework, notamment `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Fonctions Visual Basic  
 Vous pouvez utiliser des fonctions Visual Basic pour manipuler les données qui sont affichées dans les zones de texte ou qui sont utilisées pour les paramètres, les propriétés ou d’autres zones du rapport. Cette section fournit des exemples montrant certaines de ces fonctions. Pour plus d’informations, consultez [Membres de la bibliothèque runtime Visual Basic](/dotnet/visual-basic/language-reference/runtime-library-members) sur MSDN.  
  
 Le .NET Framework fournit de nombreuses options de format personnalisé, par exemple pour les formats de date spécifiques. Pour plus d’informations, voir [Types de mises en forme](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Fonctions mathématiques  
  
-   La fonction **Round** est utile pour arrondir les nombres à l’entier le plus proche. L’expression suivante arrondit 1,3 à 1 :  
  
    ```  
    = Round(1.3)  
    ```  
  
     Vous pouvez également écrire une expression pour arrondir une valeur à un multiple que vous spécifiez, de façon similaire à la fonction **MRound** dans Excel. Multiplie la valeur par un facteur qui crée un entier, arrondit le nombre, puis divise par le même facteur. Par exemple, pour arrondir 1,3 au multiple plus proche de 0,2 (1,4), utilisez l’expression suivante :  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Fonctions de date  
  
-   La fonction **Today** fournit la date actuelle. Cette expression peut être utilisée dans une zone de texte pour afficher la date sur le rapport ou dans un paramètre pour filtrer les données en fonction de la date actuelle.  
  
    ```  
    =Today()  
    ```  
  
-   Utilisez la fonction **DateInterval** pour extraire une partie spécifique d’une date. Voici quelques paramètres de **DateInterval** valides :

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Par exemple, cette expression affiche le numéro de la semaine de l’année en cours pour la date du jour :
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   La fonction **DateAdd** est utile pour fournir une plage de dates basées sur un seul paramètre. L’expression suivante fournit une date qui est six mois après la date à donnée dans un paramètre nommé *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   La fonction **Year** affiche l’année pour une date particulière. Vous pouvez utiliser ceci pour regrouper des dates ou pour afficher l’année en tant qu’étiquette pour un ensemble de dates. Cette expression fournit l’année pour un groupe donné de dates de commandes. Vous pouvez aussi utiliser la fonction **Month** et d’autres fonctions pour manipuler des dates. Pour plus d’informations, consultez la documentation de Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Vous pouvez combiner des fonctions dans une expression pour personnaliser le format. L’expression suivante change le format d’une date de la forme mois-jour-année en mois-semaine-numéro de la semaine. Par exemple, 12/23/2009 en Décembre Semaine 3 :  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Quand elle est utilisée comme champ calculé dans un jeu de données, vous pouvez utiliser cette expression sur un graphique pour agréger les valeurs par semaine dans chaque mois.  
  
-   L’expression suivante met en forme la valeur SellStartDate au format MMM-AA. Le champ SellStartDate est un type de données datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   L’expression suivante met en forme la valeur SellStartDate au format jj/MM/aaaa. Le champ SellStartDate est un type de données datetime.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   La fonction **CDate** convertit la valeur en date. La fonction **Now** retourne une valeur de date contenant la date/heure actuelle d’après votre système. **DateDiff** retourne une valeur de type Long spécifiant le nombre d’intervalles de temps entre deux valeurs de type Date.  
  
     L’exemple suivant affiche la date de début de l’année en cours  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   L’exemple suivant affiche la date de début pour le mois précédent en fonction du mois en cours.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   L’expression suivante génère l’intervalle en années entre SellStartDate et LastReceiptDate. Ces champs sont dans deux jeux de données différents, DataSet1 et DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   La fonction **DatePart** retourne une valeur entière contenant le composant spécifié d’une valeur de type Date donnée. L’expression suivante retourne l’année pour la première valeur de SellStartDate dans DataSet1. L’étendue du jeu de données est spécifiée, car il existe plusieurs jeux de données dans le rapport.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   La fonction **DateSerial** retourne une valeur de type Date représentant une année, un mois et un jour spécifiés, avec l’heure définie sur minuit. L’exemple suivant affiche la date de fin pour le mois précédent en fonction du mois en cours.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Les expressions suivantes affichent différentes dates en fonction de la valeur d’un paramètre de date sélectionnée par l’utilisateur.  
  
|Description de l’exemple|Exemple|  
|-------------------------|-------------|  
|Hier|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Il y a deux jours|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Il y a un mois|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Il y a deux mois|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Il y a un an|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Il y a deux ans|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Fonctions de chaîne  
  
-   Combiner plusieurs champs avec des opérateurs de concaténation et des constantes Visual Basic. L’expression suivante retourne deux champs, chacun sur une ligne distincte dans la même zone de texte :  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Mettez en forme les dates et les nombres dans une chaîne avec la fonction **Format**. L’expression suivante affiche les valeurs des paramètres *StartDate* et *EndDate* au format de date longue :  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Si la zone de texte contient seulement une date ou un nombre, vous devez utiliser la propriété Format de la zone de texte pour appliquer la mise en forme, au lieu de la fonction **Format** dans la zone de texte.  
  
-   Les fonctions **Right**, **Len** et **InStr** sont pratiques pour retourner une sous-chaîne, par exemple en réduisant *DOMAINE*\\*nom d’utilisateur* au seul nom d’utilisateur. L’expression suivante retourne la partie de la chaîne à droite d’une barre oblique inverse (\\) à partir d’un paramètre nommé *User* :  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     L’expression suivante retourne la même valeur que la précédente, mais en utilisant des membres de la classe `xref:System.String` du .NET Framework au lieu des fonctions Visual Basic :  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Afficher les valeurs sélectionnées à partir d’un paramètre à valeurs multiples. L’exemple suivant utilise la fonction **Join** pour concaténer les valeurs sélectionnées du paramètre *MySelection* en une seule chaîne, qui peut être définie comme une expression de la valeur d’une zone de texte dans un élément de rapport :  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     L’exemple suivant fait la même chose que l’exemple ci-dessus, mais affiche en plus une chaîne de texte avant la liste de valeurs sélectionnées.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   Les fonctions **Regex** de `xref:System.Text.RegularExpressions` du .NET Framework sont utiles pour la modification du format de chaînes existantes, par exemple pour la mise en forme d’un numéro de téléphone. L’expression suivante utilise la fonction **Replace** pour changer le format d’un numéro de téléphone à dix chiffres d’un champ de « *nnn*-*nnn*-*nnnn* » en « (*nnn*) *nnn*-*nnnn* » :  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Vérifiez que la valeur de Fields!Phone.Value ne contient pas d’espaces supplémentaires et est de type `xref:System.String`.  
  
### <a name="lookup"></a>Lookup  
  
-   En spécifiant un champ clé, vous pouvez utiliser la fonction **Lookup** pour récupérer une valeur dans un jeu de données pour une relation un-à-un, par exemple une paire clé-valeur. L’expression suivante affiche le nom du produit à partir d’un jeu de données (« Product »), étant donné l’identificateur du produit à mettre en correspondance :  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   En spécifiant un champ clé, vous pouvez utiliser la fonction **LookupSet** pour récupérer un ensemble de valeurs dans un jeu de données pour une relation un-à-plusieurs. Par exemple, une personne peut avoir plusieurs numéros de téléphone. Dans l’exemple suivant, supposons que le jeu de données PhoneList contient un identificateur de personne et un numéro de téléphone dans chaque ligne. **LookupSet** retourne un tableau de valeurs. L’expression suivante combine les valeurs de retour en une seule chaîne et affiche la liste des numéros de téléphone de la personne spécifiée par ContactID :  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Fonctions de conversion  
 Vous pouvez utiliser des fonctions Visual Basic pour convertir un champ d’un type de données en un autre type de données. Les fonctions de conversion peuvent être utilisées pour convertir le type de données par défaut d’un champ en un type de données nécessaire pour des calculs ou pour combiner du texte.  
  
-   L’expression suivante convertit la constante 500 en type Decimal pour la comparer à un type de données de devise Transact-SQL dans le champ Value d’une expression de filtre.  
  
    ```  
    =CDec(500)  
    ```  
  
-   L’expression suivante affiche le nombre de valeurs sélectionnées pour le paramètre à valeurs multiples *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Fonctions de décision  
  
-   La fonction **Iif** retourne une valeur parmi deux, selon que l’expression est vraie ou non. L’expression suivante utilise la fonction **Iif** pour retourner une valeur booléenne **True** si la valeur de `LineTotal` est supérieure à 100. Sinon, elle retourne **False** :  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Utilisez plusieurs fonctions **IIF** (on parle alors de « IIF imbriqués ») pour retourner une valeur parmi trois selon la valeur de `PctComplete`. L’expression suivante peut être placée dans la couleur de remplissage d’une zone de texte pour changer la couleur d’arrière-plan en fonction de la valeur présente dans la zone de texte.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Les valeurs supérieures ou égales à 10 s’affichent avec un arrière-plan vert, celles entre 1 et 9 s’affichent avec un arrière-plan bleu, et celles qui sont inférieures à 1 s’affichent avec un arrière-plan rouge.  
  
-   Une autre façon d’obtenir la même fonctionnalité est d’utiliser la fonction **Switch**. La fonction **Switch** est pratique quand vous avez trois conditions ou plus à tester. La fonction **Switch** retourne la valeur associée à la première expression d’une série qui s’évalue à true :  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Les valeurs supérieures ou égales à 10 s’affichent avec un arrière-plan vert, celles entre 1 et 9 s’affichent avec un arrière-plan bleu, celles égales à 1 s’affichent avec un arrière-plan jaune, et celles qui sont inférieures ou égales à 0 s’affichent avec un arrière-plan rouge.  
  
-   Tester la valeur du champ `ImportantDate`, et retourner « Red » si elle est antérieure de plus d’une semaine et « Blue » dans le cas contraire. Cette expression peut être utilisée pour contrôler la propriété Couleur d’une zone de texte dans un élément de rapport :  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Tester la valeur du champ `PhoneNumber` et retourner « No Value » si elle est **null** (**Nothing** en Visual Basic) ; sinon, retourner la valeur du numéro de téléphone. Cette expression peut être utilisée pour contrôler la valeur d’une zone de texte dans un élément de rapport.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Tester la valeur du champ `Department` et retourner un nom de sous-rapport ou **null** (**Nothing** en Visual Basic). Cette expression peut être utilisée pour les sous-rapports d’exploration conditionnelle.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Tester si la valeur d’un champ est null. Cette expression peut être utilisée pour contrôler la propriété **Masqué** d’un élément de rapport de type image. Dans l’exemple suivant, l’image spécifiée par le champ [LargePhoto] est affichée seulement si la valeur du champ n’est pas null.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   La fonction **MonthName** retourne une valeur de chaîne contenant le nom du mois spécifié. L’exemple suivant affiche NA dans le champ Month quand le champ contient la valeur 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Fonctions de rapport  
 Dans une expression, vous pouvez ajouter une référence à des fonctions de rapport supplémentaires qui manipulent les données dans un rapport. Cette section contient des exemples pour deux de ces fonctions. 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   La fonction **Sum** peut totaliser les valeurs dans un groupe ou une région de données. Cette fonction peut être pratique dans l’en-tête ou le pied de page d’un groupe. L’expression suivante affiche la somme des données dans le groupe ou la région de données Order :  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   Vous pouvez également utiliser la fonction **Sum** pour les calculs d’agrégats conditionnels. Par exemple, si un jeu de données a un champ nommé State (État) avec comme valeurs possibles Not Started (Non démarré), Started (Démarré) et Finished (Terminé), l’expression suivante, quand elle est placée dans un en-tête de groupe, calcule la somme agrégée pour la seule valeur « Finished » :  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   La fonction **RowNumber**, quand elle est utilisée dans une zone de texte au sein d’une région de données, affiche le numéro de ligne pour chaque instance de la zone de texte où l’expression apparaît. Cette fonction peut être pratique pour numéroter les lignes dans un tableau. Elle peut également être utile pour des tâches plus complexes, comme générer des sauts de page basés sur le nombre de lignes. Pour plus d’informations, consultez [Sauts de page](#PageBreaks) dans cette rubrique.  
  
     L’étendue que vous spécifiez pour **RowNumber** détermine quand la renumérotation commence. Le mot clé **Nothing** indique que la fonction commence le comptage à la première ligne dans la région de données la plus éloignée. Pour commencer le comptage dans des régions de données imbriquées, utilisez le nom de la région de données. Pour commencer le comptage dans un groupe, utilisez le nom du groupe.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> Apparence des données de rapport  
 Vous pouvez utiliser des expressions pour manipuler la façon dont les données apparaissent sur un rapport. Par exemple, vous pouvez afficher les valeurs de deux champs dans une même zone de texte, afficher des informations sur le rapport ou affecter la façon dont les sauts de page sont insérés dans le rapport.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> En-têtes et pieds de page  
 Quand vous concevez un rapport, vous pouvez afficher le nom du rapport et le numéro de page dans le pied de page. Pour cela, vous pouvez utiliser les expressions suivantes :  
  
-   L’expression suivante fournit le nom du rapport et l’heure à laquelle il a été exécuté. Elle peut être placée dans une zone de texte dans le pied de page ou le corps du rapport. L’heure est mise en forme avec la chaîne de mise en forme du .NET Framework pour la date courte :  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   L’expression suivante, placée dans une zone de texte dans le pied de page d’un rapport, fournit le numéro de page et le nombre total de pages du rapport :  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 Les exemples suivants décrivent comment afficher la première et la dernière valeur d’une page dans l’en-tête de page, de façon similaire à ce que vous pouvez trouver dans la liste d’un annuaire. L’exemple suppose qu’il existe une région de données contenant une zone de texte nommée `LastName`.  
  
-   L’expression suivante, placée dans une zone de texte sur le côté gauche de l’en-tête de page, fournit la première valeur de la zone de texte `LastName` sur la page :  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   L’expression suivante, placée dans une zone de texte sur le côté droit de l’en-tête de page, fournit la dernière valeur de la zone de texte `LastName` sur la page :  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 L’exemple suivant décrit comment afficher un total de la page. L’exemple suppose qu’il existe une région de données contenant une zone de texte nommée `Cost`.  
  
-   L’expression suivante, placée dans l’en-tête de page ou le pied de page, fournit la somme des valeurs de la zone de texte `Cost` pour la page :  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Vous pouvez référencer un seul élément de rapport par expression dans un en-tête de page ou un pied de page. Dans les expressions d’un en-tête de page ou d’un pied de page, vous pouvez aussi référencer le nom de la zone de texte, mais pas l’expression des données réelles dans la zone de texte.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Sauts de page  
 Dans certains rapports, vous voulez placer un saut de page à la fin d’un nombre spécifié de lignes, à la place ou en plus des sauts de page sur les groupes ou les éléments de rapport. Pour cela, créez un groupe qui contient les groupes ou les enregistrements détaillés de votre choix, ajoutez un saut de page au groupe, puis ajoutez une expression de groupe pour regrouper selon un nombre de lignes spécifié.  
  
-   L’expression suivante, quand elle est placée dans l’expression de groupe, affecte un numéro à chaque ensemble de 25 lignes. Quand un saut de page est défini pour le groupe, cette expression génère un saut de page toutes les 25 lignes.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Pour permettre à l’utilisateur de définir une valeur pour le nombre de lignes par page, créez un paramètre nommé `RowsPerPage` et basez l’expression de groupe sur ce paramètre, comme le montre l’expression suivante :  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Propriétés  
 Les expressions ne sont pas seulement utilisées pour afficher des données dans des zones de texte. Elles peuvent également être utilisées pour changer la façon dont les propriétés sont appliquées aux éléments de rapport. Vous pouvez changer les informations de style pour un élément de rapport ou changer sa visibilité.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Mise en forme  
  
-   L’expression suivante, quand elle est utilisée dans la propriété Couleur d’une zone de texte, change la couleur du texte en fonction de la valeur du champ `Profit` :  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Vous pouvez aussi utiliser la variable d’objet Visual Basic `Me`. Cette variable est une autre façon de référencer la valeur d’une zone de texte.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   L’expression suivante, quand elle est utilisée dans la propriété BackgroundColor d’un élément de rapport dans une région de données, fait alterner la couleur d’arrière-plan de chaque ligne entre le vert pâle et le blanc :  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Si vous utilisez une expression pour une étendue spécifiée, il peut être nécessaire d’indiquer le jeu de données pour la fonction d’agrégation :  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Les couleurs disponibles proviennent de l’énumération KnownColor du .NET Framework.  
  
### <a name="chart-colors"></a>Couleurs des graphiques  
 Pour spécifier des couleurs pour un graphique Forme, vous pouvez utiliser du code personnalisé pour contrôler l’ordre dans lequel les couleurs sont mappées aux valeurs des points de données. Ceci vous permet d’utiliser des couleurs cohérentes pour plusieurs graphiques ayant les mêmes groupes de catégories. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Visibilité  
 Vous pouvez afficher et masquer des éléments dans un rapport en utilisant les propriétés de visibilité des éléments de rapport. Dans une région de données comme un tableau, vous pouvez masquer initialement les lignes de détails en fonction de la valeur dans une expression.  
  
-   L’expression suivante, quand elle est utilisée pour la visibilité initiale des lignes de détails dans un groupe, affiche les lignes de détails pour toutes les ventes supérieures à 90 pour cent dans le champ `PctQuota` :  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   L’expression suivante, quand elle est définie dans la propriété Masqué d’un tableau, affiche le tableau seulement s’il a plus de 12 lignes :  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   L’expression suivante, quand elle est définie dans la propriété **Masqué** d’une colonne, affiche la colonne seulement si le champ existe dans le jeu de données du rapport une fois que les données sont récupérées auprès de la source de données :  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL  
 Vous pouvez personnaliser les URL en utilisant les données du rapport, et aussi contrôler de façon conditionnelle si les URL sont ajoutées en tant qu’actions pour une zone de texte.  
  
-   L’expression suivante, quand elle est utilisée en tant qu’action sur une zone de texte, génère une URL personnalisée qui spécifie le champ `EmployeeID` du jeu de données comme paramètre d’URL.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   L’expression suivante contrôle de façon conditionnelle s’il faut ajouter une URL dans une zone de texte. Cette expression dépend d’un paramètre nommé `IncludeURLs`, qui permet à un utilisateur de décider s’il faut inclure des URL actives dans un rapport. Cette expression est définie en tant qu’action sur une zone de texte. En définissant le paramètre sur False, puis en affichant le rapport, vous pouvez exporter le rapport Microsoft Excel sans liens hypertexte.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> Données du rapport  
 Les expressions peuvent être utilisées pour manipuler les données utilisées dans le rapport. Vous pouvez référencer des paramètres et d’autres informations du rapport. Vous pouvez même modifier la requête qui est utilisée pour récupérer les données pour le rapport.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Paramètres  
 Vous pouvez utiliser des expressions dans un paramètre pour faire varier la valeur par défaut du paramètre. Par exemple, vous pouvez utiliser un paramètre pour filtrer les données pour un utilisateur particulier en fonction de l’ID d’utilisateur qui est utilisé pour exécuter le rapport.  
  
-   L’expression suivante, quand elle est utilisée comme valeur par défaut pour un paramètre, collecte l’ID d’utilisateur de la personne qui exécute le rapport :  
  
    ```  
    =User!UserID  
    ```  
  
-   Pour référencer un paramètre dans un paramètre de requête, une expression de filtre, une zone de texte ou une autre zone du rapport, utilisez la collection globale **Parameters**. Cet exemple suppose que le paramètre est nommé *Department* :  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Les paramètres peuvent être créés dans un rapport, mais définis comme étant masqués. Quand le rapport s’exécute sur le serveur de rapports, le paramètre n’apparaît pas dans la barre d’outils et le lecteur du rapport ne peut pas changer la valeur par défaut. Vous pouvez utiliser un paramètre masqué défini sur une valeur par défaut comme constante personnalisée. Vous pouvez utiliser cette valeur dans n’importe quelle expression, notamment une expression de champ. L’expression suivante identifie le champ spécifié par la valeur du paramètre par défaut pour le paramètre nommé *ParameterField* :  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Code personnalisé  
 Vous pouvez utiliser du code personnalisé intégré dans un rapport. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Utilisation de variables de groupe pour une agrégation personnalisée  
 Vous pouvez initialiser la valeur d’une variable de groupe qui est locale à l’étendue d’un groupe particulier, puis inclure une référence à cette variable dans des expressions. Une des façons d’utiliser une variable de groupe avec du code personnalisé consiste à implémenter un agrégat personnalisé. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Suppression des valeurs null ou zéro à l’exécution  
 Certaines valeurs dans une expression peuvent s’évaluer à null ou à non définie au moment du traitement du rapport. Ceci peut créer des erreurs d’exécution qui provoquent l’affichage de **#Error** dans la zone de texte, au lieu de l’expression évaluée. La fonction **IIF** est particulièrement sensible à ce comportement, car contrairement à une instruction If-Then-Else, chaque partie de l’instruction **IIF** est évaluée (y compris les appels de fonction) avant d’être passée à la routine qui teste si c’est **true** ou **false**. L’instruction `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` génère **#Error** dans le rapport rendu si `Fields!Sales.Value` est NOTHING.  
  
 Pour éviter cette situation, utilisez une des stratégies suivantes :  
  
-   Définissez le numérateur sur 0 et le dénominateur sur 1 si la valeur du champ B est 0 ou non définie ; sinon, définissez le numérateur sur la valeur pour le champ A et le dénominateur sur la valeur pour le champ B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Utilisez une fonction en code personnalisé pour retourner la valeur de l’expression. L’exemple suivant retourne la différence en pourcentage entre une valeur actuelle et une valeur précédente. Ceci peut être utilisé pour calculer la différence entre deux valeurs consécutives quelconques et gère le cas de limite de la première comparaison (quand il n’existe pas valeur précédente), et les cas où la valeur précédente ou la valeur actuelle est **null** (**Nothing** en Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     L’expression suivante montre comment appeler ce code personnalisé depuis une zone de texte pour le conteneur « ColumnGroupByYear » (groupe ou région de données).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Ceci permet d’éviter les exceptions à l’exécution. Vous pouvez maintenant utiliser une expression comme `=IIF(Me.Value < 0, "red", "black")` dans la propriété **Couleur** de la zone de texte pour afficher le texte de façon conditionnelle selon que les valeurs sont supérieures ou inférieures à 0.  
  
## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
