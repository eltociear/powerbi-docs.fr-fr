---
title: Utiliser le mode de stockage dans Power BI Desktop
description: Utiliser le mode de stockage pour contrôler si les données des rapports sont mises en cache en mémoire dans Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 01/29/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 0a3121e31aa816139c338746635b102be2d8fd88
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413814"
---
# <a name="manage-storage-mode-in-power-bi-desktop"></a>Gérer le mode de stockage dans Power BI Desktop

Dans Microsoft Power BI Desktop, vous pouvez spécifier le mode de stockage d’une table. Le mode de stockage vous permet de contrôler si Power BI Desktop met dans la mémoire cache des données de table pour les rapports. 

La définition du mode de stockage offre de nombreux avantages. Vous pouvez définir le mode de stockage pour chaque table individuellement dans votre modèle. Cette action permet d’avoir un seul jeu de données, ce qui offre les avantages suivants :

* **Performances des requêtes** : Comme les utilisateurs interagissent avec les visuels dans les rapports Power BI, les requêtes Data Analysis Expressions (DAX) sont soumises au jeu de données. La mise en cache des données en mémoire par définition correcte du mode de stockage peut améliorer les performances des requêtes et l’interactivité de vos rapports.

* **Jeux de données volumineux** : Les tables qui ne sont pas mises en cache ne consomment pas de mémoire pour la mise en cache. Vous pouvez activer une analyse interactive de jeux de données volumineux qui sont trop grands ou trop coûteux pour être entièrement mis dans la mémoire cache. Vous pouvez choisir quelles tables valent la peine d’être mises en cache et quelles tables n’en valent pas la peine.

* **Optimisation de l’actualisation des données** : Vous n’avez pas besoin d’actualiser les tables qui ne sont pas mises en cache. Vous pouvez réduire les temps d’actualisation en mettant en cache uniquement les données nécessaires pour répondre à vos accords de niveau de service et aux besoins de votre entreprise.

* **Exigences de temps quasi réel** : Les tables avec des exigences de temps quasi réel peuvent tirer parti de ne pas être mises en cache afin de réduire la latence des données.

* **Réécriture** : L’écriture différée permet aux utilisateurs professionnels d’analyser des scénarios en modifiant les valeurs des cellules. Des applications personnalisées peuvent appliquer des modifications à la source de données. Les tables qui ne sont pas mises en cache peuvent afficher des modifications immédiatement, permettant l’analyse instantanée des effets.

Le paramètre de mode de stockage dans Power BI Desktop est une des trois fonctionnalités connexes :

* **Modèles composites** : Permet à un rapport d’avoir deux connexions de données ou plus, y compris des connexions provenant de DirectQuery ou d’une importation, dans toutes les combinaisons. Pour plus d’informations, consultez [Utiliser des modèles composites dans Power BI Desktop](desktop-composite-models.md).

* **Relations plusieurs à plusieurs** : avec les modèles composites, vous pouvez établir des *relations plusieurs à plusieurs* entre les tables. Dans une relation plusieurs à plusieurs, il n’y a plus la nécessité d’avoir des valeurs uniques dans les tables. Les solutions de contournement préalables, comme la présentation de nouvelles tables uniquement pour établir des relations, sont également supprimées. Pour plus d’informations, consultez [Relations plusieurs à plusieurs dans Power BI Desktop](desktop-many-to-many-relationships.md).

* **Mode de stockage** : avec cette option, vous pouvez désormais spécifier les visuels qui nécessitent une requête sur les sources de données back-end. Les visuels qui ne nécessitent pas une requête sont importés même s’ils sont basés sur DirectQuery. Cette fonctionnalité permet d’améliorer les performances et de réduire la charge du serveur principal. Auparavant, même de simples visuels, comme les segments, initiaient des requêtes qui étaient envoyées à des sources back-end. 

## <a name="use-the-storage-mode-property"></a>Utiliser la propriété Mode de stockage

La propriété **Mode de stockage** est une propriété que vous pouvez définir sur chaque table de votre modèle pour contrôler la façon dont Power BI met en cache les données de la table.

Pour définir la propriété **Mode de stockage** ou voir son paramétrage actuel : 

1. dans la vue **Modèle**, sélectionnez la table dont vous souhaitez définir ou afficher les propriétés. 
2. Dans le volet **Propriétés**, développez la section **Avancé**, puis développez la liste déroulante **Mode de stockage**.

   ![Sélectionner la propriété Mode de stockage](media/desktop-storage-mode/storage-mode-02.png)

Définissez la propriété **Mode de stockage** sur l’une de ces trois valeurs :

* **Importer** : les tables importées avec ce paramètre sont mises en cache. Les requêtes soumises au jeu de données Power BI qui retournent des données à partir de tables d’importation peuvent uniquement être satisfaites à partir de données mises en cache.

