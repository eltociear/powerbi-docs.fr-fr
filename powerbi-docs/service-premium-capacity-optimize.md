---
title: Optimiser les capacités de Microsoft Power BI Premium
description: Décrit les stratégies d’optimisation pour les capacités Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565333"
---
# <a name="optimizing-premium-capacities"></a>Optimisation des capacités Premium

En cas de problèmes de performances de capacité Premium, une première approche commune consiste à optimiser ou de régler vos solutions pour restaurer les temps de réponse acceptable. Le raisonnement à éviter d’acheter une capacité Premium supplémentaire, sauf si justifié.

Quand une capacité Premium supplémentaire est nécessaire, il existe deux options décrites dans cet article :

- Montée en charge une capacité Premium existante
- Ajouter une nouvelle capacité Premium

Enfin, test approches et dimensionnement de capacité Premium concluent cet article.

## <a name="best-practices"></a>Meilleures pratiques

Lorsque vous tentez d’obtenir des taux d’utilisation et des performances optimales, il existe quelques pratiques recommandées, y compris :

- À l’aide des espaces de travail d’application au lieu d’espaces de travail personnels.
- La séparation critique pour l’entreprise et analyse Décisionnelle libre-service (SSBI) en différentes capacités.

  ![La séparation des critique pour l’entreprise et analyse Décisionnelle libre-service en différentes capacités](media/service-premium-capacity-optimize/separate-capacities.png)

- Si le partage de contenu uniquement avec les utilisateurs de Power BI Pro, vous êtes peut-être pas nécessaire de stocker le contenu dans une capacité dédiée.
- Utiliser les capacités dédiées lors de la recherche pour obtenir une durée spécifique d’actualisation, ou lorsque des fonctionnalités spécifiques sont requises. Par exemple, avec les jeux de données volumineux ou de création de rapports paginés.

### <a name="addressing-common-questions"></a>Adressage des questions courantes

Optimisation des déploiements de Power BI Premium est un sujet complexe impliquant une compréhension des exigences de charge de travail, les ressources disponibles et leur utilisation efficace.

Cet article traite des sept questions de support courantes, décrivant les problèmes possibles et des explications et des informations sur la façon d’identifier et de les résoudre.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Pourquoi est la capacité lente, et que puis-je faire ?

Il existe de nombreuses raisons qui peuvent contribuer à une capacité Premium lente. Cette question requiert davantage d’informations pour comprendre ce que signifie le terme lente. Rapports de chargement est lent ? Ou ils échouent à charger ? Visuels de rapport sont lentes à charger ou mettre à jour lorsque les utilisateurs interagissent avec le rapport ? Sont actualisées prend plus de temps que prévu ou rencontré au préalable des ?

Avoir acquis une compréhension de la raison, vous pouvez ensuite commencer à examiner. Réponses aux questions suivantes six vous aidera à résoudre plusieurs problèmes spécifiques.

### <a name="what-content-is-using-up-my-capacity"></a>Le contenu qui est à l’aide de ma capacité ?

Vous pouvez utiliser la **métriques de capacité Power BI Premium** application à filtrer par capacité et consulter les mesures de performances pour le contenu de l’espace de travail. Il est possible passer en revue l’utilisation de métriques et les ressources de performances par heure au cours des sept derniers jours pour tout le contenu stocké au sein d’une capacité Premium. Surveillance est souvent la première action à effectuer lors du dépannage d’une inquiétude d’ordre général sur les performances de capacité Premium.

Les métriques clés à surveiller sont les suivantes :

- Moyenne du processeur et le nombre de l’utilisation élevée.
- Moyenne de mémoire et une utilisation élevée du nombre et utilisation de la mémoire pour les jeux de données spécifiques, les flux de données et les rapports paginés.
- Jeux de données active sont chargées en mémoire.
- Durées de requête moyenne et maximale.
- Temps d’attente moyenne des requêtes.
- Flux de données et le jeu de données moyen actualiser fois.

Dans l’application de métriques de capacité Power BI Premium, la mémoire active affiche la quantité totale de mémoire affectée à un rapport qui ne peut pas être supprimé, car il a été utilisé au cours des trois dernières minutes. Un pic élevé dans le temps d’attente de l’actualisation peut être mis en corrélation avec un jeu de données de grande taille et/ou très active.

