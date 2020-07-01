---
title: Connexion aux données tabulaires Analysis Services dans Power BI Desktop
description: 'Avec Power BI Desktop, vous pouvez vous connecter à vos modèles tabulaires SQL Server Analysis Services et en obtenir les données de deux façons : en utilisant une connexion active ou en sélectionnant les éléments à importer dans Power BI Desktop.'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/28/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6f9661b6cda8782e83e64e30f55ae4b0d8bf6fa2
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85224870"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Connexion aux données tabulaires Analysis Services dans Power BI Desktop
Avec Power BI Desktop, il existe deux moyens de se connecter aux modèles tabulaires SQL Server Analysis Services et d’en récupérer des données : les explorer à l’aide d’une connexion active ou sélectionner des éléments et les importer dans Power BI Desktop.

Examinons cela de plus près.

**Explorer à l’aide d’une connexion active** : si vous utilisez une connexion active, les éléments contenus dans votre perspective ou modèle tabulaire, comme les tables, les colonnes et les mesures, sont listés dans le volet **Champs** dans Power BI Desktop. Vous pouvez utiliser les outils de visualisation et de création de rapports avancés de Power BI Desktop pour explorer votre modèle tabulaire de manière interactive et novatrice.

Lors de la connexion en temps réel, aucune donnée du modèle tabulaire n’est importée dans Power BI Desktop. Chaque fois que vous interagissez avec une visualisation, Power BI Desktop interroge le modèle tabulaire et calcule les résultats que vous voyez. Vous voyez toujours les données les plus récentes qui sont disponibles dans le modèle tabulaire, provenant du dernier traitement ou des tables DirectQuery disponibles dans le modèle tabulaire. 

Gardez à l’esprit que les modèles tabulaires sont hautement sécurisés. Les éléments qui apparaissent dans Power BI Desktop varient en fonction des autorisations dont vous disposez sur le modèle tabulaire auquel vous êtes connecté.

Quand vous avez créé des rapports dynamiques dans Power BI Desktop, vous pouvez les partager en les publiant sur votre site Power BI. Quand vous publiez sur votre site Power BI un fichier Power BI Desktop avec une connexion active à un modèle tabulaire, une passerelle de données locale doit être installée et configurée par un administrateur. Pour plus d’informations, consultez [Passerelle de données locale](service-gateway-onprem.md).

**Sélectionner des éléments et les importer dans Power BI Desktop** : si vous choisissez cette option de connexion, vous pouvez sélectionner des éléments tels que des tables, des colonnes et des mesures dans votre perspective ou modèle tabulaire et les charger ensuite dans un modèle Power BI Desktop. Utilisez l’Éditeur Power Query de Power BI Desktop pour affiner la mise en forme des données ainsi que ses fonctionnalités de modélisation pour modéliser davantage les données. Étant donné qu’il n’y a pas de connexion active entre Power BI Desktop et le modèle tabulaire, vous pouvez ensuite explorer votre modèle Power BI Desktop hors connexion ou le publier sur votre site Power BI.

## <a name="to-connect-to-a-tabular-model"></a>Pour vous connecter à un modèle tabulaire
1. Dans Power BI Desktop, sous l’onglet **Accueil**, sélectionnez **Obtenir des données** > **Plus** > **Base de données**.
   
