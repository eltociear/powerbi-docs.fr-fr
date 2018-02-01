---
title: Prise en main de Power BI Gateways
description: "Découvrez les principes de base des passerelles de données pour Power BI."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 14c96dbc88784cd76099c25508409bcc24064e35
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="getting-started-with-power-bi-gateways"></a>Prise en main de Power BI Gateways
Bienvenue dans le guide **Prise en main de Power BI Gateways**. Cette courte procédure pas à pas vous permet de vous familiariser avec les fonctionnalités d’une passerelle, la manière dont elle fonctionne et la façon d’obtenir votre propre passerelle installée, configurée et opérationnelle.  

![](media/service-gateway-getting-started/gw_gettingstarted_0a.png)

Les passerelles peuvent être un sujet technique et, chaque réseau et entreprise étant distincts, la complexité des passerelles peut être importante. Pour éviter cette complexité, commençons par les notions de base.

## <a name="how-power-bi-gateways-work"></a>Fonctionnement de Power BI Gateways
Une **passerelle** est un logiciel qui facilite l’accès aux données résidant sur un réseau local privé en vue de leur utilisation ultérieure dans un service cloud tel que Power BI. Il s’agit d’une sorte d’opérateur de contrôle qui écoute les demandes de connexion des utilisateurs et n’y consent que lorsque celles-ci remplissent certains critères, tels le fait que ces utilisateurs soient autorisés à utiliser la passerelle. Cela permet aux entreprises de conserver des bases de données et entrepôts de données sur leurs réseaux locaux, tout en utilisant en toute sécurité des sous-ensembles de ces données pour créer des rapports et tableaux de bord éloquents dans Power BI.

Une passerelle sécurise également l’accès et les données en chiffrant et compressant toutes les données qui transitent par elle, ainsi que les mots de passe utilisés pour se connecter aux sources de données. Tout cela semble très simple. Pourtant, de nombreux détails doivent être pris en compte.

Parfois, vous souhaitez disposer d’une passerelle rien que pour vous. Peut-être avez-vous un classeur Excel volumineux et trois bases de données SQL avec des années de données de ventes de marketing, et souhaitez-vous créer un tableau de bord Power BI présentant ces ventes sous tous les angles. Vous êtes la seule personne à créer des rapports (il s’agit de votre classeur Excel) et à utiliser ces bases de données pour créer des rapports Power BI. Vous avez juste besoin d’une passerelle pour votre usage personnel, pas pour partager ces sources de données.

Ou il se peut que vous opériez au sein d’une organisation disposant de toutes sortes de bases de données de différents fournisseurs, notamment Analysis Services, SAP, Oracle, IBM et diverses autres sources de données, et que vous ayez besoin d’un grand nombre de personnes pour y accéder en créant une multitude de rapports. Dans ce cas, vous avez besoin d’une passerelle qui vous permette de configurer l’accès à toutes ces sources, puis vous devez la partager avec de nombreuses personnes au sein de votre organisation. Il s’agit d’un type de passerelle complètement différent.

Heureusement, Power BI offre deux passerelles prenant en charge chacun de ces scénarios. Ces deux offres de passerelle Power BI sont les suivantes :

* **Passerelle de données locale (mode personnel)** : elle permet à un utilisateur de se connecter aux sources et ne peut pas être partagée avec d’autres utilisateurs. Elle peut être utilisée uniquement avec Power BI.
* **Passerelle de données locale** : celle-ci permet à plusieurs utilisateurs de se connecter à plusieurs sources de données locales et peut être utilisée par Power BI, PowerApps, Flow et Azure Logic Apps, tout cela avec une installation de passerelle unique.

Les deux passerelles remplissent une fonction similaire : elles facilitent l’accès aux données résidant sur un réseau local privé de façon à ce que les données soient utilisables dans des services cloud tels que Power BI. La passerelle personnelle peut être utilisée par une personne et uniquement par Power BI, tandis que la **passerelle de données locale** peut être utilisée par de nombreux utilisateurs et de nombreux services.

Trois phases ou étapes sont nécessaires pour mettre une passerelle en service :

* Installer la passerelle
* Ajouter des utilisateurs à la passerelle (leur permettre de l’utiliser)
* Se connecter à la source de données

De plus, une passerelle vous permet de faire une autre chose qui peut être importante :

* Rafraîchir des données locales de façon à ce que les rapports Power BI puissent être mis à jour avec des données actualisées

L’actualisation des données signifie que vos tableaux de bord et rapports Power BI semblent à jour et reflètent les données les plus récentes. Ainsi, quand un utilisateur consulte un rapport que vous avez créé avec des données locales, ce rapport peut utiliser les informations les plus récentes, même si vous l’avez depuis un certain temps.

