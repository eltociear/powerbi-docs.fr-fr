---
title: 'Tutoriel : Définir des alertes de données dans le service Power BI'
description: Dans ce tutoriel, vous découvrez comment définir des alertes pour vous avertir quand des données de vos tableaux de bord changent au-delà des limites que vous définissez dans le service Microsoft Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: cd92374a23a2ee7023c75cfb2612c00d513e9895
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61065645"
---
# <a name="tutorial-set-data-alerts-in-power-bi-service"></a>Tutoriel : Définir des alertes de données dans le service Power BI
Définissez des alertes pour vous avertir quand des données de vos tableaux de bord changent au-delà des limites que vous définissez. 

Vous pouvez définir des alertes sur des vignettes si vous disposez d’une licence Power BI Pro ou si un tableau de bord a été partagé avec vous à partir d’une [capacité Premium](../service-premium-what-is.md). Des alertes ne peuvent être configurées que sur des vignettes épinglées à partir de visuels de rapport, et uniquement sur des jauges, des indicateurs de performance clés et des cartes. Des alertes peuvent être définies sur des visuels créés à partir de jeux de données de streaming qui ont été épinglés d’un rapport vers un tableau de bord. Mais vous ne pouvez pas les définir sur des vignettes de streaming créées directement sur le tableau de bord à l’aide de **Ajouter une vignette** > **Données de streaming personnalisées**. 

Vous seul pouvez voir les alertes que vous définissez, même si vous partagez votre tableau de bord. Les alertes de données sont entièrement synchronisées entre plateformes. Définissez et affichez les alertes de données [dans les applications mobiles Power BI](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) et dans le service Power BI. 

