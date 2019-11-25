---
title: API Power BI utilisant la stratégie de rétention automatique des données en temps réel
description: En savoir plus sur la stratégie de rétention automatique dans le service Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: cdbf50ee5078eaade7794242b3ed522e043cab22
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265852"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Stratégie de rétention automatique des données en temps réel

La stratégie de conservation automatique du service Power BI est un paramètre de chaîne de requête qui active une stratégie de conservation par défaut pour nettoyer automatiquement les anciennes données tout en conservant un flux constant de nouvelles données vers votre tableau de bord. La première stratégie de conservation est appelée *FIFO (First in, First out)* . Quand elle est activée, les données sont collectées dans une table jusqu’à atteindre 200 000 lignes. Quand les données dépassent 200 000 lignes, les lignes les plus anciennes sont supprimées du jeu de données. Ceci permet de conserver entre 200 000 et 210 000 lignes contenant seulement les données les plus récentes.  
  
<center>

![stratégie de rétention](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Les stratégies de rétention sont activées lorsque vous créez vos jeux de données pour le première fois. Il vous suffit d’ajouter le paramètre de requête « defaultRetentionPolicy » à votre appel de jeux de données POST et de lui affecter la valeur *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}