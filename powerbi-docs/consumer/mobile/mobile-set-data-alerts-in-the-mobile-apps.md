---
title: Définir des alertes de données dans les applications mobiles Power BI
description: Apprenez à définir des alertes dans les applications mobiles Power BI pour être informé quand les données d’un tableau de bord changent au-delà des limites que vous avez définies.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/11/2019
ms.author: painbar
ms.openlocfilehash: 6cddfd820da45de6141b698b8cb6e3c2bfc68069
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264896"
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Définir des alertes de données dans les applications mobiles Power BI
S’applique à :

| ![iPhone](./media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](./media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Téléphone Android](./media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Tablette Android](./media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Tablette Android](./media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Téléphones Android |Tablettes Android |Appareils Windows 10 |

Vous pouvez définir des alertes sur des tableaux de bord dans le service Power BI et les applications mobiles Power BI. Des alertes vous avertissent quand des données d’une vignette changent au-delà des limites que vous définissez. Les alertes fonctionnent pour les vignettes présentant un seul nombre, telles les cartes et les jauges, pas avec des données de streaming. Vous pouvez définir des alertes de données sur votre appareil mobile et les afficher dans le service Power BI et inversement. Vous seul pouvez voir les alertes de données que vous définissez, même si vous partagez un tableau de bord ou une capture instantanée de vignette.

Vous pouvez définir des alertes sur les vignettes si vous avez une licence Power BI Pro ou si le tableau de bord partagé se trouve dans une capacité Premium. 

> [!WARNING]
> Les notifications d’alerte pilotées par les données fournissent des informations sur vos données. Si votre appareil est volé, nous vous recommandons d’accéder au service Power BI pour désactiver toutes les règles d’alerte pilotées par les données. 
> 
> En savoir plus sur la [gestion des alertes de données dans le service Power BI](../../create-reports/service-set-data-alerts.md).
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>Alertes de données sur un iPhone ou iPad
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>Définir une alerte sur un iPhone ou iPad
1. Appuyez sur une vignette numérique ou de jauge dans le tableau de bord pour l’ouvrir en mode focus.  
   
   ![Capture d’écran d’un tableau de bord, montrant la vignette de jauge en mode Focus.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. Appuyez sur l’icône en forme de cloche ![l’icône en forme de cloche](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png) pour ajouter une alerte.  
3. Appuyez sur **Ajouter une règle d’alerte**.
   
   ![Capture d’écran de la règle d’alerte, indiquant qu’aucune alerte n’est définie.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. Choisissez de recevoir des alertes au-dessus ou en dessous d’une valeur et définissez la valeur en question.
   
   ![Capture d’écran des paramètres d’alerte, indiquant le titre et la valeur de l’alerte à définir.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. Indiquez si vous souhaitez recevoir des alertes toutes les heures ou quotidiennement et si vous voulez recevoir un courrier électronique quand vous recevez l’alerte.
   
   > [!NOTE]
   > Vous ne recevez pas d’alertes toutes les heures ou tous les jours, sauf si les données ont été réellement actualisées pendant la période en question.
   > 
   > 
6. Vous pouvez également modifier le titre de l’alerte.
7. Appuyez sur **Enregistrer**.
8. Une seule vignette peut avoir des alertes pour les valeurs à la fois au-dessus et en dessous des seuils. Dans **Gérer les alertes**, appuyez sur **Ajouter un règle d’alerte**.
   
   ![Capture d’écran de l’option Gérer l’alerte, présentant une flèche vers l’option qui permet d’ajouter une règle d’alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>Gérer les alertes sur votre iPhone ou iPad
Vous pouvez gérer des alertes spécifiques sur votre appareil mobile ou [gérer toutes les alertes dans le service Power BI](../../create-reports/service-set-data-alerts.md).

1. Dans un tableau de bord, appuyez sur une vignette numérique ou de jauge associée à une alerte.  
   
   ![Capture d’écran du tableau de bord, montrant la vignette numérique qui a une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual_has_alert.png)

2. Appuyez sur l’icône en forme de cloche ![l’icône en forme de cloche](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png).  
3. Appuyez sur le nom de l’alerte pour la modifier, appuyez sur le curseur pour désactiver les alertes par courrier électronique ou sur la poubelle pour supprimer l’alerte.
   
    ![Capture d’écran d’une alerte, avec des flèches pointant vers le nom de l’alerte, l’icône de la poubelle pour supprimer l’alerte et le curseur de désactivation de l’alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Alertes de données sur un appareil Android
### <a name="set-an-alert-on-an-android-device"></a>Définir une alerte sur un appareil Android
1. Dans le tableau de bord Power BI, appuyez sur une vignette numérique ou de jauge pour l’ouvrir.  
2. Appuyez sur l’icône en forme de cloche ![l’icône en forme de cloche](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png) pour ajouter une alerte.  
   
   ![Capture d’écran du tableau de bord, montrant la vignette numérique qui a une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. Appuyez sur l’icône plus (+).
   
   ![Capture de l’écran Gérer les alertes, présentant une flèche vers l’icône plus.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. Choisissez de recevoir des alertes au-dessus ou en dessous d’une valeur et entrez la valeur en question.
   
   ![Capture d’écran de la définition de l’alerte, présentant des flèches vers Enregistrer et Terminé.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. Appuyez sur **Terminé**.
6. Indiquez si vous souhaitez recevoir des alertes toutes les heures ou quotidiennement et si vous voulez recevoir un courrier électronique quand vous recevez l’alerte.
   
   > [!NOTE]
   > Vous ne recevez pas d’alertes toutes les heures ou tous les jours, sauf si les données ont été réellement actualisées pendant la période en question.
   > 
   > 
7. Vous pouvez également modifier le titre de l’alerte.
8. Appuyez sur **Enregistrer**.

### <a name="manage-alerts-on-an-android-device"></a>Gérer les alertes sur un appareil Android
Vous pouvez gérer des alertes spécifiques dans l’application mobile Power BI ou [gérer toutes les alertes dans le service Power BI](../../create-reports/service-set-data-alerts.md).

1. Dans un tableau de bord, appuyez sur une vignette de carte ou de jauge associée à une alerte.  
2. Appuyez sur l’icône en forme de cloche ![l’icône en forme de cloche](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png).  
3. Appuyez sur l’alerte pour modifier une valeur ou la désactiver.
   
    ![Capture d’écran de la vignette Gérer l’alerte, montrant l’icône plus pour ajouter une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. Appuyez sur l’icône plus (+) pour ajouter une autre alerte à la même vignette.
5. Pour supprimer complètement l’alerte, appuyez sur l’icône de la poubelle ![Icône de la poubelle](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Alertes de données sur un appareil Windows

>[!NOTE]
>La prise en charge des applications mobiles Power BI pour les **téléphones utilisant Windows 10 Mobile** ne sera plus disponible après le 16 mars 2021. [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2121400)

### <a name="set-data-alerts-on-a-windows-device"></a>Définir des alertes de données sur un appareil Windows
1. Appuyez sur une vignette numérique ou de jauge dans le tableau de bord pour l’ouvrir.  
2. Appuyez sur l’icône en forme de cloche ![l’icône en forme de cloche](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png) pour ajouter une alerte.  
   
   ![Capture d’écran du tableau de bord, montrant la vignette numérique qui a une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. Appuyez sur l’icône plus (+).
   
   ![Capture d’écran de la vignette Gérer les alertes, montrant qu’aucune alerte n’est définie.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. Choisissez de recevoir des alertes au-dessus ou en dessous d’une valeur et entrez la valeur en question.
   
   ![Capture d’écran des paramètres de l’alerte, indiquant les entrées permettant de modifier l’alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. Indiquez si vous souhaitez recevoir des alertes toutes les heures ou quotidiennement et si vous voulez recevoir un courrier électronique quand vous recevez l’alerte.
   
   > [!NOTE]
   > Vous ne recevez pas d’alertes toutes les heures ou tous les jours, sauf si les données ont été réellement actualisées pendant la période en question.
   > 
   > 
6. Vous pouvez également modifier le titre de l’alerte.
7. Appuyez sur la coche.
8. Une seule vignette peut avoir des alertes pour les valeurs à la fois au-dessus et en dessous des seuils. Dans **Gérer les alertes**, appuyez sur le signe plus (+).
   
   ![Capture d’écran de la vignette Gérer les alertes, montrant l’icône plus qui permet d’ajouter une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Gérer les alertes sur un appareil Windows
Vous pouvez gérer des alertes spécifiques dans l’application mobile Power BI ou [gérer toutes les alertes dans le service Power BI](../../create-reports/service-set-data-alerts.md).

1. Dans un tableau de bord, appuyez sur une vignette de carte ou de jauge associée à une alerte.  
2. Appuyez sur l’icône en forme de cloche ![l’icône en forme de cloche](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png).  
   
   ![Capture d’écran du tableau de bord, montrant la vignette numérique qui a une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. Appuyez sur l’alerte pour modifier une valeur ou la désactiver.
   
    ![Capture d’écran de la vignette Gérer les alertes, montrant l’icône plus qui permet d’ajouter une alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. Pour supprimer complètement l’alerte, cliquez avec le bouton droit ou appuyez de façon prolongée sur **Supprimer**.

## <a name="receiving-alerts"></a>Recevoir des alertes
Vous recevez des alertes dans le [centre de notification](mobile-apps-notification-center.md) Power BI de votre appareil mobile ou dans le service Power BI, ainsi que des notifications concernant les nouveaux tableaux de bord qu’un utilisateur a partagés avec vous.

Les sources de données sont souvent configurées pour être actualisées tous les jours, même s’il est possible d’augmenter la fréquence. Lorsque les données du tableau de bord sont actualisées, si les données suivies atteignent un des seuils définis, cela a plusieurs conséquences.

1. Power BI vérifie si cela fait plus d’une heure ou plus de 24 heures (selon l’option sélectionnée) que la dernière alerte a été envoyée.
   
   Tant que les données se trouvent au-delà du seuil, vous recevez une alerte toutes les heures ou toutes les 24 heures.
2. Si vous avez défini l’alerte de façon à recevoir un courrier électronique, vous recevez un message semblable à celui-ci dans votre boîte de réception.
   
   ![Capture d’écran d’une notification par e-mail, montrant l’alerte.](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. Power BI ajoute un message à votre [Centre de notification](mobile-apps-notification-center.md) et ajoute un point jaune à l’icône représentant une cloche ![icône représentant une cloche](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png) sur la barre de titre (iOS et Android) ou au bouton de navigation globale ![bouton de navigation globale](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) (appareils Windows 10).


4. Appuyez sur l’icône représentant une cloche ![icône représentant une cloche](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png) ou sur le bouton de navigation globale ![bouton de navigation globale](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) pour [ouvrir votre **Centre de notifications**](mobile-apps-notification-center.md) et consulter les détails de l’alerte.
   
     

> [!NOTE]
> Les alertes fonctionnent uniquement sur les données actualisées Lorsque les données sont actualisées, Power BI vérifie si une alerte est définie pour celles-ci. Si les données ont atteint un seuil d’alerte, une alerte est déclenchée.
> 
> 

## <a name="tips-and-troubleshooting"></a>Conseils et résolution des problèmes
* Les alertes ne sont pas actuellement prises en charge pour les vignettes Bing ou les vignettes de carte avec des mesures au format date/heure.
* Les alertes fonctionnent uniquement avec des données numériques.
* Les alertes fonctionnent uniquement sur les données actualisées (pas sur les données statiques).
* Les alertes ne fonctionnent pas avec des vignettes contenant des données de streaming.

## <a name="next-steps"></a>Étapes suivantes
* [Gérer les alertes dans le service Power BI](../../create-reports/service-set-data-alerts.md)
* [Centre de notification mobile Power BI](mobile-apps-notification-center.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