![vignettes](../media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> Les notifications d’alerte pilotées par les données fournissent des informations sur vos données. Si vous affichez vos données Power BI sur un appareil mobile et que celui-ci est volé, nous vous recommandons d’utiliser le service Power BI pour désactiver toutes les règles d’alerte pilotées par les données.
> 

Ce tutoriel couvre les points suivants.
> [!div class="checklist"]
> * Qui peut définir des alertes
> * Quels visuels sont pris en charge par les alertes
> * Qui peut voir mes alertes
> * Les alertes fonctionnent-elles sur Power BI Desktop et sur Power BI Mobile
> * Comment créer une alerte
> * Où vais-je recevoir mes alertes

Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

## <a name="set-data-alerts-in-power-bi-service"></a>Définir des alertes de données dans le service Power BI
Regardez Amanda ajouter certaines alertes à des vignettes sur son tableau de bord. Suivez ensuite les instructions détaillées sous la vidéo pour essayer vous-même.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

Cet exemple utilise une vignette de carte du tableau de bord [Retail Analysis Sample](http://go.microsoft.com/fwlink/?LinkId=529778) (Exemple Analyse de la vente au détail).

1. Dans une jauge, un indicateur de performance clé ou une vignette de carte du tableau de bord, sélectionnez les points de suspension.
   
   ![Vignette Total Stores](media/end-user-alerts/powerbi-card.png)
2. Sélectionnez l’icône en forme de cloche ![icône d’alerte](media/end-user-alerts/power-bi-bell-icon.png) ou **Gérer les alertes** pour ajouter une ou plusieurs alertes pour **Total stores** (Nombre total de magasins).
   
1. Dans le volet **Gérer les alertes**, sélectionnez **+ Ajouter une règle d’alerte**.  Vérifiez que le curseur est défini sur **Activé** et donnez un titre à votre alerte. Les titres vous aident à reconnaître facilement vos alertes.
   
   ![Fenêtre Gérer les alertes](media/end-user-alerts/powerbi-alert-title.png)
4. Faites défiler vers le bas, puis entrez les détails de l’alerte.  Dans cet exemple, nous allons créer une alerte qui nous avertit une fois par jour si le nombre total de magasins est supérieur à 100. Les alertes s’affichent dans notre centre de notification. Nous allons également demander à Power BI de nous envoyer un courrier électronique.
   
   ![Fenêtre Gérer les alertes, Seuil défini](media/end-user-alerts/power-bi-set-alert-details.png)
5. Sélectionnez **Enregistrer et fermer**.

## <a name="receiving-alerts"></a>Recevoir des alertes
Quand les données suivies atteignent un des seuils définis, plusieurs choses se produisent. Power BI vérifie d’abord si cela fait plus d’une heure ou plus de 24 heures (selon l’option sélectionnée) que la dernière alerte a été envoyée. Tant que les données se trouvent au-delà du seuil, vous recevez une alerte.

Ensuite, Power BI envoie une alerte à votre centre de notification et éventuellement par courrier électronique. Chaque alerte contient un lien direct vers vos données. Sélectionnez le lien pour afficher la vignette appropriée.  

1. Si vous avez défini l’alerte de façon à recevoir un courrier électronique, vous recevez un message semblable à celui-ci dans votre boîte de réception.
   
   ![E-mail d’alerte](media/end-user-alerts/powerbi-alerts-email.png)
2. Power BI ajoute un message à votre **centre de notification** et ajoute une nouvelle icône d’alerte à la vignette applicable.
   
   ![icône Notification dans le service Power BI](media/end-user-alerts/powerbi-alert-notifications.png)
3. Ouvrez le centre de notification pour afficher les détails de l’alerte.
   
    ![lire l’alerte](media/end-user-alerts/powerbi-alert-notification.png)
   
   > [!NOTE]
   > Les alertes fonctionnent uniquement sur les données actualisées Lorsque les données sont actualisées, Power BI vérifie si une alerte est définie pour celles-ci. Si les données ont atteint un seuil d’alerte, une alerte est déclenchée.
   > 
   > 

## <a name="managing-alerts"></a>Gestion des alertes
Il existe de nombreuses façons de gérer vos alertes : à partir de la vignette de tableau de bord elle-même, dans le menu Paramètres de Power BI et sur une vignette spécifique dans l’[application mobile Power BI sur iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) ou dans l’[application mobile Power BI pour Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>À partir de la vignette elle-même
1. Si vous devez modifier ou supprimer une alerte pour une vignette, rouvrez la fenêtre **Gérer les alertes** en sélectionnant l’icône en forme de cloche ![icône d’alerte](media/end-user-alerts/power-bi-bell-icon.png). Toutes les alertes que vous avez définies pour cette vignette sont affichées.
   
    ![Fenêtre Gérer les alertes](media/end-user-alerts/powerbi-see-alerts.png).
2. Pour modifier une alerte, sélectionnez la flèche à gauche du nom de l’alerte.
   
    ![flèche à côté du nom de l’alerte](media/end-user-alerts/powerbi-see-alerts-arrow.png).
3. Pour supprimer une alerte, sélectionnez la poubelle à droite du nom de l’alerte.
   
      ![icône de corbeille sélectionnée](media/end-user-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Dans le menu Paramètres de Power BI
1. Sélectionnez l’icône en forme d’engrenage dans la barre de menus de Power BI.
   
    ![icône d’engrenage](media/end-user-alerts/powerbi-gear-icon.png).
2. Sous **Paramètres**, sélectionnez **Alertes**.
   
    ![onglet Alertes de la fenêtre Paramètres](media/end-user-alerts/powerbi-alert-settings.png)
3. À ce stade, vous pouvez activer et désactiver les alertes, ouvrir la fenêtre **Gérer les alertes** pour apporter des modifications ou supprimer l’alerte.

## <a name="tips-and-troubleshooting"></a>Conseils et résolution des problèmes
* Les alertes ne sont pas actuellement prises en charge pour les vignettes Bing ou les vignettes de carte avec des mesures au format date/heure.
* Les alertes fonctionnent uniquement avec des données numériques.
* Les alertes fonctionnent uniquement sur les données actualisées (pas sur les données statiques).
* Les alertes fonctionnent uniquement sur des jeux de données de streaming si vous générez un visuel de rapport de type KPI/carte/jauge, puis que vous épinglez ce visuel au tableau de bord.

## <a name="clean-up-resources"></a>Nettoyer les ressources
Les instructions pour la suppression des alertes sont expliquées ci-dessus. En résumé, sélectionnez l’icône d’engrenage dans la barre de menus de Power BI. Sous **Paramètres**, sélectionnez **Alertes** et supprimez l’alerte.

> [!div class="nextstepaction"]
> [Définir des alertes de données sur votre appareil mobile](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


