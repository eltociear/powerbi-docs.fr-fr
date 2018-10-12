---
title: Utiliser des modèles composites dans Power BI Desktop (préversion)
description: Créer des modèles de données avec plusieurs connexions de données et des relations plusieurs-à-plusieurs dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 4e7692be8ec78c79076408635a75dbf0ab9080d2
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974043"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Modèles composites dans Power BI Desktop (préversion)

Précédemment dans **Power BI Desktop**, lorsque vous utilisiez un DirectQuery dans un rapport, aucune autre connexion de données, qu’elles proviennent de DirectQuery ou d’une importation, n’était autorisée pour ce rapport. Avec les **modèles composites**, cette restriction est levée, et un rapport peut en toute transparence inclure des connexions de données provenant de plusieurs connexions de données provenant de DirectQuery ou d’une importation, dans la combinaison de votre choix.

![modèles composites dans Power BI Desktop](media/desktop-composite-models/composite-models_01.png)

La fonctionnalité des **modèles composites** dans **Power BI Desktop** se compose de trois fonctionnalités connexes :

* **Modèles composites** : permet à un rapport d’avoir plusieurs connexions de données, y compris des connexions provenant de DirectQuery ou d’une importation, dans toutes les combinaisons.
* **Relations plusieurs-à-plusieurs** : les **modèles composites** vous permettent d’établir des **relations plusieurs-à-plusieurs** entre des tables, sans saisir obligatoirement des valeurs uniques dans les tables et en supprimant les précédentes solutions de contournement telles que la présentation de nouvelles tables uniquement pour établir des relations. 
* **Mode de stockage** : vous pouvez désormais spécifier les visuels qui nécessitent une requête pour les sources de données principales, et ceux qui n’en ont pas besoin sont importés même s’ils sont basés sur DirectQuery, ce qui améliore les performances et réduit la charge du serveur principal. Auparavant, même de simples visuels comme les segments initiés par des requêtes sont envoyés à des sources principales. 

Cette collection de trois fonctionnalités connexes pour **modèles composites** est décrite dans différents articles :

* Les **modèles composites** sont décrits en détail dans cet article.
* Les **relations plusieurs-à-plusieurs** sont décrites dans un propre dédié, [Relations plusieurs-à-plusieurs dans Power BI Desktop (version préliminaire)](desktop-many-to-many-relationships.md).
* Le **mode de stockage** est décrit dans un article dédié, [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md).

## <a name="enabling-the-composite-models-preview-feature"></a>Activation de la fonctionnalité préliminaire des modèles composites

La fonctionnalité **Modèles composites** est en version préliminaire et doit être activée dans **Power BI Desktop**. Pour activer les **modèles composites**, sélectionnez **Fichiers > Options et paramètres > Options > Fonctionnalités en version préliminaire**, puis cochez la case **modèles composites**. 

![activation des fonctionnalités en préversion](media/desktop-composite-models/composite-models_02.png)

Vous devrez redémarrer **Power BI Desktop** pour activer la fonctionnalité.

