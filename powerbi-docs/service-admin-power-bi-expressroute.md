---
title: Power BI et ExpressRoute
description: Power BI et ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 62289c974e25207f3a991e7f17a0ee965c729b8a
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900126"
---
# <a name="power-bi-and-expressroute"></a>Power BI et ExpressRoute

**ExpressRoute** est un service Azure qui vous permet de créer des connexions privées entre des centres de données Azure (où réside Power BI) et votre infrastructure locale, ou de créer des connexions privées entre des centres de données Azure et votre centre de données.

Avec **Power BI** et **ExpressRoute**, vous pouvez créer une connexion réseau privée de votre organisation à Power BI (ou en utilisant un centre de données d’un fournisseur de services Internet), et contourner ainsi Internet pour mieux sécuriser vos données et connexions Power BI sensibles.

Pour plus d’informations, consultez [Vue d’ensemble d’ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI est conforme à ExpressRoute, à quelques exceptions près, où Power BI obtient ou envoie des données sur l’Internet public. Pour obtenir la liste des URL qui utilisent Power BI, consultez [URL de Power BI](power-bi-whitelist-urls.md).

![Diagramme d’ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)