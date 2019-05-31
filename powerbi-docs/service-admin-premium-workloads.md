---
title: Guide pratique pour configurer des charges de travail dans Power BI Premium
description: Découvrez comment configurer des charges de travail dans une capacité Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564884"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurer des charges de travail dans une capacité Premium

Cet article décrit comment activer et configurer des charges de travail pour les capacités Power BI Premium. Par défaut, les capacités prennent en charge uniquement la charge de travail qui est associée aux requêtes Power BI en cours d’exécution. Vous pouvez également activer et configurer des charges de travail supplémentaires pour **[IA (Cognitive Services)](service-cognitive-services.md)** , **[Flux de données](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** et **[Rapports paginés](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Paramètres de mémoire par défaut

Les charges de travail de requête sont optimisées pour, et limitées par, les ressources déterminées par votre référence SKU de capacité Premium. Les capacités Premium prennent également en charge des charges de travail supplémentaires pouvant utiliser les ressources de votre capacité. Les valeurs de mémoire par défaut pour ces charges de travail dépendent des nœuds de capacité disponibles pour votre référence SKU. Les paramètres de mémoire maximale ne sont pas cumulés. La mémoire, à hauteur de la valeur maximale spécifiée, est allouée de façon dynamique pour l’IA et les dataflows, mais allouée de façon statique pour les rapports paginés. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Références (SKU) Microsoft Office pour les scénarios SaaS (Software as a Service)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | Non applicable | Non applicable | par défaut de 20 % ; minimale de 20 % | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum |
| Flux de données | Non applicable |20 % par défaut ; 12 % minimum  | 20 % par défaut ; 5 % minimum  | 20 % par défaut ; 3 % minimum | 20 % par défaut ; 2 % minimum  |
| Rapports paginés | Non applicable |Non applicable | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Références (SKU) Microsoft Azure pour les scénarios PaaS (Platform as a Service)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | Non applicable                      | par défaut de 20 % ; minimum de 100 %                     | par défaut de 20 % ; 50 % minimale                     | par défaut de 20 % ; minimale de 20 % | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum |
| Flux de données         | 40 % par défaut ; 40 % minimum | 24 % par défaut ; 24 % minimum | 20 % par défaut ; 12 % minimum | 20 % par défaut ; 5 % minimum  | 20 % par défaut ; 3 % minimum | 20 % par défaut ; 2 % minimum   |
| Rapports paginés | Non applicable                      | N/A                      | Non applicable                     | 20 % par défaut ; 10 % minimum | 20 % par défaut ; 5 % minimum | 20 % par défaut ; 2,5 % minimum |
| | | | | | |

## <a name="workload-settings"></a>Paramètres de la charge de travail

### <a name="ai-preview"></a>Intelligence artificielle (version préliminaire)

Outre le **Max Memory** définition, la charge de travail d’intelligence artificielle a un paramètre supplémentaire, **autorise l’utilisation de Power BI Desktop**. La valeur par défaut est **hors**. Ce paramètre est réservé pour une utilisation future et ne peut pas apparaître dans tous les locataires.

### <a name="datasets-preview"></a>Jeux de données (version préliminaire)

Par défaut, la charge de travail de jeux de données est activé et ne peut pas être désactivée. Cette charge de travail contient un paramètre supplémentaire, **point de terminaison XMLA**. La valeur par défaut est **1**, ce qui signifie activé. Ce paramètre spécifie les connexions à partir d’applications clientes honorent l’appartenance au groupe de sécurité définies aux niveaux application et d’espace de travail. Pour plus d’informations, consultez [se connecter à des jeux de données avec les applications clientes et des outils](service-premium-connect-tools.md).

### <a name="dataflows"></a>Flux de données

Outre le **Max Memory** définition, la charge de travail de flux de données a un paramètre supplémentaire, **taille du conteneur**. Ce paramètre vous permet d’optimiser les performances de charge de travail de flux de données pour le traitement des flux de données plus complexes, nécessitant beaucoup de calcul.

Lors de l’actualisation d’un flux de données, la charge de travail de flux de données génère un conteneur pour chaque entité dans le flux de données. Chaque conteneur peut prendre de mémoire au volume dans spécifié dans le paramètre de taille de conteneur. La valeur par défaut pour toutes les références SKU est **700 Mo**. Vous souhaiterez peut-être modifier ce paramètre si :

- Flux de données est trop longue pour actualiser ou l’actualisation de flux de données échoue sur un délai d’expiration.
- Les entités de flux de données incluent des étapes de calcul, par exemple, une jointure.  

Il s’agit de conseillé d’utiliser le [métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md) application pour analyser les performances de charge de travail de flux de données. 

Dans certains cas, l’augmentant la taille du conteneur n’améliore pas les performances. Par exemple, si le flux de données obtient des données à partir d’une source sans effectuer de calculs significatifs, modification de la taille de conteneur probablement sont inutiles. Augmenter la taille du conteneur peut aider si il prend en charge la charge de travail de flux de données à allouer davantage de mémoire pour l’entité les opérations d’actualisation. En ayant plus de mémoire allouée, elle peut réduire le temps que nécessaire pour actualiser les entités fortement calculées. 

La valeur de la taille du conteneur ne peut pas dépasser la mémoire maximale pour la charge de travail de flux de données. Par exemple, une capacité de P1 possède 25 Go de mémoire. Si la charge de travail de flux de données Max Memory (%) est défini sur 20 %, conteneur de taille (Mo) ne peut pas dépasser 5000. Dans tous les cas, la taille du conteneur ne peut pas dépasser le Max Memory, même si vous définissez une valeur plus élevée. 

### <a name="paginated-reports-preview"></a>Rapports paginés (version préliminaire)

Rapports paginés permettent au code personnalisé à exécuter lors du rendu d’un rapport. Par exemple, modifier dynamiquement la couleur du texte en fonction du contenu, ce qui peut prendre plus de mémoire. Power BI Premium génère les rapports paginés dans un espace contenu au sein de la capacité. Le Max Memory spécifié est utilisé *ou non* la charge de travail est actif. Si la modification du paramètre de mémoire maximale par défaut, veillez à définir faible suffisamment qu’elle n’affecte pas négativement autres charges de travail.

Dans certains cas, la charge de travail des rapports paginés peut devenir indisponible. Dans ce cas, la charge de travail affiche un état d’erreur dans le portail d’administration, et les utilisateurs voient des délais d’expiration pour le rendu du rapport. Pour atténuer ce problème, désactivez la charge de travail, puis l’activer à nouveau.

## <a name="configure-workloads"></a>Configurer des charges de travail

Optimisez les ressources disponibles de votre capacité en activant uniquement les charges de travail qui seront utilisées. Ne modifiez les paramètres de mémoire que si vous avez constaté que les paramètres par défaut ne répondent pas aux besoins en ressources de votre capacité de mémoire.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Pour configurer des charges de travail dans le portail d’administration Power BI

1. Dans **Paramètres de capacité** > **CAPACITÉS PREMIUM**, sélectionnez une capacité.

1. Sous **PLUS D’OPTIONS**, développez **Charges de travail**.

1. Activer une ou plusieurs charges de travail et définir une valeur de **Mémoire maximale**.   

    
    ![Activer des charges de travail](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Cliquez sur **Appliquer**.

### <a name="rest-api"></a>API REST

Les charges de travail peuvent être activées et attribuées à une capacité à l’aide des API REST [Capacités](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Surveillance des charges de travail

L’[application Métriques de capacité Power BI Premium](service-admin-premium-monitor-capacity.md) fournit un jeu de données, des flux de données et des métriques de rapports paginés afin de surveiller les charges de travail activées pour vos capacités. 

## <a name="next-steps"></a>Étapes suivantes

[Optimisation des capacités Power BI Premium](service-premium-capacity-optimize.md)     
[Préparation des données en libre-service dans Power BI avec des dataflows](service-dataflows-overview.md)   
[Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)   

D’autres questions ? [Poser des questions à la communauté Power BI](http://community.powerbi.com/)