---
title: Créer les nouveaux espaces de travail - Power BI
description: Découvrez comment créer les nouveaux espaces de travail, collections de tableaux de bord, rapports et rapports paginés conçus pour fournir des métriques clés sur votre organisation.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: maggies
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: edc06d7a46589c999e4bf18613c0c75f6d5bf983
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120590"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Créer les nouveaux espaces de travail dans Power BI

Cet article explique comment créer un des *nouveaux espaces de travail* à la place d’un espace de travail *classique*. Les deux types d’espaces de travail sont des emplacements où collaborer avec des collègues. Dans ceux-ci, vous créez des regroupements de tableaux de bord, de rapports et de rapports paginés. Si vous le souhaitez, vous pouvez également regrouper cette collection dans une *application* et la distribuer à un public plus large.

Voici comment les nouveaux espaces de travail diffèrent des anciens. Dans les nouveaux espaces de travail, vous pouvez :

- Affecter des rôles d’espace de travail à des groupes d’utilisateurs et à des individus.
- Créer un espace de travail dans Power BI sans créer de groupe Microsoft 365.
- Utiliser des rôles d’espace de travail plus granulaires, pour une gestion plus flexible des autorisations.

:::image type="content" source="media/service-create-the-new-workspaces/power-bi-workspace-sales-marketing.png" alt-text="Échantillon d’espace de travail Ventes et marketing":::

Pour plus d’informations, consultez l’article sur les [nouveaux espaces de travail](service-new-workspaces.md).

Prêt à migrer votre espace de travail classique ? Consultez [Mettre à niveau les espaces de travail classiques vers de nouveaux espaces de travail dans Power BI](service-upgrade-workspaces.md) pour plus d’informations.

> [!NOTE]
> Pour appliquer la sécurité au niveau des lignes (RLS) aux utilisateurs de Power BI Pro qui parcourent du contenu dans un espace de travail, attribuez le rôle Lecteur à ces utilisateurs.

## <a name="create-one-of-the-new-workspaces"></a>Créer un nouvel espace de travail

1. Commencez par créer l’espace de travail. Sélectionnez **Espaces de travail** > **Créer un espace de travail**.
   
     ![Créer un espace de travail](media/service-create-the-new-workspaces/power-bi-workspace-create.png)

