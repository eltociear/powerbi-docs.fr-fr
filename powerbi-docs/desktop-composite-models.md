---
title: Utiliser des modèles composites dans Power BI Desktop (préversion)
description: Créer des modèles de données avec plusieurs connexions de données et des relations plusieurs-à-plusieurs dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 47c99e40b1665b98c33d16b685e359c10277a560
ms.sourcegitcommit: 1a79e48ac820c28c5d0fd05399f49ed22fc74ed7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49435393"
---
# <a name="use-composite-models-in-power-bi-desktop-preview"></a>Utiliser des modèles composites dans Power BI Desktop (préversion)

Avant dans Power BI Desktop, quand vous utilisiez un DirectQuery dans un rapport, aucune autre connexion de données, DirectQuery ou d’importation, n’était autorisée pour ce rapport. Avec les modèles composites, cette restriction est levée. Un rapport peut en toute transparence inclure des connexions de données provenant de plusieurs connexions de données DirectQuery ou d’importation, dans la combinaison de votre choix.

![Modèles composites dans Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

La fonctionnalité des modèles composites dans Power BI Desktop se compose de trois fonctionnalités connexes :

* **Modèles composites** : permet à un rapport d’avoir plusieurs connexions de données, notamment des connexions provenant de DirectQuery ou d’une importation, dans toutes les combinaisons. Cet article décrit en détail les modèles composites.

* **Relations plusieurs à plusieurs** : avec les *modèles composites*, vous pouvez établir des *relations plusieurs à plusieurs* entre les tables. Cette approche supprime la nécessité d’avoir des valeurs uniques dans les tables. Les solutions de contournement précédentes, comme la présentation de nouvelles tables uniquement pour établir des relations, sont également supprimées. Pour plus d’informations, consultez [Relations plusieurs à plusieurs dans Power BI Desktop (préversion)](desktop-many-to-many-relationships.md).

* **Mode de stockage** : vous pouvez désormais spécifier les visuels qui nécessitent une requête sur les sources de données back-end. Les visuels qui ne nécessitent pas une requête sont importés même s’ils sont basés sur DirectQuery. Cette fonctionnalité permet d’améliorer les performances et de réduire la charge du back-end. Avant, même de simples visuels, comme les segments, lançaient des requêtes qui étaient envoyées à des sources back-end. Pour plus d’informations, consultez [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md).

## <a name="enable-the-composite-models-preview-feature"></a>Activer la fonctionnalité en préversion des modèles composites

La fonctionnalité des modèles composites est en préversion et doit être activée dans Power BI Desktop. Pour activer les modèles composites, sélectionnez **Fichier** > **Options et paramètres** > **Options** > **Fonctionnalités en préversion**, puis cochez la case **Modèles composites**. 

![Volet « Fonctionnalités en préversion »](media/desktop-composite-models/composite-models_02.png)

Pour activer la fonctionnalité, vous devez redémarrer Power BI Desktop.

![Fenêtre « La fonctionnalité nécessite un redémarrage »](media/desktop-composite-models/composite-models_03.png)


## <a name="use-composite-models"></a>Utiliser des modèles composites

Avec les modèles composites, vous pouvez vous connecter à toutes sortes de sources de données quand vous utilisez Power BI Desktop ou le service Power BI. Vous pouvez établir ces connexions aux données de deux façons :

* En important des données dans Power BI, ce qui est la méthode la plus courante pour obtenir des données.
* En vous connectant directement aux données dans leur dépôt source d’origine à l’aide de DirectQuery. Pour en savoir plus sur DirectQuery, consultez [Utiliser DirectQuery dans Power BI](desktop-directquery-about.md).

Quand vous utilisez DirectQuery, les *modèles composites* permettent de créer un modèle Power BI (par exemple, un fichier Power BI Desktop *.pbix* unique) qui effectue l’une des opérations suivantes, ou les deux :

* Combine les données d’une ou de plusieurs sources DirectQuery.
* Combine les données de sources DirectQuery et d’importation.

Par exemple, avec des modèles composites, il est possible de générer un modèle qui combine les types de données suivants :

* Données de ventes d’un entrepôt de données d’entreprise.
* Données de cibles de ventes d’une base de données SQL Server d’un service.
* Données importées à partir d’une feuille de calcul. 

Un modèle combinant les données de plusieurs sources DirectQuery ou DirectQuery avec des données d’importation est appelé *modèle composite*.

> [!NOTE]
> À partir de la version d’octobre 2018 de Power BI Desktop, vous *pouvez* publier des modèles composites sur le service Power BI. Pour l’actualisation planifiée et l’actualisation de la vignette de tableau de bord, les modèles composites dans le service Power BI se comportent de la même façon que les modèles d’importation. 

Vous pouvez créer des relations entre les tables comme vous l’avez toujours fait, même quand ces tables proviennent de différentes sources, en tenant compte de la restriction suivante : toutes les relations entre sources doivent être définies comme ayant une cardinalité *plusieurs-à-plusieurs*, quelle que soit leur cardinalité réelle. Le comportement de ces relations est alors le même que d’habitude pour les relations *plusieurs-à-plusieurs*, comme décrit dans [Relations plusieurs-à-plusieurs dans Power BI Desktop (préversion)](desktop-many-to-many-relationships.md). 

> [!NOTE]
> Dans le contexte des modèles composites, toutes les tables importées sont en fait une source unique, indépendamment de la source de données sous-jacente réelle à partir de laquelle elles sont importées.   

## <a name="example-of-a-composite-model"></a>Exemple de modèle composite

Comme exemple de *modèle composite*, prenons un rapport connecté à un entrepôt de données d’entreprise dans SQL Server à l’aide de DirectQuery. Dans cet exemple, l’entrepôt de données contient les données des ventes par pays (*Sales by Country*), trimestre (*Quarter*) et vélo (*Bike (Product)*), comme illustré dans l’image suivante :

![Vue de la relation pour les modèles composites](media/desktop-composite-models/composite-models_04.png)

À ce stade, vous pouvez générer des visuels simples à l’aide des champs de cette source. Par exemple, l’image suivant montre le total des ventes par *ProductName* d’un trimestre sélectionné. 

![Visuel basé sur des données](media/desktop-composite-models/composite-models_05.png)

Mais que se passe-t-il si vous avez des données dans une feuille de calcul Office Excel sur le chef de produit assigné à chaque produit, avec une priorité de marketing ? Si vous voulez voir le montant des ventes (*Sales Amount*) par chef de produit (*Product Manager*), il n’est peut-être pas possible d’ajouter ces données locales à l’entrepôt de données d’entreprise. Ou cela prendrait plusieurs mois dans le meilleur des cas. 

Il peut être possible d’importer ces données de ventes à partir de l’entrepôt de données, au lieu d’utiliser DirectQuery. Les données de ventes peuvent ensuite être combinées aux données importées à partir de la feuille de calcul. Toutefois, cette approche est déconseillée pour les raisons qui préconisent l’utilisation de DirectQuery. Les raisons sont notamment :

* Combinaison des règles de sécurité appliquées dans la source sous-jacente.
* Nécessité de pouvoir afficher les données les plus récentes.
* Échelle des données. 

C’est ici que les modèles composites entrent en jeu. Les modèles composites vous permettent de vous connecter à l’entrepôt de données à l’aide de DirectQuery, puis d’utiliser GetData pour des sources supplémentaires. Dans cet exemple, nous établissons d’abord la connexion DirectQuery à l’entrepôt de données d’entreprise. Nous utilisons GetData et choisissons Excel, puis accédons à la feuille de calcul contenant nos données locales. Enfin, nous importons la feuille de calcul contenant les valeurs *Product Names* (Noms des produits), *Sales Manager* (Responsable commercial) et *Priority* (Priorité).  

![Fenêtre du navigateur](media/desktop-composite-models/composite-models_06.png)

Dans la liste **Champs**, vous pouvez voir deux tables : la table *Bike* d’origine provenant de SQL Server et une nouvelle table **ProductManagers**. La nouvelle table contient les données importées à partir d’Excel. 

![Vue des champs des tables](media/desktop-composite-models/composite-models_07.png)

De même, dans le champ **Relationship view** (Vue de la relation) dans Power BI Desktop, nous voyons à présent une nouvelle table appelée **Product Managers**. 

![Vue de la relation des tables](media/desktop-composite-models/composite-models_08.png)

Nous devons maintenant associer ces tables aux autres tables du modèle. Comme toujours, nous créons une relation entre la table **Bike** à partir de SQL Server et la table **ProductManagers** importée. Autrement dit, la relation est établie entre *Bike[ProductName]* et *ProductManagers[ProductName]*. Comme indiqué précédemment, toutes les relations dans la source doivent avoir la cardinalité *plusieurs-à-plusieurs* par défaut. 

![Fenêtre Créer une relation](media/desktop-composite-models/composite-models_09.png)

Une fois cette relation établie, elle s’affiche comme prévu dans **Vue de la relation** dans Power BI Desktop.

![Vue de la nouvelle relation](media/desktop-composite-models/composite-models_10.png)

Nous pouvons maintenant créer des visuels à l’aide de l’un des champs de la liste **Champs**. Cette approche fusionne facilement les données de plusieurs sources. Par exemple, le montant total des ventes (*SalesAmount*) pour chaque chef de produit (*Product Manager*) s’affiche dans l’image suivante : 

![Le volet Champs](media/desktop-composite-models/composite-models_11.png)

L’exemple suivant montre un cas courant de table *dimension* (comme *Produit* ou *Client*) étendue avec des données supplémentaires importées à partir d’un autre emplacement. Des tables peuvent également utiliser DirectQuery pour se connecter à différentes sources. Pour étendre notre exemple, imaginez que les tables *Sales Targets* (Cibles de ventes) par *Country* (Pays) et *Period* (Période) sont stockées dans une base de données distincte d’un service. Comme vous le faites habituellement, vous pouvez utiliser *GetData* pour vous connecter à ces données, comme illustré dans l’image suivante : 

![Fenêtre du navigateur](media/desktop-composite-models/composite-models_12.png)

Comme nous l’avons fait précédemment, nous pouvons créer des relations entre la nouvelle table et d’autres tables du modèle, puis créer des visuels qui combinent leurs données. Examinons à nouveau **Vue de la relation**, où nous avons établi les nouvelles relations :

![Vue de la relation avec plusieurs tables](media/desktop-composite-models/composite-models_13.png)

L’image suivante est basée sur les nouvelles données et les relations que nous avons créées. Le visuel en haut à gauche affiche le montant total des ventes (*Sales Amount*) par rapport aux cibles de ventes (*Target*), et le calcul de la variance montre la différence. Les données *Sales Amount* et *Target* proviennent de deux bases de données SQL Server différentes. 

![Image montrant plus de données](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>Définir le mode de stockage

Chaque table d’un modèle composite comporte un mode de stockage qui indique si la table est basée sur une importation ou DirectQuery. Le mode de stockage peut être affiché et modifié dans le volet **Propriété**. Pour afficher le mode de stockage, cliquez avec le bouton droit sur une table dans la liste **Champs**, puis sélectionnez **Propriétés**. L’illustration suivante montre le mode de stockage pour la table **SalesTargets**.

![Définition du mode de stockage](media/desktop-composite-models/composite-models_15.png)

Le mode de stockage peut également être consulté dans l’info-bulle de chaque table.

![Info-bulle affichant le mode de stockage](media/desktop-composite-models/composite-models_16.png)

Pour tout fichier Power BI Desktop (fichier *.pbix*) contenant des tables provenant de DirectQuery et de certaines tables d’importation, la barre d’état affiche un mode de stockage appelé **Mixte**. Vous pouvez cliquer sur ce terme dans la barre d’état et basculer facilement toutes les tables sur Importer.

Pour plus d’informations sur le mode de stockage, consultez [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md).  

## <a name="calculated-tables"></a>Tables calculées

Vous pouvez ajouter des tables calculées à un modèle qui utilise DirectQuery. Le langage DAX (Data Analysis Expressions) qui définit la table calculée peut référencer des tables importées ou DirectQuery, ou une combinaison des deux. 

Les tables calculées sont toujours importées, et leurs données sont actualisées en même temps que les tables. Si une table calculée référence une table DirectQuery, les visuels faisant référence à la table DirectQuery affichent toujours les valeurs les plus récentes dans la source sous-jacente. Autrement, les visuels faisant référence à la table calculée affichent les valeurs au moment de la dernière actualisation de la table calculée.

## <a name="security-implications"></a>Implications en matière de sécurité 

Les modèles composites ont des implications sur la sécurité. Une requête envoyée à une source de données peut inclure des valeurs de données qui ont été récupérées à partir d’une autre source. Dans l’exemple précédent, le visuel qui montre le montant des ventes (*SalesAmount*) par chef de produit (*Product Manager*) envoie une requête SQL à la base de données relationnelle **Sales**. Cette requête SQL peut contenir les noms des chefs de produit (*Product Managers*) et leurs produits (*Products*) associés. 

![Script montrant les implications en matière de sécurité](media/desktop-composite-models/composite-models_17.png)

Pour cette raison, les informations stockées dans la feuille de calcul sont désormais incluses dans une requête envoyée à la base de données relationnelle. Si ces informations sont confidentielles, vous devez tenir compte des implications en matière de sécurité. En particulier, tenez compte des points suivants :

* Tout administrateur de la base de données capable d’afficher les traces ou les journaux d’audit peut voir ces informations, même s’il ne dispose pas des autorisations pour accéder aux données de la source d’origine. Dans cet exemple, l’administrateur a besoin d’autorisations pour le fichier Excel.

* Les paramètres de chiffrement pour chaque source doivent être considérés. Vous souhaitez éviter que les informations ne soient récupérées à partir d’une source à l’aide d’une connexion chiffrée, puis incluses par inadvertance dans une requête envoyée à une autre source à l’aide d’une connexion non chiffrée. 

Afin de confirmer que les implications en matière de sécurité ont bien été prises en compte, Power BI Desktop affiche un message d’avertissement quand vous créez un modèle composite.  

Pour des raisons similaires, vous devez faire attention quand vous ouvrez un fichier Power BI Desktop envoyé à partir d’une source non fiable. Si ce fichier contient des modèles composites, cela signifie que les informations récupérées à partir d’une source en utilisant les informations d’identification de l’utilisateur qui ouvre le fichier sont envoyées vers une autre source de données dans le cadre de la requête. Les informations peuvent être vues par l’auteur malveillant du fichier Power BI Desktop. Par conséquent, quand vous ouvrez un fichier Power BI Desktop qui contient plusieurs sources pour la première fois, Power BI Desktop affiche un avertissement. Cet avertissement est similaire à l’avertissement affiché lors de l’ouverture d’un fichier contenant des requêtes SQL natives.  

## <a name="performance-implications"></a>Impact sur les performances  

Quand vous utilisez DirectQuery, tenez toujours compte des performances pour garantir avant tout que la source backend dispose de ressources suffisantes pour assurer une bonne expérience aux utilisateurs. Une bonne expérience signifie que les visuels doivent s’actualiser en cinq secondes ou moins. Vous devez également suivre les conseils de performances présentés dans l’article [Utiliser DirectQuery dans Power BI](desktop-directquery-about.md). 

L’utilisation des modèles composites implique de nouvelles considérations sur les performances. Un seul visuel peut entraîner l’envoi de requêtes vers plusieurs sources, souvent en passant les résultats d’une requête à une deuxième source. Cette situation peut se produire dans les scénarios d’exécution suivants :

* **Une requête SQL incluant un grand nombre de valeurs littérales** : par exemple, un visuel demandant le montant total des ventes (*Sales Amount*) pour un groupe spécifique de chefs de produit (*Product Managers*) doit d’abord identifier les produits *(Products)* gérés par ces chefs de produit. Cette séquence doit se produire avant que le visuel n’envoie une requête SQL qui contient tous les ID de produit dans une clause *WHERE*.

* **Une requête SQL effectuée à un niveau inférieur de granularité avec les données agrégées localement** : comme le nombre de produits (*Products*) qui correspondent aux critères de filtre Chef de produit (*Product Manager*) est de plus en plus important, il peut s’avérer inefficace ou impossible d’inclure tous les produits dans une clause *WHERE*. Au lieu de cela, vous pouvez interroger la source relationnelle au niveau inférieur *Product* (Produit), puis agréger les résultats localement. Si la cardinalité des *produits* dépasse une limite de 1 million, la requête échoue.

* **Plusieurs requêtes SQL, une par groupe et par valeur** : quand l’agrégation utilise des données **DistinctCount** regroupées par une colonne d’une autre source, si la source externe ne prend pas en charge la transmission efficace des nombreuses valeurs littérales qui définissent le regroupement, il est nécessaire d’envoyer une requête SQL par groupe et par valeur. 

   Par exemple, un visuel demandant un décompte distinct de la valeur *CustomerAccountNumber* (de la table SQL Server) par *Product Manager* (table importée de la feuille de calcul) doit passer les détails de la table *Product Managers* dans la requête envoyée à SQL Server. Avec d’autres sources, par exemple Redshift, cette action n’est pas possible. Au lieu de cela, une requête SQL est envoyée pour chaque *responsable commercial* jusqu’à une limite pratique à laquelle la requête échoue. 

Chacun de ces cas comporte ses propres implications en termes de performances, et les détails exacts varient pour chaque source de données. Même si la cardinalité des colonnes utilisées dans la relation qui unit les deux sources reste faible (quelques milliers), les performances ne devraient pas être affectées. À mesure que cette cardinalité augmente, vous devez examiner de plus près l’impact sur les performances. Appliquez ces recommandations comme règle d’or. 

Par ailleurs, avec les relations *plusieurs-à-plusieurs*, des requêtes distinctes doivent être envoyées à la source sous-jacente pour chaque niveau total ou sous-total, au lieu d’agréger localement les valeurs détaillées. Un simple visuel de table avec des totaux envoie deux requêtes SQL plutôt qu’une. 

## <a name="limitations-and-considerations"></a>Considérations et limitations

Cette version de modèles composites présente quelques limitations.

Les sources (multidimensionnelles) Live Connect suivantes ne peuvent pas être utilisées avec les modèles composites :

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Jeux de données Power BI
* Azure Analysis Services

Quand vous vous connectez à ces sources multidimensionnelles à l’aide de DirectQuery, vous ne pouvez pas vous connecter à une autre source DirectQuery ou la combiner avec des données d’importation.

Les limitations existantes concernant DirectQuery s’appliquent toujours quand vous utilisez des modèles composites. Plusieurs de ces limitations sont désormais appliquées par table, selon le mode de stockage de la table. Par exemple, une colonne calculée d’une table d’importation peut faire référence à d’autres tables, mais une colonne calculée d’une table DirectQuery ne peut toujours faire référence qu’à des colonnes de la même table. D’autres limitations s’appliquent au modèle dans son ensemble, si aucune des tables du modèle n’est de type DirectQuery. Par exemple, les fonctionnalités QuickInsights et Questions et réponses ne sont pas disponibles sur un modèle si l’une des tables qu’il contient a un mode de stockage de type DirectQuery. 

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les modèles composites et DirectQuery, consultez les articles suivants :
* [Relations plusieurs à plusieurs dans Power BI Desktop (préversion)](desktop-many-to-many-relationships.md)
* [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md)
* [Utiliser DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI](desktop-directquery-data-sources.md)

