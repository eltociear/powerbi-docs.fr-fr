---
title: qu’est-ce qu’un tableau de bord Power BI ?
description: Les tableaux de bord sont une fonctionnalité clé du service Power BI.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: d0e1fdc79ae4bcd5946d82f2cbf7b929a47372cb
ms.sourcegitcommit: e8d924ca25e060f2e1bc753e8e762b88066a0344
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37136798"
---
# <a name="dashboards-in-power-bi-service"></a>Tableaux de bord dans le service Power BI

Un ***tableau de bord*** Power BI est une page unique, souvent appelée canevas, qui utilise des visualisations pour raconter une histoire. Comme il est limité à une seule page, un tableau de bord bien conçu contient uniquement les éléments les plus importantes de cette histoire.

![tableau de bord](media/service-dashboards/power-bi-dashboard2.png)

Les visualisations que vous voyez dans le tableau de bord sont appelées *vignettes* et sont *épinglées* au tableau de bord à partir de rapports. Si vous êtes novice dans Power BI, vous pouvez acquérir de bonnes bases en lisant [Power BI – Concepts de base](service-basic-concepts.md).

> [!NOTE]
> Les tableaux de bord sont une fonctionnalité du service Power BI et ne sont pas disponibles dans Power BI Desktop. Les tableaux de bord ne peuvent pas être créés sur les appareils mobiles, mais ils peuvent être [affichés et partagés](mobile-apps-view-dashboard.md).
> 
> 

Les visualisations sur un tableau de bord proviennent de rapports, et chaque rapport est basé sur un jeu de données. En fait, on peut considérer un tableau de bord comme une porte d’entrée dans les rapports et les jeux de données sous-jacents. La sélection d’une visualisation vous amène au rapport (et au jeu de données) utilisé(s) pour la créer.

