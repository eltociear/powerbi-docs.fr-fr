---
title: Configurer à distance l’accès d’une application mobile iOS Power BI à un serveur de rapports
description: Découvrez comment configurer à distance les applications mobiles iOS pour votre serveur de rapports.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2018
ms.author: maggies
ms.openlocfilehash: bbade67c9510b8d316364d991c09444712309514
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34722175"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>Configurer à distance l’accès d’une application mobile iOS Power BI à un serveur de rapports

Dans cet article, découvrez comment utiliser l’outil MDM de votre organisation pour configurer l’accès de l’application mobile iOS Power BI à un serveur de rapports. Pour faire cette configuration, les administrateurs informatiques créent une stratégie de configuration d’application avec les informations nécessaires à envoyer (push) à l’application. 

 Ensuite, les utilisateurs d’application mobile Power BI iOS peuvent se connecter au serveur de rapports de leur organisation plus facilement, car la connexion au serveur de rapports est déjà configurée. 


## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>Créer la stratégie de configuration d’application dans l’outil MDM 

En tant qu’administrateur, vous utilisez les étapes suivantes dans Microsoft Intune pour créer la stratégie de configuration d’application. Les étapes et l’expérience de conception de la stratégie de configuration d’application peuvent être différentes dans d’autres outils MDM. 

1. Connectez votre outil MDM. 
2. Créez et nommez une stratégie de configuration d’application. 
3. Choisissez les utilisateurs auxquels distribuer cette stratégie de configuration d’application. 
4. Créez des paires clé-valeur. 

Le tableau suivant détaille les paires.

|Clé  |Type  |Description  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | String | URL du serveur de rapports </br> Doit commencer par http/https |
| com.microsoft.powerbi.mobile.ServerUsername | String | [facultatif] </br> Nom d’utilisateur à utiliser pour la connexion du serveur. </br> Si ce nom n’est pas renseigné, l’application demande à l’utilisateur de taper le nom d’utilisateur pour la connexion.| 
| com.microsoft.powerbi.mobile.ServerDisplayName | String | [facultatif] </br> La valeur par défaut est « Report server » </br> Nom convivial utilisé dans l’application pour représenter le serveur | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | La valeur par défaut est True </br> Si la valeur est « True », ceci remplace la définition de serveur de rapports déjà présente dans l’appareil mobile (les serveurs existants déjà configurés sont supprimés). </br> Override défini sur True empêche également l’utilisateur de supprimer cette configuration. </br> La valeur « False » ajoute les valeurs envoyées (push), en conservant les paramètres existants. </br> Si la même URL de serveur est déjà configurée dans l’application mobile, l’application laisse la configuration telle quelle et ne demande pas à l’utilisateur de se réauthentifier pour le même serveur. |

Voici un exemple de définition de stratégie de configuration avec Intune.

![Paramètres de configuration Intune](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>Utilisateurs finaux se connectant à un serveur de rapports

Après la publication de la stratégie de configuration d’application, les utilisateurs et les appareils appartenant à la liste de distribution définie pour cette stratégie ont l’expérience suivante quand ils démarrent l’application mobile iOS Power BI. 

1. Ils voient un message indiquant que leur application mobile est configurée avec un serveur de rapports, puis ils appuient sur **Se connecter**.

    ![Se connecter au serveur de rapports](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  Dans la page **Se connecter au serveur**, les détails du serveur de rapports sont déjà renseignés. Ils appuient sur **Se connecter**.

    ![Détails du serveur de rapports renseignés](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. Ils tapent un mot de passe pour s’authentifier, puis appuient sur **Se connecter**. 

    ![Détails du serveur de rapports renseignés](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

Ils peuvent désormais afficher et interagir avec les indicateurs de performance clés et les rapports Power BI stockés sur le serveur de rapports.

## <a name="next-steps"></a>Étapes suivantes
[Vue d’ensemble de l’administrateur](admin-handbook-overview.md)  
[Installer Power BI Report Server](install-report-server.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