1. Sélectionnez **Base de données SQL Server Analysis Services**, puis sélectionnez **Se connecter**.
   
   ![Sélectionner une base de données SQL Server Analysis Services](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Dans la fenêtre **Base de données SQL Server Analysis Services**, entrez le nom du **Serveur**, choisissez un mode de connexion, puis sélectionnez **OK**.
   
   ![Fenêtre Base de données SQL Server Analysis Services](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Cette étape dans la fenêtre **Navigateur** varie en fonction du mode de connexion que vous avez sélectionné :

   - Si vous avez choisi d’utiliser une connexion active, sélectionnez une perspective ou un modèle tabulaire.
  
      ![Sélectionner un modèle tabulaire ou une perspective dans le Navigateur](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
   - Si vous avez choisi de sélectionner des éléments et d’obtenir des données, sélectionnez un modèle tabulaire ou une perspective, puis sélectionnez une table ou une colonne particulière à charger. Si vous voulez mettre en forme les données avant leur chargement, sélectionnez **Modifier les requêtes** pour ouvrir l’Éditeur Power Query. Lorsque vous êtes prêt, sélectionnez **Charger** pour importer les données dans Power BI Desktop.

      ![Sélectionner la table ou la colonne à charger dans le Navigateur](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Forum Aux Questions
**Question :** Une passerelle de données locale est-elle nécessaire ?

**Réponse :** Cela dépend. Si vous utilisez Power BI Desktop pour vous connecter à un modèle tabulaire à l’aide d’une connexion active, mais que vous n’avez pas l’intention de publier sur votre site Power BI, vous n’avez pas besoin de passerelle. En revanche, si vous envisagez de publier sur votre site Power BI, une passerelle de données est nécessaire pour garantir une communication sécurisée entre le service Power BI et votre serveur Analysis Services local. Parlez à votre administrateur de serveur Analysis Services avant d’installer une passerelle de données.

Si vous choisissez de sélectionner des éléments et d’obtenir des données, vous importez les données du modèle tabulaire directement dans votre fichier Power BI Desktop. Dans ce cas, aucune passerelle n’est nécessaire.

**Question :** Quelle est la différence entre une connexion active à un modèle tabulaire à partir du service Power BI et une connexion active à partir de Power BI Desktop ?

**Réponse :** Si vous établissez une connexion active à un modèle tabulaire de votre site dans le service Power BI vers une base de données Analysis Services locale dans votre organisation, une passerelle de données locale est nécessaire pour sécuriser les communications. Lors de la connexion active à un modèle tabulaire à partir de Power BI Desktop, une passerelle n’est pas nécessaire car Power BI Desktop et le serveur Analysis Services auquel vous vous connectez s’exécutent localement dans votre organisation. Toutefois, si vous publiez votre fichier Power BI Desktop sur votre site Power BI, une passerelle est nécessaire.

**Question :** Si j’ai créé une connexion active, puis-je me connecter à une autre source de données dans le même fichier Power BI Desktop ?

**Réponse :** Non. Vous ne pouvez pas explorer des données actives et vous connecter à un autre type de source de données dans le même fichier. Si vous avez déjà importé des données ou si vous vous êtes connecté à une autre source de données dans un fichier Power BI Desktop, vous devez créer un autre fichier pour effectuer une exploration active.

**Question :** Si j’ai créé une connexion active, puis-je modifier le modèle ou la requête dans Power BI Desktop ?

**Réponse :** Vous pouvez créer des mesures au niveau du rapport dans Power BI Desktop, mais toutes les autres fonctionnalités de requêtes et de modélisation sont désactivées lors de l’exploration de données actives.

**Question :** La connexion active que j’ai créée est-elle sécurisée ?

**Réponse :** Oui. Vos informations d’identification Windows actuelles sont utilisées pour la connexion au serveur Analysis Services. Vous ne pouvez pas utiliser d’informations d’identification de base ou stockées dans le service Power BI ou Power BI Desktop lors de l’exploration active.

**Question :** Dans le navigateur, je vois un modèle et une perspective. Quelle est la différence ?

**Réponse :** Une perspective est une présentation particulière d’un modèle tabulaire. Elle peut inclure uniquement des tables, des colonnes ou des mesures spécifiques, en fonction des besoins d’analyse des données. Un modèle tabulaire contient toujours au moins une perspective, qui peut inclure tout le contenu du modèle. Si vous ne savez pas quelle perspective sélectionner, contactez votre administrateur.

**Question :** Existe-t-il des fonctionnalités d’Analysis Services qui changent le comportement Power BI ?

**Réponse :** Oui. Selon les fonctionnalités utilisées par votre modèle tabulaire, l’expérience dans Power BI Desktop peut changer. Voici quelques exemples :
* Vous pouvez voir les mesures du modèle regroupées en haut de la liste du panneau **Champs** au lieu qu’elles se trouvent dans des tables en regard des colonnes. Elles sont ainsi plus faciles à trouver, mais ne vous inquiétez pas, vous pouvez toujours les utiliser comme d’habitude.

* Si des groupes de calcul sont définis pour le modèle tabulaire, vous pouvez les utiliser seulement en combinaison avec les mesures de modèle, et non pas avec les mesures implicites que vous créez en ajoutant des champs numériques à un visuel. L’indicateur **DiscourageImplicitMeasures** peut également avoir été défini manuellement pour le modèle, ce qui a le même effet. Pour plus d’informations, consultez [Groupes de calcul dans Analysis Services](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups#benefits).

## <a name="to-change-the-server-name-after-initial-connection"></a>Pour modifier le nom du serveur après la connexion initiale
Après avoir créé un fichier Power BI Desktop à l’aide d’une connexion active, il peut arriver que vous ayez besoin de vous connecter à un autre serveur. Par exemple, si vous avez créé votre fichier Power BI Desktop lors de la connexion à un serveur de développement, et avant la publication vers le service Power BI, vous souhaitez basculer la connexion vers un serveur de production.

Pour changer le nom du serveur :

1. Sélectionnez **Modifier les requêtes** sous l’onglet **Accueil**.

2. Dans la fenêtre **Base de données SQL Server Analysis Services**, entrez le nouveau nom du **Serveur**, puis sélectionnez **OK**.

   
## <a name="troubleshooting"></a>Résolution des problèmes 
La liste suivante décrit tous les problèmes connus qui peuvent se produire au moment de la connexion à SQL Server Analysis Services (SSAS) ou Azure Analysis Services : 

* **Erreur : Impossible de charger le schéma de modèle** : Cette erreur se produit généralement quand l’utilisateur qui se connecte à Analysis Services n’a pas accès à la base de données ou au modèle.

