---
title: Power BI et ExpressRoute
description: Power BI et ExpressRoute
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 12/03/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0c4618150094a4eabb0dc9745e9ac93e4f342ff1
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54291093"
---
# <a name="power-bi-and-expressroute"></a>Power BI et ExpressRoute

**ExpressRoute** est un service Azure qui vous permet de créer des connexions privées entre des centres de données Azure (où réside Power BI) et votre infrastructure locale, ou de créer des connexions privées entre des centres de données Azure et votre centre de données.

Avec **Power BI** et **ExpressRoute**, vous pouvez créer une connexion réseau privée de votre organisation à Power BI (ou en utilisant un centre de données d’un fournisseur de services Internet), et contourner ainsi Internet pour mieux sécuriser vos données et connexions Power BI sensibles.

Pour plus d’informations, consultez [Vue d’ensemble d’ExpressRoute](/azure/expressroute/expressroute-introduction). Power BI est conforme à ExpressRoute, à quelques exceptions près, où Power BI obtient ou envoie des données sur l’Internet public. Pour obtenir la liste des URL qui utilisent Power BI, consultez [URL de Power BI](power-bi-whitelist-urls.md).

![Diagramme d’ExpressRoute](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)