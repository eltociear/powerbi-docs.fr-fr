---
title: Modifier l’interaction des éléments visuels dans un rapport
description: Documentation pour savoir comment définir des interactions entre visuels dans un rapport de service Microsoft Power BI et un rapport Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: N_xYsCbyHPw
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/11/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 6f739992ed282ada92b1049df09a8b5d4b3938a9
ms.sourcegitcommit: 654fae0af739bd599e029d692f142faeba0a502f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56426582"
---
# <a name="change-how-visuals-interact-in-a-power-bi-report"></a>Modifier l’interaction des visuels dans un rapport Power BI
Si vous avez des autorisations de modification sur un rapport, vous pouvez utiliser des **interactions entre visuels** pour changer l’impact entre les visualisations d’une page de rapport. 

Par défaut, vous pouvez utiliser les visualisations d’une page de rapport pour filtrer et mettre en évidence les autres visualisations de la page. On parle alors de « filtrage croisé » et de « mise en évidence croisée ».
Par exemple, si vous sélectionnez un état sur une visualisation de carte, l’histogramme est mis en évidence et le graphique en courbes est filtré pour afficher uniquement les données qui s’appliquent à cet état.
Consultez [À propos du filtrage et de la mise en évidence](power-bi-reports-filters-and-highlighting.md). Et si vous avez une visualisation qui prend en charge l’[exploration](consumer/end-user-drill.md), par défaut, l’exploration d’une visualisation n’a aucun impact sur les autres visualisations de la page de rapport. Vous pouvez toutefois remplacer ces deux comportements par défaut et définir des interactions pour chaque visualisation.

Cet article vous explique comment utiliser des **interactions entre visuels** dans le service Power BI, le [mode Edition](service-interact-with-a-report-in-editing-view.md) et Power BI Desktop. Si un rapport a été partagé avec vous, vous ne pouvez pas changer les paramètres d’interaction entre visuels.

> [!NOTE]
> Les termes *filtrage croisé* et *sélection croisée* permettent de distinguer le comportement décrit ici de celui qui résulte de l’utilisation du volet **Filtres** pour filtrer et mettre en évidence des visualisations.  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Sélectionnez une visualisation pour l’activer.  
2. Afficher les options **Interactions entre les visuels**.
    - Dans le service Power BI, sélectionnez le menu déroulant dans la barre de menus du rapport.

       ![Liste déroulante des interactions entre les visuels](media/service-reports-visual-interactions/power-bi-visual-interaction.png)

    - Dans Desktop, sélectionnez **Format > Interactions**.

        ![sélectionner Format, puis Interactions](media/service-reports-visual-interactions/pbi-visual-interaction-desktop.png)

3. Pour activer les commandes d’interaction entre visualisations, sélectionnez **Modifier les interactions**. Power BI ajoute les icônes de filtrage croisé et de sélection croisée à toutes les autres visualisations de la page de rapport.
   
    ![rapport avec l’option Interactions entre les visuels activée](media/service-reports-visual-interactions/power-bi-icons-on.png)
3. Déterminez l’impact de la visualisation sélectionnée sur les autres visualisations.  Répétez éventuellement cette opération pour toutes les autres visualisations de la page de rapport.
   
   * Si le filtrage croisé doit être appliqué à la visualisation, sélectionnez l’icône **filtre** ![icône de filtre](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png).
   * Si la sélection croisée doit être appliquée à la visualisation, sélectionnez l’icône **sélection** ![icône de sélection](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png).
   * Si elle n’a aucun impact, sélectionnez l’icône **aucun impact** ![icône aucun impact](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png).

4. Pour activer les commandes d’exploration, sélectionnez **Filtrages d’exploration sur les autres visuels**.  Maintenant, quand vous explorez une visualisation, les autres visualisations de la page de rapport changent pour refléter votre sélection d’exploration actuelle. 

   ![vidéo d’activation des contrôles d’exploration](media/service-reports-visual-interactions/drill2.gif)

