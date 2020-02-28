---
title: Se connecter à Snowflake avec Power BI
description: Snowflake avec l’authentification unique pour Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 03e6e8efae5cd4a5f61e3d07bc0b3c524b3b0a46
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77429346"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Se connecter à Snowflake dans le service Power BI

## <a name="introduction"></a>Introduction

La connexion à Snowflake dans le service Power BI est identique à celle des autres connecteurs, à une différence près : une capacité supplémentaire est offerte pour AAD (avec une option pour l’authentification unique). Les différents aspects de l’intégration nécessitent des rôles d’administration différents sur Snowflake, Power BI et Azure. Vous pouvez également choisir d’activer l’authentification AAD sans utiliser l’authentification unique. L’authentification de base fonctionne de la même façon qu’avec d’autres connecteurs du service.

Si vous souhaitez configurer l’intégration AAD et éventuellement activer l’authentification unique :
* Si vous êtes administrateur Snowflake, consultez l’article [Power BI SSO to Snowflake - Getting Started](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) (Utilisation de Power BI pour accéder à Snowflake avec l’authentification unique - Prise en main) de la documentation Snowflake.
* (SSO) Si vous êtes administrateur Power BI, consultez la section « Configuration du service Power BI - portail d’administration ».
* (SSO) Si vous êtes créateur de jeux de données Power BI, consultez la section « Configuration du service Power BI - Activation d’un jeu de données ».

## <a name="power-bi-service-configuration"></a>Configuration du service Power BI

### <a name="admin-portal"></a>Portail d’administration

Si vous souhaitez activer l’authentification unique, l’administrateur du locataire doit accéder au portail d’administration et approuver l’envoi d’informations d’identification AAD Power BI à Snowflake.

![Paramètres d’administration de locataire pour l’authentification unique Snowflake](media/service-connect-snowflake/snowflakessotenant.png)

Accédez au « portail d’administration », sélectionnez l’élément « Paramètres du client » de la barre latérale et faites défiler la page jusqu’à « Paramètres d’intégration ». Vous voyez l’option « SSO Snowflake ».

Comme nous l’avons déjà expliqué, vous devez l’activer manuellement pour autoriser l’envoi de votre jeton AAD aux serveurs Snowflake. Pour l’activer, cliquez sur le bouton bascule « Désactivé », puis sur Appliquer. Attendez que la modification des paramètres soit prise en compte. La propagation de la configuration par le service peut prendre jusqu’à une heure.

Une fois cette opération effectuée, vous pouvez utiliser des rapports avec l’authentification unique.

### <a name="configuring-a-dataset-with-aad"></a>Configuration d’un jeu de données avec AAD

Dès lors qu’un rapport basé sur le connecteur Snowflake a été publié sur le web, dans le service web Power BI, le créateur de jeu de données doit accéder à l’espace de travail approprié, sélectionner « Jeux de données », puis « Paramètres » (dans le menu « ... » donnant accès à des actions supplémentaires, en regard du jeu de données approprié).

De par le mode de fonctionnement de Power BI, l’authentification unique fonctionne seulement si aucune source de données n’est exécutée par le biais de la passerelle de données locale.

* Si vous utilisez uniquement une source Snowflake dans votre modèle de données, vous pouvez utiliser l’authentification unique si vous choisissez de ne pas utiliser la passerelle de données locale.
* Si vous utilisez une source Snowflake et une autre source, vous pouvez utiliser l’authentification unique si aucune des sources n’utilise la passerelle de données locale.
* Si vous utilisez une source Snowflake par le biais de la passerelle de données locale, vous pouvez utiliser des informations d’identification AAD, mais pas l’authentification unique. Ceci peut être utile si vous essayez d’accéder à un réseau virtuel à partir d’une seule adresse IP sur laquelle la passerelle est installée, plutôt qu’à partir de l’intégralité de la plage d’adresses IP de Power BI.
* Si vous utilisez une source Snowflake et une autre source qui nécessite une passerelle, vous devez également utiliser Snowflake par le biais de la passerelle de données locale et vous ne pouvez pas utiliser l’authentification unique.

Pour plus d’informations sur l’utilisation de la passerelle de données locale, consultez l’article [Qu’est-ce qu’une passerelle de données locale ?](https://docs.microsoft.com/power-bi/service-gateway-onprem)

Si vous n’utilisez pas la passerelle, vous êtes prêt. Si vous avez des informations d’identification Snowflake qui sont configurées sur votre passerelle de données locale, mais que vous utilisez uniquement cette source de données dans votre modèle, vous pouvez cliquer sur le bouton bascule sur la page Paramètres du jeu de données pour désactiver la passerelle pour ce modèle de données.

![Paramètres du jeu de données - Utilisation de la passerelle désactivée](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

Le créateur de jeu de données doit sélectionner « informations d’identification de la source de données » et se connecter. Vous pouvez connecter le jeu de données à Snowflake avec des informations d’identification de base ou OAuth2 (AAD). Si vous choisissez d’utiliser AAD, vous pouvez activer l’utilisation de l’authentification unique pour le jeu de données. Quand ce premier utilisateur se connecte à Snowflake pour le jeu de données, il doit sélectionner l’option spécifiant que les autres utilisateurs utiliseront leurs informations d’identification Oauth2 pour récupérer les données. Cette option active l’authentification unique AAD. Que l’utilisateur initial se connecte ou non avec l’authentification de base ou OAuth2 (AAD), ce sont les informations d’identification AAD qui seront envoyées pour l’authentification unique. 

![Paramètres du jeu de données pour l’authentification unique Snowflake](media/service-connect-snowflake/snowflakessocredui.png)

Par la suite, les utilisateurs supplémentaires devront systématiquement utiliser l’authentification AAD pour se connecter aux données à partir de ce jeu de données Snowflake.

Si vous choisissez de ne pas activer l’authentification unique, les utilisateurs qui actualisent le rapport utiliseront les informations d’identification de l’utilisateur qui s’est connecté, comme avec la plupart des autres rapports de Power BI.

### <a name="troubleshooting"></a>Résolution des problèmes

Si vous rencontrez des problèmes d’intégration, reportez-vous au [guide de résolution des problèmes](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting) Snowflake.

