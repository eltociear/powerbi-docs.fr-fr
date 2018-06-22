---
title: Actualisation incrémentielle dans Power BI Premium
description: Découvrez comment permettre l’utilisation de jeux de données très volumineux dans le service Power BI Premium.
author: christianwade
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/30/2018
ms.author: chwade
LocalizationGroup: Premium
ms.openlocfilehash: 1b6a3c35abeff33e2fb1e0fecdc5c2a5c88e1530
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34298179"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Actualisation incrémentielle dans Power BI Premium

L’actualisation incrémentielle permet d’utiliser des jeux de données très volumineux dans le service Power BI Premium, en offrant les avantages suivants :

- **Les actualisations sont plus rapides.** Seules les données qui ont changé sont actualisées. Par exemple, vous pouvez actualiser uniquement les données des cinq derniers jours dans un jeu de données de dix ans.

- **Les actualisations sont plus fiables.** Vous n’avez notamment pas besoin de conserver des connexions longues à des systèmes sources volatiles.

- **La consommation des ressources est réduite.** Comme il y a moins de données à actualiser, la consommation globale de mémoire et d’autres ressources diminue.

## <a name="how-to-use-incremental-refresh"></a>Comment utiliser l’actualisation incrémentielle

Les stratégies d’actualisation incrémentielle sont définies dans Power BI Desktop et sont appliquées après avoir été publiées sur le service Power BI.

Commencez par activer l’actualisation incrémentielle dans les fonctionnalités en préversion.

