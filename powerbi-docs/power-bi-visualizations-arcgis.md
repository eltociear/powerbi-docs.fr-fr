---
title: "Interaction avec une carte ArcGIS partagée avec vous"
description: "Utilisation d’une carte ArcGis en mode lecture "
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: power bi, service, desktop, mobile
featuredvideoid: 
qualityfocus: monitoring
qualitydate: 06/23/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/23/2017
ms.author: mihart
ms.openlocfilehash: 511f01494410215451d9f77ff637c7cfce8e89b3
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>Interaction avec des cartes ArcGIS dans Power BI
Cette rubrique est écrite du point de vue d’une personne qui *utilise* une carte ArcGIS dans le service Power BI, dans Power BI Desktop ou dans la version mobile de Power BI. Une fois qu’un créateur a partagé une carte ArcGIS avec vous, il existe de nombreuses façons d’interagir avec celle-ci.  Pour en savoir plus sur la création d’une carte ArcGIS, consultez le [tutoriel sur les cartes ArcGIS par ESRI](power-bi-visualization-arcgis.md).

L’association des cartes ArcGIS et de Power BI porte la cartographie au-delà de la simple présentation de points sur une carte, pour accéder à un nouveau niveau. Les options disponibles pour les cartes de base, les types d’emplacement, les thèmes, les styles de symbole et les couches de référence créent des visualisations de cartes informatives exceptionnelles. L’association des couches de données faisant autorité (comme des données de recensement) sur une carte avec l’analyse spatiale permet une compréhension approfondie des données dans votre visualisation.

> [!TIP]
> SIG (ou GIS pour Geographic Information Science en anglais) signifie système d’informations géographiques.
> 
> 

L’exemple que nous utilisons est la carte ArcGIS créée dans le [tutoriel sur les cartes ArcGIS par ESRI](power-bi-visualization-arcgis.md). Il examine les ventes de l’année précédente par ville et utilise une carte classique avec des bulles pour représenter la taille et une couche de référence pour les revenus moyens des ménages. La carte contient 3 épingles et un rayon indiquant le temps de transport (en violet).

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> Visitez la page d’[ESRI sur Power BI](https://www.esri.com/powerbi) pour découvrir de nombreux exemples et consulter des témoignages. Puis consultez la [page de prise en main d’ArcGIS Maps d’ESRI pour Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm).
> 
> 

<br/>

## <a name="user-consent"></a>Consentement de l’utilisateur
La première fois qu’un collègue partage une carte ArcGIS avec vous, Power BI affiche une invite. ArcGIS Maps pour Power BI est fourni par [Esri](https://www.esri.com) et son utilisation est soumise aux conditions générales et à la politique de confidentialité d’Esri. Les utilisateurs Power BI désireux d’utiliser les visuels ArcGIS Maps pour Power BI doivent valider la boîte de dialogue de consentement.

## <a name="selection-tools"></a>Outils de sélection
ArcGIS Maps pour Power BI offre trois modes de sélection. Il n’est pas possible de sélectionner plus de 250 points de données à la fois.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) Sélectionne des points de données individuels.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) Dessine un rectangle sur la carte et sélectionne les points de données qu’il contient. Utilisez la touche Ctrl pour sélectionner plusieurs zones rectangulaires.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) Autorise l’utilisation de limites ou de polygones dans les couches de référence pour sélectionner des points de données.

<br/>

## <a name="interacting-with-an-arcgis-map"></a>Interaction avec une carte ArcGIS
Les fonctionnalités disponibles varient selon que vous êtes le *créateur* (la personne qui a créé la carte) ou l’*utilisateur* (celui qui a partagé la carte ArcGIS avec vous). Si vous interagissez avec une carte ArcGIS en tant qu’utilisateur (en [mode lecture](service-interact-with-a-report-in-reading-view.md)), voici les actions disponibles.

