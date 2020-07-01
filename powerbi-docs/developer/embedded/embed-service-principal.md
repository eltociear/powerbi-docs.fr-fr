---
title: Incorporer du contenu Power BI avec un principal de service et un secret d’application
description: Découvrez comment s’authentifier pour de l’analytique incorporée en utilisant un principal de service d’application Azure Active Directory et un secret d’application.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 05/12/2020
ms.openlocfilehash: e7b1e33322e0c1174b05a4e7b3617b5d3f7a18e8
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231236"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Incorporer du contenu Power BI avec un principal de service et un secret d’application

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

Cet article décrit l’authentification du principal de service à l’aide de l’*ID d’application* et *Secret de l’application*.

>[!NOTE]
>Nous vous recommandons de sécuriser vos services de back-end en utilisant des certificats au lieu de clés secrètes.
>* [Découvrez plus d’informations sur l’obtention de jetons d’accès auprès d’Azure AD en utilisant des clés secrètes ou des certificats](https://docs.microsoft.com/azure/architecture/multitenant-identity/client-assertion).
>* [Incorporez du contenu Power BI avec un principal de service et un certificat](embed-service-principal-certificate.md).

## <a name="method"></a>Méthode

Pour utiliser le principal de service et un ID d’application avec des analyses incorporées, procédez comme suit :

1. Créer une [application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-application-management).

    1. Créez le secret de l’application Azure AD.
    
    2. Obtenez l’*ID d’application* et *Secret d’application* de l’application.

    >[!NOTE]
    >Ces étapes sont décrites dans **l’étape 1**. Pour plus d’informations sur la création d’une application Azure AD, consultez l’article [créer une application Azure AD](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal).

2. Créez un groupe de sécurité Azure AD.

3. Activez les paramètres d’administrateur de service Power BI.

4. Ajoutez le principal de service à votre espace de travail.

5. Incorporez votre contenu.

> [!IMPORTANT]
> Une fois que vous activez le principal de service à utiliser avec Power BI, les autorisations AD de l’application n’ont plus d’effet. Les autorisations de l’application sont ensuite gérées par le biais du portail d’administration Power BI.

## <a name="step-1---create-an-azure-ad-app"></a>Étape 1 : créer une application Azure AD

Créer une application Azure AD à l’aide d’une de ces méthodes :
* Créer l’application dans le [Portail Microsoft Azure](https://portal.azure.com/#allservices)
* Créer l’application, à l’aide de [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Création d’une application Azure AD dans le Portail Microsoft Azure

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Cliquer sur l’onglet **Certificats et secrets**.

     ![ID d’application](media/embed-service-principal/certificates-and-secrets.png)


8. Cliquez sur **Nouveau secret client**.

    ![nouveau secret client](media/embed-service-principal/new-client-secret.png)

9. Dans la fenêtre *Ajouter un secret client*, entrez une description, spécifiez à quel moment vous souhaitez que le secret client expire, puis cliquez sur **Ajouter**.

10. Copiez et enregistrez la valeur *Secret client*.

    ![valeur secret client](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Une fois que vous avez quitté cette fenêtre, la valeur secret client est masquée et vous ne pouvez pas l’afficher ni la copier à nouveau.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Création d’une application Azure AD à l’aide de PowerShell

Cette section comprend un échantillon de script permettant de créer une nouvelle application Azure AD à l’aide de [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>Étape 2 : créer un groupe de sécurité Azure AD

Votre principal de service n’a accès à aucune de vos API ni au contenu Power BI. Pour accorder l’accès au principal de service, créez un groupe de sécurité dans Azure AD et ajoutez le principal de service que vous avez créé à ce groupe de sécurité.

Vous pouvez créer un groupe de sécurité Azure AD de deux façons :
* Manuellement (dans Azure)
* Avec PowerShell

### <a name="create-a-security-group-manually"></a>Créer un groupe de sécurité manuellement

Pour créer un groupe de sécurité Azure manuellement, suivez les instructions de l’article [Créer un groupe de base et ajouter des membres à l’aide d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Créer un groupe de sécurité à l’aide PowerShell

Voici un échantillon de script qui crée un nouveau groupe de sécurité et ajoute une application à ce groupe.

>[!NOTE]
>Si vous souhaitez activer l’accès au principal de service pour toute l’organisation, ignorez cette étape.

```powershell
# Required to sign in as a tenant admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Étape 3 : activer les paramètres d’administrateur de service Power BI

Pour qu’une application Azure AD soit en mesure d’accéder au contenu et aux API de Power BI, un administrateur Power BI doit activer l’accès au principal de service dans le portail d’administrateur Power BI.

Ajoutez le groupe de sécurité que vous avez créé dans Azure AD sous la section **Paramètres du développeur** relative au groupe de sécurité.

>[!IMPORTANT]
>Les principaux de service ont accès à tous les paramètres d’abonné pour lesquels ils sont activés. En fonction de vos paramètres d’administrateur, cela comprend des groupes de sécurité spécifiques ou toute l’organisation.
>
>Pour restreindre l’accès du principal de service à des paramètres d’abonné spécifiques, autorisez l’accès uniquement à des groupes de sécurité spécifiques. Vous pouvez également créer un groupe de sécurité dédié pour les principaux de service et l’exclure des paramètres d’abonné souhaités.

![Portail d’administration](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Étape 4 - Ajouter le principal de service à votre espace de travail

Pour activer vos artefacts d’accès à l’application Azure AD, tels que les rapports, les tableaux de bord et les jeux de données du service Power BI, ajoutez l’entité du principal de service en tant que membre ou administrateur à votre espace de travail.

>[!NOTE]
>Cette section fournit des instructions relatives à l’interface utilisateur. Vous pouvez également ajouter un principal de service à un espace de travail à l’aide de [Groupes : ajouter une API utilisateur de groupe](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser).

1. Accédez à l’espace de travail pour lequel vous souhaitez activer l’accès, puis dans le menu **Plus**, sélectionnez **Accès à l’espace de travail**.

    ![Paramètres de l’espace de travail](media/embed-service-principal/workspace-access.png)

2. Ajoutez le principal de service comme un **Administrateur** ou **Membre** à l’espace de travail.

    ![Administrateur de l’espace de service](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>Étape 5 : incorporer votre contenu

Vous pouvez incorporer votre contenu dans un exemple d’application ou dans votre propre application.

* [Incorporer du contenu en utilisant l’exemple d’application](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Incorporer du contenu dans votre application](embed-sample-for-customers.md#embed-content-within-your-application)

Une fois votre contenu incorporé, vous êtes prêt à [passer à la production](embed-sample-for-customers.md#move-to-production).

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Inscrire une application](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded pour vos clients](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objets d’application et de principal de service dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Sécurité au niveau des lignes à l’aide d’une passerelle de données locale avec principal de service](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Incorporer du contenu Power BI avec un principal de service et un certificat](embed-service-principal-certificate.md)
