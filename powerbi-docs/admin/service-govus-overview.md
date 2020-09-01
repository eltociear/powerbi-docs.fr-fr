---
title: Power BI for les clients du gouvernement des États-Unis – Vue d’ensemble
description: Les clients du gouvernement des États-Unis peuvent ajouter un abonnement Power BI Pro à leur offre Microsoft 365 Secteur Public. Découvrez comment connaître la disponibilité des fonctionnalités et s’y inscrire dans cette description du service.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/02/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: 75b05449de47f39fc95fd7cf42f9325b7a5d0ee9
ms.sourcegitcommit: f73ea4b9116ad186817ec5cc5d5f487d49cc0cb0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88638770"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI pour les clients du gouvernement des États-Unis

Cet article est destiné aux clients du gouvernement des États-Unis qui déploient Power BI dans le cadre d’une offre Microsoft 365 Secteur Public. Les abonnements Secteur Public sont prévus pour répondre aux besoins spécifiques des organisations qui doivent respecter les normes de conformité et de sécurité des États-Unis. Le service Power BI conçu pour les clients du gouvernement des États-Unis est différent de la version commerciale du service Power BI. Les différences de fonctionnalités sont décrites dans les sections qui suivent.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Ajouter Power BI à votre offre Microsoft 365 Secteur Public

