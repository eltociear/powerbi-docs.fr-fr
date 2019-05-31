---
title: 'Tutoriel : Combiner des données à partir d’Excel et d’un flux OData dans Power BI Desktop'
description: 'Tutoriel : Combiner des données à partir d’Excel et d’un flux OData'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 94e40681d065591db008f8a9062d851e0bd83f61
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61368565"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Tutoriel : Combiner des données de vente à partir d’Excel et d’un flux OData

Il est courant d’avoir des données réparties entre plusieurs sources de données, telles que des informations sur le produit dans une base de données et des données de vente dans une autre. Avec **Power BI Desktop**, vous pouvez combiner des données à partir de sources différentes pour créer des visualisations et des analyses de données intéressantes. 

Dans ce tutoriel, vous découvrez comment combiner des données à partir de deux sources de données : un classeur Excel qui contient des informations produit et un flux OData qui contient des données de commandes. Après avoir importé chaque jeu de données et effectué les opérations de transformation et d’agrégation, vous utilisez les données à partir des deux sources pour générer un rapport d’analyse des ventes avec des visualisations interactives. Ces techniques peuvent également être appliquées à des requêtes SQL Server, des fichiers CSV et d’autres sources de données dans Power BI Desktop.

>[!NOTE]
>Dans Power BI Desktop, vous pouvez souvent accomplir une tâche de plusieurs façons. Par exemple, plusieurs sélections dans le ruban sont également disponibles à l’aide d’un clic droit ou du menu **Plus d’options** sur une colonne ou une cellule. Plusieurs méthodes alternatives sont décrites dans les étapes ci-dessous. 

## <a name="import-the-product-data-from-excel"></a>Importer les données de produit à partir d’Excel

Tout d’abord, importez les données de produit à partir du classeur Excel Products.xlsx dans Power BI Desktop.

1. [Téléchargez le classeur Excel Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) et enregistrez-le sous **Products.xlsx**.
   
