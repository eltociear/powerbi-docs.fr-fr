---
title: "Vue d’ensemble du programme Pack de contenu du service Power BI"
description: Programme de certification du pack de contenu
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/04/2018
ms.author: maghan
ms.openlocfilehash: 1eaa549bf42c17cd2bd857efd4d50b991e862ea0
ms.sourcegitcommit: 25489cf87c31fc107a5337fa1dd36506897c4bbb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Vue d’ensemble du programme Pack de contenu du service Power BI
Un pack de contenu est un ensemble de contenu prêt à l’emploi permettant aux utilisateurs d’obtenir immédiatement des analyses depuis une source. Un pack de contenu se concentre généralement sur un scénario d’entreprise spécifique en fournissant des analyses pour un rôle, un domaine ou un flux de travail.

Les éditeurs de logiciels indépendants peuvent créer des packs de contenu de modèle permettant aux clients de se connecter et d’instancier avec leurs propres comptes. En tant qu’experts de leur domaine, ils peuvent déverrouiller les données d’une façon facilement consommable par les utilisateurs professionnels. Les packs de contenu offrent à vos clients des analyses et la surveillance ad hoc sans avoir à investir lourdement dans une infrastructure de rapports. 

Ces packs de contenu de modèle conçus pour les éditeurs de logiciels indépendants peuvent être envoyés à l’équipe Power BI qui les rendra disponibles publiquement dans la galerie de packs de contenu de Power BI (app.powerbi.com/getdata/services) et sur Microsoft AppSource (appsource.microsoft.com). Vous trouverez un exemple d’expérience de pack de contenu public [ici](template-content-pack-experience.md).

## <a name="overview"></a>Vue d’ensemble
Le processus général de développement et de soumission d’un pack de contenu de modèle implique plusieurs étapes.

 ![Processus](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Passez en revue les exigences](#requirements) et vérifiez que vous pouvez y répondre.
2. [Création de contenu](template-content-pack-authoring.md#queries) dans Power BI Desktop
3. [Création d’un tableau de bord](template-content-pack-authoring.md#dashboard) sur PowerBI.com
4. [Test du pack de contenu](template-content-pack-testing.md) par vous-même au sein de votre organisation
5. [Envoi](template-content-pack-testing.md#submission) du contenu à Power BI pour publication

<a name="requirements"></a>

## <a name="requirements"></a>Configuration requise
Pour créer et envoyer un pack de contenu pour qu’il soit publié dans le service Power BI et sur AppSource, vous devez remplir les conditions suivantes :

* Vous avez une application SaaS utilisée par des utilisateurs en entreprise.
* Votre application SaaS possède des données utilisateur qui peuvent être visualisées dans Power BI.
* Votre application SaaS a une API qui est accessible via le réseau Internet public. Dans l’idéal, l’API est une API REST ou un flux OData. Les packs de contenu Power BI prennent en charge plusieurs types d’authentification tels que l’authentification de base, OAuth 2.0 et Clé API. 
* Votre application SaaS est approuvée et peut publier un pack de contenu. Envoyez votre demande à pbiservicesapps@microsoft.com. Nous allons examiner chaque envoi en nous basant sur sa pertinence et l’utilisation attendue. 
* Accord de partenariat signé. Cette opération a lieu à l’[étape de soumission](template-content-pack-testing.md#submission).

Veuillez consulter la section [création](template-content-pack-authoring.md) pour plus d’informations sur les spécifications techniques.

## <a name="business-scenario"></a>Scénario professionnel
Les packs de contenu offrent des analyses et données sur un scénario professionnel spécifique. Comprendre votre public et les avantages qu’ils tireront du pack de contenu vous aidera à vous assurer que les utilisateurs exploitent avec succès le contenu que vous offrez.

### <a name="tips"></a>Conseils
* Identifiez votre public et la tâche à accomplir  
* Concentrez-vous sur une certaine période de temps (les 90 derniers jours) ou sur les N derniers résultats  
* Importez uniquement les tableaux/colonnes pertinentes pour votre scénario  
* Envisagez d’offrir plusieurs packs de contenu pour des scénarios uniques distincts  

## <a name="frequently-asked-questions"></a>Forum Aux Questions
**Puis-je créer un pack de contenu de service Power BI pour une application SaaS tierce dont je ne suis pas propriétaire ?**

Non. Nous exigeons actuellement la signature d’un accord de partenariat avec le propriétaire de l’application SaaS avant de publier le pack de contenu dans le service.

**Je n’ai pas d’API de développeur publique pour mon service. Puis-je quand même créer un pack de contenu de service Power BI qui extrait les données directement depuis le stockage de données ?**

Non. Les packs de contenu de service Power BI nécessitent une API développeur accessible via le réseau Internet public.

**Quels types d’API sont pris en charge par les packs de contenu de service et avec quels types d’authentification fonctionnent-ils ?**

Les packs de contenu de service Power BI prennent en charge les API REST ou les flux OData. Power BI peut accepter plusieurs types d’authentification tels que l’authentification de base, OAuth 2.0 et Clé d’API web. Pour plus d’informations, consultez la section sur les exigences techniques dans l’article sur la [création](template-content-pack-authoring.md#dashboard).

**J’ai d’autres questions sur les packs de contenu de service. Comment puis-je vous contacter ?**

N’hésitez pas à nous envoyer vos questions par courrier à l’adresse pbiservicesapps@microsoft.com.

## <a name="support"></a>Support technique
Pour de l’aide au cours du développement, veuillez utiliser [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Nous suivons et gérons activement les demandes. Les incidents utilisateur sont rapidement transmis à la bonne équipe.

## <a name="next-step"></a>Étape suivante
[Création](template-content-pack-authoring.md)

