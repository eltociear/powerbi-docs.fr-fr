---
title: Changer les chaînes de connexion de source de données avec PowerShell
description: Modifiez les chaînes de connexion de la source de données à l’aide des API dans PowerShell - Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: maggies
ms.openlocfilehash: 9ca5d47a938210c10903c916c54713b89923e287
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80751538"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Modifier les chaînes de connexion de la source de données dans les rapports Power BI avec PowerShell - Power BI Report Server


Vous pouvez modifier les chaînes de connexion de la source de données dans les rapports Power BI dans Power BI Report Server à l’aide des API dans PowerShell. 

> [!NOTE]
> Actuellement, cette fonctionnalité ne fonctionne que pour DirectQuery. La prise en charge de l’importation et de l’actualisation des données sera bientôt disponible.

1. Installez les commandlets PowerShell Power BI Report Server. Recherchez les commandlets et les instructions d’installation sur [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

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
