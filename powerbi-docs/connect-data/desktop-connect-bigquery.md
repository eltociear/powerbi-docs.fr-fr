---
title: Se connecter à une base de données Google BigQuery dans Power BI Desktop
description: Se connecter et utiliser facilement Google BigQuery dans Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 7cffba9178d4eec0bfd468040b7551768aab7f1d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405879"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Se connecter à une base de données Google BigQuery dans Power BI Desktop
Dans Power BI Desktop, vous pouvez vous connecter à une base de données Google **BigQuery** et utiliser les données sous-jacentes comme n’importe quelle autre source de données dans Power BI Desktop.

## <a name="connect-to-google-bigquery"></a>Se connecter à Google BigQuery
Pour vous connecter à une base de données Google **BigQuery**, sélectionnez **Obtenir des données** dans le ruban **Accueil** de Power BI Desktop. Sélectionnez **Base de données** dans les catégories à gauche pour afficher **Google BigQuery**.

![Obtenir la boîte de dialogue de données pour Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

Dans la fenêtre **Google BigQuery** qui s’affiche, connectez-vous à votre compte Google BigQuery et sélectionnez **Connect**.

![Se connecter à Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

Lorsque vous êtes connecté, vous voyez la fenêtre suivante qui indique que vous avez été authentifié. 

![Connecté à Google](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Une fois que vous êtes connecté, une fenêtre **Navigateur** apparaît et affiche les données disponibles sur le serveur. Vous pouvez ensuite sélectionner un ou plusieurs éléments à importer et utiliser dans **Power BI Desktop**.

![Données de Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>Considérations et limitations
Il existe quelques limites et considérations à prendre en compte pour le connecteur Google **BigQuery** :

* Le connecteur Google BigQuery est disponible dans Power BI Desktop et dans le service Power BI. Dans le service Power BI, le connecteur est accessible à l’aide de la connexion cloud-à-cloud de Power BI à Google BigQuery.

* Vous pouvez utiliser Power BI avec le **projet de facturation** Google BigQuery. Par défaut, Power BI utilise le premier projet de la liste retournée pour l’utilisateur. 

  Pour personnaliser le comportement du projet de facturation quand vous l’utilisez avec Power BI, spécifiez l’option suivante dans le M sous-jacent à l’étape Source, qui peut être personnalisée à l’aide de l’**éditeur Power Query** dans Power BI Desktop :

  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])
  ```

  À compter de la version de septembre 2020, nous avons activé la prise en charge de l’[API de stockage Google BigQuery](https://cloud.google.com/bigquery/docs/reference/storage). Cette fonctionnalité est activée par défaut et contrôlée par l’argument booléen facultatif appelé « UseStorageApi ». Certains clients peuvent rencontrer des problèmes avec cette fonctionnalité s’ils utilisent des autorisations granulaires. Dans ce scénario, le message d’erreur suivant peut s’afficher :

  `ERROR [HY000] [Microsoft][BigQuery] (131) Unable to authenticate with Google BigQuery Storage API. Check your account permissions`

  Vous pouvez résoudre ce problème en ajustant les autorisations utilisateur pour l’API de stockage. Attribuez ces autorisations d’API de stockage :

  - `bigquery.readsessions.create` : crée une nouvelle session de lecture via l’API de stockage BigQuery.
  - `bigquery.readsessions.getData` : lit des données à partir d’une session de lecture via l’API de stockage BigQuery.
  - `bigquery.readsessions.update` : met à jour une session de lecture via l’API de stockage BigQuery.

  Ces autorisations sont généralement fournies dans le rôle BigQuery.User. Pour plus d’informations, consultez [Rôles et autorisations prédéfinis de Google BigQuery](https://cloud.google.com/bigquery/docs/access-control).
  
  Si les étapes ci-dessus ne permettent pas de résoudre le problème ou si vous voulez désactiver la prise en charge de l’API de stockage, modifiez votre requête comme suit :
  ```
  Source = GoogleBigQuery.Database([UseStorageApi=false])
  ```
  Ou, si vous utilisez déjà un projet de facturation, remplacez la requête par ceci :
  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here", UseStorageApi=false])
  ```

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](../fundamentals/desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
