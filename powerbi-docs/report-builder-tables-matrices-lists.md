---
title: Tableaux, matrices et listes dans le Générateur de rapports Power BI
description: Dans Power BI Report Builder, les tableaux, les matrices et les listes sont des régions de données qui montrent des données des rapports paginés dans des cellules organisées en lignes et en colonnes.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 02ac131325dab59590cb88c524ace68a1226fc69
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953850"
---
# <a name="tables-matrixes-and-lists-in-power-bi-report-builder"></a>Tableaux, matrices et listes dans le Générateur de rapports Power BI
 Dans le Générateur de rapports, les tableaux, les matrices et les listes sont des *régions de données* qui montrent des données de rapports paginés dans des cellules organisées en lignes et en colonnes. Les cellules contiennent généralement des données texte, comme du texte, des dates et des nombres, mais elles peuvent également contenir des jauges, des graphiques ou des éléments de rapport comme des images. Collectivement, les tableaux, les matrices et les listes sont fréquemment appelées des régions de données « *tableau matriciel* ».  
  
 Les modèles de tableau, de matrice et de liste sont basés sur la région de données « tableau matriciel », qui est une grille flexible qui peut afficher des données dans des cellules. Dans les modèles de tableau et de matrice, les cellules sont organisées en lignes et en colonnes. Comme les modèles sont des variantes de la région de données « tableau matriciel » générique sous-jacente, vous pouvez afficher des données dans une combinaison de formats de modèle et modifier le tableau, la matrice ou la liste pour inclure les fonctionnalités d’une autre région de données quand vous développez votre rapport. Par exemple, si vous ajoutez un tableau et qu’il ne répond pas à vos besoins, vous pouvez ajouter des groupes de colonnes pour faire du tableau une matrice.  
  
 Les régions de données « tableau » et « matrice » peuvent afficher des relations de données complexes en incluant des tableaux, des matrices, des listes, des graphiques et des jauges imbriquées. Les tableaux et les matrices ont une disposition tabulaire, et leurs données proviennent d’un même jeu de données, basé sur une même source de données. La principale différence entre les tableaux et les matrices est que les tableaux peuvent inclure seulement des groupes de lignes, tandis que les matrices ont des groupes de lignes et des groupes de colonnes.  
  
 Les listes sont un peu différentes. Elles prennent en charge une disposition libre qui peut inclure plusieurs tableaux ou matrices appairées, chacune utilisant des données provenant d’un jeu de données différent. Les listes peuvent aussi être utilisées pour des formulaires, comme des factures.  
  
 Les images suivantes montrent des rapports simples avec un tableau, une matrice ou une liste.  

![Tableau, matrice et liste du Générateur de rapports](media/report-builder-tables-matrices-lists/report-builder-table-matrix-list.png)
  
##  <a name="Table"></a> Tableaux  
 Utilisez un tableau pour montrer des données détaillées, organiser les données en groupes de lignes, ou les deux. Le modèle de tableau contient trois colonnes avec une ligne d’en-tête de tableau et une ligne de détails pour les données. La figure suivante montre le modèle de tableau initial, sélectionné sur l’aire de conception :  

![Modèle de tableau du Générateur de rapports sélectionné sur l’aire de conception](media/report-builder-tables-matrices-lists/report-builder-new-table.png)
  
 Vous pouvez regrouper les données sur un seul champ, sur plusieurs champs ou en écrivant votre propre expression. Vous pouvez créer des groupes imbriqués ou des groupes indépendants adjacents, et afficher des valeurs agrégées pour les données regroupées ou ajouter des totaux aux groupes. Par exemple, si votre tableau a un groupe de lignes appelé **Catégorie**, vous pouvez ajouter un sous-total pour chaque groupe ainsi qu’un total général pour le rapport. Pour améliorer l’apparence du tableau et mettre en évidence les données de votre choix, vous pouvez fusionner des cellules et appliquer une mise en forme aux données et aux titres du tableau.  
  
 Vous pouvez masquer initialement des détails ou des données regroupées, et inclure des éléments qui activent/désactivent l’exploration pour permettre à un utilisateur de choisir de façon interactive la quantité de données à afficher.  
  
##  <a name="Matrix"></a> Matrices  
 Utilisez une matrice pour afficher des récapitulatifs des données agrégées, regroupées en lignes et en colonnes, de façon similaire à un tableau croisé dynamique ou à une analyse croisée. Le nombre de lignes et de colonnes pour les groupes est déterminé par le nombre de valeurs uniques pour chaque groupe de lignes et de colonnes. La figure suivante montre le modèle de matrice initial, sélectionné sur l’aire de conception :  

![Nouvelle matrice ajoutée à partir de la boîte à outils et sélectionnée dans le Générateur de rapports](media/report-builder-tables-matrices-lists/report-builder-new-matrix.png)
 
 Vous pouvez regrouper des données selon plusieurs champs ou expressions dans les groupes de lignes et de colonnes. Au moment de l’exécution, quand les données et les régions de données du rapport sont combinées, une matrice se développe horizontalement et verticalement sur la page, car des colonnes sont ajoutées pour les groupes de colonnes et des lignes pour les groupes de lignes. Les cellules de matrice affichent des valeurs agrégées qui sont délimitées à l’intersection des groupes de lignes et de colonnes auxquels la cellule appartient. Par exemple, si votre matrice a un groupe de lignes (Catégorie) et deux groupes de colonnes (Territoire et Année) qui affichent la somme des ventes, le rapport affiche deux cellules avec les sommes des ventes pour chaque valeur du groupe Catégorie. L’étendue des cellules correspond aux deux intersections : Catégorie et Territoire, et Catégorie et Année. La matrice peut inclure des groupes imbriqués et adjacents. Les groupes imbriqués ont une relation parent-enfant, et les groupes adjacents une relation de pair. Vous pouvez ajouter des sous-totaux pour tout ou partie des niveaux des groupes de lignes et de colonnes imbriqués dans la matrice.  
  
 Pour rendre les données d’une matrice plus lisibles et mettre en évidence les données de votre choix, vous pouvez fusionner des cellules, ou fractionner horizontalement et verticalement, et appliquer une mise en forme aux données et aux titres des groupes.  
  
 Vous pouvez également inclure des éléments d’activation/désactivation de l’exploration qui masquent initialement les données détaillées ; l’utilisateur peut ensuite cliquer sur ces éléments pour voir plus ou moins de détails selon les besoins.  
  
