---
title: "Power BI – Concepts de base"
description: "Power BI – Concepts de base"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/31/2017
ms.author: mihart
ms.openlocfilehash: f20ea18fb46928bf7533caacf55a0cdb3d761571
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi---basic-concepts-for-power-bi-service"></a>Power BI – Concepts de base du service Power BI
<!-- Shared newnav Include -->
[!INCLUDE [newnavbydefault](./includes/newnavbydefault.md)]

Cet article suppose que vous êtes déjà [inscrit à Power BI](service-self-service-signup-for-power-bi.md) et que vous avez [ajouté des données](service-get-data.md).

Quand vous ouvrez le service Power BI, un ***tableau de bord*** s’affiche. Les tableaux de bord sont différents dans le service Power BI et dans Power BI Desktop.

![](media/service-basic-concepts/completenewer.png)

Voici les principales fonctionnalités de l’interface utilisateur du service Power BI :

1. barre de navigation
2. tableau de bord avec vignettes
3. zone Questions et réponses
4. boutons d’aide et de commentaires
5. titre du tableau de bord
6. Lanceur d’applications Office 365
7. bouton d’accueil de Power BI
8. autres actions du tableau de bord

Nous étudierons ces éléments ultérieurement, mais passons tout d’abord en revue quelques concepts propres à Power BI.

Vous pouvez également regarder cette vidéo avant de lire le reste de cet article.  Dans cette vidéo, Will passe en revue les concepts de base et propose une visite guidée du service Power BI.

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Concepts Power BI
Les 3 blocs de construction principaux de Power BI sont : les ***tableaux de bord***, les ***rapports*** et les ***jeux de données***. Vous ne pouvez pas avoir de tableaux de bord ni de rapports sans données (vous pouvez avoir des tableaux de bord et des rapports vides, mais ils ne sont pas très utiles tant qu’ils ne contiennent pas de données). Pour commencer, intéressons-nous aux **jeux de données**.

## <a name="datasets"></a>Jeux de données
Un *jeu de données* est une collection de données que vous *importez* ou auxquelles vous *vous connectez*. Power BI vous permet de vous connecter à toutes sortes de jeux de données regroupés au même endroit et de les importer dans un même emplacement.  

Dans la barre de navigation, les jeux de données auxquels vous vous êtes connecté ou que vous avez importés sont répertoriés sous le titre **Jeux de données**. Chaque jeu de données répertorié représente une source de données unique, telle qu’un classeur Excel sur OneDrive, un jeu de données tabulaires SSAS locales ou un jeu de données Salesforce. Il existe de nombreuses sources de données prises en charge différentes, et nous en ajoutons de nouvelles en permanence. [Consultez la liste des types de jeux de données qui peuvent être utilisés avec Power BI](service-get-data.md).

**UN** jeu de données…

* peut être utilisé plusieurs fois ;
* peut être utilisé dans de nombreux rapports différents ;
* peut comprendre différentes visualisations, et ces visualisations peuvent être affichées dans de nombreux tableaux de bord différents.
  
  ![](media/service-basic-concepts/drawing2.png)

Pour vous [connecter à un jeu de données](service-get-data.md) ou en importer un, sélectionnez **Obtenir des données** (au bas de la barre de navigation) ou sélectionnez l’icône Plus à côté du titre **Jeux de données**. Suivez les instructions permettant de vous connecter à la source spécifique ou de l’importer et d’ajouter le jeu de données à votre espace de travail. Les nouveaux jeux de données sont répertoriés dans la barre de navigation de gauche et sont signalés par un astérisque jaune. Le travail que vous effectuez dans Power BI ne modifie pas le jeu de données sous-jacent.

Si vous faites [partie d’un ***espace de travail d’application***](service-collaborate-power-bi-workspace.md), les jeux de données ajoutés par un membre de cet espace de travail sont accessibles par les autres membres de l’espace de travail.

Les jeux de données peuvent être actualisés, renommés, explorés et supprimés et peuvent servir à créer des rapports. Pour explorer un jeu de données, sélectionnez-le. En agissant ainsi, vous ouvrez le rapport de données dans l’éditeur de rapport, ce qui vous permet de vous pencher concrètement sur les données et de créer des visualisations. Intéressons-nous à la rubrique suivante : les rapports.