Pour obtenir un abonnement Power BI pour le gouvernement des États-Unis et affecter des licences aux utilisateurs, vous devez vous inscrire à une offre Microsoft 365 Secteur Public. Si votre organisation dispose déjà d’une offre Microsoft 365 Secteur Public, passez directement à [Achat d’un abonnement Power BI Pro pour les clients du gouvernement](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>S’inscrire à un plan Microsoft 365 Secteur Public

Si vous êtes un nouveau client, vous devez valider l’admissibilité de votre organisation pour pouvoir vous inscrire à un abonnement Microsoft 365 Secteur Public.  Commencez par compléter le [formulaire de validation de l’admissibilité Microsoft 365 Secteur Public](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Pour sélectionner un abonnement adapté à votre organisation, consultez la [description des services Microsoft 365 pour le gouvernement des États-Unis](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Si vous avez déjà déployé Power BI dans un environnement commercial et que vous souhaitez migrer vers le cloud du gouvernement des États-Unis, vous devez ajouter un nouvel abonnement Power BI Pro à votre offre Microsoft 365 Secteur Public. Ensuite, répliquez les données commerciales sur le service Power BI pour le gouvernement des États-Unis, supprimez les attributions de licences commerciales des comptes d’utilisateurs, puis affectez une licence Power BI Pro Secteur Public aux comptes d’utilisateurs.
>
>
## <a name="government-cloud-instances"></a>Instances du cloud pour le secteur public

Microsoft 365 propose différents environnements pour les organismes gouvernementaux qui répondent à différentes exigences de conformité. Pour plus d’informations sur chaque environnement, consultez :

* Le [Cloud de la communauté du secteur public (GCC) Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) est conçu pour les administrations fédérales, nationales et locales.

* Le [Cloud de la communauté du secteur public High (GCC High) Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu pour les agences fédérales, le secteur de la défense, l’industrie aéronautique et d’autres organisations détenant des informations protégées non classées. Cet environnement est adapté aux organisations de sécurité nationale et aux entreprises disposant de données ITAR (International Traffic in Arms Regulations) ou soumises à des exigences DFARS (Defense Federal Acquisition Regulation Supplement).

* [L’environnement Microsoft 365 DoD](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu exclusivement pour le département de la Défense des États-Unis.

## <a name="connect-to-power-bi-for-us-government"></a>Connexion à Power BI pour le gouvernement des États-Unis

L’URL de connexion à Power BI diffère pour les utilisateurs du secteur public et les utilisateurs commerciaux. Pour vous connecter à Power BI, utilisez les URL suivantes :

| Version commerciale  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Votre compte peut être configuré dans plusieurs clouds. Si votre compte est configuré ainsi, lorsque vous utilisez Power BI Desktop, vous pouvez choisir à quel cloud vous connecter.

## <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Acheter un abonnement Power BI Pro pour les clients du secteur public

Après avoir déployé Microsoft 365, vous pouvez ajouter un abonnement Power BI Pro. Suivez l’aide pas à pas [Inscription d’une organisation du gouvernement des États-Unis](service-govus-signup.md) pour acheter le service Power BI Pro Secteur Public. Achetez suffisamment de licences pour tous les utilisateurs qui doivent utiliser Power BI, puis attribuez-les aux différents comptes d’utilisateur.

> [!IMPORTANT]
> Power BI pour le gouvernement des États-Unis n’est pas disponible sous licence *gratuite*. Chaque utilisateur doit disposer d’une licence *Pro* pour pouvoir accéder au cloud de la communauté du secteur public. Un compte d’utilisateur qui dispose d’une licence gratuite n’est autorisé à accéder qu’au cloud commercial et rencontrera des problèmes d’authentification et d’accès. Si vous avez acheté Power BI Premium, vous n’êtes pas obligé d’attribuer des licences Pro pour permettre l’accès des utilisateurs.  Les utilisateurs de l’organisation peuvent accéder aux rapports partagés avec eux tant que le rapport est publié sur une capacité Premium. Pour connaître les différences entre les types de licences, consultez [Fonctionnalités du service Power BI par type de licence](../fundamentals/service-features-license-type.md).
>

## <a name="connect-government-and-global-azure-cloud-services"></a>Connexion entre le service Azure Cloud pour le secteur public et le service Azure Cloud mondial

Azure est réparti sur plusieurs clouds. Par défaut, vous pouvez activer des règles de pare-feu pour ouvrir une connexion à une instance propre au cloud, mais la mise en réseau entre clouds est différente.  Pour communiquer entre les services du cloud public et ceux du Cloud de la communauté du secteur public, vous devez configurer des règles de pare-feu spécifiques. Par exemple, si vous souhaitez accéder à des instances de cloud public d’une base de données SQL à partir de votre déploiement cloud pour le secteur public de Power BI, il vous faut une règle de pare-feu dans la base de données SQL. Configurez des règles de pare-feu spécifiques dans les bases de données SQL afin d’autoriser les connexions au cloud Azure Government pour les centres de données suivants :

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Dans le cloud public, les plages d’adresses IP sont disponibles. Pour obtenir celles du cloud du gouvernement des États-Unis, téléchargez le fichier [Plages d’adresses IP et balises de service Azure – Cloud du gouvernement des États-Unis](https://www.microsoft.com/download/details.aspx?id=57063).

Pour configurer des pare-feu pour les bases de données SQL, consultez [Créer et gérer des règles de pare-feu IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilité des fonctionnalités de Power BI

Pour répondre aux besoins des clients du cloud pour le secteur public, il existe quelques différences entre les offres pour le gouvernement et les offres commerciales. Consultez le tableau suivant pour connaître les fonctionnalités disponibles dans chaque environnement gouvernemental :

|Caractéristique |   |GCC |GCC High |DoD|
|------|------|------|------|------|
|Administration|Licences gratuites|Non disponible|Non disponible|Non disponible|
|  |Définition de limites de stockage|Disponible|Disponible|Disponible|
|  |Utilisation de groupes Active Directory pour le partage et le contrôle d’accès|Disponible|Disponible|Disponible|
|  |Audit par le biais du Centre d’administration de sécurité et conformité Office 365|Disponible|Disponible|Disponible|
|  |Partage avec des utilisateurs externes|Disponible|Disponible|Disponible|
|  |Mesures d’utilisation pour les rapports et les tableaux de bord|Disponible|Disponible|Disponible|
|  |Azure B2B Collaboration entre GCC et le cloud commercial<sup>1</sup>|Disponible|Non disponible|Non disponible|
|Création de rapports|Créer et afficher des tableaux de bord et rapports|Disponible|Disponible|Disponible|
|  |Actualisation planifiée des données|Disponible|Disponible|Disponible|
|  |Tableaux de bord d’équipe actualisables|Disponible|Disponible|Disponible|
|  |Rapports paginés|Disponible|Disponible|Disponible|
|  |Applications modèles|Non disponible|Non disponible|Non disponible|
|Se connecter aux données|Importer des données et des rapports à partir d’Excel|Disponible|Disponible|Disponible|
|  |Importer des données à partir de fichiers CSV|Disponible|Disponible|Disponible|
|  |Importer des données à partir de fichiers Power BI Desktop|Disponible|Disponible|Disponible|
|  |Connectivité à CDS|Disponible|Non disponible|Non disponible|
|  |Connecteur Azure Data Lake Storage Gen2|Disponible|Non disponible|Non disponible|
|Gestion des données|Passerelle de gestion des données|Disponible|Disponible|Disponible|
|  |Chiffrement de données dans une base de données Azure SQL|Disponible|Disponible|Disponible|
|  |Chiffrement de données dans le Stockage Blob pour Power BI|Disponible|Disponible|Disponible|
|Intégration entre produits|Incorporation dans SharePoint Online à l’aide du composant WebPart Power BI|Disponible|Non disponible|Non disponible|
|  |Incorporation dans SharePoint Online à l’aide du composant WebPart Incorporer|Disponible|Disponible|Disponible|
|  |Flux de données et fonctions d’IA|Non disponible|Non disponible|Non disponible|
|  |Connectivité Power Automate pour les alertes de données|Non disponible|Non disponible|Non disponible|
|  |Onglet Power BI dans Teams|Disponible|Non disponible|Non disponible|
|  |Machine Learning automatisé|Non disponible|Non disponible|Non disponible|
|  |Azure Cognitive Services|Non disponible|Non disponible|Non disponible|
|  |Azure Machine Learning|Non disponible|Non disponible|Non disponible|

<sup>1</sup> B2B Collaboration est disponible pour GCC, à condition que l’utilisateur externe dispose d’une licence dans cet environnement. Les licences Cloud commercial ne sont pas valides dans GCC. Pour plus d’informations sur les limitations connues de B2B Collaboration pour US Government, lisez la [comparaison entre Azure Government et Azure international](https://docs.microsoft.com/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2).

## <a name="next-steps"></a>Étapes suivantes

* [Inscription à Power BI pour le gouvernement des États-Unis](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* [Démonstration de Power BI US Government](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
