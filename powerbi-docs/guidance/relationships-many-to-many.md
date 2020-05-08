---
title: Conseils sur les relations plusieurs-à-plusieurs
description: Conseils relatifs au développement de relations de modèle plusieurs à plusieurs.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 937f8ca693113cf85d265420da44f7c9f8b68f5f
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260444"
---
# <a name="many-to-many-relationship-guidance"></a>Conseils sur les relations plusieurs-à-plusieurs

Cet article s’adresse principalement aux modélisateurs de données qui utilisent Power BI Desktop. Il décrit trois scénarios de modélisation plusieurs à plusieurs différents. Il vous fournit également des conseils sur la façon de les concevoir correctement dans vos modèles.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

Il existe, en fait, trois scénarios plusieurs à plusieurs. Ils peuvent se dérouler quand vous devez :

- [Associer deux tables de type dimension](#relate-many-to-many-dimensions)
- [Associer deux tables de type fait](#relate-many-to-many-facts)
- [Associer des tables de type fait de niveau plus général](#relate-higher-grain-facts), quand la table de type fait stocke des lignes à un niveau plus général que les lignes de la table de type dimension

## <a name="relate-many-to-many-dimensions"></a>Associer des dimensions plusieurs à plusieurs

Examinons le premier type de scénario plusieurs à plusieurs avec un exemple. Le scénario classique associe deux entités : les clients d’une banque et les comptes bancaires. Considérez que les clients peuvent avoir plusieurs comptes, et que les comptes peuvent appartenir à plusieurs clients. Lorsqu’un compte appartient à plusieurs clients, ceux-ci sont communément appelés _cotitulaires du compte_.

La modélisation de ces entités est simple. Une table de type dimension stocke les comptes, et une autre table de type dimension stocke les clients. Particularité des tables de type dimension, il existe une colonne ID dans chaque table. Pour modéliser la relation entre les deux tables, une troisième table est requise. Cette table est généralement appelée _table de pontage_. Dans cet exemple, son objectif est de stocker une ligne pour chaque association client/compte. Il est intéressant de noter que, quand cette table contient uniquement des colonnes ID, elle est appelée [_table de faits sans faits_](star-schema.md#factless-fact-tables).

Voici un diagramme de modèle simpliste des trois tables.

![Un diagramme de modèle contient trois tables. La conception est décrite dans le paragraphe suivant.](media/relationships-many-to-many/bank-account-customer-model-example.png)

La première table est nommée **Account** et contient deux colonnes : **AccountID** et **Account**. La deuxième table est nommée **AccountCustomer** et contient deux colonnes : **AccountID** et **CustomerID**. La troisième table est nommée **Customer** et contient deux colonnes : **CustomerID** et **Customer**. Il n’existe aucune relation entre les tables.

Deux relations de type un à plusieurs sont ajoutées pour associer les tables. Voici un diagramme de modèle des tables associées mis à jour. Une table de type fait nommée **Transaction** a été ajoutée. Elle enregistre les transactions de compte. La table de pontage et toutes les colonnes ID ont été masquées.

![Le diagramme de modèle contient maintenant quatre tables. Des relations de type un à plusieurs ont été ajoutées pour associer toutes les tables.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

Pour mieux décrire le fonctionnement de la propagation de filtres de relation, le diagramme de modèle a été modifié afin d’afficher les lignes de la table.

> [!NOTE]
> Il n’est pas possible d’afficher les lignes de la table dans le diagramme de modèle Power BI Desktop. Cette opération est effectuée dans cet article pour étayer la discussion avec des exemples clairs.

![Le diagramme de modèle affiche désormais les lignes de la table. Les détails des lignes sont décrits dans le paragraphe suivant.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

Les détails des lignes pour les quatre tables sont décrits dans la liste à puces suivante :

- La table **Account** comporte deux lignes :
  - **AccountID** 1 correspond à Account-01
  - **AccountID** 2 correspond à Account-02
- La table **Customer** comporte deux lignes :
  - **CustomerID** 91 correspond à Customer-91
  - **CustomerID** 92 correspond à Customer-92
- La table **AccountCustomer** comporte trois lignes :
  - **AccountID** 1 est associée à **CustomerID** 91
  - **AccountID** 1 est associée à **CustomerID** 92
  - **AccountID** 2 est associée à **CustomerID** 92
- La table **Transaction** comporte trois lignes :
  - **Date** 1er janvier 2019, **AccountID** 1, **Amount** 100
  - **Date** 2 février 2019, **AccountID** 2, **Amount** 200
  - **Date** 3 mars 2019, **AccountID** 1, **Amount** -25

Voyons ce qui se passe lorsque le modèle est interrogé.

Vous trouverez ci-dessous deux visuels qui récapitulent la colonne **Amount** à partir de la table **Transaction**. Le premier visuel effectuant un regroupement par compte, la somme des colonnes **Amount** représente le _solde du compte_. Le second visuel effectuant un regroupement par client, la somme des colonnes **Amount** représente le _solde du client_.

![Deux visuels de rapport sont placés côte à côte. Les visuels sont décrits dans le paragraphe suivant.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

Le premier visuel est intitulé **Solde du compte** et il comporte deux colonnes : **Account** et **Amount**. Il affiche le résultat suivant :

- Le montant du solde pour Account-01 est égal à 75
- Le montant du solde pour Account-02 est égal à 200
- Le total est égal à 275

Le second visuel est intitulé **Solde du client** et il comporte deux colonnes : **Customer** et **Amount**. Il affiche le résultat suivant :

- Le montant du solde pour Customer-91 est égal à 275
- Le montant du solde pour Customer-92 est égal à 275
- Le total est égal à 275

Un coup d’œil rapide aux lignes de la table et au visuel **Solde du compte** montre que le résultat est correct, pour chaque compte et le montant total. Cela est dû au fait que chaque regroupement de comptes entraîne une propagation de filtres vers la table **Transaction** pour ce compte.

Toutefois, un problème semble se poser avec le visuel **Solde du client**. Chaque client du visuel **Solde du client** présente le même solde que le solde total. Ce résultat pourrait être correct uniquement si chaque client était un cotitulaire de chaque compte. Ce n’est pas le cas dans cet exemple. Le problème est lié à la propagation de filtres. Elle ne s’étend pas entièrement jusqu’à la table **Transaction**.

Suivez les directions du filtre de relation de la table **Customer** jusqu’à la table **Transaction**. Il doit être évident que la relation entre les tables **Account** et **AccountCustomer** est propagée dans la mauvaise direction. La direction du filtre pour cette relation doit être définie sur **À double sens**.

![Le diagramme de modèle a été mis à jour. Une seule modification a été apportée à la relation entre les tables Account et AccountCustomer. Elle filtre maintenant dans les deux directions.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Les deux mêmes visuels de rapport sont placés côte à côte. Le premier visuel n’a pas changé. Le second visuel affiche un résultat différent et il est décrit dans les paragraphes suivants.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Comme prévu, aucune modification n’a été apportée au visuel **Solde du compte**.

Toutefois, le visuel **Solde du client** affiche maintenant le résultat suivant :

- Le montant du solde pour Customer-91 est égal à 75
- Le montant du solde pour Customer-92 est égal à 275
- Le total est égal à 275

Le visuel **Solde du client** affiche maintenant un résultat correct. Suivez les directions du filtre de votre côté et découvrez comment les soldes des clients ont été calculés. En outre, sachez que la valeur totale affichée englobe _tous les clients_.

Une personne qui ne connaît pas les relations de modèle peut conclure que le résultat est incorrect. Elle pourrait demander : _Pourquoi le solde total de **Customer-91** et **Customer-92** n’est-il pas égal à 350 (75 + 275) ?_

La réponse à la question réside dans la compréhension de la relation plusieurs à plusieurs. Chaque solde de client peut représenter l’ajout de plusieurs soldes de comptes, de sorte que les soldes des clients sont _non additifs_.

### <a name="relate-many-to-many-dimensions-guidance"></a>Conseils sur l’association des dimensions plusieurs à plusieurs

Lorsque vous avez une relation plusieurs à plusieurs entre des tables de type dimension, nous donnons les conseils suivants :

- Ajoutez chaque entité avec une relation plusieurs à plusieurs en tant que table de modèle, en veillant à ce qu’elle possède une colonne d’identificateur unique (ID).
- Ajoutez une table de pontage pour stocker les entités associées
- Créez des relations de type un à plusieurs entre les trois tables
- Configurez **une** relation bidirectionnelle pour permettre à la propagation de filtres de continuer jusqu’aux tables de type fait
- Lorsqu’il n’est pas approprié d’avoir des valeurs ID manquantes, affectez la valeur FALSE à la propriété **Est nullable** des colonnes ID : l’actualisation des données échoue si des valeurs manquantes sont provisionnées
- Masquez la table de pontage (à moins qu’elle ne contienne des colonnes ou des mesures supplémentaires requises pour la création de rapports)
- Masquez les colonnes ID qui ne conviennent pas pour la création de rapports (par exemple, lorsque les ID sont des clés de substitution)
- S’il est judicieux de conserver une colonne ID visible, vérifiez qu’elle se trouve sur le côté « un » de la relation, et masquez toujours la colonne côté « plusieurs ». Il en résulte des performances de filtre optimales.
- Pour éviter toute confusion ou mauvaise interprétation, communiquez les explications aux utilisateurs de votre rapport : vous pouvez ajouter des descriptions avec des zones de texte ou des [info-bulles d’en-tête de visuel](report-page-tooltips.md)

Nous vous déconseillons d’associer directement les tables de type dimension plusieurs à plusieurs. Cette approche de conception nécessite la configuration d’une relation avec une cardinalité plusieurs à plusieurs. Conceptuellement, cela peut être obtenu, mais implique que les colonnes associées contiendront des valeurs en double. Le fait que les tables de type dimension aient une colonne ID constitue toutefois une pratique de conception bien acceptée. Les tables de type dimension doivent toujours utiliser la colonne ID comme le côté « un » d’une relation.

## <a name="relate-many-to-many-facts"></a>Associer des faits plusieurs à plusieurs

Le deuxième type de scénario plusieurs à plusieurs implique l’association de deux tables de type fait. Deux tables de type fait peuvent être associées directement. Cette technique de conception peut être utile pour une exploration de données rapide et simple. Toutefois, et pour être clairs, nous ne recommandons généralement pas cette approche de conception. Nous expliquerons pourquoi plus loin dans cette section.

Prenons un exemple qui implique deux tables de type fait : **Order** et **Fulfillment**. La table **Order** contient une ligne par ligne de commande et la table **Fulfillment** peut contenir zéro ou plusieurs lignes par ligne de commande. Les lignes de la table **Order** représentent les commandes client. Les lignes de la table **Fulfillment** représentent les articles commandés qui ont été expédiés. Une relation plusieurs à plusieurs associe les deux colonnes **OrderID**, avec la propagation de filtres uniquement à partir de la table **Order** (**Order** filtre **Fulfillment**).

![Un diagramme de modèle contient deux tables : Order et Fulfillment. Une relation plusieurs à plusieurs associe les deux colonnes OrderID, Order filtrant Fulfillment.](media/relationships-many-to-many/order-fulfillment-model-example.png)

La cardinalité de relation est définie sur plusieurs à plusieurs pour prendre en charge le stockage des valeurs **OrderID** en double dans les deux tables. Dans la table **Order**, il peut exister des valeurs **OrderID** en double, car une commande peut avoir plusieurs lignes. Dans la table **Fulfillment**, il peut exister des valeurs **OrderID** en double, car les commandes peuvent avoir plusieurs lignes et les lignes de commande peuvent être remplies par de nombreuses expéditions.

Examinons maintenant les lignes de la table. Dans la table **Fulfillment**, notez que les lignes de commande peuvent être remplies par plusieurs expéditions. (L’absence d’une ligne de commande signifie que la commande doit encore être remplie.)

![Le diagramme de modèle affiche désormais les lignes de la table. Les détails des lignes sont décrits dans le paragraphe suivant.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

Les détails des lignes pour les deux tables sont décrits dans la liste à puces suivante :

- La table **Order** comporte cinq lignes :
  - **OrderDate** 1er janvier 2019, **OrderID** 1, **OrderLine** 1, **ProductID** Prod-A, **OrderQuantity** 5, **Sales** 50
  - **OrderDate** 1er janvier 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Sales** 80
  - **OrderDate** 2 février 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Sales** 40
  - **OrderDate** 2 février 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Sales** 20
  - **OrderDate** 3 mars 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Sales** 100
- La table **Fulfillment** comporte quatre lignes :
  - **FulfillmentDate** 1er janvier 2019, **FulfillmentID** 50, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 2
  - **FulfillmentDate** 2 février 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** 2 février 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** 1er janvier 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

Voyons ce qui se passe lorsque le modèle est interrogé. Voici un visuel de table qui compare les quantités commandées et traitées selon la colonne **OrderID** de la table **Order**.

![Un visuel de table comporte trois colonnes : OrderID, OrderQuantity et FulfillmentQuantity. Il y a trois lignes, une pour chaque commande. Les lignes OrderID 2 et 3 ne sont pas complètement traitées.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

Le visuel présente un résultat précis. Toutefois, l’utilité du modèle est limitée : vous pouvez uniquement filtrer ou regrouper selon la colonne **OrderID** de la table **Order**.

### <a name="relate-many-to-many-facts-guidance"></a>Conseils sur l’association des faits plusieurs à plusieurs

En règle générale, nous vous déconseillons d’associer deux tables de type fait directement à l’aide de la cardinalité plusieurs à plusieurs. La raison principale est que le modèle n’offre pas de flexibilité dans la façon dont vos visuels de rapport filtrent ou regroupent. Dans l’exemple, il est uniquement possible pour les visuels de filtrer ou regrouper selon la colonne **OrderID** de la table **Order**. Une autre raison est liée à la qualité de vos données. Si vos données présentent des problèmes d’intégrité, il est possible que certaines lignes soient omises lors de l’interrogation en raison de la nature de la _relation faible_. Pour plus d’informations, consultez [Relations de modèle dans Power BI Desktop (évaluation de la relation)](../desktop-relationships-understand.md#relationship-evaluation).

Au lieu d’associer directement les tables de type fait, nous vous recommandons d’adopter les principes de conception de [schémas en étoile](star-schema.md). Pour ce faire, vous devez ajouter des tables de type dimension. Les tables de type dimension sont ensuite associées aux tables de type fait à l’aide de relations de type un à plusieurs. Cette approche de conception est fiable, car elle offre des options de création de rapports flexibles. Elle vous permet de filtrer ou de regrouper en utilisant n’importe quelle colonne de type dimension et de récapituler toute table de type fait associée.

Envisageons une meilleure solution.

![Un diagramme de modèle comprend six tables : OrderLine, OrderDate, Order, Fulfillment, Product et FulfillmentDate. Toutes les tables sont liées. La conception est décrite dans le paragraphe suivant.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Notez les modifications de conception suivantes :

- Le modèle comporte désormais quatre tables supplémentaires : **OrderLine**, **OrderDate**, **Product** et **FulfillmentDate**
- Les quatre tables supplémentaires sont toutes des tables de type dimension, et les relations de type un à plusieurs associent ces tables aux tables de type fait
- La table **OrderLine** contient une colonne **OrderLineID**, qui représente la valeur **OrderID** multipliée par 100, plus la valeur **OrderLine**, un identificateur unique pour chaque ligne de commande
- Les tables **Order** et **Fulfillment** contiennent désormais une colonne **OrderLineID**, et elles ne contiennent plus les colonnes **OrderID** ni **OrderLine**
- La table **Fulfillment** contient désormais les colonnes **OrderDate** et **ProductID**
- La table **FulfillmentDate** est associée uniquement à la table **Fulfillment**
- Toutes les colonnes d’identificateur unique sont masquées

Si vous prenez le temps d’appliquer les principes de conception de schémas en étoile, vous bénéficiez des avantages suivants :

- Vos visuels de rapport peuvent _filtrer ou regrouper_ selon n’importe quelle colonne visible à partir des tables de type dimension
- Vos visuels de rapport peuvent _récapituler_ toute colonne visible à partir des tables de type fait
- Les filtres appliqués aux tables **OrderLine**, **OrderDate** ou **Product** sont propagés aux deux tables de type fait
- Toutes les relations sont de type un à plusieurs, et chaque relation est une _relation solide_. Les problèmes d’intégrité des données ne sont pas masqués. Pour plus d’informations, consultez [Relations de modèle dans Power BI Desktop (évaluation de la relation)](../desktop-relationships-understand.md#relationship-evaluation).

## <a name="relate-higher-grain-facts"></a>Associer des faits de niveau plus général

Ce scénario de type plusieurs à plusieurs est très différent des deux autres qui sont déjà décrits dans cet article.

Prenons un exemple impliquant quatre tables : **Date**, **Sales**, **Product** et **Target**. **Date** et **Product** sont des tables de type dimension, et les relations de type un à plusieurs associent chacune à la table de type fait **Sales**. Jusqu’à présent, il s’agit d’une bonne conception de schéma en étoile. Toutefois, la table **Target** n’est pas encore liée aux autres tables.

![Un diagramme de modèle comprend quatre tables : Date, Sales, Product et Target. La table Target n’est associée à aucune autre table. La conception est décrite dans le paragraphe suivant.](media/relationships-many-to-many/sales-targets-model-example.png)

La table **Target** contient trois colonnes : **Category**, **TargetQuantity** et **TargetYear**. Les lignes de la table affichent une précision au niveau de l’année et de la catégorie de produit. En d’autres termes, les cibles, utilisées pour mesurer les performances des ventes, sont définies chaque année pour chaque catégorie de produit.

![La table Target comporte trois colonnes : TargetYear, Category et TargetQuantity. Six lignes enregistrent des cibles pour 2019 et 2020, chacune pour trois catégories.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Étant donné que la table **Target** stocke les données à un niveau supérieur à celui des tables de type dimension, il n’est pas possible de créer une relation de type un à plusieurs. Eh bien, cela est vrai pour une seule des relations. Étudions comment la table **Target** peut être associée aux tables de type dimension.

### <a name="relate-higher-grain-time-periods"></a>Associer des périodes de niveau plus général

Une relation entre les tables **Date** et **Target** doit être une relation de type un à plusieurs. Cela est dû au fait que les valeurs de la colonne **TargetYear** sont des dates. Dans cet exemple, chaque valeur de la colonne **TargetYear** est la première date de l’année cible.

> [!TIP]
> Lorsque vous stockez des faits à un niveau de précision temporelle supérieur à celui du jour, définissez le type de données de la colonne sur **Date** (ou **Nombre entier** si vous utilisez des dates clés). Dans la colonne, stockez une valeur représentant le premier jour de la période. Par exemple, une période d’un an est enregistrée en tant que 1er janvier de l’année, et une période d’un mois est enregistrée en tant que premier jour de ce mois.

Toutefois, il convient de veiller à ce que les filtres de niveau mois ou date produisent un résultat significatif. Sans logique de calcul spéciale, les visuels de rapport peuvent signaler que les dates cibles sont littéralement le premier jour de chaque année. Tous les autres jours, et tous les mois sauf janvier, récapitulent la quantité cible comme VIDE.

Le visuel de matrice suivant montre ce qui se produit quand l’utilisateur du rapport passe d’une année à ses mois. Le visuel récapitule la colonne **TargetQuantity**. (L’option [Afficher les éléments sans données](../desktop-show-items-no-data.md) a été activée pour les lignes de la matrice.)

![Un visuel de matrice affiche la quantité cible 270 pour l’année 2020. Quand il est développé pour afficher les mois de 2020, janvier correspond à 270, et la quantité cible au niveau d’un mois sur deux est VIDE.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

Pour éviter ce comportement, nous vous recommandons de contrôler la totalisation de vos données de faits à l’aide de mesures. Une façon de contrôler la totalisation consiste à retourner la valeur VIDE lorsque des périodes de niveau inférieur sont interrogées. Une autre méthode, définie avec une bibliothèque DAX sophistiquée, consiste à répartir les valeurs sur des périodes de niveau inférieur.

Considérez la définition de mesure suivante qui utilise la fonction DAX [ISFILTERED](/dax/isfiltered-function-dax). Elle retourne uniquement une valeur lorsque les colonnes **Date** ou **Month** ne sont pas filtrées.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

Le visuel de matrice suivant utilise désormais la mesure **TargetQuantity**. Elle indique que toutes les quantités cibles mensuelles sont VIDES.

![Un visuel de matrice affiche la quantité cible 270 pour l’année 2020. Quand il est développé pour afficher les mois de 2020, la quantité cible au niveau de chaque mois est VIDE.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Associer à un niveau plus général (non-date)

Une autre approche de conception est nécessaire lors de l’association d’une colonne non-date d’une table de type dimension à une table de type fait (et à un niveau plus général que la table de type dimension).

Les colonnes **Category** (des tables **Product** et **Target**) contiennent des valeurs en double. Il n’y a donc pas de « un » pour une relation de type un à plusieurs. Dans ce cas, vous devez créer une relation plusieurs à plusieurs. La relation doit propager les filtres dans une seule direction, de la table de type dimension à la table de type fait.

![Un fragment du diagramme de modèle montre les tables Target et Product. Une relation plusieurs à plusieurs associe les deux tables. La direction du filtre va de Product à Target.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Examinons maintenant les lignes de la table.

![Un diagramme de modèle contient deux tables : Target et Product. Une relation plusieurs à plusieurs associe les deux colonnes Category. Les détails des lignes sont décrits dans le paragraphe suivant.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

Dans la table **Target**, il y a quatre lignes : deux lignes pour chaque année cible (2019 et 2020) et deux catégories (Vêtements et Accessoires). Dans la table **Product**, il existe trois produits. Deux appartiennent à la catégorie Vêtements et l’autre à la catégorie Accessoires. L’une des couleurs de la catégorie Vêtements est Vert et les deux autres sont Bleu.

Un regroupement visuel de table selon la colonne **Category** de la table **Product** génère le résultat suivant.

![Un visuel de table comporte deux colonnes : Category et TargetQuantity. Accessoires correspond à 60, Vêtements à 40 et le total est égal à 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Ce visuel produit le résultat correct. Voyons maintenant ce qui se passe lorsque la colonne **Color** de la table **Product** est utilisée pour regrouper la quantité cible.

![Un visuel de table comporte deux colonnes : Color et TargetQuantity. Bleu correspond à 100, Vert à 40 et le total est égal à 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

Le visuel produit une représentation incorrecte des données. Que se passe-t-il ici ?

Un filtre sur la colonne **Color** de la table **Product** génère deux lignes. L’une des lignes concerne la catégorie Vêtements, tandis que l’autre concerne la catégorie Accessoires. Ces deux valeurs de catégorie sont propagées en tant que filtres à la table **Target**. En d’autres termes, étant donné que la couleur bleue est utilisée par les produits de deux catégories, _ces catégories_ sont utilisées pour filtrer les cibles.

Pour éviter ce comportement, comme décrit précédemment, nous vous recommandons de contrôler la totalisation de vos données de faits à l’aide de mesures.

Considérez la définition de mesure suivante. Notez que toutes les colonnes de la table **Product** qui se trouvent sous le niveau de catégorie sont testées pour les filtres.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

Le visuel de table suivant utilise désormais la mesure **TargetQuantity**. Elle indique que toutes les quantités cibles de couleur sont VIDES.

![Un visuel de table comporte deux colonnes : Color et TargetQuantity. Bleu correspond à VIDE, Vert à VIDE et le total est égal à 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

La conception du modèle final se présente comme suit.

![Le diagramme de modèle indique que les tables Date et Target sont liées par une relation de type un à plusieurs. Les tables Product et Target sont liées par une relation plusieurs à plusieurs, en filtrant depuis Product vers Target.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Conseils sur l’association des faits de niveau plus général

Lorsque vous devez associer une table de type dimension à une table de type fait, et que la table de type fait stocke des lignes à un niveau plus général que les lignes de la table de type dimension, nous donnons les conseils suivants :

- Pour les dates des faits de niveau plus général :
  - Dans la table de type fait, stockez la première date de la période
  - Créez une relation de type un à plusieurs entre la table de dates et la table de type fait
- Pour d’autres faits de niveau plus général :
  - Créez une relation plusieurs à plusieurs entre la table de type dimension et la table de type fait
- Pour les deux types :
  - Contrôlez la totalisation avec une logique de mesure : retournez la valeur VIDE quand des colonnes de type dimension de niveau inférieur sont utilisées pour filtrer ou regrouper
  - Masquez les colonnes récapitulatives de la table de type fait : ainsi, seules les mesures peuvent être utilisées pour récapituler la table de type fait

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Relations de modèle dans Power BI Desktop](../desktop-relationships-understand.md)
- [Comprendre le schéma en étoile et son importance pour Power BI](star-schema.md)
- [Aide à la résolution des problèmes de relations](relationships-troubleshoot.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
