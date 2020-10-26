---
title: Tutoriel Narrations intelligentes
description: 'Tutoriel : Créer des visualisations récapitulatives de narration intelligente dans Power BI'
author: aphilip94
ms.reviewer: aphilip94
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 09/14/2020
ms.author: anphil
LocalizationGroup: Visualizations
ms.openlocfilehash: 4417d66b4afc3c3848667364bdca47150afdf04a
ms.sourcegitcommit: 220427415e2fdc9337244b1ee23e734854179d43
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862922"
---
# <a name="create-smart-narrative-summaries-preview"></a>Créer des résumés de narration intelligente (préversion)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

La visualisation de narration intelligente vous aide à résumer rapidement les visuels et rapports. Elle fournit des insights novateurs pertinents que vous pouvez personnaliser.

![Capture d’écran montrant un résumé de narration intelligente sur le côté droit d’un rapport.](media/power-bi-visualization-smart-narratives/1.png)

Utilisez les résumés de narration intelligente dans vos rapports pour répondre à des points clés, signaler des tendances et modifier la langue et la mise en forme pour un public spécifique. Dans PowerPoint, au lieu de coller une capture d’écran des principales conclusions de votre rapport, vous pouvez ajouter des narrations qui sont mises à jour à chaque actualisation. Votre public peut utiliser les résumés pour comprendre les données, accéder aux points clés plus rapidement et expliquer les données à d’autres utilisateurs.

>[!NOTE]
> Étant donné que la fonctionnalité de narration intelligente est en préversion, vous devez l’activer si vous souhaitez l’utiliser. Dans Power BI Desktop, accédez à **Fichier** > **Options et paramètres** > **Options** > **Fonctionnalités en préversion**. Sélectionnez ensuite **Visuel de narration intelligente**.
>
>![Capture d’écran montrant les options de Power BI. L’option Visuel de narration intelligente est sélectionnée.](media/power-bi-visualization-smart-narratives/2.png)

Pour suivre ce didacticiel, téléchargez l’[exemple de fichier](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Monthly%20Desktop%20Blog%20Samples/2020/2020SU09%20Blog%20Demo%20-%20September.pbix) d’un scénario de vente en ligne.

## <a name="get-started"></a>Commencer 

Dans le volet **Visualisations**, sélectionnez l’icône de **Narration intelligente** pour générer automatiquement un résumé.

![Capture d’écran montrant le volet Visualisations. L’icône de narration intelligente est sélectionnée.](media/power-bi-visualization-smart-narratives/3.png)

Vous voyez une narration basée sur tous les visuels de la page. Par exemple, dans l’exemple de fichier, les narrations intelligentes peuvent générer automatiquement un résumé des visuels du rapport qui concernent les revenus, les visites de sites web et les ventes. Power BI analyse automatiquement les tendances pour montrer que les revenus et les visites ont augmenté. Il calcule même la croissance, qui dans ce cas est de 72 %.
 
![Capture d’écran montrant comment créer une synthèse de narration intelligente.](media/power-bi-visualization-smart-narratives/4.gif)
 
Pour générer une narration intelligente d’une visualisation, cliquez dessus avec le bouton droit, puis sélectionnez **Résumer**. Par exemple, dans l’exemple de fichier, essayez de résumer un graphique à nuages de points qui affiche différentes transactions. Power BI analyse les données et affiche la ville ou la région qui a le revenu le plus élevé par transaction et le nombre le plus élevé de transactions. La narration intelligente affiche également la plage de valeurs attendue pour ces métriques. Vous constatez que la plupart des villes produisent moins de 45 $ par transaction et qu’elles comptent moins de 10 transactions.
 
  
![Capture d’écran montrant une narration intelligente qui résume un nuage de points.](media/power-bi-visualization-smart-narratives/5.gif)
 
## <a name="edit-the-summary"></a>Modification du résumé
 
Le résumé de la narration intelligente est hautement personnalisable. Vous pouvez modifier le texte existant ou le compléter à l’aide des commandes de zone de texte. Par exemple, vous pouvez mettre le texte en gras ou modifier sa couleur.
 
![Capture d’écran montrant les commandes de mise en forme du texte dans une barre d’outils.](media/power-bi-visualization-smart-narratives/6.png)
  
Pour personnaliser le résumé ou ajouter vos propres insights, utilisez des *valeurs dynamiques*. Le texte peut être associé à des champs et mesures existants, ou à une nouvelle mesure définie en langage naturel. Par exemple, pour ajouter des informations sur le nombre d’éléments retournés dans l’exemple de fichier, ajoutez une valeur. 

