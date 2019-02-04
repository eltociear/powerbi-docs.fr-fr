---
title: Interaction avec une carte ArcGIS partagée avec vous
description: Utilisation d’une carte ArcGis en mode lecture comme consommateur de rapport Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: mihart
ms.openlocfilehash: 1de6dfc89d3b6be815c85e99b776fc9fe4d423fd
ms.sourcegitcommit: 2954de034f5e1be655dd02cc756ff34f126d3034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55234577"
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>Interaction avec des cartes ArcGIS dans Power BI
Cette rubrique est écrite du point de vue d’une personne qui *utilise* une carte ArcGIS dans le service Power BI, dans Power BI Desktop ou dans la version mobile de Power BI. Une fois qu’un créateur a partagé une carte ArcGIS avec vous, il existe de nombreuses façons d’interagir avec celle-ci.  Pour en savoir plus sur la création d’une carte ArcGIS, consultez le [tutoriel sur les cartes ArcGIS par ESRI](../visuals/power-bi-visualization-arcgis.md).

L’association des cartes ArcGIS et de Power BI porte la cartographie au-delà de la simple présentation de points sur une carte, pour accéder à un nouveau niveau. Les options disponibles pour les cartes de base, les types d’emplacement, les thèmes, les styles de symbole et les couches de référence créent des visualisations de cartes informatives exceptionnelles. L’association des couches de données faisant autorité (comme des données de recensement) sur une carte avec l’analyse spatiale permet une compréhension approfondie des données dans votre visualisation.

> [!TIP]
> GIS signifie système d’information géographique.
> 

L’exemple utilisé examine les ventes de l’année précédente par ville, et utilise une carte classique avec des bulles pour représenter la taille ainsi qu’une couche de référence pour les revenus moyens des ménages. La carte contient 3 épingles et un rayon indiquant le temps de transport (en violet).

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> Visitez la page d’[ESRI sur Power BI](https://www.esri.com/powerbi) pour découvrir de nombreux exemples et consulter des témoignages. Puis consultez la [page de prise en main d’ArcGIS Maps d’ESRI pour Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm).
> 
> 

<br/>

## <a name="user-consent"></a>Consentement de l’utilisateur
La première fois qu’un collègue partage une carte ArcGIS avec vous, Power BI affiche une invite. ArcGIS Maps for Power BI est fourni par Esri (www.esri.com) et son utilisation est soumise aux conditions générales et à la politique de confidentialité d’Esri. Les utilisateurs Power BI désireux d’utiliser les visuels ArcGIS Maps pour Power BI doivent valider la boîte de dialogue de consentement.

## <a name="selection-tools"></a>Outils de sélection
ArcGIS Maps pour Power BI offre trois modes de sélection. Il n’est pas possible de sélectionner plus de 250 points de données à la fois.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) Sélectionne des points de données individuels.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) Dessine un rectangle sur la carte et sélectionne les points de données qu’il contient. Utilisez la touche Ctrl pour sélectionner plusieurs zones rectangulaires.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) Autorise l’utilisation de limites ou de polygones dans les couches de référence pour sélectionner des points de données.

<br/>

## <a name="interacting-with-an-arcgis-map"></a>Interaction avec une carte ArcGIS
Les fonctionnalités disponibles varient selon que vous êtes le *créateur* (la personne qui a créé la carte) ou l’*utilisateur* (celui qui a partagé la carte ArcGIS avec vous). Si vous interagissez avec une carte ArcGIS en tant qu’utilisateur (en [mode Lecture](end-user-reading-view.md)), voici les actions disponibles.

* Si vous êtes consommateur Premium avec des autorisations d’*affichage*, vous pouvez [afficher les données qui ont servi à créer la visualisation](end-user-show-data.md), vous [abonner](end-user-subscribe.md), afficher la carte en [mode Focus ou Plein écran](end-user-focus.md), [afficher le contenu associé](end-user-related.md), [interagir avec les filtres](end-user-report-filter.md) définis par le *créateur du rapport*, [partager le rapport](../service-share-reports.md), etc.

* Comme avec les autres types de visualisation, en plus de l’ensemble des opérations que peut effectuer un consommateur Premium, un consommateur Power BI **Pro** peut [exporter les données sous-jacentes](../visuals/power-bi-visualization-export-data.md), [obtenir des métriques d’utilisation](../service-usage-metrics.md), enregistrer un copie et [publier sur le web](../service-publish-to-web.md), etc.

    
* Développez le volet **Filtres** pour explorer la carte à l’aide de filtres.   
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
<td>Service Power BI (app.powerbi.com)</td>
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

