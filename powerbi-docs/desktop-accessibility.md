---
title: Accessibilité dans les rapports Power BI Desktop
description: Fonctionnalités et suggestions pour la création de rapports Power BI Desktop accessibles
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 799115dc5487a196cbd5d8a2c9dce1603764034a
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223372"
---
# <a name="accessibility-in-power-bi-desktop-reports"></a>Accessibilité dans les rapports Power BI Desktop
Power BI intègre des fonctionnalités qui permettent aux personnes présentant un handicap de lire et d’utiliser les rapports Power BI plus facilement, notamment la possibilité de lire un rapport à l’aide du clavier ou d’un lecteur d’écran et de mettre en évidence divers objets de la page à l’aide de la touche de tabulation, et l’utilisation judicieuse des marqueurs dans les visualisations.

![Utiliser différents marqueurs pour les graphiques en courbes et en aires en vue d’améliorer l’accessibilité](media/desktop-accessibility/accessibility_01.png)

> [!NOTE]
> Ces fonctionnalités d’accessibilité sont disponibles dans la version de juin 2017 de **Power BI Desktop** et dans les versions ultérieures. Des fonctionnalités d’accessibilité supplémentaires sont également prévues pour les versions futures.
> 
> 

## <a name="consuming-a-power-bi-desktop-report-with-a-keyboard-or-screen-reader"></a>Lire un rapport Power BI Desktop à l’aide d’un clavier ou d’un lecteur d’écran
Depuis la version de septembre 2017 de **Power BI Desktop**, vous pouvez appuyer sur la touche **?** pour afficher une fenêtre décrivant les raccourcis clavier d’accessibilité disponibles dans **Power BI Desktop**.

![Appuyer sur la touche ? dans Power BI Desktop pour afficher les raccourcis clavier d’accessibilité](media/desktop-accessibility/accessibility_03.png)

Grâce aux améliorations de l’accessibilité, vous pouvez lire un rapport Power BI en vous aidant d’un clavier ou d’un lecteur d’écran avec les techniques suivantes :

Lorsque vous voyez un rapport, vous devez généralement avoir le mode d’analyse désactivé.

Pour faire passer la mise en évidence d’un onglet de page de rapport à un autre ou d’un objet à un autre d’une page de rapport donnée, utilisez la combinaison de touche **Ctrl+F6**.

* Lorsque la mise en évidence est sur les *onglets de page du rapport*, utilisez les touches *Tab* ou *flèche* pour faire passer la mise en évidence d’une page du rapport à la suivante. Le titre de la page de rapport est lu par le lecteur d’écran, qui indique également si cette page est actuellement sélectionnée. Pour charger la page de rapport actuellement mise en évidence, utilisez la touche *Entrée* ou *Espace*.
* Lorsque la mise en évidence est sur une *page de rapport* chargée, utilisez la touche *Tab* pour la faire passer d’un objet à un autre de la page, notamment les zones de texte, les images, les formes et les graphiques. Le lecteur d’écran lit le type d’objet, le titre de l’objet s’il a un et la description de cet objet si elle est fournie par l’auteur du rapport. 

Quand vous naviguez entre les visuels, si vous voulez interagir davantage, vous pouvez appuyer sur **Alt+Maj+F10** pour déplacer le focus sur l’en-tête du visuel. Celui-ci contient différentes options, notamment le tri, l’exportation de données dans le graphique et le mode Focus. 

![Appuyez sur Alt+Maj+F10 dans Power BI Desktop pour déplacer le focus sur l’en-tête du visuel](media/desktop-accessibility/accessibility_08.png)

Vous pouvez appuyer sur **Alt+Maj+F11** pour présenter une version accessible de la fenêtre *Afficher les données*. Vous pouvez ainsi explorer dans une table HTML les données utilisées dans le visuel, en utilisant les mêmes raccourcis clavier que ceux que vous utilisez normalement avec votre lecteur d’écran. 

