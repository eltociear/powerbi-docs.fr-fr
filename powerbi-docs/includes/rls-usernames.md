---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193817"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Utilisation des fonctions DAX username() et userprincipalname()
Vous pouvez utiliser les fonctions DAX *username()* et *userprincipalname()* dans votre jeu de données. Dans Power BI Desktop, celles-ci peuvent être utilisées dans des expressions. Une fois votre modèle publié, il est utilisé dans le service Power BI.

Dans Power BI Desktop, *username()* retourne un utilisateur au format *DOMAINE\Utilisateur* tandis que *userprincipalname()* le retourne au format <em>user@contoso.com</em>.

Dans le service Power BI, les fonctions *username()* et *userprincipalname()* retournent toutes les deux le nom d’utilisateur principal (UPN) de l’utilisateur. Celui-ci est similaire à une adresse e-mail.

