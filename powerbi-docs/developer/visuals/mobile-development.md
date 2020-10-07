---
title: Développement mobile
description: Guide pratique pour créer des visuels Power BI adaptés aux mobiles
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 99df7a301a1025d50c82c5cc7f5966325a6a6a6f
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747525"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Guide pratique pour créer des visuels Power BI adaptés aux mobiles
La consommation sur mobile a un rôle majeur dans Power BI. Une de ses forces est de rester connecté à vos données à tout moment, où que vous soyez.

En tant que développeur créant des visuels Power BI, vous devez tenir compte des contraintes spécifiques de chaque appareil mobile pour atteindre autant d’utilisateurs que possible et pour offrir une expérience mobile optimale.

Utilisez l’[application Power BI pour Windows, iOS et Android](../../consumer/mobile/mobile-apps-for-mobile-devices.md) pour permettre aux utilisateurs de votre entreprise d’avoir au bout des doigts une vue complète de leurs données en déplacement.

## <a name="requirements"></a>Configuration requise

Les exigences suivantes sont essentielles pour le développement de visuels adaptés aux mobiles :

- Rendu

  Vos visuels Power BI doivent s’afficher sur tous les appareils mobiles pris en charge, notamment les navigateurs et applications pris en charge, sans erreurs dans les rapports et les tableaux de bord, ou lors de l’exécution en mode **Focus**. 

- Interactive

  Les fonctionnalités interactives doivent être fournies de la même façon que pour les postes de travail. Tous les événements gérés sur les navigateurs des postes de travail doivent être pris en charge ou avoir des gestionnaires d’événements comparables pour les appareils mobiles.
  
  Par exemple, la navigation de base et la sélection des points de données doivent avoir les mêmes fonctionnalités que dans les navigateurs des postes de travail. Si un visuel prend en charge la sélection multiple avec **Ctrl**, le développeur doit envisager d’ajouter un gestionnaire d’événements similaire pour les appareils mobiles.

  Le tableau suivant fournit une liste des événements correspondants sur les appareils mobiles.

  | Nom de l’événement de la souris | Nom de l’événement tactile |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | Utiliser une bibliothèque externe |
  | `contextmenu` | Utiliser une bibliothèque externe |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (ou une bibliothèque externe) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > Tous les appareils mobiles ou tactiles ne prennent pas en charge les événements de souris (ou ceux préfixés par *mouse*). Dans ce cas, gérez les événements de la *souris* et les événements *tactiles* en même temps.

## <a name="optional"></a>Facultatif
Les éléments suivants sont considérés comme facultatifs et ils sont utilisés pour améliorer l’expérience de l’utilisateur final.

- Rendu

  Pour prendre en charge des tailles de visuels plus petites, essayez d’ajouter des options de mise en forme que l’utilisateur peut modifier pour ajuster la taille de chaque élément. Par exemple, ajoutez des options de mise en forme aux étiquettes, utilisables dans les rapports et les tableaux de bord. Ceci permet aux utilisateurs de personnaliser un visuel spécifiquement pour leur appareil mobile.
  
  Les mêmes paramètres peuvent également être appliqués aux visuels dans les navigateurs des postes de travail et, si nécessaire, être remplacés pour adapter le visuel à des écrans plus petits.

  > [!NOTE]
  > Pour optimiser un visuel en mode **Focus**, les orientations des tailles d’écran portrait et paysage doivent être prises en compte ; consultez [Afficher du contenu en mode Focus](../../consumer/end-user-focus.md).

- Interactive

  Envisagez d’ajouter des gestionnaires d’événements spécifiques aux mobiles, comme le glissement et le défilement.

- Basculement

  Un visuel doit afficher une erreur décrivant le problème s’il ne peut pas être rendu sur l’appareil mobile.

## <a name="supported-browsers-and-devices"></a>Navigateurs et appareils pris en charge
Le visuel Power BI doit s’afficher sur tous les appareils prenant en charge les applications Power BI. Pour plus d’informations, consultez [Navigateurs pris en charge pour Power BI](../../fundamentals/power-bi-browsers.md) et [Applications mobiles Power BI](../../consumer/mobile/mobile-apps-for-mobile-devices.md).

Lors des tests sur les modèles les plus récents des appareils Windows, iOS et Android, le développeur doit prendre en compte la plupart de ces aspects qualitatifs.

## <a name="next-steps"></a>Étapes suivantes
Pour commencer, consultez [Tutoriel : Développement d’un visuel Power BI](./custom-visual-develop-tutorial.md)