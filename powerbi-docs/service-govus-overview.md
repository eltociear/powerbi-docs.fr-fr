---
title: Power BI pour les clients US Government - Vue d’ensemble
description: Si vous êtes un client US Government, découvrez les fonctionnalités et limitations du service Power BI US Government
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/02/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: e676ef85d982a59b7058bce9e6467e8482b7aa62
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722688"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI for les clients US Government
Le **service Power BI** a une version disponible pour les clients US Government dans le cadre des abonnements de la **Communauté Office 365 US Government**. La version du **service Power BI** abordée dans cet article est spécialement conçue pour les clients US Government. Elle est distincte et différente de la version commerciale du **service Power BI**.

![](media/service-govus-overview/service_usgov_overview-1.png)

Les sections suivantes décrivent les *fonctionnalités* disponibles pour la version US Government du **service Power BI**, clarifient certaines *limitations*, répertorient les questions fréquemment posées (**FAQ**) et les réponses (y compris sur l’inscription) et fournissent des liens permettant d’accéder à plus d’informations.

## <a name="features-of-power-bi-us-government"></a>Fonctionnalités de Power BI US Government
Il est important de noter que **Power BI US Government** est disponible uniquement sous **licence Pro** et ne l’est pas sous une licence Gratuite. Certaines fonctionnalités du service Power BI sont disponibles dans la version **Power BI US Government** du service.

Les fonctionnalités suivantes sont disponibles pour les clients de **Power BI US Government** clients, tout comme elles s’appliquent aux fonctionnalité de la licence **Pro** :

* Créer et afficher des tableaux de bord et rapports
* [Limite de capacité de données](service-admin-manage-your-data-storage-in-power-bi.md)
* [Actualisation des données planifiée](refresh-data.md)
* Tableaux de bord d’équipe actualisables
* Groupes Active Directory pour le partage et la gestion de contrôle d’accès
* [Importer des données](service-get-data.md) et des rapports à partir de fichiers Excel, CSV et Power BI Desktop
* Passerelle de gestion des données
* Toutes les données sont chiffrées aussi bien dans Azure SQL que dans Stockage Blob pour Power BI
* Se connecter à des services avec des [packs de contenu](service-connect-to-services.md)

## <a name="connectivity-between-government-and-public-azure-cloud-services"></a>Connectivité entre les services cloud Azure Government et public 

Azure est réparti entre plusieurs clouds. Par défaut, les locataires sont autorisés à ouvrir des règles de pare-feu vers une instance spécifique du cloud, mais la mise en réseau entre les clouds est différente et requiert l’ouverture de règles de pare-feu spécifiques pour la communication entre les services. Si vous êtes client Power BI et que vous disposez d’instances SQL actuelles dans le cloud public auxquelles vous souhaitez accéder, vous devez ouvrir des règles de pare-feu spécifiques dans SQL vers la plage d’IP du cloud Azure Government, pour les centres de données suivants :

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

Dans le cloud public, les plages d’IP sont disponibles, mais pour le cloud Azure Government, vous devez ouvrir un ticket de support Azure pour demander les plages d’IP des centres de données répertoriés ci-dessus. 


## <a name="limitations-of-power-bi-us-government"></a>Limitations de Power BI US Government
Certaines des fonctionnalités disponibles dans la version commerciale du **service Power BI** ne sont *pas* disponibles dans le **service Power BI** US Government. L’équipe Power BI travaille activement à rendre ces fonctionnalités disponibles pour les clients US Government et mettra à jour cet article au moment opportun.

* **Incorporer dans SharePoint Online** : il n’est pas possible d’incorporer du contenu dans SharePoint Online à l’aide de la partie web de Power BI.
* **Power BI US Government** est disponible uniquement sous licence **Pro**. Toutes les références à des licences Power BI (Gratuit) dans un portail d’administration (ou en tant qu’utilisateur) s’exécutent dans un cloud de service Power BI commercial.
* **Audit** : depuis juin 2018, l’audit est disponible via le portail Sécurité et conformité Office 365.
* **Contenu Power BI dans Cortana** - Les résultats Power BI ne s’affichent pas dans les résultats de recherche de Cortana, notamment les résultats de votre contenu Power BI (tableaux de bord, rapports, applications), ainsi que les résultats qui montrent des pages de rapport optimisées pour Cortana pour des mots clés spécifiques.
* **Partage avec des utilisateurs externes** : le partage est autorisé au sein d’un même locataire Power BI et, depuis juin 2018, il est également autorisé avec des utilisateurs extérieurs à votre locataire Power BI.
* **Métriques d’utilisation des tableaux de bord et des rapports** : les métriques d’utilisation ne sont pas disponibles pour les rapports et les tableaux de bord. Les clients peuvent utiliser les données du journal d’audit pour obtenir des informations sur l’utilisation du contenu dans leur organisation.

Si vous avez des licences gratuites **Power BI** attribuées à votre compte, ces comptes s’exécutent dans une version commerciale du service **Power BI** et ne font pas partie de l’offre **Power BI US Government**. Pour ces comptes Gratuits, vous pouvez rencontrer les problèmes suivants :

* La passerelle, l’appareil mobile ou l’ordinateur ne peut pas s’authentifier
* Vous ne pouvez pas accéder aux sources de données commerciales Azure
* Les fichiers PBIX doivent être chargés manuellement à partir des sources de données commerciales
* Les applications mobiles Power BI ne sont pas disponibles

Pour résoudre ces problèmes, contactez votre responsable de compte.

## <a name="frequently-asked-questions-faq-for-the-us-government-version-of-the-power-bi-service"></a>FAQ sur la version US Government du service Power BI
Les questions (et réponses) suivantes sont fournies pour vous aider à obtenir rapidement les informations nécessaires au sujet du service.

**Question :** comment migrer mes données commerciales **Power BI** vers le **service Power BI** US Government ?

**Réponse :** votre administrateur doit créer une nouvelle instance de **Power BI** sous un abonnement distinct spécifique à la version US Government. Vous pouvez ensuite répliquer vos données commerciales dans le **service Power BI** US Government, supprimer votre licence commerciale et associer votre domaine existant au nouveau service US Government.

**Question :** pourquoi ne puis-je pas me connecter à un pack de contenu spécifique ?

**Réponse :** vous devez vérifier que votre abonnement est activé avant de vous connecter à ce pack de contenu.

**Question :** je souhaite obtenir **Power BI** pour mon organisation US Government. Par quoi commencer ?

**Réponse :** l’inscription (souvent appelée *intégration*) peut varier en fonction de vos licences et abonnements existants. Pour plus d’informations, voir [Inscription à la version US Government de Power BI](service-govus-signup.md).

**Question :** est-ce que l’URL de connexion à la version US Government de **Power BI** est différente de celle de la version commerciale de **Power BI** ?

**Réponse :** oui, les URL sont différentes. Le tableau suivant présente chaque URL :

| URL de la version commerciale | URL de la version US Government |
| --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) |

## <a name="next-steps"></a>Étapes suivantes
Power BI vous permet d’effectuer des tâches très diverses. Pour obtenir plus d’informations et accéder à des formations, dont un article qui vous montre comment vous inscrire au service, consultez les ressources suivantes :

* [Inscription à Power BI for US Government](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Démonstration de Power BI US Government</a>
* [Formation guidée sur Power BI](guided-learning/gettingstarted.yml?tutorial-step=1)
* [Prise en main du service Power BI](service-get-started.md)
* [Prise en main de Power BI Desktop](desktop-getting-started.md)

