---
title: "Contenu Power BI Pro - De quoi s’agit-il ?"
description: "Power BI Premium permet à votre organisation ou à votre équipe de bénéficier de performances plus fiables et de plus gros volumes de données sans qu’il soit nécessaire d’acquérir une licence pour chaque utilisateur."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/10/2017
ms.author: asaxton
ms.openlocfilehash: 816f1151b6f49ace8151f1c26aee18a8c746ff08
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi-premium---what-is-it"></a>Qu’est-ce que Power BI Premium ?
Power BI Premium fournit à votre organisation ou à votre équipe des ressources dédiées à l’exécution du service Power BI afin qu’elle bénéficie de performances plus fiables et de plus gros volumes de données. Premium permet également une diffusion étendue du contenu sans que vous soyez contraint d’acquérir une licence par utilisateur.

Pour tirer parti de Power BI Premium, vous pouvez attribuer des espaces de travail à une capacité Premium. Une *capacité Premium* est une ressource dédiée à votre organisation. Les espaces de travail non affectés à une capacité Premium sont attribués à une capacité partagée.

Le mode *Capacité partagée* est celui auquel vous êtes habitué avec Power BI. Vos charges de travail s’y exécutent sur des ressources de calcul partagées par d’autres clients. Une capacité partagée impose des limites aux utilisateurs individuels afin de garantir une expérience de qualité à tous les utilisateurs.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Niveaux de capacité
Il existe deux types de capacité dans Power BI : la capacité partagée et la capacité Power BI Premium. Les différences entre ces deux capacités sont décrites ci-dessous.

|  | Capacité partagée | Capacité Power BI Premium |
| --- | --- | --- |
| **Fréquence d’actualisation** |8/jour |Non restreinte |
| **Isolement avec matériel dédié** |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible") |
| **Distribution d’entreprise à** ***tous les utilisateurs*** | | |
| Applications |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible")<sup>1</sup> |
| API et commandes incorporées |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible")<sup>2</sup> |
| **Publier des rapports Power BI localement** |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible") |

*<sup>1</sup> Dans les applications, les utilisateurs « gratuits » peuvent afficher le contenu sur le web et sur leurs appareils mobiles, et utiliser les fonctionnalités Questions et réponses, Informations rapides, Cortana et Exportation au format CSV, Excel ou PowerPoint.*  
*<sup>2</sup> Améliorations prévues dans la version post disponibilité générale de Power BI Premium.*

### <a name="premium-capacity"></a>Capacité Premium
Pour commencer à utiliser une capacité Power BI Premium, vous devez lui attribuer un espace de travail. Pour plus d’informations sur l’attribution d’un espace de travail à une capacité Premium, consultez [Gérer Power BI Premium](service-admin-premium-manage.md).

Lorsqu’un espace de travail est soutenu par une capacité Premium, vous bénéficiez des avantages de Power BI Premium.

* Actualisations planifiées : auparavant, avec les modèles importés, les utilisateurs ne pouvaient pas planifier plus de 8 actualisations par jour. Cette limitation a été supprimée pour les jeux de données des espaces de travail Premium. Cela ne s’applique pas aux paramètres d’actualisation planifiée du cache pour DirectQuery. Ces paramètres restent identiques pour la capacité Premium et la capacité partagée.
* Isolement avec matériel dédié : dans une capacité partagée, les performances de vos rapports et tableaux de bord peuvent être affectées par les demandes de ressources des autres charges de travail de la capacité, en dépit des garde-fous que nous avons mis en place. À l’inverse, Premium offre des performances plus cohérentes et plus fiables en isolant les charges de travail non liées.

Si une application est soutenue par une capacité Premium (autrement dit, si elle a été publiée à partir d’un espace de travail d’applications actuellement attribué à Premium), elle peut être utilisée par n’importe quel utilisateur de votre organisation, quelle que soit sa licence. Cela signifie que les utilisateurs gratuits de Power BI peuvent eux aussi utiliser ces applications publiées.

### <a name="shared-capacity"></a>Capacité partagée
Par défaut, votre espace de travail est en mode Capacité partagée. Cela inclut votre espace de travail personnel (*Mon espace de travail*) ainsi que les espaces de travail d’applications. Le mode Capacité partagée est celui auquel vous êtes habitué avec Power BI. Vos charges de travail s’y exécutent sur des ressources de calcul partagées par d’autres clients.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nœuds de capacité Premium
Power BI Premium est disponible dans des configurations de nœuds aux capacités différentes en termes de cœurs virtuels. Pour plus d’informations sur les offres et coûts d’une référence SKU spécifique, consultez [Tarification de Power BI](https://powerbi.microsoft.com/pricing/). Un [module de calcul de coût](https://powerbi.microsoft.com/calculator/) est également disponible. Pour plus d’informations sur la planification d’une capacité d’analytique incorporée, consultez le [livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy).

* Les nœuds P peuvent être utilisés pour les déploiements incorporés ou pour les déploiements de services
* Les nœuds EM sont réservés aux déploiements incorporés

| Nœud de capacité | Nombre total de cœurs<br/>*(Serveur principal + serveur frontal)* | Cœurs du serveur principal | Cœurs du serveur frontal | Limites de connexions actives/DirectQuery | Rendus de pages au maximum aux heures de pointe | Disponibilité |
| --- | --- | --- | --- | --- | --- | --- |
| [EM3 (de mois en mois)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 cœurs virtuels |2 cœurs, 10 Go de RAM |2 cœurs | |601-1 200 |Disponibilité |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 cœurs virtuels |4 cœurs, 25 Go de RAM |4 cœurs |30 par seconde |1 201-2 400 |Disponible ([de mois en mois](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) est également disponible) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 cœurs virtuels |8 cœurs, 50 Go de RAM |8 cœurs |60 par seconde |2 401-4 800 |Disponibilité |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 cœurs virtuels |16 cœurs, 100 Go de RAM |16 cœurs |120 par seconde |4 801-9 600 |Disponibilité |

* Les cœurs du serveur frontal assurent la gestion du service web, des tableaux de bord et des rapports, des droits d’accès, de la planification, des API, des chargements et téléchargements et, plus généralement, de tout ce qui concerne l’expérience utilisateur.
* Les cœurs du serveur principal gèrent l’essentiel : traitement des requêtes, gestion du cache, exécution des serveurs R, actualisation des données, traitement du langage naturel, flux en temps réel et rendu côté serveur des rapports et images. Avec les cœurs du serveur principal, une partie de la mémoire est également réservée. Car il est impératif de disposer d’une mémoire suffisante pour traiter les modèles de données volumineux ou les grands nombres de jeux de données actifs.

## <a name="power-bi-report-server"></a>Power BI Report Server
Power BI Premium inclut le droit d’exécuter Power BI Report Server localement. Pour plus d’informations, consultez [Prise en main de Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Étapes suivantes
[Questions fréquentes Power BI Premium](service-premium-faq.md)  
[Notes de publication Power BI Premium](service-premium-release-notes.md)  
[Acheter Power BI Premium](service-admin-premium-purchase.md)  
[Gestion de Power BI Premium](service-admin-premium-manage.md)  
[Livre blanc sur Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy)  
[Administration de Power BI dans votre organisation](service-admin-administering-power-bi-in-your-organization.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

