---
title: Se connecter à un entrepôt Snowflake Computing dans Power BI Desktop
description: Se connecter facilement à un entrepôt Snowflake Computing pour l’utiliser dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7d89ea7453a74470a73786bb8001c35db9252158
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Se connecter à Snowflake dans Power BI Desktop
Dans Power BI Desktop, vous pouvez vous connecter à un entrepôt **Snowflake Computing** et utiliser les données sous-jacentes comme n’importe quelle autre source de données dans Power BI Desktop. 

> [!NOTE]
> Vous *devez* également installer le **pilote ODBC Snowflake** sur les ordinateurs qui utilisent le connecteur **Snowflake** à l’aide de l’architecture qui correspond à l’installation de **Power BI Desktop** (32 bits ou 64 bits). Cliquez sur le lien suivant et [téléchargez le pilote ODBC Snowflake approprié](http://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Se connecter à un entrepôt Snowflake Computing
Pour vous connecter à un entrepôt **Snowflake Computing**, sélectionnez **Obtenir des données** à partir du ruban **Accueil** de Power BI Desktop. Sélectionnez **Base de données** dans les catégories à gauche pour afficher **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

Dans la fenêtre **Snowflake** qui s’affiche, tapez ou collez le nom de votre entrepôt Snowflake Computing dans la zone, puis sélectionnez **OK**. Notez que vous pouvez choisir d’**importer** des données directement dans Power BI, ou utiliser **DirectQuery**. En savoir plus sur [l’utilisation de DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Lorsque vous y êtes invité, indiquez votre nom d’utilisateur et votre mot de passe.

![](media/desktop-connect-snowflake/connect_snowflake_4.png)

> [!NOTE]
> Une fois que vous indiquez le nom d’utilisateur et le mot de passe d’un serveur **Snowflake** donné, Power BI Desktop les utilise dans les tentatives de connexion ultérieures. Pour modifier ces informations d’identification, accédez à **Fichier > Options et paramètres > Paramètres de la source de données**.
> 
> 

Une fois que vous êtes connecté, une fenêtre **Navigateur** apparaît et affiche les données disponibles sur le serveur. Vous pouvez ensuite sélectionner un ou plusieurs éléments à importer et utiliser dans **Power BI Desktop**.

![](media/desktop-connect-snowflake/connect_snowflake_5.png)

Vous pouvez **charger** la table sélectionnée, ce qui permet d’afficher la table entière dans **Power BI Desktop**, ou **modifier** la requête, ce qui permet d’ouvrir l’**éditeur de requête**. Vous pouvez ainsi filtrer et affiner l’ensemble de données que vous souhaitez utiliser, puis charger ce jeu de données affiné dans **Power BI Desktop**.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

