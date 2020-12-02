---
title: Notifications d’interruption de service
description: Découvrez comment recevoir des notifications par e-mail en cas de perturbation ou de panne du service Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/25/2020
ms.openlocfilehash: e5d8f43a8edb6dc05b58cb62836e98cf209c8b5c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407811"
---
# <a name="service-interruption-notifications"></a>Notifications d’interruption de service

Il est important d’avoir un aperçu de la disponibilité de vos applications métier stratégiques. Power BI fournit une notification d’incident pour vous permettre de recevoir éventuellement des e-mails en cas de dégradation ou de perturbation du service. Même si le contrat de niveau de service (SLA) de 99,9 % de Power BI rend ces occurrences rares, nous voulons nous assurer que vous êtes tenu informé. La capture d’écran suivante montre le type d’e-mail que vous recevrez si vous activez les notifications :

![Actualiser l’e-mail de notification](media/service-interruption-notifications/refresh-notification-email.png)

À l’heure actuelle, nous envoyons des e-mails pour les _scénarios de fiabilité_ suivants :

- Fiabilité des rapports ouverts
- Fiabilité des actualisations de modèles
- Fiabilité des actualisations de requêtes

Des notifications sont envoyées en cas de _délai prolongé_ lors d’opérations telles que l’ouverture de rapports, l’actualisation du jeu de données ou l’exécution de requêtes. Après la résolution d’un incident, vous recevez un e-mail de suivi.

> [!NOTE]
> Cette fonctionnalité est disponible uniquement pour les capacités dans Power BI Premium. Elle n’est pas disponible pour la capacité partagée ou embarquée.

## <a name="capacity-and-reliability-notifications"></a>Notifications de capacité et de fiabilité

Quand une capacité Power BI Premium connaît des périodes prolongées d’utilisation intensive des ressources susceptibles d’impacter la fiabilité, un e-mail de notification est envoyé. Parmi ces impacts, citons des retards prolongés dans des opérations telles que l’ouverture d’un rapport, l’actualisation d’un jeu de données et l’exécution de requêtes. 

L’e-mail de notification fournit des informations sur la raison de l’utilisation intensive des ressources, notamment :

* ID du jeu de données responsable
* Type d'opération
* Temps processeur associé à l’usage intensif des ressources. Lisez la [définition du temps processeur](https://wikipedia.org/wiki/CPU_time) dans Wikipédia.

Power BI envoie également des notifications par e-mail en cas de détection d’une surcharge dans une capacité Power BI Premium. L’e-mail indique la raison probable de la surcharge, les opérations qui ont généré la charge au cours des 10 dernières minutes et la quantité de charge générée par chaque opération.

Si vous disposez de plusieurs capacités Premium, l’e-mail contiendra des informations sur ces capacités pendant la période de surcharge. Ces informations vous indiquent s’il est préférable de déplacer les espaces de travail qui contiennent des éléments gourmands en ressources vers des capacités dont la charge est moindre.

Les notifications de surcharge par e-mail ne sont envoyées que si un seuil de surcharge est déclenché. Vous ne recevrez pas de deuxième e-mail quand la charge sur cette capacité Premium reviendra à un niveau normal.

L’image suivante représente un exemple de notification par e-mail :

![e-mail de notification de capacité surchargée](media/service-interruption-notifications/refresh-notification-email-2.png)


## <a name="enable-notifications"></a>Activer les notifications

Un administrateur Power BI active les notifications dans le portail d’administration :

1. Identifiez ou créez un groupe de sécurité prenant en charge les e-mails qui doit recevoir des notifications.

1. Dans le portail d’administration, sélectionnez **Paramètres du locataire**. Sous **Paramètres d’aide et de support**, développez **Recevoir des notifications par e-mail pour les pannes ou incidents du service**.

1. Activez les notifications, entrez un groupe de sécurité, puis sélectionnez **Appliquer**.

    ![Activer les notifications de service](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI envoie des notifications à partir du compte no-reply-powerbi@microsoft.com. Vérifiez que ce compte est ajouté à votre liste des expéditeurs approuvés afin d’éviter que les notifications ne se trouvent dans un dossier Courrier indésirable.

## <a name="service-health-in-microsoft-365"></a>Intégrité du service dans Microsoft 365

Cet article explique comment recevoir des notifications de service par le biais de Power BI. Vous pouvez également superviser l’intégrité du service Power BI via Microsoft 365. Abonnez-vous pour recevoir des notifications par e-mail sur l’intégrité du service de la part de Microsoft 365. Pour plus d’informations, consultez [Guide pratique pour vérifier l’état du service Microsoft 365](/microsoft-365/enterprise/view-service-health).

## <a name="next-steps"></a>Étapes suivantes

[Options de support Power BI Pro et Power BI Premium](service-support-options.md)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)