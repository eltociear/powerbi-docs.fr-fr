---
title: 'Tutoriel : Créer ses propres mesures dans Power BI Desktop'
description: Les mesures incluses dans Power BI Desktop vous aident en effectuant des calculs sur vos données quand vous interagissez avec vos rapports.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0d2b316b53b4107c86a036cc8a436440dd8bd674
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "74311520"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Tutoriel : Créer ses propres mesures dans Power BI Desktop
En utilisant des mesures, vous pouvez créer des solutions d’analyse de données parmi les plus puissantes dans Power BI Desktop. Les mesures vous aident en effectuant des calculs sur vos données quand vous interagissez avec vos rapports. Ce didacticiel vous aidera à comprendre les mesures et à créer vos propres mesures élémentaires dans Power BI Desktop.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel s’adresse aux utilisateurs de Power BI déjà familiarisés avec l’utilisation de Power BI Desktop pour créer des modèles plus avancés. Vous devez déjà bien connaître l’utilisation de la fonctionnalité Obtenir des données et l’Éditeur de requête pour importer des données, utiliser plusieurs tables connexes et ajouter des champs au Canevas de rapport. Si vous découvrez seulement Power BI Desktop, veillez à consulter [Prise en main de Power BI Desktop](desktop-getting-started.md).
  
- Ce tutoriel utilise le fichier [Contoso Sales Sample for Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), qui inclut des données de vente en ligne de la société fictive Contoso. Étant donné que ces données sont importées à partir d’une base de données, vous ne pouvez pas vous connecter à la source de données ni l’afficher dans l’Éditeur de requête. Téléchargez et extrayez le fichier sur votre ordinateur.

## <a name="automatic-measures"></a>Mesures automatiques

Quand Power BI Desktop crée une mesure, elle est le plus souvent créée automatiquement pour vous. Pour voir comment Power BI Desktop crée une mesure, suivez ces étapes :

1. Dans Power BI Desktop, sélectionnez **Fichier** > **Ouvrir**, accédez au fichier *Contoso Sales Sample for Power BI Desktop.pbix*, puis sélectionnez **Ouvrir**.