La première phase, l’installation d’une passerelle, est facile. Autoriser les utilisateurs à accéder à la passerelle est également simple puisqu’il suffit de les ajouter dans une boîte de dialogue de Power BI. La connexion à des sources de données peut être complexe, car il existe de nombreuses sources de données, chacune avec ses propres exigences et nuances de connexion. Nous traitons de l’actualisation dans un autre guide afin de nous concentrer dans cet article sur la passerelle.

Commençons donc pas le facile et voyons comment installer une passerelle.

## <a name="install-the-gateway"></a>Installer la passerelle
Pour installer une passerelle, ouvrez le service Power BI (vous pouvez utiliser ce lien pour lancer le service Power BI dans votre navigateur et ouvrir une session), puis connectez-vous avec votre compte Power BI. Dans le service Power BI, sélectionnez l’**icône Téléchargement** dans l’angle supérieur droit, comme illustré dans l’image suivante, puis sélectionnez **Passerelle de données**.

![](media/service-gateway-getting-started/gw_gettingstarted_01.png)

Cela vous amène à une page de téléchargement dans laquelle vous cliquez sur le bouton **Télécharger l’installation de la passerelle** pour lancer le téléchargement.

![](media/service-gateway-getting-started/gw_gettingstarted_02.png)

Cet écran affiche l’explication extrêmement succincte de ce que fait une passerelle. Il fournit également quelques **avertissements** importants : lorsque vous installez une passerelle, celle-ci s’exécute sur l’ordinateur sur lequel vous effectuez l’installation. Et si cet ordinateur est hors tension, la passerelle l’est également (elle ne fonctionne donc pas lorsqu’elle n’est pas en cours d’exécution). Par ailleurs, l’installation sur un ordinateur à l’aide d’un réseau sans fil n’étant pas idéale, nous vous recommandons d’utiliser un ordinateur connecté à un réseau câblé.

Lorsque vous êtes prêt, sélectionnez **Suivant** pour continuer l’installation.

![](media/service-gateway-getting-started/gw_gettingstarted_03.png)

C’est à ce stade que vous déterminez la passerelle à installer : locale ou personnelle. Dans les étapes de ce guide, nous allons installer la **passerelle de données locale**.

Il convient de noter quelques éléments à ce point de décision :

* Les deux passerelles requièrent des systèmes d’exploitation Windows 64 bits.
* Vous ne pouvez pas installer les passerelles sur un contrôleur de domaine.
* Vous pouvez installer jusqu’à deux passerelles de données locales sur le même ordinateur, une dans chaque mode (personnel et standard). 
* Vous ne pouvez pas avoir plusieurs passerelles exécutées dans le même mode sur le même ordinateur.
* Vous pouvez installer plusieurs passerelles de données locales sur différents ordinateurs, et les gérer toutes à partir de la même interface de gestion de passerelle Power BI (à l’exception du mode personnel - voir la puce suivante).
* Vous ne pouvez avoir qu’une seule passerelle en mode personnel en cours d’exécution pour chaque utilisateur Power BI. Si vous installez une autre passerelle en mode personnel pour le même utilisateur, même sur un autre ordinateur, l’installation la plus récente remplace la précédente installation.

Lorsque vous sélectionnez **Suivant** l’installation de la passerelle commence. Vous devez spécifier où l’installer et l’emplacement par défaut est généralement préférable.

![](media/service-gateway-getting-started/gw_gettingstarted_06.png)

Le processus d’installation est rapide et vous bénéficiez d’une barre d’état.

![](media/service-gateway-getting-started/gw_gettingstarted_06a.png)

Lorsque vous avez presque terminé, vous devez identifier le compte à utiliser avec la passerelle. Il doit s’agir du compte (nom d’utilisateur et mot de passe) que vous utilisez pour ouvrir une session sur Power BI. En effet, la passerelle est associée à votre compte Power BI et vous configuriez les passerelles à partir du service Power BI.

![](media/service-gateway-getting-started/gw_gettingstarted_07.png)

Vous êtes connecté, comme illustré dans l’image suivante.

![](media/service-gateway-getting-started/gw_gettingstarted_08.png)

Une fois connecté, vous devez créer une **clé de récupération**. Nous abordons ce sujet plus en détail dans un autre article mais, pour l’instant, sachez que celle-ci est nécessaire pour récupérer ou déplacer votre passerelle.

![](media/service-gateway-getting-started/gw_gettingstarted_09.png)

Lorsque tout va bien, une fenêtre s’affiche, indiquant que votre passerelle est prête.

![](media/service-gateway-getting-started/gw_gettingstarted_10.png)

C’est tout ce que vous avez à faire pour installer une passerelle locale. Comme annoncé, le processus est assez simple. L’étape suivante consiste à **ajouter des utilisateurs** ou à **ajouter des sources de données**. Vous pouvez commencer par faire l’une des opérations, puis l’autre après la configuration initiale.

La section suivante décrit l’ajout d’utilisateurs à la passerelle. Nous expliquons ensuite comment y ajouter des sources de données.

