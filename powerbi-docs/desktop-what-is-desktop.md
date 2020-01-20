---
title: Qu’est-ce que Power BI Desktop ?
description: Découvrez Power BI Desktop et comment bien démarrer avec.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 12/16/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: bd95dfcc5d621b5ae4988e187d7cc6d9478feb58
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731121"
---
# <a name="what-is-power-bi-desktop"></a>Qu’est-ce que Power BI Desktop ?

*Power BI Desktop* est une application gratuite qui s’installe sur un ordinateur local et permet de se connecter à des données, de les transformer et de les visualiser. Avec Power BI Desktop, vous pouvez vous connecter à plusieurs sources de données différentes et les combiner dans un modèle de données (ce qui s’appelle la *modélisation*). Ce modèle de données vous permet de créer des visuels et des collections de visuels que vous pouvez partager sous forme de rapports avec d’autres personnes au sein de votre organisation. La plupart des utilisateurs qui travaillent sur des projets d’informatique décisionnelle utilisent Power BI Desktop pour créer des rapports, puis le *service Power BI* pour les partager avec d’autres personnes.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Voici les utilisations les plus courantes de Power BI Desktop :

* Se connecter aux données
* Transformer et nettoyer ces données pour créer un modèle de données
* Créer des visuels, par exemple, des graphiques, qui donnent des représentations visuelles des données
* Créer des rapports correspondant à des collections de visuels, sur une ou plusieurs pages de rapport
* Partager des rapports avec d’autres utilisateurs à l’aide du service Power BI

Les personnes responsables de ces tâches sont souvent considérées comme des *analystes de données* (parfois nommés simplement *analystes*) ou des professionnels de l’informatique décisionnelle (souvent appelés *créateurs de rapports*). Toutefois, nombreux sont ceux qui ne se considèrent pas comme des analystes ou des créateurs de rapports et qui utilisent Power BI Desktop pour créer des rapports attrayants, ou pour extraire des données provenant de différentes sources, générer des modèles de données et les partager avec leurs collègues et leur organisation.

Trois vues sont disponibles dans Power BI Desktop, que vous sélectionnez sur le côté gauche du canevas. Les vues, montrées dans leur ordre d’apparition, sont les suivantes :
* **Rapport** : Dans cette vue, vous créez des rapports et des visuels ; c’est là que vous passerez la majeure partie de votre temps de création.
* **Données** : Dans cette vue, vous voyez les tables, les mesures et les autres données utilisées dans le modèle de données associé à votre rapport, et vous transformez les données pour une utilisation optimale dans le modèle du rapport.
* **Modèle** : Dans cette vue, vous pouvez afficher et gérer les relations entre les tables de votre modèle de données.

L’illustration suivante montre les trois vues, telles qu’elles apparaissent sur le côté gauche du canevas :

![Vues Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop-07.png)
 

## <a name="connect-to-data"></a>Se connecter aux données
La première chose à faire pour bien démarrer avec Power BI Desktop est de se connecter aux données. De nombreuses sources de données sont accessibles avec Power BI Desktop. 

Pour se connecter à des données :

