---
title: Mise en cache des requêtes dans Power BI Premium
description: Mise en cache des requêtes dans Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: c981a3e2a05129a470c8d26675226bfb42c1bb68
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769536"
---
# <a name="query-caching-in-power-bi-premium"></a>Mise en cache des requêtes dans Power BI Premium

Les organisations avec Power BI Premium peuvent tirer parti de la *mise en cache des requêtes* pour accélérer l’exécution de rapports associés à un jeu de données. La mise en cache des requêtes indique à la capacité Premium d’utiliser son service de mise en cache local pour tenir à jour les résultats des requêtes, ce qui évite de recourir à la source de données sous-jacente pour calculer ces résultats.

> [!IMPORTANT]
> La mise en cache des requêtes est disponible uniquement sur Power BI Premium. Elle n’est pas applicable aux jeux de données LiveConnect tirant parti d’Azure Analysis Services ou de SQL Server Analysis Services.

Les résultats des requêtes mis en cache sont spécifiques au contexte de l’utilisateur et du jeu de données, et respectent toujours les règles de sécurité. Pour l’instant, le service effectue uniquement la mise en cache des requêtes pour la page initiale à laquelle vous accédez. En d’autres termes, les requêtes ne sont pas mises en cache quand vous interagissez avec le rapport. Le cache reflète les signets personnels et les filtres persistants. Les [vignettes de tableau de bord](service-dashboard-tiles.md) qui reposent sur les mêmes requêtes tirent également des avantages une fois que la requête est mise en cache. Les performances sont en particulier optimisées quand un jeu de données est fréquemment sollicité et n’a pas besoin d’être souvent actualisé. La mise en cache des requêtes peut également diminuer la charge sur votre capacité Premium en réduisant le nombre total de requêtes.

Vous contrôlez le comportement de la mise en cache des requêtes dans la page **Paramètres** pour le jeu de données dans le service Power BI. Il possède deux paramètres possibles :

- **Off** (Désactivée) : N’utilisez pas la mise en cache des requêtes pour ce jeu de données.

- **On** (Activée) : Utilisez la mise en cache des requêtes pour ce jeu de données.

![Boîte de dialogue Mise en cache des requêtes](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> Quand vous remplacez le paramètre de mise en cache **On** (Activée) par **Off** (Désactivée), tous les résultats des requêtes précédemment enregistrés pour le jeu de données sont supprimés du cache de capacité. Vous pouvez désactiver la mise en cache explicitement ou en rétablissant le paramètre par défaut de la capacité auquel un administrateur a affecté la valeur **Off** (Désactivée). Cette désactivation peut introduire un petit délai la prochaine fois qu’un rapport exécute des requêtes sur ce jeu de données. Le délai est dû à ces requêtes de rapport qui s’exécutent à la demande et ne tirent pas parti des résultats enregistrés. En outre, il est possible que le jeu de données requis doive être chargé en mémoire avant de pouvoir traiter les requêtes.


