---
title: "Didacticiel : Analyse de données de ventes à partir d’Excel et d’un flux OData dans Power BI Desktop"
description: "Didacticiel : Analyse de données de ventes à partir d’Excel et d’un flux OData"
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
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 4cab3ed114d03d42c6acf1bf62f70e7d920e16b2
ms.sourcegitcommit: d91b7bf18d5c504037134f375886633379f28ede
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2018
---
# <a name="tutorial-analyzing-sales-data-from-excel-and-an-odata-feed"></a>Didacticiel : Analyse de données de ventes à partir d’Excel et d’un flux OData
**Power BI Desktop** vous permet de vous connecter à toutes sortes de sources de données, puis de les combiner et de les mettre en forme pour faciliter la création d’analyses et de visualisations de données attrayantes et intéressantes. Dans ce didacticiel, vous allez apprendre à combiner des données provenant de deux sources de données. 

Il est courant d’avoir des données réparties entre plusieurs sources de données, telles que des informations sur le produit dans une base de données et des données de vente dans une autre. Les techniques abordées dans ce document font appel à un classeur Excel et à un flux OData, mais vous pouvez aussi les appliquer à d’autres sources de données, comme des requêtes SQL Server, des fichiers CSV ou toute autre source de données dans Power BI Desktop.

Dans ce didacticiel, vous allez importer des données provenant d’Excel (informations sur des produits) et d’un flux OData (données sur des commandes). Vous effectuerez les étapes de transformation et d’agrégation et combinerez les données de ces deux sources pour générer un rapport **Total des ventes par produit et par an** qui inclura des visualisations interactives. 

Voici à quoi ressemblera le rapport final :

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

Pour suivre les étapes de ce didacticiel, vous avez besoin du classeur des produits disponible en téléchargement : **[Cliquez ici pour télécharger Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**

Dans la boîte de dialogue **Enregistrer sous**, nommez le fichier **Products.xlsx**.

## <a name="task-1-get-product-data-from-an-excel-workbook"></a>Tâche 1 : obtenir les données sur les produits à partir d’un classeur Excel
Dans cette tâche, vous allez importer des produits à partir du fichier Products.xlsx dans Power BI Desktop.

### <a name="step-1-connect-to-an-excel-workbook"></a>Étape 1 : se connecter à un classeur Excel
1. Démarrez Power BI Desktop.
2. Dans le ruban Accueil, sélectionnez **Obtenir des données**. Excel figurant parmi les connexions de données **Les plus courantes**, vous pouvez le sélectionner directement à partir du menu **Obtenir des données**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
3. Si vous sélectionnez directement le bouton Obtenir des données, vous pouvez aussi sélectionner **FIle \> Excel** et **Connecter.**
4. Dans la boîte de dialogue **Ouvrir un fichier**, sélectionnez le fichier **Products.xlsx**.
5. Dans le volet **Navigateur**, sélectionnez la table **Products**, puis sélectionnez **Modifier**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

### <a name="step-2-remove-other-columns-to-only-display-columns-of-interest"></a>Étape 2 : supprimer d’autres colonnes pour afficher uniquement les colonnes présentant un intérêt
Cette étape permet de supprimer toutes les colonnes sauf **ProductID**, **ProductName**, **UnitsInStock**et **QuantityPerUnit**. Dans Power BI Desktop, vous pouvez souvent accomplir la même tâche de plusieurs façons. Par exemple, bon nombre des opérations que vous pouvez effectuer à l’aide des boutons du ruban sont également accessibles en cliquant avec le bouton droit sur une colonne ou une cellule.

Power BI Desktop inclut un Éditeur de requête qui vous permet de mettre en forme et de transformer vos connexions de données. L’Éditeur de requête s’ouvre automatiquement quand vous sélectionnez **Modifier** à partir du **Navigateur**. Vous pouvez également ouvrir l’Éditeur de requête en sélectionnant **Modifier les requêtes** dans le ruban **Accueil** de Power BI Desktop. Les étapes suivantes sont effectuées dans l’Éditeur de requête.

1. Dans l’Éditeur de requête, sélectionnez les colonnes **ProductID**, **ProductName**, **QuantityPerUnit**et **UnitsInStock** (utilisez **Ctrl+clic** pour sélectionner plusieurs colonnes ou **Maj+clic** pour sélectionner des colonnes adjacentes).
2. Sélectionnez **Supprimer les colonnes** \> **Supprimer d’autres colonnes** dans le ruban ou cliquez avec le bouton droit sur un en-tête de colonne, puis cliquez sur **Supprimer d’autres colonnes**.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_removeothercolumns.png)

