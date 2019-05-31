---
title: Partager des rapports et des tableaux de bord Power BI avec des collègues et d’autres utilisateurs
description: Comment partager des tableaux de bord et rapports Power BI avec vos collègues au sein et à l’extérieur de votre organisation et ce que vous devez savoir sur le partage.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: cb4fdeeea228d388197c35c69d934c0bf04c8033
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374763"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Partager des rapports et des tableaux de bord Power BI avec des collègues et d’autres utilisateurs
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Power BI propose également [d’autres façons de collaborer et de distribuer des tableaux de bord et des rapports](service-how-to-collaborate-distribute-dashboards-reports.md).

![Icône Partager dans une liste de tableaux de bord favoris](media/service-share-dashboards/power-bi-share-dash-report-favorites.png)

Que vous partagiez du contenu à l’intérieur ou à l’extérieur de votre organisation, vous devez disposer d’une [licence Power BI Pro](service-features-license-type.md). Vos destinataires doivent également disposer des licences Power BI Pro, sauf si le contenu est dans un [capacité Premium](service-premium-what-is.md). 

Vous pouvez partager des tableaux de bord et rapports à différents endroits dans le service Power BI : Favoris, récents, partagés avec moi (si le propriétaire le permet), mon espace de travail ou d’autres espaces de travail. Quand vous partagez un tableau de bord ou un rapport avec des utilisateurs, ces derniers peuvent l’afficher et interagir avec, mais pas le modifier. Ils voient les mêmes données que vous dans le tableau de bord ou le rapport, sauf si la [Sécurité au niveau des lignes](service-admin-rls.md) est appliquée. Ils peuvent également le partager avec leurs collègues, si vous les y autorisez. Les personnes en dehors de votre organisation peuvent également afficher et interagissent avec le tableau de bord ou rapport, mais pas le partager. 

Vous pouvez également [partager un tableau de bord à partir de l’une des applications mobiles Power BI](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md). Toutefois, vous ne pouvez pas partager des tableaux de bord à partir de Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vidéo : Partager un tableau de bord
Regardez Amanda partager son tableau de bord avec des collègues à l’intérieur et à l’extérieur de son entreprise. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Partager un tableau de bord ou un rapport

1. Dans la liste des tableaux de bord ou des rapports, ou dans un tableau de bord ou un rapport ouvert, sélectionnez **Partage** ![Icône de partage](media/service-share-dashboards/power-bi-share-icon.png).

