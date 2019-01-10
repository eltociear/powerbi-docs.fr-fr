---
title: Incorporer avec le composant WebPart Rapport dans SharePoint Online
description: Avec le nouveau composant WebPart Rapport pour SharePoint Online, vous pouvez incorporer facilement des rapports Power BI interactifs dans les pages SharePoint Online.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 11/01/2018
ms.openlocfilehash: 3ad4335cabac159aee38d54fbfff0f689009fd68
ms.sourcegitcommit: b3af4f7ef486c95cea173caea5a31d0472816ddd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54136596"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Incorporer avec le composant WebPart Rapport dans SharePoint Online

Avec le nouveau composant WebPart Rapport pour SharePoint Online, vous pouvez incorporer facilement des rapports Power BI interactifs dans les pages SharePoint Online.

Quand vous utilisez la nouvelle option **Incorporer dans SharePoint Online**, les rapports incorporés sont entièrement sécurisés. Vous pouvez ainsi créer facilement des portails internes sécurisés.

## <a name="requirements"></a>Configuration requise

Il existe quelques exigences à respecter pour que les rapports **Incorporer dans SharePoint Online** fonctionnent.

* Vous devez avoir une licence Power BI Pro ou une [capacité Power BI Premium (référence SKU EM ou P)](service-premium.md#premium-capacity-nodes) avec une licence Power BI.
* Le composant WebPart Power BI pour SharePoint Online nécessite des [pages modernes](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Incorporer votre rapport

Pour incorporer votre rapport dans SharePoint Online, vous devez d’abord obtenir l’URL associée, puis utiliser cette dernière avec le nouveau composant WebPart Power BI dans SharePoint Online.

### <a name="get-a-url-to-your-report"></a>Obtenir l’URL de votre rapport

1. Affichez le rapport dans le service Power BI.

2. Sélectionnez l’option de menu **Fichier**.

3. Sélectionnez **Incorporer dans SharePoint Online**.

    ![menu Fichier](media/service-embed-report-spo/powerbi-file-menu.png)

4. Copiez l’URL à partir de la boîte de dialogue.

    ![Intégrer le lien](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Ajouter le rapport Power BI à une page SharePoint Online

1. Ouvrez la page souhaitée dans SharePoint Online et sélectionnez **Modifier**.

    ![Page de modifications SP](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Ou créez une page de site moderne en sélectionnant **+ Nouveau** dans SharePoint Online.

    ![Nouvelle page SP](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Sélectionnez **+**, puis le composant WebPart **Power BI**.

    ![Nouvelle partie web SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Sélectionnez **Ajouter un rapport**.

    ![Nouveau rapport SP](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)

4. Collez l’URL du rapport dans le volet des propriétés. Cette URL du rapport est l’URL que vous avez copiée au cours de la procédure ci-dessus. Le rapport se charge automatiquement.

    ![Propriétés de la nouvelle partie web SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Sélectionnez **Publier** pour que les utilisateurs de SharePoint Online puissent voir les modifications.

    ![Rapport chargé SP](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Accorder l’accès aux rapports

Incorporer un rapport dans SharePoint Online n’accorde pas automatiquement aux utilisateurs l’autorisation d’afficher le rapport. Les autorisations pour afficher le rapport sont définies dans le service Power BI.

> [!IMPORTANT]
> Veillez à passer en revue les utilisateurs qui peuvent afficher le rapport dans le service Power BI et à accorder l’accès à ceux qui ne sont pas répertoriés.

Il existe deux moyens de fournir un accès au rapport au sein du service Power BI. Si vous utilisez un groupe Office 365 pour créer votre site d’équipe SharePoint Online, répertoriez l’utilisateur comme membre de l’**espace de travail d’application dans le service Power BI** et la **page SharePoint**. Pour plus d’informations sur la gestion d’un espace de travail d’application, consultez [Gérer l’espace de travail de votre application](service-manage-app-workspace-in-power-bi-and-office-365.md).

Vous pouvez également partager un rapport directement avec les utilisateurs en l’incorporant dans une application. L’incorporation d’un rapport dans une application s’effectue en quelques étapes.  

1. L’auteur de l’application est un utilisateur Pro.

2. L’auteur crée un rapport dans un espace de travail d’application. *Pour pouvoir être partagé avec des **utilisateurs de la version gratuite de Power BI**, l’espace de travail de l’application doit être défini comme **espace de travail Premium**.*

3. L’auteur publie l’application, puis l’installe. *L’auteur doit s’assurer d’installer l’application de manière à accéder à l’URL du rapport utilisée pour l’incorporation dans SharePoint Online.*

4. Maintenant, tous les utilisateurs finaux doivent aussi installer l’application. Toutefois, vous pouvez configurer l’application afin qu’elle soit préinstallée pour les utilisateurs finaux à l’aide de la fonctionnalité **Installer l’application automatiquement**, qui peut être activée dans le [portail d’administration de Power BI](service-admin-portal.md).

   ![Installer l’application automatiquement](media/service-embed-report-spo/install-app-automatically.png)

5. L’auteur ouvre l’application et accède au rapport.

6. L’auteur copie l’URL du rapport incorporé à partir du rapport installé par l’application. *N’utilisez pas l’URL du rapport d’origine figurant dans l’espace de travail de l’application.*

7. Créez un nouveau site d’équipe dans SharePoint Online.

8. Ajoutez l’URL du rapport copiée à l’étape 6 au composant WebPart Power BI.

9. Ajoutez tous les utilisateurs finaux et/ou groupes qui auront besoin des données dans la page SharePoint Online et dans l’application Power BI que vous avez créée.

    > [!NOTE]
    > **Les utilisateurs ou les groupes doivent avoir accès à la page SharePoint Online et au rapport dans l’application Power BI pour voir le rapport dans la page SharePoint.**

10. Les utilisateurs finaux peuvent maintenant accéder au site d’équipe dans SharePoint Online et consulter les rapports dans la page.

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

Si votre environnement Power BI nécessite une connexion via l’authentification multifacteur, vous pouvez être invité à vous connecter avec un dispositif de sécurité pour vérifier votre identité. Ce cas de figure se produit si vous ne vous êtes pas connecté à SharePoint Online avec l’authentification multifacteur, mais que votre environnement Power BI nécessite un compte validé par un dispositif de sécurité.

> [!NOTE]
> Multi-Factor Authentication n’est pas encore pris en charge dans Azure Active Directory 2.0. Les utilisateurs reçoivent un message indiquant une *erreur*. Si l’utilisateur se reconnecte à SharePoint Online en utilisant son dispositif de sécurité, il peut visualiser le rapport.

## <a name="web-part-settings"></a>Paramètres des composants WebPart

Voici une description des paramètres qui peuvent être ajustés pour le composant WebPart Power BI dans SharePoint Online.

![Propriétés de la partie web SP](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propriété | Description |
| --- | --- |
| Nom de la page |Définit la page par défaut qui est affichée par le composant WebPart. Sélectionnez une valeur dans la liste déroulante. Si aucune page ne s’affiche, votre rapport ne contient qu’une seule page ou l’URL que vous avez collée contient un nom de page. Supprimez la section du rapport de l’URL pour sélectionner une page spécifique. |
| Affichage |Option qui permet de définir la façon dont le rapport est ajusté à la page SharePoint Online. |
| Afficher le volet de navigation |Affiche ou masque le volet de navigation Page. |
| Afficher le volet Filtre |Affiche ou masque le volet Filtre. |

## <a name="reports-that-do-not-load"></a>Rapports qui ne sont pas chargés

Il se peut que votre rapport ne se charge pas dans le composant WebPart Power BI et affiche le message suivant.

*Ce contenu n’est pas disponible.*

![Message Rapport introuvable](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Il existe deux raisons habituelles pour ce message.

1. Vous n’avez pas accès au rapport.
2. Le rapport a été supprimé.

Contactez le propriétaire de la page SharePoint Online pour qu’il vous aide à résoudre le problème.

## <a name="licensing"></a>Licensing

Les utilisateurs affichant un rapport dans SharePoint ont besoin au choix d’une **licence Power BI Pro** ou le contenu doit se trouver dans un espace de travail qui se trouve dans une  **[capacité Power BI Premium (référence SKU EM ou P)](service-admin-premium-purchase.md)**.

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

* Erreur : « Une erreur s’est produite. Essayez de vous déconnecter, de vous reconnecter, puis de revenir sur cette page. ID de corrélation : indéfini, état de la réponse http : 400, code d’erreur du serveur 10001, message : Jeton d’actualisation manquant »
  
  Si vous recevez cette erreur, essayez l’une des étapes de dépannage ci-dessous.
  
  1. Déconnectez-vous de SharePoint, puis reconnectez-vous. Veillez à fermer toutes les fenêtres du navigateur avant de vous reconnecter.

  2. Si votre compte utilisateur nécessite l’authentification multifacteur, veillez à vous connecter à SharePoint en utilisant votre dispositif d’authentification multifacteur (application sur un téléphone, carte à puce, etc.).
  
  3. Les comptes d’utilisateur invités Azure B2B ne sont pas pris en charge. Les utilisateurs voient le logo Power BI qui montre que le composant WebPart se chargement, mais le rapport ne s’affiche pas.

* Power BI ne prend pas en charge les mêmes langues localisées que SharePoint Online. Par conséquent, vous risquez de ne pas voir la localisation appropriée dans le rapport incorporé.

* Vous pouvez rencontrer des problèmes si vous utilisez Internet Explorer 10. Vous pouvez passer en revue les [navigateurs pris en charge par Power BI](consumer/end-user-browsers.md) et [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* Le composant WebPart Power BI n’est pas disponible pour les [clouds souverains](https://powerbi.microsoft.com/en-us/clouds/).

* Le serveur SharePoint classique n’est pas pris en charge avec ce composant WebPart.

* Les [filtres d’URL](service-url-filters.md) ne sont pas pris en charge avec le composant WebPart SPO.

## <a name="next-steps"></a>Étapes suivantes

* [Autoriser ou empêcher la création de pages de site moderne par les utilisateurs finaux](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Créer et distribuer une application dans Power BI](service-create-distribute-apps.md)  
* [Partager un tableau de bord avec vos collègues et les autres utilisateurs](service-share-dashboards.md)  
* [Qu’est-ce que Power BI Premium ?](service-premium.md)
* [Incorporer un rapport dans un site web ou portail sécurisé](service-embed-secure.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)