---
title: Utilisation de DirectQuery dans Power BI
description: Comprendre l’utilisation de DirectQuery avec Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1104c7f90f46252a74c4aa8e5ec573a159ef1c40
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46550118"
---
# <a name="using-directquery-in-power-bi"></a>Utilisation de DirectQuery dans Power BI
Lorsque vous utilisez **Power BI Desktop** ou le **service Power BI**, vous pouvez vous connecter à toutes sortes de sources de données et établir ces connexions aux données de différentes façons. Vous pouvez soit *importer* des données dans Power BI, ce qui est la méthode la plus courante pour obtenir des données, soit vous connecter directement aux données dans leur dépôt source d’origine, ce qu’on appelle une requête **DirectQuery**. Cet article décrit la requête **DirectQuery** et ses fonctionnalités, et comprend les rubriques suivantes :

* Différentes options de connectivité pour DirectQuery
* Conseils relatifs à l’opportunité d’utiliser DirectQuery plutôt qu’une importation
* Inconvénients de l’utilisation de DirectQuery
* Meilleure pratique pour l’utilisation de DirectQuery

En bref, la meilleure pratique pour l’utilisation d’une importation plutôt que de DirectQuery est la suivante :

* Nous vous recommandons d’**importer** des données dans Power BI chaque fois que c’est possible. L’importation tire parti du moteur de requête hautes performances de Power BI et vous offre une expérience très interactive et complète de vos données.
* Si vous ne pouvez pas atteindre vos objectifs en important des données, songez à utiliser **DirectQuery**. Par exemple, lorsque les données changent fréquemment et que les rapports doivent refléter les données les plus récentes, DirectQuery est préférable. Cependant, l’utilisation de DirectQuery n’est généralement possible que lorsque la source de données sous-jacente est capable de fournir des requêtes interactives (en moins de 5 secondes) pour une requête d’agrégation type et qu’elle peut gérer la charge de requête ainsi générée. En outre, vous devez examiner avec soin la liste des limitations associées à l’utilisation de DirectQuery pour vous assurer que vos objectifs sont accessibles.

L’ensemble des fonctionnalités offertes par Power BI pour les deux modes de connectivité (importation et DirectQuery) évoluera au fil du temps. Il inclura une plus grande flexibilité lors de l’utilisation de données importées, de sorte que l’importation pourra être utilisée dans davantage de cas, tout en éliminant certains des inconvénients liés à l’utilisation de DirectQuery. Quelles que soient les améliorations, en cas d’utilisation de DirectQuery, les performances de la source de données sous-jacente resteront toujours une considération majeure. Si cette source de données sous-jacente est lente, l’utilisation de DirectQuery demeure impossible.

