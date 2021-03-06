---
title: Catégorisation des données dans Power BI Desktop
description: Catégorisation des données dans Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Model your data
ms.openlocfilehash: d99eb0355d414a9e1627da0b5629eaf45cbaf18d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415792"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Spécifier des catégories de données dans Power BI Desktop
Dans Power BI Desktop, vous pouvez spécifier la *catégorie de données* d’une colonne pour que Power BI Desktop sache comment traiter ses valeurs dans une visualisation.

Quand Power BI Desktop importe des données, il obtient d’autres informations en plus des données elles-mêmes, par exemple les noms de table et de colonne, et si les données constituent une clé primaire. Avec ces informations, Power BI Desktop émet des hypothèses pour vous procurer la meilleure expérience par défaut lors de la création d’une visualisation.
Par exemple, quand une colonne contient des valeurs numériques, Power BI Desktop part du principe que vous voudrez probablement agréger ces valeurs d’une façon ou d’une autre ; il les place donc dans la zone **Valeurs** du panneau **Visualisations**. Pour une colonne avec des valeurs de date et d’heure dans un graphique en courbes, Power BI Desktop part du principe que vous l’utiliserez sans doute comme axe de hiérarchie de temps.

Cependant, certains cas sont un peu plus complexes, comme quand il s’agit de géographie. Examinez le tableau suivant tiré d’une feuille de calcul Excel :

![Capture d’écran d’Excel montrant les données tabulaires à importer dans Power BI Desktop.](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop doit-il considérer les codes de la colonne **GeoCode** comme l’abréviation d’un pays ou d’un état ?  Cela n’est pas évident, car un code comme celui-ci peut représenter l’un ou l’autre. Par exemple, AL peut signifier Alabama ou Albanie, AR peut signifier Arkansas ou Argentine, et CA peut signifier Californie ou Canada. Cela a son importance quand nous dessinons notre champ Geocode sur une carte. 

Power BI Desktop doit-il afficher une carte du monde avec les pays en surbrillance ? Ou doit-il afficher une carte des États-Unis avec les états en surbrillance ?  Vous pouvez spécifier une catégorie de données pour les données comme celles-ci. La catégorisation des données affine les informations que Power BI Desktop peut utiliser pour fournir les meilleures visualisations.  

**Pour spécifier une catégorie de données**

1. Dans la vue **Rapport** ou **Données**, dans la liste **Champs**, sélectionnez le champ que vous souhaitez trier selon une catégorisation différente.
2. Sur le ruban, dans la zone **Propriétés** de l’onglet **Modélisation**, sélectionnez la flèche déroulante à côté de **Catégorie de données**.  Cette liste montre les différentes catégories de données que vous pouvez choisir pour votre colonne. Certaines options peuvent être désactivées si elles ne fonctionneront pas avec le type de données actuel de votre colonne.  Par exemple, si une colonne est d’un type de données date ou heure, Power BI Desktop ne vous permet pas de choisir des catégories de données géographiques. 
3. Sélectionnez la catégorie de votre choix.

   ![Capture d’écran de Power BI Desktop montrant le filtre Catégorie de données.](media/desktop-data-categorization/desktop-data-categorization.png)

Vous pouvez également être intéressé par le [filtrage géographique pour les applications mobiles Power BI](desktop-mobile-geofiltering.md).