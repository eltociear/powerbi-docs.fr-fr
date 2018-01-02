---
title: "Prise en charge de jeux de données volumineux dans Power BI Premium"
description: "Power BI Premium prend désormais en charge les jeux de données d’une taille maximale de 10 Go."
services: powerbi
documentationcenter: 
author: MarkMcGeeAtAquent
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: v-mamcge
ms.openlocfilehash: 82ac4382fe80d83b60705f135b50738718f28876
ms.sourcegitcommit: 7eb15c813a0d14322cb1316bb7aab23cbc13aae6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2017
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Prise en charge de jeux de données volumineux dans Power BI Premium

Power BI Premium prend en charge les téléchargements de fichiers Power BI Desktop (.pbix) d’une taille maximale de 10 Go. Pour utiliser un jeu de données volumineux, vous devez le publier sur un espace de travail affecté à la capacité Premium.
 
## <a name="best-practices"></a>Meilleures pratiques

Cette section décrit les recommandations relatives à l’utilisation de jeux de données volumineux.

**Les modèles volumineux peuvent être très gourmands en ressources** sur votre capacité. Nous vous recommandons d’utiliser au moins une référence SKU P1 pour tous les modèles supérieurs à 1 Go. Le tableau suivant décrit les références SKU recommandées pour différentes tailles de fichiers .pbix :


   |Référence SKU  |Taille de fichier .pbix   |
   |---------|---------|
   |P1    | < 3 Go        |
   |P2    | < 6 Go        |
   |P3    | jusqu’à 10 Go   |



**Vos fichiers .pbix représentent des données dans un état fortement compressé**. Les données seront probablement développées plusieurs fois lors de leur chargement en mémoire, et dès lors peuvent être encore développées plusieurs fois au moment de l’actualisation.

**L’actualisation planifiée de jeux de données volumineux peut nécessiter beaucoup de temps** et de ressources. Par conséquent, ne planifiez pas un trop grand nombre d’actualisations en même temps. Notez également que le délai d’expiration pour les tâches d’actualisation planifiée a été doublé à quatre heures pour tous les jeux de données dans cette capacité.

**Le chargement d’état initial des jeux de données volumineux peut être long** si la dernière utilisation du jeu de données remonte à quelque temps, car le modèle est chargé dans la mémoire de votre capacité Premium. Une barre de chargement indique la progression pour les rapports dont le chargement est plus long.

**Si vous supprimez l’espace de travail à partir de la capacité Premium**, le modèle ainsi que tous les rapports et tableaux de bord associés ne fonctionnent pas.

**Les contraintes de mémoire par requête et de temps étant plus importantes dans la capacité Premium**, nous vous recommandons vivement d’utiliser des filtres et des segments afin de limiter l’affichage des éléments visuels au strict nécessaire.

## <a name="next-steps"></a>Étapes suivantes
[Qu’est-ce que Power BI Premium ?](service-premium.md)  
[Notes de publication de Power BI Premium](service-premium-release-notes.md)  
[Livre blanc sur Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Planification d’un livre blanc sur le déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy)  
[Activation de l’essai Pro prolongé](service-extended-pro-trial.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
