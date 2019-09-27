---
title: Se connecter à des jeux de données dans le service Power BI à partir de Power BI Desktop
description: Utilisez un jeu de données commun pour plusieurs rapports Power BI Desktop dans plusieurs espaces de travail et gérez le cycle de vie de votre rapport.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f3c72de197203adcad1020bc244ff0bc215e10bd
ms.sourcegitcommit: 4222ebad1a3a32d8040f6a615a0b7f173d7869d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71164476"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Se connecter à des jeux de données dans le service Power BI à partir de Power BI Desktop
Vous pouvez établir une connexion active à un jeu de données partagé dans le service Power BI, et créer de nombreux rapports différents à partir du même jeu de données. Cela signifie que vous pouvez créer votre modèle de données idéal dans Power BI Desktop et le publier sur le service Power BI. Ensuite, vos coéquipiers et vous-même pouvez créer plusieurs rapports différents (dans des fichiers .pbix distincts) à partir de ce modèle de données commun, et les enregistrer dans différents espaces de travail. Cette fonctionnalité est appelée **Connexion active du service Power BI**.

![Obtenir des données à partir du service Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

Cette fonctionnalité présente toutes sortes d’avantages, dont des meilleures pratiques que nous allons évoquer dans le cadre de cet article. Il y a également quelques considérations et limitations à prendre en compte. Celles-ci figurent à la fin de cet article et nous vous recommandons vivement de les lire.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Utilisation d’une Connexion active du service Power BI pour gérer le cycle de vie des rapports
L’un des problèmes liés à la popularité de Power BI est la prolifération des rapports, des tableaux de bord et de leurs modèles de données sous-jacents. En effet, il est facile de créer des rapports percutants dans **Power BI Desktop** puis de les partager ([publier](desktop-upload-desktop-files.md)) sur le **service Power BI**, ainsi que de créer des tableaux de bord à partir de ces jeux de données. Étant donné que de nombreux utilisateurs procèdent de la sorte, souvent en utilisant les mêmes (ou presque les mêmes) jeux de données, il est devenu difficile de déterminer le jeu de données sur lequel un rapport est basé, ainsi que la fraîcheur du jeu de données en question. La fonctionnalité **Connexion active du service Power BI** relève ce défi en facilitant la création, le partage et le développement cohérents de rapports et tableaux de bord basés sur un jeu de données commun.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Créer et partager un jeu de données utilisable par chacun
Supposons qu’Anna (analyste d’entreprise) fait partie de votre équipe et qu’elle excelle dans la création de modèles de données (souvent appelés jeux de données) de qualité. Forte de son expertise, Anna peut créer un jeu de données et un rapport, puis partager ce dernier sur le **service Power BI**.

![Publication sur le service Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Tout le monde apprécie son rapport et son jeu de données, et cela peut occasionner un problème. En effet, tous les membres de son équipe peuvent tenter de créer *leur propre version* de ce jeu de données, puis partager leur propre rapport avec l’équipe. Soudainement, il y a une multitude de rapports (basés sur des jeux de données différents) au sein de l’espace de travail de votre équipe dans le **service Power BI**. Quel est le plus récent ? Les jeux de données utilisés sont-ils identiques, ou seulement presque identiques ? Quelles sont les différences ? La fonctionnalité **Connexion active du service Power BI** peut changer tout cela pour mieux. La section suivante explique comment d’autres personnes peuvent utiliser le jeu de données d’Annette pour créer leurs propres rapports, dans leurs propres espaces de travail, et permettre à chacun d’utiliser le même jeu de données solide, vérifié et publié pour générer leurs rapports uniques.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Se connecter à un jeu de données du service Power BI à l’aide d’une connexion active
Après avoir créé un rapport (et le jeu de données sur lequel il est basé), Anna publie celui-ci sur le **service Power BI**. Le rapport s’affiche alors dans l’espace de travail de son équipe sur le service Power BI. Si elle l’enregistre dans un *espace de travail de nouvelle expérience*, elle peut définir l’autorisation Générer pour le rendre accessible en lecture et à l’utilisation à tout le monde dans et en dehors de son espace de travail.

Pour en savoir plus sur les espaces de travail de nouvelle expérience, consultez [Espaces de travail d’application](service-new-workspaces.md).

D’autres membres dans et en dehors de l’espace de travail d’Anna peuvent à présent établir une connexion active au modèle de données qu’elle a partagé (à l’aide de la fonctionnalité **Connexion active du service Power BI**) et créer leurs propres rapports uniques à partir de *son jeu de données d’origine*, dans *leurs propres espaces de travail de nouvelle expérience*.

L’image suivante montre comment Annette crée un rapport **Power BI Desktop** (et son modèle de données) et le publie sur le **service Power BI**. Ensuite, d’autres personnes peuvent se connecter à son modèle de données à l’aide de la **connexion active du service Power BI** et créer leurs propres rapports uniques dans leurs propres espaces de travail, basés sur son jeu de données.

![Plusieurs rapports basés sur le même jeu de données](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Si vous enregistrez votre jeu de données dans un [espace de travail partagé classique](service-create-workspaces.md), seuls les membres de cet espace de travail génèrent des rapports sur votre jeu de données. Pour que vous puissiez établir une Connexion active du service Power BI, le jeu de données auquel vous vous connectez doit figurer dans un espace de travail partagé dont vous êtes membre.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Procédure détaillée d’utilisation de la fonctionnalité Connexion active du service Power BI
Maintenant que nous connaissons l’utilité de la fonctionnalité **Connexion active du service Power BI** et comment s’en servir en tant que bonne pratique de la gestion du cycle de vie des rapports, nous allons étudier les étapes qui permettent de passer de l’excellent rapport d’Annette (et du jeu de données sous-jacent) à un jeu de données partagé que ses coéquipiers Power BI peuvent utiliser.

### <a name="publish-a-power-bi-report-and-dataset"></a>Publier un rapport et un jeu de données Power BI
La première étape de la gestion du cycle de vie des rapports à l’aide de la fonctionnalité **Connexion active du service Power BI** est de disposer d’un rapport (et d’un jeu de données) que les coéquipiers ont envie utiliser. Anna doit donc commencer par **publier** son rapport à partir de **Power BI Desktop**. Pour ce faire, elle sélectionne **Publier** dans le ruban **Accueil** de Power BI Desktop.

![Publier un rapport](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Si Anna n’est pas connecté au compte service Power BI, une fenêtre contextuelle l’invite à le faire.

![Se connecter à Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

À partir de là, elle peut choisir l’espace de travail sur lequel le rapport et le jeu de données doivent être publiés. Rappelez-vous que si elle l’enregistre dans un espace de travail de nouvelle expérience, toute personne disposant de l’autorisation Générer peut accéder à ce jeu de données. L’autorisation Générer est définie dans le service Power BI, après la publication. Si le travail est enregistré dans un espace de travail classique, seuls les membres ayant accès à l’espace de travail où un rapport est publié peuvent accéder à son jeu de données à l’aide d’une **connexion active du service Power BI**.

![Publication sur le service Power BI](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

Le processus de publication commence et **Power BI Desktop** affiche sa progression.

![Publication en cours](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Une fois la publication terminée, **Power BI Desktop** vous indique la réussite de l’opération et fournit quelques liens pour accéder au rapport proprement dit sur le **service Power BI**, ainsi qu’un lien pour accéder à des **Informations rapides** sur le rapport.

![Publication réussie](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Maintenant que votre rapport avec son jeu de données se trouve dans le service Power BI, vous pouvez également le *promouvoir* afin d’attester de sa qualité et de sa fiabilité. Vous pouvez même demander qu’il soit *certifié* par une autorité centrale dans votre locataire Power BI. Avec l’une de ces approbations, votre jeu de données apparaît toujours en haut de la liste quand des utilisateurs recherchent des jeux de données. Si vous le souhaitez, vous pouvez en savoir plus sur le processus de [promotion de votre jeu de données](service-datasets-promote.md). 

La dernière étape consiste à définir l’*autorisation Générer* pour le jeu de données sur lequel le rapport est basé. L’autorisation Générer détermine qui peut voir et utiliser votre jeu de données. Vous pouvez la définir dans l’espace de travail proprement dit, ou quand vous partagez une application à partir de l’espace de travail. Apprenez-en davantage sur la configuration de l’[autorisation Générer](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

Voyons à présent comment les autres coéquipiers ayant accès à l’espace de travail dans lequel le rapport (et le jeu de données) a été publié peuvent se connecter au jeu de données pour créer leurs propres rapports.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Établir une Connexion active du service Power BI au jeu de données publié
Pour établir une connexion au rapport publié et créer votre propre rapport basé sur le jeu de données publié, sélectionnez **Obtenir des données** dans le ruban **Accueil** de **Power BI Desktop**, sélectionnez **Service Power BI** dans le volet gauche, puis **Jeux de données Power BI**.

Si vous n’êtes pas connecté à Power BI, vous êtes invité à le faire. Une fois connecté, vous voyez une fenêtre qui affiche les espaces de travail dont vous êtes membre, dans laquelle pouvez sélectionner celui qui contient le jeu de données avec lequel vous souhaitez établir une **Connexion active du service Power BI**.

Les jeux de données figurant dans la liste sont tous les jeux de données partagés pour lesquels vous disposez de l’autorisation Générer, dans n’importe quel espace de travail. Vous pouvez rechercher un jeu de données spécifique et voir son nom, son propriétaire, l’espace de travail où il réside et la date de sa dernière actualisation. Les jeux de données *approuvés*, soit certifiés soit promus, figurent également en haut de la liste. 

![Liste des jeux de données disponibles](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

Lorsque vous sélectionnez **Charger** dans la fenêtre, vous établissez une connexion active au jeu de données sélectionné, ce qui signifie que les données que vous voyez (les champs et leurs valeurs) sont chargées dans **Power BI Desktop** en temps réel.

![Champs de jeux de données dans le volet Champs](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

À présent, vous (et vos coéquipiers) pouvez créer et partager des rapports personnalisés basés sur le même jeu de données. Il s’agit d’un excellent moyen d’avoir un jeu de données bien formé créé par une personne expérimentée (en l’occurrence, Annette) et d’autoriser de nombreux coéquipiers à utiliser ce jeu de données partagé pour créer leurs propres rapports.

## <a name="limitations-and-considerations"></a>Considérations et limitations
Lors de l’utilisation de la **connexion active du service Power BI**, vous devez garder à l’esprit les quelques considérations et limitations suivantes.

* Seuls les utilisateurs disposant de l’autorisation Générer pour un jeu de données peuvent se connecter à un jeu de données publié à l’aide de la **connexion active du service Power BI**. 
* Les utilisateurs de la version gratuite voient uniquement les jeux de données de leur espace de travail personnel et des espaces de travail Premium.
* Dans la mesure où il s’agit d’une connexion active, le volet de navigation de gauche et la modélisation sont désactivés. Ce comportement est similaire à celui observé en cas de connexion à **SQL Server Analysis Services**, et vous pouvez uniquement vous connecter à un jeu de données dans chaque rapport.
* Dans la mesure où il s’agit d’une connexion active, la sécurité au niveau des lignes (RLS) et d’autres comportements de connexion similaires sont appliqués, tout comme en cas de connexion à **SQL Server Analysis Services**.
* Si le propriétaire modifie le fichier .pbix partagé d’origine, le jeu de données et le rapport partagé dans le **service Power BI** sont remplacés. Les rapports basés sur ce jeu de données ne sont pas remplacés, mais toutes les modifications apportées au jeu de données sont répercutées dans le rapport.
* Les membres d’un espace de travail ne peuvent pas remplacer le rapport partagé d’origine. Sinon, un avertissement vous invite à renommer le fichier et à le publier.
* Si vous supprimez le jeu de données partagé dans le **service Power BI**, les autres rapports basés sur ce jeu de données cessent de fonctionner correctement ou d’afficher leurs visuels.
* Pour les packs de contenu, vous devez commencer par créer une copie d’un pack de contenu afin de l’utiliser comme base pour partager un rapport et un jeu de données .pbix pour le **service Power BI**.
* Pour les packs de contenu à partir de *Mon organisation*, une fois la copie effectuée, vous ne pouvez pas remplacer le rapport créé sur le service et/ou un rapport créé dans le cadre de la copie d’un pack de contenu avec une connexion active. Sinon, un avertissement vous invite à renommer le fichier et à le publier. Dans ce cas, vous pouvez uniquement remplacer des rapports publiés connectés en direct.
* Quand vous supprimez un jeu de données partagé dans le **service Power BI**, personne ne peut plus y accéder à partir de **Power BI Desktop**.
* Les rapports qui partagent un jeu de données sur le service Power BI ne prennent pas en charge les déploiements automatisés avec l’API REST de Power BI.

