---
title: 'Didacticiel : création de colonnes calculées dans Power BI Desktop'
description: 'Didacticiel : création de colonnes calculées dans Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/26/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: cdd4f4f5058b57cbf59a3a0b35286243bd8c8f37
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75731716"
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Didacticiel : création de colonnes calculées dans Power BI Desktop

Parfois, les données que vous analysez ne contiennent pas de champ particulier vous permettant d’obtenir les résultats que vous recherchez. C’est là qu’interviennent les *colonnes calculées*. Les colonnes calculées utilisent des formules du langage DAX (Data Analysis Expressions) pour définir les valeurs d’une colonne, assembler des valeurs de texte à partir de deux colonnes différentes jusqu’à calculer une valeur numérique à partir d’autres valeurs. Par exemple, supposons que vos données incluent des champs **Ville** et **État**, mais que vous voulez un champ **Emplacement** unique qui possède ces deux informations, par exemple « Miami, FL ». C’est là précisément qu’interviennent les colonnes calculées.

Les colonnes calculées sont semblables aux [mesures](desktop-tutorial-create-measures.md), dans le sens où toutes deux reposent sur des formules DAX, mais elles diffèrent dans la manière dont elles sont utilisées. Vous utilisez souvent des mesures dans une zone **Valeurs** d’une visualisation pour calculer les résultats en fonction des autres champs. Vous utilisez des colonnes calculées en tant que nouveaux **Champs** dans les lignes, les axes, les légendes et les zones de groupes de visualisations.

Ce tutoriel va vous aider à comprendre et à créer les colonnes calculées et à les utiliser dans des visualisations de rapports dans Power BI Desktop.

## <a name="prerequisites"></a>Conditions préalables

- Ce didacticiel s’adresse aux utilisateurs de Power BI déjà familiarisés avec l’utilisation de Power BI Desktop pour créer des modèles plus avancés. Vous devez déjà savoir comment utiliser Obtenir des données et l’Éditeur Power Query pour importer des données, travailler sur plusieurs tables associées et ajouter des champs au canevas de rapport. Si vous découvrez seulement Power BI Desktop, veillez à consulter [Prise en main de Power BI Desktop](desktop-getting-started.md).
  
- Ce tutoriel utilise [l’exemple de vente Contoso pour Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), le même utilisé pour le tutoriel [Créer vos propres mesures dans Power BI Desktop](desktop-tutorial-create-measures.md). Ces données de ventes de la société fictive Contoso, Inc. ont été importées à partir d’une base de données, vous ne pourrez donc pas vous connecter à la source de données ni l’afficher dans l’Éditeur Power Query. Téléchargez et extrayez le fichier sur votre propre ordinateur, puis ouvrez-le dans Power BI Desktop.

## <a name="create-a-calculated-column-with-values-from-related-tables"></a>Créer une colonne calculée avec des valeurs de tables associées

Dans votre rapport de ventes, vous souhaitez afficher des catégories et des sous-catégories de produits sous des valeurs uniques, comme par exemple « Téléphones mobiles – Accessoires », « Téléphones mobiles – Smartphones et PDA », et ainsi de suite. Il n’existe aucun champ dans la liste **Champs** qui vous donne ces données, mais il existe un champ **ProductCategory** et un champ **ProductSubcategory**, chacun dans sa propre table. Vous pouvez créer une colonne calculée qui combine les valeurs de ces deux colonnes. Les formules DAX peuvent tirer profit de la pleine puissance du modèle que vous possédez déjà, y compris les relations entre les différentes tables existantes.

 ![Colonnes dans la liste Champs](media/desktop-tutorial-create-calculated-columns/create1.png)

1. Pour créer votre nouvelle colonne dans la table **ProductSubcategory**, cliquez avec le bouton droit sur les points de suspension **...** (ou sélectionnez) en regard de **ProductSubcategory** dans le volet **Champs**, puis sélectionnez **Nouvelle colonne** dans le menu.

   ![Nouvelle colonne](media/desktop-tutorial-create-calculated-columns/create2.png)

   Quand vous sélectionnez **Nouvelle colonne**, la **barre de formule** apparaît au-dessus du canevas de rapport, où vous pouvez nommer votre colonne et entrer une formule DAX.

   ![Barre de formule](media/desktop-tutorial-create-calculated-columns/create3.png)

2. Par défaut, une nouvelle colonne calculée est nommée **Colonne**. Si vous ne la renommez pas, les nouvelles colonnes supplémentaires seront nommées **Colonne 2**, **Colonne 3** et ainsi de suite. Si vous voulez que votre colonne soit plus identifiable, dans la barre de formule où le nom **Colonne** est déjà en surbrillance, renommez-la en tapant **ProductFullCategory**, puis tapez un signe égal ( **=** ).

