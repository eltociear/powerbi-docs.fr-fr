---
title: Distribuer du contenu à des utilisateurs invités externes avec Azure AD B2B
description: Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à l’organisation.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101811"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B

Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à votre organisation, tout en conservant le contrôle des données internes.  

De plus, vous pouvez autoriser les utilisateurs invités extérieurs à votre organisation à modifier et à gérer du contenu au sein de votre organisation.

## <a name="enable-access"></a>Activer l’accès

Veillez à activer la [partager du contenu avec des utilisateurs externes](service-admin-portal.md#export-and-sharing-settings) fonctionnalité dans le portail d’administration Power BI avant d’inviter des utilisateurs invités.

Vous pouvez également utiliser le [autoriser à modifier et gérer des utilisateurs invités externes contenu dans l’organisation](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) fonctionnalité. Il vous permet de sélectionner quel utilisateur invité peut voir et créer du contenu dans les espaces de travail, y compris la navigation Power BI de votre organisation.

## <a name="who-can-you-invite"></a>Qui pouvez-vous inviter ?

Vous pouvez inviter les utilisateurs invités avec n’importe quelle adresse de messagerie, y compris les comptes personnels comme gmail.com, outlook.com et hotmail.com. Azure AD B2B appelle ces adresses *identités sociales*.

## <a name="invite-guest-users"></a>Inviter des utilisateurs

Utilisateurs invités nécessitent uniquement les invitations à participer à la première fois que vous les invitez dans votre organisation. Il existe deux façons d’inviter des utilisateurs : planifiée invitations et invitations ad hoc.

### <a name="planned-invites"></a>Invitations planifiées

Utilisez une invitation planifiée si vous savez quels utilisateurs inviter. Vous pouvez envoyer l’invitation à l’aide du portail Azure ou de PowerShell. Vous devez être un administrateur de locataire pour inviter des personnes.

Procédez comme suit pour envoyer une invitation dans le portail Azure.

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Azure Active Directory**.

1. Sous **gérer**, sélectionnez **utilisateurs** > **tous les utilisateurs** > **nouvel utilisateur invité**.

    ![Capture d’écran du portail Azure avec la nouvelle option d’utilisateur invité exigées.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Entrez une **adresse e-mail** et un **message personnel**.

    ![Capture d’écran de la boîte de dialogue Azure AD portail nouvel utilisateur invité.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Sélectionnez **Inviter**.

Pour inviter plus d’un utilisateur, utilisez PowerShell. Pour plus d’informations, consultez [Code Azure AD B2B Collaboration et exemples PowerShell](/azure/active-directory/b2b/code-samples/).

L’utilisateur invité doit sélectionner **Mise en route** dans l’e-mail d’invitation qu’il reçoit. L’utilisateur invité est ensuite ajouté au client.

![Capture d’écran de l’invité utilisateur e-mail d’invitation.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Invitations ad hoc

Pour inviter un utilisateur externe à tout moment, les ajouter, à votre tableau de bord ou un rapport via le partage de l’interface utilisateur, ou votre application via la page d’accès. L’exemple suivant montre comment inviter un utilisateur externe à utiliser une application.

![Capture d’écran d’externe utilisateur ajouté à la liste d’accès aux applications dans Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L’utilisateur invité reçoit un e-mail indiquant que vous avez partagé l’application avec eux.

![Capture d’écran de messagerie pour l’application partagée avec l’utilisateur invité](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

L’utilisateur invité doit se connecter en utilisant l’adresse e-mail de son organisation. Ils recevront une invite à accepter l’invitation après vous être connecté. Après la connexion, l’application s’ouvre pour l’utilisateur invité. Pour revenir à l’application, il peut marquer le lien à l’aide d’un signet, ou enregistrer l’e-mail.

## <a name="licensing"></a>Licensing

L’utilisateur invité doit avoir la licence appropriée pour afficher le contenu que vous avez partagé. Il existe trois façons de s’assurer que l’utilisateur a une licence appropriée : utiliser Power BI Premium, attribuer une licence Power BI Pro ou utiliser la licence Power BI Pro de l’invité.

Quand vous utilisez la fonctionnalité [Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization), les utilisateurs invités contribuant à du contenu dans des espaces de travail ou partageant du contenu avec d’autres utilisateurs nécessitent une licence Power BI Pro.

### <a name="use-power-bi-premium"></a>Utiliser Power BI Premium

Affectation de l’espace de travail à [capacité Power BI Premium](service-premium-what-is.md) permet à l’utilisateur invité d’utiliser l’application sans avoir besoin d’une licence Power BI Pro. Power BI Premium permet également aux applications de tirer parti des autres fonctionnalités telles que les fréquences de rafraîchissement accrues, une capacité dédiée et tailles de modèle de grande taille.

![Diagramme de l’expérience utilisateur invité avec Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Affecter une licence Power BI Pro à un utilisateur invité

Attribution d’une licence Power BI Pro à l’utilisateur invité, au sein de votre client, permet à ce contenu de vue utilisateur invité dans le locataire.

![Diagramme de l’expérience utilisateur invité avec licence affecter Pro à partir de votre client.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>Utilisateur invité apportant sa propre licence Power BI Pro

L’utilisateur invité dispose déjà d’une licence Power BI Pro assignée à l’intérieur de son client.

![Diagramme de l’expérience utilisateur invité lors qu’ils introduisent leur propre licence.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Utilisateurs invités pouvant modifier et gérer du contenu 

Lorsque vous utilisez le [autoriser à modifier et gérer des utilisateurs invités externes contenu dans l’organisation](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) fonctionnalité, les utilisateurs invités spécifié accéder à Power BI votre organisation. Ils peuvent voir tout contenu auquel ils ont l’autorisation. Ils peuvent accéder à Home, parcourir les espaces de travail, installer des applications, voir où ils se trouvent sur la liste d’accès et contribuer au contenu aux espaces de travail. Ils peuvent créer ou être des administrateurs d’espaces de travail qui utilisent la nouvelle expérience d’espace de travail. Certaines limitations s’appliquent. La section Considérations et Limitations répertorier ces restrictions.
 
Pour aider ces utilisateurs à se connecter à Power BI, fournissez-lui l’URL de locataire. Pour trouver l’URL de locataire, effectuez les étapes suivantes.

1. Dans le service Power BI, menu supérieur, sélectionnez l’aide ( **?** ), puis **À propos de Power BI**.

2. Recherchez la valeur en regard de **URL de locataire**. La valeur est l’URL de locataire que vous pouvez partager avec vos utilisateurs invités.

    ![Boîte de dialogue de capture d’écran de sur Power BI avec le locataire d’utilisateur invité qu'url appelée out.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Par défaut, externe B2B de AD Azure limite aux invités de la consommation de contenu uniquement. Invités d’Azure AD B2B externes peuvent afficher des applications, des tableaux de bord, rapports, exporter des données et créer des abonnements par courrier électronique pour les rapports et tableaux de bord. Ils ne peuvent pas accéder aux espaces de travail ou publier leur propre contenu. Toutefois, ces restrictions ne s’appliquent pas aux utilisateurs invités qui ont accès via le [autoriser à modifier et gérer des utilisateurs invités externes contenu dans l’organisation](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) fonctionnalité.

* Pour les utilisateurs invités activées par le biais le [autoriser à modifier et gérer des utilisateurs invités externes contenu dans l’organisation](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) fonctionnalité, certaines expériences ne sont pas à leur disposition. Pour mettre à jour ou publier des rapports, ils doivent utiliser l’interface utilisateur web du service Power BI, notamment l’option Obtenir les données pour charger des fichiers Power BI Desktop.  Les expériences suivantes ne sont pas prises en charge :
    * Diriger la publication de Power BI Desktop vers le service Power BI
    * Les utilisateurs invités ne peuvent pas utiliser Power BI desktop pour vous connecter à des jeux de données de service dans le service Power BI
    * Espaces de travail classiques liés à des groupes Office 365 :
        * Utilisateur invité ne peut pas créer ou d’être administrateurs de ces espaces de travail
        * Les utilisateurs invités peuvent être des membres
    * Envoi des invitations ad hoc n’est pas pris en charge pour les listes d’accès espace de travail
    * Power BI Publisher pour Excel n’est pas pris en charge pour les utilisateurs invités
    * Les utilisateurs invités ne peuvent pas installer un de Power BI Gateway et le connecter à votre organisation
    * Les utilisateurs invités ne peuvent pas installer publier des applications dans toute l’organisation
    * Les utilisateurs invités ne peuvent pas utiliser, créer, mettre à jour ou installer des packs de contenu organisationnels
    * Les utilisateurs invités ne peuvent pas utiliser analyser dans Excel
    * Les utilisateurs invités ne peuvent pas être @mentioned dans les commentaires
    * Les utilisateurs invités ne peuvent pas utiliser des abonnements
    * Les utilisateurs invités qui utilisent cette fonctionnalité doivent disposer d’un compte professionnel ou scolaire. Invité feront les utilisateurs à l’aide de comptes personnels en raison des limitations de plus pour vous connecter restrictions.

* Cette fonctionnalité n’est pas actuellement disponible avec le composant WebPart rapport Power BI SharePoint Online.

* Il existe des paramètres Active Directory qui peut limiter les opérations des utilisateurs invités externes au sein de votre organisation globale. Qui s’applique également à votre environnement Power BI. La documentation suivante décrit les paramètres :
    * [Gérer les paramètres de collaboration externes](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Autoriser ou bloquer les invitations aux utilisateurs B2B provenant d’organisations spécifiques ](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir des informations détaillées, y compris le fonctionnement de la sécurité comment au niveau des lignes, consultez le livre blanc : [Distribuer du contenu Power BI à des utilisateurs invités externes à l’aide d’Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Pour plus d’informations sur Azure AD B2B, consultez [qu’est Azure AD B2B collaboration ?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
