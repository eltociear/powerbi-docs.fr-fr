---
title: Guide pratique pour configurer des charges de travail dans Power BI Premium
description: Découvrez comment configurer des charges de travail dans une capacité Power BI Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/11/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0baab138ee98d2ec96bc9f47e6e727525a57ed3e
ms.sourcegitcommit: f176ba9d52d50d93f264eca21bb3fd987dbf934b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57757243"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurer des charges de travail dans une capacité Premium

Cet article décrit comment activer et configurer des charges de travail pour les capacités Power BI Premium. Par défaut, les capacités prennent en charge uniquement la charge de travail qui est associée aux requêtes Power BI en cours d’exécution. Les charges de travail de requête sont optimisées pour, et limitées par, les ressources déterminées par votre référence SKU de capacité Premium. Les capacités Premium prennent également en charge des charges de travail supplémentaires pouvant utiliser les ressources de capacité.

## <a name="configure-workloads"></a>Configurer des charges de travail

Vous pouvez activer et configurer des charges de travail supplémentaires pour AI, les [dataflows](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) et les [rapports paginés](paginated-reports-save-to-power-bi-service.md). Les valeurs de mémoire par défaut pour ces charges de travail dépendent des nœuds de capacité disponibles pour votre référence SKU. Les paramètres de mémoire maximale ne sont pas cumulés. La mémoire, à hauteur de la valeur maximale spécifiée, est allouée de façon dynamique pour l’IA et les dataflows, mais allouée de façon statique pour les rapports paginés. 

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Pour configurer des charges de travail dans le portail d’administration Power BI

1. Dans **Paramètres de capacité** > **CAPACITÉS PREMIUM**, sélectionnez une capacité.

1. Sous **PLUS D’OPTIONS**, développez **Charges de travail**.

1. Activer une ou plusieurs charges de travail et définir une valeur de **Mémoire maximale**.   

    
    ![Activer des charges de travail](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Cliquez sur **Appliquer**.

> [!NOTE]
> Si vous activez la charge de travail des rapports paginés, les rapports paginés vous permettent d’exécuter votre propre code lors de la génération d’un rapport (par exemple, pour changer dynamiquement la couleur du texte en fonction du contenu). Power BI Premium génère les rapports paginés dans un espace contenu au sein de la capacité. La mémoire maximale attribuée à cet espace est utilisée, que la charge de travail soit activée ou non. Si vous utilisez des rapports Power BI ou des flux de données dans la même capacité, veillez à définir pour les rapports paginés une mémoire suffisamment faible qui n’affecte pas négativement les autres charges de travail. dans de rares cas, la charge de travail des rapports paginés peut devenir indisponible. La charge de travail affiche alors un état d’erreur dans le portail d’administration, et les utilisateurs voient des délais d’expiration pour la génération des rapports. Pour résoudre ce problème, désactivez la charge de travail, puis réactivez-la.


### <a name="rest-api"></a>API REST

Les charges de travail peuvent être activées et attribuées à une capacité à l’aide des API REST [Capacités](https://docs.microsoft.com/rest/api/power-bi/capacities).


## <a name="next-steps"></a>Étapes suivantes

[Gestion et optimisation des ressources de capacité de Power BI Premium](service-premium-understand-how-it-works.md)   
[Préparation des données en libre-service dans Power BI avec des dataflows](service-dataflows-overview.md)   
[Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)   

D’autres questions ? [Poser des questions à la communauté Power BI](http://community.powerbi.com/)