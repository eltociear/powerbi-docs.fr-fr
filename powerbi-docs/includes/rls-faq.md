---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409361"
---
## <a name="faq"></a>FORUM AUX QUESTIONS
**Question :** Que se passe-t-il si j’avais déjà créé des rôles et des règles pour un jeu de données dans le service Power BI ? Continuent-ils de fonctionner si je ne fais rien ?  
**Réponse :** Non, car les visuels ne seront pas rendus correctement. Vous devez recréer les rôles et les règles dans Power BI Desktop, puis les publier sur le service Power BI.

**Question :** Puis-je créer ces rôles pour des sources de données Analysis Services ?  
**Réponse :** Oui, à condition que vous ayez importé les données dans Power BI Desktop. Si vous utilisez une connexion active, vous n’êtes pas en mesure de configurer la sécurité au niveau des lignes (RLS) au sein du service Power BI. Celle-ci se définit localement dans le modèle Analysis Services.

**Question :** Puis-je utiliser SNL pour limiter les colonnes ou les mesures accessibles par mes utilisateurs ?  
**Réponse :** Non, si un utilisateur a accès à une ligne particulière de données, il peut voir toutes les colonnes de données pour cette ligne.

**Question :** Avec SNL, puis-je masquer les données détaillées tout en donnant accès aux données résumées dans les visuels ?  
**Réponse :** Non, vous sécurisez des lignes de données individuelles, mais les utilisateurs peuvent toujours voir les détails ou les données résumées.

**Question :** Ma source de données a déjà des rôles de sécurité définis (par exemple des rôles SQL Server ou des rôles SAP BW). Quelle est la relation entre ces éléments et SNL ?  
**Réponse :** La réponse varie selon que vous importez des données ou que vous utilisez DirectQuery. Si vous importez des données dans votre jeu de données Power BI, les rôles de sécurité de votre source de données ne sont pas utilisés. Dans ce cas, vous devez définir la sécurité au niveau des lignes pour appliquer des règles de sécurité aux utilisateurs qui se connectent dans Power BI. Si vous utilisez DirectQuery, les rôles de sécurité de votre source de données sont utilisés. Quand un utilisateur ouvre un rapport, Power BI envoie une requête à la source de données sous-jacente, qui applique des règles de sécurité aux données en fonction des informations d’identification de l’utilisateur.
