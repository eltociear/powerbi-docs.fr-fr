---
title: "Réduire la taille d’un classeur Excel pour l’afficher dans Power BI"
description: "Réduire la taille d’un classeur Excel pour l’afficher dans Power BI"
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 9ee4dba473cf757f23a757c44d5c3ebdd887fdfc
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Réduire la taille d’un classeur Excel pour l’afficher dans Power BI
Vous pouvez charger n’importe quel classeur Excel dans Power BI à condition que sa taille ne dépasse pas 1 Go. Un classeur Excel peut être constitué de deux parties : un modèle de données et le reste du rapport, c’est-à-dire, le contenu principal des feuilles de calcul. Dans la mesure où le rapport ne dépasse pas les tailles limites suivantes, vous pouvez l’enregistrer sur **OneDrive Entreprise**, vous y connecter à partir de Power BI et l’afficher dans Excel Online :

* La taille de l’ensemble du classeur peut atteindre jusqu’à 1 Go.
* La taille du contenu principal des feuilles de calcul peut atteindre jusqu’à 10 Mo.

## <a name="what-makes-core-worksheet-contents-larger-than-10-mb"></a>Facteurs favorisant le dépassement de la taille limite de 10 Mo au niveau du contenu principal des feuilles de calcul
Voici quelques éléments qui peuvent entraîner le dépassement de la taille limite de 10 Mo au niveau du contenu principal des feuilles de calcul :

* Images.
* Cellules ombrées. [Supprimez un format d’ombrage de cellule](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e).
* Utilisation de couleurs dans les feuilles de calcul. [Supprimez un arrière-plan de feuille](https://support.office.com/en-US/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8).
* Zones de texte.
* Images clipart.

Envisagez de supprimer ces éléments, dans la mesure du possible. 

Si le rapport inclut un modèle de données, vous avez d’autres options : 

* Effacez les données dans les feuilles de calcul Excel et stockez-les plutôt dans le modèle de données. Pour plus d’informations, consultez « Effacer des données dans les feuilles de calcul » ci-dessous. 
* [Créez un modèle de données économe en mémoire](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70) pour réduire la taille globale du rapport.

Pour apporter l’une de ces modifications, vous devez modifier le classeur dans Excel.

Pour plus d’informations, consultez les [limites de taille de fichier pour les classeurs Excel dans SharePoint Online](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e).

## <a name="remove-data-from-worksheets"></a>Effacer des données dans les feuilles de calcul
Si vous importez des données dans Excel à partir de l’onglet Power Query ou Données Excel, le classeur risque de contenir les mêmes données dans le tableau Excel et dans le modèle de données. Les tableaux volumineux peuvent occasionner le dépassement de la limite de 10 Mo dans les feuilles de calcul Excel. En supprimant le tableau dans Excel et en conservant les données dans le modèle de données, vous pouvez réduire considérablement le contenu principal des feuilles de calcul du rapport. 

Si vous devez importer des données dans Excel, suivez ces conseils :

* **Dans Power Query**: effacez la zone **Charger dans la feuille de calcul** .
  
  Les données sont importées uniquement dans le modèle de données, et pas dans des feuilles de calcul Excel.
* **À partir de l’onglet Données Excel**, si vous avez précédemment coché **Table** dans l’Assistant Importation : accédez à **Connexions existantes**\> cliquez sur la connexion \> **Créer une connexion uniquement**. Supprimez le ou les tableaux d’origine créés durant l’importation initiale.
* **À partir de l’onglet Données Excel**: ne cochez pas **Table** dans la zone **Importer des données** .

## <a name="workbook-size-optimizer"></a>Optimiseur de taille de classeur
Si votre classeur contient un modèle de données, vous pouvez exécuter l’optimiseur de taille du classeur pour réduire la taille de celui-ci. [Télécharger l’optimiseur de taille de classeur](https://www.microsoft.com/en-us/download/details.aspx?id=38793).

## <a name="related-info"></a>Informations connexes
[Créer un modèle de données économe en mémoire](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Utilisation des liens OneDrive Entreprise dans Power BI Desktop](desktop-use-onedrive-business-links.md)

