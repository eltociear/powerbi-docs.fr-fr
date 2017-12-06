---
title: Utiliser une extraction dans Power BI Desktop
description: "Découvrez comment explorer les données d’une nouvelle page de rapport dans Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: e4655326b731c118265003ba1f530c5c62ac8bfa
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Utiliser une extraction dans Power BI Desktop
Une **extraction** dans **Power BI Desktop** vous permet de créer dans votre rapport une page qui se concentre sur une entité spécifique, telle qu’un fournisseur un client ou un fabricant. Dans cette page de rapport ciblée, les utilisateurs peuvent cliquer avec le bouton droit sur un point de données renvoyant à une autre page de rapport, et opérer une extraction vers la page ciblée pour obtenir les détails filtrés en fonction de ce contexte.

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Utilisation d’une extraction
Pour utiliser une **extraction**, créez une page de rapport contenant les visuels que vous souhaitez voir concernant le type d’entité pour lequel vous allez produire l’extraction. Par exemple, si vous souhaitez produire une extraction concernant des fabricants, vous pouvez créer une page d’extraction avec des visuels présentant le total des ventes, le nombre total d’unités fournies, les ventes par catégorie, les ventes par région, et ainsi de suite. Ainsi, lorsque vous opérez l’extraction vers cette page, les visuels ont spécifiquement trait au fabricant sur lequel vous avez cliqué et que vous avez sélectionné pour obtenir une extraction à son sujet.

Dans cette page d’extraction, dans la section **Champs** du volet **Visualisations**, faites glisser vers le puits **Filtres d’extraction** le champ à propos duquel vous souhaitez obtenir une extraction.

![](media/desktop-drillthrough/drillthrough_02.png)

Lorsque vous ajoutez un champ au puits **Filtres d’extraction**, **Power BI Desktop** crée automatiquement un visuel de bouton *Précédent*. Ce visuel devient un bouton dans les rapports publiés, qui permet aux utilisateurs consultant ceux-ci dans le **service Power BI** de revenir facilement à la page de rapport qu’ils consultaient précédemment (dans laquelle ils ont opéré leur sélection pour l’extraction).

![](media/desktop-drillthrough/drillthrough_03.png)

Étant donné que le bouton *Précédent* est une image, vous pouvez remplacer celle-ci par toute image de votre choix, qui continuera à fonctionner correctement en tant que bouton permettant aux utilisateurs du rapport de revenir à la page qu’ils consultaient précédemment. Pour utiliser votre propre image pour un bouton Précédent, placez simplement un visuel sur la page de l’extraction, sélectionnez le visuel, puis placez dessus le curseur du *bouton Précédent*. Votre image fonctionne ainsi en tant que bouton *Précédent*.

![](media/desktop-drillthrough/drillthrough_05.png)

Une fois votre page d’**extraction** terminée, quand des utilisateurs cliquent avec le bouton droit sur un point de données de votre rapport qui utilise le champ que vous avez placé dans le puits **Filtres d’extraction** sur votre page d’extraction, un menu contextuel s’affiche, qui permet aux utilisateurs d’opérer l’extraction vers cette page.

![](media/desktop-drillthrough/drillthrough_04.png)

Quand ils choisissent d’opérer l’extraction, la page est filtrée pour afficher les informations relatives au point de données sur lequel ils ont cliqué avec le bouton droit. Par exemple, s’ils ont cliqué avec le bouton droit sur un point de données concernant Contoso (un fabricant), puis choisi d’opérer une extraction, la page d’extraction vers laquelle ils sont dirigés est filtrée sur Contoso.

> [!NOTE]
> Seul le champ figurant dans le puits **Filtres d’extraction** est transmis à la page du rapport d’extraction. Aucune autre information contextuelle n’est transmise.
> 
> 

C’est tout ce que vous avez à faire pour utiliser une **extraction** dans vos rapports. Il s’agit d’un excellent moyen d’obtenir une vue développée des informations d’une entité que vous sélectionnez pour votre filtre d’extraction.

