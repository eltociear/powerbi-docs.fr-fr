---
title: Power BI for les clients du gouvernement des États-Unis – Vue d’ensemble
description: Les clients du gouvernement des États-Unis peuvent ajouter un abonnement Power BI Pro à leur offre Microsoft 365 Secteur Public. Découvrez comment connaître la disponibilité des fonctionnalités et s’y inscrire dans cette description du service.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: a9a5f3fd5304e64209b6069741dffcc3fa9b07c8
ms.sourcegitcommit: c772c544ce2e1e2a147b9b62e5579ac3cb59d54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82256145"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI pour les clients du gouvernement des États-Unis
Cet article est destiné aux clients du gouvernement des États-Unis qui déploient Power BI dans le cadre d’une offre Office 365 Secteur Public. Les abonnements Secteur Public sont prévus pour répondre aux besoins spécifiques des organisations qui doivent respecter les normes de conformité et de sécurité des États-Unis. Le service Power BI conçu pour les clients du gouvernement des États-Unis est différent de la version commerciale du service Power BI. Les différences de fonctionnalités sont décrites dans les sections qui suivent.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Ajouter Power BI à une offre Office 365 Secteur Public

Pour obtenir un abonnement Power BI pour le gouvernement des États-Unis et affecter des licences aux utilisateurs, vous devez vous inscrire à une offre Office 365 Secteur Public. Si votre organisation dispose déjà d’une offre Office 365 Secteur Public, passez directement à [Achat d’un abonnement Power BI Pro Secteur Public](#purchase-a-power-bi-pro-government-subscription).

### <a name="enroll-in-office-365-government-plan"></a>Souscrire une offre Office 365 Secteur Public

Si vous êtes un nouveau client, vous devez valider l’admissibilité de votre organisation pour pouvoir vous inscrire à un abonnement Secteur Public.  Commencez par compléter le [formulaire de validation de l’admissibilité Office 365 Secteur Public](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Pour sélectionner un abonnement adapté à votre organisation, consultez la [description des services Office 365 pour le gouvernement des États-Unis](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Si vous avez déjà déployé Power BI dans un environnement commercial et que vous souhaitez migrer vers le cloud du gouvernement des États-Unis, vous devez ajouter un nouvel abonnement Power BI Pro à votre offre Office 365 Secteur Public. Ensuite, répliquez les données commerciales sur le service Power BI pour le gouvernement des États-Unis, supprimez les attributions de licences commerciales des comptes d’utilisateurs, puis affectez une licence Power BI Pro Secteur Public aux comptes d’utilisateurs.
>
>
## <a name="government-cloud-instances"></a>Instances du cloud pour le secteur public
Office 365 propose différents environnements pour les organismes gouvernementaux qui répondent à différentes exigences de conformité. Pour plus d’informations sur le contenu de chaque environnement, consultez la description des services liés.

* Le [Cloud de la communauté du secteur public (GCC) Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) est conçu pour les administrations fédérales, nationales et locales.

* Le [Cloud de la communauté du secteur public High (GCC High) Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu pour les agences fédérales, le secteur de la défense, l’industrie aéronautique et d’autres organisations détenant des informations protégées non classées. Cet environnement est adapté aux organisations de sécurité nationale et aux entreprises disposant de données ITAR (International Traffic in Arms Regulations) ou soumises à des exigences DFARS (Defense Federal Acquisition Regulation Supplement).

* [L’environnement Office 365 DoD](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) est conçu exclusivement pour le département de la Défense des États-Unis. 

## <a name="connect-to-power-bi-for-us-government"></a>Connexion à Power BI pour le gouvernement des États-Unis

Vous utilisez une autre URL que les utilisateurs commerciaux pour vous connecter à Power BI pour le gouvernement des États-Unis. Pour vous connecter à Power BI, utilisez les URL suivantes :

| Version commerciale  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Votre compte peut être provisionné dans plusieurs clouds. Dans ce cas, lorsque vous utilisez Power BI Desktop, vous pouvez choisir à quel cloud vous connecter.

## <a name="purchase-a-power-bi-pro-government-subscription"></a>Acheter un abonnement Power BI Pro Secteur Public

Après avoir déployé Office 365, vous pouvez ajouter un abonnement Power BI. Suivez l’aide pas à pas [Inscription d’une organisation du gouvernement des États-Unis](service-govus-signup.md) pour acheter le service Power BI Pro Secteur Public. Achetez suffisamment de licences pour tous les utilisateurs qui doivent utiliser Power BI, puis attribuez-les aux différents comptes d’utilisateur.

> [!IMPORTANT]
> Power BI pour le gouvernement des États-Unis n’est pas disponible sous licence gratuite. Chaque utilisateur doit disposer d’une licence Pro pour pouvoir accéder au Cloud de la communauté du secteur public. Un compte d’utilisateur qui dispose d’une licence gratuite n’est autorisé à accéder qu’au cloud commercial et rencontrera des problèmes d’authentification et d’accès. Si vous avez acheté Power BI Premium, vous n’êtes pas obligé d’attribuer des licences Pro pour permettre l’accès des utilisateurs.  Les utilisateurs de l’organisation peuvent accéder aux rapports partagés avec eux tant que le rapport est publié sur une capacité Premium. Pour connaître les différences entre les types de licences, consultez [Fonctionnalités du service Power BI par type de licence](service-features-license-type.md).
>
>

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Connectivité entre le service Azure Cloud pour le secteur public et le service Azure Cloud mondial

Azure est réparti sur plusieurs clouds. Par défaut, vous pouvez activer des règles de pare-feu pour ouvrir une connexion à une instance propre au cloud, mais la mise en réseau entre clouds est différente.  Pour communiquer entre les services du cloud public et ceux du Cloud de la communauté du secteur public, vous devez configurer des règles de pare-feu spécifiques. Par exemple, si vous souhaitez accéder à des instances de cloud public de SQL à partir de votre déploiement cloud pour le secteur public de Power BI, il vous faut une règle de pare-feu dans SQL. Configurez des règles de pare-feu spécifiques dans SQL afin d’autoriser les connexions au cloud Azure Government pour les centres de donnés suivants :

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Dans le cloud public, les plages d’adresses IP sont disponibles. Pour obtenir celles du cloud du gouvernement des États-Unis, téléchargez le fichier [Plages d’adresses IP et balises de service Azure – Cloud du gouvernement des États-Unis](https://www.microsoft.com/download/details.aspx?id=57063). 

Pour configurer des pare-feu dans SQL, suivez les étapes de la section [Créer et gérer des règles de pare-feu IP](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilité des fonctionnalités de Power BI

Pour répondre aux besoins des clients du cloud pour le secteur public, il existe quelques différences entre les offres pour le gouvernement et les offres commerciales. Consultez le tableau suivant pour connaître les fonctionnalités disponibles dans chaque environnement gouvernemental.

|Caractéristique |   |GCC |GCC High |DoD|
|------|------|------|------|------|
|Administration|Licences gratuites|Non disponible|Non disponible|Non disponible|
|  |Définition de limites de stockage|Disponible|Disponible|Disponible|
|  |Utilisation de groupes Active Directory pour le partage et le contrôle d’accès|Disponible|Disponible|Disponible|
|  |Audit par le biais du Centre d’administration de sécurité et conformité Office 365|Disponible|Disponible|Disponible|
|  |Partage avec des utilisateurs externes|Disponible|Disponible|Disponible|
|  |Mesures d’utilisation pour les rapports et les tableaux de bord|Non disponible|Non disponible|Non disponible|
|  |Azure B2B entre GCC et le cloud commercial|Non disponible|Non disponible|Non disponible|
|Création de rapports|Créer et afficher des tableaux de bord et rapports|Disponible|Disponible|Disponible|
|  |Actualisation planifiée des données|Disponible|Disponible|Disponible|
|  |Tableaux de bord d’équipe actualisables|Disponible|Disponible|Disponible|
|  |Rapports paginés|Disponible|Dans la feuille de route|Dans la feuille de route|
|  |Applications modèles|Non disponible|Non disponible|Non disponible|
|Se connecter aux données|Importer des données et des rapports à partir d’Excel|Disponible|Disponible|Disponible|
|  |Importer des données à partir de fichiers CSV|Disponible|Disponible|Disponible|
|  |Importer des données à partir de fichiers Power BI Desktop|Disponible|Disponible|Disponible|
|  |Connectivité à CDS|Disponible|Non disponible|Non disponible|
|  |Connecteur Azure Data Lake Storage Gen2|Disponible|Non disponible|Non disponible|
|Gestion des données|Passerelle de gestion des données|Disponible|Disponible|Disponible|
|  |Chiffrement de données dans Azure SQL|Disponible|Disponible|Disponible|
|  |Chiffrement de données dans le Stockage Blob pour Power BI|Disponible|Disponible|Disponible|
|Intégration entre produits|Incorporation dans SharePoint Online à l’aide du composant WebPart Power BI|Non disponible|Non disponible|Non disponible|
|  |Incorporation dans SharePoint Online à l’aide du composant WebPart Incorporer|Disponible|Disponible|Disponible|
|  |Flux de données et fonctions d’IA|Non disponible|Non disponible|Non disponible|
|  |Connectivité Power Automate pour les alertes de données|Non disponible|Non disponible|Non disponible|
|  |Onglet Power BI dans Teams|Disponible|Non disponible|Non disponible|
|  |Machine Learning automatisé|Non disponible|Non disponible|Non disponible|
|  |Cognitive Services|Non disponible|Non disponible|Non disponible|
|  |Azure ML|Non disponible|Non disponible|Non disponible|

## <a name="next-steps"></a>Étapes suivantes

* [Inscription à Power BI pour le gouvernement des États-Unis](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Démonstration de Power BI US Government</a>
