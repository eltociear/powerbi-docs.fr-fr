---
title: Guide pratique pour ajouter un lien hypertexte à un tableau
description: Liens hypertexte dans les tables
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/22/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d696a7492f1295f2e2c9b39088b0eacdb66b15ca
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34310173"
---
# <a name="hyperlinks-in-tables"></a>Liens hypertexte dans les tables
Cette rubrique explique comment utiliser Power BI Desktop pour créer des liens hypertexte. Une fois que vous avez créé des liens hypertexte, utilisez Power BI Desktop ou le service Power BI pour les ajouter à vos tableaux et matrices de rapport. 

![](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> **Remarque** : des liens hypertexte dans des [vignettes de tableaux de bord](service-dashboard-edit-tile.md) et [des zones de texte de tableaux de bord](service-dashboard-add-widget.md) peuvent être créés rapidement à l’aide du service Power BI. Les liens hypertexte des [zones de texte de rapport](service-add-hyperlink-to-text-box.md) peuvent être créés rapidement à l’aide du service Power BI et de Power BI Desktop.
> 
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Pour créer un lien hypertexte dans une table ou une matrice à l’aide de Power BI Desktop
Les liens hypertexte dans les tableaux et matrices peuvent être créés dans Power BI Desktop, mais pas dans le service Power BI. Les liens hypertexte peut également être créés dans PowerPivot pour Excel avant l’importation du classeur dans Power BI. Les deux méthodes sont décrites ci-dessous.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Créer un lien hypertexte de tableau ou matrice dans Power BI Desktop
La procédure d’ajout d’un lien hypertexte varie selon que vous avez importé les données ou que vous vous y êtes connecté à l’aide de DirectQuery. Les deux scénarios sont décrits ci-dessous.

### <a name="for-data-imported-into-power-bi"></a>Pour les données importées dans Power BI
1. Si le lien hypertexte n’existe pas déjà en tant que champ dans votre jeu de données, utilisez Desktop pour l’ajouter en tant que [colonne personnalisée](desktop-common-query-tasks.md).
2. Dans la Vue de données, sélectionnez la colonne, puis, sous l’onglet **Modélisation**, choisissez la liste déroulante **Catégorie de données**.
   
    ![](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Sélectionnez **URL web**.
4. Passez au mode Rapport et créez un tableau ou une matrice à l’aide du champ classé comme URL web. Les liens hypertexte sont en bleu et soulignés.
   
    ![](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)
5. Si vous ne souhaitez pas afficher une URL longue dans une table, vous pouvez afficher une icône de lien hypertexte ![](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) à la place. Notez que vous ne pouvez pas afficher d’icônes dans une matrice.
   
   * Sélectionnez le graphique pour l’activer.
   * Ouvrez l’onglet Mise en forme en sélectionnant l’icône en forme de rouleau ![](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png).
   * Développez **Valeurs**, recherchez **Icône d’URL** et **activez-la**.
6. (Facultatif) [Publiez le rapport de Power BI Desktop vers le service Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) et ouvrez-le dans le service Power BI. Les liens hypertexte fonctionnent ici également.

### <a name="for-data-connected-with-directquery"></a>Pour les données connectées avec DirectQuery
Vous ne pouvez pas créer de colonne en mode DirectQuery.  Mais si vos données contiennent déjà des URL, vous pouvez convertir ces dernières en liens hypertexte.

1. En mode Rapport, créez un tableau à l’aide d’un champ qui contient des URL.
2. Sélectionnez la colonne puis, sous l’onglet **Modélisation**, choisissez la liste déroulante **Catégorie de données**.
3. Sélectionnez **URL web**. Les liens hypertexte sont en bleu et soulignés.
4. (Facultatif) [Publiez le rapport de Power BI Desktop vers le service Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) et ouvrez-le dans le service Power BI. Les liens hypertexte fonctionnent ici également.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Créer un lien hypertexte de tableau ou matrice dans Excel PowerPivot
Une autre méthode pour ajouter des liens hypertexte à vos tableaux et matrices Power BI consiste à créer des liens hypertexte dans le jeu de données avant d’importer ce dernier ou de vous y connecter à partir de Power BI. Cet exemple utilise un classeur Excel.

1. Ouvrez le classeur dans Excel.
2. Sélectionnez l’onglet **PowerPivot**, puis choisissez **Gérer**.
   
   ![](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
3. Quand PowerPivot s’ouvre, sélectionnez l’onglet **Avancé**.
   
   ![](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Placez votre curseur dans la colonne qui contient les URL que vous voulez transformer en liens hypertexte dans les tables Power BI.
   
   > **REMARQUE** : l’URL doit commencer par **http://, https://** ou **www**.
   > 
   > 
5. Dans le groupe **Propriétés de rapport**, sélectionnez la liste déroulante **Catégorie des données**, puis choisissez **URL web**. 
   
   ![](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)
6. Depuis le service Power BI ou Power BI Desktop, connectez-vous à ce classeur ou importez-le.
7. Créez une visualisation de table comprenant le champ d’URL.
   
   ![](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
Q : Peut-on utiliser une URL personnalisée comme lien hypertexte dans un tableau ou dans une matrice ?    
R : Non. Il est possible d’utiliser une icône de lien. Si vous avez besoin d’un texte personnalisé pour vos liens hypertextes et que votre liste d’URL est courte, vous pouvez utiliser une zone de texte à la place.


## <a name="next-steps"></a>Étapes suivantes
[Visualisations dans des rapports Power BI](power-bi-report-visualizations.md)

[Power BI – Concepts de base](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

