---
title: Installer automatiquement des applications Power BI quand vous incorporez du contenu pour votre organisation
description: Découvrez comment installer automatiquement des applications Power BI lorsque vous incorporez du contenu pour votre organisation.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: c9f9a09d659a047ff7342dd0c90f0effe03ce6a1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417218"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Installer automatiquement des applications Power BI quand vous incorporez du contenu pour votre organisation

Pour incorporer du contenu à partir d’une application, l’utilisateur qui est chargé de l’incorporation doit avoir [accès à l’application](../../collaborate-share/service-create-distribute-apps.md). Si l’application est installée pour l’utilisateur, l’incorporation se fera facilement. Pour plus d’informations, consultez [Incorporer des rapports ou des tableaux de bord à partir d’applications](embed-from-apps.md). Sur PowerBI.com, vous pouvez décider que toutes les applications doivent être [installées automatiquement](https://powerbi.microsoft.com/blog/automatically-install-apps/). Toutefois, cette action sera effectuée au niveau du locataire et s’appliquera à toutes les applications.

## <a name="auto-install-app-on-embedding"></a>Installer automatiquement l’application lors d’une incorporation

Si un utilisateur a accès à une application, mais que celle-ci n’est pas installée, l’incorporation échoue. Afin d’éviter de tels échecs lors de l’incorporation du contenu d’une application, vous pouvez autoriser l’installation automatique de l’application lors de l’incorporation. Dans ce cas, si l’application que tente d’incorporer l’utilisateur n’est pas installée, celle-ci le sera automatiquement. Par conséquent, le contenu de votre choix est incorporé immédiatement, et tout se déroule facilement pour l’utilisateur.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Incorporer pour des utilisateurs Power BI (l’utilisateur est propriétaire des données)

Si vous souhaitez autoriser l’installation automatique des applications pour vos utilisateurs, vous devez attribuer à votre application l’autorisation « Création de contenu » lors de l’[inscription de votre application](register-app.md#register-an-azure-ad-app), ou l’ajouter si vous avez déjà inscrit votre application.

![Inscription de l’application - Création de contenu](media/embed-auto-install-app/register-app-create-content.png)

Ensuite, vous devez fournir l’ID d’application dans l’URL d’incorporation. Pour fournir l’ID d’application, le créateur de l’application doit tout d’abord installer l’application, puis utiliser l’un des appels d’[API REST Power BI](/rest/api/power-bi/) pris en charge : [Obtenir des rapports](/rest/api/power-bi/reports/getreports) ou [Obtenir des tableaux de bord](/rest/api/power-bi/dashboards/getdashboards). Ensuite, le créateur de l’application doit copier l’URL d’incorporation dans la réponse de l’API REST. L’ID d’application s’affiche dans l’URL si le contenu provient d’une application.  Une fois que vous disposez de l’URL d’incorporation, vous pouvez régulièrement l’utiliser pour incorporer du contenu.

## <a name="secure-embed"></a>Sécuriser l’incorporation

Pour utiliser l’installation automatique des applications, le créateur de l’application doit tout d’abord installer l’application, puis accéder à l’application sur PowerBI.com, accéder au rapport, et enfin, obtenir le lien comme il le ferait habituellement. Tous les autres utilisateurs qui ont accès à l’application et qui peuvent utiliser le lien sont en mesure d’incorporer le rapport.

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Vous pouvez uniquement incorporer les rapports et les tableaux de bord de ce scénario.

* Cette fonctionnalité n’est pas prise en charge si l’application est propriétaire des données et si l’incorporation se fait dans SharePoint.