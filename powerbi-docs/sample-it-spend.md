---
title: 'Exemple Analyse des dépenses informatiques pour Power BI : Visite guidée'
description: 'Exemple Analyse des dépenses informatiques pour Power BI : Visite guidée'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 00effa1838327a9463671cf9be2f5764be71deb4
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404703"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Exemple Analyse des dépenses informatiques pour Power BI : Visite guidée

Le pack de contenu de l’exemple Analyse des dépenses informatiques contient un tableau de bord, un rapport et un jeu de données permettant d’analyser les coûts prévus par rapport aux coûts réels d’un service informatique. Cette comparaison nous aide à évaluer la pertinence des prévisions de l’entreprise pour l’année et à analyser les secteurs qui présentent des écarts importants par rapport aux prévisions. L’entreprise décrite dans cet exemple suit un cycle de prévision annuel. Ensuite, tous les trimestres, elle produit ses toutes dernières estimations pour faciliter l’analyse des changements survenus en matière de dépenses informatiques pendant l’année fiscale.

![Tableau de bord pour l’exemple Analyse des dépenses informatiques](media/sample-it-spend/it1.png)

Cet exemple fait partie d’une série d’exemples qui illustre la façon dont vous pouvez utiliser Power BI avec des données, des rapports et des tableaux de bord orientés métier. Il a été créé par [obviEnce](http://www.obvience.com/) avec des données réelles qui sont présentées de façon anonyme. Les données sont disponibles dans plusieurs formats : pack de contenu, fichier .pbix Power BI Desktop ou classeur Excel. Consultez [Exemples pour Power BI](sample-datasets.md). 

Ce tutoriel utilise le pack de contenu Exemple Analyse des dépenses informatiques dans le service Power BI. Les expériences d’utilisation des rapports étant similaires dans Power BI Desktop et dans le service, vous pouvez également poursuivre avec et l’exemple de fichier .pbix dans Power BI Desktop. 

Vous n’avez pas besoin d’une licence Power BI pour explorer les exemples dans Power BI Desktop. Si vous n’avez pas de licence Power BI Pro, vous pouvez enregistrer l’exemple dans votre espace Mon espace de travail du service Power BI. 

## <a name="get-the-sample"></a>Obtenir l’exemple

 Avant de pouvoir utiliser l’exemple, vous devez le télécharger en tant que [pack de contenu](#get-the-content-pack-for-this-sample), [fichier .pbix](#get-the-pbix-file-for-this-sample) ou [classeur Excel](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Se procurer le pack de contenu pour cet exemple

1. Ouvrez le service Power BI (app.powerbi.com), connectez-vous et ouvrez l’espace de travail où vous souhaitez enregistrer l’exemple.

   Si vous n’avez pas de licence Power BI Pro, vous pouvez enregistrer l’exemple dans votre espace Mon espace de travail.

2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.
   
   ![Sélectionner Obtenir les données](media/sample-datasets/power-bi-get-data.png)
3. Dans la page **Obtenir des données** qui s’affiche, sélectionnez **Exemples**.
   
4. Sélectionnez **Exemple Analyse des dépenses informatiques**, puis choisissez **Se connecter**.  
  
   ![Se connecter à un exemple](media/sample-it-spend/it-connect.png)
   
5. Power BI importe le pack de contenu, puis ajoute un tableau de bord, un rapport et un jeu de données à votre espace de travail actuel.
   
   ![Entrée de l’exemple Analyse des dépenses informatiques](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Se procurer le fichier .pbix pour cet exemple

Vous pouvez également télécharger l’exemple Analyse des dépenses informatiques en tant que [fichier .pbix](https://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix), est conçu pour une utilisation avec Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Se procurer le classeur Excel pour cet exemple

Si vous souhaitez afficher la source de données de cet exemple, elle est également disponible en tant que [classeur Excel](https://go.microsoft.com/fwlink/?LinkId=529783). Le classeur contient des feuilles Power View que vous pouvez consulter et modifier. Pour afficher les données brutes, activez les compléments Analyse de données, puis sélectionnez **Power Pivot > Gérer**. Pour plus d’informations sur l’activation des compléments Power View et Power Pivot, consultez [Explorer des échantillons Excel dans Excel](sample-datasets.md#explore-excel-samples-inside-excel).

## <a name="it-spend-analysis-sample-dashboard"></a>Exemple de tableau de bord Analyse des dépenses informatiques
Les deux vignettes représentant des nombres sur la partie gauche du tableau de bord, **Var Plan %** (% de prévisions d’écart) et **Variance Latest Estimate % Quarter 3**(% des dernières estimations de l’écart du trimestre 3), nous donnent une vue d’ensemble de nos résultats par rapport aux prévisions et par rapport aux estimations du dernier trimestre (LE3 = Latest Estimate Quarter 3, dernières estimations Trimestre 3). Globalement, nous sommes à environ 6 % des prévisions. Examinons la cause de cet écart : quand, où et dans quelle catégorie.

## <a name="ytd-it-spend-trend-analysis-page"></a>Page « YTD IT Spend Trend Analysis » (Analyse des tendances des dépenses informatiques de l’année en cours)
En sélectionnant la vignette de tableau de bord **Var Plan % by Sales Region** (% écart prévisions par région de vente), vous accédez à la page **YTD IT Spend Trend Analysis (Analyse des tendances des dépenses informatiques de l’année en cours)** du rapport de l’exemple Analyse des dépenses informatiques. Nous voyons en un clin d’œil que nous avons un écart positif aux États-Unis et en Europe, et un écart négatif au Canada, en Amérique latine et en Australie. Les États-Unis affichent un écart d’environ 6 % au-dessus des dernières estimations et l’Australie a un écart d’environ 7 % en dessous des dernières estimations.

![Var Plan % by Sales Region](media/sample-it-spend/it2.png)

Mais le simple examen de ce graphique et le fait d’en tirer des conclusions peuvent induire en erreur. Nous devons examiner les montants réels en dollars pour replacer les choses dans leur contexte.

1. Sélectionnez **Aus and NZ** (Aus et NZ) dans le graphique **Var Plan % by Sales Region** (% de prévisions d’écart par région de vente) et observez le graphique **Var Plan by IT Area** (Prévisions d’écart par domaine informatique).

   ![Page « YTD IT Spend Trend Analysis » (Analyse des tendances des dépenses informatiques de l’année en cours)](media/sample-it-spend/it3.png)
2. Sélectionnez à présent **USA**. Notez que l’Australie et Nouvelle-Zélande représentent une très petite partie de nos dépenses globales par rapport aux États-Unis.

    Explorons maintenant quelle catégorie aux États-Unis est à l’origine de l’écart.

## <a name="ask-questions-of-the-data"></a>Poser des questions sur les données
1. Sélectionnez **Exemple Analyse des dépenses informatiques** dans le volet de navigation supérieur pour revenir à l’exemple de tableau de bord.
2. Sélectionnez **Poser une question sur vos données**.
3. À partir de la liste **Questions pour vous aider à démarrer** affichée à gauche, sélectionnez **what is the plan by IT area** (quelles sont les prévisions par domaine informatique).

   ![Graphique Plan by IT Area](media/sample-it-spend/it-area-chart.png)

4. Dans la zone Q&R, effacez l’entrée précédente puis entrez *afficher le graphique à barres Var Plan % and Var LE3 % by IT area* (% de prévisions d’écart et % des dernières estimations d’écart pour le trimestre 3).

   ![Graphique Var Plan % and Var LE3 % by IT Area](media/sample-it-spend/it4.png)

   Dans le premier domaine informatique, **Infrastructure**, notez que le pourcentage a changé considérablement entre les prévisions d’écart initiales et les dernières estimations des prévisions d’écart.

## <a name="ytd-spend-by-cost-elements-page"></a>Page « YTD Spend by Cost Elements » (Dépenses de l’année en cours par élément de coût)

1. Revenez au tableau de bord et examinez la vignette **Variance Plan %, Variance Latest Estimate % - Quarter 3** (% de prévisions d’écart, % de l’estimation du dernier écart - 3e trimestre).

   ![Vignette Var Plan %, Var LE3](media/sample-it-spend/it5.png)

   Notez que le domaine Infrastructure se démarque avec une grande variation positive par rapport aux prévisions.

1. Sélectionnez cette vignette pour ouvrir le rapport et afficher la page **YTD Spend by Cost Elements** (Dépenses de l’année en cours par élément de coût).
2. Sélectionnez la barre **Infrastructure** dans le graphique **Var Plan % and Var LE3 % by IT Area** (% de prévisions d’écart et % des dernières estimations d’écart pour le trimestre 3 par domaine informatique) dans l’angle inférieur droit, et observez l’écart par rapport aux prévisions dans le graphique **Var Plan % by Sales Region** (% de prévisions d’écart par région de vente) en bas à gauche.

    ![Page « YTD Spend by Cost Elements » (Dépenses de l’année en cours par élément de coût)](media/sample-it-spend/it6.png)
3. Sélectionnez un à un chaque nom dans le segment **Cost Element Group** (Groupe d’éléments de coût) pour rechercher l’élément de coût présentant un écart important.
4. L’option **Autres** étant sélectionnée, sélectionnez **Infrastructure** dans le segment **IT Area** (Domaine informatique), puis choisissez les sous-domaines du segment **IT Sub Area** (Sous-domaine informatique) pour trouver le sous-domaine présentant le plus grand écart.  

   Notez l’écart important pour **Mise en réseau**. Apparemment, l’entreprise a décidé d’offrir à ses employés des services téléphoniques, mais cette mesure n’a pas été prévue.

## <a name="plan-variance-analysis-page"></a>Page « Plan Variance Analysis » (Analyse des écarts des estimations)

1. Sélectionnez l’onglet **Plan Variance Analysis** (Analyse des écarts des estimations) au bas de la page.

2. Dans le graphique combiné **Var Plan and Var Plan % by Business Area** (Prévisions d’écart et % de prévisions d’écart par secteur d’activité) situé à gauche, sélectionnez la colonne **Infrastructure** pour mettre en surbrillance les valeurs du secteur d’activité Infrastructure dans le reste de la page.

    ![Page « Plan Variance Analysis » (Analyse des écarts des estimations)](media/sample-it-spend/it7.png)

   Notez, sur le graphique **Var plan % by Month and Business Area** (% de prévisions d’écart par mois et par secteur d’activité), que ce secteur d’activité Infrastructure a commencé à présenter un écart positif en février. Notez également comment l’écart par rapport à la valeur de prévision pour ce secteur d’activité varie par pays, par rapport à la valeur de tous les secteurs d’activité. 

3. Utiliser les segments **IT Area** (Domaine informatique) et **IT Sub Areas** (Sous-domaines informatiques) sur la droite pour filtrer les valeurs du reste de la page et explorer les données. 

## <a name="edit-the-report"></a>Modifier le rapport
Sélectionnez **Modifier le rapport** en haut à gauche pour faire une exploration en mode Edition :

* Découvrez la façon dont les pages sont constituées, les champs de chaque graphique, et les filtres sur les pages.
* Ajoutez des pages et des graphiques basés sur les mêmes données.
* Modifiez le type de visualisation pour chaque graphique.
* Épinglez les graphiques présentant un intérêt sur votre tableau de bord.

## <a name="next-steps-connect-to-your-data"></a>Étapes suivantes : Vous connecter à vos données
Cet environnement est sécurisé pour y jouer, étant donné que vous pouvez choisir ne pas enregistrer vos modifications. Mais si vous les enregistrez, vous pouvez toujours sélectionner **Obtenir des données** pour obtenir une nouvelle copie de cet exemple.

Nous espérons que cette visite guidée vous a montré comment les tableaux de bord, Questions et réponses et les rapports Power BI peuvent fournir des insights sur des exemples de données. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. Pour en savoir plus, consultez [Prise en main du service Power BI](service-get-started.md).
