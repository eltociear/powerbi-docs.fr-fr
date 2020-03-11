---
title: Éviter les pages blanches lors de l’impression de rapports paginés
description: Conseils pour la conception de rapports paginés afin d’éviter les pages vierges lors de l’impression.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 349459b95a815a52665e50687554f81f90a9c81b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920836"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Éviter les pages blanches lors de l’impression de rapports paginés

Cet article s’adresse à vous en tant qu’auteur de [rapports paginés](../paginated-reports/paginated-reports-report-builder-power-bi.md) Power BI. Il fournit des recommandations pour vous aider à éviter les pages vierges lorsque votre rapport est exporté vers un format de page physique (par exemple, PDF ou Microsoft Word) ou imprimé.

## <a name="page-setup"></a>Mise en page

Les propriétés de taille de page de rapport déterminent l’orientation, les dimensions et les marges de la page. Accédez à ces propriétés de rapport en procédant comme suit :

- À l’aide de la **page de propriétés** du rapport : Cliquez avec le bouton droit sur la zone gris foncé à l’extérieur du canevas du rapport, puis sélectionnez _Propriétés du rapport_.
- À l’aide du volet [**Propriétés** ](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): Cliquez sur la zone gris foncé à l’extérieur du canevas du rapport pour sélectionner l’objet de rapport. Assurez-vous que le volet **Propriétés** est affiché.

La page **Mise en page** de la **page des propriétés** du rapport fournit une interface conviviale pour afficher et mettre à jour les propriétés de mise en page.

![Image montrant la fenêtre Propriétés du rapport, avec la page Mise en page en surbrillance.](media/report-paginated-blank-page/report-page-setup-properties.png)

Vérifiez que toutes les propriétés de taille de page sont correctement configurées :

|Propriété|Recommandation|
|---------|---------|
|Unités de page|Sélectionnez les unités appropriées : pouces ou centimètres.|
|Orientation|Sélectionnez l’option appropriée : portrait ou paysage.|
|Format de papier|Sélectionnez un format de papier ou affectez des valeurs de largeur et de hauteur personnalisées.|
|Marges|Définissez les valeurs appropriées pour les marges gauche, droite, haut et bas.|
|||

## <a name="report-body-width"></a>Largeur du corps du rapport

Les propriétés de taille de page déterminent l’espace disponible pour les objets de rapport. Les objets de rapport peuvent représenter des régions de données, des visualisations de données ou d’autres éléments de rapport.

La sortie de pages vides vient souvent du fait que la largeur du corps du rapport _dépasse l’espace disponible sur la page_.

Vous pouvez uniquement afficher et définir la largeur du corps du rapport à l’aide du volet **Propriétés**. Tout d’abord, cliquez n’importe où dans une zone vide du corps du rapport.

![Image affichant le volet Propriétés, avec la propriété de largeur du corps du rapport en surbrillance.](media/report-paginated-blank-page/report-body-properties-width.png)

Vérifiez que la valeur de largeur ne dépasse pas la largeur de page disponible. Pour vous aider, retenez le principe suivant :

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Il n’est pas possible de réduire la largeur du corps du rapport lorsque des objets de rapport se trouvent déjà dans l’espace que vous souhaitez supprimer. Vous devez d’abord les repositionner ou les redimensionner avant de réduire la largeur.
>
> En outre, la largeur du corps du rapport peut augmenter automatiquement lorsque vous ajoutez de nouveaux objets ou que vous redimensionnez ou repositionnez des objets existants. Le concepteur de rapports élargit toujours le corps pour tenir compte de la position et de la taille des objets contenus dans le rapport.

## <a name="report-body-height"></a>Hauteur du corps du rapport

Une page vierge peut également survenir si le corps du rapport présente un espace supplémentaire après le dernier objet.

Nous vous recommandons de toujours réduire la hauteur du corps pour supprimer tout espace en fin de rapport.

![Image montrant une conception de rapport. L’espace sous la région des données du tableau matriciel est mis en surbrillance et marqué comme inutile.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Options des sauts de page

Chaque région de données et visualisation des données comportent des options de saut de page. Vous pouvez accéder à ces options dans la page des propriétés ou dans le volet **Propriétés**.

Vérifiez que la propriété **Insérer un saut de page après** n’est pas activée sans raison.

![Image affichant la fenêtre Propriétés d’un tableau matriciel. La propriété « Insérer un saut de page après » est activée.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Utiliser l’espace blanc d’un conteneur

Si le problème de page vierge persiste, vous pouvez également essayer de désactiver la propriété **ConsumeContainerWhitespace** du rapport. Cette propriété peut uniquement être définie dans le volet **Propriétés**.

![Image affichant le volet Propriétés, avec la propriété ConsumeContainerWhitespace en surbrillance.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Par défaut, cette propriété est désactivée. Elle indique si l’espace blanc minimal dans les conteneurs, par exemple le corps du rapport ou un rectangle, doit être utilisé. Seul l’espace blanc à droite et en dessous du contenu est affecté.

## <a name="printer-paper-size"></a>Format de papier de l’imprimante

Enfin, si vous imprimez le rapport sur papier, assurez-vous que le papier est correctement chargé dans l’imprimante. Le format du papier physique doit correspondre au [format de papier du rapport](#page-setup).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Présentation des rapports paginés dans Power BI Premium](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Pagination des rapports Power BI](../paginated-reports/paginated-reports-pagination.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)