3. Les valeurs de votre nouvelle colonne doivent commencer par le nom figurant dans le champ **ProductCategory**. Comme cette colonne figure dans une table différente, bien qu’associée, vous pouvez utiliser la fonction [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) pour l’obtenir.

   Après le signe égal, saisissez **r**. Une liste déroulante de suggestions affiche toutes les fonctions DAX commençant par la lettre R. La sélection de chaque fonction permet d’afficher une description de ses effets. La saisie permet de mettre à l’échelle la liste de suggestions au plus proche de la fonction dont vous avez besoin. Sélectionnez **RELATED**, puis appuyez sur **Entrée**.

   ![Choisir RELATED](media/desktop-tutorial-create-calculated-columns/create4.png)

   Une parenthèse ouvrante apparaît avec une autre liste de suggestions des colonnes associées, que vous pouvez passer à la fonction RELATED, avec les descriptions et les détails des paramètres attendus.

   ![Choisir ProductCategory](media/desktop-tutorial-create-calculated-columns/create5.png)

4. Vous souhaitez la colonne **ProductCategory** de la table **ProductCategory**. Sélectionnez **ProductCategory[ProductCategory]** , appuyez sur **Entrée**, puis saisissez un type de parenthèse fermante.

    > [!TIP]
    > Les erreurs de syntaxe sont le plus souvent provoquées par une parenthèse fermante manquante ou mal placée, bien que parfois Power BI Desktop l’ajoute pour vous.

