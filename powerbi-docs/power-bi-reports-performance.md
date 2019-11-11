---
title: Bonnes pratiques relatives aux performances de Power BI
description: Cet article fournit des conseils relatifs à la création de rapports fiables et rapides dans Power BI
author: Bhavik-MSFT
ms.author: bhmerc
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/30/2018
LocalizationGroup: Reports
ms.openlocfilehash: 2fd0a3d878641264e84a14579901a9685b0f6e8b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875110"
---
# <a name="power-bi-performance-best-practices"></a>Bonnes pratiques relatives aux performances de Power BI

Cet article fournit des conseils relatifs à la création de rapports fiables et rapides dans Power BI.  

## <a name="choose-an-appropriate-storage-mode-import-directquery"></a>Choisissez un mode de stockage approprié : Import, DirectQuery

Dans la plupart des cas, le mode Import est le meilleur choix, car il offre la vitesse la plus élevée en tirant parti des données en mémoire cache localement compressées avec le stockage en colonnes. Le mode Import permet également des fonctionnalités DAX complètes. Envisagez DirectQuery (et les modèles composites) quand le volume de données source est trop grand pour votre capacité Power BI. DirectQuery est également utile lorsque vous devez récupérer les données les plus récentes à partir de la source chaque fois qu’un rapport est chargé. Si vous ne répondez pas à ces exigences et que les utilisateurs doivent uniquement voir les données qui sont mises à jour un petit nombre de fois par jour (par exemple, à partir d’un entrepôt de données d’entreprise), Import est fortement recommandé. En mode DirectQuery, les utilisateurs pourraient essayer d’actualiser le rapport sans se rendre compte qu’ils récupèrent exactement les mêmes données à partir de la source.      

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>Utiliser des filtres pour limiter l’affichage des éléments visuels de rapport au strict nécessaire 

Plus un élément visuel contient de données à afficher, plus son chargement est lent. Si ce principe semble évident, on a tendance à l’oublier. Par exemple, supposons que vous avez un jeu de données volumineux, à partir duquel vous créez un rapport avec une table de la table. Les utilisateurs finaux utilisent les segments sur la page pour accéder aux lignes qui les intéressent, généralement pas plus de quelques dizaines.

Une erreur courante consiste à utiliser la vue par défaut de la table non filtrée, soit la totalité des quelques 100 millions de lignes. Les données de ces lignes sont chargées en mémoire et décompressées à chaque actualisation. Ce traitement impose des charges énormes à la mémoire. La solution consiste à réduire le nombre maximal d’éléments à afficher dans la table à l’aide du filtre « N premiers ». Vous pouvez définir un nombre maximal d’éléments supérieur à ce dont les utilisateurs peuvent avoir besoin, par exemple 10 000. Le résultat est que l’expérience de l’utilisateur final ne change pas, mais que l’utilisation de la mémoire chute considérablement. Et les performances s’améliorent.

Une approche similaire à celle-ci est recommandée pour tous les visuels de vos rapports. Demandez-vous si toutes les données présentes dans l’élément visuel sont nécessaires. Est-il possible de réduire la quantité de données affichées sur le visuel d’une manière ou d’une autre sans gêner l’utilisateur ? Les tables peuvent être coûteuses.

## <a name="limit-visuals-on-report-pages"></a>Limiter le nombre d’éléments visuels sur les pages de rapport

Le principe ci-dessus s’applique également au nombre d’éléments visuels sur les rapports. Il est fortement recommandé de limiter le nombre de visuels sur un rapport au strict nécessaire. Les pages d’extraction permettent d’ajouter des détails supplémentaires au rapport sans accumuler les éléments visuels.  

## <a name="optimize-your-model"></a>Optimiser votre modèle

Bonnes pratiques :

