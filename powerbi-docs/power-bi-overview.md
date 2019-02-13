---
title: Qu’est-ce que Power BI ?
description: 'Vue d’ensemble de Power BI et de la façon dont les différents composants s’ajustent : Power BI Desktop, Service Power BI, Power BI mobile, Report Server, Power BI Embedded.'
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: b1efe45d52b5a7a18a86407b41e8af287d3c8260
ms.sourcegitcommit: b717118c44499c8fd8f57534a275f2f78aacc0f1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2019
ms.locfileid: "55971645"
---
# <a name="what-is-power-bi"></a>Qu’est-ce que Power BI ?
**Power BI** est un ensemble de services logiciels, d’applications et de connecteurs qui œuvrent ensemble pour transformer des sources de données disparates en informations visuelles immersives et interactives. Vos données peuvent être sous forme de feuille de calcul Excel ou de collection d’entrepôts de données hybrides locaux ou sur le cloud. **Power BI** vous permet de vous connecter facilement à vos sources de données, de visualiser et de découvrir ce qui est important, et de partager ces informations avec qui vous voulez.

![diagramme montrant les sources d’entrée pour Power BI](media/power-bi-overview/power-bi-input-new.png)

**Power BI** est simple et rapide. Il peut révéler des informations à partir d’une feuille de calcul Excel ou d’une base de données locale en un tour de main. **Power BI** se veut aussi une solution d’entreprise robuste, parée pour une modélisation complète, une analyse en temps réel, ainsi qu’un développement personnalisé. Ce service peut donc être votre rapport personnel et votre outil de visualisation. Il peut également faire office de moteur d’analyse et de décision pour des projets de groupe, des divisions ou des sociétés.

## <a name="the-parts-of-power-bi"></a>Composants de Power BI
Power BI se compose d’une application de bureau Windows appelée **Power BI Desktop**, d’un service SaaS (*Software as a Service*) en ligne appelé **service Power BI**, ainsi que d’**applications mobiles** Power BI disponibles sur téléphones et tablettes Windows, iOS et Android.

![Power BI Desktop, service, mobile](media/power-bi-overview/power-bi-blocks.png)

Ces trois éléments (**Power BI Desktop**, le **service** et les **applications mobiles**) ont été conçus pour permettre à leurs utilisateurs de créer, partager et consommer de façon optimale les données d’entreprise en fonction de leurs besoins ou de leur fonction.

Un quatrième élément, **Power BI Report Server**, vous permet de publier des rapports Power BI sur un serveur de rapports local, après les avoir créés dans Power BI Desktop. En savoir plus sur [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>À chacun son Power BI
La façon dont vous utilisez Power BI peut varier selon la fonction que vous occupez dans un projet ou une équipe. D’autres personnes, qui occupent d’autres fonctions, peuvent tout aussi bien utiliser Power BI d’une autre manière.

Par exemple, vous pouvez utiliser principalement le **service Power BI**. En revanche, votre collègue spécialiste des chiffres et de la création de rapports d’entreprise préférera utiliser **Power BI Desktop** pour créer des rapports, avant de les publier dans le service Power BI, où vous pouvez ensuite les consulter. De son côté, votre collègue du service commercial pourra, quant à lui, utiliser principalement son application mobile Power BI pour suivre l’évolution de ses ventes et examiner les détails concernant les nouveaux prospects.

Si vous êtes un développeur, vous pouvez utiliser les API de Power BI pour transmettre des données à des jeux de données ou pour incorporer des tableaux de bord et des rapports dans vos propres applications personnalisées. Vous souhaitez créer un élément visuel ? Faites-le vous-même et partagez-le avec d’autres utilisateurs.  

Vous pouvez aussi être amené à utiliser chaque élément de **Power BI** à des moments différents, selon ce que vous voulez faire ou selon votre rôle dans un projet donné.

Vous utilisez peut-être **Power BI Desktop** afin de créer des rapports pour votre équipe concernant les statistiques d’engagement des clients. Vous consultez aussi peut-être l’inventaire et la progression de fabrication dans un tableau de bord en temps réel du service. Votre utilisation de Power BI dépend de la fonctionnalité ou du service de Power BI qui correspond à l’outil le plus adapté à votre situation. Chaque partie de Power BI est disponible, ce qui explique sa flexibilité et son attrait.

Pour explorer les documents relatifs à votre rôle :
- Power BI pour les [***développeurs***](desktop-what-is-desktop.md)
- Power BI pour les [***consommateurs***](consumer/end-user-consumer.md)
- Power BI pour les [***développeurs***](developer/what-can-you-do.md)
- Power BI pour les [***administrateurs***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>Flux de travail dans Power BI
Un flux de travail standard dans Power BI commence par la connexion à des sources de données et la création d’un rapport **Power BI Desktop**. Vous publiez ensuite ce rapport depuis **Power BI Desktop** dans le **service Power BI**, et le partager afin que les utilisateurs finaux du **service** et des **appareils mobiles** puissent le consulter et interagir avec.
Ce workflow est courant et montre la complémentarité entre les trois éléments principaux de Power BI.

Voici une [comparaison détaillée de Power BI Desktop et du service Power BI](service-service-vs-desktop.md).

Mais que se passe-t-il si vous n’êtes pas prêt à migrer vers le cloud et souhaitez conserver vos rapports derrière un pare-feu d’entreprise ?  Lisez la suite.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Rapports locaux avec Power BI Report Server
Créez, déployez et gérez localement des rapports Power BI mobiles et paginés avec la gamme d’outils et services prêts à l’emploi de Power BI Report Server.

![diagramme d’un déploiement local](media/power-bi-overview/power-bi-report-server2.png)

Power BI Report Server est une solution que vous déployez derrière votre pare-feu. Vous distribuez ensuite vos rapports aux utilisateurs appropriés de différentes façons afin de les afficher dans un navigateur web, sur un appareil mobile, ou sous forme d’e-mail. Et comme Power BI Report Server est compatible avec Power BI dans le cloud, vous pouvez migrer vers le cloud quand vous êtes prêt. 

En savoir plus sur [Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Étapes suivantes
[Se connecter, obtenir des données et se familiariser avec le service Power BI](service-the-new-power-bi-experience.md)   
[Tutoriel : Bien démarrer avec le service Power BI](service-get-started.md)
[Guide de démarrage rapide : Se connecter aux données dans Power BI Desktop](desktop-quickstart-connect-to-data.md)