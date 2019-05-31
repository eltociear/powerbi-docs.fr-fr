---
title: Limites de l’API REST de Power BI
description: L’API REST de Power BI présente les limites suivantes
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6699167cecebea5085eff4621c077096fd4c6c2e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385140"
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