---
title: Autorisations Power BI
description: Autorisations Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 51c43a19613381d39e0397864e55baed2022663c
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79491361"
---
# <a name="power-bi-permissions"></a>Autorisations Power BI

## <a name="permission-scopes"></a>Étendues des autorisations

Les autorisations Power BI donnent à une application la possibilité d’effectuer certaines actions au nom d’un utilisateur. Toutes les autorisations doivent être approuvées par un utilisateur pour être valides.

| Nom complet | Description | Valeur de l’étendue |
| --- | --- | --- |
| Afficher tous les jeux de données |L’application peut afficher tous les jeux de données pour l’utilisateur connecté et ceux auxquels il a accès. |Dataset.Read.All |
| Lire et écrire tous les jeux de données |L’application peut afficher tous les jeux de données pour l’utilisateur connecté et ceux auxquels il a accès, ainsi qu’y écrire. |Dataset.ReadWrite.All |
| Ajouter des données au jeu de données d’un utilisateur |Autorise l’application à ajouter ou supprimer les lignes de jeu de données d’un utilisateur. Cette autorisation ne permet pas à l’application d’accéder aux données de l’utilisateur. |Data.Alter_Any |
| Créer du contenu |L’application peut créer automatiquement du contenu et des jeux de données pour un utilisateur. |Content.Create |
| Afficher des groupes d’utilisateurs |L’application peut afficher tous les groupes auxquels l’utilisateur connecté appartient. |Group.Read |
| Afficher tous les groupes |L’application peut afficher tous les groupes auxquels l’utilisateur connecté appartient. |Group.Read.All |
| Lire et écrire tous les groupes |L’application peut afficher et écrire sur tous les groupes de l’utilisateur connecté et sur ceux auxquels il a accès. |Group.ReadWrite.All |
| Afficher tous les tableaux de bord |L’application peut afficher tous les tableaux de bord pour l’utilisateur connecté et ceux auxquels il a accès. |Dashboard.Read.All |
| Afficher tous les rapports |L’application peut afficher tous les rapports de l’utilisateur connecté et ceux auxquels celui-ci a accès. Elle peut également afficher les données des rapports, ainsi que sa structure. |Report.Read.All |
| Lire et écrire tous les rapports |L’application peut afficher tous les rapports pour l’utilisateur connecté et ceux auxquels il a accès, ainsi qu’y écrire. Cela n’octroie pas les droits nécessaires pour créer un nouveau rapport. |Report.ReadWrite.All |
| Lire et écrire toutes les capacités |L’application peut afficher et écrire sur toutes les capacités de l’utilisateur connecté et sur celles auxquels il a accès. Cela n’accorde pas les droits nécessaires pour créer une nouvelle capacité. |Capacities.ReadWrite.All |
| Lire toutes les capacités |L’application peut afficher et écrire sur toutes les capacités de l’utilisateur connecté et sur celles auxquels il a accès. Cela n’accorde pas les droits nécessaires pour créer une nouvelle capacité. |Capacities.Read.All |
| Lire et écrire tout le contenu dans un locataire |L’application peut afficher et écrire sur tous les artefacts, tels que les groupes, les rapports, les tableaux de bord et les jeux de données dans Power BI. À la condition que l’utilisateur connecté soit administrateur du service Power BI. |Tenant.ReadWrite.All |
| Afficher tout le contenu dans un locataire |L’application peut afficher tous les artefacts, tels que les groupes, les rapports, les tableaux de bord et les jeux de données dans Power BI. À la condition que l’utilisateur connecté soit administrateur du service Power BI. |Tenant.Read.All |

Une application peut demander des autorisations lorsqu’elle tente de se connecter pour la première fois à la page d’un utilisateur en transmettant les autorisations requises dans le paramètre d’étendue de l’appel. Si les autorisations sont accordées, un jeton d’accès est retourné à l’application et peut être utilisé lors des appels d’API ultérieurs. Seule une application particulière peut bénéficier de l’accès.

> [!NOTE]
> Les API Power BI font encore référence aux espaces de travail en tant que groupes. Toutes les références à des groupes indiquent que vous travaillez avec des espaces de travail.

## <a name="requesting-permissions"></a>Demande d’autorisations

Même si vous pouvez appeler l’API pour vous authentifier à l’aide d’un nom d’utilisateur et d’un mot de passe, pour effectuer des actions au nom d’un autre utilisateur, vous devrez demander des autorisations que l’utilisateur doit approuver, puis envoyer le jeton d’accès obtenu lors de tous les appels ultérieurs. Pour ce processus, nous allons suivre le protocole [OAuth 2.0 standard](https://oauth.net/2/). Bien que l’implémentation réelle puisse varier, le flux OAuth pour Power BI comporte les éléments suivants :

* **Interface utilisateur de connexion** - Le développeur peut appeler cette interface utilisateur pour demander des autorisations. L’utilisateur doit se connecter si ce n’est pas déjà fait. L’utilisateur doit également approuver les autorisations demandées par l’application. La fenêtre de connexion renvoie un code d’accès ou un message d’erreur à une URL de redirection fournie.
  * Une URL de redirection standard doit être fournie par Power BI à l’usage des applications natives.
* **Code d’autorisation** - Des codes d’autorisation sont retournés aux applications web à la suite d’une connexion via les paramètres d’URL définis dans l’URL de redirection. Dans la mesure où ils se trouvent dans les paramètres, il existe un risque de sécurité. Les applications web doivent échanger le code d’autorisation contre un jeton d’autorisation.
* **Jetons d’autorisation** : ils permettent d’authentifier les appels d’API effectués pour le compte d’un autre utilisateur. Ils sont limités à une application particulière. Les jetons ont une durée de vie définie et doivent être actualisés au moment de leur expiration.
* **Actualiser le jeton** : quand un jeton expire, un processus est lancé pour les actualiser.

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)