2. Sélectionnez la flèche déroulante en regard de **Obtenir des données** dans l’onglet **Accueil** du ruban Power BI Desktop, puis sélectionnez **Excel** dans la liste déroulante **Les plus courants**. 
   
   ![Obtenir les données](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >Vous pouvez également sélectionner l’élément **Obtenir des données** lui-même, ou sélectionnez **Obtenir des données** dans la boîte de dialogue **Prise en main** de Power BI, puis sélectionnez **Excel** ou **Fichier** > **Excel** dans la boîte de dialogue **Obtenir des données**, puis sélectionnez **Se connecter**.
   
3. Dans la boîte de dialogue **Ouvrir**, accédez au fichier **Products.xlsx**, ouvrez-le, puis sélectionnez **Ouvrir**.
   
4. Dans le volet **Navigateur**, sélectionnez la table **Products**, puis sélectionnez **Modifier**.
   
   ![Volet Navigateur pour Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
Un aperçu de la table s’ouvre dans **l’éditeur Power Query**, où vous pouvez appliquer des transformations pour nettoyer les données. 
   
![Éditeur Power Query](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>Vous pouvez également ouvrir **l’éditeur Power Query** en sélectionnant **Modifier les requêtes** > **Modifier les requêtes** à partir du ruban **Accueil** dans Power BI Desktop, ou en cliquant avec le bouton droit ou en choisissant **Plus d’options** en regard de n’importe quelle requête dans la **vue Rapport**, puis en sélectionnant **Modifier la requête**.

## <a name="clean-up-the-products-columns"></a>Nettoyer les colonnes de produits

Votre rapport combiné utilisera uniquement les colonnes **ProductID**, **ProductName**, **QuantityPerUnit** et **UnitsInStock** du classeur Excel, donc vous pouvez supprimer les autres colonnes. 

1. Dans **l’éditeur Power Query**, sélectionnez les colonnes **ProductID**, **ProductName**, **QuantityPerUnit** et **UnitsInStock** (utilisez **Ctrl**+**clic** pour sélectionner plusieurs colonnes ou **Maj**+**clic** pour sélectionner des colonnes adjacentes).
   
2. Cliquez avec le bouton droit sur l’un des en-têtes sélectionnés et choisissez **Supprimer d’autres colonnes** dans la liste déroulante, pour supprimer tout sauf les colonnes sélectionnées de la table. 
   Vous pouvez également sélectionner **Supprimer les colonnes** > **Supprimer d’autres colonnes** à partir du groupe **Gérer les colonnes** dans l’onglet du ruban **Accueil**. 
   
   ![Supprimer d’autres colonnes](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>Importer les données de commandes à partir d’un flux OData

Ensuite, importez les données de commandes à partir du flux OData sur l’exemple du système de ventes Northwind. 

1. Dans **l’éditeur Power Query**, sélectionnez **Nouvelle Source**, puis sélectionnez **Flux OData** dans la liste déroulante **Les plus courants**. 
   
   ![Obtenir OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. Dans la boîte de dialogue **Flux OData**, entrez l’URL du flux OData de Northwind, `http://services.odata.org/V3/Northwind/Northwind.svc/`, et sélectionnez **OK**.
   
   ![Boîte de dialogue Flux OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. Dans le volet **Navigateur**, sélectionnez la table **Commandes**, puis sélectionnez **OK** pour charger les données dans **l’éditeur Power Query**.
   
   ![Volet Navigateur pour OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >Dans le **Navigateur**, vous pouvez sélectionner n’importe nom de table, sans cocher la case, pour afficher un aperçu.

## <a name="expand-the-order-data"></a>Développer les données de commandes

Lorsque vous vous connectez à des sources de données qui ont plusieurs tables, comme des bases de données relationnelles ou le flux Northwind OData, vous pouvez utiliser des références entre les tables pour créer vos requêtes. La table **Commandes** contient des références à plusieurs tables connexes. Vous pouvez ajouter les colonnes **ProductID**, **UnitPrice** et **Quantity** à partir de la table **Order_Details** connexe dans la table objet ( **Commandes**) à l’aide de l’opération **Développer**. 

1. Faites défiler vers la droite dans la table **Commandes** jusqu’à ce que la colonne **Order_Details** s’affiche. Notez qu’au lieu de données, elle contient des références à une autre table.
   
   ![Colonne Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Sélectionnez l’icône **Développer** (![icône Développer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) dans l’en-tête de colonne **Order_Details**. 
   
3. Dans la liste déroulante **Développer** :
   
   1. Sélectionnez **(Sélectionner toutes les colonnes)** pour effacer toutes les colonnes.
      
   2. Sélectionnez **ProductID**, **UnitPrice** et **Quantity**, puis sélectionnez **OK**.
      
      ![Boîte de dialogue Développer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Après avoir développé la table **Order_Details**, la colonne **Order_Details** est remplacée par les trois nouvelles colonnes de la table imbriquée, et la table contient de nouvelles lignes pour les données ajoutées à partir de chaque commande. 

![Colonnes développées](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Créer une colonne calculée personnalisée

L’éditeur Power Query vous permet de créer des calculs et des champs personnalisés pour enrichir vos données. Vous allez créer une colonne personnalisée qui calcule le prix total pour chaque ligne dans une commande en multipliant le prix unitaire par la quantité d’articles.

1. Dans l’onglet du ruban **Ajouter une colonne** de l’éditeur Power Query, sélectionnez **Colonne personnalisée**.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. Dans la boîte de dialogue **Colonne personnalisée**, tapez **LineTotal** dans le champ **nouveau nom de colonne**.

3. Dans le champ **Formule de colonne personnalisé** après **=** , entrez **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** . (Vous pouvez également sélectionner les noms des champs à partir de la case de défilement **Colonnes disponibles** et sélectionner **<< insérer**, au lieu de les taper.) 
3. Sélectionnez **OK**.
   
   ![Boîte de dialogue Colonne personnalisée](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

Le nouveau champ **LineTotal** s’affiche en tant que dernière colonne dans la table **Commandes**.

## <a name="set-the-data-type-for-the-new-field"></a>Définir le type de données pour le nouveau champ

Lorsque l’éditeur Power Query se connecte aux données, il détermine le meilleur type de données pour chaque champ et affiche les données en conséquence. Vous pouvez voir les types de données assignés aux champs grâce aux icônes dans les en-têtes ou sous **Type de données** dans le groupe **Transformer** de l’onglet du ruban **Accueil**. 

Votre nouvelle colonne **LineTotal** a le type de données **N’importe lequel**, mais ses valeurs correspondent à la devise. Pour affecter un type de données, cliquez avec le bouton droit sur l’en-tête de la colonne **LineTotal**, sélectionnez **Modifier le type de données** dans la liste déroulante, puis sélectionnez **Nombre décimal fixe**. 

![Modifier le type de données](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>Vous pouvez également sélectionner la colonne **LineTotal**, puis la flèche déroulante en regard de **Type de données** dans la zone **Transformer** de l’onglet du ruban **Accueil**, puis sélectionnez **Nombre décimal fixe**.

## <a name="clean-up-the-orders-columns"></a>Nettoyer les colonnes de commandes

Pour simplifier l’utilisation de votre modèle dans les rapports, vous pouvez supprimer, renommer et réorganiser les colonnes.

Dans ce rapport, vous utiliserez uniquement les colonnes **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** et **Order_Details.Quantity**. Vous pouvez sélectionner ces colonnes et utiliser **Supprimer d’autres colonnes** comme vous l’avez fait avec les données Excel, ou vous pouvez sélectionner toutes les colonnes sauf celles répertoriées, cliquer avec le bouton droit sur l’une des colonnes sélectionnées et sélectionner **Supprimer les colonnes** pour toutes les supprimer. 

Vous pouvez rendre les colonnes **Order_Details.ProductID**, **Order_Details.UnitPrice** et **Order_Details.Quantity** plus faciles à identifier en supprimant les préfixes  *Order_Details.* dans les noms des colonnes. Pour renommer les colonnes en **ProductID**, **UnitPrice** et **Quantity**, respectivement :

1. Double-cliquez sur chaque en-tête de colonne, ou appuyez dessus en continu, ou cliquez avec le bouton droit sur l’en-tête de colonne et sélectionnez **Renommer** dans la liste déroulante. 
2. Supprimez les préfixes *Order_Details.* de chaque nom, puis appuyez sur **Entrée**.

Enfin, pour rendre la colonne **LineTotal** plus accessible, faites-la glisser vers la gauche et déposez-la, à droite de la colonne **ShipCountry**.

![Table nettoyée](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>Passer en revue les étapes de la requête

Lors de la mise en forme et de la transformation des données dans l’éditeur Power Query, chaque étape a été enregistrée dans la zone **Étapes appliquées** du volet **Paramètres de requête** à droite de l’éditeur Power Query. Vous pouvez consulter la section Étapes appliquées pour voir les modifications que vous avez effectuées. Si nécessaire, vous pouvez les modifier, les supprimer ou les réorganiser (mais cela peut être risqué, car la modification des étapes précédentes peut endommager les étapes suivantes). 

Sélectionnez chacune de vos requêtes dans la liste **Requêtes** sur le côté gauche de l’éditeur Power Query et passez en revue les **Étapes appliquées** dans **Paramètres de requête**. Après avoir appliqué les transformations de données précédentes, les Étapes appliquées pour vos deux requêtes doivent se présenter comme suit :

![Étapes appliquées de la requête Produits](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Étapes appliquées de la requête Commandes](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Sous-jacentes aux Étapes appliquées, des formules sont écrites dans le **langage Power Query**, également connu sous de langage **M**. Pour afficher et modifier les formules, sélectionnez **Éditeur avancé** dans le groupe **Requête** de l’onglet Accueil du ruban. 

## <a name="import-the-transformed-queries"></a>Importer les requêtes transformées

Lorsque vous êtes satisfait des données transformées, sélectionnez **Fermer et appliquer** > **Fermer et appliquer** dans le groupe **Fermer** de l’onglet **Accueil** du ruban pour les importer dans la vue Rapport de Power BI Desktop. 

![Fermer et appliquer](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Une fois les données chargées, les requêtes s’affichent dans la liste **Champs** de la vue Rapport de Power BI Desktop.

![Requêtes dans la liste Champs](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>Gérer la relation entre les jeux de données

Power BI Desktop ne vous demande pas de combiner des requêtes pour créer des rapports les concernant. Toutefois, vous pouvez utiliser les relations entre les jeux de données, en fonction des champs qu’ils ont en commun, pour étendre et enrichir vos rapports. Power BI Desktop peut détecter automatiquement les relations, ou vous pouvez les créer dans la boîte de dialogue **Gérer les relations** de Power BI Desktop. Pour plus d’informations plus sur les relations dans Power BI Desktop, consultez [Créer et gérer des relations](desktop-create-and-manage-relationships.md).

Les jeux de données Commandes et Produits dans ce tutoriel utilisent ont un champ *ProductID* en commun, donc il existe une relation entre eux basée sur cette colonne. 

1. Dans la vue Rapport de Power BI Desktop, sélectionnez **Gérer les relations** dans la zone **Relations** de l’onglet **Accueil** du ruban.
   
   ![Ruban Gérer les relations](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. Dans la boîte de dialogue **Gérer les relations**, notez que Power BI Desktop a déjà détecté et répertorié une relation active entre les tables Produits et Commandes. Pour afficher la relation, sélectionnez **Modifier**. 
   
   ![Boîte de dialogue Gérer les relations](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   La boîte de dialogue **Modifier la relation** s’ouvre et affiche des détails sur la relation.  
   
   ![Boîte de dialogue Modifier la relation](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. Power BI Desktop a détecté automatiquement la relation correctement, donc vous pouvez sélectionner **Annuler**, puis **Fermer** pour quitter les boîtes de dialogue relatives à la relation.

Vous pouvez également afficher et gérer les relations entre vos requêtes en sélectionnant la vue **Relation** sur le côté gauche de la fenêtre Power BI Desktop. Double-cliquez sur la flèche de la ligne reliant les deux requêtes pour ouvrir la boîte de dialogue **Modifier la relation** et afficher ou modifier la relation. 

![Vue Relation](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Pour revenir à la vue Rapport à partir de la vue Relation, sélectionnez l’icône **Vue Rapport**. 

![Icône Mode Rapport](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Créer des visualisations à l’aide de vos données

Dans la vue Rapport de Power BI Desktop, vous pouvez créer diverses visualisations pour obtenir des insights sur vos données. Vous pouvez générer des rapports de plusieurs pages et chaque page peut contenir plusieurs éléments visuels. Vous, et d’autres utilisateurs, pouvez interagir avec vos visualisations pour mieux analyser et comprendre vos données. Pour plus d’informations sur l’affichage et la modification des rapports dans le service Power BI (votre site), consultez [Modifier un rapport](service-interact-with-a-report-in-editing-view.md).

Vous pouvez utiliser vos deux jeux de données, et la relation entre eux, pour visualiser et analyser vos données de ventes. 

Commencez par créer un histogramme empilé qui utilise des champs des deux requêtes afin d’afficher la quantité de chaque produit commandé. 

1. Sélectionnez le champ **Quantité** sous **Commandes** dans le volet **Champs** à droite, ou faites-le glisser vers un espace vide du canevas. Cette opération crée un histogramme empilé affichant la quantité totale de tous les produits commandés. 
   
2. Sélectionnez **ProductName** sous **Produits** dans le volet **Champs**, ou faites-le glisser sur l’histogramme empilé pour afficher la quantité de chaque produit commandé. 
   
3. Pour trier les produits du plus commandé au moins commandé, sélectionnez les points de suspension **Plus d’options** ( **...** ) dans l’angle supérieur droit de la visualisation, puis sélectionnez **Trier par quantité**.
   
4. Utilisez les poignées dans les angles de l’histogramme empilé pour l’agrandir afin d’afficher davantage de noms de produits. 
   
   ![Graphique à barres Quantité par ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Ensuite, créez un graphique indiquant les montants en dollars des commandes (**LineTotal**) au fil du temps (**OrderDate**). 

1. Sans que rien ne soit sélectionné sur le canevas, sélectionnez **LineTotal** sous **Commandes** dans le volet **Champs**, ou faites-le glisser vers un espace vide sur le canevas. L’histogramme empilé affiche la somme totale en dollars de toutes les commandes. 
   
2. Avec le graphique sélectionné, sélectionnez **OrderDate** sous **Commandes**, ou faites-le glisser sur le graphique. Le graphique affiche maintenant les totaux par ligne pour chaque date de commande. 
   
3. Redimensionnez la visualisation en faisant glisser les angles pour afficher davantage de données. 
   
   ![Graphique en courbes LineTotals par OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Si seul l’élément Years s’affiche sur le graphique (trois points de données seulement), cliquez sur la flèche en regard de **OrderDate** dans le champ **Axe** du volet **Visualisations**, puis sélectionnez **OrderDate** au lieu de **Date Hierarchy**. 

Enfin, créez une visualisation Carte affichant les quantités de commande de chaque pays. 

1. Sans que rien ne soit sélectionné sur le canevas, sélectionnez **ShipCountry** sous **Commandes** dans le volet **Champs**, ou faites-le glisser vers un espace vide sur le canevas. Power BI Desktop détecte que les données sont des noms de pays et crée automatiquement une visualisation Carte, avec un point de données pour chaque pays avec des commandes. 
   
2. Pour que les tailles des points de données reflètent les quantités des commandes pour chaque pays, faites glisser le champ **LineTotal** sur la carte (ou faites-le glisser vers **Faire glisser les champs de données ici** sous **Taille**, dans la partie inférieure du volet **Visualisations**). Les tailles des cercles sur la carte reflètent désormais les montants en dollars des commandes de chaque pays. 
   
   ![Visualisation Carte LineTotals par ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interagir avec vos éléments visuels de rapports pour approfondir l’analyse

Power BI Desktop vous permet d’interagir avec les éléments visuels de manière à les comparer et à les filtrer pour dévoiler d’autres tendances. Pour plus d’informations, consultez [Filtrage et mise en surbrillance dans les rapports](power-bi-reports-filters-and-highlighting.md). 

En raison de la relation entre vos requêtes, les interactions avec une visualisation affectent toutes les autres visualisations sur la page. 

Sur la visualisation Carte, sélectionnez le cercle centré sur le **Canada**. Notez que les deux autres visualisations appliquent un filtre pour mettre en évidence les totaux de ligne et les quantités commandées uniquement pour le Canada.

![Données de ventes filtrées pour le Canada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Si vous sélectionnez l’un des produits dans le graphique **Quantité par ProductName**, la carte et le graphique de date sont filtrés pour refléter les données pour ce produit, et si vous sélectionnez l’une des dates dans le graphique **LineTotal par OrderDate**, la carte et le graphique de produit sont filtrés pour afficher les données correspondant à cette date. 
>[!TIP]
>Pour désélectionner une sélection, sélectionnez-la à nouveau, ou sélectionnez l’une des autres visualisations. 

## <a name="complete-the-sales-analysis-report"></a>Terminer le rapport d’analyse des ventes

Votre rapport terminé combine les données du fichier Excel Products.xlsx et du flux OData Northwind dans des éléments visuels qui vous aident à analyser les informations sur les commandes pour différents pays, dates et produits. Lorsque votre rapport est prêt, vous pouvez [le charger dans le service Power BI](desktop-upload-desktop-files.md) afin de le partager avec d’autres utilisateurs de Power BI.

## <a name="next-steps"></a>Étapes suivantes
* [Autres didacticiels Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Vidéos relatives à Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Forum Power BI](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Blog Power BI](http://go.microsoft.com/fwlink/?LinkID=519327)