### <a name="dig-deeper"></a>Aller plus loin :
* [Qu’est-ce que Power BI Premium ?](service-premium.md)
* [Obtenir des données pour Power BI](service-get-data.md)
* [Exemples de jeux de données et de packs de contenu pour Power BI](sample-datasets.md)

## <a name="reports"></a>Rapports
Un rapport Power BI se compose d’une ou de plusieurs pages de visualisations (graphiques en courbes, en secteurs, de compartimentage, etc.). Les visualisations sont également appelées ***visuels***. Toutes les visualisations dans un rapport proviennent d’un seul jeu de données. Les rapports peuvent être créés de toutes pièces dans Power BI, peuvent être importés avec les tableaux de bord que des collègues partagent avec vous ou peuvent être créés automatiquement quand vous vous connectez à des jeux de données à partir d’Excel, de Power BI Desktop, de bases de données, d’applications SaaS et de [packs de contenu](service-organizational-content-pack-introduction.md).  Par exemple, quand vous vous connectez à un classeur Excel qui contient des feuilles Power View, Power BI crée un rapport basé sur ces feuilles. Et lorsque vous vous connectez à une application SaaS, Power BI importe un rapport prédéfini.

Il existe 2 façons d’afficher les rapports et d’interagir avec eux : le [mode Lecture](service-report-open-in-reading-view.md) et le mode [Edition](service-interact-with-a-report-in-editing-view.md).  Seuls la personne qui a créé le rapport, les copropriétaires et les personnes autorisées ont accès à l’ensemble des fonctions d’exploration, de conception, de création et de partage du ***mode Edition*** pour ce rapport. Et les personnes avec qui ils partagent le rapport peuvent explorer et interagir avec les rapports en ***mode Lecture***.   

Dans le volet de navigation, vos rapports sont répertoriés sous le titre **Rapports**. Chaque rapport répertorié représente une ou plusieurs pages de visualisations basées sur l’un des jeux de données sous-jacents. Pour ouvrir un rapport, il vous suffit de le sélectionner. Par défaut, le rapport s’ouvre d’abord en mode Lecture.  Sélectionnez **Modifier le rapport** pour l’ouvrir en Mode Édition (si vous avez les autorisations requises).  Si un tableau de bord partagé comporte des rapports, le rapport NE sera PAS répertorié dans la barre de navigation. Au lieu de cela, ouvrez des rapports partagés directement depuis le tableau de bord partagé en sélectionnant une vignette du tableau de bord (nous approfondirons ce sujet ultérieurement).

**UN** rapport…

* peut être associé à plusieurs tableaux de bord (les vignettes épinglées à partir de ce rapport peuvent apparaître sur plusieurs tableaux de bord).
* peut être créé en utilisant les données d’un jeu de données (la seule exception à cela est que Power BI Desktop peut combiner plusieurs jeux de données dans un même rapport et que ce rapport peut être importé dans Power BI).
  
  ![](media/service-basic-concepts/drawing3new.png)

## <a name="dashboards"></a>Tableaux de bord
Un *tableau de bord* est un élément que vous créez ou qu’un collègue crée et partage avec vous. Il s’agit d’un canevas unique qui contient zéro vignette et widget ou plus. Chaque vignette affiche une [visualisation](power-bi-report-visualizations.md) unique qui a été créée à partir d’un jeu de données et épinglée au tableau de bord. Il existe plusieurs façons d’ajouter des vignettes à votre tableau de bord, bien trop nombreuses pour être traitées dans cette rubrique de présentation. Pour plus d’informations, consultez [Vignettes de tableau de bord dans Power BI](service-dashboard-tiles.md). 

Dans la barre de navigation, « vos » tableaux de bord sont répertoriés sous le titre **Tableaux de bord**. « Vos » signifie que vous avez accès à ceux-ci, pas nécessairement que vous les avez créés. Chaque tableau de bord représente une vue personnalisée d’un sous-ensemble des jeux de données sous-jacents.  Si vous êtes propriétaire du tableau de bord, vous avez aussi accès aux jeux de données sous-jacents, qui figurent dans la barre de navigation sous **Jeux de données**.  Si le tableau de bord a été partagé avec vous, une icône de partage ![](media/service-basic-concepts/sharing-icon.png) est apposée en regard de celui-ci et, selon la façon dont il a été partagé, vous pouvez ou non voir les jeux de données sous-jacents répertoriés dans votre barre de navigation.

