---
title: Résolution des problèmes du modèle DirectQuery dans Power BI Desktop
description: Résolvez les problèmes des modèles DirectQuery.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 623a0bbd187a997003ce7b82cc76d5c4fbe9ce44
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73868062"
---
# <a name="directquery-model-troubleshooting-in-power-bi-desktop"></a>Résolution des problèmes du modèle DirectQuery dans Power BI Desktop

Cet article cible les modélisateurs de données qui développent des modèles DirectQuery Power BI en utilisant Power BI Desktop ou le service Power BI. Il décrit comment diagnostiquer les problèmes de performances et comment obtenir des informations plus détaillées pour permettre l’optimisation des rapports.

## <a name="performance-analyzer"></a>Analyseur de performances

Il est fortement recommandé de débuter un diagnostic des problèmes de performances dans Power BI Desktop au lieu de le faire dans Power BI (le service ou Power BI Report Server). Les problèmes de performances résultent souvent simplement du niveau de performances de la source de données sous-jacente. Il est plus facile de les identifier et de les diagnostiquer au sein de l’environnement bien plus isolé de Power BI Desktop, ce qui élimine d’emblée certains composants (comme la passerelle Power BI). Si Power BI Desktop ne permet pas d’identifier les problèmes de performances, l’investigation doit se concentrer sur les spécificités du rapport dans Power BI. L’[Analyseur de performances](desktop-performance-analyzer.md) est un outil pratique pour identifier les problèmes tout au long de ce processus.

De même, il est recommandé de commencer par tenter d’isoler les problèmes d’un visuel spécifique, plutôt que d’examiner un grand nombre de visuels figurant sur une page.

Imaginons que ces étapes (décrites dans les paragraphes précédents de cette rubrique) ont été effectuées : nous avons maintenant un seul visuel sur une page dans Power BI Desktop qui reste lent. Pour déterminer les requêtes qui sont envoyées à la source sous-jacente par Power BI Desktop, vous pouvez utiliser l’Analyseur de performances. Il est également possible d’afficher les traces et les informations de diagnostic qui peuvent être émises par la source de données sous-jacente. Ces traces peuvent également contenir des informations utiles contenant des détails sur la façon dont la requête a été exécutée, et la manière d’améliorer celle-ci.

De plus, même en l’absence de telles traces de la source, il est possible d’afficher les requêtes émises par Power BI, ainsi que leurs durées d’exécution, comme décrit ci-après.

## <a name="review-trace-files"></a>Passer en revue les fichiers de trace

Par défaut, Power BI Desktop journalise les événements survenant au cours d’une session donnée dans un fichier de trace nommé **FlightRecorderCurrent.trc**.

Pour certaines sources DirectQuery, ce fichier journal contient toutes les requêtes envoyées à la source de données sous-jacente (les autres sources DirectQuery sont susceptibles d’être prises en charge dans le futur). Les sources qui écrivent les requêtes dans journal sont les suivantes :

- SQL Server
- Azure SQL Database
- Azure SQL Data Warehouse
- Oracle
- Teradata
- SAP HANA

Le fichier de trace figure dans le dossier **AppData** de l’utilisateur actuel : _\\\<Utilisateur>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces_

Voici comment accéder facilement à ce dossier : Dans Power BI Desktop, sélectionnez _Fichier > Options et paramètres > Options_, puis sélectionnez la page **Diagnostics**. La boîte de dialogue suivante s’affiche :

![La fenêtre Power BI Desktop est ouverte et la page Diagnostics généraux est sélectionnée. La section Options de diagnostic a deux propriétés : Activer le suivi et Ignorer le cache de géocodage. L’option Activer le suivi est activée. La section Collecte des vidages sur incident comporte un bouton Activer maintenant et un lien pour ouvrir le dossier des traces/vidages sur incident.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-desktop-file-options-diagnostics.png)

Quand vous sélectionnez le lien **Ouvrir le dossier des traces/vidages sur incident** sous Collecte des vidages sur incident, le dossier suivant s’ouvre : _\\\<Utilisateur>\AppData\Local\Microsoft\Power BI Desktop\Traces_

En accédant au dossier parent de ce dossier, vous pouvez voir le dossier contenant _AnalysisServicesWorkspaces_, qui contient un sous-dossier d’espace de travail pour chaque instance ouverte de Power BI Desktop. Les noms de ces sous-dossiers ont un nombre entier en suffixe, par exemple _AnalysisServicesWorkspace2058279583_.

Ce dossier comprend un sous-dossier _\Data_ contenant le fichier de trace FlightRecorderCurrent.trc pour la session Power BI active. Le dossier d’espace de travail correspondant est supprimé à l’issue de la session Power BI Desktop associée.

Vous pouvez ouvrir les fichiers de trace avec l’outil SQL Server Profiler, disponible en téléchargement gratuit avec SQL Server Management Studio. Vous pouvez y accéder [ici](/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017).

Une fois que vous avez téléchargé et installé SQL Server Management Studio, exécutez SQL Server Profiler.

![SQL Server Profiler est ouvert. Aucune trace n’a encore été ajoutée.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-sql-server-profiler-trace.png)

Pour ouvrir le fichier de trace, procédez comme suit :

1. Dans SQL Server Profiler, sélectionnez _Fichier > Ouvrir > Fichier de trace_.
2. Entrez le chemin d’accès du fichier de trace pour la session Power BI actuellement ouverte, par exemple : _\\\<Utilisateur>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data_
3. Ouvrir _FlightRecorderCurrent.trc_

Tous les événements de la session en cours sont affichés. Un exemple annoté est présenté ci-dessous, qui met en évidence les groupes d’événements. Chaque groupe comporte les éléments suivants :

