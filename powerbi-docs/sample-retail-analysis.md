---
title: 'Exemple Analyse de la vente au détail pour Power BI : Visite guidée'
description: 'Exemple Analyse de la vente au détail pour Power BI : Visite guidée'
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: ff5da3623d572b8ecb3edc8c5eb40d866e6961d5
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Exemple Analyse de la vente au détail pour Power BI : Visite guidée

Cet exemple de tableau de bord et son rapport sous-jacent permettent d’analyser les données de vente au détail d’articles vendus dans plusieurs magasins et régions. Les métriques comparent les performances de l’année à celle de l’année précédente pour les données suivantes : ventes, unités, marge brute, écart et analyse des nouveaux magasins. Il s’agit de données réelles provenant d’obviEnce ([www.obvience.com](http://www.obvience.com)), présentées de façon anonyme.

![](media/sample-retail-analysis/retail1.png)

## <a name="prerequisites"></a>Conditions préalables

 Avant de pouvoir utiliser l’exemple, vous devez le télécharger en tant que [pack de contenu](https://docs.microsoft.com/en-us/power-bi/sample-datasets#get-and-open-a-sample-content-pack-in-power-bi-service), [fichier .pbix](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) ou [classeur Excel](http://go.microsoft.com/fwlink/?LinkId=529778).

### <a name="get-the-content-pack-for-this-sample"></a>Se procurer le pack de contenu pour cet exemple

1. Ouvrez le service Power BI (app.powerbi.com), puis connectez-vous.
2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Dans la page Obtenir des données qui s’affiche, sélectionnez l’icône **Exemples**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Sélectionnez **Exemple Analyse de la vente au détail**, puis choisissez **Se connecter**.  
  
   ![Retail Analysis Sample](media/sample-retail-analysis/retail16.png)
   
5. Power BI importe le pack de contenu, puis ajoute un tableau de bord, un rapport et un jeu de données à votre espace de travail. Le nouveau contenu est signalé par un astérisque jaune. 
   
   ![Retail Analysis Sample](media/sample-retail-analysis/retail17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Se procurer le fichier .pbix pour cet exemple

Vous pouvez également télécharger l’exemple en tant que fichier .pbix, qui est conçu pour une utilisation avec Power BI Desktop. 

 * [Exemple Analyse de la vente au détail](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Se procurer le classeur Excel pour cet exemple
Vous pouvez également [télécharger uniquement le jeu de données (classeur Excel) de cet exemple](http://go.microsoft.com/fwlink/?LinkId=529778). Le classeur contient des feuilles Power View que vous pouvez consulter et modifier. Pour afficher les données brutes, sélectionnez **Power Pivot > Gérer**.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Démarrer sur le tableau de bord et ouvrir le rapport
1. Dans le tableau de bord, sélectionnez la vignette « Total Stores » (Nombre total de magasins) :

   ![](media/sample-retail-analysis/retail-analysis-7.png)  

   Vous accédez à la page « Store Sales Overview » (Vue d’ensemble des ventes des magasins) du rapport. Vous voyez que nous avons un total de 104 magasins, dont 10 sont nouveaux. Nous avons deux chaînes, Fashions Direct et Lindseys. Les magasins Fashions Direct sont en moyenne plus grands.
2. Sur le graphique en secteurs, sélectionnez **Fashions Direct**.

   ![](media/sample-retail-analysis/retail3.png)  

   Notez le résultat dans le graphique en bulles :

   ![](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   La région FD-01 a la moyenne la plus élevée des ventes par unité de surface, FD-02 a l’écart type le plus faible pour les ventes par rapport à l’année dernière, FD-03 et FD-04 ont les résultats les moins bons dans l’ensemble.
3. Sélectionnez des bulles individuelles ou d’autres graphiques pour mettre en évidence des informations croisées, reflétant l’impact de vos sélections.
4. Pour revenir au tableau de bord, sélectionnez son nom dans la barre de navigation supérieure (fils d’Ariane).

   ![](media/sample-retail-analysis/power-bi-breadcrumbs.png)
5. Dans le tableau de bord, sélectionnez la vignette indiquant « This Year’s Sales » (Ventes de cette année).

   ![](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Cela équivaut à taper « This year sales » (Ventes de cette année) dans la zone de question.

   L’écran suivant s’affiche :

   ![](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Examiner une vignette créée avec Q&R de Power BI
Effectuons une étude plus détaillée.

1. Ajoutez « This Year’s Sales **by district**» (Ventes de cette année par région) à la question. Observez le résultat : l’application met automatiquement la réponse dans un graphique à barres et suggère d’autres expressions :

   ![](media/sample-retail-analysis/retail8.png)
2. Remplacez maintenant la question par « This Year’s Sales **by zip and chain**» (Ventes de cette année par code postal et par chaîne).

   Notez comment la réponse à la question s’affiche avec les graphiques appropriés à mesure que vous tapez.
3. Essayez avec d’autres questions pour voir quel type de résultats vous obtenez.
4. Lorsque vous êtes prêt, retournez au tableau de bord.

## <a name="dive-deeper-into-the-data"></a>Explorer plus en détail les données
Effectuons maintenant un examen encore plus détaillé, en observant les performances des régions.

1. Dans le tableau de bord, sélectionnez la vignette comparant les ventes de cette année à celles de l’année dernière.

   ![](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   Notez l’important pourcentage d’écart par rapport à l’année dernière, les mois de janvier, avril et juillet étant particulièrement mauvais.

   ![](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Voyons si nous pouvons cerner avec précision les problèmes.
2. Sélectionnez le graphique en bulles, puis choisissez **020-Mens**(020-Hommes).

   ![](media/sample-retail-analysis/retail11.png)  

   Notez que la catégorie Hommes n’était pas aussi durement touchée en avril que l’ensemble de l’activité, mais que janvier et juillet sont encore des mois problématiques.
3. À présent, sélectionnez la bulle **010-Womens**(010-Dames).

   ![](media/sample-retail-analysis/retail12.png)

   Notez aussi que la catégorie Femmes s’est comportée d’une façon bien pire que l’activité globale pour tous les mois, et d’une façon bien pire également dans presque tous les mois en comparaison avec l’année précédente.
4. Sélectionnez à nouveau la bulle pour effacer le filtre.

## <a name="try-out-the-slicer"></a>Essayer le segment
Examinons les performances des différentes régions.

1. Sélectionnez Allan Guinot dans le segment situé en haut à gauche.

   ![](media/sample-retail-analysis/retail13.png)

   Notez que la région d’Allan a obtenu les meilleures performances en mars et en juin l’année dernière.
2. À présent, Allan étant sélectionné, cliquez sur la bulle correspondant à la catégorie Womens (Dames).

   ![](media/sample-retail-analysis/power-bi-allan.png)

   Notez que pour la catégorie Femmes, sa région n’a jamais atteint le volume de l’année dernière.
3. Examinez les autres responsables de région et catégories : quelles autres informations pouvez-vous découvrir ?
4. Lorsque vous êtes prêt, retournez au tableau de bord.

## <a name="what-is-our-data-telling-us-about-sales-growth-this-year"></a>Que nous apprennent nos données sur la croissance des ventes cette année ?
Le dernier domaine que nous souhaitons examiner est notre croissance : les nouveaux magasins ouverts cette année.

1. Sélectionnez la vignette « Stores Opened This Year » (Magasins ouverts cette année).

   ![](media/sample-retail-analysis/retail15.png)

   Comme le montre clairement la vignette, il s’est ouvert cette année davantage de magasins Fashions Direct que de magasins Lindseys.
2. Observez le graphique « Sales Per Sq Ft by Name » (ventes par pied carré par nom) :

   ![](media/sample-retail-analysis/retail14.png)

    Il y a une grande différence dans les ventes moyennes par pied carré pour les nouveaux magasins.
3. Cliquez sur l’élément de légende Fashions Direct dans le graphique affiché en haut à droite. Notez que, même pour la même chaîne, le meilleur magasin (Winchester Fashions Direct) a été nettement plus performant que le plus mauvais magasin (Cincinnati 2 Fashions Direct), avec 21,22 $ contre 12,86 $, respectivement.

   ![](media/sample-retail-analysis/power-bi-lindseys.png)
4. Cliquez sur Winchester Fashions Direct dans le segment, puis observez le graphique en courbes. Les premiers chiffres de ventes ont été rapportés en février.
5. Cliquez sur Cincinnati 2 Fashions Direct dans le segment : vous voyez dans le graphique en courbes qu’il a été ouvert en juin et qu’il semble être le magasin le moins performant.
6. Comme précédemment, poursuivez l’exploration en cliquant sur les autres barres, lignes et bulles dans les graphiques, afin de découvrir d’autres informations.

Il s’agit d’un environnement sécurisé à explorer. Vous pouvez toujours choisir de ne pas enregistrer les modifications apportées. Mais si vous les enregistrez, vous pouvez toujours accéder à Obtenir des données pour avoir une nouvelle copie de cet exemple.

## <a name="connect-to-your-data"></a>Vous connecter à vos données
Nous espérons que cette visite guidée vous a montré comment les tableaux de bord, Q&R et les rapports Power BI peuvent fournir des informations sur les données des ventes. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. En savoir plus sur [la prise en main de Power BI](service-get-started.md).

## <a name="next-steps"></a>Étapes suivantes
* [Télécharger l’exemple de pack de contenu Analyse de la vente au détail](sample-tutorial-connect-to-the-samples.md)
* [Télécharger un fichier zip de tous les fichiers d’exemple](http://go.microsoft.com/fwlink/?LinkId=535020)    
* [Télécharger le classeur Excel pour cet exemple Power BI](http://go.microsoft.com/fwlink/?LinkId=529778)    
* [Obtenir des données (pour Power BI)](service-get-data.md)    
* [Power BI – Concepts de base](service-basic-concepts.md)    
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
