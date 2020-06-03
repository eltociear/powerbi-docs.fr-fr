---
title: Présentation du principal de service
description: Présentation du principal de service
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 8482278d9054228dedafb6bd1b37368f5a4b5dce
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315780"
---
Le principal de service est une méthode d’authentification qui peut être utilisée pour permettre l’accès d’une application Azure AD à des API ou un contenu de service Power BI.

Lorsque vous créez une application Azure Active Directory (Azure AD), un [objet principal de service](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) est créé. L’objet principal de service, également connu sous le nom de *principal de service*, permet à Azure AD d’authentifier votre application. Une fois authentifié, l’application peut accéder aux ressources de l’abonné Azure AD.

Pour s’authentifier, le principal de service utilise l’*ID d’application* de l’application Azure AD et l’un des éléments suivants :

* Secret de l’application
* Certificat