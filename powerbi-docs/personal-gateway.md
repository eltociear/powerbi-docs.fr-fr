---
title: Passerelle Power BI - Personal
description: Power BI Gateway - Personal
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: fc062387282bf01fd06a9e3d2420ac748c0bc592
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
> [!NOTE]
> Une nouvelle version de la passerelle de données locale, appelée **Passerelle de données locale (mode personnel)** est disponible pour Power BI. L’article suivant décrit la précédente version de la passerelle personnelle, appelée **Power BI Gateway - Personal**, qui sera supprimée et cessera de fonctionner après le 31 juillet 2017. Pour plus d’informations sur la nouvelle version de la passerelle personnelle, notamment sur son installation, consultez l’article [**Passerelle de données locale (mode personnel)**](service-gateway-personal-mode.md).
> 
> 

**Power BI Gateway - Personal** fait office de pont pour assurer un transfert de données rapide et sécurisé entre le service Power BI et des sources de données locales prenant en charge l’[actualisation](refresh-data.md). Cet article a pour objectif de vous faire découvrir dans le détail le fonctionnement de la passerelle et si vous avez ou non besoin d’une passerelle. Nous avons également réalisé cette [vidéo utile](https://www.youtube.com/watch?v=de58vROLqZI) sur la passerelle personnelle. 

Elle s’installe et s’exécute comme un service sur votre ordinateur. En tant que service, elle s’exécute à l’aide d’un compte Windows que vous spécifiez lors de la configuration. Dans certains cas, la passerelle s’exécute comme une application. Nous aborderons cela plus en détail ultérieurement.

Lorsque Power BI actualise les données d’une source de données locale, la passerelle s’assure que votre compte Power BI dispose des droits suffisants pour se connecter aux données de la source et les interroger.

Le transfert de données entre Power BI et la passerelle est sécurisé via [Azure Service Bus](http://azure.microsoft.com/documentation/services/service-bus/). Le bus des services crée un canal sécurisé entre le service Power BI et votre ordinateur. Étant donné que la passerelle fournit cette connexion sécurisée, il n’est généralement pas nécessaire d’ouvrir un port dans votre pare-feu.

Avant d’entrer dans les détails au sujet de la passerelle, examinons certains termes utilisés dans Power BI :

Un *jeu de données* est constitué de données chargées dans le service Power BI à partir d’une source de données en ligne ou locales. Vous créez un jeu de données lorsque vous utilisez Obtenir des données pour vous connecter à des données et les télécharger. Les jeux de données s’affichent dans le volet Mon espace de travail de votre espace de travail Power BI dans votre navigateur. Lorsque vous créez des rapports et que vous épinglez des vignettes à vos tableaux de bord, vous consultez les données de vos jeux de données.

Une *source de données* est l’emplacement d’où proviennent vraiment les données que vous chargez dans un jeu de données. Il peut s’agir d’à peu près n’importe quoi : une base de données, une feuille de calcul Excel, un service web, etc. Avec les classeurs Excel, vous pouvez créer une feuille de calcul simple avec des lignes de données, et cela est considéré comme une source de données. Vous pouvez également utiliser Power Query ou Power Pivot dans Excel pour vous connecter à des données de sources de données aussi bien en ligne que locales, et interroger ces données, le tout le même classeur. Avec Power BI Desktop, vous utilisez Obtenir des données pour vous connecter à des données de sources de données aussi bien en ligne et locales, et interroger ces données.

La passerelle personnelle est installée via la passerelle de données locale. Vous pouvez la télécharger sur la [page Power BI Gateway](https://powerbi.microsoft.com/gateway/).

## <a name="do-i-need-a-gateway"></a>Ai-je besoin d’une passerelle ?
Avant d’installer une passerelle, il est important de savoir si vous en avez vraiment besoin. Cela dépend en fait de vos sources de données :

### <a name="on-premises-data-sources"></a>Sources de données locales
Une passerelle personnelle *est requise* pour actualiser des jeux de données qui reçoivent des données d’une source de données locale prise en charge de votre organisation.

Avec une passerelle, les fonctionnalités ACTUALISER MAINTENANT et PLANIFIER L’ACTUALISATION sont prises en charge pour les jeux de données chargés à partir des sources suivantes :

* Classeurs Microsoft Excel 2013 (ou version ultérieure) pour lesquels Power Query ou Power Pivot sont utilisés pour se connecter aux données d’une source de données locale prise en charge, ainsi que pour interroger ces données. Toutes les sources de données locales affichées dans Obtenir des données externes dans Power Query ou Power Pivot prennent en charge l’actualisation, excepté pour HDFS (Hadoop Distributed File System) et Microsoft Exchange.
* Fichiers Microsoft Power BI Desktop pour lesquels la fonctionnalité Obtenir des données est utilisée pour se connecter aux données d’une source de données locale prise en charge, ainsi que pour interroger ces données. Toutes les sources de données locales affichées dans Obtenir des données prennent en charge l’actualisation, excepté pour HDFS (Hadoop Distributed File System) et Microsoft Exchange.

### <a name="online-data-sources"></a>Sources de données en ligne
Une passerelle *est requise uniquement* si vous utilisez la fonction [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx). Dans les autres cas, une passerelle *n’est pas* requise pour actualiser des jeux de données qui reçoivent des données uniquement d’une source de données en ligne.

> [!NOTE]
> Si vous utilisez la fonction [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), vous avez uniquement besoin d’une passerelle si vous avez republié le jeu de données ou votre rapport après le 18 novembre 2016.
> 
> 

Les fonctionnalités ACTUALISER MAINTENANT et PLANIFIER L’ACTUALISATION sont prises en charge sans passerelle pour les jeux de données chargés à partir des sources suivantes :

* Packs de contenu de sources de données en ligne (content packs\\services). Par défaut, des jeux de données provenant de packs de contenu sont automatiquement mis à jour une fois par jour, mais vous pouvez également effectuer une actualisation manuelle ou configurer une planification d’actualisation.
* Classeurs Microsoft Excel 2013 (ou version ultérieure) pour lesquels Power Query ou Power Pivot sont utilisés pour se connecter aux données d’une source de données en ligne, ainsi que pour interroger ces données.
* Fichiers Microsoft Power BI Desktop pour lesquels la fonctionnalité Obtenir des données est utilisée pour se connecter aux données d’une source de données en ligne, ainsi que pour interroger ces données.

**Question :** Qu’en est-il si mon classeur Excel ou mon fichier Power BI Desktop obtient les données aussi bien de sources de données en ligne et locales ?

**Réponse :** Une passerelle *est* requise. Vous devez installer et configurer une passerelle pour actualiser les données à partir de vos sources de données locales.

**Question :** Qu’en est-il si mon classeur Excel ne comporte que des lignes de données que j’ai tapées ?**

**Réponse** : Une passerelle *n’est pas* requise. Vous devez installer et configurer une passerelle uniquement si votre classeur utilise Power Query ou Power Pivot pour interroger et charger des données dans le modèle de données à partir d’une source de données locale prise en charge.

## <a name="setting-up-a-gateway-for-the-first-time"></a>Configuration d’une passerelle pour la première fois
La première configuration d’une passerelle est un processus en trois étapes :

1. Télécharger et installer une passerelle
2. Configurer la passerelle
3. Se connecter à des sources de données dans Power BI

Examinons de plus près chaque étape.

### <a name="download-and-install-a-gateway"></a>Télécharger et installer une passerelle
> [!NOTE]
> Une nouvelle version de la passerelle de données locale, appelée **Passerelle de données locale (mode personnel)** est disponible pour Power BI. Cet article décrit la précédente version de la passerelle personnelle, appelée **Passerelle Power BI - Personal**, qui sera supprimée et cessera de fonctionner après le 31 juillet 2017. Pour plus d’informations sur la nouvelle version de la passerelle personnelle, notamment sur son installation, consultez l’article [**Passerelle de données locale (mode personnel)**](service-gateway-personal-mode.md).
> 
> 

Vous êtes invité à installer une passerelle lorsque vous cliquez pour la première fois sur ACTUALISER MAINTENANT ou sur PLANIFIER L’ACTUALISATION pour un jeu de données pris en charge. Ou, pour télécharger la passerelle, sélectionnez **Passerelle de données** dans le menu Téléchargements. Téléchargez la [passerelle de données locale](http://go.microsoft.com/fwlink/?LinkID=820925).

Vous devrez sélectionner **Passerelle personnelle** au lieu de **Passerelle de données locale** pour obtenir une passerelle pour vous-même.

L’installation d’une passerelle comprend très peu d’opérations. Vous devez sélectionner un emplacement pour l’installation, puis lire et accepter le contrat de licence comme pour toute autre application. Vous devez toutefois prendre connaissance de certaines informations importantes, en particulier, le type d’ordinateur sur lequel vous installez la passerelle et le type de compte avec lequel vous êtes connecté à Windows sur cet ordinateur.

> [!NOTE]
> La passerelle doit avoir accès à la source de données. Si votre ordinateur personnel ne peut pas se connecter à la source de données, vous pouvez installer une [passerelle de données locale](service-gateway-onprem.md) sur un ordinateur qui a accès à la source de données. Par exemple un serveur SQL Server installé sur une machine virtuelle hébergée dans Azure. Il se peut que votre ordinateur personnel n’ait pas accès à la machine virtuelle. Vous pouvez à la place installer la passerelle de données locale sur la machine virtuelle et configurer la source de données dans le service Power BI.
> 
> 

### <a name="computer-type"></a>Type d’ordinateur
Le type d’ordinateur sur lequel vous installez la passerelle est important.

> [!NOTE]
> La passerelle personnelle est prise en charge uniquement sur les systèmes d’exploitation Windows 64 bits.
> 
> 

Sur un ordinateur portable : pour qu’une actualisation planifiée se produise, la passerelle doit être opérationnelle. Les ordinateurs portables sont généralement plus souvent arrêtés ou en veille qu’en cours d’exécution. Si vous installez votre passerelle sur un ordinateur portable, veillez à définir vos heures d’actualisation planifiée de façon à ce qu’elles correspondent à des moments où l’ordinateur portable sera en cours d’exécution. Sinon, l’actualisation ne sera pas retentée avant la prochaine heure d’actualisation planifiée.

Sur un ordinateur de bureau : peu de problèmes dans ce cas. Assurez-vous simplement que l’ordinateur et la passerelle soient en cours d’exécution aux heures d’actualisation planifiée que vous définissez. De nombreux ordinateurs de bureau se mettre en veille, et l’actualisation planifiée ne peut pas se produire lorsqu’ils sont dans cet état.

Une fois une passerelle installée, vous n’aurez plus à en installer une autre. Une passerelle fonctionne pour un nombre indéfini de jeux de données pris en charge. Vous n’avez pas non plus besoin d’installer la passerelle sur l’ordinateur à partir duquel vous chargez votre classeur et vos fichiers Power BI Desktop. Supposons, par exemple, que vous ayez un classeur Excel qui se connecte à une source de données SQL Server de votre organisation. Vous avez utilisé Obtenir des données dans Power BI pour charger le classeur à partir de votre ordinateur portable. Vous avez également un ordinateur de bureau que vous laissez fonctionner tout le temps, et sur lequel vous avez installé et configuré une passerelle. Dans Power BI, vous vous êtes connecté à vos sources de données et vous avez configuré une planification d’actualisation pour le jeu de données.  À l’heure d’actualisation planifiée, Power BI établit une connexion sécurisée à la passerelle installée sur votre ordinateur de bureau. Il se connecte ensuite en toute sécurité aux sources de données pour obtenir les mises à jour. Pour l’actualisation, il n’y a aucune communication avec le classeur d’origine que vous avez chargé à partir de votre ordinateur portable.

> [!NOTE]
> Vous pouvez installer les passerelles personnelles et d’entreprise sur le même ordinateur.
> 
> 

### <a name="windows-account"></a>Compte Windows
Lorsque vous installez la passerelle, vous êtes connecté à votre ordinateur à l’aide de votre compte Windows. Le type d’autorisations dont dispose votre compte Windows a une incidence sur la façon dont la passerelle est installée et dont elle s’exécute dans Windows.

Lorsque vous êtes connecté à Windows :

|  | Avec des autorisations d’administrateur | Sans autorisations d’administrateur |
| --- | --- | --- |
| **Power BI Gateway - Personal s’exécute en tant que** |Service |Application |
| **Actualisation planifiée** |Tant que votre ordinateur et le service de passerelle sont en cours d’exécution, vous n’avez pas à vous connecter au moment de l’actualisation planifiée. |Vous devez être connecté à votre ordinateur au moment de l’actualisation planifiée. |
| **Modifier le mot de passe associé au compte Windows** |Vous devez modifier votre mot de passe dans le service de passerelle. Si le mot de passe du compte utilisé par la passerelle n’est plus valide, l’actualisation échoue. |La passerelle s’exécute toujours avec le compte et le mot de passe utilisés pour la connexion en cours. Si vous n’êtes pas connecté à Windows, la passerelle ne fonctionne pas et l’actualisation échoue. |

### <a name="configure-the-gateway"></a>Configurer la passerelle
Une fois l’Assistant Installation terminé, vous êtes invité à lancer l’Assistant Configuration. La configuration d’une passerelle est vraiment peu de chose. Vous devez vous connecter à Power BI à partir de l’Assistant. Cela est nécessaire pour que l’Assistant établisse une connexion avec votre compte Power BI dans le service Power BI.

Si vous êtes connecté à Windows avec un compte bénéficiant d’autorisations d’administrateur, vous serez invité à entrer les informations d’identification de votre compte Windows. Vous pouvez spécifier un autre compte Windows, mais n’oubliez pas que les autorisations déterminent la façon dont la passerelle s’exécute. Le service de passerelle s’exécute à l’aide de ce compte.

### <a name="sign-in-to-data-sources"></a>Se connecter à des sources de données
Une fois l’exécution de l’Assistant Configuration terminée et votre passerelle opérationnelle, vous devez spécifier un type d’authentification et vous connecter à chacune des sources de données de votre jeu de données. Vous devez effectuer cette étape dans Power BI.

![](media/personal-gateway/pg_dataset_settings_signin.png)

Vous devez uniquement spécifier un type d’authentification et vous connecter une fois à une source de données. Vous vous connectez à partir de la section **Gérer les sources de données** de l’écran Paramètres d’un jeu de données. Si vous avez plusieurs sources de données, vous devrez vous connecter à chacune d’elles. La passerelle détermine un type d’authentification par défaut en fonction de la source de données. Dans la plupart des cas, c’est l’authentification Windows ; toutefois, dans certains cas, votre source de données peut nécessiter un autre type d’authentification. En cas de doute, vérifiez auprès de votre administrateur de source de données.

## <a name="up-and-running"></a>Opérationnelle !
Lorsque votre passerelle est opérationnelle, vous pouvez cliquer sur PLANIFIER L’ACTUALISATION pour un jeu de données afin d’afficher sa page Paramètres.

![](media/personal-gateway/pg_awintsales_settings.png)

Cette page s’affiche les éléments suivants :

1. État d’actualisation : montre la réussite de l’actualisation et l’heure de la prochaine actualisation planifiée.
2. **Passerelle** : indique si une passerelle est ou non installée et en ligne. Si une passerelle est installée mais pas en ligne, les paramètres Gérer les sources de données et Planifier l’actualisation sont désactivés.
3. **Gérer les sources de données** : affiche les sources de données auxquelles le jeu de données se connecte. Vous pouvez vous connecter ou modifier le type d’authentification. Il vous suffit de vous connecter une fois à chaque source de données.
4. **Planifier l’actualisation** : vous pouvez configurer des paramètres de planification d’actualisation ici. Si la passerelle n’est pas en ligne, ces paramètres sont désactivés.
5. Notifications d’échec d’actualisation : cette option, activée par défaut, vous envoie un message électronique en cas d’échec d’une actualisation planifiée.

## <a name="updating-your-windows-account-password"></a>Mise à jour du mot de passe de votre compte Windows
Si vous étiez connecté à votre ordinateur avec un compte Windows disposant de privilèges d’administrateur lors de l’installation de votre passerelle, celle-ci s’exécute en tant que service en utilisant le compte Windows spécifié dans l’Assistant Configuration. Le plus souvent, il s’agit du même compte Windows que celui avec lequel vous vous connectez à votre ordinateur. Lorsque vous modifiez le mot de passe de votre compte Windows, vous devez également le modifier dans la passerelle. Sinon, le service ne peut pas s’exécuter et l’actualisation échoue. Pour modifier le mot de passe de votre compte Windows pour la passerelle, sélectionnez l’icône de la passerelle personnelle dans la barre des tâches du Bureau Windows, ou dans Applications.

![](media/personal-gateway/pg_programicon.png)

À ce stade, vous pouvez mettre à jour votre mot de passe et vérifier l’état de connexion de votre passerelle.

![](media/personal-gateway/pg_credentials.png)

## <a name="ports"></a>Ports
La passerelle communique sur des ports de sortie : TCP 443 (valeur par défaut), 5671, 5672, 9350 à 9354.  La passerelle ne nécessite pas de ports d’entrée.

| Noms de domaine | Ports de sortie | Description |
| --- | --- | --- |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |AMQP (Advanced Message Queuing Protocol) |
| *.servicebus.windows.net |443, 9350-9354 |Écouteurs sur Service Bus Relay via TCP (nécessite 443 pour l’acquisition de jeton de contrôle d’accès) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| login.windows.net |443 |HTTPS |

Si vous avez besoin d’approuver des adresses IP plutôt que des domaines, vous pouvez télécharger et utiliser la liste des plages IP du centre de données Microsoft Azure. [Télécharger](https://www.microsoft.com/download/details.aspx?id=41653)

## <a name="next-steps"></a>Étapes suivantes
[Passerelle de données locale (mode personnel) - nouvelle version de la passerelle personnelle](service-gateway-personal-mode.md)
[Configuration des paramètres de proxy pour les passerelles Power BI](service-gateway-proxy.md)  
[Power BI Premium](service-premium.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

