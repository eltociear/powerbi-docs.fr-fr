---
title: Conseils pour la conception des rapports dans le Générateur de rapports Power BI
description: Appliquez les conseils suivants pour concevoir vos rapports paginés dans Power BI Report Builder.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 13b9e37d4a64493dfdcac02d9df86a1e19a1c24b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921168"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Conseils pour la conception des rapports dans le Générateur de rapports Power BI
  Appliquez les conseils suivants pour concevoir vos rapports paginés dans Power BI Report Builder.  
  
   
  
##  <a name="DesigningReports"></a> Conception de rapports  
  
-   Un rapport bien conçu donne des informations qui conduisent à une action. Identifiez les questions auxquelles le rapport permet de répondre. Gardez ces questions à l’esprit lors de la conception du rapport.  
  
-   Pour concevoir des visualisations de données efficaces, pensez à la façon d’afficher des informations pour que l’utilisateur du rapport puisse les comprendre facilement. Choisissez une région de données qui correspond bien aux données que vous voulez visualiser. Par exemple, un graphique montre des informations récapitulatives et agrégées de façon plus efficace qu’un tableau, qui comprend de nombreuses pages d’informations détaillées. Vous pouvez visualiser des données provenant d’un jeu de données dans n’importe quelle région de données, ce qui inclut des graphiques, des cartes, des indicateurs, des graphiques sparkline, des histogrammes et des données tabulaires dans différentes dispositions de grille basées sur un tableau matriciel. 
  
-   Si vous prévoyez de délivrer le rapport dans un format d’exportation spécifique, testez ce format au début de votre conception. La prise en charge des fonctionnalités varie selon le convertisseur que vous choisissez.  
  
-   Quand vous créez des dispositions complexes, procédez par phases. Vous pouvez utiliser des rectangles comme conteneurs pour organiser les éléments des rapports. Vous pouvez créer des régions de données directement sur l’aire de conception pour optimiser votre espace de travail et ensuite, quand vous en avez terminé une, faites-la glisser dans le rectangle conteneur. En utilisant des rectangles comme conteneurs, vous pouvez positionner tout leur contenu en une seule étape. Les rectangles permettent aussi de contrôler la façon dont les éléments des rapports sont rendus sur chaque page.  
  
-   Pour réduire l’encombrement dans un rapport, vous pouvez envisager d’utiliser une visibilité conditionnelle pour des éléments spécifiques du rapport et permettre à l’utilisateur de choisir s’il faut afficher les éléments. Vous pouvez définir la visibilité en fonction d’un paramètre ou d’un élément d’activation/désactivation d’une zone de texte. Vous pouvez ajouter des zones de texte masquées de façon conditionnelle pour afficher les résultats d’expressions intermédiaires. Quand un rapport affiche des données inattendues, vous pouvez afficher ces résultats intermédiaires pour déboguer les expressions.  
  
-   Quand vous travaillez avec des éléments imbriqués dans des cellules de tableau matriciel ou des rectangles, vous pouvez définir des couleurs d’arrière-plan différentes pour le conteneur et pour les éléments qu’il contient. Par défaut, la couleur d’arrière-plan est **Aucune couleur**. Les éléments avec une couleur d’arrière-plan spécifique transparaissent à travers les éléments avec une couleur d’arrière-plan définie sur **Aucune couleur**. Cette technique peut vous aider à sélectionner l’élément correct pour définir les propriétés d’affichage, comme la visibilité de la bordure sur les cellules de tableau matriciel.  
  
 Pour plus d’informations sur les éléments à prendre en compte lors de la conception de votre rapport, consultez [Planification d’un rapport dans le Générateur de rapports](report-builder-planning-report.md)).  
  
##  <a name="NamingConventions"></a> Conventions de nommage pour les rapports, les sources de données et les jeux de données  
  