2. Vous créez automatiquement un espace de travail mis à niveau, sauf si vous choisissez **Revenir au type classique**.
   
     ![Nouvelle expérience d’espace de travail](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Si vous sélectionnez **Revenir au type classique**, vous créez un [espace de travail classique](service-create-workspaces.md) basé sur un groupe Microsoft 365.

2. Donnez un nom unique à l’espace de travail. Si le nom n’est pas disponible, modifiez-le de façon à obtenir un nom unique.
   
     L’application que vous créez à partir de l’espace de travail aura le même nom et la même icône que l’espace de travail.
   
1. Voici quelques éléments facultatifs que vous pouvez définir pour votre espace de travail :

    Téléchargez une **image d’espace de travail**. Les fichiers peuvent être au format .png ou .jpg. La taille du fichier doit être inférieure à 45 ko.
    
    [Ajoutez une **Liste de contacts**](#create-a-contact-list). Par défaut, les administrateurs de l’espace de travail sont les contacts. 
    
    [Spécifiez **un espace de travail OneDrive**](#set-a-workspace-onedrive) pour utiliser un emplacement de stockage de fichiers de groupe Microsoft 365. 

    Pour affecter l’espace de travail à une **Capacité dédiée**, sous l’onglet **Premium**, sélectionnez **Capacité dédiée**.
     
    ![Capacité dédiée](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Sélectionnez **Enregistrer**.

    Power BI crée l’espace de travail et l’ouvre. Vous le voyez dans la liste des espaces de travail dont vous êtes membre. 

## <a name="create-a-contact-list"></a>Créer une liste de contacts

Vous pouvez spécifier les utilisateurs qui reçoivent une notification concernant les problèmes qui se produisent dans l’espace de travail. Par défaut, tout utilisateur ou groupe spécifié comme administrateur de l’espace de travail est averti, mais vous pouvez personnaliser la *liste de contacts*. Les utilisateurs ou groupes de la liste des contacts apparaissent dans l’interface utilisateur (IU) pour aider les utilisateurs à obtenir de l’aide concernant l’espace de travail.

1. Accédez au nouveau paramètre **Liste de contacts** de l’une des deux manières suivantes :

    Dans le volet **Créer un espace de travail**, lors de sa création.

    Dans le volet de navigation, sélectionnez la flèche à côté de **Espaces de travail**, sélectionnez **Plus d’options** (...) en regard du nom de l’espace de travail > **Paramètres de l’espace de travail**. Le volet **Paramètres** s’ouvre.

    ![Paramètres de l’espace de travail](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Sous **Avancé** > **Liste de contacts**, acceptez les **Administrateurs de l'espace de travail** ou ajoutez votre propre liste **Utilisateurs ou groupes spécifiques**. 

    ![Contacts de l’espace de travail](media/service-create-the-new-workspaces/power-bi-workspace-contacts.png)

3. Sélectionnez **Enregistrer**.

## <a name="set-a-workspace-onedrive"></a>Définir un espace de travail OneDrive

La fonctionnalité OneDrive de l’espace de travail vous permet de configurer un groupe Microsoft 365 dont le stockage de fichiers de la bibliothèque de documents SharePoint est accessible aux utilisateurs de l’espace de travail. Vous devez d’abord créer le groupe en dehors de Power BI. 

Power BI ne synchronise pas les autorisations des utilisateurs ou des groupes qui sont configurés pour avoir accès à l’espace de travail avec l’appartenance au groupe Microsoft 365. La meilleure pratique consiste à attribuer au même groupe Microsoft 365, dont vous configurez le stockage de fichiers dans ce groupe Microsoft 365, l’[accès à l’espace de travail](#give-access-to-your-workspace). Gérez ensuite l’accès à l’espace de travail en gérant l’appartenance au groupe Microsoft 365. 

1. Accédez au nouveau paramètre **OneDrive de l’espace de travail** de l’une des deux manières suivantes :

    Dans le volet **Créer un espace de travail**, lors de sa création.

    Dans le volet de navigation, sélectionnez la flèche à côté de **Espaces de travail**, sélectionnez **Plus d’options** (...) en regard du nom de l’espace de travail > **Paramètres de l’espace de travail**. Le volet **Paramètres** s’ouvre.

    ![Paramètres de l’espace de travail](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Sous **Avancé** > **OneDrive de l’espace de travail**, tapez le nom du groupe Microsoft 365 que vous avez créé. Tapez simplement le nom, et non l’URL. Power BI récupère automatiquement le OneDrive du groupe.

    ![Spécifier un emplacement OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Sélectionnez **Enregistrer**.

### <a name="access-the-workspace-onedrive-location"></a>Accéder à l’emplacement OneDrive de l’espace de travail

Après avoir configuré l'emplacement OneDrive, vous y accédez de la même manière que vous accédez aux autres sources de données du service Power BI.

1. Dans le volet de navigation, sélectionnez **Obtenir des données** puis, dans la zone **Fichiers**, sélectionnez **Obtenir**.

    ![Obtenir des données, obtenir des fichiers](media/service-create-the-new-workspaces/power-bi-get-data-files.png)

1.  L'entrée **OneDrive - Entreprise** est votre propre OneDrive Entreprise. Le deuxième OneDrive est celui que vous avez ajouté.

    ![Emplacement des fichiers de l’espace de travail - Récupérer des données](media/service-create-the-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

### <a name="connect-to-apps-in-new-workspaces"></a>Se connecter à des applications dans de nouveaux espaces de travail

Le nouvel espace de travail crée et consomme des *applications* au lieu de packs de contenu. Les applications sont des collections de tableaux de bord, de rapports et de jeux de données qui se connectent à des services tiers et à des données organisationnelles. Les applications facilitent l’extraction de données à partir des services tels que Microsoft Dynamics CRM, Salesforce et Google Analytics.

Dans la nouvelle expérience d’espace de travail, vous ne pouvez pas créer ni consommer des packs de contenu d’organisation. Demandez à vos équipes internes de fournir des applications pour tous les packs de contenu que vous utilisez actuellement. 

## <a name="give-access-to-your-workspace"></a>Accorder l’accès à votre espace de travail

Toute personne disposant d’un rôle d’administrateur dans un espace de travail peut accorder à d’autres utilisateurs l’accès à l’espace de travail.

1. Dans la liste de contenu de l’espace de travail, dans la mesure où vous êtes administrateur, vous voyez **Accéder**.

    ![Liste de contenu des espaces de travail](media/service-create-the-new-workspaces/power-bi-workspace-access-icon.png)

1. Ajoutez des groupes de sécurité, des listes de distribution, des groupes Microsoft 365 ou des personnes individuelles à ces espaces de travail en tant que lecteurs, membres, contributeurs ou administrateurs. Consultez [Rôles dans les nouveaux espaces de travail](service-new-workspaces.md#roles-in-the-new-workspaces) pour une explication des différents rôles.

    ![Ajout de membres, d’administrateurs et de contributeurs aux espaces de travail](media/service-create-the-new-workspaces/power-bi-workspace-add-members.png)

9. Sélectionnez **Ajouter** > **Fermer**.


## <a name="distribute-an-app"></a>Distribuer une application

Si vous voulez distribuer du contenu officiel à un large public au sein de votre organisation, vous pouvez publier une *application* à partir de votre espace de travail.  Quand le contenu est prêt, vous choisissez les tableaux de bord et les rapports que vous voulez publier, puis vous les publiez en tant qu’application. Vous pouvez créer une application à partir de chaque espace de travail.

Découvrez comment [publier une application à partir des nouveaux espaces de travail](service-create-distribute-apps.md).

## <a name="next-steps"></a>Étapes suivantes
* Découvrir l’[organisation du travail dans la nouvelle expérience d’espace de travail dans Power BI](service-new-workspaces.md)
* [Créer des espaces de travail classiques](service-create-workspaces.md)
* [Publier une application à partir des nouveaux espaces de travail dans Power BI](service-create-distribute-apps.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