1. Dans le ruban **Accueil**, sélectionnez **Obtenir des données** > **Plus**. 

   La fenêtre **Obtenir des données** s’affiche, indiquant le vaste éventail de catégories auxquelles Power BI Desktop peut se connecter.

   ![Obtenir des données dans Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

2. Lorsque vous sélectionnez un type de données, une fenêtre vous invite à entrer les informations, par exemple, l’URL et les informations d’identification, nécessaires pour que Power BI Desktop puisse se connecter à la source de données en votre nom.

   ![Se connecter à une base de données SQL Server dans Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

3. Une fois la connexion à une ou plusieurs sources de données établie, l’objectif est de transformer les données d’une façon pertinente.

## <a name="transform-and-clean-data-create-a-model"></a>Transformer et nettoyer les données, créer un modèle de données

Dans Power BI Desktop, vous pouvez nettoyer et transformer les données à l’aide de l’[éditeur Power Query](https://docs.microsoft.com/power-bi/desktop-query-overview) intégré. Ce dernier permet d’apporter des modifications aux données, par exemple, changer un type de données, supprimer des colonnes ou combiner des données provenant de plusieurs sources. C’est comme la sculpture : vous partez d’un gros bloc d’argile (les données), puis vous enlevez certaines parties ou en ajoutez d’autres selon les endroits, jusqu’à atteindre la forme souhaitée. 

Pour démarrer l’éditeur Power Query :

- Sélectionnez **Modifier les requêtes** > **Modifier les requêtes** à partir du ruban **Accueil**.

   La fenêtre **Éditeur Power Query** s’affiche.

   ![Éditeur Power Query dans Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Chaque étape que vous effectuez pour transformer des données (par exemple, renommer une table, transformer un type de données ou supprimer une colonne) est enregistrée par l’éditeur Power Query. Ces étapes sont effectuées chaque fois que la requête se connecte à la source de données, si bien que les données sont toujours mises en forme comme vous le spécifiez.

L’illustration suivante montre la fenêtre **Éditeur Power Query** d’une requête mise en forme et transformée en modèle.

 ![Fenêtre Éditeur Power Query](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Dès que vos données auront été mises en forme, vous pourrez créer des visuels. 

## <a name="create-visuals"></a>Créer des éléments visuels 

Une fois le modèle de données élaboré, vous pouvez faire glisser des *champs* vers le canevas de rapport pour créer des *visuels*. Un visuel est une représentation graphique des données du modèle. Power BI Desktop propose de nombreux types de visuels. Le suivant représente un histogramme simple. 

![Un visuel dans Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Pour créer ou modifier un visuel : 

- Dans le volet **Visualisations**, sélectionnez l’icône de visuel. 

   ![Volet Visualisations dans Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

   Si un visuel est déjà sélectionné sur le canevas de rapport, il devient du type sélectionné. 

   Dans le cas contraire, un nouveau visuel est créé en fonction de la sélection.


## <a name="create-reports"></a>Créer des rapports

La plupart du temps, l’objectif est de créer une collection de visuels qui indiquent différents aspects des données utilisées pour créer le modèle dans Power BI Desktop. Une collection de visuels au sein d’un fichier Power BI Desktop est appelée *rapport*. Un rapport peut comporter une ou plusieurs pages, de même qu’un fichier Excel peut être composé d’une ou plusieurs feuilles de calcul. 

Avec Power BI Desktop, vous pouvez créer des rapports complexes et riches visuellement à partir de données provenant de plusieurs sources, pour ensuite les partager avec d’autres personnes de votre organisation.

L’illustration suivante montre la première page d’un rapport Power BI Desktop, nommée **Vue d’ensemble**, comme l’indique l’onglet en bas. 

![Exemple de rapport Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Partager des rapports

Une fois que le rapport est prêt à être partagé avec d’autres utilisateurs, vous pouvez le *publier* sur le service Power BI et le mettre à la disposition de tous les collaborateurs de votre organisation qui possèdent une licence Power BI. 

Pour publier un rapport Power BI Desktop : 

1. Dans le ruban **Accueil**, sélectionnez **Publier**.

   ![Publier un rapport sur Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

   Power BI Desktop vous connecte au service Power BI avec votre compte Power BI. 

2. Power BI vous invite à sélectionner l’emplacement dans le service Power BI où vous souhaitez partager le rapport, comme votre espace de travail, un espace de travail d’équipe ou un autre emplacement dans le service Power BI. 

   Vous devez disposer d’une licence Power BI pour pouvoir partager des rapports sur le service Power BI.


## <a name="next-steps"></a>Étapes suivantes

Pour bien démarrer avec Power BI Desktop, la première chose à faire est de télécharger et d’installer l’application. Il existe deux façons d’obtenir Power BI Desktop :

* [télécharger Power BI Desktop](https://aka.ms/pbidesktopstore) sur le Windows Store.
* [télécharger Power BI Desktop sur le Web](https://docs.microsoft.com/power-bi/desktop-get-the-desktop#download-power-bi-desktop-directly) ;

