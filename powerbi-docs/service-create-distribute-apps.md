---
title: Publier une application dans Power BI
description: Découvrez comment publier les nouvelles applications, qui sont des collections de tableaux de bord et rapports avec des fonctionnalités de navigation.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941558"
---
# <a name="publish-an-app-in-power-bi"></a>Publier une application dans Power BI

Dans Power BI, vous pouvez créer du contenu officiel empaqueté, puis distribuer à un public plus large en tant qu’un *application*. Vous créez des applications dans des *espaces de travail d’application*, où vous pouvez collaborer sur du contenu Power BI avec vos collègues. Vous pouvez ensuite publier les applications terminées auprès de grands groupes de personnes dans votre organisation. 

![Applications Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Vos utilisateurs en entreprise ont souvent besoin de plusieurs tableaux de bord et rapports Power BI pour effectuer leur travail. Avec les applications Power BI, vous pouvez créer des collections de tableaux de bord et de rapports et publier ces applications pour toute votre organisation ou pour des personnes ou groupes spécifiques. Pour vous, en tant que créateur de rapports ou en tant qu’administrateur, les applications facilitent la gestion des autorisations sur ces collections.

Les utilisateurs obtiennent vos applications de différentes manières :

- Ils peuvent rechercher et installer votre application à partir de Microsoft AppSource
- Vous pouvez leur envoyer un lien direct.
- Vous pouvez l’installer automatiquement dans les comptes Power BI de vos collègues si l’administrateur Power BI vous y autorise.

Vous pouvez créer l’application avec son propre navigation intégrée, afin que vos utilisateurs puissent trouver facilement leur façon autour de votre contenu. Ils ne peuvent pas modifier le contenu de l’application. Ils peuvent interagir avec lui dans le service Power BI, ou une des applications mobiles- : filtrage, mise en surbrillance et triant elles-mêmes les données. Ils obtiennent les mises à jour automatiquement, et vous pouvez contrôler la fréquence à laquelle les données sont actualisées. Pour en savoir plus, voir l’[expérience d’application pour les utilisateurs professionnels](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licences pour des applications
Pour créer ou mettre à jour une application, vous avez besoin d’une licence Power BI Pro. Pour application *consommateurs*, il existe deux options.

* Option 1 : Tous les utilisateurs professionnels ont besoin de licences **Power BI Pro** pour consulter votre application. 
* Option 2 : Si votre espace de travail d’application réside dans une capacité Power BI Premium, les utilisateurs gratuits de votre organisation peuvent consulter le contenu. Pour plus de détails, consultez [Qu’est-ce que Power BI Premium ?](service-premium.md).

## <a name="publish-your-app"></a>Publier votre application
Quand les tableaux de bord et rapports de votre espace de travail sont prêts, vous choisissez les tableaux de bord et les rapports que vous voulez publier, puis vous les publiez en tant qu’application. 

1. Dans la vue de liste d’espace de travail, décidez quels tableaux de bord et les rapports que vous souhaitez **inclus dans l’application**.

     ![Sélectionner le tableau de bord à publier](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Si vous choisissez de ne pas inclure un rapport qui contient un tableau de bord associé, vous voyez un avertissement en regard du rapport. Vous pouvez toujours publier l’application, mais les vignettes de ce rapport n’auront pas le tableau de bord associé.

     ![Avertissement concernant un tableau de bord associé](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Sélectionnez le **publier l’application** bouton dans le coin supérieur droit pour démarrer le processus de création et publication d’une application à partir de l’espace de travail.
   
     ![Publier l’application](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Sur **le programme d’installation**, renseignez le nom et la description pour aider les utilisateurs à trouver l’application. Vous pouvez définir une couleur de thème pour personnaliser l’application. Vous pouvez également ajouter un lien vers un site de prise en charge.
   
     ![Générer votre application](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Sur **Navigation**, sélectionnez le contenu à publier en tant que partie de l’application. Vous ajoutez ensuite la navigation de l’application, pour organiser le contenu dans les sections. Consultez [concevoir l’expérience de navigation pour votre application](#design-the-navigation-experience-for-your-app) dans cet article pour plus d’informations.
   
     ![Navigation de l’application](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Sur **accès**, décidez qui a accès à l’application. 
    - Dans [des espaces de travail classiques](service-create-workspaces.md): tous les membres de votre organisation, des personnes spécifiques ou les groupes de sécurité Azure Active Directory (AAD).
    - Dans le [nouveaux espaces de travail expérience](service-create-the-new-workspaces.md): des personnes spécifiques, des groupes de sécurité AAD et des listes de distribution et des groupes Office 365.

6. Si vous disposez des autorisations, vous pouvez installer l’application automatiquement pour les destinataires. Un administrateur Power BI peut activer ce paramètre dans le portail d’administration Power BI. En savoir plus sur [automatiquement installation d’une application](#automatically-install-apps-for-end-users) dans cet article.

     ![Autorisations d’application](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Lorsque vous sélectionnez **publier l’application**, vous voyez un message confirmant qu’il est prêt à publier. Dans le **partager cette application** boîte de dialogue, vous pouvez copier l’URL qui est un lien direct vers cette application.
   
     ![Achèvement de l’application](media/service-create-distribute-apps/power-bi-apps-success.png)

Vous pouvez envoyer que lien direct vers les personnes que vous avez partagé avec, ou ils peuvent trouver votre application sur l’onglet applications en accédant à **télécharger et Explorer d’autres applications à partir de AppSource**. Pour en savoir plus, voir l’[expérience d’application pour les utilisateurs professionnels](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Modifier votre application publiée
Une fois votre application publiée, il se peut que vous souhaitiez la modifier ou la mettre à jour. Il est facile de mettre à jour si vous êtes un administrateur ou un membre dans le nouvel espace de travail d’application. 

1. Ouvrez l’espace de travail d’application correspondant à l’application. 
   
     ![Ouvrir l’espace de travail](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Apportez les modifications souhaitées pour les tableaux de bord ou rapports.
 
     L’espace de travail d’application étant votre zone intermédiaire, vos modifications ne sont pas visibles dans l’application tant que vous ne la republiez pas. Cela vous permet d’apporter des modifications sans affecter les applications publiées.  
 
    > [!IMPORTANT]
    > Si vous supprimez un rapport et mettre à jour de l’application, même si vous ajoutez le rapport à l’application, vos consommateurs de l’application de perdre toutes les personnalisations telles que les signets, les commentaires, etc.  
 
3. Revenez à la liste d’espace de travail applications de contenu, puis sélectionnez **mise à jour application** dans le coin supérieur droit.
   
1. Mise à jour **le programme d’installation**, **Navigation**, et **autorisations**, si vous avez besoin pour, sélectionnez **mise à jour application**.
   
Les personnes pour lesquelles vous avez publié l’application voient automatiquement la version mise à jour de celle-ci. 

## <a name="design-the-navigation-experience-for-your-app"></a>Concevoir l’expérience de navigation pour votre application
Le **nouveau générateur de navigation** option vous permet de créer une navigation personnalisée pour votre application. Le volet de navigation personnalisé rend plus facile pour vos utilisateurs rechercher et utiliser le contenu dans l’application. Les applications existantes ont cette option est désactivée et la nouvelle valeur par défaut des applications à l’option est activée.

Lorsque l’option est désactivée, vous pouvez sélectionner le **page d’accueil application** soit **contenu spécifique**, par exemple un tableau de bord ou rapport ou sélectionnez **aucun** pour afficher la liste de base contenu à l’utilisateur.

Lorsque vous activez **nouveau générateur de navigation**, vous pouvez concevoir une navigation personnalisée. Par défaut, tous les rapports, les tableaux de bord et les classeurs Excel que vous avez inclus dans votre application sont répertoriées sous forme de liste plate. 

![Navigation de l’application](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Vous pouvez personnaliser davantage le volet de navigation par application :
* Réorganisation des éléments à l’aide de la configuration / flèches de direction. 
* Renommer des éléments dans le **rapport détails**, **détails du tableau de bord**, et **détails du classeur**.
* Masquage des éléments de la barre de navigation.
* À l’aide de la **New** option permettant d’ajouter **sections** au groupe de contenu associé.
* À l’aide de la **New** option permettant d’ajouter un **lien** à une ressource externe pour le volet de navigation gauche. 

Lorsque vous ajoutez un **lien**, dans **lien Détails** vous pouvez choisir où le lien s’ouvre. Par défaut liens s’ouvrent dans le **onglet actuel**, mais vous pouvez sélectionner **nouvel onglet**, ou **zone de contenu**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Considérations sur l’utilisation de la nouvelle option de générateur de navigation
Voici les points généraux à prendre en compte lorsque vous utilisez le nouveau générateur de navigation :
* Pages de rapport sont affichés dans la zone de navigation d’application comme une section extensible
* Si vous désactivez le nouveau générateur de navigation et puis publiez ou mettre à jour votre application, vous perdez les personnalisations que vous avez apportées. Par exemple, sections, de classement, des liens et des noms personnalisés pour les éléments de navigation sont tous perdus.

Lorsque vous ajoutez des liens à la navigation de votre application et en sélectionnant l’option de la zone de contenu :
* Vérifiez que le lien peut être incorporé. Certains services bloquent l’incorporation de leur contenu dans des sites tiers tels que Power BI.
* Incorporez du contenu de service Power BI telles que des rapports ou tableaux de bord dans les autres espaces de travail n’est pas pris en charge. 
* Incorporez Power BI Report Server contenu via son natif incorporer du contenu d’URL à partir d’un déploiement sur site. Utilisez les étapes de [création de l’URL du serveur de rapports Power BI](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) pour obtenir l’URL. Sachez que les règles d’authentification standard s’appliquent, affichant le contenu nécessite une connexion VPN sur le serveur local. 
* Un avertissement de sécurité s’affiche en haut du contenu incorporé pour indiquer que le contenu n’est pas dans Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Installer automatiquement des applications pour les utilisateurs finaux
Si un administrateur vous donne des autorisations, vous pouvez installer des applications automatiquement, *envoyant* vers les utilisateurs finaux. Cette fonctionnalité push facilite la distribution des applications appropriées aux bonnes personnes ou groupes. Votre application s’affiche automatiquement dans la liste de contenu de vos utilisateurs finaux des applications. Ils n’êtes pas obligé de le retrouver à partir de Microsoft AppSource ou de suivre un lien d’installation. Voir comment les administrateurs activer [poussez des applications pour les utilisateurs finaux](service-admin-portal.md#push-apps-to-end-users) dans l’article de portail administrateur Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Comment transmettre une application automatiquement aux utilisateurs finaux
Une fois que l’administrateur vous a affecté des autorisations, vous disposez d’une nouvelle option pour **installer l’application automatiquement**. Lorsque vous activez la case à cocher et sélectionnez **publier l’application** (ou **mise à jour application**), l’application est envoyée à tous les utilisateurs ou groupes définis dans le **autorisations** section de l’application sur le **Accès** onglet.

![Autorisation de pousser les applications](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Comment les utilisateurs obtiennent les applications que vous envoyez leur
Une fois que vous envoyez une application, il s’affiche dans leur liste d’applications automatiquement. De cette façon, vous pouvez organiser les applications que des utilisateurs ou rôles de travail dans les besoins de votre organisation d’avoir à portée de main.

![Autorisation de pousser les applications](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considérations sur l’installation automatique des applications
Voici quelques points à garder à l’esprit quand vous envoyez (push) des applications à des utilisateurs finaux :

* L’installation automatique d’une application pour les utilisateurs peut prendre un certain temps. La plupart des applications qui installer immédiatement pour les utilisateurs, mais de pousser les applications peut prendre du temps.  Tout dépend du nombre d’éléments dans l’application et du nombre de personnes qui y ont accès. Nous vous recommandons de pousser les applications pendant les heures creuses et suffisamment avant que l’utilisateur en ait besoin. Vérifiez auprès de plusieurs utilisateurs avant d’envoyer une communication générale sur la disponibilité des applications.

* Actualisez le navigateur. Pour que l’application poussée apparaisse dans la liste Applications, l’utilisateur doit peut-être actualiser son navigateur, ou le fermer et le rouvrir.

* Si les utilisateurs ne voient immédiatement l’application dans la liste des applications, ils doivent actualiser ou fermez et rouvrez leur navigateur.

* Évitez de surcharger les utilisateurs. Ne poussez pas trop d’applications pour laisser la possibilité aux utilisateurs de se rendre compte de l’utilité des applications préinstallées. Il est préférable de contrôler qui peut pousser des applications pour les utilisateurs finaux afin de coordonner la planification. Établir un point de contact d’obtention des applications dans votre organisation envoyée aux utilisateurs finaux.

* Les utilisateurs invités qui n’ont pas accepté une invitation n’obtiennent pas les applications installées automatiquement pour les.  

## <a name="unpublish-an-app"></a>Annuler la publication d’une application
Tout membre d’un espace de travail d’application peut annuler la publication de l’application.

>[!IMPORTANT]
>Lorsque vous annulez la publication d’une application, les utilisateurs de l’application perdent leurs personnalisations. Ils perdent des favoris personnels, commentaires ou des abonnements associés au contenu de l’application. N’annulez la publication d’une application que si vous devez la supprimer.
> 
> 

* Dans un espace de travail d’application, sélectionnez les points de suspension ( **...** ) dans l’angle supérieur droit > **Annuler la publication d’application**.
  
     ![Annuler la publication de l’application](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Cette action désinstalle l’application pour toutes les personnes pour lesquelles vous l’avez publiée, qui cessent d’y avoir accès. Elle ne supprime ni l’espace de travail d’application ni son contenu.

## <a name="view-your-published-app"></a>Afficher votre application publiée

Quand vos consommateurs de l’application ouvre votre application, ils voient la barre de navigation que vous avez créé, au lieu du volet de navigation gauche de Power BI standard. Le volet de navigation application répertorie les rapports et les tableaux de bord dans les sections que vous avez défini. Il répertorie également les pages individuelles dans chaque rapport, plutôt que juste le nom du rapport.

![Application avec une navigation](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Étapes suivantes
* [Créer un espace de travail d’application](service-create-workspaces.md)
* [Installer et utiliser des applications dans Power BI](consumer/end-user-apps.md)
* [Applications Power BI pour des services externes](service-connect-to-services.md)
* [Portail d’administration Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
