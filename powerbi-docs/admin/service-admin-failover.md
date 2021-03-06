---
title: FAQ sur la haute disponibilité, le basculement et la reprise d’activité avec Power BI
description: Découvrez comment le service Power BI offre la haute disponibilité et assure la continuité de l’activité et la reprise d’activité à ses utilisateurs.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2020
LocalizationGroup: Administration
ms.openlocfilehash: ff41f702edc605ee346aa10a759e633377597504
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408961"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>FAQ sur la haute disponibilité, le basculement et la reprise d’activité avec Power BI

Cet article explique comment le service Power BI offre la haute disponibilité et assure la continuité de l’activité et la reprise d’activité à ses utilisateurs. En lisant cet article, vous comprenez mieux comment la haute disponibilité est obtenue, dans quelles circonstances Power BI effectue un basculement et ce qu’il faut attendre du service quand il effectue un basculement.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Que signifie « haute disponibilité » pour Power BI ?

Power BI est un logiciel en tant que service (SaaS) complètement managé.  Microsoft le conçoit et le gère pour qu’il résiste aux pannes d’infrastructure afin que les utilisateurs puissent toujours accéder à leurs rapports.  Le service est pris en charge par un [contrat SLA à 99,9 %](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>Qu’est-ce qu’un basculement Power BI ?

Power BI conserve plusieurs instances de chaque composant dans des centres de données Azure (aussi appelés régions) pour assurer la continuité de l’activité. En cas de panne ou de problème rendant Power BI inaccessible ou inutilisable dans une région, Power BI bascule tous ses composants dans cette région sur une instance de sauvegarde. Le basculement restaure la disponibilité et l’utilisabilité de l’instance de service Power BI dans une nouvelle région (généralement dans la même zone géographique, comme indiqué dans [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Une instance de service Power BI qui a basculé prend uniquement en charge les _opérations de lecture_, ce qui signifie que les opérations suivantes ne sont pas prises en charge pendant le basculement : actualisations, opérations de publication de rapport, modifications de tableau de bord ou de rapport et autres opérations qui nécessitent un changement des métadonnées de Power BI (par exemple, insertion d’un commentaire dans un rapport).  Les opérations de lecture, comme l’affichage des tableaux de bord et des rapports (qui ne reposent pas sur DirectQuery ni Live Connect pour les sources de données locales) continuent à fonctionner normalement.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Comment les instances de sauvegarde restent-elles synchronisées avec mes données ?

Tous les composants de service Power BI synchronisent régulièrement leurs instances de sauvegarde. Nous ciblons une synchronisation de 15 minutes à un point dans le temps pour tout le contenu chargé ou changé dans Power BI. En cas de basculement, Power BI utilise la [réplication géoredondante du stockage Azure](/azure/storage/common/storage-redundancy-grs) et la [réplication géoredondante SQL Azure](/azure/sql-database/sql-database-active-geo-replication) pour que les instances de sauvegarde existent dans d’autres régions et soient utilisables en cas de basculement.

## <a name="where-are-the-failover-clusters-located"></a>Où se trouvent les clusters de basculement ?

Les instances de sauvegarde résident dans la même zone géographique que celle sélectionnée quand votre organisation s’est inscrite à Power BI, sauf indication contraire dans [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Une zone géographique peut contenir plusieurs régions et Microsoft peut répliquer des données sur n’importe quelle région d’une zone géographique donnée pour assurer la résilience des données. Microsoft ne réplique ni ne déplace les données d’un client en dehors de la zone géographique. Pour avoir un mappage des zones géographiques proposées par Power BI et des régions qu’elles contiennent, consultez [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location).

## <a name="how-does-microsoft-decide-to-fail-over"></a>Comment Microsoft détermine s’il faut effectuer un basculement ?

Deux systèmes différents permettent de déterminer si un basculement est nécessaire :

- Nos sondes de supervision internes et externes indiquent un manque de disponibilité ou une incapacité de fonctionnement normal. Ces indications peuvent s’appuyer sur des pannes détectées dans les composants de Power BI, ou dans un ou plusieurs services dont dépend Power BI dans une région.
- L’équipe des opérations centrales Microsoft Azure nous informe d’une panne critique dans une région.

Dans les deux cas, ce sont les membres de la direction Power BI qui prennent la décision d’effectuer le basculement, la décision n’est pas automatisée. Une fois la décision prise, le processus de basculement s’exécute automatiquement.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Comment savoir si Power BI est actuellement en mode de basculement ?

Une notification est publiée sur la page de support de Power BI ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). La notification indique les opérations principales qui ne sont pas disponibles pendant le basculement, notamment la publication, l’actualisation, la création de tableau de bord, la duplication de tableau de bord et les changements d’autorisation.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Combien de temps faut-il à Power BI pour effectuer le basculement ?

Quand la nécessité d’un basculement a été déterminée, Power BI est de nouveau opérationnel au bout de 15 minutes environ. Le temps nécessaire pour déterminer qu’un basculement est nécessaire varie en fonction du scénario d’interruption. 

Dès lors qu’un basculement est effectué, Power BI utilise la géoréplication du stockage Azure pour effectuer le basculement. En règle générale, ces réplications ont un point de retour de 15 minutes. Cependant, le [stockage Azure ne garantit pas ce délai](/azure/storage/common/storage-redundancy) dans le cadre d’un SLA. Power BI n’est donc pas en mesure de garantir un délai non plus. 

## <a name="what-happens-to-workspaces-and-reports-if-my-premium-capacity-becomes-unavailable"></a>Qu’advient-il des espaces de travail et des rapports si ma capacité Premium n’est plus disponible ? 

Si une capacité Premium n’est plus disponible, les espaces de travail et les rapports restent accessibles et visibles pour tous les utilisateurs titulaires d’une licence Power BI Pro qui y avaient déjà accès.

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Quand mon instance Power BI retourne-t-elle dans la région d’origine ?

Les instances de service Power BI retournent dans leur région d’origine quand le problème qui a provoqué le basculement est résolu. Consultez la page de support Power BI : Quand le problème est résolu, l’équipe Power BI supprime la notification qui décrit le basculement. À ce stade, les opérations doivent être revenues à la normale.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Suis-je responsable de la disponibilité de ma solution Power BI ?

Si la solution Power BI utilisée dans votre organisation implique l’un des éléments suivants, vous devez prendre des mesures pour assurer la haute disponibilité de la solution :

- Si votre organisation utilise Power BI Premium, vous devez vérifier que la capacité Premium est dimensionnée pour répondre aux demandes de charge de votre déploiement.  Le [livre blanc Planification et déploiement de Power BI Premium](https://aka.ms/Premium-Capacity-Planning-Deployment) et l’[application Métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md) peuvent vous aider à planifier cette exigence et à y répondre. Nous ajoutons régulièrement de nouvelles fonctionnalités à l’application de métriques et au portail d’administration dans Power BI pour fournir de l’aide.
- Si votre organisation accède à des sources de données locales à l’aide de la passerelle de données locale, vous devez configurer la passerelle [comme décrit dans cet article](/data-integration/gateway/service-gateway-high-availability-clusters) pour prendre en charge la haute disponibilité. Suivez ces instructions si vous actualisez des rapports en mode d’importation ou que vous accédez à des données ou des modèles de données à l’aide de DirectQuery ou de Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>Les passerelles fonctionnent-elles en mode de basculement ?

Non. Les données provenant des sources de données locales (tous les rapports et tableaux de bord basés sur Direct Query et Live Connect) ne fonctionnent pas pendant le basculement. Toutefois, la configuration de la passerelle ne change pas. Quand l’instance Power BI retourne à son état d’origine, les passerelles retrouvent leurs fonctions normales.

Si un sinistre grave se produit dans une région primaire et empêche le retour en ligne pendant une longue période, la région primaire basculée autorisera à la fois les opérations de lecture et d’écriture, et les clients pourront redéployer et configurer des passerelles dans la nouvelle région.

Les clients peuvent choisir d’installer une nouvelle passerelle sur une autre machine ou de prendre le contrôle de leur passerelle existante. La prise de contrôle de la passerelle existante est normalement plus simple, car toutes les sources de données associées à l’ancienne passerelle seront transférées vers la nouvelle.
