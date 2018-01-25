---
title: "Utilisation des exemples Power BI (didacticiel)."
description: "Didacticiel : Utilisation des exemples Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 03/08/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/27/2017
ms.author: mihart
ms.openlocfilehash: d92edce9ae1332c4a0c73be5db93201c9b87dc86
ms.sourcegitcommit: d803e85bb0569f6b357ba0586f5702c20d27dac4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="the-power-bi-samples-a-tutorial"></a>Exemples Power BI (didacticiel)
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

Nous vous recommandons de commencer par lire l’article [Exemples de jeux de données Power BI](sample-datasets.md). Celui-ci présente ce qu’il vous faut savoir sur nos exemples : comment les obtenir, où les enregistrer, comment les utiliser, ainsi que certains récits que les exemples peuvent illustrer. Puis, lorsque vous avez saisi les notions de base, revenez ici.   

## <a name="about-this-tutorial"></a>À propos de ce didacticiel
Ce didacticiel explique comment importer nos exemples de packs de contenu, les ajouter au service Power BI et ouvrir le contenu. Un *pack de contenu* est un type d’exemple où le jeu de données est fourni avec un tableau de bord et un rapport. Pour télécharger les packs de contenu, utilisez **Obtenir des données**dans Power BI.

> [!NOTE]
> Ce didacticiel s’applique au service Power BI, mais pas à Power BI Desktop.
> 
> 

Le pack de contenu de l’exemple *Analyse de la vente au détail* utilisé dans ce didacticiel comprend un tableau de bord, un rapport et un jeu de données.
Pour vous familiariser avec ce pack de contenu et son scénario, nous vous recommandons de [découvrir l’exemple Analyse de la vente au détail](sample-retail-analysis.md) avant de commencer.

## <a name="get-data-in-this-case-get-a-sample-content-pack"></a>Obtenir des données (dans ce cas, obtenir un exemple de pack de contenu)
1. Ouvrez le service Power BI (app.powerbi.com) et connectez-vous.
2. Sélectionnez un espace de travail et créez un tableau de bord.  
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-create-dashboard2.png)
3. Nommez-le **Exemple Analyse de la vente au détail**.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-name-dashboard.png)
4. Sélectionnez **Obtenir des données** en bas du volet de navigation gauche. Si vous ne voyez pas l’option **Obtenir des données**, développez le volet de navigation en sélectionnant ![](media/sample-tutorial-connect-to-the-samples/expand-nav.png).
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_getdata.png)
5. Sélectionnez **Samples**(Exemples).  
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_samplesdownload.png)
6. Sélectionnez *Exemple Analyse de la vente au détail*, puis choisissez **Se connecter**.   
   
   ![](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-exactly-was-imported"></a>Quels sont les éléments importés ?
Lorsque vous sélectionnez **Se connecter** en utilisant un exemple de pack de contenu, Power BI transfère pour vous une copie de ce pack de contenu sur le cloud, à des fins de stockage. Comme la personne qui a créé le pack de contenu y a inclus un jeu de données, un rapport et un tableau de bord, vous obtenez ces éléments lorsque vous cliquez sur **Se connecter**.

1. Power BI crée le tableau de bord et le répertorie sous votre onglet **Tableaux de bord**. L’astérisque jaune (*) indique qu’il s’agit d’un nouvel élément.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dashboard.png)
2. Ouvrez l’onglet **Rapports**.  Vous pouvez constater la présence d’un nouveau rapport nommé *Exemple Analyse de la vente au détail*.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Puis consultez l’onglet **Jeux de données**.  Vous pouvez également constater la présence d’un nouveau jeu de données.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>Explorer votre nouveau contenu
À présent, vous pouvez explorer le tableau de bord, le jeu de données et le rapport. Il existe différentes manières d’accéder à vos tableaux de bord, rapports et jeux de données. Nous allons décrire l’une d’elles.  

> [!TIP]
> Vous voulez d’abord quelques conseils ?  Commencez par [découvrir l’exemple Analyse de la vente au détail](sample-retail-analysis.md) en suivant une procédure pas à pas sur cet exemple.
> 
> 

1. Revenez à l’onglet **Tableaux de bord**, puis sélectionnez le tableau de bord *Exemple Analyse de la vente au détail* pour l’ouvrir.    
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards.png)
2. Le tableau de bord s’ouvre.  Il possède de nombreuses vignettes de visualisation.
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)
3. Sélectionnez une vignette pour ouvrir le rapport sous-jacent.  Dans cet exemple, sélectionnez le graphique en aires (encadré en rose dans l’image précédente). Le rapport s’ouvre à la page contenant ce graphique en aires.
   
    ![](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Si la vignette est créée à l’aide de [Questions et réponses Power BI](power-bi-q-and-a.md), c’est la page Questions et réponses qui s’ouvre.
   > 
   > 
4. Revenez à votre onglet **Jeux de données**. Vous disposez de plusieurs options pour l’exploration de votre jeu de données.  Vous ne pouvez pas l’ouvrir et afficher toutes ses lignes et colonnes (comme dans Power BI Desktop ou Excel).  Lorsqu’un utilisateur partage un pack de contenu avec des collègues, il souhaite généralement partager des insights, et non permettre à ses collègues d’accéder directement aux données. Mais vous pouvez tout de même explorer le jeu de données.  
   
   ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon2.png)
   
   * L’une des méthodes employées pour l’exploration d’un jeu de données consiste à créer vos propres visualisations et rapports à partir de zéro.  Sélectionnez l’icône de graphique ![](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) pour ouvrir le jeu de données en mode Édition de rapports.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)
   * Une autre méthode d’exploration d’un jeu de données consiste à exécuter la fonctionnalité [Informations rapides](service-insights.md). Sélectionnez les points de suspension (...) et choisissez **Obtenir des informations**. Lorsque les informations sont prêtes, sélectionnez **Afficher les informations**.
     
       ![](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="next-steps"></a>Étapes suivantes
[Power BI - Concepts de base](service-basic-concepts.md)

[Exemples pour le service Power BI](sample-datasets.md)

[Sources de données pour Power BI](service-get-data.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

