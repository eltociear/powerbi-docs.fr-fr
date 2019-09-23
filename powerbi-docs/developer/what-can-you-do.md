---
title: Que peuvent faire les développeurs avec Power BI ?
description: Power BI offre un vaste éventail d’options pour les développeurs. Cela va de l’incorporation dans des visuels personnalisés aux jeux de données en streaming.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 03/15/2019
ms.openlocfilehash: d2e3ba69cde609638e54eaa1206714f0fb420d18
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61262666"
---
# <a name="what-can-developers-do-with-power-bi"></a>Que peuvent faire les développeurs avec Power BI ?

Les développeurs ont différentes possibilités pour inclure du contenu Power BI dans des applications, En tant que développeur, vous pouvez **incorporer avec Power BI**, utiliser des **visuels personnalisés** ou **envoyer (push) des données dans Power BI**.

## <a name="embedding-power-bi-content"></a>Incorporation de contenu Power BI

Le service Power BI (SaaS) et le service Power BI Embedded dans Azure (PaaS) comportent des API permettant d’incorporer des tableaux de bord et des rapports. Cette fonctionnalité signifie que vous pouvez accéder aux dernières fonctionnalités Power BI (tableaux de bord, passerelles et espaces de travail d’application, par exemple) pour incorporer votre contenu.

Vous pouvez passer par l’[outil de configuration de l’incorporation](https://aka.ms/embedsetup) pour démarrer et télécharger rapidement un exemple d’application.

Choisissez la solution qui vous convient :

* [L’incorporation pour vos clients](embedding.md#embedding-for-your-customers) permet d’incorporer des tableaux de bord et des rapports pour les utilisateurs qui n’ont pas de compte Power BI. Exécutez la solution [Incorporer pour vos clients](https://aka.ms/embedsetup/AppOwnsData).

* [L’incorporation pour votre organisation](embedding.md#embedding-for-your-organization) vous permet d’étendre le service Power BI. Exécutez la solution [Incorporer pour votre organisation](https://aka.ms/embedsetup/UserOwnsData).

![Exemple PBIE](media/what-can-you-do/what-can-you-do-02.png)

Pour en savoir plus sur l’incorporation avec Power BI, consultez [Incorporation avec Power BI](embedding.md).

## <a name="developing-custom-visuals"></a>Développement de visuels personnalisés

Vous pouvez utiliser des visuels personnalisés avec Power BI pour créer un type de visuel unique spécialement adapté à vous ou à votre entreprise. Souvent, ces visuels personnalisés sont créés par les développeurs. Ils sont créés quand la multitude de visuels inclus dans Power BI ne répondent pas exactement à vos besoins.

Les visuels personnalisés vous permettent de créer vos visuels à utiliser dans les rapports Power BI. Les visuels personnalisés sont écrits en TypeScript, un surensemble de JavaScript. TypeScript prend en charge certaines fonctionnalités avancées ainsi qu’un accès anticipé aux fonctionnalités ES6/ES7. Les styles de visuels sont gérés à l’aide de feuilles de style en cascade (CSS). Par souci pratique, nous utilisons le précompilateur LESS, qui prend en charge certaines fonctionnalités avancées, notamment l’imbrication, les variables, les conditions, les boucles et autres fonctionnalités. Si vous ne souhaitez pas utiliser ces fonctionnalités, vous pouvez écrire une feuille de style CSS brute dans le fichier LESS.

![Exemple de visuel personnalisé](media/what-can-you-do/powerbi-custom-visual-store.png)

Pour en savoir plus sur le développement de visuels personnalisés, consultez [Développement d’un visuel personnalisé Power BI](custom-visual-develop-tutorial.md).

## <a name="using-api-automation"></a>Utilisation de l’automatisation des API

Power BI présente des tableaux de bord interactifs, qui peuvent être créés et mis à jour à partir de différentes sources de données en temps réel. À l’aide d’un langage de programmation qui prend en charge les appels REST, vous pouvez créer des applications qui s’intègrent à un tableau de bord Power BI en temps réel. Vous pouvez également intégrer des vignettes et des rapports Power BI à des applications.

Les développeurs peuvent également générer leurs propres visualisations de données qui peuvent être utilisées dans des tableaux de bord et rapports interactifs.

![Exemple de données push](media/what-can-you-do/powerbi-push-data.png)

Pour savoir ce que vous pouvez faire avec les API Power BI, consultez [Comment les développeurs peuvent-ils se servir de l’API Power BI](overview-of-power-bi-rest-api.md) ?

## <a name="next-steps"></a>Étapes suivantes

[Incorporation avec Power BI](embedding.md)  

[Développement d’un visuel personnalisé Power BI](https://microsoft.github.io/PowerBI-visuals/docs/step-by-step-lab/developing-a-power-bi-custom-visual/)

[Comment les développeurs peuvent-ils se servir de l’API Power BI ?](overview-of-power-bi-rest-api.md)

[Centre développeurs Power BI](https://powerbi.microsoft.com/developers/)