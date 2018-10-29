---
title: Présentation de Microsoft Power BI Premium
description: Power BI Premium permet à votre organisation ou à votre équipe de bénéficier de performances plus fiables et de plus gros volumes de données sans qu’il soit nécessaire d’acquérir une licence pour chaque utilisateur.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 0723ddb57131fed499d4ac86666b3cd6d8bcbd2d
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271805"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Présentation de Microsoft Power BI Premium

Microsoft Power BI Premium fournit à votre organisation ou à votre équipe des ressources dédiées à l’exécution du service Power BI. Il vous offre des performances plus fiables et permet de traiter de gros volumes de données. Premium permet également une diffusion étendue du contenu sans que vous soyez contraint d’acquérir une licence Pro par utilisateur.

Pour tirer parti de Power BI Premium, vous pouvez attribuer des espaces de travail à une *capacité Premium*. Une capacité Premium est une ressource dédiée à votre organisation. Les espaces de travail non affectés à une capacité Premium sont attribués à une *capacité partagée*. Avec une capacité partagée, vos charges de travail s’exécutent sur des ressources de calcul partagées par d’autres clients. 

Dans une capacité partagée, Power BI impose plus de limites aux utilisateurs individuels afin de garantir une expérience de qualité à tous les utilisateurs. Par défaut, votre espace de travail se trouve dans une capacité partagée, notamment votre espace *Mon espace de travail* personnel et vos espaces de travail d’application.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Niveaux de capacité

Voici un résumé des différences entre la capacité partagée et la capacité Premium.

|  | Capacité partagée | Capacité Power BI Premium |
| --- | --- | --- |
| **Fréquence d’actualisation** |8/jour |48/jour |
| **Isolement avec matériel dédié** |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible") |
| **Distribution d’entreprise à** ***tous les utilisateurs*** | | |
| Applications et partage |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible")<sup>1</sup> |
| API et commandes incorporées |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible")<sup>2</sup> |
| **Publier des rapports Power BI localement** |![](media/service-premium/not-available.png "Non disponible") |![](media/service-premium/available.png "Disponible") |

*<sup>1</sup> Pour plus d’informations, consultez [Fonctionnalités par type de licence](service-features-license-type.md).*  
*<sup>2</sup> Améliorations prévues dans Power BI Premium.*

Pour commencer à utiliser une capacité Power BI Premium, affectez un espace de travail à une capacité. Quand la capacité premium stocke un espace de travail, vous obtenez ce qui suit :

* **Actualisations planifiées** : avec une capacité partagée, les actualisations planifiées des jeux de données des modèles importés sont limitées à huit fois par jour. Pour les jeux de données dans les espaces de travail Premium, vous pouvez planifier les actualisations jusqu’à 48 fois par jour. Les actualisations du cache DirectQuery sont toujours limitées à huit fois par jour dans la capacité Premium.

* **Isolement avec matériel dédié** : dans une capacité partagée, les demandes de ressources des autres charges de travail peuvent affecter les performances de vos rapports et tableaux de bord. En revanche, la capacité Premium offre des performances plus cohérentes et plus fiables en isolant vos charges de travail des charges de travail non liées.

Si une application est adossée à une capacité Premium (autrement dit, si elle a été publiée à partir d’un espace de travail d’application actuellement affecté à Premium), elle peut être utilisée par n’importe quel utilisateur de votre organisation, quelle que soit sa licence.

Pour en savoir plus sur l’attribution des espaces de travail à une capacité Premium, consultez [Gérer Power BI Premium](service-admin-premium-manage.md).

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nœuds de capacité Premium

Power BI Premium est disponible dans des configurations de nœuds aux capacités différentes en termes de cœurs virtuels. Pour plus d’informations sur les offres et les coûts d’une référence SKU spécifique, consultez [Tarification de Power BI](https://powerbi.microsoft.com/pricing/). Un [module de calcul de coût](https://powerbi.microsoft.com/calculator/) est également disponible. Pour plus d’informations sur la planification d’une capacité d’analytique incorporée, consultez le [livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy).

* Les nœuds P peuvent être utilisés pour les déploiements incorporés ou pour les déploiements de services.

* Les nœuds EM sont réservés aux déploiements incorporés. Les nœuds EM n’ont pas accès aux fonctionnalités premium comme le partage d’applications avec des utilisateurs qui ne disposent pas d’une licence Power BI Pro.

>[!NOTE]
>Les liens indiqués dans ce tableau fonctionnent correctement seulement pour les utilisateurs qui sont administrateurs généraux d’Office 365. Les autres utilisateurs reçoivent une erreur 404.

| Nœud de capacité | Total des cœurs virtuels<br/>*(Back-end + front-end)* | Cœurs virtuels de back-end | Cœurs virtuels de front-end | Limites de connexions actives/DirectQuery | Rendus de pages au maximum aux heures de pointe | Disponibilité |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (de mois en mois)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 cœur virtuel |0,5 cœur virtuel, 2,5 Go de RAM |0,5 cœur virtuel |3,75 par seconde |150-300 |Disponible |
| [EM2 (de mois en mois)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 cœurs virtuels |1 cœur virtuel, 5 Go de RAM |1 cœur virtuel |7,5 par seconde |301-600 |Disponible |
| [EM3 (de mois en mois)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 cœurs virtuels |2 cœurs virtuels, 10 Go de RAM |2 cœurs virtuels | |601-1 200 |Disponibilité |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 cœurs virtuels |4 cœurs virtuels, 25 Go de RAM |4 cœurs virtuels |30 par seconde |1 201-2 400 |Disponible ([de mois en mois](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) est également disponible) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 cœurs virtuels |8 cœurs virtuels, 50 Go de RAM |8 cœurs virtuels |60 par seconde |2 401-4 800 |Disponibilité |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 cœurs virtuels |16 cœurs virtuels, 100 Go de RAM |16 cœurs virtuels |120 par seconde |4 801-9 600 |Disponible |

* Les cœurs virtuels de front-end assurent la gestion des documents du service web, des tableaux de bord et des rapports, la gestion des droits d’accès, la planification, les API, les chargements et téléchargements et, plus généralement, tout ce qui concerne l’expérience utilisateur.

* Les cœurs virtuels de back-end gèrent l’essentiel : traitement des requêtes, gestion du cache, exécution des serveurs R, actualisation des données, traitement du langage naturel, flux en temps réel et rendu côté serveur des rapports et images. Avec les cœurs virtuels de back-end, une partie de la mémoire est également réservée. Car il est impératif de disposer d’une mémoire suffisante pour traiter les modèles de données volumineux ou les grands nombres de jeux de données actifs.

## <a name="power-bi-report-server"></a>Power BI Report Server
Power BI Premium offre également la possibilité d’exécuter Power BI Report Server localement dans votre organisation. Pour en savoir plus, consultez [Bien démarrer avec Power BI Report Server](report-server/get-started.md).

## <a name="next-steps"></a>Étapes suivantes
[Questions fréquentes Power BI Premium](service-premium-faq.md)  
[Notes de publication Power BI Premium](service-premium-release-notes.md)  
[Acheter Power BI Premium](service-admin-premium-purchase.md)  
[Gestion de Power BI Premium](service-admin-premium-manage.md)  
[Livre blanc sur Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Livre blanc Planification d’un déploiement de Power BI en entreprise](https://aka.ms/pbienterprisedeploy)  
[Administration de Power BI dans votre organisation](service-admin-administering-power-bi-in-your-organization.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