![redémarrage requis pour appliquer les modifications](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>Utilisation des modèles composites

Avec les **modèles composites**, lorsque vous utilisez **Power BI Desktop** ou le service **Power BI**, vous pouvez vous connecter à toutes sortes de sources de données et établir ces connexions aux données de différentes façons. Vous pouvez importer des données dans Power BI, ce qui est la méthode la plus courante pour obtenir des données, ou vous connecter directement aux données dans leur dépôt source d’origine à l’aide de DirectQuery. Pour en savoir plus sur DirectQuery, consultez l’article [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md).

Lorsque vous utilisez DirectQuery avec des **modèles composites**, il est possible de créer un modèle Power BI (par exemple, un fichier Power BI Desktop .pbix unique) qui effectue les opérations suivantes :

* combine les données provenant d’une ou plusieurs sources DirectQuery, et/ou
* combine les données provenant de sources DirectQuery et de données d’importation

Par exemple, avec des **modèles composites**, il est possible de générer un modèle qui combine les données de ventes de l’entrepôt de données d’une entreprise avec les données de cibles commerciales se trouvant dans la base de données SQL Server d’un service, ainsi que certaines données importées à partir d’une feuille de calcul. Un modèle combinant les données de plusieurs sources DirectQuery ou DirectQuery avec des données importées est appelé *modèle composite*.

> [!NOTE]
> Les modèles composites en version préliminaire ne peuvent pas être publiés dans le service Power BI. 

Vous pouvez créer des relations entre les tables car vous devez toujours, même lorsque ces tables proviennent de différentes sources, tenir compte de la restriction suivante : toutes les relations entre les sources doivent être définies comme ayant une cardinalité **plusieurs-à-plusieurs** , quelle que soit leur cardinalité réelle. Le comportement de ces relations est alors le même que pour les relations **plusieurs-à-plusieurs**, comme décrit dans [Relations plusieurs-à-plusieurs dans Power BI Desktop (préversion)](desktop-many-to-many-relationships.md). Notez que dans le contexte des modèles composites, toutes les tables importées sont en fait une source unique, indépendamment de la source de données sous-jacente réelle à partir de laquelle elles sont réellement importées.   

## <a name="example-of-using-composite-models"></a>Exemple d’utilisation des modèles composites

Comme exemple de **modèle composite**, prenons un rapport connecté à un entrepôt de données d’entreprise (dans SQL Server) à l’aide de DirectQuery, où l’entrepôt de données contient les données des ventes par pays (*Sales by Country*), trimestre (*Quarter*), et vélo (*Bike (Product)*), comme illustré dans l’image suivante.

![vue relation pour les modèles composites](media/desktop-composite-models/composite-models_04.png)

À ce stade, vous pouvez générer des visuels simples à l’aide des champs de cette source. Par exemple, le visuel suivant montre le montant total des ventes par *ProductName*, d’un trimestre sélectionné. 

![visuel basé sur des données](media/desktop-composite-models/composite-models_05.png)

Mais que se passe-t-il si vous avez des informations sur le chef de produit assigné à chaque produit, avec une priorité de marketing ? Où ces données sont-elles conservées dans une feuille de calcul Excel ? Vous pouvez voir le montant des ventes (*Sales Amount*) par chef de produit (*Product Manager*), mais l’ajout de ces données locales à l’entrepôt de données d’entreprise est probablement impossible, ou prendrait plusieurs mois dans le meilleur des cas. Même s’il est possible d’importer ces données de vente à partir de l’entrepôt de données (au lieu d’utiliser DirectQuery), ce qui permettrait à ce stade de les combiner aux données importées à partir de la feuille de calcul, cette approche est déconseillée pour des raisons qui préconisent l’utilisation de DirectQuery. Par exemple, avec certaines combinaisons des règles de sécurité appliquées dans la source sous-jacente, vous devez pouvoir afficher les données les plus récentes et l’échelle des données. 

C’est ici que les **modèles composites** entrent en jeu. Les modèles composites vous donnent la possibilité de vous connecter à l’entrepôt de données à l’aide de DirectQuery et aussi d’utiliser GetData pour des sources supplémentaires. Dans ce cas, nous établissons la connexion DirectQuery à l’entrepôt de données de l’entreprise, nous utilisons GetData et choisissons Excel, puis accédons à la feuille de calcul contenant nos données locales avant d’importer la feuille contenant les valeurs *ProductNames* (noms des produits), *SalesManager* (responsable commercial) et *Priority* (priorité).  

![Fenêtre du navigateur](media/desktop-composite-models/composite-models_06.png)

Maintenant, dans la liste des **champs**, nous voyons la table des vélos (*Bike*) (provenant de SQL Server) et une nouvelle table des chefs de produit (*Product Managers*) (avec les données importées à partir d’Excel). 

![Vue des champs des tables](media/desktop-composite-models/composite-models_07.png)

De même, en examinant le champ **Relationship View** (vue relation) dans **Power BI Desktop**, nous voyons à présent une nouvelle table appelée *Product Managers* (chefs de produit). 

![Vue des relations des tables](media/desktop-composite-models/composite-models_08.png)

Nous devons maintenant associer ces éléments aux autres tables du modèle, comme nous l’avons toujours fait, en créant une relation entre la table *Bike* (dans SQL Server) et la table *Product Managers* (importée), par exemple entre *Bike[ProductName]* (Vélo[Nom du produit]) et *ProductManagers[ProductName]* (Chef[Nom du produit]). Comme indiqué plus haut dans cet article, toutes les relations dans la source doivent avoir la cardinalité **plusieurs-à-plusieurs** et, par conséquent, c’est la cardinalité par défaut qui est sélectionnée. 

![boîte de dialogue créer une relation](media/desktop-composite-models/composite-models_09.png)

Une fois cette relation créée, elle s’affiche comme prévu dans **Vue relation** dans **Power BI Desktop**.

![vue nouvelle relation](media/desktop-composite-models/composite-models_10.png)

Une fois ces relations de table établies, nous pouvons maintenant créer des visuels à l’aide d’un des champs de la liste **Champs**, en fusionnant facilement les données de plusieurs sources. Par exemple, le visuel ci-dessous affiche le total des *ventes* pour chaque *chef de produit*. 

![visuel avec volet Champs affiché](media/desktop-composite-models/composite-models_11.png)

Cet exemple montre un cas courant de table *dimension* (comme *Produit* ou *Client*) en cours d’extension avec des données supplémentaires importées à partir d’un autre emplacement. Des tables peuvent également utilisent DirectQuery avec une connexion à différentes sources. Par conséquent, pour étendre notre exemple, imaginez que les tables *SalesTargets* (Objectifs de vente) par *Country* (Pays) et *Period* (Période) sont stockées dans une base de données départementale distincte. Vous pouvez utiliser **GetData** pour vous connecter à ces données comme vous le faites habituellement, comme illustré dans l’image suivante. 

![Boîte de dialogue Navigateur](media/desktop-composite-models/composite-models_12.png)

Ensuite, comme nous l’avons fait précédemment dans cet exemple, nous pouvons créer des relations entre la nouvelle table et d’autres tables du modèle, et créer des visuels qui combinent leurs données. Examinons à nouveau la **vue Relations**, dans laquelle nous avons établi des relations dans notre scénario d’exemple étendu.

![vue des relations avec plusieurs tables](media/desktop-composite-models/composite-models_13.png)

Comme indiqué dans l’image suivante basée sur les nouvelles données et les relations que nous venons de créer, le visuel dans le coin inférieur gauche affiche le total de *Sales Amount* (ventes) par rapport à *Target* (objectif), avec une variance montrant la différence, où les valeurs *Sales Amount* (ventes) et *Target* (objectif) proviennent de deux différentes bases de données SQL Server. 

![visuels montrant plus de données](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>Définition du mode de stockage

Chaque table d’un **modèle composite** comporte un **mode de stockage** qui indique si la table est basée sur une importation ou DirectQuery. Le **mode de stockage** peut être affiché et modifié dans le volet **Propriété**. Pour y accéder, sélectionnez **Propriétés** dans le menu contextuel **Champs**. L’illustration suivante montre le **mode de stockage** (abrégé en **Stockage...**  dans l’image, en raison de la largeur du volet).

![Définition du mode de stockage](media/desktop-composite-models/composite-models_15.png)

Le **mode de stockage** peut également être consulté dans l’infobulle de chaque table.

![infobulle avec mode de stockage](media/desktop-composite-models/composite-models_16.png)

Pour tout fichier **Power BI Desktop** (fichier .pbix) contenant des tables provenant de DirectQuery et de certaines tables d’importation, la barre d’état affiche un **mode de stockage** de type **Mixed** (mixte). Vous pouvez cliquer sur ce terme dans la barre d’état et basculer facilement entre toutes les tables à importer.

Le **mode de stockage** est décrit de façon exhaustive dans l’article [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md).  

## <a name="calculated-tables"></a>Tables calculées

Des tables calculées peuvent être ajoutées à un modèle qui utilise DirectQuery, et la valeur DAX qui définit la table calculée peut référencer des tables importées ou DirectQuery, ou une combinaison des deux. 

Les tables calculées sont toujours importées, et les données de ces tables sont actualisées en même temps que la table. Par conséquent, si une table calculée référence une table DirectQuery, les visuels faisant référence à la table DirectQuery affichent toujours les valeurs les plus récentes dans la source sous-jacente, mais les visuels faisant référence à la table calculée affichent les valeurs au moment où la table calculée a été actualisée.

## <a name="security-implications"></a>Implications en matière de sécurité 

Les modèles composites ont des implications sur la sécurité. Une requête envoyée à une source de données peut inclure des valeurs de données qui ont été récupérées à partir d’une autre source. Pour l’exemple décrit plus haut dans cet article, le visuel qui montre les ventes (*Sales Amount*) par chef de produit (*Product Manager*) génère l’envoi d’une requête SQL à la base de données relationnelle des ventes (**Sales**), où cette requête SQL peut contenir les noms des chefs de produit (*Product Managers*) et leurs produits (*Products*) associés. 

![script montrant les implications sur la sécurité](media/desktop-composite-models/composite-models_17.png)

Pour cette raison, les informations stockées dans la feuille de calcul sont désormais incluses dans une requête envoyée à la base de données relationnelle. Si ces informations sont confidentielles, les implications sur la sécurité correspondantes doivent être prises en compte. En particulier, vous devez envisager les conséquences suivantes :

* Tout administrateur de la base de données capable d’afficher les traces ou les journaux d’audit peut voir ces informations, même s’il ne dispose pas des autorisations pour accéder aux données de la source d’origine (dans ce cas, les autorisations pour le fichier Excel).

* Les paramètres de chiffrement pour chaque source doivent être considérés, afin d’éviter que les informations ne soient récupérées à partir d’une source à l’aide d’une connexion chiffrée, mais qu’elles soient incluses par inadvertance dans une requête envoyée à une autre source à l’aide d’une connexion non chiffrée. 

**Power BI Desktop** affiche un message d’avertissement lorsqu’une action est déclenchée pour créer un modèle composite, afin de confirmer que les implications sur la sécurité ont bien été prises en compte.  

Pour des raisons similaires, vous devez faire attention lorsque vous ouvrez un fichier **Power BI Desktop** envoyé à partir d’une source non fiable. Si ce fichier contient des modèles composites, cela signifie que les informations récupérées à partir d’une source (en utilisant les informations d’identification de l’utilisateur à l’ouverture du fichier) seraient envoyées vers une autre source de données dans le cadre de la requête (où peuvent être vues par l’auteur malveillant du fichier Power BI Desktop). Par conséquent, lorsque vous ouvrez un fichier Power BI Desktop pour la première fois, s’il contient plusieurs sources, un avertissement s’affiche. Cet avertissement est similaire à l’avertissement affiché lors de l’ouverture d’un fichier contenant des requêtes SQL natives.  

## <a name="performance-implications"></a>Impact sur les performances  

Lorsque vous utilisez DirectQuery, tenez toujours compte des performances, pour s’assurer avant tout que le serveur principal source dispose de ressources suffisantes pour garantir une bonne expérience aux utilisateurs. Une bonne expérience signifie que les visuels doivent s’actualiser en 5 secondes ou moins. Vous devez également suivre les conseils de performances présentés dans l’article [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md). L’utilisation des modèles composites implique de nouvelles considérations sur les performances, car un seul visuel peut entraîner l’envoi de requêtes vers plusieurs sources, souvent en passant les résultats d’une requête à une deuxième source. Cette situation peut se produire dans les scénarios d’exécution suivants :

* **Une requête SQL incluant un grand nombre de valeurs littérales** : par exemple, un visuel demandant le total des ventes *Sales Amount* (à partir de la base de données SQL) pour un groupe spécifique de chefs de produit *Product Managers* (de la table associée importée à partir d’une feuille de calcul) doit d’abord identifier les produits (*Products*) gérés par les chefs de produit avant d’envoyer une requête SQL, y compris tous les ID de produit dans une clause *WHERE*.

* **Une requête SQL effectuée à un niveau inférieur de granularité avec les données agrégées localement** : en utilisant le même exemple que la liste à puces précédente, comme le nombre de *produits* qui correspondent au filtre *Product Manager* (chef de produit) devient très volumineuse et devient, à un certain point, inefficace ou incapable d’inclure toutes les données dans une clause *WHERE*. Au lieu de cela, il est nécessaire d’interroger la source relationnelle au niveau inférieur *Product* (Produit), puis d’agréger les résultats localement. Si la cardinalité des *produits* dépasse une limite de 1 million, la requête échoue.

* **Plusieurs requêtes SQL, une par groupe et par valeur** : lorsque l’agrégation utilise des données **DistinctCount** regroupées par une colonne d’une autre source, si la source externe ne prend pas en charge la transmission efficace des nombreuses valeurs littérales qui définissent le regroupement, il est nécessaire d’envoyer une requête SQL par groupe et par valeur. Par exemple, un visuel demandant un décompte distinct de la valeur *CustomerAccountNumber* (à partir de la table SQL Server) par chef de produit *Product Manager* (à partir de la table associée importée d’une feuille de calcul) doit passer les détails de la table des chefs de produit *Product Managers* dans la requête envoyée à SQL Server. Avec les autres sources, par exemple Redshift, cela n’est pas possible et une requête SQL est alors envoyée pour chaque responsable des ventes (*Sales Manager*), jusqu'à une limite pratique à laquelle la requête échoue. 

Chacun de ces cas comporte ses propres implications en termes de performances, et les détails exacts varient pour chaque source de données. Une règle empirique précise que même si la cardinalité des colonnes utilisées dans la relation qui unit les deux sources reste faible (quelques milliers), les performances ne devraient pas être très affectées. À mesure que cette cardinalité augmente, vous devez examiner de plus près l’impact sur les performances. 

Par ailleurs, avec les relations **plusieurs-à-plusieurs**, des requêtes distinctes doivent être envoyées à la source sous-jacente pour chaque niveau total/sous-total, au lieu d’agréger localement les valeurs détaillées. Par conséquent, un simple visuel de table avec des totaux envoie deux requêtes SQL plutôt qu’une. 

## <a name="limitations-and-considerations"></a>Considérations et limitations

Il existe quelques limitations pour cette version de **modèles composites**.

Les sources (multidimensionnelles) Live Connect suivantes ne peuvent pas être utilisées avec les **modèles composites** :

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Jeux de données Power BI
* Azure Analysis Services

Lors de la connexion à ces sources multidimensionnelles à l’aide de DirectQuery, vous ne pouvez pas non plus vous connecter à une autre source DirectQuery ni combiner les données avec des données importées.

Les limitations existantes concernant l’utilisation de DirectQuery s’appliquent lorsque vous utilisez des **modèles composites**. Plusieurs de ces limitations sont désormais appliquées par table, selon le **mode de stockage** de la table. Par exemple, une colonne calculée d’une table importée peut référencer d’autres tables, mais une colonne calculée d’une table DirectQuery est toujours limitée pour référencer uniquement des colonnes de la même table. D’autres limitations s’appliquent au modèle dans son ensemble, si aucune des tables du modèle n’est de type DirectQuery. Par exemple, les fonctionnalités **QuickInsights** et **Q&A** ne sont pas disponibles sur un modèle si une des tables qu’il contient possède un **mode de stockage** de type DirectQuery. 

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants décrivent en détail les modèles composites ainsi que le mode DirectQuery.

* [Relations plusieurs-à-plusieurs dans Power BI Desktop (préversion)](desktop-many-to-many-relationships.md)
* [Mode de stockage dans Power BI Desktop (préversion)](desktop-storage-mode.md)

Articles DirectQuery :

* [Utilisation de DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery dans Power BI](desktop-directquery-data-sources.md)

