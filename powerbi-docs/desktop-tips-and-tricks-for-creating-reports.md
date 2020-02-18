---
title: Conseils et astuces pour créer des rapports dans Power BI
description: Découvrez les meilleures pratiques pour la création de rapports dans le service Power BI et Power BI Desktop
author: davidiseminger
ms.reviewer: willthom
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
ms.openlocfilehash: a6d949f95f463cb988958551d825a4eae824fb70
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2020
ms.locfileid: "73865841"
---
# <a name="tips-and-tricks-for-creating-reports-in-power-bi-desktop"></a>Conseils et astuces pour créer des rapports dans Power BI Desktop
Que diriez-vous d’un petit coup de pouce pour vous aider à tirer le meilleur parti de vos données ? Cette page recense des trucs et astuces qui pourront vous être utiles lors de la création de rapports dans Microsoft Power BI Desktop *et* dans Microsoft Excel 2016 ou 2013 Professionnel Plus (après activation du complément Power Pivot et installation et activation de Power Query). 

## <a name="learning-to-use-the-query-editor"></a>Prise en main de l’Éditeur de requête
En termes de fonctionnalités, l’Éditeur de requête dans Power BI Desktop est semblable au complément Power Query dans Excel 2013. Même si les pages du support technique de Power BI comptent de nombreux articles utiles, vous pouvez également passer en revue la documentation de Power Query sur support.office.com en guise d’introduction.