![Appuyer sur Alt+Maj+F11 dans Power BI Desktop pour afficher une fenêtre Voir les données accessible pour un visuel](media/desktop-accessibility/accessibility_04.png)

> [!NOTE]
> La fonctionnalité Afficher des données n’est accessible à un lecteur d’écran qu’avec ce raccourci clavier. Si vous ouvrez Afficher les données par le biais de l’option disponible dans l’en-tête du visuel, elle ne sera pas accessible à un lecteur d’écran. Lorsque vous utilisez Afficher les données, activez le mode d’analyse pour tirer parti de tous les raccourcis que fournit votre lecteur d’écran.

À partir de la version de juillet 2018 de **Power BI Desktop**, les segments sont également dotés d’une fonctionnalité d’accessibilité intégrée. Lorsque vous sélectionnez un segment, pour régler sa valeur, actionnez CTRL + flèche droite (contrôle plus la touche flèche droite) pour vous déplacer dans les différents contrôles du segment. Par exemple, lorsque vous appuyez d’abord sur CTRL + flèche droite, le focus est mis sur la gomme, et appuyer sur la barre d’espace revient à cliquer sur le bouton Gomme, ce qui efface toutes les valeurs sur le segment. 

Vous pouvez parcourir les contrôles dans un segment en appuyant sur la touche TAB. En appuyant sur la touche TAB lorsque vous êtes sur la gomme, vous accédez au bouton de liste déroulante ; un autre actionnement de la touche TAB vous amène à la première valeur de segment (s’il existe plusieurs valeurs pour le segment, tels qu’une plage). 

![Appuyez sur CTRL + (touche flèche vers la droite) dans Power BI Desktop pour ajuster l’élément ou des valeurs dans un segment, appuyez sur la barre d’espace pour sélectionner l’élément et régler sa valeur](media/desktop-accessibility/accessibility_07.png)

Ces ajouts à l’accessibilité ont été créés pour permettre aux utilisateurs de tirer pleinement parti des rapports Power BI à l’aide d’un lecteur d’écran et d’une navigation au clavier.

## <a name="tips-for-creating-accessible-reports"></a>Conseils pour la création de rapports accessibles
Les conseils suivants peuvent vous aider à créer des rapports **Power BI Desktop** plus accessibles.

### <a name="general-tips-for-accessible-reports"></a>Conseils d’ordre général sur les rapports accessibles

* Pour les visuels **Ligne**, **Zone** et **Zone de liste modifiable** (ainsi que pour les visuels **Nuage de points** et **Bulle**), activez les marqueurs et utilisez une *forme de marqueur* différente pour chaque ligne.
  
  * Pour activer les *marqueurs*, sélectionnez la section **Format** du volet **Visualisations**, développez la section **Formes**, puis faites défiler vers le bas jusqu’à la bascule **Marqueurs** et réglez celle-ci sur *Activé*.
  * Ensuite, sélectionnez le nom de chaque ligne (ou aire, si vous utilisez un graphique en **aires**) dans la zone de liste déroulante de la section **Formes**. Sous la liste déroulante, vous pouvez alors ajuster de nombreux aspects du marqueur utilisé pour la ligne sélectionnée, notamment sa forme, sa couleur et sa taille.
  
  ![Utiliser différents marqueurs pour les graphiques en courbes et en aires en vue d’améliorer l’accessibilité](media/desktop-accessibility/accessibility_01.png)
  
  * L’utilisation d’une *forme de marqueur* différente pour chaque ligne permet aux lecteurs du rapport de plus facilement différencier les lignes (ou aires) les unes des autres.
