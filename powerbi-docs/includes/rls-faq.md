---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560956"
---
## <a name="faq"></a>FORUM AUX QUESTIONS
**Question :** Que se passe-t-il si j’avais déjà créé des rôles et des règles pour un jeu de données dans le service Power BI ? Continuent-ils de fonctionner si je ne fais rien ?  
**Réponse :** Non, car les visuels ne seront pas rendus correctement. Vous devez recréer les rôles et les règles dans Power BI Desktop, puis les publier sur le service Power BI.

**Question :** Puis-je créer ces rôles pour des sources de données Analysis Services ?  
**Réponse :** Oui, à condition que vous ayez importé les données dans Power BI Desktop. Si vous utilisez une connexion active, vous n’êtes pas en mesure de configurer la sécurité au niveau des lignes (RLS) au sein du service Power BI. Celle-ci se définit localement dans le modèle Analysis Services.

**Question :** Puis-je utiliser SNL pour limiter les colonnes ou les mesures accessibles par mes utilisateurs ?  
**Réponse :** Non, si un utilisateur a accès à une ligne particulière de données, il peut voir toutes les colonnes de données pour cette ligne.

**Question :** Avec SNL, puis-je masquer les données détaillées tout en donnant accès aux données résumées dans les visuels ?  
**Réponse :** Non, vous sécurisez des lignes de données individuelles, mais les utilisateurs peuvent toujours voir les détails ou les données résumées.