* Comme avec d’autres types de visualisation, vous pouvez les [épingler aux tableaux de bord](service-dashboard-pin-tile-from-report.md), [afficher](service-reports-show-data.md) et/ou [exporter les données sous-jacentes](power-bi-visualization-export-data.md) et afficher la carte en [mode Focus](service-focus-mode.md) et [Plein écran](service-fullscreen-mode.md).    
* Développez le volet **Filtres** pour explorer la carte à l’aide de filtres. Lorsque vous fermez le rapport, les filtres que vous avez appliqués ne sont pas enregistrés.    
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* Si la carte a une couche de référence, sélectionnez des emplacements pour afficher les détails dans une info-bulle. Dans l’image ci-dessous, Adams County a été sélectionné pour afficher des données de la couche de référence sur les revenus moyens des ménages que le créateur a ajoutée à la carte.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    Un graphique est également affiché. Sélectionnez une barre du graphique pour explorer les données. Vous voyez ici que 79 ménages d’Adams County gagnent plus de 200 000 $.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    Sélectionnez la flèche pour afficher des graphiques supplémentaires.
* Pointez sur les symboles d’emplacement sur la carte pour afficher les détails dans une info-bulle.     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > Vous devrez peut-être effectuer un zoom avant pour sélectionner un emplacement spécifique.  Sinon, si des emplacements se chevauchent, Power BI peut présenter plusieurs info-bulles. Sélectionnez les flèches pour vous déplacer entre les info-bulles.
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* Si le créateur a ajouté une couche Infographie à la carte ArcGIS, des données supplémentaires s’affichent dans le coin supérieur droit de la carte.  Par exemple, ici, le créateur de la carte a ajouté Children under 14 (Enfants de moins de 14).
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations
ArcGIS Maps pour Power BI est disponible dans les applications et services suivants :

<table>
<tr><th>Service/application</th><th>Disponibilité</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Oui</td>
</tr>
<tr>
<td>Service Power BI (PowerBI.com)</td>
<td>Oui</td>
</tr>
<tr>
<td>Applications mobiles Power BI</td>
<td>Oui</td>
</tr>
<tr>
<td>Publication Power BI sur le web</td>
<td>Non</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>Non</td>
</tr>
<tr>
<td>Incorporation au service Power BI (PowerBI.com)</td>
<td>Non</td>
</tr>
</table>

**La carte ArcGIS ne s’affiche pas**    
Dans les services ou applications où ArcGIS Maps pour Power BI n’est pas disponible, la visualisation affiche un visuel vide avec le logo Power BI.

**Je ne vois pas toutes mes adresses sur la carte**    
Lors du géocodage des adresses, seules les 1500 premières adresses sont géocodées. Le géocodage des pays ou noms de lieux n’est pas soumis à la limite de 1500 adresses.

**L’utilisation d’ArcGIS Maps pour Power BI a-t-elle un coût ?**

ArcGIS Maps pour Power BI est disponible gratuitement pour tous les utilisateurs de Power BI. Il s’agit d’un composant fourni par **Esri**, dont l’utilisation est régie par les conditions générales et la politique de confidentialité établies par **Esri** comme indiqué précédemment dans cet article.

**J’obtiens un message d’erreur indiquant que mon cache est saturé**

Il s’agit d’un bogue qui est en cours de résolution.  En attendant, sélectionnez le lien qui apparaît dans le message d’erreur pour obtenir des instructions sur l’effacement de votre cache Power BI.

**Puis-je afficher mes cartes ArcGIS hors connexion ?**

Non, Power BI nécessite une connexion au réseau pour afficher les cartes.

## <a name="next-steps"></a>Étapes suivantes
Obtenir de l’aide : **Esri** fournit une [documentation complète](https://go.microsoft.com/fwlink/?LinkID=828772) sur l’ensemble des fonctionnalités d’**ArcGIS Maps pour Power BI**.

Vous pouvez poser des questions, accéder aux informations les plus récentes, signaler des problèmes et trouver des réponses sur le [fil de discussion de la communauté Power BI consacré à **ArcGIS Maps pour Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).

Si vous avez des suggestions d’amélioration, ajoutez-les à la [liste d’idées concernant Power BI](https://ideas.powerbi.com).

[Page du produit ArcGIS Maps pour Power BI](https://www.esri.com/powerbi)