**Comment fonctionne ArcGIS Maps for Power BI ?**
ArcGIS Maps for Power BI est fourni par Esri (www.esri.com). L’utilisation d’ArcGIS Maps for Power BI est soumise aux [conditions générales](https://go.microsoft.com/fwlink/?LinkID=8263222) et à la [politique de confidentialité](https://go.microsoft.com/fwlink/?LinkID=826323) d’Esri. Les utilisateurs Power BI désireux d’utiliser les visuels d’ArcGIS Maps for Power BI doivent confirmer leur acceptation dans la boîte de dialogue de consentement (voir Consentement de l’utilisateur pour plus de détails).  L’utilisation d’ArcGIS Maps for Power BI est soumise aux conditions générales et à la politique de confidentialité d’Esri, auxquelles vous pouvez accéder à partir des liens dans la boîte de dialogue de consentement. Chaque utilisateur doit donner son consentement avant d’utiliser ArcGIS Maps for Power BI pour la première fois. Une fois que l’utilisateur accepte le consentement, les données liées au visuel sont envoyées aux services d’Esri au moins pour le géocodage, c’est-à-dire la transformation des informations de localisation en latitude et longitude qui peuvent être représentées sur une carte. Prenez en compte que toutes les données liées à la visualisation des données peuvent être envoyées aux services d’Esri. Esri fournit des services comme les cartes de base, l’analytique spatiale, le géocodage, etc. Le visuel ArcGIS Maps for Power BI interagit avec ces services à l’aide d’une connexion SSL protégée par un certificat fourni et géré par Esri. Des informations supplémentaires sur ArcGIS Maps for Power BI peuvent être obtenues dans la [page de produit ArcGIS Maps for Power BI](https://www.esri.com/powerbi) d’Esri.

**Power BI Plus**    
![Sélectionnez l’icône Plus pour vous inscrire ou vous connecter](media/power-bi-visualizations-arcgis/power-bi-plus.png)

Quand un utilisateur s’inscrit à un abonnement Plus offert par Esri via ArcGIS Maps for Power BI, il entre dans une relation directe avec Esri. Power BI n’envoie pas à Esri d’informations personnelles sur l’utilisateur. L’utilisateur se connecte à une application AAD fournie par Esri avec sa propre identité AAD et l’approuve. De cette façon, l’utilisateur partage ses informations personnelles directement avec Esri. Dès que l’utilisateur ajoute du contenu Plus à un visuel ArcGIS Maps for Power BI, les autres utilisateurs Power BI doivent également avoir un abonnement Plus d’Esri pour pouvoir afficher ou modifier ce contenu. 

Pour des questions techniques détaillées sur le fonctionnement d’ArcGIS Maps for Power BI d’Esri, contactez Esri via leur site de support.

**La carte ArcGIS ne s’affiche pas**    
Dans les services ou applications où ArcGIS Maps pour Power BI n’est pas disponible, la visualisation affiche un visuel vide avec le logo Power BI.

**Je ne vois pas toutes mes informations sur la carte**    
Quand vous géocodez la latitude/longitude sur la carte, jusqu’à 30 000 points de données peuvent s’afficher. Quand vous géocodez des points de données comme des codes postaux ou des adresses postales, seuls les 15 000 premiers points de données sont géocodés. Le géocodage des pays ou noms de lieux n’est pas soumis à la limite de 1500 adresses.

**L’utilisation d’ArcGIS Maps pour Power BI a-t-elle un coût ?**

ArcGIS Maps pour Power BI est disponible gratuitement pour tous les utilisateurs de Power BI. Il s’agit d’un composant fourni par **Esri**, dont l’utilisation est régie par les conditions générales et la politique de confidentialité établies par **Esri** comme indiqué précédemment dans cet article. Si vous vous abonnez à ArcGIS **Plus**, vous êtes soumis à des frais.

**J’obtiens un message d’erreur indiquant que mon cache est saturé**

Il s’agit d’un bogue qui est en cours de résolution.  En attendant, sélectionnez le lien qui apparaît dans le message d’erreur pour obtenir des instructions sur l’effacement de votre cache Power BI.

**Puis-je afficher mes cartes ArcGIS hors connexion ?**

Non, Power BI nécessite une connexion au réseau pour afficher les cartes.

## <a name="next-steps"></a>Étapes suivantes
Obtention d’aide : **Esri** fournit une [documentation complète](https://go.microsoft.com/fwlink/?LinkID=828772) sur l’ensemble des fonctionnalités d’**ArcGIS Maps pour Power BI**.

Vous pouvez poser des questions, accéder aux informations les plus récentes, signaler des problèmes et trouver des réponses sur le [fil de discussion de la communauté Power BI consacré à **ArcGIS Maps pour Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).


[Page du produit ArcGIS Maps pour Power BI](https://www.esri.com/powerbi)
