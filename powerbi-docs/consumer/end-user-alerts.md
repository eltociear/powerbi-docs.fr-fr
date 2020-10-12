---
title: 'Tutoriel : Définir des alertes de données sur les tableaux de bord du service Power BI'
description: Dans ce tutoriel, vous découvrez comment définir des alertes pour vous avertir quand des données de vos tableaux de bord changent au-delà des limites que vous définissez dans le service Microsoft Power BI.
author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 08/05/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 22d9baaf50ce32c4a9d3644cff455b474bdd1549
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525310"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>Tutoriel : Définir des alertes sur des tableaux de bord Power BI

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Définissez des alertes dans le service Power BI pour vous avertir quand des données de vos tableaux de bord changent au-delà ou en deçà des limites que vous définissez. Des alertes ne peuvent être définies que sur des vignettes épinglées à partir de visuels de rapport, et uniquement sur des jauges, des indicateurs de performance clés et des cartes. 

![vignette, carte, indicateur de performance clé](media/end-user-alerts/card-gauge-kpi.png)

Les alertes peuvent être créées dans les tableaux de bord :
- que vous avez créé et enregistré dans **Mon espace de travail**
- qui ont été partagés avec vous dans une [capacité Premium](end-user-license.md). 
- dans n’importe quel espace de travail auquel vous pouvez accéder si vous disposez d’une licence Power BI Pro.    

Les alertes fonctionnent uniquement sur les données actualisées Lorsque les données sont actualisées, Power BI vérifie si une alerte est définie pour celles-ci. Si les données ont atteint un seuil d’alerte, une alerte est déclenchée. 

