---
title: Rapport des métriques de protection des données
description: Découvrir le rapport des métriques de protection des données
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/16/2020
LocalizationGroup: Data from files
ms.openlocfilehash: a5aa410e6624c5cb50be055533c698afe938f0ef
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412181"
---
# <a name="data-protection-metrics-report"></a>Rapport des métriques de protection des données

## <a name="what-is-the-data-protection-metrics-report"></a>Qu’est-ce que le rapport des métriques de protection des données ?
Le rapport des métriques  de protection des données est un rapport dédié que les [administrateurs Power BI](./service-admin-role.md) peuvent utiliser pour superviser et suivre l’utilisation et l’adoption des étiquettes de sensibilité dans leur locataire.

![Rapport des métriques de protection des données](./media/service-security-data-protection-metrics-report/protection-metrics-seven-days-1.png)
 
Le rapport comprend les éléments suivants :
* Un histogramme empilé 100 % qui montre l’utilisation quotidienne des étiquettes de sensibilité dans le locataire au cours des 7, 30 ou 90 derniers jours. Ce graphique facilite le suivi de l’utilisation relative des différents types d’étiquettes au fil du temps.
* Des graphiques en anneau qui montrent l’état actuel de l’utilisation des étiquettes de sensibilité dans le locataire pour les tableaux de bord, les rapports, les jeux de données et les dataflows.
* Un lien vers le portail Cloud App Security où les alertes Power BI, les utilisateurs à risque, les journaux d’activité et d’autres informations sont disponibles. Pour plus d’informations, consultez [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](./service-security-using-microsoft-cloud-app-security-controls.md).

Le rapport est actualisé toutes les 24 heures.

## <a name="viewing-the-data-protection-metrics-report"></a>Affichage du rapport des métriques de protection des données

Vous devez disposer d’un [rôle d’administrateur Power BI](./service-admin-role.md) pour ouvrir et voir le rapport.
Pour voir le rapport, accédez à **Paramètres > Portail d’administration**, puis choisissez **Métriques de protection**.

![Portail d’administration des mesures de protection](./media/service-security-data-protection-metrics-report/protection-metrics-admin-portal.png)
 
 
La première fois que vous ouvrez le rapport des métriques de protection des données, le chargement peut prendre quelques secondes. Un rapport et un jeu de données intitulés **Métriques de protection des données (générées automatiquement)** seront créés dans votre environnement privé sous « Mon espace de travail ». Nous ne vous recommandons pas de le consulter ici, car il ne s’agit pas du rapport complet. Consultez plutôt le rapport dans le portail d’administration, comme décrit ci-dessus.

> [!CAUTION]
> Ne modifiez pas le rapport ou le jeu de données de quelque manière que ce soit, car de nouvelles versions du rapport sont déployées de temps en temps et les modifications apportées au rapport d’origine seront remplacées si vous mettez à jour vers la nouvelle version.

## <a name="report-updates"></a>Mises à jour du rapport

Des versions améliorées du rapport des métriques de protection des données sont publiées régulièrement. Quand vous ouvrez le rapport, si une nouvelle version est disponible, vous êtes invité à indiquer si vous voulez ouvrir la nouvelle version. Si vous répondez « Oui », la nouvelle version du rapport se charge et remplace l’ancienne version. Toutes les modifications éventuellement apportées à l’ancien rapport et/ou à l’ancien jeu de données seront perdues. Vous pouvez choisir de ne pas ouvrir la nouvelle version, mais dans ce cas, vous ne bénéficiez pas des améliorations de la nouvelle version. 
## <a name="notes-and-considerations"></a>Remarques et considérations
* Pour que le rapport des métriques de protection des données soit généré correctement, la [protection des informations](./service-security-enable-data-sensitivity-labels.md) doit être activée sur votre locataire et [des étiquettes de sensibilité doivent avoir été appliquées](./service-security-apply-data-sensitivity-labels.md). 
* Pour accéder aux informations de Cloud App Security, votre organisation doit disposer de la [licence Cloud App Security](./service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing) appropriée.
* Si vous décidez de partager des informations du rapport des métriques de protection des données avec un utilisateur qui n’est pas administrateur Power BI, n’oubliez pas que ce rapport contient des informations sensibles sur votre organisation.
* Le rapport des métriques de protection des données est un type spécial de rapport et n’apparaît pas dans les listes « Partagé avec moi », « Récents » et « Favoris ».
* Le rapport sur les métriques de protection des données n’est pas disponible pour les [utilisateurs externes (utilisateurs invités Azure Active Directory B2B)](./service-admin-azure-ad-b2b.md).
## <a name="next-steps"></a>Étapes suivantes
* [Étiquettes de sensibilité dans Power BI](./service-security-sensitivity-label-overview.md)
* [Utilisation des contrôles Microsoft Cloud App Security dans Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Présentation du rôle d’administrateur du service Power BI](service-admin-role.md)
* [Activer les étiquettes de sensibilité dans Power BI](service-security-enable-data-sensitivity-labels.md)