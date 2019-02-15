---
title: Relations plusieurs à plusieurs dans Power BI Desktop
description: Utiliser des relations avec une cardinalité plusieurs à plusieurs dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 3f3c901140ca4f2ae2d93d1c3bc17bb519d41212
ms.sourcegitcommit: d010b10bc14097a1948daeffbc91b864bd91f7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56225957"
---
# <a name="relationships-with-a-many-many-cardinality-in-power-bi-desktop"></a>Relations avec une cardinalité plusieurs à plusieurs dans Power BI Desktop

La fonctionnalité des *relations avec une cardinalité plusieurs à plusieurs* dans Power BI Desktop vous permet de joindre des tables qui utilisent une cardinalité *plusieurs à plusieurs*. Vous pouvez créer plus facilement et intuitivement des modèles de données qui contiennent deux ou plusieurs sources de données. Cette fonctionnalité des *relations avec une cardinalité plusieurs à plusieurs* fait partie des fonctionnalités plus larges des *modèles composites* dans Power BI Desktop.

![Relation plusieurs à plusieurs dans le volet « Modifier la relation »](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La fonctionnalité des *relations avec une cardinalité plusieurs à plusieurs* dans Power BI Desktop fait partie d’un groupe de trois fonctionnalités connexes :

* **Modèles composites** : Permet à un rapport d’avoir deux connexions de données ou plus, y compris des connexions provenant de DirectQuery ou d’une importation, dans toutes les combinaisons. Pour plus d’informations, consultez [Modèles composites dans Power BI Desktop (préversion)](desktop-composite-models.md).

* **Relations avec une cardinalité plusieurs à plusieurs** : Avec les *modèles composites*, vous pouvez établir des *relations avec une cardinalité plusieurs à plusieurs* entre les tables. Cette approche supprime la nécessité d’avoir des valeurs uniques dans les tables. Les solutions de contournement précédentes, comme la présentation de nouvelles tables uniquement pour établir des relations, sont également supprimées. La fonctionnalité est décrite en détail dans cet article.

* **Mode de stockage** : Vous pouvez désormais spécifier les visuels qui nécessitent une requête sur les sources de données back-end. Les visuels qui ne nécessitent pas une requête sont importés même s’ils sont basés sur DirectQuery. Cette fonctionnalité permet d’améliorer les performances et de réduire la charge du back-end. Avant, même de simples visuels, comme les segments, démarraient des requêtes qui étaient envoyées à des sources back-end. Pour plus d’informations, consultez [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md).

## <a name="what-relationships-with-a-many-many-cardinality-solves"></a>Ce que les *relations avec une cardinalité plusieurs à plusieurs* permettent de résoudre

Avant que n’existent la fonctionnalité des *relations avec une cardinalité plusieurs à plusieurs*, la relation entre deux tables était définie dans Power BI. Au moins une des colonnes de table impliquées dans la relation devait contenir des valeurs uniques. Souvent, cependant, aucune colonne ne contenait de valeurs uniques. 

Par exemple, deux tables pouvaient avoir une colonne étiquetée *pays*, mais les valeurs de *pays* n’étaient pas uniques dans les tables. Pour joindre ces tables, il était nécessaire de créer une solution de contournement. Celle-ci pouvait consister à introduire dans le modèle des tables supplémentaires contenant les valeurs uniques nécessaires. Avec la fonctionnalité des *relations avec une cardinalité plusieurs à plusieurs*, vous pouvez joindre ces tables directement à l’aide d’une relation avec une cardinalité **plusieurs à plusieurs**.  

## <a name="use-relationships-with-a-many-many-cardinality"></a>Utiliser des *relations avec une cardinalité plusieurs à plusieurs*

Quand vous définissez une relation entre deux tables dans Power BI, vous devez définir la cardinalité de la relation. Par exemple, la relation entre *ProductSales* et *Product*&mdash;à l’aide des colonnes *ProductSales[ProductCode]* et *Product[ProductCode]*&mdash;serait définie en tant que relation *Plusieurs à 1*. Nous définissons la relation de cette façon, car il existe de nombreuses ventes de chaque produit et la colonne de la table *Product* *(ProductCode)* est unique. Quand vous définissez une cardinalité de relation de type *Plusieurs à 1*, *1 à plusieurs*, ou *1 à 1*, Power BI la valide pour s’assurer qu’elle correspond aux données réelles.

Par exemple, examinons le modèle simple dans l’image suivante :

![Vue de la relation](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Imaginons maintenant que la table *Product* affiche seulement deux lignes, comme suit :

![Visuel de la table Product avec deux lignes](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imaginez également que la table *Sales* a seulement quatre lignes, dont une ligne pour un produit C. En raison d’une erreur d’intégrité référentielle, le produit C n’existe pas dans la table *Product*.

![Visuel de la table Sales avec quatre lignes](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Les colonnes *ProductName* et *Price* (à partir de la table *Product*), ainsi que la quantité (*Qty*) totale pour chaque produit (à partir de la table *ProductSales*) se présenteraient comme suit : 

![Visuel montrant le nom du produit, le prix et la quantité](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Comme vous pouvez le voir dans l’image précédente, il existe une ligne *ProductName* vide qui est associée aux ventes du produit C. Cette ligne vide tient compte des éléments suivants :

* Toutes les lignes de la table *ProductSales* pour lesquelles aucune ligne correspondante n’existe dans la table *Product*. Il existe un problème d’intégrité référentielle, comme nous le voyons pour le produit *C* dans cet exemple.

* Toutes les lignes de la table *ProductSales* pour lesquelles la colonne clé étrangère est Null. 

Pour ces raisons, la ligne vide dans les deux cas tient compte des ventes où *ProductName* et *Price* sont inconnus.

Il arrive parfois que les tables soient jointes par deux colonnes, mais qu’aucune colonne ne soit unique. Par exemple, considérez les deux tables suivantes :

* La table *Sales* affiche les données de ventes par État (*State*), chaque ligne contenant le montant des ventes pour le type de vente dans l’État concerné. Les États incluent CA, WA et TX. 

    ![Table des ventes affichant les ventes par État](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La table *CityData* affiche des données sur les villes, y compris la population et l’État (dont les États de CA, de WA et de New York).

    ![Table des ventes montrant les villes, les États et la population](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Bien qu’il existe une colonne *State* dans les deux tables et qu’il soit raisonnable de créer des rapports sur le total des ventes par État et population totale de chaque État, il y a un problème : la colonne *State* n’est unique dans aucune des tables. 

## <a name="the-previous-workaround"></a>Solution de contournement précédente

Dans les versions de Power BI Desktop antérieures à la version de juillet 2018, les utilisateurs ne pouvaient pas créer de relation directe entre ces tables. Une solution de contournement courante consistait à effectuer les opérations suivantes :

* Créer une troisième table contenant uniquement les ID d’*État* uniques. La table pouvait être :
  * Une table calculée (définie à l’aide du langage DAX [Data Analysis Expressions]).
  * Une table basée sur une requête définie dans l’Éditeur de requête, qui pouvait afficher les ID uniques provenant d’une des tables.
  * L’ensemble combiné.

* Lier les deux tables d’origine à cette nouvelle table, à l’aide de relations *Plusieurs à 1* classiques.

Vous pouviez laisser la table de la solution de contournement visible ou la masquer afin qu’elle n’apparaisse pas dans la liste **Champs**. Si vous masquiez la table, la relation *plusieurs à 1* était généralement définie pour filtrer dans les deux directions et vous pouviez utiliser le champ *State* d’une des deux tables. Le filtrage croisé qui s’ensuivait assurait la propagation à l’autre table. Cette approche est illustrée dans l’image suivante :

![Vue de la relation](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un visuel affichant le champ *State* (État) (à partir de la table *CityData*), ainsi que la *Population* totale et les ventes (*Sales*) totales ressemblerait alors à ce qui suit :

![Visuel de la table](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Étant donné que l’État issu de la table *CityData* est utilisé dans cette solution de contournement, seuls les États de cette table sont répertoriés, ce qui explique l’exclusion de TX. De plus, contrairement aux relations *Plusieurs à 1*, alors que la ligne totale inclut toutes les *ventes* (y compris celles du TX), les détails n’incluent pas de ligne vide couvrant les lignes qui ne correspondent pas. De même, il n’y aurait pas de ligne vide couvrant les ventes (*Sales*) pour lesquelles il y a une valeur Null pour l’État (*State*).

Si vous ajoutez également *City* à ce visuel, bien que la population par ville (*City*) soit connue, les ventes (*Sales*) indiquées pour *City* reprennent les ventes (*Sales*) pour l’État (*State*) correspondant. C’est normalement le cas quand le regroupement dans une colonne n’est pas lié à une mesure d’agrégation, comme illustré dans l’image suivante :

![Visuel de la table](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Si nous définissons la nouvelle table *Sales* en tant que combinaison de tous les *États* dans cette solution de contournement et que nous la rendons visible dans la liste **Champs**, le même visuel afficherait *State* (État) (sur la nouvelle table), ainsi que la *Population* totale et les ventes (*Sales*) totales, comme illustré dans l’image suivante :

![Visuel de la table](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Comme vous pouvez le voir, *TX*&mdash;avec données *Sales*, mais données *Population* inconnues&mdash;et *New York*&mdash; avec données *Population* connues, mais aucune donnée *Sales* connue&mdash;seraient inclus. Cette solution de contournement n’est pas optimale et présente plusieurs problèmes. Depuis la création des relations avec une cardinalité plusieurs à plusieurs, les problèmes liés sont traités comme décrit dans la section suivante.

## <a name="use-relationships-with-a-many-many-cardinality-instead-of-the-workaround"></a>Utiliser les *relations avec une cardinalité plusieurs à plusieurs* au lieu de la solution de contournement

À compter de la version de juillet 2018 de Power BI Desktop, vous pouvez lier des tables directement, telles que celles que nous avons décrites précédemment, sans devoir recourir à des solutions de contournement similaires. Il est désormais possible de définir la cardinalité de la relation sur *Plusieurs à plusieurs*. Ce paramètre indique qu’aucune table ne contient de valeurs uniques. Pour ce type de relation, vous pouvez toujours contrôler quelle table filtre l’autre table, ou appliquer un filtrage bidirectionnel où chaque table filtre l’autre.  

Dans Power BI Desktop, la cardinalité par défaut est *Plusieurs à plusieurs* quand elle est détermine qu’aucune table ne contient de valeurs uniques pour les colonnes de la relation. Dans ces cas-là, un avertissement s’affiche pour confirmer que le paramètre de la relation est votre comportement prévu, et non l’effet non intentionnel d’un problème de données. 

Par exemple, quand vous créez une relation directe entre *CityData* et *Sales*&mdash;où les filtres devraient aller de *CityData* à *Sales*&mdash;Power BI Desktop affiche la fenêtre **Modifier la relation**, comme l’illustre l’image suivante :

![Fenêtre « Modifier la relation »](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La vue **Relation** résultante montrerait alors la relation directe plusieurs à plusieurs entre les deux tables. L’aspect des tables dans la liste **Champs** et leur comportement ultérieur à la création des visuels sont similaires à ceux observables pendant l’application de la solution de contournement. Dans la solution de contournement, la table supplémentaire qui affiche les données des différents États (*State*) n’est pas rendue visible. Par exemple, comme décrit dans la section précédente, un visuel montrant les données *State*, *Population* et *Sales* s’afficherait comme suit :

![Visuel de la table](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Les principales différences entre les *relations avec une cardinalité plusieurs à plusieurs* et les relations *plusieurs à une* plus courantes sont les suivantes :

* Les valeurs indiquées n’incluent pas de ligne vide tenant compte des lignes qui ne correspondent pas dans l’autre table. Les valeurs ne tiennent pas non plus compte des lignes dans lesquelles la colonne utilisée dans la relation dans l’autre table est Null.
* Il n’est pas possible d’utiliser la fonction `RELATED()`, car plusieurs lignes pourraient être liées.
* L’utilisation de la fonction `ALL()` sur une table ne supprime pas les filtres qui sont appliqués à d’autres tables reliées par une relation plusieurs à plusieurs. Dans l’exemple précédent, une mesure définie comme illustré dans le script suivant ne supprimerait pas de filtres de colonnes dans la table *CityData* reliée :

    ![Exemple de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Un visuel montrant les donnes *State*, *Sales* et *Sales total* ressemblerait à ce qui suit :

    ![Visuel de la table](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

En tenant compte des différences indiquées plus haut, assurez-vous que les calculs qui utilisent `ALL(\<Table>)`, tels que *% du total général*, retournent les résultats prévus. 


## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations pour cette version des *relations avec une cardinalité plusieurs à plusieurs* et des modèles composites.

Les sources (multidimensionnelles) Live Connect suivantes ne peuvent pas être utilisées avec les modèles composites :

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Jeux de données Power BI
* Azure Analysis Services

Quand vous vous connectez à ces sources multidimensionnelles à l’aide de DirectQuery, vous ne pouvez pas vous connecter à une autre source DirectQuery ou la combiner avec des données importées.

Les limitations existantes sur l’utilisation de DirectQuery s’appliquent encore quand vous utilisez des *relations avec une cardinalité plusieurs à plusieurs*. Plusieurs de ces limitations sont désormais appliquées par table, selon le mode de stockage de la table. Par exemple, une colonne calculée d’une table importée peut faire référence à d’autres tables, mais une colonne calculée d’une table DirectQuery ne peut faire référence qu’à des colonnes de la même table. D’autres limitations s’appliquent au modèle dans son ensemble si aucune des tables du modèle n’est de type DirectQuery. Par exemple, les fonctionnalités QuickInsights et Questions et réponses ne sont pas disponibles sur un modèle si une des tables qu’il contient présente un mode de stockage de type DirectQuery. 

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les modèles composites et DirectQuery, consultez les articles suivants :
* [Modèles composites dans Power BI Desktop (préversion)](desktop-composite-models.md)
* [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md)
* [Utiliser DirectQuery dans Power BI Desktop](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI Desktop](desktop-directquery-data-sources.md)
