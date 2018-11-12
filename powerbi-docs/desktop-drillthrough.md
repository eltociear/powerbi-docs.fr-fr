---
title: Utiliser une extraction dans Power BI Desktop
description: Découvrez comment explorer les données d’une nouvelle page de rapport dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4989e981c3f39a637b3bb4927c427be0005c7776
ms.sourcegitcommit: b343e44dbafc0b718c564402593d4b6e3a8ce97c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51027434"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Utiliser une extraction dans Power BI Desktop
Une **extraction** dans **Power BI Desktop** vous permet de créer dans votre rapport une page qui se concentre sur une entité spécifique, par exemple, un fournisseur, un client ou un fabricant. Les utilisateurs peuvent cliquer avec le bouton droit sur un point de données dans d’autres pages du rapport. Ils peuvent ensuite extraire la page ciblée pour obtenir les détails filtrés en fonction de ce contexte.

![Utilisation d’une extraction](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Utilisation d’une extraction
1. Pour utiliser l’**extraction**, créez une page de rapport contenant les visuels souhaités pour le type d’entité pour lequel vous allez produire une extraction. 

    Par exemple, supposons que vous souhaitez fournir une extraction pour les fabricants. Vous pouvez alors créer une page d’extraction avec des visuels présentant le total des ventes, le nombre total d’unités fournies, les ventes par catégorie, les ventes par région, et ainsi de suite. Ainsi, lorsque vous opérez l’extraction vers cette page, les visuels ont spécifiquement trait au fabricant que vous avez sélectionné.

2. Dans cette page d’extraction, dans la section **Champs** du volet **Visualisations**, faites glisser le champ pour lequel vous souhaitez permettre une extraction dans le puits **Filtres d’extraction**.

    ![Puits d’extraction](media/desktop-drillthrough/drillthrough_02.png)

    Lorsque vous ajoutez un champ au puits **Filtres d’extraction**, **Power BI Desktop** crée automatiquement un visuel de bouton *Précédent*. Ce visuel devient un bouton dans les rapports publiés. Les utilisateurs qui consomment votre rapport dans le **service Power BI** peut utiliser ce bouton pour revenir à la page du rapport dont ils viennent.

    ![Image d’extraction](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Utiliser votre propre image pour un bouton Précédent    
 Étant donné que le bouton Précédent est une image, vous pouvez remplacer l’image de ce visuel par n’importe quelle image de votre choix. Il continuera à fonctionner comme un bouton Précédent afin que les consommateurs de rapports puissent revenir à la page d’origine. Pour utiliser votre propre image pour un bouton Précédent, procédez comme suit :

1. Dans l’onglet **Accueil**, sélectionnez **Image**. Recherchez ensuite votre image et placez-la sur la page d’extraction.

2. Sélectionnez votre nouvelle image sur la page d’extraction. Sous la section **Mettre en forme l’image**, définissez le curseur **Lien** sur **Activé**, puis définissez le **Type** sur **Précédent**. Votre image fonctionne désormais comme un bouton Précédent.

    ![Utiliser l’image pour revenir en arrière](media/desktop-drillthrough/drillthrough_05.png)

    
     Les utilisateurs peuvent maintenant cliquer avec le bouton droit sur un point de données dans votre rapport et afficher un menu contextuel qui prend en charge l’extraction vers cette page. 

    ![Menu d’extraction](media/desktop-drillthrough/drillthrough_04.png)

    Lorsque les consommateurs du rapport choisissent d’effectuer l’extraction, la page est filtrée pour afficher les informations relatives au point de données sur lequel ils ont cliqué avec le bouton droit. Par exemple, supposons qu’ils ont cliqué avec le bouton droit sur un point de données concernant Contoso (un fabricant) et l’ont sélectionné pour l’extraction. La page d’extraction à laquelle ils accèdent est filtrée sur Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Passer tous les filtres dans l’extraction

À partir de la version de mai 2018 de **Power BI Desktop**, vous pouvez passer tous les filtres appliqués dans la fenêtre d’extraction. Par exemple, vous ne pouvez sélectionner qu’une seule catégorie de produits et de visuels filtrés pour cette catégorie avant de sélectionner l’extraction. Vous aimeriez peut-être savoir à quoi ressemble l’extraction avec tous ces filtres appliqués.

Pour conserver tous les filtres appliqués, dans la section **Extraction** du volet **Visualisations**, définissez le bouton bascule **Passer tous les filtres** sur **activé**. 

![Conserver tous les filtres](media/desktop-drillthrough/drillthrough_06.png)

Dans les versions de **Power BI Desktop** publiées avant mai 2018, le comportement est le même que si ce bouton bascule était défini sur **désactivé**.

Lorsque vous extrayez un visuel, vous pouvez voir les filtres qui ont été appliqués comme résultat du visuel source avec les filtres temporaires appliqués. Dans la fenêtre d’extraction, ces filtres temporaires apparaissent en italique. 

![Filtres temporaires en italique](media/desktop-drillthrough/drillthrough_07.png)

Vous pouvez effectuer cette opération avec les pages d’info-bulles, mais vous vivrez une expérience étrange, parce que l’info-bulle semblera ne pas fonctionner correctement. Pour cette raison, il n’est pas recommandé de procéder ainsi avec les info-bulles.

## <a name="add-a-measure-to-drillthrough"></a>Ajouter une mesure à l’extraction

En plus du passage de tous les filtres dans la fenêtre d’extraction, vous pouvez ajouter une mesure ou une colonne numérique totalisée dans la zone d’extraction. Faites glisser le champ d’extraction dans la carte d’extraction pour l’appliquer. 

![Ajouter une mesure à l’extraction](media/desktop-drillthrough/drillthrough_08.png)

Lorsque vous ajoutez une mesure (ou une colonne numérique totalisée), vous pouvez extraire sur la page si le champ est utilisé dans la zone *Valeur* d’un visuel.

C’est tout ce que vous avez à faire pour utiliser une **extraction** dans vos rapports. C’est un excellent moyen d’obtenir une vue développée des informations d’une entité que vous avez sélectionnée pour votre filtre d’extraction.

## <a name="next-steps"></a>Étapes suivantes

Les articles suivants pourraient également vous intéresser :

* [Utilisation de segments Power BI Desktop](visuals/desktop-slicers.md)

