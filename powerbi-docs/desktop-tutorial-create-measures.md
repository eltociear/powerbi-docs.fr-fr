---
title: 'Didacticiel : créer vos propres mesures dans Power BI Desktop'
description: 'Didacticiel : créer vos propres mesures dans Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 8cfa3190acd4ef2ae2e1123f22d8f6221147afb1
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34456085"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Didacticiel : créer vos propres mesures dans Power BI Desktop
Vous pouvez créer certaines solutions d’analyse de données parmi les plus puissantes dans Power BI Desktop à l’aide de mesures. Les mesures vous aident en effectuant des calculs sur vos données quand vous interagissez avec vos rapports. Ce didacticiel vous aidera à comprendre les mesures et à créer vos propres mesures élémentaires dans Power BI Desktop.

### <a name="prerequisites"></a>Conditions préalables
- Ce didacticiel s’adresse aux utilisateurs de Power BI déjà familiarisés avec l’utilisation de Power BI Desktop pour créer des modèles plus avancés. Vous devez déjà bien connaître l’utilisation de la fonctionnalité Obtenir des données et de l’Éditeur de requête pour importer des données, l’utilisation de plusieurs tables connexes et l’ajout de champs dans le Canevas de rapport. Si vous découvrez seulement Power BI Desktop, veillez à consulter [Prise en main de Power BI Desktop](desktop-getting-started.md).
  
- Téléchargez le fichier [Contoso Sales Sample for Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip) qui contient des données sur les ventes en ligne de la société fictive Contoso, Inc. Comme ces données ont été importées à partir d’une base de données, vous ne pouvez pas vous connecter à la source de données ni l’afficher dans l’Éditeur de requête. Extrayez le fichier sur votre ordinateur et ouvrez-le dans Power BI Desktop.

## <a name="understand-measures"></a>Comprendre les mesures

Les mesures sont le plus souvent créées pour vous automatiquement. Dans le fichier Contoso Sales Sample, cochez la case en regard du champ **SalesAmount** dans la table **Sales** dans la zone Fields (Champs), ou faites glisser **SalesAmount** sur le canevas de rapport. Une nouvelle visualisation d’histogramme apparaît, affichant la somme totale de toutes les valeurs de la colonne SalesAmount de la table Sales.

