---
title: Changer les chaînes de connexion de source de données avec PowerShell
description: Modifiez les chaînes de connexion de la source de données à l’aide des API dans PowerShell - Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.author: maggies
ms.openlocfilehash: 165d38c718377ff7e47442cdf0fe67173b610bd8
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044902"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Modifier les chaînes de connexion de la source de données dans les rapports Power BI avec PowerShell - Power BI Report Server


Depuis la version d’octobre 2020 de Power BI Report Server, nous fournissons la possibilité de mettre à jour les connexions des rapports Power BI pour DirectQuery et de les actualiser.

> [!IMPORTANT]
> Cette fonctionnalité constitue également un changement cassant par rapport aux versions précédentes. Si vous utilisez une version de Power BI Report Server antérieure à celle d’octobre 2020, consultez [Changer les chaînes de connexion de la source de données dans les rapports Power BI avec PowerShell - Version de Power BI Report Server antérieure à octobre 2020](connect-data-source-apis-pre-oct-2020.md).

## <a name="prerequisites"></a>Prérequis :
- Télécharger la version d’octobre 2020 de [Power BI Report Server et de Power BI Desktop optimisé pour Power BI Report Server](https://powerbi.microsoft.com/report-server/).
- Un rapport enregistré avec la version d’octobre 2020 de Power BI Desktop optimisé pour Report Server, avec les **métadonnées de jeu de données avancées** activées.
- Un rapport qui utilise des connexions paramétrables. Seuls les rapports avec des connexions et des bases de données paramétrables peuvent être mis à jour après la publication.
- Cet exemple utilise les outils PowerShell Reporting Services. Vous pouvez obtenir le même résultat en utilisant les nouvelles API REST.

## <a name="create-a-report-with-parameterized-connections"></a>Créer un rapport avec des connexions paramétrables
    
1. Établissez une connexion SQL Server avec un serveur. Dans l’exemple ci-dessous, nous allons connecter le serveur localhost à une base de données nommée ReportServer, et tirer (pull) les données depuis ExecutionLog.

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="Se connecter à une base de données SQL Server":::

    Voici à quoi ressemble la requête M :

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Sélectionnez **Gérer les paramètres** dans le ruban de l’éditeur Power Query.

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="Sélectionner Gérer les paramètres":::

1.  Créez des paramètres pour le nom du serveur et le nom de la base de données.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="Gérer les paramètres - Définition du nom du serveur et du nom de la base de données.":::


3. Modifiez la requête pour la première connexion, puis mappez le nom de la base de données et celui du serveur.

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="Mapper le nom du serveur et de la base de données":::

    La requête ressemble à ceci :

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. Publiez ce rapport sur le serveur. Dans cet exemple, le rapport se nomme executionlogparameter. L’image suivante est un exemple de page de gestion des sources de données.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="Page de gestion des sources de données.":::

## <a name="update-parameters-using-the-powershell-tools"></a>Mettre à jour les paramètres à l’aide des outils PowerShell

1. Ouvrez PowerShell et installez les derniers outils Reporting Services, en suivant les instructions fournies ici : [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools).
    
2.  Pour obtenir le paramètre du rapport, utilisez la nouvelle API REST DataModelParameters à l’aide de l’appel PowerShell suivant :

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. Nous enregistrons le résultat de cet appel dans une variable :

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. Cette variable est mise à jour avec les valeurs que vous devez changer.
5. Nous enregistrons le résultat de cet appel dans une variable :

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. Avec les valeurs mises à jour, nous pouvons utiliser l’applet de commande `Set-RsRestItemDataModelParameters` pour mettre à jour les valeurs du serveur :

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. Une fois les paramètres mis à jour, le serveur met à jour toutes les sources de données qui étaient liées aux paramètres. Dans la boîte de dialogue **Modifier la source de données** , vous devriez pouvoir définir les informations d’identification du serveur et de la base de données mis à jour.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="Définir les informations d’identification du serveur et de la base de données mis à jour.":::

## <a name="next-steps"></a>Étapes suivantes

[Sources de données de rapport paginé dans Power BI Report Server](connect-data-sources.md) 

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
