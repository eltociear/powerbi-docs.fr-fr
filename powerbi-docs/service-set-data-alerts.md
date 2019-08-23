---
title: Définir des alertes de données dans le service Power BI
description: Découvrez comment utiliser le service Microsoft Power BI afin de définir des alertes pour vous avertir quand des données de vos tableaux de bord changent au-delà des limites que vous définissez.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/08/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: c87a54a0e991af3faa53b9ac4ac6c92893b2ed0a
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68962689"
---
# <a name="data-alerts-in-the-power-bi-service"></a>Alertes de données dans le service Power BI

Définissez des alertes pour vous avertir quand des données de vos tableaux de bord changent au-delà des limites que vous définissez.

Vous pouvez définir des alertes sur les vignettes si vous disposez d’une licence Power BI Pro. Vous pouvez également définir des alertes si quelqu’un partage un tableau de bord qui se trouve dans une [capacité Premium](service-premium-what-is.md). Des alertes ne peuvent être définies que sur des vignettes épinglées à partir de visuels de rapport, et uniquement sur des jauges, des indicateurs de performance clés et des cartes. Des alertes peuvent être définies sur des visuels créés à partir de jeux de données de streaming que vous épinglez d’un rapport vers un tableau de bord. Vous ne pouvez pas définir d’alertes sur des vignettes de streaming créées directement sur le tableau de bord à l’aide de **Ajouter une vignette** > **Données de streaming personnalisées**.

Vous seul pouvez voir les alertes que vous définissez, même si vous partagez votre tableau de bord. Les alertes de données sont entièrement synchronisées entre plateformes. Définissez et affichez les alertes de données [dans les applications mobiles Power BI](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md) et dans le service Power BI. Elles ne sont pas disponibles dans Power BI Desktop. Vous pouvez même automatiser et intégrer des alertes avec Microsoft Flow. Vous pouvez essayer vous-même dans cet article [Microsoft Flow et Power BI](service-flow-integration.md).