## <a name="add-users-to-a-gateway"></a>Ajouter des utilisateurs à une passerelle
À présent que nous avons une passerelle installée, nous gérons celle-ci à partir du **service Power BI**. Pour accéder à l’écran de gestion pour les passerelles, dans le service Power BI, sélectionnez l’icône Engrenage dans l’angle supérieur droit, puis sélectionnez **Gérer les passerelles**.

![](media/service-gateway-getting-started/gw_gettingstarted_15.png)

Une page à l’intérieur de la zone de dessin du service Power BI s’affiche, dans laquelle vous pouvez gérer vos passerelles. La page **Paramètres de la passerelle** ressemble à ceci.

![](media/service-gateway-getting-started/gw_gettingstarted_12.png)

Si vous appuyez ou cliquez sur **Administrateurs**, vous voyez la page de gestion des administrateurs suivante. Notez qu’il s’agit simplement des utilisateurs autorisés à *administrer* la passerelle, et que des utilisateurs de la passerelle sont ajoutés (ou supprimés) de chaque source de données via une autre page, comme décrit dans les quelques paragraphes suivants.

![](media/service-gateway-getting-started/gw_gettingstarted_13.png)

Après que vous avez installé et validé une source de données (en vous y connectant), celle-ci s’affiche sous sa passerelle associée du côté gauche de cet écran **Gérer les passerelles**, comme illustré dans l’image suivante. Notez que le volet droit comprend deux sections entre lesquelles vous pouvez basculer : **Paramètres de la source de données** et **Utilisateurs**. L’écran ci-dessous est la section **Paramètres de la source de données**.

![](media/service-gateway-getting-started/gw_gettingstarted_16.png)

Lorsque vous sélectionnez **Utilisateurs**, une zone de texte s’affiche dans laquelle vous pouvez entrer des utilisateurs de votre organisation auxquels vous souhaitez accorder l’accès à la source de données sélectionnée. Dans l’écran suivant, vous pouvez voir que j’ai ajouté Maggie et Adam.

Lorsque vous commencez à taper une adresse e-mail dans la zone de texte, Power BI affiche une liste d’utilisateurs dont l’adresse e-mail correspond à ce que vous tapez, ce qui vous permet de cliquer sur le nom pour l’ajouter à la liste.

Vous pouvez également ajouter des groupes d’e-mails (alias) afin d’autoriser des groupes de personnes ainsi que des personnes à accéder.

![](media/service-gateway-getting-started/gw_gettingstarted_17.png)

Lorsque vous sélectionnez **Ajouter**, les membres ajoutés s’affichent dans la zone. Vous pouvez en ajouter davantage si vous le souhaitez. La suppression d’utilisateurs est tout aussi simple. Activez simplement les cases à cocher en regard de leurs noms, puis sélectionnez le bouton **Supprimer** sous la zone.

![](media/service-gateway-getting-started/gw_gettingstarted_18.png)

C’est tout. N’oubliez pas que vous devez ajouter des utilisateurs à chaque source de données à laquelle vous souhaitez accorder l’accès. Chaque source de données dispose d’une liste distincte d’utilisateurs, et vous devez ajouter des utilisateurs séparément à chaque source de données.

## <a name="adding-data-sources"></a>Ajout de sources de données
Bien sûr, pour que votre passerelle soit utile, vous devez ajouter des sources de données. C’est là qu’apparaît la complexité de Power BI Gateways : de nombreuses sources de données différences sont disponibles, chacune avec ses propres exigences (et souvent, son propre pilote requis).

Mais avant de passer à un autre article, voici un aperçu de la manière d’ajouter une source de données. Lorsque vous travaillez dans la page **Gérer les passerelles** du **service Power BI**, sélectionnez la passerelle à laquelle vous voulez ajouter une source de données, puis choisissez **Ajouter une source de données** dans l’angle supérieur gauche de la page, juste au-dessus de la liste de vos passerelles.

Lorsque vous procédez de la sorte, la panneau **Paramètres de la source de données** s’affiche dans le volet droit, comme illustré dans l’image suivante. Vous pouvez y nommer votre source de données (dans la zone de texte **Nom de la source de données**) et sélectionner son type dans la liste déroulante **Type de source de données**.

![](media/service-gateway-getting-started/gw_gettingstarted_14.png)

Bien. Vous disposez à présent d’une passerelle installée, et vous êtes prêt à ajouter des sources de données. Excellent ! Pour plus d’informations sur les sources de données, plus de détails sur l’utilisation des passerelles et d’autres informations utiles, voir les ressources mentionnées dans la section suivante.

## <a name="next-steps"></a>Étapes suivantes
[Utilisation de la passerelle de données locale](service-gateway-onprem.md)  
[Informations approfondies sur la passerelle de données locale](service-gateway-onprem-indepth.md)  
[Passerelle de données locale (mode Personnel)](service-gateway-personal-mode.md)
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

