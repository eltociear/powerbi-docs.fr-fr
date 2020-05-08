---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "61193817"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Utilisation des fonctions DAX username() et userprincipalname()
Vous pouvez utiliser les fonctions DAX *username()* et *userprincipalname()* dans votre jeu de données. Dans Power BI Desktop, celles-ci peuvent être utilisées dans des expressions. Une fois votre modèle publié, il est utilisé dans le service Power BI.

Dans Power BI Desktop, *username()* retourne un utilisateur au format *DOMAINE\Utilisateur* tandis que *userprincipalname()* le retourne au format <em>user@contoso.com</em>.

Dans le service Power BI, les fonctions *username()* et *userprincipalname()* retournent toutes les deux le nom d’utilisateur principal (UPN) de l’utilisateur. Celui-ci est similaire à une adresse e-mail.