> [!NOTE]
> Les éléments épinglés et les vignettes sont traités plus en détail ci-dessous, dans la section Tableau de bord avec vignettes.
> 
> 

**UN** tableau de bord…

* peut afficher des visualisations à partir de nombreux jeux de données différents ;
* peut afficher des visualisations à partir de nombreux rapports différents
* peut afficher des visualisations épinglées à partir d’autres outils (par exemple Excel)
  
  ![](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>Aller plus loin :
**Un tableau de bord peut être [créé à de toutes pièces](service-dashboard-create.md)** : créez un tableau de bord vide, puis obtenez des données. 

**Vous ou un collègue pouvez créer un tableau de bord et [le partager](service-share-dashboards.md)** : quand vous acceptez l’invitation, le tableau de bord partagé (ainsi que le rapport et le jeu de données associés) est ajouté à votre barre de navigation. Power BI Pro est nécessaire pour partager un tableau de bord et afficher un tableau de bord partagé.

**Parfois, des tableaux de bord sont importés avec le jeu de données ou sont créés quand vous vous connectez au jeu de données**. Par exemple, l’Assistant **Obtenir des données** pour Salesforce vous demande si vous souhaitez créer un tableau de bord et/ou un rapport à partir du jeu de données. 

**Pourquoi créer des tableaux de bord ?**  En voici quelques raisons :

* Pour voir, en un coup d’œil, toutes les informations requises pour prendre des décisions.
* Pour surveiller les informations les plus importantes concernant votre activité.
* Pour vous assurer que tous vos collègues accèdent à la même page, et qu’ils consultent et utilisent les mêmes informations que vous.
* Pour surveiller la santé d’une entreprise, d’un produit, d’une unité organisationnelle, d’une campagne marketing, etc.
* Pour créer une vue personnalisée d’un tableau de bord plus large en affichant les métriques qui vous intéressent.

## <a name="my-workspace"></a>Mon espace de travail
Nous sommes revenus au tableau de bord et à l’espace de travail. Examinons plus en détail les éléments qui composent la page de destination pour le service Power BI.

![](media/service-basic-concepts/completenewer.png)

### <a name="1-navigation-bar-navbar"></a>1. **Barre de navigation**
Utilisez la barre de navigation pour vous déplacer entre les blocs de construction de Power BI : les tableaux de bord, les rapports et les jeux de données.  

  ![](media/service-basic-concepts/navpane-new.png)

* Sélectionnez **Obtenir des données** pour [ajouter des jeux de données, des rapports et des tableaux de bord à Power BI](service-get-data.md).
* Développez et réduisez la barre de navigation avec cette icône ![](media/service-basic-concepts/expand-icon.png).
* Utilisez **Rechercher** pour rechercher des éléments spécifiques dans la barre de navigation.
* Sélectionnez une icône plus ![](media/service-basic-concepts/pbi_nancy_plus.png) pour créer un nouveau tableau de bord ou obtenir un nouveau jeu de données.
* Les **tableaux de bord, rapports** et **jeux de données** répertoriés sont à votre disposition.  Les tableaux de bord partagés sont en lecture seule et affichent l’icône partagée ![](media/service-basic-concepts/sharing-icon.png).
* Les noms de tableaux de bord, rapports et jeux de données correspondent généralement au nom de fichier du jeu de données sous-jacent, mais vous pouvez [les renommer](service-rename.md).
* Cliquez avec le bouton droit sur un tableau de bord, un rapport ou un jeu de données pour afficher le menu contextuel. 
  
  ![](media/service-basic-concepts/menu.png)

Effectuez un clic simple sur

* un titre pour le réduire ou le développer ;
* un tableau de bord pour l’afficher ;
* un rapport pour l’ouvrir en mode Lecture ;
* un jeu de données pour l’explorer.

### <a name="2-dashboard-with-tiles"></a>2. **Tableau de bord avec vignettes**
Les tableaux de bord se composent de [vignettes](service-dashboard-tiles.md).  Les vignettes sont créées en mode Édition dans les rapports, dans Questions et réponses, dans d’autres tableaux de bord et peuvent être épinglées à partir d’Excel, de SSRS et bien plus encore. Un type spécial de vignette appelé [widget](service-dashboard-add-widget.md) est ajouté directement au tableau de bord. Les vignettes qui apparaissent dans un tableau de bord y ont été placées spécifiquement par un créateur/propriétaire de rapport.  Le fait d’ajouter une vignette à un tableau de bord est appelé *épinglage*.

![](media/service-basic-concepts/canvas.png)

Pour plus d’informations, consultez **Tableaux de bord** (ci-dessus).

### <a name="3-qa-question-box"></a>3. **Zone Questions et réponses**
Une manière d’explorer vos données consiste à poser une question et à laisser Q&R Power BI y répondre, sous la forme d’une visualisation. La zone Questions et réponses ne peut pas servir à ajouter du contenu à un rapport -- mais seulement à ajouter du contenu, sous la forme de vignettes, aux tableaux de bord.

La fonctionnalité Questions et réponses recherche une réponse dans le ou les jeux de données connectés au tableau de bord.  Un jeu de données connecté possède au moins une vignette épinglée à ce tableau de bord.

![](media/service-basic-concepts/qna.png)

Dès que vous commencez à taper votre question, Q&R vous conduit à la page Q&R. Au fur et à mesure que vous tapez du texte, la fonctionnalité Questions et réponses vous aide à poser la bonne question et à trouver la meilleure réponse via des reformulations, la saisie semi-automatique, des suggestions, etc. Quand vous obtenez une visualisation (réponse) qui vous satisfait, épinglez-la à votre tableau de bord. Pour plus d’informations, consultez [Q&R dans Power BI](service-q-and-a.md).

### <a name="4-full-screen-notifications-settings-downloads-help-and-feedback"></a>4. **Plein écran, Notifications, Paramètres, Téléchargements, Aide et Commentaires**
Les icônes figurant dans l’angle supérieur droit sont des ressources vous permettant de définir des configurations, des notifications, d’effectuer des téléchargements, d’obtenir de l’aide et de fournir des commentaires à l’équipe Power BI. Cliquez sur la flèche double pour ouvrir le tableau de bord en mode **Plein écran**.  

![](media/service-basic-concepts/help-new.png)

### <a name="5-dashboard-title-aka-what-dashboard-is-active"></a>5. **Titre du tableau de bord** (désigne le tableau de bord actif)
Il n’est pas toujours facile de déterminer quel tableau de bord est actif.  Le titre du tableau de bord s’affiche dans la page d’affichage de tableau de bord, dans la page Q&R, en mode Edition et en mode Lecture de rapport, et quand vous ouvrez un jeu de données.   

![](media/service-basic-concepts/dash-title-new.png)

### <a name="6-office-365-app-launcher"></a>6. **Lanceur d’applications Office 365**
Le Lanceur d’applications est conçu pour vous aider à accéder à vos applications Office 365.

![](media/service-basic-concepts/basicconcepts2-newer.png)

### <a name="7-power-bi-home"></a>7. **Accueil de Power BI**
Sélectionnez cet élément pour revenir au dernier tableau de bord affiché.

   ![](media/service-basic-concepts/version-new.png)

### <a name="8-options"></a>8. **Options**
Cette zone de l’espace de travail contient des icônes permettant d’interagir avec le tableau de bord.  En plus des options **Ajouter une vignette**, **Favoris** et **Partager**, vous pouvez utiliser le bouton de sélection (points de suspension) pour afficher les options de duplication, d’impression et d’actualisation du tableau de bord et bien plus encore.

   ![](media/service-basic-concepts/options.png)

## <a name="next-steps"></a>Étapes suivantes
[Prise en main de Power BI](service-get-started.md)  
[Vidéos Power BI](videos.md)  
[Qu’est-ce que Power BI Premium ?](service-premium.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

