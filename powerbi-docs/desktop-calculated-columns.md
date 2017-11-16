---
title: "Utilisation de colonnes calculées dans Power BI Desktop"
description: "Colonnes calculées dans Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 3b3f77444ef71c190404eb4dc40970ffa634aa47
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Utilisation de colonnes calculées dans Power BI Desktop
Les colonnes calculées vous permettent d’ajouter de nouvelles données à une table déjà présente dans votre modèle. Toutefois, au lieu d’interroger et de charger les valeurs dans votre nouvelle colonne à partir d’une source de données, vous créez une formule DAX (Data Analysis Expressions) qui définit les valeurs de la colonne. Dans Power BI Desktop, vous créez les colonnes calculées à l’aide de la fonctionnalité Nouvelle colonne dans la vue Rapport.

Contrairement aux colonnes personnalisées créées dans le cadre d’une requête à l’aide de l’option Ajouter une colonne personnalisée dans l’Éditeur de requête, les colonnes calculées créées dans la vue Rapport ou Données sont basées sur des données que vous avez déjà chargées dans le modèle. Par exemple, vous pouvez choisir de concaténer des valeurs de deux colonnes différentes dans deux tables différentes mais associées, d’effectuer une addition ou d’extraire des sous-chaînes.

Les colonnes calculées que vous créez apparaissent dans la liste Champs comme n’importe quel autre champ, mais elles possèdent une icône spéciale indiquant que leurs valeurs sont le résultat d’une formule. Vous pouvez nommer vos colonnes comme vous le souhaitez et les ajouter à une visualisation de rapport comme d’autres champs.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Les colonnes calculées calculent les résultats en utilisant [DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx), langage de formule conçu pour fonctionner avec les données relationnelles comme dans Power BI Desktop. Le langage DAX inclut une bibliothèque de plus de 200 fonctions, opérateurs et constructions. Il offre ainsi une flexibilité considérable pour créer des formules afin d’effectuer les calculs nécessaires pour quasiment tout type d’analyse de données. Pour plus d’informations sur DAX, consultez la section En savoir plus à la fin de cet article.

Les formules DAX sont similaires aux formules Excel. En fait, DAX possède de nombreuses fonctions identiques à celles d’Excel. Les fonctions DAX, cependant, sont destinées à opérer sur des données segmentées ou filtrées de manière interactive dans un rapport, comme dans Power BI Desktop. Contrairement à Excel, où vous pouvez spécifier une formule différente pour chaque ligne d’un tableau, quand vous créez une formule DAX pour une nouvelle colonne, elle calcule un résultat pour chaque ligne de la table. Les valeurs de colonne sont recalculées si nécessaire, comme quand les données sous-jacentes sont actualisées et que les valeurs ont changé.

## <a name="lets-look-at-an-example"></a>Examinons un exemple.
Jeff est responsable des expéditions chez Contoso. Il souhaite créer un rapport indiquant le nombre d’expéditions effectuées vers différentes villes. Il possède une table Geography avec des champs distincts pour la ville et l’État. Toutefois, Jeff souhaite que ses rapports indiquent la ville, l’État sous la forme d’une valeur unique sur la même ligne. À ce stade, la table géographique de Jeff ne contient pas le champ qu’il veut.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Cependant, avec une colonne calculée, Jeff peut simplement rassembler, ou concaténer, les villes de la colonne City avec les États de la colonne State.

Jeff clique avec le bouton droit sur la table Geography, puis clique sur Nouvelle colonne. Il entre ensuite la formule DAX suivante dans la barre de formule :

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Cette formule crée simplement une nouvelle colonne nommée CityState et, pour chaque ligne de la table Geography, elle prend la valeur de la colonne City, ajoute une virgule et un espace puis concatène la valeur de la colonne State.

À présent, Jeff dispose du champ qu’il veut.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Il peut l’ajouter au canevas de son rapport avec le nombre d’expéditions. Très rapidement et avec un minimum d’efforts, Jeff dispose désormais d’un champ City, State (Ville, État). Il peut l’ajouter à quasiment n’importe quel type de visualisation. Jeff constate même que quand il crée une visualisation de carte, Power BI Desktop sait même lire les valeurs City, State dans sa nouvelle colonne.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>En savoir plus
Nous vous avons fourni ici une brève introduction aux colonnes calculées. N’hésitez pas à consulter le didacticiel [Création de colonnes calculées dans Power BI Desktop](desktop-tutorial-create-calculated-columns.md), où vous pourrez télécharger un exemple de fichier et obtenir des indications pas à pas sur la création de colonnes supplémentaires. 

Pour en savoir plus sur DAX, consultez [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

Pour en savoir plus sur les colonnes que vous créez avec une requête, consultez la section Créer des colonnes personnalisées dans [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md).  

