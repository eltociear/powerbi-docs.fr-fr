---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621609"
---
Le principal de service est une méthode d’authentification qui peut être utilisée pour permettre l’accès d’une application Azure AD à des API ou un contenu de service Power BI.

Lorsque vous créez une application Azure Active Directory (Azure AD), un [objet principal de service](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) est créé. L’objet principal de service, également connu sous le nom de *principal de service*, permet à Azure AD d’authentifier votre application. Une fois authentifié, l’application peut accéder aux ressources de l’abonné Azure AD.

Pour s’authentifier, le principal de service utilise l’*ID d’application* de l’application Azure AD et l’un des éléments suivants :
* Secret de l’application
* Certificat