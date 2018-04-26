---
title: Utilisation de données tabulaires Analysis Services dans Power BI Desktop
description: Données tabulaires Analysis Services dans Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 4ca8e0b634cc2b47d562d535506fdc1fae6e527e
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="using-analysis-services-tabular-data-in-power-bi-desktop"></a>Utilisation de données tabulaires Analysis Services dans Power BI Desktop
Avec Power BI Desktop, il existe deux façons d’obtenir et de se connecter à des données à partir de vos modèles tabulaires SQL Server Analysis Services : vous pouvez explorer à l’aide d’une connexion active ou sélectionner des éléments et les importer dans Power BI Desktop.

Examinons cela de plus près.

**Explorer à l’aide d’une connexion active** : lors de l’utilisation d’une connexion active, les éléments dans votre perspective ou modèle tabulaire, comme les tables, les colonnes et les mesures, apparaissent dans votre liste Champs dans Power BI Desktop. Vous pouvez utiliser les outils de visualisation et de création de rapports avancés de Power BI Desktop pour explorer votre modèle tabulaire de manière interactive et novatrice.

Lors de la connexion en temps réel, aucune donnée du modèle tabulaire n’est importée dans Power BI Desktop. Chaque fois que vous interagissez avec une visualisation, Power BI Desktop interroge le modèle tabulaire et calcule les résultats que vous voyez. Les données affichées sont toujours les plus récentes. Les modèles tabulaires sont hautement sécurisés. Les éléments qui apparaissent dans Power BI Desktop varient en fonction des autorisations dont vous disposez sur le modèle tabulaire auquel vous êtes connecté.

Quand vous avez créé des rapports dynamiques dans Power BI Desktop, vous pouvez les partager en les publiant sur votre site Power BI. Quand vous publiez sur votre site Power BI un fichier Power BI Desktop avec une connexion active à un modèle tabulaire, une passerelle de données locale doit être installée et configurée par un administrateur. Pour plus d’informations, consultez [Passerelle de données locale](service-gateway-onprem.md).

**Sélectionner des éléments et les importer dans Power BI Desktop** : lorsque vous vous connectez avec cette option, vous pouvez sélectionner des éléments tels que des tables, des colonnes et des mesures dans votre perspective ou modèle tabulaire et les charger dans un modèle Power BI Desktop. Vous pouvez utiliser l’Éditeur de requête avancé de Power BI Desktop pour préciser ce que vous souhaitez obtenir. Vous pouvez utiliser les fonctionnalités de modélisation de Power BI Desktop pour modéliser davantage les données. Aucune connexion active entre Power BI Desktop et le modèle tabulaire n’est conservée. Vous pouvez ensuite explorer votre modèle Power BI Desktop hors connexion ou le publier sur votre site Power BI.

## <a name="to-connect-to-a-tabular-model"></a>Pour vous connecter à un modèle tabulaire
1. Dans Power BI Desktop, sous l’onglet **Accueil**, cliquez sur **Obtenir des données**.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata.png)
2. Cliquez sur **Base de données SQL Server Analysis Services**, puis sur **Se connecter**.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Entrez le nom du serveur et sélectionnez un mode de connexion. 
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Cette étape varie en fonction du mode de connexion que vous avez sélectionné :

* Si vous vous connectez en temps réel, dans le navigateur, sélectionnez une perspective ou un modèle tabulaire.
  
  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
* Si vous avez choisi de sélectionner des éléments et d’obtenir des données, dans le navigateur, sélectionnez une perspective ou un modèle tabulaire. Vous pouvez sélectionner en plus uniquement des tables ou des colonnes spécifiques à charger. Pour mettre en forme vos données avant le chargement, cliquez sur Modifier pour ouvrir l’Éditeur de requête. Lorsque vous êtes prêt, cliquez sur Charger pour importer les données dans Power BI Desktop.

  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Forum Aux Questions
**Question :** Ai-je besoin d’une passerelle de données locale ?

**Réponse :** cela dépend. Si vous utilisez Power BI Desktop pour vous connecter en temps réel à un modèle tabulaire mais que vous n’avez pas l’intention de publier sur votre site Power BI, vous n’avez pas besoin de passerelle. En revanche, si vous envisagez de publier sur votre site Power BI, une passerelle de données est nécessaire pour garantir une communication sécurisée entre le service Power BI et votre serveur Analysis Services local. Parlez à votre administrateur de serveur Analysis Services avant d’installer une passerelle de données.

Si vous choisissez de sélectionner des éléments et d’obtenir des données, vous importez des données de modèle tabulaire directement dans votre fichier Power BI Desktop. Dans ce cas, aucune passerelle n’est nécessaire.

**Question :** quelle est la différence entre une connexion active à un modèle tabulaire à partir du service Power BI et la connexion active à partir de Power BI Desktop ?

**Réponse :** Lors de la connexion active à un modèle tabulaire de votre site dans le service Power BI vers une base de données Analysis Services locale dans votre organisation, une passerelle de données locale est nécessaire pour sécuriser les communications. Lors de la connexion active à un modèle tabulaire à partir de Power BI Desktop, une passerelle n’est pas nécessaire car Power BI Desktop et le serveur Analysis Services auquel vous vous connectez s’exécutent localement dans votre organisation. Toutefois, si vous publiez votre fichier Power BI Desktop sur votre site Power BI, une passerelle est nécessaire.

**Question :** si j’ai créé une connexion active, puis-je me connecter à une autre source de données dans le même fichier Power BI Desktop ?

**Réponse :** non. Vous ne pouvez pas explorer des données actives et vous connecter à un autre type de source de données dans le même fichier. Si vous avez déjà importé des données ou si vous vous êtes connecté à une autre source de données dans un fichier Power BI Desktop, vous devez créer un fichier pour effectuer une exploration active.

**Question :** si j’ai créé une connexion active, puis-je modifier le modèle ou la requête dans Power BI Desktop ?

**Réponse :** Vous pouvez créer des mesures de niveau rapport dans Power BI Desktop, mais toutes les autres fonctionnalités d’interrogation et de modélisation sont désactivées lors de l’exploration de données actives.

**Question :** si j’ai créé une connexion active, est-elle sécurisée ?

**Réponse :** Oui. Vos informations d’identification Windows actuelles sont utilisées pour la connexion au serveur Analysis Services. Vous ne pouvez pas utiliser d’informations d’identification de base ou stockées dans le service Power BI ou Power BI Desktop lors de l’exploration active.

**Question :** dans le navigateur, je vois un modèle et une perspective. Quelle est la différence ?

**Réponse :** une perspective est une vue particulière d’un modèle tabulaire. Elle peut inclure uniquement des tables, des colonnes ou des mesures spécifiques, en fonction des besoins d’analyse des données. Un modèle tabulaire contient toujours au moins une perspective, qui peut inclure tout le contenu du modèle. Si vous ne savez pas quoi sélectionner, contactez votre administrateur.

## <a name="to-change-the-server-name-after-initial-connection"></a>Pour modifier le nom du serveur après la connexion initiale
Lorsque vous créez un fichier Power BI Desktop avec une connexion active, il peut arriver que vous souhaitiez basculer la connexion vers un autre serveur. Par exemple, si vous avez créé votre fichier Power BI Desktop lors de la connexion à un serveur de développement, et avant la publication vers le service Power BI, vous souhaitez basculer la connexion vers un serveur de production.

1. Sélectionnez **Modifier les requêtes** dans le ruban.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_editquery.png)
2. Entrez le nouveau nom du serveur.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_dialog.png)