* En complément de la puce précédente, ne vous fiez pas aux couleurs pour transmettre des informations. En plus de l’utilisation de formes sur les graphiques en courbes ou à nuages de points, ne vous appuyez pas sur la mise en forme conditionnelle pour fournir des insights dans des tables et des matrices. 
* Choisissez un ordre de tri intentionnel pour chaque visuel figurant sur votre rapport. Quand les utilisateurs de lecteur d’écran parcourent les données affichées dans le graphique, le lecteur d’écran utilise le même ordre de tri que le visuel.
* Sélectionnez un *thème* à contraste élevé et adapté pour les personnes daltoniennes dans la galerie de thèmes, puis importez-le à l’aide de la fonctionnalité en préversion [**Thème**](desktop-report-themes.md).
* Pour chaque objet d’un rapport, fournissez un *texte de remplacement*. Cela vous permet de garantir que les lecteurs de votre rapport comprennent ce que vous essayez de communiquer avec un visuel, même s’ils ne peuvent pas voir le visuel, l’image, la forme ou la zone de texte. Pour fournir un *Texte de remplacement* pour un objet d’un rapport **Power BI Desktop**, sélectionnez l’objet (par exemple un visuel, une forme, etc.) puis, dans le volet **Visualisations**, sélectionnez la section **Format**, développez **Général**, puis faites défiler vers le bas et renseignez la zone de texte **Texte de remplacement**.
  
  ![Il est possible d’ajouter un texte de remplacement à n’importe quel objet d’un rapport en sélectionnant Visualisations > Format > Général > zone de texte Texte de remplacement.](media/desktop-accessibility/accessibility_02.png)
