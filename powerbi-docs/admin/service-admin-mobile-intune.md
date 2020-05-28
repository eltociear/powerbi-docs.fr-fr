---
title: Configurer des applications mobiles avec Microsoft Intune
description: Comment configurer les applications mobiles Power BI avec Microsoft Intune. Vous allez voir non seulement comment ajouter et déployer l’application, mais aussi comment créer la stratégie d’application mobile pour contrôler la sécurité.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: c7d1c9a29c95cb039c90fd339f6e6a38de111916
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563690"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Configurer des applications mobiles avec Microsoft Intune

Microsoft Intune permet aux organisations de gérer des appareils et des applications. Les applications mobiles Power BI pour iOS et Android s’intègrent à Intune. Cette intégration vous permet de gérer l’application sur vos appareils et de contrôler la sécurité. Vous pouvez mettre en place des stratégies de configuration pour contrôler divers éléments, comme la nécessité de disposer d’un code confidentiel d’accès, la façon dont l’application traite les données et même le chiffrement des données de l’application quand cette dernière n’est pas utilisée.

## <a name="general-mobile-device-management-configuration"></a>Configuration générale de la gestion des appareils mobiles

Cet article part du principe qu’Intune est correctement configuré et que vous avez inscrit des appareils dans Intune. L’article n’a pas pour objet de vous expliquer la configuration complète de Microsoft Intune. Pour plus d’informations sur Intune, consultez [What ' s Intune?](/intune/introduction-intune/) (Intune, qu’est-ce que c’est ?).

Microsoft Intune et la gestion des appareils mobiles peuvent coexister dans Microsoft 365. Si vous utilisez la gestion des appareils mobiles (GPM), l’appareil apparaît comme étant inscrit pour la gestion des appareils mobiles, mais vous pouvez tout de même le gérer dans Intune.

> [!NOTE]
> Après avoir configuré Intune, l’actualisation des données d’arrière-plan est désactivée pour l’application mobile Power BI sur votre appareil iOS ou Android. Power BI actualise les données à partir du service Power BI sur le web lorsque vous entrez dans l’application.

## <a name="step-1-get-the-url-for-the-application"></a>Étape 1 : obtenir l’URL de l’application

Avant de créer l’application dans Intune, vous devez obtenir les URL des applications. Pour iOS, vous pouvez obtenir cette information dans iTunes. Pour Android, cette information est disponible dans la page mobile Power BI.

Enregistrez l’URL, car vous en aurez besoin pour créer l’application.

### <a name="get-ios-url"></a>Obtenir l’URL d’iOS

Pour obtenir l’URL de l’application pour iOS, nous devons accéder à iTunes.

1. Ouvrez iTunes.

1. Recherchez *Power BI*.

1. **Microsoft Power BI** doit figurer sous **Applications iPhone** et **Applications iPad**. L’URL étant la même, vous pouvez utiliser l’une ou l’autre.

1. Sélectionnez la liste déroulante **Télécharger** , puis sélectionnez **Copier le lien**.

    ![URL de l’application iTunes](media/service-admin-mobile-intune/itunes-url.png)

L’URL doit ressembler à ce qui suit : *https://itunes.apple.com/us/app/microsoft-power-bi/id929738808?mt=8* .

### <a name="get-android-url"></a>Obtenir l’URL d’Android

Vous pouvez obtenir l’URL de Google Play à partir de la [page Power BI mobile](https://powerbi.microsoft.com/mobile/). Sélectionnez **Télécharger à partir de Google Play** pour accéder à la page de l’application. Vous pouvez copier l’URL à partir de la barre d’adresses du navigateur. Elle doit ressembler à ce qui suit : *https://play.google.com/store/apps/details?id=com.microsoft.powerbim* .

## <a name="step-2-create-a-mobile-application-management-policy"></a>Étape 2 : créer une stratégie de gestion des applications mobiles

La stratégie de gestion des applications mobiles vous permet de forcer certains éléments, comme un code confidentiel d’accès. Vous pouvez en créer un dans le portail Intune.

Vous pouvez commencer par créer l’application ou la stratégie. L’ordre dans lequel vous les ajoutez n’a pas d’importance. Ces deux éléments doivent simplement exister au moment du déploiement.

1. Dans le portail Intune, sélectionnez **Stratégie** > **Stratégies de configuration**.

    ![Portail Intune](media/service-admin-mobile-intune/intune-policy.png)

1. Sélectionnez **Ajouter**.

1. Sous **Logiciels** , vous pouvez sélectionner la gestion des applications mobiles pour Android ou iOS. Pour démarrer rapidement, vous pouvez soit sélectionner **Créer une stratégie avec les paramètres recommandés**, soit créer une stratégie personnalisée.

1. Modifiez la stratégie pour configurer les restrictions désirées sur l’application.

## <a name="step-3-create-the-application"></a>Étape 3 : créer l’application

L’application est une référence ou un package qui est enregistré dans Intune en vue de son déploiement. Nous allons créer une application et référencer l’URL de l’application que nous avons obtenue dans Google Play ou iTunes.

Vous pouvez commencer par créer l’application ou la stratégie. L’ordre dans lequel vous les ajoutez n’a pas d’importance. Ces deux éléments doivent simplement exister au moment du déploiement.

1. Accédez au portail Intune et sélectionnez **Applications** dans le menu de gauche.

1. Sélectionnez **Ajouter une application**. L’application **Ajouter le logiciel** est alors lancée.

### <a name="create-for-ios"></a>Créer pour iOS

1. Sélectionnez **Application iOS gérée à partir de l’App Store** dans la liste déroulante.

1. Entrez l’URL de l’application obtenue à l’[étape 1](#step-1-get-the-url-for-the-application), puis sélectionnez **Suivant**.

    ![Installation du logiciel : iOS](media/service-admin-mobile-intune/intune-add-software-ios1.png)

1. Indiquez un **Éditeur**, un **Nom** et une **Description**. Vous pouvez éventuellement fournir une **Icône**. La **Catégorie** s’applique à l’application Portail d’entreprise. Une fois que vous avez terminé, sélectionnez **Suivant**.

1. Vous pouvez indiquer comment vous souhaitez publier l’application : **N’importe lequel** (par défaut), **iPad** ou **iPhone**. L’option **N’importe lequel** est sélectionnée par défaut et fonctionne pour les deux types d’appareils. L’URL de l’application Power BI est la même pour iPhone et iPad. Sélectionnez **Suivant**.

1. Sélectionnez **Charger**.

1. Si vous ne voyez pas l’application dans la liste, actualisez la page : accédez à **Vue d’ensemble** puis revenez à **Applications**.

    ![Onglet Applications](media/service-admin-mobile-intune/intune-add-software-ios2.png)

### <a name="create-for-android"></a>Créer pour Android

1. Sélectionnez **Lien externe** dans la liste déroulante.

1. Entrez l’URL de l’application obtenue à l’[étape 1](#step-1-get-the-url-for-the-application), puis sélectionnez **Suivant**.

    ![Installation du logiciel : Téléphone](media/service-admin-mobile-intune/intune-add-software-android1.png)

1. Indiquez un **Éditeur**, un **Nom** et une **Description**. Vous pouvez éventuellement fournir une **Icône**. La **Catégorie** s’applique à l’application Portail d’entreprise. Une fois que vous avez terminé, sélectionnez **Suivant**.

1. Sélectionnez **Charger**.

1. Si vous ne voyez pas l’application dans la liste, actualisez la page : accédez à **Vue d’ensemble** puis revenez à **Applications**.

    ![Onglet Applications](media/service-admin-mobile-intune/intune-add-software-android2.png)

## <a name="step-4-deploy-the-application"></a>Étape 4 : déployer l’application

Après avoir ajouté l’application, vous devez la déployer pour qu’elle soit accessible à vos utilisateurs finaux. C’est au cours de cette étape que vous allez lier la stratégie créée à l’application.

### <a name="deploy-for-ios"></a>Déployer pour iOS

1. Dans l’écran des applications, sélectionnez l’application que vous avez créée. Sélectionnez ensuite le lien **Gérer le déploiement** .

    ![Gérer le déploiement](media/service-admin-mobile-intune/intune-deploy-ios1.png)

1. Dans l’écran **Sélectionner des groupes** , vous pouvez choisir les groupes vers lesquels vous souhaitez déployer cette application. Sélectionnez **Suivant**.

1. Dans l’écran **Action de déploiement** , vous pouvez choisir la façon dont vous souhaitez déployer cette application. Sélectionnez **Installation disponible**ou **Installation requise**pour rendre l’application disponible dans le Portail d’entreprise et permettre aux utilisateurs de l’installer à la demande. Après avoir effectué votre sélection, sélectionnez **Suivant**.

    ![Action de déploiement](media/service-admin-mobile-intune/intune-deploy-ios2.png)

1. Dans l’écran **Gestion des applications mobiles**, vous pouvez sélectionner la stratégie de gestion des applications mobiles que vous avez créée à l’[étape 2](#step-2-create-a-mobile-application-management-policy). Si la stratégie que vous avez créée est la seule stratégie iOS disponible, elle est sélectionnée par défaut. Sélectionnez **Suivant**.

    ![Gestion des applications mobiles](media/service-admin-mobile-intune/intune-deploy-ios3.png)

1. Dans l’écran **Profil VPN** , vous pouvez sélectionner une stratégie s’il en existe une pour votre organisation. L’option **Aucun**est sélectionnée par défaut. Sélectionnez **Suivant**.

1. Dans l’écran **Configuration des applications mobiles** , vous pouvez sélectionner une **Stratégie de configuration des applications** si vous en avez créé une. L’option **Aucun**est sélectionnée par défaut. Cette opération est facultative. Sélectionnez **Terminer**.

Une fois l’application déployée, la mention **Oui** doit apparaître en regard de Déployé dans la page des applications.

### <a name="deploy-for-android"></a>Déployer pour Android

1. Dans l’écran des applications, sélectionnez l’application que vous avez créée. Sélectionnez ensuite le lien **Gérer le déploiement** .

    ![Gérer le déploiement](media/service-admin-mobile-intune/intune-deploy-android1.png)
1. Dans l’écran **Sélectionner des groupes** , vous pouvez choisir les groupes vers lesquels vous souhaitez déployer cette application. Sélectionnez **Suivant**.

1. Dans l’écran **Action de déploiement** , vous pouvez choisir la façon dont vous souhaitez déployer cette application. Sélectionnez **Installation disponible**ou **Installation requise**pour rendre l’application disponible dans le Portail d’entreprise et permettre aux utilisateurs de l’installer à la demande. Après avoir effectué votre sélection, sélectionnez **Suivant**.

    ![Action de déploiement](media/service-admin-mobile-intune/intune-deploy-android2.png)

1. Dans l’écran **Gestion des applications mobiles**, vous pouvez sélectionner la stratégie de gestion des applications mobiles que vous avez créée à l’[étape 2](#step-2-create-a-mobile-application-management-policy). Si la stratégie que vous avez créée est la seule stratégie Android disponible, elle est sélectionnée par défaut. Sélectionnez **Terminer**.

    ![Gestion des applications mobiles](media/service-admin-mobile-intune/intune-deploy-android3.png)

Une fois l’application déployée, la mention **Oui** doit apparaître en regard de Déployé dans la page des applications.

## <a name="step-5-install-the-application-on-a-device"></a>Étape 5 : installer l’application sur un appareil

Vous installez l’application par l’intermédiaire de l’application *Portail d’entreprise*. Si vous n’avez pas installé le Portail d’entreprise, vous pouvez le télécharger à partir du magasin d’applications de la plateforme iOS ou Android. Vous devez vous connecter au Portail d’entreprise avec les identifiants de votre organisation.

1. Ouvrez l’application Portail d’entreprise.

1. Si l’application Power BI ne figure pas parmi les applications proposées, sélectionnez **Applications d’entreprise**.

    ![Applications d’entreprise](media/service-admin-mobile-intune/intune-companyportal1.png)

1. Sélectionnez l’application Power BI que vous avez déployée.

    ![Application Power BI](media/service-admin-mobile-intune/intune-companyportal2.png)

1. Sélectionnez **Installer**.

    ![Installer l’application](media/service-admin-mobile-intune/intune-companyportal3.png)

1. Si vous êtes sur iOS, l’application est envoyée (Push) à votre appareil. Sélectionnez **Installer** dans la boîte de dialogue d’envoi (Push).

    ![Installation de l’application](media/service-admin-mobile-intune/intune-companyportal5.png)

1. Une fois l’installation de l’application terminée, la mention **Géré par votre entreprise**s’affiche. Si vous avez activé l’accès avec un code confidentiel dans la stratégie, voici ce qui apparaît à l’écran.

    ![Entrez le code confidentiel](media/service-admin-mobile-intune/intune-powerbi-pin.png)

## <a name="next-steps"></a>Étapes suivantes

[Configurer et déployer des stratégies de gestion des applications mobiles dans la console Microsoft Intune](/intune/app-protection-policies/)  

[Applications Power BI pour appareils mobiles](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)  
