---
title: Optimiser les capacités Microsoft Power BI Premium
description: Décrit les stratégies d’optimisation pour les capacités de Power BI Premium.
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
ms.openlocfilehash: 9f5357056c27d6461ad7f7d7fba1daa27a508868
ms.sourcegitcommit: 012f05efc4e97aeb6178fb2fc820b73bcc1ce920
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68391154"
---
# <a name="optimizing-premium-capacities"></a>Optimiser les capacités Premium

En cas de problèmes de performances de capacité Premium, une première approche courante consiste à optimiser ou ajuster vos solutions pour restaurer des temps de réponse acceptables. Le raisonnement est d’éviter d’acheter une capacité Premium supplémentaire, sauf si cela est justifié.

Quand une capacité Premium supplémentaire est exigée, deux options sont décrites dans cet article :

- Mise à l’échelle d’une capacité Premium existante
- Ajout d’une capacité Premium

Enfin, les approches de test et le dimensionnement de la capacité Premium concluent cet article.

## <a name="best-practices"></a>Meilleures pratiques

Lorsque vous essayez d’obtenir des performances et une utilisation optimales, il existe des pratiques recommandées, notamment :

- l’utilisation d’espaces de travail d’application au lieu d’espaces de travail personnels.
- la séparation des informations décisionnelles libre-service (SSBI) et critiques pour l’entreprise en différentes capacités.

  ![Séparation des informations décisionnelles libre-service et critiques pour l’entreprise en différentes capacités](media/service-premium-capacity-optimize/separate-capacities.png)

- Si vous partagez du contenu uniquement avec des utilisateurs Power BI Pro, il n’est pas nécessaire de stocker le contenu dans une capacité dédiée.
- Utilisez des capacités dédiées pour obtenir un temps d’actualisation spécifique, ou lorsque des fonctionnalités spécifiques sont requises. Par exemple, avec des jeux de données volumineux ou des rapports paginés.

### <a name="addressing-common-questions"></a>Répondre aux questions courantes

L’optimisation des déploiements Power BI Premium est un sujet complexe impliquant une compréhension des exigences de charge de travail, des ressources disponibles et de leur utilisation effective.

Cet article traite de sept questions de support courantes, qui décrivent les problèmes et les explications possibles, ainsi que les informations sur la façon de les identifier et de les résoudre.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Pourquoi la capacité est-elle lente et que puis-je faire ?

Il existe de nombreuses raisons pouvant contribuer à une capacité Premium lente. Cette question nécessite des informations supplémentaires pour comprendre ce qui est entendu comme lent. Le chargement des rapports est-il lent ? Le chargement échoue-t-il ? Les visuels de rapport sont-ils lents à charger ou à mettre à jour lorsque les utilisateurs interagissent avec le rapport ? Les actualisations prennent-elles plus de temps que prévu pour se terminer, ou est-ce que cela a déjà été expérimenté ?

Après avoir acquis une bonne compréhension de la raison, vous pouvez commencer à examiner. Les réponses aux six questions suivantes vous aideront à résoudre des problèmes plus spécifiques.

### <a name="what-content-is-using-up-my-capacity"></a>Quel contenu utilise ma capacité ?

Vous pouvez utiliser l’application **Mesures de capacité Power BI Premium** pour filtrer par capacité et vérifier les mesures de performance pour le contenu de l’espace de travail. Il est possible de passer en revue les mesures de performance et l’utilisation des ressources par heure au cours des sept derniers jours pour tout le contenu stocké dans une capacité Premium. La surveillance est souvent la première étape à entreprendre lors du dépannage d’une préoccupation générale concernant les performances d’une capacité Premium.

Les mesures clés à surveiller sont les suivantes :

- Compteur d’UC moyen et d’utilisation élevée.
- Compteur de mémoire moyen et d’utilisation élevée, et utilisation de la mémoire pour des jeux de données, des flux et des rapports paginés spécifiques.
- Jeux de données actifs chargés en mémoire.
- Durées des requêtes moyennes et maximales.
- Temps moyen d’attente des requêtes.
- Temps moyen d’actualisation des jeux de données et des flux de données.