![vignettes](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Les notifications d’alerte pilotées par les données fournissent des informations sur vos données. Si vous affichez vos données Power BI sur un appareil mobile et que celui-ci est perdu ou volé, nous vous recommandons d’utiliser le service Power BI pour désactiver toutes les règles d’alerte de données.

## <a name="set-data-alerts-in-the-power-bi-service"></a>Définir des alertes de données dans le service Power BI

Regardez Amanda ajouter certaines alertes à des vignettes sur le tableau de bord. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

Cet exemple utilise une vignette de carte de l’exemple de tableau Retail Analysis (Analyse de vente au détail). [Obtenir l’exemple Retail Analysis (Analyse de la vente au détail)](sample-retail-analysis.md#get-the-content-pack-for-this-sample) si vous voulez effectuer la procédure.

1. Commencez sur un tableau de bord. Dans la vignette **Total Stores** (Nombre total de magasins), sélectionnez les points de suspension.

   ![Vignette Total Stores](media/service-set-data-alerts/powerbi-card.png)

1. Sélectionnez l’icône en forme de cloche ![Icône d’alerte](media/service-set-data-alerts/power-bi-bell-icon.png) pour ajouter une ou plusieurs alertes pour **Total stores** (Nombre total de magasins).

1. Pour commencer, sélectionnez **+ Ajouter une règle d’alerte**, vérifiez que le curseur **Actif** est défini sur **Activé**, puis donnez un titre à votre alerte. Les titres vous aident à reconnaître facilement vos alertes.

   ![Fenêtre Gérer les alertes](media/service-set-data-alerts/powerbi-alert-title.png)

1. Faites défiler vers le bas, puis entrez les détails de l’alerte.  Dans cet exemple, vous allez créer une alerte qui vous avertit une fois par jour si le nombre total de magasins est supérieur à 100.

   ![Fenêtre Gérer les alertes, Seuil défini](media/service-set-data-alerts/power-bi-set-alert-details.png)

    Les alertes s’affichent dans votre **centre de notification**. Si vous cochez la case à cocher correspondante, Power BI vous envoie également un e-mail à propos de l’alerte.

1. Sélectionnez **Enregistrer et fermer**.

## <a name="receiving-alerts"></a>Recevoir des alertes

Quand les données suivies atteignent l’un des seuils définis, plusieurs choses se produisent. Tout d’abord, Power BI vérifie si plus d’une heure ou plus de 24 heures (selon l’option sélectionnée) se sont écoulées depuis la dernière alerte. Si les données se trouvent au-delà du seuil, vous recevez une alerte.

Ensuite, Power BI envoie une alerte à votre **centre de notification** et, éventuellement, un e-mail. Chaque alerte contient un lien direct vers vos données. Sélectionnez le lien pour afficher la vignette pertinente, dans laquelle vous pouvez explorer, partager et apprendre des informations supplémentaires.  

* Si vous avez défini l’alerte de façon à recevoir un courrier électronique, vous recevez un message semblable à celui-ci dans votre boîte de réception.

   ![E-mail d’alerte](media/service-set-data-alerts/powerbi-alerts-email.png)

* Power BI ajoute un message à votre **centre de notification** et ajoute une nouvelle icône d’alerte à la vignette applicable.

   ![icône Notification dans le service Power BI](media/service-set-data-alerts/powerbi-alert-notifications.png)

* Votre **centre de notification** affiche les détails de l’alerte.

    ![lire l’alerte](media/service-set-data-alerts/powerbi-alert-notification.png)

   > [!NOTE]
   > Les alertes fonctionnent uniquement sur des données actualisées. Lorsque les données sont actualisées, Power BI vérifie si une alerte est définie pour celles-ci. Si les données ont atteint un seuil d’alerte, Power BI déclenche une alerte.

## <a name="managing-alerts"></a>Gestion des alertes

Il existe de nombreuses façons de gérer vos alertes :

* À partir de la vignette de tableau de bord.

* Dans le menu Paramètres de Power BI.

* Sur une vignette dans les [applications mobiles Power BI](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-dashboard-tile"></a>À partir de la vignette de tableau de bord

1. Si vous devez changer ou supprimer une alerte pour une vignette, rouvrez la fenêtre **Gérer les alertes** en sélectionnant l’icône en forme de cloche ![Icône d’alerte](media/service-set-data-alerts/power-bi-bell-icon.png).

    Power BI affiche la ou les alertes que vous avez définies pour cette vignette.

    ![Fenêtre Gérer les alertes](media/service-set-data-alerts/powerbi-see-alerts.png)

1. Pour modifier une alerte, sélectionnez la flèche à gauche du nom de l’alerte.

    ![flèche à côté du nom de l’alerte](media/service-set-data-alerts/powerbi-see-alerts-arrow.png)

1. Pour supprimer une alerte, sélectionnez la poubelle à droite du nom de l’alerte.

      ![icône de corbeille sélectionnée](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Dans le menu Paramètres de Power BI

1. Sélectionnez l’icône en forme d’engrenage dans la barre de menus de Power BI, puis sélectionnez **Paramètres**.

    ![icône d’engrenage](media/service-set-data-alerts/powerbi-gear-icon.png).

1. Sous **Paramètres**, sélectionnez **Alertes**.

    ![onglet Alertes de la fenêtre Paramètres](media/service-set-data-alerts/powerbi-alert-settings.png)

1. À ce stade, vous pouvez activer et désactiver les alertes, ouvrir la fenêtre **Gérer les alertes** pour apporter des modifications ou supprimer l’alerte.

## <a name="tips-and-troubleshooting"></a>Conseils et résolution des problèmes

* Les alertes ne sont pas prises en charge pour les vignettes de carte avec des mesures au format date/heure.

* Les alertes fonctionnent uniquement avec des données numériques.

* Les alertes fonctionnent uniquement sur des données actualisées. (pas sur les données statiques).

* Les alertes fonctionnent uniquement sur des jeux de données de streaming si vous générez un visuel de rapport de type KPI, carte ou jauge, puis que vous épinglez ce visuel au tableau de bord.

## <a name="next-steps"></a>Étapes suivantes

* [Créer un flux Microsoft Flow qui inclut une alerte de données](service-flow-integration.md).

* [Définir des alertes de données sur votre appareil mobile](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

* [Qu’est-ce que Power BI ?](power-bi-overview.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)
