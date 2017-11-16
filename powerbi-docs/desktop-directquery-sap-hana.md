---
title: DirectQuery pour SAP HANA dans Power BI
description: "Considérations importantes concernant l’utilisation de DirectQuery avec SAP HANA"
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: d6f863df59d7374c792f1e1ac16db3a04ad99d87
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="directquery-and-sap-hana"></a>DirectQuery et SAP HANA
Vous pouvez vous connecter aux sources de données **SAP HANA** directement à l’aide de **DirectQuery**.

Lors de l’utilisation de **SAP HANA**, il est important de comprendre certains aspects du traitement des connexions pour garantir que :

* Les résultats sont ceux attendus lorsque la vue SAP HANA contient des mesures non additives (par exemple comptages de valeurs, ou moyennes, plutôt que des sommes simples).
* Les requêtes qui en résultent sont efficaces.

Il est utile de prendre le temps de clarifier le comportement d’une source relationnelle telle que **SQL Server** lorsque la requête définie dans la boîte de dialogue **Obtenir des données** ou **l’éditeur de requête** effectue une agrégation. Dans l’exemple suivant, une requête définie dans **l’éditeur de requête** renvoie le prix moyen par **ProductID**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Si vous importez les données dans Power BI (plutôt que d’utiliser DirectQuery), les résultats sont les suivants :

* Les données sont importées au niveau d’agrégation défini par la requête créée dans **l’éditeur de requête**. Par exemple, prix moyen par produit. Cela génère une table à deux colonnes (*ProductID* et *AveragePrice*) qui peut être utilisée dans les visuels.
* Dans un visuel, toute agrégation subséquente (par exemple *Sum*, *Average*, *Min*, autres) est effectuée sur ces données importées.  Par exemple, si vous incluez *AveragePrice* sur un visuel, l’agrégat *Sum* est utilisé par défaut et retourne la somme de *AveragePrice* pour chaque *ProductID*, ce qui donnerait 13,67 dans notre exemple. Cela s’applique également à toute autre fonction d’agrégation (telle que *Min*, *Average*, etc.) utilisée sur le visuel. Par exemple, *Average* de *AveragePrice* renvoie la moyenne de 6,66, 4 et 3, ce qui est égal à 4,56, et *pas* la moyenne de *Price* sur les 6 enregistrements de la table sous-jacente, qui elle est égale à 5,17.

Si vous utilisez **DirectQuery** au lieu de l’importation, la même sémantique s’applique, et les résultats sont identiques :

* Avec la même requête, exactement les mêmes données sont présentées à la couche de création de rapports, ce qui est logique, même si les données ne sont pas réellement importées.
* Dans un visuel, toute agrégation subséquente (*Sum*, *Average*, *Min*, autres) est de nouveau effectuée sur la table logique à partir de la requête. Là encore, un visuel contenant *Average* de *AveragePrice* renvoie la même valeur de 4,56.

Examinons maintenant **SAP HANA**. Power BI peut utiliser les *vues analytiques* et les *vues de calcul* dans SAP HANA, qui peuvent toutes contenir des mesures. Pourtant, aujourd’hui l’approche pour SAP HANA suit les principes décrits précédemment : la requête définie dans la boîte de dialogue **Obtenir des données** ou **l’éditeur de requête** détermine les données disponibles, puis toute agrégation subséquente dans un visuel est effectuée sur ces données, ces principes s’appliquant à la fois à l’importation et à DirectQuery.

Toutefois, étant donné la nature de HANA, la requête définie dans la boîte de dialogue **Obtenir des données** initiale ou **l’éditeur de requête** est toujours une requête d’agrégation et comprend généralement des mesures pour lesquelles l’agrégation effectivement utilisée est définie par la vue HANA.

L’équivalent de l’exemple SQL Server ci-dessus est qu’il existe une vue HANA contenant **ID**, **ProductID**, **DepotID**, et des mesures, notamment **AveragePrice**, définies dans la vue comme **Average of Price**.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_02.png)

Si, dans la boîte de dialogue **Obtenir des données**, les sélections effectuées l’ont été pour **ProductID** et la mesure **AveragePrice**, cela définit une requête sur la vue nécessitant ces données d’agrégation (dans l’exemple ci-dessus, un pseudo-SQL est utilisé par souci de simplicité et ne correspond pas à la syntaxe exacte de HANA SQL). Ensuite, toutes les agrégations supplémentaires définies dans un visuel agrègent une nouvelle fois les résultats d’une telle requête. Là encore, comme décrit ci-dessus pour **SQL Server**, cela s’applique à la fois à l’importation et à DirectQuery. Notez que dans le cas de DirectQuery, la requête définie dans la boîte de dialogue **Obtenir des données** ou **l’éditeur de requête** est utilisée dans une sous-sélection au sein d’une requête unique envoyée à HANA et, par conséquent, toutes les données ne sont pas incluses par lecture avant une agrégation supplémentaire.

Cela donne lieu aux considérations importantes suivantes lors de l’utilisation de DirectQuery via HANA :

* Chaque fois que la mesure est non additive dans HANA (par exemple, pas *Sum*, *Min* ou *Max*), vous devez surveiller toute agrégation supplémentaire effectuée dans les visuels.
* Dans la boîte de dialogue **Obtenir des données** ou **l’éditeur de requête**, seules les colonnes requises pour récupérer les données nécessaires doivent être incluses, afin de refléter le fait que le résultat est une requête, qui doit être une requête raisonnable qu’il est possible d’envoyer à HANA. Par exemple, si des dizaines de colonnes sont sélectionnées avec l’idée qu’elles serviront peut-être dans des visuels subséquents, alors, même pour DirectQuery, un simple visuel signifie que la requête d’agrégation utilisée dans la sous-sélection contient ces dizaines de colonnes, ce qui entraîne des performances très médiocres.

Examinons un exemple. Dans l’exemple suivant, la sélection de cinq colonnes (CalendarQuarter, Color, LastName, ProductLine, SalesOrderNumber) dans la boîte de dialogue **Obtenir des données** et de la mesure OrderQuantity signifie que la création ultérieure d’un visuel simple contenant OrderQuantity Min donne lieu à l’envoi de la requête SQL suivante à HANA. La partie ombrée correspond à la sous-sélection, qui contient la requête provenant de la boîte de dialogue **Obtenir des données** / **l’éditeur de requête**. Si cette sous-sélection donne un résultat de cardinalité très élevé, il est probable que la performance HANA qui en résultera sera médiocre.

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

Pour cette raison, il est recommandé de limiter les éléments sélectionnés dans la boîte de dialogue **Obtenir des données** ou **l’éditeur de requête** aux éléments nécessaires, tout en produisant une requête raisonnable pour HANA.

### <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur DirectQuery, consultez les ressources suivantes :

* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP BW](desktop-directquery-sap-bw.md)
* [Passerelle de données locale](service-gateway-onprem.md)

