---
title: Relations plusieurs à plusieurs dans Power BI Desktop
description: Utiliser des relations avec une cardinalité plusieurs à plusieurs dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761062"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Appliquer des relations plusieurs à plusieurs dans Power BI Desktop

Les *relations avec une cardinalité plusieurs à plusieurs* dans Power BI Desktop vous permettent de joindre des tables qui utilisent une cardinalité *plusieurs à plusieurs*. Vous pouvez créer plus facilement et intuitivement des modèles de données qui contiennent deux ou plusieurs sources de données. Les *relations avec une cardinalité plusieurs à plusieurs* font partie des fonctionnalités plus larges des *modèles composites* dans Power BI Desktop.

![Relation plusieurs à plusieurs dans le volet « Modifier la relation » de Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Une *relation avec une cardinalité plusieurs à plusieurs* dans Power BI Desktop comprend l’une de trois fonctionnalités connexes :

* **Modèles composites** : Un *modèle composite* permet à un rapport d’avoir deux connexions de données ou plus, y compris des connexions provenant de DirectQuery ou d’une importation, dans toutes les combinaisons. Pour plus d’informations, consultez [Utiliser des modèles composites dans Power BI Desktop](desktop-composite-models.md).

* **Relations avec une cardinalité plusieurs à plusieurs** : Avec les modèles composites, vous pouvez établir des *relations avec une cardinalité plusieurs à plusieurs* entre les tables. Cette approche supprime la nécessité d’avoir des valeurs uniques dans les tables. Les solutions de contournement précédentes, comme la présentation de nouvelles tables uniquement pour établir des relations, sont également supprimées. La fonctionnalité est décrite en détail dans cet article.

* **Mode de stockage** : Vous pouvez désormais spécifier les visuels qui nécessitent une requête sur les sources de données back-end. Les visuels qui ne nécessitent pas une requête sont importés même s’ils sont basés sur DirectQuery. Cette fonctionnalité permet d’améliorer les performances et de réduire la charge du back-end. Avant, même de simples visuels comme les segments démarraient des requêtes qui étaient envoyées à des sources back-end. Pour plus d’informations, consultez [Mode de stockage dans Power BI Desktop](desktop-storage-mode.md).

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Ce qu’une relation avec une cardinalité plusieurs à plusieurs permet de résoudre

Avant que n’existent les *relations avec une cardinalité plusieurs à plusieurs*, la relation entre deux tables était définie dans Power BI. Au moins une des colonnes de table impliquées dans la relation devait contenir des valeurs uniques. Souvent, cependant, aucune colonne ne contenait de valeurs uniques.

Par exemple, deux tables pouvaient avoir une colonne libellée Country. Pourtant, les valeurs de Country n’étaient pas uniques dans ces tables. Pour joindre ces tables, vous aviez besoin de créer une solution de contournement, pouvant consister à introduire des tables supplémentaires contenant les valeurs uniques nécessaires. Avec les *relations avec une cardinalité plusieurs à plusieurs*, vous pouvez joindre de telles tables directement si vous utilisez une relation avec une cardinalité *plusieurs à plusieurs*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Utiliser des relations avec une cardinalité plusieurs à plusieurs

Quand vous définissez une relation entre deux tables dans Power BI, vous devez définir la cardinalité de la relation. Par exemple, la relation entre ProductSales et Product (qui utilise les colonnes ProductSales[ProductCode] et Product[ProductCode]) serait définie en tant que relation *plusieurs à 1*. Nous définissons la relation de cette façon, car chaque produit a de nombreuses ventes et la colonne de la table Product (ProductCode) est unique. Quand vous définissez une cardinalité de relation de type *plusieurs à 1*, *1 à plusieurs* ou *1 à 1*, Power BI la valide de sorte que celle que vous choisissez corresponde aux données réelles.

Par exemple, examinons le modèle simple dans cette image :

![Tables ProductSales et Product, vue Relation (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Imaginons maintenant que la table **Product** affiche seulement deux lignes, comme suit :

![Visuel de la table Product avec deux lignes (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imaginez également que la table Sales a seulement quatre lignes, dont une ligne pour un produit C. En raison d’une erreur d’intégrité référentielle, le produit C n’existe pas dans la table **Product**.

![Visuel de la table Sales avec quatre lignes (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Les colonnes **ProductName** et **Price** (à partir de la table **Product**), ainsi que la quantité (**Qty**) totale pour chaque produit (à partir de la table ProductSales) se présenteraient comme suit :

![Visuel montrant le nom du produit, le prix et la quantité (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Comme vous pouvez le voir dans l’image précédente, une ligne **ProductName** vide est associée aux ventes du produit C. Cette ligne vide tient compte des éléments suivants :

* Toutes les lignes de la table **ProductSales** pour lesquelles aucune ligne correspondante n’existe dans la table **Product**. Il existe un problème d’intégrité référentielle, comme nous le voyons pour le produit C dans cet exemple.

* Toutes les lignes de la table **ProductSales** pour lesquelles la colonne clé étrangère est Null.

Pour ces raisons, la ligne vide dans les deux cas tient compte des ventes où **ProductName** et **Price** sont inconnus.

Parfois, les tables sont jointes par deux colonnes, pourtant aucune colonne n’est unique. Considérez par exemple ces deux tables :

* La table **Sales** affiche les données de ventes par État (**State**), chaque ligne contenant le montant des ventes pour le type de vente dans l’État concerné. Les États incluent CA, WA et TX.

    ![Table Sales montrant les ventes par état (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La table **CityData** affiche des données sur les villes, y compris la population et l’État (comme les États de CA, de WA et de New York).

    ![Table Sales montrant les villes, les États et la population (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Une colonne **État** figure désormais dans les deux tables. Il est raisonnable de vouloir créer des rapports sur les ventes totales par État et par population totale de chaque État. Toutefois, il existe un problème : la colonne **État** n’est pas unique dans les deux tables.

## <a name="the-previous-workaround"></a>Solution de contournement précédente

Avant la version de juillet 2018 de Power BI Desktop, vous ne pouviez pas créer une relation directe entre ces tables. Une solution de contournement courante consistait à :

* Créer une troisième table contenant uniquement les ID d’État uniques. La table pouvait être :
  * Une table calculée (définie à l’aide du langage DAX [Data Analysis Expressions]).
  * Une table basée sur une requête définie dans l’Éditeur de requête, qui pouvait afficher les ID uniques provenant d’une des tables.
  * L’ensemble combiné.

* Lier ensuite les deux tables d’origine à cette nouvelle table, à l’aide de relations *plusieurs à 1* classiques.

Vous pouviez laisser la table de la solution de contournement visible. Ou vous pouviez la masquer, afin qu’elle n’apparaisse pas dans la liste **Champs**. Si vous masquiez la table, la relation *plusieurs à 1* était généralement définie pour filtrer dans les deux directions et vous pouviez utiliser le champ State d’une des deux tables. Le filtrage croisé qui s’ensuivait assurait la propagation à l’autre table. Cette approche est illustrée dans l’image suivante :

![Table Hidden State, vue Relation,(Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un visuel affichant le champ **State** (État) (à partir de la table **CityData**), ainsi que la **Population** totale et les ventes (**Sales**) totales ressemblerait alors à ce qui suit :

![Tables State, Population et Sales (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Étant donné que l’État issu de la table **CityData** est utilisé dans cette solution de contournement, seuls les États de cette table sont listés, ce qui explique l’exclusion de TX. De plus, contrairement aux relations *plusieurs à 1*, alors que la ligne totale inclut toutes les **ventes** (y compris celles de TX), les détails n’incluent pas de ligne vide couvrant les lignes qui ne correspondent pas. De même, aucune ligne vide ne couvre les **ventes** pour lesquelles il existe une valeur Null pour l’**État**.

Supposons que vous ajoutez également City à ce visuel. Bien que la population par ville (City) soit connue, les ventes (**Sales**) indiquées pour City reprennent les ventes (**Sales**) pour l’État (**State**) correspondant. Ce scénario se produit normalement lorsque le regroupement de colonnes n’est pas lié à une mesure d’agrégation, comme illustré ici :

![Ventes et population des États et des villes (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Supposons que vous définissez la nouvelle table Sales comme la combinaison de tous les États ici et qu’elle est visible dans la liste **Champs**. Le même visuel afficherait **State** (État) (dans la nouvelle table), la **population** totale et les ventes (**Sales**) totales :

![Visuel avec les états, la population et les ventes (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Comme vous pouvez le voir, TX (dont les données **Sales** sont connues mais pas les données *Population*) et New York (dont les données **Population** sont connues mais pas les données **Sales**) seraient inclus. Cette solution de contournement n’est pas optimale et présente plusieurs problèmes. Pour les relations avec une cardinalité plusieurs à plusieurs, les problèmes liés sont traités, comme décrit dans la section suivante.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Utiliser une relation avec une cardinalité plusieurs à plusieurs au lieu de la solution de contournement

Avec la version de juillet 2018 de Power BI Desktop, vous pouvez lier des tables directement, telles que celles que nous avons décrites précédemment, sans devoir recourir à des solutions de contournement similaires. Il est désormais possible de définir la cardinalité de la relation sur *plusieurs à plusieurs*. Ce paramètre indique qu’aucune table ne contient de valeurs uniques. Pour ces relations, vous pouvez toujours contrôler la table qui filtre l’autre table. Vous pouvez également appliquer un filtrage bidirectionnel, où chaque table filtre l’autre.

Dans Power BI Desktop, la cardinalité par défaut est *plusieurs à plusieurs* quand elle détermine qu’aucune table ne contient de valeurs uniques pour les colonnes de la relation. Dans ce cas, un message d’avertissement confirme que vous voulez définir une relation, puis la modification n’a pas l’effet non souhaité d’un problème liés aux données.

Par exemple, quand vous créez une relation directe entre CityData et Sales (où les filtres devraient aller de CityData à Sales), Power BI Desktop affiche la boîte de dialogue **Modifier la relation** :

![Boîte de dialogue Modifier la relation (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La vue **Relation** résultante montrerait alors la relation directe plusieurs à plusieurs entre les deux tables. L’aspect des tables dans la liste **Champs** et leur comportement ultérieur à la création des visuels sont similaires à ceux observables pendant l’application de la solution de contournement. Dans la solution de contournement, la table supplémentaire qui affiche les données des différents États (State) n’est pas rendue visible. Comme décrit précédemment, un visuel montrant des données **State**, **Population** et **Sales** s’afficherait :

![Tables State, Population et Sales (Power BI Desktop)](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Les principales différences entre les *relations avec une cardinalité plusieurs à plusieurs* et les relations *plusieurs à une* plus courantes sont les suivantes :

* Les valeurs indiquées n’incluent pas de ligne vide tenant compte des lignes qui ne correspondent pas dans l’autre table. De plus, les valeurs ne tiennent pas compte des lignes dans lesquelles la colonne utilisée dans la relation dans l’autre table est Null.
* Vous ne pouvez pas utiliser la fonction `RELATED()`, car plusieurs lignes pourraient être liées.
* L’utilisation de la fonction `ALL()` sur une table ne supprime pas les filtres qui sont appliqués à d’autres tables reliées par une relation plusieurs à plusieurs. Dans l’exemple précédent, une mesure définie comme illustré ici ne supprimerait pas de filtres de colonnes dans la table CityData liée :

    ![Exemple de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Un visuel montrant des données **State**, **Sales** et **Sales total** donnerait ce graphique :

    ![Visuel de la table](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

En tenant compte des différences indiquées plus haut, vérifiez que les calculs qui utilisent `ALL(<Table>)`, tels que *% du total général*, retournent les résultats prévus.

## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations pour cette version des *relations avec une cardinalité plusieurs à plusieurs* et des modèles composites.

Les sources (multidimensionnelles) Live Connect suivantes ne peuvent pas être utilisées avec les modèles composites :

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Jeux de données Power BI
* Azure Analysis Services

Quand vous vous connectez à ces sources multidimensionnelles à l’aide de DirectQuery, vous ne pouvez pas vous connecter à une autre source DirectQuery ou la combiner avec des données importées.

Les limitations existantes sur l’utilisation de DirectQuery s’appliquent encore quand vous utilisez des *relations avec une cardinalité plusieurs à plusieurs*. De nombreuses limitations sont désormais appliquées par table, selon le mode de stockage de la table. Par exemple, une colonne calculée d’une table importée peut faire référence à d’autres tables, mais une colonne calculée d’une table DirectQuery ne peut faire référence qu’à des colonnes de la même table. D’autres limitations s’appliquent au modèle entier si aucune des tables du modèle n’est de type DirectQuery. Par exemple, les fonctionnalités QuickInsights et Questions et réponses ne sont pas disponibles sur un modèle si une des tables qu’il contient présente un mode de stockage de type DirectQuery.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les modèles composites et DirectQuery, consultez les articles suivants :
* [Utiliser des modèles composites dans Power BI Desktop](desktop-composite-models.md)
* [Mode de stockage dans Power BI Desktop](desktop-storage-mode.md)
* [Utiliser DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données Power BI](power-bi-data-sources.md)
