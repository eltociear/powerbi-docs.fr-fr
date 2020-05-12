---
title: Présentation du principal de service
description: Présentation du principal de service
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82616027"
---
Le principal de service est une méthode d’authentification qui peut être utilisée pour permettre l’accès d’une application Azure AD à des API ou un contenu de service Power BI.

Lorsque vous créez une application Azure Active Directory (Azure AD), un [objet principal de service](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) est créé. L’objet principal de service, également connu sous le nom de *principal de service*, permet à Azure AD d’authentifier votre application. Une fois authentifié, l’application peut accéder aux ressources de l’abonné Azure AD.

Pour s’authentifier, le principal de service utilise l’*ID d’application* de l’application Azure AD et l’un des éléments suivants :
* Secret de l’application
* Certificat