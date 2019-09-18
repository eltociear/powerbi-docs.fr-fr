---
title: Explorer des rapports dans les applications mobiles Power BI
description: Découvrez comment afficher des rapports et interagir avec eux dans les applications mobiles Power BI sur votre téléphone ou tablette. Vous créez des rapports dans le service Power BI ou Power BI Desktop, puis interagissez avec ces rapports dans les applications mobiles.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/09/2019
ms.author: mshenhav
ms.openlocfilehash: 166b7d88e6ab55481ec56b0cf4f91628cd141bef
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "69985733"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Explorer des rapports dans les applications mobiles Power BI
S’applique à :

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Téléphone Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tablette Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Appareils Windows 10](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:---: |:---: |:---: |:---: |:---: |
| iPhone |iPad |Téléphones Android |Tablettes Android |Appareils Windows 10 |

Un rapport Power BI est une vue interactive de vos données, avec des visuels qui représentent différents résultats et insights de ces données. L’affichage de rapports dans les applications mobiles Power BI est la troisième étape d’un processus en trois étapes :

1. [Créez des rapports dans Power BI Desktop](../../desktop-report-view.md). Vous pouvez même [optimiser un rapport pour les téléphones](mobile-apps-view-phone-report.md) dans Power BI Desktop.
2. Publiez ces rapports dans le service Power BI [ (https://powerbi.com)](https://powerbi.com) ou [Power BI Report Server](../../report-server/get-started.md)).  
3. Exploitez les rapports dans les applications mobiles Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Ouvrir un rapport Power BI dans l’application mobile
Les rapports Power BI sont stockés dans des emplacements différents dans l’application mobile, en fonction de leur provenance. Ils peuvent être situés dans Applications, Partagés avec moi, Espaces de travail (y compris Mon espace de travail) ou sur un serveur de rapports. Parfois, ils sont répertoriés dans un tableau de bord associé par lequel vous accédez à un rapport.

Dans les listes et les menus, vous trouverez une icône en regard du nom d’un rapport, qui vous aidera à comprendre que l’élément est un rapport :

![Rapports dans Mon espace de travail](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png)

Il existe deux icônes pour les rapports dans les applications mobiles Power BI :

* ![Icône Rapport](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) indique un rapport qui sera présenté en mode paysage dans l’application. Il a une apparence identique à celle dans un navigateur.

* ![Icône de rapport sur téléphone](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) indique un rapport qui a au moins une page optimisée pour le téléphone, et sera présenté en mode portrait.

> [!NOTE]
> Quand vous tenez votre téléphone en mode paysage, vous obtenez toujours la disposition paysage, même si la page de rapport est en mode téléphone.

Pour accéder à un rapport à partir d’un tableau de bord, appuyez sur les points de suspension (...) dans le coin supérieur droit d’une vignette, puis sur **Ouvrir un rapport** :
  
  ![Ouvrir le rapport](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  Les vignettes ne peuvent pas toutes être ouvertes en tant que rapports. Par exemple, les vignettes créées quand vous posez une question dans la zone Questions et réponses n’ouvrent pas de rapports quand vous appuyez dessus.
  
## <a name="interact-with-reports"></a>Interagir avec les rapports
Une fois que vous avez ouvert un rapport dans l’application, vous pouvez commencer à l’utiliser. Vous pouvez faire beaucoup de choses avec votre rapport et les données qu’il contient. Dans le pied de page du rapport, vous trouverez les actions que vous pouvez effectuer sur le rapport. En appuyant brièvement ou longuement sur les données du rapport, vous pouvez aussi segmenter les données.

### <a name="using-tap-and-long-tap"></a>Utilisation de l’appui et de l’appui long
Un appui équivaut à un clic de souris. Par conséquent, si vous souhaitez effectuer la sélection croisée du rapport en fonction d’un point de données, appuyez sur ce point de données.
Si vous appuyez sur une valeur de segment, elle est sélectionnée et le reste du rapport est découpé en fonction de cette valeur.
Si vous appuyez sur un lien, un bouton ou un signet, l’action définie par l’auteur du rapport se produit.

Vous avez probablement remarqué que, si vous appuyez sur un visuel, une bordure apparaît. Dans le coin supérieur droit de la bordure, vous verrez des points de suspension (...). Si vous appuyez sur les points de suspension, vous verrez un menu d’actions que vous pouvez effectuer sur ce visuel :

![Visuel et menu](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Info-bulle et actions d’exploration

Quand vous appuyez longuement sur un point de données, une info-bulle s’affiche et présente les valeurs que ce point de données représente :

![Info-bulle](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Si l’auteur du rapport a configuré une info-bulle de la page de rapport, l’info-bulle par défaut est remplacée par celle de la page de rapport :

![Info-bulle de page de rapport](./media/mobile-reports-in-the-mobile-apps/report-page-tooltip.png)

> [!NOTE]
> Les info-bulles de rapport sont prises en charge pour les appareils dont la taille est d’au moins 640 pixels et la fenêtre d’affichage d’au moins 320. Si votre appareil est plus petit, l’application affiche les info-bulles par défaut.

Les auteurs de rapports peuvent définir des hiérarchies dans les données et des relations entre les pages du rapport. Les hiérarchies permettent de monter ou descendre, et d’extraire une autre page de rapport à partir d’un visuel et d’une valeur. Ainsi, quand vous appuyez longuement sur une valeur, en plus de l’info-bulle, les options d’exploration pertinentes s’affichent dans le pied de page :

![Actions d’exploration](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)


Quand vous appuyez sur une partie spécifique d’un visuel, puis sur l’option d’*extraction*, Power BI vous redirige vers une autre page du rapport, filtrée sur la valeur que vous avez choisie. L’auteur d’un rapport peut définir une ou plusieurs options d’extraction, chacune vous redirigeant vers une page différente. Dans ce cas, vous pouvez choisir l’option que vous voulez extraire. Le bouton Précédent vous ramène à la page précédente.


Pour plus d’informations, découvrez comment [ajouter l’extraction à Power BI Desktop](../../desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > Dans les applications mobiles Power BI, les actions d’exploration des visuels de matrice et de table sont activées par le biais des valeurs de cellules uniquement, et non par en-têtes de ligne ou de colonne.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Utilisation des actions dans le pied de page du rapport
À partir du pied de page du rapport, vous pouvez effectuer plusieurs actions dans la page de rapport active ou le rapport entier. Le pied de page offre un accès rapide aux actions les plus couramment utilisées. Vous pouvez accéder à d’autres actions en appuyant sur le bouton avec des points de suspension (...) :

![Pied de page du rapport](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Vous pouvez effectuer les actions suivantes à partir du pied de page :
- Réinitialiser le filtre de rapport et rétablir l’état d’origine des sélections croisées.
- Ouvrir le volet de conversation pour voir ou ajouter des commentaires dans le rapport.
- Ouvrir le volet de filtre pour voir ou modifier le filtre actuellement appliqué au rapport.
- Lister toutes les pages du rapport. Un appui sur le nom d’une page permet de charger et de présenter cette page.
Vous pouvez passer d’une page de rapport à une autre, en effectuant un balayage du bord de l’écran vers le centre.
- Voir toutes les actions du rapport

#### <a name="all-report-actions"></a>Toutes les actions du rapport
Lorsque vous appuyez sur le bouton avec des points de suspension (...) dans le pied de page du rapport, vous voyez toutes les actions que vous pouvez effectuer sur un rapport :


![Toutes les actions du rapport](./media/mobile-reports-in-the-mobile-apps/report-all-actions.png)

Certaines des actions peuvent être désactivées, car elles dépendent de fonctionnalités du rapport spécifiques.
Par exemple :

**Filtrer par emplacement actuel** est activée si l’auteur du rapport l’a classé avec des données géographiques. Pour plus d’informations, découvrez comment [identifier des données géographiques dans un rapport](https://docs.microsoft.com/power-bi/desktop-mobile-geofiltering).

**Analyser pour filtrer le rapport par code-barres** est activée uniquement si le jeu de données dans votre rapport est balisé comme **code-barres**. Pour plus d’informations, découvrez comment [baliser des codes-barres dans Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-mobile-barcodes).

**Inviter** est activée uniquement si vous avez l’autorisation de partager le rapport avec d’autres utilisateurs. Vous disposez de cette autorisation uniquement si vous êtes le propriétaire du rapport ou si celui-ci vous a accordé l’autorisation de repartage.

L’option **Annoter et partager** peut être désactivée si une [stratégie de protection Intune](https://docs.microsoft.com/intune/app-protection-policies) de votre organisation interdit le partage à partir d’une application mobile Power BI.

## <a name="next-steps"></a>Étapes suivantes
* [Visualiser les rapports Power BI optimisés pour les téléphones et interagir avec eux](mobile-apps-view-phone-report.md)
* [Créer une version de rapport optimisée pour les téléphones](../../desktop-create-phone-report.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

