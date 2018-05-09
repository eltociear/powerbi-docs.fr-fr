---
title: 'Exemple Analyse de l’approvisionnement : visite guidée'
description: 'Exemple Analyse de l’approvisionnement pour Power BI : visite guidée'
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: 3bca6f79b3a1b92243948fb64660e8946aedca7c
ms.sourcegitcommit: 743e44fc8730fea0f7149916080b0c6d7eb6359d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Exemple Analyse de l’approvisionnement pour Power BI : visite guidée

## <a name="overview-of-the-procurement-analysis-sample"></a>Présentation de l’exemple Analyse de l’approvisionnement
Cet exemple sectoriel de tableau de bord et son rapport sous-jacent permettent d’analyser les dépenses d’une entreprise de fabrication auprès des fournisseurs, par catégorie et par emplacement géographique. Dans cet exemple, nous explorons les points suivants :

* Quels sont les meilleurs fournisseurs ?
* Dans quelles catégories dépensons-nous le plus ?
* Quels sont les fournisseurs qui nous proposent les plus fortes remises et quand ?

Cet exemple fait partie d’une série d’exemples qui illustre la façon dont vous pouvez utiliser Power BI avec des données, des rapports et des tableaux de bord orientés métier. Il s’agit de données réelles provenant d’obviEnce ([www.obvience.com](http://www.obvience.com/)), présentées de façon anonyme.

![](media/sample-procurement/procurement1.png)

## <a name="prerequisites"></a>Conditions préalables

 Avant de pouvoir utiliser l’exemple, vous devez le télécharger en tant que [pack de contenu](https://docs.microsoft.com/en-us/power-bi/sample-procurement#get-the-content-pack-for-this-sample), [fichier .pbix](http://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement Analysis Sample PBIX.pbix) ou [classeur Excel](http://go.microsoft.com/fwlink/?LinkId=529784).

### <a name="get-the-content-pack-for-this-sample"></a>Se procurer le pack de contenu pour cet exemple

1. Ouvrez le service Power BI (app.powerbi.com), puis connectez-vous.
2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Dans la page Obtenir des données qui s’affiche, sélectionnez l’icône **Exemples**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Sélectionnez l’exemple **Analyse de l’approvisionnement**, puis choisissez **Se connecter**.  
  
   ![Obtenir les données](media/sample-procurement/procurement1a.png)
   
5. Power BI importe le pack de contenu, puis ajoute un tableau de bord, un rapport et un jeu de données à votre espace de travail. Le nouveau contenu est signalé par un astérisque jaune. 
   
   ![Astérisque](media/sample-procurement/procurement1b.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Se procurer le fichier .pbix pour cet exemple

Vous pouvez également télécharger l’exemple en tant que fichier .pbix, qui est conçu pour une utilisation avec Power BI Desktop. 

 * [Exemple Analyse de l’approvisionnement](http://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Se procurer le classeur Excel pour cet exemple
Vous pouvez également [télécharger uniquement le jeu de données (classeur Excel) de cet exemple](http://go.microsoft.com/fwlink/?LinkId=529784). Le classeur contient des feuilles Power View que vous pouvez consulter et modifier. Pour afficher les données brutes, sélectionnez **Power Pivot > Gérer**.


## <a name="spending-trends"></a>Tendances en matière de dépenses
Commençons par rechercher les tendances en matière de dépenses par catégorie et par implantation géographique.  

1. Dans votre espace de travail, ouvrez l’onglet **Tableaux de bord**, puis sélectionnez le tableau de bord Analyse de l’approvisionnement.
2. Sélectionnez la vignette de tableau de bord **Total Invoice by Country/Region**(Total de facturation par pays/région). Cela ouvre la page « Spend Overview » (Vue d’ensemble des dépenses) du rapport « Exemple Analyse de l’approvisionnement ».

    ![](media/sample-procurement/procurement2.png)

Notez plusieurs choses :

* Dans le graphique en courbes **Total Invoice by Month and Category** (Total de facturation par mois et par catégorie) : la catégorie **Direct** présente des dépenses relativement homogènes, la catégorie **Logistics** (Logistique) présente un pic en décembre et la catégorie **Other** (Autre) présente un pic en février.
* Dans la carte **Total Invoice by Country/Region** (Total de facturation par pays/région) : la plupart de nos dépenses se font aux États-Unis.
* Dans l’histogramme **Total Invoice by Sub Category** (Total de facturation par sous-catégorie) : les sous-catégories **Hardware** (Matériel) et **Indirect Goods & Services** (Biens et services indirects) sont les plus importantes.
* Dans le graphique à barres Total Invoice by Tier (Total de facturation par niveau), nous traitons essentiellement avec nos fournisseurs de niveau 1 (les 10 principaux). Cela permet de mieux gérer les relations avec les fournisseurs.

## <a name="spending-in-mexico"></a>Dépenses au Mexique
Explorons les postes de dépenses au Mexique.

1. Dans le graphique à secteurs, sélectionnez la bulle **Mexico** (Mexique) dans la carte géographique. Notez que dans l’histogramme « Total Invoice by Sub Category » (Total de facturation par sous-catégorie), la sous-catégorie **Indirect Goods & Services** (Biens et services indirects) est surreprésentée.

   ![](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Explorez la colonne **Indirect Goods & Services** (Biens et services indirects) :

   * Sélectionnez la flèche ![](media/sample-procurement/pbi_drilldown_icon.png) en haut à droite du graphique.
   * Sélectionnez la colonne **Indirect Goods & Services** (Biens et services indirects).

      De loin, la dépense la plus importante dans cette catégorie est Sales & Marketing (Ventes et marketing).
   * Sélectionnez à nouveau **Mexique** dans la carte.

      La dépense la plus importante dans cette catégorie au Mexique est Maintenance & Repair (Maintenance et réparation).

      ![](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Sélectionnez la flèche vers le haut dans le coin supérieur gauche du graphique pour remonter d’un niveau.
4. Sélectionnez à nouveau la flèche pour désactiver l’exploration.  
5. Sélectionnez **Power BI** dans la barre de navigation supérieure pour revenir à votre espace de travail.

## <a name="evaluate-different-cities"></a>Évaluer différentes villes
Nous pouvons utiliser la mise en évidence pour évaluer différentes villes.

1. Sélectionnez la vignette de tableau de bord **Total Invoice, Discount % by Month**(Total de facturation, % de remise par mois). Le rapport s’ouvre à la page « Discount Analysis » (Analyse des remises).
2. Sélectionnez les différentes villes dans le graphique de compartimentage **Total Invoice by City** (Total de facturation par ville) pour les comparer. Presque toutes les factures de Miami proviennent de fournisseurs de niveau 1.

   ![](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Remises fournisseur
Intéressons-nous aussi aux remises pratiquées par les fournisseurs, ainsi qu’aux périodes où ils les consentent le plus souvent.

![](media/sample-procurement/procurement4.png)

Plus précisément, posons-nous ces questions :

* Les remises sont-elles différentes d’un mois à l’autre ou identiques tous les mois ?
* Certaines villes obtiennent-elles davantage de remises que d’autres ?

### <a name="discount-by-month"></a>Remises par mois
En examinant le graphique combiné **Total Invoice and Discount % by Month** (Total de facturation et % de remise par mois), nous pouvons observer que **February** (février) est le mois où l’activité est la plus forte, tandis que **September** (septembre) est le mois le plus calme. À présent, intéressons-nous au pourcentage de remise au cours de ces mois.
Notez que lorsque les volumes augmentent, les remises diminuent et lorsque les volumes sont faibles, les remises augmentent. Plus nous avons besoin de remises, moins nous faisons de bonnes affaires.

![](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Remises par ville
Un autre point à explorer est celui des remises par ville. Sélectionnez chaque ville dans le graphique de compartimentage pour voir comment évoluent les autres graphiques.

* Pour Saint-Louis, Missouri, le total de facturation a connu pic important en février et des remises en forte baisse en avril.
* C’est à Mexico que le pourcentage de remise est le plus élevé (11,05 %), le plus faible étant constaté à Atlanta, Géorgie (0,08 %).

![](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Modifier le rapport
Sélectionnez **Modifier le rapport** en haut à gauche et faites une exploration en mode Edition.

* Découvrir comment les pages sont réalisées
* Ajouter des pages et des graphiques basés sur les mêmes données
* Modifier le type de visualisation d’un graphique, par exemple, changer le graphique de compartimentage en graphique en anneau
* Les épingler au tableau de bord

Il s’agit d’un environnement sécurisé à explorer. Vous pouvez toujours choisir de ne pas enregistrer les modifications apportées. Si vous les enregistrez, vous pouvez toujours accéder à **Obtenir des données** pour avoir une nouvelle copie de cet exemple.

## <a name="next-steps-connect-to-your-data"></a>Étapes suivantes : Connexion à vos données
Nous espérons qu’à travers cette visite guidée, vous aurez cerné tout l’intérêt des tableaux de bord et rapports Power BI pour tirer des informations des données d’approvisionnement. À présent, c’est votre tour : connectez-vous à vos propres données. Avec Power BI, vous pouvez vous connecter à une grande variété de sources de données. En savoir plus sur [la prise en main de Power BI](service-get-started.md).