-   Utilisez les conventions de nommage pour les sources de données et les jeux de données qui documentent la source de données.  
  
    1.  **Sources de données.** Si vous ne voulez pas utiliser un serveur ou une base de données pour des raisons de sécurité, utilisez un alias qui indique à l’utilisateur quelle est la source des données.  
  
    2.  **Jeux de données.** Utilisez un nom qui indique sur quelle source de données il est basé.  
  
##  <a name="Data"></a> Utilisation des données  
  
-   Dans un premier temps, faites apparaitre toutes les données avec lesquelles vous voulez travailler dans le volet Données du rapport. Quand vous affinez les questions auxquelles le rapport est conçu pour répondre, pensez à la façon de limiter les données dans les jeux de données du rapport à ce qui est strictement nécessaire.  
  
-   D’une façon générale, incluez seulement les données que vous allez afficher dans un rapport. Utilisez des variables de requête dans vos requêtes de jeu de données pour permettre aux utilisateurs de choisir les données qu’ils veulent voir dans le rapport. Si vous créez des jeux de données partagés, spécifiez des filtres basés sur les paramètres du rapport pour fournir les mêmes fonctionnalités.  
  
-   Si vous êtes créateur de requêtes expérimenté, notez que pour les quantités de données intermédiaires, il peut être préférable de regrouper les données dans le rapport et non pas dans la requête. Si vous effectuez tous vos regroupements dans la requête, le rapport a tendance à être une présentation du jeu de résultats de la requête. En revanche, pour afficher des valeurs agrégées pour de grandes quantités de données sur un graphique ou une matrice, il n’y a pas besoin d’inclure les données détaillées.  
  
-   En fonction de vos besoins, vous pouvez afficher dans le rapport les noms et les emplacements des sources de données du rapport, le texte des commandes des requêtes sur les jeux de données et les valeurs des paramètres. La première question que posent les nouveaux utilisateurs est relative à la provenance des données. Pour réduire l’encombrement dans le rapport, vous pouvez masquer de façon conditionnelle les zones de texte avec ce type d’informations et permettre aux utilisateurs de choisir de les afficher. Essayez en ajoutant ces informations sur la dernière page du rapport. Définissez la visibilité de la zone de texte en fonction d’un paramètre de l’utilisateur peut changer.  
  
##  <a name="DesignSurface"></a> Interaction avec l’aire de conception des rapports  
 L’aire de conception des rapports n’est pas WYSIWYG. Quand vous placez des éléments de rapport sur l’aire de conception, leur emplacement relatif affecte la façon dont les éléments apparaissent dans la page de rapport rendue. L’espace vide est conservé.  
  
-   Utilisez les lignes d’alignement et les boutons de disposition pour aligner et organiser des éléments sur l’aire de conception du rapport. Par exemple, vous pouvez aligner les hauts ou les bords d’éléments sélectionnés, étendre un élément pour faire correspondre sa taille à celle d’un autre élément ou ajuster l’espacement entre des éléments.  
  
-   Utilisez les touches de direction pour ajuster la position et la taille d’éléments sélectionnés sur l’aire de conception. Par exemple, les combinaisons de touches suivantes sont très pratiques :  
  
    -   **Touches de direction** Déplacer l’élément de rapport sélectionné.  
  
    -   **Ctrl+Touches de direction** Déplacer d’un pixel à la fois l’élément de rapport sélectionné.  
  
    -   **Ctrl+Maj+Touches de direction** Augmenter ou diminuer la taille de l’élément de rapport sélectionné.  
  
-   Pour ajouter un élément à un rectangle, utilisez l’extrémité supérieure gauche de la souris pour pointer à l’emplacement initial de l’élément dans le rectangle conteneur. Utilisez les raccourcis clavier pour positionner des objets sélectionnés. Le rectangle s’étend automatiquement pour s’adapter à la taille des éléments qu’il contient.  
  
-   Pour ajouter plusieurs éléments à une cellule de tableau matriciel, commencez par ajouter un rectangle, puis ajoutez les éléments.  
  
     Par défaut, chaque cellule de tableau matriciel contient une zone de texte. Quand vous ajoutez un rectangle à une cellule, le rectangle remplace la zone de texte. Par exemple, placez des indicateurs imbriqués dans un rectangle dans une cellule de tableau matriciel pour contrôler comment la taille d’un graphique ou d’un indicateur s’étend à mesure que vous changez la hauteur de la ligne où se trouve la cellule.  
  
