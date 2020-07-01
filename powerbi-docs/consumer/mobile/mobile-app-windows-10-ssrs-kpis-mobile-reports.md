---
title: Afficher des rapports et des indicateurs de performance clés locaux dans l’application Power BI Windows
description: L’application mobile Power BI pour Windows 10 offre un accès mobile direct aux informations importantes locales de votre entreprise, via une interface tactile.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/19/2020
ms.author: painbar
ms.openlocfilehash: a56fecdadc8eddba3fa755497a4ebc978496b7a1
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231344"
---
# <a name="view-on-premises-reports-and-kpis-in-the-power-bi-windows-app"></a>Afficher des rapports et des indicateurs de performance clés locaux dans l’application Power BI Windows
L’application Power BI pour Windows 10 offre un accès mobile direct aux informations importantes locales de votre entreprise, via une interface tactile dans SQL Server 2016 Reporting Services. 

![Rapports mobiles Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>Avant tout
[Créez des rapports mobiles Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) avec l’éditeur de rapports mobiles SQL Server 2016 Enterprise Edition et publiez-les sur le [portail web Reporting Services](/sql/reporting-services/web-portal-ssrs-native-mode). Créez des indicateurs de performance clés directement dans le portail web. Organisez-les dans des dossiers et marquez vos favoris, afin de les trouver facilement. 

Ensuite, dans l’application Power BI pour Windows 10, vous pouvez afficher les indicateurs de performance clés et les rapports Power BI, organisés dans des dossiers ou regroupés en favoris. 

> [!NOTE]
> Votre appareil doit exécuter Windows 10. L’application fonctionne mieux sur les appareils avec au moins 1 Go de RAM et 8 Go de stockage interne.

>[!NOTE]
>La prise en charge des applications mobiles Power BI pour les **téléphones utilisant Windows 10 Mobile** ne sera plus disponible après le 16 mars 2021. [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Explorer des exemples sans serveur SQL Server 2016 Reporting Services
Même si vous n’avez pas accès à un portail web Reporting Services, vous pouvez toujours explorer les fonctionnalités des rapports mobiles Reporting Services.

1. Sur votre appareil Windows 10, ouvrez l’application Power BI.
2. Appuyez sur le bouton de navigation globale ![Bouton de navigation globale](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) en haut à gauche.
3. Appuyez sur l’icône **Paramètres**![Icône Paramètres](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), cliquez avec le bouton droit ou appuyez longuement sur **Se connecter au serveur**, puis appuyez sur **Afficher des exemples**.
   
   ![Afficher les exemples SSRS](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Ouvrez le dossier Retail Reports ou Sales Reports pour explorer les indicateurs de performance clés et les rapports mobiles.
   
   ![Exemples d’indicateurs de performance clés et de rapports mobiles](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Parcourez les exemples pour interagir avec les indicateurs de performance clés et les rapports mobiles.

## <a name="connect-to-a-reporting-services-report-server"></a>Se connecter à un serveur de rapports Reporting Services
1. En bas du volet de navigation, appuyez sur **Paramètres** ![Icône Paramètres](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png)
2. Appuyez sur **Se connecter au serveur**.
3. Renseignez l’adresse du serveur, ainsi que votre nom d’utilisateur et votre mot de passe. Utilisez ce format pour l’adresse du serveur :
   
     `https://<servername>/reports` OU   `https://<servername>/reports`
   
   > [!NOTE]
   > Ajoutez **http** ou **https** au début de la chaîne de connexion.
   > 
   > 
   
    Appuyez sur **Option avancée** pour affecter un nom au serveur, si vous le souhaitez.
4. Appuyez sur la coche pour vous connecter. 
   
   À présent, le serveur est visible dans le volet de navigation.
   
   ![Serveur dans le volet de navigation](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Appuyez sur le bouton de navigation globale ![bouton de navigation globale](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) à tout moment pour naviguer entre vos rapports mobiles Reporting Services et vos tableaux de bord dans le service Power BI. 
   > 

   >[!NOTE]
   >Les serveurs de rapports configurés avec des ports personnalisés ne sont pas pris en charge et ne sont pas accessibles depuis l’application Windows Power BI. 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Afficher les rapports mobiles et les indicateurs de performance clés Reporting Services dans l’application Power BI
Les indicateurs de performance clés, les rapports mobiles Reporting Services et les rapports Power BI (préversion) sont affichés dans les mêmes dossiers que sur le portail web Reporting Services.

![Dossiers de rapports](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Appuyez sur un indicateur de performance clé pour l’afficher en mode Focus.
  
    ![Indicateur de performance clé en mode Focus](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Appuyez sur un rapport mobile pour l’ouvrir et interagir avec celui-ci dans l’application Power BI.
  
    ![Rapport mobile Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Afficher vos rapports et indicateurs de performance clés favoris
Vous pouvez marquer des indicateurs de performance clés, des rapports mobiles et des rapports Power BI en tant que favoris sur votre portail web Reporting Services, puis les afficher dans un dossier approprié sur votre appareil Windows 10, ainsi que vos tableaux de bord et rapports Power BI favoris.

* Appuyez sur **Favoris**.
  
   ![Icône Favoris](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Vos favoris du portail web se trouvent tous sur cette page.
  
Accédez à des informations supplémentaires sur les [favoris dans les applications mobiles Power BI](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Supprimez une connexion à un serveur de rapports
Vous ne pouvez vous connecter qu’à un seul serveur de rapports à la fois depuis votre application mobile Power BI. Si vous souhaitez vous connecter à un autre serveur, vous devez vous déconnecter du serveur actif.

1. En bas du volet de navigation, appuyez sur **Paramètres** ![Icône Paramètres](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Appuyez sur le nom du serveur auquel vous ne voulez pas être connecté.
3. Appuyez sur **Supprimer le serveur**.
   
    ![Supprimer le serveur](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Créer des rapports mobiles et des indicateurs de performance clés Reporting Services
Vous ne créez pas de rapports mobiles ni d’indicateurs de performance clés Reporting Services dans l’application Power BI. Vous les créez dans l’éditeur de rapports mobiles Microsoft SQL Server et dans un portail web de SQL Server 2016 Reporting Services.

* [Créez vos propres rapports mobiles Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) et publiez-les sur un portail web Reporting Services.
* Créer des [indicateurs de performance clés sur un portail web Reporting Services](/sql/reporting-services/working-with-kpis-in-reporting-services)

## <a name="next-steps"></a>Étapes suivantes
* [Prise en main de l’application mobile Power BI pour Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [Qu’est-ce que Power BI ?](../../fundamentals/power-bi-overview.md)  
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