Dans l’application Mesures de capacité Power BI Premium, la mémoire active affiche la quantité totale de mémoire donnée à un rapport qui ne peut pas être supprimé car il a été utilisé au cours des trois dernières minutes. Un pic élevé du temps d’attente d’actualisation peut être mis en corrélation avec un jeu de données volumineux et/ou actif.

Le graphique **Top 5 par durée moyenne** met en évidence les cinq premiers jeux de données, rapports paginés et dataflows consommant les ressources de la capacité. Le contenu des cinq premières listes met en lumière des candidats pour des recherches et des optimisations possibles.

### <a name="why-are-reports-slow"></a>Pourquoi les rapports sont-ils lents ?

Les tableaux suivants présentent les problèmes possibles et les moyens de les identifier et de les traiter.

#### <a name="insufficient-capacity-resources"></a>Ressources de capacité insuffisantes

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Mémoire active totale élevée (le modèle ne peut pas être supprimé car il a été utilisé lors des trois dernières minutes).<br><br> Plusieurs pics élevés dans les temps d’attente des requêtes.<br><br> Plusieurs pics élevés dans les temps d’attente d’actualisation. | Surveillez les métriques de mémoire \[[1](#endnote-1)\],et le nombre d’évictions \[[2](#endnote-2)\]. | Réduisez la taille du modèle ou convertissez-le en mode DirectQuery. Consultez la section [Optimisation des modèles](#optimizing-models) dans cet article.<br><br> Mettez la capacité à l’échelle.<br><br> Attribuez le contenu à une capacité différente. |

#### <a name="inefficient-report-designs"></a>Conceptions de rapports inefficaces

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Les pages de rapport contiennent un trop grand nombre de visuels (le filtrage interactif peut déclencher au moins une requête par visuel).<br><br> Les visuels récupèrent plus de données que nécessaire. | Passez en revue les conceptions de rapports.<br><br> Questionnez les utilisateurs des rapports pour comprendre comment ils interagissent avec les rapports.<br><br> Surveiller les métriques de requête de jeu de données \[[3](#endnote-3)\]. | Remaniez les rapports avec moins d’éléments visuels par page. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Le jeu de données est lent, surtout lorsque les rapports ont été correctement exécutés

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Volumes de données d’importation de plus en plus grands.<br><br> Logique de calcul complexe ou inefficace, y compris les rôles RLS.<br><br> Modèle qui n’est pas entièrement optimisé.<br><br> Latence de la passerelle (DQ/LC).<br><br> Lenteur des temps de réponse des requêtes de source DQ. | Passez en revue les conceptions de modèles.<br><br> Surveiller les compteurs de performances de passerelle. | Consultez la section [Optimisation des modèles](#optimizing-models) dans cet article. |

#### <a name="high-concurrent-report-usage"></a>Utilisation élevée de rapports en simultané

| Explications possibles | Comment identifier | Comment résoudre |
| --- | --- | --- |
| Temps d’attente des requêtes élevé.<br><br> Saturation de l’UC.<br><br> Les limites de connexion DQ/LC sont dépassées. | Surveillez l’utilisation de l’UC \[[4](#endnote-4)\], les temps d’attente des requêtes, et les métriques d’utilisation DQ/LC \[[5](#endnote-5)\] + les durées des requêtes. En cas de fluctuation, cela peut indiquer des problèmes d’accès concurrentiel. | Mettez à l’échelle la capacité ou attribuez le contenu à une capacité différente.<br><br> Remaniez les rapports avec moins d’éléments visuels par page. |

**Notes :**    
<a name="endnote-1"></a>\[1\] Utilisation moyenne de la mémoire (Go) et consommation de mémoire la plus élevée (Go).   
<a name="endnote-2"></a>\[2\] Éviction de jeux de données.   
<a name="endnote-3"></a>\[3\] Requêtes du jeu de données, durée moyenne des requêtes de jeu de données (ms), compteur d’attente du jeu de données et temps d’attente moyen du jeu de données (ms).   
<a name="endnote-4"></a>\[4\] Compteur d’utilisation élevée de l’UC et heure de la plus forte utilisation de l’UC (sept derniers jours).   
<a name="endnote-5"></a>\[5\] Compteur d’utilisation élevée de DQ/LC et heure de la plus forte utilisation de DQ/LC (sept derniers jours).   

### <a name="why-are-reports-not-loading"></a>Pourquoi les rapports ne se chargent-ils pas ?

En cas d’échec du chargement des rapports, cela signifie forcément que la capacité ne dispose pas d’assez de mémoire et qu’elle est surchauffée. Cela peut se produire lorsque tous les modèles chargés sont activement interrogés et ne peuvent donc pas être supprimés, et toutes les opérations d’actualisation ont été suspendues ou retardées. Le service Power BI tentera de charger le jeu de données pendant 30 secondes, et l’utilisateur est normalement informé de l’échec en suggérant de réessayer dans un instant.

Il n’existe actuellement aucune mesure à surveiller pour les échecs de chargement des rapports. Vous pouvez identifier le potentiel de ce problème en surveillant la mémoire système, en particulier l’utilisation la plus élevée et le temps d’utilisation le plus élevé. Les évictions des jeux de données élevés et un temps d’attente moyen d’actualisation des jeux de données peuvent suggérer que ce problème se produit.

Si cela ne se produit que très rarement, cela peut ne pas être considéré comme un problème prioritaire. Les utilisateurs de rapports sont informés que le service est occupé et qu’ils doivent effectuer une nouvelle tentative dans très peu de temps. Si cela se produit trop fréquemment, le problème peut être résolu en mettant à l’échelle la capacité Premium ou en affectant le contenu à une capacité différente.

Les administrateurs de capacité (et les administrateurs du service Power BI) peuvent surveiller la métrique des **échecs de requête** pour déterminer quand cela se produit. Ils peuvent également redémarrer la capacité, réinitialisant ainsi toutes les opérations en cas de surcharge du système.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Pourquoi les actualisations ne commencent-elles pas selon la planification ?

Les heures de démarrage d’actualisation planifiée ne sont pas garanties. Rappelez-vous que le service Power BI met la priorité sur les opérations interactives par rapport aux opérations d’arrière-plan. L’actualisation est une opération d’arrière-plan qui peut se produire lorsque deux conditions sont remplies :

- La mémoire est suffisante
- Le nombre d’actualisations simultanées prises en charge pour la capacité Premium n’est pas dépassé

Lorsque les conditions ne sont pas remplies, l’actualisation est mise en file d’attente jusqu’à ce que les conditions soient favorables.

Pour une actualisation complète, rappelez-vous qu’au moins deux fois la taille de la mémoire actuelle du jeu de données est requise. Si la mémoire disponible n’est pas suffisante, l’actualisation ne peut pas commencer tant que l’éviction du modèle n’a pas libéré de la mémoire, ce qui signifie qu’un ou plusieurs jeux de données deviennent inactifs et peuvent être supprimés.

Rappelez-vous que le nombre maximal d’actualisations simultanées pris en charge est défini à 1,5 fois les cœurs vCore du serveur principal, arrondi à l’entier supérieur.

Une actualisation planifiée échouera si elle ne peut pas commencer avant que la prochaine actualisation planifiée ne commence. Une actualisation à la demande déclenchée manuellement à partir de l’interface utilisateur tentera de s’exécuter jusqu’à trois fois avant d’échouer.

Les administrateurs de capacité (et les administrateurs de service Power BI) peuvent surveiller la métrique de **temps d’attente d’actualisation moyen (minutes)** pour déterminer le décalage moyen entre l’heure planifiée et le début de l’opération.

Bien qu’il ne s’agisse généralement pas d’une priorité administrative, assurez-vous que la mémoire disponible est suffisante pour influencer l’actualisation des données au moment prévu. Cela peut impliquer l’isolation des jeux de données aux capacités avec des ressources suffisantes. Il est également possible que les administrateurs puissent coordonner avec les propriétaires de jeux de données pour aider à échelonner ou à réduire les temps planifiés d’actualisation des données pour réduire les collisions. Notez qu’il n’est pas possible pour un administrateur d’afficher la file d’attente d’actualisation ou de récupérer des planifications de jeu de données.

### <a name="why-are-refreshes-slow"></a>Pourquoi les actualisations sont-elles lentes ?

Les actualisations peuvent être lentes ou perçues ainsi (comme les adresses de questions courantes précédentes).

Lorsque l’actualisation est en fait lente, cela peut être dû à plusieurs raisons :

- UC insuffisante (l’actualisation peut être très gourmande en ressources du processeur).
- Mémoire insuffisante, entraînant une suspension de l’actualisation (ce qui nécessite son redémarrage une fois les conditions favorables au redémarrage).
- Raisons de non-capacité, y compris la réactivité du système DataSource, la latence du réseau, les autorisations non valides ou le débit de la passerelle.
- Volume de données, une bonne raison de configurer une actualisation incrémentielle, comme indiqué ci-dessous.

Les administrateurs de capacité (et les administrateurs de service Power BI) peuvent surveiller la métrique de **durée d’actualisation moyenne (minutes)** pour déterminer point de référence pour une comparaison au fil du temps, et les métriques **temps d’attente d’actualisation moyen (minutes)** pour déterminer le décalage moyen entre l’heure planifiée et le début de l’opération.

L’actualisation incrémentielle peut réduire considérablement la durée d’actualisation des données, en particulier pour les tables de modèles volumineuses. Quatre avantages sont associés à l’actualisation incrémentielle :

- **Actualisations plus rapides** : seul un sous-ensemble d’une table doit être chargé, ce qui réduit l’utilisation du processeur et de la mémoire, et le parallélisme peut être plus élevé lors de l’actualisation de plusieurs partitions.
- **Actualisations uniquement lorsque cela est nécessaire** : les stratégies d’actualisation incrémentielle peuvent être configurées pour être chargées uniquement lors d’un changement des données.
- **Actualisations plus fiables** : les connexions d’exécution plus courtes vers des systèmes de source de données de type volatiles sont moins susceptibles d’être déconnectées.
- **Les modèles restent découpés** : les stratégies d’actualisation incrémentielle peuvent être configurées pour supprimer automatiquement l’historique au-delà d’une fenêtre de temps coulissante.

Pour plus d’informations, consultez [Actualisation incrémentielle dans Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Pourquoi les actualisations de données ne se terminent-elles pas ?

Lorsque l’actualisation des données commence mais échoue, cela peut être dû à plusieurs raisons :

- une quantité de mémoire insuffisante, même s’il n’y a qu’un seul modèle dans la capacité Premium, c’est-à-dire que la taille du modèle est très grande.
- des raisons de non-capacité, y compris la déconnexion du système DataSource, les autorisations non valides ou une erreur de passerelle.

Les administrateurs de capacité (et les administrateurs du service Power BI) peuvent surveiller la métrique **Actualiser les échecs engendrés par un manque de mémoire**.

## <a name="optimizing-models"></a>Optimisation des modèles

Une conception de modèle optimale est essentielle pour la mise en œuvre d’une solution efficace et évolutive. Toutefois, cet article n’a pas pour but de fournir une discussion complète sur ce sujet. Au lieu de cela, cette section fournit des domaines clés à prendre en compte lors de l’optimisation des modèles.

### <a name="optimizing-power-bi-hosted-models"></a>Optimisation des modèles hébergés par Power BI

L’optimisation des modèles hébergés dans une capacité Premium peut être effectuée au niveau de la ou des sources de données et des couches du modèle.

Tenez compte des possibilités d’optimisation d’un modèle d’importation :

![Possibilités d’optimisation d’un modèle d’importation](media/service-premium-capacity-optimize/import-model-optimizations.png)

Au niveau de la couche DataSource :

- Les sources de données relationnelles peuvent être optimisées pour garantir l’actualisation la plus rapide possible en préintégrant des données, en appliquant des index appropriés, en définissant des partitions de table qui s’alignent sur des périodes d’actualisation incrémentielles et en matérialisant des calculs (à la place de tables et de colonnes de modèle calculées) ou en ajoutant une logique de calcul aux vues.
- Les sources de données non relationnelles peuvent être pré-intégrées aux magasins relationnels.
- Assurez-vous que les passerelles disposent d’assez de ressources, de préférence sur des machines dédiées, avec une bande passante réseau suffisante et à proximité des sources de données.

Au niveau de la couche du modèle :

- Les conceptions de requêtes Power Query peuvent réduire ou supprimer des transformations complexes, et en particulier celles fusionnant des sources de données différentes (les entrepôts de données y parviennent pendant leur étape d’extraction-transformation-chargement). En outre, en veillant à ce que les niveaux de confidentialité appropriés soient définis, il est possible d’éviter de demander à Power BI de charger des résultats complets pour produire un résultat combiné entre des requêtes.
- La structure du modèle détermine les données à charger et a un impact direct sur la taille du modèle. Il peut être conçu pour éviter le chargement de données inutiles en supprimant des colonnes ou des lignes (notamment des données historiques) ou en chargeant des données résumées (au détriment du chargement de données détaillées). Une réduction considérable de la taille peut être obtenue en supprimant les colonnes de cardinalité élevée (en particulier les colonnes de texte) qui ne sont pas stockées ou compressées très efficacement.
- Les performances des requêtes de modèle peuvent être améliorées en configurant des relations à sens unique, à moins qu’il y ait une raison impérieuse d’autoriser le filtrage bidirectionnel. Envisagez également d’utiliser la fonction [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) au lieu du filtrage bidirectionnel.
- Les tables d’agrégation peuvent obtenir des réponses rapides aux requêtes en chargeant des données prérésumées, mais cela augmente la taille du modèle et engendre des temps d’actualisation plus longs. En règle générale, les tables d’agrégation doivent être réservées pour les modèles très volumineux ou les conceptions de modèles composites.
- Les tables et les colonnes calculées augmentent la taille du modèle et entraînent des temps d’actualisation plus longs. En règle générale, une plus petite taille de stockage et un temps d’actualisation plus rapide peuvent être obtenus lorsque les données sont matérialisées ou calculées dans la source de données. Si ce n’est pas possible, l’utilisation des colonnes personnalisées Power Query peut offrir une meilleure compression du stockage.
- Il peut être possible de paramétrer des expressions DAX pour les mesures et les règles RLS, possiblement en réécrivant la logique afin d’éviter des formules coûteuses
- L’actualisation incrémentielle peut réduire considérablement le temps d’actualisation et économiser la mémoire et l’UC. L’actualisation incrémentielle peut également être configurée pour supprimer les données historiques, permettant ainsi de réduire la taille des modèles.
- Un modèle peut être repensé comme deux modèles lorsqu’il existe des modèles de requête différents et en conflit. Par exemple, certains rapports présentent des agrégats de haut niveau sur l’ensemble de l’historique et peuvent tolérer une latence de 24 heures. D’autres rapports sont concernés par les données actuelles et nécessitent un accès granulaire à des transactions individuelles. Au lieu de concevoir un modèle unique pour répondre à tous les rapports, créez deux modèles optimisés pour chaque besoin.

Tenez compte des possibilités d’optimisation d’un modèle DirectQuery. À mesure que le modèle émet des demandes de requête à la source de données sous-jacente, l’optimisation des sources de données est essentielle pour la transmission de requêtes de modèle réactives.

 ![Possibilités d’optimisation d’un modèle DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Au niveau de la couche DataSource :

- La source de données peut être optimisée pour assurer l’interrogation la plus rapide possible en préintégrant des données (ce qui n’est pas possible au niveau de la couche de modèle), en appliquant des index appropriés, en définissant des partitions de table, en matérialisant des données résumées (avec des vues indexées) et en réduisant la quantité de calcul. La meilleure expérience est obtenue lorsque les requêtes directes doivent uniquement filtrer et effectuer des jointures internes entre des tables ou des vues indexées.
- Assurez-vous que les passerelles disposent d’assez de ressources, de préférence sur des machines dédiées, avec une bande passante réseau suffisante et à proximité de la source de données.

Au niveau de la couche du modèle :

- De préférence, les conceptions de requêtes Power Query ne doivent pas appliquer de transformations. Sinon, essayez d’avoir le moins de transformations possible.
- Les performances des requêtes de modèle peuvent être améliorées en configurant des relations à sens unique, à moins qu’il y ait une raison impérieuse d’autoriser le filtrage bidirectionnel. En outre, les relations de modèle doivent être configurées pour supposer que l’intégrité référentielle est appliquée (lorsque c’est le cas) et entraîne des requêtes DataSource utilisant des jointures internes plus efficaces (au lieu de jointures externes).
- Évitez de créer des colonnes personnalisées de requête ou des colonnes calculées de modèle Power Query, matérialisez-les dans la source de données, lorsque cela est possible.
- Il peut être possible de paramétrer des expressions DAX pour les mesures et les règles RLS, possiblement en réécrivant la logique afin d’éviter des formules coûteuses.

Tenez compte des possibilités d’optimisation d’un modèle composite. Rappelez-vous qu’un modèle composite permet une combinaison de tables d’importation et DirectQuery.

![Possibilités d’optimisation d’un modèle composite](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- En règle générale, l’optimisation des modèles d’importation et DirectQuery s’applique aux tables de modèle composite qui utilisent ces modes de stockage.
- En général, efforcez-vous d’obtenir une conception équilibrée en configurant des tables de type dimension (représentant les entités métier) en tant que mode de stockage double et les tables de type Faits (souvent des tables volumineuses, représentant des faits opérationnels) en tant que mode de stockage DirectQuery. Le mode de stockage double signifie les modes de stockage d’importation et DirectQuery, ce qui permet au service Power BI de déterminer le mode de stockage le plus efficace à utiliser lors de la génération d’une requête native pour le transfert.
- Assurez-vous que les passerelles disposent d’assez de ressources, de préférence sur des machines dédiées, avec une bande passante réseau suffisante et à proximité des sources de données
- Les tables d’agrégations configurées en mode de stockage d’importation peuvent offrir des améliorations de performances de requête spectaculaires lorsqu’elles sont utilisées pour résumer les tables de type Faits du mode de stockage DirectQuery. Dans ce cas, les tables d’agrégation augmentent la taille du modèle et donc le temps d’actualisation, et il s’agit souvent d’un compromis acceptable pour accélérer les requêtes.

### <a name="optimizing-externally-hosted-models"></a>Optimisation des modèles hébergés en externe

De nombreuses possibilités d’optimisation présentées la section [Optimisation des modèles hébergés par Power BI](#optimizing-power-bi-hosted-models) s’appliquent également aux modèles développés avec Azure Analysis Services et SQL Server Analysis Services. Les exceptions claires sont certaines fonctionnalités actuellement non prises en charge, y compris les modèles composites et les tables d’agrégation.

Une considération supplémentaire pour les jeux de données hébergés en externe est l’hébergement de base de données par rapport au service Power BI. Par Azure Analysis Services, cela implique la création de la ressource Azure dans la même région que le locataire Power BI (région d’hébergement). Par SQL Server Analysis Services, pour IaaS, cela implique l’hébergement de la machine virtuelle dans la même région et, pour l’environnement local, cela signifie garantir une configuration de passerelle efficace.

En outre, il peut être intéressant de noter que les bases de données Azure Analysis Services et les bases de données tabulaires SQL Server Analysis Services requièrent que leurs modèles soient entièrement chargés en mémoire et qu’ils y restent à tout moment pour prendre en charge l’interrogation. À l’instar du service Power BI, il doit y avoir suffisamment de mémoire pour l’actualisation si le modèle doit rester en ligne pendant l’actualisation. Contrairement au service Power BI, il n’existe aucun concept dans lequel les modèles sont automatiquement vieillis et sortis de la mémoire en fonction de leur utilisation. Par conséquent, Power BI Premium offre une approche plus efficace pour optimiser l’interrogation du modèle avec une utilisation plus faible de la mémoire.

## <a name="capacity-planning"></a>Planification de la capacité

La taille d’une capacité Premium détermine les ressources de mémoire et de processeur disponibles, ainsi que les limites imposées à la capacité. Le nombre de capacités Premium est également un facteur important, car la création de plusieurs capacités Premium peut aider à isoler les charges de travail les unes des autres. Notez que le stockage est de 100 To par nœud de capacité, ce qui est susceptible d’être plus que suffisant pour toute charge de travail.

La détermination de la taille et du nombre de capacités Premium peut être difficile, en particulier pour les capacités initiales que vous créez. La première étape lors du dimensionnement de la capacité consiste à comprendre la charge de travail moyenne représentant l’utilisation quotidienne prévue. Il est important de comprendre que toutes les charges de travail ne sont pas égales. Par exemple, à une extrémité d’un spectre, 100 utilisateurs simultanés qui accèdent à une page de rapport unique qui contient un seul visuel est un objectif facilement réalisable. Pourtant, à l’autre extrémité du spectre, 100 utilisateurs simultanés qui accèdent à 100 différents rapports, contenant chacun 100 éléments visuels sur la page de rapport, entraînent des besoins très différents en termes de ressources de capacité.

Les administrateurs de capacité doivent donc prendre en compte de nombreux facteurs spécifiques à votre environnement, au contenu et à l’utilisation prévue. L’objectif de substitution est d’optimiser l’utilisation de la capacité tout en assurant des temps de requête cohérents, des temps d’attente acceptables et des taux d’éviction. Les facteurs à prendre en compte peuvent être les suivants :

- **Caractéristiques des données et taille du modèle** : les modèles d’importation doivent être entièrement chargés en mémoire pour permettre l’interrogation ou l’actualisation. Les jeux de données LC/DQ peuvent nécessiter beaucoup de temps du processeur et éventuellement une quantité de mémoire importante pour évaluer des mesures complexes ou des règles RLS. La taille de la mémoire et du processeur, ainsi que le débit des requêtes LC/DQ sont limités par la taille de la capacité.
- **Modèles actifs simultanés** : l’interrogation simultanée de différents modèles d’importation offre des performances et une réactivité optimales lorsqu’elles sont conservées en mémoire. Il doit y avoir suffisamment de mémoire pour héberger tous les modèles fortement interrogés, avec de la mémoire supplémentaire pour permettre leur actualisation.
- **Actualiser un modèle d’importation** : le type d’actualisation (complète ou incrémentielle), la durée et la complexité des requêtes Power Query et la logique de table/colonne calculée peuvent avoir un impact sur la mémoire et plus particulièrement sur l’utilisation du processeur. Les actualisations simultanées sont restreintes par la taille de la capacité (1,5 fois les cœurs virtuels backend, arrondi).
- **Requêtes simultanées** : de nombreuses requêtes simultanées peuvent entraîner des rapports non réactifs lorsque le processeur ou les connexions LC/DQ dépassent la limite de la capacité. C’est particulièrement le cas pour les pages de rapport incluant de nombreux visuels.
- **Rapports paginés et dataflows** : la capacité peut être configurée pour prendre en charge les rapports paginés et les dataflows, chacun nécessitant un pourcentage maximal configurable de mémoire de capacité. La mémoire est allouée dynamiquement aux flux de données, mais elle est allouée statiquement aux rapports paginés.

En plus de ces facteurs, les administrateurs de capacité peuvent créer plusieurs capacités. Plusieurs capacités permettent d’isoler les charges de travail et peuvent être configurées pour garantir que les charges de travail prioritaires disposent de ressources garanties. Par exemple, deux capacités peuvent être créées pour séparer les charges de travail critiques de l’entreprise et les charges de travail décisionnelles libre-service (SSBI). La capacité critique de l’entreprise peut être utilisée pour isoler les grands modèles d’entreprise en leur fournissant des ressources garanties, avec l’accès de création accordé uniquement au service informatique. La capacité SSBI peut être utilisée pour héberger un nombre croissant de modèles plus petits, avec un accès accordé aux analystes de l’entreprise. La capacité SSBI peut parfois rencontrer des temps d’attente acceptables pour les requêtes ou une actualisation.

Au fil du temps, les administrateurs de capacité peuvent équilibrer les espaces de travail entre les capacités en déplaçant le contenu entre des espaces de travail, ou les espaces de travail entre des capacités, et en mettant à l’échelle les capacités. En règle générale, la taille des instances est augmentée pour héberger des modèles plus volumineux et une montée en charge est effectuée pour une plus grande concurrence.

Rappelez-vous que l’achat d’une licence fournit des cœurs vCore au client. L’achat d’un abonnement **P3** peut être utilisé pour en créer une ou jusqu’à quatre capacités Premium, c’est-à-dire 1 x P3 ou 2 x P2, ou 4 x P1. En outre, avant de migrer une capacité P2 vers une capacité P3, vous pouvez envisager de fractionner les cœurs vCore pour créer deux capacités P1.

## <a name="testing-approaches"></a>Approches de test

Une fois qu’une taille de capacité est déterminée, vous pouvez effectuer des tests en créant un environnement contrôlé. Une option pratique et économique consiste à créer une capacité Azure (référence SKU A), en notant qu’une capacité P1 est de la même taille qu’une capacité A4, les capacités P2 et P3 ayant la même taille que les capacités A5 et A6, respectivement. Les capacités Azure peuvent être créées rapidement et sont facturées sur une base horaire. Ainsi, une fois les tests terminés, elles peuvent être facilement supprimées pour arrêter l’accumulation des coûts.

Le contenu du test peut être ajouté aux espaces de travail créés sur la capacité Azure, puis, en tant qu’utilisateur unique, les rapports peuvent être exécutés pour générer une charge de travail réaliste et représentative des requêtes. S’il existe des modèles d’importation, une actualisation de chaque modèle doit également être effectuée. Les outils de surveillance peuvent ensuite être utilisés pour passer en revue toutes les métriques afin de comprendre l’utilisation des ressources.

Il est important que les tests soient reproductibles. Les tests doivent être exécutés plusieurs fois et ils doivent fournir approximativement le même résultat à chaque fois. Une moyenne de ces résultats peut être utilisée pour extrapoler et estimer une charge de travail dans de véritables conditions de production.

Si vous disposez déjà d’une capacité et des rapports pour lesquels vous souhaitez charger un test, utilisez l’[outil de génération de charge PowerShell](https://aka.ms/PowerBILoadTestingTool) pour générer rapidement un test de charge. L’outil vous permet d’estimer le nombre d’instances de chaque rapport que votre capacité peut exécuter en une heure. Vous pouvez utiliser l’outil pour évaluer l’aptitude de votre capacité à effectuer un rendu de rapport individuel ou à afficher plusieurs rapports en parallèle. Pour plus d’informations, consultez la vidéo [Microsoft Power BI: Capacité Premium](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Pour générer un test plus complexe, envisagez de développer une application de test de charge simulant une charge de travail réaliste. Pour plus d’informations, consultez le webinaire [Applications Power BI de test de charge avec le test de charge Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/).

## <a name="acknowledgements"></a>Accusés de réception

Cet article a été écrit par Peter Myers, expert Data Plateform MVP et BI indépendant avec des solutions [Bitwise](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Scénarios de capacité Premium](service-premium-capacity-scenarios.md)   
  
D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

||||||