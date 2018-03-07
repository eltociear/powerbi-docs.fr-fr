---
title: Optimiser des visuels Power BI de toutes tailles
description: "Découvrez comment optimiser les visuels dans Power BI Desktop et le service Power BI pour les applications Power BI sur téléphone."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/13/2017
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 4c80048213b20365102bcb9c6842c342d8b9052b
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2018
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Optimiser des visuels Power BI de toutes tailles
Vous pouvez configurer les visuels de vos tableaux de bord ou rapports de façon à ce qu’ils soient *réactifs*, changeant de manière dynamique pour afficher une quantité maximale de données et d’informations, quelle que soit la taille de l’écran.

Quand un visuel change de taille, Power BI hiérarchise la vue de données, par exemple, en supprimant le remplissage et en déplaçant automatiquement la légende vers le haut du visuel de façon à ce que celui-ci reste informatif, même quand sa taille diminue. La réactivité est particulièrement utile dans les visuels de l’application mobile Power BI sur les téléphones.

![Redimensionnement de visuel réactif](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Vous pouvez activer la réactivité des visuels avec les axes X et Y ainsi que les segments.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Activer la réactivité dans Power BI Desktop
1. Dans Power BI Desktop, sous l’onglet **Affichage**, vérifiez que vous êtes en **Mode poste de travail**.
   
    ![Icône Mode poste de travail](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Sélectionnez un visuel, puis, dans le volet **Visualisations**, sélectionnez la section **Format**.
3. Développez **Général** > définissez **Réactif** sur **Activé**.
   
    ![Réactif activé](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Désormais, lorsque vous [créez un rapport optimisé pour le téléphone](desktop-create-phone-report.md), puis ajoutez cet visuel, celui-ci se redimensionne harmonieusement.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Activer la réactivité dans le service Power BI
Vous activez la réactivité pour un visuel dans un rapport via le service Power BI. Vous devez être en mesure de modifier le rapport.

1. Dans un rapport dans le service Power BI ([https://powerbi.com](https://powerbi.com)), sélectionnez **Modifier le rapport**.
2. Sélectionnez un visuel, puis, dans le volet **Visualisations**, sélectionnez la section **Format**.
3. Développez **Général** > définissez **Réactif** sur **Activé**.
   
    ![Réactif activé](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Désormais, lorsque vous [créez une vue téléphone d’un tableau de bord](service-create-dashboard-mobile-phone-view.md), puis ajoutez ce visuel, celui-ci se redimensionne harmonieusement.

## <a name="next-steps"></a>Étapes suivantes
* [Créer des rapports optimisés pour les applications Power BI pour téléphone](desktop-create-phone-report.md)
* [Créer une vue téléphone d’un tableau de bord dans Power BI](service-create-dashboard-mobile-phone-view.md)
* [Afficher les rapports Power BI optimisés pour votre téléphone](mobile-apps-view-phone-report.md)
* D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

