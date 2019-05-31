---
title: Incorporer des rapports ou des tableaux de bord à partir d’applications
description: Découvrez comment intégrer ou incorporer un rapport ou un tableau de bord à partir d’une application Power BI, et non à partir d’un espace de travail d’application.
author: rkarlin
ms.author: rkarlin
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
manager: kfile
ms.date: 11/27/2018
ms.openlocfilehash: 7db8c465652926caae46c25197bd135833f8e628
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61374720"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Incorporer des rapports ou des tableaux de bord à partir d’applications

Dans Power BI, vous pouvez créer des applications pour regrouper les rapports et tableaux de bord associés dans un même emplacement. Ensuite, vous les publiez pour des grands groupes de personnes dans votre organisation. L’utilisation de ces applications est appropriée quand tous vos utilisateurs sont des utilisateurs Power BI. En effet, vous pouvez partager du contenu avec eux à l’aide d’applications Power BI. Cet article vous donne quelques étapes rapides pour incorporer du contenu d’une application Power BI publiée dans une application tierce.

## <a name="grab-a-report-embedurl-for-embedding"></a>Prendre une URL d’incorporation de rapport pour l’incorporation

1. Instanciez l’application dans un espace de travail utilisateur, **Mon espace de travail**. Partagez avec vous-même ou guidez un autre utilisateur dans cette procédure.

2. Ouvrez le rapport que vous voulez dans le service Power BI.

3. Accédez à **Fichier** > **Incorporer dans SharePoint Online** et prenez l’URL d’incorporation de rapport. La capture d’écran ci-après illustre un exemple d’URL d’incorporation. Ou vous pouvez appeler l’API REST GetReports/GetReport et extrayez de la réponse le champ d’URL d’incorporation de rapport correspondant. L’appel REST ne doit pas avoir d’identificateur d’espace de travail dans l’URL, car l’application a été instanciée dans l’espace de travail utilisateur.

    ![Incorporer à partir d’applications](media/embed-from-apps/embed-from-app.png)

4. Utilisez l’URL d’incorporation récupérée à l’étape 3 avec le kit SDK JavaScript.

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
