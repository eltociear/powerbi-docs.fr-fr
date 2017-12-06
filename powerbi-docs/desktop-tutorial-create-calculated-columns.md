---
title: "Didacticiel : création de colonnes calculées dans Power BI Desktop"
description: "Didacticiel : création de colonnes calculées dans Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 9ea93980a095ca4e626b6f8071d044448af59635
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Didacticiel : création de colonnes calculées dans Power BI Desktop
Parfois, les données que vous analysez ne contiennent pas de champ particulier vous permettant d’obtenir les résultats que vous recherchez. C’est là qu’interviennent les colonnes calculées. Les colonnes calculées utilisent des formules DAX (Data Analysis Expressions) pour définir les valeurs d’une colonne. Ces valeurs peuvent concerner n’importe quoi, qu’il s’agisse d’assembler des valeurs de texte à partir de plusieurs colonnes différentes ailleurs dans le modèle, ou de calculer une valeur numérique à partir d’autres valeurs. Par exemple, supposons que vos données incluent des colonnes City (Ville) et State (État) (en tant que champs dans la liste Champs), mais que vous voulez un champ Location (Emplacement) unique qui possède ces deux informations sous la forme d’une valeur unique, telle que Miami, FL. C’est là précisément qu’interviennent les colonnes calculées.

Les colonnes calculées sont semblables aux mesures, dans le sens où toutes deux reposent sur une formule DAX, mais elles diffèrent dans la manière dont elles sont utilisées. Les mesures sont souvent utilisées dans la zone Valeurs d’une visualisation, pour calculer les résultats en fonction d’autres champs qui figurent sur une ligne d’une table ou dans une zone Axe, Légende ou Groupe d’une visualisation. Les colonnes calculées sont quant à elles utilisées quand vous souhaitez obtenir les résultats de la colonne sur cette ligne de la table, ou dans la zone Axe, Légende ou Groupe.

Ce didacticiel va vous aider à comprendre les colonnes calculées et à créer vos propres colonnes calculées dans Power BI Desktop. Il s’adresse aux utilisateurs de Power BI qui savent déjà comment créer des modèles plus avancés avec Power BI Desktop. Vous devez déjà bien connaître l’utilisation de la fonctionnalité Requête pour importer des données, l’utilisation de plusieurs tables connexes et l’ajout de champs dans le Canevas de rapport. Si vous découvrez seulement Power BI Desktop, veillez à consulter [Prise en main de Power BI Desktop](desktop-getting-started.md).

Pour effectuer les étapes de ce didacticiel, vous devez télécharger le fichier [Contoso Sales Sample for Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Il s’agit du même exemple de fichier que celui utilisé pour le didacticiel [Créer vos propres mesures dans Power BI Desktop](desktop-tutorial-create-measures.md). Il contient déjà des données sur les ventes de la société fictive Contoso, Inc. Les données figurant dans ce fichier ayant été importées à partir d’une base de données, vous ne pourrez pas vous connecter à la source de données ni l’afficher dans l’Éditeur de requête. Une fois le fichier sur votre ordinateur, ouvrez-le dans Power BI Desktop.

## <a name="lets-create-a-calculated-column"></a>Création d’une colonne calculée
Supposez que vous souhaitez afficher les catégories de produits avec les sous-catégories de produits dans une valeur unique sur les lignes, comme par exemple Cell phones – Accessories (Téléphones mobiles – Accessoires), Cell phones – Smartphones & PDAs (Téléphones mobiles – Smartphones et PDA), et ainsi de suite. Dans la vue Rapport ou Données (nous utilisons ici la vue Rapport), si nous observons nos tables de produit dans la liste Champs, nous constatons qu’aucun champ ne fournit ce que nous voulons. Nous avons toutefois un champ ProductCategory (CatégorieProduits) et un champ ProductSubcategory (SousCatégorieProduits), chacun dans sa propre table.

 ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_nonewcol.png)

Nous allons créer une colonne calculée pour combiner les valeurs de ces deux colonnes et obtenir de nouvelles valeurs pour notre nouvelle colonne. Il est intéressant de voir que vous devez combiner les données de deux tables différentes en une seule colonne. Comme nous utiliserons DAX pour créer la colonne, nous pouvons exploiter toute la puissance du modèle que nous possédons déjà, y compris les relations entre les différentes tables existantes.

