---
title: Cartes choroplèthes dans Power BI
description: Documentation sur la création de cartes choroplèthes dans Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2fa8fa5248ee1e4330804205b2cedb64021b1913
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839819"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Cartes choroplèthes dans Power BI
Une carte choroplèthe utilise des ombrages, des teintes ou des motifs pour représenter proportionnellement les variations d’une valeur entre des zones géographiques ou des régions.  Visualisez rapidement les écarts relatifs grâce aux ombrages allant du clair (moins fréquent/plus bas) au foncé (plus fréquent/plus élevé).    

![carte des États-Unis](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>Ce qui est envoyé à Bing
De par son intégration à Bing, Power BI fournit des coordonnées cartographiques par défaut (processus appelé « géocodage »). Lorsque vous créez une visualisation de carte dans le service Power BI ou Power BI Desktop, les données contenues dans les compartiments **Emplacement**, **Latitude** et **Longitude** (utilisées pour créer cette visualisation) sont envoyées à Bing.

Vous ou votre administrateur devrez peut-être mettre à jour votre pare-feu pour autoriser l’accès aux URL que Bing utilise pour le géocodage.  Il s’agit des URL suivantes :
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Pour plus d’informations sur les données envoyées à Bing et pour obtenir des conseils afin d’augmenter vos chances d’obtenir un géocodage correct, consultez [Trucs et astuces pour les visualisations de carte](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Quand faut-il utiliser une carte choroplèthe ?
Les cartes choroplèthes sont conseillées :

* pour afficher des données quantitatives sur une carte ;
* pour représenter les relations et les modèles spatiaux ;
* quand vos données sont normalisées ;
* quand vous travaillez avec des données socio-économiques ;
* quand les régions définies sont de grande taille ;
* pour obtenir une vue d’ensemble de la répartition entre les zones géographiques.

### <a name="prerequisites"></a>Conditions préalables
- Service Power BI ou Power BI Desktop
- Exemple Vente et marketing

Pour la suite, le didacticiel utilise le service Power BI, et non Power BI Desktop.

## <a name="create-a-basic-filled-map"></a>Créer une carte choroplèthe simple
Dans cette vidéo, Kim crée une carte de base et la convertit en carte choroplèthe.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="get-data-and-add-a-new-blank-page-to-the-report"></a>Obtenir des données et ajouter une nouvelle page vierge au rapport
1. Pour créer votre propre carte choroplèthe, [téléchargez l’exemple Vente et marketing](../sample-datasets.md) en vous connectant à Power BI et en sélectionnant  **Obtenir les données \> Exemples \> Ventes et marketing\> Se connecter**. Ou obtenez l’application **Power BI Ventes et marketing** sur appsource.com. 

2. Ouvrez le rapport Ventes et marketing.

   ![Ouverture du rapport Ventes et marketing](media/power-bi-visualization-filled-maps-choropleths/power-bi-report-canvas.png)
3. Power BI ouvre le rapport. Sélectionnez **Modifier le rapport** pour ouvrir le rapport en [Mode Édition](../service-interact-with-a-report-in-editing-view.md).

4. Ajoutez une nouvelle page en sélectionnant le signe « + » jaune en bas du canevas de rapport.

    ![Onglets Rapport](media/power-bi-visualization-filled-maps-choropleths/power-bi-new-page.png)

### <a name="create-a-filled-map"></a>Créer une carte choroplèthe
1. Dans le volet Champs, sélectionnez le champ **Géo** \> **État**.    

   ![coche jaune en regard de State (État)](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
5. [Convertissez le graphique](power-bi-report-change-visualization-type.md) en carte choroplèthe. Notez que **État** figure maintenant dans **Emplacement**. Bing Cartes utilise le champ dans **Emplacement** pour créer la carte.  L’emplacement peut être n’importe quel emplacement valide : pays, État, région, ville, code postal ou autre code, etc. Bing Cartes fournit des formats de cartes choroplèthes pour de nombreux emplacements dans le monde. À défaut d’entrée valide pour l’emplacement, Power BI ne peut pas créer la carte choroplèthe.  

   ![modèles avec l’icône de carte choroplèthe mis en évidence](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Filtrez la carte pour afficher uniquement la zone continentale des États-Unis.

   a.  En bas du volet Visualisations, recherchez la zone **Filtres** .

   b.  Pointez sur **State** (État) et cliquez sur la flèche de développement  
   ![filtres de niveau visuel indiquant State(All) ](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Cochez la case **All** et décochez la case **AK**.

   ![liste déroulante State avec les options All et AK non sélectionnées](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. Sélectionnez **SalesFact** \> **Sentiment** pour l’ajouter à **Saturation de la couleur**. Le champ dans **Saturation de la couleur** détermine l’ombrage de la carte.  
   ![Sentiment dans le puits du champ Saturation de la couleur](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map.png)
8. La carte choroplèthe est en rouge et vert. Le rouge représente les indices de sentiment bas et le vert représente les indices de sentiment élevés (sentiment plus positif).  Ici, j’ai mis en surbrillance l’État du Wyoming (WY) et je vois que l’indice de sentiment est très bon (74).  
   ![boîte de dialogue noire indiquant l’état et le sentiment](media/power-bi-visualization-filled-maps-choropleths/power-bi-wy.png)
9. [Enregistrez le rapport](../service-report-save.md).
##    <a name="adjust-the-color-formatting"></a>Ajuster la mise en forme des couleurs
Power BI vous donne un large contrôle sur l’apparence de votre carte choroplèthe.
1. Ouvrez le volet de mise en forme en sélectionnant l’icône en forme de rouleau.

    ![Volet de mise en forme](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-colors.png)

2. Sélectionnez **Couleurs des données** pour afficher les options de couleur.
3. Définissez les couleurs Minimum et Maximum sur jaune et bleu. Ajoutez des valeurs Minimum et Maximum, en fonction de vos données. Amusez-vous avec ces contrôles jusqu'à ce que vous obteniez l’apparence souhaitée. 

    ![couleurs non divergentes](media/power-bi-visualization-filled-maps-choropleths/power-bi-color.png)

## <a name="highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisé
Pour plus d’informations sur le volet Filtres, consultez [Ajouter un filtre à un rapport](../power-bi-report-add-filter.md).

La mise en surbrillance d’un emplacement sur une carte choroplèthe entraîne le filtrage croisé des autres visualisations sur la page du rapport et vice versa.

1. Commencez par enregistrer ce rapport en sélectionnant **Fichier > Enregistrer**. 

2. Copiez la carte choroplèthe à l’aide de Ctrl+C.

3. En bas du canevas du rapport, sélectionnez l’onglet **Sentiment** pour ouvrir la page de rapport Sentiments.

    ![Onglet Sentiment sélectionné](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Déplacez et redimensionnez les visualisations dans la page afin de libérer de la place, puis collez (Ctrl+V) la carte choroplèthe du rapport précédent.

   ![Carte choroplèthe ajoutée à la page Sentiments](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Sur la carte choroplèthe, sélectionnez un État.  Cela met en surbrillance les autres visualisations sur la page. La sélection de **Texas**, par exemple, montre que le sentiment est de 74 ; Texas se trouve dans la région centrale \#23.   
   ![Texas sélectionné](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Sélectionnez un point de données sur le graphique en courbes VanArsdel - Sentiment par mois. Cela permet de filtrer la carte choroplèthe pour afficher l’indice de sentiment pour VanArsdel et pas pour la concurrence de VanArsdel.  
   ![nouvelles couleurs](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
Les données cartographiques peuvent être ambiguës.  Par exemple, il existe un Paris en France, mais aussi un Paris au Texas. Vos données géographiques sont probablement stockées dans des colonnes distinctes (une colonne pour les noms de ville, une colonne pour les noms d’État ou de région, etc.), ce qui peut empêcher Bing de distinguer les deux Paris. Si votre jeu de données contient déjà des données de latitude et de longitude, Power BI comporte des champs spéciaux permettant de lever toute ambiguïté dans les données cartographiques. Faites simplement glisser le champ qui contient vos données de latitude vers la zone Visualisations \> Latitude.  Faites la même chose pour vos données de longitude.    

![volets Visualisations et Champs](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Si vous disposez des autorisations nécessaires pour modifier le jeu de données dans Power BI Desktop, regardez cette vidéo en cas de doute sur les cartes.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Si vous n’avez pas accès aux données de latitude et de longitude, mais que vous avez accès en modification au jeu de données, [suivez ces instructions pour mettre à jour votre jeu de données](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Pour plus d’informations sur les visualisations de carte, consultez [Tips and tricks for map visualizations](../power-bi-map-tips-and-tricks.md) (Trucs et astuces pour les visualisations de carte).

## <a name="next-steps"></a>Étapes suivantes

[Carte de formes](desktop-shape-map.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)