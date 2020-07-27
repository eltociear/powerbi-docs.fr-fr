---
title: Limitations du principal de service
description: Limitations du principal de service
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: 569d7dfe251183962a14de1c42d85ee2e58950af
ms.sourcegitcommit: d8acf2fb0318708a3e8e1e259cb3747b0312b312
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401663"
---
## <a name="considerations-and-limitations"></a>Considérations et limitations

* Un principal de service ne fonctionne qu’avec les [nouveaux espaces de travail](../collaborate-share/service-create-the-new-workspaces.md).
* **Mon espace de travail** n’est pas pris en charge lors de l’utilisation d’un principal de service.
* Une capacité dédiée est nécessaire pour passer en production.
* Vous ne pouvez pas vous connecter au portail Power BI avec un principal de service.
* Vous devez disposer de droits d’administrateur Power BI pour activer un principal de service dans les paramètres du développeur du portail d’administration Power BI.
* Les applications [incorporées pour votre organisation](../developer/embedded/embed-sample-for-your-organization.md) ne peuvent pas utiliser un principal de service.
* La gestion de [flux de données](../transform-model/service-dataflows-overview.md) n’est pas prise en charge.
* Le principal de service ne prend actuellement pas en charge aucune API administrateur.
* Quand vous utilisez un principal de service avec une source de données [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview), le principal de service doit lui-même disposer d’autorisations d’instance Azure Analysis Services. L’utilisation d’un groupe de sécurité qui contient le principal du service à cet effet ne fonctionne pas.
* Le principal de service ne peut pas accéder aux sources de données dans la passerelle. Vous ne pouvez donc pas ajouter le principal de service en tant qu’utilisateur de la source de données dans la passerelle.
