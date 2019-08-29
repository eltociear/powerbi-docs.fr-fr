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
ms.date: 08/19/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: da7b8999dfb6185b044960dde7795008d7e716f7
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69655128"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>Partager des rapports et des tableaux de bord Power BI avec des collègues et d’autres utilisateurs
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Power BI propose également [d’autres façons de collaborer et de distribuer des tableaux de bord et des rapports](service-how-to-collaborate-distribute-dashboards-reports.md).

![Icône Partager dans une liste des tableaux de bord](media/service-share-dashboards/power-bi-share-new-look.png)

Que vous partagiez du contenu à l’intérieur ou à l’extérieur de votre organisation, vous devez disposer d’une [licence Power BI Pro](service-features-license-type.md). Vos destinataires ont également besoin d’une licence Power BI Pro à moins que le contenu ne soit au niveau de [capacité Premium](service-premium-what-is.md). 

Vous pouvez partager des tableaux de bord et des rapports à partir de la plupart des emplacements du service Power BI : Favoris, Récents, Partagés avec moi (si le propriétaire le permet), Mon espace de travail ou d’autres espaces de travail. Quand vous partagez un tableau de bord ou un rapport avec des utilisateurs, ces derniers peuvent l’afficher et interagir avec, mais pas le modifier. Ils voient les mêmes données que vous dans le tableau de bord ou le rapport, sauf si la [Sécurité au niveau des lignes](service-admin-rls.md) est appliquée. Ils peuvent également le partager avec leurs collègues, si vous les y autorisez. Les utilisateurs qui ne font pas partie de votre organisation peuvent également consulter le tableau de bord ou le rapport et interagir avec celui-ci, mais pas le partager. 

Vous ne pouvez pas partager des tableaux de bord à partir de Power BI Desktop. Toutefois, vous pouvez [partager un tableau de bord à partir de l’une des applications mobiles Power BI](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md).  

## <a name="video-share-a-dashboard"></a>Vidéo : Partager un tableau de bord
Regardez Amanda partager le tableau de bord avec des collègues à l’intérieur et à l’extérieur de son entreprise. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>Partager un tableau de bord ou un rapport

1. Dans la liste des tableaux de bord ou des rapports, ou dans un tableau de bord ou un rapport ouvert, sélectionnez **Partage** ![Icône de partage](media/service-share-dashboards/power-bi-share-icon.png).