### <a name="step-3-change-the-data-type-of-the-unitsinstock-column"></a>Étape 3 : modifier le type de données de la colonne UnitsInStock
Quand l’Éditeur de requête se connecte aux données, il passe en revue chaque champ et détermine le meilleur type de données. Dans le classeur Excel, les produits en stock sont toujours des nombres entiers. Donc, dans cette étape, confirmez que la colonne **UnitsInStock** est de type Nombre entier.

1. Sélectionnez la colonne **UnitsInStock**.
2. Sélectionnez le bouton de liste déroulante **Type de données** dans le ruban **Accueil**.
3. Si l’option Nombre entier n’est pas déjà sélectionnée, spécifiez **Nombre entier** comme Type de données dans la liste déroulante (le bouton **Type de données** affiche également le type de données pour la sélection actuelle).
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_wholenumber.png)      

### <a name="power-bi-desktop-steps-created"></a>Étapes Power BI Desktop créées
Quand vous effectuez des activités liées à des requêtes dans l’Éditeur de requête, des étapes de requête sont créées et répertoriées dans le volet **Paramètres d’une requête**, dans la liste **Étapes appliquées**. Chaque étape de requête a une formule correspondante, également appelée langage « M ». Pour plus d’informations sur le langage des formules, ou « M », consultez [En savoir plus sur les formules Power BI](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

| Tâche | Étape de requête | Formule |
| --- | --- | --- |
| Se connecter à un classeur Excel |Source |Source{[Name="Products"]}[Data] |
| Promouvoir la première ligne en en-têtes des colonnes de la table |FirstRowAsHeader |[Table.PromoteHeaders](https://support.office.com/Article/TablePromoteHeaders-b8eaeb95-042a-42e1-9164-6d3c646acadc "Table.PromoteHeaders") <br /> (Produits) |
| Supprimer d’autres colonnes pour afficher uniquement les colonnes présentant un intérêt |RemovedOtherColumns |[Table.SelectColumns](https://support.office.com/Article/TableSelectColumns-20bb9e28-9fd3-4cd2-a21b-97972c82ec22 "Table.SelectColumns")  <br />(FirstRowAsHeader,{"ProductID", "ProductName", "QuantityPerUnit", "UnitsInStock"}) |
| Modifier le type de données |Changed Type |Table.TransformColumnTypes(\#"Removed Other Columns",{{"UnitsInStock", Int64.Type}}) |

## <a name="task-2-import-order-data-from-an-odata-feed"></a>Tâche 2 : importer les données de commandes à partir d’un flux OData
Dans cette tâche, vous allez importer les données de commandes. Cette étape représente une connexion à un système de vente. Les données sont importées dans Power BI Desktop à partir de l’exemple de flux Northwind OData figurant à l’adresse <http://services.odata.org/V3/Northwind/Northwind.svc/>. Copiez cette URM, puis collez-la dans les étapes ci-dessous. 

### <a name="step-1-connect-to-an-odata-feed"></a>Étape 1 : se connecter à un flux OData
1. Sous l’onglet **Accueil** du ruban de l’Éditeur de requête, sélectionnez **Obtenir les données**.
2. Accédez à la source de données **Flux OData**.
3. Dans la boîte de dialogue **Flux OData**, entrez l’ **URL** du flux OData de Northwind.
4. Sélectionnez **OK**.
5. Dans le volet **Navigateur**, sélectionnez la table **Orders**, puis sélectionnez **Modifier**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_odatafeed.png)

>[!NOTE]
>Vous pouvez cliquer sur un nom de table, sans cocher la case, pour afficher un aperçu.

### <a name="step-2-expand-the-orderdetails-table"></a>Étape 2 : Développer la table Order\_Details
La table **Orders** comporte une référence à une table **Details** qui contient les produits individuels inclus dans chaque commande. Quand vous vous connectez à des sources de données comprenant plusieurs tables (par exemple, une base de données relationnelle), vous pouvez utiliser ces références pour créer votre requête. 

Dans cette étape, vous développez la table **Order\_Details** associée à la table **Orders** pour combiner les colonnes **ProductID**, **UnitPrice** et **Quantity** de la table **Order\_Details** dans la table **Orders**. Voici une représentation des données dans ces tables :

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orderdetails.png)

L’opération **Développer** combine les colonnes d’une table associée dans une table sujet. Quand la requête est exécutée, les lignes de la table associée (**Order\_Details**) sont combinées dans les lignes de la table sujet (**Orders**).

Une fois la table **Order\_Details** développée, trois nouvelles colonnes et des lignes supplémentaires sont ajoutées à la table **Orders**, une pour chaque ligne de la table imbriquée ou associée.

1. Faites défiler la **vue Requête** jusqu’à la colonne **Order\_Details**.
2. Dans la colonne **Order\_Details**, cliquez sur l’icône de développement (![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)).
3. Dans la liste déroulante **Développer** :
   1. Sélectionnez **(Sélectionner toutes les colonnes)** pour effacer toutes les colonnes.
   2. Sélectionnez **ProductID**, **UnitPrice**et **Quantity**.
   3. Cliquez sur **OK**.
      ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)

### <a name="step-3-remove-other-columns-to-only-display-columns-of-interest"></a>Étape 3 : supprimer d’autres colonnes pour afficher uniquement les colonnes présentant un intérêt
Dans cette étape, vous supprimez toutes les colonnes à l’exception des colonnes **OrderDate, ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** et **Order\_Details.Quantity**. Dans la tâche précédente, vous avez utilisé **Supprimer d’autres colonnes**. Dans cette tâche, vous supprimez les colonnes sélectionnées.

1. Dans la vue **Requête**, sélectionnez toutes les colonnes en effectuant les opérations a. et b. :
   1. Cliquez sur la première colonne (**OrderID**).
   2. Appuyez sur Maj et cliquez sur la dernière colonne (**Shipper**).
   3. Une fois toutes les colonnes sélectionnées, utilisez Ctrl+clic pour désélectionner les colonnes suivantes : **OrderDate**, **ShipCity**, **ShipCountry**, **Order\_Details.ProductID**, **Order\_Details.UnitPrice** et **Order\_Details.Quantity**.
2. Seules les colonnes que vous souhaitez supprimer sont désormais sélectionnées. Cliquez avec le bouton droit sur n’importe quel en-tête de colonne sélectionnée, puis cliquez sur **Supprimer les colonnes**.

### <a name="step-4-calculate-the-line-total-for-each-orderdetails-row"></a>Étape 4 : Calculer le total de ligne pour chaque ligne Order\_Details
Power BI Desktop vous permet de créer des calculs basés sur les colonnes que vous importez pour enrichir les données auxquelles vous vous connectez. Dans cette étape, vous allez créer une colonne personnalisée (**Colonne personnalisée**) pour calculer le total de ligne de chaque ligne **Order\_Details**.

Calculer le total de ligne de chaque ligne **Order\_Details** :

1. Sous l’onglet **Ajouter une colonne** du ruban, cliquez sur **Ajouter** **une colonne personnalisée**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. Dans la boîte de dialogue **Ajouter une colonne personnalisée**, dans la zone de texte **Formule de colonne personnalisée**, entrez **[Order\_Details.UnitPrice] \* [Order\_Details.Quantity]**.
3. Dans la zone de texte **Nouveau nom de colonne**, entrez **LineTotal**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)
4. Cliquez sur **OK**.

