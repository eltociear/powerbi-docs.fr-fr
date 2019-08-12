---
title: Passerelle de données locale
description: Cet article présente une vue d’ensemble de la passerelle de données locale pour Power BI. Vous pouvez utiliser cette passerelle pour travailler avec les sources de données DirectQuery. Vous pouvez également utiliser cette passerelle pour actualiser les jeux de données cloud avec les données locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 883d5c83019df293628d096f5834c9b5c6d425b6
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730296"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Qu’est-ce qu’une passerelle de données locale ?

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

La passerelle de données locale agit comme un pont, en fournissant un transfert de données rapide et sécurisé entre des données locales (qui ne sont pas dans le cloud) et plusieurs services cloud Microsoft. Ces services cloud sont Power BI, PowerApps, Microsoft Flow, Azure Analysis Services et Azure Logic Apps. En utilisant une passerelle, les organisations peuvent conserver les bases de données et d’autres sources de données sur leurs réseaux locaux, tout en utilisant de façon sécurisée ces données locales dans des services cloud.

## <a name="how-the-gateway-works"></a>Fonctionnement de la passerelle

![Vue d’ensemble de la passerelle](media/service-gateway-onprem/on-premises-data-gateway.png)

Pour plus d’informations sur le fonctionnement de la passerelle , voir [Architecture de la passerelle de données locale](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Types de passerelles

Il existe deux types de passerelles différents, chacun pour un scénario différent :

* **Passerelle de données locale** : elle permet à plusieurs utilisateurs de se connecter à différentes sources de données locales. Vous pouvez utiliser une passerelle de données locale avec tous les services pris en charge, avec l’installation d’une seule passerelle. Cette passerelle est particulièrement adaptée à des scénarios complexes, dans lesquels plusieurs utilisateurs accèdent à plusieurs sources de données.

* **Passerelle de données locale (mode personnel)**  : elle permet à un utilisateur de se connecter aux sources et ne peut pas être partagée avec d’autres utilisateurs. Une passerelle de données locale (mode personnel) peut être utilisée seulement avec Power BI. Cette passerelle est adaptée aux scénarios où vous êtes la seule personne qui crée des rapports et où vous n’avez pas besoin de partager les sources de données avec d’autres utilisateurs.

## <a name="use-a-gateway"></a>Utiliser une passerelle

L’utilisation d’une passerelle passe par quatre grandes étapes.

1. [Télécharger et installer la passerelle](/data-integration/gateway/service-gateway-install) sur un ordinateur local.
2. [Configurer](/data-integration/gateway/service-gateway-app) la passerelle en fonction de votre pare-feu et d’autres exigences réseau.
3. [Ajouter des administrateurs de passerelle](/data-integration/gateway/service-gateway-manage) qui peuvent également gérer et administrer d’autres exigences réseau.
4. [Résoudre les problèmes](service-gateway-onprem-tshoot.md) de la passerelle en cas d’erreur.

## <a name="next-steps"></a>Étapes suivantes

* [Installer la passerelle de données locale](/data-integration/gateway/service-gateway-install)


D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
