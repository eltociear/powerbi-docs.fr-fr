---
title: Cartes choroplèthes dans Power BI
description: Documentation sur la création de cartes choroplèthes dans Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/05/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e7fa98be039093015e1b19ba8bf20f1368658a43
ms.sourcegitcommit: 212fb4a46af3e434a230331f18456c6a49a408fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907815"
---
# <a name="filled-maps-choropleth-in-power-bi"></a>Cartes choroplèthes dans Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

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
Ce tutoriel utilise le [fichier PBIX de l’exemple Vente et marketing](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).
1. Dans la section supérieure gauche de la barre de menus, sélectionnez **Fichier** > **Ouvrir**
   
2. Recherchez votre copie du **fichier PBIX de l’exemple Vente et marketing**.

1. Ouvrez le **fichier PBIX de l’exemple Vente et marketing** dans la vue Rapport ![Capture d’écran de l’icône Vue Rapport](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Sélectionner ![Capture d’écran de l’onglet jaune.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) pour ajouter une nouvelle page.


## <a name="create-a-basic-filled-map"></a>Créer une carte choroplèthe simple
Dans cette vidéo, Kim crée une carte de base et la convertit en carte choroplèthe.
   > [!NOTE]
   > Cette vidéo utilise une version antérieure de Power BI Desktop.
   > 
   > 

[VIDEO https://www.youtube.com/embed/ajTPGNpthcg ]

### <a name="create-a-filled-map"></a>Créer une carte choroplèthe
1. Dans le volet Champs, sélectionnez le champ **Géo** \> **État**.    

   ![coche jaune en regard de State (État)](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Convertissez le graphique](power-bi-report-change-visualization-type.md) en carte choroplèthe. Notez que **État** figure maintenant dans **Emplacement**. Bing Cartes utilise le champ dans **Emplacement** pour créer la carte.  L’emplacement peut être différents endroits valides : pays, état, région, ville, code postal ou autre code, etc. Bing Cartes fournit des formats de cartes choroplèthes pour de nombreux emplacements dans le monde. À défaut d’entrée valide pour l’emplacement, Power BI ne peut pas créer la carte choroplèthe.  

   ![modèles avec l’icône de carte choroplèthe mis en évidence](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Filtrez la carte pour afficher uniquement la zone continentale des États-Unis.

   a.  À gauche du volet Visualisations, recherchez le volet **Filtres** . Développez-le s’il est réduit

   b.  Pointez sur **State** (État) et sélectionnez la flèche de développement  
   ![filtres de niveau visuel indiquant State(All) ](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Cochez la case **All** et décochez la case **AK**.

   ![liste déroulante State avec les options All et AK non sélectionnées](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Sélectionnez l’icône en forme de rouleau pour ouvrir le volet Mise en forme et choisissez **Couleurs des données**.

    ![Volet Mise en forme affichant l’option Couleurs des données](media/power-bi-visualization-filled-maps-choropleths/power-bi-colors-data.png)

5. Sélectionnez les trois points verticaux et choisissez **Mise en forme conditionnelle**.

    ![Bouton de mise en forme conditionnelle Couleurs des données](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional.png)

6. Utilisez l’écran **Couleur par défaut - Couleurs des données** pour déterminer comment votre carte choroplèthe sera ombrée. Les options à votre disposition incluent quel champ choisir pour la base de l’ombrage et comment appliquer l’ombrage. Dans cet exemple, nous utilisons le champ **SalesFact** > **Sentiment**, et nous définissons l’orange pour la valeur la plus basse du sentiment et le bleu pour la valeur la plus élevée. Les valeurs comprises entre la valeur maximale et la valeur minimale seront des nuances d’orange et de bleu. L’illustration en bas de l’écran affiche la plage des couleurs qui seront utilisées. 

    ![Volet des couleurs par défaut avec Sentiment sélectionné](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-field.png)

7. La carte choroplèthe est en rouge et vert. Le rouge représente les indices de sentiment bas et le vert représente les indices de sentiment élevés (sentiment plus positif).  Pour afficher des détails supplémentaires, faites glisser un champ dans la zone Info-bulles.  Ici, nous avons ajouté **SalesFact** > **Sentiment gap** (Écart de sentiment). La mise en surbrillance de l’État de Idaho (ID) indique que l’écart de sentiment est faible, à 6.
   ![carte choroplèthe affichant des info-bulles Idaho](media/power-bi-visualization-filled-maps-choropleths/power-bi-idaho-filled-map.png)

10. [Enregistrez le rapport](../service-report-save.md).

Power BI vous donne un large contrôle sur l’apparence de votre carte choroplèthe. Familiarisez-vous avec ces contrôles des couleurs des données jusqu’à ce que vous atteigniez l’aspect souhaité. 

## <a name="highlighting-and-cross-filtering"></a>Mise en surbrillance et filtrage croisé
Pour plus d’informations sur le volet Filtres, consultez [Ajouter un filtre à un rapport](../power-bi-report-add-filter.md).

La mise en surbrillance d’un emplacement sur une carte choroplèthe entraîne le filtrage croisé des autres visualisations dans la page du rapport, et vice versa.

1. Commencez par enregistrer ce rapport en sélectionnant **Fichier > Enregistrer**. 

2. Copiez la carte choroplèthe à l’aide de Ctrl+C.

3. En bas du canevas du rapport, sélectionnez l’onglet **Sentiment** pour ouvrir la page de rapport Sentiments.

    ![Onglet Sentiment sélectionné](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Déplacez et redimensionnez les visualisations dans la page afin de libérer de la place, puis collez (Ctrl+V) la carte choroplèthe du rapport précédent. (Voir les images suivantes)

   ![Carte choroplèthe ajoutée à la page Sentiments](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Sur la carte choroplèthe, sélectionnez un État.  Cela met en surbrillance croisée et applique un filtrage croisé aux autres visualisations sur la page. La sélection de **Texas**, par exemple, effectue un filtrage croisé des cartes et une sélection croisée du graphique à barres. À partir de là, je sais que le sentiment est de 75 et que le Texas se trouve dans la région centrale n° 23.   
   ![Texas sélectionné](media/power-bi-visualization-filled-maps-choropleths/power-bi-filter.png)
2. Sélectionnez un point de données sur le graphique en courbes VanArsdel - Sentiment par mois. Cela permet de filtrer la carte choroplèthe pour afficher l’indice de sentiment pour VanArsdel et pas pour la concurrence de VanArsdel.  
   ![nouvelles couleurs](media/power-bi-visualization-filled-maps-choropleths/power-bi-vanarsdel.png)

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
Les données cartographiques peuvent être ambiguës.  Par exemple, il existe un Paris en France, mais aussi un Paris au Texas. Vos données géographiques sont probablement stockées dans des colonnes distinctes (une colonne pour les noms de ville, une colonne pour les noms d’État ou de région, etc.), ce qui peut empêcher Bing de distinguer les deux Paris. Si votre jeu de données contient déjà des données de latitude et de longitude, Power BI comporte des champs spéciaux permettant de lever toute ambiguïté dans les données cartographiques. Faites simplement glisser le champ qui contient vos données de latitude vers la zone Visualisations \> Latitude.  Faites la même chose pour vos données de longitude.    

![volets Visualisations et Champs](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Si vous disposez des autorisations nécessaires pour modifier le jeu de données dans Power BI Desktop, regardez cette vidéo en cas de doute sur les cartes.

[VIDEO https://www.youtube.com/embed/Co2z9b-s_yM ]

Si vous n’avez pas accès aux données de latitude et de longitude, mais que vous avez accès en modification au jeu de données, [suivez ces instructions pour mettre à jour votre jeu de données](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Pour plus d’informations sur les visualisations de carte, consultez [Tips and tricks for map visualizations](../power-bi-map-tips-and-tricks.md) (Trucs et astuces pour les visualisations de carte).

## <a name="next-steps"></a>Étapes suivantes

[Carte de formes](desktop-shape-map.md)

[Types de visualisation dans Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)