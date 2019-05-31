---
title: Trouver les utilisateurs Power BI qui se sont connectés
description: Si vous êtes un administrateur client et que vous souhaitez voir qui s’est connecté à Power BI, vous pouvez utiliser les rapports d’accès et d’utilisation Azure Active Directory pour gagner en visibilité.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906751"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Trouver les utilisateurs Power BI qui se sont connectés

Si vous êtes un administrateur client et que vous souhaitez voir qui a connecté à Power BI, utilisez le [rapports d’accès et d’utilisation Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) de gagner en visibilité.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Le **connexions** rapport fournit des informations utiles, mais elle n’identifie pas le type de licence de chaque utilisateur possède. Utilisez le Centre d’administration Microsoft 365 pour voir les licences.

## <a name="requirements"></a>Configuration requise

Tous les utilisateurs (y compris ceux qui ne sont pas administrateurs) peuvent voir un rapport de leurs propres connexions, mais pour voir un rapport concernant tous les utilisateurs, vous devez remplir les conditions suivantes.

* Votre client doit avoir une licence Azure Active Directory Premium associée.

* Vous devez avoir l’un des rôles suivants : Administrateur général, Administrateur de sécurité ou Lecteur sécurité.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Utiliser le portail Azure pour afficher les connexions

Pour afficher l’activité de connexion, procédez comme suit.

1. Dans le **portail Azure**, sélectionnez **Azure Active Directory**.

1. Sous **Surveillance**, sélectionnez **Connexions**.
   
    ![Capture d’écran de l’interface utilisateur d’Azure avec les options d’Azure Active Directory et des connexions mises en surbrillance.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrez l’application par **Microsoft Power BI** ou **Power BI Gateway** et sélectionnez **Appliquer**.

    **Microsoft Power BI** filtres à l’activité de connexion liées au service, tandis que **Power BI Gateway** filtres à l’activité de connexion spécifique à la passerelle de données sur site.
   
    ![Capture d’écran du filtre de connexions avec le champ d’Applications mis en surbrillance.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exporter les données

Vous pouvez [télécharger un rapport de connexion](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) dans un des deux formats : un fichier CSV ou un fichier JSON.

![Capture d’écran du bouton de téléchargement.](media/service-admin-access-usage/download-sign-in-data-csv.png)

En haut de la **connexions** rapport, sélectionnez **télécharger** puis sélectionnez une des options suivantes :

* **CSV** pour télécharger un fichier CSV pour les données filtrées.

* **JSON** pour télécharger un fichier JSON pour les données filtrées.

## <a name="data-retention"></a>Rétention de données

Les données de connexion sont disponibles pendant une durée maximale de 30 jours. Pour plus d’informations, consultez [stratégies de rétention de rapport Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Étapes suivantes

[Utilisation de l’audit dans votre organisation](service-admin-auditing.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)