---
title: Distribuer du contenu à des utilisateurs invités externes avec Azure AD B2B
description: Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à l’organisation.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0eba54212ff9349ed75d9d9fb18878b39d5cd29a
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580194"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B

Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à votre organisation, tout en conservant le contrôle des données internes.  

De plus, vous pouvez autoriser les utilisateurs invités extérieurs à votre organisation à modifier et à gérer du contenu au sein de votre organisation.

## <a name="enable-access"></a>Activer l’accès

Vérifiez que la fonctionnalité [Partager du contenu avec des utilisateurs externes](service-admin-portal.md#export-and-sharing-settings) est activée dans le portail d’administration Power BI avant de convier des utilisateurs invités.

De plus, la fonctionnalité [Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](service-admin-portal.md#export-and-sharing-settings) vous permet de sélectionner quel utilisateur invité peut voir et créer du contenu dans les espaces de travail, notamment la navigation dans le contenu Power BI de votre organisation.

## <a name="who-can-you-invite"></a>Qui pouvez-vous inviter ?

Vous pouvez inviter des utilisateurs qui ont une adresse e-mail, y compris des comptes personnels comme gmail.com, outlook.com et hotmail.com. Dans Azure AD B2B, ces adresses sont appelées *identités sociales*.

## <a name="invite-guest-users"></a>Inviter des utilisateurs

Une invitation n’est nécessaire que la première fois que vous invitez un utilisateur invité externe à rejoindre votre organisation. Il existe deux façons d’inviter des utilisateurs : invitations planifiées et invitations ad-hoc.

### <a name="planned-invites"></a>Invitations planifiées

Utilisez une invitation planifiée si vous savez quels utilisateurs inviter. Vous pouvez envoyer l’invitation à l’aide du portail Azure ou de PowerShell. Vous devez être un administrateur de locataire pour inviter des personnes.

Procédez comme suit pour envoyer une invitation dans le portail Azure.

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Azure Active Directory**.

1. Sous **Gérer**, accédez à **Utilisateurs** > **Tous les utilisateurs** > **Nouvel utilisateur invité**.

    ![Portail Azure AD - Nouvel utilisateur invité](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Entrez une **adresse e-mail** et un **message personnel**.

    ![Portail Azure AD - Message d’invitation d’un nouvel utilisateur](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Sélectionnez **Inviter**.

Pour inviter plus d’un utilisateur, utilisez PowerShell. Pour plus d’informations, consultez [Code Azure AD B2B Collaboration et exemples PowerShell](/azure/active-directory/b2b/code-samples/).

L’utilisateur invité doit sélectionner **Mise en route** dans l’e-mail d’invitation qu’il reçoit. L’utilisateur invité est ensuite ajouté au client.

![E-mail d’invitation d’un utilisateur](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Invitations ad hoc

Pour effectuer une invitation, ajoutez l’utilisateur externe à votre tableau de bord ou rapport à l’aide de l’interface utilisateur de partage, ou votre application à partir de la page d’accès. L’exemple suivant montre comment inviter un utilisateur externe à utiliser une application.

![Utilisateur externe ajouté à la liste d’accès d’une application](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L’utilisateur invité reçoit un e-mail l’informant que l’application a été partagée avec lui.

![E-mail pour l’application partagée avec l’utilisateur invité](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

L’utilisateur invité doit se connecter en utilisant l’adresse e-mail de son organisation. Une fois connecté, il est invité à accepter l’invitation. Ensuite, il est redirigé vers le contenu de l’application. Pour revenir à l’application, il peut marquer le lien à l’aide d’un signet, ou enregistrer l’e-mail.

## <a name="licensing"></a>Licensing

L’utilisateur invité doit disposer de la licence appropriée pour afficher le contenu qui a été partagé. Il existe trois options pour ce faire : utiliser Power BI Premium ; attribuer une licence Power BI Pro ; ou utiliser la licence Power BI Pro de l’invité.

Quand vous utilisez la fonctionnalité [Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](service-admin-portal.md#export-and-sharing-settings), les utilisateurs invités contribuant à du contenu dans des espaces de travail ou partageant du contenu avec d’autres utilisateurs nécessitent une licence Power BI Pro.

### <a name="use-power-bi-premium"></a>Utiliser Power BI Premium

L’affectation de l’espace de travail de l’application à la [capacité Power BI Premium](service-premium.md) permet à l’utilisateur invité d’utiliser l’application sans disposer d’une licence Power BI Pro. Power BI Premium permet également à des applications de tirer parti d’autres capacités, telles que des fréquences de rafraîchissement accrues, une capacité dédiée et des tailles de modèle importantes.

![Utiliser Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Affecter une licence Power BI Pro à un utilisateur invité

L’affectation d’une licence Power BI Pro à l’utilisateur invité à l’intérieur de votre client permet à cet utilisateur d’afficher du contenu dans le locataire.

![Attribuer une licence Pro à partir de votre client](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>Utilisateur invité apportant sa propre licence Power BI Pro

L’utilisateur invité dispose déjà d’une licence Power BI Pro assignée à l’intérieur de son client.

![Utilisateur invité apportant sa propre licence](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Utilisateurs invités pouvant modifier et gérer du contenu 

Quand vous utilisez la fonctionnalité [Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation ](service-admin-portal.md#export-and-sharing-settings), les utilisateurs invités spécifiés accèdent au contenu Power BI de votre organisation et consultent le contenu pour lequel ils disposent d’une autorisation. Ils peuvent accéder à l’accueil, parcourir des espaces de travail, installer des applications là où elles figurent dans la liste d’accès et contribuer à du contenu dans des espaces de travail. Ils peuvent créer ou être des administrateurs d’espaces de travail qui utilisent la nouvelle expérience d’espace de travail. Certaines limitations s’appliquent. Elles sont listées dans la section Considérations et limitations.

Pour aider ces utilisateurs à se connecter à Power BI, fournissez-leur l’URL de locataire. Pour trouver l’URL de locataire, effectuez les étapes suivantes.

1. Dans le service Power BI, menu supérieur, sélectionnez l’aide (**?**), puis **À propos de Power BI**.

2. Recherchez la valeur en regard de **URL de locataire**. Il s’agit de l’URL de locataire que vous pouvez partager avec vos utilisateurs invités.

![URL de locataire de l’utilisateur invité](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Par défaut, les invités B2B externes peuvent uniquement consommer le contenu. Les invités B2B externes peuvent consulter les applications, les tableaux de bord, les rapports, exporter des données et créer des abonnements par courrier pour les tableaux de bord et les rapports. Ils ne peuvent pas accéder aux espaces de travail ou publier leur propre contenu. Toutefois, ces restrictions ne s’appliquent pas aux utilisateurs invités qui sont autorisés par le biais du paramètres de locataire [Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation ](service-admin-portal.md#export-and-sharing-settings).

* Les utilisateurs invités autorisés par le biais du paramètres de locataire [Autoriser les utilisateurs invités externes à modifier et à gérer le contenu de l’organisation](service-admin-portal.md#export-and-sharing-settings) n’ont pas accès à certaines expériences. Pour mettre à jour ou publier des rapports, ils doivent utiliser l’interface utilisateur web du service Power BI, notamment l’option Obtenir les données pour charger des fichiers Power BI Desktop.  Les expériences suivantes ne sont pas prises en charge :
    * Diriger la publication de Power BI Desktop vers le service Power BI
    * Les utilisateurs invités ne peuvent pas utiliser Power BI Desktop pour se connecter à des jeux de données du service dans le service Power BI
    * Espaces de travail classiques liés à des groupes Office 365 : Un utilisateur invité ne peut pas créer ou être un administrateur de ces espaces de travail. Ils peuvent être membres.
    * L’envoi d’invitations ad hoc n’est pas pris en charge pour les listes d’accès aux espaces de travail
    * Power BI Publisher pour Excel n’est pas pris en charge pour les utilisateurs invités
    * Les utilisateurs invités ne peuvent pas installer une passerelle Power BI Gateway et la connecter à votre organisation
    * Les utilisateurs invités ne peuvent pas installer d’applications à publier dans toute l’organisation
    * Les utilisateurs invités ne peuvent pas utiliser, créer, mettre à jour ou installer des packs de contenu d’organisation
    * Les utilisateurs invités ne peuvent pas utiliser la fonctionnalité Analyser dans Excel
    * Les utilisateurs invités ne peuvent pas être @mentioned (@mentionnés) dans les commentaires
    * Les utilisateurs invités ne peuvent pas utiliser des abonnements
    * Les utilisateurs invités qui utilisent cette fonctionnalité doivent disposer d’un compte professionnel ou scolaire. Les utilisateurs invités utilisant des comptes personnels seront confrontés à certaines limites en raison de restrictions de connexion.

* Pour l’instant, cette fonctionnalité n’est pas disponible avec le composant WebPart de rapport Power BI SharePoint Online.

* Il existe des paramètres Active Directory qui peuvent limiter ce que les utilisateurs invités externes peuvent faire dans l’ensemble de votre organisation et qui s’appliquent également à votre environnement Power BI. La documentation suivante décrit les paramètres :
    * [Gérer les paramètres de collaboration externes](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Autoriser ou bloquer les invitations aux utilisateurs B2B provenant d’organisations spécifiques ](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Étapes suivantes

Pour des informations plus détaillées, notamment sur la manière dont fonctionne la sécurité au niveau des lignes, consultez le livre blanc : [Distribuer du contenu Power BI à des utilisateurs invités externes à l’aide d’Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Pour plus d’informations sur Azure AD B2B, consultez [Qu’est-ce qu’Azure AD B2B Collaboration ?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