2. Dans la zone supérieure, entrez les adresses e-mail complètes des personnes, des groupes de distribution ou des groupes de sécurité. Vous ne pouvez pas effectuer de partage avec des listes de distribution dynamique. 
   
   Vous pouvez partager avec des personnes dont les adresses électroniques sont externes à votre organisation, mais un message d’avertissement s’affiche.
   
   ![Avertissement concernant le partage externe](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >La zone d’entrée prend en charge, au plus 100 utilisateurs ou groupes. Si vous avez besoin de partager avec un grand nombre d’utilisateurs, envisagez de créer le tableau de bord dans un espace de travail et [sa distribution en tant qu’application](service-create-distribute-apps.md).
   > 
   > 


3. Ajoutez un message si vous le souhaitez. Ceci est facultatif.
4. Pour permettre à vos collègues de partager votre contenu avec d’autres, consultez **autoriser les destinataires à partager votre tableau de bord (ou un rapport)** .
   
   Autoriser le partage par d’autres utilisateurs est appelé *repartage*. Si vous les y autorisez, les utilisateurs peuvent repartager à partir du service Power BI et des applications mobiles ou transférer le message d’invitation à d’autres membres de votre organisation. L’invitation expire après un mois. Les personnes extérieures à votre organisation ne sont pas autorisées à le partager à nouveau. En tant que propriétaire du contenu, vous pouvez désactiver la possibilité de le partager à nouveau, ou la révoquer au cas par cas. Consultez [cesser le partage ou empêcher le partage](#stop-sharing-or-stop-others-from-sharing).

5. Sélectionnez **Partager**.
   
   ![Sélectionner le bouton Partager](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI envoie une invitation par e-mail aux personnes, mais pas à des groupes, avec un lien vers le contenu partagé. Une notification **Réussite** s’affiche. 
   
   Lorsque les destinataires de votre organisation cliquent sur le lien, Power BI ajoute le tableau de bord ou le rapport à leur page de liste **Partagés avec moi**. Ils peuvent sélectionner votre nom pour voir tout le contenu que vous avez partagé avec eux. 
   
   ![Page de liste Partagés avec moi](media/service-share-dashboards/power-bi-shared-with-me-dashboards-reports.png)
   
   Lorsque des destinataires extérieurs à votre organisation cliquent sur le lien, ils voient le tableau de bord ou le rapport, mais pas sur le portail Power BI habituel. Pour plus d’informations, consultez [partager un tableau de bord ou un rapport avec des personnes extérieures à votre organisation](#share-a-dashboard-or-report-with-people-outside-your-organization).

## <a name="who-has-access-to-a-dashboard-or-report-you-shared"></a>Qui a accès à un tableau de bord ou à un rapport partagé ?
Parfois, vous devez voir les personnes que vous avez partagé avec et qui celles-ci l’ont partagé avec :

1. Dans la liste des tableaux de bord et des rapports, ou dans le tableau de bord ou le rapport proprement dit, sélectionnez **Partager** ![Icône Partager](media/service-share-dashboards/power-bi-share-icon.png). 
2. Dans le **tableau de bord partage** ou **partager le rapport** boîte de dialogue, sélectionnez **accès**.
   
    ![Boîte de dialogue Partager le tableau de bord, onglet Accès](media/service-share-dashboards/power-bi-share-dialog-access.png)

    Les personnes extérieures à votre organisation sont répertoriées en tant qu’ **Invités**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Arrêter ou empêcher le partage
Seul le propriétaire du tableau de bord ou du rapport peut activer et désactiver la possibilité de le partager de nouveau.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Si vous n’avez pas encore envoyé l’invitation de partage
* Effacer la **autoriser les destinataires à partager votre tableau de bord (ou un rapport)** case à cocher en bas de l’invitation avant de l’envoyer.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Si vous avez déjà partagé le tableau de bord ou le rapport
1. Dans la liste des tableaux de bord et des rapports, ou dans le tableau de bord ou le rapport proprement dit, sélectionnez **Partager** ![Icône Partager](media/service-share-dashboards/power-bi-share-icon.png). 
2. Dans le **tableau de bord partage** ou **partager le rapport** boîte de dialogue, sélectionnez **accès**.
   
    ![Boîte de dialogue Partager le tableau de bord, onglet Accès](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Sélectionnez le bouton de sélection ( **...** ) en regard de **Lire et repartager**, puis sélectionnez :
   
   ![Points de suspension Lire et repartager](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Lire** pour empêcher cette personne de partager avec quiconque.
   * **Supprimez l’accès** pour empêcher cette personne de voir le contenu partagé.

4. Dans le **supprimer l’accès** boîte de dialogue zone, décidez si vous souhaitez également supprimer l’accès au contenu associé, tels que les rapports et jeux de données. Si vous supprimez des éléments avec une icône d’avertissement ![icône d’avertissement Power BI](media/service-share-dashboards/power-bi-warning-icon.png), il est préférable de supprimer également le contenu associé, car elle ne s’affiche correctement.

    ![Boîte de dialogue d’avertissement de partage Power BI](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-with-people-outside-your-organization"></a>Partager un tableau de bord ou un rapport avec des personnes extérieures à l’organisation
Lorsque vous partagez avec des personnes extérieures à votre organisation, ils reçoivent un e-mail contenant un lien vers le tableau de bord partagé ou d’un rapport, ils doivent se connecter à Power BI pour voir. Si elles ne disposent pas d’une licence Power BI Pro, elles peuvent en demander une après avoir cliqué sur le lien.

Une fois, ils se connectent, ils voient le tableau de bord partagé ou le rapport dans sa propre fenêtre de navigateur, et non dans leur portail Power BI habituel. Pour accéder ultérieurement à ce tableau de bord ou un rapport, ils doivent signet le lien.

Elles ne peuvent modifier aucun contenu dans ce tableau de bord ou ce rapport. Bien qu’ils peuvent interagir avec les graphiques et modifier des filtres ou segments appliqués, ils ne peuvent pas enregistrer leurs modifications. 

Seuls les destinataires directs peuvent voir le tableau de bord ou le rapport partagé. Par exemple, si vous avez envoyé le courrier à Vicki@contoso.com, seule Vicki peut voir le tableau de bord. Aucune autre personne peut voir le tableau de bord, même s’ils ont le lien. Vicki doit utiliser la même adresse e-mail pour y accéder ; Si elle se connecte avec une autre adresse de messagerie, elle ne pourra pas accéder au tableau de bord.

Les personnes extérieures à votre organisation ne peuvent pas voir les données si la sécurité au niveau des rôles ou des lignes est établie selon les modèles tabulaires Analysis Services locaux.

Si vous envoyez un lien à partir d’une application mobile Power BI à des personnes extérieures à votre organisation, en cliquant sur le lien ouvre le tableau de bord dans un navigateur, et non dans l’application mobile Power BI.

Si vous [autoriser à modifier et gérer des utilisateurs invités externes contenu dans l’organisation](service-admin-portal.md#export-and-sharing-settings), l’expérience de consommation uniquement par défaut ne s’y applique. [En savoir plus](service-admin-azure-ad-b2b.md).

## <a name="limitations-and-considerations"></a>Considérations et limitations
Voici quelques éléments à prendre en compte avant de partager des tableaux de bord et des rapports :

* En général, vos collègues voient les mêmes données que vous dans le tableau de bord ou le rapport. Ainsi, si vous avez l’autorisation de voir plus de données qu’eux, ils pourront consulter toutes vos données dans le tableau de bord ou le rapport. Cependant, si la [Sécurité au niveau des lignes](service-admin-rls.md) est appliquée au jeu de données sous-jacent du tableau de bord ou du rapport, les informations d’identification de chaque personne sont utilisées pour déterminer à quelles données elle est autorisée à accéder.
* Tout le monde vous partagez votre tableau de bord peut le voir et interagir avec les rapports connexes dans [mode lecture](consumer/end-user-reading-view.md#reading-view). Ils ne peuvent pas créer de rapports ni enregistrer les modifications apportées aux rapports existants.
* Bien que personne ne peut voir ou télécharger le jeu de données, ils peuvent accéder le jeu de données directement à l’aide de l’analyse dans la fonctionnalité d’Excel. Un administrateur peut limiter la capacité à utiliser analyser dans Excel pour tout le monde dans un groupe. Cependant, la restriction s’applique à tous les membres de ce groupe et à chaque espace de travail auquel le groupe appartient.
* Tout le monde peut [actualiser manuellement les données](refresh-data.md).
* Si vous utilisez Office 365 pour la messagerie électronique, vous pouvez partager avec les membres d’un groupe de distribution en entrant l’adresse de messagerie associée au groupe de distribution.
* Vos collègues qui partagent votre domaine de messagerie et les collègues dont le domaine est différent mais inscrit au sein du même client, peuvent partager le tableau de bord avec d’autres utilisateurs. Par exemple, si les domaines contoso.com et contoso2.com sont enregistrés dans le même client et votre adresse de messagerie est konrads@contoso.com, puis les deux ravali@contoso.com et gustav@contoso2.com peuvent partager, tant que vous ayez autorisé ce partage.
* Si vos collègues ont déjà accès à un rapport ou tableau de bord spécifique, vous pouvez envoyer un lien direct en copiant l’URL lorsque vous êtes sur le tableau de bord ou le rapport. Par exemple : `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* De même, si vos collègues ont déjà accès à un tableau de bord spécifique, vous pouvez [envoyer un lien direct vers le rapport sous-jacent](service-share-reports.md). 
* Vous pouvez partager avec, au maximum, 100 utilisateurs ou groupes dans une action de partage unique. Toutefois, vous pouvez permettre à plus de 500 utilisateurs d’accéder à un élément. Pour ce faire, vous pouvez partager plusieurs fois en spécifiant les utilisateurs individuellement ou partager avec un groupe d’utilisateurs qui contient tous les utilisateurs.

## <a name="troubleshoot-sharing"></a>Résoudre les problèmes de partage

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Les destinataires de mon tableau de bord voient une icône de verrou dans une vignette ou un message « Autorisation requise »

Les destinataires du partage peuvent voir une vignette verrouillée dans un tableau de bord ou un message « Autorisation requise » lorsqu’ils tentent de consulter un rapport.

![Vignette verrouillée Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

Dans ce cas, vous devez leur accorder l’autorisation au jeu de données sous-jacent :

1. Accédez à l’onglet **Jeux de données** dans votre liste de contenu.

1. Sélectionnez les points de suspension ( **...** ) en regard du jeu de données, puis **gérer les autorisations**.

    ![Gérer les autorisations](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Sélectionnez **Ajouter un utilisateur**.

    ![Sélectionnez Ajouter un utilisateur](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Entrez les adresses e-mail complètes des personnes, des groupes de distribution ou des groupes de sécurité. Vous ne pouvez pas effectuer de partage avec des listes de distribution dynamique.

    ![Ajoutez les adresses e-mail](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Sélectionnez **Ajouter**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Je n’arrive pas à partager un tableau de bord ou un rapport

Pour partager un tableau de bord ou un rapport, vous devez avoir l’autorisation de partager le contenu sous-jacent ; Autrement dit, les rapports et associés des groupes de données. Si vous voyez un message indiquant que vous ne pouvez pas partager, demandez à l’auteur du rapport afin de donner l’autorisation de ces rapports et les jeux de données partager à nouveau.

![Message « Impossible de partager »](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Étapes suivantes
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.
* [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un rapport Power BI filtré](service-share-reports.md).
* Vous avez des questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