![diagramme montrant la relation entre les tableaux de bord, les rapports, les jeux de données](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Avantages des tableaux de bord
Les tableaux de bord sont un moyen formidable pour surveiller votre activité, pour rechercher des réponses et pour afficher vos mesures les plus importantes en un coup d’œil. Les visualisations sur un tableau de bord peuvent provenir d’un ou plusieurs jeux de données sous-jacents et d’un ou plusieurs rapports sous-jacents. Un tableau de bord combine des données locales et issues du cloud, offrant ainsi une vue consolidée, quel que soit l’endroit où les données résident.

Un tableau de bord n’est pas simplement une belle image ; il est extrêmement interactif et hautement personnalisable ; et les vignettes sont mises à jour au fur et à mesure que les données sous-jacentes changent.

## <a name="dashboards-versus-reports"></a>Tableaux de bord et rapports
Les [rapports](service-reports.md) sont souvent confondus avec les tableaux de bord, car il s’agit également de canevas remplis avec des visualisations. Mais il existe quelques différences majeures.

| **Fonctionnalité** | **Tableaux de bord** | **Rapports** |
| --- | --- | --- |
| Pages |Une seule page |Une ou plusieurs pages |
| Sources de données |Un ou plusieurs rapports et un ou plusieurs jeux de données par tableau de bord |Un seul jeu de données par rapport |
| Disponible dans Power BI Desktop |Non |Oui, possibilité de créer et afficher des rapports dans Desktop |
| Épinglage |Possibilité d’épingler des visualisations existantes (vignettes) uniquement à partir du tableau de bord actuel à vos autres tableaux de bord. |Possibilité d’épingler des visualisations (sous forme de vignettes) à l’un de vos tableaux de bord. Possibilité d’épingler des pages entières de rapport à l’un de vos tableaux de bord. |
| S’abonner |Impossible de s’abonner à un tableau de bord |Possibilité de s’abonner à des pages de rapport |
| Filtrage |Impossible de filtrer ou découper |Différentes manières de filtrer, mettre en surbrillance et découper |
| Définir des alertes |Possibilité de créer des alertes pour vous envoyer un e-mail lorsque certaines conditions sont remplies |Non |
| Fonctionnalité |Possibilité de définir un tableau de bord comme votre tableau de bord « par défaut » |Impossible de créer un rapport par défaut |
| Requêtes en langage naturel |Disponible à partir du tableau de bord |Non disponible à partir de rapports |
| Possibilité de modifier le type de visualisation |Non. En fait, si le propriétaire d’un rapport change le type de visualisation dans le rapport, la visualisation épinglée sur le tableau de bord ne se met pas à jour |Oui |
| Possibilité d’afficher les tables et les champs sous-jacents d’un jeu de données |Non. Possibilité d’exporter les données, mais pas de voir les tables et les champs dans le tableau de bord. |Oui. Possibilité de voir les tables d’un jeu de données ainsi que les champs et les valeurs. |
| Possibilité de créer des visualisations |Limité à l’ajout de widgets au tableau de bord avec « Ajouter une vignette » |Possibilité de créer de nombreux d’éléments visuels de type différent, d’ajouter des éléments visuels personnalisés, de modifier des éléments visuels et bien plus encore avec les autorisations de modification |
| Personnalisation |Possibilité d’effectuer des opérations avec les visualisations (vignettes) : déplacement et réorganisation, redimensionnement, ajout de liens, attribution d’un nouveau nom, suppression, affichage plein écran, etc. Mais les données et les visualisations proprement dites sont en lecture seule. |En mode Lecture, vous pouvez publier, incorporer, filtrer, exporter, télécharger en tant que .pbix, afficher le contenu associé, générer des codes de QR, analyser dans Excel et bien plus encore.  En mode Édition, vous pouvez effectuer tout ce qui a été indiqué jusqu’ici et bien plus encore. |

## <a name="dashboard-creators-and-dashboard-consumers"></a>Créateurs et utilisateurs de tableaux de bord
Selon votre rôle, vous pouvez être amené à créer des tableaux de bord pour votre usage personnel ou pour les partager avec vos collègues. Vous souhaitez apprendre à créer et partager des tableaux de bord. Ou vous recevez peut-être des tableaux de bord d’autres personnes. Vous souhaitez apprendre à comprendre et interagir avec le tableau de bord.

Voici quelques rubriques, par rôle, qui vous aideront à démarrer.

Power BI Pro est nécessaire pour partager un tableau de bord et afficher un tableau de bord partagé.

### <a name="if-you-will-be-creating-and-sharing-dashboards"></a>Si vous devez créer et partager des tableaux de bord
* Utilisez l’un de nos exemples pour [créer un tableau de bord à partir d’un rapport](service-dashboard-create.md).
* Apprenez-en plus sur les [vignettes du tableau de bord](service-dashboard-tiles.md) et les différentes façons de les épingler sur un tableau de bord.
* Aidez vos utilisateurs en créant des tableaux de bord qui [fonctionnent correctement avec les requêtes en langage naturel Q&R](service-prepare-data-for-q-and-a.md) et avec des [informations rapides](service-insights-optimize.md).
* Découvrez les différentes méthodes disponibles pour [partager un tableau de bord avec des collègues](service-how-to-collaborate-distribute-dashboards-reports.md).

### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Si vous devez recevoir et utiliser des tableaux de bord
* Familiarisez-vous avec les tableaux de bord en effectuant une visite guidée d’un de nos [exemples de tableau de bord](sample-tutorial-connect-to-the-samples.md).
* Apprenez-en plus sur les [vignettes du tableau de bord](service-dashboard-tiles.md) et ce qui se produit lorsque vous sélectionnez une.
* Vous n’aimez pas l’aspect d’un tableau de bord ?  Vous pouvez [redimensionner, déplacer et renommer les vignettes](service-dashboard-edit-tile.md).
* Si vous souhaitez effectuer le suivi d’une vignette du tableau de bord et recevoir un e-mail lorsqu’elle atteint un certain seuil ? [Créer des alertes sur les vignettes](service-set-data-alerts.md).
* Amusez-vous en posant des questions à votre tableau de bord. Découvrez comment utiliser [Power BI Q&A](power-bi-tutorial-q-and-a.md) pour poser une question concernant vos données et obtenir la réponse sous la forme d’une visualisation.

> [!TIP]
> Si vous n’avez pas trouvé pas ce que vous cherchiez ici, utilisez la table des matières sur la gauche.
> 
> 

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI ?](power-bi-overview.md)  
[Power BI – Concepts de base](service-basic-concepts.md)  
[Qu’est-ce que Power BI Premium ?](service-premium.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

