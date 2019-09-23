---
title: Clients Office 365 dédiés - Problèmes connus
description: Prise en charge des clients Office 365 dédiés - problèmes connus. Cette rubrique décrit les problèmes propres à un client Office 365 dédié. Cela inclut les limitations de la fonctionnalité de groupe, ainsi que l’application iPhone avec les domaines personnels.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9461609b7ecaa674d3ef4d01482752a78071dbe2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187813"
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

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

