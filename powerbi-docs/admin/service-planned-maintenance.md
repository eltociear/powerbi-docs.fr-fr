---
title: Maintenance planifiée de Power BI
description: Informations destinées aux administrateurs sur l’impact de la maintenance planifiée de Power BI sur leur organisation et les étapes à suivre.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: 13bbf23c075fb1f58c2af71ae0a082d4e539d023
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537685"
---
# <a name="power-bi-planned-maintenance"></a>Maintenance planifiée de Power BI

La maintenance planifiée pour le service Power BI est un aspect indispensable de notre engagement à fournir un produit fiable à nos clients. En cas de maintenance planifiée, le service Power BI n’est pas disponible pour votre organisation pendant un certain temps. Les utilisateurs peuvent ne pas être en mesure d’accéder au service Power BI, et les opérations en arrière-plan peuvent échouer. Après la fenêtre de maintenance, nous nous attendons à ce que le service fonctionne normalement, et à ce que les opérations interactives et en arrière-plan s’exécutent avec succès.  

La maintenance est planifiée en dehors des heures de bureau normales pour réduire l’impact sur votre organisation. Pour les organisations qui ont des utilisateurs dans le monde entier, nous reconnaissons qu’« en dehors des heures de bureau normales » peut avoir une signification différente. Nous vous prions de nous excuser pour tous les désagréments envers vos utilisateurs. Nous travaillons dur pour améliorer Power BI et réduire ces fenêtres de maintenance.

Si votre organisation est affectée, nous vous fournirons une notification préalable. Les administrateurs Microsoft 365 verront un préavis dans le centre de messages Microsoft 365 et recevront un e-mail. En outre, les clients avec des contrats Support Premier seront avertis par l’intermédiaire de leur équipe des comptes Microsoft.

## <a name="actions-to-take-now"></a>Actions à entreprendre maintenant

* Les administrateurs Microsoft 365 doivent [consulter le centre de messages](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) pour tous messages relatifs à la maintenance planifiée de Power BI. Partagez le message avec les personnes qui doivent être informées, mais qui n’ont pas forcément accès au centre de messages.
* Si vous n’êtes pas un administrateur Microsoft 365, contactez votre service informatique ou vos équipes de support en interne pour vous renseigner au sujet de toute maintenance à venir.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Actions à effectuer lorsque la maintenance est terminée

* Les utilisateurs doivent actualiser toutes les fenêtres ouvertes du navigateur.
* Les utilisateurs de l’application mobile Power BI doivent vérifier qu’ils utilisent la version la plus récente et se déconnecter, puis se reconnecter à l’application. Vérifiez la boutique d’applications de votre téléphone ou consultez notre page [Power BI Mobile](https://powerbi.microsoft.com/mobile/).
* Les clients qui modifient ou publient activement des rapports qui utilisent des objets visuels organisationnels, que ce soit localement ou à partir d’emplacements OneDrive et SharePoint, doivent soit réimporter leurs objets visuels via le magasin d’objets visuels organisationnels, soit télécharger un fichier PBIX mis à jour avant de republier. Pour plus d’informations sur les objets visuels organisationnels, consultez [visuels de l’organisation](organizational-visuals.md).
* Si des classeurs Excel qui utilisent la fonctionnalité Analyser dans Excel ne sont pas actualisés, vous devrez peut-être mettre à jour la chaîne de connexion ou retélécharger la connexion ODC pour ce jeu de données. Pour plus d’informations, consultez [Analyser dans Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data).
* Les liens vers Power BI incorporés dans le contenu peuvent ne pas se connecter une fois la maintenance terminée. Par exemple, un lien incorporé dans SharePoint ou Teams peut entraîner une erreur pour l’utilisateur. Pour résoudre ce problème, vous devez régénérer le lien incorporé dans Power BI puis mettre à jour les emplacements où ils sont utilisés. Pour plus d’informations sur les liens incorporés, consultez [Incorporer un composant WebPart Rapport dans SharePoint Online](../collaborate-share/service-embed-report-spo.md) et [Collaborer dans Microsoft Teams avec Power BI](../collaborate-share/service-collaborate-microsoft-teams.md).

## <a name="next-steps"></a>Étapes suivantes

* [Activer les notifications d’interruption de service](service-interruption-notifications.md)
* [Suivre les modifications à venir dans le centre de messages](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide)