- Supprimez autant que possible les tables ou colonnes inutilisées. 
- Évitez les comptes distincts de champs avec une cardinalité élevée (soit des millions de valeurs distinctes).  
- Faites en sorte d’éviter les champs présentant une précision inutile et une cardinalité élevée. Vous pouvez par exemple fractionner les valeurs DateHeure uniques en différentes colonnes (par exemple : mois, année, date, etc). Vous pouvez également, dans certains cas, arrondir les champs à haute précision à la cardinalité inférieure (par exemple : 13,29889 -> 13,3).
- Utilisez des entiers à la place des chaînes dès que possible.
- Méfiez-vous des fonctions DAX, qui nécessitent de tester chaque ligne d’une table (par exemple RANKX). Dans le pire des cas, ces fonctions peuvent augmenter de manière exponentielle les exigences d’exécution et de mémoire en raison des augmentations linéaires de la taille de la table.
- Lors de la connexion à des sources de données via DirectQuery, envisagez d’indexer les colonnes qui sont généralement filtrées ou resegmentées. L’indexation améliore considérablement la réactivité du rapport.  

Pour plus d’informations sur l’optimisation des sources de données pour DirectQuery, voir [DirectQuery dans SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/).

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>Connexion DirectQuery et active : comprendre les performances de source de données sous-jacente

Dans le cas des connexions DirectQuery ou actives, lorsque les utilisateurs consultent un rapport Power BI, Power BI envoie des requêtes en temps réel à la source de données sous-jacente. Une fois que la source de données renvoie les données de la requête, le rapport est rendu. Par conséquent, les performances de votre rapport dépendent largement de celles de la source de données sous-jacente.

Il est alors important de comprendre les performances de votre source de données sous-jacente. Différentes sources de données disposent de différents outils pour comprendre les performances des requêtes. Par exemple, SQL Server et Azure SQL fournissent le Magasin de données des requêtes, qui capture un historique des requêtes et leurs statistiques d’exécution.

Lors du déploiement de rapports Power BI créés à partir de connexions actives et DirectQuery, testez les actions de vos utilisateurs finaux dans Power BI Desktop. Si le chargement du rapport dans Power BI Desktop est lent, il le sera probablement aussi dans le service pour vos utilisateurs finaux. 

## <a name="directquery-best-practices"></a>Bonnes pratiques relatives à DirectQuery

La section suivante décrit les bonnes pratiques générales relatives à la connexion via DirectQuery.

### <a name="db-design-guidance"></a>Aide à la conception d’une base de données

- Envoyez les colonnes calculées et les mesures à la source quand c’est possible. Plus la source est proche, plus la probabilité de bonnes performances est élevée.
- Optimisez ! Étudiez les plans d’exécution pour vos requêtes, ajoutez des indices pour les colonnes souvent filtrées, etc.

### <a name="modeling-guidance"></a>Conseils de modélisation

- Commencez dans Power BI Desktop.
- Évitez les requêtes complexes dans l’Éditeur de requête.
- N’utilisez pas de filtrage de date relative dans l’Éditeur de requête.  
- Commencez par des mesures simples, puis ajoutez progressivement de la complexité.
- Évitez les relations sur les colonnes calculées et les colonnes d’identificateur unique.
- Essayez de définir l’option « Intégrité référentielle supposée » sur les relations. Dans de nombreux cas, cela peut considérablement améliorer les performances des requêtes.  

### <a name="general"></a>Général

- Appliquez les filtres en premier lieu.
- Envisagez de désactiver l’interaction entre les éléments visuels. Cela permet de réduire la charge de requête quand les utilisateurs effectuent des sélections croisées.
- Limitez le nombre d’éléments visuels et de données par élément visuel, comme décrit ci-dessus.
- L’activation de la sécurité au niveau des lignes peut entraîner des changements importants sur le plan des performances. Veillez à tester les différents rôles de sécurité au niveau des lignes que vos utilisateurs vont assumer.
- Des délais d’expiration de requête sont appliqués par le service pour que les requêtes longues ne monopolisent pas les ressources système. Les requêtes qui dépassent 225 secondes expirent et entraînent une erreur au niveau du visuel.

