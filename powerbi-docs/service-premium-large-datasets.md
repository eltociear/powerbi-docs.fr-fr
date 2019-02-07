---
title: Prise en charge de jeux de données volumineux dans Power BI Premium
description: Power BI Premium prend désormais en charge les jeux de données d’une taille maximale de 10 Go.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 941d4bc3d66ce8e636f730d5757b7215c978d582
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794833"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Prise en charge de jeux de données volumineux dans Power BI Premium

Power BI Premium prend en charge les téléchargements de fichiers Power BI Desktop (.pbix) d’une taille maximale de 10 Go. Une fois chargé, un jeu de données peut être actualisé jusqu'à une taille maximale de 12 Go. Pour utiliser un jeu de données volumineux, vous devez le publier sur un espace de travail affecté à la capacité Premium.
 
## <a name="best-practices"></a>Meilleures pratiques

Cette section décrit les recommandations relatives à l’utilisation de jeux de données volumineux.

**Les grands modèles peuvent être très gourmands en ressources** sur votre capacité. Nous recommandons au moins une référence SKU P1 pour tous les modèles supérieurs à 1 Go. Même si la publication de grands modèles dans des espaces de travail soutenus par des références (SKU) A jusqu’à A3 peut fonctionner, il n’en est pas de même pour leur actualisation.

Le tableau suivant décrit les références SKU recommandées pour différentes tailles de fichiers .pbix :

   |Référence SKU  |Taille de fichier .pbix   |
   |---------|---------|
   |P1    | < 3 Go        |
   |P2    | < 6 Go        |
   |P3, P4, P5    | jusqu’à 10 Go   |

La référence (SKU) A4 Power BI Embedded est égale à la référence P1, A5 = P2 et A6 = P3. Notez que la publication de grands modèles pour des références SKU A et EM peut retourner des erreurs qui ne sont pas spécifiques à l’erreur de limitation de taille de modèle dans la capacité partagée. Les erreurs d’actualisation pour les grands modèles dans les références SKU A et EM sont susceptibles de pointer vers des expirations de délai. Nous travaillons sur l’amélioration des messages d’erreur pour ces scénarios.

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
