---
title: Présentation de la sécurité au niveau des lignes avec Power BI Desktop
description: Configuration de DirectQuery et de la sécurité au niveau des lignes pour les jeux de données importés dans Power BI Desktop.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/03/2018
ms.author: maghan
LocalizationGroup: Create reports
ms.openlocfilehash: 022668737f6bcce987b2923ba7a4416f4a08460a
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34287069"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Sécurité au niveau des lignes avec Power BI Desktop
La sécurité au niveau des lignes avec Power BI Desktop restreint l’accès aux données pour certains utilisateurs. Les filtres limitent les données au niveau des lignes. Vous pouvez définir des filtres au sein de rôles.

Vous pouvez maintenant configurer la sécurité au niveau des lignes pour les modèles de données importés dans Power BI avec Power BI Desktop. Vous pouvez également configurer la sécurité au niveau des lignes sur les jeux de données qui utilisent DirectQuery, tels que SQL Server. Auparavant, vous pouviez uniquement implémenter la sécurité au niveau des lignes dans les modèles Analysis Services locaux en dehors de Power BI. Pour les connexions actives Analysis Services, la sécurité au niveau des lignes doit être configurée sur le modèle local. L’option de sécurité ne s’affiche pas pour les jeux de données d’une connexion active.

> [!IMPORTANT]
> Si vous avez défini des rôles et des règles au sein du service Power BI, vous devez recréer ces rôles dans Power BI Desktop et publier le rapport sur le service.
> 
> 

En savoir plus sur les options de la [sécurité au niveau des lignes dans le service Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Étapes suivantes
[Sécurité au niveau des lignes avec Power BI Desktop](service-admin-rls.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

