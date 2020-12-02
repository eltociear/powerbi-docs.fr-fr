---
title: Restreindre l’accès aux données avec la sécurité au niveau des lignes (SNL) pour Power BI Desktop
description: Configuration de DirectQuery et de la sécurité au niveau des lignes pour les jeux de données importés dans Power BI Desktop.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 0d5501ba8929318081a5db7e34e80722f2ffbf70
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412848"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Restreindre l’accès aux données avec la sécurité au niveau des lignes (SNL) pour Power BI Desktop

Vous pouvez utiliser la sécurité au niveau des lignes avec Power BI Desktop pour restreindre l’accès aux données pour certains utilisateurs. Les filtres limitent les données au niveau des lignes. Vous pouvez définir des filtres au sein de rôles.

Vous pouvez maintenant configurer la sécurité au niveau des lignes pour les modèles de données importés dans Power BI avec Power BI Desktop. Vous pouvez également configurer la sécurité au niveau des lignes sur les jeux de données qui utilisent [DirectQuery](../connect-data/desktop-use-directquery.md), tels que SQL Server. Auparavant, vous pouviez uniquement implémenter la sécurité au niveau des lignes dans les modèles Analysis Services locaux en dehors de Power BI. Pour les connexions actives Analysis Services, la sécurité au niveau des lignes doit être configurée sur le modèle local. L’option de sécurité ne s’affiche pas pour les jeux de données d’une connexion active.

> [!IMPORTANT]
> Si vous avez défini des rôles et des règles au sein du service Power BI, vous devez recréer ces rôles dans Power BI Desktop et publier le rapport sur le service. Découvrez-en plus sur les options de la [sécurité au niveau des lignes dans le service Power BI](../admin/service-admin-rls.md).

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Sécurité au niveau des lignes (RLS) avec Power BI](../admin/service-admin-rls.md)
- [Aide sur la sécurité au niveau des lignes (SNL) dans Power BI Desktop](../guidance/rls-guidance.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
