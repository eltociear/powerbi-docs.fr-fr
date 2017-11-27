---
title: "Partager des tableaux de bord avec des collègues et d’autres utilisateurs - Power BI"
description: "Comment partager des tableaux de bord Power BI avec vos collègues, dans l’organisation et en dehors et ce que vous devez savoir sur le partage."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: monitoring
qualitydate: 08/14/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 0b50568e49df8e2594519028b90d5d833d17c6b7
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="share-your-power-bi-dashboards-with-coworkers-and-others"></a>Partager vos tableaux de bord Power BI avec vos collègues et d’autres utilisateurs
Le *partage* est une façon d’autoriser quelques utilisateurs à accéder à vos tableaux de bord et rapports. Power BI offre [plusieurs façons de collaborer et de distribuer vos tableaux](service-how-to-collaborate-distribute-dashboards-reports.md). Le partage en est une.

![Icône Partager dans une liste des tableaux de bord](media/service-share-dashboards/power-bi-share-dash.png)

Que vous partagiez du contenu à l’intérieur ou à l’extérieur de votre organisation, vous et vos destinataires devez disposer d’une [licence Power BI Pro](service-free-vs-pro.md) ou le contenu doit être dans une [capacité Premium](service-premium.md). Vous avez des suggestions ? L’équipe Power BI est toujours intéressée par vos commentaires. Pour cela, accédez au [site de la communauté Power BI](https://community.powerbi.com/).

Vous pouvez partager un tableau de bord à partir de votre espace de travail personnel ou d’un espace de travail d’application. Quand vous partagez un tableau de bord, les utilisateurs avec qui vous le partager peuvent l’afficher et interagir avec celui-ci, mais ils ne peuvent pas le modifier. Ils voient les mêmes données que vous dans le tableau de bord et les rapports, sauf si la [sécurité au niveau des lignes](service-admin-rls.md) est appliquée. Les collègues avec qui vous partagez le tableau de bord peuvent le partager avec leurs collègues si vous les y autorisez. Les personnes ne faisant pas partie de votre organisation peuvent consulter le tableau de bord et interagir avec celui-ci, mais elles ne peuvent pas le partager. 

Vous pouvez également [partager un tableau de bord à partir de l’une des applications mobiles Power BI](mobile-share-dashboard-from-the-mobile-apps.md). Vous pouvez partager des tableaux de bord à partir du service Power BI et des applications mobiles Power BI, mais pas de Power BI Desktop.

## <a name="video-share-a-dashboard"></a>Vidéo : Partager un tableau de bord
Regardez Amanda partager son tableau de bord avec des collègues à l’intérieur et à l’extérieur de son entreprise. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard"></a>Partager un tableau de bord
1. Dans votre espace de travail personnel ou dans un espace de travail d’application, ouvrez un tableau de bord et sélectionnez **Partager** ![icône Partager](media/service-share-dashboards/power-bi-share-icon.png).
2. Dans la zone supérieure, entrez les adresses e-mail complètes des personnes, des groupes de distribution ou des groupes de sécurité. Vous ne pouvez pas effectuer de partage avec des listes de distribution dynamique. 
   
   Vous pouvez partager avec des personnes dont les adresses électroniques sont externes à votre organisation, mais un message d’avertissement s’affiche.
   
   ![Avertissement concernant le partage externe](media/service-share-dashboards/power-bi-share-dialog-warning.png)  
3. Ajoutez un message si vous le souhaitez. Ceci est facultatif.
4. Pour permettre à vos collègues de partager votre tableau de bord avec d’autres personnes, cochez la case **Autoriser les destinataires à partager votre tableau de bord**.
   
   Autoriser le partage par d’autres utilisateurs est appelé *repartage*. Si vous les y autorisez, les utilisateurs peuvent repartager à partir du service Power BI et des applications mobiles ou transférer le message d’invitation à d’autres membres de votre organisation. L’invitation expire après un mois. Les personnes extérieures à votre organisation ne sont pas autorisées à le partager à nouveau. En tant que propriétaire du tableau de bord, vous pouvez désactiver le repartage ou le révoquer individuellement. Consultez [Arrêter de partager un tableau de bord ou empêcher d’autres personnes de le partager](service-share-dashboards.md#stop-sharing-a-dashboard-or-stop-others-from-sharing) ci-dessous.
5. Sélectionnez **Partager**.
   
   ![Sélectionner le bouton Partager](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI envoie à des individus (et non à des groupes) un e-mail d’invitation contenant un lien vers le tableau de bord partagé et vous voyez une notification de **réussite**. 
   
   Lorsque les destinataires de votre organisation cliquent sur le lien, Power BI ajoute le tableau de bord à leur page de liste **Partagés avec moi**. Ceux-ci peuvent sélectionner votre nom pour voir tous les tableaux de bord que vous avez partagés. 
   
   ![Page de liste Partagés avec moi](media/service-share-dashboards/power-bi-shared-with-me-list-page.png)
   
   Lorsque les destinataires en dehors de votre organisation cliquent sur le lien, ils voient le tableau de bord, mais pas dans le portail Power BI habituel. Pour plus d’informations, consultez [Partager un tableau de bord avec des personnes extérieures à votre organisation](service-share-dashboards.md#share-a-dashboard-with-people-outside-your-organization) ci-dessous.

## <a name="who-has-access-to-a-dashboard-you-shared"></a>Qui a accès à un tableau de bord que vous avez partagé ?
Vous avez parfois besoin de voir les personnes avec qui vous avez partagé un tableau de bord et avec qui celles-ci l’ont partagé.

1. Dans la liste des tableaux de bord ou dans le tableau de bord lui-même, sélectionnez **Partager** ![icône Partager](media/service-share-dashboards/power-bi-share-icon.png). 
2. Dans la boîte de dialogue **Partager le tableau de bord**, sélectionnez **Accès**.
   
    ![Boîte de dialogue Partager le tableau de bord, onglet Accès](media/service-share-dashboards/power-bi-share-dialog-access.png)
   
    Les personnes extérieures à votre organisation sont répertoriées en tant qu’ **Invités**.

## <a name="stop-sharing-a-dashboard-or-stop-others-from-sharing"></a>Arrêter de partager un tableau de bord ou empêcher d’autres personnes de le partager
Seul le propriétaire du tableau de bord peut activer et désactiver le repartage.

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>Si vous n’avez pas encore envoyé l’invitation de partage
* Décochez la case **Autoriser les destinataires à partager votre tableau de bord** en bas de l’invitation avant de l’envoyer.

### <a name="if-youve-already-shared-the-dashboard"></a>Si vous avez déjà partagé le tableau de bord
1. Dans la liste des tableaux de bord ou dans le tableau de bord lui-même, sélectionnez **Partager** ![icône Partager](media/service-share-dashboards/power-bi-share-icon.png). 
2. Dans la boîte de dialogue **Partager le tableau de bord**, sélectionnez **Accès**.
   
    ![Boîte de dialogue Partager le tableau de bord, onglet Accès](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. Sélectionnez le bouton de sélection (**...**) en regard de **Lire et repartager**, puis sélectionnez :
   
   ![Points de suspension Lire et repartager](media/service-share-dashboards/power-bi-change-access.png)
   
   * **Lire** pour empêcher cette personne de partager avec quiconque.
   * **Supprimer l’accès** pour empêcher cette personne de voir le tableau de bord.

## <a name="share-a-dashboard-with-people-outside-your-organization"></a>Partager un tableau de bord avec des personnes extérieures à votre organisation
Quand vous partagez avec des personnes extérieures à votre organisation, celles-ci reçoivent un e-mail contenant un lien vers le tableau de bord partagé et elles doivent se connecter à Power BI pour voir le tableau de bord. Si elles ne disposent pas de licence Power BI Pro, elles peuvent en demander une après avoir cliqué sur le lien.

Une fois connectées, elles voient le tableau de bord partagé dans leur propre fenêtre de navigateur sans le volet de navigation gauche, et non dans leur portail Power BI habituel. Elles doivent ajouter le lien en favori pour accéder de nouveau à ce tableau de bord à l'avenir.

Elles ne peuvent modifier aucun contenu dans ce tableau de bord ou ce rapport. Elles peuvent interagir avec les graphiques dans le rapport (surbrillance croisée) et modifier les filtres/segments disponibles dans les rapports connectés au tableau de bord, mais elles ne peuvent pas enregistrer les modifications.

Seuls vos destinataires directs peuvent voir le tableau de bord partagé. Par exemple, si vous avez envoyé le courrier à Vicki@contoso.com, seule Vicki peut voir le tableau de bord. Personne d’autre ne peut voir ce tableau de bord, même si elles disposent du lien, et Vicki doit utiliser la même adresse de messagerie pour accéder à ce tableau de bord. Si elle se connecte avec une autre adresse de messagerie, elle ne pourra pas non plus accéder au tableau de bord.

Les personnes extérieures à votre organisation ne peuvent pas du tout voir les données si la sécurité au niveau des rôles ou des lignes est établie selon les modèles tabulaires Analysis Services locaux.

Si vous envoyez un lien à partir d’une application mobile Power BI à des personnes extérieures à votre organisation, lorsque celles-ci cliquent sur le lien, le tableau de bord s’ouvre dans un navigateur, et non dans l’application mobile Power BI.

## <a name="limitations-and-considerations"></a>Considérations et limitations
Voici quelques éléments à prendre en compte lors du partage de tableaux de bord :

* En général, vos collègues et vous-même voyez les mêmes données dans le tableau de bord. Ainsi, si vous êtes autorisé à voir plus de données qu’eux, ils pourront voir toutes vos données dans votre tableau de bord. Toutefois, si la [sécurité au niveau des lignes](service-admin-rls.md) est appliquée au jeu de données sous-jacent d’un tableau de bord, les informations d’identification de chaque personne sont utilisées pour déterminer les données auxquelles celle-ci est autorisée à accéder.
* Tous les utilisateurs avec qui vous partagez votre tableau de bord peuvent le voir et interagir avec vos rapports en [mode Lecture](service-report-open-in-reading-view.md). Ils ne peuvent pas créer de rapports ni enregistrer les modifications apportées aux rapports existants.
* Aucun utilisateur ne peut voir ni télécharger le jeu de données.
* Tout le monde peut manuellement [actualiser les données de tableau de bord](refresh-data.md).
* Si vous utilisez Office 365 pour la messagerie électronique, vous pouvez partager avec les membres d’un groupe de distribution en entrant l’adresse de messagerie associée au groupe de distribution.
* Les collègues qui ont le même domaine de messagerie que le vôtre, ainsi que les collègues dont le domaine est différent mais inscrit auprès du même locataire, peuvent partager le tableau de bord avec d’autres utilisateurs. Par exemple, supposons que les domaines contoso.com et contoso2.com sont enregistrés dans le même locataire. Si votre adresse de courrier est konrads@contoso.com, ravali@contoso.com et gustav@contoso2.com peuvent partager, à condition que vous ayez autorisé ce partage.
* Si vos collègues ont déjà accès à un tableau de bord spécifique, vous pouvez envoyer un lien direct vers ce tableau de bord en copiant simplement l’URL quand vous êtes dans le tableau de bord. Par exemple : `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* De même, si vos collègues ont déjà accès à un tableau de bord spécifique, vous pouvez [envoyer un lien direct vers le rapport sous-jacent](service-share-reports.md). 

## <a name="next-steps"></a>Étapes suivantes
* Vous voulez donner votre avis ? Accédez au [site de la communauté Power BI](https://community.powerbi.com/) pour effectuer des suggestions.
* [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Partager un seul rapport Power BI](service-share-reports.md)
* Vous avez des questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).