### <a name="step-5-set-the-datatype-of-the-linetotal-field"></a>Étape 5 : définir le type de données du champ LineTotal
1. Cliquez avec le bouton droit sur la colonne **LineTotal**.
2. Sélectionnez **Modifier le type** et choisissez **Nombre décimal**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

### <a name="step-6-rename-and-reorder-columns-in-the-query"></a>Étape 6 : renommer et réorganiser les colonnes dans la requête
Dans cette étape, vous allez finir de rendre le modèle facile à utiliser lors de la création de rapports en renommant les colonnes finales et en modifiant leur ordre.

1. Dans l’ **Éditeur de requêtes**, faites glisser la colonne **LineTotal** vers la gauche, après **ShipCountry**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
2. Supprimez le préfixe *Order\_Details.* des colonnes **Order\_Details.ProductID**, **Order\_Details.UnitPrice** et **Order\_Details.Quantity** en double-cliquant sur chaque en-tête de colonne et en supprimant ce texte du nom de la colonne.

### <a name="power-bi-desktop-steps-created"></a>Étapes Power BI Desktop créées
Quand vous effectuez des activités liées à des requêtes dans l’Éditeur de requête, des étapes de requête sont créées et répertoriées dans le volet **Paramètres d’une requête**, dans la liste **Étapes appliquées**. Chaque étape de requête a une formule Power Query correspondante, également appelée langage « M ». Pour plus d’informations sur ce langage de formules, consultez [En savoir plus sur les formules Power BI](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f "En savoir plus sur les formules Power Query").

