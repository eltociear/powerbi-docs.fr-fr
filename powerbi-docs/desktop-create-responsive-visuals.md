---
title: Optimiser des visuels Power BI de toutes tailles
description: Apprenez à optimiser les visuels dans des rapports existants de Power BI Desktop et du service Power BI pour les applications Power BI sur téléphone.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/13/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: d80e96fbca893fee3ff03ef9021988f5a22bb2e7
ms.sourcegitcommit: df94efc51f261113fa90ebdf3fe68dd149cc4936
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Optimiser des visuels Power BI de toutes tailles
Par défaut, lorsque vous créez un nouveau rapport, les visuels sont *réactifs*, changeant de manière dynamique pour afficher une quantité maximale de données et d’insights, quelle que soit la taille de l’écran. Pour les rapports plus anciens, vous pouvez définir leurs visuels pour un redimensionnement dynamique également.

Quand un visuel change de taille, Power BI hiérarchise la vue de données, par exemple, en supprimant le remplissage et en déplaçant automatiquement la légende vers le haut du visuel de façon à ce que celui-ci reste informatif, même quand sa taille diminue. La réactivité est particulièrement utile dans les visuels de l’application mobile Power BI sur les téléphones.

![Redimensionnement de visuel réactif](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Tout visuel avec des axes X et Y, ainsi que des segments, peut être redimensionné de façon réactive.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Activer la réactivité dans Power BI Desktop
1. Dans un rapport plus ancien de Power BI Desktop, sous l’onglet **Affichage**, vérifiez que vous êtes en **Mode poste de travail**.
   
    ![Icône Mode poste de travail](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Sélectionnez un visuel, puis, dans le volet **Visualisations**, sélectionnez la section **Format**.
3. Développez **Général** > définissez **Réactif** sur **Activé**.
   
    ![Réactif activé](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Désormais, lorsque vous [créez un rapport optimisé pour le téléphone](desktop-create-phone-report.md), puis ajoutez cet visuel, celui-ci se redimensionne harmonieusement.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Activer la réactivité dans le service Power BI
Vous pouvez activer la réactivité pour un visuel dans un rapport plus ancien dans le service Power BI. Vous devez être en mesure de modifier le rapport.

1. Dans un rapport du service Power BI ([https://powerbi.com](https://powerbi.com)), sélectionnez **Modifier le rapport**.
2. Sélectionnez un visuel, puis, dans le volet **Visualisations**, sélectionnez la section **Format**.
3. Développez **Général** > définissez **Réactif** sur **Activé**.
   
    ![Réactif activé](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Désormais, lorsque vous [créez une affichage sur téléphone de ce rapport](desktop-create-phone-report.md), puis ajoutez ce visuel, celui-ci se redimensionne harmonieusement.

## <a name="next-steps"></a>Étapes suivantes
* [Créer des rapports optimisés pour les applications Power BI pour téléphone](desktop-create-phone-report.md)
* [Afficher les rapports Power BI optimisés pour votre téléphone](mobile-apps-view-phone-report.md)
* D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

