---
title: Principal de service - Créer une application
description: Principal de service - Créer une application
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210798"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>Étape 2 : créer un groupe de sécurité Azure AD

Votre principal de service n’a accès à aucune de vos API ni au contenu Power BI. Pour accorder l’accès au principal de service, créez un groupe de sécurité dans Azure AD et ajoutez le principal de service que vous avez créé à ce groupe de sécurité.

Vous pouvez créer un groupe de sécurité Azure AD de deux façons :
* Manuellement (dans Azure)
* Avec PowerShell

### <a name="create-a-security-group-manually"></a>Créer un groupe de sécurité manuellement

Pour créer un groupe de sécurité Azure manuellement, suivez les instructions de l’article [Créer un groupe de base et ajouter des membres à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Créer un groupe de sécurité à l’aide PowerShell

Voici un échantillon de script qui crée un nouveau groupe de sécurité et ajoute une application à ce groupe.

>[!NOTE]
>Si vous souhaitez activer l’accès au principal de service pour toute l’organisation, ignorez cette étape.

```powershell
# Required to sign in as admin
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

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="Capture d’écran montrant les paramètres de développeur dans les options d’administration dans le portail Power BI.":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Étape 4 - Ajouter le principal de service à votre espace de travail

Pour activer vos artefacts d’accès à l’application Azure AD, tels que les rapports, les tableaux de bord et les jeux de données du service Power BI, ajoutez l’entité du principal de service en tant que membre ou administrateur à votre espace de travail.

>[!NOTE]
>Cette section fournit des instructions relatives à l’interface utilisateur. Vous pouvez également ajouter un principal de service à un espace de travail à l’aide de [Groupes : ajouter une API utilisateur de groupe](/rest/api/power-bi/groups/addgroupuser).

1. Accédez à l’espace de travail pour lequel vous souhaitez activer l’accès, puis dans le menu **Plus**, sélectionnez **Accès à l’espace de travail**.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="Capture d’écran montrant les paramètres de développeur dans les options d’administration dans le portail Power BI.":::

2. Ajoutez le principal de service comme un **Administrateur** ou **Membre** à l’espace de travail.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="Capture d’écran montrant les paramètres de développeur dans les options d’administration dans le portail Power BI.":::