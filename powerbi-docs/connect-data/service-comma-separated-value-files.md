---
title: Obtenir des données de fichiers de valeurs séparées par des virgules (.csv)
description: Découvrez comment obtenir des données à partir de fichiers CSV dans Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 01bef505d48f28df869bf2be705dcda963b3d0f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403326"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Obtenir des données de fichiers de valeurs séparées par des virgules (.csv)
![Icône CSV](media/service-comma-separated-value-files/csv_icon.png)

Les fichiers de valeurs séparées par des virgules, communément appelés fichiers .csv, sont des fichiers texte simples contenant des lignes de données où les valeurs sont séparées les unes des autres par une virgule. Ces types de fichier peuvent contenir de grandes quantités de données dans un fichier de taille relativement petite, ce qui en fait une source de données idéale pour Power BI. Vous pouvez télécharger un exemple de fichier CSV [ici](https://go.microsoft.com/fwlink/?LinkID=619356).

Si vous disposez d’un fichier CSV, associez-le à votre site Power BI en tant que jeu de données où vous pouvez commencer à explorer vos données, créer des tableaux de bord et partager vos informations avec d’autres utilisateurs.

>[!TIP]
>De nombreuses organisations génèrent un fichier CSV contenant des données mises à jour tous les jours. Pour être sûr que votre jeu de données dans Power BI reste synchronisé avec votre fichier mis à jour, veillez à enregistrer le fichier dans OneDrive sous le même nom.

## <a name="where-your-file-is-saved-makes-a-difference"></a>L’emplacement d’enregistrement de votre fichier change tout
**Local** : si votre fichier CSV est enregistré sur un disque local sur votre ordinateur ou un autre emplacement de votre organisation, vous pouvez *importer* votre fichier à partir de Power BI. Votre fichier est en fait conservé sur votre disque local. Il n’est donc pas entièrement importé dans Power BI. En réalité, un nouveau jeu de données est créé dans Power BI et les données du fichier CSV sont chargées dans ce jeu de données.

**OneDrive Entreprise** : si vous disposez de OneDrive Entreprise et que vous vous connectez avec le même compte que pour Power BI, cette méthode est de loin la plus efficace pour que votre fichier CSV et vos jeu de données, rapports et tableaux de bord dans Power BI restent synchronisés. Power BI et OneDrive étant tous les deux dans le cloud, Power BI *se connecte* à votre fichier sur OneDrive toutes les heures environ. Si des modifications sont détectées, vos jeu de données, rapports et tableaux de bord sont automatiquement mis à jour dans Power BI.

**OneDrive personnel** : si vous enregistrez vos fichiers sur votre compte OneDrive personnel, vous bénéficiez de la plupart des avantages obtenus avec OneDrive Entreprise. La différence principale réside dans le fait que, la première fois que vous vous connectez à votre fichier (via Obtenir des données > Fichiers > OneDrive personnel), vous devez vous connecter à votre compte OneDrive avec votre compte Microsoft, qui est généralement différent de celui utilisé pour vous connecter à Power BI. Lorsque vous vous connectez à OneDrive avec votre compte Microsoft, veillez à sélectionner l’option Maintenir la connexion. Power BI peut ainsi se connecter à votre fichier toutes les heures environ et s’assurer que votre jeu de données dans Power BI est synchronisé.

**Sites d’équipe SharePoint** : l’enregistrement de vos fichiers Power BI Desktop sur des sites d’équipe SharePoint revient plus ou moins à enregistrer dans OneDrive Entreprise. La différence majeure réside dans la manière dont vous vous connectez au fichier à partir de Power BI. Vous pouvez spécifier une URL ou vous connecter au dossier racine.

## <a name="import-or-connect-to-a-csv-file"></a>Importer un fichier CSV ou s’y connecter
>[!IMPORTANT]
>La taille de fichier maximale que vous pouvez importer dans Power BI est de 1 gigaoctet.

1. Dans Power BI, dans le volet de navigation, cliquez sur **Obtenir des données**.
   
   ![Capture d’écran d’Obtenir des données dans Power BI Desktop, montrant le bouton dans le volet du navigateur.](media/service-comma-separated-value-files/csv_get_data_button.png)
2. Dans **Fichiers**, cliquez sur **Obtenir**.
   
   ![Capture d’écran de la boîte de dialogue Fichiers, montrant le bouton Obtenir.](media/service-comma-separated-value-files/csv_files_get.png)
3. Recherchez votre fichier.
   
   ![Capture d’écran de quatre vignettes dans le cadre de la recherche de votre fichier, montrant la sélection de Fichier local, OneDrive Entreprise, OneDrive Personnel et SharePoint.](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>Étapes suivantes
**Explorez vos données** : après avoir obtenu des données de votre fichier dans Power BI, il est temps de les explorer. Cliquez simplement avec le bouton droit sur le nouveau jeu de données, puis cliquez sur **Explorer**.

**Planifiez l’actualisation** : si votre fichier est enregistré sur un disque local, vous pouvez définir une actualisation planifiée afin que vos jeu de données et rapports dans Power BI restent à jour. Pour en savoir plus, consultez [Actualisation des données dans Power BI](refresh-data.md). Si votre fichier est enregistré dans OneDrive, Power BI synchronise automatiquement toutes les heures.