Lorsque vous entrez un nom de valeur, vous pouvez choisir parmi une liste de suggestions, comme vous le feriez dans un visuel Q&A. Ainsi, en plus de poser des questions sur vos données dans un visuel Q&A, vous pouvez désormais créer vos propres calculs sans même utiliser DAX (Data Analysis Expressions). 
  
![Capture d’écran montrant comment créer une valeur dynamique pour une visualisation avec narration intelligente.](media/power-bi-visualization-smart-narratives/7.gif)
  
Vous pouvez également mettre en forme des valeurs dynamiques. Par exemple, dans l’exemple de fichier, vous pouvez afficher les valeurs sous forme de devise, spécifier des décimales et choisir un séparateur pour les milliers. 
   
![Capture d’écran montrant comment mettre en forme une valeur dynamique.](media/power-bi-visualization-smart-narratives/8.gif)
   
Pour mettre en forme une valeur dynamique, sélectionnez la valeur dans le résumé pour afficher vos options d’édition sous l’onglet **Vérifier**. Ou, dans la zone de texte, en regard de la valeur que vous souhaitez modifier, cliquez sur le bouton Modifier. 
   
![Capture d’écran montrant la zone de texte, avec l’onglet Valeur sélectionné. À côté du nom de la valeur, le bouton Modifier est mis en surbrillance.](media/power-bi-visualization-smart-narratives/9.png)
   
L’onglet **Révision** vous permet également d’examiner, de supprimer ou de réutiliser des valeurs déjà définies. Sélectionnez le signe plus (+) pour insérer la valeur dans le résumé. Vous pouvez également afficher les valeurs générées automatiquement en activant l’option en bas de l’onglet **Vérifier**.

Parfois, un symbole de résumé masqué apparaît dans la narration intelligente. Elle indique que les données et les filtres actuels ne produisent aucun résultat pour la valeur. Un résumé est vide quand aucune information n’est disponible. Par exemple, dans le graphique en courbes de l’exemple de fichier, un résumé des valeurs hautes et basses peut être vide lorsque la ligne du graphique est plate. Toutefois, le résumé peut apparaître dans d’autres conditions. Les symboles de résumé masqué sont visibles uniquement lorsque vous essayez de modifier un résumé.


![Capture d’écran montrant deux symboles de résumé masqués à l’intérieur d’un résumé intelligent.](media/power-bi-visualization-smart-narratives/10.png)
   
## <a name="visual-interactions"></a>Interactions entre les visuels
Un résumé est dynamique. Il met automatiquement à jour le texte et les valeurs dynamiques générés en cas de filtre croisé. Par exemple, si vous sélectionnez les produits électroniques dans le graphique en anneau de l’exemple de fichier, un filtre croisé sera appliqué au reste du rapport ainsi qu’au résumé pour qu’ils se concentrent sur les produits électroniques.  

Dans ce cas, les visites et les revenus affichent des tendances différentes. Le texte récapitulatif est donc mis à jour pour tenir compte des tendances. La valeur count-of-returns que nous avons ajoutée devient 4196 $. Les résumés vides peuvent être mis à jour lorsque vous filtrez de façon croisée.
   
![Capture d’écran montrant comment une sélection sur un graphique peut filtrer un résumé.](media/power-bi-visualization-smart-narratives/11.gif)
   
Un filtrage plus avancé est également possible. Par exemple, dans l’exemple de fichier, examinez le visuel des tendances pour plusieurs produits. Si vous vous intéressez uniquement aux tendances pour un trimestre donné, sélectionnez les points de données pertinents pour mettre à jour le résumé de cette tendance.
   
![Capture d’écran montrant comment sélectionner une courbe de tendance pour filtrer le résumé pour afficher uniquement cette tendance.](media/power-bi-visualization-smart-narratives/12.gif)
   
## <a name="limitations"></a>Limites

La fonctionnalité de narration intelligente ne prend pas en charge les fonctionnalités suivantes :
- Épinglage à un tableau de bord 
- Utilisation de valeurs dynamiques et de la mise en forme conditionnelle (par exemple, titre lié aux données)
- Azure Analysis Services, AS local
- Indicateurs de performance clés, cartes, cartes à plusieurs lignes, mappages, tables, matrices, visuels R ou visuels Python, visuels personnalisés 
- Résumés des visuels dont les colonnes sont regroupées par d’autres colonnes et pour les visuels qui sont générés sur un champ Groupe de données 
- Filtrage croisé en dehors d’un visuel
- Renommage des valeurs dynamiques ou modification des valeurs dynamiques générées automatiquement
- Résumés des visuels qui contiennent des calculs à la volée tels que l’arithmétique QnA et le pourcentage du total général 
   

