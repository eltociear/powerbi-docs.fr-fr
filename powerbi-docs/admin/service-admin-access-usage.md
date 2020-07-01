---
title: Trouver les utilisateurs Power BI qui se sont connectés
description: Si vous êtes administrateur de locataire et que vous voulez voir quels utilisateurs se sont connectés à Power BI, vous pouvez utiliser les rapports d’accès et d’utilisation Azure Active Directory pour une meilleure visibilité.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 4f9b69e863b71fda0cece06df7065740bd55463e
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228890"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Trouver les utilisateurs Power BI qui se sont connectés

Si vous êtes administrateur de locataire et que vous voulez voir quels utilisateurs se sont connectés à Power BI, utilisez les [rapports d’accès et d’utilisation Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) pour une meilleure visibilité.

> [!NOTE]
> Le rapport **Connexions** fournit des informations utiles, mais n’indique pas le type de licence dont dispose chaque utilisateur. Utilisez le Centre d’administration Microsoft 365 pour voir les licences.

## <a name="requirements"></a>Conditions requises

Tous les utilisateurs (y compris ceux qui ne sont pas administrateurs) peuvent voir un rapport de leurs propres connexions, mais pour voir un rapport concernant tous les utilisateurs, vous devez remplir les conditions suivantes.

* Votre locataire doit avoir une licence Azure Active Directory Premium associée.

* Vous devez être dans un des rôles suivants : administrateur général, administrateur de la sécurité ou lecteur sécurité.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Utiliser le portail Azure pour afficher les connexions

Pour afficher l’activité de connexion, procédez comme suit.

1. Dans le **portail Azure**, sélectionnez **Azure Active Directory**.

1. Sous **Surveillance**, sélectionnez **Connexions**.
   
    ![Capture d’écran de l’interface utilisateur d’Azure avec les options Azure Active Directory et Connexions mises en surbrillance.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtrez l’application par **Microsoft Power BI** ou **Power BI Gateway** et sélectionnez **Appliquer**.

    **Microsoft Power BI** filtre l’activité de connexion liée au service, tandis que **Power BI Gateway** filtre l’activité de connexion spécifique à la passerelle de données locale.
   
    ![Capture d’écran du filtre Connexions avec le champ Applications mis en surbrillance.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exporter les données

Vous pouvez [télécharger un rapport de connexion](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) dans deux formats : CSV et JSON.

![Capture d’écran du bouton de téléchargement.](media/service-admin-access-usage/download-sign-in-data-csv.png)

En haut du rapport **Connexions**, sélectionnez **Télécharger**, puis sélectionnez l’une des options suivantes :

* **CSV** pour télécharger un fichier CSV correspondant aux données actuellement filtrées.

* **JSON** pour télécharger un fichier JSON correspondant aux données actuellement filtrées.

## <a name="data-retention"></a>Rétention de données

Les données de connexion sont disponibles pendant une durée maximale de 30 jours. Pour plus d’informations, consultez [Stratégies de rétention de rapport Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Étapes suivantes

[Utilisation de l’audit dans votre organisation](service-admin-auditing.md)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)