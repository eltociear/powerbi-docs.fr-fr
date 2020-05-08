---
title: Épingler une vignette à un tableau de bord à partir de Questions et réponses
description: Documentation sur la manière d’épingler une vignette à un tableau de bord Power BI à partir de la zone Q&R
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 77be727de3cda1d3b6fd5c34b6e572b1d505fc54
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76282003"
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Épingler une vignette à un tableau de bord à partir de Questions et réponses
## <a name="how-to-pin-a-tile-from-qa"></a>Épingler une vignette à partir de Q&R
Q&R est l’outil de génération de rapports ad hoc de Power BI. Vous avez besoin de données spécifiques ? Posez une question à propos de vos données et recevez une réponse sous la forme d’une visualisation.

Dans cette procédure, nous allons utiliser le service Power BI (app.powerbi.com) pour ouvrir un tableau de bord, poser une question en langage naturel pour créer une visualisation et épingler cette visualisation à un tableau de bord. Les tableaux de bord ne sont pas disponibles dans Power BI Desktop. Pour plus d’informations sur l’utilisation de Questions et réponses avec d’autres outils et contenu Power BI, consultez la [présentation de Questions et réponses dans Power BI](consumer/end-user-q-and-a.md). 

Pour suivre la procédure, ouvrez le tableau de bord [Exemple Analyse de la vente au détail](sample-retail-analysis.md).


1. Ouvrez un [tableau de bord](consumer/end-user-dashboards.md) sur lequel au moins une vignette est épinglée à partir d’un rapport. Lorsque vous posez une question, Power BI cherche la réponse dans un jeu de données dont une vignette est épinglée à ce tableau de bord.  Pour plus d’informations, voir [obtenir des données](service-get-data.md).
2. En haut de votre tableau de bord, dans la zone de question, commencez à taper ce que vous voulez savoir sur vos données.  
   ![zone Questions et réponses](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Par exemple, quand vous tapez « ventes de l’année dernière par mois et par secteur »…  
   ![tapez une question](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)

   la zone des questions vous propose des suggestions.
4. Pour ajouter le graphique à votre tableau de bord sous forme de vignette, sélectionnez l’icône représentant une épingle ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) en haut à droite du canevas. Si le tableau de bord a été partagé avec vous, vous ne pouvez pas l’épingler à une visualisation.

5. Épinglez la vignette à un tableau de bord existant ou à un nouveau tableau de bord.

   ![boîte de dialogue Épingler au tableau de bord](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Tableau de bord existant : sélectionnez le nom du tableau de bord dans la liste déroulante. Votre choix est limité aux tableaux de bord figurant à l’intérieur de l’espace de travail actuel.
   * Nouveau tableau de bord : tapez le nom du nouveau tableau de bord pour ajouter celui-ci à votre espace de travail actuel.

6. Sélectionnez **Épingler**.

   Un message de réussite (dans l’angle supérieur droit) vous indique que la visualisation a été ajoutée, sous forme de vignette, à votre tableau de bord.  

   ![Épinglé au tableau de bord](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Sélectionnez **Accéder au tableau de bord** pour voir la nouvelle vignette. Vous pouvez [renommer, redimensionner et repositionner la vignette, et y ajouter également un lien hypertexte](service-dashboard-edit-tile.md) depuis votre tableau de bord.

   ![tableau de bord avec vignettes](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
* Quand vous commencez à taper une question, Q&R recherche immédiatement la meilleure réponse dans tous les jeux de données associés au tableau de bord actif.  Le « tableau de bord actuel » est le tableau de bord répertorié dans le volet de navigation supérieur. Par exemple, cette question est posée dans le tableau de bord **Exemple Analyse de la vente au détail** qui fait partie de l’espace de travail **mihart**.

  ![vues miniatures](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **Comment la fonctionnalité Q&R sait-elle quels jeux de données utiliser ?**  Questions et réponses a accès à tous les jeux de données dont au moins une visualisation est épinglée au tableau de bord.

* **Vous ne voyez pas la zone de questions** ? Contactez votre administrateur Power BI. L’administrateur a la possibilité de désactiver Questions et réponses.


## <a name="next-steps"></a>Étapes suivantes
[Renommer, redimensionner, ajouter un lien hypertexte, repositionner la vignette et bien plus encore](service-dashboard-edit-tile.md)    
[Afficher la vignette de votre tableau de bord en mode Focus](consumer/end-user-focus.md)     
[Revenir à Q&R dans Power BI](consumer/end-user-q-and-a.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
