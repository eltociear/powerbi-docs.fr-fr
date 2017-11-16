---
title: "Afficher les rapports Power BI optimisés pour votre téléphone"
description: "En savoir plus sur l’interaction avec les pages de rapport optimisées pour l’affichage dans les applications Power BI pour téléphone."
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
ms.openlocfilehash: 54a1b81cc4281db7a622668ba205c1c57d5e396d
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Afficher les rapports Power BI optimisés pour votre téléphone
Quand vous créez un rapport Power BI dans Power BI Desktop, vous pouvez également créer une version [optimisée de ce rapport pour un affichage dans l’application Power BI pour téléphone](desktop-create-phone-report.md).

Ensuite, quand vous ouvrez un rapport Power BI sur un téléphone, Power BI détecte si le rapport a été optimisé pour les téléphones, puis, si c’est le cas, l’ouvre automatiquement en mode portrait.

![Rapports en mode portrait](media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Si le rapport optimisé pour les téléphones n’existe pas, le rapport s’ouvre toujours, mais en mode paysage non optimisé. Même dans un rapport optimisé pour les téléphones, si vous tournez votre téléphone sur le côté, le rapport s’ouvre dans l’affichage non optimisé avec sa disposition d’origine. Si seules certaines pages sont optimisées, un message s’affiche en mode portrait pour vous indiquer que le rapport est disponible en mode paysage.

![Page de rapport non optimisée](media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Toutes les autres fonctionnalités des rapports Power BI continuent de fonctionner dans les rapports optimisés pour les téléphones. Découvrez ce que vous pouvez faire dans :

* [Les rapports sur iPhone](mobile-reports-in-the-mobile-apps.md). 
* [Les rapports sur Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-an-iphone"></a>Filtrer la page de rapport sur un iPhone
Si des filtres ont été définis pour un rapport optimisé pour les téléphones, lorsque vous affichez le rapport sur un iPhone, vous pouvez utiliser ces filtres. 

1. Appuyez sur l’icône de filtre ![Icône de filtre de téléphone](media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) en bas de la page. 
2. Pour voir les résultats qui vous intéressent, utilisez le filtrage de base ou avancé.
   
    ![Filtre avancé de rapport sur téléphone Power BI](media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Sélection croisée de visuels
La sélection croisée de visuels dans les rapports sur téléphone fonctionne comme dans le service Power BI et dans les rapports sur téléphone en mode paysage : quand vous sélectionnez les données d’un visuel, les données connexes sont mises en évidence dans les autres visuels de cette page.

En savoir plus sur le [filtrage et la mise en évidence dans Power BI](power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Sélectionner des visuels
Quand vous sélectionnez un visuel dans des rapports sur téléphone, ces derniers le mettent en évidence et se concentrent dessus en neutralisant les mouvements sur le canevas.

Quand le visuel est sélectionné, vous pouvez effectuer différentes opérations, comme défiler au sein du visuel. Pour désélectionner un visuel, touchez n’importe où en dehors de la zone du visuel.

## <a name="open-visuals-in-focus-mode"></a>Ouvrir les visuels en mode Focus
Vous pouvez également afficher les rapports sur téléphone en mode Focus, qui permet d’obtenir une vision élargie d’un visuel et d’explorer celui-ci ainsi que le rapport.

* Dans un rapport pour téléphone, cliquez sur les points de suspension (**...**) situés dans le coin supérieur droit d’un visuel, puis sur **Développer en mode focus**.
  
    ![Développer en mode focus](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Ce que vous effectuez en mode focus se reflète sur le canevas du rapport et inversement, ce qui vous offre une expérience transparente de l’exploration. Par exemple, si vous mettez en évidence la valeur d’un visuel, puis que vous revenez à l’ensemble du rapport, celui-ci est entièrement filtré sur la valeur que vous avez mise en évidence dans le visuel.

Voici les actions qui ne sont possibles qu’en mode focus en raison des contraintes liées à la taille des écrans :

* **Descendre dans la hiérarchie** des informations affichées dans un visuel. Pour en savoir plus sur les [opérations de montée et descente dans la hiérarchie](mobile-apps-view-phone-report.md#drill-down-in-a-visual) dans un rapport pour téléphone, consultez la suite de cet article.
* **Trier** les valeurs du visuel.
* **Rétablir** : effacer les étapes d’exploration effectuées sur un visuel et revenir à la définition définie lors de la création du rapport.
  
    Pour effacer toutes les explorations à partir d’un visuel, cliquez sur les points de suspension (**...**), puis sur **Rétablir**.
  
    ![Rétablir](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    L’action Rétablir est disponible au niveau du rapport en effaçant toute l’exploration dans l’ensemble des visuels, ou au niveau du visuel en effaçant toute l’exploration du visuel spécifique sélectionné.   

## <a name="drill-down-in-a-visual"></a>Descendre dans la hiérarchie d’un visuel
Si des niveaux de la hiérarchie sont définis dans un visuel, vous pouvez descendre dans la hiérarchie des informations détaillées affichées, puis revenir en arrière. Vous pouvez [ajouter une descente dans la hiérarchie d’un visuel](power-bi-visualization-drill-down.md) soit dans le service Power BI, soit dans Power BI Desktop. La descente dans la hiérarchie fonctionne uniquement avec des rapports Power BI optimisés pour l’affichage sur téléphone. 

1. Dans un rapport pour téléphone, cliquez sur les points de suspension (**...**) situés dans le coin supérieur droit, puis sur **Développer en mode focus**.
   
    ![Développer en mode focus](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Dans cet exemple, les barres indiquent des états.
2. Appuyez sur l’icône Explorer ![Icône Explorer](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) dans l’angle inférieur gauche.
   
    ![Mode Exploration](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Appuyez sur **Afficher le niveau suivant** ou **Développer au prochain niveau**.
   
    ![Développer au prochain niveau](media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Maintenant, les barres affichent les valeurs des villes.
   
    ![Niveaux développés](media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Si vous appuyez sur la flèche dans le coin supérieur gauche, vous revenez au rapport pour téléphone contenant les valeurs toujours développées au niveau inférieur.
   
    ![Toujours développé au niveau inférieur](media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Pour remonter au niveau d’origine, appuyez de nouveau sur les points de suspension (**...**), puis sur **Rétablir**.
   
    ![Rétablir](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="next-steps"></a>Étapes suivantes
* [Créer des rapports optimisés pour les applications Power BI pour téléphone](desktop-create-phone-report.md)
* [Créer une vue téléphone d’un tableau de bord dans Power BI](service-create-dashboard-mobile-phone-view.md)
* [Créer des visuels réactifs optimisés pour toute taille](desktop-create-responsive-visuals.md)
* D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

