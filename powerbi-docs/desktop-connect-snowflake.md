---
title: Se connecter à un entrepôt Snowflake Computing dans Power BI Desktop
description: Se connecter facilement à un entrepôt Snowflake Computing pour l’utiliser dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 23d66994e88204f56ee937a4f7887225e48a5e2f
ms.sourcegitcommit: 4359baa43ca01b179d28ec59f4e61ba8c07ee288
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75304296"
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Se connecter à Snowflake dans Power BI Desktop
Dans Power BI Desktop, vous pouvez vous connecter à un entrepôt **Snowflake Computing** et utiliser les données sous-jacentes comme n’importe quelle autre source de données dans Power BI Desktop. 

> [!NOTE]
> Vous *devez* également installer le **pilote ODBC Snowflake** sur les ordinateurs qui utilisent le connecteur **Snowflake** à l’aide de l’architecture qui correspond à l’installation de **Power BI Desktop** (32 bits ou 64 bits). Cliquez sur le lien suivant et [téléchargez le pilote ODBC Snowflake approprié](https://go.microsoft.com/fwlink/?LinkID=823762).
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

Si vous souhaitez utiliser un compte Microsoft, demandez à votre administrateur Snowflake de contacter Snowflake pour accéder à la préversion privée de cette fonctionnalité.

![Type d’authentification avec un compte Microsoft dans le connecteur Snowflake.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Une fois que vous êtes connecté, une fenêtre **Navigateur** apparaît et affiche les données disponibles sur le serveur. Vous pouvez ensuite sélectionner un ou plusieurs éléments à importer et utiliser dans **Power BI Desktop**.

![Erreur ODBC 28000 provoquant un échec de connexion.](media/desktop-connect-snowflake/connect_snowflake_5.png)

Vous pouvez **charger** la table sélectionnée, ce qui permet d’afficher la table entière dans **Power BI Desktop**, ou **modifier** la requête, ce qui permet d’ouvrir l’**éditeur de requête**. Vous pouvez ainsi filtrer et affiner l’ensemble de données que vous souhaitez utiliser, puis charger ce jeu de données affiné dans **Power BI Desktop**.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

