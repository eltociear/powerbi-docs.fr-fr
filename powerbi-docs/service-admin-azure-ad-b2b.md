---
title: "Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B"
description: "Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à l’organisation."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: asaxton
ms.openlocfilehash: 5dabaa09923203c31572b413f8674b76028b7483
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuer du contenu Power BI à des utilisateurs invités externes avec Azure AD B2B

Power BI s’intègre avec Azure Active Directory B2B (Azure AD B2B) pour permettre une distribution sécurisée de contenu Power BI à des utilisateurs invités extérieurs à l’organisation, tout en conservant le contrôle des données internes.

> [!VIDEO https://www.youtube.com/embed/xxQWEQ1NnlY]

## <a name="invite-guest-users"></a>Inviter des utilisateurs

Il existe deux façons d’inviter des utilisateurs à rejoindre votre client Power BI : l’invitation planifiée ou l’invitation ad hoc. Une invitation n’est nécessaire que la première fois que vous invitez un utilisateur externe à rejoindre votre organisation.

### <a name="planned-invites"></a>Invitations planifiées

Une invitation planifiée s’effectue via le portail Microsoft Azure dans Azure AD ou à l’aide de PowerShell. Il s’agit de l’option à utiliser si vous savez quels utilisateurs doivent être invités. 

**Pour pouvoir créer des utilisateurs invités dans le portail Azure AD, vous devez être administrateur de clients.**

1. Accédez au [portail Azure](https://portal.azure.com), puis sélectionnez **Azure Active Directory**.

2. Accédez à **Utilisateurs et groupes** > **Tous les utilisateurs** > **Nouvel utilisateur invité**.

    ![Portail Azure AD - Nouvel utilisateur invité](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

3. Entrez l’**adresse e-mail** et un **message personnel**.

    ![Portail Azure AD - Message d’invitation d’un nouvel utilisateur](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

4. Sélectionnez **Inviter**.

Pour inviter plus d’un utilisateur, utilisez PowerShell. Pour plus d’informations, voir [Code Azure Active Directory B2B Collaboration et exemples PowerShell](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-code-samples).

L’utilisateur invité doit sélectionner **Mise en route** dans l’e-mail d’invitation qu’il reçoit. L’utilisateur invité est ensuite ajouté au client.

![E-mail d’invitation d’un utilisateur](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Invitations ad hoc

Pour inviter un utilisateur externe à un moment quelconque, ajoutez-le à la liste d’accès d’une application lors de publication de celle-ci.

![Utilisateur externe ajouté à la liste d’accès d’une application](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

L’utilisateur invité reçoit un e-mail l’informant que l’application a été partagée avec lui.

![E-mail pour l’application partagée avec l’utilisateur invité](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

L’utilisateur invité doit se connecter en utilisant l’adresse e-mail de son organisation. Une fois connecté, il est invité à accepter l’invitation. Ensuite, il est redirigé vers le contenu de l’application. Pour revenir à l’application, marquez le lien à l’aide d’un signet, ou enregistrez l’e-mail.

## <a name="licensing"></a>Gestion des licences

L’utilisateur invité doit disposer de la licence appropriée pour afficher l’application partagée. Trois options le permettent.

### <a name="use-power-bi-premium"></a>Utiliser Power BI Premium

L’affectation de l’espace de travail de l’application à la capacité Power BI Premium permet à l’utilisateur invité d’utiliser l’application sans disposer d’une licence Power BI Pro. Power BI Premium permet également à des applications de tirer parti d’autres capacités, telles que des fréquences de rafraîchissement accrues, une capacité dédiée et des tailles de modèle importantes.

![Utiliser Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-power-bi-pro-license-to-guest-user"></a>Affecter une licence Power BI Pro à un utilisateur invité

L’affectation d’une licence Power BI Pro à l’utilisateur invité à l’intérieur de votre client permet à cet utilisateur d’afficher le contenu.

> [!NOTE]
> Une licence Power BI Pro provenant de votre client s’applique aux utilisateurs invités uniquement quand ceux-ci accèdent à du contenu à l’intérieur de votre client.

![Attribuer une licence Pro à partir de votre client](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>Utilisateur invité apportant sa propre licence Power BI Pro

L’utilisateur invité dispose déjà d’une licence Power BI Pro assignée à l’intérieur de son client.

![Utilisateur invité apportant sa propre licence](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="next-steps"></a>Étapes suivantes

Pour des informations plus détaillées, notamment sur la manière dont fonctionne la sécurité au niveau des lignes, voir le [livre blanc](https://aka.ms/powerbi-b2b-whitepaper).

Pour plus d’informations sur Azure Active Directory B2B, voir [Qu’est-ce qu’Azure AD B2B Collaboration](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b).