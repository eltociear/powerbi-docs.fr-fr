---
title: Clients Office 365 dédiés - Problèmes connus
description: Prise en charge des clients Office 365 dédiés - problèmes connus. Cette rubrique décrit les problèmes propres à un client Office 365 dédié. Cela inclut les limitations de la fonctionnalité de groupe, ainsi que l’application iPhone avec les domaines personnels.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a5a9d080205e5f6a047ed820b8b5ed70fa9017d2
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699978"
---
# <a name="office-365-dedicated-customers---known-issues"></a>Clients Office 365 dédiés - Problèmes connus
Power BI est maintenant pris en charge pour les clients Office 365 dédiés.  Si vous êtes un client O365 dédié, vous pouvez vous connecter avec un compte de ce client et utiliser Power BI. Il existe actuellement deux problèmes connus.

## <a name="groups"></a>Groupes
Lorsque vous sélectionnez **Membres** ou **Calendrier** dans le menu contextuel du groupe, vous êtes redirigé vers l’application de messagerie.  **Fichiers** et **Conversations** fonctionnent comme prévu.

![Regrouper à partir de Power BI](media/service-admin-office-365-dedicated-known-issues/group-menu.png)

## <a name="iphone-app---sign-in-with-vanity-domain-leads-to-error"></a>Application iPhone : la connexion avec un domaine personnel génère une erreur
Quand vous vous connectez dans l’application iPhone à l’aide d’une connexion avec un domaine personnel, une erreur peut se produire.

*Erreur de connexion*  
*Une erreur interne inattendue s’est produite. Veuillez réessayer.*

Pour contourner ce problème, connectez-vous avec l’adresse de messagerie répertoriée quand vous cliquez sur l’icône de l’utilisateur dans le service Power BI plutôt qu’avec le domaine personnel.

![E-mail de connexion](media/service-admin-office-365-dedicated-known-issues/sign-in-address.png)

D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

