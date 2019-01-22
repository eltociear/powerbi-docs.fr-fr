---
title: Trouver les utilisateurs Power BI qui se sont connectés
description: Si vous êtes administrateur de locataire et que vous voulez voir quels utilisateurs se sont connectés à Power BI, vous pouvez utiliser les rapports d’accès et d’utilisation Azure Active Directory pour une meilleure visibilité.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f685a900465cc0f1b635aad7609aaae4356da6b3
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54284630"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Trouver les utilisateurs Power BI qui se sont connectés

Si vous êtes administrateur de locataire et que vous voulez voir quels utilisateurs se sont connectés à Power BI, utilisez les [rapports d’accès et d’utilisation Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) pour une meilleure visibilité.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Ce rapport d’activité fournit des informations utiles, mais n’identifie pas le type de licence dont dispose chaque utilisateur. Utiliser le centre d’administration Office 365 pour afficher des licences.

## <a name="requirements"></a>Configuration requise

Tous les utilisateurs (y compris ceux qui ne sont pas administrateurs) peuvent voir un rapport de leurs propres connexions, mais pour voir un rapport concernant tous les utilisateurs, vous devez remplir les conditions suivantes.

* Votre client doit avoir une licence Azure AD Premium associée.

* Vous devez avoir l’un des rôles suivants : Administrateur général, Administrateur de sécurité ou Lecteur sécurité.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Utiliser le portail Azure pour afficher les connexions

Pour afficher l’activité de connexion, procédez comme suit.

1. Dans le **portail Azure**, sélectionnez **Azure Active Directory**.

1. Sous **Surveillance**, sélectionnez **Connexions**.
   
    ![Connexions Azure AD](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrez l’application par **Microsoft Power BI** ou **Power BI Gateway** et sélectionnez **Appliquer**.

    **Microsoft Power BI** filtre l’activité de connexion liée au service, tandis que **Power BI Gateway** filtre l’activité de connexion spécifique à la passerelle de données locale.
   
    ![Filtrer les connexions](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exporter les données

Vous avez deux options pour exporter les données de connexion : télécharger un fichier csv ou utiliser PowerShell. En haut du rapport de connexion, sélectionnez l’une des options suivantes :

* **Télécharger** pour télécharger un fichier .csv pour les données actuellement filtrées.

* **Script** pour télécharger un script PowerShell pour les données actuellement filtrées. Vous pouvez mettre à jour le filtre dans le script en fonction des besoins.

![Télécharger un fichier .csv ou un script](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Rétention de données

Les données de connexion sont disponibles pendant une durée maximale de 30 jours. Pour plus d’informations, consultez [Stratégies de rétention de rapport Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Étapes suivantes

[Utilisation de l’audit dans votre organisation](service-admin-auditing.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

