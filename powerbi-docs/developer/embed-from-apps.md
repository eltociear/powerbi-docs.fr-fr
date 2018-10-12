---
title: Incorporer des rapports ou des tableaux de bord à partir d’applications
description: Découvrez comment intégrer ou incorporer un rapport ou un tableau de bord à partir d’une application Power BI, et non à partir d’un espace de travail d’application.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 53803c77dec8eb35c10db7f19a82f58144f88414
ms.sourcegitcommit: b45134887a452f816a97e384f4333db9e1d8b798
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237982"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Incorporer des rapports ou des tableaux de bord à partir d’applications

Dans Power BI, vous pouvez créer des applications pour regrouper les rapports et tableaux de bord associés dans un même emplacement. Ensuite, vous les publiez pour des grands groupes de personnes dans votre organisation. L’utilisation de ces applications est appropriée quand tous vos utilisateurs sont des utilisateurs Power BI. En effet, vous pouvez partager du contenu avec eux à l’aide d’applications Power BI. Cet article vous donne quelques étapes rapides pour incorporer du contenu d’une application Power BI publiée dans une application tierce.

## <a name="grab-a-report-embedurl-for-embedding"></a>Prendre une URL d’incorporation de rapport pour l’incorporation

1. Instanciez l’application dans un espace de travail utilisateur, **Mon espace de travail**. Partagez avec vous-même ou guidez un autre utilisateur dans cette procédure.

2. Ouvrez le rapport que vous voulez dans le service Power BI.

3. Accédez à **Fichier** > **Incorporer dans SharePoint Online** et prenez l’URL d’incorporation de rapport à partir de là. Elle est indiquée dans la capture instantanée suivante. Ou appelez l’API REST GetReports/GetReport et extrayez de la réponse le champ d’URL d’incorporation de rapport correspondant. L’appel REST ne doit pas avoir d’identificateur d’espace de travail dans l’URL, car l’application a été instanciée dans l’espace de travail utilisateur.

4. Utilisez l’URL d’incorporation récupérée à l’étape 3 avec le kit SDK JavaScript.

    ![Incorporer à partir d’applications](media/embed-from-apps/embed-from-app.png)

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Prendre une URL d’incorporation de tableau de bord pour l’incorporation

1. Instanciez l’application dans un espace de travail utilisateur, **Mon espace de travail**. Partagez avec vous-même ou guidez un autre utilisateur dans cette procédure.

2. Appelez l’API REST GetDashboards et extrayez de la réponse le champ d’URL d’incorporation de tableau de bord correspondant. L’appel REST ne doit pas avoir d’identificateur d’espace de travail dans l’URL, car l’application a été instanciée dans l’espace de travail utilisateur.

3. Utilisez l’URL d’incorporation récupérée à l’étape 2 avec le kit SDK JavaScript.

## <a name="next-steps"></a>Étapes suivantes

Examinez comment incorporer à partir d’espaces de travail d’application pour vos clients tiers et votre organisation :

> [!div class="nextstepaction"]
>[Incorporer pour les clients tiers](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Incorporer pour votre organisation](embed-sample-for-your-organization.md)