* Veillez à ce qu’il y ait suffisamment de contraste entre le texte et les couleurs d’arrière-plan de vos rapports. Il existe plusieurs outils, comme [Colour Contrast Analyser](https://developer.paciellogroup.com/resources/contrastanalyser/), que vous pouvez utiliser pour vérifier les couleurs de votre rapport. 
* Utilisez des tailles et polices de texte facilement lisibles. Les textes de petite taille ou les polices difficiles à lire ont un impact négatif sur l’accessibilité.
* Incluez un titre, des étiquettes d’axe et des étiquettes de données dans tous les visuels.
* Utilisez des titres significatifs pour toutes les pages du rapport.
* Évitez, si possible, les formes et les images décoratives dans votre rapport, car elles sont incluses dans l’ordre de tabulation du rapport. Si vous avez besoin d’inclure des objets décoratifs dans votre rapport, mettez à jour le texte de légende de l’objet pour informer les utilisateurs du lecteur d’écran qu’il est décoratif.

### <a name="arranging-items-in-field-buckets"></a>Organisation des éléments dans des compartiments Champ
À partir de la version d’octobre 2018 de **Power BI Desktop**, le puits **Champs** est accessible avec un clavier et interagit avec les lecteurs d’écran. 

Pour améliorer le processus de création de rapports avec les lecteurs d’écran, un menu contextuel est disponible pour permettre le déplacement des champs dans le puits vers le haut ou vers le bas dans la liste **Champs**, ou le déplacement du champ vers d’autres puits, comme **Légende** ou **Valeur**, ou autres.

![Le menu contextuel dans les Champs vous permet de déplacer les champs vers le haut, vers le bas ou vers une autre zone](media/desktop-accessibility/accessibility_09.png)

## <a name="high-contrast-support-for-reports"></a>Prise en charge du contraste élevé dans les rapports

Lorsque vous utilisez les modes de contraste élevé dans Windows, ces paramètres et la palette que vous sélectionnez sont également appliqués aux rapports dans **Power BI Desktop**. 

![Paramètres Windows de contraste élevé](media/desktop-accessibility/accessibility_05.png)

**Power BI Desktop** détecte automatiquement le thème à contraste élevé utilisé dans Windows et applique ces paramètres à vos rapports. Ces couleurs à contraste élevé suivent le rapport quand celui-ci est publié sur le service Power BI, ou ailleurs.

![Paramètres Windows de contraste élevé](media/desktop-accessibility/accessibility_05b.png)

Le service Power BI essaie aussi de détecter les paramètres de contraste élevé sélectionnés pour Windows, mais l’efficacité et la précision de cette détection dépendent du navigateur utilisé pour le service Power BI. Si vous souhaitez définir le thème manuellement dans le service Power BI, vous pouvez sélectionner **Affichage > Couleurs à contraste élevé** et choisir le thème que vous souhaitez appliquer au rapport.

![Définition du contraste élevé dans le service Power BI](media/desktop-accessibility/accessibility_06.png)

Quand vous êtes dans **Power BI Desktop**, notez que certaines zones telles que les champs **Visualisations** et **Champs** ne reflètent pas la sélection des jeux de couleurs Windows à contraste élevé.


## <a name="considerations-and-limitations"></a>Considérations et limitations
Il existe quelques limitations et problèmes connus concernant les fonctionnalités d’accessibilité, décrits dans la liste suivante :

* Pour une expérience optimale quand vous utilisez des lecteurs d’écran avec **Power BI Desktop**, ouvrez le lecteur d’écran de votre choix avant d’ouvrir des fichiers dans Power BI Desktop.
* Si vous utilisez le Narrateur, il existe certaines limitations concernant la navigation dans la fonctionnalité Afficher les données sous la forme d’une table HTML.

## <a name="keyboard-shortcuts"></a>Raccourcis clavier
### <a name="frequently-used-shortcuts"></a>Raccourcis fréquemment utilisés
| Pour           | Appuyer sur                |
| :------------------- | :------------------- |
| Déplacer le focus entre les sections  | Ctrl + F6 |
| Déplacer le focus vers l’avant de la section | Tab         |
| Déplacer le focus vers l’arrière de la section | Maj + Tab |

### <a name="on-visual"></a>Sur le visuel
| Pour           | Appuyer sur                |
| :------------------- | :------------------- |
| Déplacer le focus sur le menu du visuel | Alt + Maj + F10 |
| Afficher les données | Alt + Maj + F11  |

### <a name="pane-navigation"></a>Navigation dans les volets
| Pour           | Appuyer sur                |
| :------------------- | :------------------- |
| Ouvrir un menu contextuel | <ul><li>Clavier Windows : Touche de contexte Windows + F10.  La touche de contexte Windows se trouve entre la touche Alt de gauche et la touche Flèche Gauche</li><li>Autre clavier : Maj + F10</li></ul> |

### <a name="slicer"></a>Segment
| Pour           | Appuyer sur                |
| :------------------- | :------------------- |
| Interagir avec un segment | Ctrl + Flèche droite |

### <a name="selection-pane"></a>Volet Sélection
| Pour           | Appuyer sur                |
| :------------------- | :------------------- |
| Activer le volet Sélection | F6 |
| Déplacer un objet vers le haut dans la superposition | Ctrl + Maj + F |
| Déplacer un objet vers le bas dans la superposition | Ctrl + Maj + B |
| Masquer/afficher un objet | Ctrl + Maj + S |

### <a name="dax-editor"></a>Éditeur DAX
| Pour           | Appuyer sur                |
| :------------------- | :------------------- |
| Déplacer une ligne vers le haut/le bas | ALT + Flèche Haut / Flèche Bas |
| Copier une ligne en haut / bas | Maj +Alt + Flèche Haut / Flèche Bas |
| Insérer la ligne ci-dessous | Ctrl + Entrée |
| Insérer la ligne ci-dessus | Ctrl + Maj + Entrée |
| Sauter au crochet correspondant | Ctrl + Maj + \ |
| Mettre en retrait positif/négatif une ligne | Ctrl + ] / [ |
| Insérer le curseur | Alt + Clic |
| Sélectionner la ligne actuelle | Ctrl + I |
| Sélectionner toutes les occurrences de la sélection actuelle | Ctrl + Maj + L |
| Sélectionner toutes les occurrences du mot actuel | Ctrl + F2 |




## <a name="next-steps"></a>Étapes suivantes
* [Utiliser des thèmes de rapport dans Power BI Desktop (préversion)](desktop-report-themes.md)