* **DirectQuery** : les tables avec ce paramètre ne sont pas mises en cache. Les requêtes que vous envoyez au jeu de données Power BI, comme les requêtes DAX, et qui retournent des données de tables DirectQuery peuvent être satisfaites uniquement en exécutant des requêtes à la demande sur la source de données. Les requêtes envoyées à la source de données utilisent le langage de requête de cette source de données, par exemple, SQL.

* **Double** : les tables avec ce paramètre peuvent agir comme mises en cache ou non mises en cache, selon le contexte de la requête envoyée au jeu de données Power BI. Dans certains cas, vous répondez aux requêtes à partir des données mises en cache. Dans d’autres cas, vous répondez aux requêtes en exécutant une requête à la demande à la source de données.

Si vous changez la propriété **Mode de stockage** d’une table sur **Importer**, cette opération est *irréversible*. Une fois définie, cette propriété ne peut plus être changée en **DirectQuery** ou **Double**.

> [!NOTE]
> Vous pouvez utiliser le mode de stockage **Double** à la fois dans Power BI Desktop et le service Power BI.


## <a name="constraints-on-directquery-and-dual-tables"></a>Contraintes sur les tables DirectQuery et Double

Les tables doubles ont les mêmes contraintes fonctionnelles que les tables DirectQuery. Ces contraintes incluent des transformations M limitées et des fonctions DAX restreintes dans les colonnes calculées. Pour plus d’informations, consultez [Implications de l’utilisation de DirectQuery](../connect-data/desktop-directquery-about.md#implications-of-using-directquery).

## <a name="propagation-of-the-dual-setting"></a>Propagation du paramètre Double
Considérez le modèle simple suivant, où toutes les tables sont d’une source unique qui prend en charge l’importation et DirectQuery.

![Exemple d’affichage de relation pour le mode de stockage](media/desktop-storage-mode/storage-mode-04.png)

Supposons que toutes les tables dans ce modèle ont initialement été définies sur le mode **DirectQuery**. Si vous changez ensuite la propriété **Mode de stockage** de la table **SurveyResponse** sur **Importer**, la fenêtre d’avertissement suivante s’affiche :

![Fenêtre d’avertissement sur le mode de stockage](media/desktop-storage-mode/storage-mode-05.png)

Vous pouvez définir les tables de dimension (**Customer**, **Geography** et **Date**) sur **Double** pour réduire le nombre de relations limitées dans le jeu de données et améliorer le niveau de performance. Les relations limitées impliquent normalement au moins une table DirectQuery où la logique de jointure ne peut pas être envoyée (push) aux systèmes sources. Étant donné que les tables doubles peuvent agir comme des tables DirectQuery ou Importer, cette situation est évitée.

La logique de propagation est conçue pour apporter une aide dans le cas de modèles qui contiennent de nombreuses tables. Supposons que vous disposez d’un modèle de 50 tables et que seules certaines tables de faits (transactionnelles) doivent être mises en cache. La logique dans Power BI Desktop calcule l’ensemble minimal des tables de dimension qui doivent être définies sur **Double**, de sorte que vous n’êtes pas obligé de le faire.

La logique de propagation parcourt uniquement le côté « un » des relations un-à-plusieurs.

## <a name="storage-mode-usage-example"></a>Exemple d’utilisation du mode de stockage
Nous allons poursuivre avec l’exemple de la section précédente et imaginer que nous appliquons les paramètres de propriété de mode de stockage suivants :

| Table                   | Mode de stockage         |
| ----------------------- |----------------------| 
| Ventes                 | DirectQuery          | 
| SurveyResponse        | Importer               | 
| Date                  | Double                 | 
| Client              | Double                 | 
| Géographie             | Double                 | 


La définition de ces propriétés de mode de stockage produit les comportements suivants, en supposant que la table **Sales** comporte un volume de données important :
* Power BI Desktop met en cache les tables de dimension (**Date**, **Customer** et **Geography**), ce qui permet de charger rapidement les rapports initiaux lors de la récupération des valeurs de segment à afficher.
* Power BI Desktop ne met pas en cache la table **Sales**. En ne mettant pas en cache cette table, Power BI Desktop donne les résultats suivants :
    * Les temps d’actualisation des données sont améliorés et la consommation de mémoire est réduite.
    * Les requêtes de rapport qui sont basées sur la table **Sales** sont exécutées en mode **DirectQuery**. Ces requêtes peuvent prendre plus ou moins de temps, mais elles s’exécutent en quasi temps réel, car aucune latence de mise en cache n’est introduite.

* Les requêtes de rapport basées sur la table **SurveyResponse** sont retournées de la mémoire cache et, par conséquent, elles sont assez rapides.

## <a name="queries-that-hit-or-miss-the-cache"></a>Requêtes accédant au cache ou le manquant

Si vous connectez SQL Profiler au port de diagnostic de Power BI Desktop, vous pouvez voir quelles requêtes accèdent ou non à la mémoire cache en traçant les événements suivants :

* Événements de requêtes\Début de requête
* Traitement de requête\Début de requête Vertipaq SE
* Traitement de requête\Début de DirectQuery

Pour chaque événement de *Début de requête*, vérifiez d’autres événements ayant le même ID *ActivityID*. Par exemple, s’il n’y a pas d’événement *Début de DirectQuery*, mais qu’il y a un événement *Début de la requête Vertipaq SE*, c’est que la réponse à la requête provient du cache.

Les requêtes qui référencent des tables Double retournent des données du cache en priorité ; si cela n’est pas possible, elles rebasculent vers DirectQuery.

Si l’on continue avec l’exemple précédent, la requête suivante fait référence uniquement à une colonne de la table **Date**, qui est en mode **Double**. Par conséquent, la requête devrait accéder au cache :

![Capture d’écran montrant le texte de la requête qui fait référence à la table Date.](media/desktop-storage-mode/storage-mode-06.png)

La requête suivante fait référence uniquement à une colonne de la table **Sales**, qui se trouve en mode **DirectQuery**. Par conséquent, elle ne devrait *pas* accéder au cache :

![Capture d’écran montrant le texte de la requête qui fait référence à la table Sales.](media/desktop-storage-mode/storage-mode-07.png)

La requête suivante est intéressante, car elle combine les deux colonnes. Cette requête n’atteint pas le cache. Initialement, vous pouvez prévoir de récupérer des valeurs **CalendarYear** dans le cache et des valeurs **SalesAmount** dans la source, puis combiner les résultats, mais cette approche est moins efficace que d’envoyer l’opération SUM/GROUP BY au système source. Si l’opération est envoyée (push down) vers la source, le nombre de lignes retournées sera probablement bien moindre : 

![Capture d’écran montrant le texte de la requête qui fait référence à la table Date et à la table Sales.](media/desktop-storage-mode/storage-mode-08.png)

> [!NOTE]
> Ce comportement est différent des [relations plusieurs à plusieurs](desktop-many-to-many-relationships.md) dans Power BI Desktop quand les tables mises en cache et non mises en cache sont combinées.

## <a name="caches-should-be-kept-in-sync"></a>Les caches doivent toujours être synchronisés.

Les requêtes affichées dans la section précédente montrent que les tables Double accèdent certaines fois au cache et n’y accèdent pas d’autres fois. Pour cette raison, si le cache est obsolète, des valeurs différentes peuvent être retournées. L’exécution de la requête ne tente pas de masquer les problèmes de données, par exemple, en filtrant les résultats DirectQuery pour qu’ils correspondent aux valeurs mises en cache. Il vous incombe de connaître vos flux de données et de réaliser la conception en conséquence. Il existe des techniques établies pour gérer ces cas à la source, si nécessaire.

Le mode de stockage **Double** est une optimisation des performances. Il doit être utilisé seulement s’il ne compromet pas la capacité à répondre aux besoins de l’entreprise. Pour implémenter un autre comportement, envisagez d’utiliser les techniques décrites dans [Relations plusieurs à plusieurs dans Power BI Desktop](desktop-many-to-many-relationships.md).

## <a name="data-view"></a>Affichage des donnés
Si au moins une table dans le jeu de données a son mode de stockage défini sur **Importer** ou **Double**, l’onglet **Affichage des données** est affichable.

![Vue Données dans Power BI Desktop](media/desktop-storage-mode/storage-mode-03.png)

Quand vous sélectionnez des tables Double ou Importer dans la vue **Données**, ces tables affichent les données mises en cache. Les tables DirectQuery n’affichent pas les données, et un message s’affiche indiquant que les tables DirectQuery ne peuvent pas être affichées.


## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations pour cette version de mode de stockage et sa corrélation avec des modèles composites.

Les sources multidimensionnelles avec connexion active suivantes ne peuvent pas être utilisées avec les modèles composites :

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Jeux de données Power BI
* Azure Analysis Services

Quand vous vous connectez à ces sources multidimensionnelles à l’aide de DirectQuery, vous ne pouvez pas vous connecter à une autre source DirectQuery ni la combiner avec des données importées.

Les limitations existantes concernant l’utilisation de DirectQuery s’appliquent lorsque vous utilisez des modèles composites. Plusieurs de ces limitations sont désormais appliquées par table, selon le mode de stockage de la table. Par exemple, une colonne calculée d’une table importée peut référencer d’autres tables, mais une colonne calculée d’une table DirectQuery est toujours limitée pour référencer uniquement des colonnes de la même table. D’autres limitations s’appliquent au modèle dans son ensemble, si aucune des tables du modèle n’est de type DirectQuery. Par exemple, les fonctionnalités QuickInsights et Questions et réponses ne sont pas disponibles sur un modèle si l’une des tables qu’il contient a un mode de stockage de type DirectQuery. 

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les modèles composites et DirectQuery, consultez les articles suivants :
* [Modèles composites dans Power BI Desktop](desktop-composite-models.md)
* [Relations plusieurs à plusieurs dans Power BI Desktop](desktop-many-to-many-relationships.md)
* [Utiliser DirectQuery dans Power BI](../connect-data/desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI](../connect-data/power-bi-data-sources.md)
