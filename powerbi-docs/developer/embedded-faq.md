---
title: "Questions fréquentes sur Power BI Embedded"
description: "Parcourir une liste de questions fréquentes et de réponses sur Power BI Embedded."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 01/15/2018
ms.author: maghan
ms.openlocfilehash: 9d387208b1ace0b0f0fd700b471e07e3b2584883
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Questions fréquentes sur Power BI Embedded

* Si vous avez des questions, [essayez d’interroger la communauté Power BI](http://community.powerbi.com/).
* Le problème persiste ? Visitez la [page de support Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Général

### <a name="what-is-power-bi-embedded"></a>Qu'est-ce que Power BI Embedded ?

Microsoft Power BI Embedded permet aux développeurs d’incorporer des applications, rapports, tableaux de bord et vignettes totalement interactifs dans les applications sans que ceux-ci doivent passer du temps à créer entièrement leurs propres visualisations de données et contrôles.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Qui est le public cible de Power BI Embedded ?

Les développeurs et les éditeurs de logiciels qui créent leurs propres applications sont appelés « fournisseurs de logiciels indépendants ».

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>En quoi Power BI Embedded est différent du service Power BI ?

Power BI Embedded est conçu pour les éditeurs de logiciels indépendants ou les développeurs qui créent des applications et souhaitent y incorporer des visuels pour aider leurs clients à prendre des décisions sans générer entièrement une solution d’analytique. L’analytique incorporée permet aux utilisateurs en entreprise d’accéder aux données de l’entreprise et d’exécuter des requêtes pour générer des insights à l’aide de ces données au sein de l’application.

En revanche, Power BI est une solution d’analytique en tant que service qui offre aux organisations une vue unique de leurs données les plus critiques.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Quelle est la différence entre Power BI Premium et Power BI Embedded ?

Power BI Premium offre des fonctionnalités destinées aux entreprises qui veulent une solution d’informatique décisionnelle complète qui fournit une vue unique de leur organisation, partenaires, clients et fournisseurs. Power BI Premium aide votre organisation à prendre des décisions. Power BI Premium est un produit SaaS qui permet aux utilisateurs de consommer du contenu via le portail Power BI, l’application mobile et des applications développées en interne.

Power BI Embedded est conçu pour les éditeurs de logiciels indépendants ou les développeurs qui créent des applications et souhaitent y incorporer des visuels. Power BI Embedded aide vos clients à prendre des décisions. Comme Power BI Embedded est conçu pour les développeurs d’applications, les clients de ces applications peuvent utiliser du contenu stocké sur la capacité Power BI Embedded, y compris toute personne à l’intérieur ou à l’extérieur de l’organisation. Le contenu de la capacité Power BI Embedded ne peut pas être partagé via la publication vers le web ou SharePoint en un clic, et ne prend pas en charge les rapports SSRS.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Que recommande Microsoft à un client qui hésite entre Power BI Embedded et Power BI Premium ?

Microsoft recommande aux entreprises d’acheter Power BI Premium (solution d’informatique décisionnelle cloud libre-service de classe Entreprise), et aux éditeurs de logiciels indépendants d’acheter Power BI Embedded, qui regroupe des composants d’analytique incorporée fonctionnant dans le cloud. Toutefois, il n’existe aucune restriction sur le produit qu’un client peut acheter.

Dans certains cas, un éditeur de logiciels indépendant (généralement de grande taille) peut vouloir utiliser une référence SKU P pour obtenir les avantages supplémentaires du service Power BI complet au sein de leur organisation, ainsi que les incorporer dans leurs applications. Bien sûr, certaines entreprises peuvent décider d’utiliser des références SKU A dans Azure si elles ne sont intéressées que par la création d’applications métiers et l’incorporation d’analytiques dans celles-ci et si elles ne sont pas intéressées par l’utilisation du service Power BI complet.

### <a name="how-many-embed-tokens-can-i-create"></a>Combien de jetons incorporés puis-je créer ?

Les jetons incorporés avec une licence PRO étant destinés aux tests de développement, le nombre de jetons incorporés qu’un compte principal Power BI peut générer est limité. Vous devez [acheter une capacité](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) pour l’incorporation dans un environnement de production. Une fois une capacité achetée, le nombre de jetons incorporés que vous pouvez générer n’est pas limité.

### <a name="when-will-power-bi-embedded-be-available-in-azure"></a>Quand Power BI Embedded sera-t-il disponible dans Azure ?

Power BI Embedded est maintenant disponible.

## <a name="technical"></a>Technique

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-em-skus-in-office-365"></a>Quelle est la différence entre les références SKU A dans Azure et EM dans Office 365 ?

PowerBI.com est une solution d’entreprise qui inclut de nombreuses fonctionnalités, notamment de collaboration sociale, d’abonnement par e-mail, etc. dans une offre de logiciel en tant que service

Power BI Embedded est un ensemble d’API qui permet aux développeurs de créer une solution d’analytique incorporée dans une offre de plateforme en tant que service. Pour le scénario d’analytique incorporée, PowerBI.com doit être utilisé pour aider les éditeurs de logiciels indépendants et les développeurs à gérer le contenu des solutions d’analytique incorporée et les paramètres au niveau du locataire.

Voici un tableau des différences de fonctionnalités.

|Fonctionnalité  |Power BI Embedded<br>(Références SKU A) |Capacité Power BI Premium<br>(Références SKU EM)  |
|---------|---------|---------|
|Incorporer des artefacts à partir d’espaces de travail d’application Power BI     |Capacité Azure |Capacité Office 365 |
|Licence BI Power requise pour utiliser des rapports |Non  |Oui |
|Utiliser des rapports Power BI dans une application incorporée |Oui  |Oui |
|Utiliser des rapports Power BI dans SharePoint |Non |Oui |
|Utiliser des rapports Power BI dans Teams |Non |Oui |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI propose à présent les trois références SKU suivantes pour l’incorporation : A, EM et P. Laquelle dois-je acheter pour mon scénario ?

|  |Référence SKU A (Power BI Embedded)  |Référence SKU EM (Power BI Premium)  |Référence SKU P (Power BI Premium)  |
|---------|---------|---------|---------|
|Acheter     |Portail Azure |Office |Office |
|Cas d’usage |* Incorporer du contenu dans votre application |* Incorporer du contenu dans votre application<br>* Partager du contenu avec des utilisateurs de la version gratuite de Power BI en dehors de PowerBI.com et incorporer dans d’autres applications SaaS (SharePoint, Teams) |* Incorporer du contenu dans votre application<br>* Partager du contenu avec des utilisateurs de la version gratuite de Power BI en dehors de PowerBI.com et incorporer dans d’autres applications SaaS (SharePoint, Teams)<br>* Partager du contenu avec des utilisateurs de la version gratuite de Power BI via PowerBI.com  |
|Facturation |Toutes les heures |Mensuelle |Mensuelle |
|Avec engagement  |Sans engagement |Annuel  |Mensuelle/Annuelle |
|Différenciation |Élasticité complète : augmenter/réduire la taille, interrompre/reprendre des ressources dans le portail Azure ou via l’API  |Peut être utilisée pour incorporer du contenu dans SharePoint Online et Microsoft Teams |Combiner l’incorporation dans les applications et utiliser le service Power BI dans la même capacité |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Quelles sont les prérequis à la création d’une capacité PBIE dans Azure ?

- Vous devez vous connecter à votre annuaire d’organisation (les comptes MSA ne sont pas pris en charge).
- Vous devez avoir un locataire Power BI (c’est-à-dire qu’au moins un utilisateur dans votre annuaire doit être inscrit à Power BI). 
- Vous devez disposer d’un abonnement Azure dans votre annuaire d’organisation.

### <a name="how-can-i-monitor-capacity-consumption"></a>Comment puis-je surveiller la consommation de capacité ?

La surveillance via Azure est prévue à court terme. La ressource Azure « Power BI Embedded » inclura des indicateurs de performance clés de surveillance qui indiqueront l’intégrité et l’utilisation.

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>Ma capacité évoluera-t-elle automatiquement pour s’ajuster à la consommation de mon application ?

Bien que la mise à l’échelle automatique ne soit pas proposée à l’heure actuelle, toutes les API peuvent être mises à l’échelle à tout moment.

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Quel est le modèle d’authentification pour Power BI Embedded ?

Power BI Embedded continuera à utiliser Azure AD pour l’authentification de l’utilisateur principal (utilisateur désigné sous licence Power BI Pro), en authentifiant l’application à l’intérieur de Power BI.

L’authentification et l’autorisation des utilisateurs de l’application seront implémentées par l’éditeur de logiciels indépendant. Ce dernier peut implémenter sa propre authentification pour ses applications.

Si vous disposez déjà d’un locataire Azure AD, vous pouvez utiliser votre répertoire actuel, ou vous pouvez créer un locataire Azure AD pour garantir la sécurité du contenu de votre application incorporée.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>En quoi Power BI Embedded est différent des autres services Azure ?

L’éditeur de logiciels indépendant/le développeur doit avoir un compte Power BI avant d’acheter Power BI Embedded dans Azure. Votre région de déploiement Power BI Embedded est déterminée par votre compte Power BI. Gérez votre ressource Power BI Embedded dans Azure aux fins suivantes :

* Augmenter/réduire la taille
* Ajouter des administrateurs de capacité
* Interrompre/reprendre le service

Utilisez PowerBI.com pour attribuer/désattribuer des espaces de travail à votre capacité Power BI Embedded.

### <a name="what-deploy-regions-are-supported"></a>Quelles régions de déploiement sont prises en charge ?

Sud-Est de l’Australie, Sud du Brésil, Canada Centre, Est des États-Unis 2, Inde-Ouest, Est du Japon, Nord-Centre des États-Unis, Europe du Nord, Sud-Centre des États-Unis, Asie du Sud-Est, Royaume-Uni Sud, Europe de l’Ouest, Ouest des États-Unis et Ouest des États-Unis 2.

## <a name="licensing"></a>Gestion des licences

### <a name="how-do-i-purchase-power-bi-embedded"></a>Comment acheter Power BI Embedded ?

Power BI Embedded est disponible via Azure.

### <a name="how-power-bi-embedded-be-metered"></a>Comment est mesuré Power BI Embedded ?

Power BI Embedded est facturé sur une base horaire.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Comment s’affiche l’utilisation de Power BI Embedded sur ma facture ?

Power BI Embedded est facturé à un tarif horaire prévisible basé sur le type de nœuds déployé. Notez que tant que votre ressource est active, vous êtes facturé même si aucune utilisation n’est enregistrée. Pour ne plus être facturé, vous devez suspendre activement votre ressource. Pour cela, vous pouvez passer par Azure ou par les API ARM.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>Que se passe-t-il si j’ai déjà acheté Power BI Premium et que je veux maintenant profiter de certains des avantages de Power BI Embedded dans Azure ?

Les clients continueront à payer les achats Power BI Premium actuels jusqu’à la fin de la durée de leur contrat actuel et pourront ensuite basculer leurs achats Power BI, le cas échéant.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Dois-je toujours acheter Power BI Premium pour accéder à Power BI Embedded ?

Non. Power BI Embedded inclut la capacité basée sur Azure dont vous avez besoin pour déployer et distribuer votre solution aux clients.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Qui a besoin d’une licence Power BI Pro pour Power BI Embedded et pourquoi ?

Voici les utilisateurs qui doivent avoir une licence Power BI Pro : les analystes qui ont besoin d’ajouter des rapports à un espace de travail Power BI, les développeurs qui ont besoin d’utiliser des API REST et les administrateurs de locataire qui ont besoin de gérer le locataire et la capacité Power BI.

Comme Power BI Embedded autorise l’utilisation du portail Power BI pour la gestion et la validation du contenu intégré, la licence Power BI Pro est requise pour authentifier l’application à l’intérieur de PowerBI.com afin d’accéder aux rapports dans les dépôts appropriés.

### <a name="can-i-get-started-for-free"></a>Puis-je commencer gratuitement ?

Oui, vous pouvez utiliser vos [crédits Azure](https://azure.microsoft.com/free/) pour Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Puis-je me procurer un essai de Power BI Embedded dans Azure ?

Étant donné que Power BI Embedded fait partie d’Azure, il est possible d’utiliser le service avec le [crédit de 200 $ reçu lors de l’inscription à Azure](https://azure.microsoft.com/free/).

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Quel est la durée d’engagement pour Power BI Embedded ? 

Les clients peuvent modifier leur utilisation sur une base horaire. Il n’existe aucun engagement mensuel ou annuel pour le service Power BI Embedded.

### <a name="where-is-power-bi-embedded-available-us-government-germany-china-what-is-the-timing"></a>Où est disponible Power BI Embedded ? US Government ? Allemagne ? Chine ? Quel est le calendrier ?

Power BI Embedded sera disponible dans les clouds commerciaux Azure lors de sa mise à la disponibilité générale.  La disponibilité dans les clouds souverains sera ajoutée à l’avenir.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded est-il disponible pour les organisations à but non lucratif et les établissements d’enseignement ?

Les organisations à but non lucratif et les établissements d’enseignement peuvent acheter Azure. Il n’existe aucune tarification spéciale pour ces types de clients dans Azure.

D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)
