---
title: Afficher des rapports et des indicateurs de performance clés locaux dans des applications mobiles Power BI
description: Les applications mobiles Power BI pour iOS vous offrent un accès mobile en direct à vos informations métier locales via une interface tactile dans SQL Server Reporting Services et Power BI Report Server.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/05/2019
ms.author: painbar
ms.openlocfilehash: e9f3b41e9c8435008f732d215ae022d6a023574d
ms.sourcegitcommit: 7e99e8af9caf9340958c4607a94728d43e8c3811
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91668571"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Afficher des indicateurs de performance clés et des rapports Report Server locaux dans des applications mobiles Power BI

Les applications mobiles Power BI vous offrent un accès mobile en direct à vos informations métier locales via une interface tactile dans Power BI Report Server et SQL Server 2016 Reporting Services (SSRS).

S’applique à :

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Téléphone Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Tablette Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhone |iPad |Téléphones Android |Tablettes Android |


![Accueil de Report Server dans les applications mobiles](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Avant tout
**Les applications mobiles sont l’emplacement où vous affichez du contenu Power BI, pas celui où vous le créez.**

* Vous et d’autres créateurs de rapports dans votre organisation [créez des rapports Power BI avec Power BI Desktop, puis les publiez sur le portail web de Power BI Report Server](../../report-server/quickstart-create-powerbi-report.md). 
* Vous pouvez également créer des [indicateurs de performance clés dans le portail web](/sql/reporting-services/working-with-kpis-in-reporting-services), les organiser en dossiers et marquer vos favoris afin de pouvoir les retrouver aisément. 
* [Créez des rapports mobiles Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) avec l’éditeur de rapports mobiles SQL Server 2016 Enterprise Edition et publiez-les sur le [portail web Reporting Services](/sql/reporting-services/web-portal-ssrs-native-mode).  

Ensuite, dans les applications mobiles Power BI, connectez-vous à jusqu’à jusqu’à cinq serveurs de rapports pour afficher les rapports et indicateurs de performance clés Power BI organisés dans des dossiers ou regroupés en favoris. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Explorer des exemples dans les applications mobiles sans connexion au serveur
Même si vous n’avez pas accès à un portail web Reporting Services, vous pouvez toujours explorer les fonctionnalités des rapports mobiles et des indicateurs de performances clés de Reporting Services. 

1. Appuyez sur votre image de profil en haut à gauche, puis sur **Paramètres** dans le volet des comptes qui apparaît.

2. Dans la page des paramètres qui s’ouvre, appuyez sur **Exemples Reporting Services**, puis naviguez pour interagir avec les exemples d’indicateurs de performance clés et de rapports mobiles.
   
   ![Exemples Reporting Services](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Se connecter à un serveur de rapports local
Vous pouvez afficher des rapports Power BI locaux, des rapports mobiles Reporting Services et des indicateurs de performance clés dans les applications mobiles Power BI. 

1. Sur votre appareil mobile, ouvrez l’application Power BI.
2. Si vous n’êtes pas encore connecté à Power BI, appuyez sur **Report Server**.
   
   ![Se connecter à un serveur de rapports](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Si vous êtes déjà connecté à l’application Power BI, appuyez sur votre image de profil en haut à gauche, puis sur **Paramètres** dans le volet des comptes qui apparaît.
3. Dans la page des paramètres qui s’ouvre, appuyez sur **Se connecter au serveur**.
   
    ![Se connecter au serveur](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

    L’application mobile doit accéder au serveur d’une certaine façon. Plusieurs solutions s’offrent à vous :
     * Rester sur le même réseau/utiliser un VPN est le moyen le plus simple.
     * Il est possible d’utiliser un proxy d’application web pour se connecter depuis l’extérieur de l’organisation. Pour plus d’informations, consultez [Utilisation d’OAuth pour la connexion à Reporting Services](mobile-oauth-ssrs.md).
     * Ouvrez une connexion (port) dans le pare-feu.

4. Renseignez l’adresse du serveur et donnez un nom convivial au serveur, si vous le souhaitez. Utilisez ce format pour l’adresse du serveur :
   
     `https://<servername>/reports`
   
     OU
   
     `https://<servername>/reports`
   
   Ajoutez **http** ou **https** devant la chaîne de connexion.
   
    ![Boîte de dialogue Se connecter au serveur](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. Une fois que vous avez tapé l’adresse du serveur et le nom convivial facultatif, appuyez sur **Connecter**, puis entrez votre nom d’utilisateur et votre mot de passe quand vous y êtes invité.
6. À présent, le serveur est visible dans le volet Comptes. Dans cet exemple, il s’appelle « Work server » (Serveur de travail).
   
   ![Serveur de rapports dans le volet de navigation](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios-or-android"></a>Se connecter à un serveur de rapports local dans iOS ou Android

Si vous voyez Power BI dans l’application mobile iOS ou Android, votre administrateur informatique peut avoir défini une stratégie de configuration d’application. Dans ce cas, votre expérience de connexion au serveur de rapports est simplifiée et vous ne devez pas fournir beaucoup d’informations quand vous vous connectez à un serveur de rapports. 

1. Vous voyez un message indiquant que leur application mobile est configurée avec un serveur de rapports. Appuyez sur **Se connecter**.

    ![Se connecter au serveur de rapports](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  Dans la page **Se connecter au serveur**, les détails du serveur de rapports sont déjà renseignés. Appuyez sur **Se connecter**.

    ![Détails du serveur de rapports renseignés](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Tapez un mot de passe pour vous authentifier, puis appuyez sur **Se connecter**. 

    ![Capture d’écran montrant l’entrée de mot de passe avec un bouton de connexion.](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

Vous pouvez désormais afficher et interagir avec les indicateurs de performance clés et les rapports Power BI stockés sur le serveur de rapports.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Afficher les rapports Power BI et les indicateurs de performance clés dans l’application Power BI
Les rapports Power BI, les rapports mobiles Reporting Services et les indicateurs de performance clés sont affichés dans les mêmes dossiers que sur le portail web Reporting Services. 

* Appuyer sur un rapport Power BI ![Icône de rapport Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). Celui-ci s’ouvre en mode paysage et vous pouvez interagir avec lui dans l’application Power BI.

    > [!NOTE]
  > Monter et descendre dans une hiérarchie n’est actuellement pas autorisé dans les rapports Power BI sur un serveur Power BI Report Server.
  
    ![Rapport Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* Dans Power BI Desktop, les propriétaires de rapports peuvent [optimiser un rapport](../../create-reports/desktop-create-phone-report.md) pour les applications mobiles Power BI. Sur votre téléphone mobile, les rapports optimisés ont une icône ![icône de rapport Power BI optimisé](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png) et une disposition spéciales.
  
    ![Rapport Power BI optimisé pour les mobiles](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Appuyez sur un indicateur de performance clé pour l’afficher en mode Focus.
  
    ![Indicateur de performance clé en mode Focus](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Afficher vos rapports et indicateurs de performance clés favoris
Vous pouvez marquer des indicateurs de performance clés et des rapports en tant que favoris sur le portail web, et les afficher ainsi que vos tableaux de bord Power BI favoris dans un seul dossier sur votre appareil.

* Appuyez sur **Favoris** dans la barre de navigation.
  
   ![Favoris dans le volet de navigation](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Vos indicateurs de performance clés et rapports favoris du portail web figurent tous sur cette page, ainsi que les tableaux de bord Power BI du service Power BI :
  
   ![Rapports et tableau de bord Power BI dans la page Favoris](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Supprimez une connexion à un serveur de rapports
1. Ouvrez le volet des comptes, puis appuyez sur **Paramètres**.
2. Appuyez sur le nom du serveur duquel vous souhaitez vous déconnecter.
3. Appuyez sur **Supprimer le serveur**.

## <a name="next-steps"></a>Étapes suivantes
* [Qu’est-ce que Power BI ?](../../fundamentals/power-bi-overview.md)  
* Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)