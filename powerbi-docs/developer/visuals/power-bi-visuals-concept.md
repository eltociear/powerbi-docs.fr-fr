---
title: Concept visuel Power BI
description: L’article décrit comment un visuel s’intègre à Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700843"
---
# <a name="power-bi-visual-concept"></a>Concept visuel Power BI

L’article explique comment un utilisateur et un visuel interagissent avec Power BI et comment un utilisateur interagit avec un visuel Power BI. Dans le diagramme, vous voyez quelles actions ont un impact direct sur le visuel ou via Power BI (par exemple, l’utilisateur sélectionne des signets).

![Visuel Power BI](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>Le visuel obtient la mise à jour de Power BI

Le visuel a la méthode `update` et cette méthode contient généralement la logique principale du visuel et est responsable du rendu du graphique ou de la visualisation des données.

D’autres mises à jour accompagnent l’appel de la méthode`update`.

### <a name="user-interacts-with-visual-through-power-bi"></a>L’utilisateur interagit avec le visuel via Power BI

* L’utilisateur ouvre le panneau des propriétés visuelles.

    Power BI extrait les propriétés et les objets pris en charge à partir du `capabilities.json` du visuel et, pour recevoir les valeurs réelles des propriétés, Power BI appelle la méthode `enumerateObjectInstances` du visuel.

    Le visuel doit retourner les valeurs réelles des propriétés.

    Pour plus d’informations, [découvrez les fonctionnalités visuelles](capabilities.md).

* [L’utilisateur change la propriété du visuel](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) dans le panneau de format.

    Après avoir modifié la valeur d’une propriété, Power BI appelle la méthode `update` du visuel et passe à la méthode de mise à jour les nouvelles `options` avec les nouvelles valeurs des objets.

    Pour plus d’informations, [découvrez les objets et propriétés du visuel](objects-properties.md).

* L’utilisateur redimensionne le visuel.

    Quand un utilisateur change la taille du visuel, Power BI appelle la méthode `update` avec le nouvel objet `option`. Les options comportent un objet `viewport` imbriqué avec les nouvelles largeur et hauteur du visuel.

* L’utilisateur applique un filtre de rapport, de page ou de niveau visuel.

    Power BI filtre les données en fonction des conditions de filtre et appelle la méthode `update` du visuel pour fournir de nouvelles données au visuel.

    Le visuel obtient une nouvelle mise à jour des `options` avec de nouvelles données dans l’un des objets imbriqués. Cela dépend de la configuration du mappage de vues de données du visuel.

    Pour plus d’informations, [découvrez les mappages de vues de données](dataview-mappings.md).

* L’utilisateur sélectionne un point de données dans un autre visuel du rapport.

    Power BI filtre ou met en surbrillance les points de données sélectionnés et appelle la méthode `update` du visuel.

    Le visuel obtient de nouvelles données filtrées ou les mêmes données avec un tableau de mises en surbrillance.

    Pour plus d’informations, [découvrez comment mettre en surbrillance des données dans des visuels](highlight.md).

* L’utilisateur sélectionne un signet dans le panneau des signets du rapport.

    Deux actions peuvent alors se produire :

    1. Power BI appelle la fonction passée inscrite par la méthode `registerOnSelectionCallback` et la fonction de rappel obtient des tableaux de sélections pour le signet correspondant.

    2. Power BI appelle la méthode `update` avec l’objet filtre correspondant dans `options`.

    Dans les deux cas, le visuel doit modifier l’état de visualisation en fonction des sélections reçues ou de l’objet filtre.

    Pour plus d’informations sur les signets, [découvrez comment gérer les signets](filter-api.md).

    Pour plus d’informations sur les filtres, [découvrez comment les visuels Power BI peuvent filtrer les données dans d’autres visuels](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>L’utilisateur interagit directement avec le visuel

* L’utilisateur pointe la souris sur l’élément de données

    Le visuel peut afficher des informations supplémentaires sur le point de données via l’API des info-bulles Power BI.
    L’utilisateur pointe la souris sur l’élément visuel. Le visuel peut gérer l’événement et afficher des données sur l’élément info-bulle.

    Le visuel peut afficher une info-bulle standard ou une info-bulle de page de rapport.

    Pour plus d’informations, lisez [Guide pratique pour ajouter des info-bulles](add-tooltips.md).

* L’utilisateur modifie les propriétés visuelles (par exemple, il développe l’arborescence et le visuel enregistre l’état dans les propriétés)

    Le visuel peut enregistrer des valeurs de propriétés via l’API Power BI, par exemple lorsque l’utilisateur interagit avec le visuel. Le visuel doit aussi enregistrer ou mettre à jour les valeurs de propriétés. Pour cela, le visuel peut appeler la méthode `presistProperties`.

* L’utilisateur clique sur le lien de l’URL.

    Par défaut, le visuel ne peut pas ouvrir l’URL. Pour ouvrir l’URL dans le nouvel onglet, le visuel doit appeler la méthode `launchURL` et passer l’URL en tant que paramètre.

    Pour plus d’informations, consultez [API d’URL de lancement](launch-url.md).

* L’utilisateur applique un filtre via le visuel

    Le visuel appelle `applyJSONFilter` et passe des conditions de filtre au filtre pour filtrer les données dans un autre visuel.

    Le visuel peut utiliser plusieurs types de filtres, par exemple un filtre de base, un filtre avancé, un filtre de tuple.

    Pour plus d’informations sur les filtres, [découvrez comment les visuels Power BI peuvent filtrer les données dans d’autres visuels](filter-api.md).

* L’utilisateur clique sur des éléments ou les sélectionne sur le visuel.

    Pour plus d’informations sur les sélections, [découvrez le mode d’interaction du visuel](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>Le visuel interagit avec Power BI

* Le visuel demande plus de données à Power BI.

    Le visuel peut traiter les données en plusieurs parties. La méthode de l’API FetchMoreData demande le fragment suivant du jeu de données.

    Pour plus d’informations sur `fetchMoreData`, [découvrez comment extraire davantage de données de Power BI](fetch-more-data.md)

* Service d’événements

    Power BI peut exporter des rapports au format PDF ou les envoyer par e-mail (seuls les visuels certifiés sont pris en charge). Pour indiquer à Power BI que le rendu est terminé et qu’il est prêt à capturer le fichier PDF/l’e-mail, le visuel doit appeler l’API d’événements de rendu.

    Pour plus d’informations, [découvrez l’exportation de rapports de Power BI au format PDF](../../consumer/end-user-pdf.md)

    Recherchez d’autres [informations sur le service d’événements](event-service.md)

## <a name="next-steps"></a>Étapes suivantes

Vous êtes un développeur web et souhaitez créer vos propres visualisations et les ajouter à AppSource ? Consultez [Développement d’un visuel Power BI](./custom-visual-develop-tutorial.md) et découvrez comment [publier des visuels Power BI sur AppSource](../office-store.md).
