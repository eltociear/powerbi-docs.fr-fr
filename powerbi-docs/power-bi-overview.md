---
title: Qu’est-ce que Power BI ?
description: 'Vue d’ensemble de Power BI et de la façon dont les différents composants s’intègrent : Power BI Desktop, le service Power BI, Power BI mobile, Report Server et Power BI Embedded.'
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 05/30/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: d6c9eb47d5f88a2d835c1ba6835e871b0c64bf1c
ms.sourcegitcommit: fe8a25a79f7c6fe794d1a30224741e5281e82357
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68324765"
---
# <a name="what-is-power-bi"></a>Qu’est-ce que Power BI ?
**Power BI** est un ensemble de services logiciels, d’applications et de connecteurs qui œuvrent ensemble pour transformer des sources de données disparates en informations visuelles immersives et interactives. Vos données peuvent être sous forme de feuille de calcul Excel ou de collection d’entrepôts de données hybrides locaux ou sur le cloud. Power BI vous permet de vous connecter facilement à vos sources de données, de visualiser et de découvrir ce qui est important, et de partager ces informations avec qui vous voulez.

![diagramme montrant les sources d’entrée pour Power BI](media/power-bi-overview/power-bi-input-new.png)

Power BI est simple et rapide, et peut créer rapidement des insights à partir d’une feuille de calcul Excel ou d’une base de données locale. Power BI se veut aussi une solution d’entreprise robuste, prête pour une modélisation complète et l’analyse en temps réel, et pour des développements personnalisés. Power BI peut servir aussi bien d’outil de rapport et de visualisation personnel que de moteur d’analyse et de décision pour des projets de groupe, des divisions ou des grandes entreprises.

## <a name="the-parts-of-power-bi"></a>Composants de Power BI
Power BI se compose des éléments suivants : 
- Une application de poste de travail Windows appelée **Power BI Desktop**
- Un service SaaS en ligne (*Software as a service*) appelé le **service Power BI** 
- Des **applications mobiles** Power BI pour des appareils Windows, iOS et Android

![Power BI Desktop, service, mobile](media/power-bi-overview/power-bi-blocks.png)

Ces trois éléments (Power BI Desktop, le service et les applications mobiles) ont été conçus pour permettre à leurs utilisateurs de créer, partager et consommer de façon optimale des insights métier, en fonction de leurs besoins ou de leur rôle.

Un quatrième élément, **Power BI Report Server**, vous permet de publier des rapports Power BI sur un serveur de rapports local, après les avoir créés dans Power BI Desktop. En savoir plus sur [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>À chacun son Power BI
La façon dont vous utilisez Power BI peut varier selon la fonction que vous occupez dans un projet ou une équipe. D’autres personnes ayant d’autres rôles peuvent aussi utiliser Power BI différemment.

Par exemple, vous pouvez utiliser principalement le **service Power BI**. En revanche, votre collègue spécialiste des chiffres et de la création de rapports d’entreprise préférera utiliser **Power BI Desktop** pour créer des rapports, avant de les publier dans le service Power BI, où vous pouvez ensuite les consulter. De son côté, votre collègue du service commercial peut quant à lui utiliser principalement son **application mobile Power BI** pour suivre l’évolution de ses ventes et examiner les détails concernant les nouveaux prospects.

Si vous êtes un développeur, vous pouvez utiliser les API de Power BI pour transmettre des données à des jeux de données ou pour incorporer des tableaux de bord et des rapports dans vos propres applications personnalisées. Vous souhaitez créer un élément visuel ? Faites-le vous-même et partagez-le avec d’autres utilisateurs.  

Vous pouvez aussi être amené à utiliser chaque élément de Power BI à des moments différents, selon ce que vous voulez faire ou selon votre rôle dans un projet donné.

Votre utilisation de Power BI dépend de la fonctionnalité ou du service de Power BI qui correspond à l’outil le plus adapté à votre situation. Par exemple, vous pouvez utiliser Power BI Desktop pour créer des rapports statistiques pour les besoins de votre équipe sur l’engagement des clients, et vous pouvez visualiser l’évolution des stocks et de la production dans un tableau de bord en temps réel dans le service Power BI. Chaque partie de Power BI est disponible, ce qui explique sa flexibilité et son attrait.

Pour explorer les documents relatifs à votre rôle :
- Power BI pour les [***développeurs***](desktop-what-is-desktop.md)
- Power BI pour les [***consommateurs***](consumer/end-user-consumer.md)
- Power BI pour les [***développeurs***](developer/what-can-you-do.md)
- Power BI pour les [***administrateurs***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>Flux de travail dans Power BI
Un flux de travail standard dans Power BI commence par la connexion à des sources de données et la création d’un rapport Power BI Desktop. Vous publiez ensuite ce rapport depuis Power BI Desktop sur le service Power BI, et vous le partagez afin que les utilisateurs finaux du service Power BI et ceux travaillant sur des appareils mobiles puissent le consulter et interagir avec ce rapport.
Ce workflow est courant et montre la complémentarité entre les trois éléments principaux de Power BI.

Voici une [comparaison détaillée de Power BI Desktop et du service Power BI](service-service-vs-desktop.md).

Mais que se passe-t-il si vous n’êtes pas prêt à migrer vers le cloud et souhaitez conserver vos rapports derrière un pare-feu d’entreprise ?  Lisez la suite.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Rapports locaux avec Power BI Report Server
Créez, déployez et gérez localement des rapports Power BI mobiles et paginés avec la gamme d’outils et de services prêts à l’emploi de Power BI Report Server.

![diagramme d’un déploiement local](media/power-bi-overview/power-bi-report-server2.png)

Power BI Report Server est une solution que vous déployez derrière votre pare-feu. Vous distribuez ensuite vos rapports aux utilisateurs appropriés de différentes façons afin de les afficher dans un navigateur web, sur un appareil mobile, ou sous forme d’e-mail. Et comme Power BI Report Server est compatible avec Power BI dans le cloud, vous pouvez migrer vers le cloud quand vous êtes prêt. 

En savoir plus sur [Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Étapes suivantes
- [Démarrage rapide : Découvrir le fonctionnement du service Power BI](service-the-new-power-bi-experience.md)   
- [Tutoriel : Bien démarrer avec le service Power BI](service-get-started.md)
- [Démarrage rapide : Se connecter aux données dans Power BI Desktop](desktop-quickstart-connect-to-data.md)