| Tâche | Étape de requête | Formule |
| --- | --- | --- |
| Se connecter à un flux OData |Source |Source{[Name="Orders"]}[Data] |
| Développer la table Order\_Details |Développer Order\_Details |[Table.ExpandTableColumn](https://support.office.com/Article/TableExpandTableColumn-54903f25-75a2-4a44-a9a3-52a9d895ee98 "Table.ExpandTableColumn") <br /> (Orders, "Order\_Details", {"ProductID", "UnitPrice", "Quantity"}, {"Order\_Details.ProductID", "Order\_Details.UnitPrice", "Order\_Details.Quantity"}) |
| Supprimer d’autres colonnes pour afficher uniquement les colonnes présentant un intérêt |RemovedColumns |[Table.RemoveColumns](https://support.office.com/Article/TableRemoveColumns-6265190e-2f58-4300-85b8-df88fc1a67d3 "Table.RemoveColumns") <br />(\#"Expand Order\_Details",{"OrderID", "CustomerID", "EmployeeID", "RequiredDate", "ShippedDate", "ShipVia", "Freight", "ShipName", "ShipAddress", "ShipCity", "ShipRegion", "ShipPostalCode", "ShipCountry", "Customer", "Employee", "Shipper"}) |
| Calculer le total de ligne de chaque ligne Order\_Details |InsertedColumn |[Table.AddColumn](https://support.office.com/Article/TableAddColumn-6c64d0a5-9654-4d15-bfb6-9cc380aaf3c0 "Table.AddColumn") <br /> (RemovedColumns, "Custom", each [Order\_Details.UnitPrice] \* [Order\_Details.Quantity]) |

## <a name="task-3-combine-the-products-and-total-sales-queries"></a>Tâche 3 : combiner les requêtes Products et Total Sales
Power BI Desktop ne vous demande pas de combiner des requêtes pour créer des rapports les concernant. Au lieu de cela, vous pouvez créer des **relations** entre les jeux de données. Ces relations peuvent être créées sur une colonne quelconque commune à vos jeux de données. Pour plus d’informations, consultez [Créer et gérer les relations](desktop-create-and-manage-relationships.md).

Dans ce didacticiel, nous avons des données Orders et Products qui possèdent un champ « ProductID » en commun. Vous devez donc vous assurer qu’il existe une relation entre ces données dans le modèle que nous utilisons avec Power BI Desktop. Pour cela, il vous suffit de spécifier dans Power BI Desktop que les colonnes de chaque table sont liées (c’est-à-dire les colonnes qui ont les mêmes valeurs). Power BI Desktop détermine pour vous la direction et la cardinalité de la relation. Dans certains cas, il détecte même les relations automatiquement.

Dans cette tâche, vous confirmez qu’une relation est établie dans Power BI Desktop entre les requêtes **Products** et **Total Sales**.

### <a name="step-1-confirm-the-relationship-between-products-and-total-sales"></a>Étape 1 : confirmer la relation entre Products et Total Sales
1. Commençons par charger le modèle que nous avons créé dans l’Éditeur de requête dans Power BI Desktop. Dans le ruban **Accueil** de l’Éditeur de requête, sélectionnez **Charger et fermer**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. Power BI Desktop charge les données à partir des deux requêtes.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)      
3. Une fois les données chargées, sélectionnez le bouton **Gérer les relations** dans le ruban **Accueil**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
4. Sélectionnez le bouton **Nouveau** ...
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
5. Quand vous essayez de créer la relation, vous constatez qu’il en existe déjà une ! Comme le montrent les colonnes grisées de la boîte de dialogue **Créer une relation**, les champs **ProductsID** dans chaque requête ont déjà une relation établie.
   
    ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)
6. Sélectionnez **Annuler**, puis sélectionnez la vue **Relation** dans Power BI Desktop.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
7. Une représentation visuelle de la relation entre les requêtes s’affiche.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)
8. Quand vous double-cliquez sur la flèche sur la ligne qui connecte les deux requêtes, une boîte de dialogue **Modifier la relation** apparaît.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)
9. Il est inutile d’apporter des modifications. Sélectionnez simplement **Annuler** pour fermer la boîte de dialogue **Modifier la relation**.

