---
title: Installation automatique des applications Power BI lors de l’incorporation pour votre organisation
description: Découvrez comment auto installer Power BI des applications lors de l’incorporation pour votre organisation.
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376200"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Installer automatiquement les applications Power BI lors de l’incorporation pour votre organisation

Pour incorporer du contenu à partir d’une application, l’utilisateur qui est l’incorporation doit avoir [accès à l’application](../service-create-distribute-apps.md). Si l’application est installée pour l’utilisateur, puis l’incorporation travaille en étroite collaboration. Pour plus d’informations, consultez [incorporer des rapports ou tableaux de bord à partir de l’application](embed-from-apps.md). Il est possible de définir dans PowerBI.com toutes les applications pouvant être [installé automatiquement](https://powerbi.microsoft.com/blog/automatically-install-apps/). Toutefois, cette action est effectuée au niveau du client et s’applique à toutes les applications.

## <a name="auto-install-app-on-embedding"></a>Installer automatiquement l’application sur l’incorporation

Si un utilisateur a accès à une application, mais l’application n’est pas installé, puis l’incorporation échoue. Afin d’éviter ces échecs lors de l’incorporation d’une application, vous pouvez autoriser l’installation automatique de l’application lors de l’incorporation. Cela signifie que si l’application que tente d’incorporer de l’utilisateur n’est pas installée, il est automatiquement installé pour vous. Par conséquent, le contenu que vous voulez est incorporé immédiatement, ce qui entraîne une expérience sans heurts pour l’utilisateur.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Incorporer des utilisateurs de Power BI (utilisateur l'possède les données)

Pour autoriser l’installation automatique des applications pour vos utilisateurs, vous devez donner à votre application l’autorisation « Créer contenu » lorsque [l’inscription de votre application](register-app.md#register-with-the-power-bi-application-registration-tool), ou ajoutez-le si vous déjà inscrit votre application.

![Inscrire l’application crée du contenu](media/embed-auto-install-app/register-app-create-content.png)

Ensuite, vous devez fournir l’ID d’application dans l’URL d’incorporation. Pour fournir l’ID d’application, le créateur de l’application doit tout d’abord installer l’application, puis utilisez une des prises en charge [API Rest Power BI](https://docs.microsoft.com/rest/api/power-bi/) appels - [Get Reports](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) ou [Get Dashboards](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Puis le créateur de l’application doit prendre l’Url d’incorporation de la réponse de l’API REST. L’ID d’application s’affiche dans l’URL si le contenu émane d’une application.  Une fois que vous avez l’URL d’incorporation, vous pouvez l’utiliser pour incorporer régulièrement.

## <a name="secure-embed"></a>Sécuriser les incorporer

Pour utiliser l’installation automatique des applications, le créateur de l’application doit tout d’abord installer l’application, puis accédez à l’application sur PowerBI.com, accédez au rapport, puis obtient le lien de manière habituelle. Tous les autres utilisateurs ayant accès à l’application que vous pouvez utiliser le lien peuvent incorporer le rapport.

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Vous pouvez incorporer uniquement les rapports et tableaux de bord pour ce scénario.

* Cette fonctionnalité est actuellement pas pris en charge l’application possède les données et de scénarios d’incorporation de SharePoint.