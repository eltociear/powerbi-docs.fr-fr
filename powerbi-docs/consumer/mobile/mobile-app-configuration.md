---
title: Paramètres de configuration de l’application Power BI pour iOS
description: Comment personnaliser le comportement de Power BI pour iOS à l’aide d’un outil MDM
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: c2d619489b042e523c559a16dab249b268389cd5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879427"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Configurer à distance l’application Power BI pour iOS à l’aide d’un outil MDM

L’application Power BI Mobile pour iOS prend en charge des paramètres d’application qui permettent aux administrateurs Office 365 et MDM (par exemple, Intune) de personnaliser le comportement de l’application.

L’application Power BI Mobile pour iOS prend en charge les scénarios de configuration suivants :

- Configuration du serveur de rapports
- Paramètres de protection des données

## <a name="report-server-configuration"></a>Configuration du serveur de rapports

L’application Power BI pour iOS permet aux administrateurs d’envoyer (push) à distance la configuration du serveur de rapports vers les appareils inscrits.

| Key | Type | Description |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Chaîne | URL du serveur de rapports.<br><br>Doit commencer par http/https.|
| com.microsoft.powerbi.mobile.ServerUsername | Chaîne | [facultatif]<br><br>Nom d’utilisateur à utiliser pour la connexion du serveur.<br><br>Si ce nom n’est pas renseigné, l’application demande à l’utilisateur de taper le nom d’utilisateur pour la connexion.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Chaîne | [facultatif]<br><br>La valeur par défaut est « Report server »<br><br>Nom convivial utilisé dans l’application pour représenter le serveur. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booléen | [facultatif]<br><br>La valeur par défaut est True. Quand la valeur est True, cela remplace la définition de serveur de rapports déjà présente sur l’appareil mobile. Les serveurs existants qui sont déjà configurés sont supprimés. Override défini sur True empêche également l’utilisateur de supprimer cette configuration.<br><br>La valeur False ajoute les valeurs envoyées (push), en conservant les paramètres existants. Si la même URL de serveur est déjà configurée dans l’application mobile, l’application laisse la configuration en l’état. L’application ne demande pas à l’utilisateur de se réauthentifier auprès du même serveur. |

## <a name="data-protection-setting"></a>Paramètre de protection des données

L’application Power BI pour iOS permet aux administrateurs de personnaliser la configuration par défaut des paramètres de sécurité et de confidentialité. Vous pouvez forcer les utilisateurs à utiliser Face ID, Touch ID ou un code pour accéder à l’application Power BI.

| Key | Type | Description |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booléen | La valeur par défaut est false. <br><br>L’utilisation de fonctionnalités de biométrie, comme Touch ID ou Face ID, peut être nécessaire pour accéder à l’application sur l’appareil. Lorsque cela se révèle nécessaire, la biométrie est utilisée en plus de l’authentification.<br><br>Si vous utilisez des stratégies de protection des applications, Microsoft recommande de désactiver ce paramètre pour empêcher les invites à double accès. |

## <a name="deploying-app-configuration-settings"></a>Déploiement des paramètres de configuration d’application

Les étapes suivantes vous permettront de créer une stratégie de configuration des applications. Une fois la stratégie de configuration créée, vous pouvez affecter ses paramètres à des groupes d’utilisateurs.

1. Connectez votre outil MDM.

2. Créez et nommez une stratégie de configuration d’application.

3. Choisissez les utilisateurs auxquels distribuer cette stratégie de configuration d’application.

4. Créez des paires clé-valeur pour le paramètre que vous souhaitez envoyer (push) à vos utilisateurs.

Le portail Intune permet aux administrateurs de déployer facilement ces paramètres sur l’application Power BI pour iOS par le biais de stratégies de configuration.
Toutefois, tous les fournisseurs MDM sont pris en charge. Si vous n’utilisez pas Intune, vous devrez consulter votre documentation MDM pour savoir comment déployer ces paramètres.

## <a name="next-steps"></a>Étapes suivantes

* Télécharger l’[application mobile Power BI pour iPhone](https://go.microsoft.com/fwlink/?LinkId=522062)
* Suivre [@MSPowerBI sur Twitter](https://twitter.com/MSPowerBI)
* Rejoindre la conversation de la [Communauté Power BI](https://community.powerbi.com/)
