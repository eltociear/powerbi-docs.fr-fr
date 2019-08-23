---
title: Explorer des rapports dans les applications mobiles Power BI
description: Découvrez comment afficher des rapports et interagir avec eux dans les applications mobiles Power BI sur votre téléphone ou tablette. Vous créez des rapports dans le service Power BI ou Power BI Desktop, puis interagissez avec ces rapports dans les applications mobiles.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/09/2019
ms.author: mshenhav
ms.openlocfilehash: 3105736c6576428af2d00b6f502c94f94c409977
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995236"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorer des rapports dans les applications mobiles Power BI
S’applique à :

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Téléphone Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablette Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Appareils Windows 10](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Téléphones Android |Tablettes Android |Appareils Windows 10 |

Un rapport Power BI est une vue interactive de vos données, dont la découverte et l’analyse sont traduites par des insights. L’affichage de rapports dans les applications mobiles Power BI est la troisième étape du processus.

1. [Créez des rapports dans Power BI Desktop](../../desktop-report-view.md). Vous pouvez même [optimiser un rapport pour les téléphones](mobile-apps-view-phone-report.md) dans Power BI Desktop. 
2. Publiez ces rapports dans le service Power BI [ (https://powerbi.com)](https://powerbi.com) ou [Power BI Report Server](../../report-server/get-started.md)).  
3. Ensuite, exploitez ces rapports dans les applications mobiles Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Ouvrir un rapport Power BI dans l’application mobile
Les rapports Power BI sont stockés dans des emplacements différents dans l’application mobile, en fonction de leur provenance. Ils peuvent être situés dans Applications, Partagés avec moi, Espaces de travail (y compris Mon espace de travail) ou sur un serveur de rapports. Parfois, ils sont répertoriés dans un tableau de bord associé par lequel vous accédez à un rapport.

Dans les listes et les menus, vous trouverez une icône en regard du nom d’un rapport, qui vous aidera à comprendre que cet élément est un rapport. 

![rapports dans mon espace de travail](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png) 

Il existe deux icônes pour les rapports dans les applications Power BI Mobile :

* ![icône de rapport](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) Indique un rapport qui est présenté en mode paysage dans l’application, et dont l’apparence est identique dans le navigateur.

* ![icône de rapport sur téléphone](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) Indique un rapport qui a au moins une page de rapport optimisée pour le téléphone, et qui est présenté en mode portrait. 

> [!NOTE]
> Quand vous tiendrez votre téléphone en mode paysage, vous obtiendrez toujours la disposition paysage, même si la page de rapport a une disposition de téléphone. 

Pour obtenir un rapport à partir d’un tableau de bord, appuyez sur les points de suspension (...) dans le coin supérieur droit d’une vignette > **Ouvrir un rapport**.
  
  ![Ouvrir le rapport](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Les vignettes ne peuvent pas toutes s’ouvrir dans un rapport. Par exemple, les vignettes créées en posant une question dans la zone Questions et réponses n’ouvrent pas de rapports quand vous appuyez dessus. 
  
## <a name="interacting-with-reports"></a>Interaction avec les rapports
Une fois que vous avez ouvert un rapport dans l’application, vous pouvez commencer à l’utiliser. Vous pouvez effectuer de nombreuses opérations avec votre rapport et ses données. Dans le pied de page du rapport, vous trouverez les actions que vous pouvez effectuer dans le rapport. En appuyant brièvement ou longuement sur les données du rapport, vous pouvez segmenter les données.

### <a name="using-tap-and-long-tap"></a>Utilisation de l’appui et de l’appui long
Un appui équivaut à un clic de souris. Par conséquent, si vous souhaitez effectuer la sélection croisée du rapport en fonction d’un point de données, appuyez sur ce point de données.
Si vous appuyez sur une valeur de segment, elle est sélectionnée et le reste du rapport est découpé en fonction de cette valeur. Si vous appuyez sur un lien, un bouton ou un signet, celui-ci est activé en fonction de l’action définie par l’auteur.

Vous avez probablement remarqué que si vous appuyez sur un visuel, une bordure apparaît. En haut à droite de la bordure figurent des points de suspension (...). Quand vous appuyez dessus, vous affichez un menu contenant les actions que vous pouvez effectuer sur ce visuel.

![menu et visuel de rapport](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Info-bulle et actions d’exploration

Quand vous appuyez longuement sur un point de données, une info-bulle s’affiche et présente les valeurs que ce point de données représente. 

![info-bulle de rapport](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Si l’auteur du rapport a configuré l’info-bulle de la page de rapport, l’info-bulle par défaut est remplacée par celle de la page de rapport.

![info-bulle de page de rapport](./media/mobile-reports-in-the-mobile-apps/report-page-tooltip.png)

> [!NOTE]
> Les info-bulles de rapport sont prises en charge pour les appareils dont la taille est supérieure à 640 pixels et la fenêtre d’affichage supérieure à 320. Si votre appareil est plus petit, l’application utilise les info-bulles par défaut.

Les auteurs de rapports peuvent définir des hiérarchies dans les données et des relations entre les pages du rapport. La hiérarchie permet de monter ou descendre, et d’extraire une autre page de rapport à partir d’un visuel et d’une valeur. Ainsi, quand vous appuyez longuement sur une valeur, en plus de l’info-bulle, les options d’exploration pertinentes s’affichent dans le pied de page. 

![actions d’exploration de rapport](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)

Avec *l’extraction*, quand vous appuyez sur une partie spécifique d’un visuel, Power BI vous redirige sur une autre page du rapport, filtrée sur la valeur que vous avez choisie. L’auteur d’un rapport peut définir une ou plusieurs options d’extraction, chacune vous redirigeant sur une page différente. Vous pouvez choisir celle que vous voulez extraire. Le bouton de retour vous redirige vers la page de rapport précédente.

Découvrez comment [ajouter l’extraction dans Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > Dans l’application Power BI Mobile, l’exploration des visuels de matrice et de table est activée uniquement par le biais d’une valeur de cellule, et non par en-tête de ligne et de colonne.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Utilisation des actions dans le pied de page du rapport
Le pied de page du rapport comporte des actions que vous pouvez effectuer sur la page de rapport active ou sur le rapport entier. Le pied de page offre un accès rapide aux actions les plus utiles, et toutes les actions sont accessibles à partir des points de suspension (...).

![pied de page du rapport](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Les actions que vous pouvez effectuer à partir du pied de page sont les suivantes :
1) Réinitialiser le filtre de rapport et rétablir l’état d’origine des sélections croisées
2) Ouvrir le volet de conversation pour voir ou ajouter des commentaires sur ce rapport
3) Ouvrir le volet de filtre pour voir et modifier le filtre actuellement appliqué au rapport
4) Lister toutes les pages de ce rapport. Un appui sur le nom de la page permet de charger et de présenter cette page.
Vous pouvez passer d’une page de rapport à une autre, en effectuant un balayage du bord de l’écran vers le centre.
5) Voir toutes les actions du rapport

#### <a name="all-report-actions"></a>Toutes les actions du rapport
Lorsque vous appuyez sur l’option « ... » dans le pied de page du rapport, vous affichez toutes les actions que vous pouvez effectuer dans un rapport. 

![rapport - toutes les actions](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

Certaines actions peuvent être désactivées, car elles dépendent de certaines fonctionnalités du rapport.
Par exemple :
1) **Filtrer par emplacement actuel** est activée si les données de votre rapport ont été classées par l’auteur avec des données géographiques. [Découvrez comment identifier les données géographiques de votre rapport](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).
2) **Analyser pour filtrer le rapport par code-barres** est activée uniquement si le jeu de données dans votre rapport a été balisé comme code-barres. [Guide pratique pour baliser les codes-barres dans Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes). 
3) L’option **Inviter** est activée uniquement si vous avez l’autorisation de partager ce rapport avec d’autres utilisateurs. Vous ne disposez de cette autorisation que si vous êtes le propriétaire du rapport ou si celui-ci vous a accordé l’autorisation de repartage.
4) L’option **Annoter et partager** peut être désactivée si une [stratégie de protection Intune](https://docs.microsoft.com/intune/app-protection-policies) de votre organisation interdit le partage à partir d’une application Power BI Mobile. 

## <a name="next-steps"></a>Étapes suivantes
* [Visualiser les rapports Power BI optimisés pour les téléphones et interagir avec eux](mobile-apps-view-phone-report.md)
* [Créer une version de rapport optimisée pour les téléphones](../../desktop-create-phone-report.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

