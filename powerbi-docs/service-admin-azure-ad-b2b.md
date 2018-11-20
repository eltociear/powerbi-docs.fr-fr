---
title: Distribuer du contenu à des utilisateurs invités externes avec Azure AD B2B
description: Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à l’organisation.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: dee5c14d2ee714872409352b5e42d646e561c271
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507758"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B

Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à votre organisation, tout en conservant le contrôle des données internes.

## <a name="enable-access"></a>Activer l’accès

Assurez-vous que la fonctionnalité [Paramètres d’exportation et de partage](service-admin-portal.md#export-and-sharing-settings) est activée dans le portail d’administration de Power BI avant de convier des utilisateurs invités.

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

L’utilisateur invité doit disposer de la licence appropriée pour afficher l’application partagée. Il existe trois options pour ce faire : utiliser Power BI Premium ; attribuer une licence Power BI Pro ; ou utiliser la licence Power BI Pro de l’invité.

### <a name="use-power-bi-premium"></a>Utiliser Power BI Premium

L’affectation de l’espace de travail de l’application à la [capacité Power BI Premium](service-premium.md) permet à l’utilisateur invité d’utiliser l’application sans disposer d’une licence Power BI Pro. Power BI Premium permet également à des applications de tirer parti d’autres capacités, telles que des fréquences de rafraîchissement accrues, une capacité dédiée et des tailles de modèle importantes.

![Utiliser Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Affecter une licence Power BI Pro à un utilisateur invité

L’affectation d’une licence Power BI Pro à l’utilisateur invité à l’intérieur de votre client permet à cet utilisateur d’afficher du contenu dans le locataire.

![Attribuer une licence Pro à partir de votre client](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>Utilisateur invité apportant sa propre licence Power BI Pro

L’utilisateur invité dispose déjà d’une licence Power BI Pro assignée à l’intérieur de son client.

![Utilisateur invité apportant sa propre licence](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Les invités B2B externes peuvent uniquement consommer le contenu. Les invités B2B externes peuvent consulter les applications, les tableaux de bord, les rapports, exporter des données et créer des abonnements par courrier pour les tableaux de bord et les rapports. Ils ne peuvent pas accéder aux espaces de travail ou publier leur propre contenu.

* Cette fonctionnalité n’est pas disponible actuellement avec les applications mobiles Power BI. Sur un appareil mobile, vous pouvez afficher le contenu Power BI partagé à l’aide d’Azure AD B2B dans un navigateur.

* Pour l’instant, cette fonctionnalité n’est pas disponible avec le composant WebPart de rapport Power BI SharePoint Online.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, y compris sur le fonctionnement de la sécurité au niveau de la ligne, consultez le livre blanc : [Distribuer du contenu Power BI à des utilisateurs invités externes à l’aide d’Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Pour plus d’informations sur Azure AD B2B, consultez [Qu’est-ce qu’Azure AD B2B Collaboration ?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