![Graphique SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Tout champ qui apparaît dans la zone Fields (Champs) avec une icône sigma ![icône sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) est numérique, et ses valeurs peuvent être agrégées. Au lieu d’afficher une table avec deux millions de lignes de valeurs SalesAmount, Power BI Desktop a détecté un type de données numérique et a automatiquement créé et calculé une mesure pour agréger les données. La somme est l’agrégation par défaut pour un type de données numérique, mais vous pouvez facilement appliquer d’autres agrégations comme la moyenne ou le nombre. La compréhension des agrégations est essentielle à la compréhension des mesures, car chaque mesure effectue un certain type d’agrégation. 

Pour modifier l’agrégation du graphique sur la moyenne, dans la zone **Value** (Valeur) du volet Visualisations, cliquez sur la flèche vers le bas en regard de **SalesAmount** et sélectionnez **Average** (Moyenne). La visualisation affiche alors la moyenne de tous les prix de vente figurant dans le champ SalesAmount.

![Graphique de moyenne SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Vous pouvez modifier le type d’agrégation en fonction du résultat que vous souhaitez, mais tous les types d’agrégation ne s’appliquent pas à tous les types de données numériques. Par exemple, pour le champ SalesAmount, les opérations Sum (Somme) et Average (Moyenne) ont un sens. Les opérations Minimum et Maximum sont également possibles. En revanche, l’opération Count (Nombre) n’a pas vraiment de sens pour le champ SalesAmount, car même si les valeurs sont numériques, elles correspondent à une devise.

Les valeurs calculées à partir des mesures changent en réponse à vos interactions avec votre rapport. Par exemple, si vous faites glisser le champ **RegionCountryName** de la table **Geography** vers votre graphique, la moyenne des montants des ventes pour chaque pays est calculée et affichée.

![SaleAmount par pays](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quand le résultat d’une mesure change en raison d’une interaction avec votre rapport, vous affectez le *contexte* de votre mesure. En fait, chaque fois que vous interagissez avec les visualisations de votre rapport, vous modifiez le contexte dans lequel une mesure calcule et affiche ses résultats.

## <a name="create-and-use-your-own-measures"></a>Créer et utiliser vos propres mesures

Dans la plupart des cas, Power BI calcule et retourne automatiquement des valeurs selon les types de champs et les agrégations que vous choisissez, mais dans certains cas, vous souhaiterez peut-être créer vos propres mesures pour effectuer des calculs uniques plus complexes. Dans Power BI Desktop, vous pouvez créer vos propres mesures à l’aide du langage de formule DAX (Data Analysis Expressions). 

Les formules DAX utilisent bon nombre de fonctions, opérateurs et syntaxes identiques à ceux des formules Excel. Toutefois, les fonctions de DAX sont conçues pour fonctionner avec des données relationnelles et effectuer des calculs plus dynamiques quand vous interagissez avec vos rapports. Il existe plus de 200 fonctions DAX capables d’effectuer des opérations très diverses, de simples agrégations comme Sum (Somme) et Average (Moyenne) jusqu’à des fonctions statistiques et de filtrage plus complexes. Il existe de nombreuses ressources pour vous aider à en savoir plus sur DAX. Une fois que vous aurez terminé ce didacticiel, veillez à consulter [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Lorsque vous créez vos propres mesures, elles sont ajoutées à la liste Fields (Champs) pour la table sélectionnée et sont désignées comme mesures *modèles*. Certains avantages des mesures modèles sont que vous pouvez les nommer comme bon vous semble, pour les rendre plus identifiables. Vous pouvez les utiliser en tant qu’arguments dans d’autres expressions DAX et vous pouvez les utiliser pour effectuer des calculs complexes très rapidement.

>[!TIP]
>À compter de la version de février 2018 de Power BI Desktop, beaucoup de calculs courants sont disponibles en tant que **mesures rapides**, qui écrivent les formules DAX pour vous en fonction de vos saisies dans une boîte de dialogue. Ces calculs rapides et puissants permettent également de vous familiariser avec DAX ou d’amorcer la création de vos propres mesures personnalisées. Pour créer ou explorer les mesures rapides, sélectionnez **Nouvelle mesure rapide** dans la liste **Plus d’options** d’une table ou sous **Calculs** de l’onglet Accueil du ruban. Consultez [Utiliser les rapide mesures](desktop-quick-measures.md) pour plus d’informations sur la création et l’utilisation des mesures rapides.

### <a name="create-a-measure"></a>Créer une mesure

Vous voulez analyser vos ventes nettes en soustrayant les remises les retours des montants des ventes totales. Pour le contexte qui existe dans votre visualisation, vous avez besoin d’une mesure qui soustrait la somme de DiscountAmount et de ReturnAmount de la somme de SalesAmount. Il n’existe aucun champ Net Sales dans la liste Fields (Champs), mais vous disposez des blocs de construction pour créer votre propre mesure afin de calculer les ventes nettes. 

1.  Cliquez avec le bouton droit sur la table **Sales** dans la zone Fields (Champs), ou placez le curseur sur la table et sélectionnez les points de suspension (...) **Plus d’options**, puis sélectionnez **Nouvelle mesure**. Cela garantit l’enregistrement de votre nouvelle mesure dans la table Sales, où elle est plus facile à trouver.
    
    ![Nouvelle mesure](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Vous pouvez également créer une nouvelle mesure en sélectionnant **Nouvelle mesure** dans le groupe Calculs dans l’onglet Accueil du ruban Power BI Desktop.
    
    ![Nouvelle mesure à partir du ruban](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Lorsque vous créez une mesure à partir du ruban, elle peut être créée dans n’importe quelle table, mais elle sera plus facile à trouver si vous la créez là où vous souhaitez l’utiliser. Dans ce cas, sélectionnez d’abord la table Sales pour l’activer, puis **Nouvelle mesure**. 
    
    La barre de formule apparaît en haut du canevas de rapport, où vous pouvez renommer votre mesure et entrer une formule DAX.
    
    ![Barre de formule](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  Par défaut, une nouvelle mesure est simplement nommée Measure (Mesure). Si vous ne la renommez pas, les nouvelles mesures supplémentaires seront nommées Mesure 2, Mesure 3 et ainsi de suite. Vous souhaitez que vos mesures soient plus identifiables, donc mettez en surbrillance **Measure** (Mesure) dans la barre de formule, puis tapez **Net Sales**.
    
3.  À présent, vous pouvez commencer à entrer votre formule. Après le signe égal, commencez à taper **Sum** (Somme). Lorsque vous tapez, une liste déroulante de suggestions apparaît, affichant toutes les fonctions DAX commençant par les lettres que vous tapez. Si nécessaire, faites défiler vers le bas pour sélectionner **SUM** dans la liste, puis appuyez sur Entrée.
    
    ![Choisir SUM](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Une parenthèse ouvrante apparaît avec une autre liste déroulante de suggestions présentant toutes les colonnes disponibles que vous pouvez passer à la fonction SUM.
    
    ![Choisir une colonne](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    Les expressions apparaissent toujours entre une parenthèse ouvrante et une parenthèse fermante. Votre expression contiendra un seul argument à passer à la fonction SUM : la colonne SalesAmount. Commencez à taper « SalesAmount » jusqu’à ce qu’une seule valeur soit conservée dans la liste : Sales(SalesAmount). Le nom de colonne précédé du nom de table est appelé le *nom complet* de la colonne. Les noms de colonnes complets facilitent la lecture de vos formules. 
    
    ![Sélectionner SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. Sélectionnez **Sales[SalesAmount]** (Ventes[MontantVente]), puis tapez une parenthèse fermante.
    
    > [!TIP]
    > Les erreurs de syntaxe sont le plus souvent provoquées par une parenthèse fermante manquante ou mal placée.
    
    
    
5.  Pour soustraire les deux autres colonnes :
    1. Après la parenthèse fermante de la première expression, tapez un espace, puis un opérateur moins (**-**), suivi d’un autre espace. 
    2. Entrez une autre fonction SUM et commencez à taper « DiscountAmount » jusqu’à ce que vous puissiez choisir la colonne **Sales [DiscountAmount]** en tant qu’argument. Ajoutez une parenthèse fermante. 
    3. Tapez un espace, un autre opérateur moins, un espace, une autre fonction SUM avec **Sales [ReturnAmount]** comme argument et une parenthèse fermante.
    
    ![Formule complète](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  Appuyez sur Entrée ou cliquez sur la coche dans la barre de formule pour terminer et valider la formule. La mesure validée est maintenant prête à l’emploi dans la liste Fields (Champs) de la table Sales. 
    
    ![Mesure dans la liste Champs](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
Si vous manquez d’espace pour saisir une formule ou si vous souhaitez que la formule soit répartie sur plusieurs lignes, sélectionnez le chevron vers le bas situé à droite de la barre de formule pour obtenir davantage de place.

![Chevron de formule](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

Vous pouvez répartir des parties de votre formule sur plusieurs lignes en appuyant sur **Alt-Entrée** ou déplacer des éléments en utilisant la touche **Tab**.

![Formule développée](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Utiliser votre mesure dans le rapport
À présent, vous pouvez ajouter votre mesure Net Sales dans le canevas de rapport de manière à ce que les ventes nettes soient calculées pour les autres champs que vous ajoutez au rapport. Pour examiner les ventes nettes par pays :

1. Sélectionnez la mesure **Net Sales** dans la table **Sales** ou faites-la glisser sur le canevas de rapport.
    
2. Sélectionnez le champ **RegionCountryName** à partir de la table **Geography** ou faites-le glisser sur le graphique.
    
    ![Ventes nettes par pays](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
Sélectionnez le champ **SalesAmount** ou faites-le glisser sur le graphique pour voir la différence entre les ventes nettes et les ventes totales par pays. 

![Montant des ventes et ventes nettes par pays](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

Le graphique utilise désormais deux mesures : SalesAmount qui a été totalisée automatiquement et la mesure Net Sales que vous avez créée. Chaque mesure a été calculée dans le contexte d’un autre champ, RegionCountryName.
    
### <a name="use-your-measure-with-a-slicer"></a>Utiliser votre mesure avec un segment

Vous pouvez ajouter un segment afin de filtrer davantage les ventes nettes et les montants des ventes par année civile.
    
1.  Cliquez sur une zone vide en regard du graphique, puis dans **Visualisations**, sélectionnez la visualisation **Table**. Cette opération crée une visualisation de table vide dans le canevas de rapport.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  Faites glisser le champ **Year** à partir de la table **Calendar** dans la nouvelle visualisation de table vide. Étant donné que Year est un champ numérique, Power BI Desktop totalise ses valeurs, mais cela n’a pas de sens en tant qu’agrégation. 
    
    ![Agrégation Year](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  Dans **Values** dans le volet Visualisations, sélectionnez la flèche vers le bas en regard de **Year**, puis sélectionnez **Don’t summarize** (Ne pas résumer). La table répertorie maintenant les années individuelles.
    
    ![Ne pas totaliser](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Sélectionnez l’icône **Slicer** (Segment) dans le volet Visualisations pour convertir la table en segment.

    ![Remplacer par un segment](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Sélectionnez une valeur dans le segment **Year** pour filtrer le graphique **Net Sales and Sales Amount by Country** en conséquence. Les mesures Net Sales et SalesAmount recalculent et affichent les résultats dans le contexte du champ Year sélectionné. 
    
    ![Graphique segmenté par année](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Utiliser votre mesure dans une autre mesure

Vous voulez savoir quels produits ont les ventes nettes les plus élevées par unité vendue, donc vous avez besoin d’une mesure qui divise les ventes nettes par la quantité d’unités vendues. Vous pouvez créer une nouvelle mesure qui divise le résultat de votre mesure Net Sales par la somme de Sales[SalesQuantity].

1.  Créez une mesure nommée **Net Sales per Unit** dans la table Sales.
    
2.  Dans la barre de formule, commencez à taper **Net Sales**. La liste de suggestions vous montre ce que vous pouvez ajouter. Sélectionnez **[Net Sales]**.
    
    ![Formule utilisant Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    Vous pouvez également référencer des mesures en tapant simplement un crochet ouvrant (**[**). La liste de suggestions affiche uniquement les mesures à ajouter à votre formule.
    
    ![Le crochet montre uniquement les mesures](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Entrez un espace, un opérateur de division (**/**), un autre espace, une fonction SUM et tapez **Quantity** (Quantité). La liste de suggestions affiche toutes les colonnes dont le nom inclut Quantity. Sélectionnez **Sales[SalesQuantity]**, tapez la parenthèse fermante et appuyez sur ENTRÉE ou sélectionnez la coche pour valider votre formule. La formule doit ressembler à ceci :
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. Sélectionnez la mesure **Net Sales per Unit** dans la table Sales ou faites-la glisser sur une zone vide du canevas de rapport. Le graphique montre le montant des ventes nettes par unité pour tous les produits vendus, ce qui n’est pas très utile. 
    
    ![Ventes nettes globales par unité](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. Pour une présentation différente, modifiez le type de visualisation de graphique en spécifiant **Treemap**.
    
    ![Choisir Treemap](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Sélectionnez le champ **Product Category** ou faites-le glisser vers le Treemap ou le champ Group (Groupe) du volet Visualisations. Maintenant, vous disposez de bonnes informations !
    
    ![Treemap par catégorie de produit](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Essayez de supprimer le champ **ProductCategory** et de faire glisser le champ **ProductName** à la place sur le graphique. 
    
    ![Treemap par nom de produit](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
Bon, il est vrai que nous ne faisons qu’expérimenter, mais admettez que c’est plutôt sympa ! Faites des essais avec d’autres manières de filtrer et de mettre en forme la visualisation.

## <a name="what-youve-learned"></a>Ce que vous avez appris
Les mesures vous apportent beaucoup de puissance pour obtenir les insights souhaités à partir de vos données. Vous avez appris à créer des mesures à l’aide de la barre de formule, à les nommer de manière explicite, à rechercher et à sélectionner les éléments de formule corrects à l’aide des listes de suggestions DAX. Vous avez également bénéficié d’une présentation des contextes, dans lesquels le résultat des calculs effectués dans les mesures change en fonction d’autres champs ou d’autres expressions dans votre formule.

## <a name="next-steps"></a>Étapes suivantes
- Pour en savoir plus sur les mesures rapides de Power BI Desktop, qui vous fournissent de nombreux calculs de mesures courantes, consultez [Utiliser les Mesures rapides pour effectuer facilement des calculs courants et puissants](desktop-quick-measures.md).
  
- Si vous souhaitez approfondir vos connaissances des formules DAX et créer des mesures plus avancées, consultez [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Cet article porte sur les concepts fondamentaux propres à DAX, tels que la syntaxe, les fonctions et une compréhension plus approfondie du contexte.
  
- Veillez à ajouter la page [Informations de référence sur DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) à vos favoris. Vous y trouverez des informations détaillées sur la syntaxe DAX, les opérateurs et plus de 200 fonctions DAX.