## <a name="understand-dashboards-and-query-caches"></a>Comprendre les tableaux de bord et les caches de requête

Les visuels épinglés aux tableaux de bord sont pris en charge par le cache de requête lors du chargement du tableau de bord. À l’inverse, lors de la consultation d’un rapport, les requêtes sont immédiatement envoyées à la source de données : soit le service Power BI (dans le cas d’une importation), soit la source de données que vous spécifiez (dans le cas d’une connexion active ou DirectQuery).  

> [!NOTE]
> Lorsque vous épinglez des vignettes de rapport dynamiques à un tableau de bord, elles ne sont pas prises en charge à partir du cache de requête : elles se comportent comme des rapports et envoient immédiatement des requêtes aux serveurs principaux.

Comme son nom l’indique, la récupération de données à partir du cache de requête offre des performances supérieures et plus cohérentes que par la source de données. Pour tirer parti de cette fonctionnalité, vous pouvez notamment définir les tableaux de bord comme page d’accueil pour vos utilisateurs. Épinglez les éléments visuels les plus utilisés et demandés aux tableaux de bord. Les tableaux de bord deviennent ainsi une « première ligne de défense » utile qui offre des performances cohérentes et une charge moindre sur la capacité. Les utilisateurs peuvent cliquer pour accéder au rapport afin de consulter les détails.  
 

Pour les connexions actives et DirectQuery, le cache de requête est mis à jour régulièrement en interrogeant la source de données. Par défaut, cela se produit toutes les heures, mais la fréquence peut être configurée dans les paramètres du jeu de données. Chaque mise à jour du cache de requête envoie des requêtes à la source de données sous-jacente pour mettre à jour le cache. Le nombre de requêtes générées dépend du nombre de visuels épinglés aux tableaux de bord qui dépendent de cette source de données. Notez que si la sécurité au niveau des lignes est activée, les requêtes sont générées pour chaque contexte de sécurité différent. Par exemple, si vos utilisateurs relèvent de deux rôles différents, présentant chacun un affichage différent des données, lors de l’actualisation du cache de requête, Power BI génère deux jeux de requêtes. 

## <a name="understand-custom-visual-performance"></a>Comprendre les performances des éléments visuels personnalisés 

Pour garantir des performances élevées, veillez à mettre à l’épreuve chaque élément visuel personnalisé. Les éléments visuels personnalisés mal optimisés peuvent diminuer les performances de l’intégralité du rapport. 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>Présentation détaillée des performances de requêtes avec SQL Profiler et Power BI Desktop

Pour découvrir plus en détail quels éléments visuels consomment le plus de temps et de ressources, vous pouvez connecter SQL Profiler à Power BI Desktop afin d’obtenir une présentation complète des performances de requête.

> [!NOTE]
> Power BI Desktop prend en charge la connexion à un port de diagnostic. Le port de diagnostic permet à d’autres outils de se connecter et d’effectuer des suivis pour établir un diagnostic. *L’apport de changements au modèle n’est pas pris en charge ! Les changements apportés au modèle peuvent entraîner une altération et une perte de données.*

La procédure est la suivante :
  
1. **Installer SQL Server Profiler et exécuter Power BI Desktop**

   SQL Server Profiler est disponible dans le cadre de SQL Server Management Studio.

2. **Déterminer le port utilisé par Power BI Desktop**

   Exécutez l’invite de commandes ou PowerShell avec des privilèges d’administrateur. Et utilisez netstat pour rechercher le port que Power BI Desktop utilise pour l’analyse :

   `> netstat -b -n`

   Le résultat doit être une liste d’applications et leurs ports ouverts, par exemple :  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   Recherchez le port utilisé par msmdsrv.exe et notez-le pour la suite. Dans cet exemple, vous utilisez le port 55786.
