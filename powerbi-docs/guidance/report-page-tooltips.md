---
title: Étendre des visuels avec des info-bulles de page de rapport
description: Conseils d’utilisation des info-bulles de page de rapport.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 826af7b224b901b6dc9f3926260b1d920836a792
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76040360"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Étendre des visuels avec des info-bulles de page de rapport

Cet article s’adresse à vous en tant qu’auteur de rapports Power BI. Il fournit des suggestions et des recommandations pour créer des [info-bulles de page de rapport](../desktop-tooltips.md).

## <a name="suggestions"></a>Suggestions

Les info-bulles de page de rapport peuvent améliorer l’expérience des utilisateurs de vos rapports. Les info-bulles de page permettent aux utilisateurs de rapports d’obtenir rapidement et efficacement des insights plus approfondis à partir d’un visuel. Il est possible de les associer à différents objets de rapport :

- **Visuels :** Vous pouvez configurer individuellement les visuels qui révèlent votre info-bulle de page. Chaque visuel peut ne révéler aucune info-bulle, révéler les info-bulles visuelles par défaut (configurées dans le volet des champs visuels) ou utiliser une info-bulle de page spécifique.
- **En-têtes de visuel :** Vous pouvez configurer des visuels spécifiques pour présenter une info-bulle de page. Les utilisateurs de vos rapports peuvent alors révéler l’info-bulle de page quand ils passent leur curseur au-dessus de l’icône d’en-tête d’un visuel. Veillez à informer vos utilisateurs sur cette icône.

> [!NOTE]
> Un visuel de rapport peut uniquement révéler une info-bulle de page quand des filtres sont compatibles avec la conception du visuel. Par exemple, un visuel qui regroupe par _produit_ est compatible avec une page d’info-bulle qui filtre par _produit_.
>
> Les info-bulles de page ne prennent pas en charge l’interactivité. Si vous souhaitez que les utilisateurs de vos rapports puissent interagir, créez plutôt une [page d’extraction](../desktop-drillthrough.md).
>
> Les visuels personnalisés ne prennent pas en charge les info-bulles de page.

Voici quelques suggestions de scénarios de conception :

- [Perspective différente](#different-perspective)
- [Ajouter un détail](#add-detail)
- [Ajouter de l’aide](#add-help)

### <a name="different-perspective"></a>Perspective différente

Une info-bulle de page permet de visualiser les mêmes données que le visuel source. Elle utilise soit le même visuel et les mêmes groupes de tableaux croisés dynamiques, soit des types de visuels différents. Les info-bulles de page peuvent également appliquer des filtres différents de ceux appliqués au visuel source.

L’exemple suivant montre ce qui se produit lorsque l’utilisateur du rapport passe son curseur au-dessus de la valeur **EnabledUsers**. Le contexte du filtre de la valeur est Yammer en novembre 2018.

![Un visuel de matrice présente une grille des valeurs regroupées par année et par mois sur les lignes. L’utilisateur du rapport a pointé son curseur sur une valeur unique. Une info-bulle de page est apparue.](media/report-page-tooltips/suggestion-different-perspective.png)

Une info-bulle de page est révélée. Elle présente un visuel de données différent (graphique en courbes et histogramme groupé) et applique un filtre temporel contrasté. Notez que le contexte du filtre du point de données est novembre 2018. Pourtant, l’info-bulle de page présente la tendance sur _une année complète_.

### <a name="add-detail"></a>Ajouter un détail

Une info-bulle de page peut présenter des détails supplémentaires et ajouter un contexte.

L’exemple suivant montre ce qui se produit lorsque l’utilisateur du rapport pointe son curseur sur la valeur **Moyenne des points de violation**, pour le code postal 98022.

![Un visuel de table présente une grille de valeurs et la table contient trois colonnes. Une info-bulle de page est apparue.](media/report-page-tooltips/suggestion-add-details.png)

Une info-bulle de page est révélée. Elle présente des statistiques et attributs spécifiques pour le code postal 98022.

### <a name="add-help"></a>Ajouter de l’aide

Les en-têtes de visuel peuvent être configurés pour révéler des info-bulles de page. Vous pouvez ajouter une documentation d’aide à une info-bulle de page en utilisant des zones de texte parfaitement mises en forme. Il est également possible d’ajouter des images et des formes.

Il est intéressant de noter que les boutons, les images, les zones de texte et les formes peuvent également révéler une info-bulle de page d’en-tête de visuel.

L’exemple suivant montre ce qui se produit quand l’utilisateur du rapport passe son curseur au-dessus de l’[icône d’en-tête de visuel](../desktop-visual-elements-for-reports.md).

![L’utilisateur d’un rapport a pointé son curseur sur l’icône d’en-tête de visuel (point d’interrogation). Une info-bulle richement mise en forme est apparue.](media/report-page-tooltips/suggestion-add-help.png)

Une info-bulle de page est révélée. Elle présente du texte parfaitement mis en forme dans quatre zones de texte ainsi qu’une forme (ligne). L’info-bulle de page apporte de l’aide en décrivant chaque acronyme affiché dans le visuel.

## <a name="recommendations"></a>Recommandations

Au moment de la conception du rapport, nous vous recommandons d’adopter les pratiques suivantes :

- **Format de page :** Configurez votre info-bulle de page de sorte à ce qu’elle soit petite. Vous pouvez utiliser l’option **Info-bulle** intégrée (320 pixels de large, 240 pixels de haut). Ou vous pouvez définir des dimensions personnalisées. Veillez à ne pas utiliser un format de page trop grand, car il risque de masquer les visuels dans la page source.
- **Mode Page :** Dans le concepteur de rapports, définissez le mode Page sur **Taille réelle** (la valeur par défaut du mode Page est **Ajuster à la page**). De cette façon, vous pouvez voir la vraie taille de l’info-bulle de page pendant sa conception.
- **Style :** Envisagez de concevoir votre info-bulle de page pour qu’elle utilise le même thème et le même style que le rapport. Ainsi, les utilisateurs ont l’impression d’être dans le même rapport. Vous pouvez également concevoir un style complémentaire pour vos info-bulles et veiller à l’appliquer à toutes les info-bulles de page.
- **Filtres d’info-bulle :** Affectez des filtres à l’info-bulle de page afin de pouvoir afficher un aperçu réaliste du résultat pendant la conception. Veillez à supprimer ces filtres avant de publier votre rapport.
- **Visibilité de la page :** Masquez toujours les pages d’info-bulle : les utilisateurs ne doivent pas y accéder directement.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Créer des info-bulles basées sur des pages de rapport dans Power BI Desktop](../desktop-tooltips.md)
- [Personnalisation des info-bulles dans Power BI Desktop](../desktop-custom-tooltips.md)
- [Utiliser des visuels pour améliorer des rapports Power BI](../desktop-visual-elements-for-reports.md)
- Vidéo Guy in a Cube : [Info-bulle de page de rapport Power BI : guide pratique pour en créer une dans Power BI Desktop](https://www.youtube.com/watch?v=URTA7JZsAtw)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
