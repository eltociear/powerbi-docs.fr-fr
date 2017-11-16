---
title: "Épingler une vignette à un tableau de bord Power BI à partir d’Excel"
description: "Épinglez une vignette à un tableau de bord Power BI à partir d’Excel dans OneDrive Entreprise. Épingler des plages, des graphiques, des tableaux"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: l8JoB7w0zJA
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 855ecbe74fa4bf4ab1b1f81f22f2bab278adddb9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-excel"></a>Épingler une vignette à un tableau de bord Power BI à partir d’Excel
Avant de pouvoir épingler une vignette à partir de votre classeur Excel, connectez ce classeur au service Power BI (app.powerbi.com). La connexion d’un classeur apporte essentiellement une version en lecture seule liée de ce classeur dans le service Power BI et vous permet d’épingler des plages à des tableaux de bord. Vous pouvez même épingler une feuille de calcul entière à un tableau de bord.  
Si un classeur a été partagé avec vous, vous pouvez afficher les vignettes épinglées par le propriétaire, mais vous ne pouvez pas créer de vignettes pour le tableau de bord. 

Pour plus d’informations sur le fonctionnement conjoint d’Excel et de Power BI, consultez [Obtenir des données de classeurs Excel](http://go.microsoft.com/fwlink/?LinkID=521962).

Will présente plusieurs méthodes pour importer les données de classeurs Excel et s’y connecter.

<iframe width="560" height="315" src="https://www.youtube.com/embed/l8JoB7w0zJA" frameborder="0" allowfullscreen></iframe>

## <a name="connect-your-excel-workbook-from-onedrive-for-business-to-power-bi"></a>Connecter votre classeur Excel dans OneDrive Entreprise à Power BI
Lorsque vous choisissez **Connecter**, votre classeur apparaît dans Power BI comme il le ferait dans Excel Online. Mais contrairement à Excel Online, Power BI offre des fonctionnalités utiles pour épingler des éléments directement de vos classeurs sur vos tableaux de bord.

Vous ne pouvez pas modifier votre classeur dans Power BI. Toutefois, si vous devez apporter des modifications, vous pouvez sélectionner l’icône crayon sous l’onglet **Classeurs** de votre espace de travail, puis modifier votre classeur dans Excel Online ou l’ouvrir dans Excel sur votre ordinateur. Toutes les modifications apportées sont enregistrées dans le classeur sur OneDrive.

1. Chargez votre classeur dans votre espace OneDrive Entreprise.
2. Dans Power BI, [connectez-vous à ce classeur](service-excel-workbook-files.md)
3. Dans Power BI, le classeur est ajouté à l’onglet **Classeurs** de votre espace de travail.  L’icône ![](media/service-dashboard-pin-tile-from-excel/pbi_workbookicon.png) indique qu’il s’agit d’un classeur Excel et l’astérisque jaune indique qu’il est nouveau.
   
    Les modifications apportées au classeur dans Power BI ne sont pas enregistrées et n’affectent pas le classeur d’origine sur OneDrive Entreprise. Si vous triez, filtrez ou modifiez les valeurs dans Power BI, ces modifications ne peuvent pas être enregistrées ou épinglées. Pour mettre à jour le classeur, sélectionnez l’icône Crayon pour l’ouvrir dans Excel Online. La mise à jour dans les vignettes des modifications apportées au classeur Excel Online peut prendre quelques minutes.     
   
   ![](media/service-dashboard-pin-tile-from-excel/power-bi-workbooks.png)
4. Ouvrez le classeur dans Power BI en sélectionnant le nom du classeur.
   
   ![](media/service-dashboard-pin-tile-from-excel/power-bi-opened.png)

## <a name="pin-a-range-of-cells-to-a-dashboard"></a>Épingler une plage de cellules à un tableau de bord
Dans Power BI, vous pouvez ajouter une nouvelle [vignette de tableau de bord](service-dashboard-tiles.md) à partir d’un classeur Excel. Les plages peuvent être épinglées à partir de classeurs Excel enregistrés dans votre espace OneDrive Entreprise ou une autre bibliothèque de documents partagés dans un groupe. Elles peuvent contenir des données, graphiques, tableaux, tableaux croisés dynamiques, graphiques croisés dynamiques et autres composants Excel.

1. Mettez en surbrillance les cellules que vous souhaitez épingler au tableau de bord.
   
    ![](media/service-dashboard-pin-tile-from-excel/pbi_selectrange.png)
2. Sélectionnez l’icône ![](media/service-dashboard-pin-tile-from-excel/pbi_pintile_small.png) en forme d’épingle. 
3. Épinglez la vignette à un tableau de bord existant ou à un nouveau tableau de bord. 
   
   * Tableau de bord existant : sélectionnez le nom du tableau de bord dans la liste déroulante.
   * Nouveau tableau de bord : tapez le nom du nouveau tableau de bord.
   
   ![](media/service-dashboard-pin-tile-from-excel/pbi_dashdialog1.png)
4. Sélectionnez **Épingler**. Un message de réussite (dans l’angle supérieur droit) vous indique que la plage a été ajoutée sous forme de vignette à votre tableau de bord. 
   
    ![](media/service-dashboard-pin-tile-from-excel/power-bi-go-to-dashboard.png)
5. Sélectionnez **Accéder au tableau de bord**. Ici, vous pouvez [renommer, redimensionner, lier et déplacer](service-dashboard-edit-tile.md) la visualisation épinglée. Par défaut, la sélection de la vignette épinglée a pour effet d’ouvrir le classeur dans Power BI.

## <a name="pin-an-entire-table-or-pivot-chart-to-a-dashboard"></a>Épingler un tableau ou tableau croisé dynamique entier à un tableau de bord
Suivez les étapes ci-dessus, mais au lieu de sélectionner une plage de cellules, sélectionnez la totalité d’un tableau ou d’un tableau croisé dynamique.

Pour épingler un tableau, sélectionnez l’ensemble du tableau en incluant les en-têtes.  Pour épingler un tableau croisé dynamique, pensez à inclure toutes les parties visibles, notamment les filtres utilisés.

 ![](media/service-dashboard-pin-tile-from-excel/pbi_selecttable.png)

Une vignette créée à partir d’un tableau ou d’un tableau croisé dynamique affiche le tableau entier.  Si vous ajoutez/supprimez/filtrez les lignes ou les colonnes du classeur d’origine, elles peuvent également être ajoutées/supprimées/filtrées dans la vignette.

## <a name="view-the-workbook-linked-to-the-tile"></a>Afficher le classeur lié à la vignette
La sélection d’une vignette de classeur a pour effet d’ouvrir le classeur lié dans Power BI. Étant donné que le fichier de classeur se trouve dans l’espace OneDrive Entreprise du propriétaire, son affichage nécessite des autorisations de lecture. Si vous n’êtes pas autorisé à effectuer cette opération, vous recevez un message d’erreur.  

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
Fonctionnalités non prises en charge : Power BI utilise Excel Services pour récupérer les vignettes de classeur. Aussi, étant donné que l’API REST Excel Services ne prend pas en charge certaines fonctionnalités d’Excel, celles-ci n’apparaissent pas sur les vignettes dans Power BI. Par exemple : graphiques sparkline, mise en forme conditionnelle de jeu d’icônes et segments de temps. Pour obtenir la liste complète des fonctionnalités non prises en charge, consultez [Fonctionnalités non prises en charge dans l’API REST Excel Services](http://msdn.microsoft.com/library/office/ff394477.aspx)

## <a name="next-steps"></a>Étapes suivantes
[Partager un tableau de bord avec des liens vers un classeur Excel](service-share-dashboard-that-links-to-excel-onedrive.md)

[Obtenir des données de classeurs Excel](service-excel-workbook-files.md)

[Tableaux de bord dans Power BI](service-dashboards.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

