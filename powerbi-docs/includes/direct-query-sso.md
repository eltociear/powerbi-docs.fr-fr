---
title: Fichier include
description: Fichier include
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82255814"
---
## <a name="single-sign-on"></a>Authentification unique

Une fois que vous avez publié un jeu de données Azure SQL DirectQuery sur le service, vous pouvez activer l’authentification unique via OAuth2 d’Azure Active Directory (Azure AD) pour vos utilisateurs finaux.

Pour activer l’authentification unique, accédez aux paramètres du jeu de données, ouvrez l’onglet **Sources de données**, puis cochez la case de l’authentification unique.

![Configurer la boîte de dialogue DQ de SQL Azure](media/direct-query-sso/sso-dialog.png)

Quand l’option d’authentification unique est activée et que vos utilisateurs accèdent aux rapports basés sur la source de données, Power BI envoie leurs informations d’identification Azure AD dans les requêtes à Azure SQL Database ou à l’entrepôt de données. Cette option permet à Power BI de respecter les paramètres de sécurité qui sont configurés au niveau de la source de données.

L’option d’authentification unique prend effet sur tous les jeux de données qui utilisent cette source de données. Elle n’affecte pas la méthode d’authentification utilisée pour les scénarios d’importation.

