---
title: Se connecter à une base de données Impala dans Power BI Desktop
description: Se connecter facilement à une base de données Impala et l’utiliser dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bc27f08e476b90b720368609e75099e4af325fe0
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347743"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Se connecter à une base de données Impala dans Power BI Desktop
Dans Power BI Desktop, vous pouvez vous connecter à une base de données **Impala** et utiliser les données sous-jacentes comme avec n’importe quelle autre source de données dans Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Se connecter à une base de données Impala
Pour vous connecter à une base de données **Impala** , procédez comme suit : 

1. Sélectionnez **Obtenir des données** dans le ruban **Accueil** de Power BI Desktop. 

2. Sélectionnez **Base de données** dans les catégories à gauche. Vous voyez alors **Impala**.

    ![Obtenir des données](media/desktop-connect-impala/connect_impala_2.png)

3. Dans la fenêtre **Impala** qui s’affiche, tapez ou collez le nom de votre serveur Impala dans la zone. Sélectionnez ensuite **OK**. Vous pouvez **importer** des données directement dans Power BI, ou utiliser **DirectQuery**. En savoir plus sur [l’utilisation de DirectQuery](desktop-use-directquery.md).

    ![Fenêtre d’Impala](media/desktop-connect-impala/connect_impala_3a.png)

4. Lorsque vous y êtes invité, entrez vos informations d’identification ou connectez-vous de façon anonyme. Le connecteur Impala prend en charge les authentifications anonyme, de base (nom d’utilisateur + mot de passe) et Windows.

    ![Connecteur Impala](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > Une fois que vous avez indiqué le nom d’utilisateur et le mot de passe d’un serveur **Impala** donné, Power BI Desktop utilise ces informations d'identification lors des tentatives de connexion ultérieures. Pour modifier ces informations d’identification, accédez à **Fichier > Options et paramètres > Paramètres de la source de données**.


5. Lorsque vous être connecté, une fenêtre **Navigateur** apparaît et affiche les données disponibles sur le serveur. Choisissez les éléments à importer parmi ces données et utilisez-les dans **Power BI Desktop**.

    ![Fenêtre du navigateur](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations
Quelques limitations et considérations doivent être prises en compte pour le connecteur **Impala** :

* Le connecteur Impala est pris en charge sur la passerelle de données locale en utilisant l’un des trois mécanismes d’authentification pris en charge.

## <a name="next-steps"></a>Étapes suivantes
De nombreuses sources de données sont accessibles avec Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
