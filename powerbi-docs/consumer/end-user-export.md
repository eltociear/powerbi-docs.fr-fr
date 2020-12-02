---
title: Exporter des données à partir d’un visuel Power BI
description: Exportez des données à partir d’un élément visuel de rapport et d’un élément visuel de tableau de bord et affichez-les dans Excel.
author: mihart
ms.author: mihart
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 08/28/2020
LocalizationGroup: Consumers
ms.openlocfilehash: 13d8eda142896b406269f940823e702b2ca7cb3e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96391021"
---
# <a name="export-data-from-a-visual"></a>Exporter des données à partir d’un élément visuel

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Pour voir les données utilisées pour créer un visuel, [vous pouvez afficher ces données dans Power BI](end-user-show-data.md) ou les exporter vers Excel. L’option permettant d’exporter les données requiert un certain type de licence et les autorisations de modification sur le contenu. Si vous ne pouvez pas exporter, contactez votre administrateur Power BI ou votre support technique. 

L’exportation de données requiert une licence Power BI Pro, ou que le tableau de bord ou le rapport soit partagé avec vous à l’aide de la capacité Premium. Pour plus d’informations, consultez [Quelle est ma licence ?](end-user-license.md). L’auteur du rapport a peut-être désactivé l’exportation de données pour un rapport. Si vous ne pouvez pas exporter de données, contactez l’auteur du rapport.


## <a name="from-a-visual-on-a-power-bi-dashboard"></a>À partir d’un élément visuel dans un tableau de bord Power BI

1. Démarrer un tableau de bord Power BI. Ici, nous utilisons le tableau de bord de l’application ***Exemple Marketing et ventes** _. Vous pouvez [télécharger cette application sur AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample
).

    ![Tableau de bord de l’application](media/end-user-export/power-bi-dashboards.png)

2. Placez le curseur sur un visuel pour afficher _ *Autres options** (...) et cliquez pour afficher le menu Action.

    ![Le menu qui s’affiche lorsque vous sélectionnez les points de suspension](media/end-user-export/power-bi-option-menu.png)

3. Sélectionnez **Exporter au format .csv**.

4. Ce qui se passe ensuite dépend du navigateur que vous utilisez. Vous pouvez être invité à enregistrer le fichier ou voir un lien vers le fichier exporté en bas du navigateur. 

    ![Navigateur Chrome avec lien du fichier exporté](media/end-user-export/power-bi-dashboards-export.png)

5. Ouvrez le fichier dans Excel. 

    > [!NOTE]
    > Si vous n’avez pas d’autorisations sur les données, vous ne pouvez pas les exporter ou les ouvrir dans Excel.  

    ![Chiffre d’affaires total des unités dans Excel](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>À partir d’un élément visuel dans un rapport
Vous pouvez exporter des données à partir d’un élément visuel dans un rapport au format. csv ou. xlsx (Excel). 

1. Dans un tableau de bord, sélectionnez une vignette pour ouvrir le rapport sous-jacent.  Dans cet exemple, nous sélectionnons le même élément visuel que ci-dessus, *Total Units YTD Var %*. 

    ![Vignette du tableau de bord en surbrillance](media/end-user-export/power-bi-export-tile.png)

    Étant donné que cette vignette a été créée à partir de *l’exemple de rapport Marketing et ventes*, c’est ce rapport qui s’ouvre. Il s’ouvre sur la page qui contient l’élément visuel de la vignette sélectionnée. 

2. Sélectionnez le visuel dans le rapport. Remarquez le volet **Filtres** à droite. Des filtres sont appliqués à cet élément visuel. Pour en savoir plus sur les filtres, consultez [Utiliser les filtres dans un rapport](end-user-report-filter.md).

    ![Volet de filtre sélectionné](media/end-user-export/power-bi-export-filter-pane.png)


3. Sélectionnez **Plus d’options (...)** dans le coin supérieur droit de la visualisation. Choisissez **Exporter des données**.

    ![Exporter les données sélectionnées à partir de la liste déroulante](media/end-user-export/power-bi-export-reports.png)

4. Vous verrez des options pour exporter les données résumées ou les données sous-jacentes. Si vous utilisez *l’exemple d’application Marketing et ventes*, les **Données sous-jacentes** sont désactivées. Toutefois, vous pouvez rencontrer des rapports où les deux options sont activées. Voici une explication de la différence.

    **Données résumées** : sélectionnez cette option si vous voulez exporter les données pour ce que vous voyez actuellement dans le visuel.  Ce type d’exportation contient seulement les données qui ont été utilisées pour créer l’état actuel du visuel. Si des filtres sont appliqués à l’élément visuel, les données que vous exportez sont également filtrées. Par exemple, pour cet élément visuel, votre exportation inclura uniquement les données pour 2014 et la région centrale, et uniquement les données pour quatre des fabricants : VanArsdel, Natura, Aliqui et Pirum. Si votre visuel comporte des agrégats (somme, moyenne, etc.), l’exportation est également agrégée. 
  

    **Données sous-jacentes** : sélectionnez cette option si vous souhaitez exporter les données de ce que vous voyez dans l’élément visuel **plus** les données supplémentaires du jeu de données sous-jacent.  Cela peut inclure des données contenues dans le jeu de données, mais qui ne sont pas utilisées dans l’élément visuel. Si des filtres sont appliqués à l’élément visuel, les données que vous exportez sont également filtrées.  Si votre visuel comporte des agrégats (somme, moyenne, etc.), l’exportation supprime l’agrégation, essentiellement en mettant à plat les données. 

    ![Menu dans lequel vous choisissez sous-jacent ou résumé](media/end-user-export/power-bi-export-underlying.png)

5. Ce qui se passe ensuite dépend du navigateur que vous utilisez. Vous pouvez être invité à enregistrer le fichier ou vous pouvez voir un lien vers le fichier exporté en bas du navigateur. 

    ![Affichage des fichiers exportés dans le navigateur Microsoft Edge](media/end-user-export/power-bi-export-edge-screen.png)

    > [!NOTE]
    > Si vous n’avez pas d’autorisations sur les données, vous ne pouvez pas les exporter ou les ouvrir dans Excel.  


6. Ouvrez le fichier dans Excel. Comparez la quantité de données exportées aux données que nous avons exportées à partir du même élément visuel sur le tableau de bord. La différence est que cette exportation comprend les **Données sous-jacentes**. 

    ![Exemple Excel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Étapes suivantes

[Afficher les données utilisées pour créer un visuel](end-user-show-data.md)