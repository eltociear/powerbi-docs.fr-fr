---
title: Changer les chaînes de connexion des sources de données avec PowerShell - Version de Power BI Report Server antérieure à octobre 2020
description: Changez les chaînes de connexion des sources de données à l’aide des API PowerShell - Version de Power BI Report Server antérieure à octobre 2020.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.author: maggies
ms.openlocfilehash: 9b4d31b2acc3ce7ec43bbd3fdb91df8e32c2e953
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049405"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server-pre-october-2020"></a>Changer les chaînes de connexion des sources de données dans les rapports Power BI avec PowerShell - Version de Power BI Report Server antérieure à octobre 2020


Vous pouvez modifier les chaînes de connexion à la source de données des rapports Power BI hébergés dans Power BI Report Server à l’aide de PowerShell pour interagir avec les API nécessaires. 

> [!IMPORTANT]
> Si vous utilisez la dernière version de Power BI Report Server, c’est-à-dire celle d’octobre 2020, consultez [Changer les chaînes de connexion des sources de données dans les rapports Power BI avec PowerShell - Power BI Report Server](connect-data-source-apis.md).

> [!NOTE]
> Actuellement, cette fonctionnalité ne fonctionne que pour DirectQuery. La prise en charge de l’importation et de l’actualisation des données sera bientôt disponible.

1. Installez les commandlets PowerShell Power BI Report Server. Recherchez les commandlets et les instructions d’installation sur [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

    Installez le module `ReportingServicesTools` directement à partir de [PowerShell Gallery](https://www.powershellgallery.com/packages/ReportingServicesTools/) en utilisant la commande ci-dessous.

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. Récupérez les informations de la source de données existante pour le fichier Power BI via les commandlets PowerShell :

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Pour afficher les informations de la première source de données contenue dans le rapport Power BI : 

    ```powershell
    $dataSources[0]
    ```

3. Mettez à jour la connexion et les informations d’identification si nécessaire. Si la mise à jour de la chaîne de connexion et de la source de données utilise des informations d’identification stockées, vous devez fournir le mot de passe du compte. 

    Pour mettre à jour la chaîne de connexion de la source de données :

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Pour modifier le type des informations d’identification de la source de données :

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Pour modifier le nom d’utilisateur/mot de passe de la source de données :

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Réenregistrez les informations d’identification mises à jour sur le serveur.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Étapes suivantes

[Sources de données de rapport paginé dans Power BI Report Server](connect-data-sources.md) 

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
