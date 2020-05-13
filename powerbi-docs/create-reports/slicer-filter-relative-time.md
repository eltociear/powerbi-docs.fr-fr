---
title: Utilisation d’un segment ou d’un filtre d’heure relative dans Power BI
description: Découvrez comment utiliser un segment ou un filtre pour limiter les intervalles de temps relatif dans Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 31563e5bb5b91468b8913c3204e9d27607716c77
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279201"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Utilisation d’un segment et d’un filtre d’heure relative dans Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Avec les nouveaux scénarios d’actualisation rapide, la possibilité de filtrer sur une plus petite fenêtre de temps peut se révéler utile. À l’aide du segment ou du filtre d’heure relative, vous pouvez appliquer des filtres temporels à n’importe quelle colonne de date ou d’heure de votre modèle de données. Vous pouvez par exemple utiliser le segment d’heure relative pour n’afficher que les vues vidéo de la dernière minute ou de la dernière heure. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Exemple d’heure relative":::

Il n’est pas obligatoire d’utiliser la fonctionnalité conjointement avec celle [d’actualisation automatique de la page](../create-reports/desktop-automatic-page-refresh.md). Toutefois, de nombreux scénarios d’heure relative se marient bien avec cette dernière.  

> [!NOTE]
> Lorsque vous appliquez un filtre ou un segment d’heure relative au niveau de la page ou du rapport, tous les visuels de cette page ou de ce rapport sont filtrés sur exactement le même intervalle de temps, grâce à une heure *d’ancrage* partagée. Dans la mesure où les visuels peuvent présenter des durées d’exécution légèrement différentes, cette heure d’ancrage partagée permet de les synchroniser sur l’ensemble de la page ou du rapport. Pour plus d’informations sur [l’heure d’ancrage](#understanding-anchor-time), lisez la suite de l’article.

## <a name="turn-on-relative-time-preview"></a>Activation de la préversion de l’heure relative

Comme le filtre d’heure relative est en préversion, vous devez d’abord activer le commutateur de la fonctionnalité. Sélectionnez **Fichier** > **Options et paramètres** > **Options**. Sous **Paramètres globaux** > **Fonctionnalités d’évaluation**, sélectionnez **Filtre d’heure relative**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="Définition de l’option d’évaluation d’heure relative":::

## <a name="create-a-relative-time-slicer-or-filter"></a>Création d’un segment ou d’un filtre d’heure relative

Une fois que vous avez activé la fonctionnalité, vous pouvez glisser-déplacer le champ de date ou d’heure vers la zone de champs d’un segment ou la zone de dépôt du volet Filtres. 

### <a name="create-a-slicer"></a>Création d’un segment

1. Faites glisser un champ de date ou d’heure sur le canevas.

2. Sélectionnez le type de visualisation **Segment**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Création d’un segment d’heure":::

### <a name="create-a-filter"></a>Créer un filtre
 
- Faites glisser un champ de date ou d’heure dans le volet Filtres, pour **ce visuel**, **cette page** ou **toutes les pages**.

### <a name="set-relative-time"></a>Définition de l’heure relative 

Ensuite, remplacez le type de filtre par **Heure relative**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Remplacement par heure relative":::
 
Voici le résultat dans un segment :

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Heure relative dans un segment":::

Voici le résultat dans une carte de filtre : 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Heure relative dans un filtre":::
 
Avec ce nouveau type de filtre, vous avez la possibilité de filtrer sur la période **Dernière**, **Prochaine** ou **Actuelle** : 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Choix de la période dernière, prochaine ou actuelle":::
 
Spécifiez la fenêtre de temps en entrant un nombre entier et une unité de temps : **Minutes** ou **Heures**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Choix entre minutes et heures":::

Si vous devez économiser l’espace sur le canevas, vous pouvez également créer le filtre d’heure relative sous la forme d’une carte de filtre dans le volet Filtres.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Définition de l’heure relative dans un filtre":::
 
## <a name="understanding-anchor-time"></a>Fonctionnement de l’heure d’ancrage

Lorsqu’un filtre est appliqué au niveau de la page ou du rapport, tous les visuels de cette page ou de ce rapport sont synchronisés sur exactement le même intervalle de temps. Ces requêtes sont toutes émises par rapport à une heure appelée *heure d’ancrage*. L’heure d’ancrage est automatiquement actualisée dans les conditions suivantes :

- Chargement initial de la page
- Actualisation manuelle
- Actualisation automatique de la page ou détection de modifications
- Modification du modèle

### <a name="anchor-time-exceptions"></a>Exceptions de l’heure d’ancrage

- Le filtrage d’heure relative avec un visuel Questions et réponses ne s’appuie pas sur cette heure d’ancrage tant que ce visuel n’a pas été converti en visuel standard. En revanche, les autres visuels d’IA, comme les influenceurs clés et l’arborescence hiérarchique, sont synchronisés avec l’heure d’ancrage. 
- Par ailleurs, les filtres et segments de date relative ne s’appuient pas sur l’heure d’ancrage, sauf en présence de filtres d’heure relative. Si un filtre de date relative et un filtre d’heure relative se trouvent sur la même page, le filtre de date relative respecte l’heure d’ancrage.

## <a name="limitations-and-considerations"></a>Considérations et limitations

Voici les limitations et considérations qui s’appliquent actuellement au segment et au filtre d’heure relative.

- **Considérations relatives aux fuseaux horaires** : les modèles de données de Power BI n’incluent pas d’informations de fuseau horaire. Ces modèles peuvent stocker des heures, mais sans indication de leur fuseau horaire. Le segment et le filtre sont toujours basés sur l’heure UTC (temps universel coordonné). Si vous définissez un filtre dans un rapport et que vous l’envoyez à un collègue qui se trouve dans un autre fuseau horaire, vous voyez tous les deux les mêmes données. Sauf si vous ou votre collègue vous situez dans le fuseau horaire UTC, vous devez tous deux tenir compte du décalage temporel que vous rencontrez. Utilisez l’éditeur de requêtes pour convertir à l’heure UTC les données capturées dans un fuseau horaire local.
- Ce nouveau type de filtre est pris en charge dans Power BI Desktop, le service Power BI, Power BI Embedded et les applications mobiles Power BI. Toutefois, il existe quelques limitations de prise en charge connues :

    - Il n’est pas pris en charge par le biais de l’API Incorporer.
    - Il n’est pas pris en charge pour la publication sur le web.

- **Mise en cache des requêtes** : nous exploitons le cache du client. Supposons que vous spécifiiez « dernière minute », puis « 5 dernières minutes », puis que vous reveniez à « dernière minute ». Dans la situation actuelle, vous verrez alors les mêmes résultats qu’à la première exécution, sauf si vous actualisez la page ou qu’elle s’actualise automatiquement.

## <a name="next-steps"></a>Étapes suivantes

- [Utilisation d’un segment et d’un filtre de date relative dans Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Segments dans Power BI](../visuals/power-bi-visualization-slicers.md)
