---
title: Ajouter des liens hypertexte (URL) à une table
description: Cette rubrique explique comment ajouter des liens hypertexte (URL) à une table. Vous utilisez Power BI Desktop pour ajouter des liens hypertexte (URL) à une table ou matrice. Ensuite, vous pouvez utiliser Power BI Desktop ou le service Power BI pour ajouter des liens hypertexte à vos matrices et tables de rapports.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/30/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 58cb009e29c05ce318c5931fb418617e1ef63f4f
ms.sourcegitcommit: ba085b248c54e8fb1fd8eb2bb23a814e3fdd7ff6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937061"
---
# <a name="add-hyperlinks-urls-to-a-table"></a>Ajouter des liens hypertexte (URL) à une table
Cette rubrique explique comment ajouter des liens hypertexte (URL) à une table. Vous utilisez Power BI Desktop pour ajouter des liens hypertexte (URL) à une table ou matrice. Ensuite, vous pouvez utiliser Power BI Desktop ou le service Power BI pour ajouter des liens hypertexte à vos matrices et tables de rapports. 

![Table avec des liens hypertexte](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> Vous pouvez créer facilement des liens hypertexte dans des [vignettes de tableaux de bord](service-dashboard-edit-tile.md) et dans des [zones de texte de tableaux de bord](service-dashboard-add-widget.md) à l’aide du service Power BI. Vous pouvez créer facilement des liens hypertexte dans des [zones de texte de rapport](service-add-hyperlink-to-text-box.md) dans le service Power BI et Power BI Desktop.
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>Pour créer un lien hypertexte dans une table ou une matrice à l’aide de Power BI Desktop
Vous pouvez créer des liens hypertexte dans les tableaux et matrices avec Power BI Desktop, mais pas avec le service Power BI. Vous pouvez également créer des liens hypertexte dans PowerPivot pour Excel avant d’importer le classeur dans Power BI. Les deux méthodes sont décrites ci-dessous.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Créer un lien hypertexte de tableau ou matrice dans Power BI Desktop
La procédure d’ajout d’un lien hypertexte varie selon que vous avez importé les données ou que vous vous y êtes connecté à l’aide de DirectQuery. Les deux scénarios sont décrits ci-dessous.

### <a name="for-data-imported-into-power-bi"></a>Pour les données importées dans Power BI
1. Si le lien hypertexte n’existe pas déjà en tant que champ dans votre jeu de données, utilisez Power BI Desktop pour l’ajouter en tant que [colonne personnalisée](desktop-common-query-tasks.md).
2. Dans la Vue de données, sélectionnez la colonne, puis, sous l’onglet **Modélisation**, choisissez la liste déroulante **Catégorie de données**.
   
    ![Liste déroulante des catégories de données](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Sélectionnez **URL web**.
4. Passez au mode Rapport et créez un tableau ou une matrice à l’aide du champ classé comme URL web. Les liens hypertexte sont en bleu et soulignés.

    ![Liens bleus et soulignés](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > Les URL doivent commencer par **http:// , https://** ou **www**.
    >
   
1. Si vous ne souhaitez pas afficher une URL longue dans une table, vous pouvez afficher une icône de lien hypertexte  ![Icône de lien hypertexte](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) à la place. Notez que vous ne pouvez pas afficher d’icônes dans une matrice.
   
    Sélectionnez le graphique pour l’activer.

    Sélectionner l’icône Format ![Icône de rouleau de peinture](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) pour ouvrir l’onglet Mise en forme.

    Développez **Valeurs**, recherchez **Icône d’URL** et **activez-la**.

    ![Activer sur l’icône d’URL](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Facultatif) [Publiez le rapport de Power BI Desktop vers le service Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) et ouvrez-le dans le service Power BI. Les liens hypertexte fonctionnent ici également.

### <a name="for-data-connected-with-directquery"></a>Pour les données connectées avec DirectQuery
Vous ne pouvez pas créer de colonne en mode DirectQuery.  Mais si vos données contiennent déjà des URL, vous pouvez les convertir en liens hypertexte.

1. En mode Rapport, créez un tableau à l’aide d’un champ qui contient des URL.
2. Sélectionnez la colonne puis, sous l’onglet **Modélisation**, choisissez la liste déroulante **Catégorie de données**.
3. Sélectionnez **URL web**. Les liens hypertexte sont en bleu et soulignés.
4. (Facultatif) [Publiez le rapport de Power BI Desktop vers le service Power BI](guided-learning/publishingandsharing.yml?tutorial-step=2) et ouvrez-le dans le service Power BI. Les liens hypertexte fonctionnent ici également.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Créer un lien hypertexte de tableau ou matrice dans Excel PowerPivot
Une autre méthode pour ajouter des liens hypertexte à vos tableaux et matrices Power BI consiste à créer des liens hypertexte dans le jeu de données avant d’importer ce dernier ou de vous y connecter à partir de Power BI. Cet exemple utilise un classeur Excel.

1. Ouvrez le classeur dans Excel.
2. Sélectionnez l’onglet **PowerPivot**, puis choisissez **Gérer**.
   
   ![Ouvrir PowerPivot dans Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Quand PowerPivot s’ouvre, sélectionnez l’onglet **Avancé**.
   
   ![Onglet Avancé de PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Placez votre curseur dans la colonne qui contient les URL que vous voulez transformer en liens hypertexte dans les tables Power BI.
   
   > [!NOTE]
   > Les URL doivent commencer par **http:// , https://** ou **www**.
   > 
5. Dans le groupe **Propriétés de rapport**, sélectionnez la liste déroulante **Catégorie des données**, puis choisissez **URL web**. 
   
   ![Liste déroulante des catégories de données dans Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Depuis le service Power BI ou Power BI Desktop, connectez-vous à ce classeur ou importez-le.
7. Créez une visualisation de table comprenant le champ d’URL.
   
   ![Créer une table dans Power BI avec le champ d’URL](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
Q : Peut-on utiliser une URL personnalisée comme lien hypertexte dans un tableau ou dans une matrice ?    
R : Non. Il est possible d’utiliser une icône de lien. Si vous avez besoin d’un texte personnalisé pour vos liens hypertextes et que votre liste d’URL est courte, vous pouvez utiliser une zone de texte à la place.


## <a name="next-steps"></a>Étapes suivantes
[Visualisations dans des rapports Power BI](visuals/power-bi-report-visualizations.md)

[Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

