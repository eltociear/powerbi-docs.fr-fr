---
title: Power BI for les clients du gouvernement des États-Unis – Vue d’ensemble
description: Les clients du gouvernement des États-Unis peuvent ajouter un abonnement Power BI Pro à leur offre Microsoft 365 Secteur Public. Découvrez comment connaître la disponibilité des fonctionnalités et s’y inscrire dans cette description du service.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/02/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: 948e0260f13aa243a45ba5bdf6fe59c9699d47a0
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90855101"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI pour les clients du gouvernement des États-Unis

Cet article est destiné aux clients du gouvernement des États-Unis qui déploient Power BI dans le cadre d’une offre Microsoft 365 Secteur Public. Les abonnements Secteur Public sont prévus pour répondre aux besoins spécifiques des organisations qui doivent respecter les normes de conformité et de sécurité des États-Unis. Le service Power BI conçu pour les clients du gouvernement des États-Unis est différent de la version commerciale du service Power BI. Les différences de fonctionnalités sont décrites dans les sections qui suivent.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Ajouter Power BI à votre offre Microsoft 365 Secteur Public

Pour obtenir un abonnement Power BI pour le gouvernement des États-Unis et affecter des licences aux utilisateurs, vous devez vous inscrire à une offre Microsoft 365 Secteur Public. Si votre organisation dispose déjà d’une offre Microsoft 365 Secteur Public, passez directement à [Achat d’un abonnement Power BI Pro pour les clients du gouvernement](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>S’inscrire à un plan Microsoft 365 Secteur Public

Si vous êtes un nouveau client, vous devez valider l’admissibilité de votre organisation pour pouvoir vous inscrire à un abonnement Microsoft 365 Secteur Public.  Commencez par compléter le [formulaire de validation de l’admissibilité Microsoft 365 Secteur Public](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Pour sélectionner un abonnement adapté à votre organisation, consultez la [description des services Microsoft 365 pour le gouvernement des États-Unis](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Si vous avez déjà déployé Power BI dans un environnement commercial et que vous souhaitez migrer vers le cloud du gouvernement des États-Unis, vous devez ajouter un nouvel abonnement Power BI Pro à votre offre Microsoft 365 Secteur Public. Ensuite, répliquez les données commerciales sur le service Power BI pour le gouvernement des États-Unis, supprimez les attributions de licences commerciales des comptes d’utilisateurs, puis affectez une licence Power BI Pro Secteur Public aux comptes d’utilisateurs.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Acheter un abonnement Power BI Pro pour les clients du secteur public

Après avoir déployé Microsoft 365, vous pouvez ajouter un abonnement Power BI Pro. Suivez l’aide pas à pas [Inscription d’une organisation du gouvernement des États-Unis](service-govus-signup.md) pour acheter le service Power BI Pro Secteur Public. Achetez suffisamment de licences pour tous les utilisateurs qui doivent utiliser Power BI, puis attribuez-les aux différents comptes d’utilisateur.

> [!IMPORTANT]
> Power BI pour le gouvernement des États-Unis n’est pas disponible sous licence *gratuite*. Chaque utilisateur doit disposer d’une licence *Pro* pour pouvoir accéder au cloud de la communauté du secteur public. Un compte d’utilisateur qui dispose d’une licence gratuite n’est autorisé à accéder qu’au cloud commercial et rencontrera des problèmes d’authentification et d’accès. Si vous avez acheté Power BI Premium, vous n’êtes pas obligé d’attribuer des licences Pro pour permettre l’accès des utilisateurs.  Les utilisateurs de l’organisation peuvent accéder aux rapports partagés avec eux tant que le rapport est publié sur une capacité Premium. Pour connaître les différences entre les types de licences, consultez [Fonctionnalités du service Power BI par type de licence](../fundamentals/service-features-license-type.md).
>

## <a name="government-cloud-instances"></a>Instances du cloud pour le secteur public

Microsoft 365 propose différents environnements pour les organismes gouvernementaux qui répondent à différentes exigences de conformité. Pour plus d’informations sur chaque environnement, consultez :

* Le [Cloud de la communauté du secteur public (GCC) Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) est conçu pour les administrations fédérales, nationales et locales.

* Le [Cloud de la communauté du secteur public High (GCC High) Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu pour les agences fédérales, le secteur de la défense, l’industrie aéronautique et d’autres organisations détenant des informations protégées non classées. Cet environnement est adapté aux organisations de sécurité nationale et aux entreprises disposant de données ITAR (International Traffic in Arms Regulations) ou soumises à des exigences DFARS (Defense Federal Acquisition Regulation Supplement).

* [L’environnement Microsoft 365 DoD](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu exclusivement pour le département de la Défense des États-Unis.

## <a name="connect-to-power-bi-for-us-government"></a>Connexion à Power BI pour le gouvernement des États-Unis

L’URL de connexion à Power BI diffère pour les utilisateurs du secteur public et les utilisateurs commerciaux. Pour vous connecter à Power BI, utilisez les URL suivantes :

| Version commerciale  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Votre compte peut être configuré dans plusieurs clouds. Si votre compte est configuré ainsi, lorsque vous utilisez Power BI Desktop, vous pouvez choisir à quel cloud vous connecter.

## <a name="connect-government-and-global-azure-cloud-services"></a>Connexion entre le service Azure Cloud pour le secteur public et le service Azure Cloud mondial

Azure est réparti sur plusieurs clouds. Par défaut, vous pouvez activer des règles de pare-feu pour ouvrir une connexion à une instance propre au cloud, mais la mise en réseau entre clouds est différente.  Pour communiquer entre les services du cloud public et ceux du Cloud de la communauté du secteur public, vous devez configurer des règles de pare-feu spécifiques. Par exemple, si vous souhaitez accéder à des instances de cloud public d’une base de données SQL à partir de votre déploiement cloud pour le secteur public de Power BI, il vous faut une règle de pare-feu dans la base de données SQL. Configurez des règles de pare-feu spécifiques dans les bases de données SQL afin d’autoriser les connexions au cloud Azure Government pour les centres de données suivants :

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Dans le cloud public, les plages d’adresses IP sont disponibles. Pour obtenir celles du cloud du gouvernement des États-Unis, téléchargez le fichier [Plages d’adresses IP et balises de service Azure – Cloud du gouvernement des États-Unis](https://www.microsoft.com/download/details.aspx?id=57063).

Pour configurer des pare-feu pour les bases de données SQL, consultez [Créer et gérer des règles de pare-feu IP](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilité des fonctionnalités de Power BI

Pour répondre aux besoins des clients du cloud pour le secteur public, il existe quelques différences entre les offres pour le gouvernement et les offres commerciales. Notre objectif est de rendre toutes les fonctionnalités disponibles dans les clouds du secteur public dans un délai de 30 jours de disponibilité générale. Dans certains cas, les dépendances sous-jacentes nous empêchent de rendre une fonctionnalité disponible.

Le tableau suivant liste les fonctionnalités qui ne sont pas disponibles dans un environnement du secteur public particulier et la disponibilité estimée si la mise en production est planifiée :

|Caractéristique |GCC |GCC High |DoD|
|------|------|------|------|
|[Azure B2B Collaboration entre le cloud public et le cloud commercial](service-admin-azure-ad-b2b.md)<sup>1</sup>|![disponible](../media/yes.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Incorporation dans SharePoint Online à l’aide du composant WebPart Power BI](/esharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![disponible](../media/yes.png)|![Disponible](../media/yes.png)|![non disponible](../media/no.png)|
|[Connectivité Power Automate pour les alertes de données](../connect-data/power-bi-data-sources.md)|![disponible](../media/yes.png)|![disponible](../media/yes.png)|![non disponible](../media/no.png)|
|[Onglet Power BI dans Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![disponible](../media/yes.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|
|[Métriques de capacité](../admin/service-admin-premium-monitor-portal.md)|T3 2020 |T3 2020|T3 2020|
|[Grands modèles](service-premium-large-models.md) | T4 2020 |T4 2020| ![non disponible](../media/no.png) |
|[Dataflows - Optimisation du moteur de calcul SQL](../transform-model/service-dataflows-enhanced-compute-engine.md) | T4 2020 |T4 2020| ![non disponible](../media/no.png) |
|[Dataflows - Requête directe](../transform-model/service-dataflows-directquery.md) | T4 2020 |T4 2020|![non disponible](../media/no.png)|
|[Notifications d’interruption de service](service-premium-large-models.md)|T4 2020 |T4 2020|T4 2020|
|[Protection des données (étiquettes MIP)](service-security-sensitivity-label-overview.md)|T4 2020|T4 2020 |T4 2020|
|[Applications modèles](../connect-data/service-template-apps-overview.md)<sup>3</sup>|T4 2020 |T4 2020| T4 2020|
|[Visuels personnalisés](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|T4 2020 |T4 2020| T4 2020|
|[Génération d’un code QR](../create-reports/service-create-qr-code-for-tile.md)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|![non disponible](../media/no.png)|

<sup>1</sup> B2B Collaboration est disponible pour GCC, à condition que l’utilisateur externe dispose d’une licence dans cet environnement. Les licences Cloud commercial ne sont pas valides dans GCC. Pour plus d’informations sur les limitations connues de B2B Collaboration pour le gouvernement américain, lisez la [comparaison entre Azure Government et Azure international](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2).

<sup>2</sup> L’expérience Power BI dans Teams pour GCC est limitée : elle fonctionne uniquement pour les espaces de travail classiques et n’inclut pas les fonctionnalités améliorées décrites dans [Incorporer du contenu Power BI dans Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

<sup>3</sup> Lors de la publication, la fonctionnalité pour les applications modèles et les visuels personnalisés sera limitée aux clouds du secteur public. Des informations supplémentaires sur des limitations spécifiques seront publiées au moment de la publication.

## <a name="next-steps"></a>Étapes suivantes

* [Inscription à Power BI pour le gouvernement des États-Unis](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [Démonstration de Power BI US Government](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)