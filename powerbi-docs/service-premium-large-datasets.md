---
title: Prise en charge de jeux de données volumineux dans Power BI Premium
description: Power BI Premium prend désormais en charge les jeux de données d’une taille maximale de 10 Go.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 416f022ee3c413c69650e6f1736cc94edcd58f13
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641249"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Prise en charge de jeux de données volumineux dans Power BI Premium

Power BI Premium prend en charge les téléchargements de fichiers Power BI Desktop (.pbix) d’une taille maximale de 10 Go. Une fois chargé, un jeu de données peut être actualisé jusqu'à une taille maximale de 12 Go. Pour utiliser un jeu de données volumineux, vous devez le publier sur un espace de travail affecté à la capacité Premium. Cet article décrit les considérations et les bonnes pratiques quand vous utilisez de grands jeux de données.

**Les grands modèles peuvent être très gourmands en ressources** sur votre capacité. Nous recommandons au moins une référence SKU P1 pour tous les modèles supérieurs à 1 Go. Le tableau suivant décrit les références SKU recommandées pour différentes tailles de fichiers .pbix :

   |Référence SKU  |Taille de fichier .pbix   |
   |---------|---------|
   |P1    | < 3 Go        |
   |P2    | < 6 Go        |
   |P3, P4, P5    | jusqu’à 10 Go |

**Vos fichiers .pbix représentent des données dans un état fortement compressé**. Les données seront probablement développées plusieurs fois lors de leur chargement en mémoire, et dès lors peuvent être encore développées plusieurs fois au moment de l’actualisation.

**L’actualisation planifiée de jeux de données volumineux peut nécessiter beaucoup de temps** et de ressources. Par conséquent, ne planifiez pas un trop grand nombre d’actualisations en même temps. Notez également que le délai d’expiration pour les tâches d’actualisation planifiée a été doublé à quatre heures pour tous les jeux de données dans cette capacité. Nous recommandons une [actualisation incrémentielle](service-premium-incremental-refresh.md), car elle est plus rapide, plus fiable et consomme moins de ressources.

**Le chargement d’état initial des jeux de données volumineux peut être long** si la dernière utilisation du jeu de données remonte à quelque temps, car le modèle est chargé dans la mémoire de votre capacité Premium. Une barre de chargement indique la progression pour les rapports dont le chargement est plus long.

**Si vous supprimez l’espace de travail à partir de la capacité Premium**, le modèle ainsi que tous les rapports et tableaux de bord associés ne fonctionnent pas.

**Les contraintes de mémoire par requête et de temps étant plus importantes dans la capacité Premium**, nous vous recommandons vivement d’utiliser des filtres et des segments afin de limiter l’affichage des éléments visuels au strict nécessaire.

**Étapes suivantes**

[Nouveautés de Power BI Premium](service-premium.md)
[Notes de publication de Power BI Premium](service-premium-release-notes.md)
[Livre blanc sur Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[Livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