##  <a name="List"></a> Listes  
 Utilisez une liste pour créer une disposition de forme libre. Vous n’êtes pas limité à une disposition en grille : vous pouvez placer les champs librement à l’intérieur de la liste. Vous pouvez utiliser une liste pour concevoir un formulaire montrant un grand nombre de champs de jeu de données ou comme conteneur pour afficher plusieurs régions de données côte à côte pour des données regroupées. Par exemple, vous pouvez définir un groupe pour une liste, ajouter un tableau, un graphique et des images, et afficher des valeurs sous forme tabulaire et graphique pour chaque valeur de groupe, comme vous le feriez pour un enregistrement d’employé ou de patient.  

![Nouvelle liste ajoutée à partir de la boîte à outils et sélectionnée dans le Générateur de rapports](media/report-builder-tables-matrices-lists/report-builder-new-list.png)
  
##  <a name="PreparingData"></a> Préparation des données  
 Les régions de données tableau, matrice et liste affichent des données provenant d’un jeu de données. Vous pouvez préparer les données dans la requête qui récupère les données du jeu de données, ou en définissant des propriétés dans le tableau, la matrice ou la liste.  
  
 Les langages de requête comme Transact-SQL, que vous utilisez pour récupérer les données pour les jeux de données des rapports, peuvent préparer les données en appliquant des filtres pour inclure seulement un sous-ensemble des données, en remplaçant les valeurs null ou vides par des constantes qui rendent le rapport plus lisible, et en triant et en regroupant les données.  
  
 Si vous choisissez de préparer les données dans une région de données « tableau », « matrice » ou « liste » d’un rapport, vous définissez des propriétés sur la région de données ou sur des cellules de la région de données. Si vous voulez filtrer ou trier les données, définissez les propriétés sur la région de données. Par exemple, pour trier les données, vous spécifiez les colonnes à trier et le sens du tri. Si vous voulez fournir une valeur alternative pour un champ, vous définissez les valeurs du texte de la cellule qui affiche le champ. Par exemple, pour afficher une cellule vide quand un champ est vide ou null, vous utilisez une expression pour définir la valeur.  
  
##  <a name="BuildingConfiguringTableMatrixList"></a> Création et configuration d’un tableau, d’une matrice ou d’une liste  
 Quand vous ajoutez des tableaux ou des matrices à votre rapport, vous pouvez utiliser l’Assistant Table et matrice, ou les créer manuellement à partir de modèles fournis par le Générateur de rapports. Les listes sont créées manuellement à partir du modèle de liste.  
  
 L’Assistant vous guide à travers les étapes nécessaires pour créer et configurer rapidement un tableau ou une matrice. Après avoir terminé l’Assistant ou si vous créez les régions de données « tableau matriciel » à partir de zéro, vous pouvez les configurer et les ajuster plus avant. Les boîtes de dialogue, disponibles dans les menus contextuels sur les régions de données, vous permettent de définir facilement les propriétés les plus couramment utilisées pour les sauts de page, la répétabilité et la visibilité des en-têtes et pieds de page, les options d’affichage, les filtres et le tri. La région de données « tableau matriciel » fournit cependant une multitude de propriétés supplémentaires, que vous pouvez définir seulement dans le volet Propriétés du Générateur de rapports. Par exemple, si vous voulez afficher un message quand le jeu de données pour un tableau, une matrice ou une liste est vide, vous spécifiez le texte du message dans la propriété de tableau matriciel NoRowsMessage, dans le volet Propriétés.  
  
##  <a name="ChangingBetweenTablixTemplates"></a> Changement de modèle de tableau matriciel  
 Vous n’êtes pas limité par votre choix initial du modèle de tableau matriciel. Au fil de l’ajout de groupes, de totaux et d’étiquettes, vous pouvez souhaiter modifier la conception de votre tableau matriciel. Par exemple, vous pouvez commencer par un tableau, puis supprimer la ligne de détails et ajouter des groupes de colonnes.  
  
 Vous pouvez continuer à développer un tableau, une matrice ou une liste en ajoutant des fonctionnalités de tableau matriciel. Les fonctionnalités de tableau matriciel incluent l’affichage de données détaillées ou d’agrégats pour les données regroupées sur des lignes et des colonnes. Vous pouvez créer des groupes imbriqués, des groupes adjacents indépendants ou des groupes récursifs. Vous pouvez filtrer et trier des données regroupées et combiner facilement des groupes en incluant des expressions avec plusieurs groupes dans une définition de groupe.  
  
 Vous pouvez aussi ajouter des totaux pour un groupe ou des totaux généraux pour la région de données. Vous pouvez masquer des lignes ou des colonnes pour simplifier un rapport, et permettre à l’utilisateur d’afficher ou de masquer les données masquées, comme dans un rapport d’exploration. 

## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
