---
title: 'Erreur : Nous n’avons pas pu trouver des données dans votre classeur Excel'
description: 'Erreur : Nous n’avons pas pu trouver des données dans votre classeur Excel'
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6fb02e6cbaca30859aa00f58ae07c9a3fd7f6fe0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101466"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>Erreur : Nous n’avons pas pu trouver des données dans votre classeur Excel

>[!NOTE]  
>Cet article s’applique à Excel 2007 et versions ultérieures.

Quand vous importez un classeur Excel dans Power BI, l’erreur suivante peut s’afficher :

*Erreur : Nous n’avons pas pu trouver des données sous formatées de tableau. Pour importer à partir d’Excel dans le service Power BI, vous devez mettre en forme les données sous forme de table. Sélectionnez toutes les données que vous voulez dans le tableau et appuyez sur Ctrl + T.*

![Impossible de trouver des données dans le classeur](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

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
    
    ![Ouvrir le classeur](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. Sélectionnez la plage de cellules qui contient vos données. La première ligne doit contenir vos en-têtes de colonnes (noms des colonnes) :
   
    ![Sélectionner une plage de cellules](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. Dans le ruban, sous l’onglet **Insérer** , cliquez sur **Table**. (Ou, en guise de raccourci, appuyez sur **Ctrl+T**.)
   
    ![Insérer une table](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. La boîte de dialogue suivante apparaît. Assurez-vous que la case **Ma table comporte des en-têtes** est cochée, puis sélectionnez **OK**:
   
    ![Créer une table](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. Vos données apparaissent maintenant sous la forme d’une table :
   
    ![Données sous forme de table](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. Enregistrez le classeur.
7. Revenez à Power BI. Sélectionnez Obtenir des données en bas du volet de navigation gauche.
   
    ![Obtenir les données](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. Dans la zone **Fichiers** , sélectionnez **Obtenir**.
   
    ![Obtenir les fichiers](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Importez à nouveau votre classeur Excel. Cette fois-ci, l’importation doit trouver la table et réussir.
   
    Si l’importation échoue encore, faites-le nous savoir en cliquant sur **Communauté** dans le menu ? (Aide) :
   
    ![Lien vers la Communauté](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
