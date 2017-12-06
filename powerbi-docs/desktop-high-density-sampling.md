---
title: "Échantillonnage de ligne à haute densité dans Power BI"
description: "Échantillonnage de ligne à haute densité dans Power BI"
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
ms.openlocfilehash: c8eb43a86791fa067f7f2417780806eba007672c
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="high-density-line-sampling-in-power-bi"></a>Échantillonnage de lignes à haute densité dans Power BI
Depuis la publication en juin 2017 de **Power BI Desktop** et des mises à jour du **service Power BI**, un nouvel algorithme d’échantillonnage est disponible, qui améliore les visuels qui échantillonnent des données à haute densité. Par exemple, vous pouvez créer un graphique en courbes à partir des résultats des ventes de magasins, chacun d’eux enregistrant plus de dix mille reçus d’achat chaque année. Un graphique en courbes de telles informations échantillonne des données (sélectionnez une représentation explicite de ces données pour illustrer les variations des ventes au fil du temps) à partir des données de chaque magasin, et illustre plusieurs séries, représentant ainsi des données sous-jacentes. Il s’agit d’une pratique courante dans la visualisation de données à haute densité, et Power BI Desktop a amélioré son échantillonnage des données à haute densité décrit en détail dans cet article.

![](media/desktop-high-density-sampling/high-density-sampling_01.png)

> [!NOTE]
> L’algorithme d’**échantillonnage à haute densité** décrit dans cet article s’applique tant à **Power BI Desktop** qu’au **service Power BI**, et est disponible dans les deux.
> 
> 

## <a name="how-high-density-line-sampling-works"></a>Fonctionnement de l’échantillonnage de ligne à haute densité
Auparavant, **Power BI** sélectionnait une collection de points de données échantillons dans la plage complète des données sous-jacentes de manière déterministe. Par exemple, pour des données à haute densité sur un visuel s’étendant sur une année civile, il pouvait y avoir 350 points de données échantillons affichés dans le visuel, chacun d’eux étant sélectionné de manière à s’assurer que la plage complète des données (la série globale de données sous-jacentes) était représentée dans le visuel. Pour comprendre comment cela fonctionne, imaginons que nous tracions une cotation sur une période d’un an, et que nous ayons sélectionné 365 points de données pour créer un visuel de graphique en courbes (soit un point de données pour chaque jour).

Dans ce cas, il existe un grand nombre de valeurs pour une cotation chaque jour. Bien entendu, il existe des hausses et des baisses chaque jour, mais celles-ci peuvent se produire à tout moment de la journée lorsque la bourse est ouverte. Pour un échantillonnage de ligne à haute densité, si l’échantillon de données sous-jacentes a été pris à 10 h 30 et à 24 h 00 quotidiennement, vous obtenez un instantané représentatif des données sous-jacentes (prix à 10 h 30 et à 24 h 00), mais il ne peut pas traduire les hausses et baisses réelles de la cotation pour ce point de données représentatif (ce jour-là). Dans ce cas (entre autres), l’échantillonnage est représentatif des données sous-jacentes, mais il ne capture pas toujours certains points importants, en l’occurrence les hausses et baisses quotidiennes de la cotation.

Par définition, des données à haute densité sont échantillonnées pour permettre une génération rapide de visualisations interactives (un trop grand nombre de points de données sur un visuel peut ralentir l’affichage de celui-ci et nuire à la lisibilité des tendances). Un algorithme d’échantillonnage est la manière dont ces données sont échantillonnées afin d’offrir une expérience de visualisation optimale. Dans Power BI Desktop, l’algorithme a été amélioré afin de fournir la meilleure combinaison possible de réactivité, de représentation et de préservation claire des points importants de chaque tranche de temps.

## <a name="how-the-new-line-sampling-algorithm-works"></a>Fonctionnement du nouvel algorithme d’échantillonnage de ligne
Le nouvel algorithme d’échantillonnage de ligne à haute densité est disponible pour générer des visuels de graphique en courbes et en aires avec un axe X continu.

