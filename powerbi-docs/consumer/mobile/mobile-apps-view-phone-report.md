---
title: Afficher les rapports Power BI optimisés pour votre téléphone
description: En savoir plus sur l’interaction avec les pages de rapport optimisées pour l’affichage dans les applications Power BI pour téléphone.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: mshenhav
ms.openlocfilehash: 79ca47f83bb39ab9d6df141b5a26dcb54e00c72c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100986"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Afficher les rapports Power BI optimisés pour votre téléphone

S’applique à :

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Téléphone Android](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone |Téléphones Android |

Lorsque vous affichez un rapport Power BI sur votre téléphone, Power BI vérifie si le rapport a été optimisé pour les téléphones. S’il possède, Power BI s’ouvre automatiquement le rapport optimisé en mode portrait.

![Rapports en mode portrait](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Si le rapport optimisé pour les téléphones n’existe pas, le rapport s’ouvre toujours, mais en mode paysage non optimisé. Même dans un rapport optimisé pour les téléphones, si vous tournez votre téléphone sur le côté, le rapport s’ouvre dans l’affichage non optimisé avec sa disposition d’origine. Si seules certaines pages sont optimisées, un message s’affiche en mode portrait pour vous indiquer que le rapport est disponible en mode paysage.

![Page de rapport non optimisée](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Toutes les autres fonctionnalités des rapports Power BI continuent de fonctionner dans les rapports optimisés pour les téléphones. Découvrez ce que vous pouvez faire dans :

* [Les rapports sur iPhone](mobile-reports-in-the-mobile-apps.md). 
* [Les rapports sur Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrer la page de rapport sur un téléphone
Si des filtres ont été définis dans un rapport optimisé pour les téléphones, lorsque vous affichez le rapport sur un téléphone, vous pouvez utiliser ces filtres. Le rapport s’ouvre sur votre téléphone, des valeurs en cours de filtrage dans le rapport sur le web. Un message s’affiche indiquant qu’il existe des filtres actifs sur la page. Vous pouvez modifier les filtres sur votre téléphone.

1. Appuyez sur l’icône de filtre ![Icône de filtre de téléphone](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) en bas de la page. 
2. Pour voir les résultats qui vous intéressent, utilisez le filtrage de base ou avancé.
   
    ![Filtre avancé de rapport sur téléphone Power BI](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Sélection croisée de visuels
Sélection croisée de visuels en mode portrait vue fonctionne comme il le fait dans le service Power BI et sur les téléphones en mode paysage : Lorsque vous sélectionnez des données dans un visuel, cela met en évidence les données associées dans les autres visuels sur cette page.

En savoir plus sur le [filtrage et la mise en évidence dans Power BI](../../power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Sélectionner des visuels
Quand vous sélectionnez un visuel dans des rapports sur téléphone, ces derniers le mettent en évidence et se concentrent dessus en neutralisant les mouvements sur le canevas.

Quand le visuel est sélectionné, vous pouvez effectuer différentes opérations, comme défiler au sein du visuel. Pour désélectionner un visuel, touchez n’importe où en dehors de la zone du visuel.

## <a name="open-visuals-in-focus-mode"></a>Ouvrir les visuels en mode Focus
Rapports sur téléphone offrent également un mode focus : Vous obtenez une vue plus large d’un seul visual et faciliter l’exploration.

* Dans un rapport pour téléphone, cliquez sur les points de suspension ( **...** ) situés dans le coin supérieur droit d’un visuel, puis sur **Développer en mode focus**.
  
    ![Développer en mode Focus](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Que faire en mode focus s’appliquent au canevas du rapport et vice versa. Par exemple, si vous mettez en surbrillance une valeur dans un élément visuel, puis revenez à l’ensemble du rapport, le rapport est filtré à la valeur que vous avez sélectionnée dans le visuel.

Voici les actions qui ne sont possibles qu’en mode focus en raison des contraintes liées à la taille des écrans :

* **Descendre dans la hiérarchie** des informations affichées dans un visuel. Pour en savoir plus sur les [opérations de montée et descente dans la hiérarchie](mobile-apps-view-phone-report.md#drill-down-in-a-visual) dans un rapport pour téléphone, consultez la suite de cet article.
* **Trier** les valeurs du visuel.
* **Rétablir** : Effacer les étapes d’exploration effectuées sur un visuel et revenir à la définition définie lors de la création du rapport.
  
    Pour effacer toutes les explorations à partir d’un visuel, cliquez sur les points de suspension ( **...** ), puis sur **Rétablir**.
  
    ![Rétablir](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Rétablir est disponible au niveau du rapport, en désactivant les explorations à partir de tous les éléments visuels, ou au niveau du visuel, effacement explorations à partir de l’élément visuel sélectionné.   

## <a name="drill-down-in-a-visual"></a>Descendre dans la hiérarchie d’un visuel
Si des niveaux de la hiérarchie sont définis dans un visuel, vous pouvez descendre dans la hiérarchie des informations détaillées affichées, puis revenir en arrière. Vous pouvez [ajouter une descente dans la hiérarchie d’un visuel](../end-user-drill.md) soit dans le service Power BI, soit dans Power BI Desktop.

Il existe plusieurs types de zoom :

### <a name="drill-down-on-a-value"></a>Zoom avant sur une valeur
1. Durée pendant laquelle appuyer (cliquez et maintenez) sur un point de données dans un élément visuel.
2. Info-bulle s’affiche, et si la hiérarchie est définie, le pied de page d’info-bulle affichera exploration vers le bas et flèche vers le haut.
3. Appuyez sur la flèche vers le bas pour descendre

    ![Appuyez sur Descendre dans la hiérarchie](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Appuyez sur la flèche vers le haut pour l’extraction vers le haut.

### <a name="drill-to-next-level"></a>Accéder au prochain niveau
1. Dans un rapport pour téléphone, cliquez sur les points de suspension ( **...** ) situés dans le coin supérieur droit, puis sur **Développer en mode focus**.
   
    ![Développer en mode focus](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Dans cet exemple, les barres indiquent des états.
2. Appuyez sur l’icône Explorer ![Icône Explorer](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) dans le coin inférieur gauche.
   
    ![Mode Exploration](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Appuyez sur **Afficher le niveau suivant** ou **Développer au prochain niveau**.
   
    ![Développer au prochain niveau](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Maintenant, les barres affichent les valeurs des villes.
   
    ![Niveaux développés](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Si vous appuyez sur la flèche dans le coin supérieur gauche, vous revenez au rapport pour téléphone contenant les valeurs toujours développées au niveau inférieur.
   
    ![Toujours développé au niveau inférieur](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Pour remonter au niveau d’origine, appuyez de nouveau sur les points de suspension ( **...** ), puis sur **Rétablir**.
   
    ![Rétablir](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Explorer à partir d’une valeur
Extraction connecte à des valeurs dans une page du rapport, avec d’autres pages de rapport. Lorsque vous permet d’accéder à partir d’un point de données vers une autre page de rapport, les valeurs de points de données sont utilisés pour filtrer le percé via la page, ou elle sera dans le contexte des données sélectionnées.
Les auteurs de rapports peuvent [définir d’extraction](https://docs.microsoft.com/power-bi/desktop-drillthrough) lorsqu’ils créent le rapport.

1. Durée pendant laquelle appuyer (cliquez et maintenez) sur un point de données dans un élément visuel.
2. Info-bulle s’affiche, et si l’extraction est définie, le pied de page d’info-bulle affichera flèche d’extraction.
3. Appuyez sur la flèche pour l’extraction

    ![Appuyez sur l’extraction](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Choisir la page rapport d’extraction

    ![Choisissez la page de rapport](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Utilisez le bouton précédent, à l’en-tête de l’application pour revenir à la page que vous avez démarré depuis.


## <a name="next-steps"></a>Étapes suivantes
* [Créer des rapports optimisés pour les applications Power BI pour téléphone](../../desktop-create-phone-report.md)
* [Créer une vue téléphone d’un tableau de bord dans Power BI](../../service-create-dashboard-mobile-phone-view.md)
* [Créer des visuels réactifs optimisés pour toute taille](../../visuals/desktop-create-responsive-visuals.md)
* D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