- Des événements _Query Begin_ (Début de la requête) et _Query End_ (Fin de la requête) qui représentent le début et la fin d’une requête DAX générée par l’interface utilisateur (par exemple, à partir d’un visuel ou du remplissage d’une liste de valeurs dans l’interface utilisateur de filtre).
- Une ou plusieurs paires d’événements _DirectQuery Begin_ (Début de DirectQuery) et _DirectQuery End_ (Fin de DirectQuery), qui représentent une requête envoyée à la source de données sous-jacente, dans le cadre de l’évaluation de la requête DAX

Notez que plusieurs requêtes DAX pouvant être exécutées en parallèle, les événements de différents groupes peuvent être entrelacés. La valeur d’ID d’activité permet de déterminer les événements qui appartiennent à un même groupe.

![SQL Server Profiler est ouvert. Aucune trace n’a encore été ajoutée.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-sql-server-profiler-trace.png)

Les autres colonnes dignes d’intérêt sont les suivantes :

- **TextData :** détail textuel de l’événement. Pour les événements _Query Begin/End_, il s’agit de la requête DAX. Pour les événements _DirectQuery Begin/End_, il s’agit de la requête SQL envoyée à la source sous-jacente. La valeur de _TextData_ pour l’événement sélectionné est également affichée dans la zone inférieure.
- **EndTime :** heure de fin de l’événement.
- **Duration :** durée d’exécution de la requête DAX ou SQL, exprimée en millisecondes.
- **Error :** Indique si une erreur s’est produite, auquel cas l’événement s’affiche également en rouge.

Dans l’image ci-dessus, certaines colonnes moins intéressantes ont été rétrécies pour faciliter la visualisation des colonnes intéressantes.

L’approche recommandée pour la capture d’une trace afin de diagnostiquer un problème de performances potentiel est la suivante :

- Ouvrez une session Power BI Desktop (pour éviter les confusions possibles entre plusieurs dossiers de l’espace de travail).
- Effectuez l’ensemble des actions qui vous intéressent dans Power BI Desktop. Incluez ensuite quelques actions supplémentaires pour vous assurer que les événements intéressants sont vidés dans le fichier de trace.
- Ouvrez SQL Server Profiler, puis examinez la trace, comme décrit précédemment. Rappelez-vous que le fichier de trace est supprimé à la fermeture de Power BI Desktop. Par ailleurs, les actions supplémentaires effectuées dans Power BI Desktop n’apparaissent pas immédiatement : vous devez fermer puis réouvrir le fichier de trace pour voir les nouveaux événements.
- Conservez des sessions individuelles relativement peu volumineuses (10 secondes d’actions, pas des centaines) pour faciliter l’interprétation du fichier de trace (et la taille du fichier de trace étant limitée, pour les sessions longues il se peut que des événements du début soient supprimés).

## <a name="understand-queries-sent-to-the-source"></a>Comprendre les requêtes envoyées à la source

Le format général des requêtes générées et envoyées par Power BI Desktop utilise des sous-requêtes pour chacune des tables référencées du modèle, où la sous-requête est définie par la requête Power Query. Par exemple, supposons les tables TPC-DS suivantes dans une base de données relationnelle SQL Server :

![Un diagramme de la vue du modèle Power BI Desktop montre quatre tables, toutes liées entre elles. Les tables sont Item, Web_Sales, Customer et Date-dim.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-model-view-diagram.png)

Prenons le visuel suivant et sa configuration, en notant que la mesure **SalesAmount** est définie avec l’expression suivante :

```dax

SalesAmount = SUMX(Web_Sales, [ws_sales_price] * [ws_quantity])

```

![Un rapport Power BI Desktop se compose d’un histogramme empilé, montrant le montant des ventes par catégorie. Le volet Filtres indique un filtre sur l’année 2000.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-example-report.png)

L’actualisation de ce visuel produit la requête T-SQL présentée sous le paragraphe suivant. Comme vous pouvez le constater, il existe trois sous-requêtes pour les tables **Web_Sales**, **Item** et **Date_dim** du modèle. Chacune de ces tables retourne toutes les colonnes de la table du modèle, même si seules quatre colonnes sont réellement référencées par le visuel. Ces sous-requêtes (elles apparaissent en grisé) sont exactement la définition des requêtes de Power Query. L’utilisation de sous-requêtes de cette manière semble ne pas avoir d’incidence sur les performances en ce qui concerne les sources de données prises en charge jusqu’à présent pour DirectQuery. Des sources de données comme SQL Server optimisent les références aux colonnes inutilisées.

L’une des raisons pour lesquelles Power BI utilise ce modèle est que vous pouvez définir une requête Power Query pour utiliser une instruction de requête spécifique. Ainsi, elle est utilisée « en l’état », sans tentative de réécriture. Notez que ces modèles restreignent l’utilisation des instructions de requête qui utilisent des expressions de table communes et des procédures stockées. Ces instructions ne peuvent pas être utilisées dans les sous-requêtes.

![Une requête T-SQL très détaillée affiche des sous-requêtes incorporées, une pour chaque table du modèle.](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-example-query.png)

## <a name="gateway-performance"></a>Performances de la passerelle

Pour plus d’informations sur la résolution des problèmes de performances de la passerelle, lisez l’article [Résoudre les problèmes liés aux passerelles - Power BI](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur DirectQuery, consultez les ressources suivantes :

- [Utiliser DirectQuery dans Power BI Desktop](desktop-use-directquery.md)
- [Modèles DirectQuery dans Power BI Desktop](desktop-directquery-about.md)
- [Aide sur le modèle DirectQuery dans Power BI Desktop](guidance/directquery-model-guidance.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
