---
title: Utiliser le langage naturel avec l’importation, Live Connect et DirectQuery
description: Dans cet article, nous examinons la façon dont la fonctionnalité Questions et réponses utilise les différents types de sources de données disponibles dans Power BI. Nous allons aussi examiner les concepts d’indexation et de mise en cache.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mohaali
ms.openlocfilehash: 85ecc5adc55daee86922c39e417db1cac5ba4a52
ms.sourcegitcommit: 0f807d3c74e5202b6e6a95fad49f2787928b9613
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706197"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>Utiliser le langage naturel avec l’importation, Live Connect et DirectQuery

La fonctionnalité Questions et réponses de Power BI vous permet d’obtenir rapidement des réponses à partir de vos données en utilisant un langage naturel pour poser des questions sur ces données. Cet article décrit l’utilisation de l’indexation et de la mise en cache pour améliorer les performances de chaque configuration prise en charge.

## <a name="what-data-sources-are-supported-in-qa"></a>Quelles sont les sources de données prises en charge dans la fonctionnalité Questions et réponses ?

La fonctionnalité Questions et réponses est prise en charge dans les configurations suivantes :

- Mode Importation
- Mode Live Connect : utilisation de jeux de données SQL Server Analysis Services, Azure Analysis Services ou Power BI locaux
- DirectQuery : Azure Synapse, Azure SQL et SQL Server 2019. Bien que d’autres sources puissent fonctionner en mode DirectQuery, nous ne les prenons pas en charge officiellement.

Par défaut, la fonctionnalité Questions et réponses est activée dans un rapport si vous utilisez le visuel correspondant. Une invite s’affiche si vous utilisez DirectQuery ou Live Connect. Vous pouvez activer ou désactiver explicitement les fonctionnalités de langage naturel pour un rapport en accédant aux options.

![Options de bureau Questions et réponses](media/qna-desktop-options.png)

Pour plus d’informations, consultez [Limitations de Questions et réponses dans Power BI](q-and-a-limitations.md).

## <a name="how-does-indexing-work-with-qa"></a>Comment l’indexation fonctionne avec Questions et réponses ?

Quand vous activez Questions et réponses, un index est créé pour fournir rapidement des commentaires en temps réel à l’utilisateur et faciliter l’interprétation des questions de l’utilisateur. La génération de cet index peut prendre un certain temps et intègre les éléments et limitations suivants.

- Tous les noms de colonnes et les tables sont insérés dans l’index, sauf s’il a été explicitement désactivé dans la section de l’outil Questions et réponses.
- Toutes les valeurs de texte de moins de 100 caractères sont indexées. Les valeurs de texte de plus de 100 caractères ne sont pas indexées. 
- Questions et réponses stocke un maximum de 5 millions de valeurs uniques dans son index. Si vous dépassez ce plafond, l’index ne contient pas toutes les valeurs potentielles, ce qui risque de réduire la précision des résultats que vous recevez de Questions et réponses.
- Si une erreur se produit pendant l’indexation, l’index reste dans un état partiel et est recréé lors de la prochaine actualisation, comme décrit dans la section suivante.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>Quelle est la fréquence à laquelle l’index est actualisé et mis en cache ?

Dans Power BI Desktop, l’index est créé au moment où vous utilisez Questions et réponses. Une petite icône s’affiche pour vous informer que l’index est en cours de création. Pendant ce temps, le chargement du visuel Questions et réponses, y compris des suggestions, peut prendre un certain temps.

Dans le service Power BI, l’index est recréé lors de la publication/republication et de l’actualisation. L’index Questions et réponses n’est pas toujours créé automatiquement et s’appuie parfois sur la demande pour optimiser l’actualisation du jeu de données. Pour DirectQuery, nous indexons les données une fois par jour au plus pour réduire l’impact sur la source DirectQuery.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez intégrer le langage naturel dans vos rapports de plusieurs façons. Pour plus d’informations, consultez les articles suivants :

* [Visuel de Questions et réponses](../visuals/power-bi-visualization-q-and-a.md)
* [Bonnes pratiques pour Questions et réponses](q-and-a-best-practices.md)