2. Dans la zone supérieure, entrez les adresses e-mail complètes des personnes, des groupes de distribution ou des groupes de sécurité. Vous ne pouvez pas effectuer de partage avec des listes de distribution dynamique. 
   
   Vous pouvez partager avec des personnes dont les adresses électroniques sont externes à votre organisation, mais un message d’avertissement s’affiche.
   
   ![Avertissement concernant le partage externe](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >La zone d’entrée prend en charge au maximum 100 utilisateurs ou groupes. Si vous devez partager le tableau de bord avec un grand nombre d’utilisateurs, pensez à le créer dans un espace de travail et à le [distribuer en tant qu’application](service-create-distribute-apps.md).
   > 
   > 


3. Ajoutez un message si vous le souhaitez. Ceci est facultatif.
4. Pour permettre à vos collègues de partager votre contenu avec d’autres personnes, cochez la case **Autoriser les destinataires à partager votre tableau de bord (ou rapport)** .
   
   Autoriser le partage par d’autres utilisateurs est appelé *repartage*. Si vous les y autorisez, les utilisateurs peuvent repartager à partir du service Power BI et des applications mobiles ou transférer le message d’invitation à d’autres membres de votre organisation. L’invitation expire après un mois. Les personnes extérieures à votre organisation ne sont pas autorisées à le partager à nouveau. En tant que propriétaire du contenu, vous pouvez désactiver la possibilité de le partager à nouveau, ou la révoquer au cas par cas. Consultez [Arrêter ou empêcher le partage](#stop-sharing-or-stop-others-from-sharing).

5. Si vous sélectionnez **Autoriser les utilisateurs à générer du nouveau contenu à partir des jeux de données sous-jacents**, ils peuvent créer leurs propres rapports dans d’autres espaces de travail en fonction du jeu de données de ce tableau de bord.

1. Sélectionnez **Partager**.
   
   ![Sélectionner le bouton Partager](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI envoie à des personnes (et non à des groupes) un e-mail d’invitation contenant un lien vers le contenu partagé. Une notification **Réussite** s’affiche. 
   
   Lorsque les destinataires de votre organisation cliquent sur le lien, Power BI ajoute le tableau de bord ou le rapport à leur page de liste **Partagés avec moi**. Ils peuvent sélectionner votre nom pour voir tout le contenu que vous avez partagé avec eux. 
   
   ![Page de liste Partagés avec moi](media/service-share-dashboards/power-bi-shared-with-me-new-look.png)
   
   Lorsque des destinataires extérieurs à votre organisation cliquent sur le lien, ils voient le tableau de bord ou le rapport, mais pas sur le portail Power BI habituel. Pour plus d’informations, consultez [Partager un tableau de bord ou un rapport avec des personnes extérieures à l’organisation](#share-a-dashboard-or-report-outside-your-organization).

## <a name="see-who-has-access-to-a-dashboard-or-report"></a>Découvrez qui a accès à un tableau de bord ou à un rapport
Il est parfois utile de voir avec qui vous avez partagé un contenu, et avec qui ces utilisateurs l’ont partagé :

1. Dans la liste des tableaux de bord et des rapports, ou dans le tableau de bord ou le rapport proprement dit, sélectionnez **Partager** ![Icône Partager](media/service-share-dashboards/power-bi-share-icon.png). 
2. Dans la boîte de dialogue **Partager un tableau de bord** ou **Partager un rapport**, sélectionnez **Accès**.
   
    ![Boîte de dialogue Partager le tableau de bord, onglet Accès](media/service-share-dashboards/power-bi-share-dialog-access.png)

    Les personnes extérieures à votre organisation sont répertoriées en tant qu’ **Invités**.

## <a name="stop-sharing-or-stop-others-from-sharing"></a>Arrêter ou empêcher le partage
Seul le propriétaire du tableau de bord ou du rapport peut activer et désactiver la possibilité de le partager de nouveau.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Si vous n’avez pas encore envoyé l’invitation de partage
* Décochez la case **Autoriser les destinataires à partager le tableau de bord (ou rapport)** en bas de l’invitation avant de l’envoyer.

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>Si vous avez déjà partagé le tableau de bord ou le rapport
1. Dans la liste des tableaux de bord et des rapports, ou dans le tableau de bord ou le rapport proprement dit, sélectionnez **Partager** ![Icône Partager](media/service-share-dashboards/power-bi-share-icon.png). 
2. Dans la boîte de dialogue **Partager un tableau de bord** ou **Partager un rapport**, sélectionnez **Accès**.
   
    ![Boîte de dialogue Partager le tableau de bord, onglet Accès](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Sélectionnez le bouton de sélection ( **...** ) en regard de **Lire et repartager**, puis sélectionnez :
   
   ![Points de suspension Lire et repartager](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Lire** pour empêcher cette personne de partager avec quiconque.
   * **Supprimez l’accès** pour empêcher cette personne de voir le contenu partagé.

4. Dans la boîte de dialogue **Supprimer l’accès**, décidez si vous voulez également supprimer l’accès au contenu associé, tel que les rapports et les jeux de données. Si vous supprimez des éléments dotés d’une icône d’avertissement ![icône d’avertissement Power BI](media/service-share-dashboards/power-bi-warning-icon.png), il est recommandé de supprimer également le contenu associé, car il ne s’affichera pas correctement.

    ![Boîte de dialogue d’avertissement de partage Power BI](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-outside-your-organization"></a>Partager un tableau de bord ou un rapport hors de l’organisation
Quand vous partagez un tableau de bord ou un rapport avec des personnes extérieures à votre organisation, celles-ci reçoivent un e-mail contenant le lien vers le contenu partagé auquel elles doivent se connecter pour accéder à Power BI. Si elles ne disposent pas d’une licence Power BI Pro, elles peuvent en demander une après avoir cliqué sur le lien.

Une fois connectées, elles verront apparaître le tableau de bord ou le rapport partagés dans leur propre fenêtre de navigateur, et non sur leur portail Power BI habituel. Pour accéder ultérieurement à ce tableau de bord ou à ce rapport, elles doivent ajouter un signet pour le lien.

Elles ne peuvent modifier aucun contenu dans ce tableau de bord ou ce rapport. Même si elles peuvent interagir avec les graphiques et modifier les filtres ou les segments, elles ne peuvent pas enregistrer leurs modifications. 

Seuls les destinataires directs peuvent voir le tableau de bord ou le rapport partagé. Par exemple, si vous avez envoyé le courrier à Vicki@contoso.com, seule Vicki peut voir le tableau de bord. Personne d’autre ne peut voir le tableau de bord, même s’il en possède le lien. Vicki doit utiliser la même adresse e-mail pour y accéder. Si une personne s’inscrit avec une autre adresse e-mail, elle n’a pas accès au tableau de bord.

Les personnes extérieures à votre organisation ne peuvent pas voir les données si la sécurité au niveau des rôles ou des lignes est établie selon les modèles tabulaires Analysis Services locaux.

Si vous envoyez un lien à partir d’une application mobile Power BI à des personnes extérieures à votre organisation, le fait de cliquer sur le lien ouvre le tableau de bord dans un navigateur, et pas dans l’application mobile Power BI.

Si vous [autorisez les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](service-admin-portal.md#export-and-sharing-settings), l’expérience par défaut de consommation uniquement ne s’applique pas à eux. [En savoir plus](service-admin-azure-ad-b2b.md).

## <a name="limitations-and-considerations"></a>Considérations et limitations
Voici quelques éléments à prendre en compte avant de partager des tableaux de bord et des rapports :

* En général, vos collègues voient les mêmes données que vous dans le tableau de bord ou le rapport. Ainsi, si vous avez l’autorisation de voir plus de données qu’eux, ils pourront consulter toutes vos données dans le tableau de bord ou le rapport. Cependant, si la [Sécurité au niveau des lignes](service-admin-rls.md) est appliquée au jeu de données sous-jacent du tableau de bord ou du rapport, les informations d’identification de chaque personne sont utilisées pour déterminer à quelles données elle est autorisée à accéder.
* Tous les utilisateurs avec qui vous partagez le tableau de bord peuvent le voir et interagir avec les rapports associés en [mode Lecture](consumer/end-user-reading-view.md#reading-view). Ils ne peuvent pas créer de rapports ni enregistrer les modifications apportées aux rapports existants.
* Même si les utilisateurs ne peuvent pas voir ni télécharger le jeu de données, ils peuvent y accéder directement à l’aide de la fonctionnalité Analyser dans Excel. Un administrateur peut limiter la capacité à utiliser Analyser dans Excel pour tous les membres d’un groupe. Cependant, la restriction s’applique à tous les membres de ce groupe et à chaque espace de travail auquel le groupe appartient.
* Tout le monde peut [actualiser manuellement les données](refresh-data.md).
* Si vous utilisez Office 365 pour la messagerie électronique, vous pouvez partager avec les membres d’un groupe de distribution en entrant l’adresse de messagerie associée au groupe de distribution.
* Les collègues qui partagent votre domaine de courrier, ainsi que les collègues dont le domaine est différent, mais inscrit auprès du même locataire, peuvent partager le tableau de bord avec d’autres utilisateurs. Par exemple, si les domaines contoso.com et contoso2.com sont enregistrés dans le même locataire et que votre adresse e-mail est konrads@contoso.com, alors ravali@contoso.com et gustav@contoso2.com peuvent partager du contenu, sous réserve que vous leur donniez l’autorisation de partage.
* Si vos collègues ont déjà accès à un tableau de bord ou à un rapport spécifique, vous pouvez envoyer un lien direct en copiant l’URL qui s’affiche quand vous vous trouvez dessus. Par exemple : `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* De même, si vos collègues ont déjà accès à un tableau de bord spécifique, vous pouvez [envoyer un lien direct vers le rapport sous-jacent](service-share-reports.md). 
* Vous pouvez partager du contenu avec au maximum 100 utilisateurs ou groupes lors d’une seule action de partage. Toutefois, vous pouvez permettre à plus de 500 utilisateurs d’accéder à un élément. Pour ce faire, partagez plusieurs fois en définissant les utilisateurs individuellement, ou partagez avec un groupe d’utilisateurs qui contient tous les utilisateurs.

## <a name="troubleshoot-sharing"></a>Résoudre les problèmes de partage

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>Les destinataires de mon tableau de bord voient une icône de verrou dans une vignette ou un message « Autorisation requise »

Les destinataires du partage peuvent voir une vignette verrouillée dans un tableau de bord ou un message « Autorisation requise » lorsqu’ils tentent de consulter un rapport.

![Vignette verrouillée Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

Dans ce cas, vous devez leur accorder l’autorisation d’accès au jeu de données sous-jacent :

1. Accédez à l’onglet **Jeux de données** dans votre liste de contenu.

1. Sélectionnez les points de suspension ( **...** ) en regard du jeu de données, puis **Gérer les autorisations**.

    ![Gérer les autorisations](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Sélectionnez **Ajouter un utilisateur**.

    ![Sélectionnez Ajouter un utilisateur](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Entrez les adresses e-mail complètes des personnes, des groupes de distribution ou des groupes de sécurité. Vous ne pouvez pas effectuer de partage avec des listes de distribution dynamique.

    ![Ajoutez les adresses e-mail](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. Sélectionnez **Ajouter**.

### <a name="i-cant-share-a-dashboard-or-report"></a>Je n’arrive pas à partager un tableau de bord ou un rapport

Pour pouvoir partager un tableau de bord ou un rapport, vous devez être autorisé à en partager le contenu sous-jacent, c’est-à-dire tous les rapports et jeux de données associés. Si un message vous indique que vous ne pouvez pas effectuer le partage, demandez à l’auteur du rapport de vous autoriser à repartager ces rapports et jeux de données.

![Message « Impossible de partager »](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>Étapes suivantes
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.
* [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un rapport Power BI filtré](service-share-reports.md).
* Vous avez des questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

