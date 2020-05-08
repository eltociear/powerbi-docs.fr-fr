---
title: Jeux de données dans le service Power BI
description: Comprendre les jeux de données du service Power BI, qui représentent une source de données prêtes pour la création de rapports et la visualisation.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 6170217119e443a2eb24aac056623dce5070303e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79208008"
---
# <a name="datasets-in-the-power-bi-service"></a>Jeux de données dans le service Power BI

Cet article fournit une explication technique des jeux de données Power BI.

## <a name="dataset-types"></a>Types de jeux de données

Les jeux de données Power BI représentent une source de données prêtes pour la création de rapports et la visualisation. Il existe cinq types de jeux de données différents, créés de la manière suivante :

- Connexion à un modèle de données existant non hébergé dans une capacité Power BI
- Chargement d'un fichier Power BI Desktop contenant un modèle
- Chargement d'un classeur Excel (contenant un ou plusieurs tableaux Excel et/ou un modèle de données de classeur), ou chargement d'un fichier CSV (valeurs séparées par des virgules)
- Utilisation du service Power BI pour créer un [jeu de données push](developer/automation/walkthrough-push-data.md)
- Utilisation du service Power BI pour créer un [jeu de données de streaming ou de streaming hybride](service-real-time-streaming.md)

À l'exception des jeux de données de streaming, le jeu de données représente un modèle de données qui tire parti des technologies de modélisation éprouvées d’[Analysis Services](/analysis-services/analysis-services-overview).

> [!NOTE]
> Dans notre documentation, les termes _jeux de données_ et _modèles_ sont parfois utilisés de manière interchangeable. Généralement, du point de vue du service Power BI, il s'agit d’un **jeu de données**, et du point de vue du développement, on parle alors d’un **modèle**. Dans le contexte de notre documentation, ces termes signifient à peu près la même chose.

### <a name="external-hosted-models"></a>Modèles hébergés à l'extérieur

Il existe deux types de modèles hébergés à l'extérieur : SQL Server Analysis Services et [Azure Analysis Services](/azure/analysis-services/analysis-services-overview).

La connexion à un modèle SQL Server Analysis Services implique l'installation de la [passerelle de données locale](service-gateway-onprem.md), qu'il s'agisse d'une infrastructure en tant que service (IaaS) hébergée localement ou sur une machine virtuelle. Azure Analysis Services n'a pas besoin de passerelle.

La connexion à Analysis Services est souvent utile lorsqu'il existe des investissements de modèle existants, qui font généralement partie d'un entrepôt de données d'entreprise (EDW). Power BI permet d’établir une _connexion active_ avec Analysis Services, en appliquant des autorisations d’accès aux données avec l'identité de l'utilisateur du rapport Power BI. Pour SQL Server Analysis Services, les modèles multidimensionnels (cubes) et les modèles tabulaires sont pris en charge. Comme le montre l'image suivante, un jeu de données de connexion active transmet les requêtes à des modèles hébergés à l'extérieur.

![Un jeu de données de connexion active transmet les requêtes à un modèle hébergé à l'extérieur](media/service-datasets-understand/live-connection-dataset.png)

### <a name="power-bi-desktop-developed-models"></a>Modèles développés avec Power BI Desktop

Power BI Desktop, une application client destinée au développement Power BI, peut être utilisée pour développer un modèle. Le modèle représente en fait un modèle tabulaire Analysis Services. Les modèles peuvent être développés en important des données à partir de flux de données, qui peuvent ensuite être intégrées à des sources de données externes. Bien que les détails sur la façon dont la modélisation peut être réalisée sortent du cadre de cet article, il est important de comprendre qu'il existe trois différents types, ou _modes_, de modèles pouvant être développés en utilisant Power BI Desktop. Ces modes déterminent si les données sont importées dans le modèle ou si elles restent dans la source de données. Les trois modes sont les suivants : Import, DirectQuery et Composite. Pour plus d'informations sur chaque mode, voir l’article [Modes de jeu de données dans le service Power BI](service-dataset-modes-understand.md).

Les modèles hébergés à l'extérieur et les modèles Power BI Desktop peuvent renforcer la sécurité au niveau des lignes (RLS) afin de limiter les données récupérées pour un utilisateur donné. Par exemple, les utilisateurs affectés au groupe de sécurité **Vendeurs** ne peuvent voir que les données des rapports pour la ou les régions de vente auxquelles ils sont affectés. Les rôles RLS sont _dynamiques_ ou _statiques_. Les rôles dynamiques filtrent par utilisateur du rapport, tandis que les rôles statiques appliquent les mêmes filtres à tous les utilisateurs affectés au rôle. Pour plus d’informations, consultez [Sécurité au niveau des lignes avec Power BI](service-admin-rls.md).

### <a name="excel-workbook-models"></a>Modèles de classeur Excel

La création de jeux de données basés sur des [classeurs Excel](service-excel-workbook-files.md) ou des [fichiers CSV](service-comma-separated-value-files.md) entraîne la création automatique d'un modèle. Les tableaux Excel et les données CSV sont importés pour créer des tableaux de modèles, tandis qu'un modèle de données de classeur Excel est transposé pour créer un modèle Power BI. Dans tous les cas, les données variables sont importées dans un modèle.

## <a name="summary"></a>Résumé

Il est donc possible de distinguer les jeux de données Power BI qui représentent des modèles :

- Ils sont soit hébergés dans le service Power BI, soit hébergés en externe par Analysis Services.
- Ils peuvent stocker des données importées, émettre des demandes d'interrogation en transit aux sources de données sous-jacentes, ou utiliser une combinaison des deux.

Voici un résumé des faits importants concernant les jeux de données Power BI qui représentent des modèles :

- Les modèles hébergés SQL Server Analysis Services nécessitent une passerelle pour effectuer des requêtes de connexion active.
- Modèles hébergés par Power BI qui importent des données :
  - Pour être interrogés, ces modèles doivent être entièrement chargés en mémoire.
  - Nécessitent un rafraîchissement pour maintenir les données à jour, et doivent impliquer des passerelles lorsque les données source ne sont pas accessibles directement sur Internet.
- Les modèles hébergés par Power BI qui utilisent le mode de stockage [DirectQuery](desktop-directquery-about.md) nécessitent une connectivité aux données source. Lorsque le modèle est interrogé, Power BI envoie des requêtes aux données source pour récupérer les données actuelles. Ce mode doit impliquer des passerelles lorsque les données source ne sont pas accessibles directement sur Internet.
- Des modèles peuvent appliquer des règles RLS, en utilisant des filtres pour limiter l'accès aux données à certains utilisateurs.

## <a name="considerations"></a>Considérations

Pour déployer et gérer Power BI avec succès, il est important de comprendre où les modèles sont hébergés, leur mode de stockage, les dépendances par rapport aux passerelles, la taille des données importées, ainsi que le type et la fréquence de rafraîchissement. Ces configurations peuvent toutes avoir un impact significatif sur les ressources de capacité de Power BI. De plus, la conception même du modèle, y compris ses requêtes de préparation des données, ses relations et ses calculs, s'ajoutent à ces diverses considérations.

Il est également important de comprendre que les modèles d'importation hébergés par Power BI peuvent être actualisés selon un calendrier, ou déclenchés à la demande par un utilisateur du service Power BI.

## <a name="next-steps"></a>Étapes suivantes

- [Modes des jeux de données dans le service Power BI](service-dataset-modes-understand.md)
- D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