### <a name="to-create-a-productfullcategory-column"></a>Pour créer une colonne ProductFullCategory
1.  Effectuez un clic droit ou cliquez sur la flèche orientée vers le bas dans la table **ProductSubcategory** figurant dans la liste Champs, puis cliquez sur **Nouvelle colonne**. Cela garantira l’ajout de la nouvelle colonne dans la table ProductSubcategory (SousCatégorieProduits).
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumn.png)
    
    La barre de formule apparaît en haut du canevas Rapport ou de la grille Données. C’est là que nous pouvons renommer la colonne et entrer une formule DAX.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumnformula.png)
    
    Par défaut une nouvelle colonne calculée est nommée simplement Colonne. Si vous ne la renommez pas, quand vous en créerez d’autres, elles seront nommées Colonne 2, Colonne 3, etc. Nous voulons que nos colonnes soient facilement identifiables. Nous allons donc renommer la nouvelle colonne.
    
2.  Comme le nom **Column** (Colonne) est déjà en surbrillance dans la barre de formule, il vous suffit de taper **ProductFullCategory** (CatégorieComplèteProduits).
    
    À présent, vous pouvez commencer à entrer la formule. Les valeurs de votre nouvelle colonne doivent commencer par le nom ProductCategory issu de la table ProductCategory. Comme cette colonne figure dans une table différente, bien qu’associée, nous devons utiliser la fonction [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) pour l’obtenir.
    
3.  Après le signe égal, tapez **R**. Une liste déroulante de suggestions s’affiche avec toutes les fonctions DAX commençant par la lettre R. Plus vous tapez de caractères, plus les suggestions de la liste se rapprochent de la fonction dont vous avez besoin. En regard de la fonction, vous verrez une description de la fonction. Sélectionnez **RELATED** en faisant défiler l’affichage et en appuyant sur Entrée.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_1.png)
    
    Une parenthèse ouvrante apparaît avec une autre liste de suggestions présentant toutes les colonnes disponibles que nous pouvons passer à la fonction RELATED. Une description et des détails sur les paramètres attendus sont également affichés.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_2.png)
    
    Une expression apparaît toujours entre une parenthèse ouvrante et une parenthèse fermante. Dans le cas présent, votre expression contiendra un seul argument passé à la fonction RELATED : une colonne associée à partir de laquelle renvoyer les valeurs. La liste des colonnes est automatiquement affinée pour afficher uniquement les colonnes associées. Dans le cas présent, c’est la colonne ProductCategory (CatégorieProduits) de la table du même nom qui nous intéresse.
    
    Sélectionnez **ProductCategory[ProductCategory]**, puis tapez une parenthèse fermante.
    
    > [!TIP]
    > Les erreurs de syntaxe sont le plus souvent provoquées par une parenthèse fermante manquante ou mal placée. Souvent, Power BI Desktop l’ajoute si vous l’avez oubliée.
    > 
    > 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_3.png)
    
4. Nous souhaitons ajouter un symbole de tiret pour séparer les valeurs. Après la parenthèse fermante de la première expression, tapez une espace, une esperluette (&), un guillemet, une espace, un tiret (-), une autre espace, un guillemet fermant, puis une autre esperluette. La formule doit maintenant ressembler à ceci :
    
    **ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &**
    
    > [!TIP]
    > Cliquez sur le chevron vers le bas situé à droite de la barre de formule pour développer l’éditeur de formule. Cliquez sur Alt et Entrée pour descendre d’une ligne et sur Tab pour déplacer les éléments.
    > 
    > 
    
5.  Enfin, entrez un autre crochet ouvrant, puis sélectionnez la colonne **[ProductSubcategory]** (SousCatégorieProduits) pour finir la formule. La formule doit ressembler à ceci :
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_5.png)
    
    Vous remarquerez que nous n’avons pas utilisé d’autre fonction RELATED dans la deuxième expression appelant la colonne ProductSubcategory (SousCatégorieProduits). Cela est dû au fait que cette colonne figure déjà dans la table où nous créons la nouvelle colonne. Nous pouvons entrer [ProductCategory] avec le nom de la table (qualifié complet) ou sans (non qualifié).
    
6.  Complétez la formule en appuyant sur Entrée ou en cliquant sur la coche dans la barre de formule. La formule est validée et ajoutée à la liste de champs dans la table **ProductSubcategory** (SousCatégorieProduits).
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_6.png)
    
    Vous remarquerez que les colonnes calculées sont marquées d’une icône spéciale dans la liste de champs. Cela indique qu’elles contiennent une formule. Elles apparaissent ainsi seulement dans Power BI Desktop. Dans le service PowerBI (votre site Power BI), il n’existe aucun moyen de modifier une formule. Un champ de colonne calculée n’a donc pas d’icône.
    
## <a name="lets-add-our-new-column-to-a-report"></a>Ajouter la nouvelle colonne à un rapport
À présent, nous pouvons ajouter la nouvelle colonne ProductFullCategory (CatégorieComplèteProduits) au canevas de rapport. Examinez SalesAmount (MontantVentes) par ProductFullCategory (CatégorieComplèteProduits).

