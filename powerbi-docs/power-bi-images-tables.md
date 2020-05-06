---
title: Afficher des images dans un tableau ou une matrice dans un rapport
description: Dans Power BI Desktop, vous créez une colonne avec des liens hypertexte vers des images. Ensuite, dans Power BI Desktop ou le service Power BI, vous pouvez ajouter ces liens hypertexte à une table, une matrice, un segment ou une carte à plusieurs lignes pour afficher l’image.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 95b1dc1be3421f19fa8220629ca2003469658480
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874481"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>Afficher des images dans un tableau, une matrice ou un segment dans un rapport

Un bon moyen d’améliorer vos rapports consiste à y ajouter des images. Les images statiques sur la page sont utiles dans certains cas. Mais parfois, vous souhaitez des images liées aux données de votre rapport. Cette rubrique explique comment afficher des images dans un tableau, une matrice, un segment ou une carte à plusieurs lignes. 

![Images d’URL dans un tableau](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>Ajouter des images à votre rapport

1. Créez une colonne avec les URL des images. Pour plus d’informations sur les conditions requises, consultez [Considérations](#considerations) plus loin dans cet article.

1. Sélectionnez cette colonne. Dans le ruban **Modélisation**, pour **Catégorie de données**, sélectionnez **URL d’image**.

    ![Définir la catégorie de données sur URL d’image](media/power-bi-images-tables/power-bi-set-url-image.png)

1. Ajoutez la colonne à une table, une matrice, un segment ou une carte à plusieurs lignes.

    ![Segment avec images](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>Considérations

- L’image doit être dans un des formats de fichier suivants : .bmp, .jpg, .jpeg, .gif, .png ou .svg
- L’URL doit être accessible de manière anonyme, et non sur un site qui requiert une connexion, comme SharePoint. Toutefois, si des images sont hébergées sur SharePoint ou OneDrive, vous pouvez obtenir un code incorporé qui pointe directement vers elles. 


## <a name="next-steps"></a>Étapes suivantes

[Mise en page et mise en forme](/learn/modules/visuals-in-power-bi/12-formatting)

[Fondamentaux pour les concepteurs dans le service Power BI](service-basic-concepts.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