## <a name="task-4-build-visuals-using-your-data"></a>Tâche 4 : créer des éléments visuels à l’aide de vos données
Power BI Desktop vous permet de créer diverses visualisations pour obtenir des informations détaillées sur vos données. Vous pouvez générer des rapports de plusieurs pages et chaque page peut contenir plusieurs éléments visuels. Vous pouvez interagir avec vos visualisations pour mieux analyser et comprendre vos données. Pour plus d’informations sur la modification des rapports, consultez [Modifier un rapport](service-interact-with-a-report-in-editing-view.md).

Dans cette tâche, vous créez un rapport basé sur les données précédemment chargées. Vous utilisez le volet Champs pour sélectionner les colonnes à partir desquelles vous créez les visualisations.

### <a name="step-1-create-charts-showing-units-in-stock-by-product-and-total-sales-by-year"></a>Étape 1 : créer des graphiques indiquant les unités en stock par produit et le total des ventes par année
Faites glisser **UnitsInStock** à partir du volet Champs (situé à droite de l’écran) dans une zone vide du canevas. Une visualisation Table est créée. Ensuite, faites glisser ProductName dans la zone Axe qui se trouve dans la partie inférieure du volet Visualisations. Sélectionnez **Trier par \> UnitsInStock** à l’aide des points situés dans le coin supérieur droit de la visualisation.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

Faites glisser **OrderDate** dans le canevas sous le premier graphique, puis faites glisser LineTotal (là encore, à partir du volet Champs) dans l’élément visuel, puis sélectionnez Graphique en courbes. La visualisation suivante est créée.

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png)

 Ensuite, faites glisser **ShipCountry** dans un endroit du canevas, en haut à droite. Comme vous avez sélectionné un champ géographique, une carte est créée automatiquement. Maintenant, faites glisser **LineTotal** dans le champ **Valeurs**. La taille des cercles représentés sur la carte reflète désormais le montant des commandes expédiées vers chaque pays (**LineTotal**).

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

### <a name="step-2-interact-with-your-report-visuals-to-analyze-further"></a>Étape 2 : interagir avec vos éléments visuels de rapports pour approfondir l’analyse
Power BI Desktop vous permet d’interagir avec les éléments visuels de manière à les comparer et à les filtrer pour dévoiler d’autres tendances. Pour plus d’informations, consultez [Filtrage et mise en surbrillance dans les rapports](power-bi-reports-filters-and-highlighting.md)

1. Cliquez sur le cercle bleu clair centré sur **Canad****a.** Notez la manière dont les autres éléments visuels sont filtrés pour afficher le stock (**ShipCountry**) et le nombre total de commandes (**LineTotal**) uniquement pour le Canada.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="complete-sales-analysis-report"></a>Rapport complet d’analyse des ventes
Une fois toutes ces étapes terminées, vous obtenez un rapport des ventes qui combine les données du fichier Products.xlsx et du flux OData de Northwind. Ce rapport présente des éléments visuels favorisant l’analyse des informations de vente issues de différents pays. Vous pouvez télécharger un fichier Power BI Desktop complet pour ce didacticiel [ici](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Sales_Data.pbix).

## <a name="next-steps"></a>Étapes suivantes
* [Autres didacticiels Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Vidéos relatives à Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Forum Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Blog Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)


