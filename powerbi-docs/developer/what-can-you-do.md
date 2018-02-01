---
title: "Que peuvent faire les développeurs avec Power BI ?"
description: "Power BI offre un vaste éventail d’options pour les développeurs. Cela va de l’incorporation dans des visuels personnalisés aux jeux de données en streaming."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 07/20/2017
ms.author: maghan
ms.openlocfilehash: b310562ac31694f398a659018743b8fa7aa46e35
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="what-can-developers-do-with-power-bi"></a>Que peuvent faire les développeurs avec Power BI ?
Power BI offre un vaste éventail d’options pour les développeurs. Cela va de l’incorporation dans des visuels personnalisés aux jeux de données en streaming.

## <a name="embedding"></a>Incorporation
Le service Power BI et Power BI Embedded dans Azure s’assemblent afin d’offrir une seule API pour incorporer vos tableaux de bord et rapports. Cela signifie que vous disposez d’une surface d’API, d’un ensemble cohérent de fonctionnalités et de l’accès aux dernières fonctionnalités de Power BI telles que des tableaux de bord, des passerelles et des espaces de travail d’application lors de l’incorporation de votre contenu. Pour plus d’informations, voir [Incorporation avec Power BI](embedding.md).

![](media/what-can-you-do/powerbi-embed-sample.png)

## <a name="custom-visuals"></a>Éléments visuels personnalisés
Les visuels personnalisés vous permettent de créer vos propres visuels à utiliser dans les rapports Power BI. Les visuels personnalisés sont écrits en TypeScript, qui est un sur-ensemble de JavaScript prenant en charge certaines fonctionnalités avancées et un accès en avant-première aux fonctionnalités de ES6/ES7. Les styles de visuels sont gérés à l’aide de feuilles de style en cascade (CSS). Pour votre facilité, nous utilisons le précompilateur LESS qui prend en charge certaines fonctionnalités avancées, telles que l’imbrication, les variables, les mixins, les conditions, les boucles, etc. Si vous ne souhaitez pas utiliser ces fonctionnalités, vous pouvez simplement écrire une feuille de style CSS brute dans le fichier LESS.

Pour plus d’informations sur la façon de développer et publier un visuel personnalisé, voir [Publier des visuels personnalisés dans l’Office Store](office-store.md).

![](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Transmettre des données à Power BI
Vous pouvez utiliser l’API Power BI pour envoyer des données dans un jeu de données. Cela vous permet d’ajouter une ligne à une table à l’intérieur d’un jeu de données. Les nouvelles données peuvent ensuite être reflétées dans des vignettes sur un tableau de bord et dans des visuels à l’intérieur de votre rapport.

Pour plus d’informations, voir [Transmettre des données à un tableau de bord](walkthrough-push-data.md).

## <a name="next-steps"></a>Étapes suivantes
[Incorporation avec Power BI](embedding.md)  
[Comment migrer le contenu d’une collection d’espaces de travail Power BI Embedded vers Power BI](migrate-from-powerbi-embedded.md)  
[Dépôt Git d’API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)  
[Dépôt Git de C# pour Power BI ](https://github.com/Microsoft/PowerBI-CSharp)  
[Publier des visuels personnalisés dans l’Office Store](office-store.md)  
[Dépôt Git de visuels Power BI](https://github.com/Microsoft/PowerBI-visuals)  
[Exemple de JavaScript incorporé](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Livre blanc sur Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