Le **Top 5 par durée moyenne** graphique met en évidence les cinq premiers jeux de données, rapports paginés et flux de données consomme des ressources de capacité. Contenu dans les cinq premiers listes est candidats pour l’optimisation d’investigation et possible.

### <a name="why-are-reports-slow"></a>Pourquoi les rapports lent ?

Les tableaux suivants indiquent les problèmes potentiels et les façons d’identifier et de les gérer.

#### <a name="insufficient-capacity-resources"></a>Ressources de capacité insuffisante

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Total élevée de la mémoire active (modèle ne peut pas être supprimé, car il est en cours d’utilisation au cours des trois dernières minutes).<br><br> Temps d’attente plusieurs pics haute dans la requête.<br><br> Temps d’attente plusieurs pics élevés dans l’actualisation. | Surveiller les métriques de la mémoire \[ [1](#endnote-1)\]et le nombre d’éviction \[ [2](#endnote-2)\]. | Diminuer la taille du modèle, ou convertissez le mode DirectQuery. Consultez le [optimisation des modèles](#optimizing-models) dans cet article.<br><br> Monter en puissance la capacité.<br><br> Affecter le contenu à une autre capacité. |

#### <a name="inefficient-report-designs"></a>Conceptions de rapport inefficace

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Pages de rapport contiennent trop de visuels (filtrage interactif peut déclencher au moins une requête par visuel).<br><br> Éléments visuels récupérer plus de données que nécessaire. | Passez en revue les conceptions de rapport.<br><br> Les utilisateurs de rapport pour comprendre la façon dont ils interagissent avec les rapports qui contient un entretien.<br><br> Surveiller les métriques de requête de dataset \[ [3](#endnote-3)\]. | Nouvelle conception des rapports avec moins de visuels par page. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Jeu de données est lente, en particulier lorsque les rapports précédemment suffi

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Volumes de plus en plus grands de données d’importation.<br><br> Logique de calcul complexe ou inefficace, y compris les rôles RLS.<br><br> Modèle pas entièrement optimisée.<br><br> (DQ/LC) Latence de la passerelle.<br><br> DQ source requête réponse lents. | Passez en revue les conceptions de modèle.<br><br> Surveiller les compteurs de performances de passerelle. | Consultez le [optimisation des modèles](#optimizing-models) dans cet article. |

#### <a name="high-concurrent-report-usage"></a>Utilisation des rapports simultanées haute

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Temps d’attente élevées pour les requêtes.<br><br> Saturation de l’UC.<br><br> Limites de connexion DQ/LC dépassées. | Surveiller l’utilisation du processeur \[ [4](#endnote-4)\], temps d’attente de requête et l’utilisation de DQ/LC \[ [5](#endnote-5) \] métriques + durée des requêtes. Si fluctue, peut indiquer des problèmes d’accès concurrentiel. | La capacité de montée en charge, ou affecter le contenu à une autre capacité.<br><br> Nouvelle conception des rapports avec moins de visuels par page. |

**Remarques :**    
<a name="endnote-1"></a>\[1\] moyenne d’utilisation de la mémoire (Go) et la consommation de mémoire la plus élevée (en Go).   
<a name="endnote-2"></a>\[2\] Évictions de jeu de données.   
<a name="endnote-3"></a>\[3\] requêtes de Dataset, durée moyenne de jeu de données de la requête (ms), jeu de données attendre le nombre et le temps d’attente moyenne du jeu de données (ms).   
<a name="endnote-4"></a>\[4\] nombre de l’utilisation du processeur élevé et de temps processeur de l’utilisation la plus élevée (sept derniers jours).   
<a name="endnote-5"></a>\[5\] DQ/LC haute l’utilisation du nombre et l’heure DQ/LC de meilleurs taux d’utilisation (sept derniers jours).   

### <a name="why-are-reports-not-loading"></a>Pourquoi les rapports n’est ne pas chargé ?

Lors de l’échouent du chargement des rapports, il est un signe que la capacité mémoire est insuffisante et qu’il est trop chauffe. Cela peut se produire lorsque tous les modèles chargés sont interrogés activement et par conséquent, ne peut pas être supprimés, et toute opération d’actualisation ont été suspendue ou retardée. Le service Power BI tente de charger le jeu de données pendant 30 secondes, et l’utilisateur est prévenu normalement de l’échec avec une suggestion pour essayer à nouveau peu de temps.

Il n’existe actuellement aucune métrique pour surveiller les échecs de chargement des rapports. Vous pouvez identifier le risque de ce problème en analyse mémoire système, en particulier la plus élevée l’utilisation et l’heure de la plus forte utilisation. Évictions de jeu de données haute et la durée pendant laquelle les temps d’attente moyen dataset actualisation peuvent suggérer que ce problème se produit.

Si cela se produit très occasionnellement, cela n’est pas un problème prioritaire. Les utilisateurs de rapport sont informés que le service est occupé et qu’ils doivent retenter après une courte période. Si cela se produit trop souvent, le problème peut être résolu en augmentant la capacité Premium ou en assignant le contenu à une autre capacité.

La capacité administrateurs (Power BI et les administrateurs de service) peut surveiller le **échecs de requêtes** métrique pour déterminer quand cela se produit. Ils peuvent également redémarrer la capacité, la réinitialisation de toutes les opérations en cas de surcharge du système.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Pourquoi sont actualisations ne démarre pas sur la planification ?

Heures de début de l’actualisation planifiée ne sont pas garantis. Rappelez-vous que le service Power BI sera toujours donner la priorité opérations interactives sur des opérations d’arrière-plan. L’actualisation est une opération d’arrière-plan qui peut se produire lorsque les deux conditions sont remplies :

- Il existe suffisamment de mémoire
- Le nombre d’actualisations de simultanées prises en charge pour la capacité Premium n’est pas dépassé

Lorsque les conditions ne sont pas remplies, l’actualisation est en file d’attente jusqu'à ce que les conditions sont favorables.

Pour une actualisation complète, rappelez-vous qu’au moins le double la taille de mémoire de jeu de données actuelle est requise. Si suffisamment de mémoire n’est pas disponible, l’actualisation ne peut pas commencer tant que l’éviction de modèle libère la mémoire : cela signifie que des délais jusqu'à ce qu’un ou plusieurs jeux de données devient inactive et peut être supprimée.

Rappelez-vous que le nombre pris en charge des actualisations simultanées maximales est défini à 1,5 fois les v-cores principaux, arrondis par excès.

Une actualisation planifiée échoue lorsqu’il ne peut pas commencer avant l’échéance de commencer la prochaine actualisation planifiée. Une actualisation à la demande déclenchée manuellement à partir de l’interface utilisateur tente d’exécuter jusqu'à trois fois avant d’échouer.

La capacité administrateurs (Power BI et les administrateurs de service) peut surveiller le **actualiser les temps d’attente moyen (en minutes)** métrique pour déterminer la moyenne décalage entre l’heure planifiée et le début de l’opération.

Pendant que ne sont généralement pas une priorité d’administration, avoir une influence sur les données à l’heure actualise, assurez-vous que suffisamment de mémoire est disponible. Cela peut impliquer d’isoler les jeux de données à des capacités avec suffisamment de ressources connus. Il est également possible que les administrateurs peuvent coordonner avec les propriétaires de jeu de données pour aider à échelonner ou de réduire les temps d’actualisation planifiée des données afin de réduire les collisions. Notez qu’il n’est pas possible pour un administrateur pour afficher la file d’attente de l’actualisation, ou pour récupérer des planifications de jeu de données.

### <a name="why-are-refreshes-slow"></a>Pourquoi les actualisations lente ?

Actualisations peuvent être lente - ou perçues lente (comme les adresses de question commune précédente).

Lorsque l’actualisation est en fait lente, il peut être dû à plusieurs raisons :

- Processeur insuffisantes (actualisation peut être très sollicitant beaucoup le processeur).
- Mémoire insuffisante, entraînant la suspension d’actualisation (qui nécessite l’actualisation de repartir de zéro lorsque les conditions sont favorables de recommencer).
- Raisons de capacité non, notamment la réactivité du système source de données, latence du réseau, des autorisations non valides ou le débit de passerelle.
- Volume de données - une bonne raison pour configurer incrémentielle d’actualisation, comme indiqué ci-dessous.

La capacité administrateurs (Power BI et les administrateurs de service) peut surveiller le **durée moyenne d’actualisation (minutes)** métrique pour déterminer un point de référence pour la comparaison au fil du temps et le **actualiser les temps d’attente moyen (en minutes)** mesures pour déterminer le délai moyen entre moyenne de décalage entre l’heure planifiée et le début de l’opération.

Actualisation incrémentielle peut réduire considérablement la durée d’actualisation des données, en particulier pour les tables de modèle de grande taille. Il existe quatre avantages associés à l’actualisation incrémentielle :

- **Actualisations sont plus rapides** - uniquement un sous-ensemble d’une table doit réduire le chargement utilisation du processeur et mémoire, et parallélisme peut être plus élevé lors de l’actualisation de plusieurs partitions.
- **Actualisations ont lieu uniquement lorsque nécessaire** -stratégies d’actualisation incrémentielle peuvent être configurés pour charger uniquement lorsque les données ont changé.
- **Actualisations sont plus fiables** -des connexions en cours d’exécution plus courtes pour les systèmes de source de données volatiles sont moins vulnérables à une déconnexion.
- **Modèles restent trim** -stratégies d’actualisation incrémentielle peuvent être configurés pour supprimer automatiquement l’historique au-delà d’une fenêtre glissante de temps.

Pour plus d’informations, consultez [incrémentiel d’actualisation dans Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Pourquoi sont données actualise se terminent ne pas ?

Lorsque l’actualisation des données commence, mais ne parvient pas à terminer, il peut être dû à plusieurs raisons :

- Insuffisance de mémoire, même s’il existe un seul modèle de la capacité Premium, par exemple, la taille du modèle est très élevée.
- Raisons de capacité non, notamment la déconnexion de source de données système, des autorisations non valides ou erreur de passerelle.

La capacité administrateurs (Power BI et les administrateurs de service) peut surveiller le **actualiser échecs en raison de mémoire insuffisante** métrique.

## <a name="optimizing-models"></a>Optimisation des modèles

Conception de modèle optimal est cruciale pour fournir une solution efficace et évolutive. Toutefois, il est abordée dans cet article pour fournir une description complète. Au lieu de cela, cette section fournit les zones clés à prendre en compte lors de l’optimisation des modèles.

### <a name="optimizing-power-bi-hosted-models"></a>Optimisation Power BI hébergés de modèles

Optimisation des modèles hébergés dans une capacité Premium peut être obtenue au niveau des couches datasource(s) et le modèle.

Prenez en compte les possibilités d’optimisation pour un modèle d’importation :

![Possibilités d’optimisation pour un modèle d’importation](media/service-premium-capacity-optimize/import-model-optimizations.png)

Au niveau de la couche source de données :

- Sources de données relationnelles peuvent être optimisés pour garantir l’actualisation possible le plus rapide en avant l’intégration des données, l’appliquant des index appropriés, définition des partitions de table qui correspondent aux périodes d’actualisation incrémentielle et matérialisation des calculs (à la place de calculées tables et colonnes de modèle) ou l’ajout de la logique de calcul à des vues.
- Sources de données non relationnelles peuvent être intégrées préalablement avec des magasins relationnels.
- Assurez-vous que les passerelles ont suffisamment de ressources, de préférence sur des ordinateurs dédiés, avec suffisamment de bande passante réseau et à proximité les sources de données.

Au niveau de la couche de modèle :

- Conceptions de requête de Power Query peuvent réduire ou supprimer des transformations complexes et en particulier ceux qui fusionnent les différentes sources de données (entrepôts de données parvenir pendant leur étape d’extraction, transformation et chargement). En outre, garantir des niveaux de confidentialité cette source de données appropriée sont définies, vous éviterez ainsi nécessitant Power BI charger les résultats complets pour produire un résultat combiné entre les requêtes.
- La structure du modèle détermine les données à charger et a un impact direct sur la taille du modèle. Il peut être conçu pour éviter de charger les données inutiles en supprimant des colonnes, en supprimant les lignes (en particulier les données historiques) ou en chargeant des données résumées (aux dépens de chargement des données détaillées). Réduction de taille considérable peut être obtenue en supprimant des colonnes de cardinalité élevée (en particulier les colonnes de texte) qui ne pas stocker ou compresser très efficacement.
- Performances des requêtes de modèle peuvent être améliorées en configurant les relations de direction à sens unique, sauf s’il existe une bonne raison pour permettre le filtrage bidirectionnel. Envisagez d’utiliser également le [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) fonction au lieu de filtrage bidirectionnel.
- Tables d’agrégation peuvent atteindre des requêtes plus rapide des réponses en chargeant préalable des données synthétisées, mais cela augmentera la taille du modèle et du résultat dans le temps d’actualisation. En règle générale, les tables d’agrégation doivent être réservés pour les modèles très volumineux ou des conceptions de modèle Composite.
- Colonnes et des tables calculées augmenter la taille du modèle et entraînent des temps longs d’actualisation. En règle générale, une plus petite taille de stockage et le temps d’actualisation plus rapide est possible lorsque les données sont matérialisées ou calculées dans la source de données. Si ce n’est pas possible, à l’aide de colonnes personnalisées Power Query peut offrir la compression de stockage améliorée.
- Il peut être possible d’ajuster les expressions DAX pour les mesures et des règles RLS, peut-être logique pour éviter les formules coûteux de réécriture
- Actualisation incrémentielle peut considérablement réduire le temps d’actualisation et économiser la mémoire et processeur. L’actualisation incrémentielle peut également être configurée pour supprimer les données historiques en conservant les tailles de modèle trim.
- Un modèle peut être remanié comme deux modèles lorsqu’il existe des modèles de requête différents et en conflit. Par exemple, certains rapports présentes agrégats de haut niveau sur tous les historique et peut tolérer une latence de 24 heures. Autres rapports sont concernés par les données d’aujourd'hui et avez besoin d’un accès précis aux transactions individuelles. Au lieu de concevoir un modèle unique pour répondre à tous les rapports, créer deux modèles optimisés pour chaque exigence.

Envisagez les possibilités d’optimisation pour un modèle DirectQuery. Comme le modèle émet des demandes de requête à la source de données sous-jacente, optimisation de la source de données est essentielle pour fournir des requêtes de modèle réactif.

 ![Possibilités d’optimisation pour un modèle DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Au niveau de la couche source de données :

- La source de données peut être optimisé pour garantir l’interrogation possible le plus rapide en intégrant des données (ce qui ne sont pas possibles au niveau de la couche de modèle), appliquer des index appropriés, définir des partitions de table, la matérialisation des données (avec des vues indexées), synthétisées et Pour réduire la quantité de calcul. La meilleure expérience est obtenue lorsque les requêtes pass-through doivent uniquement filtrer et effectuer des jointures internes entre les tables indexées ou des vues.
- Assurez-vous que les passerelles ont suffisamment de ressources, de préférence sur des ordinateurs dédiés, avec suffisamment de bande passante réseau et à proximité de la source de données.

Au niveau de la couche de modèle :

- Power Query query conceptions doivent appliquer, de préférence, sans transformation - essayer de conserver les transformations au strict minimum.
- Performances des requêtes de modèle peuvent être améliorées en configurant les relations de direction à sens unique, sauf s’il existe une bonne raison pour permettre le filtrage bidirectionnel. En outre, les relations de modèle doivent être configurées pour supposer l’intégrité référentielle est appliquée (quand c’est le cas) et génèrent les requêtes de source de données à l’aide de jointures internes plus efficaces (au lieu de jointures externes).
- Évitez de créer des colonnes personnalisées de requête de Power Query ou une colonne calculée de modèle : matérialiser ces éléments dans la source de données, lorsque cela est possible.
- Il peut être possible d’ajuster les expressions DAX pour les mesures et des règles RLS, peut-être logique pour éviter les formules coûteux de réécriture.

Envisagez les possibilités d’optimisation pour un modèle Composite. Rappelez-vous qu’un modèle Composite permet une combinaison d’importation et de tables de DirectQuery.

![Possibilités d’optimisation pour un modèle composite](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- En règle générale, l’optimisation pour les modèles d’importation et DirectQuery s’appliquent aux tables de modèle Composite qui utilisent ces modes de stockage.
- En règle générale, cherchent à obtenir une conception à charge équilibrée en configurant des tables de dimension de type (représentant des entités métier) en tant que double mode et le type de fait tables de stockage (souvent des tables volumineuses, représentant les faits opérationnels) en tant que mode de stockage DirectQuery. Mode de stockage double signifie que les deux importer et modes de stockage DirectQuery et cela permet au service de Power BI déterminer le mode de stockage plus efficace à utiliser lors de la génération d’une requête native pour pass-through.
- Assurez-vous que les passerelles ont suffisamment de ressources, de préférence sur des ordinateurs dédiés, avec suffisamment de bande passante réseau et à proximité les sources de données
- Les tables d’agrégations configurées comme mode de stockage d’importation peut fournir des améliorations des performances considérables requête lorsqu’il est utilisé pour résumer les tables de faits-type de mode de stockage DirectQuery. Dans ce cas, les tables d’agrégation augmentera la taille du modèle et augmenter le temps d’actualisation, et il s’agit souvent d’un compromis acceptable pour les requêtes plus rapides.

### <a name="optimizing-externally-hosted-models"></a>Optimisation en externe hébergé des modèles

Nombreuses possibilités d’optimisation décrites dans le [optimisation Power BI hébergés modèles](#optimizing-power-bi-hosted-models) section s’appliquent également aux modèles développés avec Azure Analysis Services et SQL Server Analysis Services. Exceptions clair sont certaines fonctionnalités qui ne sont pas actuellement pris en charge, y compris des modèles composites et des tables d’agrégation.

Une considération supplémentaire pour les jeux de données hébergé en externe est la base de données d’hébergement en relation avec le service Power BI. Pour Azure Analysis Services, cela implique la création de la ressource Azure dans la même région que le locataire Power BI (région d’accueil). Pour SQL Server Analysis Services pour IaaS, cela signifie que la machine virtuelle dans la même région d’hébergement, et en local, il consiste à s’assurer une installation de la passerelle efficace.

À part cela, il peut être d’intérêt de noter que les bases de données Azure Analysis Services et bases de données tabulaires SQL Server Analysis Services nécessitent que leurs modèles d’être entièrement chargé en mémoire et qu’ils y restent à tout moment pour prendre en charge l’interrogation. Telles que le service Power BI, il doit être suffisamment de mémoire pour l’actualisation si le modèle doit rester en ligne lors de l’actualisation. Contrairement au service Power BI, il n’existe aucun concept âgés automatiquement des modèles en mémoire en fonction de l’utilisation. Power BI Premium, offre par conséquent, une approche plus efficace pour optimiser l’interrogation de modèle avec l’utilisation de mémoire inférieure.

## <a name="capacity-planning"></a>Planification de la capacité

La taille d’une capacité Premium détermine sa mémoire disponible et les ressources du processeur et les limites imposées sur la capacité. Le nombre de capacités Premium est également un facteur important, que vous la créez Premium plusieurs capacités peuvent aider à isoler les charges de travail entre eux. Notez que le stockage est de 100 To par nœud de capacité, et il est susceptible d’être plus que suffisant pour toute charge de travail.

Déterminer la taille et le nombre de capacités Premium peut être difficile, en particulier pour la capacité initiale, que vous créez. La première étape de dimensionnement de capacité est de comprendre la charge de travail moyenne représentant l’usage quotidien attendu. Il est important de comprendre que certaines charges de travail sont égales. Par exemple, à l’extrémité d’une gamme - 100 utilisateurs simultanés, l’accès à une page de rapport unique qui contient un seul visuel est facilement réalisable. Encore - à l’autre extrémité du spectre - 100 utilisateurs simultanés qui accèdent aux 100 rapports différents, chacun avec 100 visuels sur la page de rapport, va rendre très différentes demandes de ressources de capacité.

Administrateurs de capacité seront donc à prendre en compte plusieurs facteurs spécifiques à votre environnement, le contenu et l’utilisation attendue. L’objectif de substitution est de maximiser l’utilisation de la capacité tout en offrant des temps de requête cohérents, temps d’attente acceptable et taux d’éviction. Facteurs à prendre en compte peuvent inclure :

- **Caractéristiques de taille et les données de modèle** -modèles d’importation doivent être entièrement chargées en mémoire pour permettre l’interrogation ou l’actualisation. LC/DQ de jeux de données peut nécessiter significative de temps processeur et mémoire éventuellement importante pour évaluer les mesures complexes ou des règles RLS. Mémoire et de taille du processeur et de débit des requêtes LC/DQ sont limitées par la taille de la capacité.
- **Modèles actifs simultanés** -l’interrogation simultanées des modèles d’importation différente offre une meilleure réactivité et les performances lorsqu’ils restent en mémoire. Il doit exister une mémoire suffisante pour héberger tous les modèles fréquemment consultés, avec plus de mémoire pour permettre son actualisation.
- **Actualisation de modèle d’importation** -le type d’actualisation (complet ou incrémentiel), la durée et la complexité des requêtes Power Query et logique de la table/colonne calculée peuvent avoir un impact sur mémoire et l’utilisation du processeur en particulier. Actualisations simultanées sont limitées par la taille de la capacité (1,5 x backend v-cores, arrondis).
- **Requêtes simultanées** -plusieurs requêtes simultanées peuvent entraîner dans les rapports ne répond pas quand processeur ou LC/DQ connexions dépasse la limite de capacité. Cela est particulièrement vrai pour les pages de rapport qui incluent de nombreux visuels.
- **Flux de données et des rapports paginés** -la capacité peut être configurée pour prendre en charge des flux de données et des rapports paginés, chacun nécessitant un pourcentage maximal configurable de capacité de mémoire. Mémoire est allouée dynamiquement à un flux de données, mais elle est allouée de façon statique pour les rapports paginés.

En plus de ces facteurs, les administrateurs de capacité peuvent envisager de créer des plusieurs capacités. Plusieurs capacités permettant l’isolation des charges de travail et peuvent être configurées pour vous assurer de charges de travail de priorité ont garanti des ressources. Par exemple, deux capacités peuvent être créées pour séparer les charges de travail critiques en libre-service des charges de travail BI (SSBI). La capacité critique pour l’entreprise peut être utilisée pour isoler les modèles d’entreprise volumineux leur fournissant des ressources garantis, avec accès accordé uniquement au service informatique de création. La capacité SSBI peut être utilisée pour héberger un nombre croissant de modèles plus petits, avec un accès accordé pour les analystes d’entreprise. La capacité SSBI pouvez rencontrer parfois les attentes de requête ou d’actualisation sont inacceptables.

Au fil du temps, les administrateurs de capacité peut équilibrer des espaces de travail sur capacités en déplacement du contenu entre des espaces de travail, ou des espaces de travail entre les capacités et en adaptant capacités. En règle générale, pour les modèles plus volumineux hôte vous monter en puissance et pour une simultanéité plus élevée vous monter en charge.

Rappelez-vous que l’achat d’une licence fournit au locataire v-cores. L’achat d’un **P3** abonnement peut être utilisé pour créer un, ou jusqu'à quatre capacités Premium, par exemple, 1 x P3, ou 2 x P2 ou 4 x P1. En outre, avant la migration d’une capacité de P2 à une capacité P3, pouvez considération à fractionner les v-cores pour créer deux capacités P1.

## <a name="testing-approaches"></a>Approches de test

Une fois une taille de la capacité est choisie, le test peut être effectué en créant un environnement contrôlé. Une option pratique et économique consiste à créer une capacité de Azure (références SKU A), en notant qu’une capacité de P1 est la même taille qu’une capacité A4, avec le P2 et P3 capacités la même taille que les capacités de A5 et A6, respectivement. Capacités Azure peuvent être rapidement créées et sont facturées sur une base horaire. Par conséquent, une fois le test terminé, ils peuvent être facilement supprimés pour interrompre les frais de coûts.

Le contenu de test peut être ajouté aux espaces de travail créés sur la capacité d’Azure et en tant qu’un seul utilisateur peut exécuter des rapports pour générer une charge de travail réaliste et représentatif des requêtes. S’il existe des modèles d’importation, une actualisation pour chaque modèle doit être effectuée également. Outils d’analyse peut ensuite être utilisé pour passer en revue toutes les mesures pour comprendre l’utilisation des ressources.

Il est important que les tests sont renouvelables. Tests doivent être exécutés plusieurs fois et ils doivent fournir environ le même résultat chaque fois. Une moyenne de ces résultats peut être utilisée pour extrapoler et estimer une charge de travail dans des conditions de production true.

Pour générer un test de stress, envisagez de développer une application pour simuler une charge de travail de test de charge. Les spécificités de la procédure à suivre sont en dehors de la portée de cet article. Pour plus d’informations, y compris un exemple de code, reportez-vous à la [charger test d’applications Power BI avec le test de charge Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinaire.

## <a name="acknowledgements"></a>Accusés de réception

Cet article a été écrit par Peter Myers, données plateforme MVP et expert BI indépendant avec [Solutions au niveau du bit](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Scénarios de capacité Premium](service-premium-capacity-scenarios.md)   
  
D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

||||||