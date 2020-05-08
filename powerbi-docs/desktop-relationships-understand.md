---
title: Relations de modèle dans Power BI Desktop
description: Introduction à la théorie des relations de modèle dans Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 991f8b47337ba563ecfd223d69d687269a44ed78
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79041605"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Relations de modèle dans Power BI Desktop

Cet article s’adresse principalement aux modélisateurs de données d’importation qui utilisent Power BI Desktop. Il s’agit d’une rubrique essentielle pour qui souhaite concevoir des modèles intuitifs, précis et optimisés.

Pour en savoir plus sur la conception de modèles optimisés, notamment sur les relations et les rôles de table, consultez l’article [Découvrez le schéma en étoile et son importance pour Power BI](guidance/star-schema.md).

## <a name="relationship-purpose"></a>Finalité des relations

Pour simplifier, les relations Power BI propagent les filtres appliqués aux colonnes de tables de modèle à d’autres tables de modèle. La propagation des filtres se poursuit tant qu’il y a un chemin de relation à suivre et peut viser plusieurs tables.

Les chemins de relation sont déterministes, ce qui signifie que les filtres sont toujours propagés de la même façon et sans variation aléatoire. Cependant, les relations peuvent être désactivées ou le contexte de filtre peut être modifié par les calculs de modèle qui utilisent des fonctions DAX particulières. Pour plus d’informations, consultez la rubrique [Fonctions DAX à prendre en considération](#relevant-dax-functions) plus loin dans cet article.

> [!IMPORTANT]
> Il est important de comprendre que les relations de modèle n’appliquent pas l’intégrité des données. Pour plus d’informations, consultez la rubrique [Évaluation des relations](#relationship-evaluation) plus loin dans cet article. Cette rubrique explique comment les relations de modèle se comportent quand vos données ont des problèmes d’intégrité.

Voyons comment les relations propagent les filtres à travers un exemple animé.

![Exemple animé de propagation de filtres de relation](media/desktop-relationships-understand/animation-filter-propagation.gif)

Dans cet exemple, le modèle se compose de quatre tables : **Category**, **Product**, **Year** et **Sales**. La table **Category** est associée à la table **Product**, et la table **Product** est associée à la table **Sales**. La table **Year** est également associée à la table **Sales**. Toutes les relations sont de type un-à-plusieurs (vous trouverez des détails à ce sujet plus loin dans cet article).

Une requête, peut-être générée par un visuel de carte Power BI, demande les quantités totales vendues pour les commandes passées dans une catégorie unique, **Cat-A**, et pour une même année, **2018**. C’est pourquoi des filtres sont appliqués au niveau des tables **Catégorie** et **Année**. Le filtre au niveau de la table **Category** se propage à la table **Product** pour isoler deux produits relevant de la catégorie **Cat-A**. Les filtres de la table **Product** sont ensuite propagés à la table **Sales** pour isoler seulement deux lignes de ventes de ces produits. Ces deux lignes de ventes représentent les ventes de produits relevant de la catégorie **Cat-A**. Leur quantité totale est de 14 unités. Dans le même temps, le filtre de la table **Year** est propagé pour filtrer un peu plus la table **Sales**, ce qui donne une seule ligne de vente pour les produits relevant de la catégorie **Cat-A** et qui ont été commandés au cours de l’année **CY2018**. La quantité retournée par la requête est de 11 unités. Il est à noter que lorsque plusieurs filtres sont appliqués à une table (comme la table **Sales** de cet exemple), il s’agit toujours d’une opération AND, qui exige que toutes les conditions soient remplies.

### <a name="disconnected-tables"></a>Tables déconnectées

Il est rare qu’une table de modèle ne soit pas associée à une autre table de modèle. Dans une conception de modèle valide, une telle table peut être décrite comme étant une _table déconnectée_. Une table déconnectée n’est pas destinée à propager des filtres à d’autres tables de modèle. Elle sert à recueillir des « entrées utilisateur » (peut-être avec un visuel de segment), ce qui permet aux calculs de modèle d’utiliser les valeurs d’entrée de façon utile. Prenons l’exemple d’une table déconnectée qui est chargée avec une plage de valeurs de taux de change monétaires. Tant qu’un filtre est appliqué pour filtrer en fonction d’une valeur de taux unique, la valeur peut être utilisée par une expression de mesure de façon à convertir les valeurs de ventes.

Le paramètre de scénario (« what-if ») Power BI Desktop est la fonctionnalité qui crée une table déconnectée. Pour plus d’informations, consultez l’article [Créer et utiliser un paramètre de scénario pour visualiser des variables dans Power BI Desktop](desktop-what-if.md).

## <a name="relationship-properties"></a>Propriétés de relation

Une relation de modèle associe une colonne d’une table à une colonne d’une autre table. (Il existe un cas particulier où cette condition n’est pas vraie, et cela s’applique uniquement aux relations multicolonnes dans les modèles DirectQuery. Pour plus d’informations, consultez l’article sur la fonction DAX [COMBINEVALUES](/dax/combinevalues-function-dax).)

> [!NOTE]
> Il n’est pas possible d’associer une colonne à une autre colonne _d’une même table_. Il ne faut pas confondre cela avec la possibilité de définir une contrainte de clé étrangère de base de données relationnelle qui faire elle-même référence à une table. Ce concept de base de données relationnelle peut être utile pour stocker des relations parent-enfant (par exemple, chaque enregistrement d’employé est associé à un supérieur hiérarchique). La génération d’une hiérarchie de modèle basée sur ce type de relation ne peut pas être résolue en créant des relations de modèle. Pour savoir comment y parvenir, consultez l’article [Fonctions parent et enfant](/dax/parent-and-child-functions-dax).

### <a name="cardinality"></a>Cardinalité

Chaque relation de modèle doit être définie avec un type de cardinalité. Il existe quatre types de cardinalité différents qui représentent les caractéristiques des données des colonnes de départ et d’arrivée. Le côté « un » signifie que la colonne contient des valeurs uniques ; le côté « deux » signifie que la colonne peut contenir des valeurs en double.

> [!NOTE]
> Si une opération d’actualisation de données tente de charger des valeurs en double dans une colonne du côté « un », l’actualisation des données échoue entièrement.

Les quatre types (et leurs notations raccourcies) sont décrits dans la liste à puces suivante :

- Un-à-plusieurs (\*:1)
- Plusieurs-à-un (\*:1)
- Un-à-un (1:1)
- Plusieurs-à-plusieurs (\*:\*)

Quand vous créez une relation dans Power BI Desktop, le concepteur détecte et définit automatiquement le type de cardinalité. Il interroge le modèle de façon à identifier les colonnes qui contiennent des valeurs uniques. Pour les modèles Importer, il utilise des statistiques de stockage internes ; pour les modèles DirectQuery, il envoie des requêtes de profilage à la source de données. Or, il arrive parfois qu’il commette des erreurs. C’est dû au fait que les données n’ont pas encore été chargées dans les tables, ou que les colonnes censées contenir des valeurs en double contiennent en fait des valeurs uniques. Dans les deux cas, vous pouvez mettre à jour le type de cardinalité tant que des colonnes du côté « un » contiennent des valeurs uniques (ou que des lignes de données doivent encore être chargées dans la table).

Les types de cardinalité **Un-à-plusieurs** et **Plusieurs-à-un** sont pour ainsi dire identiques, et ce sont aussi les plus courants.

Au moment de configurer une relation Un-à-plusieurs ou Plusieurs-à-un, vous devez choisir celui qui correspond à l’ordre dans lequel vous avez associé les colonnes. Réfléchissez à la façon dont vous configureriez la relation entre la table **Product** et la table **Sales** à partir de la colonne **ProductID** commune à chaque table. Le type de cardinalité serait _Un-à-plusieurs_, car la colonne **ProductID** de la table **Product** contient des valeurs uniques. Si les tables étaient associées dans le sens inverse, de **Sales** à **Product**, la cardinalité serait _Plusieurs-à-un_.

Une relation **Un-à-un** indique que les deux colonnes contiennent des valeurs uniques. Ce type de cardinalité n’est pas courant et ne correspond sûrement pas à une conception de modèle optimale du fait du stockage de données redondantes. Pour plus d’informations sur l’utilisation de ce type de cardinalité, consultez [Aide sur les relations un-à-un](guidance/relationships-one-to-one.md).

Une relation **Plusieurs-à-plusieurs** signifie que les deux colonnes peuvent contenir des valeurs en double. Ce type de cardinalité n’est pas souvent employé. Il est généralement utile pour concevoir des modèles complexes. Pour obtenir des conseils sur l’utilisation de ce type de cardinalité, lisez les [conseils au sujet des relations Plusieurs-à-plusieurs](guidance/relationships-many-to-many.md).

> [!NOTE]
> Le type de cardinalité Plusieurs-à-plusieurs n’est actuellement pas pris en charge pour les modèles développés pour Power BI Report Server.

> [!TIP]
> Dans la vue de modèle Power BI Desktop, vous pouvez interpréter le type de cardinalité d’une relation en fonction des indicateurs (1 ou \*) présents de chaque côté de la ligne de la relation. Pour identifier les colonnes qui sont associées, sélectionnez ou placez le curseur sur la ligne de la relation de façon à mettre les colonnes en surbrillance.

### <a name="cross-filter-direction"></a>Direction du filtrage croisé

Chaque relation de modèle doit être définie avec une direction de filtrage croisé. Votre sélection détermine la ou les directions dans lesquelles les filtres vont se propager. Les options de filtrage croisé possibles dépendent du type de cardinalité.

| Type de cardinalité | Options de filtrage croisé |
| --- | --- |
| Un-à-plusieurs (ou Plusieurs-à-un) | Unique<br>Les deux |
| Un-à-un | Les deux |
| Plusieurs-à-plusieurs | Unique (Table1 à Table2)<br>Unique (Table2 à Table1)<br>Les deux |

La direction de filtrage croisé _Unique_ indique « une seule direction », tandis que _Les deux_ indique « deux directions ». Une relation qui filtre dans les deux directions est généralement dite _bidirectionnelle_.

Pour les relations Un-à-plusieurs, la direction du filtrage croisé est toujours du côté « un » et éventuellement du côté « plusieurs » (bidirectionnelle). Pour les relations Un-à-un, la direction du filtrage croisé part toujours des deux tables. Enfin, pour les relations Plusieurs-à-plusieurs, la direction du filtrage croisé peut démarrer de l’une ou l’autre des tables ou des deux. Notez que lorsque le type de cardinalité comporte un côté « un », les filtres se propagent toujours de ce côté-là.

Lorsque la direction du filtrage croisé est définie sur **Les deux**, une propriété supplémentaire est disponible. Elle peut appliquer le filtrage bidirectionnel lorsque les règles de sécurité au niveau des lignes (RLS) sont appliquées. Pour plus d’informations sur RLS, consultez l’article [Sécurité au niveau des lignes (RLS) avec Power BI Desktop](desktop-rls.md).

La modification de la direction du filtrage croisé des relations, notamment la désactivation de la propagation de filtre, peut être aussi être effectuée par un calcul de modèle. Pour ce faire, il convient d’utiliser la fonction DAX [CROSSFILTER](/dax/crossfilter-function).

Les relations bidirectionnelles peuvent avoir un impact négatif sur les performances. De plus, toute tentative de configuration d’une relation bidirectionnelle peut engendrer des chemins de propagation de filtre ambigus. Dans ce cas, il se peut que Power BI Desktop ne puisse pas valider la modification de la relation et vous alerte avec un message d’erreur. Pourtant, il peut parfois arriver que Power BI Desktop vous autorise à définir des chemins de relation ambigus entre des tables. Les règles de précédence qui affectent la détection des ambiguïtés et la résolution des chemins sont décrites plus loin dans cet article dans la rubrique [Règles de précédence](#precedence-rules).

L’utilisation du filtrage bidirectionnel n’est recommandée qu’en cas de nécessité. Pour plus d’informations, consultez [Guide des relations bidirectionnelles](guidance/relationships-bidirectional-filtering.md).

> [!TIP]
> Dans la vue de modèle Power BI Desktop, vous pouvez interpréter la direction du filtrage croisé d’une relation à partir des flèches située le long de la ligne de la relation. La présence d’une flèche simple indique un filtre à direction unique dans le sens de la flèche ; une flèche double indique une relation bidirectionnelle.

### <a name="make-this-relationship-active"></a>Rendre cette relation active

Seul un chemin de propagation de filtre peut être actif entre deux tables de modèle. Il est toutefois possible d’introduire des chemins de relation supplémentaires, mais ces relations doivent toutes être configurées comme étant _inactives_. Les relations inactives ne peuvent être rendues actives qu’à l’occasion de l’évaluation du calcul d’un modèle. Pour ce faire, il convient d’utiliser la fonction DAX [USERELATIONSHIP](/dax/userelationship-function-dax).

Pour plus d’informations, consultez [Guide des relations actives et inactives](guidance/relationships-active-inactive.md).

> [!TIP]
> Dans la vue de modèle Power BI Desktop, vous pouvez interpréter l’état actif ou inactif d’une relation. Une relation active est représentée par une ligne pleine ; une relation inactive est représentée par une ligne en pointillés.

### <a name="assume-referential-integrity"></a>Supposer une intégrité référentielle

La propriété _Intégrité référentielle supposée_ est disponible uniquement pour les relations Un-à-plusieurs et Un-à-un entre deux tables en mode de stockage DirectQuery basées sur la même source de données. Quand elle est activée, les requêtes natives envoyées à la source de données joignent les deux tables en utilisant une jointure interne et non une jointure externe. En règle générale, l’activation de cette propriété a pour effet d’améliorer les performances des requêtes, même si celles-ci dépendent des spécificités de la source de données.

Activez toujours cette propriété quand il y a une contrainte de clé étrangère de base de données entre les deux tables. S’il n’y a pas de contrainte de clé étrangère, vous pouvez quand même activer la propriété tant que vous êtes certain de l’intégrité des données.

> [!IMPORTANT]
> Si l’intégrité des données vient à être compromise, la jointure interne éliminera les lignes sans correspondance entre les tables. Par exemple, si une table de modèle **Sales** dont la colonne **ProductID** contient une valeur qui n’existe pas dans la table **Product** associée, la propagation de filtre de la table **Product** vers la table **Sales** élimine les lignes de ventes de produits inconnus et les résultats de ventes s’en trouvent sous-estimés.
>
> Pour plus d’informations, consultez l’article [Paramètres Intégrité référentielle supposée dans Power BI Desktop](desktop-assume-referential-integrity.md).

## <a name="relevant-dax-functions"></a>Fonctions DAX à prendre en considération

Plusieurs fonctions DAX présentent un intérêt pour les relations de modèle. Chaque fonction est décrite brièvement dans la liste à puces suivante :

- [RELATED](/dax/related-function-dax) : récupère la valeur du côté « un ».
- [RELATEDTABLE](/dax/relatedtable-function-dax) : récupère une table de lignes du côté « plusieurs ».
- [USERELATIONSHIP](/dax/userelationship-function-dax) : force l’utilisation d’une relation de modèle inactive spécifique.
- [CROSSFILTER](/dax/crossfilter-function) : modifie la direction du filtrage croisé de la relation (à une ou les deux) ou désactive la propagation de filtre (aucune).
- [COMBINEVALUES](/dax/combinevalues-function-dax) : joint deux chaînes de texte ou plus en une seule. L’objectif de cette fonction est de prendre en charge les relations multicolonnes dans les modèles DirectQuery.
- [TREATAS](/dax/treatas-function) : applique le résultat d’une expression de table comme filtres aux colonnes d’une table non associée.
- [Fonctions parent et enfant](/dax/parent-and-child-functions-dax) : famille de fonctions associées qui permettent de générer des colonnes calculées pour établir une hiérarchie parent-enfant. Ces colonnes peuvent ensuite être utilisées pour créer une hiérarchie de niveau fixe.

## <a name="relationship-evaluation"></a>Évaluation des relations

Du point de vue de l’évaluation, les relations de modèle peuvent être considérées comme _fortes_ ou _faibles_. Il ne s’agit pas d’une propriété de relation configurable. De fait, elle est déduite du type de cardinalité et de la source de données des deux tables associées. Il est important de comprendre le type d’évaluation, car cela peut avoir des implications en termes de performances ou des conséquences en cas de compromission de l’intégrité des données. Ces implications et les conséquences de l’intégrité sont décrites dans cette rubrique.

Tout d’abord, une théorie de modélisation est nécessaire pour comprendre parfaitement les évaluations des relations.

Un modèle Importer ou DirectQuery obtient toutes ses données du cache Vertipaq ou de la base de données source. Dans les deux cas, Power BI peut déterminer qu’il existe un côté « un » dans une relation.

En revanche, un modèle Composite peut comprendre des tables qui utilisent différents modes de stockage (Importer, DirectQuery ou Double) ou plusieurs sources DirectQuery. Chaque source, dont le cache Vertipaq de données d’importation, est considérée comme un _îlot de données_. Les relations de modèle peuvent ensuite être classifiées comme étant _intra-îlot_ ou _inter-îlots_. Une relation intra-îlot établit un lien entre deux tables au sein d’un même îlot de données, alors qu’une relation inter-îlots établit un lien entre des tables issues de différents îlots de données. Notez que les relations dans les modèles Importer ou DirectQuery sont toujours de type intra-îlots.

Penchons-nous sur un exemple de modèle Composite.

![Exemple de modèle Composite constitué de deux îlots](media/desktop-relationships-understand/data-island-example.png)

Dans cet exemple, le modèle Composite se compose de deux îlots : un îlot de données Vertipaq et un îlot de données sources DirectQuery. L’îlot de données Vertipaq contient trois tables, tandis que l’îlot de données sources DirectQuery en contient deux. Il existe une relation inter-îlots pour associer une table de l’îlot de données Vertipaq à une table de l’îlot de données sources DirectQuery.

### <a name="strong-relationships"></a>Relations fortes

Une relation de modèle est dite _forte_ quand le moteur de requête peut déterminer le côté « un » d’une relation. Il a la confirmation que la colonne du côté « un » contient des valeurs uniques. Toutes les relations intra-îlots Un-à-plusieurs sont des relations fortes.

Dans l’exemple suivant, il existe deux relations fortes, toutes deux représentées par la lettre **S**. Les relations incluent la relation Un-à-plusieurs contenue dans l’îlot Vertipaq et la relation Un-à-plusieurs contenue dans la source DirectQuery.

![Exemple de modèle Composite constitué de deux îlots avec indication de relations fortes](media/desktop-relationships-understand/data-island-example-strong.png)

Pour les modèles Importer, où toutes les données sont stockées dans le cache Vertipaq, une structure de données est créée pour chaque relation forte au moment où les données sont actualisées. Les structures de données sont constituées de mappages indexés de toutes les valeurs de colonne à colonne, et leur objectif est d’accélérer la jointure des tables au moment de la requête.

Au moment de la requête, les relations fortes autorisent une _extension de table_. L’extension de table entraîne la création d’une table virtuelle en incluant les colonnes natives de la table de base, puis en les développant dans les tables associées. Pour les tables d’importation, cette opération s’effectue dans le moteur de requête ; dans le cas des tables DirectQuery, cette opération s’effectue dans la requête native envoyée à la base de données source (tant que la propriété **Intégrité référentielle supposée** n’est pas activée). Le moteur de requête agit ensuite sur la table étendue, en appliquant les filtres et en effectuant un regroupement en fonction des valeurs contenues dans les colonnes de la table étendue.

> [!NOTE]
> Les relations inactives sont aussi étendues, même quand la relation n’est pas utilisée par un calcul. Les relations bidirectionnelles n’ont aucun impact sur l’extension de table.

Pour les relations Un-à-plusieurs, l’extension de table se produit du côté « plusieurs » vers le côté « un » en utilisant la sémantique de JOINTURE EXTERNE GAUCHE. Quand il n’existe pas de correspondance de valeur entre le côté « plusieurs » et le côté « un », une ligne virtuelle vide est ajoutée à la table du côté « un ».

Si l’extension de table concerne aussi les relations intra-îlots Un-à-un, elle utilise la sémantique de jointure externe entière. Cela garantit que des lignes virtuelles vides sont ajoutées de chaque côté, si nécessaire.

Les lignes virtuelles vides sont en fait des _membres inconnus_. Les membres inconnus représentent des violations d’intégrité référentielle où la valeur du côté « plusieurs » n’a pas de valeur correspondante du côté « un ». Dans l’idéal, ces lignes vides ne devraient pas exister et peuvent être éliminés par le nettoyage ou la réparation des données sources.

Voyons comment l’extension de table fonctionne à travers un exemple animé.

![Exemple animé d’extension de table](media/desktop-relationships-understand/animation-expanded-table.gif)

Dans cet exemple, le modèle se compose de trois tables : **Category**, **Product** et **Sales**. La table **Category** est liée à la table **Product** par une relation Un-à-plusieurs, et la table **Product** est liée à la table **Sales** par une relation Un-à-plusieurs. La table **Category** contient deux lignes, la table **Product** en contient trois et la table **Sales** en contient cinq. Il existe des correspondances de valeurs des deux côtés des relations, ce qui signifie qu’il n’existe pas de violations d’intégrité référentielle. Une table étendue s’affiche au moment de la requête. La table est constituée des colonnes des trois tables. Il s’agit en fait d’une perspective dénormalisée des données contenues dans les trois tables. Une nouvelle ligne est ajoutée à la table **Sales** et sa valeur d’identificateur de production (9) n’a pas de correspondance dans la table **Product**. Il s’agit d’une violation d’intégrité référentielle. Dans la table étendue, la nouvelle ligne contient des valeurs (vides) pour les colonnes des tables **Category** et **Product**.

### <a name="weak-relationships"></a>Relations faibles

Une relation de modèle est dite _faible_ quand le côté « un » n’est pas garanti. Deux raisons peuvent expliquer cela :

- La relation utilise un type de cardinalité Plusieurs-à-plusieurs (même si une colonne ou les deux contiennent des valeurs uniques)
- La relation est de type inter-îlot (ce qui ne peut être le cas que des modèles Composite)

Dans l’exemple suivant, il existe deux relations faibles, toutes deux représentées par la lettre **W**. Les deux relations incluent la relation Plusieurs-à-plusieurs contenue dans l’îlot Vertipaq et la relation inter-ilôts Un-à-plusieurs.

![Exemple de modèle Composite constitué de deux îlots avec indication de relations faibles](media/desktop-relationships-understand/data-island-example-weak.png)

Pour les modèles Importer, les relations faibles ne font jamais l’objet d’une création de structure de données. Cela signifie que les jointures de table doivent être résolues au moment de la requête.

Les relations faibles ne font jamais l’objet d’une extension de table. Les jointures de tables sont effectuées en utilisant la sémantique de jointure interne. C’est pour cette raison qu’il n’y a pas d’ajout de lignes virtuelles vides pour compenser les violations d’intégrité référentielle.

Les relations faibles s’accompagnent d’autres restrictions :

- La fonction DAX RELATED ne peut pas être utilisée pour récupérer les valeurs de colonne du côté « un »
- L’application de la sécurité au niveau des lignes est soumise à des restrictions de topologie

> [!NOTE]
> Dans la vue de modèle Power BI Desktop, il n’est pas toujours possible de déterminer si une relation de modèle est forte ou faible. Une relation Plusieurs-à-plusieurs est toujours faible, ce qui est aussi le cas d’une relation Un-à-plusieurs de type inter-îlots. Pour déterminer s’il s’agit d’une relation inter-îlots, vous devez inspecter les modes de stockage de table et les sources de données.

### <a name="precedence-rules"></a>Règles de précédence

Les relations bidirectionnelles peuvent introduire plusieurs chemins de propagation de filtre entre les tables de modèle (et donc des ambiguïtés). La liste suivante présente les règles de précédence que Power BI utilise pour la détection des ambiguïtés et la résolution des chemins :

1. Relations Plusieurs-à-un et Un-à-un, ce qui inclut les relations faibles
2. Relations Plusieurs-à-plusieurs
3. Relations bidirectionnelles, dans le sens inverse (c’est-à-dire, à partir du côté « Plusieurs »)

### <a name="performance-preference"></a>Préférences en matière de performances

La liste suivante classe les performances de propagation de filtre, des plus rapides aux plus lentes :

1. Relations intra-îlots Un-à-plusieurs
2. Relations de cardinalité Plusieurs-à-plusieurs
3. Relations de modèle Plusieurs-à-plusieurs avec une table intermédiaire et impliquant au moins une relation bidirectionnelle
4. Relations inter-ilôts

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Comprendre le schéma en étoile et son importance pour Power BI](guidance/star-schema.md)
- [Aide pour la relation un-à-un](guidance/relationships-one-to-one.md)
- [Conseils sur les relations Plusieurs-à-plusieurs](guidance/relationships-many-to-many.md)
- [Aide pour les relations actives et inactives](guidance/relationships-active-inactive.md)
- [Aide pour les relations bidirectionnelles](guidance/relationships-bidirectional-filtering.md)
- [Aide à la résolution des problèmes de relations](guidance/relationships-troubleshoot.md)
- Vidéo : [Les comportements appropriés et déconseillés concernant les relations Power BI](https://www.youtube.com/watch?v=78d6mwR8GtA)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