5. Vous avez tout intérêt à séparer les nouvelles valeurs de **ProductCategoriy** et **ProductSubcategory** avec des tirets et des espaces. Ainsi, après la parenthèse fermante de la première expression, tapez un espace, une esperluette ( **&** ), un guillemet double ( **"** ), un espace, un tiret ( **-** ), un autre espace, un autre guillemet double et une autre esperluette. La formule doit maintenant ressembler à ceci :

    `ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &`

    > [!TIP]
    > S’il vous faut plus d’espace, sélectionnez le chevron vers le bas situé à droite de la barre de formules pour développer l’éditeur de formules. Dans l’éditeur, appuyez sur **Alt et Entrée** pour descendre d’une ligne et sur **Tab** pour déplacer les éléments.

6. Saisissez un crochet ouvrant ( **[** ), puis sélectionnez la colonne **[ProductSubcategory]** pour finir la formule. 

    ![Choisir ProductSubcategory](media/desktop-tutorial-create-calculated-columns/create6.png)

    Il n’est pas nécessaire d’utiliser une autre fonction RELATED pour appeler la table **ProductSubcategory** dans la deuxième expression, car vous créez la colonne calculée dans cette table. Vous pouvez entrer **[ProductSubCategory]** avec le préfixe du nom de la table (pleinement qualifié) ou sans (non qualifié).

7. Complétez la formule en appuyant sur **Entrée** ou en sélectionnant la coche dans la barre de formules. Une fois la formule validée, le nom de colonne **ProductFullCategory** apparaît dans la table **ProductSubcategory** dans le volet **Champs**.

   ![Colonne ProductFullCategory finie](media/desktop-tutorial-create-calculated-columns/create7.png)

    >[!NOTE]
    >Dans Power BI Desktop, les colonnes calculées sont associées à une icône spéciale dans le volet **Champs**, qui indique qu’elles contiennent des formules. Dans le service PowerBI (votre site Power BI), il n’existe aucun moyen pour modifier des formules. Les colonnes calculées n’ont donc pas d’icônes.

## <a name="use-your-new-column-in-a-report"></a>Utiliser votre nouvelle colonne dans un rapport

Maintenant, vous pouvez utiliser votre nouvelle colonne **ProductFullCategory** pour afficher **SalesAmount** par **ProductFullCategory**.

1. Sélectionnez ou faites glisser la colonne **ProductFullCategory** de la table **ProductSubcategory** vers le canevas de rapport pour créer une table présentant tous les noms de **ProductFullCategory**.

   ![Table ProductFullCategory](media/desktop-tutorial-create-calculated-columns/vis1.png)

2. Sélectionnez ou faites glisser le champ **SalesAmount** de la table **Sales** vers la table pour afficher **SalesAmount** pour chaque **ProductFullCategory**.

   ![Table SalesAmount par ProductFullCategory](media/desktop-tutorial-create-calculated-columns/vis2.png)

## <a name="create-a-calculated-column-that-uses-an-if-function"></a>Créer une colonne calculée qui utilise une fonction IF

L’exemple de vente Contoso contient les données de ventes des magasins actifs et inactifs. Vous pouvez séparer clairement les ventes des magasins actifs des ventes des magasins inactifs dans votre rapport en créant un champ **Active StoreName**. Dans la nouvelle colonne calculée **Active StoreName**, chaque magasin actif apparaîtra avec le nom complet du magasin, tandis que les ventes des magasins inactifs seront regroupées dans une ligne appelée **Inactive**.

Heureusement, la table **Stores** contient une colonne nommée **Status**, avec les valeurs « On » pour les magasins actifs et « Off » pour les magasins inactifs, que nous pouvons utiliser pour créer les valeurs de la nouvelle colonne **Active StoreName**. Votre formule DAX utilise la fonction logique [IF](https://msdn.microsoft.com/library/ee634824.aspx) pour tester l’état (**Status**) de chaque magasin et retourner une valeur particulière selon le résultat. Si la valeur **Status** d’un magasin est « On », la formule retourne le nom du magasin. Si la valeur est « Off », la formule attribue à **Active StoreName** la valeur « Inactive ».

1. Créez une nouvelle colonne calculée dans la table **Magasins** et nommez-la **Active StoreName** dans la barre de formules.

2. Après le signe **=** , commencez à taper **IF**. La liste de suggestions vous montre ce que vous pouvez ajouter. Sélectionnez **IF**.

    ![Sélectionner IF](media/desktop-tutorial-create-calculated-columns/if1.png)

3. Le premier argument pour **IF** est un test logique qui vise à déterminer si la valeur **Status** d’un magasin est « On ». Tapez un crochet ouvrant **[** pour lister les colonnes de la table **Stores**, puis sélectionnez **[Status]** .

    ![Sélectionnez État](media/desktop-tutorial-create-calculated-columns/if2.png)

4. Juste après **[État]** , saisissez **= « Activé »** , puis saisissez une virgule ( **,** ) à la fin de l’argument. L’info-bulle suggère que vous devez maintenant ajouter une valeur de retour lorsque le résultat est TRUE.

    ![Ajouter la valeur TRUE](media/desktop-tutorial-create-calculated-columns/if3.png)

5. Si l’état du magasin est « Activé », vous souhaitez afficher le nom du magasin. Saisissez un crochet ouvrant ( **[** ) et sélectionnez la colonne **[StoreName]** , puis saisissez une autre virgule. L’info-bulle indique à présent que vous devez ajouter une valeur de retour lorsque le résultat est FALSE.

    ![Ajouter la valeur FALSE](media/desktop-tutorial-create-calculated-columns/if4.png)

6. Comme vous souhaitez que la valeur soit « Inactive », tapez **« Inactive »** , puis complétez la formule en appuyant sur **Entrée** ou en sélectionnant la coche dans la barre de formule. Une fois la formule validée, le nom de la nouvelle colonne apparaît dans la table **Stores** dans le volet **Champs**.

    ![Colonne Active StoreName](media/desktop-tutorial-create-calculated-columns/if5.png)

7. Vous pouvez utiliser votre nouvelle colonne **Active StoreName** dans les visualisations comme n’importe quel autre champ. Pour afficher **SalesAmounts** par **Active StoreName**, sélectionnez le champ **Active StoreName** ou faites-le glisser vers le canevas de rapport, puis sélectionnez le champ **SalesAmount** ou faites-le glisser dans la table. Dans cette table, les magasins actifs apparaissent individuellement par nom, mais les magasins inactifs sont rassemblés à la fin comme **Inactif**.

    ![SalesAmount par table Active StoreName](media/desktop-tutorial-create-calculated-columns/if6.png)

## <a name="what-youve-learned"></a>Ce que vous avez appris

Les colonnes calculées peuvent enrichir vos données en favorisant des insights simplifiés. Vous avez appris à créer des colonnes calculées dans le volet **Champs** et la barre de formule, à utiliser des listes de suggestions et des info-bulles pour vous aider à construire des formules, à appeler des fonctions DAX comme RELATED et IF avec les arguments appropriés et à utiliser vos colonnes calculées dans des visualisations de rapport.

## <a name="next-steps"></a>Étapes suivantes

Si vous souhaitez approfondir vos connaissances des formules DAX et créer des colonnes calculées avec des formules plus avancées, consultez [Informations de base sur DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Cet article porte sur les concepts fondamentaux propres à DAX, tels que la syntaxe, les fonctions et une compréhension plus approfondie du contexte.

Pensez à ajouter la page [Informations de référence sur DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) à vos favoris. Vous y trouverez des informations détaillées sur la syntaxe DAX, les opérateurs et plus de 200 fonctions DAX.
