---
title: Où est situé mon client Power BI ?
description: Découvrez où se trouve votre client Power BI et comment l’emplacement est sélectionné. C’est un élément qu’il est important de comprendre, car il peut avoir un impact sur vos interactions avec le service.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: b396b55304e468143fe28fb5ed46ed290bfb3812
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909522"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Où est situé mon client Power BI ?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Découvrez où se trouve votre client Power BI et comment l’emplacement est sélectionné. Il est important de comprendre l'emplacement, car cela peut avoir un impact sur les interactions que vous avez avec le service.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Déterminer où est situé votre client Power BI

Pour rechercher la région où se trouve votre client, procédez comme suit.

1. Dans le service Power BI, menu supérieur, sélectionnez l’aide (**?**), puis **À propos de Power BI**.

1. Recherchez la valeur suivante à côté de **Vos données sont stockées dans**. C’est la région où se trouve votre client.

    ![Région de données](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Méthode de sélection de la région de données

La région de données est basée sur le pays que vous sélectionnez lors de la création du client. Les informations étant partagées, cela s’applique aussi bien à l’inscription à Office 365 qu’à Power BI. S’il s’agit d’un nouveau client, sélectionnez le pays approprié dans la liste lorsque vous vous inscrivez.

![Sélection du pays](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI sélectionne la région de données la plus proche de cette sélection, qui détermine où les données sont stockées pour votre locataire.

> [!IMPORTANT]
> Vous ne pouvez pas modifier cette sélection après avoir créé le client.

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

