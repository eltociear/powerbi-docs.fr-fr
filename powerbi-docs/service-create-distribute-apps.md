---
title: "Créer et publier des applications avec des tableaux de bord et des rapports dans Power BI"
description: "Découvrez comment créer et publier des applications qui sont des collections de tableaux de bord et rapports générés pour fournir des mesures clés pour votre organisation."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: maggies
ms.openlocfilehash: 29a089e13c2dd687a2caf19f43b1aae28e397a20
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="create-and-publish-apps-with-dashboards-and-reports-in-power-bi"></a>Créer et publier des applications avec des tableaux de bord et des rapports dans Power BI

Dans Power BI, vous pouvez créer des *applications* qui rassemblent des tableaux de bord et rapports associés dans un même emplacement, puis les publier pour de grands groupes de personnes au sein de votre organisation. Vous pouvez également vous connecter à des [applications Power BI pour des services externes](service-connect-to-services.md), tels que Google Analytics et Microsoft Dynamics CRM.

![Applications Power BI](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Vos utilisateurs en entreprise ont souvent besoin de plusieurs tableaux de bord et rapports Power BI pour effectuer leur travail. Les applications réunissent les éléments, de sorte qu’elles n’ont pas à mémoriser les noms et emplacements de tous ces tableaux de bord.  

Avec les applications Power BI, actuellement en préversion, vous pouvez créer des collections de tableaux de bord et de rapports, et publier ces applications pour toute votre organisation, ou pour des personnes ou groupes spécifiques. Pour vous, en tant que créateur de rapports ou en tant qu’administrateur, les applications facilitent la gestion des autorisations sur les collections de tableaux de bord.

Les utilisateurs professionnels peuvent installer ces applications à partir de Microsoft AppSource ou bien vous pouvez leur envoyer un lien direct. Ils peuvent facilement trouver et revenir à votre contenu, car celui-ci figure dans un emplacement unique. Ils obtiennent les mises à jour automatiquement, et vous pouvez contrôler la fréquence à laquelle les données sont actualisées. Pour en savoir plus, voir l’[expérience d’application pour les utilisateurs professionnels](service-install-use-apps.md).

### <a name="apps-and-organizational-content-packs"></a>Applications et packs de contenu d’organisation
Les applications sont l’évolution des packs de contenu d’organisation. Si vous avez déjà des packs de contenu d’organisation, ceux-ci continuent à fonctionner parallèlement aux applications.

À présent que vous avez une idée d’ensemble des applications, nous allons évoquer les *espaces de travail d’application* dans lesquels vous créez des applications. 

## <a name="video-apps-and-app-workspaces"></a>Vidéo : applications et espaces de travail d’application
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licences pour des applications
En tant que créateur d’application, vous avez besoin d’une licence Power BI Pro. Pour les utilisateurs de votre application, il existe deux options.

* Option 1 : tous les utilisateurs professionnels ont besoin de licences **Power BI Pro** pour consulter votre application. 
* Option 2 : les utilisateurs gratuits de votre organisation peuvent consulter le contenu de l’application si votre application se trouve dans une capacité Premium de Power BI. Pour plus de détails, consultez [Qu’est-ce que Power BI Premium ?](service-premium.md).

## <a name="app-workspaces"></a>Espaces de travail d’application
Les *espaces de travail d’application* étant les emplacements où vous créez des applications, avant de créer une application, vous devez créer un espace de travail d’application. Si vous avez déjà travaillé dans des espaces de travail de groupe Power BI, vous ne serez pas dépaysé par les espaces de travail d’application. Ils constituent l’évolution des espaces de travail de groupe, avec des zones intermédiaires et des conteneurs pour le contenu des applications. 

Vous pouvez ajouter des collègues à ces espaces de travail en tant que membres ou administrateurs. Tous les membres de l’espace de travail d’application et les administrateurs doivent disposer de licences Power BI Pro. Dans l’espace de travail, tous les membres peuvent collaborer sur des tableaux de bord, rapports et autres articles que vous prévoyez de publier pour un public plus large, voire pour votre organisation toute entière. 

Une fois le contenu prêt, vous publiez l’application. Vous pouvez envoyer un lien direct à un public plus large, ou les destinataires de votre application peuvent trouver celle-ci sous l’onglet Applications en accédant à **Télécharger et explorer d’autres applications d’AppSource**. Ces personnes ne peuvent pas modifier le contenu de l’application, mais peuvent interagir avec celle-ci dans le service Power BI ou dans l’une des applications mobiles en filtrant, en mettant en surbrillance et triant elles-mêmes les données. 

### <a name="how-are-app-workspaces-different-from-group-workspaces"></a>En quoi les espaces de travail d’application diffèrent-ils des espaces de travail de groupe ?
Tous les espaces de travail de groupe existants peuvent servir d’espaces de travail d’application, et vous pouvez publier des applications à partir de ces espaces de travail. Voici l’une des différences entre les espaces de travail d’application et les espaces de travail de groupe : vous créez un espace de travail d’application en tant qu’emplacement dédié à la création et à l’hébergement d’une application spécifique. Il existe une relation un-à-un entre l’application et le contenu de l’espace de travail de l’application. Tous le contenu de l’espace de travail de l’application figure dans celle-ci lorsque vous la publiez. 

À présent que vous comprenez ce que sont les applications et les espaces de travail d’application, commençons à créer et à publier une application. 

## <a name="create-an-app-workspace"></a>Créer un espace de travail d’application
[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

L’espace de travail étant vide, vous allez maintenant y ajouter du contenu. Notez que lorsque vous créez l’espace de travail pour la première fois, il peut se passer une heure environ avant qu’il se propage à Office 365. 

L’ajout de contenu s’apparente à l’ajout de contenu à Mon espace de travail, sauf que les autres personnes au sein de l’espace de travail peuvent également en voir le contenu et travailler dessus. Une différence importante est que, lorsque vous avez terminé, vous pouvez publier le contenu en tant qu’application. Dans l’espace de travail de l’application, vous pouvez charger des fichiers ou vous y connecter, ainsi que vous connecter à des services tiers comme vous le feriez dans Mon espace de travail. Par exemple :

* [Connectez-vous à des services](service-connect-to-services.md) tels que Microsoft Dynamics CRM, Salesforce ou Google Analytics.
* [Obtenez des données de fichiers](service-get-data-from-files.md), par exemple, de formats Excel, CSV ou Power BI Desktop (PBIX).

## <a name="add-an-image-to-your-app-optional"></a>Ajouter une image à votre application (facultatif)
Par défaut, Power BI crée un petit cercle de couleur pour votre application, contenant les initiales de celle-ci. Vous pouvez le personnaliser avec une image. Pour ajouter une image, vous avez besoin d’une licence Exchange Online.

1. Sélectionnez **Espaces de travail**, sélectionnez les points de suspension (…) en regard du nom de l’espace de travail, puis choisissez **Membres**. 
   
     ![Sélectionner les membres de l’espace de travail](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    Le compte Office 365 Outlook pour l’espace de travail s’ouvre dans une nouvelle fenêtre de navigateur.
2. Lorsque vous pointez sur le cercle de couleur dans l’angle supérieur gauche, il se transforme en une icône de crayon. Sélectionnez-la.
   
     ![Icône du crayon d’Office 365](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Sélectionnez de nouveau l’icône de crayon, puis cherchez l’image que vous souhaitez utiliser.
   
     ![Sélectionnez à nouveau le crayon](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)
4. Sélectionnez **Enregistrer**.
   
     ![Sélectionnez Enregistrer](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    L’image remplace le cercle de couleur dans la fenêtre Office 365 Outlook. 
   
     ![Image personnalisée](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    Après quelques minutes, l’image apparaît également dans l’application dans Power BI.
   
     ![Image personnalisée](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="publish-your-app"></a>Publier votre application
Lorsque les tableaux de bord et rapports dans votre espace de travail d’application sont prêts, publiez-les en tant qu’application. N’oubliez pas que vous n’avez pas à publier tous les rapports et tableaux de bord dans l’espace de travail. Vous pouvez publier uniquement ceux qui sont prêts. 

1. Dans l’affichage liste de l’espace de travail, choisissez les tableaux de bord et rapports à inclure dans l’application.

     ![Sélectionner le tableau de bord à publier](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Si vous choisissez de ne pas publier un rapport, un avertissement s’affiche en regard du rapport et du tableau de bord associé. Vous pouvez toujours publier l’application, mais le tableau de bord associé ne contiendra pas les vignettes de ce rapport.

     ![Avertissement concernant un tableau de bord associé](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

1. En haut à droite, sélectionnez le bouton **Publier l’application** pour démarrer le processus de partage de tout le contenu de cet espace de travail.
   
     ![Publier l’application](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

2. Tout d’abord, sous **Détails**, entrez la description pour aider les utilisateurs à trouver l’application. Vous pouvez définir une couleur d’arrière-plan pour personnaliser l’application.
   
     ![Détails de l’application](media/service-create-distribute-apps/power-bi-apps-details.png)

3. Ensuite, sous **Contenu**, vous voyez le contenu qui va être publié avec l’application, c’est-à-dire tout ce que vous avez sélectionné dans cet espace de travail. Vous pouvez également définir la page d’accueil de l’application, c’est-à-dire le tableau de bord ou le rapport que les utilisateurs voient en premier quand ils accèdent à celle-ci. Vous pouvez choisir **Aucun**. Dans ce cas, les utilisateurs accèdent à une liste répertoriant tout le contenu de l’application. 
   
     ![Contenu de l’application](media/service-create-distribute-apps/power-bi-apps-content.png)

4. Enfin, sous **Accès**, décidez qui a accès à l’application : soit tous les membres de l’organisation, soit des personnes spécifiques ou des groupes de sécurité Active Directory. 
   
     ![Accès à l’application](media/service-create-distribute-apps/power-bi-apps-access.png)

5. Lorsque vous sélectionnez **Terminer**, un message confirme que l’application est prête pour publication. Dans la boîte de dialogue confirmant le succès de la création de l’application, vous pouvez copier l’URL qui est le lien direct vers l’application, puis envoyer ce lien aux personnes avec lesquelles vous voulez partager celle-ci.
   
     ![Achèvement de l’application](media/service-create-distribute-apps/power-bi-apps-success.png)

Les utilisateurs pour lesquels vous avez publié l’application peuvent trouver celle-ci de deux façons. Vous pouvez leur envoyer un lien direct vers l’application, ou ils peuvent rechercher celle-ci dans Microsoft AppSource où toutes les applications qui leur sont accessibles sont visibles. Ensuite, chaque fois qu’ils accèdent à Applications, ils voient cette application dans leur liste.

Pour en savoir plus, voir l’[expérience d’application pour les utilisateurs professionnels](service-install-use-apps.md).

## <a name="change-your-published-app"></a>Modifier votre application publiée
Une fois votre application publiée, il se peut que vous souhaitiez la modifier ou la mettre à jour. Il est facile de la mettre à jour si vous êtes un administrateur ou un membre de l’espace de travail de l’application. 

1. Ouvrez l’espace de travail d’application correspondant à l’application. 
   
     ![Ouvrir l’espace de travail](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Ouvrez le tableau de bord ou le rapport. Vous voyez que vous pouvez apporter toutes les modifications de votre choix.
   
     L’espace de travail de l’application étant votre zone intermédiaire, vos modifications ne sont pas envoyées en temps réel à l’application tant que vous de republiez pas celle-ci. Cela vous permet d’apporter des modifications sans affecter les applications publiées.  
 
1. Revenez à la liste de contenu de l’espace de travail de l’application, puis sélectionnez **Mettre à jour l’application**.
   
     ![Mettre à jour le bouton d’application](media/service-create-distribute-apps/power-bi-app-update-button.png)
4. Si nécessaire, mettez à jour les options **Détails**, **Contenu** et **Accès**, puis sélectionnez **Mettre à jour l’application**.
   
     ![Mettre à jour le bouton d’application](media/service-create-distribute-apps/power-bi-app-update-complete.png)

Les personnes pour lesquelles vous avez publié l’application voient automatiquement la version mise à jour de celle-ci. 

## <a name="unpublish-an-app"></a>Annuler la publication d’une application
Tout membre d’un espace de travail d’application peut annuler la publication de l’application.

* Dans un espace de travail d’application, sélectionnez les points de suspension (**...**) dans l’angle supérieur droit > **Annuler la publication d’application**.
  
     ![Annuler la publication de l’application](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Cette action désinstalle l’application pour toutes les personnes pour lesquelles vous l’avez publiée, qui cessent d’y avoir accès. Elle ne supprime ni l’espace de travail d’application ni son contenu.

## <a name="power-bi-apps-faq"></a>Forum aux questions sur les applications Power BI
### <a name="how-are-app-workspaces-different-from-group-workspaces"></a>En quoi les espaces de travail d’application diffèrent-ils des espaces de travail de groupe ?
Avec cette publication, nous avons renommé tous les espaces de travail de groupe en espaces de travail d’application. Vous pouvez publier une application indifféremment à partir de ces deux types d’espaces de travail. Les fonctionnalités sont pour l’essentiel celles des espaces de travail de groupe. Dans les prochains mois, nous prévoyons d’apporter les améliorations suivantes aux espaces de travail d’application : 

* La création d’espaces de travail d’application n’a pas pour effet de créer des entités correspondantes dans Office 365, au contraire de la création d’espaces de travail de groupe. Vous pouvez donc créer autant d’espaces de travail d’application que vous le souhaitez sans vous inquiéter que différents groupes Office 365 soient créés en coulisses (vous pouvez toujours utiliser le OneDrive Entreprise d’un groupe Office 365 pour stocker vos fichiers). 
* Actuellement, vous pouvez ajouter uniquement des utilisateurs individuels aux listes de membres et d’administrateurs. Bientôt, vous pourrez ajouter plusieurs groupes de sécurité Active Directory ou groupes modernes à ces listes afin de faciliter la gestion.  

### <a name="how-are-apps-different-from-organizational-content-packs"></a>En quoi les applications diffèrent-elles des packs de contenu d’organisation ?
Les applications constituent une évolution et une simplification des packs de contenu, et présentent quelques différences majeures. 

* Quand des utilisateurs professionnels installent un pack de contenu, celui-ci perd son identité groupée : il s’agit simplement d’une liste de tableaux de bord et de rapports entremêlés avec d’autres tableaux de bord et rapports. En revanche, les applications conservent leur regroupement et leur identité même après installation. Les utilisateurs peuvent ainsi continuer à y accéder facilement au fil du temps.  
* Vous pouvez créer plusieurs packs de contenu à partir de tout espace de travail, mais une application a une relation un-à-un avec son espace de travail. Nous pensons que cela rend les applications plus faciles à comprendre et à gérer au fil du temps. Pour plus d’informations sur la façon dont nous prévoyons d’améliorer cet aspect, voir la section de feuille de route du blog Power BI. 
* Étant donné que nous prévoyons de déconseiller progressivement les packs de contenu d’organisation, nous vous recommandons de commencer à créer des applications dès à présent.  

### <a name="what-about-read-only-members-in-groups"></a>Qu’en est-il des membres en lecture seule dans les groupes ?
Dans les groupes, vous pouvez ajouter des membres en lecture seule qui peuvent uniquement afficher le contenu. Le principal problème lié à cette approche est qu’elle rend impossible l’ajout de groupes de sécurité en tant que membres. Avec une application, vous pouvez publier une version en lecture seule de l’espace de travail de l’application destinée à un large public, y compris à des groupes de sécurité. Vous pouvez apporter des modifications intermédiaires aux tableaux de bord et rapports dans l’application sans que cela affecte les utilisateurs finaux. Nous vous recommandons d’utiliser les applications de cette façon à l’avenir. À long terme, nous prévoyons de désapprouver également les membres en lecture seule des espaces de travail.  

## <a name="next-steps"></a>Étapes suivantes
* [Installer et utiliser des applications dans Power BI](service-install-use-apps.md)
* [Applications Power BI pour des services externes](service-connect-to-services.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