![Options - fonctionnalités en préversion](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Filtrer des jeux de données volumineux dans Power BI Desktop

Les jeux de données volumineux, contenant potentiellement des milliards de lignes, ne peuvent parfois pas être ajoutés dans Power BI Desktop, généralement à cause de la limitation des ressources disponibles sur les PC de bureau des utilisateurs. Ces jeux de données sont par conséquent souvent filtrés avant d’être importés dans Power BI Desktop. C’est toujours le cas, même avec l’actualisation incrémentielle.

#### <a name="rangestart-and-rangeend-parameters"></a>Paramètres RangeStart et RangeEnd

Pour utiliser l’actualisation incrémentielle dans le service Power BI, vous devez filtrer les données à l’aide de paramètres date/heure Power Query définis avec les noms réservés respectant la casse **RangeStart** et **RangeEnd**.

Dans l’éditeur Power Query, sélectionnez **Gérer les paramètres** pour définir les paramètres avec les valeurs par défaut.

![Gérer les paramètres](media/service-premium-incremental-refresh/manage-parameters.png)

Une fois que vous avez défini les paramètres, vous pouvez appliquer le filtre en sélectionnant l’option de menu **Filtre personnalisé** pour une colonne.

![Filtre personnalisé](media/service-premium-incremental-refresh/custom-filter.png)

Vérifiez que les lignes sont filtrées quand la valeur de colonne *est postérieure ou égale à* **RangeStart** et *antérieure* à **RangeEnd**.

![Filtrer les lignes](media/service-premium-incremental-refresh/filter-rows.png)

> [!TIP]
> Les paramètres doivent avoir le type de données date/heure, mais ils peuvent être convertis pour répondre aux exigences de la source de données. Par exemple, la fonction Power Query suivante convertit une valeur date/heure en une valeur similaire à une clé de substitution de type entier au format *aaaammjj*, ce qui est courant pour les entrepôts de données. La fonction peut être appelée à l’étape du filtre.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Sélectionnez **Fermer et appliquer** dans l’éditeur Power Query. Vous devez avoir un sous-ensemble du jeu de données dans Power BI Desktop.

> [!NOTE]
> Une fois publiées, les valeurs des paramètres sont automatiquement remplacées par le service Power BI. Vous n’avez pas besoin de les définir dans les paramètres du jeu de données.

### <a name="define-the-refresh-policy"></a>Définir la stratégie d’actualisation

L’actualisation incrémentielle est disponible dans le menu contextuel des tables, à l’exception des modèles Connexion active.

![Stratégie d’actualisation](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Boîte de dialogue Actualisation incrémentielle

La boîte de dialogue Actualisation incrémentielle s’affiche. Utilisez le bouton bascule pour activer la boîte de dialogue.

![Détails de l’actualisation](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Si l’expression Power Query pour la table ne fait pas référence aux paramètres avec des noms réservés, le bouton bascule est désactivé.

Le texte d’en-tête décrit ce qui suit :

-   L’actualisation incrémentielle est prise en charge uniquement pour les espaces de travail sur une capacité Premium. Les stratégies d’actualisation sont définies dans Power BI Desktop. Elles sont appliquées par les opérations d’actualisation dans le service.

-   Si vous pouvez télécharger le fichier PBIX contenant une stratégie d’actualisation incrémentielle à partir du service Power BI, le fichier ne s’ouvre pas dans Power BI Desktop. Vous ne pourrez bientôt plus du tout le télécharger. Cela ne sera peut-être plus le cas dans une version future, mais sachez que la taille de ces jeux de données peut augmenter considérablement, au point qu’il ne soit plus possible de les télécharger ni de les ouvrir sur un PC de bureau classique.

#### <a name="refresh-ranges"></a>Plages d’actualisation

L’exemple suivant définit une stratégie d’actualisation qui permet de stocker cinq ans de données au total et d’actualiser de manière incrémentielle dix jours de données. Si le jeu de données est actualisé quotidiennement, les étapes suivantes sont effectuées à chaque opération d’actualisation.

-   Ajout d’un nouveau jour de données.

-   Actualisation des données des dix derniers jours avant la date actuelle.

-   Suppression des années du calendrier qui sont antérieures aux cinq années précédant la date actuelle. Par exemple, si la date actuelle est le 1er janvier 2019, l’année 2013 est supprimée.

La première actualisation effectuée dans le service Power BI peut être plus longue, car toutes les données des cinq ans passés doivent être importées. Les actualisations suivantes sont généralement très rapides.

![Plages d’actualisation](media/service-premium-incremental-refresh/refresh-ranges.png)

**Quand vous avez terminé la définition de ces plages, vous pouvez passer directement à l’étape de publication suivante. Les autres menus déroulants concernent des fonctionnalités avancées.**

#### <a name="detect-data-changes"></a>Détecter les changements de données

L’actualisation incrémentielle des données des dix derniers jours est évidemment beaucoup plus rapide qu’une actualisation complète des données des cinq années. Toutefois, ce processus peut encore être amélioré. Si vous cochez la case **Détecter les changements de données**, vous pouvez sélectionner une colonne date/heure à utiliser pour identifier et actualiser uniquement les jours où les données ont changé. Cela suppose que cette colonne existe dans le système source, généralement à des fins d’audit. La valeur maximale de cette colonne est évaluée pour chacune des périodes définies dans la plage incrémentielle. Si cette valeur n’a pas changé depuis la dernière actualisation, la période n’a pas besoin d’être actualisée. Dans l’exemple, cela peut réduire les jours concernés par l’actualisation incrémentielle de dix à deux.

![Détecter les changements](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> Dans la conception actuelle, la colonne utilisée pour détecter les changements de données doit être persistante et mise en mémoire cache. Essayez l’une des techniques suivantes pour réduire la consommation de mémoire et la cardinalité.
>
> Conservez uniquement la valeur maximale de cette colonne persistante au moment de l’actualisation, éventuellement à l’aide d’une fonction Power Query.
>
> Diminuez la précision à un niveau acceptable en fonction de vos exigences de fréquence d’actualisation.
>
> Nous prévoyons de permettre la définition de requêtes personnalisées pour détecter les changements de données dans une version ultérieure. Cela permettrait d’éviter totalement la persistance de la valeur de colonne.

#### <a name="only-refresh-complete-periods"></a>Actualiser uniquement les périodes complètes

Supposons que vous avez planifié l’actualisation à 4 h 00 chaque matin. Vous ne voudrez peut-être pas prendre en compte les données éventuellement ajoutées au système source pendant ces quatre heures. L’actualisation de certaines métriques métier, comme le nombre de barils par jour dans l’industrie du pétrole et du gaz, n’a aucun sens si elle concerne des jours partiels.

Un autre exemple est l’actualisation des données d’un système financier où les données du mois précédent sont approuvées le 12e jour calendaire du mois. Vous pouvez définir une plage incrémentielle d’un mois et planifier l’actualisation le 12e jour du mois. Avec cette option activée, les données du mois de janvier sont actualisées le 12 février, par exemple.

![Périodes complètes](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> Les opérations d’actualisation dans le service sont effectuées selon l’heure UTC. Cela peut déterminer la date d’effet de l’actualisation et impacter les périodes complètes. Nous prévoyons d’ajouter la possibilité d’ignorer la date d’effet pour une opération d’actualisation.

## <a name="publish-to-the-service"></a>Publier sur le service

L’actualisation incrémentielle est une fonctionnalité disponible uniquement dans Premium. Dans la boîte de dialogue Publier, vous pouvez donc uniquement sélectionner un espace de travail sur une capacité Premium.

![Publier sur le service](media/service-premium-incremental-refresh/publish.png)

Vous pouvez désormais actualiser le modèle. La première actualisation peut être plus longue en raison de l’importation des données d’historique. Les actualisations suivantes peuvent être beaucoup plus rapides si elles sont effectuées à l’aide de l’actualisation incrémentielle.

## <a name="query-timeouts"></a>Délais d’expiration des requêtes

L’article sur la [résolution des problèmes d’actualisation](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) explique que les opérations d’actualisation dans le service Power BI sont soumises à des délais d’expiration. Les requêtes peuvent également être limitées par le délai d’expiration par défaut pour la source de données. La plupart des sources relationnelles permettent d’ignorer les délais d’expiration dans l’expression M. Par exemple, l’expression ci-dessous utilise la [fonction d’accès aux données de SQL Server](https://msdn.microsoft.com/query-bi/m/sql-database) pour définir le délai à deux heures. Chaque période définie par les plages de la stratégie soumet une requête qui respecte le paramètre de délai d’expiration de la commande.

```
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```
