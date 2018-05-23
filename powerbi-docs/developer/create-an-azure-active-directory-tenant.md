---
title: Créer un locataire Azure Active Directory pour utiliser Power BI
description: Découvrez comment créer un locataire Azure Active Directory (Azure AD) pour votre application personnalisée à l’aide des API REST Power BI.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 11/30/2017
ms.author: maghan
ms.openlocfilehash: fd981b2f0c6e012444501a8a651092e11c3edf75
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>Créer un locataire Azure Active Directory pour utiliser Power BI
Découvrez comment créer un locataire Azure Active Directory (Azure AD) pour votre application personnalisée à l’aide des API REST Power BI.

Dans Azure Active Directory, un locataire représente une organisation. Il s’agit d’une instance dédiée du service Azure AD qu’une organisation reçoit et détient lorsqu’elle s’inscrit à un service cloud Microsoft tel qu’Azure, Microsoft Intune ou Office 365. Chaque locataire Azure AD est distinct et indépendant des autres locataires Azure AD.

Lorsque vous disposez d’un locataire Azure AD, vous pouvez définir une application et lui attribuer des autorisations pour lui permettre d’utiliser les API REST Power BI.

Si votre organisation possède déjà un locataire Azure AD, vous pouvez l’utiliser pour votre application. En fonction des besoins de votre application, vous pouvez recourir à ce locataire ou en créer un. Cet article explique comment créer un locataire.

## <a name="create-an-azure-active-directory-tenant"></a>Créer un client Azure Active Directory
Pour intégrer Power BI à votre application personnalisée, vous devez définir une application dans Azure AD. Pour ce faire, il vous faut un répertoire Azure AD. Il s’agit de votre locataire. Si votre organisation n’a pas encore de locataire, parce qu’elle n’utilise pas Power BI ou Office 365, [vous devez en créer un](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant). Vous pouvez également créer un locataire si vous souhaitez que votre application soit indépendante du locataire de votre organisation. Cela vous permet de bien distinguer les choses.

Si nécessaire, vous pouvez également créer un locataire à des fins de test.

Pour créer un locataire Azure AD, procédez comme suit :

1. Accédez au [portail Azure](https://portal.azure.com) et connectez-vous à l’aide d’un compte associé à un abonnement Azure.
2. Sélectionnez l’**icône Plus (+)** et recherchez *Azure Active Directory*.
   
    ![](media/create-an-azure-active-directory-tenant/new-directory.png)
3. Sélectionnez **Azure Active Directory** dans les résultats de la recherche.
   
    ![](media/create-an-azure-active-directory-tenant/new-directory2.png)
4. Sélectionnez **Créer**.
5. Entrez le **nom de l’organisation** ainsi que le **nom de domaine initial**. Sélectionnez ensuite **Créer**. Votre répertoire est ainsi créé.
   
    ![](media/create-an-azure-active-directory-tenant/organization-and-domain.png)
   
   > [!NOTE]
   > Votre domaine initial fait partie de onmicrosoft.com. Vous pourrez ultérieurement ajouter d’autres noms de domaine. Plusieurs domaines peuvent être attribués au répertoire d’un locataire.
   > 
   > 
6. Une fois le répertoire créé, sélectionnez la zone d’informations pour le gérer.

Votre répertoire est maintenant créé. L’étape suivante consiste à ajouter un utilisateur au locataire.

## <a name="create-some-users-in-your-azure-active-directory-tenant"></a>Créer des utilisateurs dans votre locataire Azure Active Directory
Maintenant que vous disposez d’un répertoire, vous devez créer au moins deux utilisateurs. L’un d’eux est l’administrateur général du locataire, et l’autre votre utilisateur principal pour l’incorporation. Considérez celui-ci comme un compte de service.

1. Dans le portail Azure, vérifiez que vous vous trouvez sur la sortie Azure Active Directory.
   
    ![](media/create-an-azure-active-directory-tenant/aad-flyout.png)
   
    Si ce n’est pas le cas, sélectionnez l’icône Azure Active Directory sur la barre de services de gauche.
   
    ![](media/create-an-azure-active-directory-tenant/aad-service.png)
2. Sous **Gérer**, sélectionnez **Utilisateurs et groupes**.
   
    ![](media/create-an-azure-active-directory-tenant/users-and-groups.png)
3. Sélectionnez **Tous les utilisateurs**, puis **+ Nouvel utilisateur**.
4. Attribuez un nom et un nom d’utilisateur à ce nouvel utilisateur. Celui-ci devient l’administrateur général du locataire. Vous devez également définir le **Rôle d’annuaire** sur *Administrateur général*. En outre, vous pouvez afficher le mot de passe temporaire. Lorsque vous avez terminé, sélectionnez **Créer**.
   
    ![](media/create-an-azure-active-directory-tenant/global-admin.png)
5. La même procédure s’applique à la création d’un utilisateur ordinaire dans votre locataire. Elle peut également être utilisée pour votre compte d’incorporation principal. Dans ce cas, le paramètre **Rôle d’annuaire** doit être défini sur *Utilisateur*. Veillez à noter le mot de passe. Sélectionnez ensuite **Créer**.
   
    ![](media/create-an-azure-active-directory-tenant/pbiembed-user.png)
6. Inscrivez-vous à Power BI à l’aide du compte d’utilisateur que vous avez créé à l’étape 5. Pour ce faire, accédez à [powerbi.com](https://powerbi.microsoft.com/get-started/) et sélectionnez **Essai gratuit** sous *Power BI - Partage et collaboration dans le cloud*.
   
    ![](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)
   
    Au moment de l’inscription, vous êtes invité à essayer Power BI Pro gratuitement pendant 60 jours. Vous pouvez opter pour cette solution pour devenir utilisateur professionnel. Si tel est votre objectif, vous pouvez également commencer à développer une solution incorporée.
   
   > [!NOTE]
   > Veillez à vous connecter avec l’adresse de courrier que vous avez spécifiée pour le compte d’utilisateur.
   > 
   > 

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous disposez d’un locataire Azure AD, vous pouvez l’utiliser pour tester des éléments dans Power BI et/ou vous pouvez commencer à incorporer des rapports et des tableaux de bord Power BI dans votre application. Pour plus d’informations sur l’incorporation d’éléments, consultez [Incorporation de vos tableaux de bord, rapports et vignettes Power BI](embedding-content.md).

[Qu’est-ce qu’un annuaire Azure AD ?](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)  
[Obtention d’un locataire Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

