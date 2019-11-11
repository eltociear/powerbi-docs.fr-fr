---
title: Limites de l’API REST de Power BI
description: L’API REST de Power BI présente les limites suivantes
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 730123ba86e00e944a543feda77308c545a5b53e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875930"
---
# <a name="power-bi-rest-api-limitations"></a>Limites de l’API REST de Power BI  
  
**Lignes POST**
  
* 75 colonnes au maximum
* 75 tables au maximum
* 10 000 lignes au maximum par demande de lignes POST uniques  
* 1 000 000 lignes ajoutées par heure et par jeu de données  
* 5 demandes de lignes POST en attente au maximum par jeu de données  
* 120 demandes de lignes POST par minute et par jeu de données
* Avec un tableau de 250 000 lignes ou plus, 120 demandes de lignes POST par heure et par jeu de données
* 200 000 lignes au maximum stockées par table dans un jeu de données FIFO
* 5 000 000 lignes au maximum stockées par table dans un jeu de données « sans stratégie de rétention »  
* 4 000 caractères par valeur de colonne de type chaîne dans une opération de lignes POST
  
## <a name="see-also"></a>Voir aussi

[Restrictions et limites du service Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Vue d’ensemble de l’API REST Power BI](https://docs.microsoft.com/rest/api/power-bi/)