-   Utilisez le contrôle **Zoom** pour ajuster votre vue de l’aire de conception. Vous pouvez travailler avec la page entière ou avec des sections plus petites de la page.  
  
-   Pour faire glisser des champs depuis le volet Données du rapport vers le volet Regroupement, évitez de faire glisser le champ à travers d’autres éléments du rapport sur l’aire de conception, car ceci sélectionne les autres éléments et désélectionne la région de données « tableau matriciel ». Faites glisser le champ vers le bas du volet Données du rapport, puis à travers le volet Regroupement.  
  
###  <a name="Selecting"></a> Sélection d’éléments  
 Pour sélectionner l’objet que vous voulez sur l’aire de conception du rapport, utilisez la touche Échap, le menu contextuel, le volet Propriétés et le volet Regroupement.  
  
-   -   Appuyez sur Échap pour parcourir la pile des éléments du rapport qui occupent le même espace sur l’aire de conception.  
  
    -   Sur certains éléments de rapport, essayez en utilisant le menu contextuel pour sélectionner l’élément de rapport ou la partie de l’élément de rapport que vous souhaitez.  
  
    -   Le volet Propriétés affiche les propriétés pour la sélection actuelle.  
  
    -   Pour utiliser des groupes de lignes et des groupes de colonnes dans une région de données « tableau matriciel », sélectionnez le groupe dans le volet Regroupement.  

  
##  <a name="ReportItems"></a> Utilisation de types spécifiques d’éléments de rapport  
  
###  <a name="Parameters"></a> Utiliser des paramètres  
  
-   L’objectif principal des paramètres de rapport est de filtrer les données de la source de données et de récupérer seulement ce qui est nécessaire pour l’objectif du rapport.  
  
-   Pour les paramètres de rapport, recherchez un équilibre entre permettre une certaine interactivité et aider un utilisateur à obtenir les résultats souhaités. Par exemple, vous pouvez définir pour un paramètre des valeurs par défaut correspondant à ce qui est fréquemment utilisé.  
  
###  <a name="Text"></a> Utilisation du texte  
  
-   Quand vous collez plusieurs lignes dans une zone de texte, le texte est ajouté en tant que séquence de texte. Chaque séquence de texte peut être mise en forme seulement comme un tout. Pour mettre en forme chaque ligne indépendamment, insérez une nouvelle ligne en appuyant sur Entrée dans la séquence de texte. Vous pouvez ensuite appliquer des mises en forme et des styles à chaque ligne de texte indépendante dans la zone de texte.  
  
-   Vous pouvez définir des propriétés de format et des actions sur une zone de texte ou sur le texte d’un espace réservé dans la zone de texte. S’il n’existe qu’une seule ligne de texte, il est plus efficace de définir des propriétés sur la zone de texte que sur le texte.  
  
###  <a name="Expressions"></a> Utilisation des expressions  
  
-   Présentation des formats d’expressions simples et complexes Vous pouvez taper un format d’expression simple directement dans des zones de texte, dans les propriétés du volet Propriétés ou aux emplacements des boîtes de dialogue qui acceptent une expression.
  
-   Quand vous créez une expression, il est recommandé de créer chaque partie indépendamment et de vérifier sa valeur. Vous pouvez ensuite combiner toutes les parties dans une expression finale. Une technique pratique est d’ajouter une zone de texte dans une cellule de matrice, d’afficher chaque partie de l’expression et de définir une visibilité conditionnelle sur la zone de texte. Pour contrôler le style et la couleur de bordure quand la zone de texte est masquée, placez d’abord la zone de texte dans un rectangle, puis définissez le style et la couleur de bordure du rectangle pour les faire correspondre à la matrice.  
  
