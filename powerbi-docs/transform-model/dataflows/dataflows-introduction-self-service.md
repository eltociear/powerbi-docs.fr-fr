---
title: Introduction aux dataflows et à la préparation des données en libre-service
description: Vue d’ensemble des dataflows Power BI et de leur fonction
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: d8315652883f644d5440c25e3203fdf004bac51c
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94669106"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>Introduction aux dataflows et à la préparation des données en libre-service

Au fur et à mesure que le volume de données continue d'augmenter, il devient de plus en plus difficile de transformer ces données en informations bien formées et exploitables. Nous voulons des données prêtes pour l'analyse, pour remplir des visuels, des rapports et des tableaux de bord, afin de pouvoir transformer rapidement nos volumes de données en informations exploitables. Avec la préparation des données en libre-service pour le Big Data dans Power BI, vous pouvez accéder à des insights de Power BI à partir de données en quelques clics seulement.

![flux de données](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>Quand utiliser les dataflows

Les dataflows ont été conçus pour prendre en charge les scénarios suivants :

* Créer une logique de transformation réutilisable pouvant être partagée par de nombreux jeux de données et rapports dans Power BI. Les dataflows favorisent la réutilisation des éléments de données sous-jacents, ce qui évite d’avoir à créer des connexions distinctes avec vos sources de données cloud ou locales.

* Exposer les données de votre propre stockage Azure Data Lake Gen 2, permettant ainsi de connecter d’autres services Azure aux données sous-jacentes brutes.

* Créer une source de référence unique en forçant les analystes à se connecter aux dataflows, et non aux systèmes sous-jacents, ce qui vous permet de contrôler l’accessibilité des données et la façon dont elles sont exposées aux créateurs de rapports. Vous pouvez aussi mapper les données aux définitions standard du secteur, ce qui vous permet de créer des vues parfaitement organisées et compatibles avec les autres services et produits rencontrés dans Power Platform.

* Si vous prévoyez d’utiliser d’importants volumes de données et d’effectuer des opérations ETL à grande échelle, les dataflows avec Power BI Premium offrent une mise à l’échelle plus efficace et confèrent davantage de souplesse. Les dataflows prennent en charge un large éventail de sources cloud et locales. 

* Empêcher les analystes d’avoir un accès direct à la source de données sous-jacente. Sachant que les créateurs de rapports peuvent bâtir par-dessus les dataflows, vous avez peut être plus intérêt à réserver l’accès aux sources de données sous-jacentes à un petit nombre de personnes et de permettre aux analystes d’accéder aux dataflows sur lesquels ils pourront bâtir. Cette approche permet de réduire la charge des systèmes sous-jacents et offre aux administrateurs les moyens de contrôler plus précisément à quel moment les systèmes sont chargés à partir des actualisations.

Une fois que vous avez créé un dataflow, vous pouvez utiliser Power BI Desktop et le service Power BI pour créer des jeux de données, des rapports, des tableaux de bord et des applications qui tirent parti du Common Data Model pour obtenir des insights approfondis sur vos activités métier. La planification de l’actualisation de flux de données est gérée directement à partir de l’espace de travail dans lequel votre flux de données a été créé, tout comme vos jeux de données.

## <a name="next-steps"></a>Étapes suivantes
Cet article a fourni une vue d’ensemble de la préparation des données en libre-service pour le Big Data dans Power BI et les nombreuses façons dont vous pouvez l’utiliser. 

Les articles suivants vous permettront d’en savoir plus sur les dataflows et Power BI :

* [Création d’un flux de données](dataflows-create.md)
* [Configurer et consommer un dataflow](dataflows-configure-consume.md)
* [Configuration du stockage de dataflows pour utiliser Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Fonctionnalités Premium des dataflows](dataflows-premium-features.md)
* [IA et dataflows](dataflows-machine-learning-integration.md)
* [Considérations et limitations des dataflows](dataflows-features-limitations.md)
* [Bonnes pratiques pour les dataflows](dataflows-best-practices.md)


Pour plus d’informations sur le modèle Common Data Model, vous pouvez lire son article de présentation :
* [Common Data Model – Vue d’ensemble](/powerapps/common-data-model/overview)