Cette rubrique a trait à DirectQuery avec Power BI, non à SQL Server Analysis Services. DirectQuery est aussi une fonctionnalité de **SQL Server Analysis Services**, et bon nombre des détails décrits ci-dessous s’appliquent à son utilisation. Cependant, il existe aussi des différences importantes. Pour plus d’informations sur l’utilisation de DirectQuery avec SQL Server Analysis Services, consultez le [livre blanc détaillant l’utilisation de DirectQuery dans SQL Server Analysis Services 2016](http://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

Si cet article se concentre sur le flux de travail recommandé pour DirectQuery, où le rapport est créé dans **Power BI Desktop**, il traite également de la connexion directe au **service Power BI**.

## <a name="power-bi-connectivity-modes"></a>Modes de connectivité Power BI
Power BI se connecte à un vaste éventail de sources de données, notamment :

* services en ligne (Salesforce, Dynamics 365, etc.) ;
* bases de données (SQL Server, Access, Amazon Redshift, etc.) ;
* fichiers simples (Excel, JSON, etc.) ;
* autres sources de données (Spark, sites web, Microsoft Exchange, etc.).

Pour ces sources, il est généralement possible d’importer les données dans Power BI. Pour certaines, il est également possible de se connecter à l’aide de DirectQuery. Le jeu exact des sources qui prennent en charge DirectQuery est décrit dans l’article [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md). D’autres sources seront prises en charge par DirectQuery dans le futur. L’accent sera mis principalement sur les sources susceptibles d’offrir de bonnes performances de requête interactive.

**SQL Server Analysis Services** constitue un cas spécial. Lors de la connexion à SQL Server Analysis Services, vous pouvez choisir d’importer les données ou d’utiliser une *connexion active*.  L’utilisation d’une *connexion active* est similaire à l’utilisation de DirectQuery, car aucune donnée n’est importée, et la source de données sous-jacente est toujours interrogée pour actualiser un visuel. Toutefois, elle s’en distingue également à maints égards, ce qui justifie l’utilisation de termes distincts (*active* et *DirectQuery*).

Les trois options pour la connexion aux données (**Importation**, **DirectQuery** et **Connexion active**) sont décrites en détail dans les sections suivantes.

### <a name="import-connections"></a>Connexions d’importation
Lorsque vous utilisez la commande **Obtenir des données** dans **Power BI Desktop** pour vous connecter à une source de données telle que SQL Server, puis choisissez **Importer**, le comportement de cette connexion est le suivant :

* Lors de l’exécution initiale de la commande **Obtenir des données**, les tables sélectionnées définissent chacune une requête qui retourne un jeu de données (ces requêtes peuvent être modifiées avant le chargement des données, par exemple, pour appliquer des filtres, agréger les données ou joindre des tables différentes).
* Lors du chargement, toutes les données définies par ces requêtes sont importées dans le cache Power BI.
* Lors de la génération d’un visuel dans **Power BI Desktop**, les données importées sont interrogées. Le magasin Power BI garantissant que la requête sera très rapide, toutes les modifications apportées au visuel sont immédiatement reflétées.
* Les modifications apportées aux données sous-jacentes n’apparaissent dans aucun visuel. Il est nécessaire d’*actualiser*, après quoi les données sont réimportées.
* Lors de la publication du rapport (fichier .pbix) sur le **service Power BI**, un jeu de données est créé et chargé sur le service Power BI.  Les données importées sont incluses dans ce jeu de données. Il est possible de configurer une actualisation planifiée des données, par exemple pour les réimporter quotidiennement. Selon l’emplacement de la source de données d’origine, il peut être nécessaire de configurer une passerelle de données locale.
* Lors de l’ouverture d’un rapport existant dans le **service Power BI** ou de la création d’un rapport, les données importées sont réinterrogées, ce qui garantit l’interactivité.
* Des visuels ou des pages de rapport entières peuvent être épinglés sous forme de vignettes de tableau de bord. Les vignettes sont actualisées automatiquement chaque fois que le jeu de données sous-jacent est actualisé.  

### <a name="directquery-connections"></a>Connexions DirectQuery
Lorsque vous utilisez la commande **Obtenir des données** dans **Power BI Desktop** pour vous connecter à une source de données, puis choisissez **DirectQuery**, le comportement de cette connexion est le suivant :

* Lors de l’exécution initiale de la commande **Obtenir des données**, la source est sélectionnée. Pour des sources relationnelles, cela signifie qu’un ensemble de tables sont sélectionnées, chacune définissant une requête qui retourne un jeu de données de façon logique. Pour des sources multidimensionnelles telles que SAP BW, seule la source est sélectionnée.
* Toutefois, lors du chargement, aucune donnée n’est réellement importée dans le magasin Power BI. Au lieu de cela, lors de la génération d’un visuel dans **Power BI Desktop**, des requêtes sont envoyées à la source de données sous-jacente pour extraire les données nécessaires. Le temps d’actualisation du visuel varie selon les performances de la source de données sous-jacente.
* Les modifications apportées aux données sous-jacentes sont immédiatement répercutées dans tous les visuels existants. Il est toujours nécessaire d’actualiser, après quoi les requêtes nécessaires sont renvoyées pour chaque visuel et le visuel mis à jour si nécessaire.
* Lors de la publication du rapport sur le **service Power BI**, celui-ci génère à nouveau un jeu de données, tout comme pour une importation. Toutefois, *aucune donnée* n’est incluse dans ce jeu de données.
* Lors de l’ouverture ou de la création d’un rapport dans le **service Power BI**, la source de données sous-jacente est à nouveau interrogée pour extraire les données nécessaires. Selon l’emplacement de la source de données d’origine, il peut être nécessaire de configurer une passerelle de données locale, comme c’est le cas pour le mode Importation si les données sont actualisées.
* Des visuels ou des pages de rapport entières peuvent être épinglés sous forme de vignettes de tableau de bord. Pour garantir la rapidité de l’ouverture d’un tableau de bord, les vignettes sont actualisées automatiquement à intervalles réguliers (par exemple, toutes les heures). La fréquence de cette actualisation peut être contrôlée afin de refléter la fréquence à laquelle les données changent, et en fonction de l’importance d’afficher les données les plus récentes. Par conséquent, lors de l’ouverture d’un tableau de bord, les vignettes reflètent les données correspondant à l’heure de la dernière actualisation, et pas nécessairement les toutes dernières modifications apportées à la source de données sous-jacente. Il est toujours possible d’actualiser un tableau de bord ouvert pour s’assurer que celui-ci est à jour.    

### <a name="live-connections"></a>Connexions actives
Lorsque vous vous connectez à **SQL Server Analysis Services** (SSAS), vous avez la possibilité d’importer les données à partir du modèle de données sélectionné ou d’établir une connexion active à celui-ci. Si vous choisissez d’**importer**, vous définissez une requête sur cette source SSAS externe et les données sont importées normalement. Si vous optez pour une **connexion active**, aucune requête n’est définie, et le modèle externe tout entier apparaît dans la liste de champs. Si vous sélectionnez **DirectQuery**, à mesure que les visuels sont générés, des requêtes sont envoyées à la source SSAS externe. Toutefois, à la différence de DirectQuery, il n’y a pas lieu de créer un *modèle*. En d’autres termes, il n’est pas possible de définir de nouvelles colonnes calculées, hiérarchies, relations et autres. Au lieu de cela, vous vous connectez directement au modèle SSAS externe.

La situation décrite dans le paragraphe précédent s’applique également à la connexion aux sources suivantes, à ceci près qu’il n’existe aucune option pour importer les données :

* jeux de données Power BI (par exemple, lorsque vous vous connectez à un jeu de données Power BI précédemment créé et publié sur le service afin de générer un nouveau rapport) ;
* Common Data Services.

Le comportement des rapports sur SSAS lors de la publication sur le **service Power BI** présente les similitudes suivantes avec les rapports DirectQuery :

* Lors de l’ouverture ou de la création d’un rapport dans le **service Power BI**, la source SSAS sous-jacente est interrogée (ce qui nécessite éventuellement une passerelle de données locale).
* Les vignettes de tableau de bord sont actualisées automatiquement à intervalles réguliers (par exemple, toutes les heures, ou selon toute autre fréquence définie).

En revanche, il existe également des différences importantes, dont le fait que, pour les connexions actives, l’identité de l’utilisateur ouvrant le rapport est toujours transmise à la source SSAS sous-jacente.

Ces comparaisons étant faites, la suite de cet article porte exclusivement sur **DirectQuery**.

## <a name="when-is-directquery-useful"></a>Quand DirectQuery est-il utile ?
Le tableau suivant décrit les scénarios où une connexion avec DirectQuery peut être particulièrement utile, y compris les cas où le fait de laisser les données dans la source d’origine est considéré comme bénéfique. La description inclut une discussion concernant la disponibilité du scénario spécifié dans Power BI.

| Limitation | Description |
| --- | --- |
| Les données changent fréquemment et des rapports en quasi temps réel sont nécessaires |Les modèles avec des données importées peuvent être actualisés au maximum une fois par heure. Par conséquent, si les données évoluent en permanence et s’il est nécessaire que les rapports présentent les données les plus récentes, l’utilisation de l’importation avec une actualisation à intervalles réguliers pourrait tout simplement ne pas répondre à ces besoins. Notez également qu’il est possible d’envoyer les données en streaming directement à Power BI, même s’il existe des limites aux volumes de données pris en charge en pareil cas. <br/> <br/> En revanche, l’utilisation de DirectQuery signifie que l’ouverture ou l’actualisation d’un rapport ou d’un tableau de bord affiche toujours les données les plus récentes dans la source. Par ailleurs, les vignettes de tableau de bord peuvent être mises à jour plus fréquemment (jusqu’à toutes les 15 minutes). |
| Les données sont très volumineuses |Si les données sont très volumineuses, il est certainement impossible de les importer toutes. À l’opposé, DirectQuery ne requiert aucun transfert important de données, car celles-ci sont interrogées sur place. <br/> <br/> Toutefois, des données volumineuses peuvent également impliquer un ralentissement excessif des performances des requêtes portant sur cette source sous-jacente (comme expliqué dans la section *Implications de l’utilisation de DirectQuery*, plus loin dans cet article). Et bien sûr, il n’est pas toujours nécessaire d’importer l’absolue totalité des données. Au lieu de cela, les données peuvent être pré-agrégées lors de l’importation (l’**Éditeur de requête** facilite précisément cette opération). À la limite, il serait possible d’importer exactement les données d’agrégation nécessaires pour chaque visuel. Ainsi, si DirectQuery constitue l’approche la plus simple pour des données volumineuses, vous devez toujours garder à l’esprit que l’importation de données agrégées peut offrir une solution si la source de données sous-jacente est trop lente. |
| Des règles de sécurité sont définies dans la source sous-jacente |Quand les données sont importées, Power BI se connecte à la source de données en utilisant les informations d’identification de l’utilisateur actif (extraites de Power BI Desktop) ou des informations d’identification définies dans le cadre de la configuration de l’actualisation planifiée (extraites du service Power BI). Par conséquent, en cas de publication et de partage d’un tel rapport, il convient de veiller à partager uniquement avec des utilisateurs autorisés à consulter les données concernées, ou de définir une sécurité au niveau des lignes associée au jeu de données. <br/> <br/> Dans l’idéal, étant donné que DirectQuery interroge toujours la source sous-jacente, cela permettrait d’appliquer toute sécurité intégrée dans cette source sous-jacente. Toutefois, aujourd’hui, Power BI se connecte toujours à la source sous-jacente à l’aide des mêmes informations d’identification que celles utilisées pour l’importation. <br/> <br/> Par conséquent, tant que Power BI ne permet pas que l’identité de l’utilisateur du rapport soit transmise directement à la source sous-jacente, DirectQuery n’offre aucun avantage en matière de sécurité de la source de données. |
| Des restrictions de souveraineté des données s’appliquent |Certaines organisations adoptent des stratégies en matière de souveraineté des données, en vertu desquelles les données ne peuvent pas quitter le site de l’organisation. Une solution basée sur l’importation occasionnerait clairement des problèmes. À l’opposé, avec DirectQuery, ces données restent dans la source sous-jacente. <br/> <br/> Toutefois, il convient de noter que, même avec DirectQuery, des caches de données au niveau du visuel sont conservés dans le service Power BI (en raison de l’actualisation planifiée des vignettes). |
| La source de données sous-jacente est une source OLAP contenant des mesures |Si la source de données sous-jacente contient des *mesures* (comme c’est le cas dans SAP HANA ou SAP Business Warehouse), l’importation des données génère d’autres problèmes. Cela signifie que les données importées présentent un niveau particulier d’agrégation, défini par la requête. Par exemple, mesurez TotalSales selon les critères Class, Year et City. Ensuite, si un visuel est créé, qui demande des données à un niveau supérieur d’agrégation (par exemple, TotalSales selon le critère Year), il agrège encore davantage la valeur agrégée. Cela convient pour des mesures additives (par exemple, Somme, Min), mais constitue un problème pour des mesures non additives (par exemple, Moyenne, DistinctCount). <br/> <br/> Pour faciliter l’obtention des données agrégées appropriées (en fonction des besoins du visuel) directement à partir de la source, il faudrait envoyer des requêtes par visuel, comme c’est le cas dans DirectQuery. <br/> <br/> Lors de la connexion à SAP Business Warehouse (BW), le choix de DirectQuery permet ce traitement des mesures. La prise en charge pour SAP BW est décrite de façon plus approfondie dans [DirectQuery et SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> Toutefois, actuellement, DirectQuery sur SAP HANA traite cela comme une source relationnelle et, par conséquent, se comporte de façon similaire à une importation. Ce sujet est développé dans [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md). |

En résumé, compte tenu des capacités actuelles de DirectQuery dans Power BI, les scénarios avantageux sont les suivants :

* Les données changent fréquemment et des rapports en quasi temps réel sont nécessaires
* Gestion de données très volumineuses ne nécessitant pas d’agrégation préalable
* Des restrictions de souveraineté des données s’appliquent
* La source est multidimensionnelle et contient des mesures (par exemple, SAP BW)

Notez que les détails de la liste précédente ont trait à l’utilisation de Power BI seul. Il existe toujours la possibilité d’utiliser un modèle SQL Server Analysis Services (ou Azure Analysis Services) externe pour importer des données, puis d’utiliser Power BI pour se connecter à ce modèle. Si cette approche nécessite des compétences supplémentaires, elle offre davantage de flexibilité. Par exemple, elle permet l’importation de volumes de données beaucoup plus importants et n’impose aucune restriction à la fréquence d’actualisation des données.

## <a name="implications-of-using-directquery"></a>Implications de l’utilisation de DirectQuery
L’utilisation de **DirectQuery** peut avoir des conséquences négatives, comme l’explique cette section. Certaines de ces limitations peuvent varier légèrement selon la source utilisée. Cela est signalé, le cas échéant, et des rubriques distinctes traitent des sources sensiblement différentes.  

### <a name="performance-and-load-on-the-underlying-source"></a>Performances et charge sur la source sous-jacente
Lors de l’utilisation de **DirectQuery**, l’expérience globale dépend beaucoup des performances de la source de données sous-jacente. Si l’actualisation de chaque visuel (par exemple, après modification d’une valeur de segment) prend quelques secondes (< 5 s), l’expérience peut être raisonnable, mais sembler lente par rapport à la réponse immédiate à laquelle nous sommes habitués lors de l’importation de données dans Power BI. Si, au lieu de cela, la lenteur de la source a pour effet que l’actualisation des visuels prend plus de temps (quelques dizaines de secondes), l’expérience devient médiocre, jusqu’au point même où les délais de requête expirent.

Outre les performances de la source sous-jacente, il convient d’accorder une attention particulière à la charge qui est placée sur celle-ci (qui a bien sûr également une incidence sur les performances). Comme évoqué plus haut, chaque ouverture de rapport partagé par un utilisateur, et chaque actualisation périodique de vignette de tableau de bord, ont pour effet d’envoyer au moins une requête par visuel à la source sous-jacente. Cela exige que la source puisse gérer une telle charge de requête, tout en continuant à offrir des performances raisonnables.

### <a name="limited-to-a-single-source"></a>Limitation à une source unique
Lors de l’importation de données, il est possible de combiner des données de plusieurs sources dans un seul modèle, par exemple pour joindre facilement des données d’une base de données SQL Server d’entreprise avec des données locales conservées dans un fichier Excel. Cela n’est pas possible avec DirectQuery. Lorsque vous sélectionnez DirectQuery pour une source, vous ne pouvez utiliser que les données de cette source (par exemple, une base de données SQL Server).

### <a name="limited-data-transformations"></a>Transformations de données limitées
De même, il existe des limitations aux transformations de données qui peuvent être appliquées dans l’**Éditeur de requête**. Avec des données importées, il est possible d’appliquer aisément un ensemble sophistiqué de transformations afin de nettoyer les données et d’en modifier la forme avant de les utiliser pour créer des visuels (par exemple, en analysant des documents JSON ou en faisant pivoter des données disposées en colonnes pour les disposer en lignes). Ces transformations sont plus limitées dans DirectQuery. Tout d’abord, lorsque vous vous connectez à une source OLAP telle que SAP Business Warehouse, aucune transformation ne peut être définie et le modèle externe entier est extrait de la source. Pour des sources relationnelles comme SQL Server, il est toujours possible de définir une série de transformations par requête, mais celles-ci sont limitées pour des raisons de performances. Toutes les transformations de ce type doivent être appliquées à chaque requête adressée à la source sous-jacente, plutôt qu’une seule fois lors de l’actualisation des données, de sorte qu’elles sont limitées aux transformations qui peuvent raisonnablement être traduites dans une seule requête native. Si vous utilisez une transformation trop complexe, vous recevez un message d’erreur indiquant que vous devez la supprimer, ou que le modèle a basculé vers le mode Importation.

De plus, la requête qui résulte de la commande **Obtenir des données** ou de l’**Éditeur de requête** est utilisée dans une sous-sélection à l’intérieur des requêtes générées et envoyées afin d’extraire les données nécessaires pour un visuel. Par conséquent, la requête définie dans l’Éditeur de requête doit être valide dans ce contexte. Cela signifie en particulier qu’il n’est pas possible d’utiliser une requête avec des expressions de table communes ou qui appelle des procédures stockées.

### <a name="modeling-limitations"></a>Limitations de la modélisation
Le terme *modélisation* dans ce contexte signifie affiner et enrichir les données brutes dans le cadre de la création d’un rapport qui les utilise. Voici quelques exemples :

* définition de relations entre des tables ;
* ajout de calculs (colonnes calculées et mesures) ;
* changement de nom et masquage de colonnes et de mesures ;
* définition de hiérarchies ;
* définition de la mise en forme, de la synthèse par défaut et de l’ordre de tri pour une colonne ;
* regroupement ou clustering de valeurs.

Lorsque vous utilisez **DirectQuery**, bon nombre de ces enrichissements de modèle peuvent être apportés, et le principe subsiste certainement que les données brutes sont enrichies afin d’améliorer leur utilisation ultérieure. Or, certaines fonctionnalités de modélisation ne sont pas disponibles ou sont limitées lors de l’utilisation de DirectQuery. Les limitations sont généralement appliquées pour éviter des problèmes de performances. Les limitations communes à toutes les sources DirectQuery sont répertoriées dans la liste à puces ci-dessous. Des limitations supplémentaires peuvent s’appliquer à certaines sources, comme décrit dans la section *Détails spécifiques de source de données* vers la fin de cet article.

* **Aucune hiérarchie de dates intégrée :** par défaut, quand vous importez des données, une hiérarchie de dates intégrée est disponible pour chaque colonne de date/heure présente. Par exemple, lors de l’importation d’une table de commandes client incluant une colonne OrderDate, en cas d’utilisation d’OrderDate dans un visuel, il est possible de choisir le niveau approprié (Année, Mois, Jour) à utiliser. Cette hiérarchie de dates intégrée n’est pas disponible en cas d’utilisation du mode DirectQuery. Notez cependant que, si une table de dates est disponible dans la source sous-jacente (comme c’est le cas dans de nombreux entrepôts de données), les fonctions Time Intelligence de DAX peuvent être utilisées normalement.
* **Limitations dans les colonnes calculées :** les colonnes calculées doivent figurer à l’intérieur d’une ligne, car elles peuvent uniquement faire référence à des valeurs d’autres colonnes de la même table, sans possibilité d’utiliser des fonctions d’agrégation. De plus, les fonctions scalaires DAX (telles que LEFT()) autorisées se limitent à celles qui peuvent simplement être envoyées (push) à la source sous-jacente, de sorte qu’elles varient selon les capacités de la source. Les fonctions non prises en charge ne sont pas proposées dans la saisie semi-automatique lors de la création du DAX pour une colonne calculée, et leur utilisation entraînerait une erreur.
* **Aucune prise en charge des fonctions DAX parent-enfant :** le modèle DirectQuery ne permet pas d’utiliser la famille de fonctions DAX PATH(), qui servent généralement à gérer des structures parent-enfant (par exemple, un graphique de comptes ou des hiérarchies d’employés).
* **Limitations (par défaut) pour les mesures :** par défaut, les fonctions et expressions DAX qui peuvent être utilisées dans les mesures sont limitées. Là encore, la saisie semi-automatique limite les fonctions affichées, et une erreur se produit en cas d’utilisation d’une fonction ou d’une expression non valide. La raison à cela est simplement de s’assurer que, par défaut, les mesures sont limitées à des mesures simples peu susceptibles d’occasionner des problèmes de performances. Les utilisateurs avancés peuvent choisir de contourner cette limitation en sélectionnant successivement **Fichier > Options et paramètres > Options**, **DirectQuery**, puis l’option *Autoriser des mesures sans restriction en mode DirectQuery*. Quand cette option est sélectionnée, toute expression DAX valide pour une mesure est utilisable. Toutefois, les utilisateurs doivent savoir que certaines expressions qui fonctionnent bien lors de l’importation de données peuvent ralentir considérablement les requêtes adressées à la source principale en mode DirectQuery.
  
  * Par exemple, par défaut :
    
    * Il serait possible de créer une mesure qui additionne simplement le montant des ventes :
      
          SalesAmount = SUMX(Web_Sales, [ws_sales_price]* [ws_quantity])
    * Il ne serait *pas* possible de créer une mesure qui calculerait ensuite une moyenne de cette valeur SalesAmount sur tous les articles, par exemple :
      
          AverageItemSalesAmount = AVERAGEX('Item', [SalesAmount])
    
    La raison à cela est qu’une telle mesure risquerait d’entraîner une dégradation des performances s’il y avait un très grand nombre d’éléments.
* **Les tables calculées ne sont pas prises en charge :** la possibilité de définir une table calculée à l’aide d’une expression DAX n’est pas prise en charge en mode DirectQuery.
* **Le filtrage des relations est limité à une seule direction :** en cas d’utilisation de DirectQuery, il n’est pas possible de définir la direction du filtrage d’une relation sur « Les deux ». Par exemple, avec les trois tables ci-dessous, il ne serait pas possible de générer un visuel affichant le genre de chaque client (Customer[Gender]) et la catégorie de produits (Product[Category]) achetée par chaque genre. L’utilisation d’un tel filtrage bidirectionnel est décrite dans ce [livre blanc détaillé](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) (le document présente des exemples dans le contexte de SQL Server Analysis Services, mais les points principaux s’appliquent également à Power BI).
  
  ![](media/desktop-directquery-about/directquery-about_01.png)
  
  Une fois encore, la limitation est imposée en raison de l’impact possible sur les performances. Une application particulièrement importante de ce principe est que, lors de la définition d’une sécurité au niveau des lignes associée au rapport, étant donné qu’un schéma courant est d’avoir une relation plusieurs à plusieurs entre les utilisateurs et les entités auxquelles ils sont autorisés à accéder, et qu’un filtrage bidirectionnel est nécessaire pour appliquer cela. Toutefois, un filtrage bidirectionnel pour des modèles DirectQuery doit être utilisé judicieusement, en accordant une attention particulière à tout impact négatif sur les performances.  
* **Absence de clustering :** DirectQuery ne permet pas d’utiliser la fonctionnalité de clustering pour rechercher automatiquement les groupes

### <a name="reporting-limitations"></a>Limitations des rapports
Presque toutes les fonctionnalités de rapports sont prises en charge pour les modèles DirectQuery. Par conséquent, tant que la source sous-jacente offre un niveau de performances approprié, le même ensemble de visualisations peut être utilisé. Toutefois, il existe des limitations importantes de certaines des autres fonctionnalités offertes dans le **service Power BI** après la publication d’un rapport, comme décrit dans la liste à puces suivante :

* **Fonctionnalité Informations rapides non prise en charge :** cette fonction de Power BI effectue des recherches rapides dans différents sous-ensembles de votre jeu de données tout en appliquant un jeu d’algorithmes sophistiqués pour détecter les informations potentiellement intéressantes. Étant donné la nécessité de performances très élevées des requêtes, cette fonctionnalité n’est pas disponible sur des jeux de données en mode DirectQuery.
* **Fonctionnalité Questions et réponses non prise en charge :** la fonctionnalité Questions et réponses de Power BI vous permet d’explorer vos données à l’aide de fonctionnalités intuitives du langage naturel et de recevoir des réponses sous la forme de graphiques et de diagrammes. Toutefois, elle n’est actuellement pas prise en charge sur des jeux de données en mode DirectQuery.
* **L’exploration dans Excel risque d’entraîner une dégradation des performances :** vous pouvez explorer vos données en utilisant la fonctionnalité « Explorer dans Excel » sur un jeu de données. Cela permet la création de tableaux croisés dynamiques et de graphiques croisés dynamiques dans Excel. Lorsque cette fonctionnalité est prise en charge sur des jeux de données en mode DirectQuery, les performances sont généralement plus lentes que celles de la création de visuels dans Power BI. Par conséquent, si l’utilisation d’Excel est importante pour vos scénarios, vous devez en tenir compte avant de décider d’utiliser DirectQuery.

### <a name="security"></a>Sécurité
Comme indiqué plus haut dans cet article, un rapport utilisant **DirectQuery** utilise toujours les mêmes informations d’identification fixes pour se connecter à la source de données sous-jacente, après publication de celles-ci sur le **service Power BI**. Notez, une fois encore, que ceci a trait spécifiquement à DirectQuery, et non aux connexions actives à SQL Server Analysis Services qui diffèrent à cet égard. Par conséquent, immédiatement après la publication d’un rapport DirectQuery, il est nécessaire de configurer les informations d’identification de l’utilisateur qui seront utilisées. Tant que cela n’est pas fait, l’ouverture du rapport sur le service Power BI entraîne une erreur.

Une fois les informations d’identification fournies, celles-ci sont utilisées, *quel que soit l’utilisateur qui ouvre le rapport*. À cet égard, cela se passe exactement comme pour les données importées, en ce que chaque utilisateur voit les mêmes données, sauf si une sécurité au niveau des lignes a été définie et intégrée au rapport. Par conséquent, il convient d’accorder la même attention au partage du rapport si des règles de sécurité sont définies dans la source sous-jacente.

### <a name="behavior-in-the-power-bi-service"></a>Comportement dans le service Power BI
Cette section décrit le comportement d’un rapport **DirectQuery** dans le **service Power BI**, principalement pour pouvoir comprendre l’importance de la charge appliquée à la source de données principale, compte tenu du nombre d’utilisateurs avec lesquels le rapport et le tableau de bord sont partagés, de la complexité du rapport, et du fait qu’une sécurité au niveau des lignes a ou non été définie dans le rapport.

#### <a name="reports--opening-interacting-with-editing"></a>Rapports : ouverture, interaction, modification
Lors de l’ouverture d’un rapport, tous les visuels sur la page visible sont actualisés. Chaque visuel requiert généralement au moins une requête à la source de données sous-jacente. Certains visuels peuvent nécessiter plus d’une requête (par exemple, si le visuel affiche des valeurs agrégées de deux tables de faits différentes, ou contient une mesure plus complexe ou des totaux d’une mesure non additive telle que Count Distinct). Le déplacement vers une nouvelle page a pour effet d’actualiser ces visuels, entraînant l’envoi d’un nouvel ensemble de requêtes à la source sous-jacente.

Chaque interaction utilisateur sur le rapport peut entraîner une actualisation des visuels. Par exemple, la sélection d’une valeur différente sur un segment nécessite l’envoi d’un nouvel ensemble de requêtes pour actualiser tous les visuels concernés. C’est également vrai en cas de clic sur un visuel pour opérer une sélection croisée d’autres visuels, ou de modification d’un filtre.  

De même, bien entendu, la modification d’un nouveau rapport exige l’envoi de requêtes à chaque étape de la production du visuel final souhaité.

Étant donné que des résultats sont mis en cache, l’actualisation d’un visuel est instantanée si des résultats rigoureusement identiques ont été récemment obtenus. De tels caches ne sont pas partagés entre les utilisateurs si une sécurité au niveau des lignes est associée au rapport.

#### <a name="dashboard-refresh"></a>Actualisation du tableau de bord
Il est possible d’épingler au tableau de bord des visuels ou des pages entières sous forme de vignettes. Les vignettes basées sur des jeux de données **DirectQuery** sont ensuite actualisées automatiquement selon une planification, ce qui a pour effet que des requêtes sont envoyées à la source de données principale. Par défaut, cela se produit toutes les heures, mais cet intervalle peut être défini dans le cadre du paramétrage du jeu de données entre une fois par semaine et toutes les 15 minutes.

Si aucune sécurité au niveau des lignes n’est définie dans le modèle, chaque vignette n’est actualisée qu’une seule fois, et les résultats sont partagés entre tous les utilisateurs. Si une sécurité au niveau des lignes est définie, cela peut avoir un effet multiplicateur important, chaque vignette nécessitant que l’utilisateur envoie des requêtes distinctes à la source sous-jacente.  

Par conséquent, un tableau de bord comportant dix vignettes, partagé avec 100 utilisateurs, créé sur un jeu de données à l’aide de **DirectQuery** avec une sécurité au niveau des lignes, et configuré pour s’actualiser toutes les 15 minutes, entraîne l’envoi d’au moins 1 000 requêtes toutes les 15 minutes à la source principale.

Il convient donc d’être particulièrement attentif à l’utilisation de la sécurité au niveau des lignes ainsi qu’à la configuration de la planification de l’actualisation.

#### <a name="timeouts"></a>Délais d’expiration
Un délai d’expiration de quatre minutes est appliqué aux requêtes individuelles dans le **service Power BI** et les requêtes qui prennent plus de temps échouent. Comme souligné précédemment, il est recommandé d’utiliser DirectQuery pour les sources qui offrent des performances de requêtes pratiquement interactives. Cette limite vise donc à éviter les problèmes résultant de temps d’exécution trop longs.

### <a name="other-implications"></a>Autres implications
Voici d’autres conséquences générales de l’utilisation de **DirectQuery** :

* **Si les données évoluent, une actualisation est nécessaire pour que les données les plus récentes s’affichent :** compte tenu de l’utilisation de caches, il n’est pas garanti que le visuel affiche toujours les données les plus récentes. Par exemple, un visuel peut afficher les transactions du dernier jour. Ensuite, la modification d’un segment peut entraîner une actualisation afin d’afficher les transactions des deux derniers jours, dont certaines toutes récentes. Le rétablissement du segment à sa valeur d’origine se traduit par le fait qu’il affiche à nouveau la valeur mise en cache obtenue précédemment, ce qui n’inclut pas la nouvelle transaction vue précédemment.
  
  La sélection de l’option Actualiser a pour effet d’effacer tous les caches et d’actualiser tous les visuels sur la page afin d’afficher les données les plus récentes.
* **Si les données changent, il n’existe aucune garantie de cohérence entre les visuels :** des visuels différents, qu’ils figurent sur une même page ou sur des pages différentes, peuvent être actualisés à des moments différents. Par conséquent, si les données de la source sous-jacente changent, il n’existe aucune garantie que chaque visuel affiche des données correspondant précisément au même point dans le temps. En effet, étant donné que plusieurs requêtes sont parfois requises pour un seul visuel (par exemple, pour obtenir les détails et les totaux), la cohérence, y compris au sein d’un même visuel, n’est pas garantie. Garantir cela nécessiterait l’actualisation de tous les visuels chaque fois qu’un visuel est actualisé, ainsi que l’utilisation de fonctionnalités coûteuses telles que l’isolement de capture instantanée dans la source de données sous-jacente.
  
  Ce problème peut être atténué dans une large mesure en sélectionnant à nouveau la commande Actualiser, qui a pour effet de mettre à jour tous les visuels de la page. Et il faut noter que, même en utilisant le mode Importation, il existe un problème similaire de garantie de la cohérence en cas d’importation de données à partir de plusieurs tables.
* **Une actualisation dans Power BI Desktop est nécessaire pour refléter les modifications des métadonnées :** après la publication d’un rapport, l’actualisation a simplement pour effet de mettre à jour les visuels dans le rapport. Si le schéma de la source sous-jacente a changé, ces modifications ne sont pas automatiquement appliquées pour modifier les champs disponibles dans la liste de champs. Par conséquent, si des tables ou des colonnes ont été supprimées de la source sous-jacente, cela peut entraîner un échec de requête lors de l’actualisation. L’ouverture du rapport dans Power BI Desktop et le choix de la commande Actualiser ont pour effet de mettre à jour les champs dans le modèle pour refléter les modifications.
* **Limite d’un million de lignes retournées sur toute requête :** une limite fixe d’un million de lignes s’applique au nombre de lignes qui peuvent être retournées dans une requête adressée à la source sous-jacente. Cela n’a généralement pas de conséquences pratiques, et il est improbable que les visuels affichent autant de points. Toutefois, la limite peut être atteinte dans les cas où Power BI n’optimise pas entièrement les requêtes envoyées et si des résultats intermédiaires demandés dépassent la limite. Cela peut également se produire lors de la création d’un visuel, en cherchant à obtenir un état final plus raisonnable. Par exemple, à défaut d’application d’un filtre, l’inclusion de Customer et de TotalSalesQuantity entraîne le dépassement de cette limite s’il y a plus de 1 million de clients.
  
  L’erreur retournée serait : « Le jeu de résultats d’une requête sur une source de données externe a dépassé la taille maximale autorisée de « 1000000 » lignes. »
* **Impossible de passer du mode Importation au mode DirectQuery :** notez que, s’il est généralement possible de basculer un modèle du mode DirectQuery au mode Importation, cela signifie que toutes les données nécessaires doivent être importées. Il est également impossible de rebasculer dans l’autre sens (principalement en raison des fonctionnalités non prises en charge en mode DirectQuery). Les modèles DirectQuery sur des sources multidimensionnelles telles que SAP BW ne peuvent pas non plus être basculés du mode DirectQuery vers le mode Importation, en raison du traitement totalement différent des mesures externes.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery dans le service Power BI
Toutes les sources sont prises en charge à partir de **Power BI Desktop**. Certaines sources sont également accessibles directement à partir du **service Power BI**. Par exemple, il est possible qu’un utilisateur professionnel utilise Power BI pour se connecter à ses données dans Salesforce et obtienne immédiatement un tableau de bord, sans utiliser **Power BI Desktop**.

Seules deux des sources compatibles avec DirectQuery sont disponibles directement dans le service :

* Spark
* Azure SQL Data Warehouse

Toutefois, il est vivement recommandé que toute utilisation de **DirectQuery** sur ces deux sources commence dans **Power BI Desktop**. La raison à cela est que, lors de l’établissement initial de la connexion dans le **service Power BI**, de nombreuses limitations clés s’appliquent. Cela signifie que, si le point de départ est facile (à partir du service Power BI), il existe des limitations à l’amélioration du rapport obtenu (par exemple, il n’est pas possible ensuite de créer des calculs, d’utiliser de nombreuses fonctionnalités analytiques, voire d’actualiser les métadonnées pour refléter des modifications apportées au schéma sous-jacent).   

## <a name="guidance-for-using-directquery-successfully"></a>Aide pour une utilisation fructueuse de DirectQuery
Si vous prévoyez d’utiliser **DirectQuery**, cette section fournit une aide de haut niveau sur la façon de réussir. L’aide fournie dans cette section est dérivée des conséquences de l’utilisation de DirectQuery décrites dans cet article.

### <a name="backend-data-source-performance"></a>Performances de la source de données principale
Il est fortement recommandé de vérifier que les visuels simples peuvent s’actualiser dans un délai raisonnable. Pour bénéficier d’une expérience interactive raisonnable, ce délai ne doit pas dépasser 5 secondes. Il est évident que, si l’actualisation des visuels prend plus de 30 secondes, il est très probable que d’autres problèmes se produisent après la publication du rapport, ce qui rend la solution impraticable.

Si les requêtes sont lentes, la première chose à faire consiste à examiner les requêtes envoyées à la source sous-jacente et la cause des problèmes de performances des requêtes observées. Cette rubrique ne couvre pas toute la gamme des meilleures pratiques d’optimisation de base de données sur l’ensemble complet des sources sous-jacentes potentielles, mais s’applique aux pratiques standard en matière de bases de données, qui s’appliquent à la plupart des situations :

* Les relations basées sur des colonnes d’entiers sont généralement plus performantes que les jointures de colonnes dont les types de données diffèrent
* Les index appropriés doivent être créés. Cela implique généralement d’utiliser des index de stockage en colonne dans les sources qui les prennent en charge (par exemple, SQL Server).
* Toutes les statistiques nécessaires dans la source doivent être mises à jour

### <a name="model-design-guidance"></a>Aide à la conception d’un modèle
Lorsque vous définissez le modèle, considérez ce qui suit :

* **Évitez les requêtes complexes dans l’Éditeur de requête.** La requête définie dans l’Éditeur de requête est convertie en une requête SQL unique, qui est ensuite incluse dans la sous-sélection de chaque requête envoyée à cette table. Si cette requête est complexe, elle peut entraîner des problèmes de performances à chaque requête envoyée. La requête SQL réelle pour un ensemble d’étapes peut être obtenue en sélectionnant la dernière étape dans l’Éditeur de requête, puis en choisissant *Afficher la requête native* dans le menu contextuel.
* **Veillez à utiliser des mesures simples.** Au départ, il est recommandé de limiter les mesures à des agrégats simples. Ensuite, si celles-ci offrent des performances satisfaisantes, vous pouvez définir des mesures plus complexes, en restant attentif aux performances de chacune d’elles.
* **Évitez les relations sur des colonnes calculées.** Cela s’applique en particulier aux bases de données où il est nécessaire d’effectuer des jointures de plusieurs colonnes. Actuellement, Power BI ne permet pas qu’une relation soit basée sur plusieurs colonnes, comme la relation FK/PK. La solution de contournement courante consiste à concaténer les colonnes à l’aide d’une colonne calculée et à baser la jointure sur cela. Si cette solution de contournement est raisonnable pour des données importées, en cas d’utilisation de **DirectQuery**, elle aboutit à une jointure sur une expression, qui, le plus souvent, empêche d’utiliser des index et entraîne une dégradation des performances. La seule solution de contournement consiste à matérialiser réellement les colonnes multiples dans une colonne unique de la base de données sous-jacente.
* **Évitez les relations sur des colonnes uniqueidentifier.** Power BI ne prend pas en charge en mode natif un type de données uniqueidentifier. Par conséquent, la définition d’une relation entre des colonnes de type uniqueidentifier entraîne une requête avec une jointure impliquant un Cast. Là encore, cela aboutit généralement à une dégradation des performances. Tant que ce cas n’est pas spécifiquement optimisé, la seule solution de contournement consiste à matérialiser des colonnes d’un autre type dans la base de données sous-jacente.
* **Masquez la colonne *à* sur les relations.** La colonne *à* sur des relations (généralement la clé primaire sur la table *à*) doit être masquée, de façon à ce qu’elle n’apparaisse pas dans la liste de champs et ne puisse pas être utilisée dans des visuels. Souvent, les colonnes sur lesquelles reposent des relations sont en fait des *colonnes système* (par exemple, des clés de substitution dans un entrepôt de données) et le masquage de colonnes de ce type est conseillé en toute occurrence. Si la colonne a du sens, introduisez une colonne calculée visible, comportant une expression simple d’égalité avec la clé primaire. Par exemple :
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  La raison de procéder de la sorte est simplement d’éviter qu’un problème se produise si un visuel inclut la colonne de clé primaire.
* **Examinez l’ensemble des utilisations de colonnes calculées et modifications de type de données.** L’utilisation de ces fonctionnalités n’est pas nécessairement nuisible. Elle entraîne l’envoi à la source sous-jacente de requêtes contenant des expressions plutôt que de simples références à des colonnes, qui pourraient à leur tour aboutir à une non-utilisation des index.  
* **Évitez d’utiliser le filtrage croisé bidirectionnel (en préversion) sur des relations.**
* **Expérimentez le paramètre d’*Intégrité référentielle supposée*.** Le paramètre d’*Intégrité référentielle supposée* appliqué à des relations permet que des requêtes utilisent des instructions de jointure interne plutôt que de jointure externe. Il améliore généralement les performances de requête, bien qu’il dépende des spécificités de la source de données.
* **N’utilisez pas de filtrage de date relative dans l’Éditeur de requête.** L’Éditeur de requête permet de définir un filtrage de date relative. Par exemple, pour filtrer les lignes où la date se situe dans les 14 derniers jours.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  Toutefois, ce filtrage est converti en un filtre basé sur la date fixe, comme au moment de la création de la requête. Cela peut être observé dans l’affichage de la requête native.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Ce n’est très probablement pas le résultat souhaité. Pour vous assurer que le filtre est appliqué en fonction de la date d’exécution du rapport, appliquez plutôt le filtre dans le rapport en tant que Filtre de rapport. Cela se fait actuellement en créant une colonne calculée calculant le nombre de jours passés (en utilisant la fonction DAX DATE()), puis en utilisant cette colonne calculée dans un filtre.

### <a name="report-design-guidance"></a>Aide à la conception d’un rapport
Lorsque vous créez un rapport à l’aide d’une connexion DirectQuery, suivez les instructions suivantes :

* **Envisagez d’utiliser les options de réduction des requêtes :** Power BI propose des options de rapport permettant d’envoyer moins de requêtes et de désactiver certaines interactions qui aboutiraient à une mauvaise expérience dans le cas où les requêtes résultantes mettent longtemps à s’exécuter. Pour accéder à ces options dans **Power BI Desktop**, cliquez sur **Fichier > Options et paramètres > Options** et sélectionnez **Réduction des requêtes**. 

   ![](media/desktop-directquery-about/directquery-about_03b.png)

    Cochez la case **Réduction des requêtes** pour désactiver la mise en surbrillance croisée sur l’ensemble du rapport. Vous pouvez également afficher un bouton *Appliquer* sur les segments ou sur les sélections de filtres, ce qui vous permet d’en sélectionner plusieurs avant de les appliquer : aucune requête n’est envoyée tant que le bouton **Appliquer**  n’est pas sélectionné sur le segment. Vos sélections peuvent ensuite être utilisées pour filtrer les données.

    Ces options s’appliqueront au rapport lorsque vous interagirez avec dans **Power BI Desktop** et lorsque vos utilisateurs l’utiliseront dans le **Service Power BI**.

* **Appliquer d’abord des filtres :** appliquez toujours les filtres applicables au début de la création d’un visuel. Par exemple, au lieu de faire glisser vers TotalSalesAmount et ProductName, puis de filtrer sur une année en particulier, appliquez le filtre à Année dès le début. Cela est dû au fait que chaque étape de création d’un visuel entraîne l’envoi d’une requête et bien qu’il soit possible d’apporter une autre modification avant l’accomplissement de la première requête, cela laisse toujours peser une charge inutile sur la source sous-jacente. L’application précoce de filtres rend généralement ces requêtes intermédiaires moins coûteuses. En revanche, la non-application précoce de filtres peut amener à atteindre la limite de 1 million de lignes évoquée ci-dessus.
* **Limitez le nombre de visuels sur une page :** lors de l’ouverture d’une page (ou bien d’un segment ou filtre modifié au niveau page), tous les visuels sur la page sont actualisés. Il existe également une limite au nombre de requêtes qui sont envoyées en parallèle. Par conséquent, à mesure que le nombre de visuels augmente, certains d’entre eux sont actualisés de façon séquentielle, ce qui augmente le temps nécessaire pour l’actualisation de la page entière. C’est pourquoi il est recommandé de limiter le nombre de visuels sur une même page, et d’avoir plutôt un nombre plus important de pages plus simples.
* **Envisagez de désactiver l’interaction entre les visuels :** par défaut, vous pouvez utiliser les visualisations d’une page de rapport pour effectuer un filtrage croisé et une sélection croisée des autres visualisations figurant sur la page. Par exemple, après que vous avez sélectionné « 1999 » sur le graphique en secteurs, l’histogramme est sélectionné de façon croisée pour afficher les ventes par catégorie pour l’année « 1999 ».                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  Dans DirectQuery, le filtrage et la mise en surbrillance croisés impliquent l’envoi de requêtes à la source sous-jacente ; l’interaction doit donc être désactivée si le temps nécessaire pour répondre aux sélections des utilisateurs devient excessivement long. La désactivation est possible soit pour l’intégralité du rapport (cf. la section *Options de réduction des requêtes* ci-dessus) soit au cas par cas comme le décrit [cet article](consumer/end-user-interactions.md).

En plus de la liste de suggestions ci-dessus, notez que chacune des fonctions de création de rapports suivantes peut entraîner des problèmes de performances :

* **Filtres de mesures :** les visuels comprenant des mesures (ou des agrégats de colonnes) peuvent également contenir des filtres dans ces mesures. Par exemple, le visuel ci-dessous affiche SalesAmount by Category, mais inclut uniquement les catégories avec plus de 20 millions de ventes.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Il en résulte l’envoi de deux requêtes à la source sous-jacente :
  
  * La première requête récupère les catégories correspondant à la condition de nombre de ventes supérieur à 20 millions.
  * La deuxième requête récupère ensuite les données nécessaires pour le visuel, notamment les catégories qui respectent la condition dans la clause WHERE.  
  
  Cela fonctionne généralement bien s’il existe des centaines, voire des milliers de catégories, comme dans cet exemple. Les performances peuvent se dégrader si le nombre de catégories est beaucoup plus élevé (en effet, la requête échoue s’il y a plus d’un million de catégories remplissant la condition, en raison de la limite d’un million de lignes évoquée précédemment).
* **Filtres TopN :** des filtres avancés peuvent être définis pour filtrer les N valeurs supérieures (ou inférieures) classées selon une mesure, par exemple pour inclure uniquement les 10 premières catégories du visuel ci-dessus. Cela entraîne une nouvelle fois l’envoi de deux requêtes à la source sous-jacente. Toutefois, la première requête retourne toutes les catégories de la source sous-jacente, puis les catégories TopN sont déterminées sur la base des résultats retournés. Selon la cardinalité de la colonne impliquée, cela peut entraîner des problèmes de performances (ou des échecs de requête en raison de la limite de 1 million de lignes).
* **Médiane :** en règle générale, toute agrégation (Somme, Count Distinct, etc.) est envoyée à la source sous-jacente. Toutefois, cela n’est pas vrai pour la valeur Médiane, car cet agrégat n’est généralement pas pris en charge par la source sous-jacente. Dans ce cas, les données détaillées sont extraites de la source sous-jacente, et la valeur Médiane calculée à partir des résultats retournés. Cela est raisonnable lorsque la valeur Médiane doit être calculée sur la base d’un nombre relativement restreint de résultats, mais des problèmes de performances (ou des échecs de requêtes en raison de la limite de 1 million de lignes) se produisent si la cardinalité est importante.  Par exemple, une valeur médiane de population d’un pays pourrait être raisonnable, tandis qu’une valeur médiane de prix de vente pourrait ne pas l’être.
* **Filtres de texte avancés (« contient » et autres) :** lors d’un filtrage sur une colonne de texte, un filtrage avancé permet d’utiliser des filtres tels que « contient », « commence par », etc. Ces filtres peuvent certainement entraîner une dégradation des performances pour certaines sources de données. En particulier, le filtre par défaut « contient » ne doit pas être utilisé en cas de recherche d’une correspondance exacte (« est » ou « n’est pas »). Si les résultats peuvent être identiques, en fonction des données réelles, les performances peuvent être considérablement différentes en raison de l’utilisation d’index.
* **Multisélection de segments :** par défaut, les segments n’autorisent qu’une seule sélection. L’autorisation d’une multisélection dans les filtres peut entraîner des problèmes de performances car, lorsque l’utilisateur sélectionne un ensemble d’éléments dans le segment (par exemple, les dix produits qui l’intéressent), chaque nouvelle sélection entraîne l’envoi de requêtes à la source principale. Bien que l’utilisateur puisse sélectionner l’élément suivant avant la fin de requête, cela entraîne une charge supplémentaire sur la source sous-jacente.

* **Envisagez de désactivez les totaux sur les visuels :** par défaut, les tables et les matrices affichent les totaux et les sous-totaux. Dans de nombreux cas, il faut envoyer des requêtes distinctes à la source sous-jacente pour obtenir les valeurs de ces totaux. Cela s’applique à chaque fois que l’agrégation *DistinctCount* est utilisée, de même que DirectQuery sur SAP BW ou SAP HANA. Ces totaux doivent être désactivés (à l’aide du volet **Format**) s’ils ne sont pas nécessaires. 

### <a name="diagnosing-performance-issues"></a>Diagnostic des problèmes de performances
Cette section décrit comment diagnostiquer des problèmes de performances ou obtenir des informations plus détaillées pour permettre l’optimisation des rapports.

Il est vivement recommandé de débuter un diagnostic de problèmes de performances dans **Power BI Desktop**, plutôt que dans le **service Power BI**. Les problèmes de performances résultent souvent simplement du niveau de performances de la source sous-jacente. Il est plus facile de les identifier et diagnostiquer au sein de l’environnement sensiblement plus isolé de **Power BI Desktop**. Par ailleurs, cela élimine d’emblée certains composants (par exemple, Power BI Gateway). Si Power BI Desktop ne permet pas d’identifier les problèmes de performances, l’investigation doit se concentrer sur les caractéristiques du rapport dans le service Power BI.

De même, il est recommandé de commencer par tenter d’isoler les problèmes d’un visuel spécifique, plutôt que d’examiner un grand nombre de visuels figurant sur une page.

Imaginons que ces étapes (décrites dans les paragraphes précédents de cette section) ont été effectuées : nous avons isolé un visuel sur une page dans **Power BI Desktop** qui reste lent. Pour déterminer les requêtes que Power BI Desktop envoie à la source sous-jacente, il est possible d’afficher des informations de trace/diagnostic susceptibles d’être émises par cette source. Ces traces peuvent également contenir des informations utiles contenant des détails sur la façon dont la requête a été exécutée, et la manière d’améliorer celle-ci.

De plus, même en l’absence de telles traces de la source, il est possible d’afficher les requêtes émises par Power BI, ainsi que leurs durées d’exécution, comme décrit ci-après.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Détermination des requêtes émises par Power BI Desktop
Par défaut, **Power BI Desktop** journalise les événements survenant au cours d’une session donnée dans un fichier de trace nommé FlightRecorderCurrent.trc.

Pour certaines sources **DirectQuery**, ce fichier journal contient toutes les requêtes envoyées à la source de données sous-jacente (les autres sources DirectQuery seront incluses dans le futur). Les sources qui envoient des requêtes au journal sont les suivantes :

* SQL Server
* Azure SQL Database
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

Le fichier de trace figure dans le dossier **AppData** de l’utilisateur actuel :

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Voici comment accéder facilement à ce dossier : dans **Power BI Desktop** sélectionnez **Fichier > Options et paramètres > Options**, puis **Diagnostics**. La boîte de dialogue suivante s’affiche :

![](media/desktop-directquery-about/directquery-about_06.png)

Lorsque vous sélectionnez le lien *Ouvrir le dossier des traces* sous **Options de diagnostic**, le dossier suivant s’ouvre :

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

En accédant au dossier parent de ce dossier, vous pouvez voir le dossier contenant *AnalysisServicesWorkspaces*, qui contient un sous-dossier d’espace de travail pour chaque instance ouverte de **Power BI Desktop**. Les noms de ces sous-dossiers ont un nombre entier en suffixe, par exemple *AnalysisServicesWorkspace2058279583*.

Ce dossier comprend un sous-dossier *\\Data* qui contient le fichier de trace FlightRecorderCurrent.trc pour la session Power BI active. Le dossier d’espace de travail correspondant est supprimé à l’issue de la session Power BI Desktop associée.

Vous pouvez lire les fichiers de trace à l’aide de l’outil **SQL Server Profiler**, disponible en téléchargement gratuit avec **SQL Server Management Studio**. Vous pouvez y accéder [ici](https://msdn.microsoft.com/library/mt238290.aspx).

Une fois que vous avez téléchargé et installé **SQL Server Management Studio**, exécutez **SQL Server Profiler**.

![](media/desktop-directquery-about/directquery-about_07.png)

Pour ouvrir le fichier de trace, procédez comme suit :

1. Dans **SQL Server Profiler**, sélectionnez **Fichier > Ouvrir > Fichier de trace**.
2. Entrez le chemin d’accès du fichier de trace pour la session Power BI actuellement ouverte, par exemple :
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Open FilghtRecorderCurrent.trc

Tous les événements de la session en cours sont affichés. Un exemple annoté est présenté ci-dessous, qui met en évidence les groupes d’événements. Chaque groupe comporte les éléments suivants :

* Des événements *Query Begin* (Début de la requête) et *Query End* (Fin de la requête) qui représentent le début et la fin d’une requête DAX générée par l’interface utilisateur (par exemple, à partir d’un visuel ou du remplissage d’une liste de valeurs dans l’interface utilisateur de filtre).
* Une ou plusieurs paires d’événements *DirectQuery Begin* (Début de DirectQuery) et *DirectQuery End* (Fin de DirectQuery), qui représentent une requête envoyée à la source de données sous-jacente, dans le cadre de l’évaluation de la requête DAX.

Notez que plusieurs requêtes DAX pouvant être exécutées en parallèle, les événements de différents groupes peuvent être entrelacés. La valeur d’ID d’activité permet de déterminer les événements qui appartiennent à un même groupe.

![](media/desktop-directquery-about/directquery-about_08.png)

Les autres colonnes dignes d’intérêt sont les suivantes :

* **TextData :** détail textuel de l’événement. Pour les événements « Query Begin/Query End », il s’agit de la requête DAX. Pour les événements « DirectQuery Begin/DirectQuery End », il s’agit de la requête SQL envoyée à la source sous-jacente. Les données TextData pour l’événement sélectionné s’affichent également dans la zone inférieure.
* **EndTime :** heure de fin de l’événement.
* **Duration :** durée d’exécution de la requête DAX ou SQL, exprimée en millisecondes.
* **Error :** indique si une erreur s’est produite (auquel cas l’événement s’affiche également en rouge).

Notez que, dans l’image ci-dessus, certaines colonnes moins intéressantes ont été rétrécies pour faciliter la visualisation des colonnes intéressantes.

L’approche recommandée pour la capture d’une trace afin de diagnostiquer un problème de performances potentiel est la suivante :

* Ouvrez une seule session **Power BI Desktop** (pour éviter la confusion de plusieurs dossiers d’espace de travail).
* Effectuez l’ensemble des actions intéressantes dans **Power BI Desktop**. Incluez ensuite quelques actions supplémentaires pour vous assurer que les événements intéressants sont vidés dans le fichier de trace.
* Ouvrez **SQL Server Profiler**, puis examinez la trace, comme décrit précédemment. Souvenez-vous que le fichier de trace est supprimé à la fermeture de **Power BI Desktop**. Par ailleurs, les actions supplémentaires effectuées dans Power BI Desktop n’apparaissent pas immédiatement : le fichier de trace doit être fermé et rouvert pour voir les nouveaux événements.
* Conservez des sessions individuelles relativement peu volumineuses (dix secondes d’actions, pas des centaines) pour faciliter l’interprétation du fichier de trace (et la taille du fichier de trace étant limitée, pour les sessions très longues il se peut que des événements du début soient supprimés).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Compréhension de la forme d’une requête envoyée par Power BI Desktop
Le format général des requêtes créées et envoyées par **Power BI Desktop** utilise des sous-sélections pour chacune des tables référencées, où la sous-sélection est définie par la requête définie dans l’**Éditeur de requête**. Par exemple, imaginez les tables TPC-DS suivantes dans SQL Server :

![](media/desktop-directquery-about/directquery-about_09.png)

Considérez la requête suivante :

![](media/desktop-directquery-about/directquery-about_10.png)

Cette requête renvoie le visuel suivant :

![](media/desktop-directquery-about/directquery-about_11.png)

L’actualisation de ce visuel génère la requête SQL présentée sous le paragraphe suivant. Comme vous pouvez le voir, il y a trois sous-sélections (Web Sales, Item et Date_dim), qui retournent chacune toutes les colonnes de la table correspondante, même si le visuel ne fait réellement référence qu’à quatre colonnes. Ces requêtes dans les sous-sélections (grisées) sont le résultat précis des requêtes définies dans l’**Éditeur de requête**. L’utilisation de sous-sélections de cette manière semble ne pas avoir d’incidence sur les performances en ce qui concerne les sources de données prises en charge jusqu'à présent pour DirectQuery. Des sources de données telles que SQL Server optimisent simplement les références aux autres colonnes.

L’une des raisons pour lesquelles Power BI utilise ce modèle est que la requête SQL utilisée peut être fournie directement par l’analyste, et exécutée telle quelle, sans nécessité de la réécrire.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Étapes suivantes
Cet article décrit les aspects de **DirectQuery** communs à toutes les sources de données. Certains détails sont propres à des sources spécifiques. Consultez les rubriques suivantes concernant les sources spécifiques :

* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)

Pour plus d’informations sur **DirectQuery**, consultez les ressources suivantes :

* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)

