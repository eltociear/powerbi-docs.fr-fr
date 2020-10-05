---
title: Configurer des applications mobiles avec Microsoft Intune
description: Comment configurer les applications mobiles Power BI avec Microsoft Intune. Vous allez voir non seulement comment ajouter et déployer l’application, mais aussi comment créer la stratégie d’application mobile pour contrôler la sécurité.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 214ef5072808decc4c153a28cf231e070c20508d
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524716"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Configurer des applications mobiles avec Microsoft Intune

Microsoft Intune permet aux organisations de gérer des appareils et des applications. Les applications mobiles Power BI pour iOS et Android s’intègrent à Intune. Cette intégration vous permet de gérer l’application sur vos appareils et de contrôler la sécurité. Vous pouvez mettre en place des stratégies de configuration pour contrôler divers éléments, comme la nécessité de disposer d’un code confidentiel d’accès, la façon dont l’application traite les données et même le chiffrement des données de l’application quand cette dernière n’est pas utilisée.

L’application mobile Microsoft Power BI vous permet d’accéder aux informations importantes de votre entreprise. Vous pouvez utiliser les tableaux de bord et les rapports concernant l’ensemble des données des appareils et des applications managés de votre organisation. Pour plus d’informations sur les applications Intune prises en charge, consultez [Applications protégées par Microsoft Intune](/intune/apps/apps-supported-intune-apps).

## <a name="general-mobile-device-management-configuration"></a>Configuration générale de la gestion des appareils mobiles

Cet article part du principe qu’Intune est correctement configuré et que vous avez inscrit des appareils dans Intune. L’article n’a pas pour objet de vous expliquer la configuration complète de Microsoft Intune. Pour plus d’informations sur Intune, consultez [What ' s Intune?](/intune/introduction-intune/) (Intune, qu’est-ce que c’est ?).

Microsoft Intune et la gestion des appareils mobiles peuvent coexister dans Microsoft 365. Si vous utilisez la gestion des appareils mobiles, l’appareil s’affichera comme étant inscrit pour la gestion des appareils mobiles. Cependant, cela ne vous empêche pas de le gérer dans Intune.

Pour que les utilisateurs finaux puissent utiliser l’application Power BI sur leurs appareils, un administrateur Intune doit ajouter l’application à Intune et l’affecter aux utilisateurs finaux.

> [!NOTE]
> Après avoir configuré Intune, l’actualisation des données d’arrière-plan est désactivée pour l’application mobile Power BI sur votre appareil iOS ou Android. Power BI actualise les données à partir du service Power BI sur le web lorsque vous entrez dans l’application.

## <a name="step-1-add-the-power-bi-app-to-intune"></a>Étape 1 : Ajouter l’application Power BI à Intune

Pour ajouter l’application Power BI à Intune, suivez les étapes fournies dans les rubriques suivantes :
- [Ajouter des applications de l’App Store iOS dans Microsoft Intune](/intune/apps/store-apps-ios)
- [Ajouter des applications de l’Android Store à Microsoft Intune](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>Étape 2 : Affecter l’application à vos utilisateurs finaux

Une fois que vous avez ajouté l’application Power BI à Microsoft Intune, vous pouvez l’affecter aux utilisateurs et aux appareils. Il est important de noter que vous pouvez affecter une application à un appareil, qu’il soit ou non managé par Intune.

Pour affecter l’application Power BI aux utilisateurs et aux appareils, procédez comme indiqué dans [Attribuer des applications à des groupes avec Microsoft Intune](/intune/apps/apps-deploy).

## <a name="step-3-create-and-assign-app-protection-policies"></a>Étape 3 : Créer et affecter des stratégies de protection des applications

Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application. Une application gérée est une application à laquelle des stratégies de protection d’application sont appliquées et pouvant être gérée par Intune.

Les stratégies de protection des applications de gestion des applications mobiles vous permettent de gérer et de protéger les données de votre organisation au sein d’une application. La gestion MAM sans inscription (MAM-WE) permet de gérer les applications professionnelles et scolaires contenant des données sensibles sur pratiquement tous types d’appareils, y compris les appareils personnels dans les scénarios BYOD (Apportez votre propre appareil). Pour plus d’informations, consultez [Vue d’ensemble des stratégies de protection des applications](/intune/apps/app-protection-policy).

Pour créer et affecter une stratégie de protection des applications à l’application Power BI, suivez les étapes décrites dans [Guide pratique pour la gestion et l’affectation des stratégies de protection des applications](/intune/apps/app-protection-policies).

## <a name="step-4-use-the-application-on-a-device"></a>Étape 4 : Utiliser l’application sur un appareil

Les applications gérées sont des applications que le support technique de votre entreprise peut configurer pour protéger les données d’entreprise auxquelles vous pouvez accéder dans cette application. Lorsque vous accédez aux données de l’entreprise dans une application managée de votre appareil, vous pouvez remarquer que l’application fonctionne autrement que prévu. Par exemple, vous ne pouvez pas copier et coller des données d’entreprise protégées, ou vous ne pouvez pas enregistrer ces données à certains emplacements.

Pour savoir comment vos utilisateurs finaux peuvent utiliser l’application Power BI sur leur appareil, passez en revue les étapes décrites dans les articles suivants :
- [Utiliser des applications gérées sur votre appareil iOS](https://docs.microsoft.com/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Utiliser des applications gérées sur votre appareil Android](https://docs.microsoft.com/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>Étapes suivantes

[Guide pratique pour créer et affecter des stratégies de protection des applications](/intune/app-protection-policies) 

[Applications Power BI pour appareils mobiles](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)  
