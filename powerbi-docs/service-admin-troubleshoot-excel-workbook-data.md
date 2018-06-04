---
title: 'Erreur : Données introuvables dans votre classeur Excel'
description: 'Erreur : impossible de trouver des données dans votre classeur Excel'
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 90fd71c59059f1b1b2c1b7d1d2da582d228c7a88
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34242361"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Erreur : impossible de trouver des données dans votre classeur Excel

>[!NOTE]
>Cet article s’applique à Excel 2007 et versions ultérieures.

Quand vous importez un classeur Excel dans Power BI, l’erreur suivante peut s’afficher :

*Erreur : Impossible de trouver des données dans ce classeur Excel. Le format de vos données n’est peut-être pas correct. Modifiez votre classeur dans Excel, puis importez-le.*

![](media/service-admin-troubleshoot-excel-workbook-data/pbi_wecouldntfindanydata.png)

## <a name="quick-solution"></a>Solution rapide
1. Ouvrez votre classeur dans Excel en vue de le modifier.
2. Sélectionnez la plage de cellules qui contient vos données. La première ligne doit contenir vos en-têtes de colonnes (noms des colonnes).
3. Appuyez sur **Ctrl+T** pour créer une table.
4. Enregistrez le classeur.
5. Revenez à Power BI et importez de nouveau votre classeur ou, si vous travaillez dans Excel 2016 et avez enregistré votre classeur sur OneDrive Entreprise, dans Excel, cliquez sur Fichier > Publier.

## <a name="details"></a>Détails
### <a name="cause"></a>Cause
Dans Excel, vous pouvez créer une **table** hors d’une plage de cellules, ce qui facilite le tri, le filtrage et la mise en forme des données.

Quand vous importez un classeur Excel, Power BI recherche ces tables et les importe dans un jeu de données. S’il ne trouve aucune table, ce message d’erreur s’affiche.

### <a name="solution"></a>Solution
1. Ouvrez votre classeur dans Excel. 
    >[!NOTE]
    >Les images fournies proviennent d’Excel 2013. Si vous utilisez une autre version, l’aspect des fenêtres peut différer légèrement, mais la procédure reste la même.
    
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht1.png)
2. Sélectionnez la plage de cellules qui contient vos données. La première ligne doit contenir vos en-têtes de colonnes (noms des colonnes) :
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht2.png)
3. Dans le ruban, sous l’onglet **Insérer** , cliquez sur **Table**. (Ou, en guise de raccourci, appuyez sur **Ctrl+T**.)
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlwksht3.png)
4. La boîte de dialogue suivante apparaît. Assurez-vous que la case **Ma table comporte des en-têtes** est cochée, puis sélectionnez **OK**:
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xlcreatetbl.png)
5. Vos données apparaissent maintenant sous la forme d’une table :
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_trb_xltbl.png)
6. Enregistrez le classeur.
7. Revenez à Power BI. Sélectionnez Obtenir des données en bas du volet de navigation gauche.
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_getdata.png)
8. Dans la zone **Fichiers** , sélectionnez **Obtenir**.
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_getfiles.png)
9. Importez à nouveau votre classeur Excel. Cette fois-ci, l’importation doit trouver la table et réussir.
   
    Si l’importation échoue encore, faites-le nous savoir en cliquant sur **Communauté** dans le menu ? (Aide) :
   
    ![](media/service-admin-troubleshoot-excel-workbook-data/pbi_questionmenucommunity.png)
