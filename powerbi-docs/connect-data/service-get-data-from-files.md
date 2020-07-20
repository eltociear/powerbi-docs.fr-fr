---
title: Obtenir des données à partir de fichiers pour Power BI
description: Découvrez comment obtenir des données à partir de fichiers Excel, Power BI Desktop et CSV dans Power BI
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b7b886b5e0c21c77e0a5a6aca83fa0ae0751f435
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264120"
---
# <a name="get-data-from-files-for-power-bi"></a>Obtenir des données à partir de fichiers pour Power BI
![Icône Excel, Power BI et CSV](media/service-get-data-from-files/file_icons.png)

Dans Power BI, vous pouvez connecter ou importer des données et des rapports à partir de trois types de fichier.

* Microsoft Excel (.xlsx ou .xlsm)
* Power BI Desktop (.pbix)
* Comma Separated Value (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>Que signifie réellement obtenir des données d’un fichier ?
Dans Power BI, les données que vous explorez proviennent d’un jeu de données. Mais pour avoir un jeu de données, vous devez d’abord obtenir des données. Aux fins de cet article, nous allons nous concentrer sur l’obtention de données à partir d’un fichier.

Pour mieux comprendre l’importance des jeux de données, et la manière d’obtenir des données pour eux, prenons l’exemple d’une voiture. Prenez place et regardez le tableau de bord. C’est un peu comme si vous étiez assis devant votre ordinateur à observer un tableau de bord dans Power BI. Le tableau de bord vous indique tout ce que fait la voiture : la vitesse de rotation du moteur, la température, le rapport de boîte de vitesse enclenché, l’allure du véhicule, etc.

Dans Power BI, un jeu de données s’apparente au moteur dans votre voiture. Il vous fournit les données, les mesures et les informations affichées dans votre tableau de bord Power BI. Bien entendu, votre moteur, ou jeu de données, a besoin de carburant. Dans Power BI, il s’agit des données. Dans votre voiture, un réservoir alimente le moteur en essence. De même dans Power BI, il vous faut un réservoir contenant des données avec lesquelles vous pouvez alimenter votre jeu de données. Dans notre cas, ce réservoir est un fichier Power BI Desktop, un classeur Excel ou un fichier CSV.

On peut même ajouter un autre point de comparaison. Le réservoir d’une voiture doit être rempli d’essence. L’essence de notre fichier Power BI Desktop, Excel ou CSV est représentée par les données provenant d’une autre source de données. Nous obtenons des données d’une autre source de données et les intégrons à un fichier Excel, Power BI Desktop ou CSV. S’il s’agit d’un classeur Excel ou d’un fichier CSV, nous pouvons entrer des lignes de données manuellement. Nous pouvons également nous connecter à une source de données externe pour interroger et charger des données dans notre fichier. Une fois que nous disposons d’un fichier contenant des données, nous pouvons l’obtenir dans Power BI en tant que jeu de données.

> [!NOTE]
> Les données des classeurs Excel doivent être situées dans un tableau, ou dans le modèle de données, elles doivent être importées par Power BI.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>L’emplacement d’enregistrement de votre fichier change tout
**Local** : si votre fichier est enregistré sur un disque local sur votre ordinateur ou un autre emplacement de votre organisation, vous pouvez *importer* votre fichier à partir de Power BI. Votre fichier est en fait conservé sur votre disque local. Il n’est donc pas entièrement importé dans Power BI. En réalité, un nouveau jeu de données est créé dans votre site Power BI, et les données, et dans certains cas le modèle de données, sont chargés dans ce jeu de données. Si votre fichier contient des rapports, ceux-ci apparaissent dans votre site Power BI sous Rapports.

**OneDrive Entreprise** : si vous disposez de OneDrive Entreprise et que vous vous connectez avec le même compte que pour Power BI, cette méthode est de loin la plus efficace pour que votre travail dans Excel, Power BI Desktop ou un fichier CSV et vos jeu de données, rapports et tableaux de bord dans Power BI restent synchronisés. Power BI et OneDrive étant tous les deux dans le cloud, Power BI se connecte à votre fichier sur OneDrive toutes les heures environ. Si des modifications sont détectées, vos jeu de données, rapports et tableaux de bord sont automatiquement mis à jour dans Power BI.

**OneDrive personnel** : si vous enregistrez vos fichiers sur votre compte OneDrive personnel, vous bénéficiez de la plupart des avantages obtenus avec OneDrive Entreprise. La différence principale réside dans le fait que, la première fois que vous vous connectez à votre fichier (via Obtenir des données > Fichiers > OneDrive personnel), vous devez vous connecter à votre compte OneDrive avec votre compte Microsoft, qui est généralement différent de celui utilisé pour vous connecter à Power BI. Lorsque vous vous connectez à OneDrive avec votre compte Microsoft, veillez à sélectionner l’option Maintenir la connexion. Power BI peut ainsi se connecter à votre fichier toutes les heures environ et s’assurer que votre jeu de données dans Power BI est synchronisé.

**Sites d’équipe SharePoint** : l’enregistrement de vos fichiers Power BI Desktop sur des sites d’équipe SharePoint revient plus ou moins à enregistrer dans OneDrive Entreprise. La différence majeure réside dans la manière dont vous vous connectez au fichier à partir de Power BI. Vous pouvez spécifier une URL ou vous connecter au dossier racine.

## <a name="ready-to-get-started"></a>Prêt à vous lancer ?
Consultez les articles suivants pour en savoir plus sur l’obtention de votre fichier dans Power BI.

* [Obtenir des données de classeurs Excel](service-excel-workbook-files.md)
* [Obtenir des données de fichiers Power BI Desktop](service-desktop-files.md)
* [Obtenir des données de fichiers de valeurs séparées par des virgules](service-comma-separated-value-files.md)

