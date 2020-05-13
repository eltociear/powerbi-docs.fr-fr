---
title: Surveiller les performances du rapport dans Power BI
description: Conseils sur la surveillance des performances du rapport dans Power BI.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 9245dd6c25917b2c8c861ea5b83710cd8b52bb22
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279017"
---
# <a name="monitor-report-performance-in-power-bi"></a>Surveiller les performances du rapport dans Power BI

Surveillez les performances des rapports dans Power BI Desktop à l’aide de l’[application Power BI Premium Metrics](../admin/service-premium-metrics-app.md), découvrez où se trouvent les goulots d’étranglement et apprenez à améliorer les performances des rapports.

La surveillance des performances est utile dans les cas suivants :

- L’actualisation de l’importation de votre modèle de données est lente.
- Vos rapports DirectQuery ou Live Connection sont lents.
- Vos calculs de modèle sont lents.

Les éléments visuels de requêtes ou de rapports lents doivent être au cœur de l’optimisation continue.

## <a name="use-query-diagnostics"></a>Utiliser Diagnostic de requête

Utilisez [Diagnostic de requête](/power-query/QueryDiagnostics) dans Power BI Desktop pour déterminer ce que Power Query fait lors de l’aperçu ou de l’application des requêtes. En outre, utilisez la fonction _Diagnostiquer l'étape_ pour enregistrer des informations d’évaluation détaillées pour chaque étape de la requête. Les résultats sont rendus disponibles dans Power Query et vous pouvez appliquer des transformations pour mieux comprendre l’exécution des requêtes.

> [!NOTE]
> Le diagnostic des requêtes étant actuellement une fonctionnalité d’évaluation, vous devez l’activer dans _Options et paramètres_. Une fois activée, ses commandes sont disponibles dans la fenêtre de l’Éditeur Power Query, sous l’onglet du ruban **Outils**.

![L’image affiche l’onglet du ruban Outils de l’Éditeur Power Query. Le ruban affiche la commande Diagnostiquer l’étape, la commande Démarrer le diagnostic et la commande Arrêter le Diagnostic.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>Utiliser l’Analyseur de performances

Utilisez [Analyseur de performances](../create-reports/desktop-performance-analyzer.md) dans Power BI Desktop pour découvrir comment se comportent chacun de vos éléments de rapport, tels que les éléments visuels et les formules DAX. Il est particulièrement utile de déterminer si les problèmes de performances sont dus à la requête ou au rendu visuel.

## <a name="use-sql-server-profiler"></a>Utiliser SQL Server Profiler

Vous pouvez également utiliser [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) pour identifier les requêtes lentes.

> [!NOTE]
> SQL Server Profiler est disponible dans le cadre de [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

Utilisez SQL Server Profiler lorsque votre source de données est :

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop prend en charge la connexion à un port de diagnostic. Le port de diagnostic permet à d’autres outils de se connecter afin d’effectuer des rapports des appels de procédure pour établir un diagnostic. La modification du modèle de données Power Desktop n’est pas prise en charge. Les modifications apportées au modèle de données peuvent entraîner une altération et une perte de données.

Pour créer un rapport des appels de procédure SQL Server Profiler trace, suivez les instructions ci-dessous :

1. Ouvrez votre rapport de Power BI Desktop (il sera donc facile de localiser le port à l’étape suivante, puis de fermer tous les autres rapports ouverts).
1. Pour déterminer le port utilisé par Power BI Desktop, dans PowerShell (avec des privilèges d’administrateur), ou à l’invite de commandes, entrez la commande suivante :
    ```powershell
    netstat -b -n
    ```
    Le résultat doit être une liste d’applications et leurs ports ouverts. Recherchez le port utilisé par **msmdsrv.exe** et enregistrez-le pour la suite. Il s’agit de votre instance Power BI Desktop.
1. Pour connecter SQL Server Profiler à votre rapport Power BI Desktop :
    1. Ouvrez SQL Server Profiler.
    1. Dans SQL Server Profiler, dans le menu _Fichier_, sélectionnez _Nouveau rapport des appels de procédure_.
    1. Dans **Type de serveur**, sélectionnez _Analysis Services_.
    1. Dans **Nom du serveur**, entrez _localhost:[port recorded earlier]_ .
    1. Cliquez sur _exécuter_ : à présent, le rapport des appels de procédure SQL Server Profiler est actif et le profilage des requêtes Power BI Desktop est actif.
1. À mesure que les requêtes Power BI Desktop sont exécutées, vous verrez leur durée respective et les temps UC. Selon le type de source de données, vous pouvez voir d’autres événements indiquant comment la requête a été exécutée. À l’aide de ces informations, vous pouvez déterminer quelles requêtes sont des goulots d’étranglement.

L’un des avantages de l’utilisation de SQL Server Profiler est qu’il est possible d’enregistrer un rapport des appels de procédure de base de données SQL Server (relationnel). Le rapport des appels de procédure peut devenir une entrée de l'[Assistant Paramétrage du moteur de base de données](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor). De cette façon, vous pouvez recevoir des suggestions sur la manière de paramétrer votre source de données.

## <a name="monitor-premium-metrics"></a>Surveiller les mesures Premium

Pour les capacités Power BI Premium, utilisez l’**application Power BI Premium Metrics** pour gérer l’intégrité et la capacité de votre abonnement Power BI Premium. Pour plus d’informations, consultez l’[application Power BI Premium Metrics](../admin/service-premium-metrics-app.md).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur cet article, consultez les ressources suivantes :

- [Diagnostic de requête](/power-query/QueryDiagnostics)
- [Analyseur de performances](../create-reports/desktop-performance-analyzer.md)
- [Résoudre les problèmes de performances de rapports dans Power BI](report-performance-troubleshoot.md)
- [Application Power BI Premium Metrics](../admin/service-premium-metrics-app.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
