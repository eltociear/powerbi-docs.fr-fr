---
title: Où est situé mon client Power BI ?
description: Découvrez où se trouve votre client Power BI et comment l’emplacement est sélectionné. C’est un élément qu’il est important de comprendre, car il peut avoir un impact sur vos interactions avec le service.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: c0c6de63292d3087aaa78dd97b73f868ef9d804e
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293648"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Où est situé mon client Power BI ?
<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Découvrez où se trouve votre client Power BI et comment l’emplacement est sélectionné. C’est un élément qu’il est important de comprendre, car il peut avoir un impact sur vos interactions avec le service.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Déterminer où est situé votre client Power BI
Pour trouver la région dans laquelle se situe votre client, vous pouvez procédez comme suit :

1. Sélectionnez le signe **?** dans le service Power BI.
2. Sélectionnez **À propos de Power BI**.
3. Recherchez la valeur suivante à côté de **Vos données sont stockées dans**. Il s’agit de la région où vous vous trouvez.

![](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Méthode de sélection de la région de données
La région de données est basée sur le pays sélectionné lors de la création du client. Les informations étant partagées, cela s’applique aussi bien à l’inscription à Office 365 qu’à Power BI. S’il s’agit d’un nouveau client, lorsque vous vous inscrivez, une liste déroulante de pays s’affiche.

![](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Cette sélection détermine l’emplacement où vos données sont stockées. Power BI utilise la région de données la plus proche de cette sélection.

> [!WARNING]
> Vous ne pouvez pas modifier cette dernière.
> 
> 

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