Pour un visuel à haute densité, **Power BI** découpe intelligemment vos données en segments haute résolution, puis sélectionne les points importants pour représenter chaque segment. Ce processus de segmentation de données haute résolution est spécialement réglé pour s’assurer que le graphique obtenu soit visuellement indiscernable du rendu de tous les points de données sous-jacents, mais qu’il soit généré beaucoup plus rapidement et soit plus interactif.

### <a name="minimum-and-maximum-values-for-high-density-line-visuals"></a>Valeurs minimales et maximales pour les visuels de ligne à haute densité
Pour chaque visualisation, les limitations visuelles suivantes s’appliquent :

* **3 500** est le nombre maximal de points de données *affichés* sur le visuel, quel que soit le nombre de points de données ou de séries sous-jacentes. Par conséquent, si vous avez 10 séries avec 350 points de données chacune, le visuel a atteint sa limite globale maximale de points de données. Si vous avez une seule série, celle-ci peut comprendre jusqu’à 3 500 points de données si le nouvel algorithme estime qu’il s’agit de l’échantillonnage optimal pour les données sous-jacentes.
* Le nombre maximal de séries pour un visuel est fixé à **60**. Si vous avez plus de 60 séries, divisez les données et créez plusieurs visuels représentant chacun au maximum 60 séries. Il est recommandé d’utiliser un **slicer** (segment) afin d’afficher uniquement des segments des données (seulement certaines séries). Par exemple, si vous affichez toutes les sous-catégories dans la légende, vous pouvez utiliser un slicer afin de filtrer par catégorie générale sur la même page de rapport.

Ces paramètres garantissent que les visuels dans Power BI Desktop s’affichent très rapidement et réagissent aux interactions des utilisateurs, et qu’ils n’entraînent pas une surcharge de calcul excessive sur l’ordinateur affichant le visuel.

### <a name="evaluating-representative-data-points-for-high-density-line-visuals"></a>Évaluation des points de données représentatifs pour les visuels de ligne à haute densité
Lorsque le nombre de points de données sous-jacents dépasse le nombre maximal de points de données qui peuvent être représentés dans le visuel (3 500), un processus appelé *compartimentage* démarre, qui découpe les données sous-jacentes en blocs nommés *emplacements* qu’il affine ensuite de manière itérative.

L’algorithme crée le plus grand nombre possible d’emplacements afin d’offrir une granularité maximale pour le visuel. Dans chaque emplacement, l’algorithme détecte les valeurs de données minimale et maximale pour s’assurer que les valeurs importantes et significatives (par exemple, des valeurs hors norme) sont capturées et affichées dans le visuel. Selon les résultats du compartimentage et de l’évaluation ultérieure des données par Power BI, la résolution minimale de l’axe X du visuel est déterminée afin de garantir une granularité maximale de celui-ci.

Comme mentionné précédemment, la granularité minimale de chaque série est de 350 points, la granularité maximale de 3 500.

Chaque emplacement est représenté par deux points de données qui deviennent les points de données représentatifs de l’emplacement dans le visuel. Les points de données sont simplement les valeurs haute et basse de cet emplacement et, en sélectionnant ces valeurs hautes et basses, le processus de compartimentage garantit qu’une valeur haute importante ou valeur basse significative est capturée et restituée dans le visuel.

Si vous trouvez que cela ressemble beaucoup à une analyse visant à vérifier que les valeurs hors norme occasionnelles sont capturées et correctement affichées dans le visuel, vous avez raison. C’est précisément la raison d’être du nouvel algorithme et du processus de compartimentage.

## <a name="tooltips-and-high-density-line-sampling"></a>Info-bulles et échantillonnage de ligne à haute densité
Il est important de noter que ce processus de compartimentage, qui entraîne la capture des valeurs minimale et maximale d’un emplacement donné et leur affichage dans le visuel, peut affecter la manière dont les info-bulles affichent les données lorsque vous pointez sur des points de données. Pour expliquer comment et pourquoi cela se produit, revenons à l’exemple des cotations évoqué plus haut dans cet article.

Supposons que vous créez un visuel basé sur une cotation et comparez deux cotations différentes, utilisant toutes deux un **échantillonnage à haute densité**. Les données sous-jacentes de chaque série comprennent un grand nombre de points de données (vous capturez peut-être la cotation à chaque seconde de la journée). L’algorithme d’échantillonnage de ligne à haute densité effectue un compartimentage pour chaque série indépendamment de l’autre.

