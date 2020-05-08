---
title: 'Retail Analysis sample pour Power BI : Visite guidée'
description: 'Retail Analysis sample pour Power BI : Visite guidée'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: eac1c22ba23f7a1a67b2cc120fe38d4c396d864a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80404710"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Retail Analysis sample pour Power BI : Visite guidée

Le pack de contenu Exemple Analyse de la vente au détail contient un tableau de bord, un rapport et un jeu de données qui analyse les données de ventes au détail d’articles vendus dans plusieurs magasins et régions. Les mesures comparent les performances de cette année à celles de l’année précédente en matière de volume des ventes, d’unités, de marge brute et d’écart et permettent une analyse des nouveaux magasins. 

![Tableau de bord pour l’Exemple Analyse de la vente au détail](media/sample-retail-analysis/retail1.png)

Cet exemple fait partie d’une série d’exemples qui illustre la façon dont vous pouvez utiliser Power BI avec des données, des rapports et des tableaux de bord orientés métier. Il a été créé par [obviEnce](http://www.obvience.com/) avec des données réelles qui sont présentées de façon anonyme. Les données sont disponibles dans plusieurs formats : pack de contenu, fichier .pbix Power BI Desktop ou classeur Excel. Consultez [Exemples pour Power BI](sample-datasets.md). 

Ce tutoriel explore le pack de contenu Exemple Analyse de la vente au détail dans le service Power BI. Les expériences d’utilisation des rapports étant similaires dans Power BI Desktop et dans le service, vous pouvez également poursuivre avec et l’exemple de fichier .pbix dans Power BI Desktop. 

Vous n’avez pas besoin d’une licence Power BI pour explorer les exemples dans Power BI Desktop. Si vous n’avez pas de licence Power BI Pro, vous pouvez enregistrer l’exemple dans votre espace Mon espace de travail du service Power BI. 

## <a name="get-the-sample"></a>Obtenir l’exemple

 Avant de pouvoir utiliser l’exemple, vous devez le télécharger en tant que [pack de contenu](#get-the-content-pack-for-this-sample), [fichier .pbix](#get-the-pbix-file-for-this-sample) ou [classeur Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Se procurer le pack de contenu pour cet exemple

1. Ouvrez le service Power BI (app.powerbi.com), connectez-vous et ouvrez l’espace de travail où vous souhaitez enregistrer l’exemple. 

    Si vous n’avez pas de licence Power BI Pro, vous pouvez enregistrer l’exemple dans votre espace Mon espace de travail.

2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.

    ![Sélectionner Obtenir les données](media/sample-datasets/power-bi-get-data.png)
3. Dans la page **Obtenir des données** qui s’affiche, sélectionnez **Exemples**.
   
4. Sélectionnez **Exemple Analyse de la vente au détail**, puis choisissez **Se connecter**.  
  
   ![Se connecter à un exemple](media/sample-retail-analysis/retail16.png)
   
5. Power BI importe le pack de contenu, puis ajoute un tableau de bord, un rapport et un jeu de données à votre espace de travail actuel.
   
   ![Entrée Exemple Analyse de la vente au détail](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Se procurer le fichier .pbix pour cet exemple

Vous pouvez aussi télécharger l’Exemple Analyse de la vente au détails en tant que [fichier .pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), qui est conçu pour être utilisé avec Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Se procurer le classeur Excel pour cet exemple

Si vous souhaitez afficher la source de données de cet exemple, elle est également disponible en tant que [classeur Excel](https://go.microsoft.com/fwlink/?LinkId=529778). Le classeur contient des feuilles Power View que vous pouvez consulter et modifier. Pour afficher les données brutes, activez les compléments Analyse de données, puis sélectionnez **Power Pivot > Gérer**. Pour plus d’informations sur l’activation des compléments Power View et Power Pivot, consultez [Explorer des échantillons Excel dans Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="start-on-the-dashboard-and-open-the-report"></a>Démarrer sur le tableau de bord et ouvrir le rapport

1. Dans l’espace de travail où vous avez enregistré l’exemple, ouvrez l’onglet **Tableaux de bord**, puis recherchez le tableau de bord **Exemple Analyse de la vente au détail** et sélectionnez-le. 
2. Dans le tableau de bord, sélectionnez la vignette **Total Stores New & Existing Stores**, qui s’ouvre dans la page **Store Sales Overview** du rapport Retail Analysis Sample. 

   ![Vignette Total Stores](media/sample-retail-analysis/retail-analysis-7.png)  

   Dans cette page du rapport, vous voyez que nous avons un total de 104 magasins, 10 d’entre eux étant nouveaux. Nous avons deux chaînes, Fashions Direct et Lindseys. Les magasins Fashions Direct sont en moyenne plus grands.
3. Dans le graphique en secteurs **This Year Sales by Chain**, sélectionnez **Fashions Direct**.

   ![Graphique This Year Sales by Chain](media/sample-retail-analysis/retail3.png)  

   Notez le résultat dans le graphique en bulles **Total Sales Variance %**  :

   ![Graphique Total Sales Variance %](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   La région **FD-01** a la moyenne la plus élevée pour **Sales per Square Foot**, et FD-02 a **Total Sales Variance** le plus faible par rapport à l’année dernière. FD-03 et FD-04 sont au global les régions les moins performantes.
4. Sélectionnez des bulles individuelles ou d’autres graphiques pour mettre en évidence des informations croisées, reflétant l’impact de vos sélections.
5. Pour revenir au tableau de bord, sélectionnez **Exemple Analyse de la vente au détail** dans le volet de navigation du haut.

   ![Barre de navigation](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. Dans le tableau de bord, sélectionnez la vignette **This Year’s Sales New & Existing Stores**, ce qui équivaut à taper *This year sales* dans la zone Questions et réponses.

   ![Vignette This Year’s Sales](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Les résultats de Questions et réponses apparaissent :

   ![This Year’s Sales dans Questions et réponses](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Examiner une vignette créée avec Q&R de Power BI
Effectuons une étude plus détaillée.

1. Changez la question en _this year sales **by district**_ . Observez le résultat : Questions et réponses met automatiquement la réponse dans un graphique à barres et suggère d’autres expressions :

   ![« This year’s sales by district » dans Questions et réponses](media/sample-retail-analysis/retail8.png)
2. Changez maintenant la question en _this year sales **by zip and chain**_ .

   Notez comment Power BI répond à la question au fil de la frappe et affiche le graphique approprié.
3. Essayez avec d’autres questions pour voir quel type de résultats vous obtenez.
4. Lorsque vous êtes prêt, retournez au tableau de bord.

## <a name="dive-deeper-into-the-data"></a>Explorer plus en détail les données
Effectuons maintenant un examen encore plus détaillé, en observant les performances des régions.

1. Dans le tableau de bord, sélectionnez la vignette **This Year’s Sales, Last Year’s Sales**, qui ouvre la page **District Monthly Sales** du rapport.

   ![Vignette This Year’s Sales, Last Year’s Sales](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   Dans le graphique **Total Sales Variance % by Fiscal Month**, notez l’importance de la variation de l’écart en % par rapport à l’année dernière, janvier, avril et juillet étant des mois particulièrement mauvais.

   ![Graphique Total Sales Variance % by Fiscal Month](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Voyons si nous pouvons cerner avec précision les problèmes.
2. Dans le graphique en bulles, sélectionnez la bulle **020-Mens**.

   ![Sélectionner 020-Mens](media/sample-retail-analysis/retail11.png)  

   Notez que même si la catégorie des hommes n’a pas été aussi durement touchée en avril que l’ensemble de l’activité, janvier et juillet restent quand même des mois problématiques.
1. Sélectionnez la bulle **010-Womens**.

   ![Sélectionner 010-Womens](media/sample-retail-analysis/retail12.png)

   Notez aussi que la catégorie des femmes s’est comportée d’une façon bien pire que l’activité globale pour tous les mois, et d’une façon bien pire également dans presque tous les mois en comparaison avec l’année précédente.
1. Sélectionnez à nouveau la bulle pour effacer le filtre.

## <a name="try-out-the-slicer"></a>Essayer le segment
Examinons les performances des différentes régions.

1. Sélectionnez **Allan Guinot** dans le sélecteur **District Manager** situé en haut à gauche.

   ![Sélectionner Allan Guinot](media/sample-retail-analysis/retail13.png)

   Notez que la région d’Allan a obtenu les meilleures performances en mars et en juin, en comparaison avec l’année dernière.
2. Avec **Allan Guinot** toujours sélectionné, sélectionnez la bulle **Womens-10** dans le graphique en bulles.

   ![Allan Guinot et Womens-10 sélectionnés](media/sample-retail-analysis/power-bi-allan.png)

   Notez que pour la catégorie Womens-10, la région d’Allan n’a pas atteint le volume de l’année dernière.
3. Examinez les autres responsables de région et catégories : quels autres insights êtes-vous susceptible de trouver ?
4. Quand vous êtes prêt, revenez au tableau de bord.

## <a name="what-the-data-says-about-sales-growth-this-year"></a>Ce que disent les données sur l’augmentation des ventes cette année
Le dernier domaine que nous voulons explorer est notre croissance, en examinant les nouveaux magasins ouverts cette année.

1. Sélectionnez la vignette **Stores Opened This Year by Open Month, Chain**, qui ouvre la page **New Stores Analysis** du rapport.

   ![Page New Stores Analysis](media/sample-retail-analysis/retail15.png)

   Comme le montre clairement la vignette, il s’est ouvert cette année davantage de magasins Fashions Direct que de magasins Lindseys.
2. Observez le graphique **Sales Per Sq Ft by Name** :

   ![Graphique Sales Per Sq Ft by Name](media/sample-retail-analysis/retail14.png)

    Notez la différence dans la moyenne des ventes rapportée à la surface pour les nouveaux magasins.
3. Sélectionnez l’élément de légende **Fashions Direct** dans le graphique **Open Store Count by Open Month and Chain** en haut à droite. Notez que, même pour la même chaîne, le meilleur magasin (Winchester Fashions Direct) a été nettement plus performant que le plus mauvais magasin (Cincinnati 2 Fashions Direct), avec respectivement 21,22 $ contre 12,86 $.

   ![Fashions Direct sélectionné](media/sample-retail-analysis/power-bi-lindseys.png)
4. Sélectionnez **Winchester Fashions Direct** dans le sélecteur **Name**, puis observez le graphique en courbes. Les premiers chiffres de ventes ont été rapportés en février.
5. Sélectionnez **Cincinnati 2 Fashions Direct** dans le sélecteur : vous voyez dans le graphique en courbes qu’il a été ouvert en juin et qu’il est le magasin le moins performant.
6. Explorez en sélectionnant d’autres barres, lignes et bulles dans les graphiques afin de découvrir d’autres insights.

## <a name="next-steps-connect-to-your-data"></a>Étapes suivantes : Vous connecter à vos données
Cet environnement est sécurisé pour y jouer, étant donné que vous pouvez choisir ne pas enregistrer vos modifications. Mais si vous les enregistrez, vous pouvez toujours sélectionner **Obtenir des données** pour obtenir une nouvelle copie de cet exemple.

Nous espérons que cette visite guidée vous a montré comment les tableaux de bord, Questions et réponses et les rapports Power BI peuvent fournir des insights sur des exemples de données. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. Pour en savoir plus, consultez [Prise en main du service Power BI](service-get-started.md).
