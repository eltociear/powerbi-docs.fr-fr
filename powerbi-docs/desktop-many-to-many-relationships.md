---
title: Relations plusieurs-à-plusieurs dans Power BI Desktop (préversion)
description: Utiliser des relations plusieurs à plusieurs dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/23/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 1105de002f6461589d61c6f0077cceeedaada471
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39210888"
---
# <a name="many-to-many-relationships-in-power-bi-desktop-preview"></a>Relations plusieurs-à-plusieurs dans Power BI Desktop (préversion)

La fonctionnalité **Relation plusieurs à plusieurs** dans **Power BI Desktop** vous permet de joindre des tables à l’aide d’une cardinalité de **plusieurs à plusieurs** et de créer des modèles de données contenant plusieurs sources de données plus facilement et de manière plus intuitive. La fonctionnalité **Relation plusieurs à plusieurs** fait partie des capacités plus étendues des **modèles composites** dans **Power BI Desktop**.

![plusieurs à plusieurs dans la boîte de dialogue Modifier la relation](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

La capacité **relations plusieurs à plusieurs** dans **Power BI Desktop** fait partie d’une collection de trois fonctionnalités connexes :

* **Modèles composites** : permet à un rapport d’avoir plusieurs connexions de données, y compris des connexions provenant de DirectQuery ou d’une importation, dans toutes les combinaisons.
* **Relations plusieurs-à-plusieurs** : les **modèles composites** vous permettent d’établir des **relations plusieurs-à-plusieurs** entre des tables, sans saisir obligatoirement des valeurs uniques dans les tables et en supprimant les précédentes solutions de contournement telles que la présentation de nouvelles tables uniquement pour établir des relations. 
* **Mode de stockage** : vous pouvez désormais spécifier les visuels qui nécessitent une requête pour les sources de données principales, et ceux qui n’en ont pas besoin sont importés même s’ils sont basés sur DirectQuery, ce qui améliore les performances et réduit la charge du serveur principal. Auparavant, même de simples visuels comme les segments initiés par des requêtes sont envoyés à des sources principales. 

Cette collection de trois fonctionnalités connexes pour **modèles composites** est décrite dans différents articles :

* Les **modèles composites** sont décrits en détail dans l’article [Modèles composites dans Power BI Desktop (préversion)](desktop-composite-models.md).
* Les **relations plusieurs à plusieurs** sont décrites dans cet article.
* Le **mode de stockage** est décrit dans un article dédié, [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md).

## <a name="enabling-the-many-to-many-relationships-preview-feature"></a>Activation de la préversion de la fonctionnalité de relation plusieurs à plusieurs

La fonctionnalité **Relation plusieurs à plusieurs** fait partie des capacités des **modèles composites** et est au stade de la préversion. Elle doit être activée dans **Power BI Desktop**. Pour activer les **modèles composites**, sélectionnez **Fichiers > Options et paramètres > Options > Fonctionnalités en préversion**, puis cochez la case **modèles composites**.

![activation des fonctionnalités en préversion](media/desktop-composite-models/composite-models_02.png)

Vous devrez redémarrer **Power BI Desktop** pour activer la fonctionnalité.

![redémarrage requis pour appliquer les modifications](media/desktop-composite-models/composite-models_03.png)


## <a name="what-many-to-many-relationships-solves"></a>Ce que résolvent les relations plusieurs à plusieurs

Avant que des **relations plusieurs à plusieurs** ne deviennent disponibles, lors de la définition d’une relation entre deux tables dans Power BI, au moins l’une des colonnes impliquées dans la relation devait contenir des valeurs uniques. Cependant, dans de nombreux cas, aucune colonne de la table ne contenait des valeurs uniques. 

Par exemple, deux tables peuvent avoir une colonne contenant le *pays*, mais les valeurs de *pays* n’étaient pas uniques dans les tables. Pour joindre ces tables, il fallait créer une solution de contournement, telle que l’introduction de tables supplémentaires dans le modèle contenant les valeurs uniques nécessaires. La fonctionnalité **relations plusieurs à plusieurs** fournit une autre approche, ce qui permet de joindre ces tables directement à l’aide d’une relation avec une cardinalité de **plusieurs à plusieurs**.  

## <a name="using-many-to-many-relationships"></a>Utilisation de relations plusieurs à plusieurs

Lorsque vous définissez une relation entre deux tables dans Power BI, vous devez définir la cardinalité de la relation. Par exemple, la relation entre *ProductSales* et *Produit* (à l’aide de colonnes *ProductSales [ProductCode]* et *Product[ProductCode]*) est définie comme étant **Many-1**, puisqu’il y a plusieurs ventes pour chaque produit, et la colonne dans la table *Product* *(ProductCode)* est unique. Lorsque vous définissez une cardinalité de la relation en tant que **Many-1**, **1-Many** ou **1-1**, Power BI effectue la validation pour garantir que la cardinalité sélectionnée correspond aux données réelles.

Par exemple, examinons le modèle simple dans l’image suivante.

![affichage des relations](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Imaginez ensuite que la table *Product* ne contenait que deux lignes.

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Imaginez également que la table *Sales* a seulement quatre lignes, y compris *Ventes* pour un produit **C** qui n’existe pas dans la table *Product* (en raison d’une erreur d’intégrité référentielle).

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

Un élément visuel qui affichait *ProductName* et *Price* (à partir de la table *Produit*), ainsi que le total *Qty* pour chaque produit (à partir de la table *ProductSales*) s’affiche comme le montre l’image suivante : 

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Comme vous pouvez le voir dans l’image précédente, une ligne du visuel a une valeur *ProductName* vide en liaison avec les ventes pour le produit *C*. Cette ligne vide tient compte de ce qui suit :

* Toutes les lignes de la table *ProductSales* pour lesquelles il n’y a pas de ligne correspondante dans la table *Product* : il y a un problème d’intégrité référentielle, comme nous le voyons pour le produit *C* dans cet exemple.

* Toutes les lignes de la table *ProductSales* pour lesquelles la colonne clé étrangère est Null. 

Pour ces raisons, dans les deux cas. la ligne vide tient compte des ventes où *ProductName* et *Price* sont inconnus.

Toutefois, il arrive parfois que les tables soient jointes par deux colonnes, mais qu’aucune colonne ne soit unique. Par exemple, considérez les deux tables suivantes :

* La table *Sales* contient des données de ventes par *état*, où chaque ligne contenant le montant des ventes pour le type de vente dans cet état (y compris les états de CA, de WA et du TX). 

    ![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* La table *CityData* contient des données sur les villes, y compris la population et l’état (y compris les états de CA, de WA et de New York)

    ![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Bien qu’il existe une colonne *État* dans les deux tables et qu’il soit raisonnable de créer des rapports sur le total des *ventes* par *état*, en indiquant la population totale de chaque état, il y a un problème : la colonne *État* n’est unique dans aucune des tables. 

## <a name="the-prior-workaround"></a>La solution de contournement précédente

Dans les versions de **Power BI Desktop** antérieures à la version de juillet 2018, il n’était pas possible de créer une relation directe entre ces tables. Une solution de contournement courante à ce problème consistait à effectuer les opérations suivantes :

* Créer une troisième table contenant uniquement les ID d’*états* uniques. Il pouvait s’agir d’une table calculée (définie à l’aide de DAX), ou d’une table définie à l’aide d’une requête définie dans **Éditeur de requête**, qui pouvait contenir les ID uniques provenant d’une des tables, ou de l’ensemble uni.

* Lier les deux tables d’origine vers cette nouvelle table, à l’aide de relations **Many-1* courantes.

Ce tableau de solution de contournement pouvait rester visible, ou être masqué de manière à ne pas apparaître dans la liste des champs. Dans ce cas, la relation **Many-1** était généralement définie pour filtrer dans les deux directions, de telle manière que le champ *État* d’une autre table pouvait être utilisé, avec propagation ultérieure à l’autre table par filtrage croisé. Cette approche de la solution de contournement est indiquée dans l’image suivante de l’**affichage des relations**.

![affichage des relations](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Un visuel montrant l’*état* (à partir de la table *CityData*), ainsi que la *Population* totale et les *ventes* totales ressemblerait alors à ce qui suit.

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

Notez qu’étant donné l’utilisation de l’état de la table *CityData* dans cette solution de contournement, seuls les *état*s de cette table sont répertoriés (et par conséquent, le TX est exclu). En outre, contrairement au cas des relations **Many-1**, alors que la ligne totale inclut toutes les *ventes* (y compris celles du TX), les détails n’incluent pas une ligne vide couvrant les lignes qui ne correspondent pas. Similairement, il n’y aurait pas de ligne vide couvrant des *Ventes* pour lesquelles il y avait une valeur Null pour l’*État*.

Si *Ville* était également ajoutée à ce visuel, si la population par *Ville* est connue, les *Ventes* affichées pour *Ville* seraient simplement une répétition des *Ventes* pour l’*État* correspondant (ce qui est normalement le cas lors du regroupement sur une colonne qui n’est pas liée à certaines mesures d’agrégation), comme le montre l’image suivante.

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Si la nouvelle table *Sales* était définie comme l’union de toutes les *états* dans cette solution de contournement et rendue visible dans la liste des champs, le même visuel montrant l’*état* (sur la nouvelle table) avec la *population* totale et les *ventes* totales serait le suivant.

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Dans ce cas, comme le montre le visuel, le *TX* (avec les *ventes*, mais population inconnue), et *New York* (avec la population connue, mais sans *ventes*) seraient inclus. 

Comme vous pouvez le voir, cette solution de contournement n’était pas optimale et pose plusieurs problèmes. Avec la création de la **relation plusieurs à plusieurs**, ces problèmes sont résolus, comme décrit dans la section suivante.

## <a name="using-many-to-many-relationships-instead-of-the-workaround"></a>Utilisation de relations plusieurs à plusieurs au lieu de la solution de contournement

Dans les versions de **Power BI Desktop** à compter de juillet 2018, vous pouvez associer directement ces tables décrites dans la section précédente, sans avoir à recourir à ces solutions de contournement. Il est désormais possible de définir la cardinalité d’une relation sur **Plusieurs à plusieurs**, indiquant qu’aucune table ne contient des valeurs uniques. Pour ce type de relation, vous pouvez toujours contrôler quelle table filtre vers l’autre table, ou veiller à avoir un filtrage bidirectionnel où les deux tables se filtrent mutuellement.  

> [!NOTE]
> La possibilité de créer des relations **Plusieurs à plusieurs** est en préversion et, au stade de la préversion, il n’est pas possible de publier des modèles à l’aide de relations **Plusieurs à plusieurs** pour le service Power BI. 

Dans **Power BI Desktop**, la cardinalité par défaut est **Plusieurs à plusieurs** quand il est déterminé qu’aucune table ne contient des valeurs uniques pour les colonnes de la relation. Dans ces cas-là, un avertissement s’affiche pour confirmer que le paramètre de la relation est votre comportement prévu, plutôt que l’effet non intentionnel d’un problème de données. 

Par exemple, lors de la création d’une relation directe entre *CityData* et *Sales*, où les filtres devraient aller de *CityData* à *Sales*, la boîte de dialogue des relations s’affiche comme l’illustre l’image suivante.

![Boîte de dialogue Modifier la relation](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

L’**affichage des relations** en résultant contiendrait alors la relation directe **Plusieurs à plusieurs** entre les deux tables. L’apparence dans la liste des **champs** et le comportement ultérieur suivant lors de la création de visuels sont alors identique à l’utilisation de la solution de contournement décrite dans la section précédente, où la table supplémentaire (contenant la commande distincte *états*) ne sont pas rendus visibles. Par exemple, comme dans la section précédente décrivant la solution de contournement, un élément visuel montrant les *états*, ainsi que la totalité de la population et des ventes, se présenterait comme suit.

![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Par conséquent, la principale différence entre des relations **Plusieurs à plusieurs** et les relations plus courantes **Many-1** sont les suivantes.

* Les valeurs indiquées n’incluent pas la prise en compte d’une ligne vide pour toutes les lignes qui ne correspondent pas dans l’autre table, ni pour les lignes où la colonne utilisée dans la relation dans l’autre table est Null.
* Il n’est pas possible d’utiliser la fonction *RELATED()* (car plusieurs lignes pourraient être liées).
* L’utilisation de la fonction *ALL()* sur une table ne supprimera pas de filtres appliqués à d’autres tables reliées à elle par une relation **Plusieurs à plusieurs**. Par exemple, une mesure définie comme suit dans l’exemple précédent ne supprimerait pas de filtres de colonnes de la table *CityData* reliée :

    ![exemple de script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    De ce fait, un visuel montrant l’*état*, les *ventes*, et le *total des ventes* ressemblerait à ce qui suit :

    ![visuel de table](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Pour cette raison, il faut veiller à ce que des calculs avec *TOUT(\<Table>)*, tels que *% du total* retournent les résultats prévus. 


## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations pour cette version de **relations plusieurs à plusieurs** et de **modèles composites**.

Les sources multidimensionnelles suivantes ne peuvent pas être utilisées avec des **modèles composites** :

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Jeux de données Power BI

Lors de la connexion à ces sources multidimensionnelles à l’aide de DirectQuery, vous ne pouvez pas non plus vous connecter à une autre source DirectQuery ni combiner les données avec des données importées.

Les limitations existantes concernant l’utilisation de DirectQuery s’appliquent lorsque vous utilisez des **relations plusieurs à plusieurs**. Plusieurs de ces limitations sont désormais appliquées par table, selon le **mode de stockage** de la table. Par exemple, une colonne calculée d’une table importée peut référencer d’autres tables, mais une colonne calculée d’une table DirectQuery est toujours limitée pour référencer uniquement des colonnes de la même table. D’autres limitations s’appliquent au modèle dans son ensemble, si aucune des tables du modèle n’est de type DirectQuery. Par exemple, les fonctionnalités **QuickInsights** et **Q&A** ne sont pas disponibles sur un modèle si une des tables qu’il contient possède un **mode de stockage** de type DirectQuery. 

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants décrivent en détail les modèles composites ainsi que le mode DirectQuery.

* [Modèles composites dans Power BI Desktop (préversion)](desktop-composite-models.md)
* [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md)

Articles DirectQuery :

* [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI](desktop-directquery-data-sources.md)