Vous pouvez obtenir des informations supplémentaires à partir du [Centre de ressources Power Query](https://support.office.com/article/Microsoft-Power-Query-for-Excel-Help-2b433a85-ddfb-420b-9cda-fe0e60b82a94).

Vous pouvez également afficher la [référence de formule](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

## <a name="data-types-in-query-editor"></a>Types de données dans l’Éditeur de requête
Quand vous utilisez l’Éditeur de requête dans Power BI Desktop pour charger des données, celui-ci détecte le type de données sur la base de la meilleure hypothèse. Si vous utilisez des formules, les paramètres de type de données affectés aux colonnes ne sont parfois pas conservés. Vérifiez que le type de données des colonnes est correct après avoir effectué les opérations suivantes :  Charger des données (chargement initial dans l’onglet Requête), Utiliser la première ligne comme en-tête, Ajouter une colonne, Regrouper par, Fusionner et Ajouter, mais aussi avant d’appuyer sur le bouton de chargement des données pour la première fois.

Souvenez-vous de ce point important : le texte en italique dans la grille de données ne signifie pas que le type de données est correctement défini. Cela veut simplement dire que les données ne sont pas considérées comme du texte.

## <a name="reference-queries-in-the-query-editor"></a>Requêtes de référence dans l’Éditeur de requête
Dans le navigateur de l’Éditeur de requête de Power BI Desktop, quand vous cliquez avec le bouton droit sur une des requêtes, une option « Référence » est disponible. Cela est utile pour la raison suivante :

* Quand vous utilisez des fichiers comme source de données d’une requête, le chemin d’accès absolu au fichier est stocké dans la requête. Cela vous permet de gagner du temps lors du partage ou du déplacement d’un fichier Power BI Desktop ou d’un classeur Excel, car il vous suffit de mettre à jour le chemin d’accès une seule fois.

Par défaut, toutes les requêtes chargent une feuille de calcul Excel ou le modèle de données (ou les deux). Certaines requêtes sont des étapes intermédiaires qui ne sont pas destinées aux utilisateurs. Quand vous référencez des requêtes comme indiqué ci-dessus, cela arrive fréquemment. Vous pouvez contrôler le comportement du chargement en cliquant avec le bouton droit sur la requête dans le navigateur et en activant ou en désactivant l’option « Activer le chargement ». Si l’option *Activer le chargement* n’est pas cochée, la requête est toujours disponible sous l’onglet Requête et vous pouvez l’utiliser avec d’autres requêtes. Cela est particulièrement utile si vous utilisez conjointement des transformations Fusionner, Ajouter et Référence. Toutefois, étant donné que les résultats de la requête ne sont pas chargés dans le modèle de données, la requête n’encombre pas la liste des champs de vos rapports ni votre modèle de données. 

## <a name="scatter-charts-need-a-point-identifier"></a>Nécessité d’un identificateur de point dans les nuages de points
Prenons un exemple simple d’une table contenant des températures et les heures de mesure. Si vous tracez ces données directement sur un nuage de points, Power BI regroupe toutes les valeurs en un seul point. Pour afficher les points de données individuels, vous devez ajouter un champ dans le compartiment Détails de la zone des champs. Pour ce faire dans Power BI Desktop, un moyen simple consiste à utiliser l’option « Ajouter une colonne d’index » sous l’onglet Requête dans le ruban « Ajouter une colonne ». 

## <a name="reference-lines-in-your-report"></a>Lignes de référence dans votre rapport
Vous pouvez utiliser une colonne calculée dans Power BI Desktop pour définir une ligne de référence. Identifiez la table et la colonne à utiliser pour créer une ligne de référence. Sélectionnez « Nouvelle colonne » dans le ruban, puis tapez la formule suivante dans la barre de formule :

    Target Value = 100

Cette colonne calculée retourne la valeur 100, quel que soit l’emplacement où elle est utilisée. Votre nouvelle colonne s’affiche dans la liste des champs. Ajoutez la colonne calculée Valeur cible à un graphique en courbes pour afficher le lien entre une série quelconque et cette ligne de référence spécifique. 

## <a name="sort-by-another-column"></a>Tri par une autre colonne
Quand vous utilisez une valeur catégorique (chaîne) dans Power BI pour les axes du graphique ou dans un segment ou un filtre, l’ordre par défaut est l’ordre alphabétique. Pour modifier cet ordre, par exemple si vous avez affaire à des éléments comme des jours de la semaine ou des mois, vous pouvez indiquer à Power BI Desktop de trier les valeurs selon une autre colonne. Pour en savoir plus, consultez [Trier par colonne dans Power BI Desktop](desktop-sort-by-column.md).

## <a name="building-maps-more-easily-with-hints-to-bing"></a>Création simplifiée de cartes grâce aux indications fournies à Bing
De par son intégration à Bing, Power BI fournit des coordonnées cartographiques par défaut (processus appelé « géocodage »), ce qui facilite la création de cartes. Bing utilise des algorithmes et des indications pour essayer d’obtenir le bon emplacement, mais il ne s’agit que d’une hypothèse. Pour augmenter vos chances d’obtenir un géocodage correct, vous pouvez utiliser les conseils suivants :

Quand vous créez une carte, vous cherchez souvent à tracer des pays, des États et des villes. Dans Power BI Desktop, si vous nommez des colonnes après la désignation géographique, Bing sera plus à même de deviner ce que vous souhaitez afficher. Par exemple, si vous avez un champ contenant des états américains comme « Californie » et « Washington », Bing peut retourner l’emplacement de la ville de Washington, DC et non celui de l’État de Washington pour le mot « Washington ». Vous pouvez nommer la colonne « État » pour améliorer le géocodage. Il en va de même pour les colonnes nommées « Pays » et « Ville ». 

Certaines désignations sont ambiguës lorsqu’elles sont envisagées dans le contexte de plusieurs pays ou régions. Dans certains cas, ce qu’un pays ou une région considère comme un « état » peut être traité comme une « province », un « département » ou une autre désignation. Pour augmenter la précision du géocodage, créez des colonnes qui regroupent plusieurs champs et utilisez-les pour tracer les emplacements de vos données. Par exemple, au lieu de passer uniquement « Wiltshire », vous pouvez passer « Wiltshire, Grande-Bretagne » pour obtenir un résultat de géocodage plus précis. 

Vous pouvez toujours fournir des emplacements spécifiques basés sur la latitude et la longitude dans le service Power BI ou Desktop. Si vous procédez de la sorte, vous devez également passer un champ Emplacement ; sinon, les données sont agrégées par défaut, et l’emplacement défini par la latitude et la longitude peut ne pas correspondre à celui que vous attendiez.

## <a name="categorizing-geographic-fields-to-hint-bings-geocoding"></a>Catégorisation des champs géographiques pour fournir des indications à Bing dans le cadre du géocodage
Vous pouvez également vous assurer que les champs sont correctement géocodés en définissant la Catégorie de données sur les champs de données. Dans Power BI Desktop, sélectionnez la table souhaitée, accédez au ruban d’options avancées, puis spécifiez Adresse, Ville, Continent, Région, Pays, Code Postal, État ou Province comme Catégorie de données. Ces catégories de données aident Bing à encoder correctement les données. Pour plus d’informations, consultez [Catégorisation des données dans Power BI Desktop](desktop-data-categorization.md).

## <a name="better-geocoding-with-more-specific-locations"></a>Amélioration du géocodage grâce à des emplacements plus spécifiques
Parfois, même la définition des catégories de données pour le mappage ne suffit pas. Générez un emplacement plus spécifique, une rue par exemple, à l’aide de l’Éditeur de requête dans Power BI Desktop. Utilisez la fonctionnalité Ajouter une colonne pour créer une colonne personnalisée. Puis créez l’emplacement souhaité comme suit : 

    = [Field1] & " " & [Field2]

Utilisez ensuite ce champ résultant dans les visualisations de carte. Cette approche est très utile pour générer des rues à partir des champs « Adresse d’expédition » qui sont couramment employés dans les jeux de données. Sachez toutefois que la concaténation ne fonctionne qu’avec des champs de texte. Si nécessaire, convertissez le numéro de rue en type de données Texte avant de vous en servir pour générer une adresse.

## <a name="histograms-in-the-query-stage"></a>Histogrammes dans l’étape de requête
Vous pouvez générer des histogrammes de plusieurs façons dans Power BI Desktop. Commençons par la plus simple :

Histogrammes simples : identifiez la requête contenant le champ à utiliser pour créer un histogramme. Utilisez l’option « Référence » de la requête pour créer une requête et nommez-la « FieldName Histogram ». Utilisez l’option « Regrouper par » dans le ruban « Transformer » et sélectionnez l’agrégation « Compter les lignes ». Vérifiez que le type de données de la colonne d’agrégation résultante est un nombre. Visualisez ensuite ces données dans la page des rapports. Cette méthode est rapide et facile, mais elle n’est pas très adaptée si vous avez plusieurs points de données. Par ailleurs, elle n’autorise pas le balayage d’éléments visuels.

Définition de compartiments pour créer un histogramme : identifiez la requête contenant le champ à utiliser pour créer un histogramme. Utilisez l’option « Référence » de la requête pour créer une requête et nommez-la « FieldName ». À présent, définissez les compartiments au moyen d’une règle. Utilisez l’option Ajouter une colonne personnalisée du ruban Ajouter une colonne et créez une règle personnalisée. Voici un exemple d’une règle simple de création de compartiments :

    if([FieldName] \< 2) then "\<2 min" else
    if([FieldName] \< 5) then "\<5 min" else
    if([FieldName] \< 10) then "\<10 min" else
    if([FieldName] \< 30) then "\<30 min" else
    "longer")

Vérifiez que le type de données de la colonne d’agrégation résultante est un nombre. Vous pouvez maintenant utiliser le groupe à l’aide de la technique décrite dans « Histogramme simple » pour générer l’histogramme. Cette option permet de traiter plus de points de données, mais elle ne prend toujours pas en charge le balayage.

Définition d’un histogramme prenant en charge le balayage : si des visuels sont liés entre eux et qu’un utilisateur sélectionne un point de données dans un visuel, les autres visuels de la page de rapport mettent en surbrillance ou filtrent les points de données liés à celui sélectionné. C’est ce que l’on entend par « balayage ». Étant donné que nous manipulons les données au moment de la requête, nous devons créer une relation entre les tables et déterminer l’élément de détail qui est lié au compartiment dans l’histogramme et vice-versa.

Pour démarrer le processus, identifiez la requête contenant le champ à utiliser pour créer un histogramme, puis sélectionnez l’option « Référence ». Nommez la nouvelle requête « Buckets ». Dans cet exemple, nous allons appeler la requête d’origine « Details ». Ensuite, supprimez toutes les colonnes à l’exception de celle que vous allez utiliser comme compartiment pour l’histogramme. Maintenant, cliquez avec le bouton droit sur la colonne et sélectionnez « Supprimer les doublons » pour faire en sorte que les valeurs restantes soient uniques dans la colonne. Si vos données comportent des nombres décimaux, vous pouvez tout d’abord suivre la procédure « Définition de compartiments pour créer un histogramme » afin d’obtenir un ensemble gérable de compartiments. Examinez à présent les données affichées dans l’aperçu de la requête. Si vous voyez des valeurs vides ou null, vous devez les corriger avant de créer une relation. Consultez la section « Création de relations si les données comprennent des valeurs null ou vides ». Cette approche peut être problématique, car elle nécessite que les données soient triées. Pour que les compartiments trient correctement les données, consultez « Ordre de tri : faire apparaître les catégories dans l’ordre souhaité ». 

>[!NOTE]
>Il est utile de réfléchir à l’ordre de tri avant de générer des visuels. 

L’étape suivante du processus consiste à définir une relation entre les requêtes « Buckets » et « Details » dans la colonne des compartiments. Dans le ruban de Power BI Desktop, cliquez sur **Gérer les relations**. Créez une relation dans laquelle « Buckets » est dans la table de gauche et « Details » dans la table de droite, puis sélectionnez le champ que vous utilisez pour l’histogramme. 

La dernière étape consiste à créer l’histogramme. Faites glisser le champ Bucket à partir de la table « Buckets ». Supprimez le champ par défaut de l’histogramme résultant. Maintenant, à partir de la table « Details », faites glisser le champ de l’histogramme dans le même élément visuel. Dans la zone des champs, spécifiez l’agrégation par défaut Nombre. L’histogramme est généré. Si vous créez un autre élément visuel comme un Treemap à partir de la table Details, sélectionnez un point de données dans Treemap pour mettre en surbrillance l’histogramme et afficher l’histogramme pour le point de données sélectionné par rapport à la tendance de l’ensemble du jeu de données.

## <a name="histograms"></a>Histogrammes
Dans Power BI Desktop, vous pouvez utiliser un champ calculé pour définir un histogramme. Identifiez la table et la colonne à utiliser pour créer un histogramme. Dans la zone de calcul, tapez la formule suivante :

> Frequency:=COUNTROWS(\<Nom de la colonne\>)
> 
> 

Enregistrez vos modifications et revenez au rapport. Ajoutez \<Column Name\> et Frequency à une table, puis procédez à la conversion en graphique à barres. Vérifiez que \<Column Name\> se trouve sur l’axe des abscisses et que le champ calculé Frequency se trouve sur l’axe des ordonnées.

## <a name="tips-and-tricks-for-creating-relationships-in-power-bi-desktop"></a>Conseils et astuces pour créer des relations dans Power BI Desktop
Lors du chargement de jeux de données détaillés en provenance de plusieurs sources, vous pouvez être dans l’impossibilité de créer des relations en raison de valeurs null, vides ou en double. 

Prenons un exemple : 

Nous allons charger un jeu de données de demandes de support technique actives émises par les clients et un autre jeu de données d’éléments de travail avec les schémas suivants :

> CustomerIncidents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

Quand nous souhaitons faire le suivi des incidents et des éléments de travail liés à un nom de client (CustomerName) spécifique, nous ne parvenons pas à créer une relation entre ces deux jeux de données. Certains éléments de travail (WorkItems) ne sont peut-être pas liés à un nom de client (CustomerName), et nous nous retrouvons avec un champ vide ou NULL. Il peut y avoir plusieurs enregistrements dans WorkItems et CustomerIncidents pour un CustomerName donné. 

### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-null-or-blank-values"></a>Création de relations dans Power BI Desktop, lorsque les données comprennent des valeurs null ou vides
Il arrive que des jeux de données contiennent des colonnes avec des valeurs null ou vides. Cela peut poser des problèmes lors de la création de relations. Pour résoudre le problème, deux options s’offrent à vous. Vous pouvez supprimer les lignes qui contiennent des valeurs null ou vides. Pour cela, utilisez la fonctionnalité de filtre sous l’onglet requête ou, si vous fusionnez des requêtes, sélectionnez l’option « Conserver uniquement les lignes correspondantes ». Vous pouvez aussi remplacer les valeurs null ou vides par des valeurs qui fonctionnent dans les relations, en général des chaînes comme « NULL » et « (Vide) ». Il n’y a pas une approche meilleure que l’autre. Le filtrage de lignes dans l’étape de requête supprime les lignes et peut affecter les calculs et les statistiques récapitulatives. Cette dernière approche conserve les lignes de données. Le problème, c’est que des lignes sans relation peuvent apparaître comme liées dans le modèle, ce qui peut engendrer des erreurs de calcul. Si vous adoptez cette solution, veillez, le cas échéant, à utiliser des filtres au niveau de la vue ou du graphique pour obtenir des résultats précis. Plus important encore, déterminez les lignes qui sont conservées/supprimés et mesurez l’impact global sur l’analyse. 

### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-duplicate-values"></a>Création de relations dans Power BI Desktop, lorsque les données comprennent des valeurs en doublon
Lors du chargement de jeux de données détaillés en provenance de plusieurs sources, vous pouvez être dans l’impossibilité de créer des relations en raison de valeurs null, vides ou en double. Pour résoudre ces problèmes, créez une table de dimension avec les valeurs uniques des deux jeux de données. 

Prenons un exemple : 

Nous allons charger un jeu de données de demandes de support technique actives émises par les clients et un autre jeu de données d’éléments de travail avec les schémas suivants :

> CustomerIncidents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

Quand nous souhaitons faire le suivi des incidents et des éléments de travail liés à un nom de client (CustomerName) spécifique, nous ne parvenons pas à créer une relation entre ces deux jeux de données. Certains éléments de travail (WorkItems) ne sont peut être pas liés à un nom de client (CustomerName), et nous nous retrouvons avec un champ vide ou NULL. Si la table CustomerNames comprend des valeurs vides ou null, vous pouvez encore être dans impossibilité de créer une relation. Consultez « Création de relations si les données comprennent des valeurs null ou vides ». Il existe peut-être plusieurs éléments WorkItems et CustomerIncidents pour un CustomerName donné. 

Pour créer une relation dans ce cas, nous devons créer un jeu de données logique de tous les éléments CustomerNames dans les deux jeux de données. Sous l’onglet Requête, vous pouvez utiliser la séquence suivante pour créer le jeu de données logique :

1. Dupliquez les deux requêtes. Pour cela, nommez la première **Temp** et la seconde **CustomerNames**.
2. Dans chaque requête, supprimez toutes les colonnes *sauf* la colonne CustomerName.
3. Dans chaque requête, utilisez  **Supprimer les doublons**.
4. Dans la requête **CustomerNames**, sélectionnez l’option **Ajouter** dans le ruban, puis sélectionnez la requête **Temp**.
5. Dans la requête **CustomerNames**, sélectionnez **Supprimer les doublons**.

Vous disposez à présent d’une table de dimension qui contient toutes les valeurs de CustomerIndicents et WorkItems. Utilisez cette table pour établir des liens à ces éléments. 

## <a name="patterns-to-jump-start-your-use-of-the-query-editor"></a>Modèles permettant d’exploiter immédiatement l’Éditeur de requête
L’Éditeur de requête est un outil de manipulation des données très puissant qui permet de mettre en forme et de nettoyer les données en vue de les visualiser ou de les modéliser. Voici quelques points clés à connaître.

### <a name="temporary-columns-can-be-deleted-after-computing-a-result"></a>Les colonnes temporaires peuvent être supprimées après le calcul d’un résultat
Il est souvent nécessaire de générer un calcul dans Power BI Desktop qui transforme les données de plusieurs colonnes en une nouvelle colonne unique. Cette opération peut être complexe. Pour y parvenir, un moyen simple consiste à décomposer l’opération en plusieurs étapes. Commencez par dupliquer les colonnes initiales. Créez ensuite les étapes des colonnes temporaires. Enfin, créez une colonne pour le résultat final. Vous pouvez ensuite supprimer les colonnes temporaires pour ne pas saturer le jeu de données final. Cette approche est possible parce que l’onglet Requête exécute les étapes dans l’ordre. 

### <a name="duplicate-or-reference-queries-followed-by-merge-to-original-query"></a>Dupliquer ou référencer des requêtes, puis fusion avec la requête d’origine
Il est parfois utile de calculer des statistiques récapitulatives pour un jeu de données. Pour cela, la méthode la plus simple consiste à dupliquer la requête ou à faire référence à celle-ci sous l’onglet Requête. Ensuite, utilisez **Regrouper par** pour calculer les statistiques récapitulatives. Les statistiques récapitulatives vous permettent de normaliser les données dans les données d’origine afin de faciliter les comparaisons. Elles sont particulièrement utiles pour comparer des valeurs individuelles à l’ensemble des valeurs. Pour cela, accédez à la requête d’origine, puis sélectionnez l’option de fusion. Ensuite, fusionnez les données de la requête de statistiques récapitulatives correspondant aux identificateurs appropriés. Vous pouvez à présent normaliser les données en fonction des besoins de votre analyse.

## <a name="using-dax-for-the-first-time"></a>Utilisation de DAX pour la première fois
DAX est le langage des formules de calcul dans Power BI Desktop. Il est optimisé pour l’analyse décisionnelle. Si votre expérience est centrée autour d’un langage de requête semblable à SQL, DAX peut vous paraître légèrement différent de ce à quoi vous êtes habitué. Si vous souhaitez apprendre DAX, vous trouverez de très bonnes ressources en ligne et divers ouvrages sur le sujet. 

[Découvrir les principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md)

[Informations de référence sur DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx)

[Centre de ressources DAX](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx)
