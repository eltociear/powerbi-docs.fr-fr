---
title: Configurer à distance l’accès d’une application mobile à un serveur de rapports
description: Découvrez comment configurer à distance les applications mobiles pour votre serveur de rapports.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: b84d7a23cf947b18302c761ff5f78143bf3356aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73925874"
---
# <a name="configure-power-bi-mobile-app-access-to-report-server-remotely"></a>Configurer à distance l’accès d’une application mobile Power BI à un serveur de rapports

S’applique à :

| ![iPhone](./media/configure-powerbi-mobile-apps-remote/ios-logo-40-px.png) | ![Téléphone Android](./media/configure-powerbi-mobile-apps-remote/android-logo-40-px.png) |
|:--- |:--- |
| iOS |Téléphone |

Dans cet article, découvrez comment utiliser l’outil MDM de votre organisation pour configurer l’accès de l’application mobile Power BI à un serveur de rapports. Pour le configurer, les administrateurs informatiques créent une stratégie de configuration d’application avec les informations nécessaires à envoyer (par push) à l’application. 

 Une fois la connexion au serveur de rapports déjà configurée, les utilisateurs d’application mobile Power BI peuvent se connecter plus facilement au serveur de rapports de leur organisation. 

## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Créer la stratégie de configuration d’application dans l’outil MDM 

En tant qu’administrateur, utilisez les étapes suivantes dans Microsoft Intune pour créer la stratégie de configuration d’application. Les étapes et l’expérience de conception de la stratégie de configuration d’application peuvent être différentes dans d’autres outils MDM. 

1. Connectez votre outil MDM. 
2. Créez et nommez une stratégie de configuration d’application. 
3. Choisissez les utilisateurs auxquels distribuer cette stratégie de configuration d’application. 
4. Créez des paires clé-valeur. 

Le tableau suivant détaille les paires.

|Clé  |Type  |Description  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | Chaîne | URL du serveur de rapports <br> Doit commencer par http/https |
| com.microsoft.powerbi.mobile.ServerUsername | Chaîne | [facultatif] <br> Nom d’utilisateur à utiliser pour la connexion du serveur. <br> Si ce nom n’est pas renseigné, l’application demande à l’utilisateur de taper le nom d’utilisateur pour la connexion.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | Chaîne | [facultatif] <br> La valeur par défaut est « Report server » <br> Nom convivial utilisé dans l’application pour représenter le serveur | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | La valeur par défaut est True <br>Quand la valeur est « True », cela remplace toute définition de serveur de rapports déjà présente dans l’appareil mobile. Les serveurs existants qui sont déjà configurés sont supprimés. <br> Override défini sur True empêche également l’utilisateur de supprimer cette configuration. <br> La valeur « False » ajoute les valeurs envoyées (push), en conservant les paramètres existants. <br> Si la même URL de serveur est déjà configurée dans l’application mobile, l’application laisse la configuration en l’état. L’application ne demande pas à l’utilisateur de se réauthentifier pour le même serveur. |

Voici un exemple de définition de stratégie de configuration avec Intune.

![Paramètres de configuration Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-report-server"></a>Utilisateurs finaux se connectant à un serveur de rapports

 Supposons que vous publiez la stratégie de configuration d’application pour une liste de distribution. Quand les utilisateurs et les appareils figurant sur cette liste de distribution démarrent l’application mobile, ils ont l’expérience suivante. 

1. Ils voient un message indiquant que leur application mobile est configurée avec un serveur de rapports, puis ils appuient sur **Se connecter**.

    ![Se connecter au serveur de rapports](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Dans la page **Se connecter au serveur**, les détails du serveur de rapports sont déjà renseignés. Ils appuient sur **Se connecter**.

    ![Détails du serveur de rapports renseignés](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Ils tapent un mot de passe pour s’authentifier, puis appuient sur **Se connecter**. 

    ![Détails du serveur de rapports renseignés](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Ils peuvent désormais afficher et interagir avec les indicateurs de performance clés et les rapports Power BI stockés sur le serveur de rapports.

## <a name="next-steps"></a>Étapes suivantes

- [Activer l’accès à distance pour Power BI Mobile avec le proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-integrate-with-power-bi)
- [Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
- [Installer Power BI Report Server](install-report-server.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

