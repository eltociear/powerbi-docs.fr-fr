---
title: Paramètres de configuration de l’application Power BI
description: Comment personnaliser le comportement de Power BI à l’aide d’un outil MDM
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: a517ee4edce6e18eadcbe2b1b6765684f8121b21
ms.sourcegitcommit: 768e1e4b19fe8c7627010127c2420d63021cb542
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199436"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Configurer à distance l’application Power BI à l’aide d’un outil MDM

L’application Power BI Mobile pour iOS et Android prend en charge des paramètres d’application qui permettent aux administrateurs Office 365 et MDM (par exemple, Intune) de personnaliser le comportement de l’application.

L’application Power BI Mobile pour prend en charge les scénarios de configuration suivants :

- Configuration du serveur de rapports (iOS et Android)
- Paramètres de protection des données (iOS)

## <a name="report-server-configuration-ios-and-android"></a>Configuration du serveur de rapports (iOS et Android)

L’application Power BI pour iOS et Android permet aux administrateurs d’envoyer à distance (« push ») la configuration du serveur de rapports aux appareils inscrits.

| Key | Type | Description |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Chaîne | URL du serveur de rapports.<br><br>Doit commencer par http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Chaîne | [facultatif]<br><br>Nom d’utilisateur à utiliser pour la connexion du serveur.<br><br>Si ce nom n’est pas renseigné, l’application demande à l’utilisateur de taper le nom d’utilisateur pour la connexion.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Chaîne | [facultatif]<br><br>La valeur par défaut est « Report server »<br><br>Nom convivial utilisé dans l’application pour représenter le serveur. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booléen | [facultatif]<br><br>La valeur par défaut est True. Quand la valeur est True, cela remplace la définition de serveur de rapports déjà présente sur l’appareil mobile. Les serveurs existants qui sont déjà configurés sont supprimés. Override défini sur True empêche également l’utilisateur de supprimer cette configuration.<br><br>La valeur False ajoute les valeurs envoyées (push), en conservant les paramètres existants. Si la même URL de serveur est déjà configurée dans l’application mobile, l’application laisse la configuration en l’état. L’application ne demande pas à l’utilisateur de se réauthentifier auprès du même serveur. |

## <a name="data-protection-settings-ios"></a>Paramètres de protection des données (iOS)

L’application Power BI pour iOS permet aux administrateurs de personnaliser la configuration par défaut des paramètres de sécurité et de confidentialité. Vous pouvez forcer les utilisateurs à utiliser Face ID, Touch ID ou un code pour accéder à l’application Power BI.

| Key | Type | Description |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booléen | La valeur par défaut est false. <br><br>L’utilisation de fonctionnalités de biométrie, comme Touch ID ou Face ID, peut être nécessaire pour accéder à l’application sur l’appareil. Lorsque cela se révèle nécessaire, la biométrie est utilisée en plus de l’authentification.<br><br>Si vous utilisez des stratégies de protection des applications, Microsoft recommande de désactiver ce paramètre pour empêcher les invites à double accès. |

## <a name="deploying-app-configuration-settings"></a>Déploiement des paramètres de configuration d’application

Les étapes suivantes sont nécessaires à la création d’une stratégie de configuration des applications. Une fois la stratégie de configuration créée, vous pouvez affecter ses paramètres à des groupes d’utilisateurs.

1. Connectez votre outil MDM.
2. Créez et nommez une stratégie de configuration d’application.
3. Choisissez les utilisateurs auxquels distribuer cette stratégie de configuration d’application.
4. Créez des paires clé-valeur pour le paramètre que vous souhaitez envoyer (push) à vos utilisateurs.

Le portail Intune permet aux administrateurs de déployer facilement ces paramètres sur l’application Power BI par le biais de stratégies de configuration. Toutefois, tous les fournisseurs MDM sont pris en charge. Si vous n’utilisez pas Intune, vous devrez consulter votre documentation MDM pour savoir comment déployer ces paramètres.

## <a name="next-steps"></a>Étapes suivantes

* Obtenir l'application mobile Power BI à partir de l’[App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808)et de [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Suivre [@MSPowerBI sur Twitter](https://twitter.com/MSPowerBI)
* Rejoindre la conversation de la [Communauté Power BI](https://community.powerbi.com/)