Cette fonctionnalité étant toujours en cours d’évolution, reportez-vous à la [section Conseils et résolution des problèmes ci-dessous](#tips-and-troubleshooting).



Vous seul pouvez voir les alertes que vous définissez, même si vous partagez votre tableau de bord. Les alertes de données sont entièrement synchronisées entre plateformes. Définissez et affichez les alertes de données [dans les applications mobiles Power BI](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) et dans le service Power BI. 

> [!WARNING]
> Ces alertes fournissent des informations sur vos données. Si vous affichez vos données Power BI sur un appareil mobile et que celui-ci est volé, nous vous recommandons d’utiliser le service Power BI pour désactiver toutes les alertes.
> 

Ce tutoriel couvre les points suivants.
> [!div class="checklist"]
> * Qui peut définir des alertes
> * Quels visuels sont pris en charge par les alertes
> * Qui peut voir mes alertes
> * Les alertes fonctionnent-elles sur Power BI Desktop et sur Power BI Mobile
> * Comment créer une alerte
> * Où vais-je recevoir mes alertes

## <a name="prerequisites"></a>Prérequis

Si vous n’êtes pas inscrit à Power BI, [inscrivez-vous à un essai gratuit](https://app.powerbi.com/signupredirect?pbi_source=web) avant de commencer.

1. Cet exemple utilise une mosaïque de cartes de tableau de bord provenant de l’échantillon Ventes et Marketing. Ouvrez le service Power BI (app.powerbi.com), connectez-vous, puis ouvrez **Mon espace de travail**.    
    ![Ouvrir Mon espace de travail](media//end-user-alerts/power-bi-my-workspace.png)

2. Dans le coin inférieur gauche, sélectionnez **Obtenir des données**.

    ![Sélectionner Obtenir les données](media//end-user-alerts/power-bi-get-data.png)

3. Dans la page Obtenir des données qui s’affiche, sélectionnez **Échantillons**.

4. Sélectionnez l’échantillon Ventes et Marketing, puis choisissez **Se connecter**.

    ![Télécharger l’échantillon Ventes et Marketing](media//end-user-alerts/power-bi-sample.png)

5. Une fois que Power BI est connecté à l’échantillon, sélectionnez **Accéder au tableau de bord** dans la boîte de dialogue qui s’affiche.     
    ![Ouvrir l’échantillon Ventes et Marketing](media//end-user-alerts/power-bi-go-to-dashboard.png)

## <a name="add-an-alert-to-a-dashboard-tile"></a>Ajouter une alerte à une mosaïque de tableaux de bord

1. Dans une jauge, un indicateur de performance clé ou une vignette de carte du tableau de bord, sélectionnez les points de suspension.
   
   ![vignette de carte](media/end-user-alerts/power-bi-card.png)

2. Sélectionnez l’icône d’alerte ![Icône d’alerte](media/end-user-alerts/power-bi-alert-icon.png) ou **Gérer les alertes** pour ajouter une ou plusieurs alertes pour la carte **Part de marché**.

   ![vignette de carte avec les points de suspension sélectionnés](media/end-user-alerts/power-bi-manage.png)

   
1. Dans le volet **Gérer les alertes**, sélectionnez **+ Ajouter une règle d’alerte**.  Vérifiez que le curseur est défini sur **Activé** et donnez un titre à votre alerte. Les titres vous aident à reconnaître facilement vos alertes.
   
   ![Fenêtre Ajouter une règle d’alerte](media/end-user-alerts/power-bi-alert-manage.png)
4. Faites défiler vers le bas, puis entrez les détails de l’alerte.  Dans cet exemple, nous allons créer une alerte qui nous avertit une fois par jour de l’augmentation de notre part de marché à 40 ou plus. Les alertes s’affichent dans notre [Centre de notification](end-user-notification-center.md). Nous allons également demander à Power BI de nous envoyer un courrier électronique.
   
   ![Fenêtre Gérer les alertes, Seuil défini](media/end-user-alerts/power-bi-manage-alert-detail.png)

5. Sélectionnez **Enregistrer et fermer**.
 


   > 

## <a name="receiving-alerts"></a>Recevoir des alertes
Quand les données suivies atteignent un des seuils définis, plusieurs choses se produisent. Power BI vérifie d’abord si cela fait plus d’une heure ou plus de 24 heures (selon l’option sélectionnée) que la dernière alerte a été envoyée. Tant que les données se trouvent au-delà du seuil, vous recevez une alerte.

Ensuite, Power BI envoie une alerte à votre Centre de notifications et éventuellement par e-mail. Chaque alerte contient un lien direct vers vos données. Sélectionnez le lien pour afficher la vignette appropriée.  

1. Si vous avez défini l’alerte de façon à recevoir un courrier électronique, vous recevez un message semblable à celui-ci dans votre boîte de réception. Il s’agit d’une alerte que nous avons définie pour la carte **Sentiment**.
   
   ![E-mail d’alerte](media/end-user-alerts/power-bi-email.png)
2. Power BI ajoute également un message à votre **Centre de notification**.
   
   ![icône Notification dans le service Power BI](media/end-user-alerts/power-bi-task.png)
3. Ouvrez le centre de notification pour afficher les détails de l’alerte.
   
    ![lire l’alerte](media/end-user-alerts/power-bi-notifications.png)
   
  

## <a name="managing-alerts"></a>Gestion des alertes

Il existe de nombreuses façons de gérer vos alertes : à partir de la mosaïque de tableaux de bord elle-même, dans le menu Paramètres Power BI et sur une mosaïque individuelle dans l’[application mobile Power BI sur iPhone](mobile/mobile-set-data-alerts-in-the-mobile-apps.md) ou dans l’[application mobile Power BI pour Windows 10](mobile/mobile-set-data-alerts-in-the-mobile-apps.md).

### <a name="from-the-tile-itself"></a>À partir de la vignette elle-même

1. Si vous devez modifier ou supprimer une alerte pour une mosaïque, rouvrez la fenêtre **Gérer les alertes** en sélectionnant l’icône d’alerte ![Icône d’alerte](media/end-user-alerts/power-bi-alert-icon.png). Toutes les alertes que vous avez définies pour cette vignette sont affichées.
   
    ![Fenêtre Gérer les alertes](media/end-user-alerts/power-bi-manage-alert.png).
2. Pour modifier une alerte, sélectionnez la flèche à gauche du nom de l’alerte.
   
    ![flèche à côté du nom de l’alerte](media/end-user-alerts/power-bi-alert-modify.png).
3. Pour supprimer une alerte, sélectionnez la poubelle à droite du nom de l’alerte.
   
      ![icône de corbeille sélectionnée](media/end-user-alerts/power-bi-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Dans le menu Paramètres de Power BI

1. Sélectionnez l’icône en forme d’engrenage dans la barre de menus de Power BI.
   
    ![icône d’engrenage](media/end-user-alerts/power-bi-gear-icon.png).
2. Sous **Paramètres**, sélectionnez **Alertes**.
   
    ![onglet Alertes de la fenêtre Paramètres](media/end-user-alerts/power-bi-settings.png)
3. À ce stade, vous pouvez activer et désactiver les alertes, ouvrir la fenêtre **Gérer les alertes** pour apporter des modifications ou supprimer l’alerte.

## <a name="tips-and-troubleshooting"></a>Conseils et résolution des problèmes 

* Si vous ne parvenez pas à définir une alerte pour une jauge, un indicateur de performance clé ou une carte, contactez votre administrateur Power BI ou le support technique informatique pour obtenir de l’aide. Des alertes sont parfois désactivées ou indisponibles pour votre tableau de bord ou pour des types spécifiques de vignettes de tableau de bord.
* Les alertes fonctionnent uniquement sur les données actualisées (pas sur les données statiques). La plupart des exemples fournis par Microsoft sont statiques. 
* Une licence Power BI Pro ou Premium est nécessaire pour recevoir et afficher du contenu partagé. Pour plus d’informations, consultez [Quelle est ma licence ?](end-user-license.md).
* Des alertes peuvent être définies sur des visuels créés à partir de jeux de données de streaming que vous épinglez d’un rapport vers un tableau de bord. Vous ne pouvez pas définir d’alertes sur des vignettes de streaming créées directement sur le tableau de bord à l’aide de **Ajouter une vignette** > **Données de streaming personnalisées**.


## <a name="clean-up-resources"></a>Nettoyer les ressources
Les instructions pour la suppression des alertes sont expliquées ci-dessus. En résumé, sélectionnez l’icône d’engrenage dans la barre de menus de Power BI. Sous **Paramètres**, sélectionnez **Alertes** et supprimez l’alerte.

> [!div class="nextstepaction"]
> [Définir des alertes de données sur votre appareil mobile](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