3. **Connecter SQL Server Profiler à Power BI Desktop**

   - Démarrez SQL Server Profiler à partir du menu **Démarrer**
   - **Fichier** > **Nouvelle trace**
   - Type de serveur : Analysis Services
   - Nom du serveur : localhost:[numéro de port identifié précédemment]
   - Sur l’écran suivant, sélectionnez **Exécuter**
   - SQL Server Profiler est maintenant actif et étudie activement les requêtes envoyées par Power BI Desktop. 
   - Lorsque les requêtes sont exécutées, vous pouvez voir la durée et le temps processeur correspondants, qu permettent d’identifier les requêtes qui constituent des goulots d’étranglement.  

Le Générateur de profils SQL Server vous permet d’identifier les requêtes qui monopolisent le plus de temps processeur. Il s’agit probablement de celles qui entraînent des goulots d’étranglement des performances. Les visuels qui exécutent ces requêtes doivent être au cœur de l’optimisation continue.

## <a name="gateway-best-practices"></a>Bonnes pratiques relatives à la passerelle

La passerelle de données locale est un excellent outil pour connecter le service Power BI à vos données locales. En revanche, une planification insuffisante peut également en faire un goulot d’étranglement pour les performances du rapport. C’est notamment le cas pour les jeux de données avec connexion DirectQuery/active, pour lesquels toutes les requêtes et les réponses aux requêtes passent par la passerelle. Voici quelques recommandations permettant de s’assurer des bonnes performances des passerelles : 

- **Utilisez le mode Entreprise**, plutôt que le mode Personnel.
- **Spécifications matérielles recommandées pour la passerelle :** 8 cœurs de processeur, 16 Go de RAM.
- **Paramétrez l’analyse :** paramétrez l’analyse des performances sur l’ordinateur dédié à la passerelle pour détecter les surcharges et voir si la passerelle devient un goulot d’étranglement. Pour plus d’informations, consultez [Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md).
- **Mettez à l’échelle :** si la passerelle constitue effectivement un goulot d’étranglement, envisagez de monter en charge (c’est-à-dire déplacer la passerelle vers un ordinateur plus puissant doté d’un processeur et d’une mémoire RAM supérieurs) ou de monter en charge (par exemple, répartir les jeux de données sur différentes passerelles). 
- **Importation séparée et DirectQuery :** si vous montez en charge, envisagez de séparer les passerelles responsables de l’importation de celles responsables de DirectQuery.

## <a name="network-latency"></a>Latence du réseau

La latence du réseau peut affecter les performances du rapport en augmentant le temps nécessaire aux demandes pour atteindre le service Power BI et aux réponses pour être envoyées. Les clients dans Power BI sont affectés à une région spécifique. Pour connaître la région « accueil » de votre client, accédez à powerbi.com et sélectionnez **?** dans l’angle supérieur droit, puis **À propos de Power BI**. Lorsque les utilisateurs d’un client accèdent au service Power BI, leurs requêtes sont acheminées vers cette région. Lorsque les requêtes atteignent le service Power BI, celui-ci peut ensuite envoyer des requêtes supplémentaires (par exemple, à la source de données sous-jacente ou à la passerelle) qui sont également soumises à la latence du réseau.

Des outils tels que [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) donnent une indication de la latence du réseau entre le client et la région Azure. De manière générale, pour minimiser l’impact de la latence du réseau, essayez de rapprocher le plus possible les sources de données, les passerelles et votre cluster Power BI. Si la latence du réseau pose problème, essayez de rapprocher les passerelles et les sources de données de votre cluster Power BI en les plaçant sur des machines virtuelles.

Pour améliorer la latence du réseau, envisagez d’utiliser [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/), qui est capable de créer des connexions réseau plus rapides et plus fiables entre vos clients et les centres de données Azure.

## <a name="next-steps"></a>Étapes suivantes

- [Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy) : guide complet sur les déploiements de Power BI à grande échelle
- [DirectQuery dans SQL Server 2016 Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] Création de rapports fiables et rapides dans Power BI](https://www.youtube.com/watch?v=GhiJABR7XX0)
- [[YouTube] Déploiements de Power BI en entreprise](https://www.youtube.com/watch?v=K-zEWICvICM)