À présent, supposons que la première cotation bondisse à 12 h 02, puis redescende rapidement dix secondes plus tard. Il s’agit là d’un point de données important. Lors du compartimentage pour cette cotation, la valeur haute enregistrée à 12 h 02 constitue un point de données représentatif pour cet emplacement.

En revanche, pour la deuxième cotation, 12 h 02 ne correspond ni à une valeur haute, ni à une valeur basse dans l’emplacement incluant cette heure (les valeurs haute et basse pour l’emplacement incluant 12:02 ont peut-être été enregistrées trois minutes plus tard). Dans ce cas, une fois le graphique en courbes créé, lorsque vous positionnez le curseur sur 12 h 02, vous voyez dans l’info-bulle une valeur pour la première cotation (car celle-ci a bondi à 12 h 02 et cette valeur a été sélectionnée comme point de données haut de cet emplacement), mais vous ne voyez *pas* de valeur dans l’info-bulle à 12 h 02 pour la deuxième cotation. Cela est dû au fait que la deuxième cotation ne présente ni de valeur haute, ni de valeur basse pour l’emplacement incluant 12 h 02. Il n’y a par conséquent aucune donnée à afficher pour la deuxième cotation à 12 h 02, de sorte qu’aucune donnée ne s’affiche dans l’info-bulle.

Cette situation se produit souvent avec les info-bulles. Les valeurs haute et basse d’un emplacement donné peuvent ne pas correspondre parfaitement avec les points de valeur d’axe X échelonnés de façon uniforme, de sorte que l’info-bulle n’affiche pas la valeur.  

## <a name="how-to-turn-on-high-density-line-sampling"></a>Comment activer un échantillonnage de ligne à haute densité
Par défaut, le nouvel algorithme est **activé**. Pour modifier ce paramètre, accédez au volet **Mise en forme**, dans la carte **Général**. Dans la partie inférieure, vous pouvez voir un curseur bascule nommé **Échantillonnage à haute densité**. Pour désactiver celui-ci, faites-le glisser en position **Désactivé**.

![](media/desktop-high-density-sampling/high-density-sampling_02.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations
Le nouvel algorithme d’échantillonnage de ligne à haute densité constitue une amélioration importante apportée à Power BI, mais il existe quelques considérations que vous devez connaître lorsque vous travaillez avec des données et valeurs à haute densité.

* En raison de la granularité accrue et du processus de compartimentage, les **info-bulles** ne peuvent afficher une valeur que si les données représentatives sont alignées sur votre curseur. Pour plus d’informations, consultez la section précédente de cet article consacrée aux **info-bulles**.
* Lorsque la taille d’une source de données globale est trop volumineuse, le nouvel algorithme élimine des séries (éléments de légende) pour respecter la contrainte d’importation maximale de données.
  
  * Dans ce cas, le nouvel algorithme trie les séries de légende par ordre alphabétique et démarre au bas de la liste des éléments de légende dans l’ordre alphabétique, jusqu’à ce que l’importation maximale de données soit atteinte, et n’importe pas de série supplémentaire.
* Quand un jeu de données sous-jacent comprend plus de 60 séries (nombre maximal de séries, comme décrit précédemment), le nouvel algorithme trie les séries par ordre alphabétique et élimine les séries au-delà de la 60ème.
* Si les valeurs des données ne sont pas de type *numérique* ou *date/heure*, Power BI n’utilise pas le nouvel algorithme et revient à l’algorithme précédent (échantillonnage sans haute densité).
* Le paramètre **Afficher les éléments sans données** n’est pas pris en charge par le nouvel algorithme.
* Le nouvel algorithme n’est pas pris en charge en cas d’utilisation d’une connexion active à un modèle hébergé dans SQL Server Analysis Services (version 2016 ou antérieure). Il est pris en charge dans les modèles hébergés dans **Power BI** ou Azure Analysis Services.

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur l’échantillonnage à haute densité dans des nuages de points, voir l’article suivant.

* [Échantillonnage à haute densité dans les nuages de points de Power BI](desktop-high-density-scatter-charts.md)

