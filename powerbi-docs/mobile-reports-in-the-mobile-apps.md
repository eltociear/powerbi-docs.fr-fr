---
title: Explorer des rapports dans les applications mobiles Power BI
description: "Découvrez comment afficher des rapports et interagir avec eux dans les applications mobiles Power BI sur votre téléphone ou tablette. Vous créez des rapports dans le service Power BI ou Power BI Desktop, puis interagissez avec ces rapports dans les applications mobiles. "
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
ms.openlocfilehash: 3515a57f88db1c8a7b12706680c0aade8b2cdbfa
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorer des rapports dans les applications mobiles Power BI
S’applique à :

| ![iPhone](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Téléphone Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablette Android](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Appareils Windows 10](media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Téléphones Android |Tablettes Android |Appareils Windows 10 |

Un rapport Power BI est une vue interactive de vos données, dont la découverte et l’analyse sont traduites par des insights. L’affichage de rapports dans les applications mobiles Power BI est la troisième étape du processus.

1. [Créez des rapports dans Power BI Desktop](desktop-report-view.md). Vous pouvez même [optimiser un rapport pour les téléphones](mobile-apps-view-phone-report.md) dans Power BI Desktop. 
2. Publiez ces rapports dans le service Power BI [(https://powerbi.com)](https://powerbi.com) ou [Power BI Report Server](report-server/get-started.md).  
3. Ensuite, exploitez ces rapports dans les applications mobiles Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Ouvrir un rapport Power BI dans l’application mobile
Les rapports Power BI sont stockés dans des emplacements différents dans l’application mobile, en fonction de leur provenance. Ils peuvent être situés dans Applications, Partagés avec moi, Espaces de travail (y compris Mon espace de travail) ou sur un serveur de rapports. Parfois, ils sont répertoriés dans un tableau de bord associé par lequel vous accédez à un rapport.

* Dans un tableau de bord, appuyez sur les points de suspension (...) dans le coin supérieur droit d’une vignette > **Ouvrir un rapport**.
  
  ![Ouvrir le rapport](media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Les vignettes ne peuvent pas toutes s’ouvrir dans un rapport. Par exemple, les vignettes créées en posant une question dans la zone Questions et réponses n’ouvrent pas de rapports quand vous appuyez dessus. 
  
  Sur un téléphone, le rapport s’ouvre en mode paysage, sauf s’il est [optimisé pour un affichage sur téléphone](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones).
  
  ![Rapport sur téléphone en mode Paysage](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>Afficher les rapports optimisés pour les téléphones
Les auteurs de rapports Power BI peuvent créer une disposition de rapport spécialement optimisée pour les téléphones. Dans la liste des rapports, un rapport optimisé possède une icône spéciale ![Icône de rapport sur téléphone](media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png):

![Ouvrir le rapport sur téléphone](media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

Lorsque vous affichez un rapport sur un téléphone, il s’ouvre en mode portrait.

![Rapport en mode Portrait](media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

Un rapport peut avoir une combinaison de pages optimisées et non optimisées pour les téléphones. Dans ce cas, lorsque vous parcourez le rapport, l’affichage bascule du mode portrait au mode paysage pour chaque page.

En savoir plus sur les [rapports optimisés pour l’affichage sur téléphone](mobile-apps-view-phone-report.md).

## <a name="use-slicers-to-filter-a-report-page"></a>Utiliser des segments pour filtrer une page de rapport
Quand vous concevez un rapport dans le service Power BI [(https://powerbi.com)](https://powerbi.com), n’oubliez pas que sur un téléphone, vous ne pouvez pas voir le volet Filtres, mais vous pouvez [voir des segments sur une page de rapport](power-bi-visualization-slicers.md). Ajoutez des segments à un rapport afin que vous et vos collègues puissiez les utiliser pour filtrer la page sur un téléphone.

* Lorsque vous sélectionnez une valeur dans un segment de la page de rapport, celle-ci filtre les autres visuels sur la page.
  
  ![Segment Rapport](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  Dans cette illustration, le segment filtre l’histogramme pour afficher uniquement les valeurs de juillet.

## <a name="cross-filter-and-highlight-a-power-bi-report-page"></a>Effectuer un filtrage croisé et mettre en surbrillance une page de rapport Power BI
Lorsque vous sélectionnez une valeur dans un visuel, elle ne filtre pas les autres visuels. Elle met en surbrillance les valeurs associées dans les autres visuels.

* Appuyez sur une valeur dans un visuel.
  
  ![Filtrage croisé d’une page](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  Un appui sur la colonne Large (Grand) dans un visuel met en surbrillance les valeurs associées dans les autres visuels. 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>Trier un visuel sur un iPad ou une tablette
* Appuyez sur le graphique, sur les points de suspension (**...**), puis sur le nom de champ.
  
   ![Trier un visuel](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* Pour inverser l’ordre de tri, rappuyez sur les points de suspension (**...**), puis appuyez sur le même nom de champ.

## <a name="drill-down-and-up-in-a-visual-on-an-ipad-or-a-tablet"></a>Monter ou descendre dans la hiérarchie d’un visuel sur un iPad ou une tablette
Si un auteur de rapport a ajouté cette fonctionnalité à un visuel, sur un iPad ou une tablette, vous pouvez descendre dans la hiérarchie d’un visuel pour afficher les valeurs qui composent une partie de celui-ci. [Ajoutez la descente dans la hiérarchie à un visuel](power-bi-visualization-drill-down.md) dans le service Power BI ou dans Power BI Desktop. 

> [!NOTE]
> Actuellement, la descente dans la hiérarchie ne fonctionne pas sur les cartes sur les iPad ou les tablettes.
> 
> 

* Appuyez sur un élément visuel. Si des flèches vers le bas et vers le haut apparaissent dans les coins supérieurs ![Icônes Monter/descendre dans la hiérarchie](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-down.png), vous pouvez descendre dans la hiérarchie. Pour descendre dans la hiérarchie d’une seule valeur, appuyez sur la flèche dans le coin supérieur droit, puis appuyez sur une valeur dans le visuel. Dans ce cas, la bulle FD-04 bleu foncé.
  
  ![Descendre dans la hiérarchie d’un visuel](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-one.png)
* Pour remonter dans la hiérarchie, appuyez sur la flèche vers le haut dans le coin supérieur gauche.
  
  ![Monter dans la hiérarchie](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up.png)

## <a name="go-back-to-my-workspace"></a>Revenir à Mon espace de travail
* Appuyez sur la flèche en regard du nom du rapport, puis sur **Mon espace de travail**.
  
  ![Retour en haut](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-back.png)

## <a name="next-steps"></a>Étapes suivantes
* [Visualiser les rapports Power BI optimisés pour les téléphones et interagir avec eux](mobile-apps-view-phone-report.md)
* [Créer une version de rapport optimisée pour les téléphones](desktop-create-phone-report.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