Faites glisser la colonne **ProductFullCategory** (CatégorieComplèteProduits) de la table **ProductSubcategory** (SousCatégorieProduits) vers le canevas de rapport, puis faites glisser le champ **SalesAmount** (MontantVentes) de la table **Sales** (Ventes) vers le graphique.

![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_report_1.png)

## <a name="lets-create-another"></a>Création d’une autre colonne calculée
Maintenant que vous savez comment créer une colonne calculée, créez-en une autre.

Le modèle Contoso Sales for Power BI Desktop contient les données de ventes des magasins actifs et inactifs. Vous souhaitez montrer clairement que les données affichées pour les magasins inactifs sont identifiées en tant que telles. Dans les faits, vous souhaitez un champ nommé Active StoreName. Pour ce faire, vous allez créer une autre colonne. Dans le cas présent, nous voulons que notre nouvelle colonne Active StoreName (NomMagasin Actif) (en tant que champ) indique « Inactive » (Inactif) quand un magasin est inactif, mais qu’elle indique le nom réel du magasin s’il est actif.

Heureusement, notre table Stores (Magasins) a une colonne nommée Status (Statut) avec la valeur On pour les magasins actifs et la valeur Off pour les magasins inactifs. Nous pouvons tester ces valeurs pour chaque ligne de la colonne Status (Statut) pour créer des valeurs dans la nouvelle colonne.

### <a name="to-create-an-active-storename-column"></a>Pour créer une colonne Active StoreName
1.  Créez une colonne calculée nommée **Active StoreName** (NomMagasin Actif) dans la table **Stores** (Magasins).
    
    Pour cette colonne, la formule DAX va vérifier le statut de chaque magasin. Si le statut d’un magasin est On, la formule retourne le nom du magasin. Si sa valeur est Off, il aura le nom « Inactive ». Pour ce faire, nous allons utiliser la fonction logique [IF](https://msdn.microsoft.com/library/ee634824.aspx) pour tester le statut des magasins et retourner une valeur particulière si le résultat est true ou false.
    
2.  Commencez à taper **IF**. La liste de suggestions vous montre ce que vous pouvez ajouter. Sélectionnez **IF**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_1.png)
    
    Le premier argument pour IF est un test logique. Nous souhaitons vérifier si un magasin a le statut « On ».
    
3.  Tapez un crochet ouvrant **[**, qui permet de sélectionner des colonnes de la table Stores. Sélectionnez **[Status]**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_2.png)
    
4.  Juste après **[Status]**, tapez **="On"**, puis entrez une virgule (**,**) pour entrer le deuxième argument. L’info-bulle suggère d’ajouter la valeur à utiliser lorsque le résultat est true.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_3.png)
    
5.  Si le magasin a le statut On, nous voulons afficher le nom du magasin. Tapez un crochet ouvrant **[** et sélectionnez la colonne **[StoreName]**, puis tapez une autre virgule pour pouvoir entrer le troisième argument.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step5.png)
    
6.  Nous devons ajouter la valeur à utiliser quand le résultat est false. Dans ce cas, nous voulons que la valeur soit **« Inactive »**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step6.png)
    
7.  Complétez la formule en appuyant sur Entrée ou en cliquant sur la coche dans la barre de formule. La formule est validée et ajoutée à la liste de champs dans la table Stores (Magasins).
    
    Comme tout autre champ, nous pouvons utiliser la nouvelle colonne Active StoreName (NomMagasin Actif) dans les visualisations. Dans ce graphique, les magasins dont le statut est On sont affichés individuellement par nom, mais les magasins dont le statut est Off sont regroupés et indiqués comme étant inactifs. 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_viz.png)
    
## <a name="what-weve-learned"></a>Ce que vous avez appris
Les colonnes calculées peuvent enrichir vos données en favorisant des analyses simplifiées. Vous avez appris à créer des colonnes calculées à l’aide de la barre de formule, à utiliser la liste des suggestions et à nommer de manière optimale vos nouvelles colonnes.

## <a name="next-steps"></a>Étapes suivantes
Si vous souhaitez approfondir vos connaissances des formules DAX et créer des colonnes calculées avec des formules DAX plus avancées, consultez [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Cet article porte sur les concepts fondamentaux propres à DAX, tels que la syntaxe, les fonctions et une compréhension plus approfondie du contexte.

Veillez à ajouter la page [Informations de référence sur DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) à vos favoris. Vous y trouverez des informations détaillées sur la syntaxe DAX, les opérateurs et plus de 200 fonctions DAX.

