---
title: Se connecter à une base de données Impala dans Power BI Desktop
description: Se connecter facilement à une base de données Impala et l’utiliser dans Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bef087b485573ba9a629887bfb05d875c88c8b4c
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Se connecter à une base de données Impala dans Power BI Desktop
Dans Power BI Desktop, vous pouvez vous connecter à une base de données **Impala** et utiliser les données sous-jacentes comme n’importe quelle autre source de données dans Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Se connecter à une base de données Impala
Pour vous connecter à une base de données **Impala**, sélectionnez **Obtenir des données** dans le ruban **Accueil** de Power BI Desktop. Sélectionnez **Base de données** dans les catégories à gauche pour afficher **Impala**.

![](media/desktop-connect-impala/connect_impala_2.png)

Dans la fenêtre **Impala** qui s’affiche, tapez ou collez l’URL de votre serveur Impala dans la zone, puis sélectionnez **OK**. Notez que vous pouvez choisir d’**importer** des données directement dans Power BI, ou utiliser **DirectQuery**. En savoir plus sur [l’utilisation de DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-impala/connect_impala_3a.png)

Lorsque vous y êtes invité, indiquez votre nom d’utilisateur et votre mot de passe ou connectez-vous de façon anonyme. Ces deux options sont prises en charge.

![](media/desktop-connect-impala/connect_impala_4.png)

> [!NOTE]
> Une fois que vous indiquez le nom d’utilisateur et le mot de passe d’un serveur **Impala** donné, Power BI Desktop les utilise dans les tentatives de connexion ultérieures. Pour modifier ces informations d’identification, accédez à **Fichier > Options et paramètres > Paramètres de la source de données**.
> 
> 

Une fois que vous êtes connecté, une fenêtre **Navigateur** apparaît et affiche les données disponibles sur le serveur. Vous pouvez ensuite sélectionner un ou plusieurs éléments à importer et utiliser dans **Power BI Desktop**.

![](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations
Il existe quelques limites et considérations à prendre en compte pour le connecteur **Impala** :

* À l’avenir, nous prévoyons d’activer l’actualisation du support à l’aide de **Power BI Gateway**.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

