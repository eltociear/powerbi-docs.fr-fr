---
title: Autorisations Power BI
description: Autorisations Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 4ba0e62dd8c9ba537f56c97489541591ec0bf2bc
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34289415"
---
# <a name="power-bi-permissions"></a>Autorisations Power BI
## <a name="permission-scopes"></a>Étendues des autorisations
Les autorisations Power BI donnent à une application la possibilité d’effectuer certaines actions au nom d’un utilisateur. Toutes les autorisations doivent être approuvées par un utilisateur pour être valides.

| Nom complet | Description | Valeur de l’étendue |
| --- | --- | --- |
| Afficher tous les jeux de données |L’application peut afficher tous les jeux de données pour l’utilisateur connecté et ceux auxquels il a accès. |Dataset.Read.All |
| Lire et écrire tous les jeux de données |L’application peut afficher tous les jeux de données pour l’utilisateur connecté et ceux auxquels il a accès, ainsi qu’y écrire. |Dataset.ReadWrite.All |
| Ajouter des données à un jeu de données d’un utilisateur (version préliminaire) |Autorise l’application à ajouter ou supprimer les lignes de jeu de données d’un utilisateur. Cette autorisation ne permet pas à l’application d’accéder aux données de l’utilisateur. |Data.Alter_Any |
| Créer du contenu (version préliminaire) |L’application peut créer automatiquement du contenu et des jeux de données pour un utilisateur. |Content.Create |
| Afficher des groupes d’utilisateurs |L’application peut afficher tous les groupes auxquels l’utilisateur connecté appartient. |Group.Read |
| Afficher tous les groupes |L’application peut afficher tous les groupes auxquels l’utilisateur connecté appartient. |Group.Read.All |
| Afficher tous les tableaux de bord (version préliminaire) |L’application peut afficher tous les tableaux de bord pour l’utilisateur connecté et ceux auxquels il a accès. |Dashboard.Read.All |
| Afficher tous les rapports (version préliminaire) |L’application peut afficher tous les rapports de l’utilisateur connecté et ceux auxquels celui-ci a accès. Elle peut également afficher les données des rapports, ainsi que sa structure. |Report.Read.All |
| Lire et écrire tous les rapports |L’application peut afficher tous les rapports pour l’utilisateur connecté et ceux auxquels il a accès, ainsi qu’y écrire. Cela n’octroie pas les droits nécessaires pour créer un nouveau rapport. |Report.ReadWrite.All |

Une application peut demander des autorisations lorsqu’elle tente de se connecter pour la première fois à la page d’un utilisateur en transmettant les autorisations requises dans le paramètre d’étendue de l’appel. Si les autorisations sont accordées, un jeton d’accès est renvoyé à l’application et peut être utilisé lors des appels d’API ultérieurs. Seule une application particulière peut bénéficier de l’accès.

> [!NOTE]
> Les API Power BI font toujours référence aux espaces de travail d’application en tant que groupes. Toutes les références aux groupes indiquent que vous travaillez avec des espaces de travail d’application.
> 
> 

## <a name="requesting-permissions"></a>Demande d’autorisations
Même si vous pouvez appeler l’API pour vous authentifier à l’aide d’un nom d’utilisateur et d’un mot de passe, pour effectuer des actions au nom d’un autre utilisateur, vous devrez demander des autorisations que l’utilisateur doit approuver, puis envoyer le jeton d’accès obtenu lors de tous les appels ultérieurs. Pour ce processus, nous allons suivre le protocole [OAuth 2.0 standard](http://oauth.net/2/). Bien que l’implémentation réelle puisse varier, le flux OAuth pour Power BI comporte les éléments suivants :

* **Interface utilisateur de connexion** : il s’agit d’une interface utilisateur que le développeur peut appeler pour demander des autorisations. L’utilisateur doit se connecter si ce n’est pas déjà fait. L’utilisateur doit également approuver les autorisations demandées par l’application. La fenêtre de connexion renvoie un code d’accès ou un message d’erreur à une URL de redirection fournie.
  * Une URL de redirection standard doit être fournie par Power BI à l’usage des applications natives.
* **Code d’autorisation** : les codes d’autorisation sont retournés aux applications web à la suite d’une connexion via les paramètres d’URL définis dans l’URL de redirection. Dans la mesure où ils se trouvent dans les paramètres, il existe un risque relatif à la sécurité. Les applications web doivent échanger le code d’autorisation contre un jeton d’autorisation.
* **Jetons d’autorisation** : ils permettent d’authentifier les appels d’API effectués pour le compte d’un autre utilisateur. Ils sont limités à une application particulière. Les jetons ont une durée de vie définie et doivent être actualisés au moment de leur expiration.
* **Actualiser le jeton** : quand un jeton expire, un processus est lancé pour les actualiser.

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