###  <a name="Indicators"></a> Utilisation des indicateurs  
  
-   Par défaut, un indicateur affiche au moins trois états. Après avoir ajouté un indicateur à un rapport, vous pouvez le configurer en ajoutant ou en supprimant des états. Pour que vos utilisateurs le voient plus facilement, choisissez un indicateur qui varie à la fois par sa couleur et par sa forme.  
  
##  <a name="Rendering"></a> Contrôle du rendu des éléments de rapport sur la page du rapport  
  
-   Sur l’aire de conception du rapport, les éléments de rapport s’agrandissent pour s’adapter au contenu provenant du jeu de données, de l’expression, du sous-rapport ou du texte associés.  
  
    -   Quand vous positionnez un élément dans la page du rapport, la distance entre l’élément et tous les éléments qui commencent à sa droite devient la distance minimale qui doit être conservée quand un élément de rapport s’agrandit horizontalement. De même, la distance entre un élément et l’élément au-dessus de celui-ci devient une distance minimale qui doit être conservée quand l’élément du haut s’agrandit verticalement.  
  
    -   Un élément d’un rapport s’agrandit pour s’adapter à ses données et repousse en dehors les éléments appairés (des éléments dans le même conteneur parent) en appliquant les règles suivantes :  
  
    -   Chaque élément se déplace vers le bas pour conserver l’espace minimal entre lui-même et les éléments qui se terminent au-dessus de lui.  
  
    -   Chaque élément se déplace vers la droite pour conserver l’espace minimal entre lui-même et les éléments qui se terminent à sa gauche. Pour les systèmes avec des dispositions de droite à gauche, chaque élément se déplace vers la gauche pour conserver l’espace minimal entre lui-même et les éléments qui se terminent à sa droite.  
  
    -   Les conteneurs s’étendent pour s’adapter à la croissance des éléments enfants. Pour un élément sélectionné, dans le volet Propriétés, la propriété Parent identifie le conteneur de l’élément. Vous pouvez également utiliser le volet Structure du document pour voir la hiérarchie de contenance des éléments de rapport.  
  
    -   La barre d’outils **Disposition** contient plusieurs boutons qui permettent d’aligner les bords, les centres et l’espacement des éléments de rapport. Pour activer la barre d’outils **Disposition**, dans le menu **Affichage**, pointez sur **Barres d’outils**, puis cliquez sur **Disposition**.  
  
-   Si vous prévoyez d’enregistrer le rapport sous forme de fichier .pdf, la largeur du rapport doit être définie explicitement sur une valeur qui vous donne les résultats souhaités dans le format de fichier d’exportation. Par exemple, définissez la largeur de la page de rapport sur exactement 20,1612 cm, et les marges gauche et droite sur 1,27 cm.  
  
-   Utilisez **Format d’impression** et **Mise en page** sur la barre d’outils de la visionneuse de rapports pour afficher un rapport dans une vue compatible avec l’impression. Pour supprimer les pages vierges inutiles, suivez les étapes ci-dessous :  
  
    1.  Supprimez tout l’espace vide superflu entre les régions de données et sur les bords du rapport.  
  
    2.  Réduisez les marges des pages dans la boîte de dialogue **Propriétés du rapport**.  
  
    3.  Utilisez des **Rectangles** comme conteneurs pour contrôler la façon dont les éléments de rapport sont rendus.  
  
    4.  Dans les en-têtes de colonne, modifiez la propriété de zone de texte WritingMode pour qu’elle utilise du texte vertical.  

 Pour obtenir de l’aide, consultez [Éviter les pages vierges lors de l’impression de rapports paginés](../guidance/report-paginated-blank-page.md).

 La combinaison de ce comportement, des propriétés de largeur et de hauteur des éléments de rapport, de la taille du corps du rapport, de la définition de la hauteur et de la largeur des pages, des paramètres de marge du rapport parent et de la prise en charge spécifique au convertisseur pour la pagination détermine quels éléments de rapport tiennent ensemble dans une page rendue.
 
## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)  