2. Dans le volet **Champs**, développez la table **Sales**. Ensuite, cochez la case en regard du champ **SalesAmount** ou faites glisser **SalesAmount** sur le canevas de rapport.

    Une nouvelle visualisation d’histogramme apparaît, affichant la somme totale de toutes les valeurs de la colonne **SalesAmount** de la table **Sales**.

    ![Histogramme SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Tous les champs (colonnes) inclus dans le volet **Champs** avec une icône sigma ![Icône sigma](media/desktop-tutorial-create-measures/meastut_sigma.png) sont numériques. Leurs valeurs peuvent être agrégées. Au lieu de présenter une table avec de nombreuses valeurs (deux millions de lignes pour **SalesAmount**), Power BI Desktop crée et calcule automatiquement une mesure permettant d’agréger les données quand un type de données numérique est détecté. La somme est l’agrégation par défaut pour un type de données numérique, mais vous pouvez facilement appliquer d’autres agrégations comme la moyenne ou le nombre. La compréhension des agrégations est essentielle à la compréhension des mesures, car chaque mesure effectue un certain type d’agrégation. 

Pour modifier l’agrégation du graphique, suivez ces étapes :

1. Sélectionnez la visualisation **SalesAmount** dans le canevas de rapport.  

1. Dans la zone **Valeur** du volet **Visualisations**, sélectionnez la flèche vers le bas située à droite de **SalesAmount**. 

1. Dans le menu qui s’affiche, sélectionnez **Moyenne**. 

    La visualisation affiche alors la moyenne de toutes les valeurs de vente figurant dans le champ **SalesAmount**.

    ![Graphique de moyenne SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Selon le résultat souhaité, vous pouvez modifier le type d’agrégation. En revanche, tous les types d’agrégation ne s’appliquent pas à tous les types de données numériques. Par exemple, pour le champ **SalesAmount**, Somme et Moyenne sont utiles, ainsi que Minimum et Maximum. En revanche, le type Nombre n’a pas vraiment de sens pour le champ **SalesAmount**, car même si les valeurs sont numériques, elles correspondent à une devise.

Les valeurs calculées à partir des mesures changent en réponse à vos interactions avec votre rapport. Par exemple, si vous faites glisser le champ **RegionCountryName** depuis la table **Geography** vers votre graphique **SalesAmount** existant, le graphique change pour refléter les montants moyens des ventes pour chaque pays.

![SaleAmount par pays](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Quand le résultat d’une mesure change en raison d’une interaction avec votre rapport, vous affectez le *contexte* de votre mesure. En fait, chaque fois que vous interagissez avec les visualisations de votre rapport, vous modifiez le contexte dans lequel une mesure calcule et affiche ses résultats.

## <a name="create-and-use-your-own-measures"></a>Créer et utiliser vos propres mesures

Dans la plupart des cas, Power BI Desktop calcule et retourne automatiquement les valeurs en fonction des types de champs et d’agrégations que vous choisissez. Toutefois, dans certains cas, vous pouvez être amené à créer vos propres mesures pour effectuer des calculs uniques plus complexes. Dans Power BI Desktop, vous pouvez créer vos propres mesures à l’aide du langage de formule DAX (Data Analysis Expressions). 

Les formules DAX utilisent bon nombre de fonctions, opérateurs et syntaxes identiques à ceux des formules Excel. Toutefois, les fonctions de DAX sont conçues pour fonctionner avec des données relationnelles et effectuer des calculs plus dynamiques quand vous interagissez avec vos rapports. Il existe plus de 200 fonctions DAX capables d’effectuer des opérations très diverses, de simples agrégations comme Sum (Somme) et Average (Moyenne) jusqu’à des fonctions statistiques et de filtrage plus complexes. Il existe de nombreuses ressources pour vous aider à en savoir plus sur DAX. Une fois que vous avez terminé ce tutoriel, consultez [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Lorsque vous créez vos propres mesures, elles sont désignées comme mesures *modèles* et ajoutées à la liste **Champs** de la table sélectionnée. Certains avantages des mesures modèles sont que vous pouvez les nommer comme bon vous semble, pour les rendre plus identifiables. Vous pouvez les utiliser en tant qu’arguments dans d’autres expressions DAX et vous pouvez les utiliser pour effectuer rapidement des calculs complexes.

### <a name="quick-measures"></a>Mesures rapides

À compter de la version de février 2018 de Power BI Desktop, beaucoup de calculs courants sont disponibles en tant que *mesures rapides*, qui écrivent les formules DAX pour vous en fonction de ce que vous entrez dans une fenêtre. Ces calculs rapides et puissants permettent également de vous familiariser avec DAX ou d’amorcer la création de vos propres mesures personnalisées. 

Créez une mesure rapide à l’aide de l’une des méthodes suivantes : 
 - À partir d’une table dans le volet **Champs**, cliquez avec le bouton droit ou sélectionnez **Autres options** ( **...** ), puis sélectionnez **Nouvelle mesure rapide** dans la liste.

 - Sous **Calculs** sous l’onglet **Accueil** du ruban Power BI Desktop, sélectionnez **Nouvelle mesure rapide**.

Pour plus d’informations sur la création et l’utilisation des mesures rapides, consultez [Utiliser les mesures rapides](desktop-quick-measures.md).

### <a name="create-a-measure"></a>Créer une mesure

Supposons que vous voulez analyser vos ventes nettes en soustrayant les remises et les retours des montants totaux des ventes. Pour le contexte qui existe dans votre visualisation, vous avez besoin d’une mesure qui soustrait la somme de DiscountAmount et de ReturnAmount de la somme de SalesAmount. Il n’existe aucun champ pour les ventes nettes dans la liste **Champs**, mais vous disposez de modules pour créer votre propre mesure afin de calculer ces ventes nettes. 

Pour créer une mesure, suivez ces étapes :

1. Dans le volet **Champs**, cliquez avec le bouton droit sur la table **Sales** ou pointez sur la table, puis sélectionnez **Autres options** ( **...** ). 

1. Dans le menu qui s’affiche, sélectionnez **Nouvelle mesure**. 

    Cette action enregistre votre nouvelle mesure dans la table **Sales**, où elle est facilement trouvable.
    
    ![Nouvelle mesure à partir de la liste](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    Vous pouvez également créer une mesure en sélectionnant **Nouvelle mesure** dans le groupe **Calculs** sous l’onglet **Accueil** du ruban Power BI Desktop.
    
    ![Nouvelle mesure à partir du ruban](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Lorsque vous créez une mesure à partir du ruban, vous pouvez le faire dans n’importe quelle table, mais elle sera plus facile à trouver si vous la créez là où vous souhaitez l’utiliser. Dans ce cas, sélectionnez d’abord la table **Sales** pour l’activer, puis **Nouvelle mesure**. 
    
    La barre de formule apparaît en haut du canevas de rapport, où vous pouvez renommer votre mesure et entrer une formule DAX.
    
    ![Barre de formule](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
1. Par défaut, chaque nouvelle mesure est nommée *Mesure*. Si vous ne la renommez pas, les nouvelles mesures supplémentaires sont nommées *Mesure 2*, *Mesure 3* et ainsi de suite. Comme nous voulons que cette mesure soit plus identifiable, mettez en surbrillance *Mesure* dans la barre de formule, puis remplacez votre sélection par *Ventes nettes*.
    
1. Commencez à entrer votre formule. Après le signe égal, commencez à taper *Sum* (Somme). Lorsque vous tapez, une liste déroulante de suggestions apparaît, affichant toutes les fonctions DAX commençant par les lettres que vous tapez. Si nécessaire, faites défiler vers le bas pour sélectionner **SUM** dans la liste, puis appuyez sur **Entrée**.
    
    ![Choisir SUM dans la liste](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Une parenthèse ouvrante apparaît avec une liste déroulante de suggestions présentant les colonnes disponibles que vous pouvez passer à la fonction SUM.
    
    ![Choisir une colonne](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
1. Les expressions apparaissent toujours entre une parenthèse ouvrante et une parenthèse fermante. Pour cet exemple, votre expression contient un seul argument à passer à la fonction SUM : la colonne **SalesAmount**. Commencez à taper *SalesAmount* jusqu’à ce que **Sales(SalesAmount)** soit la seule valeur restante dans la liste. 

    Le nom de colonne précédé du nom de table correspond au nom complet de la colonne. Les noms complets de colonnes facilitent la lecture de vos formules.
    
    ![Sélectionner SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
1. Sélectionnez **Sales[SalesAmount]** dans la liste, puis entrez une parenthèse fermante.
    
    > [!TIP]
    > Les erreurs de syntaxe sont le plus souvent provoquées par une parenthèse fermante manquante ou mal placée.
    
    
    
1. Soustrayez les deux autres colonnes à l’intérieur de la formule :

    a. Après la parenthèse fermante de la première expression, tapez un espace, puis un opérateur moins (-), suivi d’un autre espace. 

    b. Entrez une autre fonction SUM et commencez à taper *DiscountAmount* jusqu’à ce que vous puissiez choisir la colonne **Sales[DiscountAmount]** en tant qu’argument. Ajoutez une parenthèse fermante. 

    c. Tapez un espace, un opérateur moins, un espace, une autre fonction SUM avec **Sales[ReturnAmount]** comme argument, puis une parenthèse fermante.
    
    ![Formule complète](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
1. Appuyez sur **Entrée** ou sélectionnez **Valider** (icône de coche) dans la barre de formule pour terminer et valider la formule. 

    La mesure **Ventes nettes** validée est maintenant prête à être utilisée dans la table **Sales** du volet **Champs**.
    
    ![Mesure Ventes nettes dans la liste des champs de la table Sales](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
1. Si vous manquez d’espace pour entrer une formule ou si vous voulez la disposer sur plusieurs lignes, sélectionnez la flèche vers le bas située à droite de la barre de formule pour obtenir davantage de place. 

    La flèche vers le bas se transforme en flèche vers le haut et une grande zone apparaît.

    ![Flèche vers le haut d’une formule](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

1. Séparez les parties de votre formule en appuyant sur **Alt** + **Entrée** pour des lignes distinctes, ou en appuyant sur **Tab** pour ajouter l’espace d’une tabulation.

   ![Formule développée](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>Utiliser votre mesure dans le rapport
Ajoutez votre nouvelle mesure **Ventes nettes** dans le canevas de rapport de manière à ce que les ventes nettes soient calculées pour les autres champs que vous ajoutez au rapport. 

Pour examiner les ventes nettes par pays :

1. Sélectionnez la mesure **Net Sales** dans la table **Sales** ou faites-la glisser sur le canevas de rapport.
    
1. Sélectionnez le champ **RegionCountryName** à partir de la table **Geography** ou faites-le glisser sur le graphique **Ventes nettes**.
    
    ![Ventes nettes par pays](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
1. Sélectionnez le champ **SalesAmount** ou faites-le glisser sur le graphique pour voir la différence entre les ventes nettes et les ventes totales par pays. 

    ![Montant des ventes et ventes nettes par pays](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

    Le graphique utilise désormais deux mesures : **SalesAmount**, additionnée automatiquement par Power BI et la mesure **Ventes nettes**, que vous avez créée manuellement. Chaque mesure a été calculée dans le contexte d’un autre champ, **RegionCountryName**.
    
### <a name="use-your-measure-with-a-slicer"></a>Utiliser votre mesure avec un segment

Ajoutez un segment afin de filtrer davantage les ventes nettes et les montants des ventes par année civile :
    
1. Sélectionnez une zone vide en regard du graphique. Dans le volet **Visualisations**, sélectionnez la visualisation **Table**. 

    Cette action crée une visualisation de table vide dans le canevas de rapport.
    
    ![Nouvelle visualisation de table vide](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
1. Faites glisser le champ **Year** à partir de la table **Calendar** dans la nouvelle visualisation de table vide. 
    
    Étant donné que **Year** est un champ numérique, Power BI Desktop additionne ses valeurs. Cette somme ne fonctionne pas correctement en tant qu’agrégation. Nous allons nous en occuper à l’étape suivante.

    ![Agrégation Year](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3. Dans la zone **Valeurs** située dans le volet **Visualisations**, sélectionnez la flèche vers le bas à côté de **Year**, puis sélectionnez **Ne pas résumer** dans la liste. La table répertorie maintenant les années individuelles.
    
    ![Sélectionner Ne pas résumer](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Sélectionnez l’icône **Segment** dans le volet **Visualisations** pour convertir la table en segment. Si la visualisation affiche un curseur au lieu d’une liste, sélectionnez **Liste** à partir de la flèche vers le bas dans le curseur.

    ![Convertir une table en segment](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Sélectionnez une valeur dans le segment **Year** pour filtrer le graphique **Ventes nettes et montant des ventes par pays** en conséquence. Les mesures **Ventes nettes** et **SalesAmount** recalculent et affichent les résultats dans le contexte du champ **Year** sélectionné. 
    
    ![Graphique segmenté par année](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Utiliser votre mesure dans une autre mesure

Supposons que vous voulez déterminer quels produits ont le montant de ventes nettes le plus élevé par unité vendue. Vous avez besoin d’une mesure qui divise les ventes nettes par la quantité d’unités vendues. Créez une mesure qui divise le résultat de votre mesure **Ventes nettes** par la somme de **Sales[SalesQuantity]** .

1.  Dans le volet **Champs**, créez une mesure nommée **Ventes nettes par unité** dans la table **Sales**.
    
1. Dans la barre de formule, commencez à taper *Net Sales*. La liste de suggestions indique ce que vous pouvez ajouter. Sélectionnez **[Net Sales]** .
    
    ![Formule utilisant Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
1. Vous pouvez également référencer des mesures en tapant simplement un crochet ouvrant ( **[** ). La liste de suggestions présente uniquement les mesures à ajouter à votre formule.
    
    ![Le crochet montre uniquement les mesures](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
1. Entrez un espace, un opérateur de division (/), un autre espace, une fonction SUM, puis tapez *Quantity*. La liste de suggestions affiche toutes les colonnes dont le nom inclut *Quantity*. Sélectionnez **Sales[SalesQuantity]** , tapez la parenthèse fermante et appuyez sur **Entrée** ou sélectionnez **Valider** (icône de coche) pour valider votre formule. 

    La formule obtenue doit avoir l’aspect suivant :
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
1. Sélectionnez la mesure **Ventes nettes par unité** dans la table **Sales** ou faites-la glisser sur une zone vide du canevas de rapport. 

    Le graphique montre le montant des ventes nettes par unité par rapport à tous les produits vendus. Ce graphique n’est pas très instructif. Nous allons nous en occuper à l’étape suivante.
    
    ![Ventes nettes globales par unité](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
1. Pour une présentation différente, modifiez le type de visualisation de graphique en spécifiant **Treemap**.
    
    ![Choisir Treemap](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
1. Sélectionnez le champ **ProductCategory** ou faites-le glisser vers le Treemap ou le champ **Groupe** du volet **Visualisations**. Maintenant, vous disposez de bonnes informations !
    
    ![Treemap par catégorie de produit](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Essayez de supprimer le champ **ProductCategory** et de faire glisser le champ **ProductName** à la place sur le graphique. 
    
    ![Treemap par nom de produit](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
   Bon, il est vrai que nous ne faisons qu’expérimenter, mais admettez que c’est plutôt sympa ! Faites des essais avec d’autres manières de filtrer et de mettre en forme la visualisation.

## <a name="what-youve-learned"></a>Ce que vous avez appris
Les mesures vous permettent d’obtenir les insights souhaités à partir de vos données. Vous avez appris à créer des mesures à l’aide de la barre de formule, à les nommer de manière explicite, à rechercher et à sélectionner les éléments de formule corrects à l’aide des listes de suggestions DAX. Vous avez également bénéficié d’une présentation des contextes, dans lesquels le résultat des calculs effectués dans les mesures change en fonction d’autres champs ou d’autres expressions dans votre formule.

## <a name="next-steps"></a>Étapes suivantes
- Pour en savoir plus sur les mesures rapides de Power BI Desktop, qui vous fournissent de nombreux calculs de mesures courantes, consultez [Utiliser les Mesures rapides pour effectuer facilement des calculs courants et puissants](desktop-quick-measures.md).
  
- Si vous souhaitez approfondir vos connaissances des formules DAX et créer des mesures plus avancées, consultez [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Cet article porte sur les concepts fondamentaux propres à DAX, tels que la syntaxe, les fonctions et une compréhension plus approfondie du contexte.
  
- Veillez à ajouter la page [Informations de référence sur DAX (Data Analysis Expressions)](https://docs.microsoft.com/dax/index) à vos favoris. Vous y trouverez des informations détaillées sur la syntaxe DAX, les opérateurs et plus de 200 fonctions DAX.

