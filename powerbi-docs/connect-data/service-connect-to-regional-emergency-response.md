---
title: Se connecter au tableau de bord des réponses aux urgences régionales
description: Comment obtenir et installer le tableau de bord d’aide à la prise de décision dans le contexte du COVID-19 pour le modèle d’application Réponse aux urgences régionales et comment se connecter aux données
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149667"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Se connecter au tableau de bord des réponses aux urgences régionales
Le tableau de bord des réponses aux urgences régionales est le composant de production de rapports de la [solution de réponse aux urgences régionales de Microsoft Power Platform](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Les administrateurs de l’organisation régionale peuvent visualiser le tableau de bord dans leur locataire Power BI, ce qui leur permet de voir rapidement les données et les métriques importantes qui les aideront à prendre des décisions efficaces.

![Rapport de l’application Tableau de bord des réponses aux urgences régionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

Cet article vous explique comment installer l’application Réponse aux urgences régionales en utilisant le modèle d’application Tableau de bord des réponses aux urgences régionales et comment vous connecter aux sources de données.

Pour plus d’informations sur ce qui est présenté dans le tableau de bord, consultez [Obtenir des insights](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

Après avoir installé l’application modèle et établi la connexion aux sources de données, vous pouvez personnaliser le rapport selon vos besoins. Vous pouvez ensuite le distribuer en tant qu’application aux collègues de votre organisation.

## <a name="prerequisites"></a>Prérequis

Avant d’installer ce modèle d’application, vous devez d’abord installer et configurer la [solution Réponse aux urgences régionales](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy). L’installation de cette solution crée les références nécessaires aux sources de données pour renseigner l’application avec des données.

Lors de l’installation de la solution Réponse aux urgences régionales, prenez note de l’[URL de votre instance de l’environnement Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). Vous en aurez besoin pour connecter l’application modèle aux données.

## <a name="install-the-app"></a>Installer l’application

1. Cliquez sur le lien suivant pour accéder à l’application : [Modèle d’application Tableau de bord des réponses aux urgences régionales](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Dans la page AppSource de l’application, sélectionnez [**OBTENIR MAINTENANT**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response).

    [![Application Tableau de bord des réponses aux urgences régionales dans AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Sélectionnez **Installer**. 

    ![Installer l’application Tableau de bord des réponses aux urgences régionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Une fois l’application installée, elle apparaît dans votre page Applications.

   ![Application Tableau de bord des réponses aux urgences régionales dans la page Application](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Se connecter à la source de données

1. Sélectionnez l’icône dans votre page Applications pour ouvrir l’application.

1. Dans l’écran de démarrage, sélectionnez **Explorer**.

   ![Écran de démarrage de l’application modèle](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   L’application s’ouvre et présente des exemples de données.

1. Sélectionnez le lien **Connecter vos données** dans la bannière en haut de la page.

   ![Application Tableau de bord des réponses aux urgences régionales - Lien Connecter vos données](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. Dans la boîte de dialogue qui apparaît, tapez l’[URL de votre instance de l’environnement Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Par exemple : https://[myenv].crm.dynamics.com. Quand vous avez terminé, cliquez sur **Suivant**.

   ![Application Tableau de bord des réponses aux urgences régionales - Boîte de dialogue URL](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. Dans la boîte de dialogue suivante qui s’ouvre, choisissez **OAuth2** comme méthode d’authentification. Ne changez pas le paramètre de niveau de confidentialité.

   Sélectionnez **Connexion**.

   ![Application Tableau de bord des réponses aux urgences régionales - Boîte de dialogue Authentification](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Dans l’écran de connexion Microsoft, connectez-vous à Power BI.

   ![Écran de connexion Microsoft](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Une fois que vous êtes connecté, le rapport se connecte aux sources de données et est renseigné avec les dernières données disponibles. Pendant ce temps, le moniteur d’activité tourne.

   ![Application Tableau de bord des réponses aux urgences régionales - Actualisation en cours](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Planifier l’actualisation du rapport

Une fois l’actualisation des données terminée, [configurez une planification de l’actualisation](../refresh-scheduled-refresh.md) pour tenir les données du rapport à jour.

1. Dans la barre d’en-tête supérieure, sélectionnez **Power BI**.

   ![Navigation Power BI](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. Dans le volet de navigation de gauche, recherchez l’espace de travail Tableau de bord des réponses aux urgences régionales sous **Espaces de travail**, puis suivez les instructions décrites dans l’article [Configurer l’actualisation planifiée](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personnaliser et partager

Pour plus d’informations, consultez [Personnaliser et partager l’application](../service-template-apps-install-distribute.md#customize-and-share-the-app). Veillez à passer en revue les [exclusions de responsabilité du rapport](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) avant de publier ou de distribuer l’application.

## <a name="next-steps"></a>Étapes suivantes
* [Comprendre le tableau de bord des réponses aux urgences régionales](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Configurer et découvrir l’exemple de modèle de communication de crise dans Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
* [Que sont les applications modèles Power BI ?](../service-template-apps-overview.md)
* [Installer et distribuer des applications modèles dans votre organisation](../service-template-apps-install-distribute.md)
