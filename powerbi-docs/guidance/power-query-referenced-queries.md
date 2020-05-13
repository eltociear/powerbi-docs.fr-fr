---
title: Référencement des requêtes Power Query
description: Conseils pour le référencement des requêtes Power Query.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 242f1e44e3314af900d9f4d4e4fb7380b28b4103
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278672"
---
# <a name="referencing-power-query-queries"></a>Référencement des requêtes Power Query

Cet article s’adresse principalement aux modélisateurs de données qui utilisent Power BI Desktop. Il vous guide dans la définition de requêtes Power Query qui référencent d'autres requêtes.

Qu’est-ce que cela signifie ? _Lorsqu'une requête référence une seconde requête, c'est comme si les étapes de la seconde requête étaient combinées avec les étapes de la première requête et s'exécutaient avant elles._

Considérons plusieurs requêtes : **Requête1** extrait les données d'un service web, et sa charge est désactivée. **Requête2**, **Requête3** et **Requête4** référencent toutes **Requête1**, et leurs sorties sont chargées dans le modèle de données.

![Vue Dépendances de la requête, affichant les requêtes décrites dans le paragraphe précédent.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Lorsque le modèle de données est actualisé, on suppose souvent que Power Query récupère le résultat **Requête1** et qu'il est réutilisé par des requêtes référencées. Ce raisonnement est incorrect. En fait, Power Query exécute **Requête2**, **Requête3** et **Requête4** séparément.

Vous pouvez penser que **Requête2** intègre les étapes de **Requête1**. C'est aussi le cas pour **Requête3**et **Requête4**. Le diagramme suivant présente une image plus claire de la façon dont les requêtes sont exécutées.

![Version modifiée de la vue Dépendances de la requête, affichant Requête2, Requête3 et Requête4. Chacune des trois requêtes intègre la requête1.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Requête1** est exécutée trois fois. Les multiples exécutions peuvent ralentir l’actualisation des données et avoir un impact négatif sur la source de données.

L'utilisation de la fonction [Table.Buffer](/powerquery-m/table-buffer) dans **Requête1** n'élimine pas l'extraction de données supplémentaires. Cette fonction met une table en mémoire tampon. Et la table mise en mémoire tampon ne peut être utilisée que dans la même exécution de requête. Ainsi, dans cet exemple, si **Requête1** est mis en mémoire tampon lorsque **Requête2** est exécutée, les données mises en mémoire tampon ne peuvent pas être utilisées lorsque **Requête3** et **Requête4** sont exécutées. Elles mettront elles-mêmes deux fois plus de données en mémoire tampon. (Ce résultat pourrait faire chuter les performances car la table sera mise en mémoire tampon par chaque requête de référencement.)

> [!NOTE]
> L'architecture de mise en cache de Power Query est complexe, et ce n'est pas l'objet de cet article. Power Query peut mettre en cache les données extraites d'une source de données. Toutefois, lorsqu'il exécute une requête, il peut récupérer plusieurs fois les informations de la source de données.

## <a name="recommendations"></a>Recommandations

En général, nous vous recommandons de référencer les requêtes pour éviter la duplication de la logique dans vos autres requêtes. Toutefois, comme le décrit le présent article, cette approche de conception risque de ralentir l’actualisation des données et surcharger les sources de données.

Nous vous recommandons plutôt de créer un [dataflow](../transform-model/service-dataflows-overview.md). L'utilisation d'un dataflow peut accélérer l’actualisation des données et réduire l'impact sur vos sources de données.

Vous pouvez concevoir le dataflow pour encapsuler les données source et les transformations. Comme le dataflow est un stockage de données persistant dans le service Power BI, l’extraction de ses données est rapide. Ainsi, même lorsque les requêtes de référencement se traduisent par de multiples demandes de dataflow, les délais d’actualisation des données peuvent être améliorés.

Dans l'exemple, si **Requête1** est modifiée en tant qu'entité de dataflow, **Requête2**, **Requête3** et **Requête4** peuvent l'utiliser comme source de données. Avec cette méthode, l'entité sourcée par **Requête1** ne sera évaluée qu'une seule fois.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Préparation des données en libre-service dans Power BI](../transform-model/service-dataflows-overview.md)
- [Création et utilisation de flux de données dans Power BI](../transform-model/service-dataflows-create-use.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
