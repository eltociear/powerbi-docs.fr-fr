---
title: Utiliser une extraction dans Power BI Desktop
description: Découvrez comment explorer les données d’une nouvelle page de rapport dans Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d0c78643d285099f7b7856704ac7ee350ff9f93a
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2018
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Utiliser une extraction dans Power BI Desktop
Une **extraction** dans **Power BI Desktop** vous permet de créer dans votre rapport une page qui se concentre sur une entité spécifique, par exemple, un fournisseur, un client ou un fabricant. Dans cette page de rapport ciblée, les utilisateurs peuvent cliquer avec le bouton de droite sur un point de données renvoyant à une autre page de rapport et opérer une extraction vers la page ciblée pour obtenir les détails filtrés en fonction de ce contexte.

![utilisation d’une extraction](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Utilisation d’une extraction
1. Pour utiliser une **extraction**, créez une page de rapport contenant les visuels que vous souhaitez voir concernant le type d’entité pour lequel vous allez produire une extraction. 

    Par exemple, si vous souhaitez produire une extraction concernant des fabricants, vous pouvez créer une page d’extraction avec des visuels présentant le total des ventes, le nombre total d’unités fournies, les ventes par catégorie, les ventes par région, et ainsi de suite. Ainsi, lorsque vous opérez l’extraction vers cette page, les visuels ont spécifiquement trait au fabricant que vous avez sélectionné.

2. Dans cette page d’extraction, dans la section **Champs** du volet **Visualisations**, faites glisser le champ à propos duquel vous souhaitez obtenir une extraction dans le puits **Filtres d’extraction**.

    ![puits d’extraction](media/desktop-drillthrough/drillthrough_02.png)

    Lorsque vous ajoutez un champ au puits **Filtres d’extraction**, **Power BI Desktop** crée automatiquement un visuel de bouton *Précédent*. Ce visuel devient un bouton dans les rapports publiés, qui permet aux utilisateurs consultant ceux-ci dans le **service Power BI** de revenir facilement à la page de rapport qu’ils consultaient précédemment (dans laquelle ils ont opéré leur sélection pour l’extraction).

    ![image d’extraction](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Utiliser votre propre image pour un bouton Précédent    
 Étant donné que le bouton Précédent est une image, vous pouvez la remplacer par toute image de votre choix, qui continuera à fonctionner en tant que bouton Précédent permettant aux consommateurs du rapport de revenir à la page d’origine.

1. Dans l’onglet **Accueil**, cliquez sur **Image**, recherchez votre image, puis placez-la dans la page d’extraction.
2. Sélectionnez votre nouvelle image sur la page d’extraction et sous la section Format de l’image, définissez le curseur **Lien** sur Activé et définissez le **Type** sur **Retour**. Votre image fonctionne désormais comme un bouton Précédent.

    ![utiliser l’image pour revenir en arrière](media/desktop-drillthrough/drillthrough_05.png)

    Une fois votre page **Extraction** terminée et une fois que les utilisateurs cliquent avec le bouton droit sur un point de données de votre rapport qui utilise le champ que vous avez placé dans le puits **Filtres d’extraction**, un menu contextuel s’affiche prenant en charge l’extraction vers cette page.

    ![menu d’extraction](media/desktop-drillthrough/drillthrough_04.png)

    Lorsque les consommateurs du rapport choisissent d’opérer l’extraction, la page est filtrée pour afficher les informations relatives au point de données sur lequel ils ont cliqué avec le bouton de droite. Par exemple, s’ils ont cliqué avec le bouton de droite sur un point de données concernant Contoso (un fabricant), puis choisi d’opérer une extraction, la page d’extraction vers laquelle ils sont dirigés est filtrée sur Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Passer tous les filtres dans l’extraction

À partir de la version de mai 2018 de **Power BI Desktop**, vous pouvez passer tous les filtres appliqués dans la fenêtre d’extraction. Par exemple, vous avez peut-être sélectionné une seule catégorie de produits et de visuels filtrés pour cette catégorie, puis sélectionné l’extraction. Vous aimeriez peut-être savoir à quoi ressemble l’extraction avec tous ces filtres appliqués.

Pour conserver tous les filtres appliqués, dans la section **Extraction** du volet **Visualisations**, il suffit de définir le bouton bascule **Passer tous les filtres** sur **activé**. 

![conserver tous les filtres](media/desktop-drillthrough/drillthrough_06.png)

Dans les versions de **Power BI Desktop** antérieures à mai 2018, le comportement équivaut à avoir ce même bouton bascule défini sur **désactivé**.

Lorsque vous extrayez un visuel, vous pouvez voir les filtres qui ont été appliqués comme résultat du visuel source avec les filtres temporaires appliqués. Dans la fenêtre d’extraction, ces filtres temporaires apparaissent en italique. 

![filtres temporaires en italique](media/desktop-drillthrough/drillthrough_07.png)

Notez que vous pouvez effectuer cette opération avec les pages d’info-bulles, mais vous vivrez une drôle d’expérience (l’info-bulle vous semblerait ne pas fonctionner correctement), donc celle-ci n’est pas recommandée.

C’est tout ce que vous avez à faire pour utiliser une **extraction** dans vos rapports. Il s’agit d’un excellent moyen d’obtenir une vue développée des informations d’une entité que vous sélectionnez pour votre filtre d’extraction.

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Utilisation de segments Power BI Desktop](desktop-slicers.md)

