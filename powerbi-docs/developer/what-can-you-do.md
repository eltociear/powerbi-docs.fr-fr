---
title: Que peuvent faire les développeurs avec Power BI ?
description: Power BI offre un vaste éventail d’options pour les développeurs. Cela va de l’incorporation dans des visuels personnalisés aux jeux de données en streaming.
services: powerbi
author: markingmyname
ms.author: maghan
ms.date: 05/03/2018
ms.topic: overview
ms.service: powerbi
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 473052ee652c1fd6e68294efdbd7334cbb2df714
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810963"
---
# <a name="what-can-developers-do-with-power-bi"></a>Que peuvent faire les développeurs avec Power BI ?

Les développeurs ont différentes possibilités pour inclure du contenu Power BI dans des applications, notamment **l’incorporer avec Power BI**, utiliser des **visuels personnalisés** ou **envoyer (push) des données dans Power BI**.

## <a name="embedding"></a>Incorporation
Le service Power BI (SaaS) et le service Power BI Embedded dans Azure (PaaS) comportent des API permettant d’incorporer des tableaux de bord et des rapports. Vous avez donc accès aux dernières fonctionnalités de Power BI (tableaux de bord, passerelles et espaces de travail d’application, par exemple) pour incorporer votre contenu.

![Exemple PBIE](media/what-can-you-do/what-can-you-do-01.png)

## <a name="develop-custom-visuals"></a>Développer des visuels personnalisés
Les visuels personnalisés vous permettent de créer vos propres visuels à utiliser dans les rapports Power BI. Les visuels personnalisés sont écrits en TypeScript, un surensemble de JavaScript. TypeScript prend en charge certaines fonctionnalités avancées ainsi qu’un accès anticipé aux fonctionnalités ES6/ES7. Les styles de visuels sont gérés à l’aide de feuilles de style en cascade (CSS). Dans un souci de commodité, nous utilisons le précompilateur LESS, qui prend en charge certaines fonctionnalités avancées, notamment l’imbrication, les variables, les conditions, les boucles, etc. Si vous ne souhaitez pas utiliser ces fonctionnalités, vous pouvez simplement écrire une feuille de style CSS brute dans le fichier LESS.

![Exemple de visuel personnalisé](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Transmettre des données à Power BI
Vous pouvez utiliser l’API Power BI pour envoyer des données dans un jeu de données. Cela vous permet d’ajouter une ligne à une table à l’intérieur d’un jeu de données. Les nouvelles données peuvent ensuite être reflétées dans des vignettes sur un tableau de bord et dans des visuels à l’intérieur de votre rapport.

![Exemple de données push](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Étapes suivantes
[Incorporation avec Power BI](embedding.md)  
[Publier des visuels personnalisés dans l’Office Store](office-store.md)  
[Transmettre des données à un tableau de bord](walkthrough-push-data.md)
