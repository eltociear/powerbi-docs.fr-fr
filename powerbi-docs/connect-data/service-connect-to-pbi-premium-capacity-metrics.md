---
title: Se connecter à Métriques de capacité Power BI Premium
description: Découvrez comment obtenir et installer l’application modèle Métriques de capacité Power BI Premium, et comment se connecter aux données.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/18/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 612c54a201c947309394c442ba8b8ec1ed567879
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85229943"
---
# <a name="connect-to-power-bi-premium-capacity-metrics"></a>Se connecter à Métriques de capacité Power BI Premium
La supervision de vos capacités est essentielle pour prendre des décisions avisées sur la meilleure utilisation de vos ressources de capacité Premium. L’application Métriques de capacité Power BI Premium fournit des informations très détaillées sur le fonctionnement de vos capacités.

![Rapport de l’application Métriques de capacité Power BI Premium](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-report.png)

Cet article vous explique comment installer l’application et comment se connecter aux sources de données. Pour plus d’informations sur le contenu du rapport et sur son utilisation, consultez [Superviser les capacités Premium avec l’application](../service-admin-premium-monitor-capacity.md) et le [billet de blog sur l’application Métriques de capacité Premium](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/).

Après avoir installé l’application et établi la connexion aux sources de données, vous pouvez personnaliser le rapport selon vos besoins. Vous pouvez ensuite le distribuer à des collègues au sein de votre organisation.

> [!NOTE]
> L’installation d’applications modèles nécessite des [autorisations](./service-template-apps-install-distribute.md#prerequisites). Si vous ne disposez pas des autorisations suffisantes, contactez l’administrateur de votre locataire.

## <a name="install-the-app"></a>Installer l’application

1. Cliquez sur le lien suivant pour accéder à l’application : [Application modèle Métriques de capacité Power BI Premium](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Dans la page AppSource de l’application, sélectionnez [**OBTENIR MAINTENANT**](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt).

    [![Application Métriques de capacité Power BI Premium dans AppSource](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Sélectionnez **Installer**. 

    ![Installer l’application Métriques de capacité Power BI Premium](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metric-select-install.png)

    > [!NOTE]
    > Si vous avez installé l’application précédemment, vous êtes invité à indiquer si vous voulez [remplacer cette installation](./service-template-apps-install-distribute.md#update-a-template-app) ou l’installer dans un nouvel espace de travail.

    Une fois l’application installée, elle apparaît dans votre page Applications.

   ![Application Métriques de capacité Power BI Premium dans la page Application](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Se connecter à la source de données

1. Sélectionnez l’icône dans votre page Applications pour ouvrir l’application.

1. Dans l’écran de démarrage, sélectionnez **Explorer**.

   ![Écran de démarrage de l’application modèle](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-splash-screen.png)

   L’application s’ouvre et présente des exemples de données.

1. Sélectionnez le lien **Connecter vos données** dans la bannière en haut de la page.

   ![Lien Application Métriques de capacité Power BI Premium - Connecter vos données](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-connect-data.png)

1. Dans la boîte de dialogue qui s’affiche, définissez le décalage UTC, c’est-à-dire la différence en heures entre l’heure UTC et l’heure de l’endroit où vous êtes. Cliquez ensuite sur **Next**.
  
   ![Application Métriques de capacité Power BI Premium - Boîte de dialogue de définition de l’heure UTC](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-setutc-dialog.png)

1. Dans la boîte de dialogue suivante qui apparaît, vous n’avez rien à faire. Sélectionnez simplement **Se connecter**.

   ![Application Métriques de capacité Power BI Premium - Boîte de dialogue Authentification](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-authentication-dialog.png)

1. Dans l’écran de connexion Microsoft, connectez-vous à Power BI.

   ![Écran de connexion Microsoft](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-microsoft-login.png)

   Une fois que vous êtes connecté, le rapport se connecte aux sources de données et est renseigné avec les dernières données disponibles. Pendant ce temps, le moniteur d’activité tourne.

   ![Application Métriques de capacité Power BI Premium - Actualisation en cours](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-refresh-monitor.png)

   Les données de votre rapport sont actualisées automatiquement une fois par jour, sauf si vous avez désactivé cela lors du processus de connexion. Vous pouvez également [configurer votre propre planification de l’actualisation](./refresh-scheduled-refresh.md) pour mettre à jour les données du rapport comme vous le souhaitez.

## <a name="customize-and-share"></a>Personnaliser et partager

Pour commencer à personnaliser l’application, cliquez sur l’icône de crayon dans le coin supérieur droit.

 ![Écran de connexion Microsoft](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-customize.png)

Pour plus d’informations, consultez [Personnaliser et partager l’application](./service-template-apps-install-distribute.md#customize-and-share-the-app).

## <a name="next-steps"></a>Étapes suivantes
* [Superviser les capacités Premium avec l’application](../admin/service-admin-premium-monitor-capacity.md)
* [Billet de blog sur l’application Métriques de capacité Premium](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/)
* [Que sont les applications modèles Power BI ?](./service-template-apps-overview.md)
* [Installer et distribuer des applications modèles dans votre organisation](./service-template-apps-install-distribute.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)